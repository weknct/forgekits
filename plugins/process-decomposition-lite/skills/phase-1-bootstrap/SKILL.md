---
name: phase-1-bootstrap
description: Use at the very start of a process decomposition to stand up the working file system — invoke when a user is beginning to decompose a new process and you need to create the context, todos, insights, registries, and outputs workspace before any analysis.
---

# Skill: Phase 1 — Bootstrap the Workspace

## Purpose
Create the durable file system that holds every artifact of the decomposition. Nothing else happens until this workspace exists — it is how the process keeps state across sessions, agents, and memory compactions.

## When to Use
- A user is starting to decompose a new process, workflow, or business operation.
- You need a clean, consistent place to record context, tasks, insights, registries, and outputs.
- You are resuming work and the `{process-slug}/` folder does not yet exist.

## Steps

1. **Name and slug the process.** Pick a short, kebab-case slug from the process name (e.g. "Invoice Validation" → `invoice-validation`). All paths are relative to a root folder named after that slug.

2. **Capture the seed description.** If the user supplied a description (or files), drop them into `{process-slug}/.pdf-genesis/` as the raw input the discovery phase will read first.

3. **Create the folder structure.** All files are Markdown:

```
{process-slug}/
├── context/
│   ├── meta.md                       # Framework version, migration history, status
│   ├── goal.md                       # North-star goal, refined as understanding evolves
│   ├── scope.md                      # Boundaries — what's in, what's out
│   ├── assumptions.md                # Running list of assumptions
│   └── security-and-governance.md    # Security policies, data classification, governance
├── todos/
│   ├── human-tasks.md                # Tasks requiring human approval or input
│   ├── agent-tasks.md                # Tasks assigned to AI agents
│   ├── skill-tasks.md                # Atomic skill executions pending/complete
│   └── llm-tasks.md                  # Raw LLM reasoning tasks (no agent wrapper)
├── insights/
│   ├── interview-log.md              # All Q&A pairs, timestamped
│   ├── design-decisions.md           # Why we chose X over Y — rationale log
│   ├── patterns-observed.md          # Recurring patterns across the process
│   └── lessons-learned.md            # Corrections and learnings
├── registries/
│   ├── skill-registry.md             # Index: one line per skill
│   ├── skills/                       # Full skill definitions (SKILL-{NNN}.md)
│   ├── agent-registry.md             # Index: one line per agent
│   ├── agents/                       # Full agent definitions (AGENT-{NNN}.md)
│   ├── tool-registry.md              # Index: one line per tool
│   ├── tools/                        # Full tool definitions (TOOL-{NNN}.md)
│   ├── protocol-bindings.md          # MCP tool defs, A2A agent cards, API mappings
│   └── dependency-graph.md           # Tool→Skill→Agent→Human Gate chains
└── outputs/
    ├── process-map.md                # Final decomposed process map
    ├── orchestration-plan.md         # Execution order, handoffs, decision gates
    ├── evaluation-plan.md            # Test scenarios, guardrails, acceptance criteria
    ├── observability-plan.md         # Traces, metrics, alerts, dashboards
    ├── cost-model.md                 # Token budgets, per-execution costs, rate limits
    ├── cost-estimation-report.md     # Tool-level cost breakdown with scaling scenarios
    ├── data-flow.md                  # Data lineage, transformation chains, PII flow
    ├── kpi-definitions.md            # Process-level KPIs with targets and baselines
    ├── runbook.md                    # Operational runbook
    └── runtime-spec.md               # Orchestration engine, runtime, channels, deployment
```

4. **Apply the file header convention.** Every Markdown file begins with this front-matter block so any future actor knows what it is and when it changed:

```markdown
---
file: {filename}
process: {process-name}
framework-version: 2.3.0
created: {ISO-8601 timestamp}
last-updated: {ISO-8601 timestamp}
updated-by: {actor-id — human | agent-name | skill-name | llm}
version: {integer, incrementing}
---
```

5. **Seed `context/meta.md`.** Record the process name, slug, framework version (2.3.0), status (`bootstrapped`), and an empty migration history.

6. **Pre-populate the registry indexes (optional).** If common skills/agents/tools obviously apply, seed the registry index files now so later phases reuse rather than duplicate. See `templates/registry-headers.md` for the index table formats.

## Output
- A ready `{process-slug}/` workspace with every folder and stub file created and headed.
- A one-line confirmation of the slug chosen and where the seed description was placed.
- A pointer to the next step: with the workspace in place, run Process Decomposition (`phase-3-process-decomposition`) to event-storm and classify the process. (The full Deep Discovery interview phase is part of Process Decomposition Premium.)

## Bundled Templates
- `templates/folder-structure.md` — the full workspace tree to copy.
- `templates/file-header.md` — the front-matter convention for every file.
- `templates/registry-headers.md` — index table headers for the skill, agent, and tool registries.
