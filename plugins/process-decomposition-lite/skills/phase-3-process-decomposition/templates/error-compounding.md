# Error Compounding Analysis

Compute compound accuracy for each execution path. Multiply per-step accuracies; the product is end-to-end success. Even 99% per step → ~36% over 100 steps.

```markdown
### Path: {name}

| Step | Actor | Per-Step Accuracy | Cumulative Accuracy | Validation Checkpoint? |
|------|-------|-------------------|---------------------|-----------------------|
| 1 | ⚡ SKILL-001 | 99% | 99% | No |
| 2 | 🤖 AGENT-001 | 95% | 94.05% | Yes |
| 3 | ⚡ SKILL-003 | 98% | 92.17% | No |

**Compound Accuracy**: {product}%
**Acceptable Threshold**: {from discovery Q17}%
**Verdict**: ✅ Within tolerance | ❌ Below threshold — add checkpoints
```

## Validation Checkpoint Protocol

Insert an independent validation checkpoint when ANY holds:
- Cumulative accuracy drops below the threshold (default 95%).
- The next step is high-cost or irreversible.
- The output feeds an external system (API, DB, customer-facing).

A checkpoint uses an independent model/skill to verify the previous step's output before proceeding.
