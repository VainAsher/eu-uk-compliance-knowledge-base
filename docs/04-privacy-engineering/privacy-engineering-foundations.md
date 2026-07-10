---
id: privacy-engineering-foundations
title: "Privacy Engineering: Foundations, Data Protection by Design & Default"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: Privacy Engineering
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [gdpr-foundations, uk-gdpr-foundations, eprivacy-foundations]
tags: [privacy-engineering, data-protection-by-design, article-25, article-32, pets, iso-27701, nist-privacy-framework]
legal_basis: Regulation (EU) 2016/679, Articles 25 & 32
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | privacy-engineering-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.5.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**.

# Executive Summary

**Privacy engineering** is the discipline of translating data-protection obligations into concrete system design, architecture and operational controls. Its legal anchor in the EU/UK is **GDPR Article 25 — data protection by design and by default (DPbDD)** — reinforced by **Article 32 (security of processing)** [1]. Article 25 requires controllers to embed the data-protection principles (Article 5) into processing **from the design stage and throughout the lifecycle**, and to ensure that, **by default**, only the personal data necessary for each specific purpose is processed [1][2].

This document is the implementation layer for the Tier 1 foundations (`gdpr-foundations`, `uk-gdpr-foundations`, `eprivacy-foundations`). It sets out the DPbDD obligation and the EDPB's interpretation [2], the security-of-processing requirements of Article 32 [1], the recognised **frameworks and standards** (ISO/IEC 27701, 27001, 29100; the NIST Privacy Framework) [5][6][7][8], the foundational **privacy design strategies** (Hoepman's eight: minimise, hide, separate, aggregate, inform, control, enforce, demonstrate) [9], and the main **privacy-enhancing technologies (PETs)** — pseudonymisation, anonymisation, encryption and differential privacy [1][4].

Three conclusions dominate. First, **DPbDD is a legal obligation, not best practice** — it binds all controllers regardless of size [2]. Second, **default settings carry legal weight**: the least-privacy-intrusive configuration must be the default. Third, **standards operationalise the law**: ISO/IEC 27701 and the NIST Privacy Framework give controllers a structured, auditable way to demonstrate Article 25/32 compliance and accountability [5][6]. (Note: the **NIST Privacy Framework** current published version is **1.0 (2020)**; version **1.1** is in draft, realigned with CSF 2.0, expected 2026 [5].)

# Key Takeaways

- **Article 25 (DPbDD)** is a binding obligation on all controllers: embed data protection by design from the outset, and process only necessary data by default [1][2]. *(Legal obligation.)*
- **Article 32** requires appropriate technical and organisational measures for security, expressly naming **pseudonymisation and encryption**, and confidentiality, integrity, availability and resilience [1]. *(Legal obligation.)*
- The **EDPB Guidelines 4/2019** interpret Article 25: measures must be effective, implemented before and during processing, and reviewed continually [2]. *(Regulatory interpretation.)*
- **Pseudonymised data is still personal data**; only genuine **anonymisation** removes data from GDPR scope — a distinction engineers routinely get wrong (see `gdpr-foundations`) [1]. *(Legal obligation.)*
- **Hoepman's eight privacy design strategies** (minimise, hide, separate, aggregate, inform, control, enforce, demonstrate) map obligations to architecture [9]. *(Best practice / academic.)*
- **Standards operationalise compliance:** ISO/IEC 27701 (privacy information management), ISO/IEC 27001 (security management), ISO/IEC 29100 (privacy framework) and the **NIST Privacy Framework** provide auditable structures [5][6][7][8]. *(Best practice.)*
- **PETs** — pseudonymisation, encryption, differential privacy, aggregation — reduce risk but do not by themselves discharge the accountability obligation [1][4]. *(Best practice grounded in obligation.)*
- **Default settings are a compliance surface:** shipping a product with maximal data collection "on" by default breaches Article 25(2) [1][2]. *(Legal obligation.)*

# Purpose

This document gives engineering, product and compliance teams a foundational, evidence-based account of **how** to implement the data-protection obligations established in the Tier 1 legal documents. It supports secure-by-design development, DPIA scoping, standards adoption, and the accountability evidence base. It is the bridge between "what the law requires" (`gdpr-foundations`) and "how systems must be built".

# Scope

**In scope:** The DPbDD obligation (Art. 25) and its regulatory interpretation; security of processing (Art. 32) at a foundational level; privacy design strategies; the core PETs; the principal privacy/security standards and frameworks; the anonymisation/pseudonymisation distinction.

**Out of scope (spun off to the research backlog):** DPIA methodology in depth → `dpia-methodology`; a full PETs catalogue (differential privacy, SMPC, homomorphic encryption, federated learning) → `pets-catalogue`; privacy threat modelling (e.g., LINDDUN) → `privacy-threat-modelling`; anonymisation techniques and re-identification risk → `anonymisation-techniques`; detailed ISO/NIST control mappings → `privacy-controls-mapping`.

**Assumptions:** The reader has read `gdpr-foundations` (principles, accountability) and understands controller/processor roles.

# Definitions

*Shared terms (personal data, pseudonymisation, anonymous data, controller, accountability) are defined in `GLOSSARY.md`. Only privacy-engineering-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Data protection by design (DPbD) | Implementing appropriate technical and organisational measures to embed the data-protection principles into processing, from the design stage onward (Art. 25(1)). | [1][2] |
| Data protection by default (DPbDefault) | Ensuring that, by default, only personal data necessary for each specific purpose is processed — in amount, extent of processing, retention and accessibility (Art. 25(2)). | [1][2] |
| Technical and organisational measures (TOMs) | The combined technical (e.g., encryption, access control) and organisational (e.g., policies, training) controls used to meet Arts. 25 and 32. | [1] |
| Privacy-enhancing technology (PET) | A technology that minimises personal-data processing or protects it (e.g., pseudonymisation, encryption, differential privacy, aggregation). | [1][4] |
| Privacy design strategy | A high-level approach linking data-protection goals to system architecture (Hoepman's eight strategies). | [9] |
| Differential privacy | A formal, mathematical guarantee that the inclusion or exclusion of any single individual's data does not significantly change an analysis's output. | [4][9] |

# Background

The idea that privacy should be built into systems — **"Privacy by Design"** — long predates the GDPR, but the GDPR made it a **statutory obligation** in Article 25 [1]. Privacy engineering emerged as the technical discipline that operationalises this obligation, drawing on security engineering, systems architecture and formal methods. Academic work — notably Hoepman's **privacy design strategies** — provided a bridge between legal principles and engineering practice by classifying design patterns and PETs under eight goal-oriented strategies [9]. Standards bodies followed: ISO/IEC published a **privacy framework** (29100) and a **privacy information management** extension to the ISMS standards (27701), while NIST released its **Privacy Framework** to manage privacy risk analogously to its Cybersecurity Framework [5][6][7][8].

# Legal Framework

The primary legal anchors are **Articles 25 and 32** of the GDPR (and their UK GDPR equivalents) [1]:

- **Article 25(1) — data protection by design:** taking account of the state of the art, cost, and the nature/scope/context/purposes of processing, as well as the risks, the controller shall implement appropriate TOMs (e.g., **pseudonymisation**) designed to implement the data-protection principles effectively and integrate necessary safeguards [1].
- **Article 25(2) — data protection by default:** the controller shall implement measures ensuring that, by default, only personal data necessary for each specific purpose is processed — covering the amount collected, extent of processing, retention and accessibility [1].
- **Article 32 — security of processing:** appropriate TOMs to ensure a level of security appropriate to the risk, expressly including pseudonymisation and encryption; confidentiality, integrity, availability and resilience; restoration after incidents; and a process for regularly testing effectiveness [1].

DPbDD and Article 32 operationalise the **accountability principle** (Art. 5(2)) and the security principle (Art. 5(1)(f)) established in `gdpr-foundations`.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 5(1)(f) | Integrity and confidentiality (security) principle. | [1] |
| Art. 5(2) | Accountability — demonstrate compliance (DPbDD is a key means). | [1] |
| Art. 24 | Controller responsibility to implement appropriate TOMs, reviewed and updated. | [1] |
| Art. 25(1) | Data protection by design. | [1] |
| Art. 25(2) | Data protection by default. | [1] |
| Art. 32 | Security of processing (pseudonymisation, encryption, CIA + resilience, testing). | [1] |
| Art. 35 | Data protection impact assessment (where high risk) — key privacy-engineering trigger. | [1] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 78 | DPbDD elaborated — minimisation, pseudonymisation, transparency, and enabling monitoring; producers of products/services encouraged to consider DPbDD. | [1] |
| Recital 26 | Identifiability test; anonymous data falls outside the GDPR (basis for the anonymisation/pseudonymisation distinction). | [1] |
| Recital 83 | Security — risk-based measures against accidental/unlawful destruction, loss, alteration, disclosure. | [1] |

## Relevant Case Law

Not Applicable at the foundational level — Article 25/32 obligations are elaborated primarily through **regulatory guidance** (EDPB, ICO) rather than a distinct line of foundational case law. Enforcement decisions turning on inadequate TOMs (e.g., national DPA fines for security failures) will be treated in `privacy-controls-mapping` (backlog). [2][3]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **EDPB Guidelines 4/2019** confirm DPbDD is an obligation for **all controllers**, irrespective of size; measures must be **effective** in achieving the intended data-protection outcome, implemented **before** processing begins and reviewed **continually** [2]. Cost is a permitted factor, but "state of the art" and effectiveness cannot be traded away for convenience [2]. *(Regulatory interpretation.)*
- The **ICO** frames DPbDD as considering data protection "at the start of everything you do" and integral to **accountability**; it must be embedded throughout the processing lifecycle, not bolted on [3]. *(Regulatory interpretation.)*
- Both regulators treat **default settings** as substantive: the most privacy-protective option must be the default, and users should not have to act to protect themselves [2][3]. *(Regulatory interpretation.)*
- **ENISA** provides technical guidance mapping design strategies and PETs to the DPbDD obligation, aimed at engineers [4]. *(Regulatory / technical guidance.)*

# Technical Considerations

Privacy engineering translates the above into architecture. **Hoepman's eight strategies** [9] give a practical taxonomy:

- **Minimise** — collect/retain the least data (Art. 5(1)(c), Art. 25(2)); select-before-collect, delete early.
- **Hide** — restrict visibility: encryption at rest/in transit, pseudonymisation, access control (Art. 32).
- **Separate** — distribute/partition data to prevent correlation (e.g., separate identifiers from payloads).
- **Aggregate** — process at the coarsest granularity sufficient (aggregation, k-anonymity, differential privacy) [4].
- **Inform** — transparency to data subjects (Arts. 12–14).
- **Control** — give data subjects agency (consent, preferences, rights tooling).
- **Enforce** — bind processing to a policy and enforce it technically (access policy, retention automation).
- **Demonstrate** — logging, records and evidence to prove compliance (Art. 5(2)) [9].

Core engineering practices:

- **Encryption & key management** (Art. 32) — appropriate algorithms, segregated key custody, rotation.
- **Pseudonymisation** — separate the re-identification key; treat pseudonymised data as personal data still in scope [1].
- **Retention automation** — enforce storage limitation by design (TTLs, scheduled deletion/anonymisation).
- **DPIA triggers in the SDLC** — Article 35 assessments embedded at design gates.
- **Testing** — regular testing of the effectiveness of measures is an explicit Article 32 requirement [1].

# Hosting Considerations

- **Encryption & tenancy** — encryption at rest/in transit, strong tenant isolation, and customer-controlled keys where feasible support Art. 32 [1].
- **Standards alignment** — hosting/cloud environments should map controls to **ISO/IEC 27001** (ISMS) and evidence privacy controls via **ISO/IEC 27701** (PIMS); cloud-specific PII control sets (e.g., the ISO/IEC 27018 code of practice) extend this where applicable [6][7]. *(Best practice.)*
- **Shared responsibility** — the controller retains DPbDD accountability even when infrastructure is a processor's responsibility; document the control split (see `gdpr-foundations` Hosting Considerations). *(Editorial recommendation.)*
- **Data locality & minimisation** — architect so that only necessary data is replicated across regions; over-replication undermines Art. 25(2). *(Best practice.)*

# Game Hosting Considerations

- **Telemetry minimisation** — games generate high-volume telemetry; apply the *minimise* and *aggregate* strategies (sample, aggregate, pseudonymise player analytics) [9]. *(Best practice grounded in Art. 25(2).)*
- **Default privacy for players** — matchmaking, profile visibility and social features should default to the least-exposing setting, especially for likely-child users (Art. 25(2); children's codes — see `uk-gdpr-foundations`) [1]. *(Legal obligation.)*
- **Pseudonymised player IDs** — separate durable account identifiers from behavioural payloads; retain re-identification keys separately [1]. *(Best practice.)*
- **Anti-cheat & moderation data** — often sensitive; apply *hide* (encryption, access control) and strict retention. *(Best practice.)*

# AI Considerations

- **Minimisation vs. model appetite** — the central privacy-engineering tension for AI; mitigate with **aggregation, pseudonymisation, synthetic data, differential privacy and federated learning** [4][9]. *(Best practice.)*
- **Differential privacy** — provides a formal privacy guarantee for model training/analytics, bounding the influence of any single record [4]. *(Best practice; detailed in `pets-catalogue`.)*
- **DPbDD for AI pipelines** — apply Article 25 across the ML lifecycle (data collection, training, inference, logging); default to not retaining raw training inputs longer than necessary [1][2]. *(Legal obligation.)*
- **Overlap with the AI Act** — technical risk-management and data-governance duties under the AI Act complement Article 25; covered in `ai-act-foundations` / `ai-governance-foundations` (backlog). *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Embed DPbDD in the SDLC** — design gates, DPIA triggers, privacy requirements in tickets. *(OBLIGATION.)* [1][2]
2. **Default to least data** — ship the most privacy-protective configuration by default. *(OBLIGATION.)* [1][2]
3. **Apply Article 32 controls** — encryption, pseudonymisation, access control, resilience, and **regular effectiveness testing**. *(OBLIGATION.)* [1]
4. **Adopt a framework** — implement ISO/IEC 27701 and/or the NIST Privacy Framework to structure and evidence controls. *(BEST PRACTICE.)* [5][6]
5. **Use privacy design strategies** — apply the eight strategies as a design checklist. *(BEST PRACTICE.)* [9]
6. **Distinguish anonymisation from pseudonymisation** — do not treat pseudonymised data as out of scope. *(OBLIGATION.)* [1]
7. **Evidence everything** — the *demonstrate* strategy: logs, records, DPIAs, control mappings for accountability. *(OBLIGATION + BEST PRACTICE.)* [9]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | DPbDD not embedded; privacy bolted on late | High | High | Art. 25; EDPB 4/2019 [1][2] | Design gates; DPIA in SDLC | Medium |
| R2 | Over-collecting defaults (privacy off by default) | High | High | Art. 25(2) [1][2] | Least-data defaults; config review | Low |
| R3 | Treating pseudonymised data as anonymous | Medium | High | Recital 26; Art. 4(5) [1] | Identifiability assessment; scope it in | Low |
| R4 | Weak/absent encryption or key management | Medium | High | Art. 32 [1] | Encryption + segregated key custody | Low |
| R5 | No testing of measure effectiveness | Medium | Medium | Art. 32(1)(d) [1] | Scheduled control testing; pentest | Low |
| R6 | No structured framework → poor accountability evidence | Medium | Medium | Art. 5(2) [1] | Adopt ISO 27701 / NIST PF | Low |
| R7 | PETs assumed to discharge all obligations | Medium | Medium | Art. 5(2) [1][4] | Treat PETs as controls, not compliance proof | Low |

# Implementation Roadmap

- **Phase 0 — Baseline:** Map processing to Article 5 principles; identify high-risk processing (DPIA candidates). *Effort:* Medium.
- **Phase 1 — DPbDD in SDLC:** Add privacy requirements, design gates and default-setting reviews. *Effort:* Medium.
- **Phase 2 — Security controls (Art. 32):** Encryption, key management, access control, resilience, effectiveness testing. *Effort:* High.
- **Phase 3 — Framework adoption:** Implement ISO/IEC 27701 and/or NIST Privacy Framework; build the control-to-principle mapping. *Effort:* High.
- **Phase 4 — PETs & advanced:** Introduce aggregation/differential privacy where minimisation alone is insufficient. *Effort:* Medium–High.
- **Phase 5 — Assurance:** Continuous testing, audits, metrics; DPIA cadence. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Privacy considered late or reactively; no defaults discipline. | Ad hoc controls; privacy off by default. |
| 2 | Managed | Some security controls; DPIAs done inconsistently. | Encryption in places; partial DPIAs. |
| 3 | Defined | DPbDD in the SDLC; least-data defaults; framework adopted. | Design gates; ISO 27701/NIST PF in use. |
| 4 | Quantitatively Managed | Metrics on control effectiveness, DPIA coverage, incident rates. | KPIs; regular effectiveness testing. |
| 5 | Optimising | Automated enforcement; PETs where needed; continuous assurance. | Automated retention/anonymisation; DP guarantees; independent audit. |

# Audit Questions

1. How is data protection by design embedded in your development lifecycle? *(Art. 25(1) [1][2].)*
2. What are the default settings for new users/records, and why are they the least-intrusive option? *(Art. 25(2) [1][2].)*
3. Which Article 32 measures (encryption, pseudonymisation, access control, resilience) are implemented, and how is effectiveness tested? *(Art. 32 [1].)*
4. How do you distinguish pseudonymised from anonymised data, and how is re-identification risk assessed? *(Recital 26; Art. 4(5) [1].)*
5. Which framework (ISO/IEC 27701, NIST Privacy Framework) structures your privacy controls, and where is the evidence? *(Accountability [5][6].)*
6. How are DPIAs triggered and integrated with engineering? *(Art. 35 [1].)*
7. Where PETs are used (e.g., differential privacy), what guarantee do they provide and what residual risk remains? *([4][9].)*

# Implementation Checklist

- [ ] Privacy requirements and DPIA triggers embedded in the SDLC (Art. 25(1)).
- [ ] Default settings set to least-data / least-exposure (Art. 25(2)).
- [ ] Article 32 controls implemented: encryption, pseudonymisation, access control, resilience.
- [ ] Regular testing of measure effectiveness scheduled (Art. 32(1)(d)).
- [ ] Pseudonymised vs anonymised data classified; re-identification risk assessed.
- [ ] A privacy/security framework adopted (ISO/IEC 27701 and/or NIST Privacy Framework).
- [ ] Privacy design strategies applied as a design checklist.
- [ ] Accountability evidence maintained (logs, records, control-to-principle mapping).
- [ ] PETs evaluated where minimisation alone is insufficient (aggregation, differential privacy).

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Articles 24, 25, 32, 35 and Recitals 26, 78, 83. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504

## Regulatory Guidance

- [2] **Guidelines 4/2019 on Article 25 — Data Protection by Design and by Default** (v2.0). European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-42019-article-25-data-protection-design-and_en
- [3] **Data protection by design and by default.** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/guide-to-accountability-and-governance/data-protection-by-design-and-by-default/
- [4] **Privacy and Data Protection by Design — from policy to engineering.** ENISA. https://www.enisa.europa.eu/publications/privacy-and-data-protection-by-design
- [5] **NIST Privacy Framework** (v1.0, 2020; v1.1 in draft, realigned with CSF 2.0, expected 2026). NIST. https://www.nist.gov/privacy-framework — v1.0 PDF: https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.01162020.pdf

## Standards

- [6] **ISO/IEC 27701** — Privacy Information Management System (extension to ISO/IEC 27001/27002). ISO. https://www.iso.org/standard/71670.html
- [7] **ISO/IEC 27001:2022** — Information Security Management Systems. ISO. https://www.iso.org/standard/27001
- [8] **ISO/IEC 29100** — Information technology — Security techniques — Privacy framework. ISO. https://www.iso.org/standard/45123.html

## Academic Sources

- [9] **Hoepman, J.-H. (2014). "Privacy Design Strategies."** In: ICT Systems Security and Privacy Protection (IFIP SEC 2014), Springer. Also arXiv:1210.6621. https://arxiv.org/abs/1210.6621 — Springer: https://link.springer.com/chapter/10.1007/978-3-642-55415-5_38

# Further Reading

*Non-authoritative; provided for orientation only.*

- NIST Privacy Framework program and resources. https://www.nist.gov/privacy-framework
- ENISA — privacy and data protection publications. https://www.enisa.europa.eu/publications

# Related Documents

- `gdpr-foundations` — principles, accountability, anonymisation/pseudonymisation (**prerequisite reading**).
- `uk-gdpr-foundations` — UK equivalents (Art. 25/32 apply under the UK GDPR).
- `eprivacy-foundations` — consent/tracking design constraints.
- `dpia-methodology` — DPIA process in depth (planned).
- `pets-catalogue` — PETs incl. differential privacy, SMPC, federated learning (planned).
- `privacy-threat-modelling` — LINDDUN and privacy threat modelling (planned).
- `anonymisation-techniques` — anonymisation and re-identification risk (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Arts. 25/32), EDPB Guidelines 4/2019, ICO, ENISA, NIST Privacy Framework, ISO standards and Hoepman (academic). NIST PF version status live-verified. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at human review gate; removed unsourced ISO/IEC 27018 citation; frozen in release 0.5.0. Completes Tier 1. | Human reviewer |
