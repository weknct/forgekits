---
name: design-mcp-tool
description: "Use to define a Model Context Protocol (MCP) tool well — invoke when a user wants to add or refine a tool on an MCP server: a precise inputSchema and outputSchema, accurate annotations (readOnlyHint, destructiveHint, idempotentHint, openWorldHint), a clear model-facing description, and a robust handler with input validation, structured results, and correct error reporting."
---

# Skill: Design an MCP Tool

## Purpose
Tools are the model-controlled primitive: the client lists them (`tools/list`) and the model calls them (`tools/call`). The quality of a tool is mostly the quality of its **schema and description** — that is what the model reads to decide whether and how to call it. This skill produces a tool that is precise, safe, and useful.

> Verify field names and SDK signatures against `modelcontextprotocol.io/specification` (the `server/tools` page) and the SDK repos before shipping — the spec revision moves.

> This is a Lite skill. Designing resources and prompts, securing remote servers with OAuth, testing with the MCP Inspector, the full security-review pass, and packaging/publishing are in MCP Builder Premium — https://forgekits.dev/mcp-builder.

## The shape of a tool (current spec)
A tool definition includes:
- **`name`** — unique identifier (the model calls this). Stable, snake_case or kebab; treat as an API name.
- **`title`** *(optional)* — human-readable display name for UIs.
- **`description`** — what it does, when to use it, and any important constraints. Write it for the model.
- **`inputSchema`** — JSON Schema (object) describing the arguments.
- **`outputSchema`** *(optional)* — JSON Schema describing the structured result. If provided, the server **MUST** return `structuredContent` conforming to it, and clients **SHOULD** validate it.
- **`annotations`** *(optional)* — behavior hints (see below). **Untrusted** unless from a trusted server; never a security boundary.

### Annotations
- `readOnlyHint` — the tool does not modify its environment.
- `destructiveHint` — may perform destructive updates (only meaningful when not read-only).
- `idempotentHint` — repeated calls with the same args have no additional effect.
- `openWorldHint` — interacts with an open/external world (e.g. the web) vs. a closed system.
Set these honestly so clients can present the right confirmations.

### Tool results
Results carry `content` (unstructured: `text`, `image`, `audio`, `resource_link`, embedded `resource`) and optionally `structuredContent` (a JSON object). When you define an `outputSchema`, return `structuredContent`; for backwards compatibility also serialize it into a `text` content block. Tool *execution* errors are reported in-band with `isError: true` (so the model can see and react), not as JSON-RPC protocol errors. Protocol errors are reserved for unknown tools / invalid arguments / server faults.

## Write the description for the model
- State the action in the first clause ("Search the issue tracker for...").
- Say when to use it and when **not** to.
- Document units, formats, and limits that the schema can't fully express ("`limit` max 100", "dates are ISO-8601 UTC").
- Keep it specific; the model uses this to disambiguate from other tools.

## TypeScript: `registerTool` with input + output schema
```ts
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { z } from "zod";

const server = new McpServer({ name: "my-mcp-server", version: "1.0.0" });

server.registerTool(
  "get_weather",
  {
    title: "Weather lookup",
    description:
      "Get current weather for a city. Use when the user asks about " +
      "present conditions. Not a forecast. `city` is a city name or postal code.",
    inputSchema: {
      city: z.string().min(1).max(100).describe("City name or postal code"),
      units: z.enum(["metric", "imperial"]).default("metric"),
    },
    outputSchema: {
      temperature: z.number().describe("Temperature in the requested units"),
      conditions: z.string(),
    },
    annotations: {
      readOnlyHint: true,
      openWorldHint: true,
    },
  },
  async ({ city, units }) => {
    try {
      const data = await fetchWeather(city, units); // your implementation
      const output = { temperature: data.temp, conditions: data.summary };
      return {
        content: [{ type: "text", text: JSON.stringify(output) }],
        structuredContent: output,
      };
    } catch (err) {
      // In-band tool error so the model can react and retry/adjust.
      return {
        content: [{ type: "text", text: `Weather lookup failed: ${(err as Error).message}` }],
        isError: true,
      };
    }
  }
);
```
Notes: zod validates and coerces inputs before your handler runs; the SDK derives the JSON Schema from it. Keep secrets in env vars (`process.env.WEATHER_API_KEY`), never inline.

## Python (FastMCP): typed tool with structured output
```python
from pydantic import BaseModel, Field
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("my-mcp-server")

class Weather(BaseModel):
    temperature: float = Field(description="Temperature in the requested units")
    conditions: str

@mcp.tool()
def get_weather(city: str, units: str = "metric") -> Weather:
    """Get current weather for a city. Use for present conditions, not forecasts.

    Args:
        city: City name or postal code.
        units: "metric" or "imperial".
    """
    if not city.strip():
        raise ValueError("city must not be empty")
    data = fetch_weather(city, units)  # your implementation
    return Weather(temperature=data.temp, conditions=data.summary)
```
FastMCP derives the `inputSchema` from the type hints and the `outputSchema` from the `BaseModel` return type, and returns structured content automatically. Raising an exception surfaces as a tool error to the client.

## Robust handler checklist
- **Validate beyond the schema.** Enforce ranges, enums, allow-lists, and cross-field rules the JSON Schema can't express. Reject early.
- **Treat all arguments as untrusted.** Never interpolate them into shell commands, SQL, file paths, or URLs without sanitizing/parameterizing. (See `mcp-security-review`.)
- **Fail in-band.** Return `isError: true` with a useful message for execution failures; reserve protocol errors for malformed calls.
- **Bound the work.** Apply timeouts, size/row limits, and (for outbound calls) rate limits. Don't return unbounded payloads.
- **No secret leakage.** Don't echo args containing secrets, and don't put secret values in errors or results.
- **Be honest in annotations.** If it writes or deletes, it is not `readOnlyHint`.

## Next step
Add more capabilities (`design-mcp-resource`, `design-mcp-prompt`), then `test-mcp-server` to call the tool through the Inspector.
