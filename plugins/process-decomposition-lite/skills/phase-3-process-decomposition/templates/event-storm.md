# Event Storm, Classification & Decision Gates

## Event Log

```markdown
| # | Event Name | Trigger | Actor | Output | Notes |
|---|-----------|---------|-------|--------|-------|
| 1 | {event} | {what starts it} | {who/what} | {result} | {risks} |
```

## Classification Key

| Classification | Criteria | Symbol |
|----------------|----------|--------|
| Human-in-the-Middle | Judgment, approval, creative, legal, high-stakes | 🧑 |
| AI Skill | Atomic, stateless, single-purpose | ⚡ |
| AI Agent | Stateful, multi-step, orchestrates 2+ skills / routes | 🤖 |
| Raw LLM | One-shot reasoning, no full skill needed | 🧠 |

## Decision Gate

```markdown
### Decision Gate: {name}
- **Location**: Between Event {X} and Event {Y}
- **Question**: {decision}
- **Who decides**: Human | Agent | Skill
- **Options**:
  - Path A: {description} → Event {Z}
  - Path B: {description} → Event {W}
- **Fallback**: {if no decision can be made}
```
