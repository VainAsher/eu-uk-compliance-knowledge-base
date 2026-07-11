---
id: uk-childrens-code
title: "UK Children's Code (Age-Appropriate Design Code)"
version: 1.0.0
status: in-review
classification: public
jurisdiction: [UK]
topic: UK GDPR
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [uk-gdpr-foundations, duaa-2025-detail, game-hosting-foundations, gdpr-foundations, eprivacy-foundations, privacy-engineering-foundations, dpia-methodology]
tags: [childrens-code, aadc, age-appropriate-design, dpa-2018-s123, likely-to-be-accessed-by-children, age-assurance, duaa-2025, online-safety-act, ico, ofcom]
legal_basis: Data Protection Act 2018 (esp. ss.123, 125, 9); UK GDPR (Regulation (EU) 2016/679 as assimilated), esp. Arts. 8, 25, 35; Data (Use and Access) Act 2025 (c.18) s.81
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | uk-childrens-code |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.14.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The Children's Code is a live statutory code; the **Data (Use and Access) Act 2025** has added a new statutory children's duty (UK GDPR Art. 25(1A)/(1B), inserted by DUAA s.81), and the ICO has signalled that the Code itself will be revised and re-laid before Parliament in due course. Confirm the current text of the Code and the in-force status of DUAA provisions before relying on any time-sensitive statement below [5][6][12].

# Executive Summary

The **UK Children's Code** — formally the **Age-Appropriate Design Code (AADC)** — is a **statutory code of practice** prepared by the ICO under **section 123 of the Data Protection Act 2018 (DPA 2018)** and laid before Parliament under s.125 [1][2]. It sets **15 standards** that any provider of an "information society service" (ISS) **"likely to be accessed by children"** in the UK must apply when it processes children's personal data [10][11]. The Code came into force on **2 September 2020**, with a 12-month transition period, and has been **fully enforceable since 2 September 2021** [11][14]. It is not a new source of obligation so much as an authoritative interpretation of how the **UK GDPR and DPA 2018** apply to under-18s — the ICO must take it into account when exercising its enforcement powers, and courts and tribunals must take it into account where relevant [1][10].

This document builds on `uk-gdpr-foundations` (the UK consent age of **13** under DPA 2018 s.9) and `duaa-2025-detail`. It goes deep on the statutory basis; the **"likely to be accessed by children"** threshold; each of the **15 standards** (best interests, DPIAs, age-appropriate application, transparency, detrimental use of data, policies, **high-privacy default settings**, data minimisation, data sharing, geolocation, parental controls, **profiling off by default**, **nudge techniques**, connected toys/devices, online tools); **age assurance**; how the **DUAA 2025 children's duty** strengthens the position by putting a children's obligation on the face of UK GDPR Art. 25; and the interplay with the **Online Safety Act 2023** and **Ofcom's Protection of Children Codes** [5][8][11][15].

Three conclusions dominate. First, the Code's reach is **wide**: "likely to be accessed by children" is a lower bar than "aimed at" children, so most consumer-facing services — games especially — are caught [10]. Second, the DUAA has **hardened** the children's position: from 2026 there is an **express statutory duty** in Art. 25 to have regard to "children's higher protection matters", and conforming to the Code is the ICO's expected route to satisfying it [5][12][13]. Third, the Code (data-protection/privacy design) and the **Online Safety Act** (content-safety, Ofcom-regulated) are **distinct but complementary** regimes that both turn on a "likely to be accessed by children" test and both expect proportionate **age assurance** [11][15][16].

# Key Takeaways

- The Children's Code (AADC) is a **statutory code** under **DPA 2018 s.123**, laid before Parliament under s.125; it interprets how the UK GDPR/DPA 2018 apply to children and the ICO must take it into account in enforcement [1][2][10]. *(Legal obligation / regulatory interpretation.)*
- It applies to **relevant ISS "likely to be accessed by children"** (under-18s) in the UK — a **lower threshold** than services "directed at" or "intended for" children [10][11]. *(Legal obligation.)*
- It sets **15 standards**, anchored on the **best interests of the child** as a primary consideration, and including **high-privacy default settings**, **data minimisation**, **geolocation off by default**, **profiling off by default**, and **no nudge techniques** that push children to weaken privacy [11]. *(Legal obligation, as interpreted.)*
- The Code came into force **2 September 2020** and has been **enforceable since 2 September 2021** after a 12-month transition [11][14]. *(Fact — live-verified.)*
- The UK **age of consent** for ISS is **13** (DPA 2018 s.9); the Code applies to **all under-18s**, so it reaches children **above** the consent age too [3][10]. *(Legal obligation.)*
- The **DUAA 2025 (s.81)** inserts **UK GDPR Art. 25(1A)/(1B)** — an **express duty** on controllers providing an ISS likely to be accessed by children to consider **"children's higher protection matters"** in data-protection-by-design — strengthening and codifying the Code's expectations [5][12][13][17]. *(Legal obligation — DUAA commencement per `duaa-2025-detail`.)*
- **Age assurance** is central: the Code requires a **risk-based** approach — either establish age with a level of certainty appropriate to the data risks, **or** apply the standards to **all** users [11]. *(Legal obligation, as interpreted.)*
- Enforcement uses the **ICO's ordinary UK GDPR/DPA 2018 powers** (assessment notices, enforcement notices, and fines up to **£17.5m or 4%** of global turnover); non-conformity with the Code is strong evidence of a breach of the underlying law [10][14]. *(Legal obligation.)*
- The Code is **distinct from** the **Online Safety Act 2023**: the OSA (Ofcom-regulated) governs **content safety**, and its **Protection of Children Codes came into force 25 July 2025**; the two regimes overlap on "likely to be accessed by children" and age assurance but pursue different aims [8][15][16]. *(Legal fact — live-verified.)*

# Purpose

This document is the sub-topic deep-dive on the UK Children's Code. It supports: (a) legal research — the statutory basis of the Code, its scope test, and its relationship to the UK GDPR, DPA 2018 and the DUAA 2025 children's duty; (b) compliance implementation — a standard-by-standard reading and an implementation checklist for services likely to be accessed by children; and (c) programme design — reconciling the Code with the Online Safety Act, the age-13 consent rule and age-assurance choices. It **details** `uk-gdpr-foundations` (which sets the UK 13 consent age) and is a **sibling** of `duaa-2025-detail` and `game-hosting-foundations`; it does not restate the UK GDPR's constitutional basis or the EU baseline (see `gdpr-foundations`).

# Scope

**In scope:** The statutory basis of the Children's Code (DPA 2018 ss.123, 125); the "likely to be accessed by children" threshold; the 15 standards and what each requires; age assurance; the DPIA obligation for services likely to be accessed by children; the DUAA 2025 children's duty (UK GDPR Art. 25(1A)/(1B), s.81) and how it strengthens the Code; the age-13 consent cross-reference (DPA 2018 s.9); enforcement; and the interplay with the Online Safety Act 2023 / Ofcom's children's codes.

**Out of scope (cross-referenced):** UK GDPR foundations and the 13 consent age in depth → `uk-gdpr-foundations`; the DUAA 2025 in depth (ADM, recognised legitimate interests, complaints, transfers, commencement dates) → `duaa-2025-detail`; DPIA methodology → `dpia-methodology`; ePrivacy/PECR consent for SDKs → `eprivacy-foundations`; game-specific overlay (loot boxes, PEGI, DSA/OSA for UGC) → `game-hosting-foundations`; the Online Safety Act's substantive content-safety duties and Ofcom codes end-to-end (treated only at the interplay level here); detailed technical evaluation of specific **age-assurance vendors/methods** → research backlog.

**Assumptions:** The reader has `uk-gdpr-foundations` and `gdpr-foundations`. "Child" means a person **under 18** for the Code (the age of a child in England, Wales and Northern Ireland; the ICO applies the Code to under-18s across the UK), which is **wider** than the 13-year consent threshold [10][11].

# Definitions

*Shared terms (personal data, controller, processor, consent, ISS, special-category data, DPbDD, DPIA) are in `GLOSSARY.md` and carry over. Only Code-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Children's Code (AADC) | The ICO statutory code of practice under DPA 2018 s.123 setting 15 standards of age-appropriate design for relevant ISS likely to be accessed by children. Also called the Age-Appropriate Design Code. | [1][10][11] |
| Relevant information society service (ISS) | An ISS as defined for the UK GDPR/DPA, excluding certain preventive/counselling services; the class of service to which the Code and the s.9 consent rule attach. Online games, apps and websites are ISS. | [3][10] |
| Likely to be accessed by children | The Code's scope test: the possibility of the service being accessed by under-18s is **more probable than not**, judged on the nature and appeal of the service and evidence of its actual user base — a lower bar than "directed at" children. | [10][11] |
| Age assurance | The umbrella term for techniques used to establish or estimate a user's age or age range (self-declaration, age estimation, age verification, hard identifiers), applied proportionately to the data risks. | [11] |
| Children's higher protection matters | The matters a controller providing an ISS likely to be accessed by children must consider under UK GDPR Art. 25(1A)/(1B) (inserted by DUAA s.81): how to protect and support children, children's lower awareness of risks, and their differing needs at different ages and stages of development. | [5][17] |
| Best interests of the child | The primary consideration in designing services likely to be accessed by children (Standard 1), drawn from Article 3 of the UN Convention on the Rights of the Child and reflected in the Code. | [11] |

# Background

Children's data protection sat uneasily in a framework built for adults. GDPR **Recital 38** recognised that children "merit specific protection" because they may be less aware of the risks, and **Article 8** introduced a child-consent rule for ISS — but neither told designers *how* to build for children [4]. In the UK, DPA 2018 set the ISS consent age at **13** (s.9) and, unusually, **required the regulator to write a design code**: s.123 obliges the Information Commissioner to produce a code of practice on "standards of age-appropriate design" for relevant ISS likely to be accessed by children, and s.125 sets the Parliamentary procedure for laying and issuing it [1][2][3].

The ICO consulted and published the final Code in 2020. It **came into force on 2 September 2020**, the first age-appropriate design code laid under s.123/s.125, with a **12-month transition** so organisations could adapt; it has been fully in effect since **2 September 2021** [11][14]. The Code drew international attention and influenced comparable measures abroad. Since then, two developments have reshaped the landscape: the **Online Safety Act 2023**, which put content-safety duties on user-to-user and search services under Ofcom (its Protection of Children Codes came into force 25 July 2025) [8][15]; and the **Data (Use and Access) Act 2025**, which — via s.81 — put an **express children's duty on the face of UK GDPR Art. 25**, aligning the primary law with what the Code already expected [5][12]. The ICO has said it will **revise and re-lay the Code** to reflect the DUAA and its updated children's-data guidance in due course [12][13].

# Legal Framework

The Children's Code is a **statutory code of practice**, not a statute in itself. Its legal force is indirect but real: it interprets the **UK GDPR** and **DPA 2018** as they apply to children, and DPA 2018 requires the ICO to **take the Code into account** when exercising its functions (and courts/tribunals to take it into account where relevant to a question before them) [1][10]. A controller that does not conform to the Code is not automatically unlawful, but the ICO treats **non-conformity as strong evidence of a breach** of the underlying UK GDPR/DPA obligations it interprets [10][14].

The obligation stack for a service likely to be accessed by children is therefore:

1. **UK GDPR** — principles (Art. 5), lawful basis (Art. 6, incl. child consent under Art. 8 as modified), **data-protection by design and by default (Art. 25)**, and **DPIA (Art. 35)** — as assimilated under EUWA 2018 s.3 [4][9].
2. **DPA 2018** — s.9 (13-year ISS consent age), s.123 (duty to produce the Code), s.125 (procedure), and the ICO's enforcement powers [1][2][3].
3. **DUAA 2025 s.81** — inserts UK GDPR **Art. 25(1A)/(1B)**, an express duty to consider "children's higher protection matters" in DPbDD for ISS likely to be accessed by children, commenced as part of the DUAA Part 5 data-protection provisions (SI 2026/82; dates in `duaa-2025-detail`) [5][7][17].
4. **The Children's Code** — the 15 standards operationalising all of the above [11].

## Relevant Articles

*"Article" spans the UK GDPR, the DPA 2018 sections and the DUAA amendment as relevant.*

| Provision | Obligation (as relevant to the Children's Code) | Source |
|-----------|-------------------------------------------------|--------|
| DPA 2018 s.123 | Requires the ICO to prepare an **age-appropriate design code** for relevant ISS likely to be accessed by children — the Code's statutory basis. | [1] |
| DPA 2018 s.125 | Procedure for issuing the Code (laid before Parliament; the ICO and courts must have regard to it). | [2] |
| DPA 2018 s.9 | Sets the UK ISS **child-consent age at 13** (modifying UK GDPR Art. 8(1)). | [3] |
| UK GDPR Art. 8 | Conditions for a child's consent to ISS; controller must make reasonable efforts to verify parental authorisation for younger children. | [4] |
| UK GDPR Art. 25 | **Data-protection by design and by default** — the anchor for high-privacy defaults and minimisation for children. | [4] |
| UK GDPR Art. 25(1A)/(1B) (DUAA s.81) | **Express duty** on controllers of ISS likely to be accessed by children to consider **"children's higher protection matters"** in DPbDD. | [5][17] |
| UK GDPR Art. 35 | **DPIA** required where processing is likely to result in a high risk — the ICO treats services likely to be accessed by children as normally requiring one (Standard 2). | [4][11] |
| UK GDPR Recital 38 | Interpretive anchor: children merit **specific protection** as they may be less aware of risks/consequences. | [4] |
| Online Safety Act 2023 | Separate content-safety regime (Ofcom) for user-to-user/search services likely to be accessed by children — complementary to, not part of, the Code. | [8] |

## Relevant Recitals

*Recitals of the UK GDPR are retained as interpretive aids (see `gdpr-foundations`); they are not binding operative provisions.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| UK GDPR Recital 38 | Children merit **specific protection** with regard to their personal data, especially for marketing, profiling and services offered directly to a child — the core rationale for the Code. | [4] |
| UK GDPR Recital 58 | Information addressed specifically to a child should be in **clear, plain language** the child can easily understand (informs Standard 4, transparency). | [4] |

## Relevant Case Law

**Not Applicable.** The Children's Code is a regulator's statutory code rather than a provision generating its own body of judicial interpretation, and there is no reported UK judgment squarely construing the Code's 15 standards. Enforcement to date has run through **ICO regulatory action and audits** rather than litigation, and the DUAA children's duty (Art. 25(1A)/(1B)) is too new to have been tested in court [5][10]. The general UK GDPR concepts the Code interprets (personal data, DPbDD) rest on the retained/assimilated case law noted in `uk-gdpr-foundations`. Early disputes are more likely to surface as ICO enforcement than as case law.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).** The authoritative reading is the **ICO's** Children's-code guidance suite and its DUAA children's-data guidance, supported by DSIT/GOV.UK materials [10][11][12][13][14].

- **Scope is deliberately broad.** The ICO reads **"likely to be accessed by children"** as a lower bar than "aimed at" children: the question is whether the service's nature and appeal, and evidence of its actual users, make access by under-18s **more probable than not**. If children are unlikely to access the service (robustly evidenced, e.g. by effective age assurance), the Code may not bite — but the default assumption for consumer services is that it does [10][11]. *(Regulatory interpretation.)*
- **The child is under 18, not 13.** The Code protects **all under-18s**, so it applies to children who are **old enough to consent** (13+) as well as younger ones; the 13 threshold governs *consent* (DPA s.9), while the Code governs *design* for the whole 0–17 population, expecting age-band-appropriate treatment [3][10][11]. *(Regulatory interpretation.)*
- **Best interests as the lens.** Standard 1 requires the **best interests of the child** to be a **primary consideration** in design — the ICO frames every other standard as an application of this principle, drawing on the UN Convention on the Rights of the Child [11]. *(Regulatory interpretation.)*
- **Conform-or-justify defaults.** Several standards (default settings, geolocation, profiling, data sharing) require **high-privacy/off-by-default** settings **"unless you can demonstrate a compelling reason"** taking account of the child's best interests — a documented-justification model rather than an absolute ban [11]. *(Regulatory interpretation of a legal obligation.)*
- **The DUAA reinforces, it does not replace.** The ICO's position is that organisations **already conforming to the Children's Code should already satisfy** the new Art. 25(1A)/(1B) "children's higher protection matters" duty; the DUAA puts the expectation on the face of the primary law and the ICO updated its children's-data guidance (15 May 2026) to reflect it, with a revised Code to follow and be re-laid before Parliament [12][13]. *(Regulatory interpretation.)*
- **Distinct from the Online Safety Act.** The ICO (data protection) and **Ofcom** (online safety) regulate different things — privacy-by-design versus content safety — but coordinate; both use a "likely to be accessed by children" test and both expect **proportionate age assurance**. Conforming to one does **not** discharge the other [15][16]. *(Regulatory interpretation.)*

# Technical Considerations

- **Age assurance architecture.** Implement a **risk-based** age-assurance layer: either establish age/age-range with certainty proportionate to the data risks, or apply the Code's protections to **all** users. Options range from self-declaration (low assurance) through **age estimation** to **hard age verification**; escalate assurance with the risk, and **minimise** the identity data the assurance step itself collects (do not turn age-gating into a data-grab) [11]. *(Legal obligation, as interpreted.)*
- **High-privacy defaults by construction.** Ship child accounts with **high-privacy defaults**, **geolocation off**, **profiling off**, social discovery/visibility off, and behavioural advertising off — changing them should require a deliberate, age-appropriate action, not a pre-ticked box [11]. *(Legal obligation.)*
- **Data minimisation and separated choices.** Collect only what is needed for the element of the service the child is **actively and knowingly** engaged in, and give **separate** toggles for optional elements rather than an all-or-nothing bundle [11]. *(Legal obligation.)*
- **DPIA-first.** Treat a **DPIA** (see `dpia-methodology`) as the mandatory front door for any service likely to be accessed by children; it must cover differing ages/capacities and bake in Code conformance (Standard 2) [4][11]. *(Legal obligation.)*
- **No dark patterns / nudges.** Do not use **nudge techniques** or deceptive design to push children to provide unnecessary data or lower protections; this overlaps with DSA Art. 25 and consumer law for services in those regimes (see `game-hosting-foundations`) [11]. *(Legal obligation.)*
- **Connected devices.** For **connected toys/devices**, build in the tooling (clear information, controls, secure defaults) needed to conform, including at set-up when an adult may configure on the child's behalf [11]. *(Legal obligation, as interpreted.)*

# Hosting Considerations

- **Controller/processor split.** The service provider (studio/app publisher) is typically the **controller** and bears the Code duties; cloud/hosting and age-assurance vendors are usually **processors** needing Art. 28 contracts (see `gdpr-foundations`). Age-assurance providers process potentially sensitive identity/biometric data — scrutinise their minimisation and retention [11]. *(Legal obligation.)*
- **Data residency and transfers.** Children's data is ordinary personal data for transfer purposes; apply the UK transfer mechanisms (adequacy, IDTA/Addendum) — see `uk-transfers`. *(Legal obligation; cross-reference.)*
- **Retention and deletion.** Standard 8 (minimisation) implies **short retention** and prompt deletion/aggregation of children's data; hosting/log pipelines must support age-band-aware retention and honour deletion. *(Best practice grounded in obligation.)* [11]
- **Age-assurance data isolation.** Store any hard identifiers collected for age verification **separately** from the service profile, encrypted, with tight access controls and minimal retention — the assurance purpose does not license general profiling [11]. *(Best practice.)*

# Game Hosting Considerations

- **Games are the paradigm case.** The Code names **games** among the services it targets, and games are almost always **"likely to be accessed by children"**; treat a game as in-scope unless robust, evidenced age assurance shows otherwise [10][11]. This sits on top of the UK **13** consent age (DPA s.9) [3]. See `game-hosting-foundations` for the full games overlay. *(Legal obligation.)*
- **Defaults for players.** Child players should get **high-privacy defaults**: geolocation off, profiling/behavioural-ad features off, friend/visibility discovery off, and voice/chat exposure minimised — with age-appropriate, non-nudging routes to change them [11]. *(Legal obligation.)*
- **Engagement mechanics vs best interests.** Retention loops, streaks, autoplay, loot-box nudges and reward-based prompts to share more data are exactly the **nudge techniques** Standard 13 restricts for children; design against them and document the child's best interests [11]. *(Legal obligation / best practice.)*
- **Overlap with OSA and DSA.** A game with chat/UGC also faces **Online Safety Act** children's-safety duties (Ofcom) and, in the EU, DSA Art. 28 minors' protections — reconcile age assurance and children's-risk assessments across all three (see `game-hosting-foundations`) [8][15]. *(Legal obligation.)*
- **Parental controls.** Where parental controls exist, give the child **age-appropriate information** that they are in place (Standard 11) — do not use them as covert monitoring [11]. *(Legal obligation, as interpreted.)*

# AI Considerations

- **Profiling and recommender systems.** AI-driven **personalisation/recommendation** that profiles children is restricted: Standard 12 requires profiling to be **off by default** for children unless a compelling, best-interests-justified reason exists; content-recommender models trained on children's behaviour must respect this [11]. *(Legal obligation, as interpreted.)*
- **Automated decisions about children.** Where AI makes **solely automated** decisions with significant effect about children, the UK GDPR Art. 22 regime (as recast by DUAA Arts. 22A–22D — see `duaa-2025-detail`) applies with heightened caution; the Code's best-interests lens and the new Art. 25 children's duty reinforce the need for human oversight and contestability for minors [5][11]. *(Legal obligation.)*
- **Age-estimation AI.** AI-based **age estimation** (e.g. facial age estimation) is itself high-risk processing: it may involve **biometric/special-category** data, needs a DPIA and a lawful basis, and must be minimised and accurate across ages and demographics to avoid discriminatory mis-gating [4][11]. *(Legal obligation.)*
- **Nudge/engagement AI.** Optimisation models that maximise engagement can amount to prohibited **nudge techniques** when they push children to over-share or weaken privacy; align model objectives with the child's best interests [11]. *(Regulatory interpretation.)*
- **AI Act overlap (EU-facing services).** UK-only services are outside the EU AI Act, but multi-territory services should note its Art. 5 protections against exploiting children's vulnerabilities and Art. 50 transparency (see `ai-act-foundations`, `game-hosting-foundations`). *(Editorial note.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**. The 15 standards are the operational core; each is stated with its expectation.

**The 15 standards of the Children's Code** [11]:

1. **Best interests of the child** — make it a **primary consideration** in design and development. *(OBLIGATION as interpreted.)*
2. **Data protection impact assessments** — complete a **DPIA** covering differing ages/capacities and building in Code conformance. *(OBLIGATION — Art. 35.)*
3. **Age-appropriate application** — take a **risk-based** approach to recognising users' ages; establish age with proportionate certainty **or** apply the standards to all users. *(OBLIGATION.)*
4. **Transparency** — give **clear, child-friendly** privacy information at the point of use, in language a child can understand. *(OBLIGATION — Arts. 12–13.)*
5. **Detrimental use of data** — do **not** use children's data in ways shown to be **detrimental** to their wellbeing or that go against industry codes/regulatory provisions. *(OBLIGATION.)*
6. **Policies and community standards** — **uphold your own published** terms, policies and community standards for children's data. *(OBLIGATION.)*
7. **Default settings** — settings must be **"high privacy" by default** unless a compelling best-interests reason justifies otherwise. *(OBLIGATION.)*
8. **Data minimisation** — collect and retain only the **minimum** needed for the element the child is actively engaged in; offer **separate** choices. *(OBLIGATION — Art. 5(1)(c).)*
9. **Data sharing** — do **not** disclose children's data without a **compelling reason** in the child's best interests. *(OBLIGATION.)*
10. **Geolocation** — **off by default**; show an obvious sign when tracking is active; visibility-to-others defaults back to off each session. *(OBLIGATION.)*
11. **Parental controls** — if provided, give the child **age-appropriate information** about them. *(OBLIGATION as interpreted.)*
12. **Profiling** — **off by default** unless a compelling best-interests reason justifies otherwise. *(OBLIGATION.)*
13. **Nudge techniques** — do **not** nudge children to provide unnecessary data or weaken privacy protections. *(OBLIGATION.)*
14. **Connected toys and devices** — include tools to enable **conformance** with the Code. *(OBLIGATION.)*
15. **Online tools** — provide **prominent, accessible tools** for children to exercise their data-protection rights and report concerns. *(OBLIGATION.)*

**Cross-cutting actions:**

1. **Run a "likely to be accessed by children" assessment** for each service and record the conclusion and evidence. *(OBLIGATION.)* [10][11]
2. **Satisfy the DUAA Art. 25 children's duty** — document how "children's higher protection matters" are considered in DPbDD; conforming to the Code is the ICO's expected route. *(OBLIGATION.)* [5][12][13]
3. **Coordinate with Online Safety Act obligations** where the service has UGC/chat — align age assurance and children's-risk assessments, but treat the regimes separately. *(OBLIGATION.)* [15][16]
4. **Keep a children's-compliance watch-list** for the revised Code, updated ICO guidance and DUAA commencement. *(EDITORIAL RECOMMENDATION.)* [12]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Wrongly concluding a service is **not** "likely to be accessed by children" | Medium | High | Scope test [10][11] | Evidenced access assessment; default to in-scope for consumer services | Low |
| R2 | Defaults not high-privacy (geolocation/profiling on) for children | Medium | High | Standards 7, 10, 12 [11] | High-privacy-by-default build; conform-or-justify records | Low |
| R3 | Over-collecting identity data through age assurance | Medium | High | Standards 3, 8 [11] | Proportionate, risk-based assurance; isolate/minimise identifiers | Low |
| R4 | No DPIA for a children's service | Medium | High | Art. 35; Standard 2 [4][11] | DPIA-first gate; age/capacity coverage | Low |
| R5 | Nudge/engagement design pushing children to over-share | Medium | Medium | Standard 13 [11] | Design review; remove privacy-eroding nudges | Low |
| R6 | Missing the new DUAA Art. 25 children's duty | Medium | Medium | DUAA s.81 [5][17] | Map duty to Code conformance; document | Low |
| R7 | Treating OSA compliance as discharging the Code (or vice versa) | Medium | High | Distinct regimes [15][16] | Dual-regime mapping; separate assessments | Low |
| R8 | Applying only the 13 consent age and ignoring 13–17 design duties | Medium | Medium | Under-18 scope [3][10][11] | Age-band design across 0–17 | Low |
| R9 | Enforcement exposure (audit/fine) for non-conformity | Low | High | ICO powers [10][14] | Conform to 15 standards; evidence trail | Low |

# Implementation Roadmap

- **Phase 0 — Scope & DPIA:** Run the "likely to be accessed by children" assessment per service; open a DPIA covering age bands and Code conformance. *Effort:* Medium.
- **Phase 1 — Age assurance:** Choose and implement a proportionate, risk-based age-assurance approach (or apply protections to all users); isolate and minimise assurance data. *Effort:* Medium–High.
- **Phase 2 — Defaults & minimisation:** Ship high-privacy defaults (geolocation/profiling/discovery off), separated choices, minimised collection and short retention. *Effort:* Medium.
- **Phase 3 — Transparency & tools:** Child-friendly notices; prominent rights/reporting tools; parental-control information; remove nudge techniques. *Effort:* Medium.
- **Phase 4 — DUAA & OSA alignment:** Document the Art. 25(1A)/(1B) children's duty; reconcile with Online Safety Act children's-risk assessments and age assurance where UGC/chat exists. *Effort:* Medium.
- **Phase 5 — Assurance & watch:** Audit against the 15 standards; maintain a watch-list for the revised Code and DUAA/ICO updates. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Children's services treated like adult services; no access assessment. | Defaults not child-aware; no DPIA. |
| 2 | Managed | Access assessment done; basic age gate and some high-privacy defaults. | Partial Code mapping; DPIA started. |
| 3 | Defined | All 15 standards mapped and implemented; risk-based age assurance; DPIA complete. | Documented conform-or-justify records; child-friendly notices. |
| 4 | Quantitatively Managed | Metrics on assurance accuracy, default adherence, rights-tool usage; periodic review. | KPIs; internal audits; DUAA duty evidenced. |
| 5 | Optimising | Best-interests design embedded; OSA/Code/DSA reconciled; proactive tracking of the revised Code. | Adaptive age-band controls; tested cross-regime alignment. |

# Audit Questions

1. Have you assessed each service as **"likely to be accessed by children"**, and recorded the evidence? *([10][11].)*
2. Is there a completed **DPIA** covering differing ages/capacities and Code conformance? *(Art. 35; Standard 2 [4][11].)*
3. What **age-assurance** approach is used, is it proportionate to the data risks, and does it minimise identity data? *(Standard 3 [11].)*
4. Are **defaults high-privacy** — geolocation, profiling and social discovery **off by default** for children? *(Standards 7, 10, 12 [11].)*
5. Is data collection **minimised** with **separate** choices for optional elements, and retention kept short? *(Standard 8 [11].)*
6. Are privacy notices **child-friendly** and are prominent **rights/reporting tools** provided? *(Standards 4, 15 [11].)*
7. Have you removed **nudge techniques** that push children to over-share or weaken privacy? *(Standard 13 [11].)*
8. How do you evidence the DUAA **Art. 25(1A)/(1B) "children's higher protection matters"** duty? *(DUAA s.81 [5][17].)*
9. Where the service has UGC/chat, how are the **Children's Code** and the **Online Safety Act** children's duties handled **separately** but coherently? *([15][16].)*
10. Do you design across the full **0–17** range, not just gate at the 13 consent age? *([3][10][11].)*

# Implementation Checklist

- [ ] "Likely to be accessed by children" assessment completed and evidenced per service.
- [ ] DPIA completed, covering age bands/capacities and building in Code conformance.
- [ ] Risk-based age assurance implemented (or Code applied to all users); assurance data isolated and minimised.
- [ ] High-privacy defaults shipped: geolocation off, profiling off, social discovery/visibility off, behavioural ads off.
- [ ] Data minimised; separate choices for optional elements; short retention with deletion/aggregation.
- [ ] Child-friendly transparency at point of use; prominent rights and reporting tools.
- [ ] Parental-control information provided in age-appropriate form (where controls exist).
- [ ] Nudge techniques and privacy-eroding dark patterns removed from child-facing flows.
- [ ] Connected toys/devices include conformance tooling and secure set-up.
- [ ] DUAA Art. 25(1A)/(1B) "children's higher protection matters" duty documented against Code conformance.
- [ ] Online Safety Act children's-risk assessment and age assurance reconciled (where UGC/chat present), kept distinct from the Code.
- [ ] Children's-compliance watch-list maintained (revised Code, ICO guidance, DUAA commencement).

# References

*All links verified live on 2026-07-11 (`sources_verified`) via HTTP 2xx/3xx check.*

## Primary Sources

- [1] **Data Protection Act 2018, s.123** (age-appropriate design code — statutory basis of the Children's Code). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/123
- [2] **Data Protection Act 2018, s.125** (procedure for approval and issue of the code; effect of the code). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/125
- [3] **Data Protection Act 2018, s.9** (child's consent for information-society services; UK age 13). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/9
- [4] **Regulation (EU) 2016/679 (UK GDPR / EU GDPR), consolidated text** — Arts. 8, 25, 35; Recitals 38, 58. EUR-Lex, CELEX 02016R0679-20160504. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [5] **Data (Use and Access) Act 2025, s.81** ("Data protection by design: children's higher protection matters" — inserts UK GDPR Art. 25(1A)/(1B)). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/section/81
- [6] **Data (Use and Access) Act 2025 (c.18)**, contents. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/contents
- [7] **The Data (Use and Access) Act 2025 (Commencement No. 6 and Transitional and Saving Provisions) Regulations 2026 (SI 2026/82)** (commencement of Part 5 data-protection provisions). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2026/82/contents/made
- [8] **Online Safety Act 2023 (c.50)**, contents. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2023/50/contents
- [9] **European Union (Withdrawal) Act 2018, s.3** (retention of the UK GDPR in domestic law). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/16/section/3

## Regulatory Guidance

- [10] **Children's code guidance and resources** (introduction, scope, "likely to be accessed by children"). Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/childrens-information/childrens-code-guidance-and-resources/
- [11] **Age appropriate design: a code of practice for online services** (the 15 standards). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/childrens-information/childrens-code-guidance-and-resources/age-appropriate-design-a-code-of-practice-for-online-services/
- [12] **The Data (Use and Access) Act 2025 — what does it mean for organisations?** (children's higher protection matters; guidance updates). ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/the-data-use-and-access-act-2025-what-does-it-mean-for-organisations/
- [13] **The Data (Use and Access) Act 2025 (DUAA) — summary of the changes: data protection.** ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/the-data-use-and-access-act-2025-duaa-summary-of-the-changes/data-protection/
- [14] **Child online safety: data protection and privacy** (overview of the Children's Code, in-force position and children's-data expectations). GOV.UK. https://www.gov.uk/guidance/child-online-safety-data-protection-and-privacy
- [15] **New rules for a safer generation of children online** (Protection of Children Codes in force 25 July 2025; children's access assessments; age assurance). Ofcom. https://www.ofcom.org.uk/online-safety/protecting-children/new-rules-for-a-safer-generation-of-children-online
- [16] **Online safety** (regulator overview of Online Safety Act duties). Ofcom. https://www.ofcom.org.uk/online-safety/
- [17] **Data (Use and Access) Act 2025 factsheet: UK GDPR and DPA** (children's higher protection matters; Art. 25 amendment). GOV.UK / DSIT. https://www.gov.uk/government/publications/data-use-and-access-act-2025-factsheets/data-use-and-access-act-factsheet-uk-gdpr-and-dpa

## Standards

**Not Applicable** — the Children's Code is a UK statutory code and regulator guidance; no ISO/IEC/NIST/OWASP standard is specific to it. Emerging age-assurance standards (e.g. ISO/IEC 27566, IEEE 2089) may inform implementation but are not authoritative for the Code and are not relied on here; general privacy standards (ISO/IEC 27701) apply to implementation as under the UK GDPR (see `privacy-engineering-foundations`).

## Academic Sources

**Not Applicable** — this sub-topic relies on primary legislation and regulatory guidance. Peer-reviewed analysis of the Code's effects and of age-assurance efficacy is emerging and will be cited as it matures.

# Further Reading

*Non-authoritative; provided for orientation only.*

- ICO — Children's information hub (parent landing for children's-data resources). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/childrens-information/
- GOV.UK — Explanatory memorandum to the Age Appropriate Design Code 2020. https://www.gov.uk/government/publications/explanatory-memorandum-to-the-age-appropriate-design-code-2020-2020/explanatory-memorandum-to-the-age-appropriate-design-code-2020-2020

# Related Documents

- `uk-gdpr-foundations` — UK GDPR foundations; the **13** consent age (DPA 2018 s.9) (**prerequisite**).
- `duaa-2025-detail` — the DUAA 2025 in depth, incl. the children's duty and commencement dates (**sibling**).
- `game-hosting-foundations` — games overlay: Children's Code, loot boxes, PEGI, DSA/OSA (**sibling**).
- `gdpr-foundations` — EU GDPR baseline: Art. 8, Recital 38 (**prerequisite reading**).
- `eprivacy-foundations` — Art. 5(3)/PECR consent for SDKs used in children's services.
- `privacy-engineering-foundations` — DPbDD, minimisation and pseudonymisation for children's data.
- `dpia-methodology` — how to run the DPIA that Standard 2 requires.
- `uk-transfers` — UK transfer mechanisms for children's data (IDTA/Addendum).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against legislation.gov.uk (DPA 2018 ss.123/125/9, UK GDPR Arts. 8/25/35, DUAA 2025 s.81, SI 2026/82, OSA 2023, EUWA 2018 s.3), ICO Children's-code and DUAA guidance, GOV.UK/DSIT and Ofcom. **Live-verified: the 15 AADC standards; Code in force 2 Sep 2020 and enforceable from 2 Sep 2021; DUAA s.81 inserts UK GDPR Art. 25(1A)/(1B) "children's higher protection matters"; Ofcom Protection of Children Codes in force 25 Jul 2025.** | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 3 human gate; frozen in release 0.14.0. | Human reviewer |

</content>
</invoke>
