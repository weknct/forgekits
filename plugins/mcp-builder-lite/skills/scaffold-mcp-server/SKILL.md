---
name: scaffold-mcp-server
description: Use to start a brand-new Model Context Protocol (MCP) server from scratch — invoke when a user wants to create an MCP server, pick between the TypeScript (@modelcontextprotocol/sdk) or Python (mcp / FastMCP) SDK, choose a transport (stdio or Streamable HTTP), and lay out the project with a working entrypoint that registers the server and connects a transport.
---

# Skill: Scaffold MCP Server

## Purpose
Stand up a minimal, correct, runnable MCP server: pick an SDK and transport, create the project layout, and produce an entrypoint that registers a server and connects. This is step 1 of a build — capabilities (tools, resources, prompts) are added afterward by the design skills.

> APIs evolve. Confirm the current package versions, import paths, and transport classes against the official SDK repos (`github.com/modelcontextprotocol/typescript-sdk`, `github.com/modelcontextprotocol/python-sdk`) and `modelcontextprotocol.io` before relying on the exact code below.

## Decisions to make first
1. **SDK / language.** TypeScript (`@modelcontextprotocol/sdk`) or Python (`mcp`). Match the team's stack and where the server will run.
2. **Transport.**
   - **stdio** — the server runs as a local subprocess launched by the client (Claude Code, Claude Desktop). Best default for local/dev tools. JSON-RPC flows over stdin/stdout; **never write anything but protocol messages to stdout** (use stderr for logs).
   - **Streamable HTTP** — the server runs as a standalone HTTP service exposing one endpoint that handles POST and GET (optionally streaming responses via SSE). Use for remote/multi-client servers. Plan for auth (see `add-mcp-auth`).
3. **Capabilities.** Which of tools / resources / prompts will it declare? You only declare what you implement.

## TypeScript scaffold (stdio)

Project layout:
```
my-mcp-server/
  package.json
  tsconfig.json
  src/
    index.ts
  .gitignore        # block .env, node_modules, build
```

Install:
```bash
npm init -y
npm install @modelcontextprotocol/sdk zod
npm install -D typescript @types/node
```

`src/index.ts`:
```ts
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new McpServer({
  name: "my-mcp-server",
  version: "1.0.0",
});

// Tools, resources, and prompts are registered here.
// (See design-mcp-tool / design-mcp-resource / design-mcp-prompt.)

async function main() {
  const transport = new StdioServerTransport();
  await server.connect(transport);
  // Log to stderr only — stdout is reserved for the JSON-RPC protocol.
  console.error("MCP server running on stdio");
}

main().catch((err) => {
  console.error("Fatal:", err);
  process.exit(1);
});
```

Set `"type": "module"` in `package.json` and compile with `tsc` (or run with `tsx` in dev). Build to `build/index.js`, then test with the Inspector (see `test-mcp-server`).

### TypeScript scaffold (Streamable HTTP)
For a remote server, connect a `StreamableHTTPServerTransport` from `@modelcontextprotocol/sdk/server/streamableHttp.js` instead of stdio, mount it on a single HTTP route that accepts POST and GET, and generate a session id:
```ts
import { StreamableHTTPServerTransport } from "@modelcontextprotocol/sdk/server/streamableHttp.js";
import { randomUUID } from "node:crypto";

const transport = new StreamableHTTPServerTransport({
  sessionIdGenerator: () => randomUUID(),
});
await server.connect(transport);
// Wire `transport.handleRequest(req, res, body)` into your HTTP framework's
// handler for the MCP endpoint (POST + GET on the same path).
```
A remote server needs auth before exposure — go to `add-mcp-auth`.

## Python scaffold (stdio) with FastMCP

Project layout:
```
my-mcp-server/
  pyproject.toml
  server.py
  .gitignore        # block .env, __pycache__, .venv
```

Install (the `mcp` package; `cli` extra adds the dev runner / Inspector helpers):
```bash
uv add "mcp[cli]"     # or: pip install "mcp[cli]"
```

`server.py`:
```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("my-mcp-server")

# Tools, resources, and prompts are declared here with decorators.
# (See design-mcp-tool / design-mcp-resource / design-mcp-prompt.)

if __name__ == "__main__":
    mcp.run()  # defaults to the stdio transport
```

### Python scaffold (Streamable HTTP)
Run the same `FastMCP` app over HTTP:
```python
if __name__ == "__main__":
    mcp.run(transport="streamable-http")
```
Again, secure it before exposing it (`add-mcp-auth`).

## Verify the scaffold runs
- **stdio**: launch under the MCP Inspector — `npx @modelcontextprotocol/inspector node build/index.js` (TS) or `npx @modelcontextprotocol/inspector uv run server.py` (Python) — and confirm it initializes. See `test-mcp-server`.
- A freshly scaffolded server with no capabilities will list empty tools/resources/prompts; that is expected. Add capabilities next.

## Next step
Hand off to `design-mcp-tool` to add the first real capability. (For resources, prompts, OAuth for remote servers, Inspector testing, a security review, and publishing, see MCP Builder Premium — https://forgekits.dev/mcp-builder.)
