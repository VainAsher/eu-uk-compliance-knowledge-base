---
id: dmcca-subscriptions
title: "UK DMCCA 2024: Subscription Contracts Regime"
version: 1.0.0
status: in-review
classification: public
jurisdiction: [UK]
topic: Consumer Rights
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [consumer-rights-foundations]
tags: [dmcca, subscriptions, subscription-contracts, auto-renewal, cooling-off, cancellation, reminder-notices, cma, consumer-rights, uk]
legal_basis: Digital Markets, Competition and Consumers Act 2024 (c.13) Part 4 Chapter 2; Consumer Rights Act 2015 (c.15); Consumer Contracts (Information, Cancellation and Additional Charges) Regulations 2013 (SI 2013/3134)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dmcca-subscriptions |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.15.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer (loop-authorised) — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. **PENDING / not yet in force:** the DMCCA subscription-contracts regime (Part 4, Chapter 2) is **not yet commenced**. The Department for Business and Trade (DBT) confirmed in its consultation response of **2 April 2026** that it "will legislate when parliamentary time allows and … anticipate[s] that the regime will commence in **spring 2027**"; the CMA repeats that "new rules are expected to come into force in Spring 2027" [6][7]. This date is an anticipated administrative target, not a fixed statutory date — **always confirm the current in-force status** before relying on any obligation described here.

# Executive Summary

This document is a deep dive into the **subscription-contracts regime** created by **Part 4, Chapter 2 (sections 253–267) of the UK Digital Markets, Competition and Consumers Act 2024 (DMCCA)** [1][2]. It is the operational companion to the Tier 4 parent reference `consumer-rights-foundations`, which sets the wider consumer-law context [1].

The regime is the UK's response to concerns about "subscription traps": contracts that are easy to enter and hard to leave, free or low-cost trials that silently roll into paid subscriptions, and auto-renewals that consumers forget about. When commenced, it will impose four core duties on traders offering subscription contracts to consumers: (1) give clear, prescribed **pre-contract "key information"** before the consumer is bound (s.256–257); (2) send **reminder notices** ahead of a renewal — in particular before a **free or low-cost trial auto-renews into a paid subscription** and before **long (12-month-plus) contracts** renew (s.258–259); (3) make it **straightforward to exit**, including online cancellation where the consumer signed up online (s.260); and (4) honour **cooling-off cancellation rights** with proportionate **refunds** (s.261, s.264–267) [2][6].

The critical, load-bearing fact for planning is **commencement**. The substantive duties are **PENDING / not yet in force**. The DBT government response of **2 April 2026** re-timetabled the regime to **spring 2027**, and the CMA's April 2026 enforcement review restates that date [6][7]. Enforcement, once live, sits within the CMA's **direct consumer-enforcement** powers under DMCCA Part 3 — the CMA can decide breaches itself and impose penalties up to **£300,000 or 10% of global annual turnover** [1][7][8]. Businesses should build compliant subscription journeys now and treat the spring-2027 date as a movable target to be tracked.

# Key Takeaways

- The subscription regime lives in **DMCCA 2024 Part 4, Chapter 2 (ss.253–267)** and is a distinct, standalone code layered on top of the Consumer Rights Act 2015 and the Consumer Contracts Regulations 2013 [1][2][3][4]. *(Legal obligation — not yet in force.)*
- **PENDING / not yet in force:** the regime is **anticipated to commence in spring 2027** per the DBT consultation response of 2 April 2026, echoed by the CMA; it is not a fixed statutory date [6][7]. *(Regulatory statement — track for change.)*
- A **"subscription contract"** is defined in s.254 (a contract for periodic supply of goods/services/digital content for payment, typically auto-renewing), with **excluded contracts** carved out in s.255 [2]. *(Legal obligation — not yet in force.)*
- Traders must give **pre-contract "key information"** before the consumer enters the contract (s.256–257), presented clearly and close to the point of commitment [2][6]. *(Legal obligation — not yet in force.)*
- Traders must send **reminder notices** before renewal — the regime specifically targets reminders **before a free/low-cost trial auto-renews into a paid subscription** and before **12-month-plus contracts** renew (s.258–259) [2][6]. *(Legal obligation — not yet in force.)*
- Consumers get **cooling-off cancellation rights**: an **initial cooling-off period** on sign-up and a **renewal cooling-off period** after a trial or a 12-month-plus contract auto-renews, each broadly a **14-day** window (s.264–266) [2][6]. *(Legal obligation — not yet in force.)*
- Traders must make exit **straightforward** and allow **online cancellation where sign-up was online** (s.260), and on cancellation must give **proportionate refunds** without undue delay (within 14 days) (s.261, s.267) [2][6]. *(Legal obligation — not yet in force.)*
- Enforcement runs through the CMA's **direct-enforcement** regime (DMCCA Part 3): the CMA can find a breach itself and levy penalties up to **£300,000 or 10% of global annual turnover** [1][7][8]. *(Legal obligation — enforcement framework in force; subscription duties pending.)*
- The regime **sits alongside**, and does not replace, the CRA 2015 quality/terms rights, the Consumer Contracts Regulations 2013 distance-selling rules, and the DMCCA Part 4 Chapter 1 unfair-practices ban (fake reviews, drip pricing) [1][3][4][8]. *(Legal obligation.)*

# Purpose

This document supports compliance planning and product/engineering design for any business that sells to UK consumers on a recurring or auto-renewing basis (SaaS, streaming, memberships, boxes, apps, in-game passes, gym/club-style memberships). It explains what the DMCCA subscription regime will require, how each duty maps to the statute, who enforces it and how hard, when it is expected to bite, and how it interacts with existing consumer law. It is deliberately actionable: it ends in a compliance checklist, a risk register and a roadmap so teams can build to the regime ahead of commencement. It is a sub-topic of `consumer-rights-foundations`.

# Scope

**In scope:** DMCCA 2024 Part 4 Chapter 2 (ss.253–267) — the definition of a subscription contract and exclusions; the pre-contract key-information duty; reminder notices (including the trial-to-paid and long-contract triggers); the cooling-off cancellation rights and refund rules; the easy-exit / online-cancellation duty; the enforcement route (CMA direct enforcement under Part 3) and penalties; the commencement timeline (live-verified); and interaction with the CRA 2015, the Consumer Contracts Regulations 2013 and the DMCCA unfair-practices rules.

**Out of scope (covered elsewhere or on the backlog):** the DMCCA unfair-trading / banned-practices regime in operational detail (fake reviews, drip pricing) → `consumer-rights-foundations` and its planned sub-topics; general CRA 2015 quality/conformity remedies → `consumer-remedies` (planned); the DMCCA digital-markets ("SMS") competition regime → `uk-digital-markets` (planned); financial-services, insurance, utilities and telecoms subscription rules under sector regulators (FCA, Ofgem, Ofcom) → sector backlog; EU auto-renewal / subscription rules → EU consumer sub-topics. The **final secondary legislation and CMA/DBT guidance** that will fill in prescribed detail (exact content and format of key information, reminder timing tolerances) are not yet made; this document flags where that detail is pending.

**Assumptions:** The reader has read `consumer-rights-foundations` and understands the consumer/trader distinction and the CMA's direct-enforcement powers. Personal-data processing in any subscription (billing, reminders, cancellation) remains governed by the UK GDPR in parallel (see `gdpr-foundations`).

# Definitions

*Shared consumer-law terms (consumer, trader, right of withdrawal, dark pattern) are in `GLOSSARY.md`. Terms specific to this regime are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Subscription contract | A contract under which a trader agrees to supply goods, services or digital content to a consumer on a recurring basis in return for payment, typically renewing automatically until cancelled (DMCCA s.254). | [2] |
| Excluded contract | A contract falling outside the regime by virtue of DMCCA s.255 (e.g. contracts otherwise regulated, or types the Act/secondary legislation carves out). | [2] |
| Key (pre-contract) information | The prescribed information a trader must give the consumer before the consumer enters a subscription contract, so the consumer understands price, renewal, duration and how to cancel (DMCCA s.256–257). | [2] |
| Reminder notice | A notice the trader must send the consumer before a renewal payment or before a free/low-cost trial converts to a paid subscription, and before long (12-month-plus) contracts renew (DMCCA s.258–259). | [2] |
| Initial cooling-off period | A period (broadly 14 days) after entering the contract during which the consumer may cancel (DMCCA s.264–265). | [2] |
| Renewal cooling-off period | A further cooling-off period triggered when a trial, or a contract of 12 months or more, auto-renews into a (further) paid term (DMCCA s.264–265). | [2] |
| Cooling-off notice | The notice by which the trader informs the consumer of a cooling-off cancellation right (DMCCA s.266). | [2] |
| Subscription trap | Non-statutory shorthand for practices the regime targets: hard-to-cancel contracts, silent trial-to-paid conversions and unremembered auto-renewals. | [6] |

# Background

Subscriptions are now a mainstream way to buy digital and physical goods, but regulators and consumer bodies identified recurring harms: consumers signing up to a "free trial" and being charged when it silently converted, contracts that renewed automatically without a prompt, and cancellation journeys engineered to be difficult ("roach motel" / hard-to-cancel dark patterns). The UK government estimated that unwanted subscriptions cost consumers significant sums each year, and framed the new rules as delivering around **£400 million of consumer benefit per year** [6].

The DMCCA 2024 received Royal Assent on **24 May 2024**. Its consumer-protection provisions began commencing on **6 April 2025** under the Commencement No. 2 Regulations (SI 2025/272), bringing into force the CMA's direct-enforcement powers (Part 3) and the unfair-trading / banned-practices regime (Part 4 Chapter 1, replacing the Consumer Protection from Unfair Trading Regulations 2008) [1][5][8]. The **subscription-contracts regime in Part 4 Chapter 2 was deliberately held back**: it depends on further secondary legislation to set prescribed detail and on the government finalising its implementation approach. After consulting during 2025–2026, the DBT published its **government response on 2 April 2026**, confirming both the shape of the regime and a revised commencement target of **spring 2027** — later than the timetable originally floated when the Act passed [6]. The CMA's **"Direct consumer enforcement: one year on"** blog of 17 April 2026 restates that "new rules are expected to come into force in Spring 2027 with guidance from DBT" [7].

# Legal Framework

The subscription regime is **DMCCA 2024, Part 4, Chapter 2, sections 253–267** [1][2]. It is a self-contained statutory code that, once commenced, will apply to subscription contracts between traders and consumers, sitting on top of — not replacing — the CRA 2015 (quality of goods/services/digital content and unfair-terms control) and the Consumer Contracts Regulations 2013 (distance-selling pre-contract information and the 14-day cancellation right) [3][4].

The Chapter is organised as a lifecycle:

- **Definition and scope** — s.253 (overview), s.254 (meaning of "subscription contract"), s.255 (excluded contracts) [2].
- **Entry (pre-contract)** — s.256 and s.257 (key pre-contract information and additional requirements) [2].
- **During the contract (renewal)** — s.258 and s.259 (reminder notices; their content and timing), targeting trial-to-paid conversions and long-contract renewals [2].
- **Exit** — s.260 (arrangements for the consumer to exercise the right to end the contract, including online exit) and s.261 (trader's duties on cancellation or end of contract, including refunds) [2].
- **Implied terms and breach** — s.262 (terms implied into contracts) and s.263 (right to cancel for breach of an implied term) [2].
- **Cooling-off** — s.264 (right to cancel during cooling-off periods), s.265 (meaning of "initial" and "renewal" cooling-off periods), s.266 (cooling-off notice), s.267 (further provision on cancellation, including refunds) [2].

**Enforcement** does not sit in Chapter 2. Breaches of the subscription duties will be enforceable as breaches of **consumer protection law** through the CMA's (and courts'/other enforcers') powers, principally the **direct-enforcement regime in DMCCA Part 3**, which lets the CMA decide a breach administratively and impose monetary penalties (up to **£300,000 or 10% of global annual turnover** for the infringement, plus daily and other penalties) and enhanced consumer-protection measures such as redress [1][7][8].

## Relevant Articles

*"Article" = section of the DMCCA 2024 (and companion statutes). Sections in Part 4 Chapter 2 are **not yet in force** (PENDING).*

| Provision | Obligation | Source |
|-----------|------------|--------|
| DMCCA s.253 | Overview of the subscription-contracts Chapter. | [2] |
| DMCCA s.254 | Meaning of "subscription contract" (recurring supply for payment, typically auto-renewing). | [2] |
| DMCCA s.255 | Excluded contracts (types outside the regime). | [2] |
| DMCCA s.256–257 | **Pre-contract "key information"** must be given before the consumer enters the contract, with additional requirements. | [2] |
| DMCCA s.258–259 | **Reminder notices** before renewal; content and timing — including before a free/low-cost **trial auto-renews to paid** and before **12-month-plus** contracts renew. | [2] |
| DMCCA s.260 | Arrangements for the consumer to exercise the right to end the contract — **straightforward exit, online where sign-up was online**. | [2] |
| DMCCA s.261 | Trader's duties on cancellation or end of contract, including ceasing supply/charges and **refunds**. | [2] |
| DMCCA s.262–263 | Terms implied into subscription contracts and the right to cancel for breach of an implied term. | [2] |
| DMCCA s.264–266 | **Cooling-off** cancellation rights: initial and renewal cooling-off periods (broadly 14 days) and the cooling-off notice. | [2] |
| DMCCA s.267 | Further provision on cancellation, including **proportionate refunds** without undue delay. | [2] |
| DMCCA Part 3 | CMA **direct enforcement** of consumer protection law; monetary penalties (up to £300,000 or 10% of global turnover) and enhanced consumer measures. | [1] |
| DMCCA Part 4 Ch. 1 | Unfair-trading / banned practices (fake reviews, drip pricing) applying to subscription marketing and sign-up. | [1][8] |
| CRA 2015 Parts 1–2 | Parallel quality/conformity rights and unfair-terms control that continue to apply to subscription supplies. | [3] |
| CCR 2013 | Distance-selling pre-contract information and the 14-day cancellation right that apply to online subscription sign-ups. | [4] |

## Relevant Recitals

Not Applicable — UK primary legislation is not structured with recitals in the manner of EU Regulations/Directives; interpretive intent for this regime is found in the DBT consultation response and (forthcoming) statutory guidance rather than recitals [6]. Explanatory Notes to the Act and the DBT response perform the analogous interpretive function and are treated as REGULATORY INTERPRETATION below.

## Relevant Case Law

Not Applicable — the subscription-contracts regime is **new and not yet in force**, so there is no case law construing DMCCA Part 4 Chapter 2. Enforcement will initially be administrative (CMA direct enforcement under Part 3), and any judicial interpretation will develop only after commencement (anticipated spring 2027) and subsequent appeals [2][6][7]. This section will be populated as CMA decisions and appeals emerge.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **DBT government response (2 April 2026)** sets out the intended shape of the regime: clear pre-contract information, **regular reminders "particularly before trials or 12 month+ contracts auto-renew"**, **two 14-day cooling-off periods** (an initial period on sign-up and a renewal period after a trial or long contract auto-renews), a requirement that it be **"straightforward for people to exit contracts"** with **online exit where sign-up was online**, and **proportionate refunds** paid "without undue delay and within 14 days" (proportionate for services/digital content; full for returnable goods) [6]. *(Regulatory interpretation of pending obligations.)*
- On **timing**, DBT states it "will legislate when parliamentary time allows and … anticipate[s] that the regime will commence in **spring 2027**" — an explicit acknowledgement that the date is an expectation contingent on further legislation, not a fixed commencement [6]. *(Regulatory statement — track for change.)*
- The **CMA** reinforces the date and division of labour: "new rules are expected to come into force in **Spring 2027** with guidance from DBT" — signalling that operational guidance will accompany commencement [7]. *(Regulatory statement.)*
- On **enforcement posture**, the CMA's first-year direct-enforcement review (covering April 2025–April 2026) shows the regulator already active on adjacent harms — **drip pricing, fake reviews and online choice architecture** — with **14 investigations**, **£4.7m in fines**, **£760,000 in consumer refunds ordered**, and **157 advisory/warning letters**; subscription "choice architecture" (hard-to-cancel flows) is squarely within its stated focus, so subscription businesses should expect scrutiny once the specific rules commence [7][8]. *(Regulatory interpretation / factual.)*
- **CMA207 ("Unfair commercial practices")** interprets the Part 4 Chapter 1 banned-practices regime that already applies to subscription **marketing and sign-up** (e.g. hidden fees / drip pricing, fake reviews, obstacles to exercising contractual rights), independently of the not-yet-commenced Chapter 2 duties [8]. *(Regulatory interpretation of a live obligation.)*

# Technical Considerations

- **Sign-up flow (pre-contract key information)** — surface the prescribed key information (price and billing cadence, what renews and when, minimum term, how to cancel) **before** the consumer commits, prominently and close to the "subscribe/pay" action, and record that it was provided (s.256–257) [2][6]. *(Legal obligation — pending.)*
- **Trial-to-paid conversion logic** — instrument any **free or low-cost trial** so the system sends a **reminder notice before the trial converts** to a paid subscription and applies the **renewal cooling-off period** on conversion (s.258–259, s.264–265) [2][6]. *(Legal obligation — pending.)*
- **Reminder engine** — build a scheduled notification capability keyed to renewal dates, with the required lead time and content for both trial conversions and **12-month-plus** renewals; log delivery for evidence (s.258–259) [2][6]. *(Legal obligation — pending.)*
- **Cancellation / exit journey** — provide a **straightforward exit** with **online cancellation where sign-up was online**; avoid obstructive "retention" dark patterns, which also risk being an unfair practice under Part 4 Chapter 1 (s.260) [2][8]. *(Legal obligation — pending; unfair-practice overlap in force.)*
- **Refund calculation** — implement **proportionate refunds** for cancelled services/digital content (and full refunds for returnable goods), paid **within 14 days** and without undue delay (s.261, s.267) [2][6]. *(Legal obligation — pending.)*
- **Cooling-off state machine** — model both the **initial** (on sign-up) and **renewal** (post-conversion) 14-day windows, including how supply and charging behave during and after cancellation (s.264–267) [2][6]. *(Legal obligation — pending.)*
- **Records & audit trail** — retain evidence that key information, reminders and cooling-off notices were sent and that cancellations were honoured, to answer CMA information notices (Part 3) [1][7]. *(Best practice — supports defensibility.)*

# Hosting Considerations

- Consumer-facing subscription duties fall on the **trader** contracting with the consumer, not on a pure IaaS/PaaS host as such; a hosting provider is not usually the "trader" toward the end consumer [2]. *(Interpretation.)*
- However, **billing, paywall, subscription-management and notification components** supplied by a platform or host on the trader's behalf must **support compliant flows** — schedulable reminder notices, online cancellation, cooling-off handling and proportionate refunds — because the obligation flows through to the trader that relies on them (s.256–267) [2][6]. *(Best practice / obligation flows through.)*
- **Marketplaces and app stores** that mediate subscriptions should map which party owes each duty (store vs. developer) and ensure their platform cancellation and refund mechanics do not obstruct a trader's ability to offer straightforward exit and timely refunds (s.260–261) [2]. *(Editorial recommendation.)*

# Game Hosting Considerations

- **Auto-renewing battle passes, season passes, memberships and premium subscriptions** are subscription contracts: once the regime commences they require pre-contract key information, renewal reminders, easy/online exit and cooling-off/refund handling (s.254–267) [2][6]. *(Legal obligation — pending.)*
- **Free trials converting to paid** are the paradigm case the regime targets — a "free weekend" or trial tier that silently becomes a charged subscription must trigger a **reminder before conversion** and a **renewal cooling-off period** (s.258–259, s.264–265) [2][6]. *(Legal obligation — pending.)*
- **Children as consumers** — much game spend involves minors; combine the subscription duties with children's data-protection rules (ICO Children's Code) and avoid aggressive or obstructive cancellation designs, which are also unfair practices (Part 4 Ch. 1) [8]. *(Legal obligation + best practice.)*
- **In-game virtual-currency subscriptions / recurring top-ups** should present total price transparently at sign-up (drip-pricing of bundle costs is already a banned practice) and support the same reminder/exit/refund mechanics once Chapter 2 is live [2][8]. *(Legal obligation — Ch. 1 in force; Ch. 2 pending.)*

# AI Considerations

- **AI-driven retention / "save" flows** at cancellation (personalised offers, friction, chatbots that make leaving hard) risk breaching the **straightforward-exit** duty (s.260) and, independently, the unfair-practices ban on obstructing contractual rights (Part 4 Ch. 1); design AI cancellation assistants to **complete** cancellation, not to obstruct it [2][8]. *(Legal obligation — Ch. 1 in force; Ch. 2 pending.)*
- **AI-personalised pricing or trial offers** must still deliver accurate, prominent pre-contract key information and honest total pricing; algorithmic optimisation of sign-up must not bury renewal or cancellation terms (s.256–257) [2]. *(Legal obligation — pending.)*
- **Automated reminder generation** — using AI to draft or time reminder notices is acceptable provided the notices meet the statutory content and timing requirements and are reliably delivered and logged (s.258–259) [2]. *(Best practice.)*
- Any AI processing of subscriber personal data (churn prediction, targeting) engages the **UK GDPR** in parallel; run consumer-law and data-protection compliance together (see `gdpr-foundations`). *(Legal obligation — parallel regime.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**. Chapter 2 obligations are **PENDING (anticipated spring 2027)** — treat as "build now, enforce from commencement".

1. **Provide prescribed pre-contract key information** before sign-up, prominently and near the point of commitment, and record it. *(OBLIGATION — pending.)* [2][6]
2. **Send reminder notices before renewal**, especially before a **free/low-cost trial converts to paid** and before **12-month-plus** contracts renew, with the required content and lead time. *(OBLIGATION — pending.)* [2][6]
3. **Make exit straightforward and offer online cancellation** where the consumer signed up online; remove obstructive retention friction. *(OBLIGATION — pending; unfair-practice overlap in force.)* [2][8]
4. **Implement both cooling-off periods** — the initial (sign-up) and renewal (post-conversion) ~14-day windows — with correct supply/charging behaviour. *(OBLIGATION — pending.)* [2][6]
5. **Pay proportionate refunds** (full for returnable goods; proportionate for services/digital content) **within 14 days** and without undue delay. *(OBLIGATION — pending.)* [2][6]
6. **Keep an evidence trail** of key information, reminders, cooling-off notices and honoured cancellations to answer CMA information notices. *(BEST PRACTICE.)* [1][7]
7. **Align sign-up marketing with the in-force unfair-practices rules now** — no drip pricing, no fake reviews, no obstruction of rights (Part 4 Ch. 1). *(OBLIGATION — in force.)* [8]
8. **Maintain a commencement watch-list** for the subscription regime (spring 2027 target) and the forthcoming secondary legislation and DBT/CMA guidance. *(EDITORIAL RECOMMENDATION.)* [6][7]
9. **Run consumer-law and UK GDPR compliance together** — one subscription touches billing, reminders (marketing/consent) and cancellation data. *(BEST PRACTICE.)* [1]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Silent trial-to-paid conversion without a reminder | High | High | DMCCA s.258–259 [2][6] | Reminder before conversion; renewal cooling-off | Low |
| R2 | Hard-to-cancel / obstructive exit flow | High | High | DMCCA s.260; Part 4 Ch. 1 [2][8] | Straightforward online cancellation; remove friction | Low |
| R3 | Missing/inadequate pre-contract key information | Medium | High | DMCCA s.256–257 [2] | Prominent prescribed disclosure at sign-up; records | Low |
| R4 | No/late cooling-off cancellation right honoured | Medium | High | DMCCA s.264–266 [2][6] | Initial + renewal 14-day windows in the flow | Low |
| R5 | Refunds not proportionate or not within 14 days | Medium | Medium | DMCCA s.261, s.267 [2][6] | Proportionate-refund logic; 14-day SLA | Low |
| R6 | Building to the wrong date / spec (regime shifts) | Medium | Medium | Spring-2027 target is anticipatory [6][7] | Commencement watch-list; modular build | Low |
| R7 | Drip pricing / fake reviews at subscription sign-up | Medium | High | DMCCA Part 4 Ch. 1 [8] | Total-price display; review-integrity controls | Low |
| R8 | CMA direct penalty (up to 10% global turnover) | Medium | Very High | DMCCA Part 3 [1][7] | Compliance programme; evidence trail; monitor cases | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory subscription products:** Catalogue every recurring/auto-renewing offer to UK consumers (trials, memberships, passes); confirm which are "subscription contracts" (s.254) and any exclusions (s.255). *Effort:* Medium.
- **Phase 1 — Sign-up compliance:** Build prescribed pre-contract key information into sign-up; align marketing with the in-force unfair-practices rules (no drip pricing / fake reviews). *Effort:* Medium.
- **Phase 2 — Reminder engine:** Implement scheduled reminder notices for trial conversions and 12-month-plus renewals, with logging. *Effort:* Medium–High.
- **Phase 3 — Exit & cooling-off:** Deliver straightforward online cancellation, the initial and renewal cooling-off windows, and proportionate-refund logic with a 14-day SLA. *Effort:* High.
- **Phase 4 — Evidence & assurance:** Retain proof of notices, cancellations and refunds; prepare to answer CMA information notices. *Effort:* Medium.
- **Phase 5 — Monitor & finalise:** Track the spring-2027 commencement, the secondary legislation and DBT/CMA guidance; finalise prescribed content/timing once published. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Subscriptions offered with ad hoc terms; no reminder or easy-exit design. | No inventory; trials convert silently; hard cancellation. |
| 2 | Managed | Basic pre-contract disclosure and a working cancellation route exist. | Total-price shown; some cancellation path. |
| 3 | Defined | Documented mapping to ss.254–267; reminders and online exit designed; cooling-off modelled. | Reminder engine; online cancellation; cooling-off logic. |
| 4 | Quantitatively Managed | Metrics on reminders sent, cancellations honoured, refund SLAs; evidence trail maintained. | KPIs; audit logs; tested trial-conversion flow. |
| 5 | Optimising | Fully compliant, tested subscription lifecycle integrated with UK GDPR; proactive commencement/guidance tracking. | Automated compliant journeys; enforcement-ready records. |

# Audit Questions

1. Which products are "subscription contracts" (s.254) and which fall within an exclusion (s.255)? *([2].)*
2. Is prescribed **pre-contract key information** shown prominently before commitment and recorded? *(s.256–257 [2].)*
3. Are **reminder notices** sent before trial-to-paid conversion and before 12-month-plus renewals, with correct content/timing and delivery logs? *(s.258–259 [2][6].)*
4. Can a consumer who signed up online **cancel online** and is exit genuinely straightforward? *(s.260 [2].)*
5. Are the **initial and renewal cooling-off** windows implemented, with correct supply/charging behaviour? *(s.264–266 [2][6].)*
6. Are **refunds** proportionate (or full for returnable goods) and paid within 14 days? *(s.261, s.267 [2][6].)*
7. Is subscription **marketing/sign-up** free of drip pricing and fake reviews under the in-force Part 4 Ch. 1 rules? *([8].)*
8. Is there a **commencement watch-list** for the spring-2027 target and the forthcoming secondary legislation/guidance? *([6][7].)*

# Implementation Checklist

- [ ] Inventory of all UK-consumer subscription/auto-renewing products with s.254/s.255 classification.
- [ ] Prescribed pre-contract key information shown prominently at sign-up and recorded (s.256–257).
- [ ] Reminder notices scheduled before trial-to-paid conversion and 12-month-plus renewals, with delivery logging (s.258–259).
- [ ] Straightforward exit implemented; online cancellation where sign-up was online (s.260).
- [ ] Initial and renewal cooling-off (~14-day) windows built into the lifecycle (s.264–266).
- [ ] Proportionate/full refunds paid within 14 days and without undue delay (s.261, s.267).
- [ ] Subscription marketing aligned with in-force unfair-practices rules (no drip pricing / fake reviews) (Part 4 Ch. 1).
- [ ] Evidence trail retained for notices, cancellations and refunds (Part 3 information-notice readiness).
- [ ] UK GDPR compliance integrated for billing, reminders and cancellation data.
- [ ] Commencement watch-list maintained (spring-2027 target; secondary legislation and DBT/CMA guidance).

# References

*All links verified live (HTTP 2xx/3xx) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Digital Markets, Competition and Consumers Act 2024 (c.13), contents.** legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2024/13/contents
- [2] **Digital Markets, Competition and Consumers Act 2024, Part 4 Chapter 2 (Subscription contracts, ss.253–267).** legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2024/13/part/4/chapter/2
- [3] **Consumer Rights Act 2015 (c.15), contents.** legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2015/15/contents
- [4] **Consumer Contracts (Information, Cancellation and Additional Charges) Regulations 2013 (SI 2013/3134).** legislation.gov.uk. https://www.legislation.gov.uk/uksi/2013/3134/contents
- [5] **The Digital Markets, Competition and Consumers Act 2024 (Commencement No. 2) Regulations 2025 (SI 2025/272).** legislation.gov.uk. https://www.legislation.gov.uk/uksi/2025/272/contents

## Regulatory Guidance

- [6] **Government response to consultation on the implementation of the new subscription contracts regime** (web accessible version), 2 April 2026. Department for Business and Trade / GOV.UK. Confirms the regime "will commence in spring 2027", the key requirements (pre-contract information, reminders before trials/12-month-plus renewals, two 14-day cooling-off periods, straightforward/online exit, proportionate refunds within 14 days) and the ~£400m/year benefit estimate. https://www.gov.uk/government/consultations/consultation-on-the-implementation-of-the-new-subscription-contracts-regime/outcome/government-response-to-consultation-on-the-implementation-of-the-new-subscription-contracts-regime-web-accessible-version
- [7] **Direct consumer enforcement: one year on.** CMA blog, 17 April 2026. Restates subscription rules "expected to come into force in Spring 2027 with guidance from DBT"; first-year direct-enforcement figures (14 investigations, £4.7m fines, £760,000 refunds ordered, 157 advisory letters). https://competitionandmarkets.blog.gov.uk/2026/04/17/direct-consumer-enforcement-one-year-on/
- [8] **Unfair commercial practices (CMA207).** Competition and Markets Authority / GOV.UK — guidance on the DMCCA Part 4 Chapter 1 unfair-trading provisions (banned practices from 6 April 2025; drip pricing; fake reviews; obstruction of consumer rights). https://www.gov.uk/government/publications/unfair-commercial-practices-cma207/unfair-commercial-practices

## Standards

Not Applicable — subscription-contract compliance is defined by legislation and regulator guidance, not by ISO/NIST/OWASP-type technical standards. UX and accessibility standards may inform implementation of sign-up, reminder and cancellation journeys but are not the source of the legal obligations.

## Academic Sources

Not Applicable — this guidance relies on primary legislation and regulatory sources. Relevant scholarship (dark-patterns / "subscription trap" behavioural research) is cited in `consumer-rights-foundations` and its planned sub-topics.

# Further Reading

*Non-authoritative; provided for orientation only.*

- Consultation on the implementation of the new subscription contracts regime (landing page). GOV.UK. https://www.gov.uk/government/consultations/consultation-on-the-implementation-of-the-new-subscription-contracts-regime
- Digital Markets, Competition and Consumers Act 2024 (Commencement No. 2) Regulations 2025 — explanatory note. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2025/272/note/made

# Related Documents

- `consumer-rights-foundations` — Tier 4 parent reference; details the DMCCA, CMA direct enforcement and the wider consumer-law framework (**prerequisite reading**).
- `gdpr-foundations` — parallel data-protection regime for billing, reminders and cancellation data (**cross-reference**).
- `consumer-remedies` — CRA 2015 quality/conformity remedies in depth (planned).
- `uk-digital-markets` — the DMCCA digital-markets (SMS) competition regime (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against legislation.gov.uk (DMCCA 2024 contents and Part 4 Chapter 2 ss.253–267; CRA 2015; CCR 2013; SI 2025/272), the DBT subscription-contracts government response (2 Apr 2026) and the CMA direct-enforcement one-year review (17 Apr 2026) and CMA207. Commencement live-verified: subscription regime **not yet in force**, anticipated **spring 2027** per DBT response and CMA. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved via autonomous backlog loop (Cluster A); passed full QA suite; frozen in release 0.15.0. | Human reviewer (loop-authorised) |

</content>
</invoke>
