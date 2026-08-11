---
tags:
  - architecture
  - vendor-strategy
  - resilience
---

# Multi-Vendor Strategy

*Risk & leverage — deliberate redundancy*

Using two or more model providers by design — for resilience, cost arbitrage, capability specialization (e.g. one vendor for coding tasks, another for EU-resident sensitive workloads), and negotiating leverage.

- Benefit: no single point of failure, and credible exit options in vendor negotiations.
- Cost: added orchestration complexity, duplicated evaluation/monitoring work, inconsistent behavior across providers.
- Segment the decision by workload sensitivity and criticality, rather than choosing one strategy company-wide.

## Decision Areas

- Is multi-vendor genuinely segmented by workload (sensitivity, criticality, cost profile), or is it two vendors used interchangeably with no real decision logic behind which gets which request?
- Has the orchestration and evaluation overhead of running multiple vendors actually been costed, or assumed to be worth it without measurement?
- If the primary vendor is unavailable right now, is failover to the second vendor tested and working, or a plan that's never been exercised?

## Product Ops Lens

- **Cross-team dependency:** If different product teams are quietly using different vendors for similar tasks, that produces inconsistent user-facing behavior and duplicated evaluation effort — worth surfacing centrally rather than each team discovering it independently.
- **Team topology implication:** Multi-vendor strategy needs a platform or enabling team to own vendor selection criteria and evaluation, or every product team re-litigates "which vendor" from scratch, inconsistently.
- **OKR / roadmap implication:** Vendor diversification for resilience is itself a roadmap item with real engineering cost — it competes with feature work for the same capacity and should be resourced explicitly, not treated as free.
- **Budget implication:** This is a direct procurement and negotiation lever — real, quantifiable budget impact, worth involving whoever owns vendor contracts, not just engineering.
- **Who to loop in:** Architect for technical feasibility, Legal/procurement for contract terms, Cost & FinOps counterpart for the arbitrage case.

## Source

[a16z's "How 100 Enterprise CIOs Are Building and Buying Gen AI in 2025"](https://a16z.com/ai-enterprise-2025/) — surveyed 100 CIOs across 15 industries, found 81% of respondents now orchestrating three or more model families in production, up from 68% a year prior. A specific, current, verifiable finding, not a generic pointer to "periodic market analyses."

## Related

- [AI/ML Systems Engineering](index.md) — the Orchestration Layer where multi-vendor routing lives
- [Vendor-Agnostic AI-Assisted Development](vendor-agnostic-development.md) — the abstraction layer that makes multi-vendor practical
- [Cost & FinOps](../../reference/cost-finops.md) — cost arbitrage is one of the three named reasons for this strategy
- [Playbook: AI Product Alignment — Security & Resilience Non-Negotiables](../../playbooks/ai-product-alignment/security-resilience.md) — vendor exit strategy as a review-gated control, not just a nice-to-have
