---
id: compliance-audit-methodology
title: "Compliance Audit & Assurance Methodology"
version: 1.0.0
status: in-review
classification: public
jurisdiction: [EU, UK]
topic: Compliance Operations
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [compliance-operations-foundations, dpia-methodology, gdpr-foundations, uk-gdpr-foundations, dora-foundations, nis2-foundations, cybersecurity-foundations, ai-governance-foundations]
tags: [compliance-audit, assurance, iso-19011, iso-37301, three-lines-model, internal-audit, audit-programme, ropa, accountability, second-party-audit, dora-third-party, continuous-control-monitoring, maturity-model]
legal_basis: GDPR Art. 5(2) accountability (Reg (EU) 2016/679), operationalised via ISO 19011:2018, ISO 37301:2021 and the IIA Three Lines Model (2020); processor/third-party audit rights under GDPR Art. 28 and DORA Art. 30 (Reg (EU) 2022/2554)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | compliance-audit-methodology |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.15.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer (loop-authorised) — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is the **audit-and-assurance depth layer** beneath `compliance-operations-foundations`, which introduces audit as one element of the operating model; here we set out *how to design, run and report a compliance-audit programme* and how to audit a data-protection programme against GDPR accountability.

# Executive Summary

**Compliance audit and assurance** is the discipline of independently and systematically checking whether a compliance programme actually works — that controls exist, operate as designed, and discharge the underlying legal duties — and of reporting the result to those charged with governance. Its authoritative method is **ISO 19011:2018**, the international guideline for auditing management systems, which supplies the **audit principles** (integrity, fair presentation, due professional care, confidentiality, independence, evidence-based approach, and a risk-based approach) and the **audit-programme lifecycle** (establish → implement → monitor → review and improve), with each engagement running plan → conduct → report → follow-up [7]. Assurance roles are structured by the **IIA Three Lines Model (2020)**: management owns and manages risk (first line), risk/compliance functions provide oversight and expertise (second line), and **internal audit provides independent assurance** to the governing body (third line) [10].

Audit is not free-floating: it exists to test discharge of real duties. The anchor duty in EU/UK data-protection law is **accountability** — GDPR **Article 5(2)** requires a controller to be able to **demonstrate** compliance, and the audit is a principal way that demonstration is tested and evidenced [1]. A data-protection audit therefore checks the accountability artefacts against their legal criteria: **Article 30** records of processing (RoPA), **Article 35** DPIAs, **Article 32** security measures, and **Article 28** processor governance [1]. In the UK the **ICO's Accountability Framework and its data-protection audit function** give a ready-made, ten-category set of audit criteria and a maturity vocabulary [5][6].

Three conclusions dominate. First, **independence is the value of assurance** — an audit's worth depends on the auditor being organisationally separate from what is audited, which is why third-line internal audit reports to the audit committee, not to management [10][11]. Second, **audit is criteria-based and evidence-based** — findings must be measured against defined criteria (law, standard, policy) and supported by verifiable, appropriately sampled evidence, not opinion [7]. Third, **assurance is a cycle, not an event** — a risk-based audit universe, scheduled programme, tracked findings, follow-up and increasingly **continuous control monitoring** turn point-in-time checks into ongoing confidence [7][9].

# Key Takeaways

- **ISO 19011:2018** is the recognised methodology for auditing management systems; it defines the audit **principles**, the **audit-programme** lifecycle, and the per-engagement flow (planning → conducting → reporting → follow-up) that this document adopts [7]. *(Best practice.)*
- **Independence and objectivity are the point of assurance.** Under the **Three Lines Model**, internal audit (third line) must be **independent of management** and report to the governing body; the second line (compliance/risk) provides oversight but is *not* independent assurance [10][11]. *(Best practice.)*
- **Audit tests a legal duty, not just a process.** GDPR **Art. 5(2)** accountability requires the controller to **demonstrate** compliance; a data-protection audit is a primary means of testing and evidencing that demonstration [1]. *(Legal obligation anchoring the audit.)*
- **A data-protection audit measures the accountability artefacts against their criteria:** RoPA completeness (**Art. 30**), DPIA coverage and quality (**Art. 35**), security measures (**Art. 32**), and processor governance (**Art. 28**) [1]. *(Legal obligations as audit criteria.)*
- **Findings must be criteria-based and evidence-based.** A finding states the *criterion*, the *evidence* (audit trail — verifiable records/observations/interviews), and the *conclusion* (conformity or nonconformity); sampling must be planned and representative [7]. *(Best practice.)*
- **The audit universe is risk-based.** ISO 19011 requires the audit programme to be built on risk and importance, so scarce audit effort concentrates on the highest-risk processing, systems and suppliers [7][9]. *(Best practice.)*
- **The ICO gives UK organisations ready audit criteria.** The **Accountability Framework** (ten categories) and the ICO's **data-protection audit** function/toolkit supply criteria and a maturity scale to audit a privacy programme against [5][6]. *(Regulatory interpretation / tooling.)*
- **Second-party (supplier) audits are contractually and legally grounded.** GDPR **Art. 28(3)(h)** entitles a controller to audit/inspect a processor; **DORA Art. 30(3)** requires financial entities' ICT third-party contracts to include audit and access rights [1][2]. *(Legal obligation.)*
- **Working papers and reporting close the loop.** Retain audit evidence and working papers; report conclusions, nonconformities and a maturity view to the **audit committee/governing body**, and **track corrective actions to closure** with follow-up [7][11][12]. *(Best practice.)*
- **Continuous control monitoring (CCM) augments periodic audit.** Automated, ongoing testing of key controls narrows the gap between audits and feeds the risk-based programme, but it **does not replace** independent assurance [7][9]. *(Best practice / editorial.)*

# Purpose

This document gives internal audit, compliance, privacy, risk and engineering teams an **evidence-based, repeatable methodology** for standing up and running a compliance-audit and assurance programme: defining a risk-based audit universe; planning and scoping engagements; setting audit criteria; collecting and sampling evidence; raising and grading findings; scoring maturity; reporting to the audit committee; auditing a data-protection programme against GDPR accountability; conducting second-party supplier audits; and operating continuous control monitoring. It operationalises the audit-and-assurance element introduced in `compliance-operations-foundations` and complements `dpia-methodology` (which supplies one of the artefacts an audit tests).

# Scope

**In scope:** Audit principles and the ISO 19011:2018 audit-programme lifecycle (establish → implement → monitor → review/improve) and the per-engagement flow (initiating, planning, conducting on-site/remote work, evidence collection and sampling, generating findings, preparing and distributing the report, completing and follow-up); the IIA Three Lines Model and auditor **independence/objectivity**; building a **risk-based audit universe**; auditing a **data-protection programme** against GDPR accountability (Art. 5(2), Art. 30 RoPA, Art. 35 DPIAs, Art. 32 security, Art. 28 processors) and against the **ICO Accountability Framework**; **second-party/supplier audits** (GDPR Art. 28 audit rights; DORA third-party audit rights); **evidence, working papers, maturity scoring** and **audit-committee reporting**; and **continuous control monitoring**. The document provides an **audit-programme template**, a **sample audit checklist**, and a **maturity model**.

**Out of scope (covered elsewhere or in the backlog):** The wider compliance operating model, CMS and governance → `compliance-operations-foundations` (parent); the **DPIA method** whose output an audit tests → `dpia-methodology`; **penetration testing / threat-led penetration testing (TLPT)** and technical security testing, which are assurance activities of a different kind → `dora-foundations`, `cybersecurity-foundations`; **certification audits** to ISO/IEC 27001 or ISO 37301 conducted by accredited certification bodies (third-party certification), which follow ISO/IEC 17021 rather than this internal-audit method — referenced but not detailed; and the substantive article-by-article law of each regime → the respective topic documents.

**Assumptions:** The reader has read `compliance-operations-foundations` (Three Lines Model, CMS, accountability) and understands controller/processor roles. "Accountability", "controller", "processor", "RoPA" and "DPIA" carry their `GLOSSARY.md` / `dpia-methodology` meanings. "Audit" here means a systematic, independent, documented evaluation against criteria — not a financial-statement audit.

# Definitions

*Shared terms (accountability, controller, processor, RoPA, DPIA, Three Lines Model) are defined in `GLOSSARY.md` and `compliance-operations-foundations`. Only audit-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Audit | A systematic, independent and documented process for obtaining objective evidence and evaluating it objectively to determine the extent to which the **audit criteria** are fulfilled (ISO 19011, 3.1). | [7] |
| Audit criteria | The set of requirements — policies, procedures, legal obligations or standard requirements — used as a **reference** against which objective evidence is compared (ISO 19011, 3.7). | [7] |
| Audit evidence | Records, statements of fact or other information relevant to the audit criteria and **verifiable** (ISO 19011, 3.8). | [7] |
| Audit findings | The results of evaluating the collected audit evidence against the audit criteria — conformity, nonconformity, or opportunity for improvement (ISO 19011, 3.10). | [7] |
| Audit programme | Arrangements for a **set of one or more audits** planned for a specific time frame and directed towards a specific purpose (ISO 19011, 3.4). | [7] |
| Audit universe | The complete inventory of auditable entities (processes, systems, suppliers, regimes) from which the risk-based audit programme is selected. *(Practice term; not an ISO 19011 defined term.)* | [7][9] |
| First-party / second-party / third-party audit | Internal audit (first-party); an audit of a supplier/other party with an interest, e.g. a customer auditing a processor (second-party); and an audit by an independent external body, e.g. certification (third-party) (ISO 19011, Table A.1). | [7] |
| Independence (of internal audit) | The freedom from conditions that threaten the internal audit function's ability to carry out responsibilities in an unbiased manner; achieved organisationally by reporting functionally to the governing body/audit committee. | [10][11] |
| Working papers | The documented evidence, plans, sampling records, tests and notes supporting the audit findings and conclusions; retained as the accountability trail for the audit itself. | [7] |
| Continuous control monitoring (CCM) | The automated, ongoing testing of the operating effectiveness of key controls, producing near-real-time assurance that supplements periodic audit. | [7][9] |
| Nonconformity | Non-fulfilment of a requirement (an audit criterion); typically graded (e.g. major/minor) and requiring corrective action. | [7][8] |

# Background

Compliance auditing grew out of two older traditions. The first is **financial and internal audit**, which developed the concepts of independence, evidence, sampling, working papers and reporting to an audit committee, and which the **Institute of Internal Auditors (IIA)** codified — historically as the "three lines of defence", refreshed in 2020 as the **Three Lines Model**, and in its professional standards, most recently the **2024 Global Internal Audit Standards** [10][11]. The second is **management-system auditing**, which arose alongside ISO management-system standards (quality, environment, information security) and produced a common auditing method now consolidated in **ISO 19011:2018 — Guidelines for auditing management systems** [7]. ISO 19011 deliberately spans *first-party* (internal) and *second-party* (supplier) audits and informs *third-party* (certification) audits governed by ISO/IEC 17021.

Data-protection auditing gained statutory weight with the GDPR's shift to **accountability**. Under the old notification model, regulators held the register; under GDPR **Art. 5(2)** the organisation must itself be able to **demonstrate** compliance, which makes internal audit and self-assessment central to survival, not optional [1]. Regulators built tooling to match: the UK **ICO** publishes an **Accountability Framework** — ten categories with expectations an organisation can audit itself against — and operates a **data-protection audit** function (consensual and, in defined cases, compulsory) with published methodology and toolkits [5][6]. In parallel, the **digital-resilience** rulebook added supplier-audit duties: **DORA** requires ICT third-party contracts to grant audit and access rights, hard-wiring second-party audit into financial-sector supply chains [2]. Compliance audit today therefore blends internal-audit independence, ISO 19011 method, and regime-specific criteria.

# Legal Framework

Compliance audit is a **method**, not a single legal instrument; but it exists to test **duties**, and several instruments both anchor and mandate audit-type assurance. State the obligation first, then the method.

- **GDPR (Regulation (EU) 2016/679) — accountability and audit rights.** **Art. 5(2)** requires the controller to be responsible for, and *able to demonstrate*, compliance with the principles; **Art. 24** requires implementing and **reviewing** appropriate measures. The artefacts an audit tests are prescribed: **Art. 30** (RoPA), **Art. 35** (DPIAs), **Art. 32** (security of processing). Crucially, **Art. 28(3)(h)** gives the controller the right to require the processor to make available information to demonstrate compliance and to **allow for and contribute to audits, including inspections** [1]. *(Legal obligation.)*
- **DORA (Regulation (EU) 2022/2554) — governance and third-party audit rights.** **Art. 5** places ultimate accountability for ICT risk on the management body; **Art. 6(5)** requires the ICT risk-management framework to be subject to **internal audit** by auditors with sufficient knowledge and independence, on a risk-based plan; **Art. 30(3)** requires contracts with ICT third-party providers to include the entity's (and competent authorities') **rights of access, inspection and audit** [2]. *(Legal obligation.)*
- **NIS2 (Directive (EU) 2022/2555) — assessing effectiveness.** **Art. 20** makes management bodies approve and oversee cybersecurity risk-management measures; **Art. 21(2)(f)** requires **policies and procedures to assess the effectiveness** of those measures — an assurance/audit duty in substance — and Member States may require independent audits [3]. *(Legal obligation.)*

The common thread: the law requires organisations to **review, assess and be able to demonstrate** the effectiveness of their measures, and to secure **audit rights over suppliers**. ISO 19011, the Three Lines Model and the IIA Standards are the recognised, non-binding means of doing so systematically [7][10][11].

## Relevant Articles

| Article | Obligation (the audit tests/relies on) | Source |
|---------|-----------------------------------------|--------|
| GDPR Art. 5(2) | **Accountability** — be responsible for and *demonstrate* compliance (the reason to audit). | [1] |
| GDPR Art. 24 | Implement, **review** and update appropriate technical/organisational measures. | [1] |
| GDPR Art. 28(3)(h) | Processor must allow for and **contribute to audits and inspections** by the controller (second-party audit right). | [1] |
| GDPR Art. 30 | **RoPA** — a primary audit criterion for a data-protection audit. | [1] |
| GDPR Art. 32 | **Security of processing**, including a process for regularly **testing/assessing effectiveness** of measures. | [1] |
| GDPR Art. 35 | **DPIA** — coverage and quality are audit criteria (see `dpia-methodology`). | [1] |
| DORA Art. 5 | Management body **ultimately accountable** for ICT risk (governs the assurance mandate). | [2] |
| DORA Art. 6(5) | ICT risk framework subject to **internal audit** by independent, competent auditors on a risk-based plan. | [2] |
| DORA Art. 30(3) | ICT third-party contracts must grant **audit, access and inspection rights** (second-party audit). | [2] |
| NIS2 Art. 20 | Management-body **approval and oversight** of measures (assurance governance). | [3] |
| NIS2 Art. 21(2)(f) | **Policies to assess the effectiveness** of cybersecurity risk-management measures. | [3] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the articles above.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| GDPR Recital 74 | Controller responsibility and liability; measures should be able to **demonstrate** compliance — the accountability basis for auditing. | [1] |
| GDPR Recital 82 | The RoPA exists so the controller/processor can **monitor** compliance and cooperate with the supervisory authority — audit uses it as evidence. | [1] |
| DORA Recital 45 | Sound ICT governance requires clear management-body responsibility — the basis for the Art. 6(5) internal-audit duty. | [2] |
| NIS2 Recital 79 | Entities should assess their own cybersecurity maturity and the effectiveness of measures — the assurance rationale behind Art. 21(2)(f). | [3] |

## Relevant Case Law

**Not Applicable — operational.** Compliance-audit methodology is an **assurance method synthesised from voluntary standards** (ISO 19011, the IIA Three Lines Model and Global Internal Audit Standards) and from the accountability/audit-rights provisions of several instruments; it is not a single statutory concept construed by a distinct line of case law. Enforcement decisions that turn on *failures the audit would detect* — inadequate RoPA (Art. 30), missing DPIAs (Art. 35), insufficient security (Art. 32) or poor processor governance (Art. 28) — arise under the substantive regimes and are treated in `gdpr-foundations`, `dpia-methodology`, `dora-foundations` and `nis2-foundations`, not here. [1][2][3]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **ICO — accountability is auditable, and the ICO publishes the criteria.** The ICO frames accountability as an ongoing responsibility that must be **demonstrated**, and provides an **Accountability Framework** organised into **ten categories** (leadership and oversight; policies and procedures; training and awareness; individuals' rights; transparency; records of processing and lawful basis; contracts and data sharing; risks and DPIAs; records management and security; breach response and monitoring). Each category sets **expectations** an organisation can audit itself against — effectively a ready-made audit checklist and maturity vocabulary [4][5]. *(Regulatory interpretation / tooling.)*
- **ICO — the audit as a regulatory instrument.** The ICO operates a **data-protection audit** function: consensual audits, advisory visits and, where powers apply, compulsory assessments, supported by published audit methodology and self-assessment toolkits. Its existence signals the regulator's expectation that organisations run their own assurance and can produce audit evidence on demand [6]. *(Regulatory interpretation.)*
- **Interpretive caution — an audit opinion is evidence, not a safe harbour.** A clean internal-audit report, or certification to ISO 37301 / ISO/IEC 27001, is **evidence of diligence, not conclusive proof of legal compliance**; a supervisory authority assesses actual compliance with the underlying duties, for which audit findings are supporting — not determinative — evidence [1][8]. *(Regulatory interpretation.)*
- **DORA supervisors — independence of the internal-audit function.** The financial-sector reading of DORA Art. 6(5) is that the ICT risk framework's internal audit must be performed by auditors with **sufficient knowledge, skill and expertise, and independence** — reinforcing that assurance carried out by the team that owns the controls is *not* the assurance the law requires [2]. *(Regulatory interpretation of a legal obligation.)*

# Technical Considerations

An audit is only as reliable as its criteria, evidence and independence. Engineering and tooling practices that make compliance audits dependable:

- **Derive the audit universe from live inventories.** Build the auditable-entity list from the **RoPA (Art. 30)**, the asset/system inventory, the DPIA register and the third-party/vendor register, so the universe reflects reality and can be **risk-ranked**; stale inventories produce blind spots [1][7][9]. *(Best practice grounded in obligation.)*
- **Make criteria explicit and traceable.** Each audit test should name its **criterion** (a specific law/standard/policy clause), so a finding maps unambiguously to a requirement — e.g. "Art. 30(1)(g): technical and organisational security measures recorded" rather than "records look thin" [1][7]. *(Best practice.)*
- **Plan sampling; do not cherry-pick.** For populations (processing activities, DSARs, vendor assessments, access reviews), define the sampling method (statistical or judgemental), sample size and selection so the evidence is **representative and defensible**; record the sampling basis in the working papers [7]. *(Best practice.)*
- **Instrument controls for continuous monitoring.** Where controls emit logs/telemetry (access reviews, retention jobs, consent records, patch levels), wire **CCM** to test them continuously and surface exceptions to the audit programme, reserving manual audit effort for judgement-heavy areas [7][9]. *(Best practice / editorial.)*
- **Keep working papers as data.** Store audit plans, criteria, tests, samples, evidence references and findings in an audit-management tool with immutable timestamps and owner/status tracking, so the audit itself is **repeatable and defensible** and follow-up is enforced [7][11]. *(Best practice.)*
- **Separate the second line from the third line in tooling and access.** Compliance/risk (second line) monitoring dashboards and internal-audit (third line) working papers should be **distinct**, with internal audit retaining independent access to evidence rather than relying solely on management's self-reported view [10][11]. *(Best practice.)*

# Hosting Considerations

- **Audit the shared-responsibility split explicitly.** For cloud-hosted processing, the audit must test **both** sides of the responsibility model: the customer-configured controls (IAM, encryption settings, logging, retention) and the provider assurances relied upon. Provider certifications (ISO/IEC 27001, SOC 2) are **inputs** to the audit, not substitutes for testing the customer's own configuration [1][8][13]. *(Best practice grounded in Art. 32.)*
- **Exercise contractual audit rights over hosting providers.** GDPR **Art. 28(3)(h)** audit/inspection rights and, for financial entities, **DORA Art. 30(3)** access/audit rights apply to cloud/hosting providers; where on-site audit is impractical, pooled audits, third-party audit reports and standardised questionnaires are accepted evidence — but the **right** must be secured in the contract [1][2]. *(Legal obligation.)*
- **Locate audit evidence deliberately.** Logs, RoPA transfer records and control evidence must be retained in the hosting environment consistently with GDPR storage-limitation and **Art. 32** security duties, and be **retrievable for the auditor** — coordinate with `cybersecurity-foundations` [1]. *(Legal obligation.)*

# Game Hosting Considerations

- **Scale the audit programme to risk, do not skip it.** A games studio still processes player personal data (accounts, telemetry, payments, chat) and owes GDPR accountability; a proportionate **risk-based audit universe** should still cover the high-risk items — children's data, profiling/matchmaking, payments and the SDK/vendor estate — even if the programme is lighter than a bank's [1][7][9]. *(Legal obligation, proportionate.)*
- **Second-party audit the live-ops supply chain.** Games rely on many analytics, ads, anti-cheat and moderation SDKs; each is an **Art. 28** processor whose audit rights should be exercised via questionnaires, evidence review or, for high-risk vendors, inspection [1]. *(Legal obligation.)*
- **Audit age-assurance and children's-code controls.** Where a service is likely to be accessed by children, the audit should test the child-protection controls and DPIAs as criteria (see `dpia-methodology`, `uk-gdpr-foundations`) [1]. *(Legal obligation / regulatory expectation.)*

# AI Considerations

- **Fold AI assurance into the audit universe.** An AI management system (ISO/IEC 42001) shares the ISO management-system structure, so **AI controls are auditable under the same ISO 19011 method**; add AI systems (models, datasets, deployments) to the audit universe and test governance, data quality, human oversight and impact assessments (see `ai-governance-foundations`) [7]. *(Best practice.)*
- **Audit the DPIA/FRIA artefacts as criteria.** For AI processing personal data, the DPIA (GDPR Art. 35) and, where applicable, the AI Act fundamental-rights impact assessment are **artefacts an audit tests** for coverage and quality; reuse the DPIA method as the criterion (see `dpia-methodology`) [1]. *(Legal obligation as criterion.)*
- **Govern AI used *within* the audit function.** AI can accelerate evidence review, control testing and sampling, but AI-assisted audit conclusions must remain **explainable and evidence-based**, must not fabricate or over-generalise from samples, and remain subject to auditor judgement and the ISO 19011 evidence principle [7]. *(Best practice / editorial.)*

# Operational Guidance

Labels: **OBLIGATION** (must, per statute) / **BEST PRACTICE** (should, per standards/regulators) / **EDITORIAL RECOMMENDATION** (we suggest).

**A. Establish and govern the audit programme (ISO 19011, Clause 5).**

1. **Define the audit-programme objectives** aligned to organisational risk, applicable law and management priorities; secure governing-body/audit-committee endorsement. *(BEST PRACTICE; OBLIGATION-adjacent via DORA Art. 6(5) risk-based plan.)* [7][2]
2. **Build a risk-based audit universe** from the RoPA, asset inventory, DPIA and vendor registers; **risk-rank** entities and set audit frequency by risk and importance. *(BEST PRACTICE.)* [1][7][9]
3. **Resource the programme with competent, independent auditors** and preserve third-line **independence** — internal audit reports functionally to the audit committee, not to audited management. *(OBLIGATION where DORA Art. 6(5)/NIS2 apply; BEST PRACTICE generally.)* [2][10][11]

**B. Plan and scope each engagement (ISO 19011, Clause 6).**

1. **Set the objective, scope and criteria** for the audit — name the specific legal/standard/policy clauses that are the criteria (e.g. GDPR Arts. 5(2), 30, 32, 35, 28). *(BEST PRACTICE; criteria include OBLIGATIONS.)* [1][7]
2. **Prepare the audit plan and checklist**, define the **sampling** approach for each population, and confirm evidence sources and access (including supplier audit rights). *(BEST PRACTICE.)* [1][7]

**C. Conduct and collect evidence (ISO 19011, Clause 6.4).**

1. **Collect and verify objective evidence** through document review, interviews, observation and re-performance; record it against criteria in the working papers. *(BEST PRACTICE.)* [7]
2. **Sample defensibly** and record the sampling basis; where a control emits telemetry, use CCM output as corroborating evidence. *(BEST PRACTICE.)* [7][9]

**D. Generate findings and report (ISO 19011, Clauses 6.4.8–6.5).**

1. **Evaluate evidence against criteria** to produce findings; grade **nonconformities** (e.g. major/minor) and note opportunities for improvement; agree facts with the auditee. *(BEST PRACTICE.)* [7][8]
2. **Score maturity** against a defined scale (see the Compliance Maturity Model) and **report to the audit committee/governing body** with conclusions, nonconformities, maturity and recommended actions. *(BEST PRACTICE; supports OBLIGATION to demonstrate under Art. 5(2).)* [1][7][11][12]

**E. Complete, follow up and improve (ISO 19011, Clauses 6.6–6.7, 5.6–5.7).**

1. **Track corrective actions to closure** with owners and due dates; **verify** remediation in follow-up before closing findings. *(BEST PRACTICE.)* [7][11]
2. **Review and improve the programme** annually — feed findings, missed risks and CCM exceptions back into the audit universe and plan. *(EDITORIAL RECOMMENDATION.)* [7][9]

**Audit-programme template (annual programme skeleton).**

| Programme element | Content | Criteria / basis |
|-------------------|---------|------------------|
| Programme objectives | Assurance goals for the year; regimes and risks covered | Org risk appetite; DORA Art. 6(5); NIS2 Art. 21(2)(f) [2][3] |
| Audit universe | Inventory of auditable entities (processes, systems, suppliers, regimes) | RoPA, asset/DPIA/vendor registers [1][7][9] |
| Risk ranking | Likelihood × impact score per entity; drives frequency | ISO 19011 risk-based approach [7] |
| Annual schedule | Engagements by quarter; lead auditor; days budgeted | ISO 19011 Clause 5 [7] |
| Independence & competence | Auditor assignment avoiding self-review; reporting line to audit committee | Three Lines Model; IIA Standards [10][11] |
| Reporting cadence | Findings log; quarterly audit-committee report; annual opinion | ISO 37000 governance reporting [12] |
| Follow-up | Corrective-action tracker; re-test dates | ISO 19011 Clause 6.6–6.7 [7] |
| Continuous monitoring | Key controls under CCM; exception thresholds | CCM / risk-based approach [7][9] |

**Sample audit checklist — data-protection accountability audit (extract).**

| # | Audit criterion | Evidence to sample | Method |
|---|-----------------|--------------------|--------|
| 1 | GDPR Art. 5(2): compliance can be *demonstrated* | Governance records; policy set; evidence library | Document review [1] |
| 2 | GDPR Art. 30: RoPA complete and current | RoPA entries vs. actual processing; last-review dates | Sample + re-perform [1] |
| 3 | GDPR Art. 35: DPIAs for high-risk processing | DPIA register vs. high-risk inventory; DPIA quality | Sample + criteria test [1] |
| 4 | GDPR Art. 32: security measures + effectiveness testing | Control config; pen-test/CCM output; access reviews | Observation + re-perform [1] |
| 5 | GDPR Art. 28: processor contracts + audit rights | DPAs; audit-right clauses; due-diligence records | Document review [1] |
| 6 | ICO Accountability Framework — 10 categories | Self-assessment vs. expectations; maturity ratings | Mapping + interview [5] |
| 7 | DORA Art. 30(3): ICT third-party audit/access rights | Contract clauses; register of information | Document review [2] |
| 8 | Breach response and monitoring | Breach log; timelines; lessons-learned actions | Sample + walkthrough [1][4] |

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Audit not independent (self-review by control owners) | Medium | High | Three Lines Model; DORA Art. 6(5) [2][10][11] | Functional reporting to audit committee; assignment rules | Low |
| R2 | Findings not evidence/criteria-based (opinion, not proof) | Medium | High | ISO 19011 evidence principle [7] | Named criteria per test; verifiable evidence in working papers | Low |
| R3 | Audit universe not risk-based; high-risk areas missed | Medium | High | ISO 19011 risk-based approach [7][9] | Risk-ranked universe from live inventories; annual review | Medium |
| R4 | RoPA/DPIA/vendor inventories stale, so scope is wrong | Medium | High | GDPR Arts. 30, 35, 28 [1] | Reconcile inventories before scoping; sample for completeness | Medium |
| R5 | Sampling unrepresentative; conclusions unsafe | Medium | Medium | ISO 19011 sampling [7] | Documented sampling method and size; record the basis | Low |
| R6 | Findings not tracked to closure; repeat issues | Medium | High | ISO 19011 follow-up [7][11] | Corrective-action tracker; re-test before closing | Low |
| R7 | Supplier audit rights not secured or not exercised | Medium | High | GDPR Art. 28(3)(h); DORA Art. 30(3) [1][2] | Contractual audit clauses; risk-based supplier audit plan | Medium |
| R8 | Audit opinion treated as legal safe harbour | Medium | High | Audit is evidence, not compliance [1][8] | Map findings to actual duties; keep evidence trail | Low |
| R9 | CCM relied on as sole assurance; no independent audit | Low | Medium | ISO 19011; Three Lines Model [7][9][10] | CCM supplements, does not replace, independent audit | Low |

# Implementation Roadmap

- **Phase 0 — Mandate & independence:** Establish the internal-audit mandate/charter; set the reporting line to the audit committee; confirm auditor competence and independence rules. *Effort:* Medium. *Depends on:* governance from `compliance-operations-foundations`.
- **Phase 1 — Audit universe & risk ranking:** Build the auditable-entity inventory from the RoPA, asset, DPIA and vendor registers; risk-rank and set frequencies. *Effort:* Medium–High.
- **Phase 2 — Method & templates:** Adopt the ISO 19011 lifecycle; create the audit-programme template, engagement checklists (incl. the data-protection accountability checklist) and the maturity model; define sampling and grading. *Effort:* Medium.
- **Phase 3 — Run first cycle:** Execute planned engagements (data-protection accountability, security/Art. 32, key suppliers); raise findings; report to the audit committee. *Effort:* High.
- **Phase 4 — Follow-up & second-party audits:** Stand up the corrective-action tracker and re-test; exercise Art. 28 / DORA Art. 30(3) supplier audit rights on high-risk vendors. *Effort:* High.
- **Phase 5 — Continuous monitoring & improvement:** Instrument key controls for CCM; feed exceptions and missed risks back into the universe; annual programme review and (optional) external certification. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Audits ad hoc or absent; no independence; no defined criteria; reactive to incidents/regulators. | No audit universe; no charter; findings undocumented. |
| 2 | Managed | Some audits done, but by control owners or without consistent method; findings not tracked. | Occasional audits; partial criteria; weak follow-up. |
| 3 | Defined | ISO 19011 method adopted; independent internal audit reporting to the audit committee; risk-based universe; documented criteria, sampling and grading. | Audit charter; risk-ranked universe; engagement checklists; findings log. |
| 4 | Quantitatively Managed | Metrics on coverage, findings, closure time and maturity; corrective actions tracked to closure; maturity scored and reported to the board. | KPIs; corrective-action tracker; audit-committee reporting; maturity scoring. |
| 5 | Optimising | Continuous control monitoring supplements periodic audit; second-party audits routine; programme continuously improved from findings and CCM exceptions; external certification where valuable. | CCM live; supplier-audit plan; annual programme review; certified CMS/ISMS. |

# Audit Questions

1. Is the internal-audit function **independent** of the areas it audits, and to whom does it report? *(Three Lines Model; DORA Art. 6(5) [2][10][11].)*
2. Is there a **risk-based audit universe and programme**, and how is it derived and reviewed? *(ISO 19011 [7][9].)*
3. For a given audit, what were the **criteria**, and can each finding be traced to a criterion and to verifiable **evidence**? *(ISO 19011 [7].)*
4. How was **sampling** designed and recorded, and is it representative? *(ISO 19011 [7].)*
5. Does the data-protection audit test **RoPA (Art. 30), DPIAs (Art. 35), security (Art. 32) and processor governance (Art. 28)** against their criteria? *(GDPR [1].)*
6. How are the **ICO Accountability Framework** categories used as audit criteria and maturity measures? *(ICO [5][6].)*
7. Are **supplier audit rights** (Art. 28(3)(h); DORA Art. 30(3)) secured contractually and exercised on high-risk vendors? *(GDPR/DORA [1][2].)*
8. Are **findings tracked to closure** with verification, and is a **maturity view reported** to the audit committee? *(ISO 19011; ISO 37000 [7][11][12].)*
9. Where **continuous control monitoring** is used, does it supplement — not replace — independent audit? *([7][9][10].)*

# Implementation Checklist

- [ ] Internal-audit charter/mandate approved; independent reporting line to the audit committee established.
- [ ] Risk-based audit universe built from RoPA, asset, DPIA and vendor registers, and risk-ranked.
- [ ] Annual audit programme scheduled with competent, independent auditors (no self-review).
- [ ] Per-engagement objective, scope and **named criteria** (incl. GDPR Arts. 5(2), 30, 32, 35, 28) defined.
- [ ] Sampling method and size documented for each population.
- [ ] Working papers capture criteria, evidence, tests, samples and findings, and are retained.
- [ ] Findings graded (major/minor); facts agreed with auditees; opportunities noted.
- [ ] Maturity scored against a defined scale and reported to the audit committee/governing body.
- [ ] Corrective-action tracker in place; remediation verified before closing findings.
- [ ] Supplier audit rights (Art. 28(3)(h); DORA Art. 30(3)) secured and exercised on high-risk vendors.
- [ ] Continuous control monitoring instrumented for key controls; exceptions feed the programme.
- [ ] Annual programme review folds findings, missed risks and CCM exceptions back into the universe.

# References

*All links verified live on 2026-07-11 (`sources_verified`) via HTTP 2xx/3xx checks.*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Arts. 5(2), 24, 28 (incl. 28(3)(h)), 30, 32, 35 and Recitals 74, 82. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [2] **Regulation (EU) 2022/2554 (DORA)** — Arts. 5, 6(5), 30(3); Recital 45. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj
- [3] **Directive (EU) 2022/2555 (NIS2)** — Arts. 20, 21(2)(f); Recital 79. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj

## Regulatory Guidance

- [4] **Guide to accountability and governance.** Information Commissioner's Office (ICO, UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/guide-to-accountability-and-governance/
- [5] **Accountability Framework** (ten-category self-assessment). ICO (UK). https://ico.org.uk/for-organisations/accountability-framework/
- [6] **Audits** (the ICO's data-protection audit function and methodology). ICO (UK). https://ico.org.uk/for-organisations/advice-and-services/audits/

## Standards

- [7] **ISO 19011:2018 — Guidelines for auditing management systems.** ISO. https://www.iso.org/standard/70017.html
- [8] **ISO 37301:2021 — Compliance management systems — Requirements with guidance for use.** ISO. https://www.iso.org/standard/75080.html
- [9] **ISO 31000:2018 — Risk management — Guidelines** (risk-based approach informing the audit universe). ISO. https://www.iso.org/standard/65694.html
- [10] **The IIA's Three Lines Model — An update of the Three Lines of Defense (July 2020).** The Institute of Internal Auditors (IIA). https://www.theiia.org/globalassets/documents/resources/the-iias-three-lines-model-an-update-of-the-three-lines-of-defense-july-2020/three-lines-model-updated-english.pdf
- [11] **Global Internal Audit Standards (2024).** The Institute of Internal Auditors (IIA). https://www.theiia.org/en/standards/2024-standards/global-internal-audit-standards/
- [12] **ISO 37000:2021 — Governance of organizations — Guidance** (governing-body/audit-committee reporting context). ISO. https://www.iso.org/standard/65036.html
- [13] **ISO/IEC 27001:2022 — Information security management systems — Requirements** (ISMS audit criteria; provider assurance input). ISO/IEC. https://www.iso.org/standard/27001

## Academic Sources

Not Applicable — this methodology rests on primary legislation (GDPR, DORA, NIS2), endorsed regulatory guidance (ICO) and recognised auditing standards (ISO 19011; the IIA Three Lines Model and Global Internal Audit Standards). Academic critique of internal-audit effectiveness and assurance-measurement limits will be cited if a dedicated assurance-metrics sub-topic is commissioned.

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- ISO 31000 risk-management landing page (principles/framework/process overview). https://www.iso.org/iso-31000-risk-management.html
- ICO — Accountability Framework landing and self-assessment resources. https://ico.org.uk/for-organisations/accountability-framework/

# Related Documents

- `compliance-operations-foundations` — **parent**; introduces audit/assurance as one element of the compliance operating model (**prerequisite reading**).
- `dpia-methodology` — supplies the DPIA artefact whose coverage and quality a data-protection audit tests.
- `gdpr-foundations` — accountability (Art. 5(2)), RoPA (Art. 30), security (Art. 32), processor terms (Art. 28) that form the audit criteria.
- `uk-gdpr-foundations` — UK context; ICO Accountability Framework and audit function apply.
- `dora-foundations` — ICT internal-audit duty (Art. 6(5)) and third-party audit rights (Art. 30(3)).
- `nis2-foundations` — management-body oversight (Art. 20) and effectiveness-assessment duty (Art. 21(2)(f)).
- `cybersecurity-foundations` — the security controls and ISMS the audit assures (Art. 32).
- `ai-governance-foundations` — the AIMS sub-system to fold into the audit universe.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Arts. 5(2), 24, 28, 30, 32, 35; DORA Arts. 5, 6(5), 30(3); NIS2 Arts. 20, 21(2)(f)), the ICO Accountability Framework and audit function, and the auditing standards ISO 19011:2018, ISO 37301:2021, ISO 31000:2018, ISO 37000:2021, ISO/IEC 27001:2022 and the IIA Three Lines Model (2020) and Global Internal Audit Standards (2024). Standard editions and the IIA model version live-verified; all external links checked HTTP 2xx/3xx on 2026-07-11 (IIA Three Lines Model cited to the official position-paper PDF). | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved via autonomous backlog loop (Cluster A); passed full QA suite; frozen in release 0.15.0. | Human reviewer (loop-authorised) |
