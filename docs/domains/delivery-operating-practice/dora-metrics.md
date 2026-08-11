---
tags:
  - ci
  - evaluation
---

# DORA Metrics

The other named source grounding this domain, alongside Team Topologies — and until now, cited repeatedly across this hub without its own explainer page.

## Origin

DORA (DevOps Research and Assessment) began as a multi-year research program in 2014, led by Dr. Nicole Forsgren, Jez Humble, and Gene Kim, studying what actually separates high-performing software delivery organizations from the rest — not opinion, survey data across thousands of organizations. The findings were published as the 2018 book *Accelerate*. Google acquired DORA in 2019; its research now ships as the annual "State of DevOps" report at [dora.dev](https://dora.dev/).

## The original four metrics

| Metric | What it measures |
|---|---|
| **Deployment Frequency** | How often an organization ships to production |
| **Lead Time for Changes** | Time from commit to running in production |
| **Change Failure Rate** | Percentage of deployments that cause a production failure |
| **Mean Time to Recovery (MTTR)** | How quickly service is restored after a failure |

These split into two categories: **throughput** (Deployment Frequency, Lead Time — how fast) and **stability** (Change Failure Rate, MTTR — how safe). The core finding *Accelerate* is built on: these aren't in tension. High performers do both at once; slow delivery doesn't buy you safety.

## How it's evolved — worth tracking, not treating as fixed

- **2021** — a fifth metric, **Reliability**, was added.
- **2022** — the original four-tier "Elite / High / Medium / Low" performer clustering was retired; cluster analysis found only three statistically distinct groups, not four.
- **2025** — a genuine inflection point: DORA's annual report skipped the traditional State of DevOps format entirely and became dedicated to AI-assisted software development. Key finding: AI adoption improves throughput but *increases* delivery instability — speed and safety decoupling again, specifically because of AI-assisted coding. The report also introduced an **AI Capabilities Model** and replaced the old tiered clustering with seven archetypes combining technical and human performance factors.
- **2026, live debate** — a growing body of practitioner commentary argues the original four metrics get *misleading*, not just incomplete, once AI generates a large share of committed code — Deployment Frequency and Lead Time can look artificially strong while quality and team health quietly erode. This isn't settled consensus, but it's a live enough debate to flag rather than present the four-metric model as unchanged since 2018.

## Decision Areas

- Are you tracking the original four (or five) metrics as designed, or as vanity numbers disconnected from the throughput/stability pairing they were built to hold in tension?
- If AI-assisted coding is a meaningful share of your commits, have you checked whether Deployment Frequency and Lead Time still mean what they used to — per DORA's own 2025 findings, this is no longer a safe assumption?
- Is Change Failure Rate measured against a real definition of "failure," or quietly redefined to look better?

## Related

- [Team Topologies](team-topologies.md) — the team-design counterpart; DORA measures the outcome, Team Topologies helps structure the org to produce it
- [CI-by-Design](ci-by-design.md) — DORA metrics as the way to know whether this practice is actually working
- [Experts & Sources](../../reference/experts.md) — Nicole Forsgren

## Source

[dora.dev](https://dora.dev/) — the living, actively maintained research home, including the full 2025 AI-focused report.
