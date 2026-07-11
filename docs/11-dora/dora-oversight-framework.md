---
id: dora-oversight-framework
title: "DORA: Union Oversight Framework for Critical ICT Third-Party Providers"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: DORA
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [dora-foundations, dora-tlpt, dora-technical-standards, dora-third-party-contracts, cloud-shared-responsibility, nis2-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [dora, ict-third-party-risk, ctpp, union-oversight-framework, lead-overseer, joint-examination-teams, oversight-fees, subcontracting, concentration-risk, register-of-information, financial-sector, esas]
legal_basis: Regulation (EU) 2022/2554, Arts. 28–44; Commission Delegated Regulation (EU) 2024/1502 (designation criteria); Commission Delegated Regulation (EU) 2024/1505 (oversight fees); Commission Delegated Regulation (EU) 2025/532 (subcontracting)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dora-oversight-framework |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.16.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The Union Oversight Framework is now **operational**: the ESAs designated the **first list of critical ICT third-party providers (CTPPs) — 19 providers — on 18 November 2025**, and the framework's supporting delegated acts (designation criteria, oversight fees, subcontracting) are **in force**. All of these were **live-verified** for this document [1][2][3][4][5][6][7]. The **CTPP list is re-assessed and re-published annually**, and further oversight practice (examination activities, recommendations) will develop; confirm the **current CTPP list** and the live delegated-act status before relying on them [5][6].

# Executive Summary

DORA's fourth pillar (**Regulation (EU) 2022/2554**, Chapter V, Arts. 28–44) does two things at once. First, it imposes **ICT third-party risk-management** duties on every financial entity — a register of information, pre-contract due diligence, mandatory contractual provisions, concentration-risk assessment and tested exit strategies (Arts. 28–30). Second, and unusually for EU financial law, it creates a **Union Oversight Framework** that reaches **directly** into the ICT supply chain: the most systemically important ICT providers are **designated as critical (CTPPs)** by the European Supervisory Authorities (ESAs — EBA, EIOPA, ESMA) and placed under a **Lead Overseer** with real supervisory powers over an entity that is not itself a financial entity (Arts. 31–44) [1]. This document goes deep on that pillar.

The Oversight Framework became concrete on **18 November 2025**, when the ESAs designated the **first 19 CTPPs** — hyperscale cloud, data-centre, infrastructure/network, managed-service and financial-sector-specific technology providers — using the prescriptive, two-step methodology in **Commission Delegated Regulation (EU) 2024/1502** (systemic impact; systemic importance of reliant financial entities; concentration; substitutability) [2][5]. Each CTPP is assigned a **Lead Overseer** (one of the three ESAs), supported by a **Joint Examination Team (JET)** drawn from the ESAs and competent authorities under a "**one team**" joint directorate, with an **Oversight Forum** setting consistent approaches (Arts. 32, 40) [6][7]. The Lead Overseer can **request information (Art. 37), run general investigations (Art. 38), conduct on-site inspections (Art. 39)** and issue **recommendations (Art. 35)**; it can compel cooperation through **periodic penalty payments of up to 1% of the CTPP's average daily worldwide turnover** [1].

The framework's enforcement lever is indirect but sharp. A CTPP that will not follow a recommendation must, under a "**follow-or-explain**" mechanism, give reasoned justification; persistent non-compliance can be **made public** and, as a last resort, competent authorities may require financial entities to **suspend or terminate** use of the provider (Art. 42) [1]. Oversight is funded by **annual oversight fees** proportionate to turnover, with a **fixed EUR 50,000 opt-in fee** for voluntary designation (Art. 43; **Commission Delegated Regulation (EU) 2024/1505**) [3][6]. Subcontracting of ICT services supporting critical or important functions is now governed by dedicated **RTS — Commission Delegated Regulation (EU) 2025/532** (in force 22 July 2025) [4].

# Key Takeaways

- **Two regimes in one pillar:** entity-level **ICT third-party risk management** (Arts. 28–30 — register, due diligence, contracts, exit) *plus* a **Union Oversight Framework** over designated **CTPPs** (Arts. 31–44) [1]. *(Legal obligation.)*
- **Oversight is live — verified:** on **18 November 2025** the ESAs designated the **first 19 CTPPs** (hyperscale cloud, data-centre, network/infrastructure, managed-service and financial-technology providers), now under direct ESA oversight; the list is re-assessed **annually** [5]. *(Confirmed, not asserted.)*
- **Designation is criteria-driven — verified:** **Commission Delegated Regulation (EU) 2024/1502** (Art. 31(6)) sets a **two-step** method — a quantitative screen (all sub-criteria must be met) then a qualitative assessment — around systemic impact, systemic importance of reliant entities, concentration and substitutability [2][5]. *(Legal obligation.)*
- **Register of information (Art. 28(3)):** every financial entity must maintain, keep current and report to its competent authority a register of **all** ICT contractual arrangements, flagging those supporting **critical or important functions** — the data feed for the criticality assessment [1][9]. *(Legal obligation.)*
- **Key contractual provisions (Art. 30):** ICT contracts must contain mandatory terms (service description and locations, access/audit and inspection rights, incident cooperation, security, sub-contracting conditions, termination rights and **exit strategies**) — heavier where the function is critical or important [1]. *(Legal obligation.)*
- **Lead Overseer + JET:** each CTPP has a **Lead Overseer** (EBA, EIOPA or ESMA) supported by a **Joint Examination Team** under a Lead Overseer coordinator; the ESAs act as a single joint directorate ("one team"), with an **Oversight Forum** for consistency (Arts. 32, 40) [1][6][7]. *(Legal obligation / oversight structure — verified.)*
- **Oversight powers (Arts. 35–39):** information requests, general investigations and on-site inspections, culminating in **recommendations**; cooperation can be compelled by **periodic penalty payments up to 1% of average daily worldwide turnover** (Art. 35) [1]. *(Legal obligation.)*
- **"Follow-or-explain" and the suspension lever (Art. 42):** a CTPP must comply with a recommendation or give reasoned justification; unresolved non-compliance can be **made public** and, as a last resort, competent authorities may direct financial entities to **suspend or terminate** the provider [1]. *(Legal obligation.)*
- **Oversight fees (Art. 43) — verified:** **Commission Delegated Regulation (EU) 2024/1505** sets **annual fees proportionate to turnover** to cover oversight costs, plus a **fixed EUR 50,000 opt-in fee** for voluntary designation [3][6]. *(Legal obligation.)*
- **Subcontracting RTS (Art. 30(5)) — verified:** **Commission Delegated Regulation (EU) 2025/532** governs subcontracting of ICT services supporting critical/important functions (due diligence, chain conditions, contract terms); **in force 22 July 2025** [4][8]. *(Legal obligation.)*
- **Concentration risk is the whole point:** the framework exists because a few providers underpin much of the EU financial system; entities must assess **ICT concentration risk** (Arts. 28(7), 29) and the Union oversees the systemic tail [1][5]. *(Legal obligation + regulatory rationale.)*

# Purpose

This document is a Tier 3 DORA sub-topic that **details `dora-foundations`** on the ICT third-party pillar and the Union Oversight Framework. It supports: (a) legal research (the precise obligations in Arts. 28–44 and the supporting delegated acts); (b) compliance planning for **financial entities** managing ICT third-party risk (register, contracts, concentration, exit) and for **ICT providers** that are, or may become, CTPPs; and (c) product/engineering and vendor-management triage. It assumes the reader has read `dora-foundations` for the five-pillar overview, and complements `dora-tlpt` (testing of third-party-run functions) and `cloud-shared-responsibility` (how the provider/customer control split maps onto these duties). The **18 November 2025 designation of 19 CTPPs** and the delegated-act status are **live-verified**.

# Scope

**In scope:** DORA's ICT third-party pillar (Arts. 28–44) — the general principles and **register of information** (Art. 28), **preliminary concentration-risk assessment** (Art. 29), **key contractual provisions** (Art. 30), the **criticality designation** of CTPPs and the **voluntary opt-in** (Art. 31), the **structure of the Oversight Framework** (Art. 32), the **Lead Overseer** and its **tasks and powers** (Arts. 33, 35–39), the **Joint Examination Teams** and coordination (Arts. 34, 40), **harmonisation RTS** (Art. 41), **follow-up by competent authorities** and the "follow-or-explain"/suspension mechanism (Art. 42), and **oversight fees** (Art. 43); the supporting delegated acts — **designation criteria (Reg (EU) 2024/1502)**, **oversight fees (Reg (EU) 2024/1505)** and **subcontracting (Reg (EU) 2025/532)**; **concentration risk**; the **18 November 2025 first designation** as the worked example; and a **CTPP-readiness checklist** and a **financial-entity third-party-management checklist**. The **first CTPP designation** and the **delegated-act status** are **live-verified**.

**Out of scope (covered elsewhere / in the backlog):** the DORA overview and the other four pillars → `dora-foundations`; the **TLPT** regime and testing of third-party-run functions → `dora-tlpt`; the **register-of-information ITS** and Art. 30 contractual duties at clause-drafting depth → `dora-third-party-contracts` (planned); **RTS/ITS-by-RTS** analysis (ICT risk-management framework, incident classification) → `dora-technical-standards` (planned); the **cloud shared-responsibility** control split and assurance vehicles → `cloud-shared-responsibility`; general supplier-security methodology → `cybersecurity-foundations`.

**Assumptions:** The reader understands DORA's scope of "financial entities" (Art. 2), the concept of "critical or important functions" (Art. 3(22)) and the role of the three ESAs. The Oversight Framework governs **designated CTPPs only**; every financial entity, designated or not, still owes the Arts. 28–30 third-party-risk duties. Where personal data is processed, the GDPR applies in parallel (see `gdpr-foundations`).

# Definitions

*Shared terms — digital operational resilience, CTPP — are in `GLOSSARY.md`. Terms specific to the Oversight Framework are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| ICT third-party service provider | An undertaking providing ICT services to financial entities (Art. 3(19)); reached directly by the third-party-risk and, if designated, the oversight regime. | [1] |
| Critical ICT third-party provider (CTPP) | An ICT third-party service provider designated as critical by the ESAs under Art. 31, thereby brought within the Union Oversight Framework and placed under a Lead Overseer. | [1][5] |
| Critical or important function | A function whose disruption would materially impair the financial entity's financial performance, or the soundness or continuity of its services, or its continued compliance with authorisation conditions and DORA obligations (Art. 3(22)); the anchor for the heavier third-party duties. | [1] |
| Register of information | The register each financial entity must maintain of all contractual arrangements for ICT services, distinguishing those supporting critical or important functions, and report to its competent authority (Art. 28(3)). | [1][9] |
| Lead Overseer | The ESA (EBA, EIOPA or ESMA) appointed for a given CTPP to conduct oversight, exercise the Art. 35–39 powers and issue recommendations (Arts. 31(1), 33). | [1][6] |
| Joint Examination Team (JET) | The team established for each CTPP — staff from the ESAs and relevant competent authorities (and, voluntarily, certain national authorities) — that assists the Lead Overseer in investigations and inspections, under a Lead Overseer coordinator (Art. 40). | [1][6][7] |
| Oversight Forum | A sub-committee of the ESAs' Joint Committee that carries out preparatory oversight work and promotes a consistent oversight approach across CTPPs (Art. 32). | [1][6] |
| Follow-or-explain | The Art. 42 mechanism whereby a CTPP that will not implement a Lead Overseer recommendation must give a reasoned explanation; unresolved non-compliance can lead to public notice and, ultimately, a competent-authority direction to suspend or terminate use of the provider. | [1] |
| Opt-in (voluntary designation) | The Art. 31 route by which an ICT third-party provider not otherwise designated may request to be treated as critical, subject to a fixed EUR 50,000 opt-in fee (Art. 43; Reg (EU) 2024/1505). | [1][3] |
| Oversight fees | The annual fees, proportionate to turnover, levied on each CTPP to fully cover the ESAs'/competent authorities' oversight expenditure (Art. 43; Reg (EU) 2024/1505). | [1][3] |

# Background

Before DORA, EU financial supervisors could act on a **financial entity's** outsourcing (through outsourcing guidelines and prudential rules) but had **no direct hold on the ICT provider** behind it. As the sector concentrated onto a small number of hyperscale cloud, core-banking, payments and market-infrastructure providers, this created a structural gap: a failure at one provider could cascade across many regulated firms at once, yet the provider sat outside the supervisory perimeter, and each firm's outsourcing contract addressed the risk only bilaterally and inconsistently [1][5]. Recital 80 of DORA frames the response — a **Union-level oversight** of the most systemically important ICT providers to address **ICT concentration risk** that individual-entity supervision cannot reach [1].

DORA's answer is deliberately two-layered. The **entity layer** (Arts. 28–30) hardens and standardises how each financial entity manages its ICT supply chain — a **register of information** feeding supervision, **due diligence** before contracting, mandatory **contractual provisions**, and **exit strategies**. The **Union layer** (Arts. 31–44) lifts the most critical providers into a bespoke oversight regime run jointly by the three ESAs. The mechanics were filled in by delegated acts adopted in **February 2024** — the **designation-criteria RTS (Reg (EU) 2024/1502)** and the **oversight-fees delegated act (Reg (EU) 2024/1505)** — followed by the **subcontracting RTS (Reg (EU) 2025/532, in force 22 July 2025)** and the ESAs' non-binding **DORA Oversight Guide (JC 2025 29, 15 July 2025)**; the European Commission catalogues these among DORA's delegated and implementing acts [2][3][4][7][10]. The ESAs first collected register data and ran the criticality assessment through 2025, culminating in the **first designation of 19 CTPPs on 18 November 2025** [5][12].

# Legal Framework

DORA **Chapter V** governs ICT third-party risk in two sections [1]:

- **Section I — managing ICT third-party risk (all financial entities):**
  - **Art. 28 — General principles.** Third-party risk is managed as an integral part of ICT risk, under a **strategy** (including a multi-vendor/concentration policy) approved by the management body; entities maintain a **register of information** on all ICT contractual arrangements, distinguish those supporting **critical or important functions**, report the register to competent authorities (at least yearly), conduct **pre-contract due diligence**, and assess **concentration risk** and exitability before entering arrangements [1].
  - **Art. 29 — Preliminary assessment of ICT concentration risk.** Before contracting for a critical or important function, the entity assesses whether it would enter into an arrangement for services that are **not easily substitutable**, or contract with a provider that is **hard to substitute**, including risks from **long subcontracting chains** [1].
  - **Art. 30 — Key contractual provisions.** ICT contracts must set out defined rights and obligations; arrangements **supporting critical or important functions** carry an **enhanced** set — full service description and data/processing **locations**, **access, inspection and audit** rights, **incident** assistance, security and business-continuity requirements, **sub-contracting conditions**, **termination** rights and **exit strategies** with transition support [1][4].

- **Section II — the Union Oversight Framework (designated CTPPs):**
  - **Art. 31 — Designation.** The ESAs, through the Joint Committee and on the Oversight Forum's recommendation, **designate CTPPs** against Art. 31(2) criteria (detailed by RTS); a provider may **opt in** voluntarily; certain intra-group and narrowly-scoped providers are treated distinctly. Each CTPP is assigned a **Lead Overseer** (EBA, EIOPA or ESMA) by reference to the sector it predominantly serves [1][2].
  - **Art. 32 — Structure.** The framework operates through the ESAs' **Joint Committee**, the **Oversight Forum**, and the **Lead Overseers**, acting jointly [1].
  - **Art. 33 — Tasks of the Lead Overseer.** Assess whether each CTPP has comprehensive, sound and effective rules to manage the ICT risk it may pose to financial entities; issue findings and recommendations [1].
  - **Arts. 34, 40 — Coordination and Joint Examination Teams.** Lead Overseers coordinate operationally; a **Joint Examination Team** is established **for each CTPP** to assist with investigations and inspections, under a **Lead Overseer coordinator** [1].
  - **Arts. 35–39 — Powers.** General powers including **recommendations** (Art. 35) and **periodic penalty payments** to compel cooperation; exercise of powers **outside the Union** (Art. 36); **requests for information** (Art. 37); **general investigations** (Art. 38); **on-site inspections** (Art. 39) [1].
  - **Art. 41 — Harmonisation.** RTS specify the information CTPPs must provide and the conduct of oversight activities [1].
  - **Art. 42 — Follow-up by competent authorities.** The "**follow-or-explain**" mechanism and, as a last resort, the power to require financial entities to **suspend or terminate** use of a non-compliant CTPP [1].
  - **Art. 43 — Oversight fees.** Fees charged to CTPPs to cover oversight costs; detailed by delegated act [1][3].

**Interpretation (distinct from the statutory text):** The oversight regime is **not** direct enforcement against the provider in the way a competent authority enforces against a financial entity — the Lead Overseer's binding lever is **recommendations plus periodic penalty payments to compel cooperation**, and the substantive sanction runs **through the financial entities** (they may be told to suspend or terminate). The design is therefore **incentive-based**: a CTPP that ignores recommendations risks losing its regulated customer base [1][5].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 28 | General principles for sound **ICT third-party risk** management; strategy; **register of information** (Art. 28(3)); pre-contract due diligence; **concentration-risk** assessment. | [1] |
| Art. 29 | **Preliminary assessment of ICT concentration risk** before contracting for critical/important functions; substitutability and subcontracting chains. | [1] |
| Art. 30 | **Key contractual provisions**, with an enhanced set for arrangements supporting **critical or important functions** (access/audit, sub-contracting, termination, exit). | [1][4] |
| Art. 31 | **Designation of CTPPs**; criteria; **voluntary opt-in**; assignment of the **Lead Overseer**. | [1][2][5] |
| Art. 32 | **Structure** of the Oversight Framework — Joint Committee, **Oversight Forum**, Lead Overseers. | [1][6] |
| Art. 33 | **Tasks of the Lead Overseer** — assess the CTPP's ICT risk-management adequacy; issue recommendations. | [1] |
| Art. 34 | **Operational coordination** between Lead Overseers. | [1] |
| Art. 35 | **Powers of the Lead Overseer** — recommendations; **periodic penalty payments** (up to 1% of average daily worldwide turnover) to compel cooperation. | [1] |
| Art. 36 | Exercise of powers **outside the Union**. | [1] |
| Art. 37 | **Request for information** from the CTPP. | [1] |
| Art. 38 | **General investigations** of the CTPP. | [1] |
| Art. 39 | **On-site inspections** of the CTPP's premises. | [1] |
| Art. 40 | **Ongoing oversight**; the **Joint Examination Team** for each CTPP under a Lead Overseer coordinator. | [1][6][7] |
| Art. 41 | **Harmonisation** — RTS on the information provided and the conduct of oversight. | [1] |
| Art. 42 | **Follow-up by competent authorities** — "**follow-or-explain**"; last-resort **suspension/termination** direction to financial entities. | [1] |
| Art. 43 | **Oversight fees** — proportionate to turnover; EUR 50,000 opt-in fee (delegated act). | [1][3] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 63 area | Rationale for standardised **contractual** arrangements and the register of information for ICT third-party risk. | [1] |
| Recital 80 area | Rationale for a **Union Oversight Framework** to address **ICT concentration risk** at critical third-party providers that entity-level supervision cannot reach. | [1] |
| Recital 82 area | The oversight lever operates via **recommendations** and, ultimately, financial entities' ability/duty to act on non-compliance (substitutability and exit). | [1] |

## Relevant Case Law

**Not Applicable.** The Oversight Framework only became operational with the first CTPP designations on **18 November 2025**, so there is no CJEU or domestic case law interpreting Arts. 31–44, the designation-criteria RTS (Reg (EU) 2024/1502), or the fees/subcontracting delegated acts. The most likely future litigation — a challenge to a **designation decision** (which is an ESA act potentially reviewable under Art. 263 TFEU) or to an oversight/penalty measure — would be **emerging** and is tracked in the backlog rather than asserted here [1][2][5].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **The first CTPPs are designated — verified.** On **18 November 2025** the ESAs (EBA, EIOPA, ESMA) designated the **first 19 CTPPs**, spanning hyperscale cloud, data-centre, infrastructure/network, managed-service and financial-sector-specific technology providers, and stated they will **keep engaging with CTPPs in upcoming examination activities**; the list is **re-assessed and re-published annually** [5]. *(Regulatory interpretation — verified; confirm the live list.)*
- **Designation follows a prescriptive two-step method.** **Commission Delegated Regulation (EU) 2024/1502** (Art. 31(6)) specifies a **quantitative** screen — a provider must meet **all** quantitative sub-criteria — followed by a **qualitative** assessment, built around **systemic impact**, the **systemic importance** of reliant financial entities, **concentration** of reliance across sectors, and **substitutability**; designation is made through the Joint Committee on the Oversight Forum's recommendation [2][5]. *(Regulatory interpretation — verified.)*
- **Oversight is run as "one team".** Per the ESAs, the three authorities operate a **single joint directorate** overseeing CTPPs "as one team"; each CTPP has a **Lead Overseer** and a dedicated **Joint Examination Team** under a **Lead Overseer coordinator**, with the **Oversight Forum** (a Joint Committee sub-committee) ensuring consistent approaches; ESMA presents the same structure for the capital-markets CTPPs it leads [6][7][11]. *(Regulatory interpretation — verified.)*
- **The oversight process and tools are published.** The ESAs' **DORA Oversight Guide (JC 2025 29, 15 July 2025)** gives a high-level, **non-binding** account of the governance structure, oversight processes, founding principles and tools (information requests, investigations, inspections, recommendations) used by the JETs [7]. *(Regulatory interpretation — non-binding guidance.)*
- **Fees are set and turnover-proportionate.** **Commission Delegated Regulation (EU) 2024/1505** determines the **annual oversight fees** — set to **fully cover** the ESAs'/competent authorities' oversight expenditure and **proportionate to each provider's turnover** — and fixes the **voluntary opt-in fee at EUR 50,000** [3][6]. *(Regulatory interpretation — verified.)*
- **Subcontracting is now specified.** **Commission Delegated Regulation (EU) 2025/532** (Art. 30(5) RTS), **in force 22 July 2025**, sets the elements a financial entity must determine and assess when **subcontracting ICT services supporting critical or important functions** — proportionality/group application, **due diligence and risk assessment**, and **conditions/contract terms** down the chain. It was adopted only after the Commission's initial rejection of a broader draft was narrowed to the Art. 30(5) mandate [4][8]. *(Regulatory interpretation — verified.)*
- **The enforcement chain is indirect.** The Lead Overseer's binding levers are **recommendations** backed by **periodic penalty payments** to compel cooperation; the substantive sanction is **mediated through competent authorities and financial entities** under the "follow-or-explain" and **suspension/termination** mechanism (Art. 42) [1][7]. *(Regulatory interpretation.)*

# Technical Considerations

- **Build the register of information as a live data asset, not an annual scramble.** Art. 28(3) requires a structured register of **all** ICT contractual arrangements, flagging those supporting **critical or important functions**, reported to the competent authority on the ESAs' template; because the register **feeds the criticality assessment**, its completeness and accuracy have systemic consequences and should be sourced from procurement/CMDB systems, not hand-maintained spreadsheets [1][9]. *(Legal obligation.)*
- **Map critical or important functions to providers, subcontractors and substitutability.** Art. 29's concentration assessment needs a current graph linking each critical/important function (Art. 3(22)) to its ICT provider(s), the **subcontracting chain**, and the availability of alternatives; this is the same dependency map used for TLPT scoping (see `dora-tlpt`) and cloud responsibility allocation (see `cloud-shared-responsibility`) [1]. *(Best practice grounded in the Art. 29 obligation.)*
- **Engineer for exit and substitutability.** Art. 30's exit-strategy requirement is only real if data and workloads are **portable**: standard export formats, documented dependencies, and a **tested** migration/transition plan so a suspension/termination direction (Art. 42) is executable without prohibitive lock-in [1]. *(Legal obligation + best practice.)*
- **CTPPs: stand up an oversight interface.** A designated CTPP must be able to answer **Art. 37 information requests**, host **Art. 38/39 investigations and inspections**, nominate an EU coordination point, and track **recommendations** to closure — treat it as a supervisory relationship with the Lead Overseer/JET, resourced accordingly [1][6][7]. *(Regulatory — CTPPs only.)*
- **Instrument subcontracting controls.** Under Reg (EU) 2025/532, due diligence, monitoring and contractual conditions must extend **down the subcontracting chain** for critical/important functions; build supplier-onboarding and continuous-monitoring tooling that captures fourth-party and onward dependencies [1][4]. *(Legal obligation.)*

# Hosting Considerations

- **Hyperscale and data-centre providers are the paradigm CTPPs.** The first 19 designations centred on **hyperscale cloud, data-centre and network/infrastructure providers**; a hosting provider serving financial entities at scale should assume it may be **in or near scope** and prepare for the Lead Overseer/JET relationship, information requests, inspections and oversight fees [5][6]. *(Regulatory — assess role.)*
- **Contractual obligations flow to the host.** Financial-entity customers must obtain the Art. 30 enhanced provisions (access/audit and **inspection** rights, incident cooperation, security, **sub-contracting** controls, **exit** assistance) for critical/important functions; hosts should expect, and be able to support, these terms and the Reg (EU) 2025/532 subcontracting conditions [1][4]. *(Legal obligation for the entity; commercial reality for the host.)*
- **Concentration and substitutability shape architecture.** Because Art. 29 turns on substitutability, hosting architectures that support **portability, multi-region and multi-provider** options directly improve customers' DORA position — and reduce the systemic concentration the Oversight Framework targets [1][5]. *(Best practice.)*
- **The shared-responsibility split still applies.** Oversight of a CTPP does not move the provider/customer control boundary; the financial entity remains **accountable** for its own ICT risk and must still allocate controls (see `cloud-shared-responsibility`) [1]. *(Best practice / cross-reference.)*

# Game Hosting Considerations

**Not Applicable — with the same narrow caveat as `dora-foundations` and `dora-tlpt`.** The Oversight Framework governs **designated CTPPs** and the third-party duties bind **financial entities**; ordinary game hosting and studios are outside DORA entirely. It becomes relevant only where a games business is itself a **financial entity** (e.g. a scaled in-game **crypto-asset service provider** under MiCA, or an embedded payments/e-money arm) that must manage its ICT third-party risk under Arts. 28–30, or where a studio or hosting business supplies ICT services underpinning a critical or important function of such an entity — in which case Art. 30 contractual and subcontracting terms, and (only at systemic scale) the remote prospect of CTPP designation, apply on their own terms [1][4]. Standard player-facing game hosting is out of scope.

# AI Considerations

- **AI services bought from third parties are in the register and the contracts.** Where a financial entity procures AI/ML services (fraud detection, credit decisioning, model-as-a-service) from an ICT third-party provider, those arrangements sit in the **register of information** and, if they support critical or important functions, carry the full **Art. 30** provisions and **Reg (EU) 2025/532** subcontracting controls [1][4]. *(Legal obligation.)*
- **An AI provider can be a CTPP.** A provider whose AI/compute services become systemically important to reliant financial entities could meet the Art. 31/Reg (EU) 2024/1502 criteria and be **designated**, bringing its relevant services under Lead Overseer oversight [1][2][5]. *(Regulatory — assess role.)*
- **AI Act and GDPR run in parallel.** High-risk AI in financial services (e.g. credit scoring, insurance pricing) carries **AI Act** conformity duties (see `ai-act-foundations`), and personal-data processing remains governed by the **GDPR**; DORA's third-party and oversight duties apply **in addition**, not instead [1]. *(Cross-reference; parallel application.)*
- **Concentration risk has an AI dimension.** Reliance on a small number of AI/compute suppliers replicates the concentration problem the Oversight Framework addresses; assess substitutability of AI dependencies under Art. 29 just as for cloud [1]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

**For financial entities (third-party risk):**

1. **Adopt and maintain an ICT third-party strategy** approved by the management body, including a **multi-vendor/concentration** policy (Art. 28). *(OBLIGATION.)* [1]
2. **Maintain the register of information** for all ICT arrangements, flag those supporting **critical or important functions**, and report it on the ESAs' template (Art. 28(3)). *(OBLIGATION.)* [1][9]
3. **Run pre-contract due diligence and the Art. 29 concentration assessment** — substitutability and subcontracting-chain risk — before contracting for critical/important functions. *(OBLIGATION.)* [1]
4. **Embed the Art. 30 key contractual provisions** (enhanced set for critical/important functions: access/audit/inspection, incident cooperation, security, sub-contracting conditions, termination, **exit**). *(OBLIGATION.)* [1][4]
5. **Apply the subcontracting RTS** (Reg (EU) 2025/532) down the chain — due diligence, monitoring, contractual conditions. *(OBLIGATION.)* [4]
6. **Build and test exit/substitution strategies** so a suspension/termination direction (Art. 42) is executable. *(OBLIGATION + BEST PRACTICE.)* [1]
7. **Track CTPP designations** and factor the oversight regime — and possible suspension/termination — into continuity planning; monitor the **annual** list. *(EDITORIAL RECOMMENDATION.)* [5]

**For ICT providers (CTPP readiness):**

1. **Assess likely criticality** against the Reg (EU) 2024/1502 criteria and decide on **opt-in** where strategically useful (EUR 50,000 fee). *(EDITORIAL RECOMMENDATION.)* [2][3]
2. **Stand up the oversight interface** — EU coordination point, capacity to handle Art. 37 requests, Art. 38/39 investigations and inspections, and a recommendation-tracking process. *(OBLIGATION once designated.)* [1][6][7]
3. **Budget for oversight fees** (turnover-proportionate) and align internal ICT risk management to what the Lead Overseer/JET will assess under Art. 33. *(OBLIGATION once designated.)* [1][3]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Incomplete/inaccurate **register of information** → mis-scoped supervision and criticality assessment | Medium | High | Art. 28(3) [1][9] | System-sourced register; annual reconciliation; template validation | Low |
| R2 | ICT contracts missing **Art. 30** enhanced provisions (audit, sub-contracting, exit) | Medium | High | Art. 30 [1][4] | Contract remediation programme; standard DORA clause set | Low |
| R3 | **Concentration** on a provider with no viable substitute or tested exit | Medium | Very High | Arts. 28(7), 29, 42 [1][5] | Substitutability analysis; multi-provider/portability; rehearsed exit | Medium |
| R4 | Subcontracting-chain risk unmanaged (fourth-party exposure) | Medium | High | Art. 30(5); Reg (EU) 2025/532 [4] | Chain due diligence and monitoring; contractual conditions | Medium |
| R5 | **CTPP** unprepared for oversight (requests, inspections, recommendations) | Medium | High | Arts. 35–40 [1][6][7] | Oversight interface; EU coordination point; recommendation tracking | Low |
| R6 | Ignoring a Lead Overseer **recommendation** → public notice, penalty payments, customer suspension | Low | Very High | Arts. 35, 42 [1] | Follow-or-explain governance; timely remediation | Low |
| R7 | Assuming non-designated providers are "safe" and skipping Arts. 28–30 duties | Medium | Medium | Arts. 28–30 [1] | Apply third-party duties regardless of designation status | Low |
| R8 | Treating the CTPP list as static; missing the **annual** re-assessment | Medium | Medium | Art. 31; designation cycle [5] | Annual watch-list; re-scan key providers | Low |

# Implementation Roadmap

- **Phase 0 — Scope & inventory:** Confirm role (financial entity and/or ICT provider); build/complete the **register of information**; map critical/important functions to providers and subcontractors. *Effort:* Medium.
- **Phase 1 — Concentration & substitutability:** Run the Art. 29 assessment; identify hard-to-substitute providers and likely CTPPs; design portability/exit. *Effort:* Medium.
- **Phase 2 — Contracts & subcontracting:** Remediate ICT contracts to Art. 30; apply the Reg (EU) 2025/532 subcontracting conditions down the chain. *Effort:* High.
- **Phase 3 — Exit assurance:** Build and **test** exit/substitution strategies for critical/important functions. *Effort:* High.
- **Phase 4 (CTPPs) — Oversight readiness:** Stand up the EU coordination point and oversight interface; align ICT risk management to Art. 33; budget fees. *Effort:* High.
- **Phase 5 — Monitor & adapt:** Track the **annual** CTPP list, new RTS/guidance and recommendations; refresh register, contracts and exit tests. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Third-party ICT risk managed ad hoc; register incomplete; concentration unassessed. | No register; contracts un-remediated; CTPP exposure unknown. |
| 2 | Managed | Register maintained; Art. 30 clauses being inserted; concentration noted. | Register reported; contract remediation started. |
| 3 | Defined | Full register; Art. 29 concentration assessment; subcontracting controls; exit strategies drafted. | Substitutability analysis; Reg (EU) 2025/532 terms; exit plans. |
| 4 | Quantitatively Managed | Exit strategies **tested**; CTPP exposure mapped; metrics on concentration and remediation. | Exit drills; provider-criticality dashboard; KPIs. |
| 5 | Optimising | Portability-by-design; continuous concentration monitoring; (CTPPs) mature oversight relationship with the Lead Overseer/JET. | Multi-provider architecture; annual re-scan; clean oversight track record. |

# Audit Questions

1. Is a complete, current **register of information** maintained and reported, correctly flagging critical/important functions? *(Art. 28(3) [1][9].)*
2. How is **ICT concentration risk** assessed before contracting for critical/important functions, including subcontracting chains and substitutability? *(Art. 29 [1].)*
3. Do ICT contracts contain the **Art. 30** provisions, with the enhanced set (audit/inspection, sub-contracting, exit) for critical/important functions? *(Art. 30 [1][4].)*
4. How are the **subcontracting RTS** (Reg (EU) 2025/532) requirements applied down the chain? *(Art. 30(5) [4].)*
5. Are **exit/substitution** strategies documented and **tested** so a suspension/termination direction is executable? *(Arts. 28–30, 42 [1].)*
6. Which key providers are (or may become) **CTPPs**, and how is the oversight regime — including suspension/termination — reflected in continuity planning? *(Arts. 31–42 [1][5].)*
7. *(CTPPs)* How does the provider handle **information requests, investigations, inspections and recommendations**, and track them to closure? *(Arts. 35–40, 42 [1][6][7].)*
8. *(CTPPs)* Are **oversight fees** budgeted and internal ICT risk management aligned to the Lead Overseer's Art. 33 assessment? *(Arts. 33, 43 [1][3].)*

# Implementation Checklist

**Financial-entity ICT third-party-management checklist:**

- [ ] ICT third-party strategy (incl. concentration/multi-vendor policy) approved by the management body (Art. 28).
- [ ] Register of information complete, current and reported on the ESA template; critical/important functions flagged (Art. 28(3)).
- [ ] Pre-contract due diligence and Art. 29 concentration/substitutability assessment performed for critical/important functions.
- [ ] ICT contracts contain the Art. 30 provisions; enhanced set (audit/inspection, sub-contracting, termination, exit) for critical/important functions.
- [ ] Subcontracting RTS (Reg (EU) 2025/532) requirements applied and monitored down the chain.
- [ ] Exit/substitution strategies documented and **tested**; portability engineered.
- [ ] CTPP exposure assessed; oversight/suspension scenarios reflected in continuity planning; annual CTPP list tracked.

**CTPP-readiness checklist (ICT providers):**

- [ ] Criticality self-assessment against Reg (EU) 2024/1502 criteria; opt-in decision considered (EUR 50,000 fee).
- [ ] EU legal entity / coordination point nominated for the Lead Overseer relationship.
- [ ] Capability to handle Art. 37 information requests and host Art. 38/39 investigations and inspections.
- [ ] Recommendation-tracking (follow-or-explain) governance in place (Arts. 35, 42).
- [ ] Oversight fees budgeted (turnover-proportionate); internal ICT risk management aligned to the Art. 33 assessment.
- [ ] Subcontracting and concentration transparency maintained for reliant financial entities.

# References

*All links verified live (HTTP 2xx/3xx) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2022/2554 (Digital Operational Resilience Act — DORA)** — Chapter V, Articles 28–44 (ICT third-party risk management; register of information; key contractual provisions; designation of CTPPs; the Union Oversight Framework — Lead Overseer, Joint Examination Teams, powers, follow-up and fees). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj
- [2] **Commission Delegated Regulation (EU) 2024/1502 of 22 February 2024** — RTS specifying the criteria for the **designation** of ICT third-party service providers as critical (Art. 31(6)); two-step quantitative/qualitative methodology. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_del/2024/1502/oj
- [3] **Commission Delegated Regulation (EU) 2024/1505 of 22 February 2024** — determining the amount of the **oversight fees** to be charged to CTPPs and the way in which they are to be paid (Art. 43); turnover-proportionate fees; EUR 50,000 opt-in fee. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_del/2024/1505/oj
- [4] **Commission Delegated Regulation (EU) 2025/532** — RTS specifying the elements a financial entity must determine and assess when **subcontracting** ICT services supporting critical or important functions (Art. 30(5)); adopted 24 March 2025, in force 22 July 2025. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_del/2025/532/oj

## Regulatory Guidance

- [5] **European Supervisory Authorities designate critical ICT third-party providers under DORA** (first list — **19 CTPPs** — 18 November 2025; four-criteria methodology; annual re-assessment). EIOPA/EBA/ESMA. https://www.eiopa.europa.eu/european-supervisory-authorities-designate-critical-ict-third-party-providers-under-digital-2025-11-18_en
- [6] **DORA oversight** (Lead Overseer; Joint Examination Teams; Oversight Forum; "one team" joint directorate; EUR 50,000 opt-in fee; CTPP list published on ESA websites). EIOPA. https://www.eiopa.europa.eu/digital-operational-resilience-act-dora/dora-oversight_en
- [7] **ESAs publish guide on DORA Oversight activities — DORA Oversight Guide (JC 2025 29, 15 July 2025)** (governance structure, oversight processes, JETs, tools; non-binding). EIOPA (for the ESAs). https://www.eiopa.europa.eu/publications/dora-oversight-guide_en
- [8] **Joint Regulatory Technical Standards on subcontracting ICT services supporting critical or important functions** (Art. 30(5); background to Reg (EU) 2025/532). European Banking Authority (for the ESAs). https://www.eba.europa.eu/activities/single-rulebook/regulatory-activities/operational-resilience/joint-regulatory-technical-subcontracting
- [9] **ESAs publish first set of rules under DORA for ICT and third-party risk management and incident classification** (incl. the ICT third-party policy RTS and the register-of-information ITS). European Banking Authority. https://www.eba.europa.eu/publications-and-media/press-releases/esas-publish-first-set-rules-under-dora-ict-and-third-party
- [10] **Digital Operational Resilience Regulation (DORA) — implementing and delegated acts** (catalogue of DORA delegated/implementing acts). European Commission, DG FISMA. https://finance.ec.europa.eu/regulation-and-supervision/financial-services-legislation/implementing-and-delegated-acts/digital-operational-resilience-regulation_en
- [11] **DORA Oversight** (overview of the Oversight Framework and CTPP oversight). ESMA. https://www.esma.europa.eu/dora-oversight
- [12] **The ESAs announce timeline to collect information for the designation of critical ICT third-party service providers under DORA** (15 November 2024; register-data collection feeding the criticality assessment). EIOPA/EBA/ESMA. https://www.eiopa.europa.eu/esas-announce-timeline-collect-information-designation-critical-ict-third-party-service-providers-2024-11-15_en

## Standards

**Not Applicable as binding sources.** The ICT third-party pillar and the Oversight Framework are enforced through the Regulation and its RTS/ITS and delegated acts, not through voluntary technical standards. Supplier-relationship security standards commonly used to implement third-party controls (e.g. ISO/IEC 27036 on supplier relationships, and ISO/IEC 27001/27002 as the control baseline) are cross-referenced in `cloud-shared-responsibility` and `cybersecurity-foundations` rather than cited as authority here.

## Academic Sources

Not Applicable — this sub-topic relies on primary legislation, the supporting delegated acts, and ESA/Commission sources. Academic analysis of ICT concentration risk and the direct-oversight model may be cited in future depth documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- DORA: EU regulators announce list of critical ICT third-party providers (categories of the 19 designated CTPPs; annual re-assessment). Morgan Lewis — Tech & Sourcing blog. https://www.morganlewis.com/blogs/sourcingatmorganlewis/2025/11/dora-eu-regulators-announce-list-of-critical-ict-third-party-providers
- Digital Operational Resilience Act — Wikipedia (overview and implementation chronology; non-authoritative). https://en.wikipedia.org/wiki/Digital_Operational_Resilience_Act

# Related Documents

- `dora-foundations` — DORA overview and the five pillars; this document **details** its Arts. 28–44 third-party and oversight material (parent).
- `dora-tlpt` — threat-led penetration testing, including testing of functions run by ICT third-party providers (sibling).
- `cloud-shared-responsibility` — the provider/customer control split and assurance vehicles that operationalise the Art. 30 duties (sibling).
- `dora-third-party-contracts` — register of information and Art. 30 contractual duties at clause-drafting depth (planned).
- `dora-technical-standards` — RTS/ITS-by-RTS analysis across the DORA rulebook (planned).
- `nis2-foundations` — general EU cybersecurity baseline; DORA is lex specialis for financial entities.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Reg (EU) 2022/2554 Arts. 28–44; Commission Delegated Regulations (EU) 2024/1502, 2024/1505, 2025/532), the EIOPA/EBA/ESMA designation press release, the EIOPA DORA-oversight page, the ESAs' DORA Oversight Guide (JC 2025 29), the EBA subcontracting-RTS and first-rules pages, the EC DG FISMA delegated-acts catalogue, ESMA DORA-oversight, and the ESAs' 2024 designation-timeline notice. **Live-verified:** the **first CTPP designation of 18 November 2025 (19 providers)**; the two-step designation criteria (Reg (EU) 2024/1502); oversight fees and the EUR 50,000 opt-in fee (Reg (EU) 2024/1505); the subcontracting RTS (Reg (EU) 2025/532, in force 22 July 2025); and the Lead Overseer / Joint Examination Team / Oversight Forum structure. All external links returned HTTP 2xx/3xx. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster B); full-repo validator/link/lint suite green; frozen in release 0.16.0. | Orchestrator (QA-verified) |

</content>
</invoke>
