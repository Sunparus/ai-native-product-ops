---
name: human-in-the-loop-threshold
description: Use before Build starts, to decide which AI actions require human approval and which can run unsupervised.
tags:
  - security
  - governance
---

# Human-in-the-Loop Threshold

Not every AI action should run unsupervised. Before build starts, name which actions the system can take on its own and which require a human to approve first. This is a design decision, not a monitoring afterthought.

| Action category | Example | Human approval required? |
|---|---|---|
| Read-only / informational | Summarize a document, answer a question | No |
| Reversible, low-stakes write | Draft an email, tag a ticket | No, but logged |
| Reversible, high-stakes write | Update a customer record | Yes, until reliability is proven over time |
| Irreversible or high-value action | Move money, close an account, send external communication | Yes, always |

**Owner:** PM + Architect. **Decided at:** [Stage 2](stage-2-data-model-design.md). **Enforced at:** [Stage 3](stage-3-build-integration.md). **Audited at:** [Stage 4](stage-4-governance-review.md).

**Stage-gate question:** "Which specific actions can this system take without a human clicking approve, and who decided that?"

- *Rubber stamp:* "It's pretty safe, so it just goes."
- *Real answer:* names the action categories from a table like the one above, and names who signed off on where the line sits.

## Related

- [AI Security — Guardrails](../../domains/ai-security/guardrails.md) — action-approval gates as a system-level control
