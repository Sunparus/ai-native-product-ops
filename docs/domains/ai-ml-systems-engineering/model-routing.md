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

## Which to use when

- **Traffic is predictable and task types are well-defined** (support tickets, content categories) — rule-based routing is enough. Resist adding a learned router until the rules actually stop working; it's a maintenance burden you don't need yet.
- **Cost matters more than tail latency, and confidence scoring is available** — cascade routing. The cost savings are real, but budget for the escalation-latency tax on the hard cases; if too much traffic escalates, the cascade isn't saving anything.
- **Traffic is high-volume and heterogeneous enough that rules can't keep up** — learned routing earns its complexity here. Not before.

## Watch-outs

- A learned router is itself a model that needs its own evaluation, monitoring, and retraining cadence — see [Evaluation & Observability](../evaluation-observability/index.md). Treating the router as a fire-and-forget component is how routing quality silently degrades.
- Routing decisions need to be logged and auditable, especially in cascade setups — if a request escalates, you need to know why, not just that it did.

**Source:** Academic references — "RouteLLM" (UC Berkeley) and "FrugalGPT" (Stanford), the foundational papers on this specific problem.

## Related

- [AI/ML Systems Engineering](index.md) — the Orchestration Layer this technique operates within
- [Cost & FinOps](../../reference/cost-finops.md) — routing is one of the primary cost levers in the stack
- [Multi-Vendor Strategy](multi-vendor-strategy.md) — routing across vendors, not just across models from one provider
