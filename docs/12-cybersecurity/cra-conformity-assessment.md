---
id: cra-conformity-assessment
title: "EU Cyber Resilience Act: Conformity Assessment & CE Marking"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: Cybersecurity
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [cyber-resilience-act, cybersecurity-foundations, ai-act-high-risk, nis2-foundations]
tags: [cyber-resilience-act, cra, conformity-assessment, ce-marking, notified-body, annex-viii, module-a, module-b, module-c, module-h, eucc, harmonised-standards, declaration-of-conformity]
legal_basis: Regulation (EU) 2024/2847 (Cyber Resilience Act), Articles 7–8, 13, 19–20, 24, 27–33, 35–51, 71; Annexes I, III, IV, V, VI, VII, VIII
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | cra-conformity-assessment |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.16.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a Tier 3 **deep-dive** that details the conformity-assessment and CE-marking material introduced at overview level in the parent document `cyber-resilience-act`; it does not repeat that overview. Two live-verified points dominate the timing: the **notified-body regime — Chapter IV, Articles 35–51 — applies from 11 June 2026**, the **manufacturer reporting duty (Art. 14) from 11 September 2026**, and the **substantive conformity/CE obligations from full application on 11 December 2027** (Art. 71) [1][5]. The **harmonised standards** that will unlock self-assessment are **still under development** by the European standardisation organisations; until they are cited in the *Official Journal*, the presumption of conformity is not yet available and routes must be planned accordingly [1][8]. Confirm the current dates and the state of harmonised standards before relying on them.

# Executive Summary

The Cyber Resilience Act (Regulation (EU) 2024/2847, "CRA") makes **CE marking a cybersecurity gate**: a product with digital elements (PDE) may be placed on the Union market only after its manufacturer has **demonstrated conformity** with the Annex I essential cybersecurity requirements through one of the CRA's **conformity-assessment procedures** and affixed the **CE marking** [1][5]. This document details, at article and annex level, *how* that demonstration is done, *which route* each product class must take, and *who* verifies it.

The mechanics run on the EU's **New Legislative Framework** modules. Article 32 offers four demonstration routes, all of whose procedures are set out in **Annex VIII**: the **internal control procedure (Module A)** — pure self-assessment; the **EU-type examination (Module B) followed by conformity to type based on internal production control (Module C)**; **full quality assurance (Module H)**; and, where available, a **European cybersecurity certification scheme** at assurance level at least "substantial" under the Cybersecurity Act (Regulation (EU) 2019/881), operationalised by the **EUCC** (Commission Implementing Regulation (EU) 2024/482) [1][2][3]. The **product class** fixes which routes are permitted: **default PDE** may self-assess (Module A); **important Class I (Annex III)** may self-assess **only** where harmonised standards, common specifications or a "substantial" certification scheme are applied in full, otherwise a **notified body** (Module B+C or H) is mandatory; **important Class II (Annex III)** must always use a notified body (Module B+C or H) or certification; and **critical products (Annex IV)** may be pushed by delegated act to **mandatory European cybersecurity certification** (Art. 8) [1][5].

Around these routes sit the deliverables that make CE marking lawful: the **technical documentation (Annex VII, Art. 31)**, kept at market-surveillance authorities' disposal for **at least 10 years or the support period**; the **EU declaration of conformity (Annex V, Art. 28)** by which the manufacturer takes sole responsibility; the **CE marking rules (Arts. 29–30)**; and a **support period of at least five years** across which vulnerability handling and free security updates must continue (Art. 13(8)) [1]. The obligations then cascade to **importers (Art. 19)** and **distributors (Art. 20)**, who must verify the marking and documentation before making a PDE available, and a lighter regime applies to **open-source software stewards (Art. 24)**. The single most important planning input is the **notified-body availability date (11 June 2026)** relative to **full application (11 December 2027)**: third-party routes cannot be executed until notified bodies exist, and the harmonised standards that would allow Class I self-assessment are not yet cited [1][5][8].

# Key Takeaways

- **Four demonstration routes (Art. 32), all detailed in Annex VIII:** internal control (**Module A**); **Module B** (EU-type examination) **+ Module C** (conformity to type); **Module H** (full quality assurance); or a **European cybersecurity certification scheme** at assurance level ≥ "substantial" [1][2][3]. *(Legal obligation.)*
- **Class fixes the route.** *Default* PDE may **self-assess (Module A)**; *important Class I* (Annex III) may self-assess **only if** harmonised standards / common specifications / a "substantial" certification scheme are applied (else notified body); *important Class II* (Annex III) **must** use a notified body (B+C or H) or certification; *critical* (Annex IV) may require **mandatory certification** by delegated act (Art. 8) [1][5]. *(Legal obligation.)*
- **Annex VIII, not Annex VI, holds the modules.** Annex V is the **EU declaration of conformity** model; Annex VI is the **simplified** declaration; Annex VII is the **technical documentation** content; Annex VIII is the **conformity-assessment procedures** [1]. *(Legal obligation — precise references.)*
- **Presumption of conformity (Art. 27)** attaches to **harmonised standards cited in the *Official Journal***, to **common specifications** (Commission implementing acts) where standards are absent, and to **European cybersecurity certification** for covered requirements — but the Annex I requirements, not the standard, remain the legal test [1][8]. *(Legal obligation + best practice.)*
- **Notified bodies are the third-party assessors** (Chapter IV, Arts. 35–51); this chapter **applies from 11 June 2026**, ahead of full application, precisely so that the third-party routes can be executed before 11 December 2027 [1][5]. *(Legal obligation — phased.)*
- **The CE-marking deliverables:** Annex VII **technical documentation** drawn up before market placement and kept for **≥10 years or the support period** (Arts. 31, 13(13)); the **EU declaration of conformity** (Art. 28, Annex V); and **CE marking** affixed visibly/legibly/indelibly, or — for software — on the declaration or accompanying website (Arts. 29–30) [1]. *(Legal obligation.)*
- **The support period is a conformity input:** at least **five years** (or the expected use time, if shorter), across which vulnerability handling and free security updates must continue (Art. 13(8)); security updates remain available for **≥10 years or the remainder of the support period** after issue [1]. *(Legal obligation.)*
- **Obligations cascade:** **importers (Art. 19)** and **distributors (Art. 20)** must verify CE marking, the declaration and documentation before making a PDE available; **open-source software stewards (Art. 24)** carry a lighter regime, and FOSS falling in Annex III categories may use Module A if its technical documentation is made public (Art. 32(5)) [1]. *(Legal obligation.)*
- **Timeline (Art. 71):** entry into force **10 Dec 2024**; **notified-body Chapter IV from 11 Jun 2026**; **reporting (Art. 14) from 11 Sep 2026**; **full application 11 Dec 2027** — **live-verified against EUR-Lex** [1][5]. *(Legal obligation — confirm before relying.)*
- **CRA ↔ AI Act dovetailing:** a high-risk AI system that is also a PDE and undergoes CRA conformity assessment can rely on that assessment for the AI Act's cybersecurity requirement to the extent covered (AI Act Annex VI / Art. 43 interface), avoiding duplicate third-party work [1][4]. *(Cross-reference.)*

# Purpose

This document supports three tasks the parent foundation leaves open: (a) **selecting the correct conformity-assessment route** for a given PDE from its class (default / important Class I–II / critical); (b) **executing the route** — assembling the Annex VII technical documentation, running the chosen Annex VIII module (with or without a notified body), drawing up the Annex V declaration and affixing the CE marking; and (c) **allocating downstream duties** to importers, distributors and open-source stewards. It is written for compliance, product and engineering readers preparing PDE for the EU market ahead of the phased dates. It presupposes `cyber-resilience-act` for the scope, essential-requirements and class overview, and cross-refers `ai-act-high-risk` for the closely analogous AI Act conformity chain.

# Scope

**In scope:** The product classification that drives route choice (Arts. 7–8; Annexes III, IV); the conformity-assessment procedures (Art. 32; Annex VIII Modules A, B, C, H) and which class uses which; the role of harmonised standards, common specifications and European cybersecurity certification (EUCC) in enabling self-assessment (Art. 27; Reg (EU) 2019/881; Impl. Reg (EU) 2024/482); notified bodies and the Chapter IV regime (Arts. 35–51) and its 11 June 2026 start; the technical documentation (Annex VII, Art. 31), EU declaration of conformity (Annex V/VI, Art. 28) and CE marking (Arts. 29–30); the support-period input (Art. 13(8)); and how conformity duties flow to importers (Art. 19), distributors (Art. 20) and open-source software stewards (Art. 24). Includes a conformity-route decision tree and a CE-marking checklist.

**Out of scope (covered elsewhere):** The CRA's legal character, PDE scope and exclusions, the full Annex I essential requirements and vulnerability-handling regime, the Art. 14 reporting duties and penalties → `cyber-resilience-act`; the **harmonised-standards mapping** (CEN/CENELEC/ETSI deliverables against Annex I) in depth → `cra-standards-mapping` (planned); the **open-source steward regime** in depth → `cra-open-source` (planned); secure-SDLC engineering of Annex I → `application-security` (planned). General assurance frameworks (ISO/IEC 27001) are covered in `cybersecurity-foundations`.

**Assumptions:** The reader has read `cyber-resilience-act` and understands the PDE concept and the Annex I requirements. Where a product also processes personal data or the operating entity is in NIS2 scope, the GDPR and NIS2 apply in parallel to different obligated parties. Harmonised standards are treated as **not yet cited** at this document's date; routes are planned on that basis.

# Definitions

*Shared terms (product with digital elements, conformity assessment, notified body, SBOM) are in `GLOSSARY.md`. Only conformity-specific terms are narrowed here.*

| Term | Definition | Source |
|------|------------|--------|
| Conformity-assessment module | A standard EU procedure for demonstrating conformity — here Module A (internal control), B (EU-type examination), C (conformity to type), H (full quality assurance) — the CRA versions of which are set out in Annex VIII and selected via Art. 32. | [1] |
| Internal control (Module A) | Self-assessment: the manufacturer ensures and declares on its sole responsibility that the PDE and its processes meet Annex I, without any notified-body involvement (Annex VIII Part I). | [1] |
| EU-type examination (Module B) | Third-party examination by a notified body of the PDE's design/technical documentation, resulting in an EU-type examination certificate; must be followed by Module C. | [1] |
| Conformity to type (Module C) | The manufacturer's declaration, based on internal production control, that production PDE conform to the EU-type examined under Module B. | [1] |
| Full quality assurance (Module H) | Third-party approval and surveillance of the manufacturer's quality management system covering design, development and final inspection of the PDE (Annex VIII). | [1] |
| Presumption of conformity | The legal effect (Art. 27) whereby a PDE conforming to a harmonised standard cited in the *Official Journal*, a common specification, or a relevant European cybersecurity certification is presumed to meet the Annex I requirements those instruments cover. | [1] |
| European cybersecurity certification scheme | A scheme under the Cybersecurity Act (Reg (EU) 2019/881) — e.g. the **EUCC** (Impl. Reg (EU) 2024/482) — a certificate at assurance level ≥ "substantial" under which can serve as a CRA conformity route (Art. 32) or trigger mandatory certification for critical products (Art. 8). | [2][3] |
| EU declaration of conformity (DoC) | The document (Art. 28; model in Annex V, simplified form in Annex VI) by which the manufacturer takes sole responsibility that the PDE meets the applicable Annex I requirements. | [1] |

# Background

The CRA does not invent a bespoke assessment scheme; it reuses the EU's **New Legislative Framework (NLF)** for products — essential requirements, harmonised standards conferring a presumption of conformity, conformity assessment by internal control or a notified body, the EU declaration of conformity and CE marking, and market surveillance [1][5]. The same modular vocabulary (Modules A, B, C, H) is used across EU product law and, in a fundamental-rights-flavoured variant, by the **AI Act** for high-risk systems — which is why this document's structure parallels `ai-act-high-risk` [4]. The CRA's distinctive move is to graft **cybersecurity** onto that chassis: the "essential requirements" are the Annex I secure-by-design properties and the vulnerability-handling regime, and the assessment must cover not only the product but the **processes** the manufacturer puts in place (Art. 32(1)) [1].

The CRA was adopted as **Regulation (EU) 2024/2847** (signed at Strasbourg, 23 October 2024), published in the *Official Journal* on 20 November 2024 and entered into force on **10 December 2024**. Its application is deliberately phased (Art. 71): the **notified-body chapter (Chapter IV, Arts. 35–51) applies first, from 11 June 2026**, so that conformity-assessment bodies can be notified and third-party routes can operate; the **manufacturer reporting duty (Art. 14) applies from 11 September 2026**; and the **substantive conformity, documentation and CE-marking obligations apply on full application, 11 December 2027** [1][5]. The harmonised standards that will operationalise Annex I — and thereby enable Class I self-assessment — are being drafted by the European standardisation organisations under a Commission request; the ENISA/JRC standards mapping tracks which existing standards can support Annex I and where gaps remain [1][8].

# Legal Framework

Conformity is governed principally by **Chapter III of the CRA (Conformity of the product with digital elements, Arts. 27–34)** and **Chapter IV (Notification of conformity assessment bodies, Arts. 35–51)**, supported by the manufacturer obligations in **Chapter II (esp. Art. 13)** and the classification provisions **Arts. 7–8** with **Annexes III and IV** [1].

**Classification drives the route.** Art. 7 + Annex III define **important** PDE (Class I and Class II); Art. 8 + Annex IV define **critical** PDE and empower the Commission to require, by delegated act, a European cybersecurity certificate. Everything not listed is **default** PDE [1].

**Presumption of conformity (Art. 27).** Conformity with harmonised standards (or parts) cited in the *Official Journal* presumes conformity with the Annex I requirements they cover; where standards are absent or insufficient the Commission may adopt **common specifications** by implementing act; and a relevant **European cybersecurity certification** (assurance ≥ "substantial") can likewise confer presumption for covered requirements [1].

**The assessment (Art. 32 + Annex VIII).** Art. 32(1) lets any manufacturer choose Module A, Module B+C, Module H, or a certification scheme. Art. 32(2)–(4) then *restrict* the choice by class (see the decision tree below). Art. 32(5) gives FOSS in Annex III categories access to Module A if the Annex VII technical documentation is made public; Art. 32(6) requires SME-proportionate fees [1].

**The deliverables.** Art. 28 requires the **EU declaration of conformity** (model Annex V; simplified form Annex VI per Art. 13(20)); Arts. 29–30 govern the **CE marking**; Art. 31 requires the **technical documentation** (content in Annex VII) drawn up before placing on the market; and Art. 13 sequences the manufacturer's overall obligations — risk assessment, meeting Annex I, conformity assessment, drawing up the DoC, affixing CE marking, and keeping documentation and the DoC for **≥10 years or the support period** (Art. 13(13)) [1].

**The verifiers.** Chapter IV (Arts. 35–51) establishes **notified bodies** — conformity-assessment bodies notified by Member States' notifying authorities to perform Modules B and H — and applies from 11 June 2026 [1][5].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 7 + Annex III | Classification of **important** PDE into **Class I** and **Class II** — fixes the permitted routes. | [1] |
| Art. 8 + Annex IV | **Critical** PDE; Commission may require **mandatory European cybersecurity certification** by delegated act. | [1][2] |
| Art. 13 | Manufacturer sequence — risk assessment, meet Annex I, conformity assessment, DoC, CE marking; documentation retention **≥10 years / support period** (Art. 13(13)); **support period ≥5 years** (Art. 13(8)). | [1] |
| Art. 19 | **Importers** — place on the market only PDE that are CE-marked, with a DoC and technical documentation; verify manufacturer conformity. | [1] |
| Art. 20 | **Distributors** — act with due care that PDE bear CE marking and required documentation. | [1] |
| Art. 24 | **Open-source software stewards** — lighter-touch conformity/cooperation duties. | [1] |
| Art. 27 | **Presumption of conformity** — harmonised standards, common specifications, European cybersecurity certification. | [1][8] |
| Art. 28 + Annex V/VI | **EU declaration of conformity** (full model Annex V; simplified Annex VI). | [1] |
| Art. 29 | **General principles of the CE marking.** | [1] |
| Art. 30 | **Rules and conditions for affixing the CE marking** (visible/legible/indelible; software on DoC or website). | [1] |
| Art. 31 + Annex VII | **Technical documentation** — content and drawing-up before market placement. | [1] |
| Art. 32 + Annex VIII | **Conformity-assessment procedures** — Module A; B+C; H; or certification; class-based restrictions. | [1] |
| Art. 33 | Support measures / proportionate fees for SMEs and start-ups. | [1] |
| Arts. 35–51 (Chapter IV) | **Notification of conformity assessment bodies** (notified bodies) — **applies from 11 June 2026**. | [1][5] |
| Art. 71 | Entry into force and application — 10 Dec 2024; Chapter IV 11 Jun 2026; Art. 14 11 Sep 2026; full application 11 Dec 2027. | [1][5] |

## Relevant Recitals

*Recitals are not binding but aid construction (Art. 296 TFEU practice); cited from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital on NLF alignment | The CRA follows the New Legislative Framework so that its conformity assessment, presumption of conformity and CE marking operate like other Union product law. | [1] |
| Recital on critical products / EUCC | Critical products already widely use certification and are covered by the EUCC (Impl. Reg (EU) 2024/482); mandatory certification may be adequate and proportionate where a relevant scheme is in place. | [1][3] |
| Recital on open-source hosting | Merely hosting PDE on open repositories or package managers is not "making available on the market"; such providers are distributors only if they supply in the course of a commercial activity. | [1] |
| Recital on SME support | Microenterprises and SMEs should be supported and conformity-assessment fees set proportionately to their needs. | [1] |

## Relevant Case Law

**Not Applicable.** The CRA is a new instrument whose conformity and CE-marking obligations do not apply until full application on 11 December 2027 (with the notified-body chapter from 11 June 2026), so no CJEU or national court has interpreted the Art. 27–32 conformity provisions. Interpretive weight currently rests on the Regulation's text, Commission guidance, ENISA materials and — once adopted — harmonised standards and delegated/implementing acts [1][5][8]. General NLF case law on CE marking and free movement may become analogically relevant. This section will be revisited at the next review.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames conformity assessment as scaling with risk: the **majority of products (default class) self-assess**; **important Class II and critical products** require **third-party assessment**; and **important Class I** may self-assess **only where harmonised standards or a certification scheme are applied**, otherwise a notified body is required [5][6]. *(Regulatory interpretation of Art. 32.)*
- The Commission treats **harmonised standards as the practical route to conformity** — meeting a standard cited in the *Official Journal* yields the Art. 27 presumption — while stressing that the **essential requirements, not the standard, are the legal test**, and that the standards are **still being developed** [5][8]. *(Regulatory interpretation — plan around evolving standards.)*
- **ENISA and the Commission's JRC** have mapped Annex I to existing and forthcoming standards, identifying **gaps** the new harmonised standards must fill; the mapping signals the standards landscape is **not yet complete**, so Class I self-assessment via standards is **not yet available** in practice [8]. *(Regulatory interpretation.)*
- The **EU cybersecurity certification framework** (Cybersecurity Act) supplies the certification route: the **EUCC** (Impl. Reg (EU) 2024/482) is the first adopted scheme, and a certificate at assurance level **≥ "substantial"** can support CRA conformity for default/important products and underpins mandatory certification for critical products (Art. 8) [2][3][9]. *(Regulatory interpretation.)*
- The Commission and ENISA position the **notified-body regime (Chapter IV) as available from 11 June 2026** so third-party routes can be executed before the 11 December 2027 full-application date; manufacturers of Class II / certain Class I / critical products should **plan notified-body engagement against this window** [5][7]. *(Regulatory interpretation — sequencing.)*

# Technical Considerations

- **Classify before you assess.** Determine the class (default / important Class I / important Class II / critical) from Annexes III–IV; the class *restricts* the Art. 32 route options. Record the classification reasoning per product [1][5]. *(Legal obligation.)*
- **Run the decision tree (see Operational Guidance).** Default → Module A self-assessment is available. Class I → Module A **only if** harmonised standards / common specifications / a "substantial" certification scheme are applied *in full*, else Module B+C or H. Class II → Module B+C, H, or certification (no Module A). Critical → certification per Art. 8 where mandated, else a Class II route [1]. *(Legal obligation.)*
- **Assess the product *and* the processes (Art. 32(1)).** The assessment covers both the PDE's Annex I product properties (Part I) and the manufacturer's vulnerability-handling **processes** (Part II) — SBOM, coordinated vulnerability disclosure, secure-update pipeline. Module H (quality assurance) is often the pragmatic fit where processes dominate, and mapping the quality-management evidence to **ISO/IEC 27001** aids auditability [1][11]. *(Legal obligation + best practice.)*
- **Build the Annex VII technical documentation as a living artefact.** It must exist **before** market placement (Art. 31(2)), be updated across the lifecycle, and be kept at market-surveillance authorities' disposal for **≥10 years or the support period** (Art. 13(13)). Generate it from the SDLC, not as a retrofit [1]. *(Legal obligation.)*
- **Draw up the EU declaration of conformity (Art. 28).** Use the Annex V model; it must state that the applicable Annex I requirements are met and reference the elements of the Annex VIII procedure used. A **simplified** DoC (Annex VI) may accompany the product with a URL to the full text [1]. *(Legal obligation.)*
- **Affix CE marking correctly (Arts. 29–30).** Visibly, legibly and indelibly on the product or its packaging; for **software**, on the EU declaration of conformity or the accompanying **website**. Where a notified body ran Module H, its identification number accompanies the marking [1]. *(Legal obligation.)*
- **Treat the support period as a design input (Art. 13(8)).** At least five years (or expected use time, if shorter). Because vulnerability handling and free security updates must continue across it — and updates must stay available for **≥10 years or the remainder of the support period** — the declared period shapes lifecycle budgeting and the conformity evidence [1]. *(Legal obligation.)*

# Hosting Considerations

- **Integral remote solutions are assessed with the product.** Where a hosted/cloud component is a **remote data-processing solution integral to a PDE**, it falls within the product's conformity assessment and its Annex VII documentation, even though standalone SaaS is generally outside CRA product scope [1][5]. *(Legal obligation — assess integration.)*
- **Update and CVD infrastructure is conformity evidence.** Module H and the Annex VII documentation both reach the manufacturer's **processes**; reliable hosted update-distribution (signed updates, rollback) and vulnerability-intake/PSIRT infrastructure are part of demonstrating conformity, not just operations [1]. *(Best practice grounded in a legal outcome.)*
- **The manufacturer remains the obligated party.** Relying on an IaaS/PaaS provider for the product back end does not shift conformity duties; contractually secure the provider's cooperation on documentation, quality-system evidence (Module H surveillance) and vulnerability handling [1]. *(Best practice.)*
- **CE-marking hosting for software.** Because software may bear the CE marking on the **accompanying website** (Art. 30), the hosting of that declaration/marking page must be durable and version-controlled to match each released version [1]. *(Best practice.)*

# Game Hosting Considerations

- **Connected game hardware often lands in Annex III.** Consoles, connected controllers, VR headsets and smart-home-style companion devices can be **important PDE** — e.g. products with VPN, network-management or security functionalities — pulling them into a **notified-body route** rather than self-assessment; classify each SKU [1][5]. *(Legal obligation — assess class.)*
- **Game clients and launchers are default PDE (usually).** A downloadable client with a data connection is a PDE but typically **default class**, so **Module A self-assessment** is available — provided the Annex VII documentation, DoC and CE marking (on the DoC or store/website page) are produced [1]. *(Interpretation + obligation.)*
- **Anti-cheat and DRM drivers raise the assessment bar.** Kernel-level anti-cheat, DRM and networking stacks are security-sensitive; where they implement access-control or security functionalities they can tip a client toward **Annex III Class I**, changing the route; consumer-IoT baselines such as **ETSI EN 303 645** inform the underlying Annex I posture pending CRA-specific harmonised standards. Document the analysis [1][10]. *(Legal obligation once triggered.)*
- **Support period meets live-ops.** Free security updates and the CVD process must persist for the declared support period even after feature updates cease; bake this into the conformity documentation and the DoC's referenced processes [1]. *(Legal obligation.)*

# AI Considerations

- **AI-embedding PDE follow the same conformity chain.** A product embedding AI/ML is a PDE and uses the Art. 32 routes and the Annex VII/V/VIII deliverables like any other PDE [1]. *(Legal obligation.)*
- **CRA ↔ AI Act dovetailing avoids double third-party assessment.** For a **high-risk AI system that is also a PDE**, the AI Act (Art. 43 / Annex VI) is designed so that a CRA conformity assessment can be relied on for the AI Act's cybersecurity requirement to the extent covered — reducing duplicate notified-body work while both instruments still apply [1][4]. See `ai-act-high-risk` for the AI-side mechanics. *(Cross-reference; obligation under both.)*
- **Certification interfaces.** Where a European cybersecurity certification scheme (EUCC) covers the AI-embedding product, a "substantial"-level certificate can serve as the CRA route (Art. 32) and evidence for the AI Act cybersecurity duty [2][3][4]. *(Best practice.)*
- **Extend the SBOM and documentation to models.** The Annex VII documentation and the assessed vulnerability-handling processes should cover **model and data provenance** and AI-specific attack surface (poisoning, adversarial inputs), which the Annex I risk assessment must address [1]. *(Best practice, grounded in the Annex I risk-assessment duty.)*

# Operational Guidance

Labels: **OBLIGATION** (where the CRA requires the outcome) / **BEST PRACTICE** (standards consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

**Conformity-route decision tree (Art. 32):**

1. **Is the PDE listed in Annex IV (critical)?**
   - **Yes** → Is mandatory certification required by a delegated act under Art. 8(1) and a scheme in place? If **yes**, use a **European cybersecurity certification scheme (Art. 8)**. If **no**, use a **Class II route** — Module B+C, Module H, or a "substantial" certification scheme.
2. **Else, is the PDE listed in Annex III Class II (important, higher risk)?**
   - **Yes** → **Module B+C**, **Module H**, or a **"substantial" certification scheme**. *(No Module A self-assessment.)*
3. **Else, is the PDE listed in Annex III Class I (important)?**
   - **Yes** → Have you applied **harmonised standards / common specifications / a "substantial" certification scheme** in full, covering the relevant Annex I requirements?
     - **Yes** → **Module A self-assessment** is available.
     - **No / only in part / none exist** → **Module B+C** or **Module H** (notified body required).
4. **Else (default PDE)** → **Module A self-assessment** (or any higher route voluntarily). FOSS in an Annex III category may use Module A if its Annex VII documentation is **made public** (Art. 32(5)).

*(All of the above is OBLIGATION, per Art. 32 [1][5].)*

**Executing the chosen route and CE marking:**

1. **Perform the Art. 13 cybersecurity risk assessment** and implement Annex I (Parts I and II); this is the substance the assessment verifies. *(OBLIGATION.)* [1]
2. **Assemble the Annex VII technical documentation** before market placement; keep it current and available for **≥10 years or the support period**. *(OBLIGATION.)* [1]
3. **Run the selected Annex VIII module.** For B+C or H, **engage a notified body** (available from 11 Jun 2026); obtain the EU-type examination certificate (B) or QMS approval (H). *(OBLIGATION.)* [1][5]
4. **Set and publish the support period** (≥5 years or expected use) with committed free security updates. *(OBLIGATION.)* [1]
5. **Draw up the EU declaration of conformity** (Art. 28, Annex V; simplified Annex VI where used). *(OBLIGATION.)* [1]
6. **Affix the CE marking** (Arts. 29–30) — on the product/packaging, or for software on the DoC or accompanying website; add the notified body's number where Module H applies. *(OBLIGATION.)* [1]
7. **Align importers and distributors** — verify CE marking, the DoC and documentation before making the PDE available (Arts. 19–20). *(OBLIGATION for those operators.)* [1]
8. **Track harmonised standards and certification schemes** — adopt harmonised standards on *Official Journal* citation to gain the Art. 27 presumption (and to unlock Class I self-assessment), and monitor EUCC coverage. *(EDITORIAL RECOMMENDATION.)* [8][9]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Misclassifying an important/critical PDE as default and self-assessing when a notified body is required | Medium | High | Arts. 7–8, 32; Annex III/IV [1] | Documented per-SKU classification; re-check on function change | Low |
| R2 | Assuming Class I self-assessment before harmonised standards are cited | High | High | Art. 32(2); Art. 27 [1][8] | Track OJ citations; plan Module B+C/H interim; use certification | Medium |
| R3 | Engaging a notified body too late (capacity crunch before 11 Dec 2027) | Medium | High | Chapter IV from 11 Jun 2026; Art. 71 [1][5] | Early notified-body engagement; book against the 2026 window | Medium |
| R4 | Wrong or incomplete Annex VII technical documentation | Medium | High | Art. 31; Annex VII [1] | Generate from SDLC; documentation review before placement | Low |
| R5 | Defective/ absent EU declaration of conformity or CE marking | Medium | High | Arts. 28–30 [1] | DoC template (Annex V); CE-marking checklist below | Low |
| R6 | Citing the wrong annex (e.g. "Annex VI" for modules) in documentation | Medium | Medium | Annex V/VI/VII/VIII structure [1] | Use verified annex map; peer review of references | Low |
| R7 | Under-provisioned support period undermining conformity evidence | Medium | Medium | Art. 13(8), (13) [1] | Commit ≥5-yr free updates; lifecycle budget; document | Low |
| R8 | Importer/distributor makes a non-compliant PDE available | Medium | High | Arts. 19–20 [1] | Verification controls on CE marking, DoC, documentation | Low |
| R9 | Treating a certification scheme as available before EUCC covers the product | Medium | Medium | Art. 32; Impl. Reg (EU) 2024/482 [2][3] | Confirm scheme scope/level; fall back to notified-body route | Medium |

# Implementation Roadmap

- **Phase 0 — Classify & choose route:** Per-SKU classification (default / Class I / Class II / critical); run the decision tree; record the chosen Art. 32 route. *Effort:* Medium. *Depends on:* `cyber-resilience-act` scope triage.
- **Phase 1 — Annex I readiness:** Ensure the product properties (Part I) and vulnerability-handling processes (Part II) are in place — the substance the assessment verifies. *Effort:* High.
- **Phase 2 — Documentation & DoC:** Build Annex VII technical documentation; prepare the Annex V declaration of conformity; set the support period. *Effort:* Medium.
- **Phase 3 — Assessment execution:** Run Module A internally, or engage a **notified body** for B+C or H (from 11 Jun 2026), or obtain an EUCC certificate; resolve findings. *Effort:* High.
- **Phase 4 — CE marking & market access:** Affix CE marking (Arts. 29–30); finalise the DoC; align importer/distributor verification — **before 11 Dec 2027**. *Effort:* Medium.
- **Phase 5 — Sustain & re-assess:** Maintain documentation for ≥10 years / support period; adopt harmonised standards on citation to move Class I products to self-assessment; re-assess on substantial modification. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No classification; conformity route unknown; no documentation. | No class register; no Annex VII docs. |
| 2 | Managed | Products classified; route chosen per SKU; documentation started. | Classification register; draft technical documentation. |
| 3 | Defined | Annex VII documentation complete; support period set; route execution planned (notified body identified where needed). | Documentation pack; notified-body engagement plan; DoC drafted. |
| 4 | Quantitatively Managed | Assessment executed; metrics on documentation completeness and finding closure; DoC issued; CE marking applied. | EU-type certificate / QMS approval; CE marking; KPIs. |
| 5 | Optimising | Harmonised-standards presumption (or certification) secured; Class I products self-assess; continuous re-assessment on change. | OJ-cited standard alignment / EUCC; integrated CRA+AI Act conformity. |

# Audit Questions

1. For each PDE, what is the documented class (default / Class I / Class II / critical), and how was it derived from Annexes III–IV? *(Arts. 7–8 [1].)*
2. Which Art. 32 route was selected, and — for Class I — is the reliance on harmonised standards / certification for self-assessment justified given that standards may not yet be cited? *(Art. 32; Art. 27 [1][8].)*
3. Where a notified body is required (Class II / certain Class I / critical), which body is engaged and when, relative to the 11 Jun 2026 availability and 11 Dec 2027 deadline? *(Chapter IV; Art. 71 [1][5].)*
4. Does the Annex VII technical documentation exist, is it current, and is it retained for ≥10 years or the support period? *(Arts. 31, 13(13) [1].)*
5. Is the EU declaration of conformity drawn up to the Annex V model, and is the CE marking affixed per Arts. 29–30 (incl. the notified-body number for Module H)? *(Arts. 28–30 [1].)*
6. Is the support period set (≥5 years or expected use) with committed free security updates, and is that reflected in the conformity evidence? *(Art. 13(8) [1].)*
7. How do importers and distributors verify CE marking, the DoC and documentation before making a PDE available? *(Arts. 19–20 [1].)*
8. For AI-embedding or certified products, how is CRA conformity coordinated with the AI Act cybersecurity requirement and any EUCC certificate? *([2][3][4].)*

# Implementation Checklist

**CE-marking checklist (per PDE):**

- [ ] Product classified (default / important Class I / important Class II / critical) with recorded reasoning (Arts. 7–8; Annex III/IV).
- [ ] Conformity route selected via the Art. 32 decision tree; class restrictions respected.
- [ ] Annex I Part I (product properties) and Part II (vulnerability handling: SBOM, CVD, secure updates) implemented.
- [ ] Art. 13 cybersecurity risk assessment performed and documented.
- [ ] Support period set (≥5 years or expected use) with free security updates committed (Art. 13(8)).
- [ ] Annex VII technical documentation drawn up before placing on the market (Art. 31).
- [ ] Chosen Annex VIII module executed — Module A internally, or notified body engaged for Module B+C / H, or EUCC certificate obtained (from 11 Jun 2026 for notified bodies).
- [ ] EU declaration of conformity drawn up to the Annex V model (simplified Annex VI where used) (Art. 28).
- [ ] CE marking affixed per Arts. 29–30 (product/packaging, or DoC/website for software; notified-body number where Module H).
- [ ] Technical documentation and DoC retained for ≥10 years or the support period (Art. 13(13)).
- [ ] Importer (Art. 19) and distributor (Art. 20) verification controls operating where applicable.
- [ ] Harmonised standards / EUCC coverage tracked; Class I products moved to self-assessment on OJ citation; re-assess on substantial modification.

# References

*All external links verified live (HTTP 200) on 2026-07-11 (`sources_verified`) using `curl -L -A "Mozilla/5.0"`. The conformity routes, module-to-Annex-VIII mapping, class restrictions (Art. 32), annex structure (V/VI/VII/VIII), CE-marking articles (29–30), notified-body chapter (Arts. 35–51) and the Art. 71 application dates were read directly from the primary text.*

## Primary Sources

- [1] **Regulation (EU) 2024/2847 (Cyber Resilience Act).** Classification (Arts. 7–8; Annexes III, IV); manufacturer sequence and support period/retention (Art. 13); importers/distributors/stewards (Arts. 19, 20, 24); presumption of conformity (Art. 27); EU declaration of conformity (Art. 28; Annexes V, VI); CE marking (Arts. 29–30); technical documentation (Art. 31; Annex VII); conformity-assessment procedures and modules (Art. 32; Annex VIII); notified bodies (Chapter IV, Arts. 35–51); application dates (Art. 71). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/2847/oj
- [2] **Regulation (EU) 2019/881 (Cybersecurity Act).** ENISA mandate and the **European cybersecurity certification framework**; underpins the CRA certification route (Art. 32) and mandatory certification for critical products (Art. 8). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2019/881/oj
- [3] **Commission Implementing Regulation (EU) 2024/482 (EUCC).** The European Common Criteria-based cybersecurity certification scheme — the first adopted scheme usable as a CRA conformity route at assurance level ≥ "substantial". EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_impl/2024/482/oj
- [4] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** High-risk conformity assessment (Art. 43; Annexes VI, VII) that dovetails with CRA conformity for AI-embedding PDE. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj

## Regulatory Guidance

- [5] **The Cyber Resilience Act — summary of the legislative text.** Confirms the risk-scaled conformity routes (self-assessment for default; third-party for important Class II and critical; Class I self-assessment only where standards/schemes are applied), CE marking, and the phased dates (notified-body provisions 11 Jun 2026; reporting 11 Sep 2026; full application 11 Dec 2027). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cra-summary
- [6] **Cyber Resilience Act** (policy overview — mandatory lifecycle cybersecurity, CE marking as the conformity signal). European Commission. https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act
- [7] **Single Reporting Platform (SRP).** ENISA-operated single entry point (operational by 11 Sep 2026); context for the notified-body/reporting sequencing. ENISA. https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp
- [8] **Cyber Resilience Act Requirements — Standards Mapping (JRC & ENISA joint analysis).** Maps Annex I to existing/forthcoming standards and identifies gaps — evidence that harmonised standards (and thus Class I self-assessment via Art. 27) are not yet complete. ENISA / European Commission JRC. https://www.enisa.europa.eu/publications/cyber-resilience-act-requirements-standards-mapping
- [9] **EU cybersecurity certification framework.** The framework (under the Cybersecurity Act) within which the EUCC and future schemes provide the CRA certification route. European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cybersecurity-certification-framework

## Standards

- [10] **ETSI EN 303 645** — Cyber Security for Consumer Internet of Things: Baseline Requirements. A consumer-IoT baseline informing Annex I conformity pending citation of CRA-specific harmonised standards. ETSI. https://www.etsi.org/deliver/etsi_en/303600_303699/303645/02.01.01_60/en_303645v020101p.pdf
- [11] **ISO/IEC 27001:2022** — Information security management systems — Requirements. Process assurance supporting the manufacturer's quality-management evidence under Module H. ISO. https://www.iso.org/standard/27001

## Academic Sources

Not Applicable — this conformity-focused deep-dive relies on the primary Regulation, the Cybersecurity Act and its EUCC implementing regulation, and official Commission/ENISA sources. Academic critique of the conformity-assessment burden and the notified-body capacity question will be cited in `cra-standards-mapping` and `cra-open-source` as those documents are produced.

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Commission — Cyber Resilience Act policy hub (delegated/implementing acts, FAQs as adopted). https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act
- ENISA — Product security and certification materials. https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp

# Related Documents

- `cyber-resilience-act` — the CRA foundation (scope, PDE, Annex I, classes, reporting, penalties); this document **details its conformity-assessment and CE-marking material** (**prerequisite reading**).
- `ai-act-high-risk` — the closely analogous AI Act conformity chain (internal control vs. notified body; declaration of conformity; CE marking); read alongside for the NLF pattern and the CRA↔AI Act dovetailing.
- `cybersecurity-foundations` — general assurance frameworks (ISO/IEC 27001, NIST CSF) underpinning the quality-management evidence.
- `nis2-foundations` — entity-security complement (different obligated party; runs in parallel).
- `cra-standards-mapping` — harmonised-standards mapping against Annex I that will unlock Class I self-assessment (planned).
- `cra-open-source` — open-source software steward conformity regime in depth (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Deep-dive on CRA conformity assessment and CE marking, detailing the parent `cyber-resilience-act`. Researched and **live-verified against the primary text (Reg (EU) 2024/2847 on EUR-Lex)**: the four Art. 32 routes and their mapping to **Annex VIII** Modules A / B+C / H / certification; the class-based route restrictions (Art. 32(1)–(6): default self-assess; Class I self-assess only if harmonised standards/common specs/"substantial" certification applied, else notified body; Class II notified body/certification; critical mandatory certification per Art. 8 or a Class II route; FOSS Module A with public documentation); presumption of conformity (Art. 27); EU declaration of conformity (Art. 28; model **Annex V**, simplified **Annex VI**); CE marking (Arts. **29–30**); technical documentation (Art. 31; **Annex VII**) with ≥10-year/support-period retention (Art. 13(13)); support period ≥5 years (Art. 13(8)); and the notified-body chapter (**Chapter IV, Arts. 35–51**). **Application dates verified from Art. 71: entry into force 10 Dec 2024; Chapter IV from 11 Jun 2026; Art. 14 reporting from 11 Sep 2026; full application 11 Dec 2027.** Corrected a parent-document annex mismatch: conformity procedures live in **Annex VIII** (parent said Annex VI, which is in fact the *simplified* DoC), and CE marking/conformity sit in **Chapter III (Arts. 27–34)** while **Chapter IV (Arts. 35–51)** is the notified-body regime. Added EUCC (Impl. Reg (EU) 2024/482) as the certification route. All 11 external links returned HTTP 200. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster B); full-repo validator/link/lint suite green; frozen in release 0.16.0. | Orchestrator (QA-verified) |

</content>
</invoke>
