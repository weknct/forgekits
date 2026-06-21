# File Header Convention

Every Markdown file in the workspace begins with this YAML front-matter block:

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

- `framework-version` records which version of the methodology the file was created/last updated under.
- `version` is a plain integer that increments on every meaningful edit.
- `updated-by` identifies the actor that last touched the file, for traceability.
