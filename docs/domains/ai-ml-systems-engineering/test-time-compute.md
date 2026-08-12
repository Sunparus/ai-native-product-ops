---
tags:
  - architecture
  - inference
  - cost
---

# Test-Time Compute & Reasoning Models

*The dominant AI engineering trend of the current cycle — and, until now, absent from this domain entirely*

A fundamentally different lever from everything else on the adaptation ladder or in [Inference Optimization](inference-optimization.md): instead of making inference *faster*, reasoning models deliberately spend *more* inference-time compute — generating and evaluating intermediate reasoning steps before producing a final answer — to trade latency for accuracy on hard problems.

## What actually changed

Traditional models produce one answer in one pass. Reasoning models (OpenAI's o1/o3, DeepSeek-R1, and comparable systems) generate an extended internal reasoning trace first, then answer — closer to "thinking before speaking" than pattern-completion. The foundational reproduction of this technique, [**"s1: Simple test-time scaling"** (Muennighoff et al., Stanford/University of Washington/Allen Institute for AI, 2025)](https://arxiv.org/abs/2501.19393), demonstrated the mechanism with a technique called **budget forcing**: forcing the model's reasoning process to extend (or cut short) by directly controlling how long it "thinks" — and showed that more test-time compute reliably improves performance on hard math and reasoning benchmarks, on a model trained with as few as 1,000 curated examples.

## Why this doesn't fit cleanly into the existing stack

This directly complicates the [Inference Optimization](inference-optimization.md) page's framing. That page is about minimizing latency and cost. Reasoning models deliberately do the opposite for the tasks that need it — spend more time, more compute, more tokens, on purpose, because the accuracy gain justifies the cost. Both are real, valid inference-layer decisions; they're just optimizing for different things, and conflating them produces the wrong architecture call.

## Decision Areas

!!! question "Decision Areas"
    - Does this task actually benefit from extended reasoning, or is a fast, cheap, non-reasoning model already sufficient? Reasoning models cost meaningfully more per request in both latency and tokens — applying them by default, not by task fit, is a common and expensive mistake.
    - Is latency budget for this feature compatible with reasoning-model response times? Users tolerate 10–60 seconds for a research-depth answer; they don't for a chat reply. This is a product decision, not just an engineering one — see Product Ops Lens below.
    - Is pricing being tracked as "thinking time," not just token count? Reasoning models can consume many internal reasoning tokens never shown to the user — a real, easy-to-miss cost surface.

## Product Ops Lens

!!! tip "Product Ops Lens"
    - **Cross-team dependency:** Swapping a fast model for a reasoning model changes response time by an order of magnitude — any product team building UX around this feature needs that latency shift as an explicit input, not a surprise during integration testing.
    - **Team topology implication:** Deciding which tasks warrant reasoning-model cost is an architecture-level call that should be made once, centrally, and exposed as a routing decision (see [Efficient Model Routing](model-routing.md)) — not re-litigated ad hoc by each product team calling the API directly.
    - **OKR / roadmap implication:** If a roadmap commitment assumes near-instant AI responses, verify that the underlying task doesn't actually require reasoning-model latency to hit the accuracy bar the feature needs — these two goals can genuinely conflict, and it's better to know before the commitment than after.
    - **Budget implication:** This is a materially different cost profile from standard inference — reasoning tokens are billed even though the user never sees them. Cost & FinOps needs reasoning-model usage broken out separately from standard inference, not folded into the same line item.
    - **Who to loop in:** Architect for the routing decision (which tasks get reasoning-model treatment), Cost & FinOps counterpart for budget visibility into reasoning-token spend specifically, PM for whether the latency tradeoff is acceptable in the actual product surface.

## Source

["s1: Simple test-time scaling"](https://arxiv.org/abs/2501.19393) (Muennighoff, Yang, Shi, Li, Fei-Fei, Hajishirzi, Zettlemoyer, Liang, Candès, Hashimoto — Stanford/UW/Allen Institute for AI, 2025; published at EMNLP 2025, 800+ citations as of this writing). Source-currency note: this paper predates June 2025 but is cited as the standard foundational reference in papers published through at least early 2026 — checked, not assumed; the field has built on it rather than superseded it.

## Related

- [Inference Optimization](inference-optimization.md) — the directly opposing optimization goal (minimize latency/cost vs. deliberately spend more for accuracy); read both together
- [Efficient Model Routing](model-routing.md) — routing the subset of requests that actually need reasoning-model treatment
- [Prompt Engineering](prompt-engineering.md) — the field's own terminology is shifting from "prompt engineering" toward "context engineering" as reasoning models handle more of the "how" themselves
- [AI/ML Systems Engineering](index.md) — the Model and Inference layers this page sits between
