---
id: game-hosting-foundations
title: "Game Hosting: Compliance Foundations"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU, UK]
topic: Game Hosting
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
related: [gdpr-foundations, uk-gdpr-foundations, eprivacy-foundations, privacy-engineering-foundations, dsa-foundations, ai-act-foundations, ai-governance-foundations, cybersecurity-foundations, dma-foundations]
tags: [game-hosting, children, age-appropriate-design, loot-boxes, pegi, dsa, ugc, consumer-protection, dark-patterns, ai-act, anti-cheat, ddos]
legal_basis: UK GDPR / Regulation (EU) 2016/679; DPA 2018 (esp. ss.9, 123); ePrivacy Directive 2002/58/EC & PECR 2003; Regulation (EU) 2022/2065 (DSA); Regulation (EU) 2024/1689 (AI Act); consumer-protection law (UCPD 2005/29/EC as amended by 2019/2161; DMCCA 2024); Gambling Act 2005; Online Safety Act 2023
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | game-hosting-foundations |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a *sector synthesis* that assumes the reader has the frozen foundational documents to hand and does not restate them. Several areas it touches are fast-moving — the UK loot-box position, PEGI's rating criteria (changed June 2026), the ICO Children's Code, and UK/EU consumer-protection reform — so confirm the live position before relying on any time-sensitive statement below.

# Executive Summary

Online and multiplayer **game hosting** is not governed by a single "games law". It sits at the intersection of the compliance regimes already documented in this knowledge base, and its distinctive risk profile comes from three facts: games are **very likely to be accessed by children**, they are **data-rich real-time services** (player identifiers, telemetry, voice/chat), and they are **monetised** through in-game purchases, subscriptions and randomised items. This document maps those overlapping obligations for operators hosting games for EU and UK audiences and points to the foundational documents where each regime is treated in depth.

Five themes dominate. First, **children's data**: the age of valid consent for information-society services is **13 in the UK** (DPA 2018 s.9) against a GDPR default of 16 (Member States may set any age down to 13) [1][2], and the **ICO Age-Appropriate Design Code ("Children's Code")** imposes 15 design standards on services likely to be accessed by children — squarely including games [3][14][15]. Second, **player identifiers and telemetry** are personal data, so data minimisation and purpose limitation apply to accounts, device IDs, matchmaking and anti-cheat (cross-ref `privacy-engineering-foundations`). Third, **ePrivacy/PECR** governs the analytics and advertising **SDKs** typical of games: non-essential storage/access needs consent before it fires [4][5]. Fourth, where a game **hosts user-generated content, chat or a marketplace** it can be an "intermediary"/"online platform" under the **DSA**, and in the UK a user-to-user service under the **Online Safety Act 2023** [6][10][21]. Fifth, **monetisation** engages consumer-protection law (dark-pattern and pricing rules under the UCPD/Omnibus and the UK **DMCCA 2024**) and the **loot-box** debate [8][9][11][12][16][17].

On the two items that most often go stale: the UK **has not** brought loot boxes within the Gambling Act 2005, relying instead on **industry-led Ukie guidance (July 2023)** and monitoring [16][17]; and **PEGI overhauled its criteria from June 2026** so that games with paid random items now carry a **PEGI 16** rating (PEGI 18 for social-casino mechanics) rather than only an informational notice [18][19]. Both positions were live-verified for this document.

# Key Takeaways

- Game hosting has **no bespoke statute**; compliance is the *union* of GDPR/UK GDPR, ePrivacy/PECR, the DSA (and UK Online Safety Act), consumer law, the AI Act and cybersecurity duties, with children's protection as the through-line. *(Editorial synthesis.)*
- The **consent age** for online services is **13 in the UK** (DPA 2018 s.9) and **16 by GDPR default**, adjustable by Member States down to 13 — multi-territory games must gate per jurisdiction [1][2]. *(Legal obligation.)*
- The **ICO Children's Code** applies to any online service (games included) **"likely to be accessed by children"** in the UK and requires high-privacy defaults, data minimisation, geolocation off by default, and no manipulative nudges; it is issued under **DPA 2018 s.123** and enforceable since 2 September 2021 [3][14][15]. *(Legal obligation / regulatory interpretation.)*
- **Player identifiers, device IDs, IP addresses, telemetry, matchmaking and anti-cheat data are personal data**; minimisation, purpose limitation and retention limits apply (cross-ref `gdpr-foundations`, `privacy-engineering-foundations`). *(Legal obligation.)*
- **In-game analytics/ads SDKs** store or read information on the device and require **consent before firing** under Art. 5(3) ePrivacy / PECR — "strictly necessary" is read narrowly and excludes analytics and advertising [4][5]. *(Legal obligation.)*
- Games that **host user-generated content, chat or a marketplace** may be **intermediary/hosting services or "online platforms" under the DSA** (notice-and-action, minors' protection in Art. 28, no dark patterns in Art. 25), and **user-to-user/search services under the UK Online Safety Act 2023** [6][10][21]. *(Legal obligation.)*
- **In-game purchases, subscriptions and dark patterns** engage consumer law: the EU **UCPD (as amended by the Omnibus Directive)** and **Consumer Rights Directive**, and in the UK the **DMCCA 2024** (drip-pricing ban in force 6 April 2025; subscription rules expected 2026) [9][11][12][13]. *(Legal obligation; cross-ref `consumer-rights-foundations` (planned).)*
- **Loot boxes** are **not** regulated under the UK **Gambling Act 2005**; the government (July 2022) found an *association* but no established *causal* link with harm and adopted **industry-led Ukie guidance (18 July 2023)** — children should not buy loot boxes without parental consent, with spending controls and probability disclosure [8][16][17]. *(Legal / regulatory fact — live-verified.)*
- **PEGI changed its rating criteria from June 2026**: paid random items now attract **PEGI 16** (PEGI 18 for social-casino mechanics) and blockchain/NFT mechanics **PEGI 18**, replacing the 2020 "Includes Paid Random Items" notice-only approach [18][19]. *(Regulatory/industry fact — live-verified.)*
- **AI Act transparency (Art. 50)** applies to in-game **AI chatbots** (disclose the user is interacting with AI) and **generative/synthetic content** (machine-readable marking); most game AI (NPC behaviour, matchmaking) is **minimal-risk** with no mandatory obligations [7] (cross-ref `ai-act-foundations`). *(Legal obligation / interpretation.)*

# Purpose

This document is the entry point for teams **hosting online or multiplayer games** for EU/UK players. It supports (a) legal mapping — identifying *which* regimes bite on a given game and *where* the deep treatment lives, (b) product and platform design — surfacing the children's-data, consent, moderation, monetisation and security obligations that recur in games, and (c) risk triage — flagging the fast-moving areas (loot boxes, PEGI, consumer reform) that need live verification. It is deliberately a **synthesis**: it reuses the frozen foundational documents rather than duplicating them.

# Scope

**In scope:** The compliance obligations that recur across online/multiplayer game hosting for EU and UK audiences — children's data and the Children's Code; player identifiers and telemetry as personal data; ePrivacy/PECR for in-game SDKs; DSA / UK Online Safety Act where games host UGC, chat or a marketplace; consumer protection for in-game purchases, subscriptions, loot boxes and dark patterns; AI Act transparency for game AI; PEGI/age ratings; and security/resilience (anti-cheat, account security, DDoS).

**Out of scope (spun off to the research backlog):** Detailed Children's-Code standard-by-standard implementation → `uk-childrens-code` (planned); loot-box / paid-random-item regulation in depth, including divergent EU Member-State treatment and any future UK review → `loot-box-regulation` (planned); UGC/content-moderation operations (notice-and-action, trusted flaggers, transparency reporting) → `ugc-moderation` (planned); consumer-rights detail (UCPD/Omnibus, DMCCA, subscriptions, dark patterns) → `consumer-rights-foundations` (planned sibling); cloud/infrastructure hosting mechanics → `cloud-hosting-foundations` (planned sibling); age-assurance/age-verification technology assessment → backlog.

**Assumptions:** The reader has `gdpr-foundations`, `uk-gdpr-foundations`, `eprivacy-foundations`, `privacy-engineering-foundations`, `dsa-foundations`, `ai-act-foundations` and `cybersecurity-foundations`. Shared terms carry over from `GLOSSARY.md`. "Game" here means an interactive online/multiplayer service, whether client-server, peer-to-peer or cloud-streamed.

# Definitions

*Shared terms (personal data, consent, controller, processor, online platform, intermediary service) are defined in `GLOSSARY.md` and carry over. Only game-specific terms are defined here; deeper areas are deferred to the backlog documents named in Scope.*

| Term | Definition | Source |
|------|------------|--------|
| Information-society service (ISS) | A service normally provided for remuneration, at a distance, by electronic means and at the individual request of a recipient — the category to which the child-consent age rules attach. Online games are ISS. | [1][2] |
| Children's Code (Age-Appropriate Design Code) | The ICO statutory code of practice under DPA 2018 s.123 setting 15 design standards for online services likely to be accessed by children. | [3][14][15] |
| Likely to be accessed by children | The ICO threshold triggering the Children's Code: the possibility that the service is accessed by under-18s is more probable than not, judged on the nature and appeal of the service. Games are typically caught. | [14][15] |
| Telemetry | Behavioural and technical event data emitted by a game client/server (inputs, sessions, performance, crash, matchmaking, anti-cheat signals); where linkable to a player it is personal data. | [1] |
| Loot box / paid random item | An optional in-game purchase where the player does not know exactly what they receive before buying (loot boxes, card packs, gacha, prize wheels), bought with real money and/or in-game currency. | [17][18] |
| Dark pattern (online choice architecture) | An interface design that materially distorts or impairs a user's ability to make free, informed choices (e.g. drip pricing, forced action, nagging, obstructed cancellation). | [6][9][11] |
| PEGI | Pan-European Game Information — the self-regulatory age-rating system used across most of Europe (statutory in some states); applies content descriptors and, from June 2026, interactive-risk age categories. | [18][19] |

# Background

Games moved from boxed, single-player products to **always-online services** monetised by microtransactions, subscriptions and randomised content, hosting large volumes of **user-generated content** (chat, voice, mods, user-built levels, item marketplaces). That shift pulled games into regimes designed for other sectors. Data-protection law applies because games process rich behavioural data about a population **disproportionately made up of children**; the EU/UK responded with a lowered but explicit child-consent age and, in the UK, a design code specifically for children's online services [1][2][3]. The **ePrivacy** cookie/SDK rule reaches the analytics and ad tooling that games embed [4]. The **DSA** and the UK **Online Safety Act 2023** reach games that host public UGC or a marketplace [6][10]. Consumer-protection law and the **loot-box** controversy reach monetisation design [8][9][16][17]. And the **AI Act** now reaches AI-driven characters, chatbots and generative content [7]. This document exists because no single foundational document captures that intersection for a games operator.

# Legal Framework

Game hosting is governed by the *cumulative* application of several instruments. The table states the obligation source plainly; interpretation is separated into the Regulatory Interpretation section.

## Relevant Articles

| Provision | Obligation (as relevant to game hosting) | Source |
|-----------|------------------------------------------|--------|
| GDPR Art. 8 | Child's consent to ISS valid from **16**; Member States may lower to **not below 13**; controller must make reasonable efforts to verify parental authorisation for younger children. | [1] |
| DPA 2018 s.9 | Sets the UK ISS child-consent age at **13** (modifying Art. 8(1)). | [2] |
| DPA 2018 s.123 | Requires the ICO to prepare the **Age-Appropriate Design Code**; the Code is the statutory basis of the Children's Code. | [3] |
| GDPR Arts. 5, 6, 25, 32 | Principles (minimisation, purpose/storage limitation), lawful basis, data-protection by design/default, and security — apply to accounts, telemetry, anti-cheat (see `gdpr-foundations`, `privacy-engineering-foundations`). | [1] |
| ePrivacy Art. 5(3) / PECR reg. 6 | Consent required before storing/accessing information on the device (analytics/ad **SDKs**, local storage), unless strictly necessary for a requested service. | [4][5] |
| DSA Arts. 6, 16, 25, 28, 33 | Hosting-service liability conditions; notice-and-action; **prohibition on dark patterns**; **protection of minors** (no profiling-based ads to minors; safety/privacy by design); VLOP threshold (45m avg. monthly EU users). | [6] |
| Online Safety Act 2023 (UK) | Duties on user-to-user and search services (illegal-content and children's-safety duties), regulated by Ofcom — applies to many games with chat/UGC. | [10][21] |
| AI Act Art. 50 | Transparency: disclose to users they are interacting with an **AI system** (e.g. chatbots) and mark **AI-generated/synthetic content** in machine-readable form. | [7] |
| UCPD 2005/29/EC (as amended by Omnibus 2019/2161) | Prohibits unfair/misleading/aggressive commercial practices, including certain dark patterns, and adds transparency duties (rankings, reviews). | [11][12] |
| Consumer Rights Directive 2011/83/EU | Pre-contractual information, digital-content rules and cancellation rights relevant to purchases/subscriptions. | [13] |
| DMCCA 2024 (UK) | Unfair-commercial-practices regime (incl. **drip pricing** banned from 6 Apr 2025), subscription-contract rules (expected 2026), CMA direct-enforcement powers. | [9] |
| Gambling Act 2005 (UK) | Licensing regime for gambling; the government has decided **not** to extend it to loot boxes at this time. | [8][16][17] |

## Relevant Recitals

*Recitals aid interpretation and are not binding operative provisions.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| GDPR Recital 38 | Children merit **specific protection** as they may be less aware of risks and their rights — the interpretive anchor for children's-data measures in games. | [1] |
| GDPR Recital 58 | Information addressed to children should be in **clear, plain language** a child can easily understand. | [1] |
| DSA Recital 71 | Minors' protection online justifies design measures and the ban on profiling-based advertising to minors. | [6] |
| AI Act Recital 132 | Transparency obligations for AI that interacts with people and for synthetic/generated content, so users know what they are dealing with. | [7] |

## Relevant Case Law

**Not Applicable at this level.** This is a sector synthesis; the load-bearing judgments live in the foundational documents and are not re-litigated here — e.g. *Planet49* (C-673/17) on cookie/SDK consent (`eprivacy-foundations`), and *Breyer*/*Nowak* on the breadth of "personal data" (`gdpr-foundations`). Game-specific domestic case law (e.g. on loot boxes as gambling) is emerging unevenly across Member States and is deferred to `loot-box-regulation` (planned). [4][6]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **ICO — Children's Code.** The ICO treats the Code as applying to services **"likely to be accessed by children"**, a lower bar than "directed at" children; most games meet it. The 15 standards require the **best interests of the child** as a primary consideration, **high-privacy defaults**, **data minimisation**, **geolocation off by default**, transparency in child-friendly terms, and **no nudge techniques** that push children to weaken privacy or over-share. Enforceable since 2 September 2021 [14][15]. *(Regulatory interpretation of GDPR/DPA duties.)*
- **UK loot boxes.** DCMS's July 2022 response found a **consistent association** between loot-box use and problem gambling but concluded a **causal link is not established**, and decided **not** to amend or extend the Gambling Act 2005; it set the objective that **children should not buy loot boxes without parental consent** and pursued **industry-led** protections [16][17]. The trade body **Ukie published industry guidance on 18 July 2023** (default restrictions for under-18s, spending controls, probability disclosure), with government monitoring over a 12-month implementation period and independent research via the Video Games Research Framework [16]. *(Regulatory position — live-verified; policy, not statute.)*
- **PEGI.** Since April 2020 PEGI applied an informational **"Includes Paid Random Items"** notice. From **June 2026** PEGI introduced **interactive-risk categories**: games submitted with **paid random items are rated PEGI 16** (PEGI 18 for social-casino mechanics), **blockchain/NFT** mechanics **PEGI 18**, time-/quantity-limited offers PEGI 12, "play-by-appointment" mechanics PEGI 7–12, and entirely unrestricted communication features PEGI 18 [18][19]. *(Industry self-regulation — live-verified; statutory in some Member States.)*
- **CMA (UK) / DMCCA.** The CMA now has **direct enforcement** of consumer law under the DMCCA; the ban on **drip pricing** and the updated unfair-commercial-practices list took effect **6 April 2025**, and dedicated **subscription-contract** rules are expected in 2026 [9]. *(Regulatory interpretation.)*
- **EDPB / DSA supervision.** For games that are online platforms, the Commission and national Digital Services Coordinators enforce the DSA, including the **dark-patterns ban (Art. 25)** and **minors' protection (Art. 28)** (see `dsa-foundations`) [6]. *(Regulatory interpretation.)*

# Technical Considerations

- **Data mapping first.** Inventory every player-data flow: account/identity, device IDs, IP, session/telemetry, voice/chat, purchase history, matchmaking, and **anti-cheat** signals. Most are personal data; classify by lawful basis and retention (see `privacy-engineering-foundations`). *(Best practice grounded in obligation.)* [1]
- **Data minimisation in telemetry.** Collect the minimum event data needed for the stated purpose; pseudonymise where possible; separate analytics identifiers from account identity; set retention limits and delete/aggregate on schedule. *(Legal obligation — Art. 5.)* [1]
- **Consent-before-set for SDKs.** Gate analytics/ad SDKs and any non-essential device storage/access behind consent; only strictly-necessary functions (save state, security, load balancing, anti-fraud session) may fire pre-consent [4][5]. *(Legal obligation.)*
- **Child-aware defaults.** Where the service is likely to be accessed by children, ship **high-privacy defaults**, geolocation and social discovery **off by default**, and profiling/behavioural-ad features off, per the Children's Code [14][15]. *(Regulatory interpretation of obligation.)*
- **Age assurance.** Implement proportionate age-assurance/parental-consent flows for the 13/16 thresholds and for age-rated content; avoid collecting more identity data than the assurance purpose needs. *(Best practice; age-assurance detail → backlog.)* [2][14]
- **No manipulative UX.** Avoid dark patterns in purchase, consent and cancellation flows — relevant simultaneously under the Children's Code (nudges), DSA Art. 25, and consumer law [6][11][14]. *(Legal obligation / best practice.)*

# Hosting Considerations

*Cloud/infrastructure mechanics are treated in `cloud-hosting-foundations` (planned sibling); only game-relevant points are noted here.*

- **Controller/processor split.** A studio/publisher is typically the **controller**; the cloud/game-hosting provider and managed live-ops vendors are **processors** needing Art. 28 contracts (see `gdpr-foundations`). *(Legal obligation.)*
- **International transfers.** Global player bases mean cross-border flows; apply the EU/UK transfer mechanisms (adequacy, SCCs, UK IDTA/Addendum) — see `uk-gdpr-foundations` and the transfers backlog. *(Legal obligation.)*
- **Server/network logs as personal & traffic data.** Game-server and network logs may be personal data and, for communications features, traffic data — apply minimisation and retention limits (see `eprivacy-foundations`). *(Legal obligation.)*
- **Resilience & availability.** Availability is both a security objective (GDPR Art. 32 names resilience) and a player-trust issue; design for **DDoS** mitigation, capacity and failover (see Security below and `cybersecurity-foundations`). *(Legal obligation / best practice.)* [1][20]

# Game Hosting Considerations

This is the core section — the game-specific overlay on the regimes above.

- **Children everywhere.** Treat games as **likely to be accessed by children** unless robust, evidenced age assurance shows otherwise; apply the Children's Code, the 13/16 consent thresholds, and DSA Art. 28 minors' protections together [1][2][14]. *(Legal obligation.)*
- **UGC, chat and marketplaces → platform duties.** If players can post content others see (chat, voice, mods, user levels) or trade items, assess **DSA** intermediary/online-platform status (notice-and-action, T&Cs, minors' protection, transparency; VLOP if ≥45m EU users) and, in the UK, **Online Safety Act 2023** user-to-user duties enforced by Ofcom [6][10][21]. *(Legal obligation; operations → `ugc-moderation` (planned).)*
- **Monetisation design.** In-game purchases, currencies, battle passes and subscriptions must present **clear pricing** (no drip pricing), honest scarcity/urgency claims, and easy cancellation; dark patterns are prohibited under the DSA, UCPD/Omnibus and DMCCA [6][9][11][12][13]. *(Legal obligation; detail → `consumer-rights-foundations` (planned).)*
- **Loot boxes / paid random items.** UK: **not** within the Gambling Act 2005; comply with **Ukie industry guidance** (no under-18 purchase without parental consent, spending controls, **probability disclosure**) and monitor for any policy change [8][16][17]. EU: treatment **diverges by Member State** (some apply gambling or consumer law to certain mechanics) — flagged for `loot-box-regulation` (planned). Rating: from **June 2026 PEGI rates paid random items PEGI 16+** [18][19]. *(Legal/regulatory — live-verified; assert nothing beyond the sourced positions.)*
- **Age ratings (PEGI).** Ensure submissions reflect the **June 2026 interactive-risk criteria**; games with paid random items, blockchain/NFT items, or unrestricted communications now face higher age bands, which in turn affects marketing, store placement and the Children's-Code "likely to be accessed" analysis [18][19]. *(Industry obligation where PEGI applies; statutory in some states.)*
- **Anti-cheat & account security.** Anti-cheat clients process personal (sometimes device/system) data and must be minimised, disclosed and secured; account-takeover is a leading player-harm vector — enforce strong authentication and abuse monitoring (see Security) [1][23]. *(Legal obligation / best practice.)*
- **In-game AI.** Chatbots and generative content trigger AI Act Art. 50 transparency; most NPC/matchmaking AI is minimal-risk (see AI Considerations) [7]. *(Legal obligation / interpretation.)*

# AI Considerations

- **Transparency for interactive AI (AI Act Art. 50).** In-game **AI chatbots / conversational NPCs** must disclose to the player that they are interacting with an AI system, unless obvious from context [7]. *(Legal obligation.)*
- **Synthetic/generative content marking.** Where a game **generates** images, audio, video or text with AI, providers must mark outputs as artificially generated in **machine-readable** form (Art. 50) — relevant to generative asset pipelines and AI-authored content [7]. *(Legal obligation.)*
- **Most game AI is minimal-risk.** NPC behaviour, pathfinding, difficulty scaling, matchmaking and cheat-detection heuristics are generally **minimal-risk** under the AI Act, attracting no mandatory obligations beyond voluntary codes — but confirm none crosses into prohibited practices (e.g. manipulative techniques exploiting children's vulnerabilities) or high-risk use [7] (see `ai-act-foundations`). *(Regulatory interpretation.)*
- **Profiling of children.** AI-driven personalisation/recommendation that profiles children collides with the Children's Code and DSA Art. 28 minors' protections; keep such profiling **off by default** for children [6][14]. *(Legal obligation / interpretation.)*
- **Training-data governance.** Behavioural/telemetry data reused to train models needs a lawful basis and, for device-level collection, valid ePrivacy consent (see `eprivacy-foundations`, `ai-governance-foundations`) [1][4]. *(Legal obligation.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Run a "likely to be accessed by children" assessment** for each title and, if positive, implement the Children's Code standards and jurisdiction-aware consent gating (13 UK / 16 EU default). *(OBLIGATION.)* [1][2][14]
2. **Gate all non-essential SDKs behind consent** (analytics, attribution, ads); document strictly-necessary classifications. *(OBLIGATION.)* [4][5]
3. **Map and minimise telemetry/anti-cheat data**, set retention limits, and pseudonymise analytics identifiers. *(OBLIGATION + BEST PRACTICE.)* [1]
4. **Assess DSA / Online Safety Act status** for any UGC, chat or marketplace features; stand up notice-and-action, T&Cs and minors' protections accordingly. *(OBLIGATION.)* [6][10]
5. **Audit monetisation for dark patterns and pricing compliance** (no drip pricing; honest urgency; easy cancellation); align with UCPD/Omnibus and DMCCA. *(OBLIGATION.)* [9][11][12]
6. **For loot boxes/paid random items:** disclose probabilities, block under-18 purchases without parental consent, provide spending controls, and follow Ukie guidance; track any regulatory change. *(OBLIGATION per policy + BEST PRACTICE.)* [16][17]
7. **Refresh PEGI submissions** against the June 2026 interactive-risk criteria and reconcile ratings with marketing and the children's-access analysis. *(OBLIGATION where PEGI applies.)* [18][19]
8. **Add AI transparency** to chatbots and mark AI-generated content; confirm no game AI is prohibited/high-risk. *(OBLIGATION.)* [7]
9. **Harden accounts and infrastructure** (strong auth, anti-cheat data governance, DDoS mitigation, incident response) per `cybersecurity-foundations`. *(OBLIGATION + BEST PRACTICE.)* [20][22][23][24]
10. **Maintain a games-compliance watch-list** for the fast-moving items (loot boxes, PEGI, DMCCA subscriptions, Children's-Code updates). *(EDITORIAL RECOMMENDATION.)*

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Processing children's data without Children's-Code measures / correct consent age | High | High | Art. 8; DPA s.9; Children's Code [1][2][14] | Children's-access assessment; high-privacy defaults; age gating | Medium |
| R2 | Non-essential SDKs firing before consent | High | High | ePrivacy Art. 5(3); PECR [4][5] | Consent-before-set; SDK inventory; tag gating | Low |
| R3 | Excessive/over-retained telemetry or anti-cheat data | Medium | Medium | Art. 5 minimisation [1] | Minimise, pseudonymise, retention limits | Low |
| R4 | Missing DSA/Online Safety duties for UGC/chat/marketplace | Medium | High | DSA; OSA 2023 [6][10] | Platform-status assessment; notice-and-action; minors' protection | Medium |
| R5 | Dark patterns / non-compliant pricing in monetisation | Medium | High | UCPD/Omnibus; DMCCA [9][11][12] | UX audit; clear pricing; easy cancellation | Low |
| R6 | Loot-box design out of step with policy / future regulation | Medium | Medium | Gov position; Ukie guidance [16][17] | Probability disclosure; under-18 controls; watch-list | Medium |
| R7 | Outdated PEGI rating after June 2026 criteria change | Medium | Medium | PEGI 2026 criteria [18][19] | Re-rate; align marketing/store metadata | Low |
| R8 | AI chatbot/generated content lacks transparency | Medium | Medium | AI Act Art. 50 [7] | Disclosure UI; machine-readable content marking | Low |
| R9 | Account takeover / cheating / DDoS degrading service & data | High | High | Art. 32; security standards [1][20][22] | Strong auth; anti-cheat; DDoS mitigation; IR plan | Medium |

# Implementation Roadmap

- **Phase 0 — Data & feature inventory:** Map player-data flows, SDKs, UGC/chat/marketplace features, monetisation mechanics and AI components. *Effort:* Medium.
- **Phase 1 — Children & consent:** Children's-access assessment; jurisdiction-aware consent gating; Children's-Code defaults; age assurance. *Effort:* Medium–High.
- **Phase 2 — ePrivacy & minimisation:** Consent-before-set SDK gating; telemetry minimisation and retention. *Effort:* Medium.
- **Phase 3 — Platform & consumer:** DSA/OSA status and controls; monetisation/dark-pattern and pricing compliance; loot-box controls; PEGI re-rating. *Effort:* Medium–High.
- **Phase 4 — AI & security:** AI transparency; anti-cheat/account security; DDoS resilience; incident response. *Effort:* Medium.
- **Phase 5 — Assurance & watch:** DPIAs, records, training; maintain the games-compliance watch-list. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Games treated as ordinary apps; no children's-data or SDK controls. | SDKs fire on launch; no age gating. |
| 2 | Managed | Basic consent banner and age gate; some data mapping. | Partial inventory; ad-hoc moderation. |
| 3 | Defined | Children's-Code defaults; consent-before-set; DSA/OSA status assessed; monetisation reviewed. | Documented processes; probability disclosure; notice-and-action. |
| 4 | Quantitatively Managed | Metrics on consent, moderation SLAs, spending controls, security events. | KPIs; periodic DPIAs and audits. |
| 5 | Optimising | Automated jurisdiction-aware controls; proactive tracking of loot-box/PEGI/consumer reform. | Adaptive controls; tested resilience; reform contingency. |

# Audit Questions

1. Have you assessed each title as "likely to be accessed by children", and how are the Children's-Code standards implemented? *(DPA s.123; ICO [3][14].)*
2. How do you gate child consent at 13 (UK) / 16 (EU default) and verify parental authorisation? *(Art. 8; DPA s.9 [1][2].)*
3. Are all non-essential SDKs blocked until consent, with strictly-necessary classifications documented? *(ePrivacy Art. 5(3) [4].)*
4. What telemetry and anti-cheat data do you collect, on what basis, and for how long? *(Art. 5 [1].)*
5. For UGC/chat/marketplace features, what is your DSA and Online Safety Act status and control set? *(DSA; OSA [6][10].)*
6. How does monetisation avoid dark patterns and comply with pricing/subscription rules? *(UCPD/Omnibus; DMCCA [9][11][12].)*
7. For loot boxes: do you disclose probabilities, block under-18 purchases without parental consent, and follow Ukie guidance? *(Gov position; Ukie [16][17].)*
8. Are PEGI ratings current under the June 2026 criteria? *(PEGI [18][19].)*
9. Do AI chatbots disclose AI interaction, and is generated content marked? *(AI Act Art. 50 [7].)*
10. What account-security, anti-cheat and DDoS-resilience controls and incident response are in place? *(Art. 32; standards [1][20][22].)*

# Implementation Checklist

- [ ] "Likely to be accessed by children" assessment completed per title.
- [ ] Jurisdiction-aware consent gating (13 UK / 16 EU default) with parental-authorisation flow.
- [ ] Children's-Code defaults (high privacy, geolocation off, no manipulative nudges).
- [ ] SDK inventory; consent-before-set for all non-essential storage/access.
- [ ] Telemetry/anti-cheat data mapped, minimised, retention-limited, pseudonymised.
- [ ] DSA / Online Safety Act status assessed; notice-and-action and minors' protections in place.
- [ ] Monetisation audited for dark patterns; clear pricing (no drip pricing); easy cancellation.
- [ ] Loot-box controls: probability disclosure, under-18 purchase controls, spending limits (Ukie guidance).
- [ ] PEGI ratings refreshed against June 2026 interactive-risk criteria.
- [ ] AI transparency (chatbot disclosure; machine-readable marking of generated content).
- [ ] Account security, anti-cheat governance, DDoS mitigation and incident-response tested.
- [ ] Games-compliance watch-list maintained (loot boxes, PEGI, DMCCA subscriptions, Children's Code).

# References

*All links verified live on 2026-07-11 (`sources_verified`) via HTTP 200 check.*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Art. 8 (child's consent), Arts. 5, 6, 25, 32; Recitals 38, 58. EUR-Lex, CELEX 02016R0679-20160504. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [2] **Data Protection Act 2018, s.9** (child's consent for information-society services; UK age 13). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/9
- [3] **Data Protection Act 2018, s.123** (Age-appropriate design code — statutory basis of the Children's Code). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/123
- [4] **Directive 2002/58/EC (ePrivacy), consolidated** (as amended by 2009/136/EC) — Art. 5(3). EUR-Lex, CELEX 02002L0058-20091219. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219
- [5] **Privacy and Electronic Communications (EC Directive) Regulations 2003 (PECR)**, SI 2003/2426. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/contents
- [6] **Regulation (EU) 2022/2065 (Digital Services Act)** — Arts. 6, 16, 25, 28, 33; Recital 71. EUR-Lex (ELI). https://eur-lex.europa.eu/eli/reg/2022/2065/oj
- [7] **Regulation (EU) 2024/1689 (AI Act)** — Art. 50 (transparency); Recital 132. EUR-Lex (ELI). https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [8] **Gambling Act 2005 (c.19)**, contents. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2005/19/contents
- [9] **Digital Markets, Competition and Consumers Act 2024 (c.13)**, contents. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2024/13/contents
- [10] **Online Safety Act 2023 (c.50)**, contents. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2023/50/contents
- [11] **Directive 2005/29/EC (Unfair Commercial Practices Directive)** (as amended by Directive (EU) 2019/2161). EUR-Lex (ELI). https://eur-lex.europa.eu/eli/dir/2005/29/oj
- [12] **Directive (EU) 2019/2161 (Omnibus / Modernisation Directive)**. EUR-Lex (ELI). https://eur-lex.europa.eu/eli/dir/2019/2161/oj
- [13] **Directive 2011/83/EU (Consumer Rights Directive)**. EUR-Lex (ELI). https://eur-lex.europa.eu/eli/dir/2011/83/oj

## Regulatory Guidance

- [14] **Children's code guidance and resources** (Age-Appropriate Design Code — introduction, scope, "likely to be accessed"). Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/childrens-information/childrens-code-guidance-and-resources/
- [15] **Age appropriate design: a code of practice for online services** (the 15 standards). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/childrens-information/childrens-code-guidance-and-resources/age-appropriate-design-a-code-of-practice-for-online-services/
- [16] **Loot boxes in video games: update on improvements to industry-led protections** (Ukie guidance 18 July 2023; monitoring). GOV.UK (DCMS). https://www.gov.uk/guidance/loot-boxes-in-video-games-update-on-improvements-to-industry-led-protections
- [17] **Government response to the call for evidence on loot boxes in video games** (July 2022; no Gambling Act extension). GOV.UK (DCMS). https://www.gov.uk/government/calls-for-evidence/loot-boxes-in-video-games-call-for-evidence/outcome/government-response-to-the-call-for-evidence-on-loot-boxes-in-video-games
- [18] **PEGI expands age rating criteria with interactive risk categories** (announced 12 March 2026; effective June 2026). PEGI. https://pegi.info/news/pegi-expands-age-rating-criteria-interactive-risk-categories
- [19] **What do the labels mean** (in-game purchases; paid random items; June 2026 ratings). PEGI. https://pegi.info/what-do-the-labels-mean
- [20] **Denial of service (DoS) guidance collection.** National Cyber Security Centre (NCSC, UK). https://www.ncsc.gov.uk/collection/denial-service-dos-guidance-collection
- [21] **Online safety** (regulator overview of Online Safety Act duties). Ofcom. https://www.ofcom.org.uk/online-safety/

## Standards

- [22] **ISO/IEC 27001:2022 — Information security management systems.** ISO/IEC. https://www.iso.org/standard/27001
- [23] **OWASP Foundation** (application/account-security projects, incl. authentication and Top 10). OWASP. https://owasp.org/
- [24] **NIST Cybersecurity Framework 2.0.** NIST. https://www.nist.gov/cyberframework

## Academic Sources

Not Applicable — this foundational sector synthesis relies on primary legislation, regulatory guidance and industry rating rules. Academic evidence on loot-box harm (referenced qualitatively in the DCMS response [17]) will be cited in `loot-box-regulation` (planned).

# Further Reading

*Non-authoritative; provided for orientation only.*

- House of Commons Library — *Loot boxes in video games* research briefing (CBP-8498). https://commonslibrary.parliament.uk/research-briefings/cbp-8498/
- ICO — Children's information hub (parent landing for children's-data resources). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/childrens-information/

# Related Documents

- `gdpr-foundations` — personal data, principles, lawful bases, child consent (Art. 8) (**prerequisite**).
- `uk-gdpr-foundations` — UK 13 consent age, DPA 2018, Children's-Code context (**prerequisite**).
- `eprivacy-foundations` — Art. 5(3) cookie/SDK consent (**prerequisite**).
- `privacy-engineering-foundations` — minimisation, DPbDD, pseudonymisation for telemetry.
- `dsa-foundations` — intermediary/online-platform duties, dark patterns, minors' protection.
- `ai-act-foundations` — AI Act risk tiers and Art. 50 transparency.
- `ai-governance-foundations` — model/data governance for game AI.
- `cybersecurity-foundations` — security controls, DDoS resilience, incident response.
- `dma-foundations` — app-store/gatekeeper context for game distribution and payments.
- `consumer-rights-foundations` — consumer-protection detail for purchases/subscriptions/dark patterns (planned sibling).
- `cloud-hosting-foundations` — cloud/infrastructure hosting mechanics (planned sibling).
- `uk-childrens-code` — Children's-Code standards in depth (planned).
- `loot-box-regulation` — loot-box/paid-random-item regulation and divergent Member-State treatment (planned).
- `ugc-moderation` — content-moderation operations (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; sector synthesis researched against EUR-Lex (GDPR, ePrivacy, DSA, AI Act, UCPD/Omnibus/CRD), legislation.gov.uk (DPA 2018 ss.9/123, Gambling Act 2005, DMCCA 2024, OSA 2023), ICO, GOV.UK/DCMS and PEGI. Loot-box position and PEGI June 2026 criteria change live-verified against primary sources. | pending |
