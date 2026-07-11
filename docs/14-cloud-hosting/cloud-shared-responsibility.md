---
id: cloud-shared-responsibility
title: "Cloud Hosting: Shared-Responsibility Models & Assurance"
version: 1.0.0
status: in-review
classification: public
jurisdiction: [EU, UK]
topic: Cloud Hosting
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
related: [cloud-hosting-foundations, cybersecurity-foundations, privacy-engineering-foundations, gdpr-foundations, gdpr-transfers, dora-foundations, nis2-foundations, data-act-foundations]
tags: [cloud-hosting, shared-responsibility, raci, article-28, article-32, iso-27017, iso-27018, iso-27001, csa-star, ccm, soc-2, eucs, cybersecurity-act, misconfiguration, sub-processor, concentration-risk, assurance]
legal_basis: Regulation (EU) 2016/679 (GDPR) Arts. 5(2), 28, 32 & Chapter V; Regulation (EU) 2019/881 (Cybersecurity Act); Regulation (EU) 2023/2854 (Data Act)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | cloud-shared-responsibility |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.15.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | Human reviewer (loop-authorised) — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a **depth sub-topic** of `cloud-hosting-foundations` (the parent), which it details on two points: (a) *how the shared-responsibility model actually allocates controls* across IaaS/PaaS/SaaS, and (b) *the assurance vehicles* used to evidence those controls. The broader regime map (NIS2, DORA, the Data Act, international transfers) lives in the parent and its siblings and is only cross-referenced here. Two items are **moving targets** and are flagged throughout: the **EU Cloud Services certification scheme (EUCS)**, which at this document's date **remains a candidate/draft and has not been adopted** as an implementing act under the Cybersecurity Act — only the products scheme **EUCC** is adopted [5][6][9]; and the **ISO/IEC 27017/27018** cloud-standard editions, where **27018 was reissued in 2025** and a **second edition of 27017 is in draft** [13][14]. Verify both before relying on them.

# Executive Summary

The **shared-responsibility model** is the organising idea of cloud compliance: the provider secures the parts of the stack it operates ("security *of* the cloud"), and the customer secures what it puts on top ("security *in* the cloud") [1][11]. The boundary is not fixed — it slides across **IaaS, PaaS and SaaS**, with the provider absorbing progressively more of the stack as you move from infrastructure to software [11][13]. This document maps that boundary control-by-control (identity, network, operating system, application, data, encryption/keys, logging, configuration), then ties each side of the line to concrete legal hooks: the **GDPR Article 28** processor/DPA terms and the **Article 32** security-of-processing controls [1].

Three messages dominate. First, **responsibility is negotiable but accountability is not**: whoever performs a control, the cloud customer — normally the **controller** — keeps GDPR **accountability** (Art. 5(2)) and cannot contract it away [1]. Second, **the customer's side of the line is where most incidents happen**: cloud breaches are overwhelmingly **customer-side misconfiguration** (public storage, over-broad identity, disabled logging, unmanaged keys), not provider platform failures — so customer-side hardening is the highest-value work [1][11][16]. Third, **certifications are evidence, not a guarantee**: **ISO/IEC 27001** with the cloud extensions **27017** (cloud security) and **27018** (public-cloud PII), **CSA STAR** built on the **Cloud Controls Matrix (CCM)**, and **SOC 2** attestations are strong accountability evidence but never discharge a specific legal duty on specific facts [11][13][14][16][17][18].

The document provides two ready-to-use artefacts: a **RACI-style responsibility matrix** across IaaS/PaaS/SaaS keyed to Art. 28/32, and a **cloud-assurance checklist** for reading a provider's compliance documentation and contracts. On certification, the headline is unchanged from the parent: **EUCS is not yet adopted**; use ISO/CSA/SOC evidence and watch the January 2026 Cybersecurity Act revision that aims to unblock it [5][6][7][8][9].

# Key Takeaways

- The **shared-responsibility model** splits controls between provider ("*of* the cloud") and customer ("*in* the cloud"); the split **shifts across IaaS/PaaS/SaaS**, with the provider owning more toward SaaS [1][11][13]. *(Best practice / standards.)*
- **Accountability cannot be outsourced**: the cloud customer/controller retains GDPR **Art. 5(2)** accountability even where the provider performs the control [1]. *(Legal obligation.)*
- The provider is normally a **processor**; **Article 28** requires a data-processing agreement with mandatory terms (documented instructions, confidentiality, security, sub-processor authorisation, assistance, deletion/return, audit) [1]. *(Legal obligation.)*
- **Article 32** security is met *jointly* — provider platform controls plus customer configuration; encryption, **customer-managed keys**, IAM least-privilege, logging and tested recovery sit largely on the customer side in IaaS [1]. *(Legal obligation, met via controls.)*
- **Misconfiguration is the dominant cloud failure mode** — public buckets, over-permissive identity, disabled logging, exposed secrets — and it sits on the **customer** side of the line [1][11][16]. *(Best practice.)*
- **Assurance vehicles**: **ISO/IEC 27001** (ISMS) plus **27017**/**27018** cloud extensions, **CSA STAR**/**CCM**, and **SOC 2** attestations evidence controls but are **not a compliance guarantee** [11][13][14][16][17][18]. *(Standards / best practice.)*
- **Standards currency has moved**: **ISO/IEC 27018 was reissued as a 2025 edition** (superseding 2019) and a **second edition of ISO/IEC 27017 is in draft**, both aligning to ISO/IEC 27002:2022 — verify the edition a provider certifies against [13][14]. *(Verified — standards moving.)*
- **Sub-processor and concentration risk** are structural: a current sub-processor register (Art. 28(2)/(4)), flow-down terms, and a tested exit/portability path (Data Act) are the mitigations [1][3]. *(Legal obligation / best practice.)*
- **EUCS remains a candidate/draft, not adopted**; only **EUCC** is adopted, and the **20 January 2026 Cybersecurity Act revision** aims to unblock EUCS — do not assume EUCS certification exists [5][6][7][8][9]. *(Verified status — not asserted.)*

# Purpose

This document supports engineering, security and compliance teams doing three things: (a) **allocating each cloud control to an owner** across the provider/customer boundary and across service models; (b) **reading and challenging a provider's assurance package** — ISO/CSA/SOC reports, the shared-responsibility documentation, and the contract/DPA; and (c) **hardening the customer side** against the misconfiguration failures that cause most cloud incidents. It provides a **RACI-style responsibility matrix** and a **cloud-assurance checklist** ready to drop into an assessment. It is a depth companion to `cloud-hosting-foundations`; the cross-cutting regime obligations (NIS2, DORA, Data Act, transfers) are treated there.

# Scope

**In scope:** The shared-responsibility model in detail across **IaaS/PaaS/SaaS**; a **control-by-control** allocation (identity, network, OS, application, data, encryption/keys, logging, configuration); a **RACI-style responsibility matrix** mapping **GDPR Art. 28** DPA terms and **Art. 32** controls to provider vs. customer; **assurance vehicles** (ISO/IEC 27001, 27017, 27018, 27701, CSA STAR/CCM, SOC 2) described neutrally; how to **read provider compliance documentation and contracts**; **misconfiguration** risk and **customer-side hardening**; **sub-processor and concentration risk**; and the **status of the EUCS**.

**Out of scope (see the named documents):**

- The full **regime map** — NIS2 digital-infrastructure scope, DORA/CTPP oversight, the Data Act switching timeline — → `cloud-hosting-foundations` (parent).
- **International-transfer mechanics** — Chapter V mechanisms, SCC modules, Transfer Impact Assessments, UK IDTA — → `gdpr-transfers`, `uk-transfers`.
- **EUCS in detail** — assurance levels, sovereignty debate — → `eucs-deep-dive` (planned).
- **Provider-specific matrices** — AWS/Azure/GCP service-by-service splits — → `cloud-provider-responsibility-matrices` (planned).
- **General security controls** (zero trust, ISMS mechanics) — → `cybersecurity-foundations`.

**Assumptions:** The reader has read `cloud-hosting-foundations` and `gdpr-foundations` (controller/processor, Art. 28/32, Chapter V). Where personal data is processed, the GDPR applies in parallel to every control discussed here.

# Definitions

*Shared terms — controller, processor, ISMS, CIA triad, shared-responsibility model, EUCS, accountability, TOMs — are defined in `GLOSSARY.md`. Only terms specific to this document are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Security "of" vs "in" the cloud | The shorthand for the responsibility boundary: the provider secures the infrastructure that runs cloud services ("of"), the customer secures its data, identities, applications and configuration that use them ("in"). | [1][11] |
| RACI | A responsibility-assignment convention: **R**esponsible (does the work), **A**ccountable (answerable for the outcome — a single owner), **C**onsulted, **I**nformed. Applied here to the provider/customer split. | [11][16] |
| Cloud Controls Matrix (CCM) | The Cloud Security Alliance's cloud-specific control framework (control domains with a shared-responsibility mapping) that underpins the CSA STAR programme. | [16][17] |
| SOC 2 | An AICPA attestation report on a service organisation's controls against the Trust Services Criteria (security, availability, processing integrity, confidentiality, privacy); Type I = design at a point in time, Type II = operating effectiveness over a period. | [18] |
| BYOK / HYOK | "Bring/Hold Your Own Key" — customer-managed encryption-key models where the customer supplies (BYOK) or retains sole custody of (HYOK) the key material used by the cloud service. | [1][4] |
| Misconfiguration | A customer-side control set to an insecure state (e.g. public object storage, over-broad IAM, disabled logging, exposed secrets); the leading cause of cloud data exposure. | [1][11][16] |

# Background

Cloud moved compute, storage and applications from owned, single-tenant hardware into **shared, multi-tenant, provider-operated services**. That created an unavoidable division of labour: the provider runs the physical estate, the hypervisor and (increasingly) the platform and application layers, while the customer keeps control of its data, its users and its configuration. Providers formalised this as the **shared-responsibility model** — a diagram showing which layers each side owns — and the model became the reference point for both security architecture and compliance allocation [1][11].

The compliance framing followed. Under the **GDPR**, the hosting provider is typically a **processor** and the customer a **controller**, so the boundary maps onto the **Article 28** processor relationship and the **Article 32** security duties [1]. Standards bodies built cloud-specific control sets on top of the general ISMS standard: **ISO/IEC 27017** (cloud security guidance) and **ISO/IEC 27018** (PII in public clouds) extend **ISO/IEC 27001/27002**, with **ISO/IEC 27701** adding a privacy-management (PIMS) layer, and the **Cloud Security Alliance** created the **Cloud Controls Matrix** and the **STAR** assurance registry [11][12][13][14][15][16][17]. In parallel, the **AICPA SOC 2** attestation became the common North American assurance artefact that European buyers also encounter [18]. The EU sought a bespoke certification through the **Cybersecurity Act (2019)**, under which ENISA drafted the **EUCS** — but that scheme has been deadlocked since 2020 over sovereignty requirements and, unlike the products scheme **EUCC**, **remains unadopted**; the Commission's **20 January 2026** Cybersecurity Act revision aims to unblock it [2][5][6][7][8][9]. This document distils how the model allocates controls and how the assurance vehicles evidence them.

# Legal Framework

The shared-responsibility model is an **engineering and contractual construct**, not itself a legal instrument. Its legal weight comes from the duties it helps allocate. The load-bearing provisions for this document:

- **GDPR (Reg (EU) 2016/679)** — **Art. 5(2)** (accountability — stays with the controller); **Art. 24** (controller's responsibility to implement measures); **Art. 28** (processor obligations and the mandatory DPA terms); **Art. 32** (security of processing appropriate to risk); **Chapter V** (transfers, where the estate spans third countries) [1]. The provider is normally the **processor**, the customer the **controller** [1]. *(Legal obligation — see `gdpr-foundations`, `privacy-engineering-foundations`.)*
- **Cybersecurity Act (Reg (EU) 2019/881)** — establishes the EU cybersecurity **certification framework** and its assurance levels (basic/substantial/high); the legal basis under which the **EUCS** candidate cloud scheme was prepared but **not yet adopted** [2][5][6]. *(Framework in force; the cloud scheme is not.)*
- **Data Act (Reg (EU) 2023/2854)** — makes **switching, export and interoperability** duties for cloud "data processing services" a legal matter, which bears directly on **concentration and exit risk** in the responsibility allocation (detail in the parent) [3]. *(Legal obligation — phased; see `data-act-foundations`.)*

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| GDPR Art. 5(2) | **Accountability** — the controller must be responsible for, and able to demonstrate, compliance; it does not transfer to the processor/provider. | [1] |
| GDPR Art. 24 | Controller must implement appropriate technical/organisational measures and be able to demonstrate compliance. | [1] |
| GDPR Art. 28 | Processor obligations; mandatory DPA terms (documented instructions, confidentiality, Art. 32 security, sub-processor authorisation and flow-down, assistance with data-subject rights and Arts. 32–36, deletion/return, audit/inspection). | [1] |
| GDPR Art. 32 | Security of processing — risk-appropriate TOMs; encryption/pseudonymisation; confidentiality, integrity, availability and resilience; regular effectiveness testing. | [1] |
| GDPR Arts. 44–50 | Transfers to third countries (relevant where hosting stores/accesses data outside the EEA); assessed with supplementary measures. | [1][4][10] |
| Cybersecurity Act Arts. 46–54 | EU cybersecurity certification framework; European schemes and assurance levels (basic/substantial/high); legal basis for EUCS. | [2] |
| Data Act Arts. 23–31 | Switching between data-processing services; removal of obstacles; export/portability — the exit dimension of concentration risk. | [3] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| GDPR Recital 81 | Controllers should use only processors giving sufficient guarantees of appropriate measures; the relationship is governed by an Art. 28 contract. | [1] |
| GDPR Recital 83 | Security measures should be risk-based, guarding against accidental or unlawful destruction, loss, alteration or unauthorised disclosure/access. | [1] |
| Cybersecurity Act Recital 65 area | Certification schemes should raise trust and assurance in ICT products, services and processes across the internal market. | [2] |

*Recitals are not binding but aid interpretation of the enacting articles.*

## Relevant Case Law

**Not Applicable at the level of the responsibility model, with one cross-referenced exception.** The shared-responsibility model is a contractual/engineering construct with no dedicated case law. The one directly load-bearing judgment for the **encryption/key-custody** controls on the customer side of the line is **Schrems II** (C-311/18, ECLI:EU:C:2020:559), which conditioned reliance on Standard Contractual Clauses on a case-by-case assessment of third-country access risk and supplementary measures — making **customer-managed keys and in-region processing** decision-relevant controls where the estate spans third countries [4]. Transfer case law is treated in `gdpr-transfers`.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **ENISA** prepared the **EUCS** candidate scheme under the Cybersecurity Act and presents it on its own publication page as a **candidate/draft** scheme, not an adopted regulation; the scheme has been in ad-hoc-working-group and consultation stages since December 2020 and stalled on sovereignty/data-localisation requirements [5]. *(Regulatory / technical status.)*
- **European Commission** confirms that under the certification framework the **only adopted scheme is EUCC** (Common Criteria for ICT products, available from 27 February 2025); **no cloud services scheme is among the adopted schemes** [6]. On **20 January 2026** the Commission published a **cybersecurity package** including a **proposed revision of the Cybersecurity Act**, explicitly intended to simplify the certification framework and create conditions for the stalled cloud scheme to resume — with adoption expected only later, after the legislative process [7][8]. *(Regulatory interpretation — moving target.)*
- The **European Parliamentary Research Service** briefing (January 2026) frames the review as confirming the **EUCS is still awaiting adoption** and the framework needs unblocking; treat any claim that EUCS certification is available as false at this date [9]. *(Regulatory commentary.)*
- **EDPB Recommendations 01/2020** operationalise the customer-side transfer controls (encryption with keys held outside the third country, pseudonymisation, split processing) that sit on the customer side of the responsibility boundary; SCCs alone do not suffice where third-country law compromises them [10]. *(Regulatory interpretation.)*
- Regulators and standards bodies consistently treat **certification as evidence, not proof**: ISO/IEC 27001/27017/27018, CSA STAR and SOC 2 are strong evidence of appropriate measures but do not by themselves discharge a specific legal duty on specific facts [6][11][16]. *(Regulatory interpretation.)*

# Technical Considerations

## The responsibility boundary shifts by service model

The boundary is best read layer-by-layer. Moving **IaaS → PaaS → SaaS**, the provider absorbs successive layers; the customer's residual duties concentrate on **data, identity and configuration**, which never fully leave the customer [1][11][13].

| Layer / control | On-prem | IaaS | PaaS | SaaS |
|-----------------|---------|------|------|------|
| Physical / data-centre | C | **P** | **P** | **P** |
| Host / hypervisor / virtualisation | C | **P** | **P** | **P** |
| Network controls (segmentation, firewalling, DDoS) | C | S | S | **P** |
| Operating system & patching | C | **C** | **P** | **P** |
| Runtime / middleware | C | **C** | **P** | **P** |
| Application code & secure SDLC | C | **C** | S | **P** |
| Identity & access management (IAM) | C | **C** | **C** | S |
| Data classification & content | C | **C** | **C** | **C** |
| Encryption & key management | C | **C** | S | S |
| Configuration / tenant hardening | C | **C** | **C** | **C** |
| Logging, monitoring & detection | C | S | S | S |
| Backup, resilience & tested recovery | C | S | S | S |

**P** = provider-led, **C** = customer-led, **S** = shared. Two rows never move off the customer regardless of model: **data/content** and **configuration/tenant hardening** — and, above them, **accountability** (Art. 5(2)) [1]. This is why "we moved to SaaS" does not remove the customer's core duties [1][11].

## Control-by-control notes

- **Identity (IAM)** is the primary cloud perimeter and is customer-led in IaaS/PaaS: least-privilege roles, MFA, no long-lived root/admin keys, just-in-time elevation, and per-request authorisation (zero trust — see `cybersecurity-foundations`) [1]. *(Best practice; Art. 32.)*
- **Network** shifts from shared (customer defines segmentation/security groups in IaaS) to provider-owned in SaaS; DDoS protection is typically provider-side but the *configuration* of exposure is customer-side [1][11]. *(Best practice.)*
- **Operating system / runtime** is the clearest IaaS→PaaS shift: the customer patches the OS in IaaS; the provider does in PaaS/SaaS [11][13]. *(Best practice.)*
- **Encryption & keys** is the decisive control for both Art. 32 and transfer risk: prefer **customer-managed keys (BYOK/HYOK)** so the provider cannot unilaterally decrypt, which strengthens supplementary-measure arguments under Schrems II/EDPB 01/2020 [1][4][10]. *(Legal obligation, met via controls.)*
- **Data/content** is always the customer's: classification, minimisation, retention and lawful basis do not transfer to any provider [1]. *(Legal obligation.)*
- **Logging & detection** is genuinely shared: providers expose logs and control-plane audit trails, but the customer must **enable, retain, centralise and monitor** them — a frequently-skipped step [1]. *(Best practice.)*

## Misconfiguration is the dominant failure mode

Cloud data exposure is overwhelmingly **customer-side misconfiguration**, not provider platform compromise: public object storage, over-permissive IAM and access policies, disabled or unmonitored logging, exposed secrets/keys in code or metadata, and unrestricted management-plane access [1][11][16]. Because these sit on the customer side of the line, the highest-value hardening work is customer-side: secure-by-default baselines, automated configuration scanning against a benchmark (e.g. CCM control domains), least-privilege IAM, mandatory encryption with managed keys, centralised immutable logging, and secrets management [1][11][16].

## Sub-processor and concentration risk

Cloud stacks are deep chains of sub-processors, and a handful of hyperscalers underpin much of the market — creating **concentration risk** at both the entity and market level. Mitigations map to the responsibility model: an accurate **sub-processor register** and change-notice rights (Art. 28(2)/(4)), **flow-down** of Art. 28/32 terms to sub-processors, **exit and portability** design so switching is executable (Data Act), and — for regulated sectors — substitutability/exit planning (DORA; see the parent) [1][3]. *(Legal obligation / best practice.)*

# Hosting Considerations

*This document is itself a hosting deep-dive; this section states the reading-and-contracting guidance directly.*

## How to read a provider's compliance documentation

- **Start with the shared-responsibility documentation.** Confirm the provider publishes a model that matches the *specific service* you consume — the split for a managed database (PaaS) differs from raw compute (IaaS). Watch for services the provider treats as SaaS where you assumed IaaS control [11][13]. *(Best practice.)*
- **Read the certificate scope, not the logo.** An ISO/IEC 27001 certificate covers a defined **scope** (which services, which regions); confirm your service and region are in scope and check the **Statement of Applicability** and the **27017/27018** cloud extensions are included — and the **edition** certified against, given 27018:2025 and the pending 27017 second edition [11][13][14]. *(Best practice.)*
- **For SOC 2, get the Type II report under NDA and read the exceptions.** A SOC 2 **Type II** covers operating effectiveness over a period; the value is in the **tested controls, the period, and the auditor's exceptions/CUECs** (complementary user-entity controls — the things *you* must do), not in the fact a report exists [18]. *(Best practice.)*
- **Use CSA STAR / CCM as the cross-map.** The provider's **STAR** entry (self-assessment, third-party certification, or continuous) and its **CCM** mapping show, control-domain by control-domain, what the provider claims to own — a practical way to see the responsibility split in one framework [16][17]. *(Best practice.)*
- **Treat all of it as evidence, not proof.** Map each certified control to your specific legal duties; retain the reports as accountability evidence, and re-check at renewal [1][6][11]. *(Regulatory interpretation.)*

## How to read the contract / DPA

- **Article 28 terms must be present and adequate**: documented instructions, confidentiality, Art. 32 security, **sub-processor authorisation and change notice**, assistance with data-subject rights and Arts. 32–36, **deletion or return** at end of service, and **audit/inspection** rights [1]. *(Legal obligation.)*
- **Check the security schedule against the responsibility model**: the DPA's technical-and-organisational-measures annex should state what the provider does; the gap is yours to cover [1]. *(Legal obligation.)*
- **Transfers**: identify processing locations and sub-processor regions; require Chapter V mechanisms and confirm your supplementary measures (key custody, in-region processing) are contractually supported [1][4][10]. *(Legal obligation / regulatory interpretation.)*
- **Exit**: confirm export formats, assistance and timelines so the Data Act switching/portability expectations are executable, not just promised [3]. *(Legal obligation — phased.)*

# Game Hosting Considerations

- **The model is identical for game backends** — a studio running matchmaking, accounts and telemetry on IaaS/PaaS owns OS/identity/data/config exactly as any other customer; "it's a game" changes nothing in the responsibility split [1][11]. *(Best practice.)*
- **Player personal data stays customer-side** — accounts, telemetry and matchmaking data that are personal remain under Art. 28/32 and (if the estate spans third countries) Chapter V; children's-data defaults heighten the customer's configuration and minimisation duties (see `uk-childrens-code`, `privacy-engineering-foundations`) [1][10]. *(Legal obligation.)*
- **Misconfiguration bites hardest at scale spikes** — public buckets of player data and over-broad service accounts are the common exposure; bake secure-by-default baselines and config scanning into the deploy pipeline before launch peaks [1][16]. *(Best practice.)*
- **Assurance for third-party game-services vendors** — anti-cheat, analytics and live-ops SaaS are sub-processors; obtain their SOC 2 / ISO evidence and flow Art. 28 terms down [1][18]. *(Legal obligation / best practice.)*

# AI Considerations

- **Cloud-hosted AI inherits the same split** — training/inference workloads on IaaS/PaaS put OS, identity, data, keys and configuration on the customer side exactly as any workload; the model, training data and pipeline are assets in the responsibility matrix [1][11]. *(Legal obligation / best practice.)*
- **Model-as-a-service is a processor relationship** — using a provider's hosted model to process personal data typically makes the provider a **processor** needing an Art. 28 DPA, with particular attention to whether prompts/outputs are reused for provider training (which can breach documented instructions and purpose limitation) [1]. *(Legal obligation.)*
- **Keys and region are the AI control levers** — hosted-model APIs often route to non-EEA regions; prefer in-region inference and customer-managed keys, and assess transfers under Chapter V/EDPB 01/2020 [1][4][10]. *(Legal obligation / regulatory interpretation.)*
- **AI Act overlap** — high-risk AI security, logging and data-governance duties run in parallel with these hosting controls; see `ai-act-foundations` / `ai-act-high-risk`. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** (a cited law requires the outcome) / **BEST PRACTICE** (standards consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

1. **Draw the boundary per service.** For each cloud service, document the provider/customer control split using the matrix below, and record controller/processor roles. *(OBLIGATION to allocate — GDPR Arts. 24/28/32; BEST PRACTICE for the matrix.)* [1][11]
2. **Put an adequate Article 28 DPA in place** with every provider and sub-processor, including sub-processor authorisation/notice and flow-down. *(OBLIGATION.)* [1]
3. **Implement the customer-side Art. 32 controls** — least-privilege IAM with MFA, encryption with **customer-managed keys**, network exposure control, centralised immutable logging, tested backups, and effectiveness testing. *(OBLIGATION.)* [1]
4. **Harden against misconfiguration** — secure-by-default baselines, automated config scanning against a benchmark (CCM domains), secrets management, no public data stores by default. *(BEST PRACTICE.)* [1][11][16]
5. **Read the provider assurance package properly** — certificate *scope* and edition (ISO 27001 + 27017/27018), SOC 2 **Type II** exceptions and CUECs, and the STAR/CCM mapping; retain as accountability evidence. *(BEST PRACTICE.)* [11][13][14][16][17][18]
6. **Manage sub-processor and concentration risk** — maintain a current sub-processor register, flow down Art. 28/32 terms, and design a tested exit/portability path (Data Act). *(OBLIGATION / BEST PRACTICE.)* [1][3]
7. **Assess transfers where the estate spans third countries** — Chapter V mechanisms plus supplementary measures (key custody, in-region processing) per EDPB 01/2020. *(OBLIGATION / regulatory interpretation.)* [1][4][10]
8. **Do not rely on EUCS** — use ISO/CSA/SOC evidence today; monitor EUCS adoption and the January 2026 Cybersecurity Act revision. *(EDITORIAL RECOMMENDATION.)* [5][6][7][8][9]

## RACI-style responsibility matrix (Art. 28 / Art. 32)

**BEST PRACTICE / EDITORIAL** — an indicative allocation; the exact split is defined by the specific service and contract (provider-specific matrices are deferred to `cloud-provider-responsibility-matrices`). **A** always denotes *accountability* and, for personal data, stays with the **customer/controller** (Art. 5(2)); **R** = does the work; **C**/**I** as usual. Columns show who is **R** by service model.

| Control / obligation | Anchor | IaaS (R) | PaaS (R) | SaaS (R) | Accountable (A) |
|----------------------|--------|----------|----------|----------|-----------------|
| Physical & environmental security | Art. 32; ISO 27017 | Provider | Provider | Provider | Customer |
| Host/hypervisor & virtualisation isolation | Art. 32; ISO 27017 | Provider | Provider | Provider | Customer |
| OS & runtime patching | Art. 32 | Customer | Provider | Provider | Customer |
| Application security / secure SDLC | Art. 32 | Customer | Shared | Provider | Customer |
| Identity & access management (least privilege, MFA) | Art. 32 | Customer | Customer | Shared | Customer |
| Network exposure & segmentation | Art. 32; ISO 27017 | Customer | Shared | Provider | Customer |
| Data classification, minimisation & retention | Arts. 5, 32 | Customer | Customer | Customer | Customer |
| Encryption & key management (BYOK/HYOK) | Art. 32; ISO 27018 | Customer | Shared | Shared | Customer |
| Configuration / tenant hardening | Art. 32; ISO 27017 | Customer | Customer | Customer | Customer |
| Logging, monitoring & incident detection | Art. 32 | Shared | Shared | Shared | Customer |
| Backup, resilience & tested recovery | Art. 32 | Shared | Shared | Shared | Customer |
| DPA / Art. 28 terms & documented instructions | Art. 28 | Shared | Shared | Shared | Customer |
| Sub-processor authorisation, register & flow-down | Art. 28(2)/(4) | Shared | Shared | Shared | Customer |
| Assistance with data-subject rights & Arts. 32–36 | Art. 28(3)(e)/(f) | Provider→Customer | Provider→Customer | Provider→Customer | Customer |
| Deletion / return of data at end of service | Art. 28(3)(g) | Provider (on instruction) | Provider (on instruction) | Provider (on instruction) | Customer |
| Audit / inspection rights | Art. 28(3)(h) | Provider (enable) | Provider (enable) | Provider (enable) | Customer |
| International-transfer safeguards | Chapter V | Shared | Shared | Shared | Customer |
| Exit / portability / switching support | Data Act Arts. 23–31 | Shared | Shared | Shared | Customer |
| **GDPR accountability** | **Art. 5(2)** | **Customer** | **Customer** | **Customer** | **Customer** |

**Key point:** every row's **A** is the customer/controller — accountability never shifts with the service model, even where the provider is **R** for the underlying control [1].

## Cloud-assurance checklist (reading the provider)

- [ ] Shared-responsibility documentation obtained for the **specific** service(s) consumed.
- [ ] ISO/IEC 27001 certificate **scope** covers the service and region; **27017** and **27018** extensions included; **edition** noted (27018:2025 / 27017 edition).
- [ ] SOC 2 **Type II** report obtained (under NDA); period, tested controls, **exceptions** and **CUECs** reviewed.
- [ ] CSA STAR entry / CCM mapping reviewed as the responsibility cross-map.
- [ ] DPA present with adequate **Art. 28** terms (instructions, confidentiality, security, sub-processor authorisation/notice, assistance, deletion/return, audit).
- [ ] Security (TOMs) annex reconciled against the responsibility matrix; **gaps assigned to the customer**.
- [ ] Processing locations and sub-processor **regions** identified; Chapter V mechanism and supplementary measures (key custody, in-region) confirmed.
- [ ] Exit/portability terms (formats, assistance, timelines) confirmed executable.
- [ ] No reliance on **EUCS** certification; EUCS/CSA-revision watch-item logged.

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Responsibility boundary undocumented → gaps at the seam | High | High | Art. 32; shared responsibility [1][11] | Per-service responsibility matrix; config review | Medium |
| R2 | Customer-side **misconfiguration** (public storage, over-broad IAM, disabled logging) | High | High | Art. 32 [1][11][16] | Secure-by-default baselines; config scanning; least privilege; secrets mgmt | Medium |
| R3 | Provider certification treated as full legal compliance | Medium | Medium | Regulatory interpretation [6][11] | Map controls to specific duties; retain evidence; read CUECs | Low |
| R4 | Certifying/relying on an outdated **standard edition** (e.g. 27018:2019) | Medium | Low | ISO currency [13][14] | Check certified edition; track 27017 2nd ed / 27018:2025 | Low |
| R5 | Weak/absent **Art. 28** terms or sub-processor control | Medium | High | Art. 28 [1] | Adequate DPA; sub-processor register; flow-down | Low |
| R6 | Unmanaged encryption keys → provider/third-country access exposure | Medium | High | Art. 32; Schrems II [1][4][10] | Customer-managed keys (BYOK/HYOK); in-region processing | Medium |
| R7 | **Concentration / lock-in** with no tested exit | Medium | High | Data Act; DORA substitutability [3] | Portability by design; rehearsed exit; register | Medium |
| R8 | Relying on **EUCS** certification that does not yet exist | Low | Medium | EUCS not adopted [5][6][9] | Use ISO 27017/27018/CSA STAR/SOC 2; monitor adoption | Low |

# Implementation Roadmap

- **Phase 0 — Boundary mapping:** For each cloud service, document the provider/customer split and controller/processor roles. *Effort:* Medium.
- **Phase 1 — Contracts & DPAs:** Verify/insert adequate Art. 28 terms; build the sub-processor register; confirm exit terms. *Effort:* Medium.
- **Phase 2 — Customer-side hardening:** Least-privilege IAM, encryption with managed keys, network exposure control, centralised logging, tested backups, secure-by-default baselines and config scanning. *Effort:* High.
- **Phase 3 — Assurance review:** Read provider ISO/SOC 2/STAR packages against the matrix; assign residual gaps; retain evidence. *Effort:* Medium.
- **Phase 4 — Transfers & concentration:** Chapter V mechanisms and supplementary measures; rehearsed exit/portability. *Effort:* Medium.
- **Phase 5 — Monitor & adapt:** Track ISO edition changes (27017 2nd ed, 27018:2025), EUCS adoption and the Cybersecurity Act revision. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Cloud adopted ad hoc; boundary undocumented; assurance unread. | No matrix; DPAs unchecked; public defaults. |
| 2 | Managed | Some role mapping; DPAs in place; basic encryption/IAM. | Art. 28 DPAs; MFA in places; partial logging. |
| 3 | Defined | Responsibility matrix per service; assurance packages read against it. | Matrix; ISO/SOC 2 reviewed; CUECs assigned. |
| 4 | Quantitatively Managed | Config drift, misconfig and key-coverage metrics; hardening automated. | Config scanning; managed keys; tested backups; register. |
| 5 | Optimising | Portability-by-design; rehearsed exit; continuous assurance and edition tracking. | Switching drills; continuous STAR; standards-currency watch. |

# Audit Questions

1. Is the provider/customer boundary documented for each service, with a control owner and a single accountable party? *(Art. 32; shared responsibility [1][11].)*
2. How is customer-side **misconfiguration** prevented and detected (baselines, scanning, least privilege)? *(Art. 32 [1][16].)*
3. Are **Art. 28** terms adequate, with a maintained sub-processor register and flow-down? *(Art. 28 [1].)*
4. Which provider certifications are held, what is their **scope and edition**, and are they treated as evidence not proof (CUECs assigned)? *([6][11][13][14][18].)*
5. Are encryption keys **customer-managed**, and how does key custody support transfer safeguards? *(Art. 32; Schrems II; EDPB 01/2020 [1][4][10].)*
6. Is there a tested **exit/portability** path addressing concentration risk? *(Data Act [3].)*
7. How is reliance on **EUCS** avoided, and is the Cybersecurity Act revision tracked? *([5][6][7][8][9].)*

# Implementation Checklist

- [ ] Per-service responsibility matrix documented (IaaS/PaaS/SaaS), with controller/processor roles.
- [ ] Adequate Art. 28 DPAs in place with providers and sub-processors; sub-processor register maintained; flow-down confirmed.
- [ ] Customer-side Art. 32 controls implemented: least-privilege IAM + MFA, encryption with customer-managed keys, network exposure control, centralised immutable logging, tested backups, effectiveness testing.
- [ ] Misconfiguration hardening: secure-by-default baselines, config scanning against a benchmark, secrets management, no public data stores by default.
- [ ] Provider assurance reviewed: ISO 27001 scope + 27017/27018 (edition noted), SOC 2 Type II exceptions/CUECs, STAR/CCM mapping — retained as evidence.
- [ ] Transfers assessed where estate spans third countries; Chapter V + supplementary measures confirmed.
- [ ] Tested exit/portability path in place (Data Act); concentration risk assessed.
- [ ] No reliance on EUCS; EUCS + Cybersecurity Act revision watch-item maintained.

# References

*All links verified live (HTTP 2xx/3xx) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Arts. 5(2), 24, 28 (processors), 32 (security of processing) and Chapter V (Arts. 44–50); Recitals 81, 83. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [2] **Regulation (EU) 2019/881 (Cybersecurity Act)** — EU cybersecurity certification framework and European schemes (assurance levels basic/substantial/high); legal basis for EUCS. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2019/881/oj
- [3] **Regulation (EU) 2023/2854 (Data Act)** — switching between data-processing services (Chapter VI, Arts. 23–31); the exit/portability dimension of concentration risk. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2023/2854/oj
- [4] **Data Protection Commissioner v Facebook Ireland & Schrems (Schrems II)**, C-311/18, ECLI:EU:C:2020:559 — SCCs conditional on case-by-case assessment and supplementary measures (key custody, in-region processing). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:62018CJ0311

## Regulatory Guidance

- [5] **EUCS — Cloud Services Scheme** (candidate/draft scheme prepared under the Cybersecurity Act; **not adopted** at this document's date). ENISA. https://www.enisa.europa.eu/publications/eucs-cloud-service-scheme
- [6] **The EU cybersecurity certification framework** (EUCC adopted and available from 27 Feb 2025; **no cloud services scheme among adopted schemes**). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cybersecurity-certification-framework
- [7] **New measures to strengthen cybersecurity resilience and capabilities** (cybersecurity package incl. proposed Cybersecurity Act revision, 20 January 2026; aims to unblock cloud certification). European Commission. https://commission.europa.eu/news-and-media/news/new-measures-strengthen-cybersecurity-resilience-and-capabilities-2026-01-20_en
- [8] **Proposal for a Regulation for the EU Cybersecurity Act** (revision proposal; simplified certification framework). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/library/proposal-regulation-eu-cybersecurity-act
- [9] **Cybersecurity Act review: what to expect** (EPRS briefing, Jan 2026 — EUCS still awaiting adoption). European Parliamentary Research Service. https://epthinktank.eu/2026/01/05/cybersecurity-act-review-what-to-expect/
- [10] **Recommendations 01/2020 on measures that supplement transfer tools** (six-step Schrems II methodology; supplementary measures). European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-012020-measures-supplement-transfer_en

## Standards

- [11] **ISO/IEC 27001:2022** — Information security management systems (ISMS) — Requirements. ISO. https://www.iso.org/standard/27001
- [12] **ISO/IEC 27002:2022** — Information security controls (companion control set; basis for the cloud extensions). ISO. https://www.iso.org/standard/75652.html
- [13] **ISO/IEC 27017:2015** — Code of practice for information security controls for cloud services (first edition current; a **second edition aligned to ISO/IEC 27002:2022 is in draft**). ISO. https://www.iso.org/standard/43757.html
- [14] **ISO/IEC 27018:2025** — Protection of personally identifiable information (PII) in public clouds acting as PII processors (**2025 edition; supersedes 27018:2019**). ISO. https://www.iso.org/standard/27018
- [15] **ISO/IEC 27701** — Privacy Information Management System (PIMS) extension to ISO/IEC 27001/27002 (where the estate processes PII at scale). ISO. https://www.iso.org/standard/71670.html
- [16] **CSA STAR (Security, Trust, Assurance & Risk)** — cloud-assurance programme and public registry (self-assessment / third-party certification / continuous). Cloud Security Alliance. https://cloudsecurityalliance.org/star
- [17] **CSA Cloud Controls Matrix (CCM)** — cloud-specific control framework with shared-responsibility mapping; underpins CSA STAR. Cloud Security Alliance. https://cloudsecurityalliance.org/research/cloud-controls-matrix
- [18] **SOC 2 (System and Organization Controls) — Trust Services Criteria** (service-organisation attestation; Type I/II). AICPA & CIMA. https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2

## Academic Sources

Not Applicable — this practical guidance relies on primary legislation, regulator/Commission/ENISA/EDPB sources and international standards. Academic analysis (cloud concentration risk, misconfiguration empirics, EUCS sovereignty debate) will be cited in the deeper sub-topics in the backlog.

# Further Reading

*Non-authoritative; provided for orientation only.*

- ENISA cybersecurity certification portal (schemes, candidate documents). https://certification.enisa.europa.eu/index_en
- SOC suite of services (SOC 1/2/3 overview). AICPA & CIMA. https://www.aicpa-cima.com/resources/landing/system-and-organization-controls-soc-suite-of-services

# Related Documents

- `cloud-hosting-foundations` — **parent**; the cross-cutting regime map (NIS2, DORA, Data Act, transfers) and the foundational responsibility matrix.
- `cybersecurity-foundations` — ISMS, zero trust, ISO 27001/27002 and the controls this document allocates.
- `privacy-engineering-foundations` — DPbDD and Art. 32 controls (encryption, key management, tenancy).
- `gdpr-foundations` — controller/processor roles, Art. 28/32, Chapter V (**prerequisite reading**).
- `gdpr-transfers` / `uk-transfers` — Chapter V mechanics, SCCs/IDTA, TIAs (transfer detail).
- `dora-foundations` — ICT third-party risk, CTPP oversight and substitutability for financial-sector hosting.
- `data-act-foundations` — cloud switching, portability and interoperability (concentration/exit).
- `eucs-deep-dive` — EUCS assurance levels and sovereignty debate (planned).
- `cloud-provider-responsibility-matrices` — provider-specific shared-responsibility detail (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; depth sub-topic of `cloud-hosting-foundations` on the shared-responsibility model and assurance vehicles. Researched against EUR-Lex (GDPR consolidated Arts. 5/24/28/32/Ch.V; Cybersecurity Act 2019/881; Data Act 2023/2854; Schrems II), ENISA/EC certification-framework pages, the 20 Jan 2026 Cybersecurity Act revision package and EPRS briefing, EDPB Recommendations 01/2020, and ISO/IEC 27001/27002/27017/27018/27701, CSA STAR/CCM and AICPA SOC 2. **EUCS live-verified as still a candidate/draft (not adopted; only EUCC adopted; CSA revision proposed 20 Jan 2026 to unblock).** **ISO currency live-verified: 27018 reissued as 2025 edition; 27017 second edition in draft.** All 18 external links returned HTTP 2xx/3xx on 2026-07-11. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved via autonomous backlog loop (Cluster A); passed full QA suite; frozen in release 0.15.0. | Human reviewer (loop-authorised) |
