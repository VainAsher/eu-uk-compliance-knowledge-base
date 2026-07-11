---
id: cyber-resilience-act
title: "EU Cyber Resilience Act: Product Cybersecurity Foundations"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU]
topic: Cybersecurity
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [cybersecurity-foundations, nis2-foundations, dora-foundations, ai-act-foundations]
tags: [cyber-resilience-act, cra, product-security, products-with-digital-elements, ce-marking, conformity-assessment, vulnerability-handling, secure-by-design, sbom, enisa]
legal_basis: Regulation (EU) 2024/2847 (Cyber Resilience Act)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | cyber-resilience-act |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The CRA is a **Regulation** (directly applicable, no national transposition) but is in a **phased transition**: reporting duties apply from **11 September 2026** and the substantive requirements from **full application on 11 December 2027**. The **harmonised standards** that will operationalise the essential requirements are **still under development** by CEN/CENELEC/ETSI. Confirm the current application dates and the state of harmonised standards before relying on them [1][5][8].

# Executive Summary

The **EU Cyber Resilience Act (Regulation (EU) 2024/2847**, "CRA") is the first horizontal EU law to impose **mandatory cybersecurity requirements on products** — hardware and software — placed on the Union market. Where NIS2 secures **entities** and DORA secures **financial-sector operations**, the CRA secures the **product** itself, across its whole lifecycle, from design through the end of its support period [1][2][5]. It applies to **"products with digital elements" (PDE)** — any software or hardware product whose intended or reasonably foreseeable use includes a direct or indirect data connection to a device or network (Art. 3(1)) — subject to carve-outs for products already governed by equivalent sectoral law (e.g. medical devices, motor vehicles, civil aviation) [1][5].

This document details the CRA's mechanics: the **scope** and the PDE concept; the **essential cybersecurity requirements** in **Annex I** (secure-by-design and secure-by-default product properties, plus a vulnerability-handling regime including an SBOM and a coordinated-vulnerability-disclosure policy) [1]; the **risk-based product classes** — *default*, *important* (Class I and Class II, Annex III) and *critical* (Annex IV) — and the **conformity-assessment routes** each triggers, culminating in **CE marking** [1][5]; the **reporting duties** to ENISA and CSIRTs for **actively exploited vulnerabilities and severe incidents** through the ENISA **single reporting platform** (24-hour early warning, 72-hour notification, 14-day final report) [1][7]; and the differentiated obligations of **manufacturers, importers, distributors** and **open-source software stewards** [1].

Three points dominate. First, the **phased timeline** (Art. 71): entry into force **10 December 2024**; conformity-assessment-body (notified-body) provisions from **11 June 2026**; **reporting obligations from 11 September 2026**; **full application from 11 December 2027** [1][5]. Second, **CE marking becomes a cybersecurity gate** — non-compliant PDE cannot lawfully be placed on the EU market, with fines up to **€15m or 2.5% of worldwide turnover** for breaching the essential requirements [1]. Third, the CRA **complements rather than duplicates** NIS2 and the AI Act: a secure product (CRA) is an input to a secure entity (NIS2) and to a robust high-risk AI system (AI Act) [1][2][3].

# Key Takeaways

- The **CRA (Regulation (EU) 2024/2847)** imposes **binding, horizontal cybersecurity requirements on products with digital elements** placed on the EU market; as a Regulation it is **directly applicable** in all Member States without transposition [1][5]. *(Legal obligation.)*
- **Scope** turns on the **"product with digital elements" (PDE)** definition (Art. 3(1)) — hardware or software with a direct/indirect data connection — with **exclusions** for products covered by equivalent sectoral law (medical devices, motor vehicles, civil aviation, marine equipment) and for genuinely **non-commercial open source** [1][5]. *(Legal obligation / scope.)*
- **Annex I** sets the **essential requirements**: Part I = **secure-by-design / secure-by-default product properties** (no known exploitable vulnerabilities at release, secure default configuration, protection of confidentiality/integrity, data minimisation, resilience to DoS, minimised attack surface, security logging, secure updates); Part II = **vulnerability handling** (SBOM, timely remediation, free security updates, a coordinated-vulnerability-disclosure policy) [1]. *(Legal obligation.)*
- Products are risk-classified as **default** (self-assessment), **important Class I** (Annex III — self-assessment only if harmonised standards/schemes are applied, else third-party), **important Class II** (Annex III — third-party), and **critical** (Annex IV — may require **European cybersecurity certification**); compliant products bear the **CE marking** [1][5]. *(Legal obligation.)*
- Manufacturers must provide **security updates for a support period of at least five years** (or the expected use time, if shorter) (Art. 13) [1]. *(Legal obligation.)*
- **Reporting (Art. 14, via the ENISA single reporting platform, Art. 16):** for an **actively exploited vulnerability** or a **severe incident**, a **24-hour early warning**, a **72-hour notification**, and a **14-day / final report** to the designated CSIRT and ENISA — **applies from 11 September 2026** [1][5][7]. *(Legal obligation — phased.)*
- Obligations cascade across the supply chain: **manufacturers (Art. 13)**, **importers (Art. 19)**, **distributors (Art. 20)** and, in a lighter-touch regime, **open-source software stewards (Art. 24)** [1]. *(Legal obligation.)*
- **Phased timeline (Art. 71):** entry into force **10 Dec 2024**; notified-body provisions **11 Jun 2026**; reporting duties **11 Sep 2026**; **full application 11 Dec 2027** — **live-verified against EUR-Lex and the Commission** [1][5]. *(Legal obligation — confirm before relying.)*
- **Penalties (Art. 64):** up to **€15m or 2.5% of worldwide annual turnover** for breaching the essential requirements or Arts. 13/14; €10m/2% and €5m/1% for lesser breaches [1]. *(Legal obligation.)*
- The CRA **complements NIS2 (entities) and the AI Act (AI systems)** — product security is an input to entity security and to AI robustness/cybersecurity, not a substitute [1][2][3]. *(Cross-reference.)*

# Purpose

This document is a Tier 3 sub-topic that **details the CRA material** introduced in `cybersecurity-foundations`. It supports: (a) **scope triage** — determining whether a hardware or software product is a PDE and, if so, its risk class; (b) **compliance design** — mapping the Annex I essential requirements and the vulnerability-handling/reporting duties onto a secure development lifecycle; and (c) **conformity planning** — selecting the correct conformity-assessment route and CE-marking path ahead of the phased dates. It is the product-security counterpart to the entity-security document `nis2-foundations` and the financial-resilience document `dora-foundations`.

# Scope

**In scope:** The CRA's legal character and objectives; the "product with digital elements" scope and its exclusions; the Annex I essential cybersecurity requirements (product properties and vulnerability handling); the product classes (default, important Class I/II, critical) and their conformity-assessment routes; CE marking and market-surveillance/enforcement at a foundational level; the Art. 14 reporting duties and the ENISA single reporting platform; the obligations of manufacturers, importers, distributors and open-source software stewards; the phased application timeline (**live-verified**); and the CRA's relationship to NIS2, DORA, the AI Act and the Cybersecurity Act.

**Out of scope (deferred to the research backlog):** The **conformity-assessment modules** (A / B+C / H) and notified-body mechanics article-by-article → `cra-conformity-assessment`; the **harmonised standards mapping** (CEN/CENELEC/ETSI deliverables against Annex I) → `cra-standards-mapping`; the **open-source steward regime** and community impact in depth → `cra-open-source`; the **secure-SDLC engineering** implementation of Annex I → `application-security`; the **delegated/implementing acts** (Annex III/IV updates, SBOM format, reporting technical detail) as they are adopted → tracked in this document's revisions. General security frameworks (ISO 27001, NIST CSF, OWASP) are covered in `cybersecurity-foundations`.

**Assumptions:** The reader understands the EU **Regulation vs Directive** distinction (a Regulation is directly applicable; contrast NIS2, a Directive). The reader has read `cybersecurity-foundations`. Where a product also processes personal data, the **GDPR** applies in parallel; where an entity operating the product is in NIS2 scope, **NIS2** applies to the entity in parallel.

# Definitions

*Shared terms are in `GLOSSARY.md` (incl. "product with digital elements", "CIA triad"). Only CRA-specific terms are narrowed here.*

| Term | Definition | Source |
|------|------------|--------|
| Product with digital elements (PDE) | Any software or hardware product and its remote data-processing solutions, whose intended or reasonably foreseeable use includes a direct or indirect logical or physical data connection to a device or network (Art. 3(1)). | [1] |
| Important product with digital elements | A PDE listed in **Annex III**, whose core functionality carries a heightened cybersecurity risk (Class I and Class II); triggers stricter conformity-assessment routes (Art. 7). | [1] |
| Critical product with digital elements | A PDE listed in **Annex IV** whose compromise could cause the most significant disruption; may be required to hold a **European cybersecurity certificate** (Art. 8). | [1] |
| Manufacturer | A natural/legal person who develops or manufactures PDE, or has them designed/developed/manufactured, and markets them under its own name or trademark (Art. 3(13)); bears the primary CRA obligations (Art. 13). | [1] |
| Open-source software steward | A legal person, other than a manufacturer, that systematically and sustainedly supports the development of specific free and open-source PDE intended for commercial activities (Art. 3(14)); subject to a lighter-touch regime (Art. 24). | [1] |
| Actively exploited vulnerability | A vulnerability for which there is reliable evidence that a malicious actor has exploited it in a system without the owner's permission (Art. 3(42)); triggers Art. 14 reporting. | [1] |
| Support period | The period during which a manufacturer must handle vulnerabilities and supply security updates — **at least five years**, or the product's expected use time if shorter (Art. 13(8)). | [1] |
| CE marking | The marking by which a manufacturer indicates a PDE conforms with the CRA (and other applicable Union harmonisation law), affixed before market placement (Arts. 29–30). | [1] |

# Background

Products with digital elements — from routers and IoT sensors to operating systems and mobile apps — have become a routine vector for cyberattacks, yet before the CRA there was **no horizontal EU rule requiring them to be secure**. Security was addressed piecemeal (sectoral product law, voluntary standards such as ETSI EN 303 645 for consumer IoT, or entity-level duties under NIS2), leaving two structural gaps the Commission identified: a **low level of cybersecurity** in many products, and **insufficient information** for users to choose and configure products securely [5][6][9]. The CRA closes those gaps by making cybersecurity a **CE-marking condition** for placing PDE on the market — the same "New Legislative Framework" mechanism used for product safety and electromagnetic compatibility, now extended to cyber [1][5].

The CRA was adopted as **Regulation (EU) 2024/2847** on 23 October 2024, published in the Official Journal on 20 November 2024, and **entered into force on 10 December 2024** [1][5]. Because it is a **Regulation**, it is **directly applicable** in every Member State — a deliberate contrast with NIS2, a Directive whose fragmented national transposition the EU found unsatisfactory. The CRA sits within a coherent EU cyber package: **NIS2** (entity risk management and incident reporting), **DORA** (financial-sector operational resilience), the **Cybersecurity Act (Regulation (EU) 2019/881)** (ENISA's mandate and the European cybersecurity certification framework), and the **AI Act** (trustworthy AI, including cybersecurity of high-risk systems) [1][2][3][4].

# Legal Framework

The CRA is a **directly applicable Regulation** structured around the New Legislative Framework for products. Its architecture:

- **Chapter I (Arts. 1–6)** — subject matter, **scope**, **definitions** (incl. Art. 3(1) PDE), and the relationship with other Union law (sectoral carve-outs).
- **Chapter II (Arts. 13–26)** — **obligations of economic operators**: manufacturers (Art. 13), their reporting duties (Art. 14), the ENISA **single reporting platform** (Art. 16), importers (Art. 19), distributors (Art. 20), and **open-source software stewards** (Art. 24); classification of **important** (Art. 7) and **critical** (Art. 8) products sits at the start of the scope/obligation machinery.
- **Chapter III (Arts. 27–28)** — **conformity**: presumption of conformity via harmonised standards, and the **EU declaration of conformity**.
- **Chapter IV (Arts. 29–34)** — **CE marking** (Arts. 29–30) and **conformity-assessment procedures** (Art. 32), performed by **notified bodies** where third-party assessment is required.
- **Chapters V–VII** — notification of conformity-assessment bodies, **market surveillance and enforcement**, and **delegated/implementing powers** (to update Annexes III/IV, specify the SBOM format, and detail reporting).
- **Penalties** — **Art. 64** (administrative fines).
- Substance lives in the **Annexes**: **Annex I** (essential requirements — product properties + vulnerability handling), **Annex II** (information to users), **Annex III** (important products, Class I/II), **Annex IV** (critical products), **Annex V** (EU declaration of conformity), **Annex VI** (conformity-assessment procedures).

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 3(1) | Definition of "product with digital elements" — anchors the entire scope. | [1] |
| Art. 6 + Annex I | Products may be made available only if they meet the **essential cybersecurity requirements** in Annex I. | [1] |
| Art. 7 + Annex III | **Important** products with digital elements (Class I and Class II) — stricter conformity routes. | [1] |
| Art. 8 + Annex IV | **Critical** products with digital elements — may require a European cybersecurity certificate. | [1][4] |
| Art. 13 | **Manufacturers' obligations** — risk assessment; meet Annex I; security updates for a **support period of ≥5 years**; documentation; conformity assessment; CE marking. | [1] |
| Art. 14 | **Reporting** of **actively exploited vulnerabilities** and **severe incidents** — 24h early warning, 72h notification, 14-day/final report (applies **11 Sep 2026**). | [1][5] |
| Art. 16 | Establishment of the **single reporting platform** operated by ENISA. | [1][7] |
| Art. 19 | **Importers' obligations** — place on the market only compliant, CE-marked PDE; verify manufacturer conformity. | [1] |
| Art. 20 | **Distributors' obligations** — act with due care that PDE bear CE marking and required documentation. | [1] |
| Art. 24 | **Open-source software stewards** — lighter-touch duties (cybersecurity policy, cooperation, vulnerability reporting). | [1] |
| Arts. 29–30 | **CE marking** — general principles and rules for affixing. | [1] |
| Art. 32 + Annex VI | **Conformity-assessment procedures** — internal control (Module A), EU-type examination (B+C), or full quality assurance (H). | [1] |
| Art. 64 | **Administrative fines** — up to €15m / 2.5% (essential requirements, Arts. 13/14); €10m / 2%; €5m / 1%. | [1] |
| Art. 71 | **Entry into force and application** — 10 Dec 2024; Ch. IV bodies 11 Jun 2026; reporting 11 Sep 2026; full application 11 Dec 2027. | [1][5] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting articles (Art. 296 TFEU); cited from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 1 area | Rationale — PDE are a frequent, successful attack vector; low product cybersecurity and inadequate updates cause cross-border harm, justifying horizontal rules. | [1] |
| Recital on scope/exclusions | Products already subject to equivalent Union cybersecurity requirements (e.g. medical devices, motor vehicles, civil aviation) are excluded to avoid double regulation. | [1] |
| Recital on open source | Free and open-source software developed or supplied outside a commercial activity is not covered; stewards of commercially-relied-upon OSS get a proportionate, lighter regime. | [1] |
| Recital on support period | Manufacturers should determine the support period by expected product use; it should normally be at least five years. | [1] |

## Relevant Case Law

**Not Applicable.** The CRA is a new instrument whose substantive obligations do not begin to apply until 11 September 2026 (reporting) and 11 December 2027 (full application), so there is no CJEU or national case law interpreting it. Interpretive weight currently rests on the Regulation's text, Commission guidance, ENISA materials and — once adopted — harmonised standards and delegated/implementing acts [1][5][8]. This will be revisited at the next review.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames the CRA as introducing **mandatory cybersecurity requirements across the whole product lifecycle**, built on **security-by-design and by-default**, transparency to users, and vulnerability handling, evidenced by **CE-marked conformity** — deliberately phased so manufacturers can prepare (full application 11 Dec 2027) [5][6]. *(Regulatory interpretation of a legal obligation.)*
- The Commission's **summary of the legislative text** confirms the operational split: **self-assessment** for the majority of products (default class); **third-party assessment** for important Class II and critical products; and, for important Class I, self-assessment **only if harmonised standards or a certification scheme are applied**, otherwise third-party [5]. *(Regulatory interpretation.)*
- **ENISA** operates the **single reporting platform** (SRP) that is the CRA's single entry point for manufacturers and stewards to report actively exploited vulnerabilities and severe incidents "only once" rather than to multiple national authorities; ENISA states the SRP is to be operational by **11 September 2026**, aligning with the Art. 14 reporting start date [7]. *(Regulatory interpretation / operational.)*
- **ENISA and the Commission's Joint Research Centre** have published a **CRA Requirements–Standards Mapping**, identifying which existing and forthcoming European/international standards can support the Annex I requirements and where **gaps** remain to be filled by new harmonised standards — signalling that the standards landscape is **not yet complete** [8]. *(Regulatory interpretation — plan around evolving standards.)*
- Regulators treat **harmonised standards as the practical route to conformity**: products conforming to a harmonised standard (once cited in the Official Journal) enjoy a **presumption of conformity** with the corresponding Annex I requirements, but the essential requirements — not the standard — remain the legal test [1][5]. *(Regulatory interpretation.)*

# Technical Considerations

- **Scope triage first** — determine whether a product is a **PDE** (Art. 3(1)) and whether an **exclusion** applies (products under equivalent sectoral law; non-commercial open source; pure SaaS that is not a remote data-processing solution integral to the product). This determines everything downstream [1][5]. *(Legal obligation.)*
- **Engineer to Annex I Part I (product properties)** — secure-by-default configuration; **no known exploitable vulnerabilities** at placing on the market; protection of confidentiality and integrity (encryption of stored/transmitted data as appropriate); **data minimisation**; access control; resilience to and mitigation of **denial-of-service**; **minimised attack surface**; security-relevant **logging**; and **secure, ideally automatic, updates** with the ability to roll back [1]. *(Legal obligation.)*
- **Stand up Annex I Part II (vulnerability handling)** — maintain an **SBOM** covering top-level dependencies; identify and remediate vulnerabilities **without delay**; provide **free security updates** for the support period; run a **coordinated vulnerability disclosure (CVD) policy** and a contact address; and, after fixing, share information about resolved vulnerabilities [1]. *(Legal obligation.)*
- **Map the product to a class and route** — *default* → **Module A internal control** (self-assessment); *important Class I* → self-assessment **only** if harmonised standards/scheme applied, else **notified-body** third-party (Module B+C or H); *important Class II* → **third-party**; *critical (Annex IV)* → third-party and potentially **European cybersecurity certification** (Cybersecurity Act) [1][4][5]. *(Legal obligation.)*
- **Standards alignment** — align the SDLC to **ISO/IEC 27001** (ISMS) and **NIST CSF 2.0** for process assurance, and to product baselines such as **ETSI EN 303 645** (consumer IoT) pending citation of CRA-specific harmonised standards; track the **ENISA/JRC standards mapping** for gap areas [8][9][10][11]. *(Best practice; presumption of conformity attaches only to harmonised standards once cited.)*
- **Build the reporting pipeline** — instrument the product and the PSIRT so an **actively exploited vulnerability** or **severe incident** can be detected and pushed to the **ENISA SRP** within the **24h / 72h / 14-day** windows from 11 Sep 2026 [1][7]. *(Legal obligation — phased.)*

# Hosting Considerations

- **"Remote data-processing solutions" can pull hosting into product scope** — where a hosted/cloud component is **integral to a PDE** (its absence would prevent the product performing its functions), that remote solution falls within the product's CRA conformity, even though standalone SaaS is generally outside scope [1][5]. *(Legal obligation — assess integration.)*
- **Update and reporting infrastructure** — meeting the Annex I secure-update duty and the Art. 14 reporting timelines requires reliable hosted **update-distribution** and **vulnerability-intake/PSIRT** infrastructure; provision for signed updates, rollback and secure telemetry [1][7]. *(Best practice grounded in a legal outcome.)*
- **Shared-responsibility clarity** — where a manufacturer relies on an IaaS/PaaS provider for the product's back end, the **manufacturer remains the CRA obligated party**; contractually secure the provider's cooperation on vulnerability handling and incident evidence (see the shared-responsibility model in `cybersecurity-foundations`) [1]. *(Best practice.)*
- **Overlap with NIS2 for the operator** — a cloud/hosting operator may itself be a NIS2 **essential/important entity**; NIS2 duties on the operator run **in parallel** with the CRA duties on the product manufacturer — different obligated parties, different instruments [1][2]. *(Legal obligation — distinguish the roles.)*

# Game Hosting Considerations

- **Game hardware and companion software are PDE** — consoles, controllers with connectivity, VR headsets, and downloadable game clients or launchers with a data connection are **products with digital elements** and fall within the CRA; their manufacturers owe the Annex I and vulnerability-handling duties [1][5]. *(Legal obligation — assess product scope.)*
- **Online game services vs products** — a purely server-side, subscription **game service** is closer to SaaS and generally outside direct CRA product scope, but any **distributed client** or **connected device** it ships is in scope; the boundary is the product, not the service [1][5]. *(Interpretation.)*
- **Update duty meets live-ops** — the Annex I **secure-update** obligation and the **≥5-year support period** interact with games' live-ops patch cadence: security updates must remain **free** and available for the support period even after feature updates cease [1]. *(Legal obligation.)*
- **Vulnerability disclosure for game clients** — anti-cheat drivers, DRM and networking stacks in game clients are security-sensitive; a **CVD policy** and SBOM (Annex I Part II) are required, and an actively exploited client vulnerability triggers Art. 14 reporting [1][7]. *(Legal obligation — phased.)*

# AI Considerations

- **AI-enabled products are PDE too** — a hardware or software product embedding an AI/ML component is a **product with digital elements**; the CRA's Annex I requirements apply to it as to any other PDE, adding secure-by-design and vulnerability-handling duties on top of any AI Act obligations [1][3]. *(Legal obligation.)*
- **CRA ↔ AI Act interface** — for **high-risk AI systems**, the AI Act (Arts. 8–15) requires accuracy, robustness and **cybersecurity by design**; the CRA is designed to **dovetail** so that a high-risk AI system which is also a PDE and **conforms to the CRA** is presumed to meet the AI Act's cybersecurity requirement to the extent covered — reducing double conformity work while both instruments still apply [1][3]. *(Cross-reference; legal obligation under both.)*
- **AI-specific attack surface** — model/data poisoning, adversarial inputs and prompt injection are cybersecurity risks to be addressed in the Annex I **risk assessment** and vulnerability handling for AI-embedding products; SBOMs should extend to model and dependency provenance [1]. *(Best practice, grounded in the Annex I risk-assessment duty.)*
- **Reporting overlap** — an actively exploited vulnerability in an AI-embedding PDE triggers **CRA Art. 14** reporting; if the same event affects a NIS2 entity or a personal-data breach, **NIS2 Art. 23** and **GDPR Art. 33** clocks may run in parallel to different authorities [1][2]. *(Legal obligation — run the relevant clocks.)*

# Operational Guidance

Labels: **OBLIGATION** (where the CRA requires the outcome) / **BEST PRACTICE** (standards consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

1. **Inventory products and triage scope** — list every hardware/software product placed (or to be placed) on the EU market, decide PDE status (Art. 3(1)) and whether an exclusion applies. *(OBLIGATION — foundational.)* [1][5]
2. **Classify each PDE** — default, important Class I/II (Annex III) or critical (Annex IV); this fixes the conformity route. *(OBLIGATION.)* [1][5]
3. **Run the Art. 13 cybersecurity risk assessment** — and let it drive design, development, production and maintenance decisions; document it. *(OBLIGATION.)* [1]
4. **Implement Annex I** — Part I product properties (secure-by-default, no known exploitable vulnerabilities, encryption, DoS resilience, logging, secure updates) and Part II vulnerability handling (SBOM, remediation, free updates, CVD policy). *(OBLIGATION.)* [1]
5. **Set and publish the support period** — at least five years unless expected use is shorter; commit to free security updates for that period. *(OBLIGATION.)* [1]
6. **Select and execute the conformity route** — internal control (Module A) or, where required, a **notified body** (B+C or H); draw up the **EU declaration of conformity** and affix the **CE marking**. *(OBLIGATION.)* [1]
7. **Stand up Art. 14 reporting** — PSIRT, detection and the **24h/72h/14-day** flow to the **ENISA single reporting platform** and the coordinating CSIRT; ready **before 11 Sep 2026**. *(OBLIGATION — phased.)* [1][7]
8. **Align importers/distributors** — verify CE marking, documentation and manufacturer conformity before making PDE available (Arts. 19–20). *(OBLIGATION for those operators.)* [1]
9. **Handle open-source stewardship** — where you steward commercially-relied-upon OSS, adopt a cybersecurity policy and cooperate on vulnerability handling (Art. 24). *(OBLIGATION for stewards — lighter-touch.)* [1]
10. **Track evolving standards and acts** — monitor CEN/CENELEC/ETSI harmonised standards, the ENISA/JRC mapping, and delegated/implementing acts (Annex III/IV, SBOM format); adopt harmonised standards to gain the presumption of conformity. *(EDITORIAL RECOMMENDATION.)* [8]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Wrongly concluding a product is out of CRA scope | Medium | High | Art. 3(1); exclusions [1][5] | Documented PDE/scope assessment per product | Low |
| R2 | Misclassifying an important/critical product as default | Medium | High | Arts. 7–8; Annex III/IV [1] | Class assessment; re-check on function change | Low |
| R3 | Annex I gaps (e.g. no SBOM, insecure defaults, no CVD) | High | High | Annex I Parts I/II [1] | Secure-SDLC; SBOM; CVD policy; secure-update pipeline | Medium |
| R4 | Placing a non-CE-marked/non-conforming PDE on the market | Medium | High | Arts. 13, 29–32; Art. 64 (€15m/2.5%) [1] | Conformity route executed; DoC; CE marking pre-market | Low |
| R5 | Missing the 24h/72h/14-day Art. 14 reporting windows | Medium | High | Art. 14; SRP [1][7] | PSIRT; SRP integration; drills before 11 Sep 2026 | Medium |
| R6 | Under-provisioned support period / paid-for security updates | Medium | Medium | Art. 13(8) [1] | Commit ≥5-yr free security updates; lifecycle budget | Low |
| R7 | Relying on not-yet-cited harmonised standards for presumption of conformity | Medium | Medium | Arts. 27; evolving standards [1][8] | Track OJ citations; interim third-party assessment | Medium |
| R8 | Treating CRA as covering the operating entity (NIS2 confusion) | Medium | Medium | Scope boundary [1][2] | Separate product (CRA) vs entity (NIS2) programmes | Low |

# Implementation Roadmap

- **Phase 0 — Product inventory & scope:** Catalogue products; determine PDE status and exclusions; identify the obligated role (manufacturer/importer/distributor/steward). *Effort:* Medium.
- **Phase 1 — Classification & route:** Classify each PDE (default/important I-II/critical); select the conformity-assessment route and identify a notified body where needed. *Effort:* Medium.
- **Phase 2 — Annex I engineering:** Implement product properties (Part I) and vulnerability handling (Part II) in the SDLC; produce SBOMs; establish the CVD policy and support period. *Effort:* High.
- **Phase 3 — Reporting readiness:** Stand up the PSIRT and the 24h/72h/14-day reporting flow to the ENISA SRP; run drills — **target before 11 Sep 2026**. *Effort:* Medium.
- **Phase 4 — Conformity & CE marking:** Complete conformity assessment; draw up the EU declaration of conformity; affix CE marking; assemble technical documentation — **before 11 Dec 2027**. *Effort:* High.
- **Phase 5 — Sustain & adapt:** Operate vulnerability handling across the support period; track harmonised standards, the ENISA/JRC mapping and delegated/implementing acts; adopt standards for presumption of conformity. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No CRA scoping; product security ad hoc. | No PDE inventory; no CVD; unknown dependencies. |
| 2 | Managed | Products inventoried and PDE-scoped; basic secure defaults and update mechanism exist. | Scope register; SBOM started; update channel. |
| 3 | Defined | Annex I Parts I/II implemented; class and conformity route decided; support period set; CVD live. | SBOM maintained; CVD policy; reporting runbook drafted. |
| 4 | Quantitatively Managed | Metrics on vulnerability remediation latency, update coverage and reporting timeliness; conformity assessed. | KPIs on MTTR/patch coverage; DoC drawn up; drills run. |
| 5 | Optimising | CE-marked conforming products; automated secure updates; harmonised-standards presumption of conformity; continuous improvement. | CE marking; harmonised-standard alignment; integrated CRA+NIS2 governance. |

# Audit Questions

1. Which products are PDE, and how was scope (and any exclusion) determined per product? *(Art. 3(1); exclusions [1][5].)*
2. How is each PDE classified (default / important Class I-II / critical), and which conformity route follows? *(Arts. 7–8; Annex III/IV [1].)*
3. How does the product meet each Annex I Part I property (secure defaults, no known exploitable vulnerabilities, encryption, DoS resilience, logging, secure updates)? *(Annex I [1].)*
4. What is the vulnerability-handling process — SBOM, remediation SLAs, free updates, CVD policy — and the declared support period? *(Annex I Part II; Art. 13(8) [1].)*
5. How will an actively exploited vulnerability or severe incident be reported within 24h/72h/14 days via the ENISA SRP? *(Art. 14; Art. 16 [1][7].)*
6. Where third-party assessment is required, which notified body is engaged, and is the EU declaration of conformity and CE marking in place? *(Arts. 30–32 [1].)*
7. For importers/distributors, how is manufacturer conformity, CE marking and documentation verified before making PDE available? *(Arts. 19–20 [1].)*
8. How are harmonised standards, the ENISA/JRC mapping and delegated/implementing acts tracked, and how is CRA compliance coordinated with NIS2/AI Act duties? *([1][2][3][8].)*

# Implementation Checklist

- [ ] Product inventory built; PDE status and exclusions assessed per product (Art. 3(1)).
- [ ] Obligated role identified (manufacturer / importer / distributor / open-source steward).
- [ ] Each PDE classified (default / important Class I-II / critical) and conformity route selected.
- [ ] Art. 13 cybersecurity risk assessment performed and documented.
- [ ] Annex I Part I product properties implemented (secure defaults, no known exploitable vulnerabilities, encryption, DoS resilience, logging, secure updates).
- [ ] Annex I Part II vulnerability handling in place (SBOM, remediation, free updates, CVD policy and contact).
- [ ] Support period set (≥5 years or expected use) with free security updates committed.
- [ ] Conformity assessment completed; EU declaration of conformity drawn up; CE marking affixed; technical documentation assembled.
- [ ] Art. 14 reporting pipeline to the ENISA single reporting platform operational and drilled (before 11 Sep 2026).
- [ ] Importer/distributor verification controls operating (Arts. 19–20) where applicable.
- [ ] Harmonised standards / ENISA-JRC mapping / delegated acts tracked; CRA coordinated with NIS2 and AI Act programmes.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`) using `curl -L -A "Mozilla/5.0"`.*

## Primary Sources

- [1] **Regulation (EU) 2024/2847 (Cyber Resilience Act).** Essential cybersecurity requirements, product classes, conformity assessment, CE marking, vulnerability/incident reporting, economic-operator obligations, penalties and phased application (Arts. 3, 6–8, 13–16, 19–20, 24, 29–32, 64, 71; Annexes I, III, IV). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/2847/oj
- [2] **Directive (EU) 2022/2555 (NIS2 Directive).** Entity-level cybersecurity risk-management (Art. 21) and incident reporting (Art. 23) — the entity-security complement to the CRA's product security. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj
- [3] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** Cybersecurity/robustness of high-risk AI systems (Arts. 8–15) — interfaces with the CRA for AI-embedding products. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [4] **Regulation (EU) 2019/881 (Cybersecurity Act).** ENISA's permanent mandate and the European cybersecurity certification framework — relevant to CRA critical products (Annex IV) and certification schemes. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2019/881/oj

## Regulatory Guidance

- [5] **The Cyber Resilience Act — summary of the legislative text.** Confirms entry into force (10 Dec 2024), notified-body provisions (11 Jun 2026), reporting obligations (11 Sep 2026), full application (11 Dec 2027), product classes and conformity/self-assessment routes, and CE marking. European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cra-summary
- [6] **Cyber Resilience Act** (policy overview — mandatory lifecycle cybersecurity, security-by-design/default). European Commission. https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act
- [7] **Single Reporting Platform (SRP).** The ENISA-operated single entry point for reporting actively exploited vulnerabilities and severe incidents under the CRA; to be operational by 11 Sep 2026. ENISA. https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp
- [8] **Cyber Resilience Act Requirements — Standards Mapping (JRC & ENISA joint analysis).** Maps Annex I requirements to existing/forthcoming standards and identifies gaps for new harmonised standards. ENISA / European Commission JRC. https://www.enisa.europa.eu/publications/cyber-resilience-act-requirements-standards-mapping

## Standards

- [9] **ETSI EN 303 645** — Cyber Security for Consumer Internet of Things: Baseline Requirements. A widely used consumer-IoT security baseline informing CRA-aligned product security pending citation of CRA-specific harmonised standards. ETSI. https://www.etsi.org/deliver/etsi_en/303600_303699/303645/02.01.01_60/en_303645v020101p.pdf
- [10] **ISO/IEC 27001:2022** — Information security management systems (ISMS) — Requirements; process assurance for a CRA-compliant secure development lifecycle. ISO. https://www.iso.org/standard/27001
- [11] **NIST Cybersecurity Framework (CSF) 2.0** — outcome framework supporting the CRA risk-assessment and vulnerability-handling processes. NIST. https://www.nist.gov/cyberframework

## Academic Sources

Not Applicable — this foundational reference relies on the primary Regulation and official Commission/ENISA sources. Academic analysis (e.g. of the open-source steward regime, SBOM efficacy or the conformity-assessment burden) will be cited in the sub-topic documents (`cra-conformity-assessment`, `cra-open-source`).

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Commission — Cyber Resilience Act policy hub (news, FAQs, delegated/implementing acts as adopted). https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act
- ENISA — Publications (threat landscape, product-security and certification materials). https://www.enisa.europa.eu/publications

# Related Documents

- `cybersecurity-foundations` — parent foundation doc; this document **details** its CRA material (prerequisite reading).
- `nis2-foundations` — the entity-security complement (NIS2 secures entities; the CRA secures products).
- `dora-foundations` — financial-sector operational resilience (sibling EU cyber-package instrument).
- `ai-act-foundations` — AI Act overlap for AI-embedding products (cybersecurity of high-risk AI systems).
- `cra-conformity-assessment` — conformity-assessment modules and notified-body mechanics (planned).
- `cra-standards-mapping` — harmonised-standards mapping against Annex I (planned).
- `cra-open-source` — open-source software steward regime in depth (planned).
- `application-security` — secure SDLC implementing the Annex I essential requirements (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Regulation (EU) 2024/2847), the European Commission CRA summary/policy pages, ENISA (Single Reporting Platform; JRC/ENISA standards mapping), and standards (ETSI EN 303 645, ISO/IEC 27001, NIST CSF 2.0). **Phased application dates live-verified on 2026-07-11** against EUR-Lex (Art. 71) and the Commission summary: entry into force 10 Dec 2024; notified-body provisions 11 Jun 2026; reporting obligations 11 Sep 2026; full application 11 Dec 2027. Article numbering (Art. 13 manufacturers, Art. 14 reporting, Art. 16 SRP, Arts. 19–20 importers/distributors, Art. 24 stewards, Arts. 29–32 CE/conformity, Art. 64 penalties, Annex I/III/IV), the ≥5-year support period (Art. 13(8)) and the Art. 64 fines (€15m/2.5%; €10m/2%; €5m/1%) verified. All 11 external links returned HTTP 200. | — |
