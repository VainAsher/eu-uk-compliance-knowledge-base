---
id: dma-obligations
title: "EU Digital Markets Act: Gatekeeper Obligations in Depth"
version: 1.0.0
status: in-review
classification: public
jurisdiction: [EU]
topic: Digital Markets
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [dma-foundations, dsa-foundations, ai-act-foundations, gdpr-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [dma, digital-markets-act, gatekeeper, article-5, article-6, article-7, self-preferencing, anti-steering, interoperability, sideloading, data-portability, anti-circumvention, enforcement]
legal_basis: Regulation (EU) 2022/1925
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dma-obligations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.14.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is the obligation-by-obligation deep dive that expands the parent overview `dma-foundations`. The DMA's enforcement landscape is **actively evolving** — the designated-gatekeeper register, specification decisions, open non-compliance proceedings, appeals and fines all change over time. The designation and enforcement facts below were **live-verified against European Commission and Court of Justice sources on 2026-07-11**; always re-confirm the current register, the status of specification proceedings and any open proceedings before relying on them.

# Executive Summary

The **EU Digital Markets Act (Regulation (EU) 2022/1925**, "DMA") imposes a closed list of **do's and don'ts** on designated **gatekeepers** in respect of their designated **core platform services (CPS)**. This document goes beneath the foundational overview in `dma-foundations` and works through those obligations one by one: the **self-executing** duties in **Article 5**, the duties **susceptible of further specification** in **Article 6**, the **messaging interoperability** regime in **Article 7**, the **anti-circumvention** rule (Article 13), the **compliance-reporting** duty (Article 11) and **compliance function** (Article 28), the Commission's **specification proceedings** (Article 8), and the **enforcement and penalty** architecture (Articles 18, 29–31) [1].

The distinction between Articles 5 and 6 is structural and matters for compliance. **Article 5** obligations apply directly from the compliance date and are not, in principle, open to a "regulatory dialogue" — the gatekeeper must simply comply (e.g. no combining personal data across services without consent; no anti-steering or wide parity clauses; no forced use of the gatekeeper's browser engine, identification or payment service; no tying of further CPS) [1]. **Article 6** obligations are equally binding but the Commission may, under **Article 8(2)**, adopt a decision **specifying the measures** a gatekeeper must implement (e.g. sideloading, no self-preferencing in ranking, data portability and business-user data access, uninstall/defaults, and the Article 6(7) interoperability duty) [1]. **Article 7** governs interoperability of **number-independent interpersonal communications services (NIICS)** on a phased timeline [1].

**Live-verified status (2026-07-11):** **seven** gatekeepers (Alphabet, Amazon, Apple, Booking, ByteDance, Meta, Microsoft) and **23** core platform services are currently designated [2]. The Commission's **first non-compliance decisions (23 April 2025)** fined **Apple €500 million** for breaching the anti-steering obligation (Art. 5(4)) and **Meta €200 million** for its "consent or pay" model breaching the data-combination consent rule (Art. 5(2)) [3][4]. Separately, on **19 March 2025** the Commission adopted its **first Article 6(7) specification decisions**, setting out the interoperability measures Apple must deliver [5]. On **5 February 2026** the Commission decided that **Apple Ads and Apple Maps should not be designated** [6], and on **8 July 2026** the General Court **upheld** Apple's existing gatekeeper designation [7].

# Key Takeaways

- **Article 5** sets **self-executing** obligations that bind from the compliance date without a specification step: no cross-service personal-data combination without consent (5(2)); no wide price-parity / MFN clauses (5(3)); **anti-steering** — business users may promote and conclude off-platform offers free of charge (5(4)); use of off-platform-acquired content (5(5)); no forced use of the gatekeeper's identification, browser engine or payment service (5(7)); no tying of further CPS (5(8)); advertising-pricing transparency (5(9)–(10)) [1]. *(Legal obligation.)*
- **Article 6** obligations are binding but **susceptible of further specification** under Art. 8(2): no use of non-public business-user data to compete (6(2)); uninstall and choice screens (6(3)); third-party app stores / **sideloading** (6(4)); no **self-preferencing** in ranking, indexing, crawling (6(5)); switching freedom (6(6)); **interoperability** with OS/hardware features (6(7)); ad-measurement access (6(8)); end-user **data portability** (6(9)) and business-user **data access** (6(10)); search-data access on FRAND terms (6(11)); **FRAND** app-store/search/social access (6(12)); FRAND termination (6(13)) [1]. *(Legal obligation.)*
- **Article 7** requires designated **NIICS** (messaging) gatekeepers to make basic functionalities interoperable on request, on a **phased** timeline — 1:1 text and file-sharing at designation, group messaging within two years, and 1:1 then group voice/video calls within four years — while preserving security, including end-to-end encryption (7(3)), via a published **reference offer** (7(8)) [1]. *(Legal obligation.)*
- **Anti-circumvention (Art. 13)** prohibits any behaviour — contractual, commercial, technical or otherwise — that undermines effective compliance, including degrading conditions and making rights unreasonably difficult to exercise; consent refused under Art. 5(2) may be re-requested **no more than once per year** (13(6)) [1]. *(Legal obligation.)*
- Gatekeepers must file an **Art. 11 compliance report** within six months of designation and update it annually, and maintain an **independent compliance function** with compliance officers reporting to management (Art. 28) [1]. *(Legal obligation.)*
- The Commission can **specify** Article 6 and 7 measures through **Art. 8 proceedings**; it exercised this for the first time in the **19 March 2025** Apple interoperability decisions (Art. 6(7)) [5]. *(Legal fact — verified.)*
- **Penalties** reach **10% of total worldwide annual turnover**, rising to **20% for repeat infringement** (Art. 30), with **periodic penalty payments** up to **5% of average daily worldwide turnover** (Art. 31); **systematic** non-compliance can trigger a market investigation and behavioural/structural remedies (Art. 18) [1]. *(Legal obligation.)*
- **Worked enforcement:** the first non-compliance decisions (**23 April 2025**) fined **Apple €500m** (Art. 5(4)) and **Meta €200m** (Art. 5(2)) [3][4]; Alphabet's Google Play and Google Search compliance remain under investigation following **March 2025 preliminary findings** [8]; the General Court **upheld Apple's designation** on **8 July 2026** [7]. *(Legal fact — verified.)*

# Purpose

This document exists to give compliance, legal and engineering teams a **precise, article-level map** of what a designated gatekeeper must do (or must not do) under the DMA, and to translate each obligation into technical and operational consequences. It supports three tasks: (1) building a per-CPS obligation matrix for a gatekeeper; (2) advising business users on the rights they can now assert against a gatekeeper; and (3) reading the Commission's enforcement and specification practice (Apple, Meta, Alphabet) as a guide to how each obligation is tested in practice. It is the planned deep-dive that `dma-foundations` defers to, and it should be read after that overview.

# Scope

**In scope:** The substantive obligations in **Articles 5, 6 and 7** clause by clause; the **anti-circumvention** rule (Art. 13); **compliance reporting** (Art. 11) and the **compliance function** (Art. 28); the Commission's **specification proceedings** and regulatory-dialogue mechanics (Art. 8); the **enforcement and penalty** framework (Arts. 18, 25, 29–31); and the **Apple / Meta / Alphabet** matters as worked examples, live-verified.

**Out of scope (covered elsewhere or in the backlog):**

- **Gatekeeper designation** criteria and the Art. 3 thresholds → parent `dma-foundations`.
- **NIICS / messaging interoperability mechanics** in engineering depth (reference-offer parsing, security models, ETSI/IETF work) → `dma-interoperability` (planned); this document states the Art. 7 legal duties only.
- **Full case histories and appeals** of the Apple, Meta and Alphabet proceedings → `dma-enforcement-cases` (planned); this document uses them illustratively.
- The **Digital Services Act (DSA)** content/systemic-risk regime → `dsa-foundations` [9].
- **GDPR** consent, DPbDD and profiling detail underpinning Art. 5(2) → `gdpr-foundations` [10].

**Assumptions:** The reader has read `dma-foundations` and understands gatekeeper designation, the CPS categories and basic EU legislative structure. Personal-data processing by gatekeepers remains governed by the **GDPR** in parallel [10].

# Definitions

*Shared terms are in `GLOSSARY.md` (Gatekeeper, Core platform service, NIICS, Self-preferencing). Obligation-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Self-executing obligation | An Article 5 obligation that applies directly on the compliance date and, unlike Article 6 duties, is not subject to a Commission specification decision — the gatekeeper must comply as drafted. | [1] |
| Specifiable obligation | An Article 6 (or 7) obligation that is binding but which the Commission may render operational by adopting, under Art. 8(2), a decision **specifying** the measures the gatekeeper must implement. | [1] |
| Anti-steering | The Art. 5(4) prohibition on preventing business users, free of charge, from communicating and promoting offers (including at different prices) to end users acquired via the CPS, and concluding contracts with them, whether or not through the CPS. | [1] |
| Wide parity / MFN clause | A contractual term stopping a business user from offering the same goods/services on better terms through other channels; prohibited by Art. 5(3). | [1] |
| Sideloading | Installation and effective use of third-party software applications or third-party app stores on the gatekeeper's operating system, which Art. 6(4) requires be technically permitted (subject to proportionate security measures). | [1] |
| Self-preferencing | More favourable ranking, indexing or crawling of the gatekeeper's own services/products versus comparable third-party offers; prohibited by Art. 6(5), which requires transparent, fair and non-discriminatory conditions. | [1] |
| Reference offer | The published statement of technical details and general terms and conditions under which a NIICS gatekeeper provides interoperability (Art. 7(8)). | [1] |
| Specification proceeding (regulatory dialogue) | The Art. 8(2) process by which the Commission may adopt a decision specifying the measures a gatekeeper must implement to comply with Arts. 6 or 7. | [1][5] |
| Anti-circumvention | The Art. 13 duty not to undermine effective compliance by any behaviour — contractual, commercial, technical or of any other nature. | [1] |

# Background

The DMA (Regulation (EU) 2022/1925) entered into force on 1 November 2022 and applied from 2 May 2023; the Commission made its first gatekeeper designations on 6 September 2023, and designated gatekeepers had until **7 March 2024** to bring their CPS into compliance with Articles 5, 6 and 7 [1][11]. The obligations were drafted as a **closed list** precisely so that they would be predictable and could be applied without the lengthy effects-analysis of traditional competition law [1][12].

The design choice that most shapes day-to-day compliance is the split between **Article 5 and Article 6**. Article 5 duties are "self-executing": Recital 65-area reasoning treats them as clear enough to apply without further specification. Article 6 duties are equally mandatory but the legislator recognised they might need operationalising for a given service; **Article 8** therefore lets the Commission engage in a "regulatory dialogue" and, where needed, adopt a **specification decision** setting out exactly what the gatekeeper must do [1]. Article 7 sits apart as a self-standing interoperability regime for messaging. This document is organised around that architecture, then turns to circumvention, reporting, the compliance function, specification and enforcement.

# Legal Framework

The obligations live in **Chapter III (Arts. 5–15)** of the DMA, with enforcement in **Chapter V (Arts. 20–34)** and market investigations in **Chapter IV (Arts. 16–19)** [1]. The obligation architecture:

- **Article 5 — obligations for gatekeepers** (self-executing do's and don'ts), sub-paragraphs 5(2)–5(10).
- **Article 6 — obligations susceptible of being further specified** under Article 8, sub-paragraphs 6(2)–6(13).
- **Article 7 — interoperability of number-independent interpersonal communications services** (messaging), with a phased functionality timeline and a reference-offer duty.
- **Article 8 — compliance and the specification mechanism**: the gatekeeper must ensure and demonstrate compliance; the Commission may specify Article 6/7 measures.
- **Article 11 — compliance report**; **Article 13 — anti-circumvention**; **Article 14 — concentration notifications**; **Article 15 — audited profiling description**.
- **Article 28 — compliance function** (independent, resourced, with compliance officers).
- **Enforcement**: **Article 18** (systematic non-compliance market investigation), **Articles 20–27** (investigatory powers, commitments, monitoring), **Article 29** (non-compliance decisions), **Article 30** (fines), **Article 31** (periodic penalty payments).

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 5(2) | No processing/combining of end-user personal data across the CPS and other services, no cross-use, and no sign-in to other services to combine data — **without consent**. | [1] |
| Art. 5(3) | No **wide parity / MFN** clauses: business users may offer the same products/services on different prices/conditions through third-party channels or their own. | [1] |
| Art. 5(4) | **Anti-steering**: allow business users, free of charge, to communicate and promote offers (incl. at different conditions) to end users acquired via the CPS, and to conclude contracts. | [1] |
| Art. 5(5) | Allow end users to access and use, via the CPS, content/subscriptions/features acquired from a business user off-platform. | [1] |
| Art. 5(6) | No restriction on business/end users raising non-compliance issues with public authorities (no anti-complaint clauses). | [1] |
| Art. 5(7) | No forced use of the gatekeeper's **identification service, web-browser engine, or payment service** (and supporting technical services). | [1] |
| Art. 5(8) | No **tying**: cannot require business/end users to subscribe to or register with any further CPS as a condition of use. | [1] |
| Art. 5(9)–(10) | Advertising **transparency**: give advertisers and publishers, on request, free daily information on prices and remuneration/fees. | [1] |
| Art. 6(2) | No use of **non-public data** generated by business users (and their end users) on the CPS to compete with them. | [1] |
| Art. 6(3) | Allow easy **uninstalling** of apps and changing of defaults; provide **choice screens** for default search/browser/virtual assistant. | [1] |
| Art. 6(4) | Allow third-party **app stores and sideloading**, with proportionate security measures permitted. | [1] |
| Art. 6(5) | No **self-preferencing** in ranking, indexing and crawling; transparent, fair, non-discriminatory conditions. | [1] |
| Art. 6(6) | No technical restrictions on end users **switching** between and subscribing to apps/services accessed via the CPS. | [1] |
| Art. 6(7) | **Interoperability**: free, effective interoperability with, and access to, the same OS/hardware/software features available to the gatekeeper's own services. | [1][5] |
| Art. 6(8) | Give advertisers/publishers, on request, free access to **performance-measuring tools** and verification data. | [1] |
| Art. 6(9) | **Data portability** for end users: free, effective, continuous and real-time access/portability of provided and generated data. | [1] |
| Art. 6(10) | **Business-user data access**: free, effective, continuous, real-time access to aggregated and non-aggregated data generated on the CPS. | [1] |
| Art. 6(11) | Give third-party search engines **FRAND** access to ranking, query, click and view data (personal data anonymised). | [1] |
| Art. 6(12) | **FRAND** general access conditions for business users to app stores, search engines and social-networking services. | [1] |
| Art. 6(13) | No disproportionate contract-**termination** conditions; termination on FRAND terms. | [1] |
| Art. 7 | **Interoperability of NIICS** (messaging): phased functionalities; security preserved; published reference offer. | [1] |
| Art. 8 | Gatekeeper must ensure/demonstrate compliance; Commission may **specify** Art. 6/7 measures (regulatory dialogue). | [1][5] |
| Art. 11 | **Compliance report** within six months of designation, updated at least annually. | [1] |
| Art. 13 | **Anti-circumvention** — no behaviour undermining effective compliance. | [1] |
| Art. 15 | **Independently audited** description of consumer-profiling techniques. | [1] |
| Art. 18 | **Market investigation** into systematic non-compliance → behavioural/structural remedies. | [1] |
| Art. 28 | **Compliance function** — independent, resourced, with compliance officers. | [1] |
| Art. 29 | **Non-compliance decision** finding a breach and ordering compliance. | [1] |
| Art. 30 | **Fines** up to **10%** of worldwide annual turnover; up to **20%** for repeat infringement. | [1] |
| Art. 31 | **Periodic penalty payments** up to **5%** of average daily worldwide turnover. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited here from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 36–37 area | Rationale for the **Art. 5(2) consent** rule — combining personal data across services entrenches data advantages; consent must meet the GDPR standard. | [1] |
| Recital 50 area | **Anti-steering (Art. 5(4))** — business users must be able to steer customers to and complete transactions on more favourable terms outside the CPS. | [1] |
| Recital 52 area | No forced use of the gatekeeper's **identification, browser engine or payment** services (Art. 5(7)); leveraging is prevented. | [1] |
| Recital 62 area | **Self-preferencing (Art. 6(5))** in ranking distorts contestability and fairness. | [1] |
| Recital 64–65 area | **Sideloading (Art. 6(4))** and the proportionality of any security measures the gatekeeper may take. | [1] |
| Recital 8 area | Article 6 duties may require **further specification** by the Commission; Article 5 duties are directly applicable. | [1] |

## Relevant Case Law

The DMA's substantive obligations are recent and there is **no settled CJEU case law interpreting Articles 5–7** on the merits. The most significant judgment to date concerns **designation**, not the obligations:

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Apple v Commission | General Court, Joined Cases **T-1079/23, T-1080/23 and T-214/24**, judgment **8 July 2026** (Press release CP 96/26) | The General Court **dismissed** Apple's challenge and **confirmed** its gatekeeper designation for the **App Store and iOS**, treating App Store variants as a **single CPS**; **iMessage** challenges were held inadmissible. | Confirms who is bound by the Chapter III obligations; substantive-obligation challenges (e.g. appeals of the 23 April 2025 fines) are pending and tracked in `dma-enforcement-cases`. [7] |

*Appeals of the Article 5 non-compliance fines and challenges to the Article 6(7) specification decisions are emerging; they are tracked in `dma-enforcement-cases` (planned) rather than asserted here.* [3][4][5][7]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (European Commission — not statutory text unless a specific obligation is cited).**

- **Compliance is outcome-tested, not formal.** The Commission's first non-compliance decisions found that Apple's steering restrictions did not deliver the outcome **Art. 5(4)** requires and that Meta's binary "consent or pay" model did not satisfy **Art. 5(2)**, because users had no equivalent, less-personal-data alternative [3][4]. *(Regulatory interpretation of Arts. 5(2), 5(4).)*
- **Article 6(7) is operationalised through specification.** On **19 March 2025** the Commission adopted two decisions specifying Apple's interoperability measures — one on **nine iOS connectivity features** for connected devices (smartwatches, headphones, TVs), the other on the **process** for handling developers' interoperability requests — with staged implementation deadlines running into 2026; this is the DMA's "regulatory dialogue" in action [5]. *(Regulatory interpretation of Arts. 6(7), 8.)*
- **Designation is service-specific and dynamic.** The Commission **added** services (Apple iPadOS, 29 April 2024), **undesignated** others (Meta Facebook Marketplace, 23 April 2025), and on **5 February 2026** decided that **Apple Ads and Apple Maps should not be designated**, as neither is an important gateway for business users [2][4][6]. *(Regulatory interpretation / legal fact.)*
- **Open proceedings signal the Commission's reading of Article 6.** Following **March 2025 preliminary findings**, Alphabet remains under investigation for **anti-steering in Google Play (Art. 5(4))** and **self-preferencing on Google Search (Art. 6(5))**; the Commission's concern is that third-party services are not treated in a fair, non-discriminatory way against Alphabet's own [8]. *(Regulatory interpretation — preliminary, not a final finding.)*
- **Verification note:** the designation register, the status of the Article 6(7) specification decisions, and the open Alphabet proceedings above were confirmed against the Commission's DMA portal and news service on **2026-07-11**; these are the items most likely to change and must be re-checked at each review [2][5][6][8]. *(Editorial recommendation.)*

# Technical Considerations

- **Article 5(2) — data separation by architecture.** Combining end-user personal data across a designated CPS and other services (or across CPS) requires **GDPR-grade consent**; the engineering consequence is service-level data segregation, consent capture and enforcement, and a genuinely equivalent **less-personal-data** variant where consent is refused [1][10]. *(Legal obligation for gatekeepers.)*
- **Article 5(4)/(7) — steering and payments.** Apps and business users must be able to link out to and complete purchases off-platform and must not be forced onto the gatekeeper's in-app payment, browser engine or identity service; this reshapes app-review rules, entitlement APIs and payment SDKs [1]. *(Legal obligation.)*
- **Article 6(4) — sideloading and alternative stores.** Operating systems must technically permit third-party apps and app stores, subject only to **proportionate** security measures (notarisation, malware screening, permissioning) — proportionality is the litigated edge [1]. *(Legal obligation.)*
- **Article 6(5) — ranking neutrality.** Ranking, indexing and crawling must apply transparent, fair, non-discriminatory conditions; this constrains recommender and search-ranking design and requires auditable ranking parameters [1]. *(Legal obligation.)*
- **Article 6(7) — interoperability surfaces.** Third parties must get effective, free interoperability with the same OS/hardware features the gatekeeper's own services use; the Apple specification decisions concretise this as **published APIs, staged betas and dispute resolution** [1][5]. *(Legal obligation.)*
- **Articles 6(9)–(10) — real-time data pipes.** End-user **portability** and business-user **data access** must be continuous and real-time — i.e. export/streaming APIs, not batch dumps — with authorisation flows for third parties acting on the user's behalf [1]. *(Legal obligation.)*
- **Article 7 — messaging interoperability.** NIICS gatekeepers must expose interoperable messaging while **preserving end-to-end encryption and security** (Art. 7(3)); the technical detail is deferred to `dma-interoperability` [1]. *(Legal obligation.)*

# Hosting Considerations

- **Cloud computing is a CPS category (Art. 2(2)), but no cloud service is currently designated** [2]. A hyperscale cloud provider that met the Art. 3 thresholds would inherit Chapter III duties most relevant to infrastructure: **data portability** (6(9)), **business-user data access** (6(10)), **FRAND** access (6(12)) and **no self-preferencing** (6(5)) [1]. *(Legal obligation — assess designation status.)*
- **Most hosting providers are not gatekeepers.** Their practical interest is as **business users** of gatekeeper CPS (app stores, marketplaces, ad services) who can now assert the Article 5–6 rights — steering, FRAND terms, data access, no forced ancillary services [1]. *(Interpretation.)*
- **Portability as a competitive baseline.** DMA-driven Art. 6(9)–(10) real-time portability raises customer expectations across hosting generally; providers should treat continuous export tooling as table stakes even when not themselves in scope. *(Editorial recommendation.)*

# Game Hosting Considerations

- **App-distribution rights are the headline change for game developers.** Developers distributing through a gatekeeper **app store** can steer users to external offers (Art. 5(4)), avoid **forced in-app payment** (Art. 5(7)), and use **alternative app stores / sideloading** (Art. 6(4)) [1]. *(Legal obligation for gatekeepers — opportunity for developers.)*
- **Cross-service player data needs consent.** Where a game platform is itself a gatekeeper CPS (e.g. a social network or messaging service), combining player personal data across services requires **Art. 5(2) consent**, reinforcing GDPR practice [1][10]. *(Legal obligation.)*
- **FRAND store terms and switching.** Game storefront and subscription terms imposed by a gatekeeper must be **FRAND** (Art. 6(12)), and technical barriers to players switching services must be removed (Art. 6(6)) [1]. *(Legal obligation for gatekeepers.)*
- **Real-time/matchmaking mechanics are out of scope** — the DMA targets platform contestability, not game-server latency; those remain governed by GDPR and, where relevant, the AI Act. *(Interpretation.)*

# AI Considerations

- **AI ranking sits inside Art. 6(5).** AI-based ranking/recommendation within a designated CPS must meet the **no-self-preferencing** and transparency conditions; the "fair and non-discriminatory" test applies to the model's treatment of third parties [1]. *(Legal obligation for gatekeepers.)*
- **Virtual assistants are a CPS category and an Art. 6(7) surface.** Interoperability and default/choice-screen duties (6(3), 6(7)) reach AI virtual assistants where designated [1]. *(Legal obligation.)*
- **Parallel regimes.** The DMA governs **market power**; the **AI Act (Reg (EU) 2024/1689)** governs AI **risk**; the **GDPR** governs **personal data**. An AI recommender inside a gatekeeper CPS can engage all three at once [1][10]. *(Interpretation — read with `ai-act-foundations` and `gdpr-foundations`.)*
- **Generative-AI as a future CPS is unresolved.** The CPS list is fixed by Art. 2; extending it to foundation-model services would require the market-investigation route or legislative change. Track, do not assume. *(Editorial recommendation.)* [1]

# Operational Guidance

Labels: **OBLIGATION** (gatekeeper must) / **BEST PRACTICE** (should) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Build a per-CPS obligation matrix.** For each designated CPS, map every applicable Art. 5 and Art. 6 sub-paragraph (and Art. 7 for NIICS) to a concrete measure and an owner. *(OBLIGATION.)* [1]
2. **Treat Article 5 as immediately binding.** Do not wait for a specification decision — 5(2) consent, 5(3) parity, 5(4) steering, 5(7) forced-service and 5(8) tying duties apply as drafted. *(OBLIGATION.)* [1]
3. **Engage the Article 8 regulatory dialogue for Article 6/7.** Where a measure is uncertain, document it and be ready for a Commission **specification decision** (as in the Apple Art. 6(7) case). *(OBLIGATION + BEST PRACTICE.)* [1][5]
4. **Make consent GDPR-grade and offer a less-data alternative.** The Meta decision shows a binary consent-or-pay model does not satisfy Art. 5(2). *(OBLIGATION.)* [1][4][10]
5. **Deliver effective steering.** Remove technical and commercial restrictions that blunt Art. 5(4); the Apple decision penalised restrictions that prevented developers from benefiting from off-platform channels. *(OBLIGATION.)* [1][3]
6. **File the Art. 11 compliance report and stand up the Art. 28 compliance function** — independent, resourced, with compliance officers reporting to management. *(OBLIGATION.)* [1]
7. **Design against circumvention (Art. 13).** Ensure remedies are effective in practice; avoid degrading conditions or making rights hard to exercise, and do not re-request refused consent more than once a year. *(OBLIGATION.)* [1]
8. **Business users: assert and log your rights.** Exercise steering, FRAND access, portability, data access and interoperability; document refusals for complaint to the Commission. *(BEST PRACTICE.)* [1][12]
9. **Maintain a designation/enforcement watch-list.** Re-verify the register, specification decisions and open proceedings at each review — they change. *(EDITORIAL RECOMMENDATION.)* [2][5][6][8]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Ineffective steering (Art. 5(4)) — restrictions blunt off-platform promotion | Medium | Very High | Art. 30 (10%); Apple €500m decision [1][3] | Remove technical/commercial restrictions; outcome-test developer flows | Medium |
| R2 | Consent-or-pay fails Art. 5(2) — no equivalent less-data option | Medium | Very High | Meta €200m decision [1][4][10] | GDPR-grade consent; genuine less-personal-data alternative | Medium |
| R3 | Self-preferencing in ranking (Art. 6(5)) | Medium | Very High | Alphabet Search preliminary findings [1][8] | Transparent, non-discriminatory ranking; auditable parameters | Medium |
| R4 | Non-compliant/incomplete Art. 6(7) interoperability | Medium | High | Art. 8 specification decisions [1][5] | Deliver specified measures on deadline; dispute-resolution process | Medium |
| R5 | Circumvention through design ("malicious compliance") (Art. 13) | Medium | High | Art. 13; enforcement practice [1][3][4] | Outcome testing; avoid degrading conditions/friction | Medium |
| R6 | Repeat/systematic non-compliance | Low | Very High | Art. 30 (20% repeat); Art. 18 market investigation [1] | Timely remediation; monitoring; compliance function | Low |
| R7 | Weak or under-resourced compliance function / late report | Low | High | Arts. 11, 28 [1] | Independent function, compliance officers, annual report | Low |
| R8 | Business user under-uses new DMA rights | Medium | Medium | Arts. 5–7 opportunities [1][12] | Adopt steering/portability/interoperability; complaint route | Low |

# Implementation Roadmap

- **Phase 0 — Obligation mapping:** Build the per-CPS Art. 5/6/(7) matrix; assign owners. *Effort:* Medium.
- **Phase 1 — Article 5 delivery:** Implement the self-executing duties (consent, parity, steering, forced-service, tying, ad transparency). *Effort:* High.
- **Phase 2 — Article 6 delivery + specification readiness:** Sideloading, no self-preferencing, uninstall/defaults, portability, business-user data access, FRAND access; prepare for Art. 8 dialogue. *Effort:* Very High.
- **Phase 3 — Article 7 (NIICS only):** Reference offer and phased interoperability, preserving security. *Effort:* Very High (messaging gatekeepers).
- **Phase 4 — Governance:** Art. 28 compliance function; Art. 11 report; Art. 15 audited profiling; Art. 13 circumvention review. *Effort:* High.
- **Phase 5 — Outcome testing & monitoring:** Validate remedies are effective; track specification decisions, appeals and open proceedings. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Obligations not mapped to CPS; ad-hoc responses to Commission contact. | No obligation matrix. |
| 2 | Managed | Per-CPS obligation matrix exists; Article 5 duties implemented in form. | Matrix + owners; consent/steering built. |
| 3 | Defined | Article 6 measures implemented; compliance function and Art. 11 report in place. | Sideloading/ranking/portability live; Art. 28 function. |
| 4 | Quantitatively Managed | Remedies outcome-tested with metrics; specification decisions delivered on time; circumvention monitored. | KPIs on steering/interoperability/data access. |
| 5 | Optimising | Integrated DMA + GDPR + AI Act governance; proactive regulatory-dialogue and case-law tracking. | Cross-regime programme; audit-ready; live watch-list. |

# Audit Questions

1. Is there a **per-CPS obligation matrix** covering every applicable Art. 5, 6 and (for NIICS) 7 sub-paragraph, with owners? *(Arts. 5–7 [1].)*
2. For **Art. 5(2)**, is cross-service data combination gated on **GDPR-grade consent** with a genuine less-personal-data alternative? *(Art. 5(2) [1][4][10].)*
3. For **Art. 5(4)**, can business users promote and conclude off-platform offers **free of charge and without effective restriction**, and is that outcome-tested? *(Art. 5(4) [1][3].)*
4. For **Art. 6(4)–(5)**, are sideloading/third-party stores permitted (with only proportionate security), and is ranking transparent and non-discriminatory? *(Arts. 6(4), 6(5) [1][8].)*
5. For **Art. 6(7)** (and any Art. 8 specification decision), are the specified interoperability measures delivered on the deadlines? *(Arts. 6(7), 8 [1][5].)*
6. Are **Art. 6(9)–(10)** end-user portability and business-user data access **real-time and continuous**? *([1].)*
7. For NIICS, is there a compliant **Art. 7 reference offer** and phased interoperability preserving security? *(Art. 7 [1].)*
8. Is there an independent, resourced **compliance function** (Art. 28) and a current **Art. 11 compliance report**? *([1].)*
9. Has **anti-circumvention (Art. 13)** been reviewed against remedy design, including the once-a-year consent-re-request limit? *(Art. 13 [1].)*

# Implementation Checklist

- [ ] Per-CPS obligation matrix built (Arts. 5, 6, and 7 for NIICS) with owners.
- [ ] Art. 5(2) consent + genuine less-personal-data alternative implemented.
- [ ] Art. 5(3) wide parity / MFN clauses removed.
- [ ] Art. 5(4) steering enabled free of charge and outcome-tested.
- [ ] Art. 5(7)–(8) forced-service and tying restrictions removed.
- [ ] Art. 5(9)–(10) advertising-pricing transparency provided on request.
- [ ] Art. 6(2) non-public business-user data not used to compete.
- [ ] Art. 6(3)–(4) uninstall, choice screens, third-party stores/sideloading enabled.
- [ ] Art. 6(5) no self-preferencing in ranking/indexing/crawling.
- [ ] Art. 6(6) switching restrictions removed.
- [ ] Art. 6(7) interoperability delivered (incl. any Art. 8 specification decision).
- [ ] Art. 6(9)–(10) real-time end-user portability and business-user data access.
- [ ] Art. 6(11)–(13) search-data FRAND access, FRAND store/search/social access, FRAND termination.
- [ ] Art. 7 reference offer + phased NIICS interoperability (messaging gatekeepers).
- [ ] Art. 11 compliance report filed and annually updated; Art. 28 compliance function established.
- [ ] Art. 13 anti-circumvention reviewed against remedy design.
- [ ] Joint DMA + GDPR + AI Act governance established.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`). consilium.europa.eu is bot-blocked to automated agents and is not cited here; Commission (EC) and EUR-Lex sources are used throughout.*

## Primary Sources

- [1] **Regulation (EU) 2022/1925 (Digital Markets Act).** EUR-Lex, ELI (Arts. 5–8, 11, 13, 15, 18, 28–31). https://eur-lex.europa.eu/eli/reg/2022/1925/oj
- [7] **General Court judgment of 8 July 2026, Apple v Commission (Joined Cases T-1079/23, T-1080/23, T-214/24)** — designation upheld; Press release CP 96/26. Court of Justice of the EU. https://curia.europa.eu/site/upload/docs/application/pdf/2026-07/cp260096en.pdf
- [9] **Regulation (EU) 2022/2065 (Digital Services Act)** — the DSA package sibling. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2065/oj
- [10] **Regulation (EU) 2016/679 (GDPR), consolidated text** — parallel application to gatekeeper personal-data processing; the consent standard for Art. 5(2). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504

## Regulatory Guidance

- [2] **DMA designated gatekeepers (gatekeepers portal)** — 7 gatekeepers / 23 CPS; adds and undesignations. European Commission. https://digital-markets-act.ec.europa.eu/gatekeepers-portal_en
- [3] **Commission finds Apple and Meta in breach of the Digital Markets Act** (Apple €500m under Art. 5(4); 23 April 2025). European Commission — Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/news/commission-finds-apple-and-meta-breach-digital-markets-act
- [4] **Commission finds Apple and Meta in breach of the DMA** — press release IP/25/1085 (Meta €200m under Art. 5(2); Facebook Marketplace undesignated). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_1085
- [5] **Commission provides guidance under the DMA to facilitate development of innovative products on Apple's platforms** — the two Article 6(7) specification decisions (DMA.100203 connected-device features; DMA.100204 interoperability-request process), 19 March 2025. European Commission. https://digital-markets-act.ec.europa.eu/commission-provides-guidance-under-digital-markets-act-facilitate-development-innovative-products-2025-03-19_en
- [6] **Commission finds that Apple Ads and Apple Maps should not be designated under the DMA** (5 February 2026). European Commission. https://digital-markets-act.ec.europa.eu/commission-finds-apple-ads-and-apple-maps-should-not-be-designated-under-digital-markets-act-2026-02-05_en
- [8] **Commission opens non-compliance investigations against Alphabet, Apple and Meta under the DMA** — press release IP/24/1689 (Google Play steering / Google Search self-preferencing; preliminary findings issued March 2025). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_24_1689
- [11] **Designated gatekeepers must now comply with all obligations under the DMA** (7 March 2024). European Commission. https://digital-markets-act.ec.europa.eu/designated-gatekeepers-must-now-comply-all-obligations-under-digital-markets-act-2024-03-07_en
- [12] **About the Digital Markets Act.** European Commission. https://digital-markets-act.ec.europa.eu/about-dma_en

## Standards

Not Applicable — the DMA's obligations are set by the Regulation and operationalised through Commission specification decisions, not by ISO/NIST/OWASP/ETSI standards. Technical interoperability specifics (e.g. NIICS reference offers, messaging security standards) are addressed in `dma-interoperability` (planned).

## Academic Sources

Not Applicable — this obligation-level reference relies on primary legislation and Commission enforcement/specification sources. Academic analysis (self-preferencing economics, interoperability design, consent-or-pay debate) will be cited in `dma-enforcement-cases` and `dma-interoperability` (planned).

# Further Reading

*Non-authoritative; provided for orientation only.*

- Digital Markets Act — overview article (Wikipedia). https://en.wikipedia.org/wiki/Digital_Markets_Act
- European Commission — DMA developer portal (interoperability). https://digital-markets-act.ec.europa.eu/developer-portal/interoperability_en

# Related Documents

- `dma-foundations` — parent overview: gatekeeper designation, CPS categories and the obligations at foundational level (**prerequisite reading**).
- `dsa-foundations` — the Digital Services Act sibling in the DSA/DMA package.
- `gdpr-foundations` — the consent standard underpinning Art. 5(2) and profiling (**prerequisite for the data obligations**).
- `ai-act-foundations` — parallel EU regime for AI ranking/virtual-assistant systems inside gatekeeper CPS.
- `dma-interoperability` — NIICS/messaging and OS interoperability mechanics in depth (planned).
- `dma-enforcement-cases` — the Apple, Meta and Alphabet proceedings and appeals in depth (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; obligation-by-obligation deep dive researched against EUR-Lex (Reg (EU) 2022/1925, Arts. 5–8, 11, 13, 28–31) and European Commission DMA sources. Current designation state (7 gatekeepers / 23 CPS), the 23 April 2025 Apple €500m (Art. 5(4)) and Meta €200m (Art. 5(2)) non-compliance decisions, the 19 March 2025 Article 6(7) Apple interoperability specification decisions, the March 2025 Alphabet preliminary findings, the 5 February 2026 Apple Ads/Maps non-designation, and the 8 July 2026 General Court judgment upholding Apple's designation were live-verified on 2026-07-11. All external links returned HTTP 200. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 3 human gate; frozen in release 0.14.0. | Human reviewer |

</content>
</invoke>
