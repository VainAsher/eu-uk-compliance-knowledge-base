---
id: nis2-foundations
title: "NIS2 Directive: Foundations, Scope & Cybersecurity Obligations"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: NIS2
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [dora-foundations, dsa-foundations, ai-act-foundations, gdpr-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [nis2, nis2-directive, cybersecurity, essential-entities, important-entities, incident-reporting, risk-management, transposition, dora, cyber-resilience-act]
legal_basis: Directive (EU) 2022/2555
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | nis2-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.8.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. NIS2 is a **Directive**, so the binding rules that apply to any organisation are the **national transposition laws**, not the Directive text directly — and transposition is **incomplete and still moving**: as at this document's date the Commission has **referred four Member States (Ireland, Spain, France, the Netherlands) to the Court of Justice** (8–9 July 2026) for non-transposition [8]. Always confirm the current national law and its exact obligations for each Member State in which an entity operates before relying on this document.

# Executive Summary

The **NIS2 Directive (Directive (EU) 2022/2555**, "NIS2") is the EU's second-generation, horizontal cybersecurity law for network and information systems. It **repealed and replaced the original NIS Directive ((EU) 2016/1148) with effect from 18 October 2024** and pursues a **high common level of cybersecurity across the Union** by widening the range of covered sectors, harmonising **risk-management** and **incident-reporting** duties, and sharpening **supervision, governance accountability and enforcement** [1][5]. Because it is a **Directive**, it binds Member States as to the result but must be **transposed** into national law to take effect against organisations [1].

NIS2 sorts in-scope organisations into **essential entities** and **important entities** drawn from **18 sectors** listed in **Annex I (high criticality)** and **Annex II (other critical sectors)**, generally using a **size-cap rule** (medium-sized and large entities), with a number of entity types in scope **regardless of size** [1][5]. Covered entities must implement **cybersecurity risk-management measures** on an all-hazards basis — a minimum list of ten measure categories in **Article 21** — and report **significant incidents** through the **Article 23 cascade**: an **early warning within 24 hours**, an **incident notification within 72 hours**, and a **final report within one month** [1]. **Article 20** makes **management bodies** approve and oversee those measures and requires them to undergo **training**. Supervision and penalties are **differentiated**: essential entities face proactive (ex ante and ex post) supervision, important entities face reactive (ex post) supervision, and administrative fines run to **at least €10m or 2% of worldwide annual turnover** for essential entities and **at least €7m or 1.4%** for important entities [1].

The single most important — and most volatile — point is **transposition status**. The deadline was **17 October 2024**; most Member States missed it. The Commission opened infringement proceedings (letters of formal notice, November 2024; reasoned opinions to 19 Member States, 7 May 2025) and, on **8–9 July 2026, referred Ireland, Spain, France and the Netherlands to the Court of Justice**, asking for **lump-sum and daily financial penalties** until each notifies full transposition [6][7][8]. NIS2 also sits alongside sibling instruments: **DORA** is **lex specialis** for the financial sector, and the **Cyber Resilience Act** covers the security of products with digital elements [2][3].

# Key Takeaways

- **NIS2 (Directive (EU) 2022/2555)** repealed the original NIS Directive **with effect from 18 October 2024** and aims for a **high common level of cybersecurity** across the EU; being a Directive, it applies through **national transposition** [1][5]. *(Legal obligation.)*
- In-scope organisations are classified as **essential** or **important** entities across **18 sectors** in **Annex I** and **Annex II**, generally caught by a **medium/large size-cap**, with some entity types in scope **regardless of size** [1][5]. *(Legal obligation.)*
- **Article 21** requires **all-hazards cybersecurity risk-management measures** — a minimum of **ten categories** (incident handling, business continuity, **supply-chain security**, vulnerability handling, cyber hygiene and training, cryptography, access control, MFA, etc.) [1]. *(Legal obligation.)*
- **Article 23** imposes a staged reporting duty for **significant incidents**: **early warning within 24 hours**, **notification within 72 hours**, and a **final report within one month** [1]. *(Legal obligation.)*
- **Article 20** makes **management bodies accountable** — they must **approve and oversee** the risk-management measures and undergo **training** [1]. *(Legal obligation.)*
- Supervision and penalties are **differentiated**: essential entities get **ex ante + ex post** supervision, important entities **ex post only**; fines reach **≥ €10m or 2%** of worldwide turnover (essential) and **≥ €7m or 1.4%** (important) [1]. *(Legal obligation.)*
- **Live-verified transposition status:** the deadline (**17 October 2024**) was widely missed; on **8–9 July 2026** the Commission **referred Ireland, Spain, France and the Netherlands to the Court of Justice** (with a request for financial penalties), following reasoned opinions to 19 Member States on 7 May 2025 [6][7][8]. *(Confirmed today, not asserted — status is dynamic.)*
- NIS2 interacts with sibling law: **DORA is lex specialis** for finance (Art. 4 equivalence), and the **Cyber Resilience Act** governs security of **products with digital elements** [1][2][3]. *(Legal obligation / cross-reference.)*

# Purpose

This document is the Tier 3 entry point for the NIS2 Directive. It supports legal research (mapping scope, entity classification and the core obligation set), compliance planning (determining whether an organisation is in scope, in which sector and tier, and what it must do), and product/engineering triage (risk-management controls, incident-reporting readiness, governance). It sits alongside `dora-foundations` (the financial-sector lex specialis) and complements the wider EU digital rulebook (`dsa-foundations`, `ai-act-foundations`, `gdpr-foundations`).

# Scope

**In scope:** NIS2's purpose and legal character (Directive vs Regulation); the essential/important entity distinction; the Annex I/II sectors and the size-cap thresholds; the Article 21 cybersecurity risk-management measures; the Article 23 incident-reporting cascade and timelines; Article 20 governance and management-body accountability and training; registration duties; the differentiated supervision and enforcement/penalty regime; the current state of national transposition (**live-verified**); and the relationship to DORA and the Cyber Resilience Act at a foundational level.

**Out of scope (spun off to the research backlog):** The full **incident-reporting mechanics** and the Commission Implementing Regulation (EU) 2024/2690 detail (significant-incident thresholds, technical/methodological requirements for digital sectors) → `nis2-incident-reporting`; **sector-specific duties** and the Annex I/II sector-by-sector analysis → `nis2-sectors`; a **national transposition comparison** across Member States → `nis2-transposition-tracker`; the **Article 21 measures mapped to ISO/IEC 27001 and NIST CSF** control-by-control → `nis2-controls-mapping`; the **DORA/NIS2 boundary** in depth → `dora-foundations`; the **Critical Entities Resilience (CER) Directive** companion regime → `cer-foundations`.

**Assumptions:** The reader understands the EU **Directive vs Regulation** distinction (a Directive requires national transposition; a Regulation is directly applicable). Where an entity processes personal data, the **GDPR applies in parallel** (see `gdpr-foundations`); a personal-data breach may trigger both NIS2 incident reporting and GDPR Art. 33 notification.

# Definitions

*Shared terms are in `GLOSSARY.md`. NIS2-specific terms are defined here; deeper terms (significant incident thresholds, sector sub-definitions) are deferred to the backlog documents above.*

| Term | Definition | Source |
|------|------------|--------|
| Essential entity | An entity classified as "essential" under Art. 3(1) — broadly, large entities in the Annex I high-criticality sectors plus specified types in scope regardless of size (e.g., qualified trust service providers, TLD name registries, DNS providers, certain public-administration and critical entities). Subject to the fullest supervision. | [1] |
| Important entity | An entity within scope that is not an essential entity (Art. 3(2)) — typically medium-sized entities in Annex I sectors and entities in the Annex II "other critical" sectors. Subject to ex-post supervision. | [1] |
| Network and information system | An electronic communications network, any device or group of interconnected devices processing digital data, or the digital data such systems process/store/transmit for their operation, use, protection and maintenance (Art. 6(1)). | [1] |
| Significant incident | An incident that has caused or is capable of causing severe operational disruption of services or financial loss, or that has affected or is capable of affecting other persons by causing considerable material or non-material damage (Art. 23(3)). | [1] |
| Cybersecurity risk-management measures | The all-hazards technical, operational and organisational measures required by Art. 21 to manage risks to network and information systems and prevent/minimise incident impact. | [1] |
| Management body | The body (e.g., board/senior management) that under Art. 20 must approve the entity's risk-management measures, oversee their implementation, and follow training; members may be held liable. | [1] |
| CSIRT | A Computer Security Incident Response Team designated by each Member State (Art. 10) to which entities submit incident reports and which provides response support. | [1] |

# Background

The original **NIS Directive ((EU) 2016/1148)** was the EU's first horizontal cybersecurity law, but it left significant gaps: inconsistent national scoping of "operators of essential services", divergent security and reporting requirements, and weak supervision and enforcement. As dependence on digital infrastructure and the frequency of cross-border cyber incidents grew, the EU replaced it with **NIS2** to raise and harmonise the baseline [1][5]. NIS2 **broadens the sectoral scope**, replaces the old operator-identification approach with a **size-cap rule** plus **essential/important** tiers, **standardises** risk-management and incident-reporting duties, introduces **management-body accountability**, and materially **strengthens supervision and penalties** [1][5]. It was adopted on **14 December 2022**, entered into force on **16 January 2023**, and **repealed the NIS Directive with effect from 18 October 2024**, with a **transposition deadline of 17 October 2024** [1]. It forms part of a wider EU cyber and resilience package alongside **DORA** (finance), the **Cyber Resilience Act** (products), and the **Critical Entities Resilience (CER) Directive** (physical resilience) [1][2][3].

# Legal Framework

NIS2 is a **Directive**: it sets out the obligations Member States must achieve, but the **legally binding rules for organisations are the national transposition measures** [1]. Its structure:

- **Chapter I (Arts. 1–6)** — subject matter, scope, definitions, and the relationship with sector-specific EU acts (**Art. 4** equivalence / lex specialis).
- **Chapter II (Arts. 7–13)** — national cybersecurity frameworks: strategies, competent authorities, single points of contact, **CSIRTs**, and cooperation.
- **Chapter III (Arts. 14–19)** — EU-level cooperation: the **Cooperation Group**, the **CSIRTs network**, **EU-CyCLONe** (crisis coordination), peer reviews.
- **Chapter IV (Arts. 20–25)** — the **core obligations on entities**: **governance (Art. 20)**, **cybersecurity risk-management measures (Art. 21)**, coordinated risk assessments of critical supply chains (Art. 22), **reporting obligations (Art. 23)**, use of European cybersecurity **certification** schemes (Art. 24), and **standardisation** (Art. 25).
- **Chapter V (Arts. 26–27)** — **jurisdiction and territoriality** (Art. 26) and the **registry of entities** maintained by ENISA for certain digital service types (Art. 27).
- **Chapter VII (Arts. 31–37)** — **supervision and enforcement**: supervisory measures for **essential entities (Art. 32)** and **important entities (Art. 33)**, and **administrative fines (Art. 34)**.
- Scope is fixed by **Art. 2** together with **Annex I** (high-criticality sectors) and **Annex II** (other critical sectors); entity classification is in **Art. 3**.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 2 + Annexes I, II | Scope: sectors covered and the size-cap rule (medium/large), with entities in scope regardless of size in defined cases. | [1] |
| Art. 3 | Classification of entities as **essential** or **important**. | [1] |
| Art. 3(4) | Member States establish and maintain a **list of essential and important entities** (deadline 17 April 2025). | [1] |
| Art. 4 | Relationship with sector-specific EU acts — where equivalent, those apply as **lex specialis** (e.g., DORA for finance). | [1][2] |
| Art. 20 | **Governance** — management bodies approve and oversee risk-management measures and must undergo **training**; liability for infringements. | [1] |
| Art. 21 | **Cybersecurity risk-management measures** — all-hazards approach; minimum list of ten measure categories, incl. supply-chain security. | [1] |
| Art. 22 | Union-level coordinated security risk assessments of critical ICT supply chains. | [1] |
| Art. 23 | **Reporting obligations** for significant incidents — **24h early warning, 72h notification, 1-month final report**; recipient notification. | [1] |
| Art. 24 | Use of European cybersecurity **certification** schemes (may be mandated by implementing act). | [1] |
| Art. 26 | Jurisdiction and territoriality (main-establishment rule for certain digital providers). | [1] |
| Art. 27 | **Registration** — ENISA registry for DNS, TLD, cloud, data-centre, CDN, managed (security) service providers and online marketplaces/search/social. | [1] |
| Art. 32 | Supervisory and enforcement measures for **essential entities** (ex ante + ex post). | [1] |
| Art. 33 | Supervisory and enforcement measures for **important entities** (ex post only). | [1] |
| Art. 34 | **Administrative fines** — essential: max ≥ €10m or 2% worldwide turnover; important: max ≥ €7m or 1.4%. | [1] |
| Art. 41 | **Transposition** — Member States adopt and publish measures by **17 October 2024**, applying them from **18 October 2024**. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited here from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 4 | Purpose — remove divergences by setting minimum rules for a coordinated regulatory framework and improving the functioning of the internal market. | [1] |
| Recital 8 | The original NIS Directive's shortcomings (fragmented scope and supervision) motivating the reform. | [1] |
| Recital 28 area | Relationship with sector-specific Union acts and the equivalence/lex specialis mechanism (e.g., DORA). | [1] |
| Recital 79 area | Incident-reporting design — the multi-stage approach balancing rapid warning against complete information. | [1] |

## Relevant Case Law

**Not Applicable at the foundational level.** NIS2 is recent and, as a Directive whose substantive obligations bite through national law, there is no settled CJEU case law interpreting its risk-management or reporting provisions. The only NIS2 litigation to date concerns **enforcement of the transposition duty against Member States** — the Commission's referrals of Ireland, Spain, France and the Netherlands to the Court of Justice (July 2026) are **infringement actions under Art. 258/260 TFEU**, not interpretations of the substantive obligations, and are tracked as **emerging** rather than asserted here [8]. [1]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames NIS2 as a **unified legal framework to uphold cybersecurity in 18 critical sectors**, requiring medium-sized and large entities in those sectors to take risk-management measures and notify significant incidents [5]. *(Regulatory interpretation.)*
- **ENISA** supports implementation with **technical guidance** — notably its *Technical Implementation Guidance on cybersecurity risk-management measures*, which maps the Art. 21 measures (as specified for certain digital sectors by the Implementing Regulation) to actionable evidence and controls [9][10]. *(Regulatory guidance — supports, does not replace, national law.)*
- **Commission Implementing Regulation (EU) 2024/2690 (17 October 2024)** lays down **technical and methodological requirements** for the Art. 21(2) measures and specifies when an incident is **"significant"** for defined digital-infrastructure, ICT-service-management and digital-provider entities (DNS, TLD, cloud, data centres, CDNs, managed and managed-security service providers, online marketplaces/search engines/social platforms, trust service providers) [4]. *(Legal obligation for those entity types; regulatory specification of Art. 21/23.)*
- **Transposition is incomplete and enforced:** the Commission's own **transposition state-of-play** page records which Member States have and have not notified full transposition (a **dynamic list**), and its infringement track — **formal notices (Nov 2024) → reasoned opinions to 19 Member States (7 May 2025) → CJEU referrals of four Member States (8–9 July 2026)** — shows active enforcement [6][7][8]. *(Regulatory interpretation — verify the live list per Member State.)*

# Technical Considerations

- **Scope triage first** — determine whether the organisation meets the **size-cap** (or is in scope regardless of size), which **Annex I/II sector(s)** it falls in, and whether it is **essential or important**; this drives every downstream duty and the supervision tier [1][5]. *(Legal obligation.)*
- **All-hazards control set (Art. 21)** — implement the ten measure categories: risk-analysis and information-system security policies; **incident handling**; **business continuity, backup and disaster recovery, crisis management**; **supply-chain security**; security in acquisition/development/maintenance incl. **vulnerability handling and disclosure**; policies to assess measure effectiveness; **basic cyber hygiene and security training**; **cryptography/encryption** policies; **HR security, access control and asset management**; and **multi-factor authentication**, secured voice/video/text and secured emergency communications [1]. *(Legal obligation.)*
- **Standards alignment** — the Art. 21 measures map naturally onto **ISO/IEC 27001:2022** (ISMS) and **NIST CSF 2.0**; using a recognised framework provides evidence of the "appropriate and proportionate" standard and eases audits, though it does not by itself satisfy national law [11][12]. *(Best practice.)*
- **Incident-reporting pipeline** — build the capability to detect a **significant incident** and emit a **24h early warning**, a **72h notification** (with initial severity/impact assessment and indicators of compromise) and a **1-month final report** to the CSIRT/competent authority, plus **recipient notification** where required (Art. 23) [1]. *(Legal obligation.)*
- **Digital-sector specifics** — entities within the Implementing Regulation (EU) 2024/2690 scope should engineer to its **detailed technical requirements** and **significant-incident thresholds** rather than the Directive's general wording [4]. *(Legal obligation for those entities.)*

# Hosting Considerations

- **Cloud, data-centre, CDN and hosting providers are squarely in scope** — "digital infrastructure" and "ICT service management (B2B)" are **Annex I high-criticality sectors**; cloud computing service providers, data-centre service providers, content-delivery-network providers and managed/managed-security service providers are named entity types, and several must **register with ENISA under Art. 27** [1]. *(Legal obligation — assess role.)*
- **Registration and jurisdiction** — for certain digital providers, **Art. 26** fixes jurisdiction by **main establishment** (broadly, where cybersecurity decisions are taken) and **Art. 27** requires submission of registration details to ENISA; multi-country hosting operators should identify their **main establishment** and the **competent authority/CSIRT** accordingly [1]. *(Legal obligation.)*
- **Supply-chain security flows downstream** — because Art. 21(2)(d)/(e) require **supply-chain and product/service security**, in-scope customers will impose NIS2-driven contractual and assurance requirements on their hosting and managed-service providers; providers should expect **security clauses, evidence requests and incident-cooperation duties** [1]. *(Legal obligation for the customer; best practice for providers to anticipate.)*
- **Logging and evidence** — incident-reporting and supervisory-audit duties require robust **logging, detection and retention**; align retention with **GDPR** limits where personal data is involved (see `gdpr-foundations`). *(Best practice.)*

# Game Hosting Considerations

- **Most pure game-hosting is not directly in NIS2 scope** — online gaming and entertainment are **not** among the Annex I/II sectors, so a studio or game-server operator is generally **not** an essential/important entity *by virtue of gaming alone* [1][5]. *(Interpretation.)*
- **But underlying infrastructure roles can pull an operator in** — if the operator also provides **cloud computing, data-centre, CDN or managed-security services**, or is a **DNS/domain-registration** provider, those **digital-infrastructure/ICT** activities are in scope regardless of the gaming context [1]. *(Legal obligation — assess by activity, not by industry label.)*
- **Third-party dependency risk** — even when out of direct scope, game hosts rely on cloud/CDN/managed providers that **are** in scope; their NIS2 **supply-chain security** duties will propagate as contractual security and incident-cooperation requirements [1]. *(Best practice — expect and prepare for these.)*
- **Watch adjacent regimes** — player-facing platforms may separately engage the **DSA** (if they store and disseminate user content to the public) and the **GDPR**; NIS2 does not displace those. *(Cross-reference.)*

# AI Considerations

- **AI/ML systems are network and information systems** — where an in-scope entity operates AI systems, those systems fall within the **all-hazards Art. 21** risk-management duty (data security, access control, vulnerability handling, robustness), so AI security is part of NIS2 compliance, not separate from it [1]. *(Legal obligation.)*
- **Overlap with the AI Act** — for **high-risk AI systems**, the AI Act's **accuracy, robustness and cybersecurity** requirements run in parallel with NIS2's entity-level duties; an organisation may owe both. See `ai-act-foundations`. *(Cross-reference.)*
- **AI in incident detection** — AI-driven detection and response can help meet the tight **Art. 23** timelines, but automated triage must not delay the **24h/72h** clock or degrade the accuracy of reports [1]. *(Best practice.)*
- **GDPR overlap** — where AI processes personal data, the **GDPR applies in full**; a security incident may trigger **both** NIS2 Art. 23 reporting and GDPR Art. 33 breach notification, on **different clocks and to different authorities** [1]. *(Legal obligation — run both.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Determine scope and tier** — assess size-cap, Annex I/II sector and essential/important classification for **each Member State of operation**, and identify the competent authority/CSIRT. *(OBLIGATION — foundational.)* [1][5]
2. **Confirm the applicable national law** — because NIS2 binds through transposition, identify the **transposing statute** in each relevant Member State; where none is in force yet, track its progress (transposition is incomplete). *(OBLIGATION where transposed; EDITORIAL RECOMMENDATION to track where not.)* [1][6][8]
3. **Register where required** — submit Art. 27 registration details (and comply with any Art. 3(4) national listing) for in-scope digital service types. *(OBLIGATION.)* [1]
4. **Implement the Art. 21 measures** — stand up the ten measure categories on an all-hazards basis, ideally mapped to ISO/IEC 27001 / NIST CSF. *(OBLIGATION; BEST PRACTICE for the mapping.)* [1][11][12]
5. **Build the Art. 23 reporting capability** — detection, severity assessment, and the **24h / 72h / 1-month** report flow to the CSIRT, plus recipient notification. *(OBLIGATION.)* [1]
6. **Engage the management body** — secure board approval and oversight of the measures and complete Art. 20 **training**; document accountability. *(OBLIGATION.)* [1]
7. **Address supply-chain security** — impose and evidence security requirements on ICT suppliers and service providers (Art. 21(2)(d)/(e)). *(OBLIGATION.)* [1]
8. **Apply the digital-sector implementing rules** — where in scope, engineer to Implementing Regulation (EU) 2024/2690's technical requirements and significant-incident thresholds. *(OBLIGATION for those entities.)* [4]
9. **Map overlaps** — where DORA applies, treat it as **lex specialis** (Art. 4); coordinate NIS2 and GDPR breach processes; watch CRA product duties. *(OBLIGATION + cross-reference.)* [1][2][3]
10. **Track transposition and enforcement** — monitor the Commission's state-of-play page and infringement actions; adjust to each national law as it lands. *(EDITORIAL RECOMMENDATION.)* [6][8]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Wrongly concluding the organisation is out of scope | Medium | High | Art. 2, Annexes I/II [1] | Documented scope/tier assessment per Member State | Low |
| R2 | Relying on the Directive where national law differs or is absent | Medium | High | Directive character; transposition gaps [1][6] | Track/confirm transposing statute per Member State | Medium |
| R3 | Incomplete Art. 21 measures (e.g., no supply-chain or vulnerability handling) | Medium | High | Art. 21(2) [1] | Gap-assess against Art. 21 + ISO 27001/NIST CSF | Low |
| R4 | Missing the 24h/72h/1-month reporting deadlines | Medium | High | Art. 23 [1] | Incident runbook; pre-drafted report templates; drills | Low |
| R5 | Management body not engaged/trained | Medium | Medium | Art. 20 [1] | Board approval, oversight cadence, documented training | Low |
| R6 | Failure to register (Art. 27) or appear on national list (Art. 3(4)) | Medium | Medium | Arts. 3(4), 27 [1] | Complete ENISA/national registration | Low |
| R7 | Treating DORA and NIS2 as duplicative rather than lex specialis | Low | Medium | Art. 4 [1][2] | Map financial-entity duties to DORA as lex specialis | Low |
| R8 | Under-managing supplier/third-party cyber risk | Medium | High | Art. 21(2)(d)/(e) [1] | Supplier security clauses, assurance, incident cooperation | Medium |

# Implementation Roadmap

- **Phase 0 — Scope & tier assessment:** Determine in-scope status, sector, essential/important tier, and competent authority/CSIRT per Member State. *Effort:* Medium.
- **Phase 1 — Legal baseline:** Identify the transposing national law (or its status) for each relevant Member State; complete Art. 3(4)/Art. 27 registration. *Effort:* Medium.
- **Phase 2 — Risk-management measures:** Implement the Art. 21 ten-category control set, mapped to ISO/IEC 27001 / NIST CSF; close gaps. *Effort:* High.
- **Phase 3 — Incident reporting:** Build detection, severity assessment and the 24h/72h/1-month reporting workflow; run tabletop drills. *Effort:* Medium.
- **Phase 4 — Governance:** Board approval and oversight of measures; management-body training; documented accountability. *Effort:* Medium.
- **Phase 5 — Supply chain & overlaps:** Supplier security programme; coordinate DORA (finance), GDPR breach and CRA product duties. *Effort:* High.
- **Phase 6 — Monitor & adapt:** Track transposition/enforcement and the Implementing Regulation guidance; adjust to national law. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Scope unknown; no NIS2 mapping. | No scope assessment; ad-hoc security. |
| 2 | Managed | Scope/tier assessed; basic Art. 21 measures and an incident process exist. | Scope register; incident runbook drafted. |
| 3 | Defined | Full Art. 21 control set implemented and mapped to a standard; 24h/72h/1-month reporting operational; registration done. | ISO/CSF mapping; drills run; ENISA/national registration. |
| 4 | Quantitatively Managed | Metrics on detection, reporting timeliness and supplier assurance; board oversight cadence. | KPIs on MTTR/report timeliness; supplier scorecards. |
| 5 | Optimising | Integrated NIS2 + DORA/GDPR/CRA governance; continuous improvement and independent assurance. | Cross-regime programme; audits; management-body training embedded. |

# Audit Questions

1. How was in-scope status, sector and essential/important tier determined, and for which Member States? *(Art. 2–3, Annexes I/II [1].)*
2. Which transposing national law applies in each Member State of operation, and how is its status tracked where not yet in force? *(Directive character; Art. 41 [1][6].)*
3. Are all ten Art. 21 measure categories implemented, and how are they evidenced (e.g., ISO/IEC 27001, NIST CSF)? *(Art. 21 [1][11][12].)*
4. How does the organisation meet the 24h early warning, 72h notification and 1-month final-report deadlines? *(Art. 23 [1].)*
5. How does the management body approve and oversee the measures, and what training has it completed? *(Art. 20 [1].)*
6. Has the entity registered where required (Art. 27) and been listed under Art. 3(4)? *([1].)*
7. How is supply-chain and supplier cyber risk managed and evidenced? *(Art. 21(2)(d)/(e) [1].)*
8. Where DORA applies, how are financial-entity duties treated as lex specialis, and how are GDPR breach obligations coordinated? *(Art. 4 [1][2].)*

# Implementation Checklist

- [ ] Scope, sector and essential/important tier assessed per Member State.
- [ ] Transposing national law identified (or status tracked) for each relevant Member State.
- [ ] Art. 27 registration and Art. 3(4) national listing completed where required.
- [ ] Art. 21 ten-category risk-management measures implemented and mapped to ISO/IEC 27001 / NIST CSF.
- [ ] Incident detection and the 24h / 72h / 1-month Art. 23 reporting workflow operational and drilled.
- [ ] Recipient-notification process in place for significant incidents.
- [ ] Management body has approved and oversees the measures and completed Art. 20 training.
- [ ] Supply-chain security requirements imposed on and evidenced from ICT suppliers.
- [ ] Digital-sector Implementing Regulation (EU) 2024/2690 requirements applied where in scope.
- [ ] DORA (lex specialis for finance), GDPR breach and CRA product duties mapped and coordinated.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Directive (EU) 2022/2555 (NIS2 Directive).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj
- [2] **Regulation (EU) 2022/2554 (DORA).** EUR-Lex, ELI (lex specialis for the financial sector under NIS2 Art. 4). https://eur-lex.europa.eu/eli/reg/2022/2554/oj
- [3] **Regulation (EU) 2024/2847 (Cyber Resilience Act).** EUR-Lex, ELI (cybersecurity of products with digital elements). https://eur-lex.europa.eu/eli/reg/2024/2847/oj
- [4] **Commission Implementing Regulation (EU) 2024/2690** — technical and methodological requirements for Art. 21(2) measures and significant-incident specification for certain digital entities. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_impl/2024/2690/oj

## Regulatory Guidance

- [5] **NIS2 Directive: securing network and information systems.** European Commission, Shaping Europe's Digital Future (18 critical sectors; risk-management and reporting overview). https://digital-strategy.ec.europa.eu/en/policies/nis2-directive
- [6] **NIS2 Directive transposition in EU countries** (state-of-play of Member State transposition; last updated 1 July 2025 — dynamic). European Commission. https://digital-strategy.ec.europa.eu/en/policies/nis-transposition
- [7] **Commission calls on 19 Member States to fully transpose the NIS2 Directive** (reasoned opinions, 7 May 2025). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-calls-19-member-states-fully-transpose-nis2-directive
- [8] **Commission refers Ireland, Spain, France and the Netherlands to the Court of Justice for failing to transpose the rules on cybersecurity** (IP/26/1499, 8–9 July 2026; request for lump-sum and daily penalties). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_26_1499
- [9] **NIS Directive 2 (NIS2) — topic page.** ENISA. https://www.enisa.europa.eu/topics/state-of-cybersecurity-in-the-eu/cybersecurity-policies/nis-directive-2
- [10] **NIS2 Technical Implementation Guidance** (guidance on cybersecurity risk-management measures). ENISA. https://www.enisa.europa.eu/publications/nis2-technical-implementation-guidance

## Standards

- [11] **ISO/IEC 27001:2022** — Information security management systems (ISMS); reference framework for the Art. 21 measures. ISO. https://www.iso.org/standard/27001
- [12] **NIST Cybersecurity Framework 2.0** — reference framework for cyber risk management supporting Art. 21 alignment. NIST. https://www.nist.gov/cyberframework

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation and official regulatory sources. Academic analysis (e.g., of incident-reporting effectiveness or the essential/important boundary) will be cited in the sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- ENISA — Network and Information Systems Directive 2 (NIS2) awareness campaign. https://www.enisa.europa.eu/topics/awareness-and-cyber-hygiene/raising-awareness-campaigns/network-and-information-systems-directive-2-nis2
- European Commission — Cyber Resilience Act policy page (product-security companion to NIS2). https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act

# Related Documents

- `dora-foundations` — DORA, the financial-sector **lex specialis** under NIS2 Art. 4 (planned).
- `gdpr-foundations` — parallel data-protection regime; a personal-data breach may trigger both NIS2 Art. 23 and GDPR Art. 33 (prerequisite reading).
- `ai-act-foundations` — AI Act overlap (high-risk cybersecurity/robustness duties running alongside NIS2).
- `dsa-foundations` — adjacent digital-platform regime for user-content services.
- `nis2-incident-reporting` — incident-reporting mechanics and Implementing Regulation (EU) 2024/2690 detail (planned).
- `nis2-sectors` — Annex I/II sector-by-sector scope analysis (planned).
- `nis2-transposition-tracker` — national transposition comparison across Member States (planned).
- `cer-foundations` — Critical Entities Resilience Directive companion regime (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Directive (EU) 2022/2555, DORA, CRA, Implementing Regulation (EU) 2024/2690) and European Commission/ENISA sources. **Transposition status live-verified on 2026-07-11**: deadline 17 Oct 2024; reasoned opinions to 19 Member States (7 May 2025); CJEU referrals of Ireland, Spain, France and the Netherlands (IP/26/1499, 8–9 July 2026) with a request for financial penalties. Art. 23 (24h/72h/1-month) and Art. 34 fines (≥€10m/2% essential; ≥€7m/1.4% important) confirmed. All 12 external links returned HTTP 200. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at batch human review gate; orchestrator verified Art. 23 timeline and Art. 34 fines against EUR-Lex raw text; frozen in release 0.8.0. | Human reviewer |
