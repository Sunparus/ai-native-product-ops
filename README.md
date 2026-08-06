# AI-Native Product Operations — Expertise Hub

A git-versioned, markdown-based knowledge base. Built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

Content is licensed [CC BY-NC 4.0](LICENSE.md) — read, share, and quote freely with attribution; no commercial use without permission.

## Why this replaced the single-file interactive artifact

- **Resilience** — content lives in plain markdown files, one per topic. A mistake in one file can't break the rest of the site.
- **Versioning** — every change is a git commit. Full history, diffs, and rollback (`git log`, `git diff`, `git revert`).
- **Scalability** — add a new file, add a nav entry, done. No monolithic component to hand-edit.

## Local preview

```bash
pip install mkdocs mkdocs-material
mkdocs serve
```

Open `http://127.0.0.1:8000`.

## Deploy for free

**Option A — GitHub Pages** (recommended, gives you a real shareable URL):
```bash
# after pushing this repo to a GitHub repo you own:
mkdocs gh-deploy
```

**Option B — Netlify:** drag-and-drop the `site/` folder (run `mkdocs build` first) onto app.netlify.com/drop.

## Editing content

Every page is a `.md` file under `docs/`. Edit any file, then:

```bash
git add -A
git commit -m "describe what changed"
```

That commit is your version history. `git log --oneline` shows every change ever made to the hub.

## Structure

```
docs/
  index.md                        Home
  architecture/
    dependency-map.md             6-layer pipeline + 4 cross-cutting concerns
    glossary.md                   37 terms, categorized
  deep-dives/                     9 topic explainers
  dmbok/
    wheel.md                      11 knowledge areas
    operationalizing.md           5-step operationalization pathway
  legal-regulatory.md             EU / US / Global / Industry standards
  experts.md                      20 people & orgs, 6 groups
  landscape.md                    Open questions, trends, companies
mkdocs.yml                        Site config & navigation
```
