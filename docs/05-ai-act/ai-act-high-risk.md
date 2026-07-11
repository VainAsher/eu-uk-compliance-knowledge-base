---
id: ai-act-high-risk
title: "EU AI Act: High-Risk Systems & Conformity Assessment"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: AI Act
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
related: [ai-act-foundations, ai-governance-foundations, gdpr-foundations, privacy-engineering-foundations]
tags: [ai-act, high-risk-ai, annex-iii, conformity-assessment, ce-marking, fria, human-oversight, harmonised-standards, ai-omnibus]
legal_basis: Regulation (EU) 2024/1689 (Articles 6–27, 40–49, 71; Annexes I, III, IV, VI, VII)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-act-high-risk |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.10.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a Tier 2 **deep-dive** that details the high-risk material introduced at overview level in `ai-act-foundations`; it does not repeat that overview. **Timeline warning:** the high-risk application dates were amended by the **"AI Omnibus"** simplification package, which — unlike the position recorded in the parent foundation document — was **formally adopted by both co-legislators in June 2026** (European Parliament plenary, 16 June 2026; Council final approval, 29 June 2026) and was awaiting **publication in the Official Journal** at this document's date. The revised dates become legally binding only on that publication (entry into force on the third day thereafter) — confirm the OJ citation before relying on them [3][4][5][6].

# Executive Summary

The EU AI Act (Regulation (EU) 2024/1689) reserves its heaviest obligations for **high-risk AI systems** — the systems most capable of harming health, safety or fundamental rights. This document details, at article level, **how a system becomes high-risk**, **what it must satisfy**, and **who must do what** to place it lawfully on the EU market [1].

Classification runs on two routes. The **product-safety route (Art. 6(1), Annex I)** captures AI that is, or is a safety component of, a product already regulated under Union harmonisation legislation (machinery, medical devices, toys, vehicles, etc.) and subject to third-party conformity assessment. The **use-case route (Art. 6(2), Annex III)** lists eight sensitive domains — biometrics, critical infrastructure, education, employment, essential public/private services (incl. credit scoring and insurance), law enforcement, migration/border control, and justice/democracy. A **filter (Art. 6(3))** can pull an Annex III system back out of scope where it performs only a narrow, preparatory or human-confirming task and does **not** profile natural persons [1][9].

High-risk providers must build a **risk-management system (Art. 9)**, meet **data-governance (Art. 10)**, **technical-documentation (Art. 11)**, **logging (Art. 12)**, **transparency-to-deployer (Art. 13)**, **human-oversight (Art. 14)** and **accuracy/robustness/cybersecurity (Art. 15)** requirements; operate a **quality management system (Art. 17)**; complete **conformity assessment (Art. 43)**; draw up an **EU declaration of conformity (Art. 47)**; affix **CE marking (Art. 48)**; and **register in the EU database (Art. 49/71)** [1]. Deployers carry their own duties (Art. 26), and some must run a **fundamental-rights impact assessment (Art. 27)** [1]. Compliance is presumed where **harmonised standards** (Art. 40) are met [1][8]. The single most important planning input is the **amended, now-adopted timeline**: standalone Annex III duties apply from **2 December 2027** and product-embedded (Annex I) duties from **2 August 2028**, subject to Official Journal publication [3][4][5][6].

# Key Takeaways

- **Two classification routes.** A system is high-risk if it is (or is a safety component of) an **Annex I product** subject to third-party conformity assessment (Art. 6(1)), **or** it falls within an **Annex III use case** (Art. 6(2)) [1]. *(Legal obligation.)*
- **The Art. 6(3) filter is narrow.** An Annex III system escapes high-risk status only if it poses no significant risk to health, safety or fundamental rights (narrow procedural / preparatory / human-confirming tasks) — but it is **always high-risk if it profiles** natural persons, and the provider must **document** the exemption assessment [1]. *(Legal obligation.)*
- **Seven core requirements (Arts. 8–15)** apply to every high-risk system: risk management, data governance, technical documentation, record-keeping/logging, transparency to deployers, human oversight, and accuracy/robustness/cybersecurity [1]. *(Legal obligation.)*
- **Providers carry the market-access chain:** quality management system (Art. 17), conformity assessment (Art. 43), EU declaration of conformity (Art. 47), CE marking (Art. 48) and registration in the EU database (Arts. 49, 71) [1]. *(Legal obligation.)*
- **Most Annex III systems self-assess** via internal control (Annex VI); **third-party notified-body assessment (Annex VII)** is required for certain biometric systems and via sectoral law on the product route (Art. 43) [1]. *(Legal obligation.)*
- **Deployers are not passive:** Art. 26 imposes use-per-instructions, human oversight, input-data control, monitoring and log-keeping; **Art. 27** adds a **fundamental-rights impact assessment (FRIA)** for public bodies, public-service providers and certain credit/insurance deployers [1]. *(Legal obligation.)*
- **Harmonised standards give a presumption of conformity (Art. 40);** where they are absent the Commission may adopt **common specifications (Art. 41)**. CEN-CENELEC is drafting the standards under a Commission request [1][8]. *(Legal obligation + best practice.)*
- **Timeline — now adopted, not merely proposed:** the AI Omnibus moves standalone Annex III duties to **2 Dec 2027** and product-embedded duties to **2 Aug 2028**; it was adopted by Parliament (16 Jun 2026) and Council (29 Jun 2026) and awaited OJ publication at this document's date [3][4][5][6]. *(Legal obligation — pending OJ publication.)*

# Purpose

This document supports three tasks that the foundation document leaves open: (a) **classifying** a candidate system (product-safety route vs. Annex III vs. Art. 6(3) exemption); (b) **engineering and documenting** the Art. 8–15 requirements and the provider quality/conformity chain; and (c) **allocating obligations between provider and deployer**, including the FRIA. It is written for legal, compliance and engineering readers preparing high-risk systems ahead of the (now-amended) application dates. It presupposes `ai-act-foundations` for the risk-tier overview and cross-refers `ai-governance-foundations` for the operational management-system detail.

# Scope

**In scope:** High-risk classification (Art. 6, Annexes I & III; the Art. 6(3) filter and Art. 6(4) documentation duty); the requirements of Arts. 8–15; provider obligations (Arts. 16–25) including the QMS (Art. 17), conformity assessment (Arts. 43–44), EU declaration of conformity (Art. 47), CE marking (Art. 48) and registration (Arts. 49, 71); deployer obligations (Art. 26) and the FRIA (Art. 27); harmonised standards and common specifications (Arts. 40–41); and the high-risk application timeline as amended by the AI Omnibus.

**Out of scope (covered elsewhere):** The four-tier overview, GPAI regime and penalties → `ai-act-foundations`; prohibited practices (Art. 5) → `ai-act-prohibited-practices` (planned); the GPAI/systemic-risk regime → `ai-act-gpai` (planned); the AI Omnibus package as a whole → `digital-omnibus` (planned); operational AI management systems, ISO/IEC 42001 and human-oversight design method → `ai-governance-foundations`; Art. 50 transparency obligations in depth (touched only where they intersect the high-risk timeline).

**Assumptions:** The reader has read `ai-act-foundations`. Where a high-risk system processes personal data, the GDPR applies in parallel (see `gdpr-foundations`, `privacy-engineering-foundations`); this document does not restate GDPR duties.

# Definitions

*Shared terms (AI system, provider, deployer, high-risk AI system, human oversight) are in `GLOSSARY.md`. Only high-risk-specific terms are defined here; keep this table short per sub-topic policy.*

| Term | Definition | Source |
|------|------------|--------|
| Safety component | A component of a product or system which fulfils a safety function for that product/system, or whose failure or malfunction endangers the health and safety of persons or property (Art. 3(14)); central to the Art. 6(1) product-safety route. | [1] |
| Conformity assessment | The process of demonstrating whether the requirements of Arts. 8–15 have been fulfilled (Art. 3(20)); performed by internal control (Annex VI) or a notified body (Annex VII). | [1] |
| Notified body | A conformity assessment body notified under the AI Act to carry out third-party conformity assessment (Arts. 3(22), 28–39). | [1] |
| Harmonised standard | A European standard adopted on the basis of a Commission request under Regulation (EU) 1025/2012; conformity with it confers a presumption of conformity with the corresponding requirement (Art. 40). | [1][8] |
| Common specification | A set of technical specifications adopted by Commission implementing act providing an alternative route to compliance where harmonised standards are absent or insufficient (Art. 41). | [1] |
| Substantial modification | A change to a high-risk AI system after placing on the market/putting into service which affects compliance with Chapter III or changes the intended purpose (Art. 3(23)); can turn a deployer/distributor into a provider (Art. 25). | [1] |
| Fundamental-rights impact assessment (FRIA) | The Art. 27 assessment certain deployers must perform before deploying an Annex III high-risk system, describing use, affected persons, risks of harm, human-oversight and governance measures. | [1] |

# Background

The AI Act's high-risk chapter is not built from scratch: it deliberately borrows the EU's **New Legislative Framework (NLF)** for product safety — essential requirements, harmonised standards conferring presumption of conformity, conformity assessment (self-assessment or notified body), the **EU declaration of conformity** and **CE marking**, and market surveillance [1][9]. The AI Act layers onto that machinery a **fundamental-rights** dimension absent from classic product law: a use-case list (Annex III) untethered from any single product, a **deployer-side** duty set, and the **FRIA**. Academic analysis has noted both the strength of reusing a mature compliance architecture and the friction of grafting fundamental-rights protection onto a product-safety chassis that traditionally addresses physical safety, not societal harm [9].

The timeline has been the most contested element. The Regulation's original Art. 113 phased high-risk duties in from **2 August 2026** (Annex III standalone) and **2 August 2027** (Annex I product route). During 2025 the Commission's **Digital Omnibus / AI Omnibus** simplification agenda proposed to postpone these and reduce documentation burden. Crucially for this deep-dive, that package has now **completed the legislative procedure**: the European Parliament adopted it in plenary on **16 June 2026** and the Council gave final approval on **29 June 2026**, with Official Journal publication the remaining step at this document's date [3][4][5][6].

# Legal Framework

High-risk AI is governed by **Chapter III** of Regulation (EU) 2024/1689, supported by definitions in Chapter I and governance/market-surveillance provisions in Chapters VII–IX. Chapter III has four sections: **classification (Arts. 6–7)**, **requirements (Arts. 8–15)**, **obligations of providers, deployers and other operators (Arts. 16–27)**, and **notified bodies / conformity assessment / registration (Arts. 28–49)** [1].

**Classification (Section 1).** Art. 6(1) sets the **product-safety route**: an AI system is high-risk if (a) it is intended to be used as a **safety component** of a product, or is itself a product, covered by the Union harmonisation legislation in **Annex I**, **and** (b) that product must undergo **third-party conformity assessment** under that legislation. Art. 6(2) sets the **use-case route**: systems in **Annex III** are high-risk. Art. 6(3) is the **filter** (see below); Art. 6(4) requires a provider claiming the filter to **document** its assessment and still **register**. Art. 7 empowers the Commission to amend Annex III.

**Requirements (Section 2, Arts. 8–15).** These are the substantive engineering obligations, met "taking into account the intended purpose and the generally acknowledged state of the art" (Art. 8) [1].

**Obligations (Section 3, Arts. 16–27).** Provider obligations (Art. 16 as the index, elaborated in Arts. 17–22, 25), operator/value-chain rules (Arts. 23–25), **deployer** obligations (Art. 26) and the **FRIA** (Art. 27) [1].

**Conformity, standards and registration (Section 4 + Chapter III standards provisions).** Harmonised standards (Art. 40), common specifications (Art. 41), conformity assessment procedures (Art. 43, Annexes VI/VII), certificates (Art. 44), EU declaration of conformity (Art. 47), CE marking (Art. 48), and registration in the EU database (Arts. 49, 71) [1].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 6(1) + Annex I | Product-safety classification route: AI as/within a regulated product subject to third-party conformity assessment. | [1] |
| Art. 6(2) + Annex III | Use-case classification route: eight listed high-risk domains. | [1] |
| Art. 6(3) | Derogation/filter: Annex III system not high-risk where no significant risk (narrow, preparatory or human-confirming tasks); never applies where the system profiles natural persons. | [1] |
| Art. 6(4) | Provider relying on Art. 6(3) must document the assessment; registration still required. | [1] |
| Art. 7 | Commission power to amend the Annex III list. | [1] |
| Art. 8 | Compliance with Arts. 9–15 in light of intended purpose and state of the art. | [1] |
| Art. 9 | Risk-management system — continuous, iterative, lifecycle-wide. | [1] |
| Art. 10 | Data and data governance — quality, representativeness, bias examination; special-category data for bias correction under safeguards. | [1] |
| Art. 11 + Annex IV | Technical documentation demonstrating conformity. | [1] |
| Art. 12 | Automatic record-keeping (logging) enabling traceability. | [1] |
| Art. 13 | Transparency and provision of information (instructions for use) to deployers. | [1] |
| Art. 14 | Human oversight — understand, monitor, intervene, override; two-person rule for certain remote biometric ID. | [1] |
| Art. 15 | Accuracy, robustness and cybersecurity (incl. resilience to data/model poisoning and adversarial inputs). | [1] |
| Art. 16 | Index of provider obligations for high-risk systems. | [1] |
| Art. 17 | Quality management system. | [1] |
| Arts. 18–21 | Documentation retention (10 yrs), automatic logs retention, corrective actions, cooperation with authorities. | [1] |
| Art. 22 | Authorised representative for non-EU providers. | [1] |
| Arts. 23–25 | Importer/distributor duties; value-chain responsibilities; when an operator becomes a provider (substantial modification, own name/trademark). | [1] |
| Art. 26 | Deployer obligations (use per instructions, human oversight, input control, monitoring, logs, information duties). | [1] |
| Art. 27 | Fundamental-rights impact assessment for specified deployers. | [1] |
| Art. 40 | Harmonised standards → presumption of conformity. | [1][8] |
| Art. 41 | Common specifications where standards absent/insufficient. | [1] |
| Art. 43 + Annexes VI/VII | Conformity assessment — internal control vs. notified body. | [1] |
| Art. 47 | EU declaration of conformity. | [1] |
| Art. 48 | CE marking of conformity. | [1] |
| Arts. 49, 71 | Registration of high-risk systems in the EU database. | [1] |
| Art. 113 (as amended) | Application dates for high-risk systems (amended by the AI Omnibus). | [1][3][5] |

## Relevant Recitals

*Recitals are not binding but aid construction (Art. 296 TFEU practice); this is stated expressly.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 46–47 | Rationale for the product-safety classification route and its link to existing Union harmonisation legislation. | [1] |
| Recital 52–53 | Rationale for the Annex III use-case list and the fundamental-rights focus of high-risk classification. | [1] |
| Recital 53 area | Basis of the Art. 6(3) filter — systems that do not materially influence decision outcomes should not be high-risk, but profiling always is. | [1] |
| Recital 66 area | Human-oversight rationale — enabling natural persons to prevent or minimise risks. | [1] |
| Recital 74 area | Accuracy, robustness and cybersecurity expectations for high-risk systems. | [1] |
| Recital 96 area | Purpose of the fundamental-rights impact assessment for deployers. | [1] |

## Relevant Case Law

**Not Applicable — no CJEU case law yet.** The AI Act is recent and its high-risk provisions are not yet applicable (application dates fall in 2027–2028 as amended), so no court has interpreted Arts. 6–27. Interpretive weight currently rests on the Regulation's text, forthcoming Commission guidelines (Art. 6(5)), harmonised standards, and — for personal-data aspects — GDPR case law (see `gdpr-foundations`) [1]. This section should be revisited once the provisions apply and litigation emerges.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **European Commission (framework page):** presents high-risk as the tier carrying "strict obligations" — risk assessment/mitigation, high-quality datasets, logging, detailed documentation, clear user information, human oversight, and robustness/accuracy/cybersecurity — and confirms conformity assessment before market placement [2]. *(Regulatory interpretation.)*
- **Art. 6(3) guidelines:** the Commission is mandated (Art. 6(5)) to issue guidelines specifying the practical implementation of the classification rules, including the filter; providers should treat the exemption conservatively pending those guidelines and the profiling carve-out [1][2]. *(Regulatory interpretation — track guidance.)*
- **Standardisation:** the Commission has issued a standardisation request to **CEN-CENELEC** (Joint Technical Committee 21) to develop harmonised standards operationalising Arts. 9–15; meeting them will confer the Art. 40 presumption of conformity. Until they are cited in the Official Journal, providers rely on the Regulation directly or on common specifications (Art. 41) [1][8]. *(Regulatory interpretation + best practice.)*
- **AI Omnibus (now adopted):** the co-legislators postponed high-risk application (standalone Annex III to 2 Dec 2027; product-embedded to 2 Aug 2028), introduced new Art. 5 prohibitions (non-consensual intimate imagery / CSAM generators, from 2 Dec 2026), and eased documentation for SMEs and small mid-caps. Unlike the parent foundation document — which recorded only a *provisional* agreement — the measure was **adopted by Parliament (16 Jun 2026) and Council (29 Jun 2026)** and takes effect on OJ publication (+3 days) [3][4][5][6]. *(Legal obligation — pending OJ publication; verify the OJ citation.)*

# Technical Considerations

- **Classify first, and re-classify on change.** Run the Art. 6 decision: (1) is it, or a safety component of, an Annex I product needing third-party assessment? → high-risk (product route). (2) Else, does it match an Annex III entry? → high-risk (use-case route) unless (3) the Art. 6(3) filter applies **and** it does not profile. Record the reasoning (Art. 6(4)) [1][9]. *(Legal obligation.)*
- **Risk-management as a living loop (Art. 9).** Implement a continuous, iterative process spanning the lifecycle: identify known and reasonably foreseeable risks to health, safety and fundamental rights; adopt targeted mitigations; test against pre-defined metrics; and give specific consideration to impacts on persons under 18 and other vulnerable groups [1]. *(Legal obligation.)*
- **Data governance (Art. 10).** Training, validation and testing datasets must be relevant, sufficiently representative, and — to the best extent possible — free of errors and complete for the intended purpose; examine for **biases** likely to affect health, safety or fundamental rights. Art. 10 permits processing of **special-category data** strictly for bias detection and correction subject to safeguards (a point the AI Omnibus clarified) [1][3]. *(Legal obligation.)*
- **Documentation and logging by construction (Arts. 11–12).** Generate **Annex IV** technical documentation and **automatic logs** as pipeline outputs, not retrofits; logs must enable traceability of events, functioning and risk situations across the system's lifetime [1]. See `ai-governance-foundations` for the auto-documentation pattern. *(Legal obligation.)*
- **Human oversight designed in (Art. 14).** Build measures enabling overseers to understand capacities and limits, stay alert to **automation bias**, interpret output correctly, and **decide not to use / override / stop** the system; certain remote biometric identification requires separate **two-person verification** before action [1]. *(Legal obligation.)*
- **Accuracy, robustness, cybersecurity (Art. 15).** Declare accuracy metrics in the instructions; build resilience to errors, faults and inconsistencies and to feedback loops; and harden against AI-specific attacks — **data poisoning, model poisoning, adversarial examples, and model evasion** [1]. Coordinate with `privacy-engineering-foundations` and security baselines. *(Legal obligation.)*

# Hosting Considerations

- **Role determines obligation set.** Hosting a high-risk system usually makes an organisation a **deployer** (Art. 26 duties). But branding it under one's own name/trademark, or making a **substantial modification** or repurposing it to a new intended purpose, makes the host a **provider** with the full Arts. 8–15 and conformity chain (Art. 25) [1]. *(Legal obligation — assess role explicitly.)*
- **Log retention.** Providers retain automatically generated **logs** (Art. 19) and documentation for **10 years** (Art. 18); deployers keep logs under their control (Art. 26(6)). Hosting must retain these while honouring GDPR storage-limitation and security (see `privacy-engineering-foundations`) [1]. *(Legal obligation.)*
- **Environment for oversight and robustness.** Hosting must support the Art. 14 oversight controls (e.g., stop/override interfaces, monitoring telemetry) and the Art. 15 resilience/cybersecurity posture (segregation, integrity protection, adversarial-input monitoring) [1]. *(Legal obligation + best practice.)*
- **EU database registration is not the host's escape hatch.** Registration (Arts. 49, 71) is a provider/deployer duty tied to role, not to who owns the infrastructure [1]. *(Legal obligation.)*

# Game Hosting Considerations

- **Most game AI stays minimal-risk and outside Chapter III.** NPC behaviour, matchmaking and procedural generation are not Annex III use cases, so the high-risk requirements do not attach [1][2]. *(Interpretation.)*
- **Watch the Annex III edges.** Features doing **biometric categorisation** or **emotion recognition** (Annex III(1)), or AI affecting **access to essential services** (e.g., age-gating tied to services, or credit-like in-game financial features), can cross into high-risk; assess carefully, especially where **minors** are involved [1]. *(Legal obligation once triggered.)*
- **Transparency vs. high-risk are different regimes.** AI chatbots/companions and generative content trigger **Art. 50** transparency (deep-dive in `ai-act-foundations`), not necessarily the high-risk chapter — but the AI Omnibus's new prohibitions on non-consensual intimate-image generators (from 2 Dec 2026) are directly relevant to user-generated-content and image tools in games [3][5]. *(Legal obligation.)*

# AI Considerations

*This document is itself an AI-regulation deep-dive; the "AI Considerations" here concern interaction with adjacent regimes and the operational stack.*

- **Operationalising Arts. 9–17 via management systems.** ISO/IEC 42001 (AIMS) maps closely to the **Art. 17 quality management system** and to the risk-management, data-governance, documentation and oversight duties; the NIST AI RMF supplies the Map/Measure/Manage loop. These are the practical route to conformity and are detailed in `ai-governance-foundations` — do not duplicate here [7]. *(Best practice.)*
- **GDPR runs in parallel.** Where a high-risk system processes personal data, GDPR **lawful basis, DPbDD (Art. 25), security (Art. 32), DPIA (Art. 35)** and **automated-decision (Art. 22)** rules apply alongside Chapter III; the **FRIA (Art. 27)** and a **DPIA** should be run together and cross-referenced, not conflated [1]. *(Legal obligation.)*
- **Harmonised standards will define "state of the art."** As CEN-CENELEC standards are cited, they will concretise Art. 8's "state of the art" benchmark; providers should design to draft standards now and adopt final versions on citation to secure the Art. 40 presumption [1][8]. *(Best practice.)*
- **GPAI upstream.** High-risk systems built on general-purpose models inherit documentation and information dependencies from the GPAI provider (see `ai-act-gpai`, planned); value-chain information duties (Art. 25) matter for conformity [1]. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Classify and document every candidate system** against Art. 6(1)/Annex I and Art. 6(2)/Annex III; where relying on the Art. 6(3) filter, record the assessment (Art. 6(4)) and confirm the system does **not profile**. *(OBLIGATION.)* [1]
2. **Stand up the Art. 9 risk-management system** as a continuous lifecycle process with tested mitigations and explicit vulnerable-group consideration. *(OBLIGATION.)* [1]
3. **Engineer Art. 10 data governance** — representativeness, error/completeness checks, bias examination, and controlled special-category-data use for bias correction. *(OBLIGATION.)* [1]
4. **Produce Annex IV technical documentation and Art. 12 logs automatically.** *(OBLIGATION; BEST PRACTICE to auto-generate.)* [1]
5. **Write Art. 13 instructions for use** giving deployers the characteristics, limits, performance and oversight measures they need. *(OBLIGATION.)* [1]
6. **Design Art. 14 human oversight** (understand/monitor/intervene/override; two-person rule for relevant biometric ID). *(OBLIGATION.)* [1]
7. **Meet Art. 15 accuracy/robustness/cybersecurity,** including AI-specific threat hardening; declare accuracy metrics. *(OBLIGATION.)* [1]
8. **Operate the Art. 17 quality management system;** map it to ISO/IEC 42001 for auditability. *(OBLIGATION + BEST PRACTICE.)* [1][7]
9. **Select the correct conformity route (Art. 43):** internal control (Annex VI) for most Annex III; **notified body (Annex VII)** for the relevant biometric systems and via sectoral law on the product route. *(OBLIGATION.)* [1]
10. **Draw up the EU declaration of conformity (Art. 47), affix CE marking (Art. 48), and register (Arts. 49, 71)** before placing on the market. *(OBLIGATION.)* [1]
11. **Deployers: implement Art. 26** (use per instructions, oversight, input control, monitoring, logs, worker/affected-person information) and, where applicable, **complete the Art. 27 FRIA** and notify the market-surveillance authority. *(OBLIGATION.)* [1]
12. **Plan to the adopted 2027/2028 dates but confirm OJ publication;** do not treat obligations as removed, only deferred — and prepare now. *(EDITORIAL RECOMMENDATION.)* [3][5][6]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Misclassifying a high-risk system as minimal (missing Annex III or the product route) | Medium | Very High | Art. 6, Annexes I/III [1] | Documented classification; re-assess on change; legal review | Low |
| R2 | Over-relying on the Art. 6(3) filter (esp. where the system profiles) | Medium | High | Art. 6(3)–(4) [1] | Conservative filter use; document; treat profiling as always high-risk | Low |
| R3 | Weak data governance / undetected bias | Medium | High | Art. 10 [1] | Representativeness + bias testing; controlled special-category use | Medium |
| R4 | Inadequate human oversight (automation bias, no override) | Medium | High | Art. 14 [1] | Designed oversight roles, training, two-person rule where required | Low |
| R5 | Insufficient robustness/cybersecurity (poisoning, adversarial inputs) | Medium | High | Art. 15 [1] | Threat modelling; adversarial testing; integrity controls | Medium |
| R6 | Wrong conformity route / missing CE marking or registration | Medium | High | Arts. 43, 47–49, 71 [1] | Route decision record; notified-body engagement; registration checklist | Low |
| R7 | Deployer skips the FRIA where required | Medium | High | Art. 27 [1] | FRIA template; integrate with DPIA; authority notification | Low |
| R8 | Treating the AI Omnibus delay as removal, or pre-relying before OJ publication | Medium | Medium | Amended Art. 113 [3][5][6] | Plan to adopted dates; confirm OJ citation; keep building | Low |
| R9 | Assuming standards presumption before harmonised standards are cited | Low | Medium | Arts. 40–41 [1][8] | Design to drafts; use common specifications; adopt on citation | Medium |

# Implementation Roadmap

- **Phase 0 — Classification & inventory:** Apply Art. 6 to each system; record product-route vs. Annex III vs. Art. 6(3) exemption; assign provider/deployer role. *Effort:* Medium. *Depends on:* `ai-act-foundations` triage.
- **Phase 1 — Requirements build (Arts. 9–15):** Risk-management system, data governance, technical documentation, logging, deployer instructions, human oversight, robustness/cybersecurity. *Effort:* High.
- **Phase 2 — Quality & conformity (Arts. 17, 43):** Stand up the QMS (map to ISO/IEC 42001); choose and execute the conformity-assessment route; engage a notified body where required. *Effort:* High.
- **Phase 3 — Market access (Arts. 47–49, 71):** EU declaration of conformity, CE marking, EU-database registration. *Effort:* Medium.
- **Phase 4 — Deployer duties & FRIA (Arts. 26–27):** Deployer controls, monitoring and logs; FRIA where applicable, integrated with DPIA; authority notification. *Effort:* Medium.
- **Phase 5 — Standards & monitoring:** Adopt harmonised standards on citation; track Art. 6(5) guidelines and the AI Omnibus OJ publication; re-assess on change. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No classification; unaware whether systems are high-risk. | No Art. 6 assessment. |
| 2 | Managed | Systems classified and roles assigned; requirements gaps identified. | Classification register; gap analysis. |
| 3 | Defined | Arts. 9–15 controls documented and operating; QMS in place. | Risk-management loop; Annex IV docs; logs; QMS. |
| 4 | Quantitatively Managed | Conformity assessment completed; oversight and robustness measured with metrics; FRIA where required. | Declaration of conformity; CE mark; KPIs; FRIA. |
| 5 | Optimising | Harmonised-standards conformity; integrated AI + data-protection governance; continual re-assessment. | Standards presumption; DPIA/FRIA integration; audit cycle. |

# Audit Questions

1. For each system, is there a documented Art. 6 classification (product route / Annex III / Art. 6(3) exemption), and does any exemption record address profiling? *(Art. 6 [1].)*
2. Is the Art. 9 risk-management system continuous, tested, and does it consider vulnerable groups? *(Art. 9 [1].)*
3. How are datasets governed for representativeness and bias, and how is special-category data controlled? *(Art. 10 [1].)*
4. Are Annex IV technical documentation and Art. 12 logs generated and retained (10 years / logs)? *(Arts. 11, 12, 18, 19 [1].)*
5. Do deployer instructions (Art. 13) and human-oversight measures (Art. 14) exist and function, including any two-person biometric rule? *(Arts. 13–14 [1].)*
6. What accuracy metrics are declared and what robustness/cybersecurity testing (incl. adversarial/poisoning) is performed? *(Art. 15 [1].)*
7. Which conformity route was used (Annex VI vs. VII), and are the declaration of conformity, CE marking and EU-database registration in place? *(Arts. 43, 47–49, 71 [1].)*
8. For deployers, are Art. 26 duties met and has an Art. 27 FRIA been completed and notified where required? *(Arts. 26–27 [1].)*
9. How is conformity evidenced against harmonised standards / common specifications, and how is the AI Omnibus timeline tracked to OJ publication? *(Arts. 40–41; amended Art. 113 [1][3][5][8].)*

# Implementation Checklist

- [ ] Art. 6 classification recorded for every system (product route / Annex III / Art. 6(3) + profiling check).
- [ ] Provider/deployer role assigned; value-chain (Art. 25) triggers assessed.
- [ ] Art. 9 risk-management system operating (continuous, tested, vulnerable-group aware).
- [ ] Art. 10 data governance: representativeness, bias examination, controlled special-category use.
- [ ] Annex IV technical documentation (Art. 11) and automatic logs (Art. 12) generated and retained.
- [ ] Art. 13 instructions for use issued to deployers.
- [ ] Art. 14 human oversight designed (incl. two-person rule where relevant).
- [ ] Art. 15 accuracy declared; robustness and cybersecurity (poisoning/adversarial) tested.
- [ ] Art. 17 quality management system in place (mapped to ISO/IEC 42001).
- [ ] Conformity assessment completed via correct route (Annex VI/VII).
- [ ] EU declaration of conformity (Art. 47), CE marking (Art. 48), EU-database registration (Arts. 49, 71).
- [ ] Deployer Art. 26 duties met; Art. 27 FRIA completed and notified where applicable.
- [ ] Harmonised-standards / common-specifications conformity tracked; AI Omnibus OJ publication confirmed.

# References

*All external links verified HTTP 200 on 2026-07-11 (`sources_verified`) using `curl … -A "Mozilla/5.0"`. The Council of the EU press release corroborating the 29 June 2026 final adoption is authoritative but its site (consilium.europa.eu) bot-blocks automated requests; the same facts are cited here via European Parliament sources that verify HTTP 200.*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act)** — full text incl. Arts. 6–27, 40–49, 71 and Annexes I, III, IV, VI, VII. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj

## Regulatory Guidance

- [2] **Regulatory framework on AI / AI Act** (high-risk obligations overview). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai
- [3] **Digital Omnibus on AI — regulation proposal** (proposal of 19 Nov 2025; postponed high-risk dates; SME/bias-data clarifications). European Commission. https://digital-strategy.ec.europa.eu/en/library/digital-omnibus-ai-regulation-proposal
- [4] **AI Act: deal on simplification measures, ban on "nudifier" apps** (provisional agreement, 7 May 2026; new high-risk dates 2 Dec 2027 / 2 Aug 2028). European Parliament press release. https://www.europarl.europa.eu/news/en/press-room/20260427IPR42011/ai-act-deal-on-simplification-measures-ban-on-nudifier-apps
- [5] **AI Act: EP approves simplification measures and "nudifier" app ban** (plenary adoption 16 June 2026, 423–57 with 174 abstentions; Council formal adoption expected 29 June 2026). European Parliament press release. https://www.europarl.europa.eu/news/en/press-room/20260611IPR45207/ai-act-ep-approves-simplification-measures-and-nudifier-app-ban
- [6] **Digital Omnibus on AI — Legislative Train Schedule** (procedural status: Commission proposal 19 Nov 2025; trilogue agreement 7 May 2026; Coreper 13 May 2026; Parliament vote 16 Jun 2026; entry into force on OJ publication +3 days). European Parliament. https://www.europarl.europa.eu/legislative-train/package-digital-package/file-digital-omnibus-on-ai

## Standards

- [7] **ISO/IEC 42001:2023 — Artificial intelligence — Management system (AIMS).** Maps to the Art. 17 quality management system. ISO/IEC. https://www.iso.org/standard/42001
- [8] **CEN-CENELEC — Artificial Intelligence (harmonised standards under the Commission's AI Act standardisation request).** CEN-CENELEC. https://www.cencenelec.eu/areas-of-work/cen-cenelec-topics/artificial-intelligence/

## Academic Sources

- [9] **Veale, M. & Zuiderveen Borgesius, F. (2021), "Demystifying the Draft EU Artificial Intelligence Act" — Computer Law Review International 22(4), 97–112.** Analyses the reuse of the EU product-safety (New Legislative Framework) architecture for high-risk classification and conformity assessment. Open-access preprint, arXiv:2107.03721. https://arxiv.org/abs/2107.03721 *(Analyses the draft text; its account of the Annex III/product-safety structure remains apposite to the adopted Regulation, but article numbering and detail were revised in the final text — cite alongside [1].)*

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- EU Artificial Intelligence Act — Implementation Timeline (Future of Life Institute). https://artificialintelligenceact.eu/implementation-timeline/
- European Commission — "Navigating the AI Act" FAQ. https://digital-strategy.ec.europa.eu/en/faqs/navigating-ai-act

# Related Documents

- `ai-act-foundations` — the AI Act overview, risk tiers, GPAI, penalties and timeline; this deep-dive **details its high-risk material** (**prerequisite reading**).
- `ai-governance-foundations` — operationalising Arts. 9–17 via ISO/IEC 42001 and the NIST AI RMF; human-oversight design; **cross-reference, not duplicated here**.
- `gdpr-foundations` / `privacy-engineering-foundations` — parallel data-protection duties (DPIA, DPbDD, security) that run alongside high-risk data governance and logging.
- `ai-act-gpai` — GPAI and systemic-risk regime feeding into high-risk value chains (planned).
- `ai-act-prohibited-practices` — Art. 5 prohibitions, incl. the new nudifier/CSAM bans (planned).
- `digital-omnibus` — the 2025–2026 simplification package in full (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Deep-dive on AI Act high-risk classification (Arts. 6–7, Annexes I/III, Art. 6(3) filter), requirements (Arts. 8–15), provider obligations and conformity chain (Arts. 16–25, 40–49, 71), and deployer obligations incl. the FRIA (Arts. 26–27). Researched against EUR-Lex (Reg (EU) 2024/1689), European Commission and European Parliament sources. **High-risk timeline / AI Omnibus adoption status live-verified: found the package has now been FORMALLY ADOPTED (EP plenary 16 Jun 2026; Council final approval 29 Jun 2026), superseding the "provisional" status recorded in `ai-act-foundations`; OJ publication pending at this date.** All external links checked HTTP 200 on 2026-07-11 (Council/Consilium 29 Jun release corroborated via EP sources, as consilium.europa.eu bot-blocks curl). | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch gate; AI Omnibus final adoption (Council 29 Jun 2026) orchestrator-verified; frozen in release 0.10.0. | Human reviewer |
