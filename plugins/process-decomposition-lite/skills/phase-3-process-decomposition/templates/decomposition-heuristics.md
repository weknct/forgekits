# Decomposition Depth Heuristics

## When to Split (or Merge) Further

| Heuristic | Signal | Threshold | Action |
|-----------|--------|-----------|--------|
| Multi-Error | Skill has multiple error modes needing different recovery | ≥2 distinct recovery strategies | Split into one skill per recovery path |
| Skill Overload | Agent orchestrates too many skills | >5 skills | Introduce sub-agents with narrower bounded contexts |
| Time Threshold | Single step too long for sync execution | >5 minutes | Decompose into async trigger + callback |
| I/O Sprawl | Skill has too many parameters | >5 inputs or >3 outputs | Split into a pipeline of simpler skills |
| Branching Factor | Decision gate has too many paths | >3 paths | Decompose into a hierarchy of binary/ternary gates |
| Token Bloat | Single LLM call needs too much context | >32K tokens input | Split into chunked sub-tasks with aggregation |
| Coupling | Two skills always run together in sequence | 100% co-occurrence | Merge into one skill or formalize as a named pipeline |

## How to Apply

1. After defining a skill or agent, run each heuristic against it.
2. If any triggers, document the rationale in `insights/design-decisions.md`.
3. Apply the prescribed action (split, merge, restructure).
4. Re-register the resulting skills/agents in the registry.
5. Re-run the error-compounding analysis for affected paths.
