# Contributing to This Hub

The four templates below are the entire structural contract. Follow them and consistency doesn't depend on remembering why a decision was made months ago.

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
