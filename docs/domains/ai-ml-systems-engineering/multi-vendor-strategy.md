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
- The decision is not binary — segment by workload sensitivity and criticality rather than choosing one strategy company-wide.

**Source:** [a16z](https://a16z.com/) and [Epoch AI](https://epochai.org/) both publish periodic market-structure analyses relevant to vendor concentration risk.

## Related

- [AI/ML Systems Engineering](index.md) — the Orchestration Layer where multi-vendor routing lives
- [Vendor-Agnostic AI-Assisted Development](vendor-agnostic-development.md) — the abstraction layer that makes multi-vendor practical
- [Cost & FinOps](../../reference/cost-finops.md) — cost arbitrage is one of the three named reasons for this strategy
- [Playbook: AI Product Alignment — Security & Resilience Non-Negotiables](../../playbooks/ai-product-alignment/security-resilience.md) — vendor exit strategy as a review-gated control, not just a nice-to-have
