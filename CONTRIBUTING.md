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
| 4 | ToV is professional but human and non-synthetic, in an authentic individual voice? | **Rule defined against 2 samples; existing content not yet recalibrated** | See **ToV Guide** below. Applies to all *new* content going forward. Retroactively recalibrating existing pages is a separate, unscoped pass, not done automatically by defining the rule |
| 5 | Non-verbose, scannable, memorable, readable? | **Enforced by template** | Tables over paragraphs, bolded key terms, schema diagram before any prose |
| 6 | Validated and fact-checked? | **House rule** | No claim ships without a checkable source. Case studies require multiple independent sources before writing (see §3). Statistics from vendor-adjacent research get explicitly hedged, not stated as fact (see Metadata Management page for the pattern) |
| 7 | Well linked and traceable to source of truth? | **Enforced by template** | Every playbook and case study ends in a `## Source` / `## Sources` section; tags + Related sections cross-link concepts hub-wide |
| 8 | Clear when each page was created, how, and its next recommended review date? | **Half built** | "Last updated" now shows automatically on every page (`mkdocs-git-revision-date-localized-plugin`, live). The forward-looking `review_by:` date still needs manual frontmatter rollout per page — git can't infer that half |
| 9 | Are all terms and concepts explained? | **Ongoing discipline** | Every domain-specific term used should exist in the Reference Glossary — not yet audited end-to-end |
| 10 | Are all major best frameworks presented? | **Ongoing discipline**, tracked via the domain promotion rule | Coverage completeness per domain, checked against each domain's named standard |
| 11 | As objective and vendor-neutral as possible? | **House rule** | Vendors named factually; analyst "leader" status stated explicitly as a shortlist input, never an endorsement (see Metadata Management page for the pattern) |
| 12 | Gaps, contradictions, and open industry issues flagged? | **Structural — via each domain's Landscape section** | Every domain ends with its own Landscape (Open Questions / Trends / Expertise Leads), not a separate reference page; case studies flag what failed, not just what happened |
| 13 | Easy to navigate down *and* up from any page? | **Met** | Down: domain skeleton (schema → In this domain list). Up: breadcrumb path navigation now live (`navigation.path`), plus `Related` sections |
| 14 | Easy to turn each page into a skill.md? | **True for Playbooks by design; not true for Domain pages, deliberately** | Domain pages explain *why* and stay prose — forcing skill.md shape onto a concept page was the mistake avoided early in this hub's build. Each domain instead points to its corresponding Playbook when one exists — that's the operationalizable version |
| 15 | Is there a feedback mechanism — a reaction or a short text comment — for any reader? | **Not yet built** | Requires enabling GitHub Discussions (available, not yet turned on) plus a per-page "Discuss this page" link. A reaction-click widget would need an analytics backend this static, free setup doesn't have — Discussions is the realistic mechanism here |

---

## ToV Guide

Calibrated against two real samples in different registers — a flowing conversational reply, and a punchy structured LinkedIn post. What holds across both matters more than either register alone.

**Banned word: "honest" / "honestly."** Not part of the professional lexicon for this hub. Self-describing a statement as honest is exactly the kind of unearned credibility claim the ToV Guide otherwise exists to strip out — either the statement is accurate and stands on its own, or it isn't. State the gap, the limitation, or the correction plainly, without the adjective vouching for itself. ("Acknowledged gap," "stated limitation," or just the fact itself, with no framing word at all.)

**Banned — the synthetic aphorism pattern:**
> "X isn't really about A — it's about B."
> "This isn't a framework, it's a mindset."

Flat, declarative, closes the thought instead of opening it. Reads as manufactured cleverness. (Caught and fixed twice already in domain schemas — e.g. "Not one spoke among ten — it's what makes the others enforceable" got rewritten for exactly this reason.)

**What's explicitly *not* banned — these are authentic, keep using them:**

- Rhetorical questions as an opener: "Is the bullet always faster than the shield?"
- "While many do X, they continue to: [gap list]" — a real pattern in the source material, and structurally close to how this hub already writes Watch-outs sections
- "If A, it should also do B" — a forward parallel, not a corrective negation
- Punchy, emoji-marked bullet lists when the content is genuinely a fast scan (threat examples, structured lists) — this voice is *not* uniformly hedged-and-flowing; it shifts register by context, and both registers are authentic

**The one real distinction that matters:** the banned pattern specifically *negates one thing to assert another as truer*. Everything above does something else — poses a question, flags a gap, proposes a parallel, or just presents a fast list. None of it claims false certainty by knocking down a straw version of the alternative first.

**Concrete markers to write toward:**

- **Ground claims in named, specific sources — never vague.** Not "attacks are getting more sophisticated" but "a single email triggered zero-click exfiltration in Microsoft Copilot (CVE-2025-32711)." This instinct — cite the specific paper, the specific CVE, the specific number — is exactly why this hub grounds every domain in a named standard instead of an invented hierarchy. It's not a hub-specific rule, it's how this voice already thinks.
- **Lead with humility even when the content is expert-level.** "I am not a security expert, it just struck me how broad the attack surface is" — precedes a genuinely rigorous 6-layer framework breakdown. Confidence in the material, not in the author's authority over it.
- **Hedge causal claims that aren't proven.** "It seems that," "I assume that," "would be interesting to know whether this is measurable" — even in punchy mode, the hedge survives.
- **Close with attribution and shared responsibility, not a solo mic-drop.** The P.S. crediting "the recent exchange with IT security & data experts" and reframing the takeaway as a shared, ongoing responsibility is a real closing pattern, not filler.
- **Actionable, specific, implementable — never abstract advice.** "Set up a weekly job via GitHub Actions that pulls latest CVEs and maps them against your stack" beats "stay on top of security research." This is the same instinct behind every Playbook's `## Steps` section.
- Light, occasional warmth (an emoji, a parenthetical aside) at genuine close points — not scattered throughout, not decorative.

---

## 1. Adding a new domain

**The control-plane / execution-plane boundary rule** — needed twice already (Data Layer's lineage-tracking overlap with Data Governance, and the Dataset Engineering vs. Data Quality question), so it's written down now instead of re-litigated a third time: **Data Governance owns who's accountable and what "good" means** — authority, standards, quality thresholds, lineage requirements as policy. **AI/ML Systems Engineering owns how data actually gets there** — the technique: pipelines, acquisition, augmentation, deduplication, curation. Same underlying subject, different plane. When a new topic seems to belong to both, ask which question it answers — "who decides and what's the standard" is Governance; "how do you actually do it" is Systems Engineering. Cross-link, don't duplicate.

A domain gets its own folder only when it's substantial enough to need multiple pages. One-off content goes in an existing domain or Reference instead.

**Checklist:**
- [ ] Folder: `docs/domains/<slug>/`
- [ ] `index.md` order, fixed: title → 1-sentence definition → Mermaid schema diagram → `## In this domain` → body content → `## IRL Lens` (Focus areas & deep dives, Case studies) → `## Related` → `## Landscape` (Open Questions / Trends / Expertise Leads) as the literal last section — not a separate reference page
- [ ] Every page in the folder has `tags:` front matter — reuse an existing tag before inventing one (see current list below)
- [ ] Add the domain to `mkdocs.yml` nav, in the same position pattern as the others (Overview first, then pages in the order they appear on the index)
- [ ] Every claim in Landscape (especially Trends and Open Questions) gets a real, verified, non-paywalled link where one exists. If the primary source is paywalled, link the organization's own site rather than a vendor's promotional summary of it — never leave a specific claim unlinked just because the ideal source is gated
- [ ] Run `mkdocs build --strict` before committing — broken links fail the build, not silently

**Schema diagram rule, learned the hard way:** if two concepts are *distinct parallel dimensions* (e.g. residency vs. sovereignty), don't draw a sequential arrow between them — that claims one causes or precedes the other. Check the diagram's arrows against your own prose before shipping; this was the actual defect found in the last QA pass, twice, in two different domains.

**Content/diagram drift rule, also learned the hard way:** any time a page is added to a domain's "In this domain" list, check whether the schema diagram needs a matching update. A domain's diagram and its actual page list drifted apart within a single commit once already — the fix is a habit, not a one-time correction.

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

**Source tiers, by epistemic weight — not a single admit/reject bar.** Excluding anything with an incentive attached throws out most of the freshest, most current signal in a fast-moving field. The fix is tiering plus mandatory interpretation, not exclusion:

| Tier | What | Strong for | Weak for | Named incentive risk |
|---|---|---|---|---|
| **A — Peer-reviewed research** | arXiv, ACL/NeurIPS/ICLR/MLSys | General mechanisms, causal claims | Whether it holds at real production scale | Publication pressure, benchmark gaming |
| **B — Analyst/consultancy aggregate research** | Gartner, McKinsey, IDC, Menlo Ventures, a16z's research arm | Base rates across many companies | Causal mechanism, "why" | Paid inclusion, portfolio bias — name which |
| **C — Named-company engineering data about their own systems** | A named engineer's post about their own architecture/cost/performance | Current, concrete, often the freshest real numbers available | Cherry-picked framing, no peer review | Lower than D — no customer to flatter, but still a PR incentive |
| **D — Vendor marketing case studies about customers** | "Company X saw Y% using our product" | Almost nothing in isolation | Everything — cherry-picked customer, undisclosed methodology | Highest — direct sales incentive |

Any tier can be used. Tier D alone needs to be labeled as a single, weighted data point, not presented as fact. Tier A+B or A+C corroborating the same pattern earns real confidence, worth noting.

**Search approach — signal over noise:** search the primary claim directly (company + specific research, not generic "case study" terms — those surface SEO farms first), then search specifically for independent analysis / discrepancy-checking coverage of that same claim, not just more restatements of it. For consultancy sources, go to the firm's own domain rather than a blog quoting them secondhand.

**Required shape**, appended to `docs/reference/case-studies.md` — signal first, provenance last:

```
## Title — what happened, in a few words (Company, Month Year)

**What happened:** 2-4 sentences, factual, paraphrased in your own words.

**What moved:** The concrete, measurable result — the actual number, not an adjective.

**Portable lesson:** The generalizable principle, decoupled from the specific vendor's product.

**Where it may break:** The conditions under which this wouldn't generalize — don't skip this even when the result is impressive.

**Source & confidence:** Tier, named author/org, the incentive stated plainly, and whether it's independently corroborated or a single claim standing alone. Lowest-emphasis section, last on purpose — context for the learning above, not the point of the entry.
```

Both failure and success cases belong here. If a documented case is genuinely actionable, consider whether it should also become a playbook (see the AI Eval Containment playbook — extracted directly from a case study).

---

## The "prove it" rule for any "best practice" claim

Any content that calls something a best practice, industry standard, or significant approach needs one of two things attached, not just the assertion:

- **A named framework or standard** — if it's genuinely a field-wide convention, link the actual standard (an RFC, an ISO number, a named academic framework). This is what most of this hub's domain grounding already does.
- **A case study or validating research** — if it's validated by industry leaders rather than codified as a formal standard, link a real case study (see `reference/case-studies.md`'s bar: independently verifiable, sourced, not a vendor's self-report) or named industry/consultancy research (a peer-reviewed paper, an analyst report, a named company's published post-mortem).

An unsupported "this is best practice" is exactly the kind of claim the ToV Guide's grounding-in-named-sources instinct exists to catch. If neither a framework link nor a validating case study is available, say so plainly — "no independent validation found yet" — rather than assert it anyway.

## Product Ops Lens — required on every domain content page

Every technical concept page needs a `## Product Ops Lens` section, same standing as `Decision Areas` — not optional, not only for pages that feel like they need it. The audience for this hub includes product leads and product ops who need to align with architects/engineers on decisions, not just hold a conversation about them. Five fixed sub-points, each answered specifically for that page's actual content, never generic filler:

- **Cross-team dependency** — what this choice constrains or enables for other product teams' input/output requirements
- **Team topology implication** — does this need a platform/enabling team, or does it stay embedded in product teams
- **OKR / roadmap implication** — what to plan for explicitly, not discover reactively
- **Budget implication** — the cost lever, if there is one
- **Who to loop in** — a named role, not a vague "the team"

If a page genuinely has nothing here (rare), say so per sub-point rather than skip the section — "No direct cross-team dependency" is a real answer; a missing section reads as an oversight.

## Source-currency stage-gate

Any cited source last published or updated **before June 2025** gets an explicit currency check before it ships, not a silent pass: is this finding/technique still accurate, or has the field moved past it since?

Two legitimate outcomes, both fine — the check itself is what's required, not a specific answer:

- **Cite it as foundational/historical, on purpose.** Some sources are cited *because* they're the origin point (Sculley et al. 2015, ReAct, "Lost in the Middle") — their age is the point, not a defect. Say so explicitly rather than presenting a 2022 paper as if it described this week's state of the art.
- **Add a currency caveat if the field has genuinely moved.** If newer work supersedes or qualifies the finding, say what and how — see the "Lost in the Middle" caveat on the Prompt Engineering page (some newer models show reduced sensitivity to the original effect) as the pattern to follow.

What's not acceptable: citing a pre-June-2025 source as current practice without checking either way.

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
