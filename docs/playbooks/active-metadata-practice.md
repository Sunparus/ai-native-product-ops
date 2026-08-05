---
name: active-metadata-practice
description: Use when moving from a static, manually-maintained data catalog to an active, continuously-updated metadata practice.
tags:
  - governance
  - data
---

# Playbook: Standing Up Active Metadata

## When to use

The organization has a data catalog, but it's stale within weeks of being populated — or there's no catalog and the choice of where to start is unclear.

## Steps

1. **Centralize before automating.** Integrate metadata from warehouses, BI tools, and transformation layers into one unified catalog before adding automation on top. Automating a fragmented setup just automates the fragmentation.
2. **Adopt an interoperable schema.** Check W3C DCAT v3 compatibility before committing to a platform — this determines whether metadata can move between systems later without a rebuild.
3. **Wire it bidirectionally.** Metadata capture should push back into producing and consuming tools — schema-change alerts, glossary flags, quality warnings — not just collect information for later manual review.
4. **Find stewards by behavior, not title.** Surface who is already documenting datasets, answering questions, and maintaining definitions informally, and formalize the stewardship role around them. This is Robert Seiner's Non-Invasive Data Governance approach, and it gets more durable buy-in than top-down assignment.
5. **Prioritize the data AI systems already touch.** If AI initiatives are in flight or planned, bring lineage and technical-metadata completeness on those specific data sources to a high standard first — this is the leading, well-documented cause of AI project failure that's actually addressable.

## Watch-outs

- A stale catalog is often worse than no catalog — it creates false confidence. If freshness can't be maintained, scope the catalog down rather than letting it silently rot.
- Vendor "leader" status in an analyst report is a shortlist input, not a decision. Validate against your own integration and schema-interoperability needs.

## Source

[Data Governance — Metadata Management: Modern Practice](../domains/data-governance/metadata-management.md)
