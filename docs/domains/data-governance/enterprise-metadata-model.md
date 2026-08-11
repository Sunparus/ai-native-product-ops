---
tags:
  - governance
  - data
  - security
---

# Enterprise Metadata Model

*Foundational — governs what AI can access*

A centrally maintained model of what data exists, where, who owns it, how sensitive it is, and how it relates to other data — the "map of the map." Without it, no residency, security, or cost-governance policy can be enforced consistently across AI systems.

- Core components: data catalog, business glossary, lineage tracking, sensitivity classification (PII/confidential tiers), stewardship/ownership records.
- The global reference framework is DAMA-DMBOK — vendor-neutral, decades-proven, now in its DMBOK 3.0 revision (active since 2025) which explicitly extends the framework to AI governance and ML data management.
- For AI specifically: sensitivity tags in the metadata model should directly drive routing decisions (e.g. "restricted" data never leaves an EU-hosted model).
- Adoption reality check: [Gartner projects 80% of data-governance initiatives fail by 2027](https://www.gartner.com/en/newsroom/press-releases/2024-02-28-gartner-predicts-80-percent-of-data-and-analytics-governance-initiatives-will-fail-by-2027-due-to-a-lack-of-a-real-or-manufactured-crisis-) — not from a weak framework, but because governance stays documentation rather than becoming daily operating practice. See [DMBOK Operationalizing](dmbok-operationalizing.md).

**See also:** [Metadata Management — Modern Practice](metadata-management.md) for current standards, category-leading tooling, and how leading engineering organizations built this practice.

**Source:** [DAMA International — DAMA-DMBOK](https://www.dama.org/cpages/body-of-knowledge) (the standard reference, not a product).

## Related

- [DAMA-DMBOK — The Wheel](dmbok-wheel.md) — this model's parent knowledge area within the 11
- [Core Principles](core-principles.md)
- [Metadata Management — Modern Practice](metadata-management.md) — the operational, tooling-and-standards layer on top of this conceptual model
