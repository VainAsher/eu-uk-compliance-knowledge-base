---
id: ai-governance-foundations
title: "AI Governance: Foundations, ISO/IEC 42001 & Operational Assurance"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: AI Governance
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [ai-act-foundations, gdpr-foundations, privacy-engineering-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [ai-governance, iso-42001, aims, nist-ai-rmf, oecd-ai-principles, trustworthy-ai, model-lifecycle, human-oversight]
legal_basis: Regulation (EU) 2024/1689 (operationalised via ISO/IEC 42001, NIST AI RMF, OECD AI Principles)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-governance-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.7.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It covers **AI governance and operations** — the management systems and voluntary frameworks organisations use to run AI responsibly. The **law itself** (the EU AI Act) is covered in `ai-act-foundations`; this document operationalises that law and should be read alongside it.

# Executive Summary

**AI governance** is the set of policies, roles, processes and controls through which an organisation directs and assures its development and use of AI — the operational counterpart to the EU AI Act's legal obligations [1][7]. Where `ai-act-foundations` states *what the law requires*, this document describes *how organisations meet it in practice*, using management systems and internationally recognised frameworks [3][7].

Three instruments dominate. **ISO/IEC 42001:2023** is the world's first certifiable **AI management system (AIMS)** standard, applying the familiar Plan-Do-Check-Act structure to AI so that governance is systematic, auditable and continually improved [7]. The **NIST AI Risk Management Framework (AI RMF 1.0**, January 2023) is a voluntary, outcomes-based framework organised around four functions — **Govern, Map, Measure, Manage** — and now extended by a **Generative AI Profile (NIST AI 600-1**, 26 July 2024) that names twelve GenAI-specific risk categories [11][12][13]. The **OECD AI Principles** (adopted 2019, **updated 3 May 2024**) supply the values baseline — human-centred, transparent, robust, accountable AI — that underpins both the AI Act and national policy [15][16].

The core message: governance frameworks are **voluntary but load-bearing**. They are not legally binding in themselves, yet adopting ISO/IEC 42001 and the NIST AI RMF is the most direct route to demonstrating AI Act conformity, GDPR accountability and trustworthy-AI due diligence [1][2][7]. The most important operational disciplines are **risk management across the model lifecycle**, **clear accountability**, **documentation and audit trails**, and **effective human oversight** [7][12].

# Key Takeaways

- **AI governance operationalises the law.** It translates AI Act obligations (risk management, data governance, logging, human oversight) into management-system controls [1][7]. *(Best practice.)*
- **ISO/IEC 42001:2023** is the first **certifiable** AI management system standard; it uses the ISO harmonised (Annex SL) management-system structure and is auditable by accredited certification bodies [7]. *(Best practice.)*
- **NIST AI RMF 1.0** (Jan 2023) is voluntary and organised around **Govern, Map, Measure, Manage**; its **Generative AI Profile (NIST AI 600-1**, 26 July 2024) adds twelve GenAI risk categories and 200+ suggested actions [11][12][13]. *(Best practice.)*
- **OECD AI Principles** (2019, **updated May 2024**) are the first intergovernmental AI standard — five values-based principles plus five policy recommendations — and were revised to address generative and general-purpose AI [15][16]. *(Best practice / soft law.)*
- **Governance frameworks are not law** but are the primary means of **demonstrating** AI Act and GDPR **accountability**; certification is evidence, not a legal safe harbour [1][2][7]. *(Regulatory interpretation.)*
- **Model lifecycle governance** — problem framing, data, training, evaluation, deployment, monitoring, retirement — is the spine of operational assurance and maps to the AI RMF functions [12]. *(Best practice.)*
- **Human oversight** is both an AI Act obligation (Art. 14) for high-risk systems and a governance control that frameworks help design and evidence [1][7]. *(Legal obligation + best practice.)*
- The **UK** has no horizontal AI statute; it applies a **principles-based, regulator-led** approach, making voluntary frameworks and existing law (data protection, equality) the practical governance baseline [4][5]. *(Regulatory interpretation.)*

# Purpose

This document is the Tier 2 entry point for **AI governance and operational assurance**. It supports: (a) building an AI management system that satisfies AI Act and GDPR accountability duties; (b) selecting and combining frameworks (ISO/IEC 42001, NIST AI RMF, OECD Principles); and (c) establishing lifecycle governance, roles, documentation and human-oversight practices. It presupposes `ai-act-foundations` (the law) and `gdpr-foundations` (parallel data-protection duties) and turns their requirements into an operating model.

# Scope

**In scope:** What AI governance is and why it exists; ISO/IEC 42001 (AIMS) structure and use; the NIST AI RMF 1.0 and its Generative AI Profile; the OECD AI Principles; AI risk management; model lifecycle governance; roles and accountability; documentation and audit; human oversight; the relationship of governance to the AI Act and GDPR; UK and global framing.

**Out of scope (spun off to the research backlog):** Detailed **model risk management** methodology (validation, back-testing, challenger models) → `ai-model-risk-management`; **AI audit and assurance** methodology in depth → `ai-audit-methodology`; **sector-specific** AI governance (financial services, healthcare, public sector) → respective sector documents; the **AI Act's** article-by-article obligations → `ai-act-foundations`, `ai-act-high-risk`, `ai-act-gpai`; GPAI Code of Practice detail → `ai-act-gpai`.

**Assumptions:** The reader has read `ai-act-foundations` and `gdpr-foundations`. "Governance" here means organisational management and assurance, not the AI Act's institutional "governance" bodies (AI Office etc.), which are covered in `ai-act-foundations`.

# Definitions

*Shared terms (AI system, GPAI model, high-risk AI system, accountability) are in `GLOSSARY.md`. Governance-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| AI governance | The organisational structures, policies, roles and processes that direct, resource and assure the responsible development, deployment and use of AI systems. | [7][16] |
| AI management system (AIMS) | A set of interrelated elements an organisation uses to establish policies and objectives, and processes to achieve them, in respect of the responsible development and use of AI systems (ISO/IEC 42001). | [7] |
| Trustworthy AI | AI that is lawful, robust and ethical — characterised (per NIST) as valid and reliable, safe, secure and resilient, accountable and transparent, explainable, privacy-enhanced, and fair with harmful bias managed. | [12] |
| AI RMF function | One of the four core functions of the NIST AI RMF — **Govern, Map, Measure, Manage** — under which outcomes and actions are organised. | [12] |
| AI system impact assessment | A structured, documented assessment of how an AI system may affect individuals, groups and society across its lifecycle (ISO/IEC 42005:2025). | [10] |
| Model lifecycle | The stages an AI/ML model passes through — problem definition, data acquisition, development/training, evaluation, deployment, monitoring, and retirement (ISO/IEC 22989 lifecycle concepts). | [9] |
| Human oversight | Measures enabling natural persons to understand, monitor, intervene in, or override an AI system's operation (AI Act Art. 14; a designed governance control). | [1] |

# Background

For most of the last decade AI risk was managed, if at all, through general IT, data-protection and model-risk controls not designed for machine learning. Three pressures changed this. First, **general-purpose and generative AI** created capabilities — and failure modes such as hallucination, data leakage and mass content generation — that generic controls did not anticipate [13]. Second, **regulation arrived**: the EU AI Act (Regulation (EU) 2024/1689) made risk management, data governance, documentation, human oversight and robustness legal obligations for high-risk systems [1][3]. Third, a **standards ecosystem** matured to give organisations a repeatable way to meet those expectations [7][12].

The result is a layered landscape. At the top sit **values and soft law**: the **OECD AI Principles** (2019, updated 2024), the first intergovernmental AI standard, adopted by 47 adherents including the EU, which shaped the AI Act's own "trustworthy, human-centric" framing [15][16]. Beneath them sit **frameworks and management standards** that make the values operational: the **NIST AI RMF** (voluntary, outcomes-based) and **ISO/IEC 42001** (certifiable management system) [7][12]. In the EU these are the practical means of demonstrating AI Act conformity; in the UK — which has **no horizontal AI law** and instead relies on a **principles-based, regulator-led approach** [4][5] — they are, for now, the main governance yardstick. This document sits at that operational layer.

# Legal Framework

AI governance is not itself a legal instrument; it is how organisations **discharge and evidence** obligations that arise elsewhere. Two bodies of law drive it, and a set of voluntary standards operationalise it.

- **EU AI Act (Regulation (EU) 2024/1689)** — imposes, for high-risk systems, a **risk-management system (Art. 9)**, **data governance (Art. 10)**, **technical documentation (Art. 11)**, **record-keeping/logging (Art. 12)**, **transparency (Art. 13)**, **human oversight (Art. 14)** and **accuracy/robustness/cybersecurity (Art. 15)** [1]. These are governance requirements in legal form. Providers must also operate a **quality management system (Art. 17)** — the AI Act's own management-system hook, to which ISO/IEC 42001 maps closely [1][7].
- **GDPR (Regulation (EU) 2016/679)** — where AI processes personal data, **accountability (Art. 5(2))**, **data protection by design and by default (Art. 25)**, **security (Art. 32)**, **DPIAs (Art. 35)** and rules on **automated decision-making (Art. 22)** apply in parallel; AI governance must therefore integrate with the data-protection programme [2].
- **Voluntary frameworks** — **ISO/IEC 42001**, the **NIST AI RMF** and the **OECD AI Principles** are not binding, but are the recognised means of meeting the above in a systematic, auditable way [7][12][15].

## Relevant Articles

*The AI Act articles are stated fully in `ai-act-foundations`; listed here only as the obligations that governance operationalises.*

| Article | Obligation (governance operationalises) | Source |
|---------|------------------------------------------|--------|
| AI Act Art. 9 | Risk-management system across the high-risk AI lifecycle. | [1] |
| AI Act Art. 10 | Data and data-governance practices (quality, relevance, bias examination). | [1] |
| AI Act Art. 11 + Annex IV | Technical documentation. | [1] |
| AI Act Art. 12 | Automatic record-keeping (logging) and traceability. | [1] |
| AI Act Art. 14 | Human oversight (understand, monitor, intervene, override). | [1] |
| AI Act Art. 17 | Quality management system for high-risk providers. | [1] |
| GDPR Art. 5(2) / Art. 25 | Accountability; data protection by design and by default. | [2] |
| GDPR Art. 35 | Data protection impact assessment. | [2] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| AI Act Recital 1 | Purpose — promote trustworthy, human-centric AI while protecting health, safety and fundamental rights (the values governance serves). | [1] |
| AI Act Recital 27 | References the trustworthy-AI principles (human agency/oversight, technical robustness, privacy/data governance, transparency, diversity/non-discrimination, societal well-being, accountability) that governance frameworks implement. | [1] |

## Relevant Case Law

**Not Applicable.** AI governance frameworks (ISO/IEC 42001, NIST AI RMF, OECD Principles) are voluntary standards and soft law, not statutes interpreted by courts; there is no case law construing them. Litigation touching AI to date turns on the GDPR, equality or consumer law (see `gdpr-foundations`), not on these frameworks. [7][12]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **European Commission:** presents AI Act compliance as a systematic, lifecycle undertaking and points providers toward harmonised standards and management systems (including a quality management system under Art. 17) as the route to conformity; the **AI Office** coordinates implementation and the GPAI Code of Practice [3][6]. *(Regulatory interpretation.)*
- **ICO (UK):** its **AI and data protection** guidance treats governance and accountability as central — organisations must document AI processing, assess risks (including bias and explainability), and embed data protection by design; the ICO frames this as existing-law obligations, not new AI-specific ones [4]. *(Regulatory interpretation.)*
- **UK Government:** the **"pro-innovation approach to AI regulation"** declines a horizontal statute in favour of **five cross-sector principles** (safety/security/robustness; transparency/explainability; fairness; accountability/governance; contestability/redress) applied by existing regulators — making voluntary frameworks the practical governance baseline in the UK [5]. *(Regulatory interpretation.)*
- **Interpretive caution:** certification to ISO/IEC 42001 or alignment to the NIST AI RMF is **evidence of diligence, not a legal safe harbour**; regulators assess actual compliance with the AI Act and GDPR, for which a certificate is supporting — not conclusive — proof [1][2][7]. *(Regulatory interpretation.)*

# Technical Considerations

- **Adopt a management-system spine.** ISO/IEC 42001 follows the ISO harmonised structure (context, leadership, planning, support, operation, performance evaluation, improvement) plus AI-specific controls in **Annex A** (e.g., AI policy, roles, impact assessment, data management, lifecycle controls) with implementation guidance in **Annex B** [7]. Build governance on this spine so it is auditable. *(Best practice.)*
- **Use the AI RMF functions as the operating loop.** **Govern** (culture, roles, policy) is cross-cutting; **Map** (context and risk framing), **Measure** (assessment, metrics, testing) and **Manage** (prioritise, respond, monitor) run iteratively across the lifecycle [12]. *(Best practice.)*
- **Instrument the model lifecycle.** Attach controls at each stage — data provenance and quality (AI Act Art. 10), evaluation and red-teaming (especially for GenAI), deployment gates, and post-deployment **monitoring** for drift and incidents [1][12][13]. *(Legal obligation for high-risk + best practice.)*
- **Impact assessment.** Use **ISO/IEC 42005:2025** to conduct AI system impact assessments, and align them with GDPR **DPIAs** where personal data is involved so a single assessment serves both regimes [2][10]. *(Best practice.)*
- **Documentation and logging by design.** Technical documentation (AI Act Art. 11), model/system cards, decision logs and automatic record-keeping (Art. 12) should be generated as a by-product of the pipeline, not retrofitted [1]. *(Legal obligation for high-risk + best practice.)*
- **GenAI-specific controls.** The NIST GenAI Profile flags risks such as confabulation/hallucination, data leakage, harmful bias, CBRN/cyber uplift, and content-integrity harms — address them with input/output filtering, provenance/watermarking, and human review [13]. *(Best practice.)*

# Hosting Considerations

- **Infrastructure operators are usually deployers or processors, not framework owners.** Hosting an AI system does not by itself require an AIMS, but where the host brands, materially modifies, or takes provider-level responsibility, ISO/IEC 42001 scope and AI Act provider duties may attach [1][7]. *(Legal obligation — assess role.)*
- **Logging and retention.** High-risk logging (AI Act Art. 12) must be retained in the hosting environment while honouring GDPR storage-limitation and security duties (Arts. 5, 32) — coordinate with `privacy-engineering-foundations` [1][2]. *(Legal obligation.)*
- **Shared-responsibility clarity.** Cloud providers increasingly hold ISO/IEC 42001 certification for named AI services; deployers should map which AIMS controls the provider covers and which remain the deployer's own [7]. *(Best practice.)*

# Game Hosting Considerations

- **Most game AI is minimal risk**, so a full AIMS is rarely mandatory; nonetheless a **lightweight governance baseline** (inventory, transparency for AI chatbots/companions, content monitoring for generative features) is advisable, especially where minors are involved [1][3]. *(Best practice.)*
- **Generative content governance.** Player-facing GenAI (NPC dialogue, user-generated content tools) should adopt the GenAI Profile's controls — output filtering, provenance marking, abuse monitoring — to manage toxicity, IP and safety risks [13]. *(Best practice.)*
- **Escalation triggers.** Biometric, emotion-inference or matchmaking features affecting access to services can cross into higher-risk tiers, at which point AI Act governance obligations and a formal AIMS become material [1]. *(Legal obligation once triggered.)*

# AI Considerations

*This document is itself about AI operations; the "AI Considerations" here concern how governance interlocks with the AI-regulation and data-protection stack.*

- **Operationalises the AI Act.** ISO/IEC 42001's management system and the NIST AI RMF functions are the practical vehicle for AI Act Arts. 9–17 duties; harmonised European standards (under development via CEN/CENELEC) will formalise this mapping, but 42001 and the AI RMF are the interim best practice [1][7][12]. *(Best practice.)*
- **Integrates with GDPR.** AI governance must not run separately from the data-protection programme: AI impact assessments should dovetail with DPIAs, and lifecycle data controls with DPbDD and Art. 32 security [2][10]. *(Legal obligation + best practice.)*
- **Values traceability.** The OECD Principles' five values (inclusive growth/well-being; human rights and democratic values; transparency and explainability; robustness, security and safety; accountability) trace directly into both the AI Act's trustworthy-AI recitals and the NIST trustworthiness characteristics — use them as the north star when frameworks are silent [12][15][16]. *(Best practice / soft law.)*
- **GenAI and GPAI.** For organisations building on foundation models, governance must extend up the supply chain — evaluating model providers, documenting model choices, and applying the GenAI Profile — complementing the GPAI obligations covered in `ai-act-foundations`/`ai-act-gpai` [13]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Stand up an AI governance function** — assign accountable ownership (e.g., an AI governance board and a named senior owner), an AI policy, and defined roles across the lifecycle. *(BEST PRACTICE; OBLIGATION-adjacent via AI Act Art. 17 QMS and GDPR Art. 5(2).)* [1][2][7]
2. **Maintain an AI system inventory** with tier, role (provider/deployer) and risk rating; this is the precondition for every other control. *(BEST PRACTICE; supports OBLIGATION.)* [1][7]
3. **Adopt a recognised framework and map it to the law** — implement ISO/IEC 42001 and/or the NIST AI RMF and cross-map controls to AI Act Arts. 9–17 and GDPR. *(BEST PRACTICE.)* [7][12]
4. **Run risk management continuously** — use ISO/IEC 23894 (AI risk management) and the AI RMF Map/Measure/Manage loop; re-assess on material change. *(OBLIGATION for high-risk via Art. 9; BEST PRACTICE otherwise.)* [1][8][12]
5. **Conduct AI system impact assessments** (ISO/IEC 42005) and align them with GDPR DPIAs. *(OBLIGATION where DPIA triggered; BEST PRACTICE otherwise.)* [2][10]
6. **Design human oversight in, not on** — define who can monitor, intervene and override, with the authority and training to do so. *(OBLIGATION for high-risk via Art. 14; BEST PRACTICE otherwise.)* [1]
7. **Generate documentation and logs automatically** — technical documentation, model/system cards, evaluation records and decision logs as pipeline outputs. *(OBLIGATION for high-risk via Arts. 11–12; BEST PRACTICE otherwise.)* [1]
8. **Apply GenAI-specific controls** using the NIST GenAI Profile and its suggested actions. *(BEST PRACTICE.)* [13][14]
9. **Prepare for external assurance** — internal audit against ISO/IEC 42001, then accredited certification where it adds market or regulatory value. *(EDITORIAL RECOMMENDATION.)* [7]
10. **Use the NIST AI RMF Playbook** for concrete, function-by-function suggested actions when translating outcomes into tasks. *(EDITORIAL RECOMMENDATION.)* [14]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | No AI governance ownership; controls ad hoc | High | High | AI Act Art. 17; GDPR Art. 5(2) [1][2] | Governance board; named owner; AI policy | Medium |
| R2 | Treating certification as a legal safe harbour | Medium | High | Certification is evidence, not compliance [7] | Map controls to actual AI Act/GDPR duties; keep audit trail | Low |
| R3 | Model risk unmanaged across lifecycle | Medium | High | AI Act Art. 9; ISO/IEC 23894 [1][8] | Continuous risk loop (Map/Measure/Manage); monitoring | Medium |
| R4 | Inadequate human oversight for high-risk AI | Medium | High | AI Act Art. 14 [1] | Designed oversight roles, authority, training | Low |
| R5 | Poor documentation/logging; not audit-ready | Medium | High | AI Act Arts. 11–12 [1] | Auto-generated docs, model cards, logs | Low |
| R6 | GenAI-specific harms unaddressed | Medium | High | NIST GenAI Profile [13] | Output filtering, provenance, red-teaming, human review | Medium |
| R7 | AI governance siloed from data protection | Medium | Medium | GDPR Arts. 25, 35 [2] | Integrate AI impact assessments with DPIAs | Low |
| R8 | UK reliance on voluntary frameworks misread as "no rules" | Low | Medium | Existing law still applies [4][5] | Apply data-protection/equality law + frameworks | Low |

# Implementation Roadmap

- **Phase 0 — Foundations:** Establish AI governance ownership, AI policy, and an AI system inventory (tier + role). *Effort:* Medium. *Depends on:* `ai-act-foundations` triage.
- **Phase 1 — Framework adoption:** Select ISO/IEC 42001 and/or NIST AI RMF; map controls to AI Act Arts. 9–17 and GDPR. *Effort:* High.
- **Phase 2 — Lifecycle controls:** Implement risk management (ISO/IEC 23894 + AI RMF), impact assessments (ISO/IEC 42005), data governance, documentation and logging. *Effort:* High.
- **Phase 3 — Human oversight & GenAI controls:** Design oversight roles; apply the GenAI Profile to generative systems. *Effort:* Medium.
- **Phase 4 — Assurance:** Internal audit; align DPIAs and AI impact assessments; pursue accredited ISO/IEC 42001 certification where valuable. *Effort:* High.
- **Phase 5 — Continual improvement:** Monitor performance, incidents and drift; track harmonised standards and framework updates; re-certify. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No AI governance; controls absent or ad hoc. | No inventory; no owner. |
| 2 | Managed | Basic ownership and inventory; some risk awareness. | AI policy drafted; partial inventory. |
| 3 | Defined | Framework adopted and mapped to law; lifecycle controls documented. | ISO/IEC 42001 or AI RMF in use; impact assessments. |
| 4 | Quantitatively Managed | Controls measured and tested; oversight and GenAI controls operating with metrics. | KPIs on bias, drift, oversight; internal audit. |
| 5 | Optimising | Integrated AI + data-protection governance; certified AIMS; continual improvement. | ISO/IEC 42001 certified; DPIA/impact-assessment integration; re-certification cycle. |

# Audit Questions

1. Who is accountable for AI governance, and what AI policy and roles are documented? *(AI Act Art. 17; GDPR Art. 5(2) [1][2].)*
2. Is there a complete AI system inventory with tier and provider/deployer role? *([1][7].)*
3. Which framework(s) have you adopted, and how are their controls mapped to AI Act Arts. 9–17 and the GDPR? *([7][12].)*
4. How is AI risk managed continuously across the lifecycle, and re-assessed on change? *(Art. 9; ISO/IEC 23894 [1][8].)*
5. Do you conduct AI system impact assessments, and are they integrated with DPIAs? *([2][10].)*
6. How is human oversight designed, resourced and evidenced for high-risk systems? *(Art. 14 [1].)*
7. Are technical documentation, model/system cards and logs generated and retained? *(Arts. 11–12 [1].)*
8. What GenAI-specific controls (filtering, provenance, red-teaming) are in place? *(NIST GenAI Profile [13].)*
9. Has the AIMS been internally audited, and is external certification pursued where valuable? *([7].)*

# Implementation Checklist

- [ ] AI governance owner and board established; AI policy approved.
- [ ] AI system inventory with tier + provider/deployer role.
- [ ] ISO/IEC 42001 and/or NIST AI RMF adopted and mapped to AI Act + GDPR.
- [ ] Continuous AI risk management loop (Map/Measure/Manage; ISO/IEC 23894) operating.
- [ ] AI system impact assessments (ISO/IEC 42005) integrated with DPIAs.
- [ ] Human oversight roles designed, resourced and evidenced (Art. 14).
- [ ] Technical documentation, model/system cards and logs auto-generated (Arts. 11–12).
- [ ] GenAI controls applied per the NIST GenAI Profile.
- [ ] Internal audit completed; certification path decided.
- [ ] Framework/standard update watch-list maintained.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [2] **Regulation (EU) 2016/679 (GDPR).** EUR-Lex, ELI (parallel application to AI processing personal data). https://eur-lex.europa.eu/eli/reg/2016/679/oj

## Regulatory Guidance

*Includes intergovernmental soft-law instruments (OECD), which are authoritative but non-binding.*

- [3] **Regulatory framework on AI / AI Act.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai
- [4] **Artificial intelligence — guidance for organisations.** ICO (UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/artificial-intelligence/
- [5] **A pro-innovation approach to AI regulation.** UK Government (DSIT), GOV.UK. https://www.gov.uk/government/publications/a-pro-innovation-approach-to-ai-regulation
- [6] **The AI Office.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/ai-office
- [15] **Recommendation of the Council on Artificial Intelligence (OECD/LEGAL/0449).** OECD Legal Instruments (adopted 2019; amended 3 May 2024). https://legalinstruments.oecd.org/en/instruments/OECD-LEGAL-0449
- [16] **OECD AI Principles overview.** OECD.AI Policy Observatory. https://oecd.ai/en/ai-principles

## Standards

- [7] **ISO/IEC 42001:2023 — Information technology — Artificial intelligence — Management system (AIMS).** ISO/IEC. https://www.iso.org/standard/42001
- [8] **ISO/IEC 23894:2023 — Artificial intelligence — Guidance on risk management.** ISO/IEC. https://www.iso.org/standard/77304.html
- [9] **ISO/IEC 22989:2022 — Artificial intelligence — Concepts and terminology.** ISO/IEC. https://www.iso.org/standard/74296.html
- [10] **ISO/IEC 42005:2025 — Artificial intelligence — AI system impact assessment.** ISO/IEC. https://www.iso.org/standard/42005
- [11] **AI Risk Management Framework (AI RMF 1.0) — overview.** NIST. https://www.nist.gov/itl/ai-risk-management-framework
- [12] **Artificial Intelligence Risk Management Framework (AI RMF 1.0), NIST AI 100-1** (Jan 2023). NIST. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf
- [13] **AI RMF: Generative Artificial Intelligence Profile, NIST AI 600-1** (26 July 2024). NIST. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf
- [14] **NIST AI RMF Playbook.** NIST AI Resource Center (AIRC). https://airc.nist.gov/airmf-resources/playbook/

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation, regulator guidance and recognised standards. Academic analysis (e.g., model-risk-management theory, AI-audit methodology critique) will be cited in the spun-off sub-topic documents (`ai-model-risk-management`, `ai-audit-methodology`).

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- OECD.AI Policy Observatory — national AI policies and tools catalogue. https://oecd.ai/en/ai-principles
- NIST AI Resource Center (AIRC) — Playbook and crosswalks. https://airc.nist.gov/airmf-resources/playbook/

# Related Documents

- `ai-act-foundations` — the EU AI Act (the **law** this document operationalises); **prerequisite reading**.
- `gdpr-foundations` — parallel data-protection regime; accountability and DPIAs.
- `privacy-engineering-foundations` — DPbDD and security controls underpinning AI data governance and logging.
- `ai-model-risk-management` — deep-dive on model validation and monitoring (planned; out-of-scope spin-off).
- `ai-audit-methodology` — AI audit and assurance methodology (planned; out-of-scope spin-off).
- `ai-act-gpai` — GPAI regime and Code of Practice (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against ISO/IEC 42001/23894/22989/42005, NIST AI RMF 1.0 and the Generative AI Profile (NIST AI 600-1, 26 Jul 2024), and the OECD AI Principles (2024 update); framework versions and dates live-verified; all external links checked HTTP 200 on 2026-07-11 (OECD principles cited via OECD.AI and OECD Legal Instruments, as oecd.org main-site pages bot-block curl). | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at batch human review gate (parallel cluster); frozen in release 0.7.0. | Human reviewer |
