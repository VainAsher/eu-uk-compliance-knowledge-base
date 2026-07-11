---
id: data-act-foundations
title: "EU Data Act: Foundations, Data Access & Sharing"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: Data Act
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [gdpr-foundations, privacy-engineering-foundations, ai-act-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [data-act, eu-data-act, iot, connected-products, cloud-switching, b2g, interoperability, non-personal-data]
legal_basis: Regulation (EU) 2023/2854
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | data-act-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.7.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The Data Act's core provisions became applicable on **12 September 2025**; certain obligations phase in later (notably the Article 3(1) connected-product design duty from **12 September 2026** and the withdrawal of cloud switching charges from **12 January 2027**). Always confirm the current in-force dates before relying on them.

# Executive Summary

The **EU Data Act (Regulation (EU) 2023/2854)** is the horizontal EU rulebook on **fair access to and use of data**. Adopted on **13 December 2023**, it **entered into force on 11 January 2024** and its main provisions **became applicable on 12 September 2025** [1][3]. It complements the GDPR: where the Data Act touches **personal** data, the **GDPR (and ePrivacy) continue to govern**, and prevail in the event of conflict (Art. 1(5)) [1][2].

The Act pursues a single objective — unlock the economic and social value of data while keeping its allocation fair — through several distinct regimes: (i) **user access to data from connected products** (IoT) and related services; (ii) **B2B data-sharing** on fair, reasonable and non-discriminatory (FRAND) terms where a data holder is obliged to share; (iii) **business-to-government (B2G)** access in situations of **exceptional need**; (iv) protection against **unfair contractual terms** unilaterally imposed on SMEs; (v) rules to make **switching between cloud/data-processing services** easier and eventually free; (vi) **interoperability** requirements; and (vii) **safeguards against unlawful third-country governmental access** to non-personal data held in the EU [1][3][4].

This document establishes the foundations: purpose and scope, the chapter-by-chapter structure, the **phased application timeline**, the core obligations at a foundational level, and the **relationship with the GDPR**. Deeper mechanics — cloud switching, IoT data-sharing mechanics and B2G access — are deferred to dedicated sub-topic documents (see Scope). The single most important operational fact is that the **headline obligations are already in force (from 12 September 2025)**, with the connected-product **design** duty biting for products placed on the market **after 12 September 2026** [1][2].

# Key Takeaways

- The **Data Act (Regulation (EU) 2023/2854)** entered into force **11 January 2024** and applies from **12 September 2025** (Art. 50) [1][3]. *(Legal obligation — in force.)*
- Its purpose is **fair access to and use of data**; it is horizontal (cross-sectoral) and covers **non-personal and personal data**, complementing rather than replacing the GDPR [1][3]. *(Legal obligation.)*
- **Users of connected products (IoT)** and related services gain rights to **access the data they generate** and to have it shared with third parties (Chapter II, Arts. 3–7) [1][3]. *(Legal obligation.)*
- The **Article 3(1) "data access by design and by default"** duty applies to connected products and related services **placed on the market after 12 September 2026** [1][3]. *(Legal obligation — phased.)*
- Where a data holder **must** make data available, it must do so on **fair, reasonable, non-discriminatory (FRAND)** terms and may not impose **unfair contractual terms** on SMEs (Chapters III–IV, Arts. 8–13) [1]. *(Legal obligation.)*
- **B2G access**: public bodies may obtain data in cases of **exceptional need** (e.g., public emergencies) under strict conditions (Chapter V, Arts. 14–22) [1]. *(Legal obligation.)*
- **Cloud/data-processing switching**: providers must remove obstacles to switching; **switching charges are gradually withdrawn and prohibited from 12 January 2027** (Chapter VI, Arts. 23–31) [1][5]. *(Legal obligation — phased.)*
- **International transfers of non-personal data**: providers must take measures against **unlawful third-country governmental access/transfer** of non-personal data held in the EU (Art. 32) [1][3]. *(Legal obligation.)*
- **GDPR prevails on personal data**: in any conflict, Union/national data-protection and privacy law prevails (Art. 1(5)) [1][2]. *(Legal obligation.)*

# Purpose

This document is the Tier 2 entry point for the EU Data Act. It supports legal research (mapping the Act's several regimes and the application timeline), compliance planning (what applies now vs. later, and to whom), and product/engineering triage (whether an organisation is a data holder, a connected-product manufacturer, a data-processing-service provider, or a data recipient, and the resulting duties). It builds on `gdpr-foundations` and `privacy-engineering-foundations` and sits alongside `ai-act-foundations` in the EU digital-regulation stack.

# Scope

**In scope:** The Data Act's purpose and scope; its chapter structure; the phased application timeline (incl. the 12 September 2025, 12 September 2026, 12 September 2027 and 12 January 2027 milestones); a foundational overview of IoT/connected-product data access, B2B and B2G data sharing, unfair contractual terms, cloud/data-processing-service switching, interoperability and non-personal-data international-transfer safeguards; and the relationship with the GDPR.

**Out of scope (spun off to the research backlog):**

- Cloud/data-processing-service **switching** mechanics, timelines and charge-withdrawal detail → `data-act-cloud-switching` (planned).
- **IoT / connected-product** data-sharing mechanics, data-holder/user obligations, trade-secret handling → `data-act-iot-sharing` (planned).
- **B2G exceptional-need** access procedures and safeguards → `data-act-b2g` (planned).
- **Interoperability** requirements and standards, and the interaction with the Data Governance Act (Reg (EU) 2022/868) → future documents.

**Assumptions:** The reader has read `gdpr-foundations`. Personal-data processing under any Data Act right or obligation remains governed by the GDPR (and, where relevant, the ePrivacy rules) in parallel.

# Definitions

*Shared terms are in `GLOSSARY.md`. Data-Act-specific terms are defined here; see the Regulation's Art. 2 for the full list.*

| Term | Definition | Source |
|------|------------|--------|
| Connected product | An item that obtains, generates or collects data about its use or environment and can communicate product data via an electronic communications service, physical connection or on-device access (Art. 2(5)). | [1] |
| Related service | Digital service, other than an electronic communications service, connected with a product at purchase/rental/lease such that its absence would prevent the product performing a function (Art. 2(6)). | [1] |
| Data holder | A legal or natural person that has the right or obligation to use and make available data, including product/related-service data it has the ability to make available (Art. 2(13)). | [1] |
| User | A person who owns, rents or leases a connected product, or receives a related service (Art. 2(12)). | [1] |
| Data processing service | A digital service enabling on-demand, broad remote network access to a shared pool of configurable, scalable computing resources (i.e., cloud/edge services) (Art. 2(8)). | [1] |
| Non-personal data | Data other than personal data as defined in GDPR Art. 4(1) (personal data remains governed by the GDPR). | [1][2] |

# Background

The EU's data economy strategy identified that a large share of industrial and machine-generated data went unused, and that value was concentrated with a small number of actors who controlled the devices and platforms generating the data. Existing law (GDPR for personal data; the Database Directive; competition law) addressed only parts of the problem, leaving **connected-product data**, **B2B bargaining imbalances**, **cloud vendor lock-in** and **public-sector access in emergencies** without a horizontal framework [3][4].

The Data Act is the second pillar (with the 2022 **Data Governance Act**, Reg (EU) 2022/868) of the European Strategy for Data. Where the Data Governance Act creates structures and trust mechanisms for voluntary data sharing, the **Data Act allocates rights and obligations** over who can access and use data and on what terms [3][4]. It was adopted on 13 December 2023 with a deliberately **staggered application** to give manufacturers, cloud providers and data holders time to redesign products, contracts and systems [1][3].

# Legal Framework

The Data Act is a **Regulation** — directly applicable across the EU without national transposition. It states obligations plainly; interpretation is aided by its recitals and by Commission guidance. Its structure (chapters):

- **Chapter I (Arts. 1–2)** — subject matter, scope, definitions; and the **relationship-with-other-law** clause (incl. Art. 1(5) on GDPR primacy for personal data).
- **Chapter II (Arts. 3–7)** — **data sharing from connected products/IoT**: user access to product and related-service data, and sharing with third parties.
- **Chapter III (Arts. 8–12)** — obligations for data holders **legally obliged to make data available**: **FRAND** terms, non-discrimination, reasonable compensation.
- **Chapter IV (Art. 13)** — protection against **unfair contractual terms** unilaterally imposed (SME protection).
- **Chapter V (Arts. 14–22)** — **business-to-government (B2G)** data sharing on the basis of **exceptional need**.
- **Chapter VI (Arts. 23–31)** — **switching between data-processing (cloud/edge) services**, removal of obstacles and switching charges.
- **Chapter VII (Art. 32)** — safeguards against **unlawful third-country governmental access and transfer** of non-personal data.
- **Chapter VIII (Arts. 33–36)** — **interoperability** of data, data-sharing mechanisms and data-processing services.
- **Chapter IX (Arts. 37–42)** — implementation and **enforcement** by competent authorities; penalties set by Member States.
- **Chapters X–XI (Arts. 43–50)** — sui generis database-right clarification; final provisions incl. **Art. 50 application dates** [1].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 1(5) | Relationship with data-protection/privacy law — GDPR, Reg (EU) 2018/1725 and ePrivacy apply to personal data and **prevail in case of conflict**. | [1][2] |
| Art. 2 | Definitions (connected product, related service, data holder, user, data processing service, etc.). | [1] |
| Arts. 3–4 | Connected-product/related-service data must be accessible to the user; **Art. 3(1)** = access by design and by default; access "without undue delay, easily, securely". | [1] |
| Art. 5 | User's right to have data shared with a **third party** on request. | [1] |
| Arts. 8–9 | Data holder obligated to share must use **FRAND**, non-discriminatory terms; **reasonable compensation**. | [1] |
| Art. 13 | **Unfair contractual terms** unilaterally imposed on an enterprise are not binding. | [1] |
| Arts. 14–22 | **B2G** data sharing on the basis of exceptional need; conditions and safeguards. | [1] |
| Arts. 23–31 | **Switching** between data-processing services: removal of obstacles; **Art. 29** gradual withdrawal of switching charges. | [1][5] |
| Art. 32 | Measures against **unlawful international access/transfer** of non-personal data by third-country authorities. | [1] |
| Arts. 33–36 | **Interoperability** requirements (data, data spaces, smart contracts, data-processing services). | [1] |
| Art. 50 | **Entry into force and application** — applies from 12 September 2025, with phased dates. | [1] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 1 | Data as a key resource; objective of fair access to and use of data across the internal market. | [1] |
| Recital 7 | Horizontal, cross-sectoral framework complementing sectoral and data-protection law. | [1] |
| Recital 34 area | **FRAND** and non-discrimination rationale for mandated B2B data sharing. | [1] |

*Recitals are not binding but aid construction of the operative articles; they are cited here as interpretive aids only.*

## Relevant Case Law

**Not Applicable.** The Data Act's main provisions applied only from 12 September 2025; there is no CJEU or national case law interpreting it at this document's date. Interpretive weight rests on the Regulation's text, its recitals and Commission guidance [1][3][4].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames the Data Act as making "more data available for use" while ensuring **fairness** in how value from data is allocated, and stresses it is **horizontal** (applying across sectors and to all connected products placed on the EU market, irrespective of manufacturer establishment) [3][4]. *(Regulatory interpretation.)*
- **IoT / connected products:** the Commission explains users should be able to access data generated by their use of connected products and share it with third parties (e.g., independent repairers), improving competition in aftermarket services [3][4]. *(Regulatory interpretation.)*
- **Cloud switching:** the Commission presents the switching rules as targeting **vendor lock-in**, requiring providers to remove commercial, technical and contractual obstacles and to withdraw switching charges over a transition period [3][5]. *(Regulatory interpretation.)*
- **International transfers / non-personal data:** Art. 32 is presented as protecting EU-held non-personal data against **unlawful** third-country governmental access, mirroring GDPR-style safeguards for the non-personal sphere [3]. *(Regulatory interpretation.)*
- **GDPR interplay:** the Commission and commentators emphasise the Data Act **does not create a new legal basis** for processing personal data; controllers must still identify a GDPR lawful basis, and the GDPR prevails on conflict (Art. 1(5)) [1][2][4]. *(Regulatory interpretation / legal obligation.)*

# Technical Considerations

- **Data access by design (Art. 3(1))** — connected products and related services placed on the market **after 12 September 2026** must be engineered so product/related-service data is, by default, **easily, securely and (where feasible) directly accessible** to the user, in a structured, commonly used, machine-readable format [1][3]. *(Legal obligation — phased.)*
- **Interfaces and formats** — data holders must provide access "without undue delay, of the same quality as available to the data holder, and, where applicable, continuously and in real-time" (Art. 4); expose stable APIs and machine-readable formats [1]. *(Legal obligation.)*
- **Trade secrets and security** — sharing obligations must be reconciled with trade-secret protection and product security/safety; technical measures (e.g., need-to-know disclosure, protective agreements) are contemplated [1]. *(Legal obligation — detail deferred to `data-act-iot-sharing`.)*
- **Switching engineering (Chapter VI)** — providers must support **functional equivalence** (where feasible), open interfaces and export of exportable data/digital assets to enable switching; this is an architectural, not merely contractual, requirement [1][5]. *(Legal obligation — detail deferred to `data-act-cloud-switching`.)*
- **Interoperability (Arts. 33–36)** — align data, metadata and interfaces with essential interoperability requirements and, where adopted, common specifications/standards for data spaces and data-processing services [1]. *(Legal obligation.)*

# Hosting Considerations

- **Cloud/edge providers are directly in scope** — "data processing services" (IaaS/PaaS/SaaS-type on-demand compute) must meet Chapter VI switching obligations: remove obstacles, provide pre-contractual switching information, support export, and **stop charging switching fees from 12 January 2027** [1][5]. *(Legal obligation — phased.)*
- **Contractual overhaul** — hosting contracts must include mandated switching clauses (maximum notice/transition periods, assistance obligations); unfair-term protections (Art. 13) also constrain terms imposed on SME customers [1]. *(Legal obligation.)*
- **Non-personal-data transfer safeguards (Art. 32)** — providers holding EU non-personal data must implement technical, organisational and legal measures to resist **unlawful** third-country governmental access/transfer; assess jurisdictional exposure and government-access request handling [1][3]. *(Legal obligation.)*
- **Interoperability posture** — position for functional equivalence and open export formats now, ahead of enforcement maturity. *(Editorial recommendation.)*

# Game Hosting Considerations

- **Connected-product angle is usually narrow** — pure online game services are generally not "connected products", but **IoT peripherals, VR/AR headsets, wearables and connected controllers** that collect usage/environment data can fall within Chapter II, triggering user data-access duties for their manufacturers [1][3]. *(Interpretation — assess per device.)*
- **Cloud switching applies to game backends** — studios hosting on cloud/edge "data processing services" benefit from the switching rules as **customers**, and (if they resell managed hosting) may owe them as **providers** [1][5]. *(Legal obligation — assess role.)*
- **Personal data still governed by GDPR** — player telemetry that is personal data remains under the GDPR; the Data Act adds access/portability expectations but does not displace consent/lawful-basis analysis, especially for minors [1][2]. *(Legal obligation.)*

# AI Considerations

- **Data Act feeds AI data pipelines** — connected-product and B2B data made available under the Data Act may become **training or operational input** for AI systems; the acquiring party must still hold a GDPR lawful basis for any personal data and honour Art. 1(5) primacy [1][2]. *(Legal obligation.)*
- **Overlap with the AI Act** — high-risk AI **data-governance** duties (AI Act Arts. 10) and the Data Act's data-access/quality provisions are complementary; see `ai-act-foundations`. Sourcing data via Data Act rights does not exempt an AI provider from AI Act obligations. *(Cross-reference / best practice.)*
- **Interoperability and data spaces** — the Data Act's interoperability rules underpin **common European data spaces** that AI developers may draw on; align data formats accordingly. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Map your role(s)** — determine whether you are a connected-product manufacturer, data holder, user, third-party recipient, or data-processing-service provider; roles drive every obligation. *(OBLIGATION — foundational.)* [1]
2. **Inventory connected products and data** — catalogue products/related services placed (or to be placed) on the EU market and the data they generate. *(OBLIGATION.)* [1][3]
3. **Build data-access-by-design** — for products launching **after 12 September 2026**, engineer Art. 3(1) default, secure, machine-readable access. *(OBLIGATION — phased.)* [1]
4. **Regularise B2B sharing terms** — where obliged to share, apply **FRAND**, non-discriminatory terms and reasonable compensation; remove **unfair terms** (Art. 13) from SME contracts. *(OBLIGATION.)* [1]
5. **Prepare a B2G response process** — define how you assess and answer public-body exceptional-need requests (Arts. 14–22). *(OBLIGATION.)* [1]
6. **Cloud providers: implement switching** — update contracts, expose export/interoperability, and remove switching charges by **12 January 2027**. *(OBLIGATION — phased.)* [1][5]
7. **Address non-personal-data transfer risk** — implement Art. 32 safeguards against unlawful third-country government access. *(OBLIGATION.)* [1]
8. **Run Data Act and GDPR together** — never treat a Data Act right as a GDPR lawful basis; keep DPIAs/DPbDD in play (see `privacy-engineering-foundations`). *(OBLIGATION + BEST PRACTICE.)* [1][2]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Connected products launched after 12 Sep 2026 without Art. 3(1) access-by-design | Medium | High | Art. 3(1) [1] | Design-stage data-access build; product roadmap review | Low |
| R2 | Withholding/blocking user data access or third-party sharing | Medium | High | Arts. 4–5 [1] | Access APIs; documented request handling | Low |
| R3 | Non-FRAND or unfair B2B contract terms with SMEs | Medium | Medium | Arts. 8–13 [1] | FRAND policy; contract remediation | Low |
| R4 | Cloud switching charges/obstacles persisting past 12 Jan 2027 | Medium | High | Arts. 23–31; Art. 29 [1][5] | Remove charges; export/interoperability; contract update | Medium |
| R5 | Unlawful third-country access to EU non-personal data | Medium | High | Art. 32 [1] | Legal/technical safeguards; request-handling protocol | Medium |
| R6 | Treating a Data Act right as a GDPR lawful basis | Medium | High | Art. 1(5) [1][2] | Separate lawful-basis analysis; DPIA | Low |
| R7 | Mis-scoping (missing a connected-product or data-holder role) | Medium | High | Art. 2 [1] | Role/asset mapping; periodic re-assessment | Low |

# Implementation Roadmap

- **Phase 0 — Role & asset mapping:** Identify roles (holder/user/provider) and in-scope products, services and data. *Effort:* Medium.
- **Phase 1 — In-force compliance (from 12 Sep 2025):** User data access (Arts. 4–5), FRAND terms (Arts. 8–12), unfair-term removal (Art. 13), Art. 32 safeguards, switching-obstacle removal. *Effort:* High.
- **Phase 2 — Product design (by 12 Sep 2026):** Engineer Art. 3(1) access-by-design into new connected products. *Effort:* High.
- **Phase 3 — Switching charge withdrawal (by 12 Jan 2027):** Remove switching charges; finalise export/interoperability. *Effort:* Medium.
- **Phase 4 — Legacy contracts (by 12 Sep 2027):** Bring qualifying pre-existing contracts into line (Art. 50 transitional). *Effort:* Medium.
- **Phase 5 — Monitor & adapt:** Track Commission guidance, delegated/implementing acts, interoperability standards and enforcement practice. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No role mapping; unaware of Data Act obligations. | Products/data unmapped. |
| 2 | Managed | Roles identified; in-force basics (user access, unfair-term review) started. | Partial inventory; contract review begun. |
| 3 | Defined | Documented role/asset register; FRAND and Art. 32 processes in place. | Access APIs; B2G process defined. |
| 4 | Quantitatively Managed | Access-by-design in new products; switching export tested; metrics tracked. | Art. 3(1) builds; switching drills. |
| 5 | Optimising | Integrated Data Act + GDPR + AI Act governance; interoperability-ready. | Unified data-governance; audits. |

# Audit Questions

1. Have you mapped your Data Act roles (data holder, user, connected-product manufacturer, data-processing-service provider)? *(Art. 2 [1].)*
2. For products launching after 12 Sep 2026, how is Art. 3(1) access-by-design implemented? *(Art. 3(1) [1].)*
3. How do users access their data and request third-party sharing, and within what timeframe? *(Arts. 4–5 [1].)*
4. Where you must share data, how do you evidence FRAND, non-discriminatory terms and reasonable compensation? *(Arts. 8–12 [1].)*
5. How have unfair contractual terms been removed from SME contracts? *(Art. 13 [1].)*
6. What is your process for B2G exceptional-need requests? *(Arts. 14–22 [1].)*
7. For cloud/data-processing services, are switching obstacles removed and charges withdrawn (by 12 Jan 2027)? *(Arts. 23–31 [1][5].)*
8. What safeguards prevent unlawful third-country governmental access to EU non-personal data? *(Art. 32 [1].)*
9. How do you ensure a Data Act right is not treated as a GDPR lawful basis? *(Art. 1(5) [1][2].)*

# Implementation Checklist

- [ ] Data Act role and asset register completed (Art. 2).
- [ ] User data-access and third-party-sharing mechanism live (Arts. 4–5).
- [ ] Art. 3(1) access-by-design scoped for post-12 Sep 2026 products.
- [ ] FRAND / non-discrimination policy for mandated B2B sharing (Arts. 8–12).
- [ ] Unfair contractual terms removed from SME contracts (Art. 13).
- [ ] B2G exceptional-need request-handling process defined (Arts. 14–22).
- [ ] Cloud switching obstacles removed; charges withdrawal planned by 12 Jan 2027 (Arts. 23–31).
- [ ] Art. 32 non-personal-data international-access safeguards implemented.
- [ ] GDPR lawful-basis analysis and DPIA/DPbDD run alongside Data Act work.
- [ ] Legacy contracts remediated ahead of 12 Sep 2027 transitional deadline.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2023/2854 (Data Act)** — harmonised rules on fair access to and use of data. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2023/2854/oj
- [2] **Regulation (EU) 2016/679 (GDPR)** — parallel application to personal data processed under the Data Act (prevails on conflict, Art. 1(5)). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj

## Regulatory Guidance

- [3] **Data Act (policy page).** European Commission, Shaping Europe's Digital Future (entry into force 11 Jan 2024; application 12 Sep 2025). https://digital-strategy.ec.europa.eu/en/policies/data-act
- [4] **Data Act explained (FAQ).** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/faqs/data-act-explained
- [5] **Switching cloud service providers / cloud switching.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cloud-switching

## Standards

Not Applicable at the foundational level. Interoperability standards/common specifications adopted under Arts. 33–36 will be cited in the interoperability and cloud-switching sub-topic documents once published.

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation and Commission guidance. Academic analysis (e.g., GDPR/Data Act interplay, FRAND critique) will be cited in the sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- Data Act (European Union) — overview. Wikipedia. https://en.wikipedia.org/wiki/Data_Act_(European_Union)
- Regulation (EU) 2022/868 (Data Governance Act) — companion instrument. EUR-Lex. https://eur-lex.europa.eu/eli/reg/2022/868/oj

# Related Documents

- `gdpr-foundations` — parallel data-protection regime (**prerequisite reading**); GDPR prevails on personal-data conflicts (Art. 1(5)).
- `privacy-engineering-foundations` — DPbDD/security controls relevant to data-access-by-design and Art. 32 safeguards.
- `ai-act-foundations` — adjacent EU digital regime; Data Act data may feed AI systems.
- `data-act-cloud-switching` — Chapter VI switching detail (planned).
- `data-act-iot-sharing` — Chapter II connected-product data-sharing mechanics (planned).
- `data-act-b2g` — Chapter V business-to-government access (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Reg (EU) 2023/2854) and European Commission sources; application dates (12 Sep 2025 general; 12 Sep 2026 Art. 3(1); 12 Jan 2027 switching charges; 12 Sep 2027 legacy contracts) and GDPR-primacy (Art. 1(5)) live-verified. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at batch human review gate (parallel cluster); frozen in release 0.7.0. | Human reviewer |
