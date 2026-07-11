---
id: consumer-rights-foundations
title: "Consumer Rights: Foundations (EU & UK)"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU, UK]
topic: Consumer Rights
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [gdpr-foundations, dsa-foundations, dma-foundations, eprivacy-foundations]
tags: [consumer-rights, crd, ucpd, uctd, digital-content, dmcca, cma, subscriptions, fake-reviews, drip-pricing]
legal_basis: Directive 2011/83/EU; Directive 2005/29/EC; Directive 93/13/EEC; Directive (EU) 2019/770; Directive (EU) 2019/771; Directive (EU) 2019/2161; Consumer Rights Act 2015; Consumer Contracts Regulations 2013; Digital Markets, Competition and Consumers Act 2024
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | consumer-rights-foundations |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The UK regime is undergoing **phased commencement** under the Digital Markets, Competition and Consumers Act 2024 — in particular the **subscription-contracts rules were re-timetabled to Spring 2027** — always confirm the current in-force status of a specific provision before relying on it [12][13].

# Executive Summary

Consumer-protection law sets the baseline rules for how businesses may market, contract with and treat consumers — natural persons acting outside their trade. For digital businesses (e-commerce, apps, SaaS, games, streaming and subscriptions) it governs pre-contract disclosure, the right to cancel distance purchases, quality rights in goods, services and **digital content**, the fairness of standard contract terms, and the honesty of commercial practices including pricing and reviews.

In the **EU**, the framework is a set of harmonising Directives: the **Consumer Rights Directive 2011/83/EU (CRD)** (pre-contract information; 14-day right of withdrawal) [1]; the **Unfair Commercial Practices Directive 2005/29/EC (UCPD)** (the general prohibition on misleading and aggressive practices, plus a blacklist) [2]; the **Unfair Contract Terms Directive 93/13/EEC (UCTD)** (non-negotiated terms causing significant imbalance are not binding) [3]; and the 2019 "digital content" pair — **Directive (EU) 2019/770** on the supply of digital content and services and **Directive (EU) 2019/771** on the sale of goods [4][5]. The **"Omnibus" / Modernisation Directive (EU) 2019/2161** (applicable since **28 May 2022**) added transparency duties on **price reductions**, **fake reviews** and **online marketplaces**, and put stronger penalties behind the UCPD [6].

In the **UK**, the **Consumer Rights Act 2015 (CRA)** consolidated goods, services and — importantly — **digital content** quality rights [7], and the **Consumer Contracts Regulations 2013** carry the CRD's distance-selling information and cancellation rules [8]. The decisive recent change is the **Digital Markets, Competition and Consumers Act 2024 (DMCCA)** [9]: it received Royal Assent on **24 May 2024**, and its consumer provisions began to commence on **6 April 2025**, replacing the 2008 unfair-trading regime, banning **fake reviews** and **drip pricing**, and — critically — giving the **Competition and Markets Authority (CMA) direct enforcement powers** with fines up to **£300,000 or 10% of global annual turnover** [9][10][11][12]. The DMCCA **subscription-contracts** regime was **delayed to Spring 2027** by the government's consultation response of 2 April 2026 [12][13]. Consumer law operates alongside — not instead of — the GDPR and the Digital Services Act (see `gdpr-foundations`, `dsa-foundations`).

# Key Takeaways

- **Consumer law is a distinct layer** from data-protection and platform law: it governs pre-contract disclosure, cancellation, quality/conformity and fair dealing for **consumers** (natural persons acting outside a trade) [1][7]. *(Legal obligation.)*
- The **EU CRD (2011/83/EU)** requires extensive **pre-contract information** and a **14-day right of withdrawal** for distance/off-premises contracts, with defined exceptions (e.g. supply of digital content where the consumer consents to immediate performance and waives withdrawal) [1]. *(Legal obligation.)*
- The **UCPD (2005/29/EC)** prohibits misleading and aggressive practices via a general clause plus an Annex I **blacklist** of always-unfair practices; the **Omnibus Directive** added fake-review and price-reduction rules [2][6]. *(Legal obligation.)*
- The **UCTD (93/13/EEC)** makes **unfair non-negotiated terms non-binding** and requires plain, intelligible language; core-price and subject-matter terms escape assessment only if transparent [3]. *(Legal obligation.)*
- **Directives (EU) 2019/770 and 2019/771** created harmonised **conformity (quality) rights** for **digital content/services** and for goods (including goods with digital elements), applicable in Member States since **1 January 2022** [4][5]. *(Legal obligation.)*
- The **UK CRA 2015** gives statutory quality rights in **goods, services and digital content** (satisfactory quality, fit for purpose, as described) with a tiered remedy structure [7]. *(Legal obligation.)*
- The **DMCCA 2024** (Royal Assent **24 May 2024**) commenced its core consumer-protection provisions on **6 April 2025**, replacing the Consumer Protection from Unfair Trading Regulations 2008 and banning **fake reviews** and **drip pricing** [9][10][11]. *(Legal obligation — in force.)*
- The DMCCA gives the **CMA direct enforcement** (no court finding required) with penalties up to **£300,000 or 10% of global annual turnover** for consumer-law breaches; in its first year the CMA opened investigations into 14 businesses and issued penalties (e.g. an AA driving-school drip-pricing case) [11][12]. *(Legal obligation — in force.)*
- The DMCCA **subscription-contracts** regime (pre-contract info, renewal reminders, cooling-off, easy exit) was **postponed to Spring 2027** by the DBT consultation response of **2 April 2026** — plan to that date, but treat it as movable [12][13]. *(Legal obligation — not yet in force.)*

# Purpose

This document is the Tier 4 entry point to consumer-protection law for the compliance knowledge base. It supports legal research (mapping the EU Directives and UK statutes and how they interact), compliance planning (what a digital business must disclose, honour and refrain from), and product/engineering triage (checkout flows, cancellation journeys, review systems, subscription lifecycles). It builds on and cross-references `gdpr-foundations` and `dsa-foundations`, and deliberately pushes deep sub-topics to the backlog.

# Scope

**In scope:** The EU consumer-protection instruments relevant to digital businesses (CRD, UCPD, UCTD, Directives 2019/770 and 2019/771, and the Omnibus Directive); the UK CRA 2015, Consumer Contracts Regulations 2013, and the DMCCA 2024 consumer-protection provisions at a foundational level; live-verified DMCCA commencement status; and how the regime interacts with the GDPR and DSA.

**Out of scope (spun off to the research backlog):** DMCCA subscription-contracts rules in operational detail → `dmcca-subscriptions`; the DMCCA digital-markets / gatekeeper regime → covered by `dma-foundations` (EU) and to be extended for the UK CMA "SMS" regime in `uk-digital-markets`; product-specific consumer regimes (financial services, package travel, timeshare, consumer credit) → topic backlog; **ADR/ODR** (alternative/online dispute resolution) mechanics → `consumer-adr`; product safety (GPSR) → `product-safety`; guarantees/commercial warranties in depth → `consumer-remedies`.

**Assumptions:** The reader understands the difference between a **consumer** (natural person acting outside trade) and a **trader/business**. Personal-data processing in any consumer transaction remains governed by the GDPR in parallel (see `gdpr-foundations`).

# Definitions

*Shared cross-cutting terms (personal data, controller, online platform) are defined in `GLOSSARY.md`. Only consumer-law terms of art used in this document are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Consumer | A natural person acting for purposes wholly or mainly outside that person's trade, business, craft or profession (CRD Art. 2(1); CRA 2015 s.2(3)). | [1][7] |
| Trader | Any natural or legal person acting for purposes relating to their trade, business, craft or profession in consumer transactions (CRD Art. 2(2)). | [1] |
| Distance contract | A contract concluded without simultaneous physical presence of trader and consumer, using exclusively means of distance communication (CRD Art. 2(7)). | [1] |
| Right of withdrawal | The consumer's right to withdraw from a distance/off-premises contract within 14 days without reason and without cost (CRD Arts. 9–16). | [1] |
| Digital content | Data produced and supplied in digital form (CRD Art. 2(11); Directive (EU) 2019/770 Art. 2(1)); under the CRA 2015 it carries statutory quality rights. | [1][4][7] |
| Conformity | The requirement that goods/digital content/services meet subjective and objective quality criteria (Directive (EU) 2019/770 Arts. 6–8; 2019/771 Arts. 5–7). | [4][5] |
| Unfair commercial practice | A business-to-consumer practice contrary to professional diligence that materially distorts consumers' economic behaviour, or a misleading/aggressive practice, or one on the Annex I blacklist (UCPD Arts. 5–9, Annex I). | [2] |
| Unfair contract term | A non-individually-negotiated term that, contrary to good faith, causes a significant imbalance in the parties' rights to the consumer's detriment (UCTD Art. 3). | [3] |
| Drip pricing | Advertising an initial ("headline") price and then adding mandatory or effectively unavoidable charges later in the purchase journey; banned as an unfair practice under the DMCCA. | [9][11] |
| Subscription contract | A contract under which a consumer is periodically supplied goods/services/digital content for payment, typically with automatic renewal; subject to the DMCCA's (not-yet-in-force) subscription regime. | [9][13] |

# Background

EU consumer law developed as a series of minimum- and later **maximum-harmonisation** Directives to build the internal market while protecting consumers. The **UCTD (1993)** and **UCPD (2005)** set fairness baselines for terms and practices; the **CRD (2011)** harmonised pre-contract information and the withdrawal right for distance and off-premises contracts, replacing the older Distance Selling Directive [1][2][3]. As commerce moved to paid apps, streaming and cloud services, the EU adopted the 2019 "digital content" pair — **Directive (EU) 2019/770** (supply of digital content/services) and **Directive (EU) 2019/771** (sale of goods, including goods with digital elements) — applicable in Member States from **1 January 2022** [4][5]. The **Omnibus / Modernisation Directive (EU) 2019/2161**, applicable since **28 May 2022**, modernised the older Directives for the digital economy: transparency of **price reductions**, disclosure of **paid ranking** and whether reviews are verified, a ban on **fake/incentivised reviews**, information duties for **online marketplaces**, and GDPR-style **penalties** (up to at least 4% of turnover for widespread cross-border infringements) [6].

The UK implemented the EU baseline while a Member State. The **Consumer Rights Act 2015** consolidated and modernised goods/services rights and, for the first time in UK statute, created a dedicated **digital content** category [7]. The **Consumer Contracts (Information, Cancellation and Additional Charges) Regulations 2013** transposed the CRD [8]. After Brexit these instruments were retained. The UK then diverged and modernised through the **Digital Markets, Competition and Consumers Act 2024**, which — alongside a new digital-markets competition regime — overhauled consumer enforcement: it replaced the Consumer Protection from Unfair Trading Regulations 2008, codified banned practices (including fake reviews and drip pricing), and gave the **CMA** the power to decide breaches and levy fines **directly**, rather than only through the courts [9][10][11].

# Legal Framework

Consumer protection for a digital business is best understood as **four functional layers**, each with an EU and a UK instrument:

1. **Pre-contract information & cancellation** — EU: **CRD 2011/83/EU** [1]; UK: **Consumer Contracts Regulations 2013** [8].
2. **Fair commercial practices** (marketing, pricing, reviews) — EU: **UCPD 2005/29/EC** as amended by the **Omnibus Directive** [2][6]; UK: **DMCCA 2024 Part 4 Ch. 1** (replacing the 2008 Regulations) [9][11].
3. **Fair contract terms** — EU: **UCTD 93/13/EEC** [3]; UK: **CRA 2015 Part 2** [7].
4. **Quality / conformity rights & remedies** — EU: **Directives (EU) 2019/770 and 2019/771** [4][5]; UK: **CRA 2015 Part 1** (goods, services, digital content) [7].

The **DMCCA** adds a fifth, cross-cutting layer for the UK: **enforcement** (Part 3) and **subscription contracts** (Part 4 Ch. 2, not yet in force) [9]. Consumer law is generally **fully harmonised** in the EU for the CRD and the 2019 Directives (Member States may not add or subtract), whereas the UCTD sets a minimum floor.

## Relevant Articles

*Selected foundational provisions. EU Directive articles bind via national transposition; UK statutory sections apply directly.*

| Provision | Obligation | Source |
|-----------|------------|--------|
| CRD Arts. 5–6 | Mandatory pre-contract information (identity, price incl. taxes, delivery, withdrawal rights, duration/termination of contracts). | [1] |
| CRD Arts. 9–16 | 14-day right of withdrawal for distance/off-premises contracts; model withdrawal form; exceptions (incl. digital content with prior consent and waiver, Art. 16(m)). | [1] |
| UCPD Arts. 5–9 + Annex I | Prohibition of unfair (misleading/aggressive) practices; Annex I "blacklist" of always-unfair practices. | [2] |
| UCPD Art. 6a (via Omnibus) / Art. 7(6) | Fake-review prohibition; disclosure of whether reviews are from actual purchasers; disclosure of paid ranking. | [2][6] |
| Price Indication Dir. Art. 6a (via Omnibus) | Price-reduction announcements must state the prior lowest price in the preceding 30 days. | [6] |
| UCTD Arts. 3–6 + Annex | Unfair non-negotiated terms not binding; plain-language requirement; indicative "grey list" of suspect terms. | [3] |
| Dir. (EU) 2019/770 Arts. 6–14 | Conformity criteria, trader liability and remedies for digital content and digital services. | [4] |
| Dir. (EU) 2019/771 Arts. 5–14 | Conformity, liability and remedies for goods, including goods with digital elements. | [5] |
| CRA 2015 ss.9–11, 34–36 | Goods and digital content to be of satisfactory quality, fit for purpose, and as described. | [7] |
| CRA 2015 ss.19–24, 42–45 | Consumer remedies: repair/replacement, price reduction, right to reject / refund tiers. | [7] |
| CRA 2015 ss.49–50, 62 | Services with reasonable care and skill; fairness test for consumer contract terms. | [7] |
| DMCCA 2024 Part 3 | CMA direct enforcement of consumer protection law; penalties (fines and enhanced consumer measures). | [9] |
| DMCCA 2024 Part 4 Ch. 1 + Sch. 20 | Protection from unfair trading; 32 always-unfair practices (incl. fake reviews, drip pricing). | [9][11] |
| DMCCA 2024 Part 4 Ch. 2 | Subscription contracts regime (pre-contract info, reminders, cooling-off, exit) — **not yet commenced**. | [9][13] |

## Relevant Recitals

*Recitals are non-binding but aid construction of the Directives.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| CRD Recital 4–5 | Full harmonisation of information and withdrawal rules to remove internal-market barriers and boost consumer confidence. | [1] |
| UCPD Recital 6–8 | The Directive protects consumers' economic interests via a general prohibition plus specific misleading/aggressive categories. | [2] |
| Dir. (EU) 2019/770 Recital 19–20 | Digital content/services covered irrespective of medium; addresses "data as counter-performance" (paying with personal data). | [4] |
| Omnibus Dir. Recital 47–49 | Rationale for review-transparency and fake-review measures as consumers increasingly rely on reviews. | [6] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| *Content Services v Bundesarbeitskammer* | CJEU, C-49/11, ECLI:EU:C:2012:419 | Making information available only via a hyperlink does not satisfy "durable medium" pre-contract disclosure requirements. | Digital pre-contract disclosure must be provided durably, not merely linked [1]. |
| *Verein für Konsumenteninformation v Amazon* | CJEU, C-191/15, ECLI:EU:C:2016:612 | A term in online T&Cs choosing the trader's home-country law can be unfair if it misleads the consumer about applicable mandatory rules. | Illustrates UCTD fairness control over standard online terms [3]. |
| *(UK DMCCA case law)* | — | To be added as CMA direct-enforcement decisions and any appeals develop from 2025 onward. | Not Applicable at foundational level (regime new) [9][12]. |

*Case citations above are illustrative of established EU consumer-law principles; full case-law treatment is deferred to sub-topic documents. Neutral citations were not independently re-verified against a court database at `sources_verified` and are labelled REGULATORY INTERPRETATION / EDITORIAL context rather than load-bearing primary authority.*

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** treats the CRD, UCPD, UCTD and the 2019 Directives as an integrated consumer *acquis*, and has issued guidance notices on each (e.g. UCPD guidance, price-indication guidance) explaining how the Omnibus changes on reviews, ranking and price reductions apply to online traders [14][15]. *(Regulatory interpretation.)*
- The **CMA** interprets the DMCCA unfair-trading provisions in its guidance **"Unfair commercial practices" (CMA207)**: the provisions **replace and update the 2008 CPUT Regulations** and apply to commercial practices occurring **from 6 April 2025**; **Schedule 20** lists **32 practices that are unfair in all circumstances**, including fake reviews and hidden/drip fees [11]. *(Regulatory interpretation of a legal obligation.)*
- On **enforcement approach**, the CMA said it would focus its first 12 months on the most **egregious** conduct — objectively false information, aggressive practices targeting the vulnerable, banned practices (fake reviews), hidden fees, and clearly imbalanced terms — and applied a **grace period** of roughly six months before actively enforcing the **fake-review** rules [11][12]. *(Regulatory interpretation.)*
- The CMA's **one-year review (April 2026)** reports real enforcement: investigations into **14 businesses**, settlements, 157 advisory letters, and concrete outcomes such as a **drip-pricing** case (AA / BSM driving schools) with consumer refunds and a multi-million-pound penalty [12]. *(Regulatory interpretation / factual.)*
- On **subscriptions**, the **DBT** confirmed in its **2 April 2026** consultation response that the new regime is **delayed to Spring 2027**; the CMA's own communications now say "new rules are expected to come into force in Spring 2027" [12][13]. *(Regulatory statement — not yet law; track for change.)*

# Technical Considerations

- **Checkout price transparency** — display the **total price inclusive of taxes and all mandatory charges** up front; do not reveal unavoidable fees only late in the flow (drip pricing is a banned practice in the UK and misleading under the UCPD) [9][11]. *(Legal obligation.)*
- **Pre-contract information capture** — surface CRD/CCR-mandated information (identity, price, delivery, duration, withdrawal rights, cancellation form) and record that it was provided on a **durable medium**, not just a hyperlink [1][8]. *(Legal obligation.)*
- **Cancellation / withdrawal journeys** — implement a working **14-day** withdrawal mechanism for distance sales, with the model form; for digital content delivered immediately, capture the consumer's **express consent and acknowledgement of loss of withdrawal** before performance [1][8]. *(Legal obligation.)*
- **Reviews systems** — do not publish or commission **fake or incentivised reviews**; disclose whether and how reviews are verified as coming from actual purchasers; disclose **paid ranking/placement** [2][6][11]. *(Legal obligation.)*
- **Reference-price / discount logic** — where advertising a price reduction to EU consumers, compute the "was" price as the **lowest price in the prior 30 days** [6]. *(Legal obligation, EU.)*
- **Digital-content conformity & updates** — build **update delivery** and conformity guarantees into digital products; the 2019/770 regime and CRA extend quality liability across the supply period, including required updates [4][7]. *(Legal obligation.)*
- **Terms drafting** — standard terms must be in **plain, intelligible language**; avoid terms on the UCTD "grey list" / CRA fairness blacklist (e.g. disproportionate exit charges, unilateral variation) [3][7]. *(Legal obligation.)*

# Hosting Considerations

- Consumer-law duties fall on the **trader** (the business contracting with the consumer), not the hosting/infrastructure provider as such; a pure IaaS/PaaS host is not usually the "trader" toward the end consumer. *(Interpretation.)*
- However, **billing, checkout, paywall and subscription-management components** that a host or platform provides on the trader's behalf must support compliant flows (total-price display, cancellation, withdrawal, renewal reminders once the DMCCA subscription rules commence) [1][9][13]. *(Best practice / obligation flows through to the trader.)*
- **Marketplaces/platforms** have their own information duties under the Omnibus Directive (e.g. disclosing whether a third-party seller is a trader) and under the **DSA** (see `dsa-foundations`); a hosting business that operates a marketplace should not assume it is out of scope [6]. *(Legal obligation for marketplace operators.)*

# Game Hosting Considerations

- **In-game purchases, loot boxes, virtual currency and DLC** are digital-content/services supplies: pre-contract price transparency, honest presentation, and conformity rights apply; presenting the true total cost (avoiding drip/obscured pricing of virtual-currency bundles) is directly relevant [1][4][7][11]. *(Legal obligation.)*
- **Subscriptions and auto-renewing battle passes / memberships** will fall within the DMCCA subscription regime (reminders, cooling-off, easy exit) once it commences in **Spring 2027**; design renewal and cancellation journeys now [9][13]. *(Obligation once in force — prepare early.)*
- **Fake or incentivised reviews / ratings** of games or in-game items are banned; review-manipulation and shill ratings are Schedule 20 practices [9][11]. *(Legal obligation.)*
- **Children as consumers** — much game spend involves minors; combine consumer-law fairness with the data-protection children's rules (see `uk-gdpr-foundations`, ICO Children's Code) and avoid aggressive/manipulative practices targeting the vulnerable [2][11]. *(Legal obligation + best practice.)*

# AI Considerations

- **AI-generated or AI-amplified fake reviews** are squarely within the fake-review bans (UCPD Art. 6a as amended; DMCCA Sch. 20) regardless of whether a human or a model authored them [2][6][11]. *(Legal obligation.)*
- **Dark patterns / manipulative UX**, including AI-personalised persuasion and choice architecture that distorts a consumer's decision, can be an **unfair (aggressive or misleading) commercial practice**; the UCPD/DMCCA fairness tests apply to algorithmic interfaces, and the DSA separately restricts dark patterns on platforms (see `dsa-foundations`) [2][11]. *(Legal obligation / interpretation.)*
- **Automated/dynamic and personalised pricing** must still meet transparency duties (total price, and — EU — the 30-day reference-price rule for advertised reductions); personalised pricing based on automated decision-making must be disclosed under the CRD as amended and engages the GDPR (see `gdpr-foundations`) [1][6]. *(Legal obligation.)*
- **AI chatbots/agents that contract with consumers** do not displace the trader's pre-contract information and withdrawal duties; the trader remains responsible for what its automated agent tells the consumer [1]. *(Interpretation.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Display total, inclusive prices** (taxes + mandatory fees) before the consumer commits; eliminate drip pricing. *(OBLIGATION.)* [9][11]
2. **Provide full pre-contract information on a durable medium** and confirm the contract afterwards (identity, price, delivery, duration, withdrawal). *(OBLIGATION.)* [1][8]
3. **Offer a working 14-day withdrawal** for distance sales; for immediate digital content, capture express consent + waiver of withdrawal before performance. *(OBLIGATION.)* [1][8]
4. **Ban fake/incentivised reviews and disclose verification and paid ranking**; audit any review or ratings feature. *(OBLIGATION.)* [2][6][11]
5. **Apply the EU 30-day reference-price rule** to advertised reductions for EU consumers. *(OBLIGATION, EU.)* [6]
6. **Honour statutory quality/conformity rights and remedies** for goods, services and digital content, including required updates. *(OBLIGATION.)* [4][5][7]
7. **Review standard terms for fairness** — plain language; remove imbalanced terms (unfair exit charges, unilateral variation). *(OBLIGATION.)* [3][7]
8. **Prepare subscription journeys now** for the DMCCA regime (pre-contract info, renewal reminders, cooling-off, easy/online exit), targeting the **Spring 2027** date but tracking DBT/CMA updates. *(BEST PRACTICE — obligation once in force.)* [9][13]
9. **Maintain a DMCCA commencement watch-list** and a CMA-enforcement risk view given direct fines up to 10% of global turnover. *(EDITORIAL RECOMMENDATION.)* [11][12]
10. **Run consumer-law and GDPR/DSA compliance together** — one checkout touches all three. *(BEST PRACTICE.)* [1]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Drip pricing / hidden mandatory fees at checkout | High | High | DMCCA Sch. 20; UCPD [9][11] | Show total inclusive price up front | Low |
| R2 | Fake / incentivised reviews or undisclosed paid ranking | Medium | High | UCPD Art. 6a; DMCCA Sch. 20 [2][6][11] | Review-integrity controls; disclosures | Low |
| R3 | Defective withdrawal / cancellation journey (distance sales) | Medium | Medium | CRD Arts. 9–16; CCR 2013 [1][8] | Compliant 14-day flow + model form | Low |
| R4 | Missing/ non-durable pre-contract information | Medium | Medium | CRD Arts. 5–6 [1][8] | Durable-medium disclosure + records | Low |
| R5 | Unfair standard terms (exit charges, unilateral variation) | Medium | High | UCTD; CRA 2015 s.62 [3][7] | Legal review of T&Cs; plain language | Low |
| R6 | Non-conforming digital content / missing updates | Medium | Medium | Dir. 2019/770; CRA 2015 [4][7] | Conformity + update commitments; remedy process | Low |
| R7 | Non-compliant subscription flows when DMCCA regime commences | Medium | High | DMCCA Part 4 Ch. 2 [9][13] | Build reminders/cooling-off/exit ahead of Spring 2027 | Medium |
| R8 | CMA direct penalty (up to 10% global turnover) | Medium | Very High | DMCCA Part 3 [9][11][12] | Compliance programme; monitor CMA cases | Medium |

# Implementation Roadmap

- **Phase 0 — Map obligations:** Identify which layers apply (pre-contract, practices, terms, conformity) per product and per market (EU vs UK). *Effort:* Medium.
- **Phase 1 — Pricing & practices:** Remove drip pricing; fix reference-price logic (EU); audit reviews and ranking disclosures. *Effort:* Medium.
- **Phase 2 — Pre-contract & cancellation:** Durable-medium disclosure; compliant 14-day withdrawal; digital-content consent/waiver capture. *Effort:* Medium.
- **Phase 3 — Terms & conformity:** Legal review of standard terms; conformity/update commitments and remedy workflows for goods and digital content. *Effort:* Medium–High.
- **Phase 4 — Subscriptions readiness:** Build DMCCA subscription flows (reminders, cooling-off, exit) to the Spring 2027 target. *Effort:* High.
- **Phase 5 — Monitor & assure:** DMCCA commencement watch-list; track CMA enforcement and EC guidance; periodic legal review. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Consumer law treated ad hoc; checkout and terms unreviewed. | No mapping; drip pricing / weak cancellation. |
| 2 | Managed | Core disclosures and withdrawal in place; obvious unfair practices removed. | Basic CRD/CCR compliance. |
| 3 | Defined | Documented obligations per market; reviews/ranking disclosures; fair terms; conformity remedies. | Consumer-law control set; DMCCA watch-list. |
| 4 | Quantitatively Managed | Metrics on cancellation, complaints, refund SLAs; subscription flows built and tested. | KPIs; periodic legal review. |
| 5 | Optimising | Integrated consumer-law + GDPR + DSA controls; proactive tracking of DMCCA/EC reform. | Automated compliant flows; enforcement-ready records. |

# Audit Questions

1. Does the checkout display a **total price** inclusive of taxes and all mandatory charges before commitment? *(DMCCA Sch. 20; UCPD [9][11].)*
2. How is **pre-contract information** delivered and retained on a durable medium? *(CRD Arts. 5–6; CCR 2013 [1][8].)*
3. Is there a working **14-day withdrawal** process, and for immediate digital content, a captured consent + waiver? *(CRD Arts. 9–16 [1].)*
4. What controls prevent **fake/incentivised reviews**, and how are verification and paid ranking disclosed? *(UCPD Art. 6a; DMCCA Sch. 20 [2][6][11].)*
5. For EU price reductions, is the **30-day lowest prior price** used? *(Omnibus Dir. [6].)*
6. How are **conformity rights and remedies** (incl. updates) honoured for goods and digital content? *(Dir. 2019/770/771; CRA 2015 [4][5][7].)*
7. Have **standard terms** been reviewed for fairness and plain language? *(UCTD; CRA 2015 s.62 [3][7].)*
8. What is the plan and current status for the **DMCCA subscription regime** (Spring 2027 target)? *(DMCCA Part 4 Ch. 2 [9][13].)*

# Implementation Checklist

- [ ] Total, tax-and-fee-inclusive pricing shown before commitment (no drip pricing).
- [ ] Full pre-contract information provided on a durable medium and confirmed.
- [ ] Working 14-day withdrawal flow with model cancellation form.
- [ ] Digital-content express consent + waiver-of-withdrawal captured before immediate performance.
- [ ] Fake/incentivised reviews prohibited; review verification and paid ranking disclosed.
- [ ] EU 30-day reference-price rule applied to advertised reductions.
- [ ] Conformity/quality remedies (repair/replace/refund) and update commitments in place.
- [ ] Standard terms reviewed for fairness and plain language.
- [ ] DMCCA subscription flows (reminders, cooling-off, easy exit) scoped for Spring 2027.
- [ ] DMCCA commencement watch-list and CMA-enforcement risk view maintained.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Directive 2011/83/EU on consumer rights (CRD).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2011/83/oj
- [2] **Directive 2005/29/EC on unfair commercial practices (UCPD).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2005/29/oj
- [3] **Directive 93/13/EEC on unfair terms in consumer contracts (UCTD).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/1993/13/oj
- [4] **Directive (EU) 2019/770 on contracts for the supply of digital content and digital services.** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2019/770/oj
- [5] **Directive (EU) 2019/771 on contracts for the sale of goods.** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2019/771/oj
- [6] **Directive (EU) 2019/2161 ("Omnibus" / Modernisation Directive).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2019/2161/oj
- [7] **Consumer Rights Act 2015 (c.15), contents.** legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2015/15/contents
- [8] **Consumer Contracts (Information, Cancellation and Additional Charges) Regulations 2013 (SI 2013/3134).** legislation.gov.uk. https://www.legislation.gov.uk/uksi/2013/3134/contents
- [9] **Digital Markets, Competition and Consumers Act 2024 (c.13), contents.** legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2024/13/contents
- [10] **The Digital Markets, Competition and Consumers Act 2024 (Commencement No. 2) Regulations 2025 (SI 2025/272).** legislation.gov.uk. https://www.legislation.gov.uk/uksi/2025/272/contents

## Regulatory Guidance

- [11] **Unfair commercial practices (CMA207).** Competition and Markets Authority / GOV.UK (guidance on the DMCC Act unfair-trading provisions; practices from 6 April 2025; Schedule 20 blacklist; updated 18 Nov 2025). https://www.gov.uk/government/publications/unfair-commercial-practices-cma207/unfair-commercial-practices
- [12] **Direct consumer enforcement: one year on.** CMA blog, 17 April 2026 (first-year enforcement summary; fake-review grace period; drip-pricing outcomes; subscription rules "expected Spring 2027"). https://competitionandmarkets.blog.gov.uk/2026/04/17/direct-consumer-enforcement-one-year-on/
- [13] **Government response to consultation on the implementation of the new subscription contracts regime** (web accessible version), 2 April 2026. Department for Business and Trade / GOV.UK (regime delayed to Spring 2027). https://www.gov.uk/government/consultations/consultation-on-the-implementation-of-the-new-subscription-contracts-regime/outcome/government-response-to-consultation-on-the-implementation-of-the-new-subscription-contracts-regime-web-accessible-version
- [14] **Consumer Rights Directive — EU consumer contract law.** European Commission. https://commission.europa.eu/law/law-topic/consumer-protection-law/consumer-contract-law/consumer-rights-directive_en
- [15] **Unfair Commercial Practices Directive.** European Commission. https://commission.europa.eu/law/law-topic/consumer-protection-law/unfair-commercial-practices-law/unfair-commercial-practices-directive_en

## Standards

Not Applicable — consumer-protection compliance is defined by legislation and regulator guidance, not by ISO/NIST/OWASP-type technical standards. (Accessibility and UX standards may inform implementation but are not the source of the legal obligations.)

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation and regulatory guidance. Academic analysis (e.g. dark-patterns scholarship, harmonisation critique) will be cited in sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- The Digital Markets, Competition and Consumers Act 2024 (Commencement No. 2) Regulations 2025 — explanatory note. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2025/272/note/made
- Consumer rights and complaints (citizen-facing overview). European Commission. https://commission.europa.eu/live-work-travel-eu/consumer-rights-and-complaints_en

# Related Documents

- `gdpr-foundations` — data-protection regime that applies in parallel to every consumer transaction (**prerequisite context**).
- `dsa-foundations` — Digital Services Act: platform duties, dark-patterns restrictions, marketplace transparency (**cross-reference**).
- `dma-foundations` — EU Digital Markets Act; the DMCCA's digital-markets (SMS) regime is the UK analogue (**cross-reference**).
- `dmcca-subscriptions` — DMCCA subscription-contracts regime in depth (planned).
- `consumer-adr` — alternative/online dispute resolution (planned).
- `consumer-remedies` — quality/conformity remedies and guarantees in depth (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (CRD, UCPD, UCTD, Dirs 2019/770, 2019/771, 2019/2161), legislation.gov.uk (CRA 2015, CCR 2013, DMCCA 2024 + Commencement No. 2 Regs), CMA and DBT/GOV.UK sources. DMCCA commencement status live-verified: consumer provisions in force 6 April 2025; subscription regime delayed to Spring 2027 per DBT consultation response of 2 April 2026 and CMA one-year review of April 2026. | pending |
