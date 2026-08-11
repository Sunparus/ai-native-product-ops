---
tags:
  - architecture
  - inference
  - cost
---

# Inference Optimization

*What "batching, quantization, GPU allocation" actually means in 2026 — the Inference Layer's bullet list, made current*

## Core techniques

- **Continuous batching** — grouping requests dynamically as they arrive, rather than waiting to fill a fixed batch. The current default in serving frameworks (vLLM and comparable), replacing older static batching that wasted GPU capacity waiting for a batch to fill.
- **Speculative decoding** — a small, fast "draft" model proposes several tokens ahead, which the larger target model verifies in parallel rather than generating token-by-token. Meaningful latency reduction with no quality loss when implemented correctly, at the cost of running two models.
- **KV-cache management** — the key-value cache from attention layers is the dominant memory cost during generation. How it's allocated, shared across requests, and evicted is now a first-class serving-infrastructure concern, not an implementation detail.
- **Quantization** — reducing numerical precision of model weights (e.g., to 8-bit or 4-bit) to shrink memory footprint and increase throughput, at a small, measurable accuracy cost that needs to be evaluated, not assumed acceptable.

## Decision Areas

- Is latency measured as time-to-first-token, or total generation time? They have different bottlenecks and different optimization levers — conflating them produces the wrong fix.
- Is the serving stack's batching strategy actually visible and tunable, or an unexamined default from whatever framework was picked first?
- Does quantization's accuracy cost get measured against the eval set before shipping, or assumed to be negligible?

## Product Ops Lens

- **Cross-team dependency:** Batching strategy and quantization choices directly set latency, which shapes what UX a product team can credibly promise — instant single-shot response, streaming, or async batch. A platform-side batching change can silently break a product team's latency assumptions if it isn't communicated upstream.
- **Team topology implication:** This is platform-team territory by nature (see [Team Topologies](../delivery-operating-practice/team-topologies.md)) — product teams should consume inference as a service with a published latency/cost SLA, not each tune their own serving stack independently.
- **OKR / roadmap implication:** If a roadmap commitment depends on sub-200ms response time, that's an infrastructure capacity dependency that belongs in planning conversations explicitly, not something discovered when the feature ships slow.
- **Budget implication:** Quantization and batching are where "why does our AI feature cost 3x the competitor's" gets answered — or quietly avoided. A real FinOps conversation, not just an engineering one.
- **Who to loop in:** AI/Platform Engineer owns the serving stack; loop in the Cost & FinOps counterpart when latency and cost trade-offs are being decided, not after they're already shipped.

## Source

Chip Huyen, *AI Engineering* — inference optimization gets a dedicated chapter; [vLLM's own technical documentation](https://docs.vllm.ai/) is the current practical reference for continuous batching and KV-cache management specifically.

## Related

- [AI/ML Systems Engineering](index.md) — the Inference Layer this page expands on
- [Cost & FinOps](../../reference/cost-finops.md) — every technique here is fundamentally a cost/latency trade-off
- [Efficient Model Routing](model-routing.md) — routing decisions happen alongside, not instead of, inference optimization
