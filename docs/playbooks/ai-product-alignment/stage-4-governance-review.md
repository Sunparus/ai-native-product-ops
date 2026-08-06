---
name: ai-product-stage-4-governance-review
description: Use for the go/no-go production decision — evaluation results, risk classification, bias testing, and legal sign-off.
tags:
  - governance
  - evaluation
  - security
---

# Stage 4 — Evaluation & Governance Review

**Roles required:** DS (leads eval), Architect, Governance/Enablement, Legal (contract and liability sign-off), Security (adversarial test results)

**Decisions to lock:** go/no-go for production, risk tier classification, audit logging requirements, bias/fairness sign-off, confirmation that kill switch and isolation controls actually work as designed.

**Top 5 preventable issues**

| # | Issue | Owner | Prevention |
|---|---|---|---|
| 1 | Evaluation only covers the happy path, not edge cases or adversarial inputs | DS | Eval set explicitly includes edge cases, plus a red-team pass before sign-off |
| 2 | Bias/fairness testing skipped because "there's no obviously sensitive attribute" | DS + Governance | Bias testing is mandatory above a defined risk tier, not optional by assumption |
| 3 | Audit logging spec is written after launch, so the first incident has no usable trail | Governance + AI Engineer | Logging spec is a build requirement, reviewed at this gate, not a post-launch fix |
| 4 | Risk tier assigned informally in conversation, never documented | Governance | Written risk classification, with the assigned tier and who assigned it |
| 5 | Sign-off given based on a demo, not the actual eval results against Stage 2 thresholds | PM + Governance | Sign-off explicitly references the numeric eval results, not a live demo impression |

**Also non-negotiable:** security testing results (prompt injection, exfiltration attempts) aren't part of the sign-off packet, only functional eval results get reviewed. *Owner: Security + Governance. Prevention: the security test report is a required attachment to the go/no-go decision, not a separate track that may or may not happen.*

**Stage-gate questions:**

- "Show me the eval results against the thresholds we set in Stage 2, not a demo."
    - *Rubber stamp:* "It looked good in the demo."
    - *Real answer:* actual eval numbers vs. target, clear pass/fail per metric.
- "Has Legal signed off on this specific use case's data flows and liability exposure, separately from the master vendor agreement?"
    - *Rubber stamp:* "Legal already reviewed the vendor contract when we signed the deal."
    - *Real answer:* confirms this specific use case (its data, its actions, its blast radius) was reviewed, not just the general vendor relationship.

## Related

- [Data Governance — Core Principles](../../domains/data-governance/core-principles.md)
- [DAMA-DMBOK Operationalization](../dmbok-operationalization.md) — named decision rights and auditable controls, same discipline applied here

---

**Previous:** [← Stage 3 — Build & Integration](stage-3-build-integration.md) · **Next:** [Stage 5 — Launch & Rollout →](stage-5-launch-rollout.md)
