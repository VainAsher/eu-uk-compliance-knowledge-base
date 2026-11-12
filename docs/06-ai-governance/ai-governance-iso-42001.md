---
id: ai-governance-iso-42001
title: "AI Governance: Implementing ISO/IEC 42001 (AI Management System)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: AI Governance
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
related: [ai-governance-foundations, ai-act-high-risk, ai-act-foundations, privacy-engineering-foundations]
tags: [ai-governance, iso-42001, aims, annex-a, annex-b, pdca, certification, nist-ai-rmf, iso-23894, iso-42005, ai-act-art-17]
legal_basis: ISO/IEC 42001:2023 (voluntary standard) operationalising Regulation (EU) 2024/1689 (AI Act)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-governance-iso-42001 |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.15.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | Human reviewer (loop-authorised) — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a Tier 2 **deep-dive** that **details** the ISO/IEC 42001 material introduced at overview level in `ai-governance-foundations` (its parent); it does not repeat the parent's treatment of the NIST AI RMF or the OECD Principles except where they intersect the management system. **Standards-edition warning:** ISO/IEC standards are periodically revised. The editions relied on here were **live-verified on 2026-07-11** — ISO/IEC 42001:**2023**, ISO/IEC 23894:**2023**, ISO/IEC 42005:**2025**, ISO/IEC 42006:**2025**, ISO/IEC 38507:**2022**, ISO/IEC 22989:**2022** — and NIST AI RMF **1.0** (Jan 2023) with the Generative AI Profile (**NIST AI 600-1**, 26 Jul 2024). Confirm the current edition and any amendment before relying on clause or control numbering.

# Executive Summary

**ISO/IEC 42001:2023** is the world's first certifiable **AI management system (AIMS)** standard [8]. It applies the same harmonised management-system structure used by ISO/IEC 27001 (information security) and ISO 9001 (quality) — Clauses 4 to 10, run on a **Plan-Do-Check-Act (PDCA)** cycle — to the specific problem of developing and using AI responsibly [8][19]. Where `ai-act-foundations` and `ai-act-high-risk` state *what the EU AI Act requires*, and `ai-governance-foundations` surveys the framework landscape, this document is the practical **how-to for standing up, operating and certifying an AIMS**, and for using that AIMS to discharge and evidence AI Act obligations [1][8].

The standard has two load-bearing parts. The **management clauses (4–10)** set auditable requirements: understand the organisation's context and interested parties (Cl. 4); secure leadership and an **AI policy** (Cl. 5); plan by running an **AI risk assessment**, **AI risk treatment** and **AI system impact assessment** (Cl. 6); provide resources, competence and documented information (Cl. 7); operate the planned controls (Cl. 8); evaluate through monitoring, internal audit and management review (Cl. 9); and improve via corrective action (Cl. 10) [8]. **Annex A** then lists reference **controls** grouped under nine areas — policies, internal organisation, resources, impact assessment, AI system life cycle, data for AI, information for interested parties, use of AI, and third-party relationships — with **Annex B** giving implementation guidance for each [8].

The core message: ISO/IEC 42001 is **voluntary but the most direct auditable route** to AI Act conformity. Its clauses map closely onto the AI Act's **quality management system (Art. 17)** and its risk-management, data-governance, documentation, logging, transparency and human-oversight duties (Arts. 9–15) [1][8]. Certification is **evidence of diligence, not a legal safe harbour** [3][12].

# Key Takeaways

- **ISO/IEC 42001:2023 is the first certifiable AIMS standard** and uses the ISO harmonised (Annex SL) structure shared with ISO/IEC 27001, so it integrates with an existing ISMS/QMS rather than duplicating it [8][19]. *(Best practice.)*
- **The AIMS runs on PDCA:** Plan (Cl. 4–7), Do (Cl. 8), Check (Cl. 9), Act (Cl. 10) — governance becomes a continual, auditable loop rather than a one-off project [8]. *(Best practice.)*
- **Planning is the AI-specific heart of the standard:** Clause 6 requires an **AI risk assessment**, **AI risk treatment** (selecting Annex A controls) and an **AI system impact assessment** on individuals and society — the last is distinctive to AI management systems [8][10]. *(Best practice.)*
- **Annex A lists reference controls under nine areas; Annex B gives implementation guidance** — policies, internal organisation, resources, impact assessment, AI system life cycle, data for AI, information for interested parties, use of AI, and third-party relationships [8]. *(Best practice.)*
- **42001 operationalises the EU AI Act.** Its clauses and controls map closely to the **Art. 17 quality management system** and the high-risk requirements of **Arts. 9–15**; a control-mapping table is provided below [1][8]. *(Best practice; the underlying AI Act duties are legal obligations.)*
- **42001 complements, not replaces, other instruments:** it references **ISO/IEC 23894** for AI risk-management method, **ISO/IEC 42005** for impact-assessment method, **ISO/IEC 22989** for terminology, and interoperates with the **NIST AI RMF** functions [9][10][11][14]. *(Best practice.)*
- **Certification is a third-party, accredited process** governed by **ISO/IEC 42006:2025** (requirements for AIMS audit and certification bodies): Stage 1 and Stage 2 audits, surveillance, and a three-year cycle — mirroring ISO/IEC 27001 [8][12]. *(Best practice.)*
- **An AI inventory and a defined governance operating model are preconditions:** the AIMS scope (Cl. 4.3) cannot be set, nor controls applied, without knowing which AI systems exist and each organisation's **provider/deployer** role [1][8]. *(Best practice; supports legal obligation.)*
- **Board-level accountability** for AI is addressed by **ISO/IEC 38507:2022** (governance implications of AI for the governing body), which sits above the AIMS and informs Clause 5 leadership [8][13]. *(Best practice.)*

# Purpose

This document supports three tasks the parent `ai-governance-foundations` leaves open: (a) **building** an AIMS clause by clause (Clauses 4–10) and selecting Annex A controls with Annex B guidance; (b) **certifying** it (the PDCA cycle, the accredited audit process and ISO/IEC 42006); and (c) **using** the AIMS to operationalise and evidence EU AI Act obligations — especially the Art. 17 quality management system and the Art. 9–15 high-risk requirements — with a concrete **42001 ↔ AI Act control-mapping table**. It is written for AI governance leads, compliance officers, quality managers and engineering leaders. It presupposes `ai-governance-foundations` (framework landscape), `ai-act-foundations` (the law) and `ai-act-high-risk` (the high-risk duties this AIMS helps satisfy).

# Scope

**In scope:** The ISO/IEC 42001:2023 AIMS — the harmonised structure and Clauses 4–10 (context, leadership, planning incl. AI risk assessment, AI risk treatment and AI system impact assessment, support, operation, performance evaluation, improvement); Annex A controls and Annex B implementation guidance across the nine themes; the PDCA cycle; certification and the accredited audit process (ISO/IEC 42006); how 42001 operationalises the EU AI Act (Arts. 9–17) and complements the NIST AI RMF, ISO/IEC 23894 and ISO/IEC 42005; building an AI inventory and a governance operating model; an implementation roadmap and a 42001 ↔ AI Act control-mapping table.

**Out of scope (covered elsewhere):** The NIST AI RMF functions, OECD Principles and framework selection in general → `ai-governance-foundations`; the AI Act risk tiers, GPAI regime, penalties and timeline → `ai-act-foundations`; the high-risk classification and Art. 8–15/conformity-assessment mechanics in detail → `ai-act-high-risk`; GDPR DPIA methodology → `dpia-methodology`; model validation/monitoring method in depth → `ai-model-risk-management` (planned); AI audit methodology in depth → `ai-audit-methodology` (planned).

**Assumptions:** The reader has read `ai-governance-foundations` and `ai-act-foundations`. Full clause and control **text** is in the ISO/IEC standard itself, which is copyrighted and paywalled; this document describes structure and intent and must be read alongside the purchased standard, not as a substitute for it. Where an AI system processes personal data, the GDPR applies in parallel (see `privacy-engineering-foundations`, `dpia-methodology`).

# Definitions

*Shared terms (AI system, AIMS, AI governance, human oversight, trustworthy AI, conformity assessment, notified body, FRIA) are in `GLOSSARY.md`. Only 42001-specific terms are defined here; the table is kept short per sub-topic policy.*

| Term | Definition | Source |
|------|------------|--------|
| Harmonised structure (Annex SL) | The common high-level clause structure (Clauses 4–10), identical text and shared terms mandated for ISO management-system standards, enabling integration across ISO/IEC 42001, 27001, 9001 etc. | [8][19] |
| AI risk assessment | The Clause 6.1.2 process of identifying, analysing and evaluating risks related to the organisation's AI systems (drawing on ISO/IEC 23894 method). | [8][9] |
| AI risk treatment | The Clause 6.1.3 process of selecting risk-treatment options and determining which Annex A controls (and any additional controls) are necessary, recorded in a Statement of Applicability. | [8] |
| AI system impact assessment | The Clause 6.1.4 / Annex A process of assessing potential consequences of an AI system for individuals, groups and society across its life cycle (method detailed in ISO/IEC 42005:2025). | [8][10] |
| Statement of Applicability (SoA) | A documented statement of the Annex A controls the organisation has determined necessary (or excluded), with justification — the auditable bridge between risk treatment and controls. | [8] |
| Annex A control | A reference control listed in ISO/IEC 42001 Annex A, grouped under nine control areas (A.2–A.10); implementation guidance for each is in Annex B. | [8] |
| Surveillance audit | A periodic audit by the certification body between certification and recertification (typically annual) confirming the AIMS remains effective, per ISO/IEC 42006. | [12] |

# Background

Management-system standards are a mature EU/international compliance technology. ISO 9001 (quality, 1987) and later ISO/IEC 27001 (information security) established a repeatable pattern: define a scope, secure leadership, assess risks, select controls, operate, audit and improve — then have an **accredited certification body** attest conformity. From 2012 onward ISO required all such standards to share a common **harmonised structure** ("Annex SL"), so an organisation running one management system can bolt on another with minimal duplication [8][19].

AI created governance gaps those generic systems did not cover: data-driven behaviour that drifts, opacity, bias, and societal (not just organisational) impact. The response was a dedicated AI **management** standard. **ISO/IEC 42001:2023** was published in December 2023 as the first certifiable AIMS [8]. It does not stand alone: it is anchored in the **ISO/IEC SC 42** family — **ISO/IEC 22989** (concepts and terminology) [11], **ISO/IEC 23894** (AI risk-management guidance, itself an AI-specific application of ISO 31000) [9][18], and **ISO/IEC 42005** (AI system impact assessment) [10] — and is designed to interoperate with the **NIST AI RMF** [14]. Certification of AIMS is in turn governed by **ISO/IEC 42006:2025**, which sets requirements for the bodies that audit and certify [12].

The regulatory pull is the EU AI Act. Its high-risk chapter requires a **quality management system (Art. 17)** and a lifecycle **risk-management system (Art. 9)**, plus data governance, documentation, logging, transparency and human oversight (Arts. 10–15) [1]. **Harmonised European standards** under a Commission request to CEN-CENELEC will eventually confer a formal presumption of conformity; until they are cited in the Official Journal, ISO/IEC 42001 is the leading international AIMS and the practical interim vehicle [1][7]. In the **UK**, which has no horizontal AI statute and relies on a principles-based, regulator-led approach, 42001 serves as a voluntary governance yardstick alongside existing data-protection and equality law [4][5].

# Legal Framework

ISO/IEC 42001 is **not law**; it is a voluntary standard. The legal obligations it helps discharge arise elsewhere, principally the EU AI Act and the GDPR. This section states those obligations plainly; the standard's role is **best practice** that operationalises and evidences them.

- **EU AI Act (Regulation (EU) 2024/1689).** For high-risk systems the Act imposes a **risk-management system (Art. 9)**, **data governance (Art. 10)**, **technical documentation (Art. 11)**, **record-keeping/logging (Art. 12)**, **transparency to deployers (Art. 13)**, **human oversight (Art. 14)**, **accuracy/robustness/cybersecurity (Art. 15)** and a **quality management system (Art. 17)** [1]. An AIMS is the systematic means to plan, operate, evidence and continually improve these — but conformity is assessed against the Act, not the standard [1][3].
- **GDPR (Regulation (EU) 2016/679).** Where AI processes personal data, **accountability (Art. 5(2))**, **data protection by design/default (Art. 25)**, **security (Art. 32)** and **DPIAs (Art. 35)** apply in parallel; the AIMS impact-assessment process (Cl. 6.1.4) should be run together with the DPIA, not conflated with it [2].
- **Voluntary standard status.** ISO/IEC 42001 confers **no** automatic legal presumption of conformity; only **harmonised standards** cited in the Official Journal do so (Art. 40, developed by CEN-CENELEC) [1][7]. Certification is admissible evidence of due diligence, weighed alongside actual compliance [3][12].

## Relevant Articles

*These AI Act articles are stated fully in `ai-act-high-risk`; listed here only as the obligations the AIMS operationalises. GDPR articles apply where personal data is processed.*

| Article | Obligation (AIMS operationalises) | Source |
|---------|-----------------------------------|--------|
| AI Act Art. 9 | Continuous, lifecycle AI risk-management system. | [1] |
| AI Act Art. 10 | Data and data-governance (quality, representativeness, bias examination). | [1] |
| AI Act Art. 11 + Annex IV | Technical documentation demonstrating conformity. | [1] |
| AI Act Art. 12 | Automatic record-keeping (event logging) and traceability. | [1] |
| AI Act Art. 13 | Transparency and instructions for use to deployers. | [1] |
| AI Act Art. 14 | Human oversight (understand, monitor, intervene, override). | [1] |
| AI Act Art. 15 | Accuracy, robustness and cybersecurity. | [1] |
| AI Act Art. 17 | Quality management system for high-risk providers. | [1] |
| AI Act Arts. 25–27 | Value-chain roles; deployer duties; fundamental-rights impact assessment. | [1] |
| GDPR Art. 5(2) / Art. 25 / Art. 35 | Accountability; data protection by design/default; DPIA. | [2] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| AI Act Recital 1 | Purpose — trustworthy, human-centric AI protecting health, safety and fundamental rights (the values the AIMS serves). | [1] |
| AI Act Recital 27 | Names the trustworthy-AI principles (human oversight, robustness, privacy/data governance, transparency, non-discrimination, well-being, accountability) that Annex A controls implement. | [1] |
| AI Act Recital 81 area | A quality management system is central to high-risk provider compliance — the hook to which ISO/IEC 42001 maps. | [1] |

## Relevant Case Law

**Not Applicable.** ISO/IEC 42001 and its sibling standards are voluntary international standards, not statutes construed by courts; there is no case law interpreting them. The AI Act's high-risk provisions are not yet applicable (application dates fall in 2027–2028 as amended), so no CJEU judgment interprets Arts. 9–17 either. Interpretive weight rests on the Regulation's text, forthcoming Commission guidance and harmonised standards; for personal-data aspects, GDPR case law applies (see `gdpr-foundations`) [1][8]. Revisit once the high-risk provisions apply and litigation emerges.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **European Commission:** frames AI Act conformity as a systematic, lifecycle undertaking and points high-risk providers toward a **quality management system (Art. 17)** and harmonised standards as the route to conformity; it has issued a **standardisation request to CEN-CENELEC** to develop European standards operationalising Arts. 9–15 [3][7]. Until those are cited in the Official Journal, providers rely on the Regulation directly, with ISO/IEC 42001 as the leading international AIMS [1][3]. *(Regulatory interpretation.)*
- **CEN-CENELEC (JTC 21):** is developing the harmonised standards; some are expected to build on or align with the ISO/IEC SC 42 family (including 42001), but a European harmonised standard is a distinct instrument from an ISO standard and only the former confers the Art. 40 presumption [7]. *(Regulatory interpretation + best practice — track citation.)*
- **ICO (UK):** treats governance, accountability and documentation as central to lawful AI, and expects organisations to assess risks (including bias and explainability) and embed data protection by design — obligations the AIMS helps evidence, framed as existing-law duties rather than new AI-specific ones [4]. *(Regulatory interpretation.)*
- **UK Government (DSIT):** the "pro-innovation approach to AI regulation" declines a horizontal statute in favour of five cross-sector principles applied by existing regulators, making voluntary standards such as ISO/IEC 42001 the practical UK governance baseline [5]. *(Regulatory interpretation.)*
- **Interpretive caution:** certification to ISO/IEC 42001 is **evidence of diligence, not a legal safe harbour**; a certificate attests that an AIMS meets the standard's requirements, not that any given AI system complies with the AI Act or GDPR — regulators assess actual compliance [3][12]. *(Regulatory interpretation.)*

# Technical Considerations

This section sets out the AIMS clause by clause, then the Annex A/B controls and the PDCA cycle. Unless an AI Act article is cited, requirements described are **standard requirements (best practice)**, not legal obligations.

**Clause 4 — Context of the organisation.** Determine external/internal issues relevant to AI (4.1); identify **interested parties** and their needs — users, affected persons, regulators, supply chain (4.2); define the **AIMS scope** (4.3), which forces an explicit statement of which AI systems, roles (provider/deployer) and life-cycle stages are covered; and establish the AIMS itself (4.4) [8]. Scope-setting is where the **AI inventory** (below) becomes indispensable. *(Best practice.)*

**Clause 5 — Leadership.** Top management must demonstrate commitment, establish an **AI policy** aligned to organisational purpose and trustworthy-AI values (the OECD AI Principles supply the recognised values baseline), and assign **roles, responsibilities and authorities** (5.1–5.3) [8][6]. Board-level duties are informed by **ISO/IEC 38507:2022**, which addresses the governance implications of AI for the governing body and sits above the AIMS [13]. *(Best practice.)*

**Clause 6 — Planning (the AI-specific core).** Three linked processes:

- **6.1.2 AI risk assessment** — identify, analyse and evaluate AI risks (to the organisation *and* to individuals/society), applying the **ISO/IEC 23894** method (an AI-specific application of ISO 31000) [8][9][18].
- **6.1.3 AI risk treatment** — select treatment options and determine which **Annex A controls** are necessary, recording the decision and any exclusions in a **Statement of Applicability** [8].
- **6.1.4 AI system impact assessment** — assess consequences for individuals, groups and society across the life cycle, using the **ISO/IEC 42005** method; this is distinctive to AI management systems and aligns with the AI Act **FRIA (Art. 27)** and the GDPR **DPIA (Art. 35)** [8][10][1][2].

Clause 6 also sets **AI objectives** and plans changes [8]. *(Best practice; the risk-management and impact duties mirror AI Act Arts. 9 and 27.)*

**Clause 7 — Support.** Provide **resources**, ensure **competence** and **awareness** (feeding AI-literacy duties), manage **communication**, and control **documented information** (7.1–7.5) — the standard's documentation backbone, which the AI Act's Art. 11 technical documentation can be built upon [8][1]. *(Best practice.)*

**Clause 8 — Operation (the "Do").** Plan and control the processes needed to meet requirements, and **operationally re-run** the AI risk assessment, risk treatment and AI system impact assessment (8.1–8.4) whenever changes warrant [8]. *(Best practice.)*

**Clause 9 — Performance evaluation (the "Check").** Monitor, measure, analyse and evaluate the AIMS (9.1); conduct **internal audits** (9.2); and hold a **management review** (9.3) [8]. This is where drift, incident and oversight metrics are examined. *(Best practice.)*

**Clause 10 — Improvement (the "Act").** Drive **continual improvement** and handle **nonconformities with corrective action** (10.1–10.2) [8]. *(Best practice.)*

**Annex A controls / Annex B guidance (nine areas).** Clause 6.1.3 draws controls from **Annex A**, whose reference controls are grouped under nine areas; **Annex B** gives implementation guidance for each [8]:

1. **AI policies** — establishing, aligning and reviewing AI policy.
2. **Internal organisation** — roles, responsibilities and a route to raise concerns.
3. **Resources for AI systems** — documenting data, tooling, compute/system and human resources.
4. **Assessing impacts of AI systems** — the impact-assessment process and its documentation (links to ISO/IEC 42005).
5. **AI system life cycle** — responsible-development objectives and life-cycle processes (requirements, design, development, verification/validation, deployment, operation/monitoring, technical documentation, **event logging**).
6. **Data for AI systems** — data management, acquisition, quality, provenance and preparation.
7. **Information for interested parties** — system documentation and information for users, external reporting and incident communication.
8. **Use of AI systems** — responsible-use objectives and processes.
9. **Third-party and customer relationships** — allocating responsibilities across suppliers and customers in the AI value chain.

These nine areas correspond directly to the AI Act requirement clusters (data governance, documentation, logging, transparency, oversight, value chain), which is why the AIMS is such an efficient operationalisation vehicle [1][8].

**PDCA mapping.** **Plan** = Clauses 4–7; **Do** = Clause 8; **Check** = Clause 9; **Act** = Clause 10 [8]. Because the structure is the harmonised Annex SL structure, an organisation with ISO/IEC 27001 can **integrate** rather than rebuild — shared context, leadership, competence, documented-information, internal-audit and management-review machinery [8][19]. *(Best practice.)*

# Hosting Considerations

- **Scope and role drive whether an AIMS is needed.** Hosting an AI system does not by itself mandate ISO/IEC 42001, but where a host **brands**, **materially modifies** or otherwise takes **provider-level** responsibility, provider AI Act duties (and a broader AIMS scope) attach; the Clause 4.3 scope statement must capture this [1][8]. *(Best practice; the role determination is a legal question under the AI Act.)*
- **Cloud providers increasingly hold 42001 certification** for named AI services; deployers should use the provider's Statement of Applicability and shared-responsibility documentation to map which Annex A controls the provider covers and which remain the deployer's own — mirroring the ISO/IEC 27001 shared-responsibility pattern [8][12]. *(Best practice.)*
- **Event logging and documented information** (Annex A life-cycle and information areas) must be retained in the hosting environment to satisfy AI Act Art. 12 logging while honouring GDPR storage-limitation and security (see `privacy-engineering-foundations`) [1][2][8]. *(Best practice; Art. 12 logging is a legal obligation for high-risk providers.)*

# Game Hosting Considerations

- **Most game AI is minimal-risk**, so a full certified AIMS is rarely required; a **proportionate AIMS scope** (Cl. 4.3) can be limited to the higher-impact systems (e.g. generative content tools, recommendation/matchmaking that affects access, any biometric/emotion features) [1][8]. *(Best practice.)*
- **Annex A "use of AI" and "information for interested parties"** map neatly onto player-facing transparency for AI chatbots/companions and generative features (AI Act Art. 50 transparency, detailed in `ai-act-foundations`) [1][8]. *(Best practice; Art. 50 disclosure is a legal obligation.)*
- **Impact assessment for minors.** Where features are likely to be accessed by children, the Clause 6.1.4 AI system impact assessment should be run together with the UK Children's Code / GDPR DPIA analysis rather than separately [2][10]. *(Best practice.)*

# AI Considerations

*This document is itself about AI governance; the "AI Considerations" here concern how the AIMS interlocks with the AI-regulation and standards stack.*

- **42001 is the connective tissue of the SC 42 family.** It **references** ISO/IEC 22989 for terminology, invokes ISO/IEC 23894 as the risk-management method for Clause 6, and points to ISO/IEC 42005 for the impact-assessment method — so adopting 42001 pulls in a coherent toolset rather than a single document [8][9][10][11]. *(Best practice.)*
- **Complementarity with the NIST AI RMF.** The AIMS supplies the auditable management shell; the NIST AI RMF **Govern/Map/Measure/Manage** functions and its Playbook supply concrete, function-level actions that populate Clauses 6, 8 and 9. Organisations commonly run both, crosswalking RMF outcomes to Annex A controls [8][14][15][17]. *(Best practice.)*
- **Generative AI.** For systems built on foundation models, the NIST **Generative AI Profile (AI 600-1)** names GenAI-specific risks (confabulation, data leakage, harmful bias, CBRN/cyber uplift, content-integrity) that should feed the Clause 6 AI risk assessment and the Annex A third-party-relationship controls covering upstream model providers [16]. *(Best practice.)*
- **Integration, not proliferation.** Because 42001 shares the harmonised structure with ISO/IEC 27001 and ISO 9001, the AIMS should be built **into** the existing management-system estate; a separate, parallel AI programme wastes effort and creates conflicting audit trails [8][19]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** (AI Act/GDPR duty) / **BEST PRACTICE** (standard/consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

1. **Build the AI inventory first.** Catalogue every AI system with its purpose, life-cycle stage, **provider/deployer role**, AI Act tier and personal-data footprint. Without it you cannot set AIMS scope (Cl. 4.3) or select controls. *(BEST PRACTICE; supports OBLIGATION.)* [1][8]
2. **Set a defensible AIMS scope (Cl. 4.3)** covering the systems and roles that matter; document exclusions and their justification. *(BEST PRACTICE.)* [8]
3. **Secure leadership and publish an AI policy (Cl. 5)**; assign a named senior owner and a governance body; use ISO/IEC 38507 to brief the board. *(BEST PRACTICE; OBLIGATION-adjacent via AI Act Art. 17 and GDPR Art. 5(2).)* [8][13][1][2]
4. **Run the Clause 6 planning trio:** AI risk assessment (ISO/IEC 23894), AI risk treatment with a **Statement of Applicability**, and AI system impact assessment (ISO/IEC 42005), aligned to the AI Act FRIA and the GDPR DPIA. *(BEST PRACTICE; OBLIGATION where Art. 9/Art. 27/Art. 35 apply.)* [8][9][10][1][2]
5. **Select Annex A controls with Annex B guidance** across all nine areas; justify any excluded control. *(BEST PRACTICE.)* [8]
6. **Wire documentation and event logging in by construction (Cl. 7.5; Annex A life-cycle/information areas)** so AI Act Art. 11 technical documentation and Art. 12 logs are by-products. *(BEST PRACTICE; OBLIGATION for high-risk via Arts. 11–12.)* [1][8]
7. **Operate, monitor and audit (Cl. 8–9):** metrics on bias, drift, incidents and oversight; internal audit; management review. *(BEST PRACTICE.)* [8]
8. **Integrate, don't duplicate:** map Annex A onto existing ISO/IEC 27001 controls and reuse the shared management machinery. *(EDITORIAL RECOMMENDATION.)* [8][19]
9. **Crosswalk to the NIST AI RMF** to source concrete actions, and apply the GenAI Profile to generative systems. *(BEST PRACTICE.)* [14][16][17]
10. **Pursue accredited certification where it adds market or regulatory value,** using a certification body accredited under ISO/IEC 42006; treat the certificate as evidence, not a safe harbour. *(EDITORIAL RECOMMENDATION.)* [12][3]

## Control-mapping table — ISO/IEC 42001 ↔ EU AI Act

*Best-practice mapping (not an official crosswalk). AI Act articles are legal obligations for high-risk systems; the AIMS elements are voluntary means of meeting and evidencing them [1][8].*

| AI Act obligation (high-risk) | ISO/IEC 42001 AIMS element | Notes |
|-------------------------------|----------------------------|-------|
| Art. 9 — risk-management system | Cl. 6.1.2 AI risk assessment + 6.1.3 treatment; Cl. 8.2–8.3 operation; ISO/IEC 23894 method | Continuous lifecycle loop; re-run on change [1][8][9] |
| Art. 10 — data & data governance | Annex A **data-for-AI** area (management, quality, provenance, preparation) | Bias examination; controlled special-category use [1][8] |
| Art. 11 + Annex IV — technical documentation | Cl. 7.5 documented information; Annex A **life-cycle** (technical documentation) | Generate as pipeline output [1][8] |
| Art. 12 — record-keeping/logging | Annex A **life-cycle** (event logging) | Traceability across the system's life [1][8] |
| Art. 13 — transparency to deployers | Annex A **information for interested parties** (documentation/info for users) | Instructions for use [1][8] |
| Art. 14 — human oversight | Annex A **internal organisation** + **use of AI**; Cl. 5.3 roles/authorities | Understand/monitor/intervene/override [1][8] |
| Art. 15 — accuracy/robustness/cybersecurity | Annex A **life-cycle** (verification/validation); Cl. 9 monitoring; integrate ISO/IEC 27001 | AI-specific threat hardening [1][8][19] |
| Art. 17 — quality management system | The **whole AIMS** (Cl. 4–10 on PDCA) | Closest single mapping [1][8] |
| Art. 27 — fundamental-rights impact assessment | Cl. 6.1.4 / Annex A **impact assessment**; ISO/IEC 42005 | Run with GDPR DPIA (Art. 35) [1][8][10][2] |
| Arts. 25–26 — value-chain & deployer duties | Annex A **third-party & customer relationships** | Allocate responsibilities across the chain [1][8] |

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | AIMS scope (Cl. 4.3) set too narrowly, omitting high-impact systems | Medium | High | ISO/IEC 42001 Cl. 4.3 [8] | Drive scope from a complete AI inventory; review at management review | Low |
| R2 | Treating 42001 certification as a legal safe harbour for the AI Act | Medium | High | Certificate is evidence, not conformity [3][12] | Map controls to actual Art. 9–17 duties; keep audit trail | Low |
| R3 | Clause 6 planning done once, not re-run on change | Medium | High | AI Act Art. 9; ISO/IEC 42001 Cl. 8 [1][8] | Trigger re-assessment on material change; scheduled reviews | Medium |
| R4 | AI system impact assessment skipped or conflated with DPIA | Medium | High | Cl. 6.1.4; ISO/IEC 42005; GDPR Art. 35 [8][10][2] | Run distinct-but-linked impact assessment and DPIA | Low |
| R5 | Annex A controls selected without a justified Statement of Applicability | Medium | Medium | ISO/IEC 42001 Cl. 6.1.3 [8] | Document control decisions and exclusions; auditor-ready SoA | Low |
| R6 | Documentation/logging retrofitted, not built in | Medium | High | AI Act Arts. 11–12 [1] | Auto-generate technical docs and event logs from the pipeline | Low |
| R7 | Parallel AI programme duplicating an existing ISMS/QMS | Medium | Medium | Shared Annex SL structure [8][19] | Integrate the AIMS into the existing management-system estate | Low |
| R8 | Certification body not accredited under ISO/IEC 42006 | Low | Medium | ISO/IEC 42006:2025 [12] | Select an accredited body; verify accreditation scope | Low |
| R9 | Assuming 42001 gives an AI Act presumption of conformity | Medium | Medium | Only harmonised standards do (Art. 40) [1][7] | Track CEN-CENELEC citation in the OJ; design to drafts | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory & context (Cl. 4):** Build the AI system inventory (purpose, role, tier, data); define AIMS scope and interested parties. *Effort:* Medium. *Depends on:* `ai-act-foundations` triage; `ai-governance-foundations` operating model.
- **Phase 1 — Leadership & policy (Cl. 5):** Assign accountable ownership and a governance body; approve the AI policy; brief the board using ISO/IEC 38507. *Effort:* Low–Medium.
- **Phase 2 — Planning (Cl. 6):** AI risk assessment (ISO/IEC 23894); risk treatment + Statement of Applicability; AI system impact assessment (ISO/IEC 42005) linked to FRIA/DPIA; set AI objectives. *Effort:* High.
- **Phase 3 — Support & controls (Cl. 7; Annex A):** Competence/awareness, communication, documented information; implement selected Annex A controls with Annex B guidance across the nine areas. *Effort:* High.
- **Phase 4 — Operate & evaluate (Cl. 8–9):** Run controls; monitor bias/drift/incidents/oversight; internal audit; management review. *Effort:* High (then ongoing).
- **Phase 5 — Improve & certify (Cl. 10; ISO/IEC 42006):** Corrective action; Stage 1 (documentation) and Stage 2 (implementation) certification audits; surveillance and three-year recertification where certification adds value. *Effort:* High.
- **Phase 6 — Continual improvement:** Track CEN-CENELEC harmonised-standard citation, NIST RMF and ISO SC 42 updates; re-run planning on material change. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No AIMS; AI governance ad hoc; no inventory or scope. | No AI inventory; no AI policy. |
| 2 | Managed | Inventory and AIMS scope defined; leadership and AI policy in place. | Cl. 4–5 addressed; owner assigned. |
| 3 | Defined | Clause 6 planning operating; Annex A controls selected with a Statement of Applicability. | Risk assessment, treatment + SoA, impact assessment done. |
| 4 | Quantitatively Managed | Controls operated and measured; internal audit and management review running with metrics. | KPIs on bias/drift/oversight; audit records. |
| 5 | Optimising | Integrated AIMS (with ISMS/QMS); accredited certification; continual improvement and AI Act mapping maintained. | ISO/IEC 42001 certified; 42001↔AI Act map; recertification cycle. |

# Audit Questions

1. Is there a complete AI inventory, and does it drive a defensible AIMS scope (Cl. 4.3)? *([8]; supports AI Act Art. 17 [1].)*
2. Has top management established an AI policy and assigned roles/authorities (Cl. 5)? *(Cl. 5 [8]; AI Act Art. 17; GDPR Art. 5(2) [1][2].)*
3. Are the Clause 6 AI risk assessment, risk treatment (with a Statement of Applicability) and AI system impact assessment documented and current? *([8][9][10]; AI Act Arts. 9, 27 [1].)*
4. Which Annex A controls were selected or excluded, and is each decision justified in the SoA with Annex B guidance applied? *([8].)*
5. Are documentation and event logging generated by construction to satisfy AI Act Arts. 11–12? *([8]; Arts. 11–12 [1].)*
6. Do monitoring, internal audit and management review (Cl. 9) operate, with metrics on bias, drift, incidents and oversight? *([8].)*
7. How is the AIMS integrated with an existing ISO/IEC 27001 ISMS to avoid duplication? *([8][19].)*
8. Is the AI system impact assessment run together with the GDPR DPIA and any AI Act FRIA? *([10][2]; AI Act Art. 27 [1].)*
9. If certified, is the certification body accredited under ISO/IEC 42006, and is the certificate treated as evidence rather than a safe harbour? *([12][3].)*

# Implementation Checklist

- [ ] AI system inventory built (purpose, provider/deployer role, tier, personal-data footprint).
- [ ] AIMS scope, context and interested parties defined (Cl. 4).
- [ ] AI policy approved; senior owner and governance body assigned; board briefed (Cl. 5; ISO/IEC 38507).
- [ ] AI risk assessment completed (ISO/IEC 23894) (Cl. 6.1.2).
- [ ] AI risk treatment done; Statement of Applicability produced (Cl. 6.1.3).
- [ ] AI system impact assessment completed (ISO/IEC 42005), linked to FRIA/DPIA (Cl. 6.1.4).
- [ ] Annex A controls implemented with Annex B guidance across the nine areas.
- [ ] Documentation and event logging generated by construction (Cl. 7.5; life-cycle controls).
- [ ] Monitoring, internal audit and management review operating (Cl. 8–9).
- [ ] Corrective action and continual improvement process running (Cl. 10).
- [ ] AIMS integrated with existing ISMS/QMS (shared Annex SL machinery).
- [ ] 42001 ↔ AI Act control map maintained; CEN-CENELEC harmonised-standard watch-list kept.
- [ ] Certification path decided; certification body accreditation (ISO/IEC 42006) verified where pursued.

# References

*All external links verified HTTP 200 on 2026-07-11 (`sources_verified`) using `curl -L -A "Mozilla/5.0"`. ISO landing pages were checked for HTTP status and the exact edition/title confirmed from the page `<title>` (ISO/IEC 42001:2023; 23894:2023; 42005:2025; 42006:2025; 38507:2022; 22989:2022). Full clause and control text is in the copyrighted standards themselves.*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** EUR-Lex, ELI (Arts. 9–17, 25–27, Annex IV). https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [2] **Regulation (EU) 2016/679 (GDPR).** EUR-Lex, ELI (parallel application; Arts. 5(2), 25, 32, 35). https://eur-lex.europa.eu/eli/reg/2016/679/oj

## Regulatory Guidance

- [3] **Regulatory framework on AI / AI Act.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai
- [4] **Artificial intelligence — guidance for organisations.** ICO (UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/artificial-intelligence/
- [5] **A pro-innovation approach to AI regulation.** UK Government (DSIT), GOV.UK. https://www.gov.uk/government/publications/a-pro-innovation-approach-to-ai-regulation
- [6] **Recommendation of the Council on Artificial Intelligence (OECD/LEGAL/0449).** OECD Legal Instruments (adopted 2019; amended 3 May 2024) — trustworthy-AI values baseline the AIMS serves. https://legalinstruments.oecd.org/en/instruments/OECD-LEGAL-0449
- [7] **CEN-CENELEC — Artificial Intelligence (harmonised standards under the Commission's AI Act standardisation request).** CEN-CENELEC. https://www.cencenelec.eu/areas-of-work/cen-cenelec-topics/artificial-intelligence/

## Standards

- [8] **ISO/IEC 42001:2023 — Information technology — Artificial intelligence — Management system (AIMS).** ISO/IEC (Clauses 4–10; Annex A controls; Annex B guidance). https://www.iso.org/standard/42001
- [9] **ISO/IEC 23894:2023 — Artificial intelligence — Guidance on risk management.** ISO/IEC (method for the Clause 6 AI risk assessment). https://www.iso.org/standard/77304.html
- [10] **ISO/IEC 42005:2025 — Artificial intelligence — AI system impact assessment.** ISO/IEC (method for the Clause 6.1.4 impact assessment). https://www.iso.org/standard/42005
- [11] **ISO/IEC 22989:2022 — Artificial intelligence — Concepts and terminology.** ISO/IEC (terminology referenced by 42001). https://www.iso.org/standard/74296.html
- [12] **ISO/IEC 42006:2025 — Requirements for bodies providing audit and certification of AI management systems.** ISO/IEC (accreditation basis for AIMS certification bodies). https://www.iso.org/standard/42006
- [13] **ISO/IEC 38507:2022 — Governance of IT — Governance implications of the use of artificial intelligence by organizations.** ISO/IEC (board/governing-body duties above the AIMS). https://www.iso.org/standard/56641.html
- [14] **AI Risk Management Framework (AI RMF 1.0) — overview.** NIST. https://www.nist.gov/itl/ai-risk-management-framework
- [15] **Artificial Intelligence Risk Management Framework (AI RMF 1.0), NIST AI 100-1** (Jan 2023). NIST. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf
- [16] **AI RMF: Generative Artificial Intelligence Profile, NIST AI 600-1** (26 July 2024). NIST. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf
- [17] **NIST AI RMF Playbook.** NIST AI Resource Center (AIRC). https://airc.nist.gov/airmf-resources/playbook/
- [18] **ISO 31000:2018 — Risk management — Guidelines.** ISO (the general risk-management basis ISO/IEC 23894 applies to AI). https://www.iso.org/standard/65694.html
- [19] **ISO/IEC 27001:2022 — Information security management systems.** ISO/IEC (shared harmonised structure; integration target for the AIMS). https://www.iso.org/standard/27001

## Academic Sources

Not Applicable — this implementation guidance relies on primary legislation, regulator guidance and recognised standards. Academic critique of AI management systems and AI audit will be cited in the planned spin-offs (`ai-audit-methodology`, `ai-model-risk-management`).

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- ISO — "AI management systems: what businesses need to know" (ISO/IEC 42001 explainer). https://www.iso.org/artificial-intelligence
- NIST AI Resource Center (AIRC) — Playbook and framework crosswalks. https://airc.nist.gov/airmf-resources/playbook/

# Related Documents

- `ai-governance-foundations` — **parent**; the framework landscape (ISO/IEC 42001, NIST AI RMF, OECD Principles) this document details for 42001 (**prerequisite reading**).
- `ai-act-foundations` — the EU AI Act overview, risk tiers and timeline (the law the AIMS operationalises).
- `ai-act-high-risk` — the high-risk Arts. 8–15 duties and the Art. 17 QMS that the 42001 controls map onto (**cross-reference, not duplicated here**).
- `privacy-engineering-foundations` / `dpia-methodology` — DPbDD, security and DPIA that run alongside the AIMS data and impact-assessment controls.
- `ai-model-risk-management` — model validation and monitoring method (planned).
- `ai-audit-methodology` — AI audit and assurance method, incl. AIMS certification audit (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Deep-dive on implementing ISO/IEC 42001:2023 (AIMS): the harmonised Clauses 4–10, the Clause 6 planning trio (AI risk assessment, risk treatment + Statement of Applicability, AI system impact assessment), Annex A controls and Annex B guidance across the nine areas, the PDCA cycle, certification and ISO/IEC 42006, and a 42001 ↔ AI Act control-mapping table. **Standards editions live-verified from ISO page titles on 2026-07-11: ISO/IEC 42001:2023, 23894:2023, 42005:2025, 42006:2025, 38507:2022, 22989:2022; NIST AI RMF 1.0 + AI 600-1 (26 Jul 2024).** All external links checked HTTP 200 on 2026-07-11. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved via autonomous backlog loop (Cluster A); passed full QA suite; frozen in release 0.15.0. | Human reviewer (loop-authorised) |
