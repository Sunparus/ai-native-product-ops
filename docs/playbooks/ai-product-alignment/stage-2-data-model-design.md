---
name: ai-product-stage-2-data-model-design
description: Use when choosing the modeling approach (RAG, fine-tune, prompt-only) and defining evaluation criteria, before build starts.
tags:
  - data
  - evaluation
---

# Stage 2 — Data & Model Design

**Roles required:** DE (pipeline), DS (model and eval design), AI Engineer (serving constraints consult)

**Decisions to lock:** RAG vs. fine-tune vs. prompt-only, evaluation metric and target threshold, data pipeline architecture, feature freshness requirements, [human-in-the-loop thresholds](human-in-the-loop.md), vendor exit fallback documented.

**Top 5 preventable issues**

| # | Issue | Owner | Prevention |
|---|---|---|---|
| 1 | Eval metrics get chosen after the model is built, so "good" is defined retroactively | DS | Eval criteria and thresholds are written and signed off before training or prompting starts |
| 2 | Training/reference data reflects a different population than production traffic (survivorship bias, historical skew) | DS | DS documents known biases and gaps explicitly, not just data volume |
| 3 | No freshness SLA on the pipeline, so "real-time" features are actually hours or days stale | DE | DE defines and monitors a freshness SLA per feature, not per pipeline |
| 4 | Feature store and model training use different definitions of the same field (train/serve skew) | DE + DS | Shared feature definitions from a single source of truth, validated at each release |
| 5 | RAG vs. fine-tune vs. prompt-only never gets formally decided, so build starts on the wrong pattern and gets redone | AI Engineer + DS | Use the decision heuristic (data volatility, cost, consistency need) and record the choice with reasoning |

**Stage-gate question:** "What exactly does 'good' mean for this model, in numbers, and who signed off on that threshold?"

- *Rubber stamp:* "It should just work well."
- *Real answer:* a named metric (accuracy, precision/recall, groundedness, etc.), a target number, and who approved it.

---

**Previous:** [← Stage 1 — Discovery & Framing](stage-1-discovery.md) · **Next:** [Stage 3 — Build & Integration →](stage-3-build-integration.md)
