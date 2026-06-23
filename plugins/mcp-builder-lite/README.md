# MCP Builder (Lite)

A free starter for building **Model Context Protocol (MCP) servers** with Claude Code. Stand up a new server in TypeScript or Python and design your first tool the right way — with a precise schema, honest annotations, and a robust, validated handler.

> MCP is the open protocol that standardizes how applications give context to LLMs. This Lite plugin gets you from zero to a working server with a real tool. The full build pipeline — resources, prompts, OAuth, testing, security review, and publishing — is in MCP Builder Premium.

## What's included

| Slug | Component | What it does |
|------|-----------|--------------|
| `mcp-architect` | Agent | Orchestrates the start of a build: clarify the goal, scaffold, design the first tool |
| `scaffold-mcp-server` | Skill | Start a new server: pick TS or Python SDK + transport (stdio / Streamable HTTP), project layout, working entrypoint |
| `design-mcp-tool` | Skill | Define a tool with a precise `inputSchema`/`outputSchema`, accurate annotations, and a handler that validates input and reports errors correctly |

## Install

```
/plugin install mcp-builder-lite@forgekits
```

## How to use

Ask the **MCP Architect** agent to help you build a server ("scaffold an MCP server in TypeScript that I can run locally"), or invoke a skill directly. The architect routes you: scaffold first, then design your first tool.

## Upgrade to Premium

**MCP Builder (Premium)** adds the rest of the pipeline:

- `design-mcp-resource` — read-only data + URI templates
- `design-mcp-prompt` — reusable prompt templates
- `add-mcp-auth` — OAuth 2.1 for remote (Streamable HTTP) servers
- `test-mcp-server` — MCP Inspector + real-client round-trips
- `mcp-security-review` — injection, least privilege, secrets, rate limits
- `publish-mcp-server` — package (npm/PyPI), document, and register (`.mcp.json`)

```
/plugin install mcp-builder@forgekits-premium
```

Get it at **https://forgekits.dev/mcp-builder**.

## A note on accuracy

The MCP spec and SDKs move quickly. This plugin is written against the current specification and official SDKs, and instructs Claude to re-verify version-specific details at build time. Sources used:

- MCP specification (tools, transports): https://modelcontextprotocol.io/specification
- MCP docs: https://modelcontextprotocol.io
- TypeScript SDK (`@modelcontextprotocol/sdk`): https://github.com/modelcontextprotocol/typescript-sdk
- Python SDK (`mcp` / FastMCP): https://github.com/modelcontextprotocol/python-sdk
- Connect Claude Code to MCP servers: https://code.claude.com/docs/en/mcp

---

Part of **ForgeKits** — production-grade Claude Code plugins. (c) 2026 WEKNCT, INC.
