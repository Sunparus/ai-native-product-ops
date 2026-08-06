---
name: ai-product-stage-5-launch-rollout
description: Use when planning rollout — staged cohorts, rollback trigger, feedback capture, and end-user change management.
tags:
  - lean
  - evaluation
---

# Stage 5 — Launch & Rollout

**Roles required:** PM (leads), AI Engineer, Enablement/Change Management (or PM-owned if no dedicated function)

**Decisions to lock:** rollout strategy (percentage, cohort), rollback trigger, feedback capture mechanism, end-user training and communication plan.

**Top 5 preventable issues**

| # | Issue | Owner | Prevention |
|---|---|---|---|
| 1 | Full rollout on day one, no staged cohort | PM | Staged rollout with a defined percentage and hold period before expansion |
| 2 | No defined rollback trigger, so a bad launch becomes a judgment call under pressure | PM + AI Engineer | Numeric rollback trigger agreed before launch, not during the incident (this is the kill switch, exercised for real) |
| 3 | User feedback mechanism exists but routes nowhere actionable | PM | Feedback loop has a named owner and a review cadence, not just a collection box |
| 4 | Launch messaging doesn't set accurate expectations about limitations | PM | UX copy signals confidence or uncertainty where relevant |
| 5 | No pre-AI baseline captured, so nobody can prove the launch improved anything | PM + DS | Baseline metric captured before launch, compared after |

**Also non-negotiable:** no plan to train or communicate to the humans whose workflow changes, so adoption stalls even when the model works correctly. *Owner: PM + Enablement. Prevention: a change management plan (training, comms, updated SOPs) ships alongside the model, not after. The best model in the world fails if the people using it don't know what changed or what to do when it's wrong.*

**Stage-gate question:** "What's the specific number that triggers a rollback, and who has the authority to pull it?"

- *Rubber stamp:* "We'll keep an eye on it."
- *Real answer:* a named metric and threshold, and a named person with rollback authority.

---

**Previous:** [← Stage 4 — Evaluation & Governance Review](stage-4-governance-review.md) · **Next:** [Stage 6 — Operate & Monitor →](stage-6-operate-monitor.md)
