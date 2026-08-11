---
tags:
  - lean
  - ci
  - evaluation
---

# CI-Processes-by-Design for AI

*Engineering practice — verification as infrastructure*

Continuous integration extended to cover model behavior, not just code: every change (prompt, model version, retrieved data source) runs through automated evaluation before reaching production, the same way code runs through tests.

- **Shift-left principle** — catch failures in evaluation pipelines, not in production. Costs compound the later a defect is caught.
- **Golden-path tooling** — one sanctioned, secure, pre-approved path to ship AI features is adopted faster than a rulebook, because it's the path of least resistance.
- **Resilience pairs with this directly** — circuit-breaker patterns (auto-disable a failing model/tool call) and defined blast radius (contain failure to one team/workflow) are CI concerns, not incident-response afterthoughts.

**Source:** *Accelerate* (Forsgren, Humble, Kim) — [dora.dev](https://dora.dev/) for the living, actively maintained research — DORA metrics (deployment frequency, lead time, change failure rate, recovery time) are the standard way to measure whether this is actually working.

## Related

- [Team Topologies](team-topologies.md) — the platform-team pattern that makes golden-path tooling organizationally sustainable, not just technically correct
- [Evaluation & Observability](../evaluation-observability/index.md) — the automated eval pipelines this practice depends on
- [Playbook: CI-by-Design](../../playbooks/ci-by-design.md)
