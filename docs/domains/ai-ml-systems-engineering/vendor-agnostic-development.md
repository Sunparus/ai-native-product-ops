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

## Source

No single canonical source — evaluate via your own architecture review against each vendor's actual API/data contracts.

## Related

- [AI/ML Systems Engineering](index.md) — the Orchestration Layer where this abstraction typically lives
- [Multi-Vendor Strategy](multi-vendor-strategy.md) — this pattern is what makes a multi-vendor strategy operationally practical, not just a contractual possibility
- Glossary: [MCP (Model Context Protocol)](../../reference/glossary.md), [Vendor Lock-in](../../reference/glossary.md)
