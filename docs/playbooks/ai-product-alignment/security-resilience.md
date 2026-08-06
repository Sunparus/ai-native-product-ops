---
name: ai-product-security-resilience-controls
description: Use when designing, reviewing, or auditing an AI product's security and resilience posture across its lifecycle.
tags:
  - security
  - resilience
  - sovereignty
  - governance
---

# Security & Resilience: Non-Negotiables

Five controls, cross-cutting, not stage-specific. They get designed in at **[Build (Stage 3)](stage-3-build-integration.md)**, verified at **[Governance Review (Stage 4)](stage-4-governance-review.md)**, and drilled at **[Operate (Stage 6)](stage-6-operate-monitor.md)**. Treat missing any one as a launch blocker, not a follow-up item.

| Control | What it actually means | Owner | Verified at |
|---|---|---|---|
| **Kill switch** | A single action that takes the AI feature offline or reverts it to a safe fallback (no live model calls) without needing a full deploy. Must work faster than the deploy pipeline, not depend on it. | AI Engineer | Exists at Stage 3, tested at Stage 4, drilled periodically at Stage 6 |
| **Backups** | Three things, not one: model version history (roll back to a prior pinned version), data backups upstream of any transformation (a bad pipeline run is recoverable), and prompt/config version history (a prompt change is reversible). | AI Engineer + DE | Existence confirmed at Stage 3; **restore actually tested**, not just backups taken, at Stage 6 |
| **Isolation** | Blast radius containment. A failure in the AI system (bad output, runaway cost, security incident) should not cascade into core systems or other tenants. Includes sandboxed execution for tool/agent calls and least-privilege access to underlying data. | Architect | Designed in at Stage 3, reviewed as a named risk control at Stage 4 |
| **Data residency & sovereignty** | Where data physically sits, and which jurisdiction's law governs it, confirmed for every hop: source, processing, model hosting, logs. Not the same as encryption or access control, and not the same as isolation above — this is about geography and jurisdiction specifically. | Architect + Legal | Requirement identified at Stage 1, locked at Stage 3, re-verified at Stage 4 |
| **Vendor exit strategy** | A documented answer to: what happens if this vendor deprecates the model version, doubles pricing, or becomes export-restricted. Includes a named fallback vendor or in-house option, even if untested. | Architect + Legal | Documented at Stage 2 vendor selection, reviewed annually or on material vendor change |

**Stage-gate questions:**

- "If we hit the kill switch right now, what actually happens, and how fast?"
    - *Rubber stamp:* "We'd just roll back the deploy."
    - *Real answer:* names the exact mechanism (feature flag, circuit breaker), confirms it's faster than a full deploy cycle, and confirms when it was last tested.
- "Where does this data actually sit, physically and legally, at every stage, and who confirmed that?"
    - *Rubber stamp:* "It's all in the cloud, so it should be fine."
    - *Real answer:* names the specific regions/jurisdictions for source data, processing, model hosting, and logs, and confirms Legal signed off on that map.
- "If this vendor doubled pricing or got export-restricted tomorrow, what's our move?"
    - *Rubber stamp:* "We'd figure it out."
    - *Real answer:* names a specific fallback vendor or in-house option, and the last time that fallback was actually assessed as viable.

## Related

- [AI Security — Guardrails](../../domains/ai-security/guardrails.md)
- [Sovereignty & Infrastructure](../../domains/sovereignty-infrastructure/index.md) — the residency vs. sovereignty distinction referenced above
- [Lean & Engineering — CI-by-Design](../../domains/lean-engineering/ci-by-design.md) — circuit breakers and blast radius, same concept applied at the pipeline level
- Glossary: [Circuit Breaker](../../reference/glossary.md), [Blast Radius](../../reference/glossary.md), [Vendor Lock-in](../../reference/glossary.md)
