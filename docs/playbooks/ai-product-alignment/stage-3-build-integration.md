---
name: ai-product-stage-3-build-integration
description: Use during build — orchestration, tool integration, and the point where the five security & resilience controls get designed in.
tags:
  - architecture
  - security
---

# Stage 3 — Build & Integration

**Roles required:** AI Engineer (leads), Architect, DE (pipeline integration), Security (consult, adversarial testing plan)

**Decisions to lock:** orchestration pattern, tool/API integration points, latency budget, failure handling, and the [five Security & Resilience controls](security-resilience.md).

**Top 5 preventable issues**

| # | Issue | Owner | Prevention |
|---|---|---|---|
| 1 | No defined latency budget, so the app layer designs for instant response the model can't deliver | Architect + AI Engineer | Agree a latency budget per interaction type before UI design locks |
| 2 | Tool/API calls have no timeout or fallback, so one slow dependency hangs the whole request | AI Engineer | Every external call gets a timeout and a defined fallback behavior |
| 3 | Integration is built directly against a vendor's current API shape, no abstraction layer | Architect | An internal interface layer between the app and any external model/tool provider |
| 4 | Retry logic is unbounded, so a failing dependency spikes cost or cascades into a bigger outage | AI Engineer | Hard retry ceilings and circuit breakers |
| 5 | The pipeline feeding the build isn't tested for schema drift, so a silent upstream change corrupts inputs | DE | Schema validation on ingest, alerts on drift |

**Also non-negotiable:** no adversarial testing plan for prompt injection, jailbreak attempts, or data exfiltration through tool calls. *Owner: Security. Prevention: security review is scheduled before Stage 4 sign-off and treated as a required gate, not an optional nice-to-have.*

**Stage-gate question:** "What happens, specifically, when [dependency X] is slow or down? Walk me through it."

- *Rubber stamp:* "It'll retry."
- *Real answer:* names the timeout, the fallback UX, and who gets paged.

## Related

- [AI Architecture — Vendor-Agnostic Development](../../domains/ai-architecture/vendor-agnostic-development.md) — the abstraction-layer point above, in depth

---

**Previous:** [← Stage 2 — Data & Model Design](stage-2-data-model-design.md) · **Next:** [Stage 4 — Evaluation & Governance Review →](stage-4-governance-review.md)
