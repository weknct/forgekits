# SDLC Forge (Lite)

A free taste of **SDLC Forge** — an AI-guided software delivery framework for Claude Code that runs a project from initial idea through development, delivery, and end-of-life across a **9-phase SDLC** (Setup → Genesis → Discovery → POC → PRD → Backlog → Sprint Planning → Sprint Execution → Sprint Review → Delivery).

The Lite plugin ships the orchestration core, so you can ask **"what's next?"** at any point in your project and get routed to the right activity — no setup, no cost.

## What's included (free)

| Component | Type | What it does |
|-----------|------|--------------|
| **Forge Guide** (`forge-guide`) | Agent | The SDLC orchestrator. Detects your current phase from project state and routes you to the highest-value next action. |
| **Phase Detection** (`phase-detection`) | Skill | The deterministic "what phase am I in?" logic — first-match-wins detection across all 9 phases with the recommended next step. |
| **Morning Standup** (`/morning-standup`) | Command | A daily standup brief: yesterday's progress, today's plan, blockers, and sprint pulse, pulled from your trackers. |

## Install

```
/plugin install sdlc-forge-lite@forgekits
```

Once installed, ask the Forge Guide *"what's next?"* on any project, or run `/morning-standup` for a daily brief. The phase-detection skill auto-invokes when you ask where your project stands.

## Upgrade to Premium

Lite gives you the orchestration and daily-standup layer. **Premium** gives you the whole framework:

- **100+ natural-language commands** across planning, sprint management, scope governance, day-to-day operations, reporting, stakeholders, quality & security, architecture, and project lifecycle — including `create PRD`, `break down PRD`, `plan sprint`, `start sprint`, `new sprint ceremony`, `run retrospective`, and more.
- **ForgeSync** — a PowerShell module for two-way sync of work items (stories, bugs, epics, spikes) with **GitHub Issues, Azure DevOps, or Jira**.
- **63 project templates** — PRDs, epics, user stories, sprints, ADRs, risk/assumptions/tech-debt registers, status reports, runbooks, and more.

Learn more and purchase a license at **https://forgekits.dev/sdlc-forge**.

---

Part of **ForgeKits** — production-grade Claude Code plugins. Built by a Claude Certified Architect.
