---
id: dsa-recommender-transparency
title: "DSA: Recommender-System Transparency & Online Advertising"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: Digital Services
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [dsa-foundations, dsa-vlop-obligations, gdpr-foundations, ai-act-foundations, uk-childrens-code]
tags: [dsa, digital-services-act, recommender-systems, transparency, online-advertising, ad-repository, profiling, non-profiling-option, protection-of-minors, dark-patterns, systemic-risk, addictive-design, gdpr-profiling]
legal_basis: Regulation (EU) 2022/2065
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dsa-recommender-transparency |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.17.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is the planned sub-topic deep dive that `dsa-foundations` and `dsa-vlop-obligations` defer to on **recommender-system transparency (Arts. 27, 38)** and **online advertising (Arts. 26, 28, 39)**. DSA enforcement touching recommender and advertising systems is **active and fast-moving**: proceedings are opened, preliminary findings issued, decisions appealed, and the designated-platform list changes. Every enforcement and guidance fact below was **live-verified against European Commission sources on 2026-07-11**; re-confirm the status of any open proceeding before relying on it.

# Executive Summary

The **EU Digital Services Act (Regulation (EU) 2022/2065**, "DSA") regulates two of the most consequential design surfaces of modern platforms: the **recommender systems** that rank and select what users see, and the **advertising systems** that monetise their attention. This document maps the DSA rules that govern both. For **all online platforms**, the DSA requires **recommender-system transparency** — the *main parameters* of any recommender must be set out in plain language, with the options a user has to modify them (Art. 27) — and **advertising transparency**, so each ad is clearly identifiable, with who paid for it and the main targeting parameters disclosed (Art. 26) [1]. It **prohibits dark patterns** that distort user choices (Art. 25) and **bans profiling-based advertising to minors** and, more broadly, advertising based on **special-category data** (Art. 28, Art. 26(3)) [1].

For the largest services — designated **Very Large Online Platforms (VLOPs)** and **Search Engines (VLOSEs)** — the obligations intensify: at least one recommender option must **not be based on profiling** (Art. 38); a public, **API-searchable advertising repository** must be maintained for one year after an ad's last presentation (Art. 39); recommender and ad systems are a named **systemic-risk** vector that must be assessed and mitigated (Arts. 34–35); and **vetted researchers** must be given data access to study those risks (Art. 40), operationalised by a **2025 delegated act** [1][13]. Because recommenders and ad targeting process personal data, the **GDPR applies in parallel** — the DSA's "profiling" concept is GDPR Art. 4(4), and automated decisions may engage GDPR Art. 22 [2].

This is now live law. The Commission's **first DSA fine — €120 million against X (5 December 2025)** — turned in part on a non-compliant **Art. 39 ad repository** and **Art. 40** access barriers [10][11]. And in a novel line of enforcement, the Commission has issued **preliminary findings that the "addictive design" of TikTok (6 Feb 2026) and of Meta's Facebook/Instagram (10 Jul 2026)** — infinite scroll, autoplay and highly personalised **recommender systems** — breaches the DSA's risk-management duties, especially for minors [7][9]. Forward-looking and pending items are flagged throughout.

# Key Takeaways

- **Recommender transparency is a platform-wide duty (Art. 27).** Every online platform using a recommender must set out, in its terms in **plain and intelligible language**, the **main parameters** used and any options to modify or influence them [1]. *(Legal obligation — in force.)*
- **VLOPs/VLOSEs must offer a non-profiling option (Art. 38).** At least one recommender configuration must **not be based on profiling** as defined in GDPR Art. 4(4), and it must be a genuine, directly accessible alternative [1][2]. *(Legal obligation.)*
- **Advertising must be transparent (Art. 26).** Each ad must be clearly identifiable as such, in real time, with the natural/legal person on whose behalf it is shown, **who paid** (if different), and the **main parameters** used to target the recipient — plus a way to access more [1]. *(Legal obligation.)*
- **No profiling-based ads to minors, and no special-category targeting (Arts. 28, 26(3)).** Platforms must not present advertising **based on profiling** using minors' personal data where they are aware with reasonable certainty the recipient is a minor, and must not target ads using **special-category data** (GDPR Art. 9) [1][2]. *(Legal obligation.)*
- **VLOPs must run an ad repository (Art. 39).** A public, multi-criteria-**searchable, API-accessible** repository of ads, with specified fields, retained **one year** after last presentation [1]. The X decision shows delays and access barriers count as non-compliance [10]. *(Legal obligation.)*
- **Recommender and ad systems are a systemic-risk vector (Arts. 34–35).** VLOPs/VLOSEs must assess and mitigate risks their **algorithmic (recommender) systems** create, including to minors' well-being and civic discourse [1]. *(Legal obligation.)*
- **Dark patterns are prohibited (Art. 25).** Interfaces must not deceive or manipulate users' free, informed choices — constraining default settings, consent flows and the friction placed around recommender/ad controls [1][15]. *(Legal obligation.)*
- **GDPR runs in parallel.** Recommender profiling and ad targeting are personal-data processing: lawful basis, transparency and (for solely automated decisions with legal/significant effect) **Art. 22** safeguards apply [2][16]. *(Legal obligation.)*
- **Enforcement is live-verified (2026-07-11):** the €120m **X** fine (Art. 39/40) [10][11]; **TikTok** (6 Feb 2026) and **Meta** (10 Jul 2026) preliminary findings on **addictive recommender design** [7][9]; the Oct 2025 TikTok/Meta transparency findings (Art. 40) [12]; the Art. 40 **data-access delegated act** in force 29 Oct 2025 [13]; and the Commission's **Art. 28 minor-protection guidelines** (14 Jul 2025) [14]. *(Confirmed, not asserted.)*

# Purpose

This document gives legal, compliance, product and engineering teams an article-level map of the DSA rules on **recommender systems** and **online advertising**, and translates each into concrete obligations, controls and audit questions. It supports three tasks: (1) designing recommender-transparency disclosures and, where a service is a VLOP/VLOSE, a genuine non-profiling option; (2) building compliant advertising labelling, minor-protection controls and (for VLOPs) an advertising repository and researcher-access interface; and (3) reading the Commission's recommender/advertising enforcement (X, TikTok, Meta) as a guide to how each duty is tested. It expands the recommender/advertising threads deferred by `dsa-foundations` and `dsa-vlop-obligations` and should be read after those.

# Scope

**In scope:** Recommender-system transparency for all online platforms (Art. 27); the VLOP/VLOSE non-profiling recommender option (Art. 38); advertising transparency (Art. 26) including the special-category-data limit (Art. 26(3)); protection of minors and the profiling-based-advertising ban (Art. 28); the advertising repository (Art. 39); recommender/ad systems as a systemic-risk vector (Arts. 34–35); dark patterns as they constrain recommender/ad interfaces (Art. 25); vetted-researcher data access (Art. 40) as it bears on studying recommenders; the GDPR interplay (profiling, Art. 22); and the AI Act overlap. The X / TikTok / Meta matters and the Commission's minor-protection guidelines are covered as worked, live-verified examples.

**Out of scope (covered elsewhere or in the backlog):** The full VLOP **systemic-risk-assessment and mitigation methodology** (Arts. 34–35 in engineering depth) → `dsa-vlop-risk-management` (planned); the wider **VLOP/VLOSE Section 5** regime → `dsa-vlop-obligations`; the **intermediary tiers, notice-and-action and enforcement structure** → `dsa-foundations`; **GDPR** consent, lawful basis and Art. 22 detail → `gdpr-foundations`; the **UK** age-appropriate-design regime for children's services → `uk-childrens-code`; the **AI Act** transparency and risk regime for recommender/generative systems → `ai-act-foundations`.

**Assumptions:** The reader has read `dsa-foundations` and understands the intermediary tiers and the VLOP/VLOSE designation concept. Personal-data processing by recommender and advertising systems is governed by the **GDPR in parallel** [2].

# Definitions

*Shared terms (online platform, VLOP/VLOSE, dark pattern, advertising repository, vetted researcher, systemic risk) are in `GLOSSARY.md`. Terms specific to this document are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Recommender system | A fully or partially automated system used by an online platform to **suggest, prioritise or rank** information in its online interface, including as a result of a search or determining the relative order/prominence of content (DSA Art. 3(s)). | [1] |
| Main parameters | The criteria that are **most significant** in determining the information suggested to a recipient and the reasons for their relative importance — the core of the Art. 27 disclosure. | [1] |
| Profiling | Any automated processing of personal data to evaluate personal aspects of a natural person, in particular to analyse or predict aspects concerning that person (GDPR Art. 4(4)); the concept the DSA imports for Arts. 26(3), 28 and 38. | [2] |
| Advertisement | Information designed to promote the message of a legal/natural person, whether for commercial or non-commercial purposes, presented on an online interface against remuneration specifically for promoting that information (DSA Art. 3(r)). | [1] |
| Non-profiling recommender option | A recommender configuration a VLOP/VLOSE must offer that is **not based on profiling** (GDPR Art. 4(4)) — e.g. reverse-chronological or non-behaviourally-inferred ranking (DSA Art. 38). | [1][2] |
| Advertising repository | The public, multi-criteria-searchable, **API-accessible** database of advertisements each VLOP/VLOSE must maintain under Art. 39, retained for **one year** after an ad's last presentation. | [1] |
| Addictive / "rabbit-hole" design | Regulatory shorthand (not a statutory term) for engagement-maximising interface and recommender features (infinite scroll, autoplay, personalised feeds) whose risks the Commission assesses under Arts. 34–35; the subject of the TikTok and Meta proceedings. | [7][9] |

# Background

When the DSA was designed, the EU legislature judged that **algorithmic curation** and **behavioural advertising** — not just illegal content — were central drivers of online harm: recommender systems shape what billions of people read and watch, and opaque ad-targeting monetises inferred profiles, including those of children. The e-Commerce Directive (2000/31/EC) said nothing about either. The DSA's response is layered: baseline **transparency** duties for every online platform (Arts. 26–27), **prohibitions** on the most harmful practices (dark patterns, Art. 25; profiling-based ads to minors, Art. 28), and, for the largest services, **structural** obligations — a non-profiling recommender option (Art. 38), a searchable ad repository (Art. 39), and systemic-risk assessment of the algorithms themselves (Arts. 34–35) [1][4].

The regime moved quickly from text to enforcement. The first VLOPs/VLOSEs were designated in April 2023; the Commission stood up the **European Centre for Algorithmic Transparency (ECAT)** to scrutinise recommender systems technically; it opened proceedings against **TikTok (Feb 2024)** and **Meta (May 2024)** targeting the **"rabbit-hole" effect** of their recommenders and their impact on minors [6][8]; it issued its **first fine against X (Dec 2025)** touching the ad repository and researcher access [10][11]; and in 2026 it issued **preliminary findings that TikTok's and Meta's addictive recommender design breaches the DSA** [7][9]. The statutory duties are stable; the enforcement gloss is dynamic, which is why every enforcement fact below is flagged as live-verified.

# Legal Framework

The recommender and advertising rules sit in **Chapter III** of the DSA and are **cumulative** by tier. The **online-platform** duties (Section 3, Arts. 19–28) apply to any hosting service that stores and disseminates information to the public; the **VLOP/VLOSE** duties (Section 5, Arts. 33–43) add on top once a service is designated for **≥ 45 million average monthly active EU recipients** [1]:

- **Online-platform layer (all online platforms):** prohibition of **dark patterns** (Art. 25), **advertising transparency** (Art. 26) including the special-category-data limit (26(3)), **recommender-system transparency** (Art. 27), and **protection of minors** including the profiling-based-advertising ban (Art. 28).
- **VLOP/VLOSE layer (designated services only):** **systemic-risk assessment** and **mitigation** covering algorithmic/recommender and advertising systems (Arts. 34–35), a **non-profiling recommender option** (Art. 38), an **advertising repository** (Art. 39), and **data access** for authorities and vetted researchers to study those systems (Art. 40).
- **Enforcement:** national **Digital Services Coordinators** supervise Arts. 25–28 under the country-of-origin principle; the **Commission** has **exclusive** competence over the Section 5 duties (Arts. 38–40), with fines up to **6% of worldwide annual turnover** (Art. 74) [1].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 3(s) | Defines **recommender system** (automated suggestion/ranking/prioritisation of information). | [1] |
| Art. 3(r) | Defines **advertisement** (paid promotional information on an online interface). | [1] |
| Art. 25 | **Prohibition of dark patterns**: online interfaces must not deceive/manipulate or materially distort recipients' free, informed decisions. | [1] |
| Art. 26(1) | **Advertising transparency**: each ad clearly identifiable in real time; disclose on whose behalf shown, **who paid** (if different), and **main targeting parameters** (with access to more). | [1] |
| Art. 26(3) | **No ad targeting** based on **profiling** using **special-category data** (GDPR Art. 9). | [1][2] |
| Art. 27 | **Recommender-system transparency**: set out the **main parameters** and reasons for their importance in **plain, intelligible** terms in the T&Cs; provide options to modify/influence them where available. | [1] |
| Art. 28(1) | **Protection of minors**: appropriate, proportionate measures for a high level of privacy, safety and security of minors. | [1] |
| Art. 28(2) | **No advertising based on profiling** (GDPR Art. 4(4)) using minors' personal data where the platform is aware with reasonable certainty the recipient is a minor. | [1][2] |
| Art. 34 | **Systemic-risk assessment**: identify risks stemming from **recommender systems and other algorithmic systems** and ad systems, across the four risk categories. | [1] |
| Art. 35(1) | **Mitigation**: reasonable, proportionate, effective measures, expressly including **adapting the design/functioning of recommender systems** and advertising systems. | [1] |
| Art. 38 | **Non-profiling recommender option**: VLOPs/VLOSEs using recommenders must provide at least one option **not based on profiling** (GDPR Art. 4(4)). | [1][2] |
| Art. 39 | **Advertising repository**: public, multi-criteria-searchable, **API-accessible** repository with specified fields (content, advertiser, who paid, period, targeting parameters, recipients reached); retained **1 year** after last presentation. | [1] |
| Art. 40 | **Data access**: to the Commission/DSC on reasoned request and to **vetted researchers** to study systemic risks (incl. recommender risks); conditions in a delegated act. | [1][13] |
| Art. 74 | **Fines** up to **6% of total worldwide annual turnover** for breach (Commission, VLOP/VLOSE duties). | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited here from the primary text [1]. Numbers are given as approximate areas, consistent with the exemplar DSA documents.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 68–70 area | Rationale for **advertising transparency** (Art. 26) and its interaction with **online-interface design**: recipients should know, clearly and unambiguously, that and on whose behalf content is an advert, and the main targeting parameters. | [1] |
| Recital 70 area | Rationale for **recommender-system transparency** (Art. 27): recipients should understand the main parameters that determine what is suggested to them and how to influence them. | [1] |
| Recital 71 area | The **protection of minors** and the prohibition on **profiling-based advertising** to them (Art. 28), including that platforms need not process extra data to assess whether a recipient is a minor. | [1] |
| Recital 94–95 area | The **non-profiling recommender option** (Art. 38) and the **advertising repository** (Art. 39) as user-empowerment and transparency tools at VLOP/VLOSE scale. | [1] |

## Relevant Case Law

**Not Applicable at this level.** There is no settled CJEU merits ruling interpreting Arts. 26–28, 38–39. The General Court has ruled on the DSA **supervisory fee** (T-55/24, T-58/24, 10 Sep 2025 — see `dsa-vlop-obligations`) but not on the recommender/advertising duties. Challenges to the **€120m X decision** (which rested partly on Art. 39/40) and to the pending TikTok/Meta addictive-design findings are **emerging** and are tracked in the enforcement backlog rather than asserted here [10][11][7][9]. On the GDPR side, the CJEU's profiling jurisprudence (e.g. SCHUFA, C-634/21) informs the Art. 4(4) concept the DSA imports and is covered in `gdpr-foundations` [2].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (European Commission — not statutory text unless a specific article is cited).**

- **Designation drives the heavier duties.** The Commission's non-profiling-option (Art. 38) and ad-repository (Art. 39) duties bind only **designated** VLOPs/VLOSEs; its published list (updated **10 July 2026**) covers 20+ VLOPs and two VLOSEs and changes over time [5][17]. *(Regulatory interpretation — verify the live list.)*
- **The ad repository and researcher access are outcome-tested.** The **€120m X decision (5 Dec 2025)** found X's **Art. 39** repository non-compliant because of design features and access barriers (excessive delays, missing search functionality/fields) and found X imposed unnecessary **Art. 40** barriers on researchers — alongside a deceptive "verified account" design [10][11]. *(Regulatory interpretation — first final decision.)*
- **Recommender design is now enforced as a systemic risk.** In a novel line, the Commission issued **preliminary findings that TikTok's addictive design (6 Feb 2026)** and **Meta's Facebook/Instagram addictive design (10 Jul 2026)** breach the DSA: infinite scroll, autoplay, push notifications and **highly personalised recommender systems** were found to be inadequately risk-assessed and mitigated under Arts. 34–35, especially for minors and vulnerable users [7][9]. These build on the **TikTok (Feb 2024)** and **Meta (May 2024)** formal proceedings targeting recommender **"rabbit-hole"** effects [6][8]. *(Regulatory interpretation — preliminary findings are not final.)*
- **Researcher access is being operationalised.** The Oct 2025 **TikTok/Meta transparency findings** turned on inadequate **Art. 40** access [12], and the Commission made Art. 40(4) operational via the **data-access delegated act** (in force **29 Oct 2025**), through which vetted researchers apply via a Data Access Portal to study risks including recommender effects [13]. *(Regulatory interpretation.)*
- **Minor protection has a Commission playbook.** The Commission's **guidelines on the protection of minors online (Art. 28(1), 14 Jul 2025)** recommend modifying **recommender systems** to prioritise explicit signals from children over behavioural signals, disabling engagement features (autoplay, streaks, read-receipts) by default, and guarding against manipulative commercial practices; they are a compliance reference, not a hard rule [14]. *(Regulatory interpretation — non-binding.)*
- **Verification note:** the designation list, the X appeal status, and the open TikTok/Meta proceedings are the items most likely to change and were confirmed against Commission sources on **2026-07-11**; re-check at each review [5][7][9][10]. *(Editorial recommendation.)*

# Technical Considerations

- **Enumerate and publish the recommender's main parameters (Art. 27).** Identify the criteria **most significant** in ranking (e.g. predicted watch time, engagement signals, recency, social graph, explicit preferences), why they matter, and expose user-facing controls to modify them; keep the disclosure in plain language in the terms and, ideally, contextually near the feed [1]. *(Legal obligation.)*
- **Engineer a genuine non-profiling feed (Art. 38, VLOP/VLOSE).** At least one option must not rely on **profiling** (GDPR Art. 4(4)) — i.e. not built from inferred behavioural profiles (reverse-chronological or interest-declared ranking are common patterns) — and must be a real, easily selectable alternative, not buried [1][2]. *(Legal obligation once designated.)*
- **Label ads and capture targeting metadata at serve time (Art. 26).** The ad-serving pipeline must attach, in real time, a clear "advertisement" marker, the advertiser/payer identity, and the **main targeting parameters**, with a link to fuller information; this metadata is also the raw material for the Art. 39 repository [1]. *(Legal obligation.)*
- **Gate special-category and minor targeting (Arts. 26(3), 28(2)).** Targeting logic must **exclude special-category data** (GDPR Art. 9) and must **suppress profiling-based ads** where the recipient is, with reasonable certainty, a minor — without collecting extra data just to make that determination [1][2]. *(Legal obligation.)*
- **Build the ad repository as a real product (Art. 39, VLOP/VLOSE).** Public, **multi-criteria-searchable, API-accessible**, complete fields, low-latency, retained one year after last presentation; the X decision makes delays and access friction a compliance failure [1][10]. *(Legal obligation once designated.)*
- **Instrument recommender risk metrics (Arts. 34–35).** The systemic-risk assessment must cover the recommender itself — measuring exposure patterns (e.g. amplification, "rabbit-hole" chaining, time-on-app for minors, night-time use) the Commission has said platforms must not disregard [1][7][9]. *(Legal obligation once designated.)*

# Hosting Considerations

- **Repository and researcher interfaces have real infrastructure cost.** The Art. 39 public API and Art. 40 researcher-access endpoints imply durable storage, rate-limited public APIs and **one-year-plus retention** pipelines; hosting/IaaS providers to a VLOP should expect contractual flow-down of export, logging and availability support [1][13]. *(Best practice for in-scope providers.)*
- **Recommender feature-stores process personal data.** Behavioural feature pipelines that feed recommenders are GDPR processing; hosting architecture should support data-minimisation, retention limits and the ability to serve a **non-profiling** path that does not read those stores [1][2]. *(Legal obligation — read with `gdpr-foundations`.)*
- **Not applicable to pure infrastructure roles.** A host that merely provides compute to a platform is not itself the online platform owing Arts. 26–28; the platform provider carries these duties [1]. *(Interpretation.)*

# Game Hosting Considerations

- **UGC/feeds can pull a game into Art. 27.** If a game **stores and disseminates content to the public** with an algorithmic feed (creator hubs, discovery feeds, recommended servers/mods), the operator likely owes recommender-transparency (Art. 27) and, if designated, the non-profiling option (Art. 38) [1]. *(Legal obligation — assess feature by feature.)*
- **Minor protection is acute for games (Arts. 28, 34–35).** A large under-18 audience engages the profiling-based-advertising ban (Art. 28(2)), heightens dark-pattern scrutiny of monetisation and engagement loops (Art. 25), and — for a designated service — makes child-safety-by-design central to recommender risk assessment; the Commission's minor-protection guidelines expressly flag virtual currencies and loot-boxes [1][14]. The UK's parallel regime is in `uk-childrens-code`. *(Legal obligation.)*
- **In-game advertising must be labelled and metadata-captured (Art. 26).** Paid promotional placements in-client fall within the advertisement definition (Art. 3(r)) and the Art. 26 transparency duties [1]. *(Legal obligation — assess.)*
- **Engagement mechanics are assessable "addictive design."** For a very large game platform, autoplay-style content chaining, streaks and personalised feeds are exactly the features the Commission has challenged for TikTok/Meta; pre-assess them against Arts. 34–35 [1][7][9]. *(Best practice; obligation once designated.)*

# AI Considerations

- **Recommenders are the AI system at the centre of the regime.** Ranking, retrieval and ad-targeting models are the "algorithmic systems" expressly named in Arts. 34–35, and the Art. 38 non-profiling option is a direct **design constraint** on personalised recommender AI [1][2]. *(Legal obligation once designated.)*
- **GDPR profiling and Art. 22 overlap.** Recommender profiling and ad targeting are personal-data processing needing a lawful basis and transparency; where a **solely automated** decision produces legal or similarly significant effects, **GDPR Art. 22** safeguards apply, informed by the EDPB-endorsed WP29 guidance on automated decision-making and profiling [2][16]. *(Legal obligation.)*
- **AI Act overlap.** Where a platform deploys AI for recommendation, generation or moderation, the **AI Act (Reg (EU) 2024/1689)** may apply in parallel — including **Art. 50** transparency for AI-generated/synthetic content and chatbot disclosure; the DSA governs **systemic and transparency risk**, the AI Act governs **AI risk**, and both can bind the same recommender at once — see `ai-act-foundations` [3]. *(Cross-reference.)*
- **Explainability is an operational necessity, not just an ideal.** Art. 27's "main parameters" disclosure and Art. 34's algorithmic-risk analysis both require the provider to be able to **explain** how its recommender ranks — implying model documentation, feature inventories and red-teaming of amplification effects [1]. *(Legal obligation / best practice.)*

# Operational Guidance

Labels: **OBLIGATION** (the platform must) / **BEST PRACTICE** (should) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Publish a plain-language recommender-transparency statement (Art. 27)** listing the main parameters, why they matter, and the controls to change them. *(OBLIGATION — all online platforms.)* [1]
2. **Expose usable recommender controls** contextually (near the feed), not just buried in terms. *(BEST PRACTICE.)* [1][14]
3. **Ship a genuine non-profiling recommender option (Art. 38)** as an easily selectable alternative, and verify it reads no behavioural profile. *(OBLIGATION once designated.)* [1][2]
4. **Label every advertisement in real time (Art. 26)** with advertiser/payer identity and main targeting parameters, plus a link to fuller information. *(OBLIGATION.)* [1]
5. **Enforce targeting exclusions (Arts. 26(3), 28(2))** — no special-category-data targeting; no profiling-based ads to minors — with technical gating, not policy alone. *(OBLIGATION.)* [1][2]
6. **Operate a compliant advertising repository (Art. 39)** — public, API-searchable, complete fields, one-year retention, no delays or access barriers. *(OBLIGATION once designated; the X decision is the benchmark.)* [1][10]
7. **Assess and mitigate recommender/ad systemic risk (Arts. 34–35)** with metrics on amplification, rabbit-hole chaining and minors' usage; document mitigations. *(OBLIGATION once designated.)* [1][7][9]
8. **Review interfaces against the dark-pattern prohibition (Art. 25)** — including default settings and any friction placed around opting into the non-profiling feed or ad controls. *(OBLIGATION.)* [1][15]
9. **Provide vetted-researcher and public-data access (Art. 40)** via the Data Access Portal so recommender risks can be studied. *(OBLIGATION once designated.)* [1][13]
10. **Run DSA and GDPR together** for profiling, targeting and Art. 22 automated-decision safeguards. *(OBLIGATION + BEST PRACTICE.)* [2][16]
11. **Adopt the Commission's minor-protection guidelines (Art. 28(1))** as a design baseline for services accessible to minors. *(EDITORIAL RECOMMENDATION.)* [14]
12. **Maintain a live enforcement watch-list** (X appeal, TikTok/Meta addictive-design proceedings, designation changes) and feed it into product review. *(EDITORIAL RECOMMENDATION.)* [7][9][10]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Incomplete/opaque recommender "main parameters" disclosure | Medium | High | Art. 27 [1] | Plain-language statement of significant parameters + controls | Low |
| R2 | Non-profiling option missing or not genuine (hidden profiling) | Medium | High | Art. 38 [1][2] | Real, selectable non-profiling feed; verify no behavioural reads | Low |
| R3 | Ads not clearly labelled / missing targeting-parameter disclosure | Medium | High | Art. 26 [1] | Serve-time labelling and metadata capture | Low |
| R4 | Profiling-based ads served to minors / special-category targeting | Medium | Very High | Arts. 26(3), 28(2) [1][2] | Technical gating; age-aware suppression; exclude Art. 9 data | Medium |
| R5 | Non-compliant ad repository (fields, delays, access barriers) | Medium | Very High | Art. 39; **X €120m** [1][10] | Complete-field, low-latency public API; one-year retention | Medium |
| R6 | Inadequate systemic-risk assessment of recommender ("addictive design") | Medium | Very High | Arts. 34–35; TikTok/Meta findings [1][7][9] | Metrics on amplification/rabbit-hole/minor use; mitigations | Medium |
| R7 | Dark patterns around consent, defaults or non-profiling opt-in | Medium | Medium | Art. 25 [1][15] | UX review against Art. 25 and EDPB deceptive-design guidance | Low |
| R8 | Inadequate vetted-researcher access to study recommenders | Medium | High | Art. 40; X fine; TikTok/Meta [1][10][12] | Data Access Portal support; no undue barriers | Medium |
| R9 | GDPR profiling / Art. 22 non-compliance in targeting | Medium | High | GDPR Arts. 4(4), 22 [2][16] | Lawful basis, transparency, ADM safeguards | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory:** Catalogue every recommender and ad surface; map data inputs (behavioural vs explicit) and whether the service is/near VLOP designation. *Effort:* Medium.
- **Phase 1 — Transparency baseline:** Publish the Art. 27 recommender statement and Art. 26 ad-labelling/metadata capture across all platforms. *Effort:* Medium.
- **Phase 2 — Prohibitions & minors:** Implement Art. 26(3)/28(2) targeting exclusions, minor-aware suppression, and an Art. 25 dark-pattern review. *Effort:* Medium.
- **Phase 3 — VLOP structural duties (if in scope):** Non-profiling option (38), advertising repository (39), and vetted-researcher/public-data access (40). *Effort:* Very High.
- **Phase 4 — Recommender risk governance (if in scope):** Art. 34–35 assessment and mitigation of recommender/ad systems with metrics and red-teaming. *Effort:* Very High.
- **Phase 5 — Assurance & monitoring:** Feed into independent audit (Art. 37), align with the minor-protection guidelines, and maintain the enforcement watch-list. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Recommender/ad surfaces uncatalogued; no transparency disclosures. | No Art. 27 statement; ads unlabelled. |
| 2 | Managed | Art. 27 statement published; ads labelled with basic targeting info. | Arts. 26–27 live; targeting exclusions drafted. |
| 3 | Defined | Minor/special-category gating enforced; (if VLOP) non-profiling option and ad repository operational. | Arts. 26(3), 28, 38–39 operational. |
| 4 | Quantitatively Managed | Recommender risk metrics tracked and mitigated; researcher access live; dark-pattern audits done. | Arts. 34–35, 40 evidenced; KPIs on amplification/minor use. |
| 5 | Optimising | Integrated DSA + GDPR + AI Act governance of recommender/ad systems; guidelines adopted; audit-passed. | Cross-regime programme; closed audit findings; watch-list feeds design. |

# Audit Questions

1. Does the platform publish, in **plain language**, the **main parameters** of each recommender and the options to modify them? *(Art. 27 [1].)*
2. For a VLOP/VLOSE: is there a genuine, easily selectable **non-profiling recommender option**, verified free of behavioural profiling? *(Art. 38 [1][2].)*
3. Is every advertisement **clearly identifiable** in real time, with advertiser/payer identity and **main targeting parameters** disclosed? *(Art. 26 [1].)*
4. Are **special-category-data targeting** and **profiling-based advertising to minors** technically prevented? *(Arts. 26(3), 28(2) [1][2].)*
5. Is the **advertising repository** public, API-searchable, complete, timely and retained one year — with no access barriers of the kind penalised in the X decision? *(Art. 39 [1][10].)*
6. Does the **systemic-risk assessment** cover the recommender itself (amplification, rabbit-hole, minor usage) and mitigations? *(Arts. 34–35 [1][7][9].)*
7. Have recommender/ad **interfaces and defaults** been reviewed for dark patterns? *(Art. 25 [1][15].)*
8. Can **vetted researchers** obtain data access to study recommender risks via the Data Access Portal? *(Art. 40 [1][13].)*
9. Is recommender/ad **profiling** GDPR-compliant, with **Art. 22** safeguards where automated decisions have significant effects? *(GDPR Arts. 4(4), 22 [2][16].)*
10. Has the service assessed itself against the Commission's **minor-protection guidelines**? *(Art. 28(1) [14].)*

# Implementation Checklist

- [ ] Recommender-transparency statement (Art. 27) published in plain language with modification options.
- [ ] Usable recommender controls exposed contextually, not only in terms.
- [ ] Genuine non-profiling recommender option live and verified (Art. 38, if designated).
- [ ] Advertisements labelled in real time with advertiser/payer and main targeting parameters (Art. 26).
- [ ] Special-category-data targeting disabled (Art. 26(3)).
- [ ] Profiling-based advertising to minors suppressed with reasonable certainty (Art. 28(2)).
- [ ] Advertising repository public, API-searchable, complete, one-year retention, no delays (Art. 39, if designated).
- [ ] Recommender/ad systemic-risk assessment and mitigation with amplification/minor-use metrics (Arts. 34–35, if designated).
- [ ] Interfaces and defaults reviewed against the dark-pattern prohibition (Art. 25).
- [ ] Vetted-researcher and public-data access via the Data Access Portal (Art. 40, if designated).
- [ ] GDPR profiling lawful basis, transparency and Art. 22 safeguards in place.
- [ ] Service assessed against the Commission's Art. 28(1) minor-protection guidelines.
- [ ] Enforcement watch-list maintained (X appeal; TikTok/Meta addictive-design proceedings; designation changes).

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`). Enforcement, designation and guidance facts were re-confirmed against European Commission sources on the same date.*

## Primary Sources

- [1] **Regulation (EU) 2022/2065 (Digital Services Act).** EUR-Lex, ELI (Arts. 3, 25–28, 34–35, 38–40, 74; Recitals 68–95 area). https://eur-lex.europa.eu/eli/reg/2022/2065/oj
- [2] **Regulation (EU) 2016/679 (GDPR), consolidated text** — "profiling" (Art. 4(4)) imported by DSA Arts. 26(3), 28, 38; special-category data (Art. 9); automated individual decision-making (Art. 22); parallel application. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [3] **Regulation (EU) 2024/1689 (AI Act), ELI** — parallel AI-risk and Art. 50 transparency regime for recommender/generative/moderation systems. EUR-Lex. https://eur-lex.europa.eu/eli/reg/2024/1689/oj

## Regulatory Guidance

- [4] **The Digital Services Act package.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/digital-services-act-package
- [5] **Supervision of the designated VLOPs and VLOSEs under the DSA** (designation list; last updated 10 July 2026). European Commission. https://digital-strategy.ec.europa.eu/en/policies/list-designated-vlops-and-vloses
- [6] **Commission opens formal proceedings against TikTok under the Digital Services Act** (19 February 2024; recommender "rabbit-hole"/addictive-design risk management, protection of minors, advertising transparency (Art. 39), researcher access (Art. 40)). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-opens-formal-proceedings-against-tiktok-under-digital-services-act
- [7] **Commission preliminarily finds TikTok's addictive design in breach of the Digital Services Act** (6 February 2026; infinite scroll, autoplay, push notifications and highly personalised recommender system; Arts. 34–35 risk to minors). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-preliminarily-finds-tiktoks-addictive-design-breach-digital-services-act
- [8] **Commission opens formal proceedings against Meta related to the protection of minors on Facebook and Instagram** (press release IP/24/2664, 16 May 2024; "rabbit-hole" effects, recommendation systems, minors). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_24_2664
- [9] **Commission preliminarily finds Meta's addictive design in breach of the Digital Services Act** (press release IP/26/1579, 10 July 2026; Facebook/Instagram infinite scroll, autoplay and personalised recommender systems; risk to minors). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_26_1579
- [10] **Commission fines X €120 million under the Digital Services Act** (first DSA non-compliance decision, 5 December 2025; non-compliant Art. 39 ad repository and Art. 40 researcher-access barriers). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-fines-x-eu120-million-under-digital-services-act
- [11] **Commission fines X for breaching the DSA — press release IP/25/2934** (5 December 2025). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_2934
- [12] **Commission preliminarily finds TikTok and Meta in breach of their transparency obligations under the DSA** (24 October 2025; Art. 40 researcher data access for both; Arts. 16/20 for Meta). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-preliminarily-finds-tiktok-and-meta-breach-their-transparency-obligations-under-digital
- [13] **Commission adopts delegated act on data access under the Digital Services Act** (Art. 40(4) vetted-researcher access; adopted 2 July 2025, in force 29 October 2025; Data Access Portal). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-adopts-delegated-act-data-access-under-digital-services-act
- [14] **Commission publishes guidelines on the protection of minors online under the DSA** (Art. 28(1); 14 July 2025; recommender-system modification, disabling engagement features by default, manipulative commercial practices). European Commission. https://digital-strategy.ec.europa.eu/en/library/commission-publishes-guidelines-protection-minors
- [15] **EDPB Guidelines 03/2022 on deceptive design patterns in social media platform interfaces.** European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-032022-deceptive-design-patterns-social-media_en
- [16] **Endorsed WP29 Guidelines** (incl. WP251rev.01, Guidelines on automated individual decision-making and profiling — GDPR Art. 22). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/general-guidance/endorsed-wp29-guidelines_en
- [17] **DSA: Very large online platforms and search engines** (supervision hub). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/dsa-vlops

## Standards

Not Applicable — the DSA recommender and advertising duties are enforced through legislation, Commission decisions and guidelines rather than voluntary technical standards. Related AI-governance and audit standards (ISO/IEC 42001, ISO/IEC 23894, ISO 19011) are treated in the AI and VLOP documents.

## Academic Sources

Not Applicable — this sub-topic reference relies on primary legislation, the GDPR, the AI Act and Commission enforcement/guidance. Peer-reviewed analysis of recommender-amplification and dark-pattern effects will be cited in `dsa-vlop-risk-management` (planned).

# Further Reading

*Non-authoritative; provided for orientation only.*

- Commission opens proceedings against TikTok regarding TikTok Lite's "Task and Reward" programme (addictive-design concern; reward feature subsequently withdrawn). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-opens-proceedings-against-tiktok-under-dsa-regarding-launch-tiktok-lite-france-and-spain
- European Centre for Algorithmic Transparency (ECAT) — supports Commission technical scrutiny of recommender systems. https://algorithmic-transparency.ec.europa.eu/index_en
- Digital Services Act — Wikipedia (overview and enforcement chronology; non-authoritative). https://en.wikipedia.org/wiki/Digital_Services_Act

# Related Documents

- `dsa-foundations` — parent overview: intermediary tiers, online-platform duties (Arts. 25–28) and enforcement structure (**prerequisite reading**).
- `dsa-vlop-obligations` — Section 5 deep dive: the non-profiling option (38), ad repository (39) and researcher access (40) in their VLOP context.
- `gdpr-foundations` — the "profiling" definition (Art. 4(4)), special-category data (Art. 9) and Art. 22 automated-decision safeguards.
- `ai-act-foundations` — parallel AI regime (incl. Art. 50 transparency) for recommender/generative/moderation systems.
- `uk-childrens-code` — the UK age-appropriate-design regime for children's online services (parallel minor-protection regime).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; recommender-transparency (Arts. 27, 38) and online-advertising (Arts. 26, 28, 39) sub-topic researched against EUR-Lex (Reg (EU) 2022/2065), the GDPR and the AI Act. Enforcement/guidance live-verified on 2026-07-11: the €120m X fine (5 Dec 2025, Art. 39/40); the TikTok (6 Feb 2026) and Meta (10 Jul 2026) addictive-design preliminary findings; the TikTok (Feb 2024) and Meta (May 2024) formal proceedings; the Oct 2025 TikTok/Meta transparency findings; the Art. 40 data-access delegated act (in force 29 Oct 2025); and the Commission's Art. 28(1) minor-protection guidelines (14 Jul 2025). All 17 external references and 3 further-reading links returned HTTP 200. | pending |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster C); full-repo validator/link/lint suite green; frozen in release 0.17.0. | Orchestrator (QA-verified) |
