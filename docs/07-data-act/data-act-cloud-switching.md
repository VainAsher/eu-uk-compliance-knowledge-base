---
id: data-act-cloud-switching
title: "EU Data Act: Cloud Switching, Portability & Interoperability"
version: 1.0.0
status: in-review
classification: public
jurisdiction: [EU]
topic: Data Act
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [data-act-foundations, cloud-hosting-foundations, dora-foundations, nis2-foundations, gdpr-foundations, gdpr-transfers]
tags: [data-act, cloud-switching, portability, interoperability, functional-equivalence, switching-charges, vendor-lock-in, iaas, paas, saas, data-egress, exit-strategy]
legal_basis: Regulation (EU) 2023/2854, Chapter VI (Arts. 23–31) and Chapter VIII (Arts. 33–36)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | data-act-cloud-switching |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.15.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer (loop-authorised) — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a sub-topic deep dive that details the switching material summarised in `data-act-foundations`. The Data Act's switching rules (Chapter VI) **apply from 12 September 2025**, but the headline commercial obligation — the **prohibition on switching charges — takes effect on 12 January 2027** (Art. 29(1)); until then only cost-based *reduced* switching charges are permitted (Art. 29(2)) [1]. Always confirm the current in-force dates and any delegated/implementing acts before relying on them.

# Executive Summary

The **EU Data Act (Regulation (EU) 2023/2854)** devotes **Chapter VI (Articles 23–31)** to **switching between data processing services** — its answer to cloud **vendor lock-in** — and **Chapter VIII (Articles 33–36)** to **interoperability** [1]. Together they impose, on providers of "data processing services" (the Art. 2(8) term that captures cloud **IaaS, PaaS and SaaS** and edge services), a legally enforceable duty to let customers **leave**: to switch to a competing service of the same type, move to on-premises infrastructure, or use several providers in parallel, taking their **exportable data and digital assets** with them [1].

Three mechanics dominate. First, **obstacle removal (Art. 23)**: providers must not impose, and must remove, "pre-commercial, commercial, technical, contractual and organisational" obstacles to switching [1]. Second, **mandatory contract terms (Art. 25)**: a written contract must guarantee a **maximum notice period of no more than two months**, a **mandatory maximum transitional period of 30 calendar days** (extendable, only where technically unfeasible, to no more than seven months), a **data-retrieval period of at least 30 days**, an exhaustive specification of exportable data, and full erasure on exit [1]. Third, **charges (Art. 29)**: from **11 January 2024 to 12 January 2027** providers may levy only **reduced, cost-based switching charges**, and **from 12 January 2027 they may impose no switching charges at all** [1][5].

For infrastructure services (IaaS), Art. 30(1) adds a duty to facilitate **functional equivalence** — re-establishing a "minimum level of functionality" on the destination service (Art. 2(37)) [1]. Other services must offer **free open interfaces** and align with **common specifications / harmonised standards** for interoperability once published (Arts. 30, 35) [1]. The single most important operational fact is the **12 January 2027 charge prohibition**: providers must have re-engineered pricing, contracts and exit tooling before that date [1][5].

# Key Takeaways

- **Chapter VI (Arts. 23–31)** requires providers of **data processing services** (cloud/edge IaaS, PaaS, SaaS) to enable effective **switching** to another provider, to on-premises infrastructure, or to parallel multi-provider use, and applies from **12 September 2025** [1]. *(Legal obligation — in force.)*
- **Art. 23** obliges providers to **not impose and to remove** "pre-commercial, commercial, technical, contractual and organisational obstacles" to switching, terminating contracts, and porting exportable data and digital assets [1]. *(Legal obligation.)*
- **Art. 29(1): from 12 January 2027, providers "shall not impose any switching charges"**; from **11 January 2024 until 12 January 2027** only **reduced** charges "not exceeding the costs … directly linked to the switching process" are permitted (Art. 29(2)–(3)) [1][5]. *(Legal obligation — phased; the headline date.)*
- **Art. 25** mandates a written contract with: a **maximum notice period ≤ two months**; a **mandatory maximum transitional period of 30 calendar days** (extendable to **≤ seven months** only where technically unfeasible, with notice within **14 working days**); a **data-retrieval period ≥ 30 days**; assistance, business continuity and security duties; and a full-erasure guarantee [1]. *(Legal obligation.)*
- **Functional equivalence (Art. 30(1) + Art. 2(37))** applies to **IaaS-type** services: the source provider must take all reasonable measures to help the customer re-establish a minimum level of functionality on the destination service [1]. *(Legal obligation.)*
- **Interoperability (Arts. 30, 34, 35)**: non-IaaS providers must offer **open interfaces free of charge**, support **in-parallel use**, and comply with **common specifications / harmonised standards** within 12 months of their publication in the central Union standards repository [1]. *(Legal obligation — standards-dependent.)*
- **Data egress charges** are a form of switching charge (Art. 2(35)–(36)) — so they too fall to zero on **12 January 2027**; separately, for **in-parallel use**, egress may be charged only at cost (Art. 34(2)) [1]. *(Legal obligation.)*
- **Exemptions (Art. 31)**: the charge, free-egress and IaaS functional-equivalence duties do **not** apply to genuinely **custom-built** services or to non-production **test/evaluation** environments [1]. *(Scope limit.)*
- **GDPR still governs personal data**: switching/porting personal data is not a new lawful basis; the GDPR prevails on conflict (Data Act Art. 1(5)) [1][2]. Switching duties also complement **DORA exit** and **NIS2** resilience expectations [3][4]. *(Legal obligation / cross-reference.)*

# Purpose

This document is the Tier 2 sub-topic deep dive on the Data Act's cloud-switching, portability and interoperability regime. It supports: (a) **legal mapping** of Chapter VI/VIII obligations onto a cloud provider or cloud customer; (b) **contract remediation** (the mandatory Art. 25 clauses and the Art. 29 charge phase-out); (c) **engineering** for export, functional equivalence and interoperability; and (d) **exit-programme design** — including a **switching runbook** and a **contract-clause checklist**. It details the switching material introduced in `data-act-foundations` and dovetails with `cloud-hosting-foundations`, `dora-foundations` (exit/substitutability) and `gdpr-transfers` (personal-data movement).

# Scope

**In scope:** Chapter VI (Arts. 23–31) switching obligations for data processing services; the definition of data processing service (Art. 2(8)) across **IaaS/PaaS/SaaS**; obstacle removal (Art. 23); scope of technical obligations (Art. 24); mandatory contract terms and the transition/notice/retrieval periods (Art. 25); the information obligation (Art. 26); the good-faith duty (Art. 27); contractual transparency on international access (Art. 28); the **phased withdrawal and 12 January 2027 prohibition** of switching charges (Art. 29); technical aspects and **functional equivalence** for IaaS (Art. 30); exemptions (Art. 31); Chapter VIII interoperability (Arts. 33–35, incl. in-parallel use and open interoperability specifications); the relationship to unfair-contract-term controls (Art. 13), GDPR, DORA and NIS2; a switching runbook; and a contract-clause checklist.

**Out of scope (covered elsewhere):**

- **IoT / connected-product** data sharing (Chapter II) → `data-act-iot-sharing` (planned); `data-act-foundations`.
- **B2G exceptional-need** access (Chapter V) → `data-act-b2g` (planned).
- **International-transfer** mechanics for personal data (GDPR Chapter V, Schrems II) → `gdpr-transfers`; the Data Act **Art. 32** non-personal-data safeguard is summarised in `data-act-foundations`.
- **DORA CTPP oversight and Art. 30 financial-sector exit clauses** → `dora-foundations`, `dora-tlpt`.
- **Smart-contract interoperability (Art. 36)** — noted only; deeper treatment deferred.

**Assumptions:** The reader has read `data-act-foundations` and `cloud-hosting-foundations`. Where switching moves **personal** data, the GDPR applies in parallel and prevails on conflict (Art. 1(5)) [1][2].

# Definitions

*Shared terms are in `GLOSSARY.md` (see "data processing service", "shared-responsibility model"). Switching-specific terms of art are defined here from the Regulation's Article 2.*

| Term | Definition | Source |
|------|------------|--------|
| Data processing service | A digital service enabling on-demand administration and broad remote access to a scalable, elastic pool of shareable computing resources of a centralised, distributed or highly distributed nature (Art. 2(8)) — i.e. cloud/edge IaaS, PaaS and SaaS. | [1] |
| Switching | The process whereby a customer changes from using one data processing service to using another of the **same service type**, or other service, offered by a different provider, or to on-premises ICT infrastructure (Art. 2(34)). | [1] |
| Same service type | A set of data processing services sharing the same primary objective, basic model and core functionality (Art. 2(33)); switching duties run between services of the same type. | [1] |
| Functional equivalence | Re-establishing, on the basis of the customer's exportable data and digital assets, a **minimum level of functionality** in the environment of a new data processing service of the same service type after switching, delivering a materially comparable outcome for shared features (Art. 2(37)). | [1] |
| Exportable data | Input and output data, including metadata, directly or indirectly generated or co-generated by the customer's use of the service, **excluding** provider/third-party IP-protected assets or trade secrets (Art. 2(38); for Arts. 23–31 and 35). | [1] |
| Digital assets | Elements in digital format the customer is entitled to use, including applications and metadata relating to service configuration, which the customer may port (Art. 2(39); referenced throughout Chapter VI). | [1] |
| Switching charges | Charges — other than standard service fees or early-termination penalties — imposed for the switching actions mandated by the Regulation, **including data egress charges** (Art. 2(36)). | [1] |
| Data egress charges | Data-transfer fees charged for extracting data through the network to a different provider or to on-premises infrastructure (Art. 2(35)); a sub-set of switching charges. | [1] |

# Background

Cloud computing concentrated compute, storage and platform services in a small number of hyperscale providers whose proprietary APIs, data formats and pricing created **lock-in**: even where a customer wished to leave, the technical effort and — above all — the **data egress fees** made switching uneconomic. The European Strategy for Data identified this as a barrier to a competitive EU cloud market and to the free flow of data. Earlier soft-law responses — notably the industry **SWIPO** Codes of Conduct (Switching and Porting) developed with the Commission under the Free Flow of Non-Personal Data Regulation — were voluntary and unevenly adopted [10].

The Data Act converts that policy goal into **binding law**. Chapter VI makes switching a customer **right** and an obstacle-removal, contract and pricing **obligation** on providers, culminating in the abolition of switching charges; Chapter VIII adds interoperability duties and a mandate for open specifications and harmonised standards so that portability becomes technically real, not merely contractual [1][6]. The Commission frames the rules as directly targeting vendor lock-in and levelling the field for smaller EU providers [5][6].

# Legal Framework

Chapter VI applies to **any data and services processed by providers of data processing services** (Art. 1) and, per Art. 50, applies from **12 September 2025**; the Art. 29 charge prohibition bites on **12 January 2027** [1]. The obligations attach to the **source provider** (Art. 24). The structure:

- **Art. 23 — Removing obstacles to effective switching:** providers "shall not impose and shall remove pre-commercial, commercial, technical, contractual and organisational obstacles" to termination, contracting with a new provider, porting exportable data/digital assets (including after a free-tier offering) and parallel use [1]. *(Legal obligation.)*
- **Art. 24 — Scope:** the switching responsibilities apply only to the services, contracts or commercial practices of the **source** provider [1].
- **Art. 25 — Contractual terms:** the mandatory written-contract terms (notice ≤ two months; transitional period 30 days, extendable ≤ seven months; retrieval ≥ 30 days; assistance, continuity, security; exportable-data specification; erasure) [1]. *(Legal obligation.)*
- **Art. 26 — Information obligation:** provide switching/porting procedures, methods, formats and known limitations, plus an up-to-date online register of data structures, formats and standards [1]. *(Legal obligation.)*
- **Art. 27 — Good faith:** all parties, including the destination provider, must cooperate in good faith to make switching effective [1]. *(Legal obligation.)*
- **Art. 28 — Contractual transparency on international access:** publish information on the jurisdiction of the ICT infrastructure and measures against unlawful international governmental access [1]. *(Legal obligation.)*
- **Art. 29 — Gradual withdrawal of switching charges:** reduced (cost-based) charges until 12 Jan 2027; **no switching charges from 12 Jan 2027**; pre-contractual information; Commission monitoring by delegated act [1][5]. *(Legal obligation — phased.)*
- **Art. 30 — Technical aspects:** IaaS **functional equivalence** (30(1)); free **open interfaces** (30(2)); **common-specification/harmonised-standard** compatibility within 12 months (30(3)); export in a structured, commonly used, machine-readable format where no standard exists (30(5)); no duty to develop new tech or disclose IP/trade secrets (30(6)) [1]. *(Legal obligation.)*
- **Art. 31 — Specific regime:** exemptions for genuinely custom-built services and non-production test/evaluation services [1].
- **Chapter VIII (Arts. 33–36) — Interoperability:** essential requirements (Art. 33); in-parallel use (Art. 34); open interoperability specifications and harmonised standards for data processing services (Art. 35); smart contracts (Art. 36) [1]. *(Legal obligation.)*

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 2(8), (33)–(39) | Definitions: data processing service, same service type, switching, functional equivalence, exportable data, digital assets, switching/egress charges. | [1] |
| Art. 23 | Remove pre-commercial, commercial, technical, contractual and organisational obstacles to switching, termination, porting and parallel use. | [1] |
| Art. 24 | Technical obligations bind the **source** provider's services, contracts and practices only. | [1] |
| Art. 25(2)(a) | Mandatory maximum **transitional period of 30 calendar days** (with assistance, continuity, risk information and security duties). | [1] |
| Art. 25(2)(d) | **Maximum notice period** to initiate switching **shall not exceed two months**. | [1] |
| Art. 25(2)(e)–(f) | Exhaustive specification of exportable data; permitted trade-secret exemptions that must not impede switching. | [1] |
| Art. 25(2)(g)–(h) | **Data-retrieval period of at least 30 calendar days**; guaranteed full erasure after retrieval. | [1] |
| Art. 25(4) | Where 30 days is technically unfeasible: notify within **14 working days**, justify, and allow an alternative period **not exceeding seven months**. | [1] |
| Art. 26 | Information obligation (procedures, formats, limitations) and up-to-date online register. | [1] |
| Art. 27 | Good-faith cooperation duty on all parties, including the destination provider. | [1] |
| Art. 28 | Transparency on international governmental access and infrastructure jurisdiction. | [1] |
| Art. 29(1)–(3) | **From 12 Jan 2027: no switching charges.** Until then: reduced, cost-based charges only. | [1][5] |
| Art. 29(4)–(7) | Pre-contractual fee information; publication; Commission monitoring via delegated act. | [1] |
| Art. 30(1) | **Functional equivalence** duty for IaaS-type infrastructure services. | [1] |
| Art. 30(2)–(5) | Free open interfaces; harmonised-standard compatibility within 12 months; machine-readable export fallback. | [1] |
| Art. 31 | Exemptions for custom-built and non-production test/evaluation services. | [1] |
| Arts. 33–35 | Interoperability essential requirements; in-parallel use (egress at cost only); open interoperability specifications/harmonised standards; central Union standards repository (Art. 35(8)). | [1] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 80 area | Rationale for removing switching obstacles and lock-in in data-processing services. | [1] |
| Recital 91 area | Data egress charges as a barrier; the case for withdrawing switching charges over a transition period. | [1] |
| Recital 93 area | Functional equivalence for infrastructure services and the limits of "reasonable measures". | [1] |
| Recital 99 area | Interoperability, open specifications and harmonised standards for data-processing services. | [1] |

*Recitals are not binding but aid construction of the operative articles; they are cited here as interpretive aids only.*

## Relevant Case Law

**Not Applicable.** The Data Act is a new instrument; Chapter VI/VIII applied only from 12 September 2025, and there is no CJEU or national case law interpreting the switching or interoperability provisions at this document's date. Interpretive weight rests on the Regulation's text, its recitals and Commission guidance [1][5][6]. This section will be revisited once judgments or enforcement decisions emerge.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** presents the switching rules as targeting **vendor lock-in**: providers must remove commercial, technical and contractual obstacles, support export and interoperability, and **withdraw switching charges over a transition period** ending with the 12 January 2027 prohibition [5][6]. *(Regulatory interpretation.)*
- On **charges**, the Commission distinguishes ordinary **standard service fees** and **early-termination penalties** (which remain lawful) from **switching charges including data egress fees** (which reduce to cost and then to zero) — a distinction that mirrors the Art. 2(35)–(36) definitions [1][5]. *(Regulatory interpretation.)*
- The Commission's **Data Act FAQ** stresses that switching is a **customer right** exercisable without disproportionate effort, and that providers must give clear pre-contractual information so customers can compare exit terms [7]. *(Regulatory interpretation.)*
- On **interoperability**, the Commission and ENISA foresee **open interoperability specifications and harmonised standards** referenced in a **central Union standards repository** (Art. 35(8)); until those are published, the machine-readable export fallback (Art. 30(5)) governs [1][6]. *(Regulatory interpretation.)*
- For **financial-sector** customers, the **ESAs** designated the first **critical ICT third-party providers (CTPPs)** on 18 November 2025; DORA's **exit/substitutability** expectations run alongside Data Act switching, and a robust Data Act exit capability helps satisfy both [3][8]. *(Regulatory interpretation — assess role.)*

# Technical Considerations

- **Export is an engineering deliverable, not a clause.** Providers must expose exportable data (input/output data and metadata, Art. 2(38)) and digital assets in a **structured, commonly used, machine-readable format** where no common specification exists (Art. 30(5)), and maintain an **online register** of data structures, formats and standards (Art. 26(b)) [1]. *(Legal obligation, met via controls.)*
- **Functional equivalence is bounded.** For IaaS (Art. 30(1)), the source provider must take "all reasonable measures" to help the customer re-establish a **minimum level of functionality** on the destination service — providing capabilities, documentation, technical support and tools — but need not develop new technology or hand over IP/trade secrets (Art. 30(6)); PaaS/SaaS providers instead owe **free open interfaces** (Art. 30(2)) [1]. Standards such as **ISO/IEC 19941** (cloud interoperability and portability) give a vocabulary for scoping equivalence [9]. *(Legal obligation + best practice.)*
- **Transition-period orchestration.** The **30-day** mandatory transition (Art. 25(2)(a)) demands automation: pre-staged export pipelines, dual-run capability, integrity verification and a rehearsed cutover. The **≤ seven-month** extension is available **only** where 30 days is technically unfeasible, with justification notified within **14 working days** (Art. 25(4)) — it is an exception, not a default [1]. *(Legal obligation.)*
- **Security during switching.** Art. 25(2)(a)(iv) requires a high level of security throughout the transfer and retrieval, so encryption in transit/at rest, key handover procedures and access controls must extend across both source and destination environments [1]. Align with **ISO/IEC 27017** cloud controls and CSA STAR assurance [11][12]. *(Legal obligation, met via controls.)*
- **Parallel / multi-cloud use.** Art. 23 and Art. 34 protect **in-parallel use**; interoperability must not be blocked, and egress for parallel use may be charged **only at cost** (Art. 34(2)) — distinct from the switching-charge phase-out [1]. *(Legal obligation.)*
- **Standards adoption lead time.** Once common specifications/harmonised standards are published in the central Union standards repository (Art. 35(8)), non-IaaS providers have **12 months** to achieve compatibility (Art. 30(3)) [1]. Track the repository and align data/portability formats early using **ISO/IEC 19941** and **SWIPO** artefacts [9][10]. *(Best practice.)*

# Hosting Considerations

- **Cloud/edge providers are directly in scope.** Any provider of a "data processing service" (Art. 2(8)) — IaaS, PaaS or SaaS — owes the Chapter VI duties as a **source provider** (Art. 24) and must implement obstacle removal, mandatory contract terms, the information/register duty and the charge phase-out [1][5]. *(Legal obligation.)*
- **Repricing before 12 January 2027.** Providers must re-model pricing so that **no switching charges (including data egress)** are levied from that date; until then, any switching charge must be **cost-based** and pre-disclosed (Art. 29(2)–(4)) [1][5]. Standard service fees and early-termination penalties may continue but must not be re-badged switching charges [1]. *(Legal obligation — phased.)*
- **Customers gain leverage.** Cloud **customers** should use the mandatory Art. 25 terms (notice ≤ two months, 30-day transition, ≥ 30-day retrieval, erasure) as a baseline in procurement and renegotiation, and demand the Art. 26 register and Art. 28 international-access transparency [1]. *(Best practice.)*
- **Interaction with DORA and NIS2.** For hosting serving **financial entities**, DORA's Art. 30 exit provisions and CTPP oversight run in parallel; a Data Act-compliant exit capability is reusable evidence for DORA substitutability [3][8]. For **NIS2** digital-infrastructure entities, switching/portability supports availability and business-continuity duties (Art. 21) [4]. *(Legal obligation — assess role.)*
- **Unfair-term control.** Data Act **Art. 13** voids unilaterally imposed **unfair contractual terms** on enterprises; exit, egress and assistance clauses that undermine the switching right may be unenforceable, independent of the Art. 29 timeline [1]. *(Legal obligation.)*

# Game Hosting Considerations

- **Studios benefit as customers.** Game studios hosting backends, matchmaking, telemetry and live-ops on cloud/edge "data processing services" are **customers** entitled to the switching right — a lever against lock-in for latency-sensitive, high-egress workloads where egress fees have historically been punitive [1][5]. *(Legal obligation — assess role.)*
- **Managed-hosting resellers owe the duties.** A studio or platform that **resells** managed hosting or a backend-as-a-service to third parties may itself be a **source provider** of a data processing service, owing the Chapter VI obligations to its customers [1]. *(Legal obligation — assess role.)*
- **Player personal data stays under the GDPR.** Porting player accounts, saves or telemetry that are personal data engages GDPR portability (Art. 20) and transfer rules in parallel; the Data Act adds switching/export expectations but is not a lawful basis, and the GDPR prevails on conflict (Art. 1(5)) [1][2]. Children's-data defaults heighten the duty (see `uk-childrens-code`). *(Legal obligation.)*
- **Test/dev environments may be exempt.** Non-production test/evaluation environments and genuinely bespoke, non-catalogue custom builds may fall under the Art. 31 exemptions from the charge and IaaS functional-equivalence duties — assess per environment [1]. *(Scope limit.)*

# AI Considerations

- **Model and pipeline portability.** AI training/inference workloads on cloud "data processing services" are within Chapter VI; **exportable data** (Art. 2(38)) covers input/output data and metadata generated by the customer's use, so datasets, feature stores and job artefacts should be portable, subject to the provider IP/trade-secret carve-out (Art. 30(6)) [1]. *(Legal obligation, bounded.)*
- **Functional equivalence rarely covers models.** Proprietary managed-AI/model-as-a-service features are often IP-protected and need not be re-created; functional equivalence targets a **minimum level of functionality** for shared features (Art. 2(37)), so AI customers should avoid deep coupling to provider-specific model APIs and keep training data and pipeline definitions portable [1]. *(Best practice.)*
- **Egress economics for AI.** Large training corpora make **data egress charges** a material lock-in factor; the Art. 29 phase-out to zero by 12 January 2027 materially changes multi-cloud AI economics [1][5]. *(Legal obligation — phased.)*
- **Parallel use for AI.** Running inference across providers (Art. 34) is protected, with egress chargeable only at cost — supporting multi-vendor AI resilience [1]. *(Legal obligation.)*
- **AI Act overlap.** Switching does not displace **AI Act** obligations (data governance, logging) or the **GDPR** for personal data; see `ai-act-foundations`, `ai-act-high-risk`. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** (a cited law requires the outcome) / **BEST PRACTICE** (standards/industry consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

## For providers (source providers of data processing services)

1. **Inventory in-scope services** — classify each offering as a data processing service (Art. 2(8)) and by type/model (IaaS/PaaS/SaaS); flag Art. 31 exemption candidates. *(OBLIGATION to scope.)* [1]
2. **Remove obstacles (Art. 23)** — audit and eliminate pre-commercial, commercial, technical, contractual and organisational barriers to termination, re-contracting, porting and parallel use. *(OBLIGATION.)* [1]
3. **Re-paper contracts (Art. 25)** — insert the mandatory clauses (see the contract-clause checklist below); make the contract available pre-signature in a storable form. *(OBLIGATION.)* [1]
4. **Publish switching information and a register (Art. 26)** — procedures, methods, formats, known limitations, and an up-to-date online register of data structures/formats/standards. *(OBLIGATION.)* [1]
5. **Re-price to zero switching charges by 12 January 2027 (Art. 29)** — until then charge only cost-based reduced switching/egress fees, disclosed pre-contract and published; separate genuine standard fees and early-termination penalties. *(OBLIGATION — phased.)* [1][5]
6. **Build export and (for IaaS) functional-equivalence tooling (Art. 30)** — machine-readable export, free open interfaces, documentation, technical support; track the central Union standards repository for the 12-month compatibility clock. *(OBLIGATION.)* [1][9]
7. **Publish international-access transparency (Art. 28)** — jurisdiction of infrastructure and safeguards against unlawful governmental access. *(OBLIGATION.)* [1]

## For customers (cloud users)

1. **Demand Art. 25 baselines** — notice ≤ two months, 30-day transition, ≥ 30-day retrieval, assistance/continuity/security, and full erasure on exit. *(OBLIGATION on the provider; leverage for you.)* [1]
2. **Maintain a portability posture** — prefer open formats and interfaces; avoid proprietary coupling; keep an exportable data map. *(BEST PRACTICE.)* [9][10]
3. **Rehearse the exit** — run a switching drill against the runbook below at least annually; reconcile with DORA exit testing where in finance. *(BEST PRACTICE; obligation elements under DORA.)* [3]

## Switching runbook (indicative, provider-agnostic)

1. **Trigger & notice** — issue the switching request; provider's maximum notice period (≤ two months) starts (Art. 25(2)(d)). *(OBLIGATION.)* [1]
2. **Scope & register** — obtain the exportable-data specification and online register (Art. 25(2)(e), Art. 26); identify digital assets and any trade-secret exemptions. *(OBLIGATION.)* [1]
3. **Feasibility & timing** — confirm the **30-day** transition; if the provider claims unfeasibility, require written justification within **14 working days** and an alternative period **≤ seven months** (Art. 25(4)). *(OBLIGATION.)* [1]
4. **Prepare destination** — provision the same-service-type destination; for IaaS, use functional-equivalence capabilities/tools (Art. 30(1)); for PaaS/SaaS, integrate via open interfaces (Art. 30(2)). *(OBLIGATION on source; BEST PRACTICE for you.)* [1][9]
5. **Transfer securely** — export in a machine-readable format (Art. 30(5)); maintain security throughout (Art. 25(2)(a)(iv)); verify integrity; run in parallel where feasible (Art. 34). *(OBLIGATION.)* [1]
6. **Cut over & assure** — validate functional equivalence / service parity; maintain business continuity (Art. 25(2)(a)(ii)). *(OBLIGATION on source.)* [1]
7. **Retrieve & erase** — use the **≥ 30-day** retrieval window (Art. 25(2)(g)); confirm full erasure of exportable data/digital assets (Art. 25(2)(h)); document completion and contract termination. *(OBLIGATION.)* [1]
8. **Verify charges** — confirm no switching/egress charge is levied on/after 12 January 2027, or only cost-based reduced charges before it (Art. 29). *(OBLIGATION.)* [1][5]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Switching or data egress charges persisting on/after 12 Jan 2027 | Medium | High | Art. 29(1) [1][5] | Re-price to zero; remove egress fees; audit invoices | Low |
| R2 | Reduced charges above cost before 12 Jan 2027 | Medium | Medium | Art. 29(2)–(3) [1] | Cost-model charges; pre-contract disclosure; publish | Low |
| R3 | Contracts lacking mandatory Art. 25 terms (notice/transition/retrieval/erasure) | Medium | High | Art. 25 [1] | Contract remediation to the clause checklist | Low |
| R4 | Transition exceeding 30 days without valid technical-unfeasibility justification | Medium | High | Art. 25(2)(a), (4) [1] | Automate export; justify + notify in 14 working days; cap ≤ 7 months | Medium |
| R5 | Technical obstacles / no machine-readable export or open interfaces | Medium | High | Arts. 23, 30 [1] | Build export tooling, open interfaces, register | Medium |
| R6 | IaaS functional equivalence not facilitated | Medium | High | Art. 30(1); Art. 2(37) [1] | Capabilities, docs, tools; ISO/IEC 19941 scoping | Medium |
| R7 | Missing information/register or Art. 28 transparency | Low | Medium | Arts. 26, 28 [1] | Publish procedures, register and access transparency | Low |
| R8 | Unfair exit/egress terms imposed on SME customers | Medium | Medium | Art. 13 [1] | Fair-term review; remove unilateral unfair clauses | Low |
| R9 | Treating a Data Act switch of personal data as a GDPR lawful basis | Medium | High | Art. 1(5) [1][2] | Separate lawful-basis analysis; transfer safeguards | Low |
| R10 | Data Act exit misaligned with DORA substitutability (finance) | Medium | High | DORA Art. 30 [3][8] | Unify exit testing; reuse switching runbook | Medium |

# Implementation Roadmap

- **Phase 0 — Scoping:** Classify data processing services (Art. 2(8)) and roles (source provider / customer); identify Art. 31 exemptions. *Effort:* Medium.
- **Phase 1 — Obstacle removal & contracts:** Remove Art. 23 obstacles; insert mandatory Art. 25 terms; publish Art. 26 information/register and Art. 28 transparency (all applicable from 12 Sep 2025). *Effort:* High.
- **Phase 2 — Export & interoperability engineering:** Machine-readable export (Art. 30(5)); IaaS functional-equivalence tooling (Art. 30(1)); free open interfaces (Art. 30(2)); align to ISO/IEC 19941 / SWIPO. *Effort:* High.
- **Phase 3 — Charge withdrawal:** Move to cost-based reduced charges now; **eliminate all switching/egress charges by 12 January 2027** (Art. 29). *Effort:* Medium.
- **Phase 4 — Standards compatibility:** On publication of common specifications/harmonised standards in the central Union standards repository, achieve compatibility within **12 months** (Art. 30(3), Art. 35(8)). *Effort:* Medium (standards-dependent).
- **Phase 5 — Assurance & drills:** Rehearse the switching runbook; reconcile with DORA exit testing; maintain evidence. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Switching duties unmapped; proprietary formats; egress fees unmanaged. | No service classification; no exit clauses. |
| 2 | Managed | Services classified; Art. 25 terms drafted; charge phase-out planned. | Contract review begun; charge model started. |
| 3 | Defined | Mandatory clauses live; information/register published; machine-readable export available. | Art. 25/26/28 in place; export tooling. |
| 4 | Quantitatively Managed | Functional equivalence / open interfaces tested; switching drills; charges cost-based → zero-ready. | Rehearsed exits; egress-to-zero plan; metrics. |
| 5 | Optimising | Interoperability by design; standards-compatible; unified Data Act/DORA/NIS2 exit governance. | Standards-repository alignment; integrated exit programme. |

# Audit Questions

1. Are all in-scope data processing services classified (Art. 2(8)), with source-provider/customer roles and Art. 31 exemptions identified? *(Arts. 2, 24, 31 [1].)*
2. Have pre-commercial, commercial, technical, contractual and organisational obstacles to switching been removed? *(Art. 23 [1].)*
3. Do contracts contain the mandatory Art. 25 terms — notice ≤ two months, 30-day transition, ≥ 30-day retrieval, assistance/continuity/security, exportable-data specification and erasure? *(Art. 25 [1].)*
4. Is switching/porting information and an up-to-date online register published, plus Art. 28 international-access transparency? *(Arts. 26, 28 [1].)*
5. Are switching charges (including data egress) cost-based now and eliminated by 12 January 2027, with pre-contractual disclosure? *(Art. 29 [1][5].)*
6. For IaaS, how is functional equivalence facilitated; for PaaS/SaaS, are free open interfaces provided? *(Art. 30(1)–(2); Art. 2(37) [1].)*
7. Is machine-readable export available where no common specification exists, and is the 12-month standards clock tracked? *(Art. 30(3), (5); Art. 35(8) [1].)*
8. Where personal data is switched, is a GDPR lawful basis and transfer analysis run separately? *(Art. 1(5) [1][2].)*
9. For financial-sector hosting, is the Data Act exit capability reconciled with DORA exit/substitutability? *(DORA Art. 30 [3][8].)*

# Implementation Checklist

**Contract-clause checklist (Art. 25 mandatory terms):**

- [ ] Written contract, available pre-signature in a storable/reproducible form (Art. 25(1)).
- [ ] Switch/port right to another same-type service or to on-premises, within a **30-day** mandatory maximum transition (Art. 25(2)(a)).
- [ ] Source-provider duties during transition: reasonable assistance, business continuity, risk information, security maintained (Art. 25(2)(a)(i)–(iv)).
- [ ] Support for the customer's **exit strategy** and provision of all relevant information (Art. 25(2)(b)).
- [ ] Termination triggers defined (successful switch, or erasure at end of notice) (Art. 25(2)(c)).
- [ ] **Maximum notice period ≤ two months** to initiate switching (Art. 25(2)(d)).
- [ ] Exhaustive specification of portable **exportable data** and digital assets (Art. 25(2)(e)).
- [ ] Any trade-secret exemptions specified and **not** impeding switching (Art. 25(2)(f)).
- [ ] **Data-retrieval period ≥ 30 calendar days** post-transition (Art. 25(2)(g)).
- [ ] Guaranteed **full erasure** of exportable data/digital assets after retrieval (Art. 25(2)(h)).
- [ ] Switching charges clause consistent with Art. 29 (cost-based now; **zero from 12 Jan 2027**) (Art. 25(2)(i)).
- [ ] Technical-unfeasibility handling: notice within **14 working days**, justification, alternative ≤ **seven months** (Art. 25(4)).

**Wider programme checklist:**

- [ ] Data processing services classified (Art. 2(8)); roles and Art. 31 exemptions determined.
- [ ] Art. 23 obstacles removed (pre-commercial/commercial/technical/contractual/organisational).
- [ ] Art. 26 switching information and online register published.
- [ ] Art. 28 international-access transparency published.
- [ ] Art. 29 charges: reduced/cost-based now; **all switching and egress charges eliminated by 12 January 2027**.
- [ ] Art. 30 export tooling (machine-readable), IaaS functional equivalence and/or free open interfaces built and tested.
- [ ] Central Union standards repository monitored; 12-month compatibility plan (Art. 30(3), Art. 35(8)).
- [ ] Switching runbook rehearsed; DORA exit alignment where in finance; GDPR lawful-basis/transfer analysis for personal data.

# References

*All links verified live on 2026-07-11 (`sources_verified`). Article text quoted above was taken from the EUR-Lex consolidated/OJ text of Regulation (EU) 2023/2854 on 2026-07-11.*

## Primary Sources

- [1] **Regulation (EU) 2023/2854 (Data Act)** — harmonised rules on fair access to and use of data; **Chapter VI (Arts. 23–31)** switching, **Chapter VIII (Arts. 33–36)** interoperability, and Art. 2 definitions. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2023/2854/oj
- [2] **Regulation (EU) 2016/679 (GDPR)** — parallel application to personal data switched/ported under the Data Act; prevails on conflict (Data Act Art. 1(5)). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [3] **Regulation (EU) 2022/2554 (DORA)** — ICT third-party risk and exit/substitutability (Art. 30) for financial-entity cloud arrangements, running alongside Data Act switching. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj
- [4] **Directive (EU) 2022/2555 (NIS2)** — availability/business-continuity risk-management measures (Art. 21) for digital-infrastructure entities, supported by portability. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj

## Regulatory Guidance

- [5] **Switching cloud service providers / cloud switching** (Data Act Chapter VI; removal of obstacles and withdrawal of switching charges). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cloud-switching
- [6] **Data Act (policy page)** (objectives, cloud switching and interoperability). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/data-act
- [7] **Data Act explained (FAQ).** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/faqs/data-act-explained
- [8] **European Supervisory Authorities designate critical ICT third-party providers under DORA** (first CTPP list, 18 November 2025) — DORA exit/oversight context. EIOPA/EBA/ESMA. https://www.eiopa.europa.eu/european-supervisory-authorities-designate-critical-ict-third-party-providers-under-digital-2025-11-18_en

## Standards

- [9] **ISO/IEC 19941:2017** — Information technology — Cloud computing — Interoperability and portability (terminology and concepts for scoping portability and functional equivalence). ISO. https://www.iso.org/standard/66639.html
- [10] **SWIPO — Switching Cloud Providers and Porting Data Codes of Conduct** (industry codes developed with the European Commission; precursor and complement to Data Act switching). SWIPO AISBL. https://swipo.eu/
- [11] **ISO/IEC 27017:2015** — Code of practice for information security controls for cloud services (security during switching/transfer). ISO. https://www.iso.org/standard/43757.html
- [12] **CSA STAR (Security, Trust, Assurance & Risk)** — cloud-assurance programme and public registry (portability/interoperability evidence). Cloud Security Alliance. https://cloudsecurityalliance.org/star

## Academic Sources

**Not Applicable.** This deep dive relies on the primary Regulation, Commission/ESA guidance and international standards. Peer-reviewed analysis of Data Act cloud-switching and lock-in economics will be added if it becomes load-bearing on a specific contested point.

# Further Reading

*Non-authoritative; provided for orientation only.*

- Data Act (European Union) — overview. Wikipedia. https://en.wikipedia.org/wiki/Data_Act_(European_Union)
- Regulation (EU) 2018/1807 on the free flow of non-personal data (context for SWIPO and cloud portability). EUR-Lex. https://eur-lex.europa.eu/eli/reg/2018/1807/oj

# Related Documents

- `data-act-foundations` — **parent**; Chapter-by-chapter overview and application timeline (this document details its Chapter VI/VIII switching material).
- `cloud-hosting-foundations` — **sibling**; responsibility matrix and the cross-cutting cloud regime (GDPR/NIS2/DORA/Data Act).
- `dora-foundations` — ICT third-party exit/substitutability and CTPP oversight for financial-entity cloud.
- `nis2-foundations` — availability/business-continuity duties for digital-infrastructure entities.
- `gdpr-foundations` / `gdpr-transfers` — personal-data portability (Art. 20) and Chapter V transfers when switching moves personal data.
- `data-act-iot-sharing` — Chapter II connected-product data sharing (planned).
- `data-act-b2g` — Chapter V business-to-government access (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; deep dive on Data Act Chapter VI (switching) and Chapter VIII (interoperability). Article text live-verified against the EUR-Lex text of Regulation (EU) 2023/2854: Art. 29 charge prohibition from **12 January 2027** (reduced cost-based charges 11 Jan 2024 – 12 Jan 2027); Art. 25 mandatory terms (notice ≤ two months; 30-day transition, extendable ≤ seven months with 14-working-day notice; ≥ 30-day retrieval; erasure); Art. 23 obstacle removal; Art. 30 functional equivalence / open interfaces; Art. 31 exemptions; Arts. 34–35 interoperability; and Art. 2(33)–(38) definitions. All 12 references returned HTTP 200 on 2026-07-11. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved via autonomous backlog loop (Cluster A); passed full QA suite; frozen in release 0.15.0. | Human reviewer (loop-authorised) |
