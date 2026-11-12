---
id: dora-tlpt
title: "DORA: Threat-Led Penetration Testing (TLPT)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: DORA
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [dora-foundations, cybersecurity-foundations, nis2-foundations]
tags: [dora, tlpt, threat-led-penetration-testing, tiber-eu, red-teaming, resilience-testing, ict-risk, financial-sector, rts]
legal_basis: Regulation (EU) 2022/2554, Arts. 24–27; Commission Delegated Regulation (EU) 2025/1190
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dora-tlpt |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.11.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The advanced-testing regime is now supported by a **finalised, in-force** Regulatory Technical Standard — **Commission Delegated Regulation (EU) 2025/1190** under DORA Art. 26(11) — and by the **DORA-aligned TIBER-EU framework** (updated 11 February 2025); both were **live-verified** for this document [1][2][5]. Because national TLPT implementation (via the competent authority or, for many entities, the relevant TIBER cyber team) and the ESAs'/ECB's guidance continue to evolve, confirm the current RTS text and the applicable national/TIBER implementation guidance before relying on them.

# Executive Summary

**Threat-led penetration testing (TLPT)** is the most demanding element of DORA's third pillar — digital operational resilience testing (Arts. 24–27 of **Regulation (EU) 2022/2554**) [1]. Where the baseline testing programme (Art. 24) and the toolbox of vulnerability assessments, scans and ordinary penetration tests (Art. 25) apply to **all** financial entities on a risk-based, at-least-annual basis, **TLPT is reserved for the most significant entities** and is a fundamentally different exercise: an intelligence-led, adversarial red-team test conducted on **live production systems** that support **critical or important functions**, mimicking the tactics, techniques and procedures (TTPs) of real-world threat actors, at least **once every three years** (Art. 26) [1].

This document goes deep on the TLPT regime. It explains the testing pillar and how it fits the wider ICT risk-management framework; **which entities must perform TLPT and how competent authorities identify them** (Art. 26(8)); how **scope** is set around critical or important functions — including functions **outsourced to ICT third-party providers**; the end-to-end **TLPT lifecycle** (preparation/scoping → threat-intelligence-led targeting → red-team testing → closure and purple-teaming → remediation); and the requirements for **testers and threat-intelligence providers**, including the internal-versus-external rules (Art. 27) [1]. It gives a practical scoping methodology and maps TLPT against ordinary penetration testing and ISO/IEC 27001.

The single most important status point — **live-verified** for this document — is that the enabling RTS is **no longer a draft**. The European Commission adopted **Commission Delegated Regulation (EU) 2025/1190** on **13 February 2025**; it was published in the **Official Journal on 18 June 2025** and **entered into force on 8 July 2025** (the twentieth day after publication), specifying the criteria for identifying in-scope entities, the scope/methodology/results requirements, the standards for internal testers, and the **mutual-recognition** and cooperation arrangements under Art. 26(11) [2][4]. In parallel, the **Eurosystem's TIBER-EU framework** was updated on **11 February 2025** to align with DORA — renaming the "White Team" to **"Control Team"**, making **purple-teaming mandatory**, and synchronising deliverables with the RTS — so that a TIBER-EU test can serve as the recognised means of conducting a DORA TLPT [5][6][7].

# Key Takeaways

- **TLPT sits at the top of DORA's testing pillar (Arts. 24–27):** all entities run a risk-based testing programme (Art. 24) and a testing toolbox (Art. 25); only identified significant entities run **TLPT** on live systems at least **every three years** (Art. 26) [1]. *(Legal obligation.)*
- **TLPT is defined narrowly:** a controlled test of **live production ICT systems** mimicking real threat-actor **TTPs**, driven by **targeted threat intelligence**, covering **critical or important functions** (Art. 3(17); Art. 26(1)–(2)) [1]. *(Legal obligation.)*
- **The enabling RTS is finalised and in force — verified:** **Commission Delegated Regulation (EU) 2025/1190** under **Art. 26(11)** was adopted **13 Feb 2025**, published in the OJ **18 Jun 2025**, and applies from **8 Jul 2025** [2][4]. *(Confirmed, not asserted.)*
- **Competent authorities identify who is in scope** using criteria set in the RTS (impact-related factors, systemic importance and ICT risk profile), not simple size thresholds (Art. 26(8); Reg (EU) 2025/1190) [1][2]. *(Legal obligation.)*
- **Scope must reach ICT third parties:** where a critical or important function is provided by an **ICT third-party provider**, that provider's systems fall within the TLPT scope, with pooled-testing options and safeguards (Art. 26(2)–(4)) [1]. *(Legal obligation.)*
- **The lifecycle is prescribed:** preparation/scoping, threat-intelligence-led red-teaming on production, **closure with mandatory purple-teaming**, and a remediation plan, ending in an **attestation** enabling EU-wide **mutual recognition** (Art. 26(4)–(7); TIBER-EU) [1][5][7]. *(Legal obligation + framework guidance.)*
- **Testers are tightly regulated (Art. 27):** they must have proven suitability, capability and independence; **internal testers** are allowed only with competent-authority approval and safeguards, external testers must be used for **one in every three tests**, and the **threat-intelligence provider must always be external** (Arts. 26(8), 27) [1][2]. *(Legal obligation.)*
- **TIBER-EU is the recognised implementation path — verified:** the Eurosystem updated **TIBER-EU on 11 Feb 2025** to align with DORA (Control Team, mandatory purple-teaming, RTS-synchronised deliverables); the **ECB** issued an SSM implementation guide in **November 2025** [5][6][7]. *(Regulatory framework — verified.)*
- **TLPT ≠ ordinary pentesting:** it is broader in scope (whole functions, live systems, real TTPs), longer (months), intelligence-led and scenario-based; it complements but does not replace Art. 25 penetration testing or ISO/IEC 27001/27002 controls testing [1][11][12][13]. *(Best practice / interpretation.)*

# Purpose

This document is a Tier 3 DORA sub-topic that **details `dora-foundations`** on the advanced-testing regime. It supports: (a) legal research (the precise obligations in Arts. 24–27 and the RTS); (b) scoping and programme design for entities that are — or may be — identified for TLPT; and (c) engineering and security triage (how a threat-led red-team engagement is planned, run, closed and remediated, and how testers and threat-intelligence providers are selected). It assumes the reader has read `dora-foundations` for the five-pillar overview and `cybersecurity-foundations` for the underlying red-team/penetration-testing discipline.

# Scope

**In scope:** DORA's testing pillar (Arts. 24–27) with emphasis on **TLPT** (Art. 26) and **testers** (Art. 27); identification of in-scope entities (Art. 26(8)); TLPT scope-setting over critical or important functions, including functions delivered by **ICT third-party providers**; the TLPT **lifecycle** and the **≥3-year cadence**; the enabling **RTS (Commission Delegated Regulation (EU) 2025/1190)** under Art. 26(11); **TIBER-EU** alignment and the ECB/Eurosystem implementation guidance; internal versus external testers and the role of threat-intelligence providers; **mutual recognition** across the EU; a practical scoping methodology; and the overlap with ordinary penetration testing and ISO/IEC 27001. The **RTS status** and **TIBER-EU alignment** are **live-verified**.

**Out of scope (covered elsewhere / in the backlog):** the DORA overview and the other four pillars → `dora-foundations`; ICT risk-management framework detail (Arts. 5–16) and the Art. 25 testing toolbox at implementation depth → `dora-technical-standards` (planned); the CTPP Union Oversight Framework mechanics → `dora-oversight-framework` (planned); ICT third-party contractual and register duties → `dora-third-party-contracts` (planned); generic red-team/penetration-testing methodology and control frameworks → `cybersecurity-foundations`; national TIBER implementation guides by Member State (referenced, not reproduced).

**Assumptions:** The reader understands DORA's scope of "financial entities" (Art. 2) and the concept of "critical or important functions". TLPT is additive to, not a substitute for, the baseline Art. 24/25 testing programme. Where personal data is processed on systems in scope, the GDPR applies in parallel (see `gdpr-foundations`).

# Definitions

*Shared terms (digital operational resilience, TLPT, CTPP) are in `GLOSSARY.md`. TLPT-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Threat-led penetration testing (TLPT) | A framework that mimics the tactics, techniques and procedures of real-life threat actors perceived as a genuine cyber threat, delivering a controlled, bespoke, intelligence-led (red-team) test of the financial entity's critical live production systems (Art. 3(17)). | [1] |
| Critical or important function | A function whose disruption would materially impair the financial entity's financial performance or the soundness/continuity of its services and activities, or whose discontinued/defective performance would materially impair continued compliance with authorisation conditions or other DORA obligations (Art. 3(22)). | [1] |
| Red team | The team of testers that emulates a real adversary, seeking to compromise in-scope targets through intelligence-led attack scenarios without prior knowledge shared with defenders. | [1][5] |
| Blue team | The financial entity's defenders (security operations, incident response) who, during the active test, are unaware they are being tested (except the Control Team). | [5] |
| Control Team (formerly "White Team") | The small, trusted group inside the financial entity that commissions, controls and keeps the TLPT secret, managing risk and liaising with testers and the authority; renamed from "White Team" in the DORA-aligned TIBER-EU update. | [5][7] |
| Purple teaming | A collaborative replay/closure phase in which red and blue teams work together to walk through the attack scenarios, transfer knowledge and validate detections; **mandatory** under the DORA-aligned TIBER-EU framework. | [5][7] |
| Threat-intelligence (TI) provider | The external provider that produces the **Targeted Threat Intelligence Report** — the threat landscape, threat-actor profiles and attack scenarios that drive the red-team test; under DORA the TI provider must always be external (Art. 26(8)). | [1][5] |
| Attestation | The document confirming a TLPT was performed in accordance with the requirements, provided by the authorities solely for the purpose of **mutual recognition** across the EU (Art. 26(7)). | [1] |
| TIBER-EU | The Eurosystem's *Threat Intelligence-Based Ethical Red Teaming* framework — the common EU methodology for intelligence-led red-team testing, updated in 2025 to serve as the recognised way to conduct a DORA TLPT. | [5][6] |

# Background

Before DORA, intelligence-led red-teaming of financial firms was **voluntary and fragmented**. The **Bank of England's CBEST** scheme (2014) pioneered regulator-driven, threat-intelligence-led testing; the **ECB launched TIBER-EU in 2018** as a common Eurosystem framework, adopted by a growing set of national central banks and authorities on an opt-in basis. These schemes proved the model — realistic, scenario-based tests on live systems reveal resilience gaps that checklist audits and scoped penetration tests miss — but participation and methodology varied by jurisdiction, and there was no single legal obligation, no consistent identification of who should be tested, and only informal cross-border recognition [5][6].

DORA converts this good practice into **hard law** for the EU financial sector. Art. 26 makes intelligence-led testing on live production systems **mandatory** for identified significant entities, on a common methodology, with a **legal basis for mutual recognition** so that a single test can satisfy authorities across the EU [1]. Critically, DORA **did not discard TIBER-EU** — instead the Eurosystem **re-based TIBER-EU onto DORA** in February 2025, so the established framework becomes the operational vehicle for the legal duty, and financial entities and TI/red-team providers can continue to use familiar processes and roles (now DORA-conformed) [5][7]. The regime is completed by the **Art. 26(11) RTS**, finalised as **Commission Delegated Regulation (EU) 2025/1190**, which fills in the identification criteria, scope, methodology, tester standards and cooperation/mutual-recognition mechanics [2][4].

# Legal Framework

DORA's **Chapter IV (Arts. 24–27)** establishes the "digital operational resilience testing" pillar. It has two tiers [1]:

- **Baseline testing (all financial entities, except microenterprises on a risk-based frequency):**
  - **Art. 24 — General requirements.** Every financial entity (other than those on the simplified regime) must establish, maintain and review a **sound and comprehensive digital operational resilience testing programme** as an integral part of its ICT risk-management framework, applying a **risk-based approach** and covering ICT systems and applications supporting critical or important functions. Tests are carried out by **independent parties** (internal or external) and adverse findings are fully addressed [1].
  - **Art. 25 — Testing of ICT tools and systems.** The programme must include a **range of assessments and tests** — vulnerability assessments and scans, open-source analyses, network security assessments, gap analyses, physical security reviews, questionnaires and scanning software, source-code reviews where feasible, scenario-based tests, compatibility/penetration testing and end-to-end testing — with critical ICT systems tested **at least yearly** [1].

- **Advanced testing (identified significant entities only):**
  - **Art. 26 — Advanced testing of ICT tools, systems and processes based on TLPT.** Identified entities must carry out **TLPT at least every three years** (competent authorities may adjust the frequency to the entity's risk profile and operational circumstances), covering **several or all critical or important functions** and performed on **live production systems**; the test must include those functions even where they are **outsourced to ICT third-party providers** [1].
  - **Art. 27 — Requirements for testers.** Sets the suitability, capability, independence and (for external testers) insurance requirements, and governs the use of **internal testers** [1].

**Interpretation (distinct from the statutory text):** The two tiers are cumulative — TLPT does not displace the Art. 24/25 programme; an in-scope entity runs both. TLPT is deliberately **outcome-focused and adversarial**: it tests **protection, detection, response and recovery** capabilities of people, processes and technology under realistic attack, rather than confirming the presence of controls. The **Art. 26(11) RTS** (Reg (EU) 2025/1190) is the binding detail; the **TIBER-EU framework** is the recognised *how-to* the ECB/Eurosystem and national authorities expect entities to follow [1][2][5][7].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 3(17) | Defines **threat-led penetration testing (TLPT)**. | [1] |
| Art. 3(22) | Defines **critical or important function** (scoping anchor for TLPT). | [1] |
| Art. 24 | General requirement — a **risk-based digital operational resilience testing programme** for all non-simplified entities. | [1] |
| Art. 25 | The **testing toolbox** (vulnerability assessments, scans, penetration tests, etc.); critical systems tested at least yearly. | [1] |
| Art. 26(1) | **TLPT at least once every three years** for identified entities (frequency adjustable to risk). | [1] |
| Art. 26(2)–(3) | TLPT covers **critical or important functions** on **live production systems**; scope validated with the authority. | [1] |
| Art. 26(4) | **Pooled testing** where multiple entities/ICT third parties share systems; safeguards and a lead entity. | [1] |
| Art. 26(5)–(7) | Test conduct, and the **attestation** issued **solely for mutual recognition** across the EU. | [1] |
| Art. 26(8) | Competent authorities **identify** the entities required to perform TLPT; rules on testers and the always-external **threat-intelligence provider**. | [1] |
| Art. 26(11) | Mandate for the ESAs, **in agreement with the ECB**, to develop the **RTS** on identification criteria, scope, methodology, internal testers, and cooperation/mutual recognition. | [1] |
| Art. 27(1) | Requirements for **testers** — suitability/reputation, technical and organisational capability, threat-intelligence/red-team expertise, certification or codes of conduct, independence, and professional indemnity insurance for external testers. | [1] |
| Art. 27(2)–(4) | Conditions for using **internal testers** (authority approval, dedicated resources, conflict-of-interest management) and related safeguards. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 47 area | Advanced testing through TLPT is warranted for entities that are significant and ICT-mature, to raise the sector's overall resilience. | [1] |
| Recital 48 area | TLPT should build on established frameworks such as **TIBER-EU** and enable **mutual recognition** to avoid duplicative tests across Member States. | [1] |
| Recital 49 area | Requirements for testers safeguard the quality, independence and integrity of TLPT. | [1] |

## Relevant Case Law

**Not Applicable.** TLPT is a recent, technical supervisory obligation that became operative with DORA's application on 17 January 2025 and its RTS on 8 July 2025; there is no CJEU or domestic case law interpreting Arts. 26–27 or Commission Delegated Regulation (EU) 2025/1190. Interpretive weight rests on the Regulation, the RTS, and the ECB/ESA and national TIBER guidance [1][2][5]. Any future disputes (e.g. over identification decisions or attestations) would be tracked in the backlog rather than asserted here.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **The Art. 26(11) RTS is final and in force.** The European Commission adopted **Commission Delegated Regulation (EU) 2025/1190** on **13 February 2025**; it was published in the **Official Journal on 18 June 2025** and **entered into force on 8 July 2025**. It specifies: the **criteria** competent authorities use to identify entities required to perform TLPT; requirements on **scope, testing methodology and results**; the **requirements and standards governing the use of internal testers**; and the forms of **supervisory and other cooperation** needed for TLPT implementation and **mutual recognition** [2][4]. The European Commission catalogues this RTS among DORA's delegated acts [8], and EIOPA's overview confirms that the testing pillar operates from DORA's 17 January 2025 application date [9]. *(Regulatory interpretation — verified.)*
- **The ESAs developed the RTS "in agreement with the ECB".** DORA Art. 26(11) uniquely requires ECB agreement, reflecting the ECB/Eurosystem's ownership of TIBER-EU; the EBA hosts the joint RTS on behalf of the three ESAs [1][4]. *(Regulatory interpretation.)*
- **TIBER-EU is the recognised delivery framework — and it was re-based on DORA.** On **11 February 2025** the Eurosystem published an updated **TIBER-EU framework** aligned with DORA and its RTS: the **"White Team" was renamed "Control Team"**, **purple-teaming was made mandatory**, process steps were synchronised with the **RTS deliverables and timelines**, and guidance documents were added so authorities can reference TIBER-EU directly [5][6]. *(Regulatory interpretation — verified.)*
- **The ECB issued SSM implementation guidance.** In **November 2025** the ECB (Banking Supervision) published a **TIBER-EU implementation guide** explaining how to implement TIBER-EU for a DORA TLPT within the Single Supervisory Mechanism [7]. *(Regulatory interpretation — verified.)*
- **Compliance and attestation.** Where an entity follows the TIBER-EU process and the DORA/RTS requirements, the process concludes with an **attestation** confirming the test was performed as required — the instrument that enables **EU-wide mutual recognition** so the test need not be repeated for each Member State's authority (Art. 26(7)) [1][5]. *(Regulatory interpretation.)*
- **Identification is supervisory and risk-based, not a bright-line size test.** Competent authorities identify in-scope entities using the RTS criteria — grounded in impact-related factors, the systemic character of the entity, and its ICT risk profile/maturity — so being large does not automatically mean in-scope, and being identified reflects supervisory judgement (Art. 26(8); Reg (EU) 2025/1190) [1][2]. *(Regulatory interpretation.)*

# Technical Considerations

- **Treat TLPT as an intelligence-led, full-scope engagement, not a scoped pentest.** The red team works from a **Targeted Threat Intelligence (TTI) Report** to build realistic **attack scenarios** against whole critical/important functions on **live production**, exercising the full kill chain (reconnaissance, initial access, persistence, lateral movement, actions on objectives) while defenders remain unaware [1][5]. *(Best practice grounded in the Art. 26 obligation.)*
- **Protect the production estate.** Because testing is on live systems, the **Control Team** must run rigorous **risk management** — legal sign-off, a tested rollback/"leg-up" and abort process, out-of-band communications, and safeguards so the test cannot cause the very disruption it simulates (Art. 26 requires controlled testing) [1][5]. *(Best practice.)*
- **Map critical or important functions to underlying assets first.** A defensible scope requires a current inventory linking each critical/important function (Art. 3(22)) to applications, infrastructure, identities and **ICT third-party dependencies**; this is drawn from the Art. 6 framework — specified in detail by the ICT risk-management RTS (Commission Delegated Regulation (EU) 2024/1774) — and the register of information [1][3]. *(Best practice; obligation to maintain the framework/register under DORA.)*
- **Include third-party-run functions and plan pooled testing.** Where a critical/important function runs on an ICT third-party provider (e.g. cloud, core-banking, payments), the provider's in-scope systems must be tested; **pooled TLPT** with a designated lead entity is available where several entities rely on shared systems, subject to Art. 26(4) safeguards and provider cooperation [1][10]. *(Legal obligation + best practice.)*
- **Instrument detection and response for the purple-teaming replay.** Value is realised in **closure**: the mandatory purple-teaming replay compares red-team actions against blue-team telemetry and detections, producing concrete SOC/EDR/logging improvements — build for this by preserving detailed test logs [5][7]. *(Best practice.)*
- **Feed findings into remediation and re-testing.** Adverse findings must be addressed under Art. 24's "fully address" duty; track remediation to closure and re-validate high-severity gaps [1]. *(Legal obligation.)*

# Hosting Considerations

- **Cloud/hosting providers are frequently in TLPT scope.** If a critical or important function of a financial-entity customer runs on your platform, your relevant systems fall within that customer's TLPT; expect **contractual cooperation** obligations (access, coordination, safe testing windows) flowing from Art. 30 and the third-party-risk regime [1]. *(Legal obligation for the financial entity; commercial reality for the host.)*
- **CTPPs and concentration.** A hosting/cloud provider designated a **critical ICT third-party provider** already sits under direct ESA oversight; TLPT of dependent entities adds resilience assurance over the same estate, and **pooled testing** is likely where many entities share the platform [1][10]. *(Regulatory context.)*
- **Live-system safety.** Testing on production shared infrastructure demands provider-side safeguards (blast-radius limits, tenant isolation assurances, coordinated abort procedures) so a red-team scenario cannot degrade other tenants — a key subject of pooled-testing safeguards under Art. 26(4) [1][5]. *(Best practice.)*
- **Evidence and logging.** Hosts should be able to supply the telemetry needed for the purple-teaming replay and remediation validation without breaching other customers' confidentiality [5]. *(Best practice.)*

# Game Hosting Considerations

**Not Applicable — with the same narrow caveat as `dora-foundations`.** TLPT is an obligation of **identified significant financial entities**; ordinary game hosting and studios are outside DORA entirely. It becomes relevant only where a games business is itself a financial entity (e.g. a scaled in-game **crypto-asset service provider** under MiCA, or an embedded payments/e-money arm) that a competent authority **identifies** for TLPT, or where a studio supplies ICT services underpinning a critical or important function of such an entity — in which case its systems could be pulled into that entity's TLPT scope on the third-party terms above [1]. Standard player-facing game security testing is governed by general good practice (see `cybersecurity-foundations`), not DORA TLPT.

# AI Considerations

- **AI systems on in-scope functions are legitimate TLPT targets.** Where AI/ML supports a critical or important function (fraud detection, credit decisioning, trading surveillance, security automation), those models, data pipelines and inference endpoints are part of the ICT estate and can be included in the red-team scope and scenarios [1]. *(Legal obligation — as ICT.)*
- **AI-specific attack scenarios.** Threat intelligence should reflect AI-relevant TTPs (data/model poisoning, prompt injection against LLM-backed services, model theft, evasion of ML-based detection); purple-teaming should validate whether such attacks are detected [1][5]. *(Best practice.)*
- **AI at ICT third parties.** AI services bought from providers underpinning in-scope functions are captured just like any other third-party dependency, with cooperation and pooled-testing considerations [1][10]. *(Legal obligation.)*
- **AI Act and GDPR run in parallel.** High-risk AI in financial services carries AI Act robustness/cybersecurity duties (see `ai-act-foundations`), and any personal data on tested systems remains governed by the GDPR; TLPT does not displace either [1]. *(Cross-reference; parallel application.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

**A practical TLPT scoping methodology (recommended):**

1. **Confirm identification status.** Establish whether your competent authority has identified the entity for TLPT under Art. 26(8) and the RTS criteria; if not yet identified but plausibly in scope (systemic role, ICT maturity), prepare proactively. *(OBLIGATION once identified; EDITORIAL RECOMMENDATION to prepare early.)* [1][2]
2. **Enumerate critical or important functions.** Use the Art. 3(22) definition and the Art. 6 framework to list functions whose disruption would materially impair the business or compliance. *(OBLIGATION — framework; foundational to scope.)* [1]
3. **Map functions to assets and third parties.** For each function, trace supporting applications, infrastructure, identities, data flows and **ICT third-party dependencies** (from the register of information). *(BEST PRACTICE.)* [1]
4. **Select the TLPT scope with the authority.** Choose several or all critical/important functions to cover, including third-party-run ones; validate the scope specification with the competent authority/TIBER team. *(OBLIGATION.)* [1][2]
5. **Stand up the Control Team and risk controls.** Appoint the small trusted Control Team, secure legal sign-off, and define the abort/rollback and out-of-band comms before any active testing on production. *(BEST PRACTICE — required for controlled testing.)* [1][5]
6. **Procure compliant TI and red-team providers.** Engage an **external threat-intelligence provider** and testers meeting Art. 27 requirements; if using internal red-teamers, obtain authority approval and manage conflicts, and remember external testers are required for **one in every three tests**. *(OBLIGATION.)* [1][2]
7. **Run the intelligence-led red-team test on live systems.** Deliver the Targeted Threat Intelligence Report, then execute scenario-based attacks against in-scope functions with the blue team unaware. *(OBLIGATION.)* [1][5]
8. **Close with mandatory purple-teaming.** Replay scenarios collaboratively, capture detection/response gaps and transfer knowledge. *(OBLIGATION under the DORA-aligned framework.)* [5][7]
9. **Remediate and obtain the attestation.** Produce a remediation plan, address adverse findings, and secure the **attestation** for EU-wide mutual recognition. *(OBLIGATION.)* [1]
10. **Schedule the next cycle.** Plan the next TLPT within the **three-year** cadence (or the authority-adjusted frequency), and integrate lessons into the Art. 24/25 programme. *(OBLIGATION.)* [1]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Mis-scoping — omitting a critical/important function or a third-party-run system | Medium | High | Art. 26(2)–(3) [1] | Function-to-asset mapping from register; authority validation of scope | Low |
| R2 | Assuming not in scope; missing an authority identification | Medium | High | Art. 26(8); Reg (EU) 2025/1190 [1][2] | Track identification; proactive readiness for likely in-scope entities | Low |
| R3 | Production disruption caused by testing live systems | Medium | Very High | Art. 26 controlled-testing duty [1][5] | Control Team risk management; abort/rollback; safe windows | Medium |
| R4 | Using non-compliant testers or an internal TI provider | Low | High | Arts. 26(8), 27; RTS [1][2] | Art. 27 due diligence; always-external TI; authority approval for internal testers | Low |
| R5 | Breaching the internal/external tester ratio (external for 1 in 3) | Low | Medium | Art. 26(8) [1] | Multi-cycle tester plan ensuring external every third test | Low |
| R6 | Weak closure — no purple-teaming, findings not remediated | Medium | High | Art. 24 (fully address); TIBER-EU [1][5] | Mandatory purple-teaming; tracked remediation; re-test high-severity | Medium |
| R7 | No mutual recognition — duplicative tests across Member States | Low | Medium | Art. 26(5)–(7) [1] | Follow TIBER-EU; obtain attestation; engage lead authority | Low |
| R8 | Treating TLPT as a substitute for Art. 25 testing or ISO 27001 controls | Medium | Medium | Arts. 24–26 [1][11] | Run baseline programme and TLPT as cumulative layers | Low |

# Implementation Roadmap

- **Phase 0 — Readiness & identification:** Confirm identification status (Art. 26(8)); baseline the Art. 24/25 testing programme; assess ICT maturity for TLPT. *Effort:* Medium.
- **Phase 1 — Scope definition:** Enumerate critical/important functions; map to assets and ICT third parties; draft the scope specification for the authority. *Effort:* Medium.
- **Phase 2 — Governance & procurement:** Stand up the Control Team and risk controls; procure Art. 27-compliant external TI and red-team providers (or approve internal testers). *Effort:* Medium.
- **Phase 3 — Test execution:** Deliver threat intelligence; run the intelligence-led red-team test on live production against in-scope functions. *Effort:* High.
- **Phase 4 — Closure & remediation:** Mandatory purple-teaming; remediation plan; address adverse findings; obtain the attestation. *Effort:* High.
- **Phase 5 — Cycle & integration:** Schedule the next ≥3-year test; feed lessons into the ICT risk-management framework and baseline testing. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | TLPT obligation unassessed; no red-team capability; scope undefined. | No function inventory; identification status unknown. |
| 2 | Managed | Baseline Art. 24/25 testing runs; identification status confirmed; scope drafting begun. | Testing programme; provisional function list. |
| 3 | Defined | Critical/important functions mapped to assets and third parties; Control Team and scope agreed with authority. | Scope specification; Art. 27-compliant providers engaged. |
| 4 | Quantitatively Managed | Full TLPT executed on live systems; purple-teaming and remediation completed; attestation obtained. | Attestation; remediation metrics; detection-improvement data. |
| 5 | Optimising | TLPT embedded on a ≥3-year cycle; findings drive continuous resilience improvement; mutual recognition leveraged EU-wide. | Multi-cycle programme; threat-informed defence; cross-border recognition. |

# Audit Questions

1. Has the competent authority identified the entity for TLPT under Art. 26(8), and how is that identification evidenced? *(Art. 26(8); Reg (EU) 2025/1190 [1][2].)*
2. How were the **critical or important functions** in scope determined, and does the scope include functions run by **ICT third-party providers**? *(Art. 26(2)–(4) [1].)*
3. What controls protect **live production systems** during testing (Control Team, abort/rollback, out-of-band comms)? *(Art. 26 [1][5].)*
4. Do **testers** meet Art. 27 requirements, is the **threat-intelligence provider external**, and — if internal testers are used — is authority approval in place with external testers used every third test? *(Arts. 26(8), 27 [1][2].)*
5. Was the test conducted per the **TIBER-EU** framework, including **mandatory purple-teaming** at closure? *([5][7].)*
6. How were adverse findings **remediated**, and were high-severity gaps re-validated? *(Art. 24 [1].)*
7. Was an **attestation** obtained, and is **mutual recognition** relied on across Member States? *(Art. 26(5)–(7) [1].)*
8. Is the next TLPT scheduled within the **three-year** cadence (or the authority-adjusted frequency), and are lessons fed into the Art. 24/25 programme? *(Art. 26(1) [1].)*

# Implementation Checklist

- [ ] TLPT identification status confirmed with the competent authority (Art. 26(8)).
- [ ] Critical/important functions enumerated (Art. 3(22)) and mapped to assets and ICT third parties.
- [ ] TLPT scope specification agreed with the authority, including third-party-run functions (Art. 26(2)–(4)).
- [ ] Control Team stood up; live-system risk controls (abort/rollback, out-of-band comms, legal sign-off) in place.
- [ ] External threat-intelligence provider engaged; testers meet Art. 27; internal-tester approval and 1-in-3 external ratio managed.
- [ ] Targeted Threat Intelligence Report delivered; intelligence-led red-team test executed on live production.
- [ ] Mandatory purple-teaming completed at closure; detection/response gaps captured.
- [ ] Remediation plan produced; adverse findings addressed; high-severity gaps re-validated (Art. 24).
- [ ] Attestation obtained; mutual recognition leveraged across Member States (Art. 26(5)–(7)).
- [ ] Next TLPT scheduled within the ≥3-year cadence; lessons integrated into the Art. 24/25 programme.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2022/2554 (Digital Operational Resilience Act — DORA)** — Chapter IV, Articles 24–27 (digital operational resilience testing; TLPT; testers) and Art. 3(17), (22) definitions. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj
- [2] **Commission Delegated Regulation (EU) 2025/1190 of 13 February 2025** supplementing Regulation (EU) 2022/2554 with regard to **RTS specifying the criteria for identifying financial entities required to perform TLPT**, testing scope/methodology/results, use of internal testers, and cooperation/mutual recognition (Art. 26(11)); published in the OJ on 18 June 2025, in force from 8 July 2025. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_del/2025/1190/oj
- [3] **Commission Delegated Regulation (EU) 2024/1774** — RTS specifying ICT risk-management tools, methods, processes and policies (the framework and simplified framework within which the Art. 24/25 testing programme sits). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_del/2024/1774/oj

## Regulatory Guidance

- [4] **Joint Regulatory Technical Standards specifying elements related to threat-led penetration tests.** European Banking Authority (on behalf of the ESAs; RTS under Art. 26(11), developed in agreement with the ECB). https://www.eba.europa.eu/activities/single-rulebook/regulatory-activities/operational-resilience/joint-regulatory-technical-standards-specifying-elements-related-threat-led-penetration-tests
- [5] **TIBER-EU Framework updated to align with DORA** (11 February 2025; "White Team" renamed "Control Team", purple-teaming made mandatory, deliverables synchronised with the RTS). European Central Bank — MIP news. https://www.ecb.europa.eu/press/intro/news/html/ecb.mipnews250211.en.html
- [6] **TIBER-EU (Threat Intelligence-Based Ethical Red Teaming) framework.** European Central Bank — cyber resilience hub. https://www.ecb.europa.eu/paym/cyber-resilience/tiber-eu/html/index.en.html
- [7] **TIBER-EU Guide — How to implement the TIBER-EU framework for the DORA TLPT** (SSM implementation guide, November 2025). ECB Banking Supervision. https://www.bankingsupervision.europa.eu/ecb/pub/pdf/ssm.supervisory_guide202511.en.pdf
- [8] **Digital Operational Resilience Regulation (DORA)** — implementing and delegated acts (incl. the TLPT RTS). European Commission, DG FISMA. https://finance.ec.europa.eu/regulation-and-supervision/financial-services-legislation/implementing-and-delegated-acts/digital-operational-resilience-regulation_en
- [9] **Digital Operational Resilience Act (DORA)** — overview (application date; testing pillar). EIOPA. https://www.eiopa.europa.eu/digital-operational-resilience-act-dora_en
- [10] **European Supervisory Authorities designate critical ICT third-party providers under DORA** (18 November 2025; context for third-party-run functions within TLPT scope). EIOPA/EBA/ESMA. https://www.eiopa.europa.eu/european-supervisory-authorities-designate-critical-ict-third-party-providers-under-digital-2025-11-18_en

## Standards

- [11] **ISO/IEC 27001:2022** — Information security management systems (ISMS). The control-assurance baseline that TLPT complements but does not replace. ISO. https://www.iso.org/standard/27001
- [12] **ISO/IEC 27002:2022** — Information security controls (incl. threat intelligence and technical vulnerability management), the control catalogue an ISMS applies. ISO. https://www.iso.org/standard/75652.html
- [13] **NIST SP 800-115 — Technical Guide to Information Security Testing and Assessment.** Distinguishes vulnerability scanning and penetration testing from full adversary-emulation exercises. NIST. https://csrc.nist.gov/pubs/sp/800/115/final

## Academic Sources

Not Applicable — this sub-topic relies on primary legislation, the Art. 26(11) RTS, and ECB/ESA framework guidance. Academic analysis of red-team efficacy and financial-sector cyber-resilience testing may be cited in future depth documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- TIBER.info — community resource tracking TIBER-EU and DORA TLPT developments (non-authoritative). https://tiber.info/
- Digital Operational Resilience Act — Wikipedia (overview and implementation chronology; non-authoritative). https://en.wikipedia.org/wiki/Digital_Operational_Resilience_Act

# Related Documents

- `dora-foundations` — DORA overview and the five pillars; this document **details** its Arts. 24–27 testing material (parent).
- `cybersecurity-foundations` — red-team/penetration-testing discipline, ISO 27001/27002 and controls underpinning TLPT execution.
- `nis2-foundations` — general cybersecurity baseline; DORA is lex specialis for financial entities.
- `dora-oversight-framework` — CTPP designation and Lead Overseer mechanics (planned).
- `dora-technical-standards` — RTS/ITS-by-RTS analysis, incl. the Art. 24/25 testing toolbox (planned).
- `dora-third-party-contracts` — register of information and Art. 30 contractual duties relevant to third-party-run functions (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Reg (EU) 2022/2554 Arts. 24–27; Commission Delegated Regulation (EU) 2025/1190), the EBA joint RTS page, the ECB/Eurosystem TIBER-EU framework and the ECB SSM implementation guide, EIOPA, the European Commission (DG FISMA), and ISO/NIST standards. **Live-verified:** the Art. 26(11) RTS is finalised — Reg (EU) 2025/1190 adopted 13 Feb 2025, OJ 18 Jun 2025, in force 8 Jul 2025 — and TIBER-EU was updated on 11 Feb 2025 to align with DORA (Control Team; mandatory purple-teaming; RTS-synchronised deliverables). All external links returned HTTP 200. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 2 human gate; frozen in release 0.11.0. | Human reviewer |

</content>
</invoke>
