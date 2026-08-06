---
name: ai-product-stage-1-discovery
description: Use when framing a new AI product idea, before any build commitment — confirms the problem, data, and owner are real.
tags:
  - governance
  - data
---

# Stage 1 — Discovery & Framing

**Roles required:** PM (leads), Architect (feasibility consult), DS (data feasibility consult), Legal (consult on vendor and data terms)

**Decisions to lock before moving on:** problem definition, success metric (business *and* technical), confirmation that the data actually exists and is accessible, data residency/jurisdiction requirements identified, and whether AI is the right tool at all.

**Top 5 preventable issues**

| # | Issue | Owner | Prevention |
|---|---|---|---|
| 1 | Success metric is defined only in business terms, with no measurable model-level proxy | PM + DS | Define the business metric and the technical proxy metric together, before scoping starts |
| 2 | Data is assumed to exist ("it's in the CRM somewhere") without access, freshness, or volume confirmed | DE | DE runs a data availability spike before commitment, not after |
| 3 | AI is proposed for a problem a deterministic rule or lookup would solve better and cheaper | Architect | Force a "why not a simpler system" check at framing |
| 4 | No named owner for the eventual go/no-go decision | PM | Name the decision-maker for governance sign-off now, not at Stage 4 |
| 5 | Scope includes sensitive data (PII, financial, health) with governance not flagged early | Governance | Data sensitivity classification happens at framing, not at review |

**Also non-negotiable:** vendor contract terms (data processing agreement, IP ownership of outputs, liability for bad outputs) not reviewed before build starts. *Owner: Legal. Prevention: Legal reviews vendor agreement terms during framing, in parallel with technical feasibility, not after build has started.*

**Stage-gate question:** "What data, specifically, does this need, and has anyone confirmed we can access it at the volume and freshness required?"

- *Rubber stamp:* "Yeah, it's in our systems."
- *Real answer:* names the specific source/tables, confirms access is granted, confirms update frequency matches the use case.

---

**Next:** [Stage 2 — Data & Model Design →](stage-2-data-model-design.md)
