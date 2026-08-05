---
name: ci-by-design
description: Use when setting up or auditing how AI-assisted changes (prompts, model versions, data sources) reach production.
tags:
  - lean
  - ci
  - evaluation
---

# Playbook: CI-by-Design for AI

## When to use

Standing up a delivery pipeline for AI-assisted features, or auditing an existing one that treats model/prompt changes as exempt from the testing discipline applied to code.

## Steps

1. **Extend CI to cover model behavior, not just code.** Every change — prompt, model version, retrieved data source — runs through automated evaluation before production, the same way code runs through tests.
2. **Shift left.** Catch failures in evaluation pipelines, not in production. Cost compounds the later a defect is caught.
3. **Build one golden path.** A single sanctioned, secure, pre-approved way to ship AI features gets adopted faster than a rulebook, because it's the path of least resistance.
4. **Add circuit breakers.** Auto-disable a failing model or tool call rather than letting failures cascade through dependent systems.
5. **Define blast radius up front.** Know, before an incident, how much of the system one failure can actually take down — and design containment to that boundary.

## Watch-outs

- Resilience patterns (circuit breakers, blast radius) are CI concerns to design in from the start, not incident-response afterthoughts bolted on after the first outage.
- Track DORA metrics (deployment frequency, lead time, change failure rate, recovery time) to know whether this is actually working — not just whether it's in place.

## Source

[Lean & Engineering — CI-by-Design (full explainer)](../domains/lean-engineering/ci-by-design.md)
