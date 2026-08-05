# Enterprise Metadata Model

*Foundational — governs what AI can access*

A centrally maintained model of what data exists, where, who owns it, how sensitive it is, and how it relates to other data — the "map of the map." Without it, no residency, security, or cost-governance policy can be enforced consistently across AI systems.

- Core components: data catalog, business glossary, lineage tracking, sensitivity classification (PII/confidential tiers), stewardship/ownership records.
- The global reference framework is DAMA-DMBOK — vendor-neutral, decades-proven, now in its DMBOK 3.0 revision (active since 2025) which explicitly extends the framework to AI governance and ML data management.
- For AI specifically: sensitivity tags in the metadata model should directly drive routing decisions (e.g. "restricted" data never leaves an EU-hosted model).
- Adoption reality check: Gartner projects most data-governance initiatives fail by 2027 — not from a weak framework, but because governance stays documentation rather than becoming daily operating practice. See [DMBOK Operationalizing](../dmbok/operationalizing.md).

**Source:** DAMA International — DAMA-DMBOK (the standard reference, not a product). dama.org/learning-resources.
