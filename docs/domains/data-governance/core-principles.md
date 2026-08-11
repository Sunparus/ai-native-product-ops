---
tags:
  - governance
  - data
  - security
---

# Data Governance — Core Principles

*Foundational — the discipline itself*

Data governance is the exercise of authority and control over data assets. Beneath any framework (DAMA-DMBOK, ISO, or homegrown), the same handful of principles recur — these are what to check for regardless of which framework label a vendor or team uses.

1. **Accountability** — a named owner for every data domain, not a shared or implied responsibility.
2. **Transparency** — data flows, model access, and decisions are documented and inspectable, not just policy-compliant on paper.
3. **Data quality as a defined standard** — accuracy, completeness, and timeliness measured against explicit thresholds, not judged subjectively.
4. **Least-privilege access** — access granted by need, tiered by sensitivity, revoked by default when no longer needed.
5. **Auditability** — every access and use is logged in a way that reconstructs "who did what, when, with what data" after the fact.
6. **Lifecycle management** — defined retention and deletion rules; data governed from creation to disposal, not just while in active use.
7. **Purpose limitation** — data used only for the purpose it was collected or authorized for; the most common quiet failure point once AI systems start reusing data across use cases.

**Source:** These principles are common across DAMA-DMBOK, ISO/IEC 38505 (governance of data), and ISO/IEC 42001 (AI management systems) — see [Legal & Regulatory](../../reference/legal-regulatory.md) for the standards themselves.

## Related

- [DAMA-DMBOK — The Wheel](dmbok-wheel.md) — Data Governance as the central hub these principles underlie
- [Enterprise Metadata Model](enterprise-metadata-model.md) — these principles applied to metadata specifically
- [Playbook: DAMA-DMBOK Operationalization](../../playbooks/dmbok-operationalization.md)
- [Dataset Engineering](../ai-ml-systems-engineering/dataset-engineering.md) — the technique layer these principles govern the standard for, not the technique itself
