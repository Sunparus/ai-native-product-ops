---
tags:
  - security
  - governance
---

# Ethics & Bias

Fairness isn't a separate concern bolted onto security — NIST's AI RMF names it as one of seven core trustworthy-AI characteristics, addressed through the same Govern/Map/Measure/Manage functions as any other AI risk. It gets its own page here because the practice is substantial enough to need one, not because it's a different discipline.

## Grounded in

- **NIST AI RMF** — fairness with harmful bias managed is one of seven named trustworthy-AI characteristics, not an optional add-on
- **ISO/IEC TR 24027** — the technical standard specifically on bias in AI systems and AI-aided decision-making
- **ACM FAccT** (Fairness, Accountability, and Transparency) — the primary academic venue for this research; useful as a pointer to current work, not a framework to implement directly

## Where bias actually enters an AI system

- **Training/reference data** — a model trained on historically skewed data reproduces that skew; this is a data governance problem as much as a modeling one (see [Core Principles](../data-governance/core-principles.md) on purpose limitation and data quality)
- **Evaluation design** — an eval set that only covers the happy-path population won't surface disparate outcomes for underrepresented groups; this is why the [AI Product Alignment playbook's Stage 4](../../playbooks/ai-product-alignment/stage-4-governance-review.md) treats bias testing as mandatory above a defined risk tier, not optional-by-assumption
- **Deployment context** — a model that's fair in the training distribution can still produce disparate impact once deployed against a different real-world population

## Interrogate

- Is bias testing mandatory above a defined risk tier, or skipped by default because "there's no obviously sensitive attribute"?
- Does the eval set explicitly include edge cases and known-underrepresented segments, or only the happy path?
- Is there a named owner for fairness sign-off, distinct from general governance sign-off?

## Related

- [Guardrails](guardrails.md) — system-level controls, including fairness-related output filtering
- [AI Adoption & Organizational Maturity](../ai-adoption-maturity/index.md) — MITRE's AI Maturity Model names Ethical, Equitable, and Responsible Use as one of its six pillars
