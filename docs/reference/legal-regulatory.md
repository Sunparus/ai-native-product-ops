# Legal & Regulatory Landscape

!!! danger "Not legal advice"
    Reference only. Regulatory status — especially the EU AI Act's high-risk timeline and the US federal/state preemption fight — is actively moving as of mid-2026. Verify current status against official sources before any compliance decision.

## European Union

| Instrument | Status | Relevance |
|---|---|---|
| **[GDPR](https://eur-lex.europa.eu/eli/reg/2016/679/oj)** | In force since 2018 | The bedrock data-protection law — lawful basis, data subject rights, cross-border transfer rules. Everything else EU builds on top of this. |
| **[EU AI Act (Reg. 2024/1689)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)** | Staggered; core dates shifting — verify current status | Risk-tiered AI regulation. Prohibitions & GPAI rules already live; high-risk (Annex III) obligations are under an active deferral proposal ("Digital Omnibus") as of mid-2026 — treat exact dates as moving, not fixed. |
| **[Data Governance Act](https://eur-lex.europa.eu/eli/reg/2022/868/oj)** | In force since 2022 | Facilitates data sharing/reuse across sectors and borders under trusted intermediary models. |
| **[Data Act](https://eur-lex.europa.eu/eli/reg/2023/2854/oj)** | Applicable since Sept 2025 | Governs access to IoT and B2B-generated data, including cloud-switching rights relevant to vendor lock-in. |
| **[NIS2 Directive](https://eur-lex.europa.eu/eli/dir/2022/2555/oj)** | In force | Cybersecurity risk-management obligations for critical and important entities — relevant to the Resilience layer. |
| **[DORA (Digital Operational Resilience Act)](https://eur-lex.europa.eu/eli/reg/2022/2554/oj)** | Applicable since Jan 2025 | ICT risk management for financial-sector entities specifically. Unrelated to the DORA engineering metrics referenced elsewhere in this hub — same acronym, different field. |

## United States

| Instrument | Status | Relevance |
|---|---|---|
| **No comprehensive federal AI statute** | As of 2026 | Federal layer is executive orders and voluntary frameworks, not binding legislation — the single most important fact for US strategy. |
| **[EO 14365 — National AI Policy Framework](https://www.federalregister.gov/presidential-documents/executive-orders)** | Signed Dec 2025; contested | Attempts to preempt state AI laws deemed "burdensome." Legal durability is unresolved — an executive order cannot itself override state statute without congressional action. Federal Register link goes to the executive orders index — verify the specific EO there, as direct per-order permalinks shift. |
| **State AI laws (CA, CO, TX, IL, UT)** | Live, binding | The actual enforceable layer today. California TFAIA and Texas RAIGA effective Jan 2026; Colorado's reenacted framework takes effect Jan 2027. Track state-by-state via [National Conference of State Legislatures' AI legislation tracker](https://www.ncsl.org/technology-and-communication/artificial-intelligence-2025-legislation). |
| **Sector-specific: [HIPAA](https://www.hhs.gov/hipaa/index.html) / [GLBA](https://www.ftc.gov/business-guidance/privacy-security/gramm-leach-bliley-act) / [COPPA](https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa)** | Long-standing | Pre-date AI but govern health, financial, and children's data respectively — apply fully to AI systems touching that data. |
| **[NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)** | Voluntary | Not law, but the most widely referenced US risk framework — often adopted contractually even where not mandated. |

## Global Guidelines

| Instrument | Status | Relevance |
|---|---|---|
| **[OECD AI Principles](https://oecd.ai/en/ai-principles)** | 2019, updated 2024 | First intergovernmental AI standard; underpins most national AI policy language worldwide, including early EU AI Act drafting. |
| **[UNESCO Recommendation on the Ethics of AI](https://www.unesco.org/en/artificial-intelligence/recommendation-ethics)** | Adopted 2021 | Broadest global consensus document on AI ethics — non-binding but frequently cited in procurement and policy language. |
| **[G7 Hiroshima AI Process](https://www.mofa.go.jp/policy/economy/g7summit/hiroshima23/index.html)** | 2023 onward | Voluntary code of conduct for advanced AI developers, signed by major frontier labs. |

## Industry Standards & Frameworks

| Instrument | Status | Relevance |
|---|---|---|
| **[ISO/IEC 42001](https://www.iso.org/standard/42001)** | Published 2023 | The first certifiable AI management system standard — the closest AI equivalent to ISO 27001 for security. Increasingly requested in enterprise vendor due diligence. |
| **[ISO/IEC 27001:2022](https://www.iso.org/standard/27001)** | Established | Information security management — near-universal baseline for enterprise vendor security posture, AI or not. |
| **[ISO/IEC 38505-1](https://www.iso.org/standard/56639.html)** | Established (2017) | Governance of data — the ISO-side counterpart to DAMA-DMBOK's governance knowledge area. |
| **[ISO/IEC TR 24027](https://www.iso.org/standard/77607.html)** | Published 2021 | Bias in AI systems and AI-aided decision-making — measurement techniques referenced in [Ethics & Bias](../domains/ai-security-risk/ethics-bias.md). |
| **[SOC 2](https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2)** | Established | US-originated but globally requested attestation on security, availability, and confidentiality controls — standard vendor due-diligence ask. Governed by AICPA, not ISO. |
