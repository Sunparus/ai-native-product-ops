---
tags:
  - architecture
---

# Prompt Engineering

*The cheapest lever, and usually the first one to pull*

Structuring instructions and examples given to a model to reliably shape its output — before reaching for RAG, fine-tuning, or a bigger model. The most-used technique in the field, and until now, absent from this domain entirely.

## Core techniques

- **Zero-shot** — instruction alone, no examples. Cheapest, works when the task is close to what the model was trained on.
- **Few-shot** — 2–5 worked examples in the prompt. Meaningfully improves reliability on structured or unusual output formats, at the cost of context-window space and per-request tokens.
- **Chain-of-thought** — prompting the model to expose intermediate reasoning before the final answer. Generally improves accuracy on multi-step tasks; costs more output tokens and latency.
- **System prompts** — persistent instructions applied before user input, defining role, constraints, and behavior. The mechanism most production guardrails are actually implemented through — see [Guardrails](../ai-security-risk/guardrails.md).
- **Structured output constraints** — forcing a specific schema (JSON, function-call format) rather than hoping the model produces parseable text.

## A finding worth designing around: position matters

["Lost in the Middle" (Liu et al., Stanford, 2023)](https://arxiv.org/abs/2307.03172) found that models retrieve information most reliably when it sits at the beginning or end of a long context, and measurably worse when it's buried in the middle — even in models explicitly built for long context. Practical implication: if a prompt has one critical instruction or fact among many, its position in the context isn't a cosmetic choice. (Some newer frontier models show reduced sensitivity to this effect — worth re-testing against your specific model rather than assuming the original finding still applies at full strength.)

## Decision Areas

- Is the prompt engineered against a real eval set, or tuned by eyeballing a handful of outputs? The latter produces prompts that look good in a demo and degrade in production — see [Evaluation & Observability](../evaluation-observability/index.md).
- Where does prompt engineering stop being sufficient? The honest signal: when the same failure mode recurs across many different phrasings of the prompt, that's usually a capability gap prompting can't close — the point to consider [Fine-Tuning](fine-tuning.md) or [RAG](rag-agent-architecture.md) instead.
- Is the system prompt versioned and reviewed like code, or edited ad hoc in a chat window? Prompt changes are behavior changes — they belong in the same CI discipline as everything else, see [CI-by-Design](../delivery-operating-practice/ci-by-design.md).

## Source

Chip Huyen, *AI Engineering* — the chapter this page was missing from this domain until now. ["Lost in the Middle"](https://arxiv.org/abs/2307.03172) (Liu et al., Stanford, 2023) for the context-position finding above.

## Related

- [AI/ML Systems Engineering](index.md) — the Model Layer this technique operates within
- [Fine-Tuning & Model Adaptation](fine-tuning.md) — the next lever when prompting stops being enough
- [RAG & Agent Architecture](rag-agent-architecture.md) — the other next lever, for knowledge gaps rather than behavior gaps
- [Evaluation & Observability](../evaluation-observability/index.md) — eval design is what tells you whether a prompt change actually helped
