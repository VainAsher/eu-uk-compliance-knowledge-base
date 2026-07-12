---
id: data-act-b2g
title: "EU Data Act: Business-to-Government Data Sharing (Chapter V)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: Data Act
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-12
updated: 2026-07-12
review_due: 2027-07-12
confidence: High
supersedes: Not Applicable
related: [data-act-foundations, data-act-cloud-switching, gdpr-foundations, nis2-foundations]
tags: [data-act, b2g, exceptional-need, public-emergency, public-sector-body, non-personal-data, compensation, gdpr-interplay, open-data]
legal_basis: Regulation (EU) 2023/2854, Chapter V (Arts. 14–22)
sources_verified: 2026-07-12
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | data-act-b2g |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.18.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-12 |
| Last Updated | 2026-07-12 |
| Review Due | 2027-07-12 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a sub-topic deep dive that details the business-to-government (B2G) material summarised in `data-act-foundations`. The Data Act's Chapter V obligations **apply from 12 September 2025** (Art. 50) [1]. Always confirm the current in-force dates and any delegated/implementing acts before relying on them.

# Executive Summary

**Chapter V (Articles 14–22) of the EU Data Act (Regulation (EU) 2023/2854)** creates a **business-to-government (B2G)** data-access regime: where a public sector body, the European Commission, the European Central Bank (ECB) or a Union body demonstrates an **exceptional need**, a data holder must **make the requested data available** (Art. 14) [1]. It is a narrow, tightly conditioned mechanism — not a general information-gathering power and expressly **not** a route around data-protection law [1][2].

"Exceptional need" exists only in two situations (Art. 15): (a) responding to a **public emergency** (e.g. a public-health crisis, natural or human-induced major disaster, or a major cybersecurity incident); or (b) a **non-emergency** case, **limited to non-personal data**, where a body acting under law cannot fulfil a specific public-interest task because it lacks specific data and has exhausted all other means of obtaining it [1]. The regime carries hard limits: it **does not apply to the prevention, investigation, detection or prosecution of criminal or administrative offences, the execution of criminal penalties, or customs/taxation administration** (Art. 16); the non-emergency case **does not apply to micro and small enterprises** at all (Art. 15(2)); requests must be **specific, proportionate and justified** (Art. 17); and use is **strictly purpose-limited**, with the **GDPR continuing to govern** any personal data (Arts. 19, 1(5)) [1][2].

Compensation is asymmetric: data provided to respond to a **public emergency is free of charge** (micro/small enterprises excepted), whereas non-emergency provision attracts **reasonable compensation** covering technical and organisational costs plus a reasonable margin (Art. 20) [1]. Obtained data may be shared onward with **research organisations or statistical bodies** for compatible purposes (Art. 21), and **cross-border requests** are mediated through competent authorities and, where personal data is involved, data-protection supervisory authorities (Art. 22) [1]. The single most important operational fact is that **Chapter V is already in force (from 12 September 2025)**: data holders should have a documented request-handling process ready now [1][4].

# Key Takeaways

- **Chapter V (Arts. 14–22)** obliges a **data holder** to make data available to a **public sector body, the Commission, the ECB or a Union body** that demonstrates an **exceptional need**, and applies from **12 September 2025** (Art. 50) [1][4]. *(Legal obligation — in force.)*
- **Exceptional need is exhaustively defined (Art. 15):** only (a) responding to a **public emergency**, or (b) a **non-emergency** public-interest task where the body cannot obtain the data by other means — and case (b) is **limited to non-personal data** [1]. *(Legal obligation.)*
- **Micro and small enterprises are exempt from the non-emergency case (Art. 15(2))** — they can be compelled only in a **public emergency**, and even then are entitled to compensation (Art. 20) [1]. *(Scope limit.)*
- **Chapter V cannot be used for law enforcement or penalties (Art. 16):** it does **not** apply to the prevention, investigation, detection or prosecution of criminal/administrative offences, execution of criminal penalties, or customs/taxation — those remain under their own legal regimes [1]. *(Scope limit.)*
- **Requests must be specific, proportionate and justified (Art. 17):** specify the data and metadata, state the exceptional need and purpose, be the least disruptive option, seek **non-personal data first** and personal data only in **pseudonymised** form where unavoidable, and be **made public** via the data coordinator [1]. *(Legal obligation.)*
- **A data holder may decline or seek modification (Art. 18)** where it lacks control of the data, an identical request has already been met, or the request fails Art. 17 — responding within **5 working days** (public emergency) or **30 working days** (other cases); disputes escalate to the competent authority [1]. *(Legal obligation.)*
- **Use is purpose-limited and the GDPR still governs (Arts. 19, 1(5)):** requested data may be used only for the stated purpose, must be deleted when no longer needed, and any personal data must be **minimised, pseudonymised/anonymised** and processed on a lawful basis — Chapter V is **not** a new GDPR legal basis [1][2]. *(Legal obligation.)*
- **Compensation is asymmetric (Art. 20):** **free** for public-emergency response (micro/small excepted); otherwise **reasonable compensation** = technical/organisational costs **plus a reasonable margin** (margin excluded for micro/small) [1]. *(Legal obligation.)*
- **Onward sharing (Art. 21) and cross-border cooperation (Art. 22):** obtained data may be shared with **research organisations/statistical bodies** for compatible purposes, and cross-border requests run through competent authorities and, for personal data, **DPAs** [1]. *(Legal obligation.)*
- **B2G differs from FoI and open-data regimes:** Chapter V is a **demand-driven, exceptional** business-to-government transfer, distinct from freedom-of-information access to *public-sector* documents and from the **Open Data Directive** / Data Governance Act rules on **re-using public-sector data** [1][3][4]. *(Distinction — see Background.)*

# Purpose

This document is the Tier 2 sub-topic deep dive on the Data Act's B2G (exceptional-need) regime. It supports: (a) **legal mapping** of Chapter V onto an organisation that holds data (the data holder) and onto requesting public bodies; (b) **request-handling process design** — how to receive, assess, comply with, or lawfully object to a request; (c) the **GDPR interplay** — ensuring that responding to a B2G request never becomes an unlawful disclosure of personal data; and (d) **compensation and onward-sharing** governance. It details the B2G material introduced in `data-act-foundations` and dovetails with `gdpr-foundations` (personal-data safeguards) and `nis2-foundations` (major-cybersecurity-incident emergencies).

# Scope

**In scope:** Chapter V (Arts. 14–22) of Regulation (EU) 2023/2854 — the obligation to make data available (Art. 14); the definition and two limbs of **exceptional need** (Art. 15) and the micro/small-enterprise carve-out (Art. 15(2)); the relationship-with-other-obligations exclusions incl. law enforcement, penalties and customs/tax (Art. 16); request requirements and transparency (Art. 17); compliance, timeframes and objection grounds (Art. 18); use limitations and data-protection duties of requesting bodies (Art. 19); compensation (Art. 20); onward sharing with research/statistical bodies (Art. 21); mutual assistance and cross-border cooperation (Art. 22); the interplay with the GDPR (Art. 1(5)); and the distinction from freedom-of-information and open-data / public-sector-information re-use regimes.

**Out of scope (covered elsewhere):**

- **IoT / connected-product** data sharing (Chapter II) → `data-act-iot-sharing` (planned); `data-act-foundations`.
- **B2B FRAND** data-sharing and **unfair contractual terms** (Chapters III–IV) → `data-act-foundations`.
- **Cloud/data-processing-service switching** (Chapter VI) → `data-act-cloud-switching`.
- **International-transfer** mechanics for personal data (GDPR Chapter V) → `gdpr-transfers`; the Data Act **Art. 32** non-personal-data safeguard is summarised in `data-act-foundations`.
- **Re-use of public-sector data** under the **Open Data Directive** and the **Data Governance Act** (the mirror-image, government-to-business flow) — noted here only for contrast.

**Assumptions:** The reader has read `data-act-foundations` and `gdpr-foundations`. Where a B2G request touches **personal** data, the GDPR (and, where relevant, ePrivacy and Regulation (EU) 2018/1725 for Union institutions) applies in parallel and **prevails on conflict** (Data Act Art. 1(5)) [1][2].

# Definitions

*Shared terms are in `GLOSSARY.md` (see "data holder"). B2G-specific terms of art are defined here from the Regulation's Article 2 and Chapter V.*

| Term | Definition | Source |
|------|------------|--------|
| Exceptional need | The tightly bounded trigger for Chapter V: a need to use data that is limited in time and scope, existing only to respond to a public emergency (Art. 15(1)(a)) or, for non-personal data, where a body cannot otherwise fulfil a specific public-interest task explicitly provided for by law (Art. 15(1)(b)). | [1] |
| Public emergency | An exceptional situation, limited in time, negatively affecting the population (or a part of it) — e.g. a public-health emergency, a natural or human-induced major disaster, or a major cybersecurity incident (Art. 2, and Art. 15(1)(a)). | [1] |
| Public sector body | A State, regional or local authority, or a body governed by public law, or an association of such authorities/bodies, of a Member State (Art. 2), to whom (with the Commission, ECB and Union bodies) the Chapter V right is available. | [1] |
| Data holder | A legal or natural person that has the right or obligation to use and make available data, including product/related-service data it has the ability to make available (Art. 2(13)); the party bearing the Chapter V obligation (public sector bodies themselves are excluded as data holders here). | [1] |
| Business-to-government (B2G) data sharing | The making available of privately held data to public bodies, the Commission, the ECB or Union bodies on the basis of exceptional need under Chapter V — distinct from public-sector-information re-use and from freedom-of-information access. | [1] |

# Background

The Data Act is the second pillar (with the 2022 **Data Governance Act**, Reg (EU) 2022/868) of the European Strategy for Data. Where the Data Governance Act and the **Open Data Directive** (Directive (EU) 2019/1024) govern the **re-use of data held by the public sector** — a government-to-business flow — Chapter V of the Data Act addresses the **reverse**: exceptional situations in which the public sector legitimately needs data held by **private** businesses and cannot obtain it by ordinary means [1][3][4]. The COVID-19 pandemic crystallised the gap: authorities needed mobility, health and logistics data at speed, but had no clear, proportionate, rights-respecting mechanism to obtain it from private holders [4].

Chapter V answers that gap with a **demand-driven, exceptional** power, deliberately hedged with conditions so that it does not become a routine or surveillance tool. It is important to distinguish B2G from three adjacent regimes:

- **Freedom of information (FoI)** grants the *public* a right to access documents *held by public authorities*; Chapter V runs in the opposite direction (public body → private holder) and is not a transparency right [1].
- **Open data / public-sector information (PSI) re-use** (Open Data Directive) concerns re-using data the *public sector already holds*; it does not compel private parties to hand over data [3][4].
- **Law-enforcement and judicial data access** operate under their own instruments; Chapter V **expressly excludes** those purposes (Art. 16) [1].

Chapter V applied from **12 September 2025** alongside the Act's other headline obligations (Art. 50) [1][4]. As a new instrument, its practical contours will be shaped by Commission guidance, Member-State designation of **data coordinators** and competent authorities, and — in time — case law.

# Legal Framework

The Data Act is a **Regulation** — directly applicable across the EU without national transposition. Chapter V states the B2G obligation plainly; interpretation is aided by its recitals and by Commission guidance. The obligation attaches to a **data holder** (other than a public sector body, the Commission, the ECB or a Union body) and runs to those same public actors when they demonstrate an exceptional need. The chapter's architecture:

- **Art. 14 — Obligation to make data available on the basis of an exceptional need:** upon request, a data holder shall make data available (with metadata needed to interpret it) to a public sector body, the Commission, the ECB or a Union body that demonstrates an exceptional need [1]. *(Legal obligation.)*
- **Art. 15 — Exceptional need to use data:** exhaustively defines the trigger — (1)(a) public-emergency response; (1)(b) non-emergency, **non-personal data only**, public-interest task explicitly provided for by law where alternatives are exhausted; and (2) **point (b) does not apply to micro and small enterprises** [1]. *(Legal obligation / scope limit.)*
- **Art. 16 — Relationship with other obligations:** Chapter V is **without prejudice** to other reporting/access duties and **does not apply** to activities for the prevention, investigation, detection or prosecution of criminal or administrative offences, the execution of criminal penalties, or customs/taxation administration [1]. *(Scope limit.)*
- **Art. 17 — Requests for data to be made available:** the request must specify the data/metadata, state and evidence the exceptional need (per Art. 15), be **proportionate** in granularity, volume and frequency, explain the purpose and intended use and any onward sharing, use the **least disruptive** means, seek **non-personal** data first and personal data only where strictly necessary and pseudonymised, and be **made publicly available online** (via the data coordinator, or by the Commission/Union body) [1]. *(Legal obligation.)*
- **Art. 18 — Compliance with requests for data:** data to be made available **without undue delay**; a holder may **decline or request modification** on limited grounds (no control over the data; a substantially identical request already fulfilled; the request does not meet Art. 17), acting within **5 working days** (public emergency) or **30 working days** (other cases); disputes go to the **competent authority** [1]. *(Legal obligation.)*
- **Art. 19 — Obligations of public sector bodies, the Commission, the ECB and Union bodies:** use the data only for the requested purpose; do not reuse it for other purposes; **destroy** it when no longer needed and inform the data holder; apply technical/organisational measures and respect the GDPR; may not use Chapter V data for the excluded (criminal/penalty) purposes [1][2]. *(Legal obligation.)*
- **Art. 20 — Compensation in the context of exceptional need:** **free of charge** for public-emergency response (Art. 15(1)(a)) — save that **micro/small enterprises** may claim compensation; otherwise **reasonable compensation** covering technical and organisational costs, **including a reasonable margin** (margin excluded for micro/small) [1]. *(Legal obligation.)*
- **Art. 21 — Sharing of data obtained in the context of exceptional need with research organisations or statistical bodies:** the public actor may share the data with **research organisations or statistical bodies** carrying out **compatible** activities, subject to the same use limits and safeguards [1]. *(Legal obligation.)*
- **Art. 22 — Mutual assistance and cross-border cooperation:** competent authorities cooperate; a request touching a holder in another Member State is notified to that State's competent authority; where **personal data** is involved, the relevant **data-protection supervisory authority** is engaged; objections are possible where the request breaches Chapter V [1]. *(Legal obligation.)*

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 14 | Data holder must, upon request, make data available to a public sector body / Commission / ECB / Union body demonstrating an exceptional need. | [1] |
| Art. 15(1)(a) | Exceptional need where data is **necessary to respond to a public emergency** and the body cannot obtain it by alternative means in time. | [1] |
| Art. 15(1)(b) | **Non-emergency** exceptional need — **non-personal data only** — to fulfil a specific public-interest task explicitly provided for by law where alternatives are exhausted. | [1] |
| Art. 15(2) | **Micro and small enterprises are excluded** from the non-emergency case (Art. 15(1)(b)); compellable only in a public emergency. | [1] |
| Art. 16 | Chapter V **does not apply** to criminal/administrative-offence prevention/investigation/prosecution, execution of criminal penalties, or customs/taxation; without prejudice to other access duties. | [1] |
| Art. 17 | Request requirements: specificity, proportionality, stated exceptional need and purpose, least-disruptive means, non-personal-first / pseudonymised personal data, and **public availability** of the request. | [1] |
| Art. 18 | Compliance without undue delay; decline/modification grounds; **5 working days** (emergency) / **30 working days** (other); escalation to competent authority. | [1] |
| Art. 19 | Requesting bodies: purpose limitation, no reuse, deletion when no longer needed, technical/organisational measures, GDPR compliance. | [1][2] |
| Art. 20 | Compensation: **free** for emergency response (micro/small excepted); otherwise costs **+ reasonable margin** (margin excluded for micro/small). | [1] |
| Art. 21 | Onward sharing of obtained data with **research organisations / statistical bodies** for compatible activities. | [1] |
| Art. 22 | **Mutual assistance / cross-border** cooperation; DPA involvement where personal data; objection where Chapter V criteria unmet. | [1] |
| Art. 1(5) | Relationship with data-protection law — GDPR, Reg (EU) 2018/1725 and ePrivacy apply to personal data and **prevail on conflict**. | [1][2] |
| Art. 50 | Application of the Regulation (incl. Chapter V) **from 12 September 2025**. | [1] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 10 area | Chapter V is without prejudice to, and does not displace, law providing for data access/use for criminal-offence prevention/investigation/prosecution or execution of criminal penalties. | [1] |
| Recital 65 area | Rationale for a narrow B2G exceptional-need power distinct from ordinary reporting duties; emphasis on proportionality and time/scope limitation. | [1] |
| Recital 68 area | Public-emergency response should generally be free of charge; non-emergency provision merits reasonable compensation including a margin (excluded for micro/small enterprises). | [1] |
| Recital 72 area | Onward sharing with research organisations and statistical bodies acting in the public interest, under compatible purposes and safeguards. | [1] |

*Recitals are not binding but aid construction of the operative articles; they are cited here as interpretive aids only. Recital numbering is indicative and should be confirmed against the OJ text.*

## Relevant Case Law

**Not Applicable.** The Data Act is a new instrument; Chapter V applied only from 12 September 2025, and there is no CJEU or national case law interpreting the B2G exceptional-need provisions at this document's date. Interpretive weight rests on the Regulation's text, its recitals and Commission guidance [1][4][5]. This section will be revisited once judgments or enforcement decisions emerge.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames B2G access as a **narrow, exceptional** mechanism for situations such as public emergencies, deliberately conditioned so that it is neither a routine data-collection power nor a substitute for market purchase, statutory reporting or law-enforcement channels [4][5]. *(Regulatory interpretation.)*
- The Commission stresses **proportionality and minimisation**: bodies should request the least data necessary, prefer non-personal data, and use pseudonymisation where personal data is unavoidable — consistent with Art. 17 and the GDPR [4][5]. *(Regulatory interpretation.)*
- On **compensation**, the Commission presents public-emergency response as **free of charge** (recognising the public-interest urgency), with reasonable, cost-based compensation plus a margin in non-emergency cases and protective treatment for micro/small enterprises [1][5]. *(Regulatory interpretation.)*
- The **European Parliament's** research service (EPRS) situates Chapter V within the wider data-governance package, noting the COVID-19 experience as the motivating case and the careful boundary drawn against law-enforcement and general surveillance uses [6]. *(Analytical interpretation.)*
- The Commission and commentators emphasise that Chapter V **does not create a new legal basis** for processing personal data; a requesting body must still identify a GDPR (or Reg (EU) 2018/1725) lawful basis, and the GDPR **prevails on conflict** (Art. 1(5)) [1][2][5]. *(Regulatory interpretation / legal obligation.)*

# Technical Considerations

- **Request intake and triage.** A data holder needs a defined intake channel and a triage checklist to test each request against Art. 15 (is there a genuine exceptional need, and which limb?), Art. 16 (is this an excluded purpose?), and Art. 17 (is it specific, proportionate and public?) before any data leaves the organisation [1]. *(Legal obligation, met via process.)*
- **Data minimisation by construction.** Because Art. 17 requires **non-personal data first** and personal data only where strictly necessary and **pseudonymised**, holders should be able to **extract, filter and pseudonymise** the specific fields requested — not export whole datasets [1][2]. Techniques align with ENISA/ISO pseudonymisation guidance (see `pets-foundations`). *(Legal obligation, met via controls.)*
- **Metadata and interpretability.** Art. 14 requires the data holder to include the **metadata necessary to interpret and use** the data; export tooling should attach schemas, units, provenance and quality indicators [1]. *(Legal obligation.)*
- **Secure delivery and logging.** Provide the data through a secure channel with integrity protection, and **log** what was disclosed, to whom, on what legal basis and for what stated purpose — evidence needed for accountability, the Art. 20 compensation claim, and any Art. 18 objection [1]. *(Best practice / evidentiary.)*
- **Deletion and purpose enforcement (on the requester side).** Public bodies must apply technical/organisational measures and **destroy** the data when no longer needed (Art. 19); technically this means scoped storage, retention timers and audit trails on the receiving side [1]. *(Legal obligation.)*

# Hosting Considerations

- **Where the data physically sits.** A hosting or cloud provider may itself be a **data holder** for data it controls, or merely a **processor** hosting a customer's data. A B2G request is addressed to the entity that is the **data holder**; a pure hosting provider generally routes the request to its customer rather than disclosing unilaterally, consistent with its contract and the GDPR processor role [1][2]. *(Interpretation — assess role.)*
- **Cross-border and jurisdiction.** Where data is hosted in another Member State, Art. 22 mutual-assistance routing and, for personal data, DPA involvement apply; providers should know **where** requested data resides and which competent authority governs [1]. *(Legal obligation — assess.)*
- **Segregation and extraction tooling.** Hosting architectures should support **targeted extraction** of specific datasets/fields so that a proportionate, minimised response (Art. 17) is technically feasible without over-disclosure [1]. *(Best practice.)*
- **No conflict with third-country access safeguards.** Responding to an EU B2G request is distinct from — and must not be conflated with — Art. 32 safeguards against **unlawful third-country governmental access** to non-personal data (see `data-act-foundations`) [1]. *(Distinction.)*

# Game Hosting Considerations

- **Usually low exposure, but not zero.** Most game studios will rarely receive a Chapter V request, but operators of **large-scale connected-play, telemetry or IoT-peripheral** platforms could hold data relevant to a **public emergency** (e.g. aggregate network, location or device-telemetry data in a natural disaster or major cybersecurity incident) [1]. *(Interpretation — assess per case.)*
- **Micro/small studios are largely shielded.** Many independent studios are **micro or small enterprises** and are therefore **exempt from the non-emergency case** (Art. 15(2)); they can be compelled only in a genuine **public emergency**, and even then may claim compensation (Art. 20) [1]. *(Scope limit.)*
- **Player personal data stays under the GDPR.** Any request touching player accounts, location or behavioural data engages the GDPR in parallel; respond with **non-personal/aggregated** data first and pseudonymised personal data only where strictly necessary (Arts. 17, 19; Art. 1(5)) — Chapter V is not a lawful basis, and children's-data defaults heighten the duty (see `uk-childrens-code`) [1][2]. *(Legal obligation.)*
- **Never a law-enforcement channel.** Requests for player data for the **investigation or prosecution of offences** fall **outside** Chapter V (Art. 16) and must be handled under the applicable law-enforcement/judicial-cooperation instruments instead [1]. *(Scope limit.)*

# AI Considerations

- **Emergency analytics and models.** Public bodies may seek privately held data to **train or run models** supporting emergency response (e.g. epidemiological or disaster-response analytics). Any such use remains bound by Art. 19 purpose limitation and, for personal data, the **GDPR and (from 2 Aug 2026) relevant AI Act** obligations — Chapter V does not exempt an AI use from either [1][2]. *(Legal obligation / cross-reference.)*
- **Minimisation feeds trustworthy AI.** The Art. 17 preference for non-personal and pseudonymised data supports data-minimised, privacy-preserving model development; align with **PETs** approaches (federated/aggregated analytics) where feasible (see `pets-foundations`) [1][2]. *(Best practice.)*
- **Onward sharing for research.** Art. 21 permits sharing obtained data with **research organisations/statistical bodies** for compatible purposes — a lawful route for public-interest research/AI work, but still subject to purpose limits and data-protection safeguards [1]. *(Legal obligation — bounded.)*
- **No repurposing.** Data obtained for an emergency may **not** be silently repurposed to train general-purpose or unrelated models (Art. 19 no-reuse) [1]. *(Legal obligation.)*

# Operational Guidance

Labels: **OBLIGATION** (a cited law requires the outcome) / **BEST PRACTICE** (standards/industry consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

## For data holders (recipients of a B2G request)

1. **Stand up a request-handling process now** — a named owner, an intake channel and a documented assessment workflow; Chapter V is **in force** (from 12 Sep 2025). *(OBLIGATION to be able to comply.)* [1][4]
2. **Test the trigger (Art. 15)** — confirm a genuine **exceptional need** and which limb applies; if non-emergency, confirm the data is **non-personal** and, if you are a **micro/small enterprise**, that you are exempt (Art. 15(2)). *(OBLIGATION.)* [1]
3. **Screen for excluded purposes (Art. 16)** — refuse to treat a criminal/administrative-penalty, customs or tax request as a Chapter V request; redirect to the correct legal channel. *(OBLIGATION.)* [1]
4. **Check the request against Art. 17** — specificity, proportionality, stated purpose, least-disruptive means, non-personal-first, public availability; if deficient, **seek modification** (Art. 18). *(OBLIGATION.)* [1]
5. **Minimise before disclosing** — extract only the specified data/fields with necessary metadata; pseudonymise any unavoidable personal data; never export whole datasets by default. *(OBLIGATION + BEST PRACTICE.)* [1][2]
6. **Meet the timeframe (Art. 18)** — respond/decline within **5 working days** (public emergency) or **30 working days** (other cases); document the decision. *(OBLIGATION.)* [1]
7. **Claim compensation where due (Art. 20)** — free for emergency response (unless you are a micro/small enterprise); otherwise cost **+ reasonable margin**. *(Right — evidence your costs.)* [1]
8. **Run Chapter V and the GDPR together** — never treat a B2G request as a GDPR lawful basis; keep records of processing and, where warranted, a DPIA (see `privacy-engineering-foundations`). *(OBLIGATION.)* [1][2]

## For requesting public bodies (orientation)

1. **Evidence the exceptional need and purpose (Arts. 15, 17)**, request the **minimum** data, and make the request **public** via the data coordinator. *(OBLIGATION on the requester.)* [1]
2. **Enforce use limits (Art. 19)** — purpose limitation, no reuse, deletion when no longer needed, and DPA engagement for personal data. *(OBLIGATION.)* [1]
3. **Use Art. 21/22 correctly** — onward-share only with research/statistical bodies for compatible purposes, and route cross-border requests through competent authorities. *(OBLIGATION.)* [1]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | No process to receive/assess a Chapter V request (non-compliance on demand) | Medium | High | Arts. 14, 18 [1] | Stand up documented request-handling workflow and owner | Low |
| R2 | Over-disclosure — exporting whole datasets instead of minimised, specified data | Medium | High | Art. 17 [1] | Targeted extraction; non-personal-first; pseudonymisation | Low |
| R3 | Treating a B2G disclosure as a GDPR lawful basis (unlawful personal-data disclosure) | Medium | High | Arts. 19, 1(5) [1][2] | Separate lawful-basis analysis; minimise; DPIA where needed | Low |
| R4 | Mishandling an excluded (criminal/tax/customs) request as Chapter V | Low | High | Art. 16 [1] | Purpose screen; redirect to correct legal channel | Low |
| R5 | Micro/small enterprise wrongly compelled in a non-emergency case | Low | Medium | Art. 15(2) [1] | Assert exemption; respond only to emergency requests | Low |
| R6 | Missing the Art. 18 response window (5 / 30 working days) | Medium | Medium | Art. 18 [1] | SLA and calendar controls in the workflow | Low |
| R7 | Failing to claim, or over-claiming, compensation | Medium | Low | Art. 20 [1] | Cost model; free-for-emergency rule; margin rules | Low |
| R8 | Uncontrolled onward sharing beyond research/statistical bodies | Low | Medium | Art. 21 [1] | Restrict onward sharing; contractual/purpose controls | Low |
| R9 | Cross-border request handled without competent-authority / DPA routing | Low | Medium | Art. 22 [1] | Jurisdiction mapping; authority/DPA escalation path | Low |

# Implementation Roadmap

- **Phase 0 — Readiness & role mapping:** Confirm whether you are a **data holder** for any datasets of potential public interest; classify enterprise size (micro/small exemption). *Effort:* Low–Medium.
- **Phase 1 — Request-handling capability:** Build the intake channel, assessment checklist (Arts. 15–17), decision/objection templates (Art. 18) and response SLAs (5 / 30 working days). *Effort:* Medium.
- **Phase 2 — Minimisation tooling:** Implement targeted extraction, metadata attachment and pseudonymisation so a proportionate response is technically feasible. *Effort:* Medium.
- **Phase 3 — Data-protection integration:** Wire Chapter V into the GDPR accountability stack (records of processing, lawful-basis check, DPIA trigger, DPA-engagement path for cross-border). *Effort:* Medium.
- **Phase 4 — Compensation & onward-sharing governance:** Cost model for non-emergency requests; controls on Art. 21 onward sharing. *Effort:* Low.
- **Phase 5 — Monitor & adapt:** Track Commission guidance, Member-State designation of data coordinators/competent authorities, and emerging practice/case law. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No awareness of Chapter V; no way to receive or assess a B2G request. | No process; no owner. |
| 2 | Managed | Owner named; basic intake exists; ad hoc assessment against Art. 15/16. | Draft checklist; size/exemption known. |
| 3 | Defined | Documented request-handling workflow with Art. 17/18 templates and response SLAs. | Decision/objection templates; SLA tracking. |
| 4 | Quantitatively Managed | Minimisation/pseudonymisation tooling; GDPR-integrated; compensation model; drills run. | Targeted extraction tested; DPIA path; rehearsed responses. |
| 5 | Optimising | B2G integrated with wider data-governance (GDPR/AI/NIS2); cross-border routing mature; continuous monitoring. | Unified governance; authority/DPA playbooks; metrics. |

# Audit Questions

1. Do you have a documented process to **receive and assess** a Chapter V request, with a named owner and response SLAs? *(Arts. 14, 18 [1].)*
2. How do you test each request for a genuine **exceptional need** and identify which limb of Art. 15 applies (and whether the non-personal-only limit bites)? *(Art. 15 [1].)*
3. As a **micro/small enterprise**, do you correctly assert the Art. 15(2) exemption from non-emergency requests? *(Art. 15(2) [1].)*
4. How do you **screen out excluded purposes** (criminal/administrative offences, penalties, customs/tax) and redirect them? *(Art. 16 [1].)*
5. How do you verify a request meets **Art. 17** (specificity, proportionality, purpose, least-disruptive, non-personal-first, public availability) and seek modification if not? *(Arts. 17, 18 [1].)*
6. How do you **minimise and pseudonymise** before disclosing, and attach only necessary metadata? *(Arts. 14, 17, 19 [1][2].)*
7. How do you ensure a B2G disclosure is **not** treated as a GDPR lawful basis, and is documented in your records of processing? *(Arts. 19, 1(5) [1][2].)*
8. How do you calculate and claim **compensation** (free for emergency response; cost + margin otherwise; micro/small rules)? *(Art. 20 [1].)*
9. How do you control **onward sharing** (Art. 21) and route **cross-border** requests through competent authorities and DPAs (Art. 22)? *(Arts. 21, 22 [1].)*

# Implementation Checklist

- [ ] Data-holder status and enterprise-size (micro/small exemption) assessed.
- [ ] B2G request-handling workflow documented, with a named owner and intake channel.
- [ ] Assessment checklist covering Art. 15 (exceptional need / limb), Art. 16 (excluded purposes) and Art. 17 (request requirements).
- [ ] Decision, modification-request and objection templates prepared (Art. 18), with **5 / 30 working-day** SLAs.
- [ ] Minimisation tooling: targeted extraction, metadata attachment and pseudonymisation of any personal data (Arts. 14, 17, 19).
- [ ] GDPR integration: lawful-basis check, records of processing, DPIA trigger, DPA-engagement path for cross-border (Arts. 19, 22, 1(5)).
- [ ] Compensation model: free-for-emergency rule and cost-plus-margin for non-emergency (Art. 20).
- [ ] Onward-sharing controls limiting disclosure to research/statistical bodies for compatible purposes (Art. 21).
- [ ] Cross-border routing to competent authorities and supervisory authorities established (Art. 22).
- [ ] Monitoring of Commission guidance and Member-State data-coordinator/competent-authority designations.

# References

*All links verified live on 2026-07-12 (`sources_verified`). Chapter V article content summarised above was checked against the EUR-Lex text of Regulation (EU) 2023/2854 and per-article annotated reproductions on 2026-07-12; Art. 15(2) (micro/small carve-out), Art. 16 (excluded purposes), Art. 18 (5/30 working-day windows) and Art. 20 (free emergency response; cost + margin) were specifically verified.*

## Primary Sources

- [1] **Regulation (EU) 2023/2854 (Data Act)** — harmonised rules on fair access to and use of data; **Chapter V (Arts. 14–22)** B2G data sharing on the basis of exceptional need, plus Art. 1(5), Art. 2 definitions and Art. 50 application date. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2023/2854/oj
- [2] **Regulation (EU) 2016/679 (GDPR)** — parallel application to personal data disclosed under Chapter V; prevails on conflict (Data Act Art. 1(5)). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [3] **Regulation (EU) 2022/868 (Data Governance Act)** — companion instrument on data intermediation and re-use of protected public-sector data; context for Art. 21 research/statistical sharing and the contrast with government-to-business flows. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/868/oj
- [4] **Directive (EU) 2019/1024 (Open Data Directive)** — governs re-use of public-sector information (the mirror-image, government-to-business flow), contrasted with Chapter V B2G. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2019/1024/oj

## Regulatory Guidance

- [5] **Data Act (policy page)** and **Data Act explained (FAQ)** — objectives and B2G exceptional-need context; application from 12 September 2025. European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/data-act
- [6] **The Data Act** (briefing, PE 733.681) — legislative background and B2G analysis. European Parliament, EPRS. https://www.europarl.europa.eu/RegData/etudes/BRIE/2022/733681/EPRS_BRI(2022)733681_EN.pdf

## Standards

**Not Applicable.** Chapter V is a legal-obligation regime with no directly governing technical standard. Data-minimisation and pseudonymisation techniques relevant to a compliant response are covered, with citations, in `pets-foundations` and `privacy-engineering-foundations`.

## Academic Sources

**Not Applicable.** This deep dive relies on the primary Regulation, companion legislation and Commission/Parliament guidance. Peer-reviewed analysis of B2G data sharing will be added if it becomes load-bearing on a specific contested point.

# Further Reading

*Non-authoritative; provided for orientation only.*

- Data Act (European Union) — overview. Wikipedia. https://en.wikipedia.org/wiki/Data_Act_(European_Union)
- EU Data Act — Article 15 (Exceptional need to use data), annotated per-article text. https://data-act-law.eu/article/15/
- European Commission, Data Act explained (FAQ). https://digital-strategy.ec.europa.eu/en/faqs/data-act-explained

# Related Documents

- `data-act-foundations` — **parent**; Chapter-by-chapter overview and application timeline (this document details its Chapter V B2G material).
- `data-act-cloud-switching` — **sibling** deep dive on Chapter VI (switching) and Chapter VIII (interoperability).
- `gdpr-foundations` — parallel data-protection regime; GDPR prevails on personal-data conflict (Art. 1(5)) and governs any personal data disclosed under Chapter V.
- `nis2-foundations` — cybersecurity regime; a **major cybersecurity incident** can constitute a public emergency triggering Art. 15(1)(a).
- `data-act-iot-sharing` — Chapter II connected-product data sharing (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-12 | Technical Writer (virtual agent) | Initial draft; deep dive on Data Act Chapter V (B2G exceptional-need access, Arts. 14–22). Article content verified against the EUR-Lex text of Regulation (EU) 2023/2854 and per-article annotated reproductions: Art. 15(2) micro/small carve-out from the non-emergency case; Art. 16 exclusion of criminal/administrative-offence, penalty and customs/tax purposes; Art. 15(1)(b) non-personal-data limitation; Art. 17 request requirements; Art. 18 compliance windows (5 / 30 working days) and objection grounds; Art. 19 use limits/GDPR; Art. 20 compensation (free emergency response; cost + reasonable margin otherwise); Arts. 21–22 onward sharing and cross-border cooperation. All references returned HTTP 200 on 2026-07-12. | — |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster D, residual list); full-repo validator/link/lint suite green; frozen in release 0.18.0. | Orchestrator (QA-verified) |
