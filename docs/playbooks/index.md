# Playbooks

Concept pages in this hub explain *why* something matters. Playbooks are different: stripped down, procedural, execution-ready — the *how*, in a shape a person or an AI agent can act on directly.

Each playbook follows a fixed, skill.md-compatible template:

```
---
name: short identifier
description: when to use this, one line
---
# Playbook: Title
## When to use
## Steps
## Watch-outs
## Source
```

That shape isn't arbitrary — a file in this format can be dropped directly into an AI agent's skills folder and used as-is, not just read.

Not every concept page has a playbook yet, and that's intentional. A playbook only gets written once a practice is concrete enough to instruct, not just explain. Thin domains (like AI Security today) will grow playbooks as their concept pages mature.

**Most playbooks are single files.** A few are big enough to need a series instead — a full lifecycle with multiple stakeholder-facing stages, where someone opens one specific stage during a live meeting rather than scrolling a long document. AI Product Alignment & Review is the first example: one overview page plus 8 sub-pages, each still following the skill.md shape.

## Available now

- **[DAMA-DMBOK Operationalization](dmbok-operationalization.md)** — the 5-step path from framework to daily practice
- **[Standing Up Active Metadata](active-metadata-practice.md)** — moving from a static catalog to continuously-updated metadata
- **[CI-by-Design for AI](ci-by-design.md)** — building verification into the pipeline, not bolting it on after
- **[AI Capability Evaluation — Containment](ai-eval-containment.md)** — extracted directly from the [sandbox containment case study](../reference/case-studies.md)
- **[AI Product Alignment & Review](ai-product-alignment/index.md)** — full-lifecycle cross-functional playbook series, Discovery through Operate
