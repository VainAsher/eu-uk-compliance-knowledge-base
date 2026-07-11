---
id: compliance-operations-foundations
title: "Compliance Operations: Running a Compliance Programme"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: Compliance Operations
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [gdpr-foundations, uk-gdpr-foundations, eprivacy-foundations, privacy-engineering-foundations, ai-act-foundations, ai-governance-foundations, data-act-foundations, dsa-foundations, dma-foundations, nis2-foundations, dora-foundations, cybersecurity-foundations]
tags: [compliance-operations, accountability, three-lines-model, iso-37301, iso-31000, cms, ropa, dpia, incident-management, third-party-risk, audit-assurance, regulatory-change]
legal_basis: GDPR Art. 5(2) accountability (Reg (EU) 2016/679); NIS2 Art. 20 governance (Dir (EU) 2022/2555); DORA Art. 5 governance (Reg (EU) 2022/2554); operationalised via ISO 37301, ISO 31000, IIA Three Lines Model
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | compliance-operations-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.9.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is the **cross-cutting capstone** of the knowledge base: it describes *how to operate a compliance programme* across every regime the other documents cover. Where each topic document states *what a given law requires*, this document sets out the *operating model, artefacts and processes* that discharge and evidence those requirements together.

# Executive Summary

**Compliance operations** is the discipline of running a compliance programme as a managed system rather than a series of one-off legal responses. Its anchor duty in EU/UK law is **accountability**: GDPR **Article 5(2)** requires a controller not merely to comply with the data-protection principles but to be able to **demonstrate** compliance [1]. The same accountability logic — documented governance, assigned senior responsibility and evidence on demand — now recurs across the digital rulebook: **NIS2 Article 20** makes management bodies approve and oversee cybersecurity risk measures (and undergo training) [2], and **DORA Article 5** makes the management body of a financial entity *ultimately accountable* for ICT risk [3]. A compliance programme is how an organisation satisfies all of these at once.

This document assembles the operating model. Governance and accountability are structured through the **Three Lines Model** (operational management; risk and compliance oversight; independent internal audit) [15], underpinned by a **Compliance Management System (CMS)** — the certifiable **ISO 37301:2021** standard — and a **risk-management framework** built on **ISO 31000:2018** [11][12]. On that spine sit the **core operational artefacts** every regime reuses: records of processing (GDPR **Art. 30**), data protection impact assessments (**Art. 35**), risk registers, policies and procedures, training and awareness, third-party/vendor management (**Art. 28**; DORA Art. 28), and — most time-critical — **incident and breach management** [1][3].

Three conclusions dominate. First, **accountability is a legal obligation, not an option**: the programme itself is the evidence [1][2][3]. Second, **build once, report many**: a single incident can trigger GDPR 72-hour breach notification (Art. 33), NIS2 reporting (Art. 23, 24h/72h/1-month) and DORA major-incident reporting (Art. 19) on *different clocks to different authorities* — so the operating model, not the individual law, is what makes this survivable [1][2][3]. Third, **standards operationalise the duties**: ISO 37301, ISO 31000 and the Three Lines Model are voluntary but load-bearing — the recognised route to systematic, auditable accountability [11][12][15].

# Key Takeaways

- **Accountability is the anchor duty.** GDPR **Art. 5(2)** requires organisations to *demonstrate* compliance, not just achieve it; the compliance programme is that demonstration [1]. *(Legal obligation.)*
- **Senior management is on the hook.** NIS2 **Art. 20** (approve/oversee measures, undergo training, personal liability) and DORA **Art. 5** (management body *ultimately accountable* for ICT risk) put board-level responsibility in statute [2][3]. *(Legal obligation.)*
- **The Three Lines Model** separates risk ownership (1st line), oversight by risk/compliance (2nd line) and independent assurance by internal audit (3rd line), coordinated by the governing body [15]. *(Best practice.)*
- **A Compliance Management System (ISO 37301:2021)** is the certifiable management-system spine for a compliance programme; it uses the ISO harmonised (Annex SL) structure [11]. *(Best practice.)*
- **Risk management (ISO 31000:2018)** supplies the principles, framework and process (identify → analyse → evaluate → treat → monitor) that feed the risk register [12]. *(Best practice.)*
- **Core artefacts are reused across regimes:** RoPA (GDPR Art. 30), DPIAs (Art. 35), processor/vendor contracts (Art. 28), policies, training, and a risk register — build them once and map them to every applicable law [1][4][5][7]. *(Legal obligation + best practice.)*
- **Incident management is the highest-stakes operational muscle.** One event can trigger **GDPR Art. 33/34 (72h)**, **NIS2 Art. 23 (24h/72h/1-month)** and **DORA Art. 19** in parallel — design one runbook that services all clocks [1][2][3][9]. *(Legal obligation.)*
- **Third-party risk is in scope by law:** GDPR Art. 28 controller-processor terms and DORA Art. 28 ICT third-party principles make supply-chain governance a compliance obligation, not a procurement afterthought [1][3]. *(Legal obligation.)*
- **Audit, metrics and maturity close the loop.** Independent assurance (ISO 19011 auditing guidance), KPIs/monitoring and a maturity model turn compliance from episodic to continually improved [11][13]. *(Best practice.)*
- **A regulatory-change watch is essential** because much of this rulebook is in flux (Digital Omnibus, NIS2 transposition, DUAA 2025) — assign ownership and cadence to horizon-scanning [2][10]. *(Editorial recommendation.)*

# Purpose

This document is the Tier 4 capstone entry point for **running a compliance programme**. It supports: (a) establishing compliance governance and accountability across multiple regimes; (b) standing up a Compliance Management System and risk-management framework; (c) building and reusing the core operational artefacts (RoPA, DPIAs, risk register, policies, training, vendor management, incident/breach management); and (d) operating audit, assurance, metrics and regulatory-change processes. It presupposes the substantive topic documents (GDPR, UK GDPR, ePrivacy, AI Act, AI governance, Data Act, DSA, DMA, NIS2, DORA, cybersecurity, privacy engineering) and shows *how to operationalise them as one programme*.

# Scope

**In scope:** Compliance governance and accountability (GDPR Art. 5(2); NIS2 Art. 20; DORA Art. 5; the DPO role); the Three Lines Model; risk management (ISO 31000); the Compliance Management System (ISO 37301); the core operational artefacts (RoPA, DPIAs, risk register, policies and procedures, training and awareness, third-party/vendor management, incident and breach management); audit and assurance; monitoring, metrics and KPIs; a compliance maturity approach; and regulatory-change management. Coverage is **operational and cross-cutting** — the programme layer that sits above the individual regimes.

**Out of scope (spun off to the research backlog):** Detailed **audit methodology** and audit-programme design → `compliance-audit-methodology`; specific **policy templates** and a policy library → `compliance-policy-library`; regime-specific **breach-response playbooks** and runbooks → `incident-response-playbooks`; **DPIA methodology** in depth → `dpia-methodology` (privacy-engineering backlog); the **article-by-article substance** of each law → the respective topic documents. This document references those regimes; it does not restate them.

**Assumptions:** The reader has read (or can consult) the topic documents this capstone ties together, and understands controller/processor roles and the basic obligations of each regime. "Compliance" here means the organisational programme and management system, not the substantive rules of any single instrument.

# Definitions

*Shared terms (accountability, controller, processor, personal data, ISMS, significant incident, digital operational resilience) are defined in `GLOSSARY.md`. Only compliance-operations-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Compliance management system (CMS) | A set of interrelated elements an organisation uses to establish compliance policy and objectives, and processes to achieve them, and to embed a culture of compliance (ISO 37301). | [11] |
| Three Lines Model | The IIA's governance model distinguishing three roles — first line (operational management owning and managing risk), second line (risk/compliance oversight and expertise), third line (independent internal audit assurance) — coordinated by the governing body, with external assurance as a fourth reference point (2020 update of the "three lines of defence"). | [15] |
| Records of Processing Activities (RoPA) | The written record of processing operations a controller (and processor) must maintain under GDPR Art. 30, documenting purposes, categories of data/subjects, recipients, transfers, retention and security measures. | [1][5] |
| Data protection impact assessment (DPIA) | A structured assessment, required by GDPR Art. 35 where processing is likely to result in a high risk to individuals, of the processing's necessity, proportionality and risks, and the measures to address them. | [1][7] |
| Risk register | The living record of identified risks with their assessed likelihood/impact, owner, treatment and residual rating — the operational output of the ISO 31000 risk-management process. | [12] |
| Regulatory-change management (horizon scanning) | The ongoing, assigned process of identifying, assessing and actioning changes to applicable laws, guidance and standards before they take effect. | [11] |

# Background

For most organisations, "compliance" began as a set of separate, reactive projects — a GDPR programme here, a security certification there — each owned by a different team and evidenced differently. Three pressures made that model untenable. First, the **volume and overlap of obligations** exploded: within a decade the EU adopted the GDPR, ePrivacy reforms, the AI Act, the Data Act, the DSA and DMA, NIS2, DORA and the Cyber Resilience Act, many with their own governance, documentation and incident-reporting duties that **overlap heavily**. Second, regulators shifted from *rules* to *accountability*: it is no longer enough to comply — an organisation must be able to **demonstrate** it, on demand, with documented governance and evidence (GDPR Art. 5(2)) [1]. Third, the law began naming **senior management** personally: NIS2 Art. 20 and DORA Art. 5 place approval, oversight and ultimate accountability at board level [2][3].

The response, borrowed from finance and internal audit, is to run compliance as a **managed system with defined lines of responsibility**. The **"three lines of defence"** — originally a risk-governance convention — was formalised and updated by the Institute of Internal Auditors as the **Three Lines Model (2020)** [15]. In parallel, standards bodies produced management-system standards that give the programme an auditable spine: **ISO 37301:2021** (compliance management systems, superseding the earlier ISO 19600 guidance) [11], **ISO 31000:2018** (risk management) [12], **ISO 19011** (auditing management systems) [13], and — at the governing-body level — **ISO 37000:2021** (governance of organizations) [14], all sharing the ISO harmonised (Annex SL) structure so they interlock with ISO/IEC 27001 (ISMS) and ISO/IEC 42001 (AIMS). This document sits at that programme layer.

# Legal Framework

Compliance operations is **not a single legal instrument**; it is the operating model through which an organisation discharges and evidences duties that arise across many instruments. Rather than one governing law, the following **accountability and governance duties** converge to require a managed programme:

- **GDPR (Regulation (EU) 2016/679) — accountability.** **Art. 5(2)** requires the controller to be responsible for, and *able to demonstrate* compliance with, the data-protection principles; **Art. 24** requires implementing (and reviewing) appropriate technical and organisational measures and, where proportionate, data-protection policies. The GDPR then prescribes the **core artefacts** a programme operates: **Art. 30** (records of processing), **Art. 28** (processor contracts), **Art. 35** (DPIAs), **Arts. 33–34** (breach notification), and **Arts. 37–39** (the Data Protection Officer) [1]. *(Legal obligation.)*
- **NIS2 (Directive (EU) 2022/2555) — management-body accountability.** **Art. 20** requires management bodies of essential and important entities to **approve and oversee** cybersecurity risk-management measures and to **undergo training**, with possible personal liability; **Art. 21** sets the measures; **Art. 23** sets the incident-reporting duties (24h/72h/1-month) [2]. *(Legal obligation.)*
- **DORA (Regulation (EU) 2022/2554) — ultimate accountability for ICT risk.** **Art. 5** makes the **management body ultimately responsible** for ICT risk with defined roles, approval of the framework and training; **Art. 17–19** govern incident management, classification and reporting; **Art. 28** sets ICT third-party risk principles [3]. *(Legal obligation.)*

The common thread is **accountability discharged through a documented, senior-owned, continually reviewed programme**. Standards (ISO 37301, ISO 31000, the Three Lines Model) are the recognised, non-binding means of meeting these duties systematically [11][12][15].

## Relevant Articles

*These articles are stated in full in the respective topic documents; listed here as the duties the compliance programme operationalises.*

| Article | Obligation (the programme operationalises) | Source |
|---------|---------------------------------------------|--------|
| GDPR Art. 5(2) | **Accountability** — be responsible for and *demonstrate* compliance. | [1] |
| GDPR Art. 24 | Controller responsibility; implement, review and update appropriate measures/policies. | [1] |
| GDPR Art. 28 | Processor engagement only under a binding contract with prescribed terms (third-party management). | [1] |
| GDPR Art. 30 | **Records of processing activities (RoPA).** | [1] |
| GDPR Art. 33 / 34 | Personal-data breach notification to the supervisory authority (**72h**) and to data subjects (high risk). | [1] |
| GDPR Art. 35 | **Data protection impact assessment** for high-risk processing. | [1] |
| GDPR Arts. 37–39 | Designation, position and tasks of the **Data Protection Officer**. | [1] |
| NIS2 Art. 20 | **Governance** — management bodies approve/oversee measures; mandatory training; liability. | [2] |
| NIS2 Art. 23 | Incident reporting — **24h early warning, 72h notification, 1-month final report**. | [2] |
| DORA Art. 5 | ICT governance — **management body ultimately accountable**; roles, approval, training. | [3] |
| DORA Art. 19 | Reporting of **major ICT-related incidents** to competent authorities. | [3] |
| DORA Art. 28 | ICT **third-party risk** management principles; register of information. | [3] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| GDPR Recital 74 | Controller responsibility and liability — measures should account for risk and be able to *demonstrate* compliance (the accountability rationale for a programme). | [1] |
| GDPR Recital 82 | Records of processing enable the controller/processor to monitor compliance and cooperate with the supervisory authority (why RoPA exists operationally). | [1] |
| NIS2 Recital 91 | Management bodies should approve measures and be trainable/accountable, reflecting the governance emphasis of Art. 20. | [2] |
| DORA Recital 45 | Sound ICT governance requires clear management-body responsibility — the basis for Art. 5 ultimate accountability. | [3] |

*Recitals are not binding but aid interpretation.*

## Relevant Case Law

**Not Applicable.** Compliance operations is an **operating model synthesised across multiple instruments and voluntary standards** (ISO 37301, ISO 31000, the Three Lines Model), not a single statute construed by a distinct line of case law. Enforcement decisions that turn on *failures of accountability, records or breach handling* arise under the substantive regimes — for example GDPR Art. 5(2)/Art. 30/Art. 33 enforcement (see `gdpr-foundations`) or NIS2/DORA supervision (see `nis2-foundations`, `dora-foundations`) — and are treated in those documents, not here. [1][2][3]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **ICO (UK) — accountability as a programme.** The ICO's **Accountability and Governance** guidance frames accountability as an ongoing organisational responsibility that must be *demonstrated* through documented governance, policies, RoPA, DPIAs, training and a designated DPO where required; its **Accountability Framework** is a practical, ten-category self-assessment tool for building exactly the programme this document describes [4][5][6][7][8]. *(Regulatory interpretation.)*
- **ICO — breach handling.** The ICO's personal-data-breach guidance operationalises GDPR Arts. 33–34: assess without undue delay, notify the ICO within **72 hours** where the breach is likely to result in a risk, and notify affected individuals where the risk is high; keep an internal breach log regardless of whether notification is required [9]. *(Regulatory interpretation.)*
- **EDPB — consistency across the EU.** The EDPB's guidelines and recommendations (on Art. 25, DPIAs, breach notification, DPOs, etc.) are the authoritative gloss on how the GDPR's accountability artefacts should be operated across Member States; a programme should track and align to them [10]. *(Regulatory interpretation.)*
- **Interpretive caution — certification is evidence, not a safe harbour.** Certification to ISO 37301 (or ISO/IEC 27001/42001) and alignment to the Three Lines Model are **evidence of diligence, not conclusive proof of legal compliance**; regulators assess actual compliance with the underlying duties, for which a certificate is supporting — not determinative — evidence [1][11]. *(Regulatory interpretation.)*

# Technical Considerations

- **Adopt a management-system spine.** ISO 37301 follows the ISO harmonised structure (context, leadership, planning, support, operation, performance evaluation, improvement) with compliance-specific requirements — compliance obligations register, compliance risk assessment, compliance function, and top-management leadership — so the programme is auditable and interlocks with ISO/IEC 27001 and ISO/IEC 42001 [11]. *(Best practice.)*
- **Run one risk process, many registers.** ISO 31000's process (establish scope/context/criteria → identify → analyse → evaluate → treat → monitor → record/report) should drive a **single risk taxonomy** feeding topic-specific registers (privacy, security, AI, resilience), so the board sees one aggregated risk picture rather than silos [12]. *(Best practice.)*
- **Instrument the Three Lines.** Make the first line (product/engineering/operations) own and evidence controls in-workflow; give the second line (compliance, privacy/DPO, security, risk) oversight tooling and a challenge role; and preserve **independent** third-line internal audit reporting to the governing body [15]. *(Best practice.)*
- **Build artefacts as data, not documents.** RoPA (Art. 30), DPIAs (Art. 35), the risk register, the processor/vendor inventory (Art. 28) and the control library should live in a governance tool with owners, review dates and cross-mappings — so evidence is queryable and accountability is demonstrable on demand [1][5]. *(Best practice grounded in Art. 5(2).)*
- **Engineer the incident pipeline once.** A single detection-to-report workflow should classify an event and fan out to the correct clocks: GDPR Art. 33 (72h to the DPA), NIS2 Art. 23 (24h/72h/1-month to the CSIRT) and DORA Art. 19 (ESA templates), with pre-drafted templates and drills [1][2][3]. *(Legal obligation + best practice.)*
- **Metrics by design.** Define KPIs (RoPA coverage, DPIA completion rate, overdue actions, training completion, time-to-detect/report, vendor-assessment currency) as by-products of the tooling, not a manual reporting exercise [11][13]. *(Best practice.)*

# Hosting Considerations

- **Cloud is a shared-responsibility, third-party-risk problem.** Hosting on a cloud provider engages GDPR **Art. 28** (a compliant processor contract / DPA) and, for financial entities, **DORA Art. 28** ICT third-party principles and the register of information; the compliance programme must inventory the provider, map the control split, and evidence due diligence [1][3]. *(Legal obligation.)*
- **Certifications feed assurance, not replace it.** Provider certifications (ISO/IEC 27001, SOC 2, ISO 37301) are inputs to the second/third-line assurance process; the controller/entity retains accountability and must independently assess residual risk [11][16]. *(Best practice.)*
- **Locate evidence and logs deliberately.** RoPA transfer records, breach-relevant logs and audit trails must be retained in the hosting environment consistently with GDPR storage-limitation and security duties (Arts. 5, 32) — coordinate with `privacy-engineering-foundations` and `cybersecurity-foundations` [1]. *(Legal obligation.)*

# Game Hosting Considerations

- **Scale the programme to risk, do not skip it.** A games studio still processes player personal data (accounts, telemetry, payments) and so owes GDPR accountability — RoPA, DPIAs for high-risk features, a breach process and, where thresholds are met, a DPO — even if lighter-weight than a bank's DORA programme [1][6][7]. *(Legal obligation, proportionate.)*
- **Third-party/live-ops sprawl.** Games rely on many SDKs, analytics, ad and anti-cheat vendors; each is an Art. 28 processor relationship to be contracted, inventoried and risk-assessed in the vendor register [1]. *(Legal obligation.)*
- **Incident readiness for always-on services.** Real-time multiplayer and account systems are attractive breach targets; a 72-hour GDPR clock (Art. 33) and — for larger operators potentially in scope of NIS2 — a 24h/72h clock (Art. 23) demand a pre-drilled runbook, not an ad hoc response [1][2][9]. *(Legal obligation once in scope.)*

# AI Considerations

- **AI governance is a sub-system of the compliance programme.** ISO/IEC 42001 (AIMS) shares the ISO management-system structure with ISO 37301, so an AI management system should plug into — not sit apart from — the compliance operating model, sharing the risk register, incident pipeline and audit programme (see `ai-governance-foundations`) [11]. *(Best practice.)*
- **Reuse artefacts across regimes.** AI system impact assessments should dovetail with GDPR DPIAs (Art. 35), and AI vendor/model-provider due diligence with the Art. 28 third-party process, so one assessment serves multiple duties [1][7]. *(Best practice + legal obligation where DPIA triggered.)*
- **AI in the compliance function itself.** AI can accelerate horizon-scanning, control testing and incident triage, but automated triage must not delay statutory reporting clocks (GDPR 72h; NIS2 24h/72h; DORA Art. 19) or degrade report accuracy, and its use is itself subject to governance [2][3]. *(Best practice / cross-reference.)*
- **The AI Act adds, it does not replace.** High-risk AI providers owe a quality-management system (AI Act Art. 17) that maps closely to ISO/IEC 42001 and, by extension, to this programme; substantive AI-Act obligations are covered in `ai-act-foundations`. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Assign accountability at the top.** Name senior/board owners for the programme and for each regime; secure documented approval and oversight and complete required training. *(OBLIGATION via GDPR Art. 5(2), NIS2 Art. 20, DORA Art. 5.)* [1][2][3]
2. **Appoint a DPO where required** and give the role independence, resources and reporting lines (GDPR Arts. 37–39); appoint a compliance function under ISO 37301 more broadly. *(OBLIGATION where triggered; BEST PRACTICE otherwise.)* [1][6][11]
3. **Stand up a Compliance Management System.** Adopt ISO 37301; build a **compliance obligations register** mapping each applicable law to owners, controls and evidence. *(BEST PRACTICE.)* [11]
4. **Operate one risk process (ISO 31000).** Maintain a live risk register with owners, treatment and residual ratings; aggregate topic registers into a board view; re-assess on material change. *(BEST PRACTICE; OBLIGATION-adjacent via Art. 24.)* [1][12]
5. **Structure roles by the Three Lines Model.** First line owns risk; second line (compliance/privacy/security) oversees; third line (internal audit) provides independent assurance to the governing body. *(BEST PRACTICE.)* [15]
6. **Maintain the core GDPR artefacts.** Keep RoPA current (Art. 30); run DPIAs for high-risk processing (Art. 35); use compliant processor contracts (Art. 28). *(OBLIGATION.)* [1][5][7]
7. **Run policies, procedures and training as a managed cycle** — approved, versioned, communicated, and evidenced with completion metrics. *(OBLIGATION-adjacent via Art. 24; BEST PRACTICE.)* [1][11]
8. **Govern third parties and the supply chain** — inventory vendors, risk-assess, contract (Art. 28 / DORA Art. 28), and monitor; keep the DORA register of information where in scope. *(OBLIGATION.)* [1][3]
9. **Build one incident/breach process for many clocks** — detection, classification, and fan-out to GDPR Art. 33/34 (72h), NIS2 Art. 23 (24h/72h/1-month) and DORA Art. 19; drill it. *(OBLIGATION.)* [1][2][3][9]
10. **Assure and measure.** Run internal audit (ISO 19011), track KPIs, and report to the governing body; pursue external certification where it adds value. *(BEST PRACTICE; EDITORIAL RECOMMENDATION for certification.)* [11][13]
11. **Watch the regulatory horizon.** Assign ownership and cadence to horizon-scanning (Digital Omnibus, NIS2 transposition, DUAA 2025, evolving guidance) and route changes into the obligations register. *(EDITORIAL RECOMMENDATION.)* [2][10]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | No clear accountability; programme ownerless/ad hoc | High | High | GDPR Art. 5(2); NIS2 Art. 20; DORA Art. 5 [1][2][3] | Named senior owners; board approval/oversight; training | Medium |
| R2 | Siloed, duplicated compliance per regime; no shared system | High | Medium | Overlapping duties; Art. 24 [1] | ISO 37301 CMS; single obligations register; shared artefacts | Low |
| R3 | Incident/breach reporting deadlines missed or mis-routed | Medium | High | GDPR Art. 33; NIS2 Art. 23; DORA Art. 19 [1][2][3] | One runbook, pre-drafted templates, clock-mapping, drills | Medium |
| R4 | RoPA/DPIA/vendor records stale or incomplete | Medium | High | GDPR Arts. 30, 35, 28 [1][5][7] | Governance tooling with owners and review dates | Low |
| R5 | Third-party/supply-chain risk unmanaged | Medium | High | GDPR Art. 28; DORA Art. 28 [1][3] | Vendor inventory, risk assessment, contracts, monitoring | Medium |
| R6 | No independent assurance; controls unverified | Medium | Medium | Three Lines Model; ISO 19011 [13][15] | Independent internal audit to governing body; testing | Low |
| R7 | Certification treated as legal safe harbour | Medium | High | Certification is evidence, not compliance [11] | Map controls to actual duties; keep evidence trail | Low |
| R8 | Regulatory change missed; obligations out of date | Medium | Medium | Rulebook in flux [2][10] | Assigned horizon-scanning; obligations-register updates | Low |
| R9 | Metrics absent; programme not demonstrably effective | Low | Medium | Art. 5(2) accountability [1] | KPIs, monitoring, board reporting | Low |

# Implementation Roadmap

- **Phase 0 — Governance & accountability:** Assign senior/board ownership; confirm DPO/compliance-function requirements; establish the governing-body oversight cadence. *Effort:* Medium. *Depends on:* topic-document triage of applicable regimes.
- **Phase 1 — Obligations register & CMS:** Adopt ISO 37301; build the compliance obligations register mapping every applicable law (from the 12 topic documents) to owners, controls and evidence. *Effort:* High.
- **Phase 2 — Risk framework & Three Lines:** Implement the ISO 31000 process and a single risk register; define first/second/third-line roles. *Effort:* High.
- **Phase 3 — Core artefacts:** Stand up RoPA (Art. 30), DPIA process (Art. 35), policies/procedures, training, and the vendor register (Art. 28 / DORA Art. 28). *Effort:* High.
- **Phase 4 — Incident & assurance:** Build the unified incident/breach runbook (GDPR/NIS2/DORA clocks) and the internal-audit programme (ISO 19011); define KPIs. *Effort:* High.
- **Phase 5 — Continual improvement:** Operate horizon-scanning, metrics/board reporting, periodic audit and (optional) external certification; re-assess on change. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Compliance reactive and project-based; no shared ownership. | No obligations register; ad hoc artefacts; no board oversight. |
| 2 | Managed | Basic accountability and artefacts exist per regime, largely siloed. | Named owners; partial RoPA/DPIA; some policies. |
| 3 | Defined | A CMS and shared risk process are in place; artefacts mapped across regimes. | ISO 37301 adopted; single risk register; Three Lines defined. |
| 4 | Quantitatively Managed | Controls measured and independently assured; KPIs drive the board view. | Internal audit operating; KPIs on RoPA/DPIA/incident/training; unified incident runbook drilled. |
| 5 | Optimising | Integrated, continually improved programme; horizon-scanning and certification embedded. | Certified CMS/ISMS/AIMS; regulatory-change loop; cross-regime evidence on demand. |

# Audit Questions

1. Who is accountable for the compliance programme, and how do the DPO/compliance function and the governing body exercise and evidence oversight? *(GDPR Art. 5(2); NIS2 Art. 20; DORA Art. 5 [1][2][3].)*
2. Is there a compliance obligations register mapping every applicable law to owners, controls and evidence? *(ISO 37301 [11].)*
3. How is risk identified, assessed, treated and monitored, and aggregated into a board-level view? *(ISO 31000 [12].)*
4. Are the three lines (ownership, oversight, independent audit) defined and operating, with internal audit independent of management? *(Three Lines Model; ISO 19011 [13][15].)*
5. Is the RoPA current and complete, and are DPIAs conducted for high-risk processing? *(GDPR Arts. 30, 35 [1][5][7].)*
6. How are third parties inventoried, risk-assessed and contracted (Art. 28 / DORA Art. 28), and is the register of information maintained where required? *([1][3].)*
7. Is there a single incident/breach runbook that services the GDPR 72h, NIS2 24h/72h/1-month and DORA Art. 19 clocks, and is it drilled? *([1][2][3][9].)*
8. What KPIs and monitoring evidence the programme's effectiveness, and how are they reported? *(Accountability [1][11].)*
9. How is regulatory change tracked and routed into the obligations register? *([2][10].)*

# Implementation Checklist

- [ ] Senior/board accountability assigned; oversight cadence and training in place (Art. 5(2); NIS2 Art. 20; DORA Art. 5).
- [ ] DPO appointed where required; compliance function established (Arts. 37–39; ISO 37301).
- [ ] Compliance obligations register maps all applicable regimes to owners, controls and evidence.
- [ ] ISO 31000 risk process operating; single risk register with owners and residual ratings.
- [ ] Three Lines Model roles defined; internal audit independent and reporting to the governing body.
- [ ] RoPA current (Art. 30); DPIA process operating for high-risk processing (Art. 35).
- [ ] Policies, procedures and training managed as a versioned, evidenced cycle.
- [ ] Vendor/third-party register with risk assessments and Art. 28 / DORA Art. 28 contracts.
- [ ] Unified incident/breach runbook (GDPR 72h; NIS2 24h/72h/1-month; DORA Art. 19) drilled.
- [ ] Internal audit programme (ISO 19011) and KPIs/monitoring in place; board reporting live.
- [ ] Regulatory-change watch assigned with cadence; changes routed into the obligations register.

# References

*All links verified live on 2026-07-11 (`sources_verified`) via HTTP 200 checks.*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Arts. 5(2), 24, 28, 30, 33, 34, 35, 37–39 and Recitals 74, 82. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [2] **Directive (EU) 2022/2555 (NIS2)** — Arts. 20, 21, 23; Recital 91. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj
- [3] **Regulation (EU) 2022/2554 (DORA)** — Arts. 5, 17–19, 28; Recital 45. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj

## Regulatory Guidance

- [4] **Guide to accountability and governance.** Information Commissioner's Office (ICO, UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/guide-to-accountability-and-governance/
- [5] **Documentation (records of processing activities).** ICO (UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/guide-to-accountability-and-governance/documentation/
- [6] **Data protection officers.** ICO (UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/guide-to-accountability-and-governance/data-protection-officers/
- [7] **Data protection impact assessments (DPIAs).** ICO (UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/guide-to-accountability-and-governance/data-protection-impact-assessments/
- [8] **Accountability Framework.** ICO (UK). https://ico.org.uk/for-organisations/accountability-framework/
- [9] **Personal data breaches — report a breach.** ICO (UK). https://ico.org.uk/for-organisations/report-a-breach/personal-data-breach/
- [10] **Guidelines, Recommendations and Best Practices.** European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/general-guidance/guidelines-recommendations-best-practices_en

## Standards

- [11] **ISO 37301:2021 — Compliance management systems — Requirements with guidance for use.** ISO. https://www.iso.org/standard/75080.html
- [12] **ISO 31000:2018 — Risk management — Guidelines.** ISO. https://www.iso.org/standard/65694.html
- [13] **ISO 19011:2018 — Guidelines for auditing management systems.** ISO. https://www.iso.org/standard/70017.html
- [14] **ISO 37000:2021 — Governance of organizations — Guidance.** ISO. https://www.iso.org/standard/65036.html
- [15] **The IIA's Three Lines Model — An update of the Three Lines of Defense (July 2020).** The Institute of Internal Auditors (IIA). https://www.theiia.org/globalassets/documents/resources/the-iias-three-lines-model-an-update-of-the-three-lines-of-defense-july-2020/three-lines-model-updated-english.pdf
- [16] **ISO/IEC 27001:2022 — Information security management systems.** ISO/IEC (third-party/hosting assurance input). https://www.iso.org/standard/27001

## Academic Sources

Not Applicable — this operational capstone relies on primary legislation, regulator guidance and recognised management-system standards. Academic analysis (e.g., internal-audit theory, compliance-effectiveness measurement) will be cited in the spun-off sub-topic documents (`compliance-audit-methodology`).

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- ISO 31000 risk-management landing page (principles/framework/process overview). https://www.iso.org/iso-31000-risk-management.html
- ISO 37000:2021 — Governance of organizations — Guidance (board-level governance context). https://www.iso.org/standard/65036.html

# Related Documents

*This capstone operationalises every substantive topic document in the knowledge base. Each is the authoritative source for the duties the programme discharges.*

- `gdpr-foundations` — accountability (Art. 5(2)), RoPA (Art. 30), DPIAs (Art. 35), breach notification (Arts. 33–34), DPO (Arts. 37–39): the **core anchor** for this programme.
- `uk-gdpr-foundations` — UK equivalents; ICO accountability framework and DUAA 2025 changes.
- `eprivacy-foundations` — ePrivacy/PECR obligations the programme must track (consent, marketing).
- `privacy-engineering-foundations` — DPbDD and Art. 32 controls the programme evidences.
- `ai-act-foundations` — AI Act duties (incl. Art. 17 QMS) the programme operationalises.
- `ai-governance-foundations` — the AIMS (ISO/IEC 42001) sub-system that plugs into this programme.
- `data-act-foundations` — Data Act access/sharing and cloud-switching obligations to govern.
- `dsa-foundations` — DSA platform obligations, transparency and risk management to operate.
- `dma-foundations` — DMA gatekeeper obligations and compliance reporting to operate.
- `nis2-foundations` — governance (Art. 20) and incident reporting (Art. 23) feeding the incident runbook.
- `dora-foundations` — ICT governance (Art. 5), incident reporting (Art. 19) and third-party (Art. 28).
- `cybersecurity-foundations` — the security controls and ISMS the programme assures.
- `consumer-rights` *(topic not yet started)* — consumer-protection duties to fold into the obligations register (planned).
- `cloud-hosting` *(topic not yet started)* — hosting/cloud compliance operations (planned).
- `game-hosting` *(topic not yet started)* — game-hosting-specific compliance operations (planned).
- `compliance-audit-methodology`, `compliance-policy-library`, `incident-response-playbooks` — out-of-scope spin-offs (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft of the cross-cutting compliance-operations capstone; anchored on GDPR Art. 5(2) accountability, NIS2 Art. 20 and DORA Art. 5 governance duties; operationalised via ISO 37301, ISO 31000, ISO 19011 and the IIA Three Lines Model (2020). Standard editions and IIA model version live-verified; all external links checked HTTP 200 on 2026-07-11 (IIA Three Lines Model cited to the official position-paper PDF, as the HTML landing page returns 404). | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at batch human review gate; capstone completing all 16 topics; frozen in release 0.9.0. | Human reviewer |
