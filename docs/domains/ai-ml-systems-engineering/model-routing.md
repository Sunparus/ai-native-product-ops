---
tags:
  - architecture
  - inference
  - cost
---

# Efficient Model Routing

*Optimization — cost/latency/capability trade-off*

Techniques for directing each request to the most appropriate model automatically, rather than hardcoding one model for all traffic.

- **Rule-based routing** — classify task type, route by fixed policy. Simple, auditable, coarse.
- **Cascade routing** — attempt a cheap/fast model first, escalate to a stronger model only on low-confidence output. Strong cost savings, adds latency on escalation.
- **Learned routing** — a small classifier model predicts the best target model per query. Most efficient at scale, adds a new component to maintain and monitor.

**Source:** Academic references — "RouteLLM" (UC Berkeley) and "FrugalGPT" (Stanford), the foundational papers on this specific problem.
