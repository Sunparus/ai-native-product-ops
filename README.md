# AI-Native Product Operations — Expertise Hub

A git-versioned, markdown-based knowledge base. Built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

Content is licensed [CC BY-NC 4.0](LICENSE.md) — read, share, and quote freely with attribution; no commercial use without permission.

## Why this replaced the single-file interactive artifact

- **Resilience** — content lives in plain markdown files, one per topic. A mistake in one file can't break the rest of the site.
- **Versioning** — every change is a git commit. Full history, diffs, and rollback (`git log`, `git diff`, `git revert`). Two milestones are also tagged directly: `v1-poc-personal-interest-map` (before the domain taxonomy was rebuilt on named standards) and `v2-objective-taxonomy` (after).
- **Scalability** — add a new file, add a nav entry, done. No monolithic component to hand-edit. See [CONTRIBUTING.md](CONTRIBUTING.md) for the exact templates and the domain-promotion rule that keeps this from drifting.

## Local preview

```bash
pip install mkdocs mkdocs-material mkdocs-git-revision-date-localized-plugin
mkdocs serve
```

Open `http://127.0.0.1:8000`.

## Deploy

**Automatic, already set up:** every push to `main` triggers a GitHub Actions workflow (`.github/workflows/deploy.yml`) that builds and deploys to GitHub Pages — no manual step needed.

**Manual fallback**, if the workflow needs to be re-run by hand:
```bash
mkdocs gh-deploy --force
```

## Editing content

Every page is a `.md` file under `docs/`. Edit any file, run `mkdocs build --strict` to catch broken links before committing, then:

```bash
git add -A
git commit -m "describe what changed"
git push
```

That commit is your version history. `git log --oneline` shows every change ever made to the hub.

## Structure

```
docs/
  index.md                              Home
  domains/
    ai-ml-systems-engineering/          The stack, model routing, vendor strategy
    evaluation-observability/           Eval design, pipelines, monitoring, feedback loops
    data-governance/                    DAMA-DMBOK, metadata management, core principles
    ai-security-risk/                   NIST AI RMF, OWASP, MITRE ATLAS, sovereignty, ethics & bias
    delivery-operating-practice/        DORA, Team Topologies, CI-by-design
    ai-adoption-maturity/               MIT CISR / Gartner / MITRE maturity models, lean org design
  playbooks/                            Skill.md-shaped, procedural extracts from the domains
    ai-product-alignment/               9-page full-lifecycle playbook series (Discovery -> Operate)
  reference/
    glossary.md                         Terms, categorized
    legal-regulatory.md                 EU / US / Global / Industry standards, every entry linked
    cost-finops.md                      Cross-cutting practice, deliberately not a domain
    case-studies.md                     Verified, sourced cases with an actionable takeaway
    experts.md                          People & organizations worth following
    landscape/                          Open questions, trends, expertise leads -- one page per domain
    tags.md                             Auto-generated cross-domain tag index
mkdocs.yml                              Site config & navigation
CONTRIBUTING.md                         Content templates, Quality Bar, ToV Guide, domain promotion rule
LICENSE.md                              CC BY-NC 4.0
```

This tree is generated from the actual repo, not hand-maintained prose — if it ever looks stale again, regenerate it with `find docs -name "*.md" | sort` rather than trust memory.
