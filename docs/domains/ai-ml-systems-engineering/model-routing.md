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
- **Learned routing** — a small classifier model predicts the best target model per query. Most efficient at scale, adds a new component to maintain and monitor. RouteLLM's own reported result (ICLR 2025): an 85% cost reduction on MT-Bench while retaining 95% of GPT-4-Turbo-equivalent quality — benchmark-specific, not a universal guarantee, but a real, checkable number rather than a directional claim.

## Which to use when

- **Traffic is predictable and task types are well-defined** (support tickets, content categories) — rule-based routing is enough. Resist adding a learned router until the rules actually stop working; it's a maintenance burden you don't need yet.
- **Cost matters more than tail latency, and confidence scoring is available** — cascade routing. The cost savings are real, but budget for the escalation-latency tax on the hard cases; if too much traffic escalates, the cascade isn't saving anything.
- **Traffic is high-volume and heterogeneous enough that rules can't keep up** — learned routing earns its complexity here. Not before.

## Decision Areas

- A learned router is itself a model that needs its own evaluation, monitoring, and retraining cadence — see [Evaluation & Observability](../evaluation-observability/index.md). Treating the router as a fire-and-forget component is how routing quality silently degrades.
- Routing decisions need to be logged and auditable, especially in cascade setups — if a request escalates, you need to know why, not just that it did.

## Product Ops Lens

- **Cross-team dependency:** Routing decisions determine response consistency across every team sharing the same underlying models — a routing-threshold change can silently shift quality or latency for a feature nobody intended to touch.
- **Team topology implication:** Routing infrastructure is platform-team territory the moment more than one product team depends on it; a bespoke router per team multiplies maintenance cost for no real benefit.
- **OKR / roadmap implication:** If a roadmap commitment assumes a specific model tier handles a task, that assumption needs to be explicit — routing can quietly downgrade quality to save cost unless the threshold is a named, agreed decision.
- **Budget implication:** Routing is the single highest-leverage cost lever in this domain — a well-tuned cascade is often the largest cost reduction available without touching product scope at all.
- **Who to loop in:** AI/ML Engineer owns routing logic; loop in the Cost & FinOps counterpart whenever a routing threshold trades quality for cost, not after the threshold is already live.

## Source

[RouteLLM](https://arxiv.org/abs/2406.18665) (Ong et al., UC Berkeley, 2024) and [FrugalGPT](https://arxiv.org/abs/2305.05176) (Chen, Zaharia, Zou — Stanford, 2023), the foundational papers on this specific problem. FrugalGPT predates the June 2025 currency threshold; checked against newer routing papers (GraphRouter, BestRoute, and others published in 2025–2026) that still cite both as the standard baseline references, not as superseded work — the currency check passes, not silently assumed. Notably, Matei Zaharia co-authored FrugalGPT — the same researcher named in this domain's Expertise Leads.

## Related

- [AI/ML Systems Engineering](index.md) — the Orchestration Layer this technique operates within
- [Cost & FinOps](../../reference/cost-finops.md) — routing is one of the primary cost levers in the stack
- [Multi-Vendor Strategy](multi-vendor-strategy.md) — routing across vendors, not just across models from one provider
- [Inference Optimization](inference-optimization.md) — routing and inference optimization are complementary cost/latency levers, often tuned together
- [RAG & Agent Architecture](rag-agent-architecture.md) — routing decisions inside a multi-step agent workflow
