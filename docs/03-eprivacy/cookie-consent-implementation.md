---
id: cookie-consent-implementation
title: "Cookie Consent: Implementation & Consent Management"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: ePrivacy
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [eprivacy-foundations, gdpr-foundations, uk-gdpr-foundations, privacy-engineering-foundations, dsa-foundations, consumer-protection-foundations]
tags: [eprivacy, cookies, consent, cmp, tcf, iab-europe, consent-or-pay, dark-patterns, planet49, pecr]
legal_basis: Directive 2002/58/EC Art. 5(3) (as amended by 2009/136/EC); Regulation (EU) 2016/679 Arts. 4(11), 7; PECR 2003 reg. 6
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | cookie-consent-implementation |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.11.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a deep-dive that **details** the parent reference `eprivacy-foundations` (Art. 5(3) / cookie rule) — read that first. The ePrivacy landscape is in flux: the **Digital Omnibus** (published November 2025) proposes moving the cookie rule into the GDPR (new Arts. 88a/88b) — a **proposal, not law**. Confirm the live position before relying on any future-state provision.

# Executive Summary

This document is the practical implementation companion to `eprivacy-foundations`. It translates the **Article 5(3) ePrivacy cookie rule** [1] and the GDPR conditions of consent [2] into concrete design requirements for **cookie banners, consent-management platforms (CMPs), tag governance and consent records**.

The controlling standard is settled. Storing or accessing information on a user's terminal equipment (cookies, and — per **EDPB Guidelines 2/2023** — pixels, URL/link decoration tracking, local storage, IP-only tracking and device fingerprinting) requires **consent** unless *strictly necessary* for a service the user requested [1][7]. That consent must meet the GDPR's **Art. 4(11)/Art. 7** conditions — freely given, specific, informed, unambiguous, by clear affirmative action — as confirmed for cookies by **Planet49 (C-673/17)**: a **pre-ticked box is never valid consent**, whether or not the data is personal [2][3]. Regulators (EDPB, ICO) require **reject to be as easy as accept**, **granular** per-purpose control, **no consent before the choice is made**, and consent that can be **withdrawn as easily as given** [6][8][10].

Three live, contested frontiers dominate 2024–2026 practice. First, **"consent or pay" / "pay-or-okay"**: in **EDPB Opinion 08/2024** the Board held that large online platforms generally **cannot** obtain valid consent by offering only a binary "consent to tracking or pay" choice, and should offer a genuine, usually free, equivalent alternative [6]. Second, the **IAB Europe Transparency & Consent Framework (TCF)**: in **C-604/22** the CJEU ruled that a **TC String is personal data** and that IAB Europe is a (limited) **joint controller** for it — a finding the Brussels Market Court largely upheld on 14 May 2025 [4][11]. Third, **dark-pattern avoidance**, where data-protection, DSA and consumer law converge [9]. The document closes with an **implementation checklist** and a **CMP requirements specification**.

# Key Takeaways

- **Consent before set:** no non-essential cookie/SDK/tracker may fire before the user gives valid consent; only *strictly necessary* technologies are exempt from Art. 5(3) [1][10]. *(Legal obligation.)*
- **Planet49 standard:** a pre-ticked checkbox, "continue browsing" or inactivity is **not** consent; consent must be active and unambiguous, personal data or not [3]. *(Case law.)*
- **GDPR conditions govern the quality of consent:** freely given, specific, informed, unambiguous, and as easy to withdraw as to give (Arts. 4(11), 7) [2]. *(Legal obligation.)*
- **Reject-as-easy-as-accept + granularity:** a "reject all" must be as prominent and low-friction as "accept all", with independent per-purpose toggles and no pre-selected non-essential options [6][8][10]. *(Regulatory interpretation grounded in obligation.)*
- **Art. 5(3) is technology-neutral:** EDPB Guidelines 2/2023 confirm it captures pixels, link decoration/URL tracking, local storage, unique identifiers, IP-only tracking and fingerprinting — not just HTTP cookies [7]. *(Regulatory interpretation.)*
- **"Consent or pay":** per EDPB Opinion 08/2024, large online platforms generally cannot rely on a binary consent-or-pay wall; a real (usually free) equivalent alternative is expected [6]. *(Regulatory interpretation — contested; under legal challenge.)*
- **TCF / TC String:** the CJEU held in C-604/22 that a TC String is **personal data** and IAB Europe a **joint controller** for creating/encoding it (not for downstream ad processing); upheld by the Brussels Market Court on 14 May 2025 [4][11]. *(Case law.)*
- **"Strictly necessary" is narrow:** it means necessary to deliver the service the *user* requested (e.g. session, load-balancing, security, consent-state) — **not** analytics or advertising [1][7][10]. *(Legal obligation / regulatory interpretation.)*
- **Dark patterns are unlawful across regimes:** deceptive consent UX breaches GDPR fairness (EDPB Guidelines 03/2022) and overlaps with the DSA and consumer law [9]; empirical study shows "reject all" is rarely as easy as "accept all" and that design nudges consent [13]. *(Regulatory interpretation / academic.)*
- **Reform watch:** the Digital Omnibus (Nov 2025) proposes moving cookie rules into the GDPR with machine-readable/browser consent signals — a **proposal only**; the Directive and PECR remain in force [12]. *(Regulatory — proposal.)*

# Purpose

This document supports engineering, product, marketing and privacy teams that must **design, build, configure and audit** cookie-consent experiences and consent-management platforms. It answers: *what makes cookie consent valid; how must a banner and CMP be designed; what is "strictly necessary"; how do we record and honour withdrawal; how do the TCF and "consent or pay" affect us; and how do we avoid dark patterns?* It provides an implementation checklist and a CMP requirements specification that can be handed to a vendor or build team.

# Scope

**In scope:** Valid consent for cookies and equivalent device access (Art. 5(3)); CMP design and configuration requirements (granularity, symmetry, no pre-ticking, no cookie walls); the "consent or pay" debate and EDPB Opinion 08/2024; the IAB Europe TCF and C-604/22; classification of "strictly necessary"; recording, storing and withdrawing consent; analytics and tag governance; dark-pattern avoidance and its cross-regime overlap (DSA/consumer law); EU and UK (PECR) positions at implementation depth.

**Out of scope:** The foundational ePrivacy/GDPR relationship and Art. 5(3) doctrine → `eprivacy-foundations` (parent). The meaning and general conditions of consent → `gdpr-foundations`. UK PECR marketing, enforcement and DUAA cookie changes in depth → `pecr-detail` (backlog). Direct-marketing consent (Art. 13 / PECR regs 22–23) → `eprivacy-foundations` and `pecr-detail`. The Digital Omnibus package as a whole → `digital-omnibus` (backlog). DSA/consumer dark-pattern law in depth → `dsa-foundations`, `consumer-protection-foundations`.

**Assumptions:** The reader has read `eprivacy-foundations` and `gdpr-foundations`. "Consent" carries its `GLOSSARY.md` meaning. The organisation is a *controller* deploying a website/app that sets cookies or equivalent trackers.

# Definitions

*Shared terms (consent, controller, personal data, dark pattern) are in `GLOSSARY.md`. Only terms specific to cookie-consent implementation are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Consent-management platform (CMP) | A tool that presents consent choices to users, records the decision, and signals it to tags/vendors so that non-essential technologies fire only with consent. | [7][10] |
| Strictly necessary | An Art. 5(3) exemption: storage/access essential to provide the information-society service *explicitly requested by the user* (e.g. session state, security, load-balancing, consent-preference storage). Analytics and advertising are **not** strictly necessary. | [1][10] |
| Cookie wall / "take-it-or-leave-it" | Blocking access to a site/service unless the user consents to non-essential cookies, leaving no genuine choice; treated as invalidating "freely given" consent. | [6][8] |
| Consent or pay ("pay-or-okay") | A model offering users a binary choice: consent to tracking-based advertising, or pay a fee for a tracking-free version. | [6] |
| Transparency & Consent Framework (TCF) | IAB Europe's industry standard for capturing and transmitting users' consent/objection signals across the online-advertising (RTB) supply chain. | [4][11] |
| TC String (Transparency & Consent String) | The encoded character string produced under the TCF recording a user's consent/objection preferences; held to be **personal data** in C-604/22. | [4] |
| Link decoration / URL tracking | Appending identifiers to URLs to track users across pages/domains; within Art. 5(3) per EDPB Guidelines 2/2023. | [7] |
| Global Privacy Control (GPC) / browser signal | A machine-readable, automated signal by which a user expresses a consent/objection preference at browser or device level. | [12] |

# Background

The 2009 amendment (Directive 2009/136/EC) reshaped Art. 5(3) from a notice-and-opt-out rule into a **consent** rule for storing or accessing information on terminal equipment [1]. When the GDPR replaced Directive 95/46/EC in 2018, the ePrivacy consent standard was read as **GDPR-standard consent** (Art. 4(11)) [1][2]. The **Planet49** judgment (2019) then removed any doubt that a **pre-ticked box** is invalid and that this holds regardless of whether the stored/accessed data is personal [3].

Two forces have shaped the implementation landscape since. First, the ad-tech industry converged on the **IAB Europe TCF** to manage consent signalling for real-time-bidding advertising; the Belgian DPA's 2022 decision, the CJEU's 2024 ruling in **C-604/22** and the Brussels Market Court's **14 May 2025** judgment together clarified that the **TC String is personal data** and that the framework operator bears controller responsibility for it [4][11]. Second, platforms responded to tighter enforcement by deploying **"consent or pay"** walls, prompting the **EDPB's Opinion 08/2024** and a wave of national scrutiny and litigation [6].

Meanwhile the regulatory reading of *what counts as a tracker* broadened: **EDPB Guidelines 2/2023** (adopted October 2024) confirmed Art. 5(3) reaches well beyond cookies to pixels, URL/link tracking, local processing, unique identifiers and IP-only tracking [7]. Enforcement has been substantial — national authorities (notably France's CNIL) issued nine-figure cookie-related fines through 2025 — reinforcing that consent UX is a front-line compliance risk.

# Legal Framework

The obligation is **statutory**: Art. 5(3) of Directive 2002/58/EC (as amended) prohibits storing or gaining access to information on a user's terminal equipment **unless** the user "has given his or her consent, having been provided with clear and comprehensive information", subject to a narrow exemption where storage/access is "strictly necessary" for a service the user "explicitly requested" [1]. Because ePrivacy is a **Directive**, the operative duty arises under national transposition — in the UK, **PECR 2003 reg. 6** [5].

The **meaning and conditions of consent** are supplied by the GDPR: Art. 4(11) (definition) and Art. 7 (conditions — demonstrability, no detriment to withdrawal, withdrawal as easy as giving, freely given assessed with regard to conditionality) [2]. Recital 32 GDPR states expressly that silence, pre-ticked boxes or inactivity do **not** constitute consent [2].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| ePrivacy Art. 5(3) | Consent (with prior clear information) required before storing/accessing information on terminal equipment; exemption only where strictly necessary for a service the user explicitly requested. | [1] |
| GDPR Art. 4(11) | Consent means a freely given, specific, informed and unambiguous indication by a statement or clear affirmative action. | [2] |
| GDPR Art. 7(1) | The controller must be able to **demonstrate** that consent was given (consent records). | [2] |
| GDPR Art. 7(3) | The right to **withdraw** consent at any time; withdrawal must be **as easy as** giving consent. | [2] |
| GDPR Art. 7(4) | "Freely given" — account is taken of whether service provision is conditioned on consent not necessary for that service (conditionality/bundling). | [2] |
| PECR 2003 reg. 6 | UK transposition of Art. 5(3): consent + information before storing/accessing information on terminal equipment; strictly-necessary exemption. | [5] |

## Relevant Recitals

*Recitals aid interpretation but are not binding operative provisions.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| ePrivacy Recital 25 | Cookies can be legitimate (e.g. analysing service effectiveness) but users must receive clear information and the opportunity to refuse. | [1] |
| ePrivacy Recital 66 (2009/136/EC) | Reinforces that storing/accessing information requires consent, the user having been given clear and comprehensive information. | [1] |
| GDPR Recital 32 | Consent by clear affirmative act; pre-ticked boxes, silence or inactivity do not amount to consent; granularity for distinct purposes. | [2] |
| GDPR Recital 43 | Consent is not freely given where there is a clear imbalance, or where separate consents cannot be given for separate processing operations (bundling). | [2] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Planet49 | CJEU (Grand Chamber), C-673/17, 1 Oct 2019, ECLI:EU:C:2019:801 | A **pre-ticked checkbox** is not valid consent for storing/accessing cookies; the standard applies whether or not the information is personal data; users must receive information including cookie duration and third-party access. | Sets the consent standard for cookies and CMP design [3]. |
| IAB Europe | CJEU (Fourth Chamber), C-604/22, 7 Mar 2024, ECLI:EU:C:2024:214 | A **TC String is personal data** where it can be combined (e.g. with an IP address) to identify a user; IAB Europe is a **joint controller** for recording consent preferences in the TC String (but not for members' subsequent ad processing). | Governs TCF/CMP deployments and RTB consent signalling [4]. |
| IAB Europe (national follow-on) | Brussels Market Court (Cour d'appel de Bruxelles), 14 May 2025, case 2022/AR/292 | Largely **upheld** the Belgian DPA: TC Strings are personal data; IAB Europe is joint controller for creating/encoding TC Strings only; €250,000 fine and GDPR infringements confirmed. | Applies C-604/22 domestically; confirms TCF compliance obligations [11]. |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **EDPB Guidelines 2/2023 (technical scope of Art. 5(3)):** Art. 5(3) is technology-neutral and captures pixels, tracking links/URL decoration, local storage, cached identifiers, IP-only tracking and device fingerprinting — three cumulative elements ("information", "terminal equipment", "gaining access/storage") determine applicability [7]. *(Regulatory interpretation.)*
- **EDPB Guidelines 05/2020 (consent):** consent must be freely given, specific, informed and unambiguous; **cookie walls** that condition access on consent are, as a rule, not "freely given"; consent bundled across purposes is invalid; the controller must keep records and enable easy withdrawal [8]. *(Regulatory interpretation.)*
- **EDPB Opinion 08/2024 (consent or pay):** for **large online platforms**, a binary "consent to behavioural advertising or pay" model will in most cases **not** yield valid consent; controllers should offer an **equivalent alternative** that does not entail a fee (e.g. advertising with less or no personal-data processing). Personal data is not a tradeable commodity; fees must not make users feel *compelled* to consent. Free choice is assessed against **conditionality, detriment, imbalance of power and granularity** [6]. *(Regulatory interpretation — contested; see Concerns.)*
- **EDPB Guidelines 03/2022 (deceptive design patterns):** consent interfaces that nudge, obstruct, or mislead ("dark patterns") breach the GDPR **fairness** principle (Art. 5(1)(a)); examples include asymmetric accept/reject buttons, hidden reject options and repeated re-prompting [9]. *(Regulatory interpretation.)*
- **ICO (UK):** cookie consent requires **GDPR-standard consent**; "strictly necessary" is read **narrowly** and does not cover analytics or advertising; **"reject all" must be as easy as "accept all"**; the ICO enforces PECR alongside the UK GDPR [10]. *(Regulatory interpretation.)*
- **Reform status:** the **Digital Omnibus** proposal (Nov 2025) would move cookie rules into the GDPR (new Arts. 88a/88b), add machine-readable/browser-level consent signalling, a single-click refusal and a bar on re-prompting for the same purpose within six months — but it is a **proposal**; the Directive and PECR remain in force [12]. *(Regulatory interpretation — proposal only.)*

# Technical Considerations

- **Prior blocking (consent-before-set):** the CMP must **block** non-essential tags, scripts, SDKs, pixels and storage writes until a valid consent signal exists; "block-then-unblock on consent" — never "load-then-delete" [1][10]. *(Legal obligation.)*
- **Server- and client-side scope:** Art. 5(3) applies to *any* read/write of terminal-equipment information, including **server-side tagging**, SDK reads, `localStorage`/`IndexedDB`, cache-based identifiers and fingerprinting; gating must cover these, not only document.cookie [7]. *(Legal obligation.)*
- **Granular architecture:** implement independent purpose categories (e.g. strictly necessary [always on, no toggle], functional/preferences, analytics/measurement, advertising/targeting) with per-category (and where feasible per-vendor) toggles, all defaulting **off** for non-essential [2][8]. *(Best practice grounded in obligation.)*
- **Symmetric controls:** first-layer **"Accept all"** and **"Reject all"** buttons of equal prominence, styling and click-cost; do not hide "reject" behind a second layer or greyed styling [6][10]. *(Regulatory interpretation.)*
- **Consent record schema:** capture and retain, per decision — a consent ID, timestamp, the specific purposes/vendors consented to or refused, the consent-string/version, the UI/text version presented, and the collection mechanism — to satisfy Art. 7(1) demonstrability [2]. *(Legal obligation.)*
- **Withdrawal parity:** provide a persistent, easily reachable control (e.g. a footer link or floating icon) to re-open preferences and **withdraw** as easily as consent was given; on withdrawal, stop the processing and delete/expire the affected cookies [2]. *(Legal obligation.)*
- **TCF specifics:** if deploying the IAB TCF, treat the **TC String as personal data** and IAB Europe as a **joint controller** for its creation — meaning joint-controller arrangements, transparency and a valid legal basis for the string itself, distinct from downstream processing [4][11]. *(Legal obligation.)*
- **Browser signals (forward-looking):** design CMPs to be capable of reading/honouring automated signals (e.g. GPC), anticipating the Digital Omnibus Art. 88b direction — but do not treat unadopted rules as binding [12]. *(Editorial recommendation.)*

# Hosting Considerations

- **CDN and edge features:** CDNs and edge platforms may set device storage (e.g. load-balancing, bot-management, A/B or analytics cookies). Classify each: load-balancing/security are typically strictly necessary; analytics/experimentation are not and must be gated [1][10]. *(Legal obligation.)*
- **Server-side / first-party tagging:** relocating tags to a first-party server endpoint does **not** exempt them from Art. 5(3) where they still read/write terminal-equipment information or set identifiers; gate them on consent [7]. *(Legal obligation.)*
- **Consent-record storage:** consent logs are themselves personal data (they link an identifier to choices) and must be stored securely with a defined retention period and access controls; host them so they are producible on regulator or data-subject request [2]. *(Legal obligation / best practice.)*
- **Controller responsibility for third-party tags:** the site operator remains responsible for third-party tags it deploys; use tag-manager governance, allow-lists and contractual controls over vendors [4][10]. *(Editorial recommendation.)*

# Game Hosting Considerations

- **Analytics/ads/attribution SDKs:** mobile and console games routinely embed analytics, advertising and attribution SDKs (e.g. IDFA/GAID reads, install attribution) that store/read device information and fall within Art. 5(3); they must not initialise before consent [1][7]. *(Legal obligation.)*
- **Consent in constrained UIs:** in-game and TV/console interfaces still require a genuine, granular, symmetric consent flow; a "press A to continue" that bundles tracking consent is invalid on Planet49/EDPB reasoning [3][8]. *(Legal obligation / regulatory interpretation.)*
- **Children:** games likely accessed by children face heightened scrutiny (see `gdpr-foundations`, `uk-gdpr-foundations`, Children's Code); default tracking off and avoid nudging minors toward consent [9]. *(Legal obligation / best practice.)*
- **Cross-ref:** in-game/telemetry SDK gating is also covered at foundational level in `eprivacy-foundations` (Game Hosting Considerations). *(Cross-reference.)*

# AI Considerations

- **Consent is the collection gate for AI personalisation:** where behavioural data captured via cookies/SDKs feeds recommendation, ad-targeting or other ML models, a valid **Art. 5(3) consent** is required for the *collection layer*, in addition to a GDPR lawful basis for downstream training/inference [1][2]. Consent is frequently the **binding constraint**. *(Legal obligation.)*
- **"Consent or pay" and profiling:** EDPB Opinion 08/2024 targets exactly the behavioural-advertising/profiling use case that powers ad-tech ML; a binary pay-wall generally cannot validly consent users into large-scale profiling [6]. *(Regulatory interpretation.)*
- **RTB and TC Strings as AI inputs:** TC Strings and bid-stream data flowing into ad-tech models are personal data; C-604/22 confirms controller responsibility attaches to the consent-signal layer [4]. *(Case law.)*
- **AI-generated consent UX:** using AI to optimise banner design toward higher acceptance risks producing **dark patterns** breaching the fairness principle; optimise for comprehension and genuine choice, not consent rate [9]. *(Editorial recommendation.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Inventory every read/write of terminal-equipment information** — cookies, local/session storage, pixels, SDKs, fingerprinting, tracking URLs — and classify each as *strictly necessary* or *consent-required*. Document the necessity rationale for each "strictly necessary" call. *(OBLIGATION.)* [1][7]
2. **Enforce consent-before-set** — block all non-essential technologies until a valid consent signal exists; verify with network inspection that nothing non-essential fires on first load. *(OBLIGATION.)* [1][10]
3. **Design a symmetric, granular first layer** — equal-prominence "Accept all" / "Reject all"; per-purpose toggles defaulting off; no pre-ticked non-essential boxes; clear, plain-language purpose descriptions. *(OBLIGATION + BEST PRACTICE.)* [2][8][10]
4. **Do not deploy cookie walls** (and, for large platforms, avoid binary consent-or-pay without a genuine equivalent alternative). *(OBLIGATION per EDPB.)* [6][8]
5. **Record consent to Art. 7(1) standard** and provide **withdrawal parity** via a persistent control. *(OBLIGATION.)* [2]
6. **Govern the TCF deployment** — if using IAB TCF, put joint-controller terms in place, treat the TC String as personal data, and confirm CMP certification/version. *(OBLIGATION.)* [4][11]
7. **Audit for dark patterns** — remove asymmetric buttons, confirmshaming, obstruction and nudging; align with EDPB Guidelines 03/2022 and DSA/consumer expectations. *(BEST PRACTICE.)* [9]
8. **Interpret "strictly necessary" narrowly** — never classify analytics or advertising as strictly necessary. *(OBLIGATION per ICO.)* [10]
9. **Track reform** — monitor the Digital Omnibus (Arts. 88a/88b, browser signals) without pre-implementing unadopted rules. *(EDITORIAL RECOMMENDATION.)* [12]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Non-essential trackers firing before consent | High | High | Art. 5(3); Planet49 [1][3] | Consent-before-set; tag gating; network-inspection audit | Low |
| R2 | Asymmetric "accept" vs "reject" / dark patterns | High | High | EDPB [6][9]; ICO [10] | Symmetric first layer; dark-pattern audit | Low |
| R3 | Pre-ticked non-essential toggles / bundled consent | Medium | High | Planet49 [3]; Recital 32/43 [2] | Off-by-default granular toggles | Low |
| R4 | Treating analytics/ads as "strictly necessary" | High | Medium | Art. 5(3); ICO [10]; EDPB 2/2023 [7] | Correct classification; documented rationale | Low |
| R5 | Cookie wall / non-compliant consent-or-pay | Medium | High | EDPB Opinion 08/2024 [6] | Remove wall; provide equivalent (free) alternative | Medium |
| R6 | TCF deployed without joint-controller/legal-basis controls | Medium | High | C-604/22 [4]; Market Court [11] | JC arrangement; certified CMP; TC-String basis | Medium |
| R7 | Inability to demonstrate consent / honour withdrawal | Medium | Medium | Art. 7(1),(3) [2] | Consent-record schema; persistent withdrawal control | Low |
| R8 | Missing non-cookie trackers (pixels, fingerprinting, URLs) | Medium | Medium | EDPB 2/2023 [7] | Full tracker inventory incl. server-side/SDK | Low |
| R9 | Pre-implementing unadopted Digital Omnibus rules | Low | Medium | Reform status [12] | Track official status; comply with current law | Low |

# Implementation Roadmap

- **Phase 0 — Discovery:** Full inventory of all terminal-equipment reads/writes (cookies, storage, pixels, SDKs, fingerprinting, tracking URLs, server-side tags); necessity classification with rationale. *Effort:* Medium. *Depends on:* tag-management access.
- **Phase 1 — CMP selection & architecture:** Choose/build a CMP meeting the requirements spec (below); design purpose taxonomy, consent-record schema and prior-blocking mechanism. *Effort:* Medium–High.
- **Phase 2 — Banner & preference UX:** Symmetric, granular, plain-language first layer; persistent withdrawal control; no pre-ticking; dark-pattern review. *Effort:* Medium.
- **Phase 3 — Enforcement & governance:** Wire tag gating to consent state; if using TCF, complete joint-controller and legal-basis controls; vendor allow-listing. *Effort:* Medium–High.
- **Phase 4 — Assurance & watch:** Consent-rate/tag-compliance metrics; periodic re-scan for rogue tags; monitor Digital Omnibus / browser-signal developments. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Cookies/trackers set on load; banner (if any) is notice-only. | Non-essential tags fire before consent; no inventory. |
| 2 | Managed | Banner with accept; partial gating; some categories. | "Accept" present; "reject" buried; partial inventory. |
| 3 | Defined | Consent-before-set; symmetric, granular UX; consent records; withdrawal control. | Reject-as-easy-as-accept; off-by-default toggles; full tracker inventory. |
| 4 | Quantitatively Managed | Metrics on consent, tag compliance and withdrawal; periodic re-scans; dark-pattern audits. | KPIs; automated tag-gating verification; no non-cookie blind spots. |
| 5 | Optimising | Automated tag governance; certified CMP; TCF/joint-controller controls; browser-signal readiness; reform contingency. | Enforcing tag manager; GPC-capable; documented equivalent-alternative strategy. |

# Audit Questions

1. Is there a complete, current inventory of all terminal-equipment reads/writes (incl. pixels, SDKs, fingerprinting, tracking URLs, server-side tags), each classified by necessity with a documented rationale? *(Art. 5(3); EDPB 2/2023 [1][7].)*
2. Do you verify (by network inspection) that no non-essential technology fires before consent? *(Art. 5(3); ICO [1][10].)*
3. Are "Accept all" and "Reject all" equally prominent and low-friction on the first layer, with off-by-default granular toggles and no pre-ticking? *(Planet49 [3]; EDPB [6][8].)*
4. How is consent recorded (schema, versioning) to demonstrate it, and how do users withdraw as easily as they consented? *(Art. 7(1),(3) [2].)*
5. On what basis is each "strictly necessary" classification made? *(Art. 5(3); ICO [10].)*
6. If you deploy a cookie wall or consent-or-pay model, how do you satisfy "freely given" and (for large platforms) provide an equivalent alternative? *(EDPB Opinion 08/2024 [6].)*
7. If you use the IAB TCF, do you treat the TC String as personal data and have joint-controller and legal-basis controls in place? *(C-604/22 [4]; Market Court [11].)*
8. Have consent interfaces been audited against deceptive-design-pattern criteria? *(EDPB 03/2022 [9].)*
9. How are you tracking Digital Omnibus reform without pre-implementing unadopted rules? *([12].)*

# Implementation Checklist

- [ ] Complete inventory of all cookies/storage/pixels/SDKs/fingerprinting/tracking-URLs/server-side tags, classified strictly-necessary vs consent-required, with rationale.
- [ ] Consent-before-set enforced; verified by network inspection that nothing non-essential fires on first load.
- [ ] First layer offers **equal-prominence** "Accept all" and "Reject all" (no buried/greyed reject).
- [ ] Granular per-purpose (and where feasible per-vendor) toggles, all non-essential **off by default**; no pre-ticked boxes.
- [ ] No cookie wall; any consent-or-pay reviewed against EDPB Opinion 08/2024 (equivalent, usually free, alternative).
- [ ] Plain-language, layered information (purposes, vendors, durations, third-party access) before consent.
- [ ] Consent records captured (ID, timestamp, purposes/vendors, string/version, UI version) and retained securely.
- [ ] Persistent withdrawal control; withdrawal stops processing and expires/deletes affected cookies.
- [ ] TCF (if used): joint-controller arrangement, TC-String legal basis, certified CMP/version.
- [ ] Dark-pattern audit passed (symmetry, no confirmshaming/obstruction/nudging/re-prompting).
- [ ] "Strictly necessary" classifications documented and defensible (analytics/ads excluded).
- [ ] Reform watch-list: Digital Omnibus Arts. 88a/88b and browser-signal readiness.

**CMP requirements specification (hand to vendor/build team):** (a) prior blocking of all non-essential technologies incl. server-side/SDK; (b) configurable granular purpose taxonomy, off-by-default; (c) symmetric accept/reject at first layer; (d) tamper-evident consent-record store meeting Art. 7(1) with export; (e) persistent withdrawal/re-consent control with parity; (f) IAB TCF certification and current framework/GVL version if TCF is used; (g) capability to read/honour automated browser signals (e.g. GPC); (h) audit/reporting for consent rates and tag-gating compliance; (i) versioning of banner text/UI for evidential purposes.

# References

*All links verified live on 2026-07-11 (`sources_verified`). Classification per `SOURCE_REGISTRY.md`.*

## Primary Sources

- [1] **Directive 2002/58/EC (ePrivacy Directive), consolidated text** (as amended by Directive 2009/136/EC), Art. 5(3). EUR-Lex, CELEX 02002L0058-20091219. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219
- [2] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Arts. 4(11), 7; Recitals 32, 43. EUR-Lex, CELEX 02016R0679-20160504. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [3] **Planet49 (Verbraucherzentrale Bundesverband v Planet49 GmbH)**, CJEU, C-673/17, ECLI:EU:C:2019:801. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:62017CJ0673
- [4] **IAB Europe v Gegevensbeschermingsautoriteit**, CJEU, C-604/22, 7 Mar 2024, ECLI:EU:C:2024:214 (TC String = personal data; joint controllership). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A62022CJ0604
- [5] **Privacy and Electronic Communications (EC Directive) Regulations 2003 (PECR)**, SI 2003/2426, reg. 6. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/contents

## Regulatory Guidance

- [6] **Opinion 08/2024 on valid consent in the context of consent or pay models implemented by large online platforms** (adopted 17 April 2024). European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/our-documents/opinion-board-art-64/opinion-082024-valid-consent-context-consent-or_en
- [7] **Guidelines 2/2023 on the technical scope of Art. 5(3) of the ePrivacy Directive**, v2.0 (adopted 7 October 2024). EDPB. https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-22023-technical-scope-art-53-eprivacy-directive_en
- [8] **Guidelines 05/2020 on consent under Regulation 2016/679**, v1.1 (adopted 4 May 2020) — incl. cookie walls and conditionality. EDPB. https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-052020-consent-under-regulation-2016679_en
- [9] **Guidelines 03/2022 on deceptive design patterns in social media platform interfaces**, v2.0 (adopted 14 February 2023). EDPB. https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-032022-deceptive-design-patterns-social-media_en
- [10] **Guide to PECR** (incl. cookies and "reject all"/strictly-necessary interpretation). Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/
- [11] **IAB Europe case — the CJEU answers the questions referred for a preliminary ruling** (background to C-604/22 and Belgian proceedings; Market Court judgment of 14 May 2025). Belgian Data Protection Authority (APD/GBA). https://www.dataprotectionauthority.be/citizen/iab-europe-case-the-cjeu-answers-the-questions-referred-for-a-preliminary-ruling
- [12] **Legislative Train Schedule — the digital package (Digital Omnibus context)**. European Parliament. https://www.europarl.europa.eu/legislative-train/theme-a-new-plan-for-europe-s-sustainable-prosperity-and-competitiveness/file-digital-package

## Standards

Not Applicable — there is no ePrivacy-specific technical standard governing cookie consent. The **IAB Europe Transparency & Consent Framework (TCF)** is an *industry specification*, not a formal standard, and is treated as subject matter (not authority) in this document; see Further Reading. ISO/IEC 27701 (PIMS) applies to the underlying processing (per `gdpr-foundations`).

## Academic Sources

- [13] **Nouwens, Liccardi, Veale, Karger & Kagal, "Dark Patterns after the GDPR: Scraping Consent Pop-ups and Demonstrating their Influence"** (CHI 2020) — empirical evidence that reject-all is rarely as easy as accept and that design nudges consent. arXiv:2001.02479. https://arxiv.org/abs/2001.02479

# Further Reading

*Non-authoritative; provided for orientation only.*

- IAB Europe — Transparency & Consent Framework (industry specification and Global Vendor List). https://iabeurope.eu/transparency-consent-framework/
- Irish Council for Civil Liberties — facts on the Brussels Court of Appeal judgment of 14 May 2025 (complainant's account). https://www.iccl.ie/digital-data/facts-about-the-brussels-court-of-appeal-judgement-of-14-may-2025/
- European Commission — ePrivacy Regulation policy overview. https://digital-strategy.ec.europa.eu/en/policies/eprivacy-regulation

# Related Documents

- `eprivacy-foundations` — **parent**; Art. 5(3) cookie rule and ePrivacy/GDPR relationship (**prerequisite reading**).
- `gdpr-foundations` — meaning and conditions of consent (Arts. 4(11), 7).
- `uk-gdpr-foundations` — UK regime and PECR context.
- `privacy-engineering-foundations` — data-protection-by-design for consent mechanisms.
- `dsa-foundations` / `consumer-protection-foundations` — dark-pattern overlap (DSA Art. 25; UCPD/DMCCA).
- `pecr-detail` — UK PECR incl. DUAA cookie changes (planned).
- `digital-omnibus` — the 2025 simplification package and cookie-rule migration (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (ePrivacy Art. 5(3), GDPR Arts. 4(11)/7, Planet49, IAB Europe C-604/22), EDPB (Opinion 08/2024 consent-or-pay; Guidelines 2/2023, 05/2020, 03/2022), ICO Guide to PECR, Belgian DPA and academic literature; consent-or-pay and TCF/C-604/22 (incl. Brussels Market Court 14 May 2025) live-verified. | pending |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 2 human gate; frozen in release 0.11.0. | Human reviewer |
