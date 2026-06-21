# Registry Index Headers

Registry indexes are lightweight — one row per item for fast lookup. Read the index first; only open a full definition file when a row matches.

## Skill Registry Index (`registries/skill-registry.md`)

```markdown
## Skill Registry Index

| ID | Name | Version | Status | Purpose (short) |
|----|------|---------|--------|-----------------|
| SKILL-001 | Document Extractor | 1.0.0 | Active | Extract structured data from documents |
```

## Agent Registry Index (`registries/agent-registry.md`)

```markdown
## Agent Registry Index

| ID | Name | Version | Status | Role (short) | Skills Count |
|----|------|---------|--------|-------------|-------------|
| AGENT-001 | Intake Agent | 1.0.0 | Active | Receive and categorize work items | 3 |
```

## Tool Registry Index (`registries/tool-registry.md`)

```markdown
## Tool Registry Index

| ID | Name | Version | Status | Category | Provider | Pricing Model | Purpose (short) |
|----|------|---------|--------|----------|----------|---------------|-----------------|
| TOOL-001 | OpenAI GPT | 1.0.0 | Active | LLM API | OpenAI | Pay-per-use | LLM inference for text generation and reasoning |
```

Status values: skills/agents use Draft | Active | Deprecated; tools add Seed.
