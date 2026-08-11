---
tags:
  - architecture
---

# RAG & Agent Architecture

*Closing knowledge gaps and coordinating multi-step work — the two patterns most systems eventually need*

Previously reduced to one sentence each inside the Context and Orchestration layer descriptions. Both deserve real treatment: they're where most of the architectural complexity in a production AI system actually lives.

## RAG patterns, in order of complexity

- **Naive RAG** — embed the query, retrieve top-k similar chunks, stuff them into context, generate. Works for well-scoped knowledge bases; degrades fast once the corpus is large, heterogeneous, or requires multi-hop reasoning.
- **Hybrid search** — combining sparse retrieval (keyword/BM25) with dense vector similarity, rather than relying on embeddings alone. Validated in peer-reviewed research, not just common practice: [Luan et al. (Google Research, *TACL* 2021)](https://aclanthology.org/2021.tacl-1.20/) found sparse and dense methods retrieve complementary results, with hybrids outperforming either alone — the practical version of that finding is that pure vector search misses exact-match terms (product codes, names) that keyword search catches trivially.
- **Re-ranking RAG** — retrieve a larger candidate set cheaply, then re-rank with a more expensive (often cross-encoder) model before generation. Trades latency for precision.
- **Agentic RAG** — the model decides *whether* and *what* to retrieve, potentially issuing multiple retrieval calls across a reasoning chain, rather than retrieval happening once, upfront, unconditionally.
- **Graph RAG** — retrieval over a knowledge graph rather than flat vector similarity, for questions that require traversing relationships (this entity connects to that entity) rather than semantic similarity alone.

## Agent patterns

- **Single tool-use loop** — the foundational pattern named **[ReAct](https://arxiv.org/abs/2210.03629)** (Yao et al., Princeton/Google, 2022): the model interleaves reasoning traces with actions, observes the result, and decides the next step. Nearly every more complex agent pattern is a variation on this loop, not a departure from it.
- **Multi-agent coordination** — multiple specialized agents (a planner, a retriever, a critic) collaborate on one task. Higher capability ceiling, meaningfully higher failure surface — see the AI Eval Containment case study for what happens when the coordination layer is under-specified.
- **Human-in-the-loop checkpoints** — the agent pauses for approval before high-stakes actions. See the [Human-in-the-Loop Threshold playbook](../../playbooks/ai-product-alignment/human-in-the-loop.md) for exactly which actions warrant this.

## Decision Areas

- Is retrieval quality actually measured (precision/recall against a labeled set), or judged by whether the demo looked right?
- Does the agent's tool permission scope match what the task actually requires, or is it broader "just in case"? See LLM06 (Excessive Agency) in [Guardrails](../ai-security-risk/guardrails.md).
- At what point does multi-agent coordination stop paying for its own complexity? Every additional agent in the loop is a new failure mode and a cost multiplier, not a free capability increase.

## Source

Chip Huyen, *AI Engineering* — RAG and agents get a dedicated chapter; this page condenses it into the decision points that matter for architecture review. [ReAct](https://arxiv.org/abs/2210.03629) (Yao et al., 2022) for the foundational agent-loop pattern.

## Related

- [AI/ML Systems Engineering](index.md) — the Context and Orchestration layers this page expands on
- [Prompt Engineering](prompt-engineering.md) — the technique underneath every step in an agent loop
- [Efficient Model Routing](model-routing.md) — routing decisions inside a multi-step agent workflow
- [AI Security & Risk — Guardrails](../ai-security-risk/guardrails.md) — LLM06 Excessive Agency, the OWASP category this directly maps to
- [Playbook: AI Eval Containment](../../playbooks/ai-eval-containment.md) — a real, documented coordination-layer failure
