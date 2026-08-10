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

Full listing, generated directly from the repo — not hand-summarized:

```
docs/
  index.md                                              Home

  domains/
    ai-ml-systems-engineering/
      index.md                                          The stack, cross-cutting concerns
      model-routing.md
      vendor-agnostic-development.md
      multi-vendor-strategy.md
    evaluation-observability/
      index.md
    data-governance/
      index.md
      core-principles.md
      dmbok-wheel.md
      dmbok-operationalizing.md
      enterprise-metadata-model.md
      metadata-management.md
    ai-security-risk/
      index.md
      guardrails.md
      sovereign-infrastructure.md
      mistral-ai.md
      ethics-bias.md
    delivery-operating-practice/
      index.md
      ci-by-design.md
    ai-adoption-maturity/
      index.md
      lean-ai-org.md

  playbooks/
    index.md
    dmbok-operationalization.md
    active-metadata-practice.md
    ci-by-design.md
    ai-eval-containment.md
    ai-product-alignment/
      index.md
      security-resilience.md
      human-in-the-loop.md
      stage-1-discovery.md
      stage-2-data-model-design.md
      stage-3-build-integration.md
      stage-4-governance-review.md
      stage-5-launch-rollout.md
      stage-6-operate-monitor.md

  reference/
    glossary.md
    legal-regulatory.md
    cost-finops.md
    case-studies.md
    experts.md
    tags.md
    landscape/
      index.md
      ai-ml-systems-engineering.md
      evaluation-observability.md
      data-governance.md
      ai-security-risk.md
      delivery-operating-practice.md
      ai-adoption-maturity.md

mkdocs.yml                    Site config & navigation
CONTRIBUTING.md                Content templates, Quality Bar, ToV Guide, domain promotion rule
GETTING-STARTED-GIT.md         Git/GitHub quick reference
LICENSE.md                     CC BY-NC 4.0
```

To regenerate this listing yourself and check it hasn't drifted: `find docs -name "*.md" | sort`.

This tree is generated from the actual repo, not hand-maintained prose — if it ever looks stale again, regenerate it with `find docs -name "*.md" | sort` rather than trust memory.
