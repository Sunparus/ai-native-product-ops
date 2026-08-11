---
tags:
  - architecture
  - data
  - evaluation
---

# Dataset Engineering

*How training and eval datasets actually get built — distinct from who's accountable for them*

This page covers technique: acquisition, augmentation, deduplication, curation. It deliberately does not cover accountability, quality standards, or lineage policy — that's [Data Governance's Core Principles](../data-governance/core-principles.md). Same underlying subject, different question: Governance owns what "good" means and who signs off; this page covers how you actually get there. See the boundary rule in `CONTRIBUTING.md` for why these stay separate instead of merged.

## Core activities

- **Acquisition** — sourcing raw data, whether scraped, licensed, purchased, or internally generated. The point where data residency and licensing questions first enter the pipeline — see [Sovereign Infrastructure](../ai-security-risk/sovereign-infrastructure.md).
- **Augmentation** — synthetically expanding a dataset (paraphrasing, back-translation, synthetic generation via another model) to increase volume or coverage without new acquisition. **Real risk, not theoretical:** ["The Curse of Recursion" (Shumailov et al., 2023, later published in *Nature*)](https://arxiv.org/abs/2305.17493) documented "model collapse" — training recursively on model-generated content causes irreversible loss of distributional diversity. Synthetic augmentation is a legitimate technique, not a free multiplier; it needs a real ratio of genuine to synthetic data, checked, not assumed safe.
- **Deduplication** — removing near-duplicate examples, which otherwise silently overweight the model's exposure to redundant patterns and can inflate eval scores if duplicates leak across train/eval splits.
- **Curation** — the judgment layer: deciding what stays, what gets filtered, and what the resulting distribution actually represents versus what it was intended to represent.

## Decision Areas

- Is the eval set drawn from the same distribution as production traffic, or from whatever was easiest to label? A mismatch here produces eval scores that don't predict real-world performance.
- Has deduplication been checked specifically across the train/eval boundary, not just within each set individually? Leakage here silently inflates every eval result downstream.
- Who owns the quality bar this dataset needs to meet — is that a documented standard from [Data Governance](../data-governance/core-principles.md), or an implicit assumption held by whoever built the pipeline?

## Product Ops Lens

- **Cross-team dependency:** A shared training or eval dataset used across product teams means one team's curation choices affect every model built on that data — ownership and a change process need to be explicit, not assumed.
- **Team topology implication:** This is the clearest case in the domain for the control-plane/execution-plane boundary rule — dataset engineering technique lives here, but the quality standard it's held to is [Data Governance's](../data-governance/core-principles.md) call, and both need a seat when this work gets planned.
- **OKR / roadmap implication:** "We need more training data" is often a roadmap blocker discovered too late — data acquisition and curation lead time belongs in planning explicitly, especially for eval sets, which get treated as an afterthought more often than they should.
- **Budget implication:** Data acquisition and licensing carries a real, often underestimated cost. Synthetic augmentation looks free but carries the model-collapse risk described above — a quality cost, not a budget line, but just as real to plan for.
- **Who to loop in:** Data Engineer for pipeline feasibility, Data Governance counterpart for the quality standard, PM for whether the eval set actually represents real usage.

## Source

Chip Huyen, *AI Engineering* — dataset engineering gets a dedicated chapter, positioned as foundational infrastructure most teams underinvest in relative to model selection. [Shumailov et al.](https://arxiv.org/abs/2305.17493) for model collapse specifically.

## Related

- [Data Governance — Core Principles](../data-governance/core-principles.md) — accountability and quality standards for the datasets this page describes building
- [Evaluation & Observability](../evaluation-observability/index.md) — eval set construction is dataset engineering applied specifically to measurement
- [Fine-Tuning & Model Adaptation](fine-tuning.md) — the reason most dataset engineering effort exists: fine-tuning is only as good as the data behind it
- [AI/ML Systems Engineering](index.md) — the Data Layer this page expands on
