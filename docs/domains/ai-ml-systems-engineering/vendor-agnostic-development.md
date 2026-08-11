---
tags:
  - architecture
  - vendor-strategy
---

# Vendor-Agnostic AI-Assisted Development

*Architecture pattern — avoiding lock-in*

Building product and engineering workflows so application code calls "a model" through an abstraction layer, not a specific vendor's proprietary API/format — prompts, evals, and tool definitions stay portable across providers.

- The abstraction cost is real: it forecloses some vendor-specific features (e.g. proprietary fine-tuning formats, agent frameworks) in exchange for switching flexibility.
- Protocols like MCP reduce (not eliminate) lock-in at the tool-integration layer specifically.
- Decide deliberately, per workflow, whether portability or best-in-class capability is the higher priority — treating it as a blanket policy is usually wrong.

## Decision Areas

- Is the abstraction layer actually tested against a second vendor's API before it's needed, or does "vendor-agnostic" exist only in the architecture diagram?
- Which specific vendor-native features is the team giving up by abstracting — has that trade-off been named explicitly, or assumed to be free?
- Does the abstraction cover evals and tool definitions too, or only the model-call interface? A portable prompt with a vendor-locked eval harness isn't actually portable.

## Product Ops Lens

- **Cross-team dependency:** If one product team locks into vendor-specific features, that constrains the whole organization's ability to negotiate or switch vendors later — one team's convenience becomes an enterprise-level lock-in risk.
- **Team topology implication:** Abstraction-layer discipline is naturally architecture/platform-team territory; expecting every product team to independently maintain portability is unrealistic and produces inconsistent results.
- **OKR / roadmap implication:** "Ship fast with vendor-specific features" and "stay portable" is a real, explicit tradeoff per feature — worth naming on the roadmap, not assumed away by default.
- **Budget implication:** Portability has a real upfront cost (forgoing vendor-specific speed or capability features) traded against future negotiating leverage — a genuine budget conversation, not just an engineering preference.
- **Who to loop in:** Architect owns the abstraction-layer decision; loop in whoever owns vendor contracts before a team builds something vendor-specific that would be costly to unwind later.

## Source

No single canonical source — evaluate via your own architecture review against each vendor's actual API/data contracts.

## Related

- [AI/ML Systems Engineering](index.md) — the Orchestration Layer where this abstraction typically lives
- [Multi-Vendor Strategy](multi-vendor-strategy.md) — this pattern is what makes a multi-vendor strategy operationally practical, not just a contractual possibility
- Glossary: [MCP (Model Context Protocol)](../../reference/glossary.md), [Vendor Lock-in](../../reference/glossary.md)
