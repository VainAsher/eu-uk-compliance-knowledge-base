---
id: dma-foundations
title: "EU Digital Markets Act: Foundations & Gatekeeper Obligations"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: Digital Markets
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [ai-act-foundations, gdpr-foundations, privacy-engineering-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [dma, digital-markets-act, gatekeeper, core-platform-service, self-preferencing, interoperability, sideloading, contestability]
legal_basis: Regulation (EU) 2022/1925
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dma-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.7.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The DMA's enforcement landscape is **actively evolving** — the designated-gatekeeper list, live non-compliance investigations, appeals and fines change over time. The lists and enforcement outcomes below were **live-verified against European Commission and Court of Justice sources on 2026-07-11**; always re-confirm the current gatekeeper register and open proceedings before relying on them.

# Executive Summary

The **EU Digital Markets Act (Regulation (EU) 2022/1925**, "DMA") is an *ex ante* competition-style regulation for large digital platforms. Its aim is to make digital markets more **contestable** (new entrants and rivals can compete) and **fair** (business users are not exploited by dominant platforms) [1][2]. Unlike traditional competition law, which acts *after* harm, the DMA imposes a fixed list of **do's and don'ts** on a small set of designated **gatekeepers** before harm occurs, and is enforced **solely by the European Commission** [1][2].

A firm becomes a **gatekeeper** when the Commission designates it under Article 3: it has a **significant impact on the internal market**, provides a **core platform service (CPS)** that is an **important gateway** for business users to reach end users, and enjoys an **entrenched and durable position**. Article 3 sets **rebuttable quantitative presumptions** for each limb (turnover/market-cap thresholds, and 45 million monthly active end users plus 10,000 yearly active business users in the EU) [1]. Designation attaches to specified CPS — the ten categories in Article 2 include app stores, search engines, social networks, messaging, operating systems, browsers, virtual assistants, cloud and online advertising [1].

Once designated, gatekeepers must comply with the obligations in **Articles 5, 6 and 7** — including no **self-preferencing**, no combining personal data across services without consent, allowing **sideloading** and third-party app stores, permitting **steering** to offers outside the platform, no forced bundling, data-access/portability duties, and **messaging interoperability** [1]. They must file **compliance reports** (Art. 11) and an **independently audited** consumer-profiling description (Art. 15). Breaches carry fines of up to **10% of total worldwide annual turnover**, rising to **20% for repeat infringement** (Art. 30) [1].

**Live-verified status (2026-07-11):** gatekeeper obligations became fully applicable on **7 March 2024** [4]; **seven** gatekeepers (Alphabet, Amazon, Apple, Booking, ByteDance, Meta, Microsoft) and **23** core platform services are currently designated [3]; and the Commission's **first non-compliance decisions (23 April 2025)** fined **Apple €500 million** (anti-steering, Art. 5(4)) and **Meta €200 million** (consent-or-pay, Art. 5(2)) [5][6]. On **8 July 2026** the General Court **upheld** Apple's gatekeeper designation for the App Store and iOS [7].

# Key Takeaways

- The **DMA (Regulation (EU) 2022/1925)** entered into force on **1 November 2022**, applied from **2 May 2023**, and gatekeeper **obligations became fully applicable on 7 March 2024** [1][4]. *(Legal obligation.)*
- Its twin goals are **contestability** and **fairness** in digital markets; it is enforced **exclusively by the European Commission**, not national competition authorities (Art. 1) [1][2]. *(Legal obligation.)*
- **Gatekeeper designation (Art. 3)** rests on three limbs with **rebuttable quantitative presumptions**: significant internal-market impact (≥ €7.5bn EU turnover in each of the last 3 FYs **or** ≥ €75bn market cap), an important-gateway CPS (**≥45m monthly EU end users** and **≥10,000 yearly EU business users**), and an entrenched, durable position [1]. *(Legal obligation.)*
- The DMA applies only to designated **core platform services** — ten categories in Art. 2 (app stores/intermediation, search, social networking, video-sharing, messaging, operating systems, browsers, virtual assistants, cloud, online advertising) [1]. *(Legal obligation.)*
- **Articles 5–7** set self-executing and specifiable obligations: no **self-preferencing** (Art. 6(5)), **data-use limits** (Arts. 5(2), 6(2)), **sideloading** and third-party app stores (Art. 6(4)), **steering / anti-anti-steering** (Art. 5(4)), no **forced bundling/tying** (Arts. 5(7)–(8)), data access/portability (Arts. 6(9)–(10)), and **messaging interoperability** (Art. 7) [1]. *(Legal obligation.)*
- Gatekeepers must submit a **compliance report** within six months of designation and update it annually (Art. 11), plus an **independently audited** consumer-profiling description (Art. 15) [1]. *(Legal obligation.)*
- **Penalties** reach **10% of total worldwide annual turnover**, or **20% for repeat infringement**; periodic penalty payments up to **5% of average daily worldwide turnover** (Art. 30); systematic non-compliance can trigger a **market investigation** and behavioural/structural remedies (Art. 18) [1]. *(Legal obligation.)*
- **Live-verified enforcement:** the Commission's first non-compliance decisions (**23 April 2025**) fined **Apple €500m** and **Meta €200m** [5][6]; the General Court **upheld Apple's designation** on **8 July 2026** [7]. *(Legal fact — verified.)*

# Purpose

This document is the Tier 2 foundational entry point for the EU Digital Markets Act. It supports legal research (what the DMA is, whom it binds and how gatekeepers are designated), compliance planning (which obligations attach on designation and how they are reported and audited), and product/engineering triage (whether an organisation is in scope, and what a gatekeeper-facing business user can now expect — sideloading, steering, interoperability, data access). It sits alongside `ai-act-foundations` and `gdpr-foundations` as part of the EU digital-regulation cluster and precedes deeper DMA sub-topic documents.

# Scope

**In scope:** The DMA's purpose (contestability and fairness); the gatekeeper **designation** criteria (Art. 3 thresholds and the CPS categories in Art. 2); the **obligations** in Articles 5–7 at a foundational level (self-preferencing, data-use limits, sideloading, steering, bundling, interoperability, data access); the **compliance-report and audit** mechanics (Arts. 11, 15); **enforcement and penalties** (Arts. 18, 30); and the current designation and enforcement landscape as live-verified.

**Out of scope (spun off to the research backlog):**

- The **article-by-article obligation detail** and each remedy's technical specification → `dma-obligations` (planned).
- **Messaging / NIICS interoperability mechanics** (Art. 7 reference offers, phasing) → `dma-interoperability` (planned).
- **Specific gatekeeper cases** and non-compliance proceedings in depth (Apple, Meta, others), including appeals → `dma-enforcement-cases` (planned).
- The **Digital Services Act (DSA)** systemic-risk / content regime → `dsa-foundations` (planned) [8].
- **Interplay with EU/GDPR data-protection and the AI Act** in depth → cross-referenced, not re-derived here.

**Assumptions:** The reader understands basic EU legislative structure (Regulation, Articles, Recitals). Personal-data processing by gatekeepers remains governed by the **GDPR** in parallel (see `gdpr-foundations`) [10].

# Definitions

*Shared terms are in `GLOSSARY.md`. DMA-specific terms are defined here; deeper per-obligation terms are deferred to `dma-obligations`.*

| Term | Definition | Source |
|------|------------|--------|
| Gatekeeper | An undertaking providing one or more core platform services that the Commission has **designated** under Art. 3 as having a significant internal-market impact, an important gateway CPS, and an entrenched, durable position. | [1] |
| Core platform service (CPS) | One of the ten service categories listed in Art. 2(2) (e.g. online intermediation/app stores, search engines, social networks, video-sharing, number-independent messaging, operating systems, browsers, virtual assistants, cloud, online advertising). Obligations attach to **designated** CPS. | [1] |
| Business user | A natural or legal person that, in a commercial or professional capacity, uses a core platform service to supply goods or services to end users (Art. 2(21)). | [1] |
| End user | A natural or legal person using a core platform service other than as a business user (Art. 2(20)). | [1] |
| Contestability | The degree to which firms can effectively enter, expand within, or challenge incumbents in a digital market — a core DMA objective (Recital 32 area). | [1][2] |
| Self-preferencing | A gatekeeper ranking or treating its own products/services more favourably than comparable third-party offers; prohibited in ranking, indexing and crawling by Art. 6(5). | [1] |
| Number-independent interpersonal communications service (NIICS) | An interpersonal communications service that does not connect with the public switched telephone network (e.g. many messaging apps); subject to interoperability duties under Art. 7. | [1] |

# Background

Large online platforms increasingly act as private gatekeepers between businesses and consumers. Their scale, data advantages, network effects and control of app-distribution and ranking give them entrenched positions that traditional, case-by-case competition enforcement (Articles 101–102 TFEU) addresses only slowly and after harm has occurred [1][2]. The EU's response was a **regulatory** instrument setting **clear, pre-defined rules** for the largest platforms, applied uniformly and enforced centrally, so that markets stay open to challengers and business users are treated fairly [2].

The DMA was adopted on **14 September 2022** as Regulation (EU) 2022/1925, **entered into force on 1 November 2022**, and **started to apply on 2 May 2023** [1]. Potential gatekeepers then had to notify their qualifying CPS; the Commission made its **first designations on 6 September 2023**, and the designated gatekeepers had until **7 March 2024** to bring their CPS into compliance [3][4]. The DMA is one pillar of the EU's digital-rulebook alongside the **Digital Services Act (Regulation (EU) 2022/2065)**, which addresses illegal content and systemic risks rather than market contestability [8].

# Legal Framework

The DMA regulates **designated gatekeepers** in respect of their **designated core platform services**. Its architecture:

- **Chapter I (Arts. 1–2)** — subject matter, scope, and definitions (incl. the ten CPS categories in Art. 2(2)). The Commission is the **sole enforcer**; Member States may not impose diverging obligations on gatekeepers for the same objective (Art. 1) [1].
- **Chapter II (Arts. 3–4)** — **designation** of gatekeepers (quantitative thresholds and rebuttable presumptions; market-investigation route) and review of designations.
- **Chapter III (Arts. 5–15)** — the **obligations**: self-executing duties (Art. 5), duties susceptible of further specification (Art. 6), messaging interoperability (Art. 7), plus anti-circumvention (Art. 13), concentration notifications (Art. 14), **compliance reporting** (Art. 11) and **audited profiling** disclosure (Art. 15).
- **Chapter IV (Arts. 16–19)** — **market investigations** (designation, systematic non-compliance, new services/practices).
- **Chapter V (Arts. 20–34)** — **investigatory and enforcement powers**, non-compliance decisions (Art. 29), **fines** (Art. 30), periodic penalty payments (Art. 31), and the **compliance function** (Art. 28).
- **Chapter VI (Arts. 35–54)** — final provisions, cooperation, and reviews.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 1 | Subject matter and scope; Commission is the **exclusive enforcer** of gatekeeper obligations. | [1] |
| Art. 2(2) | Definition of the **ten core platform service** categories. | [1] |
| Art. 3 | **Gatekeeper designation** — three limbs with rebuttable quantitative presumptions (turnover/market cap; 45m monthly end users + 10k yearly business users; entrenched/durable position). | [1] |
| Art. 5 | **Self-executing obligations** — e.g. no cross-service personal-data combination without consent (5(2)); allow steering/promotion of off-platform offers (5(4)); allow use of content acquired off-platform (5(5)); no forced use of the gatekeeper's identification/browser/payment services (5(7)); no tying/bundling of other CPS (5(8)). | [1] |
| Art. 6 | **Specifiable obligations** — no use of non-public business-user data to compete (6(2)); uninstall pre-installed apps and choice screens (6(3)); allow third-party app stores / **sideloading** (6(4)); no **self-preferencing** in ranking (6(5)); interoperability with OS/hardware features (6(7)); data portability and business-user data access (6(9)–(10)); FRAND access to app stores/search/social (6(12)). | [1] |
| Art. 7 | **Interoperability** of number-independent interpersonal communications services (messaging). | [1] |
| Art. 11 | **Compliance report** — file within six months of designation and update at least annually, describing how each obligation is met. | [1] |
| Art. 13 | **Anti-circumvention** — no behaviour that undermines effective compliance. | [1] |
| Art. 14 | Obligation to **inform the Commission of concentrations** in the digital sector. | [1] |
| Art. 15 | **Independently audited** description of consumer-profiling techniques; publish an overview. | [1] |
| Art. 18 | **Market investigation into systematic non-compliance** — behavioural or structural remedies. | [1] |
| Art. 28 | **Compliance function** — independent, adequately resourced, with compliance officers. | [1] |
| Art. 29 | **Non-compliance decisions** finding a breach and ordering compliance. | [1] |
| Art. 30 | **Fines** up to **10% of total worldwide annual turnover**; up to **20% for repeat infringement**. | [1] |
| Art. 31 | **Periodic penalty payments** up to **5% of average daily worldwide turnover**. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 7–8 | The DMA complements, and does not replace, EU/national competition law; it pursues distinct objectives (contestability and fairness) through *ex ante* rules. | [1] |
| Recital 23 | Rationale for the **quantitative thresholds** as proxies for gateway power and entrenched position, subject to rebuttal. | [1] |
| Recital 32 area | **Contestability** — lowering barriers to entry and expansion so rivals can challenge gatekeepers. | [1] |
| Recital 62 area | **Self-preferencing** in ranking distorts contestability and fairness, hence the Art. 6(5) prohibition. | [1] |

## Relevant Case Law

The DMA is recent and its case law is emerging. The most significant judgment to date concerns **designation**, not the substantive obligations:

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Apple v Commission | General Court, Joined Cases **T-1079/23, T-1080/23 and T-214/24**, judgment **8 July 2026** (Press release CP 96/26) | The General Court **dismissed** Apple's challenge and **confirmed** its gatekeeper designation for the **App Store and iOS**, holding that the different App Store variants form a **single CPS**; challenges concerning **iMessage** were held inadmissible. | Confirms the Commission's Art. 3 designation methodology and the treatment of a service's variants as one CPS. [7] |

*Further non-compliance decisions (e.g. against Apple and Meta) are under appeal; those proceedings are tracked in `dma-enforcement-cases` (planned).* [5][6][7]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (European Commission — not statutory text unless a specific obligation is cited).**

- The Commission frames the DMA around **two objectives — contestability and fairness** — and stresses that it applies a **closed, predictable list of obligations** to a small number of gatekeepers, enforced **centrally by the Commission** rather than by 27 national regimes [2]. *(Regulatory interpretation.)*
- **Designation is service-specific.** The Commission designates named CPS, and it has both **added** services (e.g. Apple **iPadOS**, 29 April 2024) and, following review, **undesignated** others (e.g. Meta **Facebook Marketplace**, 23 April 2025), showing that designation is dynamic and evidence-based [3]. *(Regulatory interpretation / legal fact.)*
- **Compliance is outcome-tested, not box-ticking.** The Commission assesses whether measures are **effective**; its first non-compliance decisions found that Apple's steering restrictions and Meta's binary "consent or pay" model did **not** deliver the outcomes Articles 5(4) and 5(2) require [5][6]. *(Regulatory interpretation of Arts. 5(2), 5(4).)*
- The Commission has reported that, after its **first review**, the DMA "remains fit for purpose" and has opened opportunities for businesses and developers — signalling continuity rather than reopening the substantive obligations [2]. *(Regulatory interpretation.)*
- **Verification note:** the designation list and enforcement outcomes above were confirmed against the Commission's **gatekeepers portal** and news releases and the **Court of Justice** press service on **2026-07-11**; these are the items most likely to change and must be re-checked at each review [3][5][6][7]. *(Editorial recommendation.)*

# Technical Considerations

- **Sideloading and alternative app stores (Art. 6(4))** — gatekeeper operating systems must technically permit installation of third-party apps and app stores, which reshapes platform security models (notarisation, permissions, malware screening) [1]. *(Legal obligation for gatekeepers.)*
- **Steering and off-platform transactions (Arts. 5(4)–(5))** — apps and business users must be able to link out to, and complete, purchases outside the gatekeeper's channel without punitive restrictions [1]. *(Legal obligation for gatekeepers.)*
- **Anti-self-preferencing in ranking (Art. 6(5))** — ranking, indexing and crawling must apply **transparent, fair and non-discriminatory** conditions to third parties versus the gatekeeper's own services [1]. *(Legal obligation for gatekeepers.)*
- **Interoperability (Arts. 6(7), 7)** — third parties must get effective interoperability with OS/hardware features, and messaging gatekeepers must offer **interoperable** basic functionality (1:1 messaging, then groups and calls per the Art. 7 phasing) [1]. *(Legal obligation for gatekeepers.)*
- **Data access and portability (Arts. 6(9)–(10))** — real-time, continuous data portability for end users and access to business-user-generated data are architectural requirements (APIs, export tooling) [1]. *(Legal obligation for gatekeepers.)*
- **For non-gatekeeper business users**, the technical impact is an **opportunity**: they can build on new interoperability, sideloading and data-access surfaces — but should design to the gatekeeper's published reference offers and monitor changes. *(Best practice.)*

# Hosting Considerations

- **Cloud computing is a CPS category (Art. 2(2)).** A hyperscale cloud provider could, on meeting the Art. 3 thresholds, be designated for its cloud service — bringing data-portability, interoperability and no-self-preferencing duties into infrastructure [1]. *(Legal obligation — assess designation status.)* No cloud service is designated as a CPS at this document's date [3]. *(Legal fact — verified.)*
- **Most hosting providers are not gatekeepers** and fall outside the DMA; their relevance is as **business users** of gatekeeper CPS (e.g. marketplaces, app stores, ad services) who now benefit from fairer terms and data access [1]. *(Interpretation.)*
- **Multi-homing enablement** — DMA-driven data portability and interoperability make it easier for customers to move between hosts; providers should treat portability tooling as a competitive expectation. *(Editorial recommendation.)*

# Game Hosting Considerations

- **App-distribution changes matter most.** Game and game-service developers distributing through gatekeeper **app stores** gain rights to **steer** users to external offers, use **alternative app stores / sideloading**, and avoid **forced use** of the gatekeeper's in-app payment system (Arts. 5(4), 5(7), 6(4)) [1]. *(Legal obligation for gatekeepers — opportunity for developers.)*
- **Cross-service data limits.** Where a game platform is itself a gatekeeper CPS (e.g. a social network or messaging service), combining player personal data across services requires **consent** (Art. 5(2)), reinforcing GDPR consent practice [1][10]. *(Legal obligation.)*
- **Real-time / player-data specifics are largely out of scope** — the DMA targets platform contestability, not game-server latency or matchmaking; those remain governed by GDPR and, where relevant, the AI Act. *(Interpretation.)*

# AI Considerations

- **Virtual assistants and AI-driven ranking are in scope.** "Virtual assistants" are an explicit CPS category (Art. 2(2)), and AI-based **ranking/recommendation** engines within designated CPS are subject to the **anti-self-preferencing** and transparency duties (Art. 6(5)) [1]. *(Legal obligation for gatekeepers.)*
- **Parallel regimes, not substitutes.** The DMA governs **market power**; the **AI Act (Regulation (EU) 2024/1689)** governs AI **risk**, and the **GDPR** governs **personal data**. An AI recommender inside a gatekeeper CPS can engage all three simultaneously [1][9][10]. *(Interpretation — read together with `ai-act-foundations` and `gdpr-foundations`.)*
- **Emerging question:** whether **generative-AI / foundation-model** services will be designated as CPS is an open policy debate; the DMA's CPS list is fixed by Art. 2, so extension would require the market-investigation route or legislative change. Track, do not assume. *(Editorial recommendation.)* [1]

# Operational Guidance

Labels: **OBLIGATION** (gatekeeper must) / **BEST PRACTICE** (should) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Determine whether you are a gatekeeper.** Map turnover/market-cap and CPS user metrics against the Art. 3 thresholds; if presumptions are met, you must **notify** qualifying CPS. *(OBLIGATION.)* [1]
2. **If designated, stand up a compliance function** (Art. 28) and file the **Art. 11 compliance report** within six months, updated annually. *(OBLIGATION.)* [1]
3. **Implement Articles 5–7 by service:** enable sideloading/third-party stores, permit steering, remove self-preferencing in ranking, honour data-access/portability, deliver messaging interoperability, and stop cross-service data combination without consent. *(OBLIGATION.)* [1]
4. **Prepare the Art. 15 audited profiling description** and keep it current. *(OBLIGATION.)* [1]
5. **Avoid circumvention (Art. 13).** Ensure remedies are **effective in practice** — the Commission tests outcomes, as the Apple/Meta decisions show. *(OBLIGATION.)* [1][5][6]
6. **If you are a business user of a gatekeeper**, exercise your new rights (steering, portability, interoperability, FRAND access) and document any refusals for complaint to the Commission. *(BEST PRACTICE.)* [1][2]
7. **Run DMA, GDPR and AI Act workstreams together** — consent (Art. 5(2)) overlaps GDPR; AI ranking overlaps the AI Act. *(BEST PRACTICE.)* [1][9][10]
8. **Maintain a designation/enforcement watch-list** — re-verify the gatekeeper register and open proceedings at each review; they change. *(EDITORIAL RECOMMENDATION.)* [3]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Gatekeeper fails an Art. 5–7 obligation | Medium | Very High | Art. 30 fine up to 10% worldwide turnover [1][5][6] | Effective (outcome-tested) remedies; compliance function; legal review | Medium |
| R2 | Repeat/systematic non-compliance | Low | Very High | Art. 30 (20% repeat); Art. 18 market investigation → structural remedies [1] | Robust monitoring; timely remediation of Commission findings | Low |
| R3 | Circumvention through design choices (Art. 13) | Medium | High | Art. 13; Apple/Meta decisions [1][5][6] | Outcome testing; avoid "malicious compliance" patterns | Medium |
| R4 | Cross-service data combination without valid consent | Medium | High | Art. 5(2); GDPR overlap [1][10] | Genuine, GDPR-valid consent; less-data alternative service | Low |
| R5 | Business user under-uses new DMA rights | Medium | Medium | Arts. 5–7 opportunities [1][2] | Adopt steering/portability/interoperability; complaint route | Low |
| R6 | Assuming designation status is static | Medium | Medium | Dynamic designation (adds/undesignations) [3] | Periodic re-verification of the gatekeeper register | Low |
| R7 | Treating DMA compliance as covering GDPR/AI Act | Medium | High | Parallel regimes [1][9][10] | Joint DMA + GDPR + AI Act programme | Low |

# Implementation Roadmap

- **Phase 0 — Scoping:** Assess CPS portfolio and Art. 3 thresholds; determine gatekeeper vs business-user posture. *Effort:* Medium.
- **Phase 1 — Governance (gatekeepers):** Establish the Art. 28 compliance function; build the Art. 11 reporting process and Art. 15 audited profiling description. *Effort:* High.
- **Phase 2 — Obligation implementation:** Deliver Arts. 5–7 measures per service (sideloading, steering, anti-self-preferencing, data access, interoperability, consent). *Effort:* Very High.
- **Phase 3 — Outcome testing:** Validate that remedies are effective in practice; remediate circumvention risk. *Effort:* High.
- **Phase 4 — Business-user enablement:** For non-gatekeepers, operationalise new rights and build a complaint/evidence trail. *Effort:* Medium.
- **Phase 5 — Monitor & adapt:** Track designations, non-compliance decisions, appeals and reviews; integrate with GDPR/AI Act. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No assessment of DMA applicability. | Gatekeeper/business-user status unknown. |
| 2 | Managed | Applicability assessed; basic obligations or rights identified. | Threshold analysis done; owner assigned. |
| 3 | Defined | Compliance function and reporting in place (gatekeeper); rights operationalised (business user). | Art. 11/15 processes; documented measures. |
| 4 | Quantitatively Managed | Remedies outcome-tested with metrics; circumvention risk monitored. | KPIs on steering/interoperability/data access. |
| 5 | Optimising | Integrated DMA + GDPR + AI Act governance; proactive tracking of designations and case law. | Cross-regime programme; audit-ready. |

# Audit Questions

1. Has DMA applicability been assessed against the Art. 3 thresholds, and is the conclusion (gatekeeper / business user / out of scope) documented? *(Art. 3 [1].)*
2. For designated gatekeepers, is there a compliant Art. 11 **compliance report** and an Art. 15 **audited profiling** description, both current? *([1].)*
3. How is each Art. 5–7 obligation implemented per designated CPS, and how is effectiveness (not mere form) evidenced? *(Arts. 5–7; Art. 13 [1].)*
4. Is cross-service personal-data combination gated on **valid, GDPR-grade consent**, with a genuine less-data alternative? *(Art. 5(2) [1][10].)*
5. Is there an independent, resourced **compliance function** (Art. 28)? *([1].)*
6. For business users, are new rights (steering, portability, interoperability, FRAND access) actually exercised, with refusals logged? *(Arts. 5–7 [1].)*
7. Is the **gatekeeper register and open-proceedings status** re-verified periodically? *([3][5][6][7].)*
8. Are DMA, GDPR and AI Act obligations governed together where they overlap? *([1][9][10].)*

# Implementation Checklist

- [ ] DMA applicability assessed and documented (gatekeeper / business user / out of scope).
- [ ] Art. 3 threshold analysis retained with evidence.
- [ ] (Gatekeeper) Art. 28 compliance function established.
- [ ] (Gatekeeper) Art. 11 compliance report filed and annually updated.
- [ ] (Gatekeeper) Art. 15 audited consumer-profiling description prepared and published.
- [ ] Arts. 5–7 measures implemented per designated CPS and outcome-tested.
- [ ] Cross-service data combination gated on valid consent (Art. 5(2)), with less-data alternative.
- [ ] Anti-circumvention (Art. 13) reviewed against remedy design.
- [ ] (Business user) New DMA rights operationalised; refusals logged for complaint.
- [ ] Gatekeeper register / enforcement watch-list maintained.
- [ ] Joint DMA + GDPR + AI Act governance established.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2022/1925 (Digital Markets Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/1925/oj
- [7] **General Court judgment of 8 July 2026, Apple v Commission (Joined Cases T-1079/23, T-1080/23, T-214/24)** — designation upheld; Press release CP 96/26. Court of Justice of the EU. https://curia.europa.eu/site/upload/docs/application/pdf/2026-07/cp260096en.pdf
- [8] **Regulation (EU) 2022/2065 (Digital Services Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2065/oj
- [9] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [10] **Regulation (EU) 2016/679 (GDPR), consolidated text** (parallel application to gatekeeper personal-data processing). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504

## Regulatory Guidance

- [2] **About the Digital Markets Act.** European Commission. https://digital-markets-act.ec.europa.eu/about-dma_en
- [3] **DMA designated gatekeepers (gatekeepers portal).** European Commission. https://digital-markets-act.ec.europa.eu/gatekeepers-portal_en
- [4] **Designated gatekeepers must now comply with all obligations under the DMA** (7 March 2024). European Commission. https://digital-markets-act.ec.europa.eu/designated-gatekeepers-must-now-comply-all-obligations-under-digital-markets-act-2024-03-07_en
- [5] **Commission finds Apple and Meta in breach of the Digital Markets Act** (23 April 2025). European Commission — Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/news/commission-finds-apple-and-meta-breach-digital-markets-act
- [6] **Commission finds Apple and Meta in breach of the DMA** — press release IP/25/1085. European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_1085

## Standards

Not Applicable — the DMA is a self-contained regulatory instrument enforced by the European Commission; no ISO/NIST/OWASP/ETSI standard governs its obligations. Technical interoperability specifics (e.g. messaging reference offers) are set by gatekeepers under Commission supervision and are addressed in `dma-interoperability` (planned).

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation, Commission guidance and the Court of Justice. Academic analysis (contestability theory, self-preferencing economics, interoperability design) will be cited in the DMA sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- Digital Markets Act — overview article (Wikipedia). https://en.wikipedia.org/wiki/Digital_Markets_Act

# Related Documents

- `ai-act-foundations` — parallel EU digital regime governing AI risk (cross-reference).
- `gdpr-foundations` — parallel data-protection regime; underpins Art. 5(2) consent (**prerequisite reading**).
- `privacy-engineering-foundations` — DPbDD/security controls relevant to data-access and portability duties.
- `dma-obligations` — article-by-article obligation detail (planned).
- `dma-interoperability` — messaging/NIICS and OS interoperability mechanics (planned).
- `dma-enforcement-cases` — specific non-compliance proceedings and appeals (planned).
- `dsa-foundations` — the Digital Services Act companion regime (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Reg (EU) 2022/1925), European Commission (DMA portal, gatekeepers register, 7 March 2024 applicability, Apple/Meta non-compliance decisions IP/25/1085) and the Court of Justice (General Court judgment of 8 July 2026). Current gatekeeper list (7 gatekeepers / 23 CPS) and enforcement outcomes live-verified 2026-07-11. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at batch human review gate (parallel cluster); frozen in release 0.7.0. | Human reviewer |

</content>
</invoke>
