---
tags:
  - cost
---

# Cost & FinOps for AI

A cross-cutting practice, not a domain — deliberately. It lacks the independent, citable body of knowledge (a DAMA-DMBOK, a DORA) that earns a topic a full peer domain in this hub. What it has instead is a lens applied *within* decisions made in other domains: an inference architecture choice has a cost dimension, a vendor security decision has a cost dimension, but neither makes cost governance a separable discipline with its own methodology.

## Grounded in

- **FinOps Foundation's AI cost-management work** — the closest thing this space has to an institutional body, extending general cloud FinOps practice to AI-specific unit economics
- General cloud FinOps practice (chargeback models, unit economics, cost allocation) applied to AI's specific cost drivers: tokens, inference compute, fine-tuning runs

## Where cost decisions actually get made

- **[AI/ML Systems Engineering](../domains/ai-ml-systems-engineering/index.md)** — model choice, inference optimization, and orchestration complexity are the primary cost levers; cost is a consequence of architecture decisions, not a separate one
- **[Multi-Vendor Strategy](../domains/ai-ml-systems-engineering/multi-vendor-strategy.md)** — cost arbitrage and negotiating leverage are one of the three named reasons for a deliberate multi-vendor approach
- **[AI Security & Risk](../domains/ai-security-risk/index.md)** — vendor exit strategy (a Security & Resilience non-negotiable in the [AI Product Alignment playbook](../playbooks/ai-product-alignment/security-resilience.md)) is fundamentally a cost-exposure question dressed as a security control

## Decision Areas

- Cost per resolved task, not cost per token — the unit that actually maps to business value
- Is there quota governance by team, or does spend only surface at the invoice, after the fact ([Stage 6 of the AI Product Alignment playbook](../playbooks/ai-product-alignment/stage-6-operate-monitor.md) names this exact failure mode)
- Hidden cost of orchestration complexity — every additional agent step or tool call is a cost multiplier, not just a latency one

## Related

- [AI/ML Systems Engineering](../domains/ai-ml-systems-engineering/index.md)
- [Playbook: AI Product Alignment — Stage 6](../playbooks/ai-product-alignment/stage-6-operate-monitor.md) — cost dashboard as an operational, not just financial, requirement
