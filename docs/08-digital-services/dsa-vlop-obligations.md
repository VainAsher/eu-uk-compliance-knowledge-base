---
id: dsa-vlop-obligations
title: "EU Digital Services Act: VLOP & VLOSE Obligations"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: Digital Services
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [dsa-foundations, dma-obligations, ai-act-foundations, gdpr-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [dsa, digital-services-act, vlop, vlose, systemic-risk, risk-assessment, risk-mitigation, independent-audit, recommender-systems, advertising-repository, researcher-data-access, compliance-function, transparency-reporting, supervisory-fee, commission-enforcement]
legal_basis: Regulation (EU) 2022/2065
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dsa-vlop-obligations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.15.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer (loop-authorised) — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is the Section 5 deep dive that expands the parent overview `dsa-foundations`. DSA enforcement against VLOPs/VLOSEs is **active and fast-moving**: the designated-platform list changes as services cross or fall below the user threshold, proceedings are opened and closed, decisions are appealed, and the supervisory-fee methodology is being re-adopted following its annulment by the General Court. The designation and enforcement facts below were **live-verified against European Commission and Court of Justice sources on 2026-07-11**; always re-confirm the current list, the status of open proceedings and any appeals before relying on them.

# Executive Summary

The heaviest tier of the **EU Digital Services Act (Regulation (EU) 2022/2065**, "DSA") sits in **Section 5 of Chapter III (Articles 33–43)** and applies only to **Very Large Online Platforms (VLOPs)** and **Very Large Online Search Engines (VLOSEs)** — services the European Commission has **designated** for reaching **at least 45 million average monthly active recipients in the Union** (Art. 33) [1]. These obligations are **additional and cumulative**: a VLOP already owes every duty of an intermediary, hosting service and online platform, and then this systemic layer on top [1]. This document works through that layer clause by clause and maps it to engineering, governance and enforcement reality.

The Section 5 duties are a governance programme, not a feature list: an annual **systemic-risk assessment** across four risk categories (Art. 34); **risk mitigation** measures that are reasonable, proportionate and effective (Art. 35); a Commission-triggered **crisis-response mechanism** (Art. 36); an **independent annual audit** at the provider's own expense (Art. 37); a **non-profiling recommender option** (Art. 38); a public, API-searchable **advertising repository** (Art. 39); **data access** for the Commission, national coordinators and **vetted researchers** (Art. 40); an independent **compliance function** (Art. 41); enhanced **transparency reporting** every six months (Art. 42); and an annual **supervisory fee** capped at 0.05% of worldwide net income (Art. 43) [1]. Enforcement of these systemic duties is the **European Commission's exclusive competence** (Art. 56), backed by fines of **up to 6% of total worldwide annual turnover** (Art. 74) and periodic penalty payments up to **5% of average daily turnover** (Art. 76) [1].

This is now live law. On **5 December 2025** the Commission issued its **first DSA non-compliance fine — €120 million against X** — for a deceptive "verified account" design, a non-compliant Article 39 ad repository and Article 40 researcher-access barriers [8][9]. In **October 2025** it issued **preliminary findings against TikTok and Meta** on researcher data access and (for Meta) notice-and-action and appeals [10]. And on **10 September 2025** the **General Court annulled** the Commission's Article 43 supervisory-fee decisions for Facebook, Instagram and TikTok, though it kept their effects in force while the methodology is re-adopted [3].

# Key Takeaways

- **Designation is the trigger and it is dynamic.** The Commission designates a service as a VLOP/VLOSE once it reports **≥ 45 million average monthly active EU recipients** (Art. 33); the Section 5 obligations bite **four months after** designation is notified [1]. The published list (updated **10 July 2026**) covers **20+ VLOPs and two VLOSEs (Google Search, Bing)** and changes over time [6]. *(Legal obligation — verify the live list.)*
- **Systemic-risk assessment (Art. 34) is the keystone.** VLOPs/VLOSEs must assess, **at least annually** and before launching functionalities with critical impact, four risk categories: illegal content; fundamental rights; civic discourse, elections and public security; and gender-based violence, public health, minors and physical/mental well-being [1]. *(Legal obligation.)*
- **Mitigation (Art. 35) must be effective, not cosmetic.** Measures must be reasonable, proportionate and tailored to the identified risks — spanning design, moderation, recommender and advertising systems, and terms [1]. *(Legal obligation.)*
- **Independent audits (Art. 37) run annually at the provider's cost**, with an audit opinion (positive / positive-with-comments / negative) and an **audit implementation report** the provider must act on [1]. *(Legal obligation.)*
- **Recommender, advertising and researcher-access duties are the enforcement front line.** VLOPs must offer a **non-profiling recommender option** (Art. 38), publish an **advertising repository** (Art. 39), and give **vetted researchers** data access (Art. 40) — the last two central to the X fine and the TikTok/Meta findings [1][8][10]. *(Legal obligation.)*
- **Governance is mandated:** an independent **compliance function** with compliance officers reporting to management (Art. 41), enhanced **transparency reports every six months** (Art. 42), and an annual **supervisory fee** capped at **0.05% of worldwide net income** (Art. 43) [1]. *(Legal obligation.)*
- **The Commission enforces Section 5 exclusively** (Art. 56), with fines up to **6% of total worldwide annual turnover** (Art. 74), periodic penalties up to **5% of average daily worldwide turnover** (Art. 76) and enhanced supervision of remedies (Art. 75) [1]. *(Legal obligation.)*
- **Worked enforcement (live-verified 2026-07-11):** first fine **€120m against X** (5 Dec 2025) for deceptive verified-account design, a deficient Art. 39 repository and Art. 40 access barriers [8][9]; **preliminary findings against TikTok and Meta** (24 Oct 2025) on Art. 40 and, for Meta, Arts 16/20 [10]; the Art. 40 **researcher-data-access delegated act** in force **29 Oct 2025** [11]; and the **General Court's annulment** of the Art. 43 fee decisions (T-55/24, T-58/24, 10 Sep 2025) [3]. *(Confirmed, not asserted.)*

# Purpose

This document gives legal, compliance, product and engineering teams an **article-level map of the VLOP/VLOSE regime** and translates each Section 5 duty into concrete obligations, controls and audit questions. It supports three tasks: (1) building a designation-readiness and Section 5 compliance programme for a platform approaching or crossing the 45-million threshold; (2) reading the Commission's enforcement practice (X, TikTok, Meta) and the General Court's supervisory-fee judgments as a guide to how each obligation is tested; and (3) providing a VLOP compliance checklist an auditor or board can use. It is the planned deep dive that `dsa-foundations` defers to and should be read after that overview.

# Scope

**In scope:** The Section 5 obligations of **Articles 33–43** clause by clause — designation (33), systemic-risk assessment (34), mitigation (35), crisis response (36), independent audit (37), recommender non-profiling option (38), advertising repository (39), data access including vetted-researcher access (40), compliance function (41), enhanced transparency reporting (42) and the supervisory fee (43); the Commission's **exclusive enforcement** architecture for these duties (Arts. 56, 66–76); and the **X / TikTok / Meta** matters and the **supervisory-fee judgments** as worked examples, live-verified.

**Out of scope (covered elsewhere or in the backlog):**

- The **tiered obligations for all intermediaries, hosting services and online platforms** (Arts. 11–32) that VLOPs also owe → parent `dsa-foundations`.
- The **systemic-risk-assessment methodology in engineering depth** (metrics, red-teaming, mitigation design) → `dsa-vlop-risk-management` (planned); this document states the Art. 34–35 legal duties and structure.
- **Recommender-system transparency** at the online-platform level (Art. 27) and the profiling opt-out mechanics in depth → `dsa-recommender-transparency` (planned).
- **Codes of conduct, crisis protocols and the Disinformation Code** (Arts. 45–48) → `dsa-codes-of-conduct` (planned); Art. 36's statutory crisis mechanism is covered here, the voluntary protocols are not.
- The **country-of-origin / Digital Services Coordinator** structure for non-VLOP duties → `dsa-foundations` [5].
- **GDPR** consent, profiling and DPbDD detail underpinning Arts. 38–40 → `gdpr-foundations` [4]; **AI Act** overlap for recommender/moderation AI → `ai-act-foundations`.

**Assumptions:** The reader has read `dsa-foundations` and understands the intermediary tiers, notice-and-action and the enforcement split. Personal-data processing by a VLOP remains governed by the **GDPR** in parallel [4].

# Definitions

*Shared terms (VLOP/VLOSE, intermediary service, online platform, DSC) are in `GLOSSARY.md`. Section 5-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| VLOP / VLOSE | An online platform / online search engine designated by the Commission under Art. 33 for reaching **≥ 45 million average monthly active recipients in the Union**; the threshold is 10% of the ~450m EU population. | [1] |
| Average monthly active recipients (AMAR) | The count of recipients actually engaging with a service at least once in a given period, averaged over six months (Art. 3(p) / Recital area); the metric that drives both designation (Art. 33) and the supervisory fee (Art. 43). It must be defined uniformly across the DSA — the point on which the fee decisions were annulled. | [1][3] |
| Systemic risk | A risk stemming from the design, functioning or use of a VLOP/VLOSE (including algorithmic systems) that falls within one of the four Art. 34(1) categories, assessed at Union level. | [1] |
| Risk-mitigation measure | A reasonable, proportionate and effective measure under Art. 35 tailored to an identified systemic risk (e.g. adapting design, recommender or advertising systems, moderation, terms, or awareness measures). | [1] |
| Crisis (Art. 36) | Extraordinary circumstances leading to a **serious threat to public security or public health** in the Union, allowing the Commission (on Board recommendation) to require assessment and time-limited mitigation. | [1] |
| Independent audit | The annual, provider-funded audit under Art. 37 of the Section 5 obligations and any commitments, performed by independent auditors and yielding an audit opinion and operational recommendations. | [1] |
| Advertising repository | The public, searchable, API-accessible database each VLOP/VLOSE must maintain under Art. 39 containing specified information on each advertisement presented, kept for one year after last presentation. | [1] |
| Vetted researcher | A researcher granted data access under Art. 40(4)–(8), vetted by the Digital Services Coordinator of establishment against independence, funding-disclosure, data-security and research-purpose criteria, to study systemic risks. | [1][11] |
| Compliance function | The independent function under Art. 41 with one or more compliance officers, whose head reports directly to senior management, resourced and empowered to monitor Section 5 compliance. | [1] |
| Supervisory fee | The annual fee under Art. 43 that VLOPs/VLOSEs pay towards the Commission's supervisory costs, capped per provider at **0.05% of its worldwide annual net income** in the preceding year. | [1][2] |

# Background

When the DSA was designed, the EU legislature judged that the largest platforms and search engines pose **societal-scale risks** that ordinary due-diligence duties do not address: their reach means that design choices, recommender algorithms and advertising systems can shape public discourse, elections, public health and minors' safety across the whole Union [1][5]. Section 5 is the response — a **risk-based, systemic** layer modelled more on financial-sector prudential regulation (assess, mitigate, audit, supervise) than on classic content law.

The regime went live quickly. The Commission designated the **first VLOPs and VLOSEs on 25 April 2023**, and their Section 5 obligations applied about four months later, in **late August 2023** — well before the DSA became fully applicable to all intermediaries on 17 February 2024 [1][7]. The Commission stood up the **European Centre for Algorithmic Transparency (ECAT)** to support technical scrutiny, opened formal proceedings against several platforms through 2024, adopted the **Article 40 researcher-data-access delegated act** (in force 29 October 2025), issued its **first fine** in December 2025, and saw its **supervisory-fee methodology annulled** by the General Court in September 2025 [3][8][11]. The obligations are therefore stable in the statute but **dynamic in enforcement**, which is why this document flags every enforcement fact as live-verified.

# Legal Framework

Section 5 of Chapter III (Arts. 33–43) applies **on top of** the obligations for intermediary services (Arts. 11–15), hosting services (Arts. 16–18) and online platforms (Arts. 19–28), and — for VLOP marketplaces — Section 4 (Arts. 29–32) [1]. The structure runs from designation, through the substantive risk-governance duties, to fees:

- **Designation (Art. 33)** — the ≥ 45m-AMAR threshold, the Commission designation decision, and the four-month lead-in before Section 5 applies.
- **Risk governance (Arts. 34–37)** — systemic-risk assessment (34), mitigation (35), crisis response (36), independent audit (37).
- **Transparency and user-empowerment duties (Arts. 38–40)** — non-profiling recommender option (38), advertising repository (39), data access for authorities and vetted researchers (40).
- **Institutional duties (Arts. 41–43)** — compliance function (41), enhanced transparency reporting (42), supervisory fee (43).
- **Enforcement (Chapter IV, Section 4, Arts. 56, 64–76)** — the Commission's **exclusive competence** over Section 5 (Art. 56), investigatory powers (Arts. 66–72), non-compliance decisions (Art. 73), **fines up to 6%** (Art. 74), enhanced remedy supervision (Art. 75) and **periodic penalty payments up to 5%** of average daily turnover (Art. 76) [1].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 33 | **Designation**: Commission designates online platforms/search engines with **≥ 45m average monthly active EU recipients**; obligations apply **4 months** after notification; providers report user numbers (Art. 24(2)) at least every 6 months. | [1] |
| Art. 34 | **Systemic-risk assessment**: diligently identify, analyse and assess systemic risks **at least annually** and before deploying critical-impact functionalities, across four risk categories; keep supporting documents ≥ 3 years. | [1] |
| Art. 35 | **Mitigation of systemic risks**: put in place reasonable, proportionate and effective measures tailored to the risks (design, recommender/advertising systems, moderation, terms, awareness, codes, crisis protocols). | [1] |
| Art. 36 | **Crisis-response mechanism**: on the Board's recommendation the Commission may require a VLOP/VLOSE to assess its contribution to a serious threat to **public security or public health** and apply time-limited (≤ 3 months) mitigation. | [1] |
| Art. 37 | **Independent audit**: at least annually, at the provider's expense, by independent qualified auditors; audit report with an **opinion** and operational recommendations; provider adopts an **audit implementation report**. | [1] |
| Art. 38 | **Recommender systems**: provide at least one option **not based on profiling** (as defined in GDPR Art. 4(4)). | [1][4] |
| Art. 39 | **Advertising transparency**: maintain a public, multi-criteria-searchable, **API-accessible repository** of ads with specified fields, retained for **1 year** after the ad's last presentation. | [1] |
| Art. 40 | **Data access and scrutiny**: give the DSC of establishment / Commission data access on reasoned request; give **vetted researchers** access to study systemic risks (40(4)); give access to publicly available data (40(12)); conditions set by delegated act. | [1][11] |
| Art. 41 | **Compliance function**: independent function with one or more **compliance officers**; its head reports directly to senior management; adequate authority, standing and resources. | [1] |
| Art. 42 | **Transparency reporting**: publish Art. 15/24 reports **at least every six months**, with VLOP-specific additions (content-moderation human resources, audit reports, risk assessments, AMAR every six months). | [1] |
| Art. 43 | **Supervisory fee**: pay an annual fee toward the Commission's supervisory costs; individual fee **capped at 0.05% of worldwide annual net income**; methodology set by delegated act. | [1][2] |
| Art. 56 | **Enforcement competence**: the Commission has **exclusive** powers over the Section 5 (Art. 33–43) obligations of VLOPs/VLOSEs. | [1] |
| Arts. 66–72 | Commission **investigatory and procedural powers**: initiate proceedings (66), information requests (67), interviews/inspections (68–69), interim measures (70), commitments (71), monitoring (72). | [1] |
| Art. 73 | **Non-compliance decision** finding a breach of the DSA (including Section 5) and ordering compliance. | [1] |
| Art. 74 | **Fines** up to **6% of total worldwide annual turnover** (and up to 1% for procedural infringements such as incorrect information). | [1] |
| Art. 75 | **Enhanced supervision** of remedies for systemic infringements (action plan, independent monitoring). | [1] |
| Art. 76 | **Periodic penalty payments** up to **5% of average daily worldwide turnover** to compel compliance. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited here from the primary text [1]. Recital numbers are given as approximate ranges ("area").*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 75–76 area | Rationale for the VLOP/VLOSE tier: very large services carry systemic, Union-scale risks that justify additional obligations. | [1] |
| Recital 79–83 area | The **four systemic-risk categories** (Art. 34) and the expectation of a diligent, documented assessment covering algorithmic systems. | [1] |
| Recital 87–88 area | **Mitigation (Art. 35)** must be effective and proportionate, with respect for fundamental rights and without unjustified content removal. | [1] |
| Recital 91 area | The **crisis-response mechanism (Art. 36)** as an exceptional, time-limited tool for serious public-security/health threats. | [1] |
| Recital 92–93 area | **Independent audits (Art. 37)** as an accountability mechanism; auditor independence and methodology. | [1] |
| Recital 94–95 area | The **non-profiling recommender option (Art. 38)** and the **advertising repository (Art. 39)** as transparency and user-control tools. | [1] |
| Recital 96–97 area | **Data access (Art. 40)** for supervisory authorities and vetted researchers to scrutinise systemic risks. | [1] |

## Relevant Case Law

Unlike the substantive risk duties — for which there is still **no CJEU merits ruling** — the **supervisory fee (Art. 43)** has already produced binding case law from the General Court, and challenges to designation and to the X fine are emerging.

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Meta Platforms Ireland v Commission | General Court, **T-55/24**, judgment **10 September 2025** (Press release CP 114/25) | **Annulled** the Commission's 2023 implementing decision setting the **Art. 43 supervisory fee** for Facebook and Instagram: the methodology for calculating **average monthly active recipients** had to be laid down in a **delegated act** (Art. 43(4)), not in individual implementing decisions. Effects **maintained** for up to 12 months to let the Commission re-adopt. | Directly constrains how the Art. 43 fee — and the AMAR concept underpinning designation — must be operationalised. [3] |
| TikTok Technology v Commission | General Court, **T-58/24**, judgment **10 September 2025** (Press release CP 114/25) | Same holding as T-55/24 for TikTok's Art. 43 fee; decision annulled, effects provisionally maintained. | Confirms the ruling is not platform-specific; the fee methodology must be re-based in a delegated act. [3] |

*Appeals of these judgments, any challenge to the €120m X fine, and General Court challenges to VLOP **designation** are **emerging** and are tracked in the enforcement backlog rather than asserted here.* [3][8]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (European Commission / Court — not statutory text unless a specific article is cited).**

- **Designation is dynamic and closely managed.** The Commission designates services as they cross the 45m threshold and ends designation when they fall below it; its published list — updated **10 July 2026** — covers **20+ VLOPs and two VLOSEs (Google Search, Bing)** [6], and the Commission maintains a dedicated VLOP/VLOSE supervision hub [12]. *(Regulatory interpretation — verify the live list.)*
- **The advertising repository and researcher access are outcome-tested.** The **€120m X decision (5 Dec 2025)** found X's ad repository non-compliant because of "design features and access barriers, such as excessive delays" and missing fields, and found that X imposed "unnecessary barriers" on eligible researchers accessing public data — an Art. 39 and Art. 40 reading, alongside a deceptive "verified account" design [8][9]. *(Regulatory interpretation — first final decision.)*
- **Researcher data access (Art. 40) is a standing priority.** The **preliminary findings against TikTok and Meta (24 Oct 2025)** turned on inadequate researcher access to public data for **both**, and — for Meta's Facebook and Instagram — deficient **notice-and-action** and **appeal** mechanisms [10]. The Commission then made Art. 40(4) operational via the **data-access delegated act** (adopted 2 July 2025; in force **29 October 2025**), through which vetted researchers apply via a **Data Access Portal** [11]. *(Regulatory interpretation — preliminary findings are not final.)*
- **The supervisory fee must be re-based.** The General Court's **annulment** of the Art. 43 fee decisions (T-55/24, T-58/24) means the AMAR methodology must be set by **delegated act**; the fee owed is not extinguished, but the calculation is being corrected [3]. *(Legal fact — verified.)*
- **The Commission alone enforces Section 5.** National Digital Services Coordinators supervise the lower tiers, but the **Commission holds exclusive competence** over the VLOP/VLOSE systemic obligations (Art. 56), which is why the X, TikTok and Meta actions are Commission-led [1][5]. *(Regulatory interpretation.)*
- **Verification note:** the designation list, the open TikTok/Meta proceedings, the X appeal status and the re-adoption of the fee methodology were confirmed against Commission and Court sources on **2026-07-11**; these are the items most likely to change and must be re-checked at each review [3][6][8][10]. *(Editorial recommendation.)*

# Technical Considerations

- **Instrument the AMAR metric first.** Both designation (Art. 33) and the fee (Art. 43) turn on **average monthly active recipients**; the General Court has held the concept must be applied uniformly [1][3]. Build a defensible, documented counting methodology early — it is the number regulators and courts scrutinise. *(Legal obligation once in scope.)*
- **Treat the systemic-risk assessment as an engineering artefact (Art. 34).** It must cover **algorithmic systems** — recommender, ranking, ad-targeting and moderation models — and be repeated before shipping critical-impact functionality, not just annually [1]. This demands model documentation, red-teaming and metrics pipelines. *(Legal obligation.)*
- **Build the advertising repository as a real product (Art. 39).** It must be **public, multi-criteria searchable and API-accessible**, carry specified fields (content, advertiser, who paid, period, targeting parameters, recipients reached), and retain records **one year** after last presentation; the X decision shows delays and access barriers count as non-compliance [1][8]. *(Legal obligation.)*
- **Stand up vetted-researcher and public-data access interfaces (Art. 40).** Following the delegated act (in force 29 Oct 2025), VLOPs must support the Data Access Portal workflow, structured data formats and documentation for vetted researchers, plus access to publicly available data under Art. 40(12) [1][11]. *(Legal obligation.)*
- **Ship a genuine non-profiling recommender option (Art. 38).** At least one feed option must not rely on **profiling** as defined in GDPR Art. 4(4) — i.e. not built from inferred behavioural profiles — and must be a real, selectable alternative [1][4]. *(Legal obligation.)*
- **Make transparency reporting a data pipeline (Art. 42).** Reports are due **every six months** with VLOP-specific content (moderation human resources, audit and risk-assessment outputs, AMAR), so reporting must be automated from moderation and analytics systems rather than hand-assembled [1]. *(Legal obligation.)*

# Hosting Considerations

- **Section 5 attaches to the platform provider, not the underlying cloud.** A hyperscale host that merely provides infrastructure to a VLOP is not itself a VLOP; the designated provider carries the Art. 33–43 duties [1]. Hosting/IaaS providers should nonetheless expect **contractual flow-down** — VLOP customers will require data-export, logging and availability support to meet audit (Art. 37), repository (Art. 39) and data-access (Art. 40) duties. *(Interpretation — assess contracts.)*
- **Data-access and repository interfaces have real infrastructure cost.** Public API repositories (Art. 39) and researcher-access portals (Art. 40) imply durable storage, rate-limited public APIs, and one-year+ retention pipelines — capacity and resilience the hosting layer must underwrite [1]. *(Best practice for in-scope providers.)*
- **Audit-grade logging and retention.** Art. 34 requires supporting documents to be retained (≥ 3 years) and Art. 37 audits require evidence; hosting and logging architecture should preserve tamper-evident records across the assessment and audit cycle [1]. *(Best practice; ISO 19011 audit-evidence principles apply [13].)*

# Game Hosting Considerations

- **A very large game platform can be designated.** If a game or game-adjacent service **stores and disseminates user content to the public** (public forums, mod hubs, shared creations, public feeds) and reaches **45m average monthly EU recipients**, it can be designated a VLOP and inherit all of Section 5 [1][6]. Monitor AMAR against the threshold. *(Legal obligation once designated; best practice to pre-assess.)*
- **Minor-protection is a named systemic-risk vector.** Art. 34's fourth category expressly covers **minors** and physical/mental well-being; a large game audience of under-18s makes child-safety design, default settings and monetisation flows central to the risk assessment and mitigation (Arts. 34–35), reinforcing the online-platform minor-protection duty (Art. 28) [1]. *(Legal obligation.)*
- **Recommender and engagement mechanics are in scope.** Algorithmic content/feed ranking and engagement-optimising design fall within Arts. 34–35 and the Art. 38 non-profiling option; "addictive design" and dark-pattern risks are assessable systemic risks for large platforms [1]. *(Legal obligation once designated.)*
- **Real-time gameplay and matchmaking are not the target.** Section 5 addresses societal/systemic risk from public dissemination and algorithmic systems, not game-server latency or netcode; those remain governed by GDPR and, where relevant, the AI Act. *(Interpretation.)*

# AI Considerations

- **Algorithmic systems are the heart of the risk assessment.** Recommender, ranking, ad-targeting and automated-moderation models are expressly within the Art. 34 systemic-risk analysis and the Art. 35 mitigation duty; a VLOP must be able to explain and test how these AI systems generate the four categories of risk [1]. *(Legal obligation.)*
- **The non-profiling option constrains recommender AI (Art. 38).** At least one recommender configuration must not use **profiling** (GDPR Art. 4(4)) — a direct design constraint on personalised feed models [1][4]. *(Legal obligation.)*
- **AI Act overlap.** Where a VLOP deploys AI (recommenders, generative features, moderation classifiers), the **AI Act (Reg (EU) 2024/1689)** may apply in parallel, including Art. 50 transparency for AI-generated/synthetic content; the DSA governs **systemic risk**, the AI Act governs **AI risk**, and they can bind the same system at once — see `ai-act-foundations` [1]. *(Cross-reference.)*
- **GDPR overlap.** Recommender profiling, ad targeting and researcher-data pipelines all process personal data, so the **GDPR applies in full** (lawful basis, DPbDD, Art. 22 safeguards); Art. 40 access to internal data must be reconciled with data-protection and confidentiality duties [1][4]. *(Legal obligation — read with `gdpr-foundations`.)*

# Operational Guidance

Labels: **OBLIGATION** (the VLOP/VLOSE must) / **BEST PRACTICE** (should) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Confirm designation status and the four-month clock.** Track AMAR; on designation, map the Section 5 lead-in (obligations apply four months after notification). *(OBLIGATION once designated.)* [1]
2. **Run the annual systemic-risk assessment (Art. 34)** across all four categories and before critical-impact launches; document methodology, algorithmic-system analysis and evidence; retain ≥ 3 years. *(OBLIGATION.)* [1]
3. **Implement and evidence mitigation (Art. 35)** tailored to each identified risk; record why measures are reasonable, proportionate and effective, and their fundamental-rights impact. *(OBLIGATION.)* [1]
4. **Commission the independent annual audit (Art. 37)**; act on the audit opinion and publish an **audit implementation report**. *(OBLIGATION; align auditor methodology with ISO 19011 principles [13].)* [1]
5. **Ship the non-profiling recommender option (Art. 38)** as a genuine, easily selectable alternative. *(OBLIGATION.)* [1][4]
6. **Operate a compliant advertising repository (Art. 39)** — public, API-searchable, complete fields, one-year retention, no access barriers or delays. *(OBLIGATION; the X decision is the benchmark.)* [1][8]
7. **Provide data access (Art. 40)** to the Commission/DSC on reasoned request, and to vetted researchers via the Data Access Portal, plus public-data access under 40(12). *(OBLIGATION.)* [1][11]
8. **Establish the compliance function (Art. 41)** — independent, resourced, with compliance officers whose head reports to senior management. *(OBLIGATION; ISO 37301 offers a management-system model [14].)* [1]
9. **Publish enhanced transparency reports every six months (Art. 42)** and report AMAR; automate from source systems. *(OBLIGATION.)* [1]
10. **Budget and validate the supervisory fee (Art. 43)**, re-checking the (re-adopted) methodology and your AMAR basis in light of the General Court judgments. *(OBLIGATION.)* [1][2][3]
11. **Prepare for Commission oversight** (Arts. 56, 66–76): evidence packs, information-request readiness, and a remedy/action-plan capability for enhanced supervision. *(BEST PRACTICE.)* [1]
12. **Maintain a live enforcement watch-list** (X appeal, TikTok/Meta proceedings, fee re-adoption, designation changes) and feed it into the annual cycle. *(EDITORIAL RECOMMENDATION.)* [3][6][8][10]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Inadequate / undocumented systemic-risk assessment | Medium | Very High | Arts. 34; Art. 74 (6%) [1] | Documented annual + pre-launch assessment; algorithmic-system analysis; evidence retention | Medium |
| R2 | Ineffective or cosmetic mitigation ("paper compliance") | Medium | Very High | Art. 35; enforcement practice [1][8] | Outcome-tested measures tied to each risk; fundamental-rights review | Medium |
| R3 | Non-compliant advertising repository (fields, delays, access barriers) | Medium | Very High | Art. 39; **X €120m** [1][8] | Complete-field, low-latency public API; one-year retention; access-barrier review | Medium |
| R4 | Inadequate vetted-researcher / public-data access | High | Very High | Art. 40; X fine; TikTok/Meta findings [1][8][10] | Data Access Portal support; structured formats; no undue barriers | Medium |
| R5 | Missing or non-genuine non-profiling recommender option | Medium | High | Art. 38 [1][4] | Real, selectable non-profiling feed; verify no hidden profiling | Low |
| R6 | Audit failure / ignored audit recommendations | Low | High | Art. 37 [1] | Independent qualified auditor; act on opinion; audit implementation report | Low |
| R7 | Weak/under-resourced compliance function; late transparency report | Low | High | Arts. 41–42 [1] | Independent function; compliance officers to management; automated reporting | Low |
| R8 | Deceptive interface / dark-pattern design in core features | Medium | High | Art. 25 + Art. 34; **X** verified-account finding [1][8] | UX review; remove manipulative design; document choices | Medium |
| R9 | Supervisory-fee / AMAR miscalculation or dispute | Medium | Medium | Art. 43; **T-55/24, T-58/24** [1][2][3] | Track re-adopted methodology; robust, uniform AMAR counting | Low |
| R10 | Unpreparedness for Commission proceedings and remedies | Low | Very High | Arts. 56, 66–76 [1] | Evidence packs; information-request readiness; action-plan capability | Medium |

# Implementation Roadmap

- **Phase 0 — Designation readiness:** Instrument AMAR; assess proximity to the 45m threshold; scope the Section 5 programme and the four-month clock. *Effort:* Medium.
- **Phase 1 — Risk governance:** Build the Art. 34 systemic-risk assessment methodology (all four categories, algorithmic-system analysis) and the Art. 35 mitigation catalogue. *Effort:* Very High.
- **Phase 2 — Transparency & user-empowerment surfaces:** Non-profiling recommender option (38), advertising repository (39), vetted-researcher and public-data access interfaces (40). *Effort:* Very High.
- **Phase 3 — Assurance:** Independent audit (37) and audit-implementation process; align auditor methodology and evidence. *Effort:* High.
- **Phase 4 — Institutional duties:** Compliance function (41), six-monthly transparency reporting (42), supervisory-fee budgeting and AMAR validation (43). *Effort:* High.
- **Phase 5 — Crisis & enforcement readiness:** Art. 36 crisis-response capability; Commission-oversight evidence packs and remedy/action-plan capability (Arts. 56, 66–76). *Effort:* Medium.
- **Phase 6 — Continuous monitoring:** Enforcement watch-list, annual re-assessment, methodology and designation-change tracking. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No Section 5 programme; AMAR not instrumented; unaware of designation exposure. | No risk assessment; no repository. |
| 2 | Managed | AMAR tracked; a first systemic-risk assessment and basic mitigation exist; repository stood up. | Art. 34 assessment drafted; Art. 39 repository live. |
| 3 | Defined | All Section 5 surfaces operational: non-profiling option, compliant repository, researcher access, compliance function, six-monthly reporting. | Arts. 34–42 operational; compliance officers appointed. |
| 4 | Quantitatively Managed | Mitigation outcome-tested with metrics; independent audit passed and recommendations closed; AMAR methodology validated. | Audit opinion positive; KPIs on repository/access; closed audit findings. |
| 5 | Optimising | Integrated DSA + GDPR + AI Act risk governance; pre-launch risk assessment embedded; live enforcement and methodology tracking. | Cross-regime programme; crisis-response tested; watch-list feeds annual cycle. |

# Audit Questions

1. How is **AMAR** measured, is the methodology documented and uniform, and how close is the service to (or over) the **45m threshold**? *(Arts. 33, 43 [1][3].)*
2. Does the **systemic-risk assessment (Art. 34)** cover all four categories and **algorithmic systems**, run at least annually and before critical-impact launches, with evidence retained? *([1].)*
3. Are **mitigation measures (Art. 35)** tied to specific identified risks, outcome-tested, and assessed for fundamental-rights impact? *([1].)*
4. Is there an **independent audit (Art. 37)** with an opinion, and an **audit implementation report** acted upon? *([1][13].)*
5. Is there a genuine **non-profiling recommender option (Art. 38)** and is it verifiably free of profiling? *([1][4].)*
6. Is the **advertising repository (Art. 39)** public, API-searchable, complete, timely and retained for a year — with no access barriers of the kind penalised in the X decision? *([1][8].)*
7. Can the **Commission/DSC and vetted researchers** obtain data access (Art. 40) via compliant interfaces and the Data Access Portal? *([1][11].)*
8. Is there an independent, resourced **compliance function (Art. 41)** with compliance officers reporting to senior management? *([1][14].)*
9. Are **transparency reports (Art. 42)** published every six months with the VLOP-specific content and AMAR? *([1].)*
10. Is the **supervisory fee (Art. 43)** budgeted and the AMAR basis validated against the re-adopted methodology, and is the organisation ready for Commission proceedings and remedies (Arts. 56, 66–76)? *([1][2][3].)*

# Implementation Checklist

- [ ] AMAR instrumented with a documented, uniform methodology; threshold proximity monitored.
- [ ] Designation lead-in mapped (Section 5 applies four months after notification).
- [ ] Annual + pre-launch systemic-risk assessment (Art. 34) covering all four categories and algorithmic systems; evidence retained ≥ 3 years.
- [ ] Mitigation catalogue (Art. 35) tied to identified risks, outcome-tested, fundamental-rights-reviewed.
- [ ] Crisis-response capability ready (Art. 36).
- [ ] Independent annual audit commissioned (Art. 37); audit implementation report produced and actioned.
- [ ] Genuine non-profiling recommender option live (Art. 38).
- [ ] Advertising repository (Art. 39): public, API-searchable, complete fields, one-year retention, no access barriers/delays.
- [ ] Data access delivered (Art. 40): Commission/DSC on request; vetted researchers via Data Access Portal; public data under 40(12).
- [ ] Independent compliance function with compliance officers reporting to management (Art. 41).
- [ ] Enhanced transparency reports published every six months, including AMAR (Art. 42).
- [ ] Supervisory fee budgeted; AMAR basis validated against the re-adopted methodology (Art. 43).
- [ ] Commission-oversight readiness: evidence packs, information-request handling, remedy/action-plan capability (Arts. 56, 66–76).
- [ ] Joint DSA + GDPR + AI Act governance for recommender, advertising and researcher-data systems.
- [ ] Live enforcement watch-list maintained (X appeal, TikTok/Meta proceedings, fee methodology, designation changes).

# References

*All links verified live (HTTP 200/3xx) on 2026-07-11 (`sources_verified`). Enforcement and designation facts were re-confirmed against European Commission and Court of Justice sources on the same date.*

## Primary Sources

- [1] **Regulation (EU) 2022/2065 (Digital Services Act).** EUR-Lex, ELI (Arts. 33–43, 56, 66–76; Recitals 75–97 area). https://eur-lex.europa.eu/eli/reg/2022/2065/oj
- [2] **Commission Delegated Regulation (EU) 2023/1127** — detailed methodology and procedures for the DSA **supervisory fee** (Art. 43). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_del/2023/1127/oj
- [3] **General Court judgments of 10 September 2025, Meta Platforms Ireland v Commission (T-55/24) and TikTok Technology v Commission (T-58/24)** — annulment of the Art. 43 supervisory-fee implementing decisions; effects provisionally maintained. Press release CP No 114/25, Court of Justice of the EU. https://curia.europa.eu/site/upload/docs/application/pdf/2025-09/cp250114en.pdf
- [4] **Regulation (EU) 2016/679 (GDPR), consolidated text** — definition of "profiling" (Art. 4(4)) underpinning the Art. 38 non-profiling option, and parallel data-protection application. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504

## Regulatory Guidance

- [5] **The Digital Services Act package.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/digital-services-act-package
- [6] **Supervision of the designated VLOPs and VLOSEs under the DSA** (list of designated platforms/search engines; last updated 10 July 2026). European Commission. https://digital-strategy.ec.europa.eu/en/policies/list-designated-vlops-and-vloses
- [7] **Commission designates first set of Very Large Online Platforms and Search Engines** (IP/23/2413, 25 April 2023). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_23_2413
- [8] **Commission fines X €120 million under the Digital Services Act** (first DSA non-compliance decision, 5 December 2025; Art. 39 repository, Art. 40 access, deceptive verified-account design). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-fines-x-eu120-million-under-digital-services-act
- [9] **Commission fines X for breaching the DSA — press release IP/25/2934** (5 December 2025). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_2934
- [10] **Commission preliminarily finds TikTok and Meta in breach of their transparency obligations under the DSA** (preliminary findings, 24 October 2025; Art. 40 for both; Arts. 16/20 for Meta). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-preliminarily-finds-tiktok-and-meta-breach-their-transparency-obligations-under-digital
- [11] **Commission adopts delegated act on data access under the Digital Services Act** (Art. 40(4) vetted-researcher access; adopted 2 July 2025, in force 29 October 2025; Data Access Portal). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-adopts-delegated-act-data-access-under-digital-services-act
- [12] **DSA: Very large online platforms and search engines.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/dsa-vlops

## Standards

- [13] **ISO 19011:2018 — Guidelines for auditing management systems.** ISO. Referenced as best-practice methodology for the Art. 37 independent audit. https://www.iso.org/standard/70017.html
- [14] **ISO 37301:2021 — Compliance management systems — Requirements with guidance for use.** ISO. Referenced as a management-system model for the Art. 41 compliance function. https://www.iso.org/standard/75080.html

## Academic Sources

Not Applicable — this obligation-level reference relies on primary legislation, Commission enforcement/guidance and General Court case law. Academic analysis (systemic-risk methodology, recommender transparency, researcher-access design) will be cited in `dsa-vlop-risk-management` and `dsa-recommender-transparency` (planned).

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Centre for Algorithmic Transparency (ECAT) — supports Commission technical scrutiny of VLOP/VLOSE algorithmic systems. https://algorithmic-transparency.ec.europa.eu/index_en
- Digital Services Act — Wikipedia (overview and enforcement chronology; non-authoritative). https://en.wikipedia.org/wiki/Digital_Services_Act

# Related Documents

- `dsa-foundations` — parent overview: intermediary tiers, hosting and online-platform duties, enforcement structure (**prerequisite reading**).
- `dma-obligations` — the Digital Markets Act obligation-by-obligation sibling in the DSA/DMA package (style reference).
- `ai-act-foundations` — parallel EU regime for recommender/generative/moderation AI inside VLOP services.
- `gdpr-foundations` — the profiling definition (Art. 4(4)) and parallel data-protection regime for Arts. 38–40.
- `dsa-vlop-risk-management` — systemic-risk assessment, mitigation and audit methodology in depth (planned).
- `dsa-recommender-transparency` — recommender-system transparency and the profiling opt-out in depth (planned).
- `dsa-codes-of-conduct` — codes of conduct, crisis protocols and the Disinformation Code (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; Section 5 (Arts. 33–43) deep dive researched against EUR-Lex (Reg (EU) 2022/2065) and Delegated Regulation (EU) 2023/1127. Enforcement and designation facts live-verified on 2026-07-11: the designated VLOP/VLOSE list (Commission list updated 10 July 2026); the €120m X fine (5 Dec 2025, IP/25/2934) and its Art. 39/40 basis; the TikTok/Meta preliminary findings (24 Oct 2025); the Art. 40 researcher-data-access delegated act (in force 29 Oct 2025); and the General Court's annulment of the Art. 43 supervisory-fee decisions (T-55/24, T-58/24, 10 Sep 2025, CP 114/25). All external links returned HTTP 200/3xx. | pending |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved via autonomous backlog loop (Cluster A); passed full QA suite; frozen in release 0.15.0. | Human reviewer (loop-authorised) |
