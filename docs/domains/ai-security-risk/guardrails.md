---
tags:
  - security
  - governance
---

# Guardrails

*Governance — constraining model behavior*

Mechanisms that constrain what a model can input, output, or act on. Split into model-level (system prompts, RLHF alignment) and system-level (secondary classifiers, rule engines, human-approval gates) — system-level guardrails are the ones an enterprise actually controls.

- Categories: input validation, output content filtering, PII redaction, prompt-injection defense, action-approval thresholds for agents.
- Model-level alignment is necessary but not sufficient — it can be bypassed; system-level guardrails are your enforceable control layer.
- Reputable reference frameworks: [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework), [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/), [MITRE ATLAS](https://atlas.mitre.org/).

**Source:** [OWASP GenAI Security Project — Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/).
