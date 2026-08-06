---
name: ai-product-stage-6-operate-monitor
description: Use for ongoing operation — quality monitoring, drift detection, cost review, and the incident postmortem process.
tags:
  - evaluation
  - resilience
  - ci
---

# Stage 6 — Operate & Monitor

**Roles required:** AI Engineer, DE, PM (shared, ongoing ownership)

**Decisions to lock:** monitoring cadence, drift detection process, cost review cadence, recurring drill schedule for kill switch and backup restore.

**Top 5 preventable issues**

| # | Issue | Owner | Prevention |
|---|---|---|---|
| 1 | Monitoring covers uptime and latency only, not answer quality | AI Engineer + DS | A running quality sample or eval process, not just infra metrics |
| 2 | Data drift goes undetected because nobody owns data quality after launch | DE | DE owns a standing data quality/drift monitor, not just launch-time validation |
| 3 | Cost creeps up silently as usage grows, discovered only at the invoice | AI Engineer + PM | A cost dashboard reviewed on a defined cadence, with an alert threshold |
| 4 | Model or vendor updates happen with no internal review | AI Engineer | Pinned versions; any update re-enters the Stage 4 eval gate |
| 5 | Feedback is collected but never fed back into the next iteration | PM | A recurring review cadence that explicitly closes the loop from feedback to backlog |

**Stage-gate question:** "If quality quietly degraded over the last month, how would we actually know?"

- *Rubber stamp:* "We'd see it in the metrics."
- *Real answer:* names the specific quality signal tracked, and the cadence it's reviewed on.

## Incident postmortem

Triggered every time the kill switch fires, not reserved for major incidents only.

- **Owner:** AI Engineer runs it, PM ensures it actually happens.
- **Timeline:** scheduled within 5 business days of any kill-switch event.
- **Required output:** root cause, what the eval or monitoring missed, and specific action items with named owners.
- **Non-negotiable:** action items feed back into Stage 2 assumptions and Stage 4 eval criteria. A postmortem that doesn't change anything is a report, not a postmortem.

**Stage-gate question:** "Show me the last postmortem and what actually changed because of it."

- *Rubber stamp:* "We wrote it up and filed it."
- *Real answer:* names a specific change to eval criteria, monitoring, or process that resulted directly from the last incident.

## Related

- [CI-by-Design](../ci-by-design.md) — the same shift-left, closed-loop discipline applied to code and prompts
- [Case Studies](../../reference/case-studies.md) — see the sandbox containment case for what an undisciplined postmortem loop costs

---

**Previous:** [← Stage 5 — Launch & Rollout](stage-5-launch-rollout.md) · **Back to:** [Playbook overview](index.md)
