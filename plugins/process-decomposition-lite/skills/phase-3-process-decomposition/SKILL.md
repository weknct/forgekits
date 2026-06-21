---
name: phase-3-process-decomposition
description: Use after discovery to break a process into atomic, classified units — invoke when you need to event-storm a workflow, classify each step as Human / Skill / Agent / LLM, map decision gates, and run an error-compounding analysis to decide where validation checkpoints belong.
---

# Skill: Phase 3 — Process Decomposition

## Purpose
Turn the interview output into an atomic, classified process map. This is where a fuzzy "how it works today" becomes a precise sequence of events, each labelled as a human gate, an AI skill, an AI agent, or a raw LLM call — with decision gates and a hard-nosed error-compounding analysis that tells you where validation checkpoints are mandatory.

## When to Use
- Discovery is complete and you have the steps, failure modes, and an acceptable error rate.
- You need to decide which parts of a process become skills, which become agents, and where humans stay.
- You need to know whether an end-to-end path will actually hit its accuracy target.

## Step 3.1 — Event Storm
List every event (something that happens) in chronological order. Store in `outputs/process-map.md`:

```markdown
## Event Log

| # | Event Name | Trigger | Actor | Output | Notes |
|---|-----------|---------|-------|--------|-------|
| 1 | Contract Received | Email arrives | Human (Client) | Raw contract PDF | Entry point |
| 2 | Contract Triaged | Event 1 | AI Agent: Intake | Categorized metadata | May fail on non-standard formats |
```

## Step 3.2 — Classify Each Event
For every event, assign exactly one execution type:

| Classification | Criteria | Symbol |
|----------------|----------|--------|
| **Human-in-the-Middle** | Judgment, approval, creative input, legal authority, or high-stakes / low error tolerance | 🧑 |
| **AI Skill** | Atomic, stateless, single-purpose (extract, classify, generate, validate, transform) | ⚡ |
| **AI Agent** | Stateful, multi-step, orchestrates 2+ skills or makes routing decisions | 🤖 |
| **Raw LLM** | One-shot reasoning not worth a full skill definition (ad-hoc summary, clarification) | 🧠 |

## Step 3.3 — Identify Decision Gates
Mark every branch point:

```markdown
### Decision Gate: {name}
- **Location**: Between Event {X} and Event {Y}
- **Question**: {What decision is being made?}
- **Who decides**: Human | Agent | Skill
- **Options**:
  - Path A: {description} → Event {Z}
  - Path B: {description} → Event {W}
- **Fallback**: {What happens if no decision can be made?}
```

## Step 3.4 — Error Compounding Analysis
For each execution path, compute compound accuracy. Even 99% per-step accuracy yields ~36% success over 100 steps — this is the single most important number in the whole design.

```markdown
### Path: {name}

| Step | Actor | Per-Step Accuracy | Cumulative Accuracy | Validation Checkpoint? |
|------|-------|-------------------|---------------------|-----------------------|
| 1 | ⚡ SKILL-001 | 99% | 99% | No |
| 2 | 🤖 AGENT-001 | 95% | 94.05% | Yes — independent model validates output |
| 3 | ⚡ SKILL-003 | 98% | 92.17% | No |
| 4 | 🧑 HUMAN-GATE-001 | 99.9% | 92.08% | Inherent (human review) |

**Compound Accuracy**: 92.08%
**Acceptable Threshold**: 90% (from discovery Q17)
**Verdict**: ✅ Within tolerance
```

### Validation Checkpoint Protocol
Insert an independent validation checkpoint when ANY of these is true:
- Cumulative accuracy drops below the threshold (default 95%).
- The next step is high-cost or irreversible.
- The output feeds an external system (API, database, customer-facing).

A checkpoint uses an independent model/skill to verify the previous step's output before proceeding.

## Step 3.5 — Decomposition Depth Assessment
Run each event through the depth heuristics and split/merge as needed. See `templates/decomposition-heuristics.md`:

- **Multi-Error** (≥2 recovery strategies) → split skill per recovery path
- **Skill Overload** (>5 skills) → sub-agents
- **Time Threshold** (>5 min) → async trigger + callback
- **I/O Sprawl** (>5 inputs / >3 outputs) → pipeline of simpler skills
- **Branching Factor** (>3 paths) → hierarchy of binary/ternary gates
- **Token Bloat** (>32K tokens) → chunk + aggregate
- **Coupling** (100% co-occurrence) → merge or formalize as a named pipeline

Document every triggered heuristic and the action taken in `insights/design-decisions.md`.

## Output
- A complete `outputs/process-map.md` with event log, classifications, decision gates, and error-compounding analysis.
- A verdict on whether each path meets the acceptable error rate, with checkpoints inserted where it doesn't.
- A list of events that need further decomposition, with rationale.
- A classified, error-compounded process map ready for the next steps: defining the ⚡ skills and 🤖 agents, specifying human gates, orchestration, security & governance, and runtime. Those later phases (4–9), with their templates and SOC 2 / HIPAA / GDPR compliance kit, are part of Process Decomposition Premium — see https://forgekits.dev/process-decomposition.

## Bundled Templates
- `templates/event-storm.md` — event log + classification + decision gate formats.
- `templates/error-compounding.md` — the compound-accuracy table and checkpoint protocol.
- `templates/decomposition-heuristics.md` — the full depth-heuristic table and how to apply it.
