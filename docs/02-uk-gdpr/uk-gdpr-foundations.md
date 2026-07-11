---
id: uk-gdpr-foundations
title: "UK GDPR: Foundations & Divergence from the EU GDPR"
version: 1.0.1
status: approved
classification: public
jurisdiction: [UK]
topic: UK GDPR
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-10
updated: 2026-07-10
review_due: 2027-07-10
confidence: High
supersedes: Not Applicable
related: [gdpr-foundations, eprivacy-foundations, privacy-engineering-foundations]
tags: [uk-gdpr, dpa-2018, duaa-2025, brexit, adequacy, ico, data-protection]
legal_basis: UK GDPR; Data Protection Act 2018; Data (Use and Access) Act 2025
sources_verified: 2026-07-10
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | uk-gdpr-foundations |
| Version | 1.0.1 |
| Status | approved (frozen in release 0.10.1) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-10 |
| Last Updated | 2026-07-10 |
| Review Due | 2027-07-10 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-10 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. UK data protection law is undergoing phased reform under the Data (Use and Access) Act 2025; confirm the commencement status of specific provisions before relying on them.

# Executive Summary

The **UK GDPR** is the United Kingdom's post-Brexit version of Regulation (EU) 2016/679. It was created by retaining the EU GDPR in domestic law under **section 3 of the European Union (Withdrawal) Act 2018** and amending it (via the "DPPEC" EU-Exit Regulations 2019) so it operates in a UK-only context from 1 January 2021 [1][6]. It works **alongside the Data Protection Act 2018 (DPA 2018)**, which supplements it with exemptions, special-category conditions, law-enforcement and intelligence-services regimes, and the powers of the regulator [2][6].

This document assumes familiarity with `gdpr-foundations`; rather than restate the principles and lawful bases, it focuses on **what is different in the UK**: the constitutional basis, the UK GDPR/DPA 2018 division of labour, the key substantive divergences (notably the age of consent for online services, set at **13** by DPA 2018 s.9), the reforms introduced by the **Data (Use and Access) Act 2025 (DUAA, c.18)**, and the **EU adequacy** position that permits EEA→UK data flows [3][4][9].

Three conclusions dominate. First, the UK framework is *substantially aligned* with the EU GDPR but is now **actively diverging** through the DUAA, which amends — but does not replace — the UK GDPR, DPA 2018 and PECR [7][8]. Second, **adequacy is secured**: the European Commission renewed its UK adequacy decisions on 19 December 2025, valid until 27 December 2031, having assessed the DUAA reforms [9]. Third, organisations operating in both the EU and UK must now track **two diverging rulebooks** rather than one.

# Key Takeaways

- The UK GDPR is retained/assimilated EU law under **EUWA 2018 s.3**, operable domestically from 1 January 2021, and sits alongside the **DPA 2018** [1][2][6]. *(Legal obligation.)*
- The **DPA 2018 supplements** the UK GDPR (exemptions, Art. 9 conditions, law-enforcement and intelligence regimes, ICO powers) — the two must be read together [2][6]. *(Legal obligation.)*
- The **age at which a child can consent** to an information-society service is **13** in the UK (DPA 2018 s.9 modifying Art. 8(1)), versus the EU default of 16 [3]. *(Legal obligation.)*
- The **Data (Use and Access) Act 2025 (c.18)** received Royal Assent on **19 June 2025** and is being **phased in between June 2025 and June 2026**; it amends the UK GDPR, DPA 2018 and PECR [4][7][8]. *(Legal obligation.)*
- The DUAA introduces a new **"recognised legitimate interests"** lawful basis for specified public-interest purposes, liberalises **automated decision-making**, clarifies **scientific research**, adds duties on **children's online services** and **complaints handling**, and reconstitutes the regulator as the **Information Commission** with a new strategic framework [7][8]. *(Legal obligation / regulatory interpretation.)*
- **EU adequacy** for the UK, first granted on **28 June 2021** [10], was **renewed on 19 December 2025 to run to 27 December 2031**, following a technical extension in June 2025 — this keeps EEA→UK transfers free of additional safeguards [9][11]. *(Regulatory / legal.)*
- The **ICO** (transitioning to the Information Commission) is the UK supervisory authority; UK-based controllers deal with the ICO, not EU authorities [6][7]. *(Legal obligation.)*
- Organisations subject to **both** regimes must manage **divergence**: the cores align, but consent age, ADM, recognised legitimate interests and future reforms differ. *(Editorial recommendation.)*

# Purpose

This document is the UK entry point to the data-protection topic area. It supports legal research (mapping the UK instruments and their interaction), compliance implementation (what UK-specific obligations differ from the EU baseline), and cross-border programme design (managing EU/UK divergence). It deliberately builds on, and does not duplicate, `gdpr-foundations`.

# Scope

**In scope:** How the UK GDPR was created and its constitutional basis; the UK GDPR/DPA 2018 relationship; the principal substantive divergences from the EU GDPR; the DUAA 2025 reforms at a foundational level; the ICO/Information Commission; the EU adequacy position.

**Out of scope (spun off to the research backlog):** UK international transfers mechanics (IDTA and the UK Addendum to EU SCCs) → `uk-transfers`; the DUAA 2025 in depth → `duaa-2025-detail`; UK PECR / ePrivacy → `eprivacy-uk`; the ICO Age-Appropriate Design (Children's) Code → `uk-childrens-code`; law-enforcement processing (DPA 2018 Part 3) → `uk-le-processing`.

**Assumptions:** The reader has read `gdpr-foundations`. Principles (Art. 5) and lawful bases (Art. 6) carry over to the UK GDPR except where noted here.

# Definitions

*Shared terms (personal data, controller, processor, consent, special-category data, supervisory authority) are defined in `GLOSSARY.md` and carry over to the UK GDPR. Only UK-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| UK GDPR | Regulation (EU) 2016/679 as retained/assimilated in UK domestic law under EUWA 2018 s.3 and amended for the UK context. | [1][5][6] |
| DPA 2018 | Data Protection Act 2018 — the UK Act that supplements the UK GDPR and implements the law-enforcement and intelligence-services regimes. | [2] |
| DUAA / DUAA 2025 | Data (Use and Access) Act 2025 (c.18), which amends the UK GDPR, DPA 2018 and PECR. | [4] |
| Assimilated law | The status (from 1 January 2024) of what was formerly "retained EU law", including the UK GDPR, following the Retained EU Law (Revocation and Reform) Act 2023. | [1] |
| Adequacy decision | A European Commission finding that a third country ensures an adequate level of data protection, permitting EEA→that-country transfers without further safeguards. | [9][11] |
| Information Commission | The reconstituted UK data-protection regulator under the DUAA, succeeding the Information Commissioner's Office (ICO). | [7] |

# Background

When the UK left the EU, the EU GDPR ceased to apply directly. To avoid a legal vacuum, the **European Union (Withdrawal) Act 2018** retained the GDPR in UK law [1]. The **Data Protection, Privacy and Electronic Communications (Amendments etc.) (EU Exit) Regulations 2019** ("DPPEC Regulations") then amended the retained text and the DPA 2018 so the framework functions domestically — for example, replacing EU institutions and cross-border mechanisms with UK equivalents [6]. From **1 January 2021** the UK operated the "UK GDPR" plus the DPA 2018 [6]. Following the Retained EU Law (Revocation and Reform) Act 2023, "retained EU law" was renamed **"assimilated law"** from 1 January 2024; the UK GDPR is assimilated direct legislation [1].

The UK has since pursued its own reform agenda. After earlier proposals lapsed, the **Data (Use and Access) Act 2025** reached Royal Assent on 19 June 2025 and is being commenced in stages to June 2026 [4][8].

# Legal Framework

The UK data-protection framework has three principal statutory pillars, read together:

1. **UK GDPR** — the retained/assimilated Regulation, carrying the principles (Art. 5), lawful bases (Art. 6), data-subject rights, controller/processor obligations and transfer rules, adapted for the UK [1][6].
2. **DPA 2018** — supplements the UK GDPR (Part 2), and separately governs law-enforcement processing (Part 3) and the intelligence services (Part 4); it also constitutes the regulator and its enforcement powers [2].
3. **DUAA 2025** — amends the above (and PECR), introducing targeted reforms rather than a new regime [4][7][8].

Because the UK GDPR's article numbering mirrors the EU GDPR, the `gdpr-foundations` article map applies in the UK **except** where the DPA 2018 or DUAA modifies it. The principal foundational modifications are set out below.

## Relevant Articles

| Provision | Effect in the UK | Source |
|-----------|------------------|--------|
| UK GDPR Art. 5–6 | Principles and lawful bases carry over from the EU GDPR (see `gdpr-foundations`). | [1] |
| UK GDPR Art. 8(1) (as modified) | Age of consent for information-society services reduced from 16 to **13**. | [3] |
| DPA 2018 s.9 | Modifies Art. 8(1) to set the 13-year threshold; disapplies for online preventive/counselling services. | [3] |
| DPA 2018 Sch. 1–4 | Conditions for special-category/criminal-offence data and exemptions. | [2] |
| DPA 2018 Part 3 | Law-enforcement processing regime (separate from UK GDPR). | [2] |
| UK GDPR Art. 6 (new basis) | DUAA adds a **"recognised legitimate interests"** basis for listed public-interest purposes (no balancing test for those purposes). | [4][7][8] |
| UK GDPR Art. 22 (as amended) | DUAA provides a more permissive framework for solely automated decisions with legal/similar effect, subject to safeguards. | [7][8] |

## Relevant Recitals

*The UK GDPR retains recitals as interpretive aids; see `gdpr-foundations` for the core recitals (26, 32, 39, 47). No UK-specific recitals are added, but DUAA provisions are construed against the Act's own provisions and explanatory materials rather than EU recitals.* Not Applicable (no distinct UK recitals). [1]

## Relevant Case Law

*EU case law decided before 31 December 2020 (e.g., Google Spain, Breyer, Nowak) is "retained/assimilated case law" and remains persuasive/binding on lower UK courts, subject to UK courts' power to depart. Post-2020 CJEU decisions are not binding in the UK.* [1]

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Retained pre-2021 CJEU case law | Various (see `gdpr-foundations`) | Interpretations of GDPR concepts (personal data, processing) carried into UK law. | Baseline construction of UK GDPR terms [1]. |
| *(UK-specific foundational case law)* | — | To be added in sub-topic documents as it develops. | Not Applicable at foundational level. |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).** The **ICO** publishes the authoritative UK guidance (Guide to the UK GDPR, plus DUAA-specific guidance and consultations) [6][7]. Key foundational positions:

- The UK GDPR and DPA 2018 **must be read together**; the ICO frames the DPA 2018 as supplementing the UK GDPR (e.g., exemptions, Art. 9 conditions) [6]. *(Regulatory interpretation.)*
- The DUAA **amends, and does not replace**, existing law; organisations already compliant with the UK GDPR have a foundation to build on, but must adjust for the new provisions as they commence [7][8]. *(Regulatory interpretation.)*
- The DUAA adds duties to **help complainants** (e.g., an electronic complaints route; acknowledge within 30 days; respond without undue delay) and to consider **children's needs** when designing online services likely to be used by children [7][8]. *(Legal obligation, per ICO summary.)*
- The regulator is being reconstituted as the **Information Commission** with a new strategic framework (a principal objective plus regard to innovation, competition and children's protection) [7]. *(Regulatory interpretation.)*

# Technical Considerations

- **Dual-regime configuration** — systems serving both EU and UK users should be able to apply the correct rules per data subject's jurisdiction (e.g., 13 vs 16 consent age; ADM safeguards; recognised legitimate interests). *(Best practice.)*
- **Consent-age gating** — UK information-society services relying on a child's consent must gate at 13 and verify parental responsibility for under-13s (DPA 2018 s.9) [3]. *(Legal obligation.)*
- **ADM safeguards** — where relying on the DUAA's more permissive automated-decision framework, implement the required safeguards (information, human intervention, contestation) [7][8]. *(Legal obligation.)*
- **Records & lawful-basis mapping** — add "recognised legitimate interests" as a distinct basis in the processing register where used, and document the qualifying purpose [7][8]. *(Best practice grounded in obligation.)*
- Core security and privacy-by-design expectations mirror the EU GDPR (Arts. 25, 32) — see `gdpr-foundations` and `privacy-engineering-foundations`.

# Hosting Considerations

- **Controller/processor split and Art. 28 contracts** operate as under the EU GDPR (see `gdpr-foundations`).
- **EEA→UK transfers** are permitted without additional safeguards while EU **adequacy** subsists (renewed to 27 December 2031) [9][11]. *(Legal.)*
- **UK→third-country transfers** use UK mechanisms (UK adequacy regulations, the International Data Transfer Agreement (IDTA), or the UK Addendum to the EU SCCs) — covered in `uk-transfers` (backlog). *(Legal obligation; cross-reference.)*
- Hosting providers to UK controllers are typically **processors** requiring DPA-compliant contracts and, where relevant, UK-appropriate transfer terms. *(Editorial recommendation: keep an EU/UK transfer matrix.)*

# Game Hosting Considerations

- **Children's data** is acute for games: the UK consent age is **13** (DPA 2018 s.9) and the **ICO Children's Code (Age-Appropriate Design Code)** imposes design expectations for services likely to be accessed by children; the DUAA adds a duty to consider children's needs [3][7][8]. Multi-territory games must reconcile the UK's 13 with EU thresholds of 13–16. *(Legal obligation.)*
- **Player identifiers, telemetry and anti-cheat** are personal data as under the EU GDPR (see `gdpr-foundations`); minimisation and retention apply.
- Detailed children's-code obligations are covered in `uk-childrens-code` (backlog). *(Cross-reference.)*

# AI Considerations

- **Automated decision-making** — the DUAA's more permissive Art. 22 framework is directly relevant to AI systems making consequential decisions about UK data subjects; the liberalisation is conditional on safeguards, and diverges from the stricter EU position [7][8]. *(Legal obligation; divergence risk.)*
- **Scientific research** — the DUAA clarifies when personal data may be used for scientific research, including commercial research, which affects AI/ML training on UK data [7][8]. *(Legal obligation / interpretation.)*
- **Recognised legitimate interests** may support certain public-interest data uses relevant to AI (e.g., safeguarding), without the full balancing test for listed purposes [7][8]. *(Regulatory interpretation.)*
- The UK has **no equivalent to the EU AI Act** at the time of writing; UK AI governance is principles-based and sector-led — see `ai-governance-foundations` (backlog). *(Editorial note.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Read UK GDPR + DPA 2018 together**; do not rely on the UK GDPR text alone for exemptions and Art. 9 conditions. *(OBLIGATION.)* [2][6]
2. **Track DUAA commencement** — maintain a watch-list of which provisions are in force, as the phase-in runs to June 2026. *(BEST PRACTICE.)* [8]
3. **Gate children's consent at 13** for UK information-society services and verify parental responsibility for under-13s. *(OBLIGATION.)* [3]
4. **Map lawful bases including "recognised legitimate interests"** where used, and document the qualifying purpose. *(OBLIGATION + BEST PRACTICE.)* [7][8]
5. **Stand up a complaints process** (electronic route; 30-day acknowledgement; timely response) as DUAA provisions commence. *(OBLIGATION.)* [7][8]
6. **Maintain an EU/UK divergence register** if you operate in both jurisdictions. *(EDITORIAL RECOMMENDATION.)*
7. **Monitor adequacy** — although renewed to 2031, adequacy is periodically reviewed; keep a contingency plan for EEA→UK transfers. *(EDITORIAL RECOMMENDATION.)* [9]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Applying EU 16 consent age (not UK 13) or vice versa | Medium | Medium | DPA 2018 s.9 [3] | Jurisdiction-aware consent gating | Low |
| R2 | Missing a DUAA provision as it commences | High | Medium | DUAA phase-in [8] | Commencement watch-list; periodic legal review | Medium |
| R3 | Relying on liberalised ADM without required safeguards | Medium | High | UK GDPR Art. 22 as amended [7][8] | Implement information/intervention/contestation safeguards | Low |
| R4 | Misusing "recognised legitimate interests" beyond listed purposes | Medium | High | DUAA new basis [7][8] | Restrict to qualifying purposes; document | Low |
| R5 | Assuming EU/UK law is identical | Medium | Medium | Divergence via DUAA [7] | Divergence register; dual guidance | Low |
| R6 | Adequacy lapse disrupting EEA→UK flows | Low | High | EU adequacy review cycle [9][11] | Contingency SCCs/IDTA; monitor reviews | Medium |
| R7 | Non-compliant complaints handling | Medium | Medium | DUAA complaints duties [7][8] | Electronic complaints route; 30-day SLA | Low |

# Implementation Roadmap

- **Phase 0 — Baseline:** Confirm UK GDPR + DPA 2018 compliance (build on `gdpr-foundations`). *Effort:* Medium.
- **Phase 1 — Divergence mapping:** Identify UK-specific obligations (consent age, exemptions) and stand up an EU/UK divergence register. *Effort:* Medium.
- **Phase 2 — DUAA readiness:** Track commencement; implement recognised-legitimate-interests mapping, ADM safeguards, complaints process, children's-service duties. *Effort:* Medium–High.
- **Phase 3 — Transfers:** Configure UK transfer mechanisms (IDTA/Addendum) for UK→third-country flows; confirm EEA→UK adequacy reliance. *Effort:* Medium.
- **Phase 4 — Assurance:** Update DPIAs, records and training for the UK context; monitor adequacy and reform. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Treats UK law as identical to EU; no UK-specific controls. | No divergence awareness. |
| 2 | Managed | UK GDPR + DPA 2018 acknowledged; consent age handled. | Basic UK mapping. |
| 3 | Defined | Divergence register; DUAA watch-list; UK transfer mechanisms in place. | Documented UK processes. |
| 4 | Quantitatively Managed | Metrics on complaints SLAs, ADM safeguards, DUAA adoption. | KPIs; periodic legal review. |
| 5 | Optimising | Automated jurisdiction-aware controls; proactive reform tracking. | Dual EU/UK controls; contingency plans tested. |

# Audit Questions

1. Do your policies reference both the UK GDPR **and** the DPA 2018, and are exemptions correctly sourced? *(DPA 2018 [2].)*
2. How do UK information-society services gate children's consent at 13 and verify parental responsibility? *(DPA 2018 s.9 [3].)*
3. Which DUAA provisions are in force, and how have you adjusted for them? *(DUAA [4][8].)*
4. Where "recognised legitimate interests" is relied on, is the purpose within the listed categories and documented? *(DUAA [7][8].)*
5. If you make solely automated decisions with significant effect, what safeguards are in place? *(UK GDPR Art. 22 as amended [7][8].)*
6. What is your complaints-handling process (electronic route, 30-day acknowledgement)? *(DUAA [7][8].)*
7. For UK→third-country transfers, which mechanism applies (UK adequacy/IDTA/Addendum)? *(cross-ref `uk-transfers`.)*
8. Do you monitor the EU→UK adequacy position and hold a contingency plan? *(Adequacy [9][11].)*

# Implementation Checklist

- [ ] Policies and records reference the UK GDPR and DPA 2018 (read together).
- [ ] Children's-consent gating set to 13 with parental-responsibility verification (DPA 2018 s.9).
- [ ] DUAA commencement watch-list maintained.
- [ ] "Recognised legitimate interests" basis mapped where used, with qualifying purpose documented.
- [ ] Automated-decision safeguards implemented where the DUAA framework is relied on.
- [ ] Complaints process (electronic route, 30-day acknowledgement) in place.
- [ ] EU/UK divergence register maintained (if operating in both).
- [ ] UK transfer mechanisms (IDTA/Addendum) configured for UK→third-country flows.
- [ ] EEA→UK adequacy reliance confirmed; contingency plan documented.

# References

*All links verified live on 2026-07-10 (`sources_verified`).*

## Primary Sources

- [1] **European Union (Withdrawal) Act 2018, s.3** (retention of direct EU legislation). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/16/section/3
- [2] **Data Protection Act 2018 (c.12)**, contents. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/contents
- [3] **Data Protection Act 2018, s.9** (child's consent — information-society services; 13-year threshold). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/9
- [4] **Data (Use and Access) Act 2025 (c.18)**, contents. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/contents
- [5] **Regulation (EU) 2016/679 (EU GDPR)**, consolidated text (base instrument for the UK GDPR). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504

## Regulatory Guidance

- [6] **Overview — Data Protection and the EU.** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/data-protection-and-the-eu/overview-data-protection-and-the-eu/
- [7] **Data (Use and Access) Act 2025 — what it means for organisations.** ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/
- [8] **Data (Use and Access) Act 2025: data protection and privacy changes.** GOV.UK. https://www.gov.uk/guidance/data-use-and-access-act-2025-data-protection-and-privacy-changes
- [9] **Commission renews decisions to allow the free and safe flow of personal data with the UK** (IP/25/3059, 19 December 2025). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_3059
- [10] **Data protection: Commission adopts adequacy decisions for the UK** (IP/21/3183, 28 June 2021). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_21_3183
- [11] **Adequacy decisions** (international dimension of data protection). European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/adequacy-decisions_en

## Standards

*As per `gdpr-foundations` — ISO/IEC 27001:2022 and ISO/IEC 27701 apply equally to UK processing. No UK-specific standards are introduced at the foundational level.* Not Applicable (no distinct UK standards).

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation and regulatory guidance. Academic analysis of UK/EU divergence will be cited in sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- GOV.UK — Data protection: the UK's data protection legislation. https://www.gov.uk/data-protection
- GOV.UK — Data (Use and Access) Act 2025 (collection). https://www.gov.uk/government/collections/data-use-and-access-act-2025

# Related Documents

- `gdpr-foundations` — EU GDPR foundations (the base instrument; **prerequisite reading**).
- `uk-transfers` — UK international transfers (IDTA / UK Addendum) (planned).
- `duaa-2025-detail` — Data (Use and Access) Act 2025 in depth (planned).
- `uk-childrens-code` — ICO Age-Appropriate Design Code (planned).
- `eprivacy-uk` — UK PECR / ePrivacy (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-10 | Technical Writer (virtual agent) | Initial draft; researched against legislation.gov.uk (EUWA 2018, DPA 2018, DUAA 2025), ICO, GOV.UK and European Commission adequacy sources. | — |
| 1.0.0 | 2026-07-10 | Editorial Reviewer (virtual agent) | Approved at human review gate; frozen in release 0.3.0. | Human reviewer |
| 1.0.1 | 2026-07-11 | Repository Maintainer (virtual agent) | Citation-hygiene patch (surfaced by `scripts/validate.py`): added in-text citations for refs [5] (base GDPR) and [10] (2021 adequacy decision), previously listed but uncited. No substantive change. | Human reviewer |
