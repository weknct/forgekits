# Listing Copy — paste-ready

Pre-written copy for every submission destination. Don't invent new claims; this all
derives from the marketplace.json + plugin READMEs.

---

## Marketplace (top-level)

- **Name:** ForgeKits
- **Repo:** `https://github.com/weknct/forgekits`
- **Install:** `/plugin marketplace add weknct/forgekits`
- **Owner:** WEKNCT, INC. · admin@weknct.com · https://forgekits.dev
- **One-liner:** Production-grade Claude Code plugins for marketing automation, AI
  process decomposition, AI-guided SDLC, and MCP server development.
- **Description (long):** ForgeKits is a marketplace of production-grade Claude Code
  plugins built by a Claude Certified Architect. Four packs ship a free Lite edition
  (installable now) with a Premium upgrade: the Client Attraction Engine (marketing
  automation), Process Decomposition (turn any workflow into a governed multi-agent
  architecture), SDLC Forge (run a project across a 9-phase SDLC), and MCP Builder
  (design, secure, and publish MCP servers). Independent; not affiliated with Anthropic.

---

## Per-plugin (4 Lite packs)

### 1 · Client Attraction Engine (Lite)
- **Install:** `/plugin install client-attraction-engine-lite@forgekits`
- **Category:** marketing · **Keywords:** marketing, lead-generation, copywriting, ab-testing, funnel
- **Homepage:** https://forgekits.dev/client-attraction-engine
- **Description:** Free taste of the Client Attraction Engine: Split Test Lab (A/B
  variant generator) + Pipeline Health Check. Upgrade to Premium for the full 6-agent,
  12-skill marketing system.

### 2 · Process Decomposition (Lite)
- **Install:** `/plugin install process-decomposition-lite@forgekits`
- **Category:** productivity · **Keywords:** ai-agents, process-design, automation, decomposition, workflow
- **Homepage:** https://forgekits.dev/process-decomposition
- **Description:** Free intro to the AI Process Decomposition framework: decompose any
  workflow into humans, AI skills, and AI agents. Premium unlocks the full 9-phase
  method, registries, and SOC 2 / HIPAA / GDPR compliance templates.

### 3 · SDLC Forge (Lite)
- **Install:** `/plugin install sdlc-forge-lite@forgekits`
- **Category:** productivity · **Keywords:** sdlc, project-management, agile, devops, automation
- **Homepage:** https://forgekits.dev/sdlc-forge
- **Description:** Free taste of SDLC Forge: the Forge Guide orchestrator, phase
  detection, and the morning-standup command. Premium unlocks 100+ commands, ForgeSync
  (GitHub/ADO/Jira), and 63 templates.

### 4 · MCP Builder (Lite)
- **Install:** `/plugin install mcp-builder-lite@forgekits`
- **Category:** productivity · **Keywords:** mcp, model-context-protocol, ai-agents, tools, typescript, python
- **Homepage:** https://forgekits.dev/mcp-builder
- **Description:** Free starter for building Model Context Protocol (MCP) servers: the
  MCP Architect agent plus Scaffold MCP Server and Design an MCP Tool. Premium adds
  resources, prompts, OAuth, Inspector testing, security review, and publishing.

---

## PR snippet — for anthropics/claude-plugins-official marketplace.json

> Adapt to that repo's actual schema/structure at PR time (it may list marketplaces or
> individual plugins; match the surrounding entries). Representative entry:

```json
{
  "name": "forgekits",
  "source": "weknct/forgekits",
  "description": "Production-grade Claude Code plugins by a Claude Certified Architect: marketing automation (Client Attraction Engine), AI process decomposition, AI-guided SDLC (SDLC Forge), and MCP server development. Free Lite editions with Premium upgrades.",
  "homepage": "https://forgekits.dev",
  "owner": "WEKNCT, INC."
}
```

**PR title:** `Add ForgeKits marketplace (4 plugins by WEKNCT, INC.)`

**PR body:**
> Adds the ForgeKits marketplace (`weknct/forgekits`) — 4 free Lite plugins (Client
> Attraction Engine, Process Decomposition, SDLC Forge, MCP Builder), each with a
> Premium upgrade on forgekits.dev. Built by a Claude Certified Architect. All Lite
> packs pass `claude plugin validate`. Independent; not affiliated with Anthropic.

---

## Short social-bio / submit-box blurb (≤200 chars)

> ForgeKits — production-grade Claude Code plugins: marketing automation, process
> decomposition, AI-guided SDLC, MCP builder. Free Lite + Premium.
> `/plugin marketplace add weknct/forgekits`
