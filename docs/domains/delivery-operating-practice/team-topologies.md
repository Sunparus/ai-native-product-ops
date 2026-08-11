---
tags:
  - lean
  - ci
---

# Team Topologies

The other half of this domain's grounding, and — until now — never actually explained here despite being cited as a source. [Team Topologies](https://teamtopologies.com/) (Skelton & Pais) is a team-design framework built on one core claim: **team structure determines system architecture, not the other way around** (a deliberate inversion of Conway's Law — organizations ship designs that mirror their communication structure, so design the org chart on purpose).

## Four team types

| Type | Owns | AI-delivery application |
|---|---|---|
| **Stream-aligned** | End-to-end delivery of a specific product or feature stream | The team shipping an AI-assisted feature to users — should consume shared AI infrastructure, not build it from scratch |
| **Platform** | Shared, self-service internal capability | Owns the model-serving infrastructure, eval pipelines, and shared tooling stream-aligned teams consume — see [CI-by-Design](ci-by-design.md) |
| **Enabling** | Helps other teams adopt a new capability, temporarily | Onboards teams onto AI-assisted workflows, then hands off — a short-lived team by design, not a permanent dependency |
| **Complicated-subsystem** | A component requiring deep specialist knowledge | Rare in most AI-assisted product work, but real for teams building the model/inference layer itself |

## Three interaction modes

- **Collaboration** — two teams working closely together temporarily, high communication overhead, used deliberately for a bounded period (e.g. a stream-aligned team and the platform team co-designing a new integration point)
- **X-as-a-Service** — one team consumes another's output with minimal communication overhead (a stream-aligned team calling the platform team's eval API without needing to understand its internals)
- **Facilitating** — one team helps another improve, without doing the work for them (an enabling team teaching, not building)

## Why this matters for AI-assisted delivery specifically

The common failure mode: every team tries to own its own AI infrastructure — model access, eval tooling, cost governance — because no platform team exists to own it as a shared service. This multiplies both cognitive load (every stream-aligned team now needs deep AI infrastructure knowledge, not just their product domain) and inconsistency (five teams build five different, incompatible versions of the same guardrails). A platform team offering AI capability as X-as-a-Service is the structural fix — the same logic as [CI-by-Design](ci-by-design.md)'s golden-path tooling, applied to team boundaries instead of pipelines.

## Interrogate

- Is there a platform team who owns shared AI infrastructure as a service, or is every stream-aligned team quietly rebuilding it?
- When two teams are in "collaboration" mode, is there an end date, or has temporary collaboration quietly become a permanent, high-overhead dependency?
- Does an enabling team actually hand off and step back, or does "enabling" become a euphemism for permanent hand-holding?

## Related

- [CI-by-Design](ci-by-design.md) — golden-path tooling is the pipeline-level expression of the same platform-team logic
- [DORA Metrics](dora-metrics.md) — what platform-team investment should actually move
- [AI Adoption & Organizational Maturity](../ai-adoption-maturity/index.md) — team structure is one lever among several for organizational readiness
- [Experts & Sources](../../reference/experts.md) — Matthew Skelton, co-author
