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

## OWASP Top 10 for LLM Applications (2025 v2.0)

The actual named threat list guardrails exist to address — published November 2024, current as of this writing:

| # | Risk | What it means |
|---|---|---|
| LLM01 | **Prompt Injection** | Crafted input overrides the model's original instructions — direct (in the user's own prompt) or indirect (hidden in a document, webpage, or email the model processes) |
| LLM02 | **Sensitive Information Disclosure** | Secrets, PII, or confidential data leak through outputs or traces |
| LLM03 | **Supply Chain** | Compromised models, datasets, libraries, or hosting providers |
| LLM04 | **Data and Model Poisoning** | Malicious training, fine-tuning, or retrieval data shapes model behavior |
| LLM05 | **Improper Output Handling** | Model output trusted and acted on downstream without validation |
| LLM06 | **Excessive Agency** | An agent has more permissions or autonomy than the task actually requires |
| LLM07 | **System Prompt Leakage** | Internal instructions or configuration exposed through the model's own responses |
| LLM08 | **Vector and Embedding Weaknesses** | Poisoned or manipulated vector stores in RAG systems, or insufficient access control across tenant boundaries |
| LLM09 | **Misinformation** | The model generates confident, plausible, factually wrong output — hallucination, sharpened to include the model's own contribution, not just user overreliance |
| LLM10 | **Unbounded Consumption** | Resource exhaustion — cost or compute spend without limits, an expansion of the older "Model Denial of Service" category |

Prompt injection (LLM01) has held the top spot since the list's first edition — worth treating as the default assumption for any system that processes untrusted input, not an edge case.

**Source:** [OWASP GenAI Security Project — Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/).

## Related

- [Ethics & Bias](ethics-bias.md) — LLM09 (Misinformation) and fairness-related output filtering overlap directly
- [AI/ML Systems Engineering](../ai-ml-systems-engineering/index.md) — where these controls actually get implemented, in the Orchestration and Application layers
- [Playbook: AI Eval Containment](../../playbooks/ai-eval-containment.md) — LLM03 (Supply Chain, the compromised package-registry proxy) in a real, documented incident. Worth noting precisely: the intrusion happened because guardrails were *deliberately* disabled to test capability, not because of an Excessive Agency (LLM06) design flaw — a different failure mode than most OWASP categories assume, since OWASP's list targets production applications, not adversarial capability evaluations
- Glossary: [Prompt Injection](../../reference/glossary.md), [Hallucination](../../reference/glossary.md)
