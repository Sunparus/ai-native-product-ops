# Contributing to This Hub

The four templates below are the entire structural contract. Follow them and consistency doesn't depend on remembering why a decision was made months ago.

---

## 0. Quality Bar

Every page, at all times, should answer these questions positively. Status noted honestly — some are structurally guaranteed by the templates below, some are house rules that need active discipline, and a few are real gaps, not yet built.

| # | Question | Status | How it's met (or isn't yet) |
|---|---|---|---|
| 1 | Covers the most critical core domains and concepts for a modern AI-native enterprise with international exposure? | **Ongoing discipline** | Governed by the domain promotion rule (§1) — a topic gets a domain only with an independent, citable body of knowledge behind it |
| 2 | Structure and content reflect top global expertise level? | **Ongoing discipline** | Every domain traces to a named external standard (DAMA-DMBOK, NIST AI RMF, DORA/Team Topologies, Chip Huyen's AI Engineering) — never an internally-invented hierarchy |
| 3 | Narrative is excellent, lean, concise, high-signal, actionable to top-consultancy level? | **Enforced by template** | Top-5-issues tables, stage-gate "rubber stamp vs. real answer" pairs, Actionable Now sections — structure forces this, not just editing discipline |
| 4 | ToV is professional but human and non-synthetic, in an authentic individual voice? | **Partially met — open item** | House rule: no "it's not X, it's Y" antithesis construction, no corporate/AI-cliché phrasing (caught and fixed twice already in domain schemas). What's *not* yet solved: this voice was drafted by Claude across the session, not sampled from the author's own long-form writing. If a specific writing sample exists to calibrate against, provide it — otherwise this hub's voice is a deliberate house style (direct, no fluff, no press-release tone), not literally the author's personal register |
| 5 | Non-verbose, scannable, memorable, readable? | **Enforced by template** | Tables over paragraphs, bolded key terms, schema diagram before any prose |
| 6 | Validated and fact-checked? | **House rule** | No claim ships without a checkable source. Case studies require multiple independent sources before writing (see §3). Statistics from vendor-adjacent research get explicitly hedged, not stated as fact (see Metadata Management page for the pattern) |
| 7 | Well linked and traceable to source of truth? | **Enforced by template** | Every playbook and case study ends in a `## Source` / `## Sources` section; tags + Related sections cross-link concepts hub-wide |
| 8 | Clear when each page was created, how, and its next recommended review date? | **Half built** | "Last updated" now shows automatically on every page (`mkdocs-git-revision-date-localized-plugin`, live). The forward-looking `review_by:` date still needs manual frontmatter rollout per page — git can't infer that half |
| 9 | Are all terms and concepts explained? | **Ongoing discipline** | Every domain-specific term used should exist in the Reference Glossary — not yet audited end-to-end |
| 10 | Are all major best frameworks presented? | **Ongoing discipline**, tracked via the domain promotion rule | Coverage completeness per domain, checked against each domain's named standard |
| 11 | As objective and vendor-neutral as possible? | **House rule** | Vendors named factually; analyst "leader" status stated explicitly as a shortlist input, never an endorsement (see Metadata Management page for the pattern) |
| 12 | Gaps, contradictions, and open industry issues flagged? | **Structural — via IRL Lens** | Each domain's IRL Lens section links to relevant Open Questions in Landscape; case studies flag what failed, not just what happened |
| 13 | Easy to navigate down *and* up from any page? | **Met** | Down: domain skeleton (schema → In this domain list). Up: breadcrumb path navigation now live (`navigation.path`), plus `Related` sections |
| 14 | Easy to turn each page into a skill.md? | **True for Playbooks by design; not true for Domain pages, deliberately** | Domain pages explain *why* and stay prose — forcing skill.md shape onto a concept page was the mistake avoided early in this hub's build. Each domain instead points to its corresponding Playbook when one exists — that's the operationalizable version |
| 15 | Is there a feedback mechanism — a reaction or a short text comment — for any reader? | **Not yet built** | Requires enabling GitHub Discussions (available, not yet turned on) plus a per-page "Discuss this page" link. A reaction-click widget would need an analytics backend this static, free setup doesn't have — Discussions is the realistic mechanism here |

---

## 1. Adding a new domain

A domain gets its own folder only when it's substantial enough to need multiple pages. One-off content goes in an existing domain or Reference instead.

**Checklist:**
- [ ] Folder: `docs/domains/<slug>/`
- [ ] `index.md` starts with: title → 1-sentence definition → a Mermaid schema diagram (before any other content) → `## In this domain` (bullet list linking every page) → `## Related` (links to other domains/reference this one touches)
- [ ] Every page in the folder has `tags:` front matter — reuse an existing tag before inventing one (see current list below)
- [ ] Add the domain to `mkdocs.yml` nav, in the same position pattern as the others (Overview first, then pages in the order they appear on the index)
- [ ] Run `mkdocs build --strict` before committing — broken links fail the build, not silently

**Schema diagram rule, learned the hard way:** if two concepts are *distinct parallel dimensions* (e.g. residency vs. sovereignty), don't draw a sequential arrow between them — that claims one causes or precedes the other. Check the diagram's arrows against your own prose before shipping; this was the actual defect found in the last QA pass, twice, in two different domains.

---

## 2. Adding a playbook

Only write one once a practice is concrete enough to instruct, not just explain. A playbook without real steps is just a concept page with extra formatting.

**Two shapes, pick based on scope:**

- **Single file** — one focused practice, one skill.md-shaped page. Use this by default.
- **Series** (folder with an index + sub-pages) — a full lifecycle with multiple stakeholder-facing stages, where someone would realistically open one specific stage during a live meeting rather than scroll a long document. See `ai-product-alignment/` for the reference example: index page carries the shared front matter (purpose, roles glossary, concepts glossary, lifecycle diagram), each stage is its own page, and genuinely cross-cutting sections (Security & Resilience, Human-in-the-Loop) get their own page too so they can be tagged and cross-linked into the domains they connect to — don't bury cross-cutting content inside one stage's page just because it was first mentioned there.

**Required shape** (single file, or each page within a series):

```
---
name: short-identifier
description: one line — when to use this
tags:
  - relevant-tag
---
# Playbook: Title

## When to use

## Steps
1. ...

## Watch-outs
- ...

## Source
Link back to the concept page(s) it's extracted from.
```

This exact shape is intentional — it's skill.md-compatible, meaning it can be dropped into an AI agent's skills folder and used directly, not just read.

**Checklist:**
- [ ] Add to `docs/playbooks/index.md` under "Available now"
- [ ] Add to `mkdocs.yml` nav under Playbooks
- [ ] Link it from the domain page(s) it was extracted from, under `## Related`

---

## 3. Adding a case study

**Bar for inclusion: independently verifiable, sourced, publicly reported.** Not "this seems like it probably happened" — actually check multiple independent sources before writing it in. Speculative or single-source reports get left out on purpose.

**Required shape**, appended to `docs/reference/case-studies.md`:

```
## Title — what happened, in a few words (Company, Month Year)

**What happened:** 2-4 sentences, factual, paraphrased in your own words (not copied from source articles).

**Actionable now:**
- Concrete, implementable point — not a restated summary
- ...

**Sources:**
- [Publication: headline](url)
```

Both failure and success cases belong here. If a documented case is genuinely actionable, consider whether it should also become a playbook (see the AI Eval Containment playbook — extracted directly from a case study).

---

## 4. Tags currently in use

Reuse these before adding a new one — a proliferating tag list defeats the point of tagging:

`architecture` · `ci` · `cost` · `culture` · `data` · `evaluation` · `governance` · `inference` · `lean` · `resilience` · `security` · `sovereignty` · `vendor-strategy`

New tags are fine when a genuinely new cross-cutting concern shows up — just check this list first.

---

## Before every commit

```bash
python3 -m mkdocs build --strict
```

If this doesn't pass clean, don't commit. It catches broken internal links, malformed nav entries, and invalid Mermaid syntax before they reach the live site.
