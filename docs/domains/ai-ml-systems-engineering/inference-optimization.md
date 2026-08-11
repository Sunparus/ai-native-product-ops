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

## Source

Chip Huyen, *AI Engineering* — inference optimization gets a dedicated chapter; [vLLM's own technical documentation](https://docs.vllm.ai/) is the current practical reference for continuous batching and KV-cache management specifically.

## Related

- [AI/ML Systems Engineering](index.md) — the Inference Layer this page expands on
- [Cost & FinOps](../../reference/cost-finops.md) — every technique here is fundamentally a cost/latency trade-off
- [Efficient Model Routing](model-routing.md) — routing decisions happen alongside, not instead of, inference optimization
