---
id: dpia-methodology
title: "Data Protection Impact Assessments: Methodology"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU, UK]
topic: Privacy Engineering
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [privacy-engineering-foundations, gdpr-foundations, uk-gdpr-foundations, ai-act-foundations, ai-act-high-risk, compliance-operations-foundations]
tags: [dpia, article-35, article-36, prior-consultation, wp248, high-risk, fria, records-of-processing, privacy-engineering]
legal_basis: Regulation (EU) 2016/679, Articles 35 & 36
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dpia-methodology |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**.

# Executive Summary

A **Data Protection Impact Assessment (DPIA)** is the GDPR's principal instrument for assessing, in advance, the risks that a processing operation poses to the rights and freedoms of natural persons, and for demonstrating that those risks have been managed. Its legal anchor is **Article 35 GDPR**, reinforced by **Article 36 (prior consultation)** [1]. This document is the methodology layer beneath `privacy-engineering-foundations`, which introduces the Article 35 trigger at a foundational level; here we set out **when a DPIA is mandatory, how to screen for it, how to run one step by step, and how to sustain it as an operational capability**.

A DPIA is **mandatory** where processing is "likely to result in a high risk" (Art. 35(1)); Article 35(3) lists three cases that always qualify, and each supervisory authority must publish its own **Article 35(4) list** of operations requiring a DPIA [1][7]. The Article 29 Working Party guidelines **WP248 rev.01** — formally endorsed by the EDPB — supply a **nine-criteria test**: as a rule of thumb, processing meeting **two or more** criteria is likely high risk and needs a DPIA [4][5][7]. The **minimum statutory content** of a DPIA is fixed by Article 35(7): a systematic description of the processing, an assessment of **necessity and proportionality**, an assessment of the **risks**, and the **measures** to mitigate them [1].

Three conclusions dominate. First, the DPIA is an **accountability obligation, not a form-filling exercise** — it must be done *before* processing and *reviewed* when risk changes (Art. 35(1), 35(11)) [1]. Second, if residual risk remains high after mitigation, the controller **must consult the supervisory authority** before proceeding (Art. 36) [1][8]. Third, the DPIA is becoming the **hub of a family of assessments** — it dovetails with the AI Act **Article 27 Fundamental Rights Impact Assessment (FRIA)** and with the **Article 30 records of processing** [1][2].

# Key Takeaways

- A DPIA is **legally required before** processing "likely to result in a high risk" to rights and freedoms (Art. 35(1)); it must be done at the design stage, not retrospectively [1]. *(Legal obligation.)*
- **Article 35(3)** names three cases that always require a DPIA: systematic and extensive **automated evaluation/profiling** with significant effects; **large-scale** processing of special-category or criminal-offence data; and **systematic monitoring of a publicly accessible area** on a large scale [1][7]. *(Legal obligation.)*
- Each supervisory authority must publish an **Article 35(4) "blacklist"**; the ICO's list adds **ten** operation types (e.g., innovative technology, denial of service, large-scale profiling, biometrics, genetic data, data matching, invisible processing, tracking, targeting of children, risk of physical harm) [1][7]. *(Legal obligation, as specified by the SA.)*
- **WP248 rev.01** (endorsed by the EDPB) gives **nine risk criteria**; meeting **two or more** ordinarily indicates a DPIA is needed, though a single criterion can suffice [4][5][7]. *(Regulatory interpretation.)*
- **Article 35(7)** fixes the minimum content: systematic **description**, **necessity & proportionality** assessment, **risk** assessment, and **mitigation** measures [1]. *(Legal obligation.)*
- The **DPO must be consulted** (Art. 35(2)); where appropriate, so must **data subjects** (Art. 35(9)); the DPO also **monitors** DPIA performance (Art. 39(1)(c)) [1]. *(Legal obligation.)*
- If residual risk stays high, **prior consultation with the supervisory authority is mandatory** (Art. 36); the authority responds within **8 weeks, extendable by 6** [1][8]. *(Legal obligation.)*
- A DPIA must be **reviewed** when the risk represented by processing changes (Art. 35(11)); it is a living document, not a one-off [1][6]. *(Legal obligation.)*
- The DPIA **interlocks** with the AI Act **Art. 27 FRIA** and the **Art. 30 RoPA**; the standards **ISO/IEC 29134** (PIA) and **ISO/IEC 42005** (AI system impact assessment) provide auditable process structure [1][2][10][11]. *(Best practice grounded in obligation.)*

# Purpose

This document gives privacy, engineering, product and legal teams an **evidence-based, repeatable methodology** for deciding whether a DPIA is required, conducting it to the Article 35(7) standard, escalating to prior consultation where necessary, and operating DPIAs at scale across a portfolio of processing. It operationalises the Article 35 trigger described in `privacy-engineering-foundations` and supports DPIA integration into the SDLC, the AI Act conformity workstream, and the accountability evidence base.

# Scope

**In scope:** The Article 35 DPIA obligation and screening/threshold assessment; the Article 35(3) mandatory cases and Article 35(4)/(5) national lists; the WP248 rev.01 nine-criteria "likely high risk" test; the end-to-end DPIA process (describe → necessity & proportionality → risk assessment → mitigation → sign-off → review); Article 36 prior consultation; the DPO and data-subject roles; links to the AI Act Art. 27 FRIA and the Art. 30 records; ICO guidance and template; a practical methodology and maturity view.

**Out of scope (covered elsewhere or in the backlog):** The DPbDD and Art. 32 security controls a DPIA relies on → `privacy-engineering-foundations`; privacy threat-modelling techniques (LINDDUN) that feed the risk step → `privacy-threat-modelling` (planned); anonymisation/re-identification analysis → `anonymisation-techniques` (planned); the full AI Act high-risk regime and FRIA mechanics → `ai-act-high-risk`; running the wider accountability programme → `compliance-operations-foundations`.

**Assumptions:** The reader has read `gdpr-foundations` (principles, accountability, high-risk concept) and `privacy-engineering-foundations` (DPbDD, TOMs). "Controller", "processor", "special category data" and "RoPA" carry their `GLOSSARY.md` meanings.

# Definitions

*Shared terms (controller, processor, personal data, special category data, RoPA, accountability, FRIA) are defined in `GLOSSARY.md`. Only DPIA-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Data Protection Impact Assessment (DPIA) | An assessment of the impact of envisaged processing operations on the protection of personal data, required where a type of processing is likely to result in a high risk to the rights and freedoms of natural persons (Art. 35(1)). | [1] |
| Screening / threshold assessment | The preliminary step of determining whether the mandatory Art. 35(3) cases, an SA Art. 35(4) list entry, or the WP248 criteria are met, such that a DPIA is required. | [1][7] |
| "Likely to result in a high risk" | The threshold triggering a DPIA; assessed against the nature, scope, context and purposes of processing, aided by the WP248 nine criteria. | [1][4][7] |
| Article 35(4) list ("blacklist") | The list, published by each supervisory authority, of processing operations that require a DPIA. | [1][7] |
| Article 35(5) list ("whitelist") | An optional SA list of processing operations that do **not** require a DPIA. | [1] |
| Prior consultation | The Art. 36 duty to consult the supervisory authority before processing where a DPIA indicates a high residual risk that the controller cannot mitigate. | [1][8] |
| Residual risk | The level of risk remaining after planned mitigation measures are applied; determines whether Art. 36 consultation is triggered. | [1][8] |
| Necessity and proportionality | The Art. 35(7)(b) assessment of whether the processing is necessary for, and proportionate to, its purpose(s) — a lawfulness test distinct from the security-risk assessment. | [1] |

# Background

Before the GDPR, EU data protection relied on a **prior-notification** model: controllers notified processing to the regulator. The GDPR abolished general notification and replaced it with a **risk-based accountability** model in which the controller itself must identify and manage high-risk processing (Recital 89) [1]. The **DPIA** is the centrepiece of that shift — a structured, documented, forward-looking risk assessment that the controller performs, retains and can produce on demand (Recital 84) [1].

The concept did not appear from nowhere. **Privacy Impact Assessments (PIAs)** had been practised for years in Canada, Australia, the UK (the ICO ran a PIA code from 2007) and elsewhere, and were codified internationally in **ISO/IEC 29134** [10]. The GDPR "hardened" the PIA into a **statutory** instrument with mandatory triggers, minimum content and an escalation route to the regulator. The Article 29 Working Party issued **WP248** in 2017, revised as **WP248 rev.01**, to explain when processing is "likely to result in a high risk"; the EDPB **endorsed** these guidelines on becoming operational in 2018, so they remain the authoritative interpretive source [4][5]. The instrument continues to spread: the **AI Act** (2024) introduced a parallel **Fundamental Rights Impact Assessment** for certain high-risk AI deployers, expressly designed to sit alongside the DPIA [2].

# Legal Framework

The DPIA regime lives in **Chapter IV, Section 3 of the GDPR (Articles 35–36)**, supported by Articles 30 (records) and 39 (DPO tasks) and by Recitals 84 and 89–96 [1]. The obligation rests on the **controller**.

- **Article 35(1)** — where a type of processing, in particular **using new technologies**, is **likely to result in a high risk** to the rights and freedoms of natural persons, taking account of the nature, scope, context and purposes, the controller **shall, prior to the processing, carry out a DPIA** [1].
- **Article 35(2)** — the controller **shall seek the advice of the DPO**, where designated [1].
- **Article 35(3)** — a DPIA is **required in particular** in three cases: (a) systematic and extensive **evaluation** based on automated processing, including profiling, on which decisions producing **legal or similarly significant effects** are based; (b) processing **on a large scale** of **special categories** (Art. 9(1)) or **criminal-offence** data (Art. 10); (c) **systematic monitoring of a publicly accessible area** on a large scale [1].
- **Article 35(4)–(6)** — each supervisory authority **shall publish a list** of operations requiring a DPIA (the "blacklist"), **may publish** a list of operations not requiring one, and must run cross-border lists through the **consistency mechanism** [1].
- **Article 35(7)** — the DPIA **shall contain at least**: (a) a systematic **description** of the processing and its purposes; (b) an assessment of the **necessity and proportionality**; (c) an assessment of the **risks** to rights and freedoms; and (d) the **measures** envisaged to address the risks (safeguards, security, mechanisms to demonstrate compliance) [1].
- **Article 35(9)** — where appropriate, the controller **shall seek the views of data subjects** or their representatives [1].
- **Article 35(10)–(11)** — a limited exemption applies where a DPIA-equivalent assessment was already made at the **legislative** stage; and the controller **shall review** whether processing is performed in line with the DPIA, at least when the **risk changes** [1].
- **Article 36** — where a DPIA indicates a **high residual risk** absent mitigation, the controller **shall consult** the supervisory authority **before** processing; the authority responds within **8 weeks (extendable by 6)** [1].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 24 | Controller's general duty to implement, review and update appropriate measures (context for DPIA). | [1] |
| Art. 25 | Data protection by design and by default — DPIA outputs feed DPbDD (see `privacy-engineering-foundations`). | [1] |
| Art. 30 | Records of processing activities (RoPA) — the inventory from which DPIA candidates are screened. | [1] |
| Art. 35(1) | Obligation to carry out a DPIA prior to high-risk processing. | [1] |
| Art. 35(2) | Seek the DPO's advice. | [1] |
| Art. 35(3) | The three mandatory-DPIA cases. | [1] |
| Art. 35(4)–(6) | SA lists (blacklist/whitelist) and consistency mechanism. | [1] |
| Art. 35(7) | Minimum content of a DPIA. | [1] |
| Art. 35(9) | Seek data subjects' views where appropriate. | [1] |
| Art. 35(10)–(11) | Legislative-basis exemption; obligation to review. | [1] |
| Art. 36 | Prior consultation with the supervisory authority on high residual risk. | [1] |
| Art. 39(1)(c) | DPO to advise on and monitor DPIA performance. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the articles above.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 84 | A DPIA should be carried out to enhance compliance where processing is likely to result in a high risk. | [1] |
| Recital 89 | General notification abolished; replaced by focused obligations (incl. DPIAs) for genuinely high-risk processing. | [1] |
| Recital 90 | The DPIA should describe processing, assess necessity/proportionality and risks, and determine mitigating measures. | [1] |
| Recital 91 | "Large scale" and the mandatory cases; individual physicians/lawyers processing patient/client data are not "large scale". | [1] |
| Recital 92 | A single DPIA may address a set of similar operations with similar high risks. | [1] |
| Recital 94–95 | Prior consultation where risk cannot be mitigated; processor to assist the controller. | [1] |

## Relevant Case Law

Not Applicable at the methodology level. The Article 35–36 DPIA obligation is elaborated principally through **regulatory guidance** (WP248 rev.01; national SA lists; ICO guidance) rather than a distinct line of CJEU authority; enforcement decisions turning on a missing or inadequate DPIA are taken by national supervisory authorities and are better treated as sector examples in `compliance-operations-foundations`. General GDPR case law on high risk and profiling (see `gdpr-foundations`) informs the threshold. [1][4][7]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **WP248 rev.01** (Article 29 Working Party, **endorsed by the EDPB**) is the authoritative reading of "likely to result in a high risk". It offers **nine criteria**: (1) evaluation or scoring; (2) automated decision-making with legal or similar significant effect; (3) systematic monitoring; (4) sensitive data or data of a highly personal nature; (5) large-scale processing; (6) matching or combining datasets; (7) data on vulnerable subjects; (8) innovative use of new technology/organisational solutions; (9) processing that prevents subjects from exercising a right or using a service/contract [4][5][7]. *(Regulatory interpretation.)*
- The **"two or more" rule of thumb**: WP248 and the ICO agree that processing meeting **two or more** criteria will in most cases require a DPIA, though a **single** criterion may suffice, and a controller may justify *not* doing a DPIA only if it documents why the processing is nonetheless unlikely to be high risk [4][7]. *(Regulatory interpretation.)*
- The **ICO** frames the trigger as three layers: the **Art. 35(3)** cases, its own **Art. 35(4) list of ten** operation types, and the **European (WP29) criteria**; where processing fits none but is arguably high risk, the controller must still decide, and "if in doubt, do a DPIA" [6][7]. *(Regulatory interpretation.)*
- On **process**, the ICO sets out a staged method — identify the need; describe the processing; consult where appropriate; assess necessity, proportionality and compliance; identify and assess risks; identify measures; sign off and record; integrate outcomes and keep under review [8]. *(Regulatory interpretation.)*
- On **consultation**, both the statute and the ICO confirm the controller **cannot begin** high-residual-risk processing until it has consulted the authority, which generally responds within **8 weeks** [1][8]. *(Regulatory interpretation of a legal obligation.)*

# Technical Considerations

A DPIA is only as good as the system description and risk model beneath it. Engineering practices that make DPIAs reliable:

- **Derive DPIA scope from the RoPA and data-flow diagrams** — the Art. 30 record and current data-flow/DFD artefacts give the "systematic description" required by Art. 35(7)(a); keep them versioned so the DPIA can be re-run on change [1]. *(Best practice grounded in obligation.)*
- **Feed the risk step from threat modelling** — privacy threat-modelling (e.g., LINDDUN) and security threat modelling produce the harm scenarios the Art. 35(7)(c) risk assessment scores; align the DPIA risk register with the security risk register (see `privacy-engineering-foundations`). *(Best practice.)*
- **Bind mitigations to controls** — each Art. 35(7)(d) measure should map to a concrete technical/organisational control (encryption, pseudonymisation, access control, minimisation, retention automation) with an owner and a verification method [1]. *(Best practice.)*
- **Instrument the trigger in the SDLC** — a lightweight screening questionnaire at design-gate/change-control automatically flags Art. 35(3)/35(4)/WP248 hits, so DPIAs are raised before build, not after launch [7]. *(Editorial recommendation.)*
- **Adopt a process standard** — **ISO/IEC 29134** structures the PIA lifecycle and report; **ISO/IEC 27701** provides the management-system wrapper that keeps DPIAs auditable and repeatable [10][12]. *(Best practice.)*

# Hosting Considerations

- **Processor assistance is contractual and legal** — under Art. 28(3)(f) and Recital 95 the processor (including a hosting/cloud provider) must **assist** the controller with DPIAs; the DPIA should reflect real infrastructure facts (regions, sub-processors, encryption, key custody) [1]. *(Legal obligation — reflected in the DPA/contract.)*
- **The controller owns the DPIA** — hosting a workload does not transfer the Art. 35 duty; the controller must obtain the technical evidence it needs from the provider to complete the description and risk steps [1]. *(Legal obligation.)*
- **Transfers feed the risk assessment** — where hosting entails a restricted transfer, the Chapter V analysis and any transfer risk assessment are inputs to (not substitutes for) the DPIA (see `gdpr-transfers`). *(Best practice.)*
- **UK context** — for UK controllers the obligation is the assimilated **UK GDPR** Art. 35/36 read with the **DPA 2018**; the ICO's list and template apply [3][6]. *(Legal obligation.)*

# Game Hosting Considerations

- **Children trigger DPIAs readily** — services likely to be accessed by children engage the WP248 "vulnerable subjects" criterion and the ICO "targeting of children" list item; a DPIA is effectively expected, and the ICO Children's Code treats it as integral (see `game-hosting-foundations`, `uk-gdpr-foundations`) [7]. *(Legal obligation / regulatory expectation.)*
- **Profiling and matchmaking** — behavioural profiling, engagement optimisation and ad targeting can meet the "evaluation/scoring" and "automated decision-making" criteria, raising a DPIA even before scale is considered [1][7]. *(Legal obligation once high risk.)*
- **Biometrics and voice** — anti-cheat, age-assurance or voice-moderation features processing biometric data hit both Art. 35(3)(b) (if large scale/special category) and the ICO biometrics list item [1][7]. *(Legal obligation.)*
- **Innovative technology** — novel AI-driven features (generative NPCs, AI companions) engage the "innovative use" criterion and should be DPIA-screened at design [7]. *(Best practice grounded in obligation.)*

# AI Considerations

- **DPIA vs FRIA — related but distinct** — the **AI Act Art. 27** requires certain **deployers** of Annex III high-risk AI systems to run a **Fundamental Rights Impact Assessment**; Art. 27 expressly provides that where obligations are already met through a **DPIA**, the FRIA **complements** it rather than duplicating it [2]. *(Legal obligation under a separate regime.)*
- **Run them together** — for AI that processes personal data, the DPIA (GDPR) and FRIA (AI Act) share inputs (system description, affected persons, risk scenarios, mitigations); a combined assessment template avoids divergence and evidences both [1][2]. *(Best practice.)*
- **Automated decision-making** — solely automated decisions with legal/significant effect engage Art. 35(3)(a) **and** GDPR Art. 22; the DPIA must document the logic, safeguards and human-oversight measures [1]. *(Legal obligation.)*
- **AI-specific impact standard** — **ISO/IEC 42005** gives a process for **AI system impact assessment** that can structure the AI-risk portions of a combined DPIA/FRIA [11]. *(Best practice.)*
- **New technology is an explicit trigger** — Art. 35(1) singles out "new technologies", so novel AI/ML pipelines should be screened for a DPIA by default [1][7]. *(Legal obligation.)*

# Operational Guidance

Labels: **OBLIGATION** (must, per statute) / **BEST PRACTICE** (should, per standards/regulators) / **EDITORIAL RECOMMENDATION** (we suggest).

**A. Screen every new or changed processing operation.**
1. Run a **threshold/screening assessment** against Art. 35(3), the SA's Art. 35(4) list, and the WP248 nine criteria; treat **two or more** criteria (or a single strong one) as a trigger. *(OBLIGATION to assess; BEST PRACTICE for the questionnaire form.)* [1][7]
2. **Document a negative screen** — if you decide no DPIA is needed, record why (the processing is unlikely to be high risk). *(OBLIGATION.)* [7]

**B. Conduct the DPIA to the Art. 35(7) standard.**
3. **Describe** the processing systematically — nature, scope, context, purposes, data categories, recipients, retention, transfers; reuse the RoPA and data-flow diagrams. *(OBLIGATION.)* [1]
4. **Assess necessity and proportionality** — lawful basis, purpose limitation, minimisation, accuracy, retention, transparency, data-subject rights. *(OBLIGATION.)* [1]
5. **Assess the risks** to rights and freedoms — identify harm scenarios, estimate likelihood and severity, and record the risk rating. *(OBLIGATION.)* [1]
6. **Identify measures** to eliminate or reduce each risk, with owners and residual-risk ratings. *(OBLIGATION.)* [1]
7. **Consult the DPO** (Art. 35(2)) and, **where appropriate, data subjects** (Art. 35(9)). *(OBLIGATION.)* [1]

**C. Escalate, sign off and sustain.**
8. **Prior consultation** — if residual risk remains high, **consult the supervisory authority before processing** (Art. 36) and do not start until you have. *(OBLIGATION.)* [1][8]
9. **Sign off and record** — obtain documented approval; retain the DPIA as accountability evidence and link it to the RoPA entry. *(OBLIGATION for accountability; BEST PRACTICE for the register.)* [1]
10. **Review on change** — re-assess at least when the risk changes and on a periodic cadence (Art. 35(11)). *(OBLIGATION.)* [1]
11. **Use a recognised template** — the **ICO DPIA template** and **ISO/IEC 29134** report structure are known-good starting points; adapt, don't reinvent. *(BEST PRACTICE / EDITORIAL RECOMMENDATION.)* [9][10]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | High-risk processing launched with **no DPIA** | High | High | Art. 35(1) [1] | SDLC screening gate; DPIA register | Low |
| R2 | DPIA done **after** go-live (retrospective) | High | High | Art. 35(1) ("prior to") [1] | Design-stage trigger; change control | Low |
| R3 | **Screening misses** a mandatory case or SA-list item | Medium | High | Art. 35(3)/(4) [1][7] | Structured questionnaire mapped to criteria | Low |
| R4 | DPIA **omits Art. 35(7) content** (e.g., no necessity/proportionality) | Medium | High | Art. 35(7) [1] | Template enforcing all four elements | Low |
| R5 | High residual risk but **no prior consultation** | Low | Very High | Art. 36 [1][8] | Residual-risk gate forcing Art. 36 referral | Low |
| R6 | **DPO not consulted**; data-subject views not sought | Medium | Medium | Art. 35(2), 35(9) [1] | Workflow sign-off steps; DPO in the loop | Low |
| R7 | DPIA **not reviewed** after material change | High | Medium | Art. 35(11) [1] | Change triggers + periodic review cadence | Medium |
| R8 | DPIA and **AI Act FRIA diverge** or duplicate | Medium | Medium | AI Act Art. 27 [2] | Combined DPIA/FRIA template | Low |
| R9 | Processor **fails to supply** DPIA evidence | Medium | Medium | Art. 28(3)(f); Recital 95 [1] | Contractual assistance clause; evidence SLA | Low |

# Implementation Roadmap

- **Phase 0 — Inventory & screening baseline:** Reconcile the RoPA; build a screening questionnaire mapped to Art. 35(3), the SA list and WP248; triage the existing portfolio. *Effort:* Medium.
- **Phase 1 — Method & template:** Adopt a DPIA template covering all Art. 35(7) elements (ICO template / ISO 29134 structure); define risk-scoring and sign-off. *Effort:* Medium.
- **Phase 2 — SDLC integration:** Wire screening into design-gates/change-control; define residual-risk escalation to Art. 36. *Effort:* Medium–High.
- **Phase 3 — Backlog remediation:** Run DPIAs for high-risk processing already live; consult the SA where required. *Effort:* High.
- **Phase 4 — AI & assessment convergence:** Merge DPIA with the AI Act FRIA and (where used) ISO/IEC 42005 for AI systems. *Effort:* Medium–High.
- **Phase 5 — Assurance & metrics:** DPIA coverage KPIs, review cadence, internal audit, and continuous improvement. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | DPIAs done ad hoc, if at all; no screening; often retrospective. | No register; no template; missed triggers. |
| 2 | Managed | A template exists; DPIAs done for obvious cases but inconsistently; late in the lifecycle. | Some DPIAs; partial screening. |
| 3 | Defined | Documented screening mapped to Art. 35(3)/(4)/WP248; DPIAs at design stage; DPO in the loop; sign-off recorded. | Screening questionnaire; DPIA register; Art. 36 route defined. |
| 4 | Quantitatively Managed | Metrics on DPIA coverage, timeliness, residual risk and review currency; DPIAs linked to the RoPA. | KPIs; audit trail; change-triggered reviews. |
| 5 | Optimising | DPIA integrated with FRIA and security risk; automated triggers; continuous review and independent assurance. | Combined DPIA/FRIA; automated SDLC gates; external audit. |

# Audit Questions

1. How do you **screen** new/changed processing for a DPIA, and how is the decision recorded? *(Art. 35(1), 35(3)–(4) [1][7].)*
2. Show a DPIA that addresses **all four Art. 35(7) elements** — description, necessity/proportionality, risk, measures. *(Art. 35(7) [1].)*
3. How do you evidence that DPIAs are done **before** processing begins? *(Art. 35(1) [1].)*
4. Where a DPIA identified **high residual risk**, how did you handle **prior consultation**? *(Art. 36 [1][8].)*
5. How is the **DPO** involved, and when are **data subjects'** views sought? *(Art. 35(2), 35(9), 39(1)(c) [1].)*
6. How and when are DPIAs **reviewed** after changes? *(Art. 35(11) [1].)*
7. For AI systems, how do the **DPIA and Art. 27 FRIA** relate and avoid duplication? *(AI Act Art. 27 [2].)*
8. How do **processors** provide the assistance and evidence your DPIAs need? *(Art. 28(3)(f); Recital 95 [1].)*

# Implementation Checklist

- [ ] Screening questionnaire mapped to Art. 35(3), the SA's Art. 35(4) list, and the WP248 nine criteria.
- [ ] Negative-screen decisions documented with reasons.
- [ ] DPIA template enforcing all Art. 35(7) elements (description, necessity/proportionality, risk, measures).
- [ ] DPIAs raised at design stage / change control, before processing begins.
- [ ] DPO consultation and (where appropriate) data-subject consultation built into the workflow.
- [ ] Residual-risk gate that forces Art. 36 prior consultation when risk stays high.
- [ ] Documented sign-off; DPIA linked to the RoPA entry and retained as evidence.
- [ ] Review triggers (material change) plus a periodic review cadence.
- [ ] Combined DPIA/FRIA approach for high-risk AI (AI Act Art. 27).
- [ ] Processor DPIA-assistance clauses and evidence expectations in contracts.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Articles 24, 25, 30, 35, 36, 39 and Recitals 84, 89–96. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [2] **Regulation (EU) 2024/1689 (Artificial Intelligence Act)** — Article 27 (fundamental rights impact assessment; relationship to the DPIA). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [3] **Data Protection Act 2018 (c.12)** — UK companion to the UK GDPR (DPIA duties for general and law-enforcement processing). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/contents

## Regulatory Guidance

- [4] **Guidelines on Data Protection Impact Assessment (DPIA) and determining whether processing is "likely to result in a high risk" (WP248 rev.01).** Article 29 Data Protection Working Party (adopted 4 Apr 2017; revised 4 Oct 2017). European Commission newsroom. https://ec.europa.eu/newsroom/article29/item-detail.cfm?item_id=611236
- [5] **Endorsed WP29 Guidelines** (the EDPB's endorsement of Article 29 Working Party guidelines, incl. WP248 rev.01). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/general-guidance/endorsed-wp29-guidelines_en
- [6] **Data Protection Impact Assessments (DPIAs).** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/data-protection-impact-assessments-dpias/
- [7] **When do we need to do a DPIA?** (Art. 35(3) cases; the ICO's Art. 35(4) list of ten; the WP29 nine criteria; the "two or more" rule). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/data-protection-impact-assessments-dpias/when-do-we-need-to-do-a-dpia/
- [8] **How do we do a DPIA?** (the staged process; prior consultation and the 8-week response). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/data-protection-impact-assessments-dpias/how-do-we-do-a-dpia/
- [9] **Sample DPIA template (.docx).** ICO. https://ico.org.uk/media2/migrated/2553993/dpia-template.docx

## Standards

- [10] **ISO/IEC 29134:2023** — Information technology — Security techniques — Guidelines for privacy impact assessment. ISO/IEC. https://www.iso.org/standard/86012.html
- [11] **ISO/IEC 42005:2025** — Artificial intelligence — AI system impact assessment. ISO/IEC. https://www.iso.org/standard/42005
- [12] **ISO/IEC 27701** — Privacy Information Management System (PIMS); management-system wrapper for privacy processes incl. DPIAs. ISO/IEC. https://www.iso.org/standard/71670.html

## Academic Sources

Not Applicable — this methodology rests on primary legislation (GDPR; AI Act), endorsed regulatory guidance (WP248 rev.01; ICO) and international standards. Academic critique of DPIA effectiveness and risk-methodology limits will be cited in `privacy-threat-modelling` (planned).

# Further Reading

*Non-authoritative; provided for orientation only.*

- ICO — Examples of processing "likely to result in high risk". https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/data-protection-impact-assessments-dpias/examples-of-processing-likely-to-result-in-high-risk/
- EDPB — Guidelines, Recommendations and Best Practices (index). https://www.edpb.europa.eu/our-work-tools/general-guidance/guidelines-recommendations-best-practices_en

# Related Documents

- `privacy-engineering-foundations` — **parent**; introduces the Art. 35 DPIA trigger, DPbDD and Art. 32 controls (**prerequisite reading**).
- `gdpr-foundations` — principles, accountability and the high-risk concept underpinning the DPIA.
- `uk-gdpr-foundations` — UK GDPR/DPA 2018 context; ICO list and template apply.
- `ai-act-foundations` / `ai-act-high-risk` — the Art. 27 FRIA that dovetails with the DPIA.
- `gdpr-transfers` — Chapter V transfer analysis feeding the DPIA risk step.
- `compliance-operations-foundations` — running DPIAs as part of the wider accountability programme.
- `privacy-threat-modelling`, `anonymisation-techniques` — feed the DPIA risk and necessity steps (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Arts. 35–36, 30, 39; AI Act Art. 27), WP248 rev.01 (EDPB-endorsed), ICO DPIA guidance/template and ISO/IEC 29134 / 42005 / 27701. Art. 35(3)/(4) lists, the WP29 nine criteria and the "two or more" rule live-verified against the ICO guidance. | — |
