---
id: cloud-hosting-foundations
title: "Cloud Hosting: Compliance Foundations"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU, UK]
topic: Cloud Hosting
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
related: [gdpr-foundations, privacy-engineering-foundations, cybersecurity-foundations, nis2-foundations, dora-foundations, data-act-foundations]
tags: [cloud-hosting, shared-responsibility, article-28, article-32, international-transfers, schrems-ii, nis2, dora, ctpp, data-act, cloud-switching, iso-27017, iso-27018, csa-star, eucs, cybersecurity-act]
legal_basis: Cross-cutting — Regulation (EU) 2016/679 (GDPR) Arts. 28, 32 & Chapter V; Directive (EU) 2022/2555 (NIS2); Regulation (EU) 2022/2554 (DORA); Regulation (EU) 2023/2854 (Data Act); Regulation (EU) 2019/881 (Cybersecurity Act)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | cloud-hosting-foundations |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a **cross-cutting synthesis** drawing together instruments treated in depth elsewhere (`gdpr-foundations`, `nis2-foundations`, `dora-foundations`, `data-act-foundations`, `privacy-engineering-foundations`, `cybersecurity-foundations`); the primary obligations live in those documents. Two areas are **moving targets** and are flagged throughout: the **EU Cloud Services certification scheme (EUCS)**, which at this document's date **remains a candidate/draft scheme and has not been adopted** as an implementing act under the Cybersecurity Act [7][8][9]; and the **Data Act cloud-switching timeline**, whose withdrawal of switching charges bites on **12 January 2027** [4][10]. Confirm both before relying on them.

# Executive Summary

**Cloud hosting** — the provision of on-demand compute, storage and platform/software services (IaaS, PaaS, SaaS) — sits at the intersection of nearly every EU/UK digital-compliance regime. This document is a **cross-cutting synthesis** of how cloud and infrastructure hosting must comply, pulling together obligations that the topic-specific foundations documents establish in depth. It does **not** restate those regimes in full; it maps them onto the hosting provider and the cloud customer and sets out a concrete **responsibility matrix**.

Five threads dominate. First, the **shared-responsibility model**: providers secure the platform "of" the cloud, customers secure what they put "in" it — but responsibility for a control is not the same as **accountability**, which the cloud customer (typically the data **controller**) cannot outsource [1]. Second, **data-protection roles**: a hosting provider is usually a **processor**, requiring a GDPR **Article 28** data-processing agreement (DPA) and **Article 32** security of processing; where hosting entails storage or access from outside the EEA, **Chapter V / Schrems II** transfer rules apply [1][6][12]. Third, **sector security law**: cloud, data-centre, CDN and managed-service providers are named **"digital infrastructure" entities** under **NIS2** [2], and a cloud provider serving financial entities is an **ICT third-party provider** under **DORA** that may be designated a **critical ICT third-party provider (CTPP)** under direct ESA oversight — the first such designations were made on 18 November 2025 [3][11]. Fourth, the **Data Act** makes cloud "data processing services" directly subject to **switching, portability and interoperability** duties, with switching charges prohibited from **12 January 2027** [4][10]. Fifth, **security standards and certification**: ISO/IEC 27001 with the cloud extensions **27017** (cloud security) and **27018** (cloud PII), plus **CSA STAR**, are the recognised assurance vehicles, while the **EUCS** remains **not yet adopted** [13][14][15][16][18][7][8].

The single most important operational message: **map every control to an owner** (provider vs. customer), keep GDPR **accountability** with the customer, and treat certifications as **evidence, not a compliance guarantee**.

# Key Takeaways

- The **shared-responsibility model** allocates security controls between provider and customer, but **GDPR accountability stays with the controller** — usually the cloud customer — and cannot be contracted away [1]. *(Best practice; accountability is a legal obligation under GDPR Art. 5(2).)*
- A hosting provider is typically a **processor**; the customer must put an **Article 28 DPA** in place with the mandatory terms (sub-processor controls, security, assistance, deletion/return) [1]. *(Legal obligation.)*
- **Article 32** requires security of processing appropriate to the risk (encryption, pseudonymisation, CIA + resilience, effectiveness testing) — met in cloud through the provider's platform controls **and** the customer's configuration [1]. *(Legal obligation.)*
- Where hosting stores or exposes personal data outside the EEA, **Chapter V** transfer mechanisms and the **Schrems II** requirement to assess third-country government-access risk and add supplementary measures apply [1][6][12]. *(Legal obligation / regulatory interpretation.)*
- **NIS2** names **cloud computing, data-centre, CDN and managed/managed-security service providers** as "digital infrastructure" / "ICT service management" entities — squarely in scope as essential or important entities, with several required to register with ENISA [2]. *(Legal obligation.)*
- **DORA** treats a cloud provider serving financial entities as an **ICT third-party provider**; if systemically important it may be designated a **CTPP** under direct ESA oversight (first designations 18 Nov 2025), and financial-entity contracts must carry the **Art. 30** key provisions [3][11]. *(Legal obligation — assess role.)*
- The **Data Act** subjects cloud "data processing services" to **switching, export and interoperability** duties; **switching charges are prohibited from 12 January 2027** [4][10]. *(Legal obligation — phased.)*
- **ISO/IEC 27017** (cloud security controls) and **ISO/IEC 27018** (PII in public cloud) extend ISO/IEC 27001/27002 for cloud; **CSA STAR** provides a cloud-specific assurance registry [13][14][15][16][18]. *(Best practice / standards.)*
- The **EUCS** cloud certification scheme is, at this document's date, **still a candidate/draft** under the Cybersecurity Act (only the **EUCC** products scheme has been adopted); do not assume EUCS certification is available [5][7][8][9]. *(Verified status — not asserted.)*

# Purpose

This document is the **Tier 4 cross-cutting entry point** for cloud/infrastructure hosting compliance. It supports: (a) allocating obligations across the provider/customer boundary (the responsibility matrix); (b) triaging which regimes apply to a given hosting arrangement (GDPR processor/transfer duties, NIS2, DORA, Data Act); and (c) choosing assurance vehicles (ISO/IEC 27001/27017/27018, CSA STAR, and — when adopted — EUCS). It is deliberately a **synthesis**: each underlying regime is treated in depth in its own document, cross-referenced throughout.

# Scope

**In scope:** The shared-responsibility model and a provider/customer **responsibility matrix**; GDPR **controller/processor** roles for hosting, **Article 28** DPAs and **Article 32** security at a foundational, cross-referencing level; **international transfers** for cloud (**Chapter V / Schrems II**) at a foundational level; **NIS2** obligations for cloud/infrastructure providers; **DORA** for cloud serving financial entities including **CTPP** oversight; the **Data Act** cloud-switching, portability and interoperability rules including the phase-out of switching charges; security standards (**ISO/IEC 27001, 27017, 27018, 27701**, **CSA STAR**); and the status of the **EUCS** under the Cybersecurity Act.

**Out of scope (spun off to the research backlog):**
- **Transfer-mechanism mechanics** — SCC module selection, Transfer Impact Assessments, supplementary measures, the UK IDTA/Addendum → `international-transfers` (planned).
- **EUCS in detail** — assurance levels (Basic/Substantial/High), sovereignty requirements and the adoption debate → `eucs-deep-dive` (planned).
- **Provider-specific shared-responsibility models** — AWS/Azure/GCP control matrices and service-by-service splits → `cloud-provider-responsibility-matrices` (planned).
- **Data Act cloud-switching mechanics** → `data-act-cloud-switching` (planned).
- **DORA CTPP oversight mechanics and Art. 30 contract detail** → `dora-oversight-framework`, `dora-third-party-contracts` (planned).

**Assumptions:** The reader has read `gdpr-foundations` (controller/processor, Chapter V), and can consult `nis2-foundations`, `dora-foundations`, `data-act-foundations`, `privacy-engineering-foundations` and `cybersecurity-foundations`. Where personal data is processed, the GDPR applies in parallel to every regime discussed here.

# Definitions

*Shared terms — controller, processor, ISMS, CIA triad, essential/important entity, CTPP, data processing service — are defined in `GLOSSARY.md`. Only cloud-hosting-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Shared-responsibility model | The division of security and compliance controls between the cloud provider (responsible for security "of" the cloud — hardware, virtualisation, physical facilities) and the customer (responsible for security "in" the cloud — data, identity, configuration, application). The split shifts across IaaS/PaaS/SaaS. | [1][13] |
| IaaS / PaaS / SaaS | Cloud service models: Infrastructure- (compute/storage/network), Platform- (managed runtime/middleware) and Software-as-a-Service (managed application). More is provider-managed moving from IaaS to SaaS, shifting the responsibility boundary. | [15] |
| Data processing service | An on-demand, scalable cloud or edge computing service (Data Act Art. 2(8)); the Data Act term that brings cloud providers within its switching/interoperability regime. | [4] |
| ICT third-party service provider | An undertaking providing ICT services (including cloud/hosting) to financial entities (DORA Art. 3(19)); reached directly by DORA's third-party-risk and oversight regime. | [3] |
| EUCS | The candidate **European Cybersecurity Certification Scheme for Cloud Services**, developed by ENISA under the Cybersecurity Act (Reg (EU) 2019/881); **not yet adopted** as an implementing act at this document's date. | [5][7][8] |
| CSA STAR | The Cloud Security Alliance's Security, Trust, Assurance & Risk programme — a public registry and multi-level (self-assessment / third-party certification / continuous) cloud-assurance scheme built on the Cloud Controls Matrix. | [18] |

# Background

Cloud hosting reorganised IT from owned, on-premises assets into **shared, multi-tenant, on-demand services** operated by third parties — often across borders and at hyperscale. That shift concentrated both **capability** and **risk**: a handful of providers now underpin large parts of the economy, so their security, resilience, portability and jurisdictional exposure became matters of public regulation rather than private contract alone.

EU/UK law responded on several fronts, each addressed in its own foundations document. The **GDPR** (2016) made the **controller/processor** split and **security of processing** binding, and — after **Schrems II** (2020) invalidated Privacy Shield — turned international transfers into a case-by-case risk assessment [1][6]. **NIS2** (2022) brought cloud, data-centre and CDN providers into a horizontal cybersecurity regime as **digital-infrastructure** entities [2]. **DORA** (2022) added a financial-sector regime with, for the first time, **direct EU oversight** of the most critical ICT (including cloud) providers [3]. The **Data Act** (2023) attacked **vendor lock-in**, making switching and interoperability legal duties for cloud "data processing services" [4]. And the **Cybersecurity Act** (2019) created the EU certification framework under which a cloud-specific scheme (**EUCS**) has been drafted but — unlike the products scheme (**EUCC**) — **not yet adopted** [5][8]. This document synthesises those threads for the hosting context.

# Legal Framework

This document describes a **cross-cutting application**, not a single instrument. The binding duties live in the instruments below (and in their dedicated documents); they are summarised here as they bear on cloud hosting.

- **GDPR (Reg (EU) 2016/679)** — **Art. 28** (processor obligations and mandatory DPA terms), **Art. 32** (security of processing), and **Chapter V, Arts. 44–50** (transfers to third countries). The hosting provider is normally a **processor**; the customer is normally the **controller** and retains accountability (Art. 5(2)) [1]. *(Legal obligation — see `gdpr-foundations`, `privacy-engineering-foundations`.)*
- **NIS2 (Dir (EU) 2022/2555)** — cloud computing, data-centre, CDN and managed/managed-security service providers are **Annex I "digital infrastructure" / "ICT service management" (B2B)** entity types; in-scope providers are **essential or important entities** subject to Art. 21 risk-management measures and Art. 23 incident reporting, and several must **register with ENISA (Art. 27)** [2]. *(Legal obligation — see `nis2-foundations`.)*
- **DORA (Reg (EU) 2022/2554)** — a cloud provider serving financial entities is an **ICT third-party service provider** (Art. 3(19)); customers must embed the **Art. 30 key contractual provisions**, and systemically important providers may be designated **CTPPs (Art. 31)** under the **Union Oversight Framework** with a **Lead Overseer** (Arts. 31–44) [3]. *(Legal obligation — see `dora-foundations`.)*
- **Data Act (Reg (EU) 2023/2854)** — "data processing services" must remove **switching** obstacles, support **export/portability** and **interoperability** (Chapter VI, Arts. 23–31; Chapter VIII, Arts. 33–36), and **stop charging switching fees from 12 January 2027** (Art. 29); Art. 32 adds safeguards against unlawful third-country governmental access to non-personal data [4]. *(Legal obligation — phased; see `data-act-foundations`.)*
- **Cybersecurity Act (Reg (EU) 2019/881)** — establishes the EU cybersecurity **certification framework**; ENISA prepared the **EUCS** candidate cloud scheme, which **has not been adopted** as an implementing act at this document's date [5][7][8]. *(Framework in force; the cloud scheme is not yet adopted.)*

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| GDPR Art. 28 | Processor obligations; mandatory DPA terms (documented instructions, confidentiality, security, sub-processor authorisation, assistance, deletion/return, audit). | [1] |
| GDPR Art. 32 | Security of processing — risk-appropriate TOMs; encryption/pseudonymisation; CIA + resilience; effectiveness testing. | [1] |
| GDPR Arts. 44–50 | Transfers to third countries — adequacy, appropriate safeguards (SCCs, BCRs), derogations; Schrems II risk assessment. | [1][6] |
| NIS2 Art. 21 | Cybersecurity risk-management measures for essential/important entities (incl. supply-chain security). | [2] |
| NIS2 Art. 23 | Significant-incident reporting (early warning, notification, final report). | [2] |
| NIS2 Art. 27 | ENISA registration for cloud, data-centre, CDN, DNS, managed/managed-security providers and certain digital services. | [2] |
| DORA Art. 30 | Key contractual provisions required in ICT service arrangements (audit/access, security, incident cooperation, sub-outsourcing, exit). | [3] |
| DORA Arts. 31–44 | Designation of CTPPs and the Union Oversight Framework (Lead Overseer powers). | [3][11] |
| Data Act Arts. 23–31 | Switching between data-processing services; removal of obstacles; **Art. 29** gradual withdrawal of switching charges (prohibited from 12 Jan 2027). | [4][10] |
| Data Act Arts. 33–36 | Interoperability of data, data-sharing mechanisms and data-processing services. | [4] |
| Data Act Art. 32 | Safeguards against unlawful third-country governmental access to non-personal data held in the EU. | [4] |
| Cybersecurity Act Arts. 46–54 | EU cybersecurity certification framework; European schemes (assurance levels basic/substantial/high). | [5] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| GDPR Recital 81 | Controllers should use only processors providing sufficient guarantees; the relationship is governed by a contract (Art. 28). | [1] |
| GDPR Recital 83 | Security measures should be risk-based, guarding against accidental/unlawful destruction, loss, alteration or disclosure. | [1] |
| Data Act Recital 80 area | Rationale for removing switching obstacles and lock-in in data-processing services. | [4] |
| Cybersecurity Act Recital 65 area | Certification schemes should raise trust and assurance in ICT products, services and processes across the internal market. | [5] |

*Recitals are not binding but aid interpretation of the enacting articles.*

## Relevant Case Law

**Not Applicable at the foundational level, with one cross-referenced exception.** Cloud hosting is a cross-cutting application rather than a single instrument, so there is no distinct body of "cloud hosting" case law. The one directly load-bearing judgment is **Schrems II** (C-311/18, ECLI:EU:C:2020:559), which invalidated the EU–US Privacy Shield and conditioned reliance on Standard Contractual Clauses on a case-by-case assessment of third-country access risk and supplementary measures — foundational for cloud transfers and treated in `gdpr-foundations` [6]. NIS2, DORA and the Data Act are too recent for settled case law on their cloud-facing provisions [2][3][4].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **EDPB** — on transfers, **Recommendations 01/2020** set out the six-step methodology (know your transfers, identify the mechanism, assess third-country law, adopt supplementary measures, procedural steps, re-evaluate) that operationalises Schrems II for cloud data flows; SCCs alone do not suffice where third-country law compromises them [12]. *(Regulatory interpretation.)*
- **ENISA** — prepared the **EUCS** candidate scheme under the Cybersecurity Act and maintains the certification portal; ENISA's own page presents EUCS as a **draft candidate** scheme, not an adopted regulation [7]. ENISA also supports NIS2 implementation for digital-infrastructure providers. *(Regulatory / technical guidance.)*
- **European Commission** — confirms that under the certification framework the **only adopted scheme is EUCC** (Common Criteria, for ICT products, available from 27 February 2025); a cloud services scheme is **not among the adopted schemes**, and the Commission proposed a **revision of the Cybersecurity Act on 20 January 2026** partly to unblock scheme development [8][9]. On the Data Act, the Commission frames the switching rules as targeting **vendor lock-in**, requiring removal of commercial, technical and contractual obstacles and withdrawal of switching charges over a transition period [10]. *(Regulatory interpretation.)*
- **ESAs (EBA/EIOPA/ESMA)** — designated the **first CTPPs on 18 November 2025** (reported as 19 providers, including hyperscale cloud), placing them under direct oversight with a Lead Overseer; the list is re-assessed over time, so cloud customers in finance should track it [11]. *(Regulatory interpretation — verify the live list.)*
- Regulators consistently treat **certification as evidence, not proof**: ISO/IEC 27001/27017/27018 or CSA STAR are strong evidence of appropriate measures but do not by themselves discharge a specific legal duty on specific facts [8][13]. *(Regulatory interpretation.)*

# Technical Considerations

- **The responsibility boundary shifts by service model** — in **IaaS** the customer owns the OS, runtime, data, identity and configuration; in **PaaS** the provider absorbs the runtime/middleware; in **SaaS** the provider manages nearly everything except data, identity/access and tenant configuration. Misconfiguration on the customer side of the line is the dominant cloud failure mode [1][13][15]. *(Best practice.)*
- **Encryption and key management** — encryption at rest/in transit and, where feasible, **customer-managed keys (BYOK/HYOK)** support Art. 32 and reduce exposure to provider or third-country access; key custody is a decisive control for transfer-risk mitigation [1][12]. *(Legal obligation, met via controls.)*
- **Tenant isolation and identity** — strong multi-tenant isolation, least-privilege IAM, and per-request authorisation (zero-trust) are core cloud controls; identity is the primary perimeter (see `cybersecurity-foundations`) [1]. *(Best practice.)*
- **Logging, resilience and backup** — availability and recoverability are explicit legal outcomes (GDPR Art. 32; NIS2 Art. 21 business continuity/backup; DORA response/recovery); ensure immutable, tested backups, centralised logging and a tested exit/portability path [1][2][3]. *(Legal obligation, met via controls.)*
- **Portability and interoperability by design** — the Data Act makes **export in a structured, commonly used, machine-readable format** and **functional equivalence (where feasible)** engineering requirements, not just contract clauses; build open interfaces and avoid proprietary lock-in ahead of the 12 Jan 2027 charge phase-out [4][10]. *(Legal obligation — phased.)*
- **Sub-processor / sub-outsourcing transparency** — maintain a current sub-processor register and flow-down controls; this serves GDPR Art. 28, DORA Art. 30 sub-outsourcing conditions and NIS2 supply-chain security simultaneously [1][2][3]. *(Legal obligation.)*

## Cloud responsibility matrix

**BEST PRACTICE / EDITORIAL** — an indicative allocation; the exact split is defined by the specific service and contract (provider-specific matrices are deferred to `cloud-provider-responsibility-matrices`). "P" = provider-led, "C" = customer-led, "S" = shared.

| Control domain | IaaS | PaaS | SaaS | Anchoring obligation |
|----------------|------|------|------|----------------------|
| Physical / data-centre security | P | P | P | NIS2 Art. 21; ISO 27017 [2][15] |
| Host / hypervisor / virtualisation | P | P | P | NIS2 Art. 21; ISO 27017 [2][15] |
| Network controls (segmentation, firewalling) | S | S | P | GDPR Art. 32; ISO 27017 [1][15] |
| Operating system / patching | C | P | P | GDPR Art. 32; NIS2 Art. 21 [1][2] |
| Application security / secure SDLC | C | S | P | GDPR Art. 32; OWASP (see `cybersecurity-foundations`) [1] |
| Identity & access management | C | C | S | GDPR Art. 32 [1] |
| Data classification & encryption (incl. keys) | C | C | S | GDPR Art. 32; ISO 27018 [1][16] |
| Configuration / tenant hardening | C | C | C | GDPR Art. 32; ISO 27017 [1][15] |
| Logging, monitoring & incident detection | S | S | S | NIS2 Art. 23; DORA Arts. 17–19 [2][3] |
| Backup, resilience & tested recovery | S | S | S | GDPR Art. 32; NIS2 Art. 21; DORA [1][2][3] |
| International-transfer safeguards | S | S | S | GDPR Chapter V; Schrems II [1][6] |
| DPA / Art. 28 terms & sub-processor control | S | S | S | GDPR Art. 28 [1] |
| Exit, portability & switching support | S | S | S | Data Act Arts. 23–31 [4] |
| **GDPR accountability** | **C** | **C** | **C** | GDPR Art. 5(2) [1] |

**Key point:** accountability (bottom row) is **always the customer/controller's** and never shifts with the service model, even where the provider performs the underlying control [1].

# Hosting Considerations

*This document is itself the hosting synthesis; this section states the provider- and customer-facing obligations directly.*

- **Provider as processor** — a hosting provider processing personal data on a customer's instructions is a **processor** and must accept **Art. 28** terms; acting outside instructions, or determining purposes/means, risks re-characterisation as a **controller** with direct liability [1]. *(Legal obligation.)*
- **NIS2 direct scope** — cloud, data-centre, CDN and managed/managed-security providers are **digital-infrastructure/ICT-service-management** entities; in-scope providers must implement Art. 21 measures, report significant incidents (Art. 23) and register with ENISA (Art. 27) where required [2]. *(Legal obligation — assess role, per Member State.)*
- **DORA for financial-sector hosting** — providers serving financial entities must support **Art. 30** contract rights (audit/access, security, incident cooperation, sub-outsourcing controls, exit assistance); a **CTPP** designation adds direct ESA oversight duties (EU coordination point, cooperation with the Lead Overseer, oversight fees) [3][11]. *(Legal obligation — assess role.)*
- **Data Act switching duties** — providers must remove switching obstacles, give pre-contractual switching information, support export/interoperability, and **stop charging switching fees from 12 January 2027**; hosting contracts must carry the mandated switching clauses, and Art. 13 unfair-term protections constrain terms imposed on SME customers [4][10]. *(Legal obligation — phased.)*
- **Transfers and government-access exposure** — where the estate spans non-EEA regions or a provider is subject to third-country access laws, apply **Chapter V** mechanisms with a transfer-risk assessment and supplementary measures (encryption/key custody, split processing), and address the Data Act Art. 32 non-personal-data safeguard in parallel [1][4][6][12]. *(Legal obligation / regulatory interpretation.)*
- **Assurance posture** — evidence controls via **ISO/IEC 27001** plus **27017/27018** (and **27701** where the estate processes PII at scale) and/or **CSA STAR**; treat these as accountability evidence, and monitor **EUCS** for eventual adoption before relying on it [13][15][16][17][18][7]. *(Best practice.)*

# Game Hosting Considerations

- **Most pure game hosting is not a NIS2 digital-infrastructure entity** — online gaming is not among the NIS2 Annex I/II sectors, so a studio or game-server operator is generally not an essential/important entity *by virtue of gaming alone*; but if it *also* provides cloud, data-centre, CDN or managed-security services, those activities pull it into scope regardless of the gaming context (see `nis2-foundations`) [2]. *(Interpretation — assess by activity.)*
- **Cloud switching applies to game backends** — studios hosting on cloud/edge "data processing services" benefit from the Data Act switching rules as **customers**, and (if they resell managed hosting) may owe them as **providers** [4][10]. *(Legal obligation — assess role.)*
- **Player personal data stays under the GDPR** — telemetry, accounts and matchmaking data that are personal remain governed by GDPR Art. 28/32 and Chapter V; children's-data defaults heighten the duty (see `privacy-engineering-foundations`) [1][6]. *(Legal obligation.)*
- **DORA only via a financial nexus** — game hosting engages DORA only where the operator is itself a financial entity (e.g. a MiCA crypto-asset service provider or embedded payments arm) or supplies ICT services to one [3]. *(Interpretation — narrow.)*

# AI Considerations

- **Cloud-hosted AI inherits every hosting duty** — training/inference workloads on cloud infrastructure carry the same Art. 28/32, transfer, NIS2 and (in finance) DORA obligations as any other workload; the model, training data and pipeline are assets in the responsibility matrix [1][2][3]. *(Legal obligation.)*
- **Managed AI / model-as-a-service is a processor relationship** — using a provider's hosted model to process personal data typically makes the provider a **processor** requiring an Art. 28 DPA, with special attention to whether prompts/outputs are reused for provider model training (which can breach instructions/purpose limitation) [1]. *(Legal obligation.)*
- **Transfers bite hard for AI** — hosted-model APIs often route to non-EEA regions; apply Chapter V assessment and prefer EEA/in-region inference or customer-managed keys [1][6][12]. *(Legal obligation / regulatory interpretation.)*
- **AI Act overlap** — high-risk AI systems' security, robustness and data-governance duties run in parallel with hosting controls; see `ai-act-foundations` / `ai-governance-foundations`. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** (a cited law requires the outcome) / **BEST PRACTICE** (standards consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

1. **Map roles and the responsibility boundary** — for each service, document controller/processor status and the provider/customer control split (use the matrix above). *(OBLIGATION to allocate — GDPR Arts. 28/32; BEST PRACTICE for the matrix.)* [1]
2. **Put Article 28 DPAs in place** — with every provider and sub-processor, including sub-processor authorisation, security, assistance and deletion/return terms. *(OBLIGATION.)* [1]
3. **Implement Article 32 controls** — encryption (prefer customer-managed keys), IAM/least privilege, isolation, logging, tested backups, and regular effectiveness testing. *(OBLIGATION.)* [1]
4. **Assess and safeguard transfers** — inventory non-EEA data flows, apply Chapter V mechanisms and the EDPB six-step method, add supplementary measures. *(OBLIGATION.)* [1][6][12]
5. **Confirm NIS2 status** — determine whether the provider (or the customer's own infrastructure role) is an essential/important digital-infrastructure entity; implement Art. 21 measures, Art. 23 reporting and Art. 27 registration where applicable. *(OBLIGATION where in scope.)* [2]
6. **Finance: embed DORA third-party controls** — include Art. 30 key provisions, maintain the register of information, assess CTPP exposure and build tested exit strategies. *(OBLIGATION where DORA applies.)* [3][11]
7. **Prepare for Data Act switching** — remove switching obstacles, expose export/interoperability, and eliminate switching charges by **12 January 2027**. *(OBLIGATION — phased.)* [4][10]
8. **Adopt cloud assurance standards** — ISO/IEC 27001 with 27017/27018, and/or CSA STAR; obtain provider certifications and audit reports (e.g. SOC 2) as accountability evidence. *(BEST PRACTICE.)* [13][15][16][18]
9. **Track EUCS and the Cybersecurity Act revision** — do not assume EUCS certification exists; monitor adoption and the 2026 CSA revision. *(EDITORIAL RECOMMENDATION.)* [7][8][9]
10. **Design a tested exit** — maintain and rehearse a portability/exit plan so switching, DORA substitutability and resilience expectations are executable. *(BEST PRACTICE; obligation elements under Data Act and DORA.)* [3][4]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Responsibility boundary undocumented → security gaps at the seam | High | High | GDPR Art. 32; shared responsibility [1][13] | Documented responsibility matrix; config review | Medium |
| R2 | Missing/weak Art. 28 DPA or sub-processor control | Medium | High | GDPR Art. 28 [1] | Standard DPA; sub-processor register; flow-down | Low |
| R3 | Non-compliant international transfer (Schrems II) | Medium | High | GDPR Chapter V; Schrems II [1][6][12] | Transfer mapping; SCCs + supplementary measures; key custody | Medium |
| R4 | Cloud/infrastructure role in NIS2 scope but untreated | Medium | High | NIS2 Arts. 21/23/27 [2] | Scope assessment; Art. 21 measures; registration | Medium |
| R5 | Financial-sector hosting without Art. 30 terms / CTPP planning | Medium | High | DORA Arts. 30–44 [3][11] | Contract remediation; register; exit strategy | Medium |
| R6 | Switching charges/obstacles persisting past 12 Jan 2027 | Medium | High | Data Act Arts. 23–31 [4][10] | Remove charges; export/interoperability; contract update | Medium |
| R7 | Treating provider certification as full legal compliance | Medium | Medium | Regulatory interpretation [8][13] | Map controls to specific duties; retain evidence | Low |
| R8 | Relying on EUCS certification that does not yet exist | Low | Medium | EUCS not adopted [7][8] | Use ISO 27017/27018/CSA STAR; monitor adoption | Low |
| R9 | Vendor lock-in with no tested exit (resilience/portability) | Medium | High | Data Act; DORA substitutability [3][4] | Portability by design; rehearsed exit | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory & role mapping:** Catalogue cloud services, data flows and roles (controller/processor; NIS2/DORA/Data Act status). *Effort:* Medium.
- **Phase 1 — Contracts & DPAs:** Put Art. 28 DPAs, DORA Art. 30 terms (where relevant) and Data Act switching clauses in place; build the sub-processor register. *Effort:* Medium–High.
- **Phase 2 — Security controls (Art. 32):** Encryption/key management, IAM, isolation, logging, backup/resilience, effectiveness testing. *Effort:* High.
- **Phase 3 — Transfers:** Map non-EEA flows; apply Chapter V mechanisms and supplementary measures. *Effort:* Medium.
- **Phase 4 — Sector duties:** NIS2 Art. 21/23/27 where in scope; DORA register, CTPP exposure and exit planning for finance. *Effort:* High.
- **Phase 5 — Portability & assurance:** Data Act export/interoperability and charge withdrawal (by 12 Jan 2027); ISO 27017/27018 / CSA STAR assurance; EUCS watch. *Effort:* Medium–High.
- **Phase 6 — Monitor & adapt:** Track EUCS adoption, the CSA revision, CTPP list changes and Data Act guidance. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Cloud adopted ad hoc; roles and responsibility boundary undocumented. | No matrix; DPAs missing; transfers unmapped. |
| 2 | Managed | DPAs in place; basic security controls; some role mapping. | Art. 28 DPAs; encryption in places; partial inventory. |
| 3 | Defined | Responsibility matrix documented; transfers assessed; sector scope determined. | Matrix; Chapter V TIAs; NIS2/DORA scope decided. |
| 4 | Quantitatively Managed | Metrics on config drift, incident MTTR, transfer coverage; assurance certifications held. | ISO 27017/27018 or CSA STAR; tested backups; register maintained. |
| 5 | Optimising | Portability-by-design; rehearsed exit; integrated GDPR/NIS2/DORA/Data Act governance. | Switching drills; unified control mapping; continuous assurance. |

# Audit Questions

1. Is the provider/customer responsibility boundary documented for each service, and who owns each control? *(GDPR Art. 32; shared responsibility [1].)*
2. Are Art. 28 DPAs in place with all providers and sub-processors, with sub-processor authorisation and flow-down? *(GDPR Art. 28 [1].)*
3. Which Art. 32 measures (encryption, key management, IAM, resilience) are implemented, and how is effectiveness tested? *(GDPR Art. 32 [1].)*
4. Which data flows leave the EEA, and what Chapter V mechanism and supplementary measures apply? *(Chapter V; Schrems II; EDPB 01/2020 [1][6][12].)*
5. Is any cloud/infrastructure role in NIS2 scope, and are Art. 21/23/27 duties met? *(NIS2 [2].)*
6. For financial-sector hosting, are Art. 30 terms, the register of information and CTPP/exit planning in place? *(DORA [3][11].)*
7. Are Data Act switching obstacles removed and charges withdrawn by 12 Jan 2027, with export/interoperability supported? *(Data Act Arts. 23–31 [4][10].)*
8. What cloud assurance (ISO 27017/27018, CSA STAR) is held, and is it treated as evidence rather than proof of compliance? *([13][15][16][18].)*

# Implementation Checklist

- [ ] Cloud service, data-flow and role inventory completed (controller/processor; NIS2/DORA/Data Act status).
- [ ] Responsibility matrix documented per service (IaaS/PaaS/SaaS).
- [ ] Art. 28 DPAs in place with all processors and sub-processors; sub-processor register maintained.
- [ ] Art. 32 controls implemented: encryption/key management, IAM, isolation, logging, tested backup/resilience, effectiveness testing.
- [ ] International transfers mapped; Chapter V mechanisms and supplementary measures applied (EDPB six-step).
- [ ] NIS2 scope determined; Art. 21 measures, Art. 23 reporting and Art. 27 registration addressed where applicable.
- [ ] DORA Art. 30 terms, register of information and CTPP/exit planning in place where hosting serves financial entities.
- [ ] Data Act switching obstacles removed; export/interoperability supported; charges withdrawn by 12 Jan 2027.
- [ ] Cloud assurance obtained (ISO/IEC 27001 + 27017/27018 and/or CSA STAR); audit reports retained as evidence.
- [ ] EUCS adoption and Cybersecurity Act revision monitored; no reliance on EUCS certification until adopted.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Articles 5(2), 28 (processors), 32 (security of processing) and Chapter V (Arts. 44–50, transfers); Recitals 81, 83. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [2] **Directive (EU) 2022/2555 (NIS2)** — Articles 21, 23 and 27; Annex I "digital infrastructure" / "ICT service management (B2B)" entity types (cloud, data-centre, CDN, managed/managed-security providers). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj
- [3] **Regulation (EU) 2022/2554 (DORA)** — ICT third-party risk (Arts. 28–30) and the Union Oversight Framework for critical ICT third-party providers (Arts. 31–44). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj
- [4] **Regulation (EU) 2023/2854 (Data Act)** — switching between data-processing services (Chapter VI, Arts. 23–31, incl. Art. 29 charge withdrawal), interoperability (Arts. 33–36), Art. 32 non-personal-data safeguards. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2023/2854/oj
- [5] **Regulation (EU) 2019/881 (Cybersecurity Act)** — EU cybersecurity certification framework and European schemes (assurance levels basic/substantial/high); legal basis for EUCS. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2019/881/oj
- [6] **Data Protection Commissioner v Facebook Ireland & Schrems (Schrems II)**, C-311/18, ECLI:EU:C:2020:559 — invalidated Privacy Shield; SCCs conditional on case-by-case assessment and supplementary measures. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:62018CJ0311

## Regulatory Guidance

- [7] **EUCS — Cloud Services Scheme** (candidate/draft scheme prepared under the Cybersecurity Act; not adopted). ENISA. https://www.enisa.europa.eu/publications/eucs-cloud-service-scheme
- [8] **The EU cybersecurity certification framework** (EUCC adopted and available from 27 Feb 2025; cloud scheme not among adopted schemes). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cybersecurity-certification-framework
- [9] **Cybersecurity Act review: what to expect** (EPRS briefing, Jan 2026 — EUCS still awaiting adoption; CSA revision proposed 20 Jan 2026). European Parliamentary Research Service. https://epthinktank.eu/2026/01/05/cybersecurity-act-review-what-to-expect/
- [10] **Switching cloud service providers / cloud switching** (Data Act Chapter VI; removal of obstacles and withdrawal of switching charges). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cloud-switching
- [11] **European Supervisory Authorities designate critical ICT third-party providers under DORA** (first CTPP list, 18 November 2025). EIOPA/EBA/ESMA. https://www.eiopa.europa.eu/european-supervisory-authorities-designate-critical-ict-third-party-providers-under-digital-2025-11-18_en
- [12] **Recommendations 01/2020 on measures that supplement transfer tools** (six-step Schrems II methodology). European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-012020-measures-supplement-transfer_en

## Standards

- [13] **ISO/IEC 27001:2022** — Information security management systems (ISMS) — Requirements. ISO. https://www.iso.org/standard/27001
- [14] **ISO/IEC 27002:2022** — Information security controls (companion control set). ISO. https://www.iso.org/standard/75652.html
- [15] **ISO/IEC 27017:2015** — Code of practice for information security controls for cloud services (based on ISO/IEC 27002). ISO. https://www.iso.org/standard/43757.html
- [16] **ISO/IEC 27018:2019** — Code of practice for protection of personally identifiable information (PII) in public clouds acting as PII processors. ISO. https://www.iso.org/standard/76559.html
- [17] **ISO/IEC 27701** — Privacy Information Management System (PIMS) extension to ISO/IEC 27001/27002. ISO. https://www.iso.org/standard/71670.html
- [18] **CSA STAR (Security, Trust, Assurance & Risk)** — cloud-assurance programme and public registry (Cloud Controls Matrix; self-assessment / third-party / continuous levels). Cloud Security Alliance. https://cloudsecurityalliance.org/star

## Academic Sources

Not Applicable — this cross-cutting synthesis relies on primary legislation, regulator/Commission/ESA guidance and international standards. Academic analysis (e.g. of cloud concentration risk, transfer-mechanism efficacy, EUCS sovereignty debate) will be cited in the sub-topic documents in the backlog.

# Further Reading

*Non-authoritative; provided for orientation only.*

- ENISA cybersecurity certification portal (schemes, candidate documents). https://certification.enisa.europa.eu/index_en
- ISO/IEC 27701 (privacy information management) — where cloud processing involves PII. https://www.iso.org/standard/71670.html

# Related Documents

- `gdpr-foundations` — controller/processor roles, Art. 28/32, Chapter V transfers, Schrems II (**prerequisite reading**).
- `privacy-engineering-foundations` — DPbDD and Art. 32 controls (encryption, key management, tenancy) for cloud.
- `cybersecurity-foundations` — shared-responsibility, ISO 27001/27002, zero trust and the controls cloud hosting relies on.
- `nis2-foundations` — cloud/data-centre/CDN/managed providers as digital-infrastructure entities.
- `dora-foundations` — ICT third-party risk and CTPP oversight for cloud serving financial entities.
- `data-act-foundations` — cloud switching, portability and interoperability duties.
- `international-transfers` — Chapter V mechanics, SCCs, TIAs, UK IDTA (planned).
- `eucs-deep-dive` — EUCS assurance levels and sovereignty debate (planned).
- `cloud-provider-responsibility-matrices` — provider-specific shared-responsibility detail (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; cross-cutting synthesis of cloud-hosting compliance. Researched against EUR-Lex (GDPR consolidated Arts. 28/32/Ch.V, NIS2, DORA, Data Act, Cybersecurity Act 2019/881, Schrems II), EDPB Recommendations 01/2020, ENISA/EC certification-framework pages, ESAs CTPP designation, EC cloud-switching, and ISO/IEC 27001/27002/27017/27018/27701 and CSA STAR. **EUCS status live-verified as not yet adopted** (only EUCC adopted; CSA revision proposed 20 Jan 2026); **Data Act switching-charge date (12 Jan 2027) verified**. All 18 external links returned HTTP 200 on 2026-07-11. | pending |
