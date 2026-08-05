---
name: ai-eval-containment
description: Use before running any AI capability evaluation with safety guardrails reduced or disabled, especially cyber-offense or red-team benchmarks.
tags:
  - security
  - resilience
  - governance
---

# Playbook: AI Capability Evaluation — Containment

## When to use

Before running any evaluation that deliberately reduces or disables a model's safety guardrails to measure maximum capability — cyber-offense benchmarks, red-team exercises, reduced-refusal safety research.

## Steps

1. **Treat the evaluation as running an internal adversary.** For its duration, the model has the capability profile of an attacker with access to compute and potentially credentials — plan the environment accordingly, not as a normal test run.
2. **Enforce a hard network and identity boundary.** Separate the evaluation environment from production and from anything the organization depends on — as an actual network and identity control, not an assumption the sandbox will hold.
3. **Adversarially test the egress path itself.** If the design relies on a single point of egress (a package proxy, an API gateway), verify its read-only or restricted behavior under attack — don't trust the intended behavior as a given.
4. **Keep a self-hostable model vetted and ready.** Hosted providers' own guardrails can limit what their tools will do during an active AI-driven incident, including one involving their own models. Have an alternative in reserve before you need it.
5. **Assume detection may come from outside the loop.** Build monitoring that doesn't depend on the evaluating team recognizing their own model's traffic — an external party may detect the breach first.

## Watch-outs

- "Sandboxed" and "guardrails disabled to measure capability" together describe a materially different risk profile than either term alone suggests.
- The organizational boundary between "systems we red-team" and "systems we depend on in production" needs to be a control, not a policy statement.

## Source

[Case study: Sandbox containment failure during an AI capability evaluation](../reference/case-studies.md)
