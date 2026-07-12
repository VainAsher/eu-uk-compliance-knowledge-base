---
id: ugc-moderation
title: "DSA: Content Moderation, Notice-and-Action & Statements of Reasons"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: Digital Services
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-12
updated: 2026-07-12
review_due: 2027-07-12
confidence: High
supersedes: Not Applicable
related: [dsa-foundations, dsa-vlop-obligations, dsa-recommender-transparency, consumer-rights-foundations, uk-childrens-code]
tags: [dsa, digital-services-act, content-moderation, notice-and-action, statement-of-reasons, trusted-flaggers, internal-complaints, out-of-court-dispute-settlement, safe-harbour, no-general-monitoring, intermediary-liability, transparency-database, online-safety-act, ofcom]
legal_basis: Regulation (EU) 2022/2065
sources_verified: 2026-07-12
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ugc-moderation |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.18.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-12 |
| Last Updated | 2026-07-12 |
| Review Due | 2027-07-12 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is the planned sub-topic deep dive that `dsa-foundations` defers to on **notice-and-action (Art. 16)**, **statements of reasons (Art. 17)**, the **redress ladder (Arts. 20–21)**, **trusted flaggers (Art. 22)** and the **liability safe harbour / no-general-monitoring rule (Arts. 4–8)**. DSA enforcement of moderation and redress duties is **active and evolving**, and the UK Online Safety Act regime is **still being phased in by Ofcom**; forward-looking and pending items are flagged in the text. Every enforcement and guidance fact was **live-verified against primary and European Commission / Ofcom sources on 2026-07-12**; re-confirm the status of any open proceeding or unfinished code before relying on it.

# Executive Summary

The **EU Digital Services Act (Regulation (EU) 2022/2065**, "DSA") converts content moderation from an opaque, discretionary activity into a **regulated, procedural** one. For **hosting services**, it requires an accessible **notice-and-action** mechanism through which anyone can flag allegedly illegal content (Art. 16), and — for **every** restriction a provider imposes on a recipient, whether on legality or terms-of-service grounds — a **statement of reasons** explaining what was done, on what factual and legal/contractual basis, whether automated means were used, and how to seek redress (Art. 17) [1]. These duties sit on top of the **liability safe harbour** (mere conduit, caching, hosting) and the **prohibition on general monitoring** that the DSA carried over from the e-Commerce Directive (2000/31/EC) and re-enacted as Arts. 4–8 [1][2].

For **online platforms**, the DSA adds a three-rung **redress ladder**: a free **internal complaint-handling system** (Art. 20), certified **out-of-court dispute settlement** (Art. 21), and, throughout, the right to go to court [1]. It gives **trusted flaggers** priority handling (Art. 22), requires **measures against misuse** by repeat bad actors and abusive notifiers (Art. 23), and — through Art. 17(4) and Art. 24(5) — makes platforms publish their statements of reasons in the public **DSA Transparency Database**, turning moderation into an auditable, aggregate record [1][6]. Enforcement is real: the Commission's October 2025 **preliminary findings against Meta** targeted deficient **notice-and-action and appeal** mechanisms, and its **first DSA fine (€120m against X, December 2025)** shows the procedural duties are outcome-tested [8][9].

The **UK Online Safety Act 2023 (OSA)** pursues the same goal — safer handling of illegal and harmful content — but through a **different instrument**: a **systemic duty-of-care and risk-assessment** model supervised by a single regulator, **Ofcom**, through binding codes of practice, rather than the DSA's harmonised notice-and-action-plus-statement-of-reasons-plus-redress architecture [3][10][11]. A service reaching users in both blocs must satisfy both.

# Key Takeaways

- **Hosting services must run a notice-and-action mechanism (Art. 16).** It must be easy to access, user-friendly and electronic, and let anyone flag specific allegedly illegal items; a sufficiently precise and substantiated notice gives the provider **actual knowledge** for liability purposes (Art. 16(3)) [1]. *(Legal obligation — in force.)*
- **Every restriction needs a statement of reasons (Art. 17).** For any removal, disabling, demotion, suspension or account action taken on legality **or** terms-of-service grounds, the provider must give the affected recipient a **clear and specific** statement covering the action, the facts relied on, whether automated means were used, the legal or contractual ground, and the available redress [1]. *(Legal obligation.)*
- **Statements of reasons are published (Arts. 17(4), 24(5)).** Online platforms must submit their statements of reasons — stripped of personal data — to the Commission's public **DSA Transparency Database**, creating an auditable moderation record [1][6]. *(Legal obligation.)*
- **Online platforms owe a three-rung redress ladder (Arts. 20–21).** A free, six-month **internal complaint-handling system** whose decisions are **not solely automated** (Art. 20), then certified **out-of-court dispute settlement** (Art. 21), without prejudice to going to court [1]. *(Legal obligation.)*
- **Trusted flaggers get priority (Art. 22).** Notices from entities awarded trusted-flagger status by a Digital Services Coordinator must be processed **with priority and without undue delay** [1]. *(Legal obligation.)*
- **Abuse cuts both ways (Art. 23).** Platforms must, after warning, **suspend** users who frequently post manifestly illegal content **and** suspend processing of notices/complaints from those who frequently submit manifestly unfounded ones [1]. *(Legal obligation.)*
- **The safe harbour is preserved but conditional (Arts. 4–8).** Hosting providers avoid liability only while they lack actual knowledge and act **expeditiously** on obtaining it; there is **no general monitoring obligation** (Art. 8), though specific orders (Arts. 9–10) are permitted — the framework inherited from the e-Commerce Directive [1][2]. *(Legal obligation.)*
- **Terms and transparency reinforce moderation duties (Arts. 14, 15, 24).** Providers must disclose their moderation policies and tools (including algorithmic decision-making) in their terms and apply them diligently and proportionately, and must publish periodic transparency reports [1]. *(Legal obligation.)*
- **The UK takes a different route.** The **Online Safety Act 2023** imposes illegal-content **risk assessments and safety duties** enforced by **Ofcom** through codes of practice, not a DSA-style notice-and-action / statement-of-reasons / redress-ladder regime; Ofcom's illegal-harms codes are being **phased in** [3][10][11]. *(Legal obligation — UK, phasing.)*
- **Enforcement is live-verified (2026-07-12):** the **€120m X** fine (5 Dec 2025) and the **Meta** preliminary findings on inadequate notice-and-action and appeal mechanisms (24 Oct 2025) show the procedural moderation duties are actively tested [8][9]. *(Confirmed, not asserted.)*

# Purpose

This document gives legal, trust-and-safety, product and engineering teams an article-level map of the DSA's **content-moderation procedure**: how to build a compliant notice-and-action flow, what a statement of reasons must contain and where it must be published, how the internal-complaint / out-of-court / judicial redress ladder fits together, how trusted flaggers and anti-misuse measures work, and how all of this rests on the conditional liability safe harbour and the no-general-monitoring rule. It also contrasts the DSA's procedural, harmonised model with the **UK Online Safety Act's** systemic duty-of-care model so that a service operating across the EU and UK can design one moderation system that satisfies both. It expands the moderation and redress threads deferred by `dsa-foundations` and should be read after it.

# Scope

**In scope:** Notice-and-action mechanisms for hosting services (Art. 16); statements of reasons and their publication (Arts. 17, 24(5)); the DSA Transparency Database; internal complaint-handling (Art. 20); out-of-court dispute settlement (Art. 21); trusted flaggers (Art. 22); measures against misuse (Art. 23); the liability exemptions and no-general-monitoring rule (Arts. 4–8) and their e-Commerce Directive origin; orders to act against illegal content / to provide information (Arts. 9–10); terms-and-conditions and transparency-reporting duties as they bear on moderation (Arts. 14, 15, 24); and a comparison with the UK Online Safety Act 2023 illegal-content regime and Ofcom's role. The X and Meta matters are covered as worked, live-verified examples.

**Out of scope (covered elsewhere or in the backlog):** **Recommender-system and advertising transparency** (Arts. 25–28, 38–39) → `dsa-recommender-transparency`; the wider **VLOP/VLOSE Section 5** systemic-risk, audit and researcher-access regime → `dsa-vlop-obligations`; the **intermediary tiers, enforcement structure and penalties** in overview → `dsa-foundations`; **marketplace / trader-traceability** duties (Arts. 30–32) → `dsa-marketplaces` (planned); the **UK age-appropriate-design** regime for children's services → `uk-childrens-code`; **GDPR** retention and data-subject-rights detail → `gdpr-foundations`.

**Assumptions:** The reader has read `dsa-foundations` and understands the intermediary tiers (mere conduit / caching / hosting / online platform) and the VLOP/VLOSE designation concept. Where moderation processes personal data (notifier identity, retained statements of reasons), the **GDPR applies in parallel** [4].

# Definitions

*Shared terms (intermediary service, online platform, VLOP/VLOSE, Digital Services Coordinator, illegal content, dark pattern) are in `GLOSSARY.md`. Terms specific to this document are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Notice-and-action | The Art. 16 mechanism by which any individual or entity can notify a hosting provider of specific items of allegedly illegal content, triggering a duty to act in a timely, diligent, non-arbitrary and objective manner. | [1] |
| Statement of reasons | The Art. 17 clear and specific explanation a hosting provider must give an affected recipient for any restriction imposed on legality or terms-of-service grounds. | [1] |
| Actual knowledge / awareness | The state — arising from an own-initiative investigation or a sufficiently substantiated Art. 16 notice — on which the hosting liability exemption turns; once obtained, the provider must act expeditiously (Art. 6, Art. 16(3)). | [1] |
| Internal complaint-handling system | The free, electronic, at-least-six-month appeal system online platforms must operate against moderation decisions, with non-solely-automated review (Art. 20). | [1] |
| Out-of-court dispute settlement body | A body certified by a Digital Services Coordinator to resolve moderation disputes recipients may refer under Art. 21; its decisions are not binding. | [1] |
| Trusted flagger | An entity awarded status by a Digital Services Coordinator (expertise, independence, diligence) whose notices online platforms must handle with priority (Art. 22). | [1] |
| Order to act against illegal content | An order issued by a national judicial or administrative authority under Art. 9 requiring a provider to act against one or more specific items of illegal content, subject to minimum content and territorial-scope limits. | [1] |
| DSA Transparency Database | The public Commission database in which online platforms publish their statements of reasons (Arts. 17(4), 24(5)), enabling aggregate scrutiny of moderation decisions. | [1][6] |

# Background

Until 2024, intermediary liability in the EU was governed by the **e-Commerce Directive (2000/31/EC)**, whose Arts. 12–15 created the "safe harbours" for mere conduit, caching and hosting and barred any **general obligation to monitor**. That framework was minimal and procedural gaps had grown: it said what a provider could be liable for, but little about *how* content should be flagged, *how quickly* it should be handled, *what a user should be told* when their content was removed, or *how they could contest it*. National laws diverged, fragmenting the single market and producing inconsistent, unaccountable moderation [1][2].

The DSA answers those gaps. It **preserves** the liability exemptions and the no-general-monitoring principle — re-enacting them as Arts. 4–8 — but repeals the corresponding e-Commerce provisions: DSA Art. 89 **deletes Arts. 12–15 of Directive 2000/31/EC**, so the safe harbours now live in the DSA itself [1][2]. On top of that stable liability base it layers **binding procedural due-diligence**: notice-and-action (Art. 16), statements of reasons (Art. 17), the redress ladder (Arts. 20–21), trusted flaggers (Art. 22) and anti-misuse measures (Art. 23), scaled cumulatively by service type. The regime entered into force on 16 November 2022 and became fully applicable to all intermediaries on 17 February 2024 [1][5]. The pre-DSA CJEU jurisprudence on hosting and injunctions (e.g. *Glawischnig-Piesczek*, C-18/18, on the compatibility of specific injunctions with the no-general-monitoring rule) remains contextually relevant but is not asserted here; it is tracked in the enforcement backlog [2].

# Legal Framework

The moderation duties sit in **Chapters II and III** of the DSA and are **cumulative** by tier: the liability rules (Arts. 4–8) apply to all intermediaries; notice-and-action and statements of reasons (Arts. 16–18) apply to **hosting services**; the redress ladder, trusted flaggers and anti-misuse rules (Arts. 20–23) apply to **online platforms** [1].

- **Liability layer (all intermediaries, Arts. 4–8):** mere conduit (4), caching (5), hosting (6), the voluntary "Good Samaritan" investigation clause (7), and **no general monitoring** (8). Hosting exemption under Art. 6 holds only while the provider lacks actual knowledge and acts **expeditiously** upon obtaining it.
- **Orders layer (Arts. 9–10):** providers must give effect to, and report on, **orders to act against illegal content** (9) and **orders to provide information** (10) from national authorities, each subject to minimum-content and territorial-scope safeguards.
- **All-intermediary due diligence (Arts. 14–15):** **terms and conditions** must disclose content-moderation policies, procedures and tools, including any algorithmic decision-making, and be applied diligently, objectively and proportionately with due regard to fundamental rights (14); **transparency reports** on moderation must be published (15).
- **Hosting layer (Arts. 16–18):** **notice-and-action** (16), **statement of reasons** (17), and notification of suspicions of serious criminal offences to authorities (18).
- **Online-platform layer (Arts. 20–24):** **internal complaint-handling** (20), **out-of-court dispute settlement** (21), **trusted flaggers** (22), **measures against misuse** (23), and platform **transparency reporting**, including submission of statements of reasons to the DSA Transparency Database (24, esp. 24(5)).

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 6 | Hosting liability exemption: no liability for stored content absent actual knowledge; on obtaining it, act **expeditiously** to remove/disable. | [1] |
| Art. 7 | Voluntary own-initiative investigations do not, by themselves, forfeit the exemptions ("Good Samaritan"). | [1] |
| Art. 8 | **No general obligation** to monitor or actively seek facts indicating illegal activity. | [1] |
| Arts. 9–10 | Give effect to and report on **orders to act against illegal content** and **orders to provide information**; minimum-content and scope safeguards. | [1] |
| Art. 14 | **Terms and conditions**: disclose moderation policies, procedures and tools (incl. algorithmic decision-making); apply them diligently, objectively, proportionately, with due regard to fundamental rights. | [1] |
| Art. 15 | **Transparency reporting** on content moderation for all intermediary providers. | [1] |
| Art. 16 | **Notice-and-action**: easy-to-access, user-friendly, electronic mechanism to flag specific allegedly illegal items; confirmation of receipt; decision + redress notice; a substantiated notice confers **actual knowledge** (16(3)). | [1] |
| Art. 17 | **Statement of reasons** for every restriction (removal, disabling, demotion, suspension, account action) on legality **or** T&C grounds; specified mandatory content; publish to the transparency database (17(4)). | [1] |
| Art. 18 | Notify competent authorities of information giving rise to suspicion of a serious criminal offence threatening life/safety. | [1] |
| Art. 20 | **Internal complaint-handling system**: free, electronic, ≥6 months, decisions **not solely automated**, reversible where the complaint is founded. | [1] |
| Art. 21 | **Out-of-court dispute settlement** before DSC-certified bodies; non-binding; fee allocation favouring the recipient. | [1] |
| Art. 22 | **Trusted flaggers**: priority, undue-delay-free handling of their notices; status awarded and revocable by a DSC; public database. | [1] |
| Art. 23 | **Measures against misuse**: suspend repeat posters of manifestly illegal content and repeat submitters of manifestly unfounded notices/complaints, after warning. | [1] |
| Art. 24(5) | Online platforms submit **statements of reasons** to the Commission's public **DSA Transparency Database**. | [1][6] |
| Art. 89 | Amends Directive 2000/31/EC by **deleting its Arts. 12–15** (the former safe harbours), now re-enacted as DSA Arts. 4–8. | [1][2] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited here from the primary text [1]. Numbers are given as approximate areas, consistent with the exemplar DSA documents.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 22 | Actual knowledge/awareness for the hosting exemption arises via own-initiative investigation or a sufficiently substantiated notice; expeditious action is then required. | [1] |
| Recital 50 area | Rationale for **notice-and-action**: mechanisms must be easy to access and use, and notices sufficiently precise to allow a diligent provider to assess the content. | [1] |
| Recital 53–54 area | Rationale for the **statement of reasons**: affected recipients should be given clear, meaningful information enabling them to seek redress. | [1] |
| Recital 61–62 area | Rationale for **trusted flaggers**: priority handling for entities with demonstrated expertise, independence and diligence. | [1] |
| Recital 63 area | Rationale for **measures against misuse**: proportionate suspension of repeat abusers and abusive notifiers, with safeguards. | [1] |

## Relevant Case Law

**Not Applicable at this level.** There is no settled CJEU merits ruling interpreting the DSA's Arts. 16–23 procedural duties. Pre-DSA jurisprudence on the e-Commerce Directive — notably *Glawischnig-Piesczek* (C-18/18) on specific injunctions and the no-general-monitoring rule, and *L'Oréal v eBay* (C-324/09) on hosting neutrality and knowledge — informs the inherited Arts. 6–8 concepts but is **not asserted here** and is tracked in the enforcement backlog [2]. Challenges to DSA enforcement decisions touching moderation procedure (e.g. the €120m X decision) are **emerging** and likewise tracked rather than relied on [8].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (European Commission / Ofcom — not statutory text unless a specific article is cited).**

- **"What is illegal offline should be illegal online," handled through accountable procedure.** The Commission frames the DSA's moderation regime as notice-and-action, transparency and redress rather than open-ended takedown discretion [5]. *(Regulatory interpretation.)*
- **The transparency database makes statements of reasons auditable at scale.** The Commission operates the **DSA Transparency Database**, into which online platforms submit their Art. 17 statements of reasons; it publishes millions of moderation records and is the primary lens on how platforms apply Arts. 16–17 [6]. *(Regulatory interpretation / operational fact.)*
- **Notice-and-action and appeals are enforcement priorities.** The Commission's **preliminary findings against Meta (24 October 2025)** included that Facebook's and Instagram's **notice-and-action** mechanisms for illegal content and their **complaint/appeal** processes were insufficiently easy to use and allegedly involved dark-pattern friction, engaging Arts. 16 and 20 [9]. *(Regulatory interpretation — preliminary, not final.)*
- **Procedural duties are outcome-tested.** The Commission's **first DSA fine — €120m against X (5 December 2025)** — concerned deceptive interface design, a non-compliant advertising repository and researcher-access barriers; while not a notice-and-action decision, it establishes that the DSA's procedural and transparency duties carry material penalties (up to 6% of worldwide turnover) [8]. *(Regulatory interpretation — first final decision.)*
- **The Commission publishes practical Q&A on moderation duties.** Its **DSA Questions-and-Answers** guidance explains notice-and-action, statements of reasons and redress for providers and users, and is a useful compliance reference (non-binding) [7]. *(Regulatory interpretation — non-binding.)*
- **The UK regulator takes a codes-of-practice route.** **Ofcom** supervises the Online Safety Act's illegal-content duties through **binding codes of practice and risk-assessment guidance**; its illegal-harms materials require services to assess and mitigate illegal-content risk rather than operate a DSA-style notice-and-action-plus-statement-of-reasons mechanism, and the codes are being **phased in** [10][11]. *(Regulatory interpretation — UK, phasing.)*

# Technical Considerations

- **Build the notice intake to Art. 16(2) fields.** The mechanism must capture a **substantiated explanation** of why the item is alleged illegal, the **exact electronic location** (e.g. URL), the **notifier's name and email** (except for notices concerning certain child-sexual-abuse offences), and a **good-faith accuracy statement**; only notices with these elements confer actual knowledge, so the schema should enforce them [1]. *(Legal obligation.)*
- **Automate acknowledgement and decision notices.** Art. 16 requires a **confirmation of receipt** and a notice of the **decision and available redress**; the pipeline must emit both, and disclose where **automated means** were used in processing [1]. *(Legal obligation.)*
- **Generate statements of reasons as structured records (Art. 17).** Each restriction must produce a record capturing: the action type and its **territorial scope and duration**; the **facts and circumstances** relied on (including whether triggered by a notice or own-initiative, and whether automated detection was used); the **legal ground** (for illegality) or **contractual/T&C ground** (for terms breaches) with an explanation; and the **redress options**. This structure both satisfies the recipient-facing duty and feeds the transparency-database submission [1][6]. *(Legal obligation.)*
- **Wire the transparency-database submission (Arts. 17(4), 24(5)).** Online platforms must push statements of reasons — **with personal data removed** — to the Commission's database, so the record pipeline needs a personal-data-scrubbing and API-submission stage [1][4][6]. *(Legal obligation for online platforms.)*
- **Implement the redress ladder as first-class product surfaces (Arts. 20–21).** A free, electronic **internal complaint** flow retained **at least six months**, whose decisions are **not solely automated** and are reversible, plus routing to **certified out-of-court** bodies and a clear statement of the right to court [1]. *(Legal obligation for online platforms.)*
- **Prioritise trusted-flagger channels and instrument misuse controls (Arts. 22–23).** A separate high-priority queue for trusted-flagger notices, and metering to detect **frequent manifestly illegal** posting and **frequent manifestly unfounded** notices/complaints so warnings and time-limited suspensions can be applied proportionately [1]. *(Legal obligation for online platforms.)*

# Hosting Considerations

- **The safe harbour is conditional on process (Arts. 6, 16).** A hosting provider keeps the Art. 6 exemption only while it lacks actual knowledge and acts **expeditiously** once a substantiated notice or own-initiative finding gives it knowledge; the notice-and-action mechanism is the very channel through which that knowledge is acquired, so its SLA is a liability control, not merely a UX feature [1]. *(Legal obligation — assess role.)*
- **No general monitoring, but specific orders bind (Arts. 8–10).** Providers cannot be required to generally monitor, but must still act on **specific** Art. 9 orders; architecture should support targeted takedown/blocking of identified items without standing up mass content surveillance [1]. *(Legal obligation.)*
- **Retention of statements of reasons is a GDPR-bounded data pipeline.** Statements of reasons and notice records contain personal data (notifier and recipient identity); retention must respect **GDPR** purpose-limitation and storage-limitation, and the transparency-database copy must be **anonymised** before submission [1][4]. *(Legal obligation — read with `gdpr-foundations`.)*
- **Pure infrastructure roles differ from the platform role.** A provider that merely supplies compute/storage to a platform is not itself the online platform owing Arts. 20–23; those duties fall on the provider that stores and disseminates the content to the public [1]. *(Interpretation.)*

# Game Hosting Considerations

- **UGC and public chat can pull a game into the hosting/platform tiers.** If a game **stores** user content (uploads, mods, profiles) it is a hosting service owing notice-and-action (16) and statements of reasons (17); if it **stores and disseminates content to the public** (public forums, mod hubs, shared creations, unmoderated public chat) the operator is likely an **online platform** owing the redress ladder, trusted-flagger priority and anti-misuse duties (Arts. 20–23). Purely private/session chat is more likely a minor/ancillary feature outside the online-platform definition [1]. *(Legal obligation — assess feature by feature.)*
- **In-game moderation actions are "restrictions" needing statements of reasons.** Muting, shadow-restriction/demotion, item or content removal, and account/service **suspensions or bans** are Art. 17 restrictions and require a statement of reasons and redress route — including where an anti-cheat or automated toxicity classifier drove the action [1]. *(Legal obligation.)*
- **Repeat-offender and false-report handling maps to Art. 23.** Games already run repeat-abuse and false-report systems; these must be aligned with Art. 23's **warning-then-proportionate-suspension** structure for both abusive players and abusive reporters [1]. *(Legal obligation for online platforms.)*
- **Child-safety context raises the stakes.** Large under-18 audiences intensify scrutiny of moderation and reporting flows and interact with the UK Children's Code and OSA child-safety duties; see `uk-childrens-code` [1][3]. *(Legal obligation — assess.)*

# AI Considerations

- **Automated moderation still owes a statement of reasons (Art. 17).** Where content is detected, demoted or removed by a classifier or an LLM-based safety model, Art. 17 requires disclosure that **automated means** were used and an explanation of the ground; automation does not reduce the transparency duty [1]. *(Legal obligation.)*
- **Internal complaints cannot be solely automated (Art. 20).** The appeal against a moderation decision must involve non-solely-automated review, so an AI-first moderation stack needs a **human-in-the-loop** appeal path [1]. *(Legal obligation.)*
- **GDPR Art. 22 may engage automated moderation.** Where a **solely automated** moderation decision (e.g. permanent account termination) produces legal or similarly significant effects on a person, **GDPR Art. 22** safeguards apply in parallel with the DSA [4]. *(Legal obligation — read with `gdpr-foundations`.)*
- **AI Act overlap.** Where a provider deploys AI for moderation, generation or recommendation, the **AI Act (Reg (EU) 2024/1689)** may apply alongside the DSA (e.g. Art. 50 transparency for AI-generated/synthetic content); the DSA governs the **moderation procedure**, the AI Act governs **AI risk** — see `ai-act-foundations` and `dsa-recommender-transparency` [1]. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** (the provider must) / **BEST PRACTICE** (should) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Stand up an Art. 16 notice-and-action mechanism** with the mandatory notice fields, automated receipt confirmation, and a decision-plus-redress notice. *(OBLIGATION — hosting services.)* [1]
2. **Treat a complete notice as actual knowledge** and act expeditiously; set and monitor takedown SLAs as a safe-harbour control (Art. 6, 16(3)). *(OBLIGATION.)* [1]
3. **Generate a statement of reasons for every restriction (Art. 17)** — legality *and* terms-of-service actions — with action, scope/duration, facts, automated-means disclosure, legal/contractual ground and redress. *(OBLIGATION.)* [1]
4. **Submit statements of reasons to the DSA Transparency Database (Arts. 17(4), 24(5))**, anonymised. *(OBLIGATION — online platforms.)* [1][6]
5. **Operate the redress ladder (Arts. 20–21):** free ≥6-month internal complaints with non-solely-automated, reversible review, then certified out-of-court dispute settlement, and always the right to court. *(OBLIGATION — online platforms.)* [1]
6. **Give trusted flaggers priority handling (Art. 22)** via a distinct queue and SLA. *(OBLIGATION — online platforms.)* [1]
7. **Implement anti-misuse measures (Art. 23)** — warning-then-suspension for repeat illegal posters and repeat unfounded notifiers, with logged justification. *(OBLIGATION — online platforms.)* [1]
8. **Publish moderation policies and tools in your terms (Art. 14)** and apply them diligently, objectively and proportionately; publish transparency reports (Arts. 15, 24). *(OBLIGATION.)* [1]
9. **Build orders-handling (Arts. 9–10)** to give effect to and report back on national authority orders without general monitoring. *(OBLIGATION.)* [1]
10. **Run DSA and GDPR together** for notifier/recipient data, statement-of-reasons retention and Art. 22 automated-decision safeguards. *(OBLIGATION + BEST PRACTICE.)* [1][4]
11. **For UK reach, map to the Online Safety Act** illegal-content risk assessment and safety duties and the relevant **Ofcom codes**, and reconcile them with your DSA moderation system. *(OBLIGATION where in scope — UK.)* [3][10][11]
12. **Maintain a live enforcement watch-list** (Meta notice/appeal findings, X decision, evolving Ofcom codes) and feed it into product and policy review. *(EDITORIAL RECOMMENDATION.)* [8][9][11]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Missing or non-conforming notice-and-action mechanism | Medium | High | Art. 16 [1] | Build compliant intake with mandatory fields, receipts, decision notices | Low |
| R2 | Losing the hosting safe harbour by not acting expeditiously on knowledge | Medium | High | Arts. 6, 16(3) [1] | Treat complete notices as knowledge; enforce takedown SLAs | Low |
| R3 | Statements of reasons absent, incomplete or not published | Medium | High | Arts. 17, 24(5) [1][6] | Structured SoR records; anonymised transparency-database submission | Low |
| R4 | Redress ladder missing or appeals solely automated | Medium | High | Arts. 20–21 [1] | Free ≥6-month complaints with human review; certified out-of-court routing | Low |
| R5 | Trusted-flagger notices not prioritised | Low | Medium | Art. 22 [1] | Dedicated priority queue and SLA | Low |
| R6 | Inadequate anti-misuse handling (or disproportionate suspensions) | Medium | Medium | Art. 23 [1] | Warning-then-proportionate-suspension with logged justification and appeal | Low |
| R7 | Dark-pattern friction in notice/appeal flows (Meta-type finding) | Medium | High | Arts. 16, 20; Meta prelim [1][9] | UX review; remove manipulative friction from reporting/appeal | Medium |
| R8 | GDPR breach in retaining/publishing moderation data | Medium | High | GDPR [4]; Arts. 17(4) [1] | Purpose/storage limits; anonymise before database submission | Low |
| R9 | Divergent EU/UK obligations mishandled (OSA duties missed) | Medium | High | OSA [3]; Ofcom codes [10][11] | Joint DSA/OSA control mapping; track Ofcom code phasing | Medium |
| R10 | Over-removal chilling lawful expression / under-removal of illegal content | Medium | Medium | Arts. 14, 17 [1] | Diligent, proportionate policies; reasoned decisions; redress metrics | Medium |

# Implementation Roadmap

- **Phase 0 — Tier & role mapping:** Confirm whether each service is a hosting service and/or online platform and which moderation duties attach. *Effort:* Medium.
- **Phase 1 — Notice-and-action & knowledge (Arts. 6, 16):** Build the intake, receipts, decision notices and takedown SLAs; treat complete notices as actual knowledge. *Effort:* Medium.
- **Phase 2 — Statements of reasons (Art. 17):** Structured SoR generation for every restriction, with automated-means disclosure and redress info. *Effort:* Medium.
- **Phase 3 — Transparency database & reporting (Arts. 17(4), 15, 24):** Anonymised submission pipeline and periodic transparency reports. *Effort:* Medium.
- **Phase 4 — Redress ladder & flaggers (Arts. 20–23):** Internal complaints, out-of-court routing, trusted-flagger priority, anti-misuse controls. *Effort:* High.
- **Phase 5 — Terms, orders & GDPR alignment (Arts. 9–10, 14; GDPR):** Publish moderation policies; orders-handling; joint data-protection review. *Effort:* Medium.
- **Phase 6 — UK OSA reconciliation & monitoring:** Map to OSA illegal-content duties and Ofcom codes; maintain the enforcement watch-list. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Ad-hoc, discretionary moderation; no notice-and-action or reasons. | Removals without records; no appeal path. |
| 2 | Managed | Notice-and-action live; basic statements of reasons issued. | Art. 16 intake and Art. 17 records exist. |
| 3 | Defined | Full SoR content, transparency-database submission, internal complaints and out-of-court routing operational. | Arts. 17, 20–21, 24(5) operational; trusted-flagger queue. |
| 4 | Quantitatively Managed | Metrics on notices, takedown time, appeals and reversals; anti-misuse and dark-pattern controls tested. | KPIs on Arts. 16/17/20/23; UX audits; DB data quality checks. |
| 5 | Optimising | Integrated DSA + GDPR + (for UK) OSA moderation governance with independent assurance. | Cross-regime programme; audited moderation; watch-list feeds design. |

# Audit Questions

1. How do users submit notices (Art. 16), and does the intake capture the mandatory fields and issue receipts and decision-plus-redress notices? *([1].)*
2. Is a complete notice treated as **actual knowledge**, with expeditious action and monitored SLAs? *(Arts. 6, 16(3) [1].)*
3. Does every restriction — on legality **and** terms grounds — generate a **statement of reasons** with all Art. 17 elements, including automated-means disclosure? *(Art. 17 [1].)*
4. Are statements of reasons submitted to the **DSA Transparency Database**, anonymised? *(Arts. 17(4), 24(5) [1][6].)*
5. Is there a free, ≥6-month **internal complaint** system whose decisions are not solely automated and are reversible? *(Art. 20 [1].)*
6. Can recipients use **certified out-of-court dispute settlement**, and is the right to court preserved? *(Art. 21 [1].)*
7. Are **trusted-flagger** notices prioritised, and are **anti-misuse** suspensions applied proportionately after warning? *(Arts. 22–23 [1].)*
8. Do the **terms and conditions** disclose moderation policies and tools, and are transparency reports published? *(Arts. 14, 15, 24 [1].)*
9. Is moderation data handled in line with **GDPR** (retention, anonymisation, Art. 22)? *(GDPR [4]; Arts. 17(4) [1].)*
10. For UK-facing services: are the **Online Safety Act** illegal-content risk assessment and safety duties, and the relevant **Ofcom codes**, satisfied and reconciled with the DSA system? *(OSA [3]; Ofcom [10][11].)*

# Implementation Checklist

- [ ] Notice-and-action mechanism (Art. 16) live with mandatory fields, receipts and decision-plus-redress notices.
- [ ] Complete notices treated as actual knowledge; expeditious-action SLAs monitored (Arts. 6, 16(3)).
- [ ] Statement of reasons generated for every restriction, legality and T&C, with automated-means disclosure (Art. 17).
- [ ] Statements of reasons submitted to the DSA Transparency Database, anonymised (Arts. 17(4), 24(5)).
- [ ] Free, ≥6-month internal complaint-handling system with non-solely-automated, reversible review (Art. 20).
- [ ] Certified out-of-court dispute settlement routing and right-to-court notice (Art. 21).
- [ ] Trusted-flagger priority queue (Art. 22).
- [ ] Anti-misuse warning-then-suspension controls for repeat abusers and abusive notifiers (Art. 23).
- [ ] Moderation policies/tools disclosed in terms (Art. 14); transparency reports published (Arts. 15, 24).
- [ ] Orders-handling for Arts. 9–10 without general monitoring.
- [ ] GDPR retention/anonymisation and Art. 22 safeguards for moderation data.
- [ ] UK Online Safety Act illegal-content duties and Ofcom codes mapped and reconciled (where in scope).
- [ ] Enforcement watch-list maintained (Meta notice/appeal findings; X decision; Ofcom code phasing).

# References

*All links verified live (HTTP 200) on 2026-07-12 (`sources_verified`). Enforcement and guidance facts were re-confirmed against primary and European Commission / Ofcom sources on the same date.*

## Primary Sources

- [1] **Regulation (EU) 2022/2065 (Digital Services Act).** EUR-Lex, ELI (Arts. 4–10, 14–18, 20–24, 89; Recitals 22, 50–63 area). https://eur-lex.europa.eu/eli/reg/2022/2065/oj
- [2] **Directive 2000/31/EC (e-Commerce Directive).** EUR-Lex, ELI — the former Arts. 12–15 safe harbours and no-general-monitoring rule, deleted by DSA Art. 89 and re-enacted as DSA Arts. 4–8. https://eur-lex.europa.eu/eli/dir/2000/31/oj
- [3] **Online Safety Act 2023 (c.50).** legislation.gov.uk — UK illegal-content risk-assessment and safety-duty framework; Ofcom as regulator. https://www.legislation.gov.uk/ukpga/2023/50/contents
- [4] **Regulation (EU) 2016/679 (GDPR).** EUR-Lex, ELI — parallel application to notifier/recipient data, statement-of-reasons retention/anonymisation, and Art. 22 automated-decision safeguards. https://eur-lex.europa.eu/eli/reg/2016/679/oj

## Regulatory Guidance

- [5] **The Digital Services Act package.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/digital-services-act-package
- [6] **DSA Transparency Database.** European Commission — public database of statements of reasons submitted under Arts. 17(4) and 24(5). https://transparency.dsa.ec.europa.eu/
- [7] **The Digital Services Act — Questions and Answers.** European Commission — practical guidance on notice-and-action, statements of reasons and redress (non-binding). https://digital-strategy.ec.europa.eu/en/faqs/digital-services-act-questions-and-answers
- [8] **Commission fines X €120 million under the Digital Services Act** (first DSA non-compliance decision, 5 December 2025). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-fines-x-eu120-million-under-digital-services-act
- [9] **Commission preliminarily finds TikTok and Meta in breach of their transparency obligations under the DSA** (24 October 2025; Meta's notice-and-action (Art. 16) and complaint/appeal (Art. 20) mechanisms among the concerns). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-preliminarily-finds-tiktok-and-meta-breach-their-transparency-obligations-under-digital
- [10] **Online safety.** Ofcom — the UK online-safety regime and Online Safety Act duties hub. https://www.ofcom.org.uk/online-safety/
- [11] **Protecting people from illegal harms online.** Ofcom — illegal-content codes of practice and risk-assessment guidance (phased implementation). https://www.ofcom.org.uk/online-safety/illegal-and-harmful-content/statement-protecting-people-from-illegal-harms-online/

## Standards

Not Applicable — the DSA moderation and redress duties are enforced through legislation, Commission decisions and guidance rather than voluntary technical standards. Related security, privacy and auditing standards (ISO/IEC 27001, ISO/IEC 27701, ISO 19011) are treated in the security, privacy-engineering and governance documents.

## Academic Sources

Not Applicable — this sub-topic reference relies on primary legislation (the DSA, the e-Commerce Directive, the OSA and the GDPR) and Commission / Ofcom guidance and enforcement. Peer-reviewed analysis of notice-and-action and over-removal effects will be cited in `dsa-vlop-obligations` (planned) if adopted.

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Commission — DSA Transparency Database (dashboard and data downloads). https://transparency.dsa.ec.europa.eu/
- Digital Services Act — Wikipedia (overview and enforcement chronology; non-authoritative). https://en.wikipedia.org/wiki/Digital_Services_Act
- Online Safety Act 2023 — Wikipedia (UK regime overview; non-authoritative). https://en.wikipedia.org/wiki/Online_Safety_Act_2023

# Related Documents

- `dsa-foundations` — parent overview: intermediary tiers, the liability regime and the enforcement structure (**prerequisite reading**).
- `dsa-vlop-obligations` — Section 5 deep dive: systemic-risk, audit and researcher-access duties for designated services.
- `dsa-recommender-transparency` — recommender-system and advertising transparency, dark patterns and minor protection (Arts. 25–28, 38–39).
- `consumer-rights-foundations` — EU/UK consumer-protection regime intersecting with terms-and-conditions and dark-pattern rules.
- `uk-childrens-code` — the UK age-appropriate-design regime and child-safety duties intersecting with moderation.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-12 | Technical Writer (virtual agent) | Initial draft; content-moderation, notice-and-action (Art. 16), statements of reasons (Art. 17), the redress ladder (Arts. 20–21), trusted flaggers (Art. 22), anti-misuse (Art. 23) and the liability safe harbour / no-general-monitoring rule (Arts. 4–8, Art. 89) researched against EUR-Lex (Reg (EU) 2022/2065 and Directive 2000/31/EC), the GDPR, the UK Online Safety Act 2023, and European Commission / Ofcom sources. Enforcement live-verified on 2026-07-12: the €120m X fine (5 Dec 2025) and the TikTok/Meta transparency preliminary findings (24 Oct 2025, incl. Meta's Art. 16/20 mechanisms). All 11 external references and 3 further-reading links returned HTTP 200. | pending |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster D, residual list); full-repo validator/link/lint suite green; frozen in release 0.18.0. | Orchestrator (QA-verified) |
