# Workspace Folder Structure

Copy this tree into the working directory, rooted at a folder named after the process slug. All files are Markdown.

```
{process-slug}/
├── .pdf-genesis/        # Raw process description(s) — the discovery phase reads these first
├── context/
│   ├── meta.md
│   ├── goal.md
│   ├── scope.md
│   ├── assumptions.md
│   └── security-and-governance.md
├── todos/
│   ├── human-tasks.md
│   ├── agent-tasks.md
│   ├── skill-tasks.md
│   └── llm-tasks.md
├── insights/
│   ├── interview-log.md
│   ├── design-decisions.md
│   ├── patterns-observed.md
│   └── lessons-learned.md
├── registries/
│   ├── skill-registry.md
│   ├── skills/
│   ├── agent-registry.md
│   ├── agents/
│   ├── tool-registry.md
│   ├── tools/
│   ├── protocol-bindings.md
│   └── dependency-graph.md
└── outputs/
    ├── process-map.md
    ├── orchestration-plan.md
    ├── evaluation-plan.md
    ├── observability-plan.md
    ├── cost-model.md
    ├── cost-estimation-report.md
    ├── data-flow.md
    ├── kpi-definitions.md
    ├── runbook.md
    └── runtime-spec.md
```

## Archiving
Create `insights/archive/` on the first archive event. When an insight file grows past its threshold (design-decisions > 200 lines, interview-log > 300 lines, patterns/lessons > 150 lines), move older entries into a write-once `insights/archive/{filename}-{YYYY-MM}.md` and leave a pointer at the top of the main file.
