---
id: pecr-detail
title: "UK PECR: Marketing, Cookies & Enforcement in Depth"
version: 1.0.0
status: approved
classification: public
jurisdiction: [UK]
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
related: [eprivacy-foundations, cookie-consent-implementation, duaa-2025-detail, uk-gdpr-foundations, digital-omnibus]
tags: [pecr, eprivacy, direct-marketing, cookies, soft-opt-in, tps, duaa-2025, ico-enforcement, uk]
legal_basis: Privacy and Electronic Communications (EC Directive) Regulations 2003 (SI 2003/2426), as amended by the Data (Use and Access) Act 2025 (c.18)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | pecr-detail |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.16.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a deep-dive that **details** the parent reference `eprivacy-foundations` (PECR as the UK transposition of the ePrivacy Directive) — read that first, and read `cookie-consent-implementation` (cookie UX/CMP depth) and `duaa-2025-detail` (the DUAA reforms end-to-end) alongside it. PECR was **materially amended by the Data (Use and Access) Act 2025**, with the main changes commencing **5 February 2026**; confirm the in-force status of any specific provision before relying on it [11][12][19].

# Executive Summary

The **Privacy and Electronic Communications (EC Directive) Regulations 2003 ("PECR", SI 2003/2426)** are the UK transposition of the ePrivacy Directive and sit alongside the UK GDPR [1][13]. They govern **electronic direct marketing** (live and automated calls, fax, email and SMS), **cookies and similar device access**, the **security** of public electronic-communications services, and **traffic and location data** [1]. The ICO enforces PECR; it takes many of its investigatory and sanctioning powers from the Data Protection Act 2018 [15].

Two pillars dominate day-to-day compliance. First, **direct marketing**: automated calls (reg. 19), fax (reg. 20) and **email/SMS** (reg. 22) require the recipient's **prior consent**, with a narrow **"soft opt-in"** for an organisation's own existing customers; **live calls** (reg. 21) run on an **opt-out** model policed by the **Telephone Preference Service (TPS/CTPS)** [6][7][8][9]. Second, **cookies and similar technologies** (reg. 6): storing or accessing information on a user's device requires **consent** unless it is strictly necessary for a service the user requested — the same GDPR-standard consent confirmed for cookies by **Planet49** [2][14].

The **Data (Use and Access) Act 2025 (DUAA)** rewired PECR in three ways that this document live-verifies. (1) **Enforcement uplift** — the ICO's PECR monetary-penalty ceiling rises from the historic **£500,000** to the **UK GDPR maxima of £17.5m or 4% of global annual turnover**, and the old "substantial damage or distress" threshold is removed [18][20]. (2) **New cookie-consent exemptions** — a new PECR Schedule exempts defined **low-risk** device-access purposes (statistical/analytics to improve a service, remembering display preferences, security/fraud prevention, technical delivery and emergency-location) from the consent requirement [16][17][20]. (3) **Charity soft opt-in** — the reg. 22 soft opt-in is extended so **charities** can email/text people who previously expressed interest in their charitable purposes, for fundraising and campaigning [9][20][22]. These changes commenced on **5 February 2026** [12][19]; the separate DUAA complaints-handling duty follows on 19 June 2026 [19].

# Key Takeaways

- **PECR (SI 2003/2426)** is the UK's ePrivacy law: it governs electronic marketing, cookies, communications security and traffic/location data, and works **alongside** the UK GDPR [1][13][15]. *(Legal obligation.)*
- **Automated calls (reg. 19), fax (reg. 20) and email/SMS (reg. 22)** are **consent-first** marketing channels; **live calls (reg. 21)** are **opt-out**, screened against the **TPS/CTPS** register [6][7][8][9]. *(Legal obligation.)*
- The **email/SMS "soft opt-in"** (reg. 22(3)) lets a business market its **own similar products** to people whose details it collected **in the course of a sale (or negotiations for a sale)**, provided an opt-out was offered at collection and in every message [9][15]. *(Legal obligation.)*
- **Cookies and similar device access (reg. 6)** require **consent** unless **strictly necessary** for a service the user requested; consent takes its meaning from the UK GDPR, and a pre-ticked box is not valid consent (**Planet49**) [2][14]. *(Legal obligation / case law.)*
- **DUAA enforcement uplift (LIVE-VERIFIED):** PECR maximum penalties rise from **£500,000** to **£17.5m / 4% of global turnover**, aligning ICO PECR powers with the UK GDPR/DPA 2018 and removing the "substantial damage or distress" hurdle [18][20]. *(Legal obligation — in force 5 Feb 2026.)*
- **DUAA cookie exemptions (LIVE-VERIFIED):** a new PECR Schedule exempts low-risk device access — service-improvement **statistics/analytics**, remembering **preferences**, **security/fraud**, technical delivery and **emergency location** — from consent; **profiling/advertising still needs consent** [16][17][20]. *(Legal obligation — in force 5 Feb 2026.)*
- **DUAA charity soft opt-in (LIVE-VERIFIED):** reg. 22 is amended so **charities** may use the soft opt-in for fundraising/charitable-purpose marketing to prior supporters/interested persons; the ICO consulted on its approach in 2025 [9][20][22]. *(Legal obligation — in force 5 Feb 2026.)*
- **Commencement:** the main PECR changes took effect **5 February 2026** (DUAA Commencement No. 6 Regulations, SI 2026/82); the DUAA statutory complaints duty commences **19 June 2026** and some ICO-governance provisions follow later [12][19]. *(Legal fact.)*

# Purpose

This document is the UK PECR deep-dive. It supports (a) marketing, CRM and growth teams choosing a lawful basis per channel; (b) engineering and web teams gating cookies and similar technologies; (c) privacy/legal teams pricing enforcement risk after the DUAA uplift; and (d) charity/non-profit fundraisers assessing the new soft opt-in. It answers: *which PECR rule applies to each marketing channel; when consent versus soft opt-in versus opt-out applies; what "strictly necessary" and the new cookie exemptions cover; and how the DUAA changed fines, cookies and the charity soft opt-in.* It provides a **channel × consent-basis decision matrix** and a **PECR compliance checklist**.

# Scope

**In scope:** PECR electronic direct-marketing rules (regs. 19–23) including consent, soft opt-in, the TPS/CTPS and sender-identification; the reg. 6 cookie/device-access rule and the strictly-necessary and new DUAA exemptions; communications security (reg. 5) and traffic/location data (regs. 7, 14) at implementation depth; ICO PECR enforcement and the DUAA fine uplift; the PECR ↔ UK GDPR consent relationship; and the DUAA changes with their commencement.

**Out of scope (cross-referenced):** The foundational ePrivacy/GDPR relationship and Directive text → `eprivacy-foundations` (**parent**). Cookie-banner/CMP design, "consent or pay", the IAB TCF and dark patterns → `cookie-consent-implementation`. The DUAA reforms as a whole (recognised legitimate interests, ADM, transfers, the Information Commission) → `duaa-2025-detail`. The general meaning of consent → `gdpr-foundations` / `uk-gdpr-foundations`. The EU reform trajectory (ePrivacy Regulation withdrawal; Digital Omnibus cookie-rule migration) → `digital-omnibus`. Data-retention/communications-data case law under Art. 15 → `data-retention-caselaw` (backlog).

**Assumptions:** The reader has read `eprivacy-foundations`. "Consent", "PECR" and "cookie rule" carry their `GLOSSARY.md` meanings. The organisation is a UK-facing sender/operator subject to PECR and the UK GDPR.

# Definitions

*Shared terms (consent, controller, personal data, PECR, cookie rule) are in `GLOSSARY.md`. Only PECR-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Direct marketing | The communication (by whatever means) of advertising or marketing material directed to particular individuals (DPA 2018 s.122(5), applied by PECR). | [15] |
| Soft opt-in | The reg. 22(3) exception permitting email/SMS marketing of an organisation's **own similar products/services** to a person whose contact details were obtained in the course of a sale (or negotiations for a sale), where opt-out was offered at collection and in each message. | [9][15] |
| Charitable-purpose soft opt-in | The DUAA extension of the soft opt-in enabling charities to market (fundraising/charitable purposes) to people who previously expressed interest in those purposes. | [9][20][22] |
| Telephone Preference Service (TPS) | The statutory register of individuals/organisations who have opted out of unsolicited live marketing calls; the CTPS is its corporate-subscriber equivalent (reg. 26). | [8][15] |
| Automated calling system | Equipment that makes calls and plays a recorded message without a live operator (reg. 19); always requires prior consent. | [6] |
| Strictly necessary (reg. 6 exemption) | Device storage/access essential to provide the service the subscriber/user **explicitly requested** (e.g. session, security, load-balancing, consent-preference storage); analytics and advertising are **not** strictly necessary. | [2][15] |
| Low-risk cookie exemption (DUAA) | A purpose listed in the DUAA-inserted PECR Schedule for which device storage/access is exempt from consent (service-improvement statistics, preferences, security/fraud, technical delivery, emergency location). | [16][17][20] |

# Background

PECR came into force in **December 2003** to transpose the ePrivacy Directive (2002/58/EC); it was amended in **2004, 2011 and 2018** — the 2011 amendments moved the cookie rule to a **consent** model and introduced the security-breach duty, and the DPA 2018 re-based PECR's enforcement onto the 2018 Act's powers [1][13][15]. Throughout, PECR has operated in tandem with the general data-protection law: PECR sets **channel-specific** rules, while the (UK) GDPR supplies the **definition and conditions of consent** and applies to any personal data processed [13][15].

Enforcement history shaped the reform debate. The ICO's PECR monetary-penalty power was historically capped at **£500,000** — two orders of magnitude below the UK GDPR ceiling — and originally required proof that a contravention caused **substantial damage or distress**, a threshold that constrained action against nuisance-call and spam-text operators until it was relaxed for those channels [15]. Nuisance marketing (automated calls, spam SMS, and TPS-breaching live calls) remained the ICO's highest-volume PECR enforcement area.

The **Data (Use and Access) Act 2025** is the reform vehicle. It does not replace PECR; it **amends** it — raising the fine ceiling to UK GDPR levels, inserting a new Schedule of low-risk **cookie exemptions**, and extending the **soft opt-in to charities** [11][18][20]. Ahead of commencement the ICO consulted (October 2025) on how the new **charitable-purpose soft opt-in** should work and updated its cookie/storage-and-access guidance [17][22]. The main changes commenced on **5 February 2026** [12][19]. Looking further ahead, the EU's Digital Omnibus proposes migrating the cookie rule into the GDPR (see `digital-omnibus`), but that is EU-side and does not bind PECR [21].

# Legal Framework

PECR is **secondary legislation** (made under the European Communities Act 1972 and preserved as assimilated law). Its operative duties fall into four blocks: **marketing** (regs. 19–24), **cookies/device access** (reg. 6), **security** (reg. 5) and **communications data** (regs. 7–14) [1]. Enforcement runs through **reg. 31 and Schedule 1**, which apply parts of the DPA 2018 enforcement regime (information notices, assessment notices, enforcement notices and monetary penalties) to PECR contraventions [1][15]. Where PECR is silent, the UK GDPR applies to the underlying personal data; where PECR sets a specific rule (e.g. marketing consent, cookie consent), that rule governs the channel [13][15].

Distinguish throughout: **OBLIGATION** (what PECR requires), **REGULATORY INTERPRETATION** (ICO reading), **BEST PRACTICE**, and **EDITORIAL RECOMMENDATION**.

## Relevant Articles

*"Article" here means the PECR regulation (or the amending DUAA provision) as the case may be.*

| Provision | Obligation / effect | Source |
|-----------|---------------------|--------|
| PECR reg. 5 (+ 5A/5C) | Providers of public electronic-communications services must take appropriate technical/organisational security measures and notify certain personal-data breaches. | [3] |
| PECR reg. 6 | Consent (with prior clear information) required before storing/accessing information on terminal equipment; exemption where strictly necessary for a requested service — plus the DUAA low-risk exemptions. | [2][16] |
| PECR reg. 7 | Restrictions on processing **traffic data**; erase or anonymise when no longer needed for transmission/billing, subject to consent for value-added services. | [4] |
| PECR reg. 14 | **Location data** (other than traffic data) may be processed only if anonymised or with consent, for a value-added service. | [5] |
| PECR reg. 19 | **Automated calling systems** (recorded-message calls) for direct marketing require the **prior consent** of the subscriber. | [6] |
| PECR reg. 20 | Marketing by **fax** to individuals requires prior consent; corporate faxes are opt-out (fax preference/objection). | [7] |
| PECR reg. 21 | Unsolicited **live marketing calls** are permitted unless the subscriber has objected or is registered with the **TPS/CTPS** (opt-out model); special consent rules apply to claims-management and pensions calls (regs. 21A–21B). | [8] |
| PECR reg. 22 | Unsolicited **email/SMS** direct marketing to individuals requires **prior consent**, subject to the **soft opt-in** (reg. 22(3)); DUAA extends the soft opt-in to **charities**. | [9][20] |
| PECR reg. 23 | Prohibits sending marketing email/SMS that **disguises/conceals the sender's identity** or lacks a valid opt-out address. | [10] |
| DUAA 2025 (amending PECR + Sch.) | Raises PECR maximum penalties to **£17.5m / 4%**; inserts a Schedule of **low-risk cookie exemptions**; extends the **soft opt-in** to charities. | [11][18][20] |

## Relevant Recitals

**Not Applicable** as a distinct set. PECR is UK secondary legislation and does not carry recitals; its interpretive background is the **ePrivacy Directive's recitals** (esp. Recitals 24–25 and 40 on device confidentiality and unsolicited communications) and **ICO guidance** [13][15]. The Directive recitals are treated at parent level in `eprivacy-foundations`; the interpretive weight for PECR now rests on the regulations' text, the DUAA amendments, and ICO guidance [15][16].

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Planet49 | CJEU (Grand Chamber), C-673/17, 1 Oct 2019, ECLI:EU:C:2019:801 | A **pre-ticked checkbox** is not valid consent for storing/accessing cookies; the standard applies whether or not the stored information is personal data. | Sets the consent standard applied to PECR reg. 6. As EU case law decided before IP-completion day it is **assimilated case law** — persuasive and followed by the ICO, though UK courts may in principle depart from it [2][14]. |

*No binding UK appellate judgment has redefined PECR cookie consent; the operative UK authority is PECR reg. 6 read with UK GDPR-standard consent and ICO guidance [2][15]. PECR marketing enforcement is litigated mainly as monetary-penalty appeals to the First-tier Tribunal (General Regulatory Chamber); individual penalty cases are fact-specific and are not treated here as precedent.*

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).** The authoritative UK readings are the **ICO Guide to PECR**, the ICO's storage-and-access-technologies guidance and its DUAA change summaries [15][16][17][18].

- **"Consent" means UK GDPR consent.** For both marketing (regs. 19/22) and cookies (reg. 6), the ICO requires **freely given, specific, informed, unambiguous** consent by clear affirmative action; opt-out boxes, silence and "continue to browse" are invalid, consistent with **Planet49** [14][15]. *(Regulatory interpretation of a legal obligation.)*
- **"Strictly necessary" is narrow.** The ICO reads the reg. 6 exemption as covering only what is essential to deliver the service the user asked for (session, security, load-balancing, consent storage); **analytics and advertising are not strictly necessary** and, absent a new exemption, need consent [15][16]. *(Regulatory interpretation.)*
- **New low-risk cookie exemptions are purpose-scoped.** The ICO's storage-and-access guidance explains the DUAA exemptions (service-improvement **statistics**, remembering **preferences**, **security/fraud**, technical delivery, **emergency location**) and stresses they apply only where that is the **sole purpose**; mixed-purpose or profiling tags still require consent, and users must still receive clear information [16][17][20]. *(Regulatory interpretation.)*
- **Soft opt-in is for your own similar products.** The ICO treats reg. 22(3) as available only to the organisation that collected the details **during a sale or its negotiations**, for **similar** products, with a refusal opportunity in every message; it does **not** cover cold prospecting, bought lists, or unrelated third parties [9][15]. *(Regulatory interpretation.)*
- **Charitable-purpose soft opt-in.** The ICO consulted (Oct 2025) on the DUAA charity soft opt-in and guides charities that it applies to people who **previously expressed interest** in the charity's purposes, subject to the same opt-out discipline; it is not a general licence to email all past contacts [20][22]. *(Regulatory interpretation.)*
- **Enforcement posture after the uplift.** On commencement the ICO signalled a supportive-but-watchful approach, but the **£17.5m / 4%** ceiling and the removal of the "substantial damage or distress" hurdle materially raise PECR exposure — especially for nuisance calls, spam SMS and non-compliant cookies [18][19]. *(Regulatory interpretation.)*

# Technical Considerations

- **Consent-before-set gating** — non-essential cookies, SDKs, pixels, local storage and fingerprinting must not fire before a valid consent signal exists; only reg. 6 strictly-necessary and the DUAA low-risk exemptions may load without consent [2][16]. Implementation depth is in `cookie-consent-implementation`. *(Legal obligation.)*
- **Exemption classification engine** — tag each device-access technology to a single purpose and map it to: *strictly necessary* / *DUAA-exempt (which limb)* / *consent-required*; record the rationale, because exemptions are lost the moment a tag also serves advertising or cross-site profiling [16][17]. *(Best practice grounded in obligation.)*
- **Suppression and preference infrastructure** — maintain per-channel consent and opt-out records, a do-not-contact/suppression list, and automated **TPS/CTPS screening** (typically every 28 days) before live-call campaigns [8][15]. *(Legal obligation / best practice.)*
- **Soft opt-in provenance** — capture, per contact, the **source event** (sale/negotiation), the products marketed, and evidence that opt-out was offered at collection and in each message; charities must additionally record the **expression of interest** relied on [9][22]. *(Legal obligation.)*
- **Sender identity and unsubscribe** — every marketing email/SMS must identify the sender and carry a working, free opt-out route (reg. 23); wire unsubscribe to genuine suppression, not just list removal [10][15]. *(Legal obligation.)*
- **Traffic/location data lifecycle** — where the organisation is a communications-service provider, minimise, anonymise or erase traffic data when no longer needed and gate value-added location uses on consent (regs. 7, 14) [4][5]. *(Legal obligation.)*

# Hosting Considerations

- **Server-side and CDN tags still count** — relocating analytics/measurement to a first-party or server-side endpoint does **not** escape reg. 6 where it still reads/writes device information; classify CDN, bot-management and A/B features and gate the non-exempt ones [2][16]. *(Legal obligation.)*
- **Analytics under the new exemption** — first-party statistics collected **solely** to improve the service may now fall within the DUAA low-risk exemption, removing the consent gate for that narrow purpose; configure the analytics stack so it does not also feed advertising/profiling, which would forfeit the exemption [16][17][20]. *(Legal obligation.)*
- **Provider security duty (reg. 5)** — operators of **public** electronic-communications services carry the reg. 5 security and breach-notification duties in addition to UK GDPR Art. 32; most website operators are not PECR "service providers" but should confirm their status [3]. *(Legal obligation — assess role.)*
- **Consent/suppression records as personal data** — logs of consent, opt-outs and TPS screening are personal data; host them securely, retain them to evidence compliance, and make them producible on ICO request [15]. *(Best practice grounded in obligation.)*

# Game Hosting Considerations

- **In-game analytics/ads/attribution SDKs** read device identifiers and fall under reg. 6; they must not initialise before consent unless a DUAA low-risk exemption genuinely applies (e.g. pure service-improvement statistics) — **advertising/attribution SDKs do not qualify** [2][16]. *(Legal obligation.)*
- **Push notifications and promo messages** — in-game/promotional emails, SMS and equivalent electronic messages are direct marketing under reg. 22; use consent or a properly evidenced soft opt-in, with opt-out in every message [9][10]. *(Legal obligation.)*
- **Children** — services likely accessed by children face heightened scrutiny; default non-essential tracking **off**, avoid nudging minors to consent, and align with the Children's Code (see `uk-childrens-code`) [15]. *(Legal obligation / best practice.)*
- **Higher stakes** — the £17.5m / 4% ceiling means unlawful player marketing or cookie practices in a game with a large install base is now a material financial risk, not a capped one [18]. *(Editorial note.)*

# AI Considerations

- **Consent is the collection gate for AI personalisation** — where cookies/SDKs feed recommendation, ad-targeting or churn models, a valid reg. 6 consent is required for the **collection layer**, in addition to a UK GDPR basis for the downstream processing; the DUAA analytics exemption does **not** extend to profiling [2][16]. *(Legal obligation.)*
- **Marketing automation** — AI-driven send-time/audience optimisation does not change the lawful-basis question: each channel still needs consent, soft opt-in or (live calls) TPS-screened opt-out under regs. 19–22 [6][9]. *(Legal obligation.)*
- **Automated nuisance at scale** — AI-generated or auto-dialled campaigns amplify reg. 19/21 exposure; the removal of the "substantial damage or distress" threshold plus the higher ceiling make automated non-compliant outreach especially costly [8][18]. *(Editorial recommendation.)*
- **Cross-reference** — for AI decisions about UK data subjects (ADM safeguards, recognised legitimate interests) see `duaa-2025-detail`; PECR governs the messaging/tracking layer, not the model logic. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

The **channel × consent-basis decision matrix** (individual/consumer subscribers unless noted):

| Channel | PECR reg. | Default basis | Soft opt-in available? | Screening / notes |
|---------|-----------|---------------|------------------------|-------------------|
| Live marketing calls | reg. 21 | **Opt-out** (may call unless objected) | N/A | Screen against **TPS** (individuals) / **CTPS** (corporates); honour prior objections; claims-management & pensions calls need consent (regs. 21A–21B) [8] |
| Automated (recorded) calls | reg. 19 | **Prior consent** (always) | No | Consent must be specific to automated calls [6] |
| Fax | reg. 20 | Individuals: **consent**; corporates: **opt-out** | No | Honour Fax Preference Service objections [7] |
| Email / SMS (and equivalent) | reg. 22 | **Prior consent** | **Yes** (own similar products; charities for charitable purposes) | Opt-out in every message; sender identifiable (reg. 23) [9][10][20] |
| Cookies / device access | reg. 6 | **Consent** | N/A | Exempt only if **strictly necessary** or within a **DUAA low-risk exemption** [2][16] |
| B2B email/SMS to corporate bodies | reg. 22 | Outside reg. 22's individual-subscriber consent rule | N/A | Still subject to reg. 23 identity/opt-out and UK GDPR where individuals are identifiable [10][15] |

1. **Map every marketing channel to its PECR rule and basis** using the matrix; record the lawful basis and evidence per contact. *(OBLIGATION.)* [6][7][8][9]
2. **Obtain GDPR-standard consent** for automated calls, fax-to-individuals and email/SMS, unless a valid soft opt-in applies. *(OBLIGATION.)* [6][9][15]
3. **Operate the soft opt-in strictly** — own similar products, details obtained in a sale/negotiation, opt-out at collection and in every message; charities: rely on a recorded expression of interest in the charitable purpose. *(OBLIGATION.)* [9][20][22]
4. **Screen live calls against TPS/CTPS** and suppress prior objectors before every campaign. *(OBLIGATION.)* [8]
5. **Gate cookies consent-before-set**; classify each device-access technology as strictly necessary, DUAA-exempt (name the limb) or consent-required, and document it. *(OBLIGATION.)* [2][16][17]
6. **Do not over-claim the new exemptions** — keep analytics single-purpose and away from advertising/profiling; retain the consent gate for anything that tracks or targets. *(OBLIGATION.)* [16][17]
7. **Ensure sender identity and a working opt-out** in every electronic message (reg. 23), wired to genuine suppression. *(OBLIGATION.)* [10]
8. **Re-price PECR risk** internally to the £17.5m / 4% ceiling and brief marketing/leadership on the removed "damage or distress" threshold. *(BEST PRACTICE.)* [18]
9. **Track commencement and ICO guidance** — the main changes are in force (5 Feb 2026); monitor the ICO's finalised charity soft opt-in and storage-and-access guidance. *(EDITORIAL RECOMMENDATION.)* [17][19][22]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Sending email/SMS marketing without consent or a valid soft opt-in | High | High | reg. 22 [9]; £17.5m ceiling [18] | Consent capture; strict soft-opt-in provenance; suppression | Low |
| R2 | Live calls to TPS/CTPS-registered or objecting subscribers | High | High | reg. 21 [8] | 28-day TPS/CTPS screening; objection suppression | Low |
| R3 | Automated (recorded) calls without specific consent | Medium | High | reg. 19 [6] | Consent gate specific to automated calls | Low |
| R4 | Non-essential cookies/SDKs firing before consent | High | High | reg. 6 [2]; Planet49 [14] | Consent-before-set; tag gating; audits | Low |
| R5 | Over-claiming DUAA low-risk exemptions for analytics that also profile/advertise | Medium | High | reg. 6 Sch. [16][17] | Single-purpose analytics; documented classification | Medium |
| R6 | Charity soft opt-in used beyond "expressed interest" / for unrelated contacts | Medium | Medium | reg. 22 as amended [20][22] | Record expressions of interest; scope to charitable purpose | Low |
| R7 | Missing sender identity or broken opt-out in messages | Medium | Medium | reg. 23 [10] | Identity + working unsubscribe wired to suppression | Low |
| R8 | Provider security/breach duties overlooked (reg. 5) | Low | Medium | reg. 5 [3] | Confirm provider status; security + breach-notification controls | Low |
| R9 | Treating the DUAA PECR changes as "future" when in force since 5 Feb 2026 | Medium | High | SI 2026/82 [12][19] | Re-baseline compliance to amended PECR | Low |

# Implementation Roadmap

- **Phase 0 — Channel & tracker inventory:** Enumerate every marketing channel and every device-access technology; assign PECR rule and basis. *Effort:* Medium.
- **Phase 1 — Marketing bases:** Implement consent capture; codify soft-opt-in provenance (incl. charity expressions of interest); wire TPS/CTPS screening and suppression. *Effort:* Medium.
- **Phase 2 — Cookie gating & exemptions:** Enforce consent-before-set; classify tags against strictly-necessary and the DUAA exemptions; document rationales. *Effort:* Medium–High.
- **Phase 3 — Message hygiene:** Sender identity and working opt-outs (reg. 23) across all electronic messaging, wired to genuine suppression. *Effort:* Low–Medium.
- **Phase 4 — Enforcement re-pricing & governance:** Update risk registers/policies to the £17.5m/4% ceiling; brief teams; add a PECR commencement/guidance watch-list. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Marketing sent without documented basis; cookies fire on load; unaware of DUAA changes. | No inventory; opt-out-only consent. |
| 2 | Managed | Some consent capture and a cookie banner; ad hoc TPS screening. | Partial inventory; buried reject. |
| 3 | Defined | Per-channel basis mapped; soft-opt-in provenance recorded; consent-before-set; tags classified against exemptions. | Decision matrix in use; documented classifications. |
| 4 | Quantitatively Managed | Metrics on consent rates, suppression, TPS screening and tag compliance; periodic PECR audits. | KPIs; automated screening; audit trail. |
| 5 | Optimising | Automated tag governance and suppression; charity/soft-opt-in controls; proactive guidance/commencement tracking. | Enforcing tag manager; evidence-ready records. |

# Audit Questions

1. For each marketing channel, what is the PECR rule and lawful basis, and where is the per-contact evidence held? *(regs. 19–22 [6][7][8][9].)*
2. Where you rely on the **soft opt-in**, can you show own-similar-products, a sale/negotiation source, and opt-out at collection and in every message? *(reg. 22(3) [9][15].)*
3. If you use the **charity** soft opt-in, how do you record the recipient's prior expression of interest in your charitable purpose? *([20][22].)*
4. How are **live calls** screened against TPS/CTPS and prior objections before each campaign? *(reg. 21 [8].)*
5. Are non-essential cookies/SDKs blocked until consent, and is each device-access technology classified as strictly necessary, DUAA-exempt (which limb) or consent-required? *(reg. 6 [2][16].)*
6. For any tag relying on a DUAA low-risk exemption, how do you ensure it is single-purpose and not also profiling/advertising? *([16][17].)*
7. Does every marketing message identify the sender and carry a working, free opt-out wired to suppression? *(reg. 23 [10].)*
8. Have your risk registers, policies and training been updated to the **£17.5m / 4%** PECR ceiling and the removed "damage or distress" threshold? *([18][19].)*

# Implementation Checklist

- [ ] Complete inventory of marketing channels and device-access technologies, each mapped to its PECR rule and basis.
- [ ] GDPR-standard consent captured for automated calls, fax-to-individuals and email/SMS (where soft opt-in does not apply).
- [ ] Soft-opt-in provenance recorded (own similar products; sale/negotiation source; opt-out at collection and each message).
- [ ] Charity soft opt-in scoped to recorded expressions of interest in the charitable purpose.
- [ ] TPS/CTPS screening (≈28-day) and objection suppression run before every live-call campaign.
- [ ] Consent-before-set enforced; tags classified strictly-necessary / DUAA-exempt (limb named) / consent-required, with rationale.
- [ ] DUAA low-risk exemptions used only for single-purpose, non-profiling tags.
- [ ] Sender identity and working, free opt-out in every electronic marketing message (reg. 23), wired to genuine suppression.
- [ ] Traffic/location-data minimisation and consent controls applied where the organisation is a communications-service provider.
- [ ] Risk registers, policies and training updated to the £17.5m / 4% ceiling; PECR commencement/guidance watch-list maintained.

# References

*All links verified live on 2026-07-11 (`sources_verified`) with HTTP 200. Classification per `SOURCE_REGISTRY.md`.*

## Primary Sources

- [1] **Privacy and Electronic Communications (EC Directive) Regulations 2003 (PECR)**, SI 2003/2426 — contents. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/contents
- [2] **PECR reg. 6** (confidentiality of communications — storing/accessing information on terminal equipment; cookies). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/6
- [3] **PECR reg. 5** (security of public electronic-communications services). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/5
- [4] **PECR reg. 7** (restrictions on the processing of traffic data). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/7
- [5] **PECR reg. 14** (location data other than traffic data). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/14
- [6] **PECR reg. 19** (automated calling systems — recorded-message marketing calls). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/19
- [7] **PECR reg. 20** (use of fax for direct marketing). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/20
- [8] **PECR reg. 21** (unsolicited live marketing calls; TPS/CTPS). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/21
- [9] **PECR reg. 22** (unsolicited email/SMS direct marketing; soft opt-in). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/22
- [10] **PECR reg. 23** (prohibition on disguising sender identity; valid opt-out address). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/regulation/23
- [11] **Data (Use and Access) Act 2025 (c.18)**, contents (amends PECR; Royal Assent 19 June 2025). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/contents
- [12] **The Data (Use and Access) Act 2025 (Commencement No. 6 and Transitional and Saving Provisions) Regulations 2026 (SI 2026/82)** — brings the main PECR changes into force on 5 February 2026. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2026/82/contents/made
- [13] **Directive 2002/58/EC (ePrivacy Directive), consolidated text** (as amended by 2009/136/EC) — the instrument PECR transposes. EUR-Lex, CELEX 02002L0058-20091219. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219
- [14] **Planet49 (Verbraucherzentrale Bundesverband v Planet49 GmbH)**, CJEU, C-673/17, ECLI:EU:C:2019:801 (pre-ticked box not valid cookie consent). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:62017CJ0673

## Regulatory Guidance

- [15] **Guide to PECR** (marketing, cookies, security, penalties). Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/
- [16] **Guide to PECR — Exemptions** (strictly-necessary and DUAA low-risk cookie exemptions). ICO. https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/exemptions/
- [17] **Guidance on the use of storage and access technologies** (updated for the DUAA cookie exemptions). ICO. https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guidance-on-the-use-of-storage-and-access-technologies/
- [18] **The Data (Use and Access) Act 2025 — DUAA summary of the changes: privacy and electronic communications** (PECR enforcement uplift to £17.5m/4%; cookie exemptions; charity soft opt-in). ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/the-data-use-and-access-act-2025-duaa-summary-of-the-changes/privacy-and-electronic-communications/
- [19] **Statement on the commencement of the Data (Use and Access) Act (DUAA)** (5 February 2026; enforcement approach; complaints duty 19 June 2026). ICO. https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/02/statement-on-the-commencement-of-the-data-use-and-access-act-duaa/
- [20] **Data (Use and Access) Act factsheet: PEC Regulations** (cookie exemptions; charity soft opt-in; staged commencement). GOV.UK / DSIT. https://www.gov.uk/government/publications/data-use-and-access-act-2025-factsheets/data-use-and-access-act-factsheet-pec-regulations
- [21] **Data (Use and Access) Act 2025: data protection and privacy changes** (overview incl. low-risk storage/access without explicit consent). GOV.UK. https://www.gov.uk/guidance/data-use-and-access-act-2025-data-protection-and-privacy-changes
- [22] **Consultation on new "charitable purpose soft opt-in" rules to support fundraising** (October 2025). ICO. https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2025/10/consultation-on-new-charitable-purpose-soft-opt-in-rules-to-support-fundraising/

## Standards

**Not Applicable** — there is no ISO/IEC/NIST/OWASP standard specific to PECR. General privacy/security standards (ISO/IEC 27001, 27701) apply to the underlying processing as under the UK GDPR (see `privacy-engineering-foundations`); consent-signal industry specifications (IAB TCF) are treated in `cookie-consent-implementation`.

## Academic Sources

**Not Applicable** — this sub-topic relies on primary legislation (PECR, DUAA) and ICO/GOV.UK guidance. Empirical consent-UX literature is cited in `cookie-consent-implementation` (Nouwens et al., CHI 2020).

# Further Reading

*Non-authoritative; provided for orientation only.*

- ICO — Electronic and telephone marketing (within the Guide to PECR). https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/electronic-and-telephone-marketing/
- ICO — Guidance on direct marketing using electronic mail (PECR electronic-mail rules). https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guidance-on-direct-marketing-using-electronic-mail/
- Telephone Preference Service (TPS) — registration and screening. https://www.tpsonline.org.uk/

# Related Documents

- `eprivacy-foundations` — **parent**; ePrivacy Directive and PECR as its UK transposition (**prerequisite reading**).
- `cookie-consent-implementation` — cookie banner/CMP design, "consent or pay", IAB TCF, dark patterns (reg. 6 depth).
- `duaa-2025-detail` — the DUAA reforms end-to-end (RLI, ADM, transfers, Information Commission; PECR changes cross-referenced).
- `uk-gdpr-foundations` — UK GDPR context and the meaning/conditions of consent.
- `digital-omnibus` — EU proposal to migrate the cookie rule into the GDPR (EU-side; does not bind PECR).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against legislation.gov.uk (PECR SI 2003/2426 regs. 5–23; DUAA c.18; SI 2026/82), the ePrivacy Directive consolidated text, Planet49, and ICO/GOV.UK guidance. **DUAA-PECR changes live-verified: PECR penalty ceiling raised to £17.5m/4% (removing the "substantial damage or distress" threshold); new low-risk cookie-consent exemptions inserted by a new PECR Schedule; soft opt-in extended to charities — all commencing 5 February 2026 (SI 2026/82); complaints duty 19 June 2026.** | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster B); full-repo validator/link/lint suite green; frozen in release 0.16.0. | Orchestrator (QA-verified) |
