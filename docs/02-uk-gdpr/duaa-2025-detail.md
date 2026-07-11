---
id: duaa-2025-detail
title: "Data (Use and Access) Act 2025: Detailed Analysis"
version: 1.0.0
status: approved
classification: public
jurisdiction: [UK]
topic: UK GDPR
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [uk-gdpr-foundations, gdpr-foundations, eprivacy-uk, uk-childrens-code, uk-transfers]
tags: [duaa-2025, uk-gdpr, dpa-2018, pecr, recognised-legitimate-interests, automated-decision-making, information-commission, commencement]
legal_basis: Data (Use and Access) Act 2025 (c.18); UK GDPR; Data Protection Act 2018; PECR (SI 2003/2426)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | duaa-2025-detail |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.10.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The Data (Use and Access) Act 2025 is being **commenced in stages**; several provisions came into force on **5 February 2026**, the complaints-handling duty is scheduled for **19 June 2026**, and some governance provisions follow later. Confirm the in-force status of any specific provision before relying on it [1][3][9].

# Executive Summary

The **Data (Use and Access) Act 2025 (c.18)** ("DUAA") is the UK's first substantive reform of its post-Brexit data-protection framework. It received **Royal Assent on 19 June 2025** and does **not replace** the UK GDPR, the Data Protection Act 2018 (DPA 2018) or the Privacy and Electronic Communications Regulations (PECR); it **amends** them through targeted, mostly permission-widening changes [1][10]. This deep-dive details the DUAA material introduced at foundational level in `uk-gdpr-foundations`, going provision-by-provision rather than restating the overview.

The reforms most relevant to controllers are: a new **"recognised legitimate interests"** lawful basis for a closed list of public-interest purposes that carries **no balancing test** [10][13][15]; a rebuilt **automated decision-making** regime (new UK GDPR Articles 22A–22D via s.80) that lifts the general prohibition for non-special-category data but mandates safeguards [2][10]; clarified **scientific-research** provisions (including a workable "broad consent") [10][13]; a statutory **complaints-handling** duty on controllers (electronic route, 30-day acknowledgement) [10][12]; a duty to consider **children's higher protection** in service design [12][13]; a recast **international-transfers** "data protection test" ("not materially lower") [10][13]; **PECR** changes (cookie-consent exemptions, extended soft opt-in, and maximum fines raised from £500,000 to **£17.5m / 4% of turnover**) [10][13][16]; and reconstitution of the ICO as the **Information Commission** [9][11].

Three conclusions dominate. First, **most data-protection provisions are already live** (5 February 2026), so this is operational law, not a future project [3][9][14]. Second, the reforms **increase UK–EU divergence** while the Commission has **renewed UK adequacy to 27 December 2031** having assessed the DUAA [17]. Third, the changes are **enabling, not deregulatory in substance** — the new freedoms are conditional on documented safeguards, and the ICO has signalled a supportive-but-watchful enforcement posture [14].

# Key Takeaways

- The **DUAA (c.18)** received Royal Assent on **19 June 2025** and amends — does not replace — the UK GDPR, DPA 2018 and PECR [1][10]. *(Legal obligation.)*
- The **majority of the data-protection provisions in Part 5 came into force on 5 February 2026** via the **Commencement No. 6 Regulations (SI 2026/82)** [3][9][14]. *(Legal obligation — in force.)*
- The **complaints-handling duty (s.103)** is scheduled to commence **19 June 2026** — organisations must have a compliant process by then [9][10]. *(Legal obligation — pending commencement.)*
- **Recognised legitimate interests** is a new lawful basis for a **closed list of public-interest purposes** (e.g. national/public security, crime detection/prevention, safeguarding, emergencies, democratic engagement) that requires **no legitimate-interests balancing test** — but **cannot** be used for significant automated decisions [10][13][15]. *(Legal obligation.)*
- The DUAA replaces UK GDPR **Article 22 with new Articles 22A–22D (s.80)**: the general ban on solely automated significant decisions is lifted for **non-special-category** data, subject to **safeguards** (information, representations, human intervention, contestation); special-category ADM stays tightly restricted [2][10][13]. *(Legal obligation.)*
- **PECR** maximum penalties rise from **£500,000 to £17.5m or 4% of global turnover**, cookie **consent exemptions** are added for low-risk purposes (e.g. analytics, security), and **soft opt-in** is extended to charities/non-profits [10][13][16]. *(Legal obligation.)*
- International transfers move to a **"data protection test"** — protection in the destination must be **"not materially lower"** than the UK standard — a lower threshold than the EU's "essentially equivalent" [10][13]. *(Legal obligation / regulatory interpretation.)*
- The ICO is reconstituted as the **Information Commission** (a body corporate with a board and statutory objectives) [9][11][13]. *(Legal obligation.)*
- **EU adequacy** for the UK was **renewed to 27 December 2031** after the Commission assessed the DUAA reforms [17]. *(Regulatory / legal.)*

# Purpose

This document is the sub-topic deep-dive on the DUAA 2025. It supports: (a) legal research — mapping each reform to the amending section and to the amended UK GDPR / DPA 2018 / PECR provision; (b) compliance implementation — what to change now that most provisions are in force; and (c) programme tracking — the staged commencement timetable and outstanding dates. It **details** `uk-gdpr-foundations` and does not restate the UK GDPR's constitutional basis or the EU baseline (see `gdpr-foundations`).

# Scope

**In scope:** The DUAA's data-protection and e-privacy reforms — recognised legitimate interests; automated decision-making (Arts 22A–22D); scientific research; complaints handling (s.103); children's online-services duty; international transfers ("data protection test"); PECR changes (cookies, soft opt-in, fines); the Information Commission; and the staged commencement timetable.

**Out of scope (spun off / cross-referenced):** UK international-transfer mechanics (IDTA / UK Addendum) → `uk-transfers`; the ICO Children's Code in depth → `uk-childrens-code`; UK PECR end-to-end → `eprivacy-uk`; the DUAA's **non-data-protection** parts (digital verification services / trust framework, smart data / open banking-style schemes, the National Underground Asset Register, births/deaths registration, dataset/interoperability provisions) are noted only where they bear on commencement. Law-enforcement/intelligence processing changes (DPA 2018 Parts 3–4) are noted but not detailed.

**Assumptions:** The reader has read `uk-gdpr-foundations` and `gdpr-foundations`. Article numbering and principles carry over from the UK GDPR except where the DUAA amends them.

# Definitions

*Shared terms (personal data, controller, processor, consent, special-category data, legitimate interests, ISS, PECR, adequacy) are in `GLOSSARY.md` and carry over. Only DUAA-specific terms are defined here; keep short.*

| Term | Definition | Source |
|------|------------|--------|
| DUAA / DUAA 2025 | Data (Use and Access) Act 2025 (c.18), amending the UK GDPR, DPA 2018 and PECR. | [1] |
| Recognised legitimate interest | A specified public-interest purpose (listed in the new Annex introduced by the DUAA) for which a controller may process personal data **without** performing the legitimate-interests balancing test. | [13][15] |
| Significant decision | A decision producing legal effects concerning, or similarly significantly affecting, a data subject (new UK GDPR Art. 22A). | [2][13] |
| Data protection test | The DUAA test for approving transfers / adequacy: whether the destination's standard of protection is **not materially lower** than under UK law. | [10][13] |
| Information Commission | The body corporate that replaces the Information Commissioner's Office as the UK data-protection regulator under the DUAA. | [9][11] |
| Commencement regulations | Secondary legislation (a series of SIs) that bring individual DUAA provisions into force on staged dates. | [3][4][9] |

# Background

UK data-protection reform has a long gestation. Earlier attempts (the Data Protection and Digital Information Bill of 2022–23, reintroduced 2023) fell with the 2024 general election. The DUAA is the successor vehicle: narrower and more targeted than a wholesale rewrite, it keeps the UK GDPR/DPA 2018 architecture and edits it [10]. Its stated aims are to enable safe data use to support growth and public services, reduce compliance friction on lower-risk processing, and modernise the regulator — while preserving the high level of protection on which **EU adequacy** depends [10][17].

The Act reached **Royal Assent on 19 June 2025** [1]. Because it edits three instruments at once and depends on secondary legislation and updated ICO guidance, the Government adopted a **staged commencement plan** run by the Department for Science, Innovation and Technology (DSIT) [9]. Some provisions commenced automatically on assent or shortly after; the bulk of the data-protection reforms were switched on by the **Commencement No. 6 Regulations 2026 (SI 2026/82)** on **5 February 2026** [3][9]. A small number of provisions — most visibly the complaints-handling duty — commence later [9].

# Legal Framework

The DUAA is a large Act; its data-protection substance sits mainly in **Part 5** (data protection and privacy), with the regulator reconstituted elsewhere in the Act [1][10]. The mechanism is amendment-in-place: DUAA sections insert, substitute or repeal text in the UK GDPR (retained/assimilated under EUWA 2018 s.3 [7]), the **DPA 2018 [5]** and PECR. The consolidated effect must therefore be read in the **amended** UK GDPR/DPA 2018/PECR, not in the DUAA alone [1][10].

The principal data-protection reforms, and where they land, are set out below. Distinguish throughout: **OBLIGATION** (what the amended law requires), **REGULATORY INTERPRETATION** (ICO/GOV.UK reading), **BEST PRACTICE**, and **EDITORIAL RECOMMENDATION**.

## Relevant Articles

*"Article" here means the amended UK GDPR article (or the DUAA / DPA 2018 / PECR provision) as the case may be.*

| Provision | Obligation / effect | Source |
|-----------|---------------------|--------|
| UK GDPR Art. 6 + new Annex (recognised legitimate interests) | New lawful basis for a closed list of public-interest purposes; **no balancing test** for listed purposes. | [10][13][15] |
| UK GDPR Art. 6(1)(f) / recitals (listed legitimate interests) | Certain commercial interests (e.g. direct marketing, intra-group transmission, network/information security) expressly recognised as **capable of being** legitimate interests — balancing test still required. | [13][15] |
| UK GDPR Arts. 22A–22D (DUAA s.80) | Replaces Art. 22: lifts the general prohibition on solely automated significant decisions for **non-special-category** data, subject to safeguards; restricts special-category ADM; empowers the Secretary of State to define thresholds. | [2][10][13] |
| UK GDPR Arts. 4/8a-area + DPA 2018 (scientific research) | Clarified definition of "research and statistical purposes"; workable **broad consent** to areas of scientific research; confirms commercial research can qualify. | [10][13] |
| DPA 2018 (DUAA s.103) (complaints) | Controllers must facilitate complaints (incl. an **electronic route**), **acknowledge within 30 days**, and investigate/respond without undue delay; ICO gains related powers. | [10][12] |
| UK GDPR Art. 25-area (children) | Providers of ISS likely to be accessed by children must consider **"children's higher protection matters"** in data-protection-by-design/default decisions. | [12][13] |
| UK GDPR Ch. V + DPA 2018 (transfers) | New **"data protection test"**: destination protection must be **"not materially lower"** than the UK standard; Secretary of State may approve countries/mechanisms. | [10][13] |
| PECR (SI 2003/2426) as amended | Cookie **consent exemptions** for low-risk purposes; **soft opt-in** extended to non-commercial bodies; maximum fines raised to **£17.5m / 4%** of turnover. | [10][13][16] |

## Relevant Recitals

The UK GDPR retains its recitals as interpretive aids (see `gdpr-foundations`). The DUAA operates by amending the enacting text and, in places, by adding definitional and Annex material rather than new recitals; it is construed against the **Act's own provisions, Explanatory Notes and ICO guidance** rather than EU-style recitals [1][10]. **Not Applicable** as a distinct set — no new UK GDPR recitals are introduced; interpretation of the new lawful basis and ADM regime rests on the statutory text and ICO guidance [13][15].

## Relevant Case Law

**Not Applicable.** The DUAA is new (Royal Assent June 2025; most data-protection provisions in force February 2026), so there is no judicial interpretation of its provisions yet. Pre-2021 retained/assimilated CJEU case law continues to inform the **unamended** UK GDPR concepts (see `uk-gdpr-foundations`), but the DUAA-specific provisions — recognised legitimate interests, Arts 22A–22D, the transfers test — are as yet untested in the courts [1][8]. Early disputes are more likely to surface first as ICO enforcement and guidance than as litigation.

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).** The authoritative UK readings are DSIT's commencement materials and the ICO's DUAA guidance suite [9][11][12][13].

- **Commencement is staged and mostly complete for data protection.** DSIT's plan sets out phased entry into force; the ICO confirms that the **main UK GDPR and PECR changes took effect on 5 February 2026**, with the complaints duty to follow and some ICO-governance provisions later [9][14]. *(Regulatory interpretation.)*
- **"Amend, don't replace."** The ICO frames the DUAA as building on existing compliance — organisations already compliant with the UK GDPR have a foundation, but must adjust for the new provisions as they commence [11][13]. *(Regulatory interpretation.)*
- **Recognised legitimate interests is narrow and public-interest.** The ICO's final guidance (published 23 March 2026) stresses that a recognised legitimate interest is a **specified public-interest purpose**, is **different from** the ordinary legitimate-interests basis, and — while it removes the balancing test — still requires the processing to be **necessary** for the listed purpose; it **cannot** support significant automated decisions [13][15]. *(Regulatory interpretation of a legal obligation.)*
- **ADM freedom is conditional.** GOV.UK and the ICO present the Art. 22A–22D reform as removing the need for a *qualifying* lawful basis before making a significant automated decision (except for special-category data), **provided** the safeguards are in place; the ICO has consulted on ADM/profiling guidance [10][13]. *(Regulatory interpretation.)*
- **Enforcement posture.** On commencement the ICO signalled a **supportive but watchful** approach — expecting organisations to work towards compliance and prioritising engagement — while retaining its enforcement powers, now materially larger for PECR [14][16]. *(Regulatory interpretation.)*

# Technical Considerations

- **Lawful-basis registers** must add **recognised legitimate interests** as a distinct basis (not a variant of Art. 6(1)(f)), recording the specific listed purpose and the necessity assessment; do **not** attach a balancing-test record to it (there is none) but **do** document why the purpose falls within the list [13][15]. *(Best practice grounded in obligation.)*
- **ADM pipelines** relying on Arts 22A–22D need: (i) detection of whether a decision is *solely* automated (no genuine, meaningful human involvement) and *significant*; (ii) a **special-category gate** (Art. 22B) blocking automated significant decisions on special-category data absent explicit consent or legal authorisation; and (iii) implemented **safeguards** (Art. 22C) — proactive information, a channel to make representations, human intervention/review, and a contest route [2][13]. *(Legal obligation.)*
- **Consent-management platforms (CMPs)** should be reconfigured for the new **cookie exemptions** (e.g. statistical/analytics to improve the service, security, fraud prevention, technical delivery) — but exemptions are purpose-scoped, so mixed-purpose tags still need consent [13][16]. *(Legal obligation.)*
- **Complaints tooling** (ahead of 19 June 2026): an **electronic complaints form/route**, a workflow enforcing **30-day acknowledgement**, case tracking and outcome communication [10][12]. *(Legal obligation — pending commencement.)*
- **Research data flows** benefit from the clarified definitions and broad consent, but require documented scoping of the research area and recognised ethical/safeguarding standards [10][13]. *(Best practice.)*
- **Jurisdiction-awareness** — because the DUAA widens UK-only freedoms (RLI, ADM, transfers test), systems serving both EU and UK subjects should apply rules per jurisdiction rather than a single global setting [10]. *(Best practice.)*

# Hosting Considerations

- **International transfers** now turn on the **"data protection test"** ("not materially lower"): re-paper transfer risk assessments against the UK test rather than the EU "essentially equivalent" standard for **UK-origin** exports, while keeping the EU standard for EU-origin data [10][13]. *(Legal obligation.)*
- **EU→UK adequacy** subsists (renewed to **27 December 2031**), so hosting EU personal data in the UK remains lawful without additional safeguards — but this is **conditional on the UK not diverging too far**, making the DUAA's transfer and ADM liberalisations a watch-item [17]. *(Legal / editorial.)*
- **Processor contracts (Art. 28)** are unchanged in structure, but processors offering analytics/telemetry should surface which cookie/PECR exemptions their tooling relies on so controllers can document them [16]. *(Best practice.)*
- **Log retention for ADM** — safeguards (human-review, contestation) imply retaining decision logs and model inputs long enough to service data-subject challenges, balanced against minimisation/retention limits [2][13]. *(Best practice grounded in obligation.)*

# Game Hosting Considerations

- **Children's higher-protection duty** is acute for games: providers of ISS **likely to be accessed by children** must consider "children's higher protection matters" in DPbDD decisions — children merit specific protection, are less aware of risks, and have different needs at different ages [12][13]. This layers on top of the UK **age-13** consent threshold (DPA 2018 s.9) and the ICO Children's Code (see `uk-childrens-code`) [6]. *(Legal obligation.)*
- **Automated moderation / anti-cheat / matchmaking** that makes *significant* decisions about players (e.g. bans, account restrictions) may now fall under Arts 22A–22D — assess whether the decision is solely automated and significant, and implement the safeguards, especially where minors are affected [2][13]. *(Legal obligation.)*
- **In-game marketing** benefits from the extended **soft opt-in** only for the narrow conditions (existing supporters/customers, related purposes, opt-out at collection and each message); higher PECR fines (£17.5m/4%) sharpen the cost of unlawful marketing to players [16]. *(Legal obligation.)*
- **Analytics/telemetry** on player behaviour may use the new cookie exemptions where genuinely for service-improvement statistics or security — but profiling for personalisation/ads still needs consent [16]. *(Legal obligation.)*

# AI Considerations

- **ADM liberalisation is the headline AI change.** Arts 22A–22D (s.80) shift the UK from a *prohibition-plus-exceptions* model to a *permission-plus-safeguards* model for solely automated significant decisions on non-special-category data — directly relevant to AI-driven credit, hiring, pricing and fraud systems [2][10][13]. This **diverges** from the stricter EU Art. 22 position and the EU AI Act overlay (see `ai-act-foundations`). *(Legal obligation; divergence risk.)*
- **Special-category ADM remains restricted** (Art. 22B): AI making significant decisions on health, biometric or other special-category data needs **explicit consent or legal authorisation** — a hard constraint on, e.g., health-AI and biometric systems [2][13]. *(Legal obligation.)*
- **Recognised legitimate interests cannot power significant ADM** — a deliberate carve-out preventing the balancing-test-free basis from being used to automate consequential decisions [13][15]. *(Legal obligation.)*
- **Scientific-research clarifications** ease lawful reuse of personal data for AI/ML research, including **commercial** research, via clarified definitions and broad consent — but purpose-scoping and safeguards remain [10][13]. *(Legal obligation / interpretation.)*
- **Explainability gap** — commentators note the safeguards (information, human review, contest) do not by themselves guarantee algorithmic *explainability*; controllers should treat transparency as a live design requirement, not a checkbox [13]. *(Editorial recommendation.)*
- **UK has no AI Act equivalent** — AI governance stays principles-based; the DUAA's ADM rules are the closest hard-law touchpoint for AI decisions about UK data subjects [10]. *(Editorial note.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Re-baseline your compliance to the 5 Feb 2026 changes** — treat the amended UK GDPR/PECR as current law, not a future project. *(OBLIGATION.)* [3][9]
2. **Add recognised legitimate interests to the lawful-basis register** where used, recording the specific listed purpose and necessity; do not use it for significant ADM. *(OBLIGATION.)* [13][15]
3. **Re-engineer significant-ADM systems to Arts 22A–22D** — special-category gate, plus information/representations/human-intervention/contest safeguards. *(OBLIGATION.)* [2][13]
4. **Stand up a complaints process before 19 June 2026** — electronic route, 30-day acknowledgement, investigation and outcome communication. *(OBLIGATION — pending commencement.)* [9][10][12]
5. **Reconfigure your CMP** for the new cookie exemptions, keeping consent for non-exempt/profiling purposes. *(OBLIGATION.)* [13][16]
6. **Update marketing rules** for the extended soft opt-in and the £17.5m/4% PECR fine ceiling. *(OBLIGATION.)* [16]
7. **Re-paper UK transfer risk assessments** against the "not materially lower" data-protection test. *(OBLIGATION.)* [10][13]
8. **Embed the children's higher-protection duty** into DPbDD for services likely accessed by children. *(OBLIGATION.)* [12][13]
9. **Maintain a commencement watch-list** for outstanding provisions (complaints, ICO-governance) and track ICO guidance updates. *(BEST PRACTICE.)* [9]
10. **Keep an EU/UK divergence register and an adequacy contingency plan** — DUAA freedoms increase divergence even though adequacy runs to 2031. *(EDITORIAL RECOMMENDATION.)* [17]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Treating DUAA changes as "future" when most are in force (5 Feb 2026) | High | High | SI 2026/82 [3][9] | Re-baseline compliance to amended law | Medium |
| R2 | Misusing recognised legitimate interests beyond the listed purposes, or for significant ADM | Medium | High | New Art. 6 basis; carve-out [13][15] | Restrict to listed purposes; document necessity; block for ADM | Low |
| R3 | Relying on Arts 22A–22D without the mandated safeguards | Medium | High | Art. 22C [2][13] | Implement information/representation/intervention/contest controls | Low |
| R4 | Automating significant decisions on special-category data without explicit consent/legal authority | Medium | Very High | Art. 22B [2][13] | Special-category gate in ADM pipeline | Low |
| R5 | No complaints process in place by 19 June 2026 | Medium | Medium | s.103 [9][10] | Build electronic route + 30-day SLA now | Low |
| R6 | PECR breach under the new £17.5m/4% ceiling (cookies/marketing) | Medium | High | PECR as amended [16] | CMP reconfig; soft opt-in discipline | Low |
| R7 | Over-relying on the softer "not materially lower" transfer test for EU-origin data | Medium | High | Transfers test [10][13] | Apply EU standard to EU-origin; UK test to UK-origin | Low |
| R8 | Divergence erodes EU adequacy at next review | Low | Very High | Adequacy to 2031 [17] | Divergence register; SCC/IDTA contingency | Medium |
| R9 | Weak children's-protection design for services accessed by minors | Medium | High | Children's duty [12][13] | Embed duty in DPbDD; align to Children's Code | Low |

# Implementation Roadmap

- **Phase 0 — Gap assessment (now):** Map current processing to the amended UK GDPR/PECR; identify uses of legitimate interests, ADM, cookies, marketing and transfers affected by the DUAA. *Effort:* Medium.
- **Phase 1 — Lawful bases & ADM:** Add recognised legitimate interests where apt; re-engineer significant-ADM systems to Arts 22A–22D with safeguards and the special-category gate. *Effort:* Medium–High.
- **Phase 2 — Complaints readiness (by 19 June 2026):** Build the electronic complaints route, 30-day acknowledgement SLA and outcome workflow. *Effort:* Medium.
- **Phase 3 — PECR & marketing:** Reconfigure the CMP for new cookie exemptions; update soft opt-in rules; brief on the £17.5m/4% ceiling. *Effort:* Medium.
- **Phase 4 — Transfers & children:** Re-paper UK transfer assessments to the "not materially lower" test; embed the children's higher-protection duty in DPbDD. *Effort:* Medium.
- **Phase 5 — Assurance & monitoring:** Update DPIAs, RoPA, policies and training; maintain a commencement watch-list and EU/UK divergence register; monitor adequacy. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Unaware DUAA is in force; still operating pre-2026 UK GDPR/PECR assumptions. | No gap assessment. |
| 2 | Managed | Aware of the 5 Feb 2026 changes; ad hoc adjustments to cookies/marketing. | Partial mapping. |
| 3 | Defined | Recognised-legitimate-interests and ADM registers updated; complaints process built; CMP reconfigured; transfer assessments re-papered. | Documented DUAA processes. |
| 4 | Quantitatively Managed | Metrics on complaints SLAs, ADM safeguard usage, consent rates; periodic legal review of new provisions. | KPIs; internal audit. |
| 5 | Optimising | Jurisdiction-aware automated controls; proactive commencement tracking; tested adequacy-contingency plans. | Dual EU/UK controls; assurance evidence. |

# Audit Questions

1. Which DUAA provisions do you treat as in force, and does your compliance reflect the **5 February 2026** changes? *(SI 2026/82 [3][9].)*
2. Where you rely on **recognised legitimate interests**, is the purpose within the statutory list, is necessity documented, and have you ensured it is **not** used for significant ADM? *([13][15].)*
3. For solely automated **significant decisions**, how do you meet Arts 22A–22D — including the special-category gate and the four safeguards? *([2][13].)*
4. Is your **complaints process** (electronic route, 30-day acknowledgement, investigation) in place ahead of **19 June 2026**? *([9][10][12].)*
5. Have you reconfigured your **cookie/CMP** setup for the new exemptions without over-claiming them? *([13][16].)*
6. Do your **marketing** practices reflect the extended soft opt-in and the **£17.5m/4%** PECR ceiling? *([16].)*
7. Have you re-papered **UK transfer** risk assessments to the **"not materially lower"** test while preserving the EU standard for EU-origin data? *([10][13].)*
8. How is the **children's higher-protection** duty embedded in your DPbDD for services likely accessed by children? *([12][13].)*

# Implementation Checklist

- [ ] Gap assessment against the amended UK GDPR/DPA 2018/PECR completed.
- [ ] Recognised-legitimate-interests basis added to the lawful-basis register (listed purpose + necessity documented); excluded from significant ADM.
- [ ] Significant-ADM systems re-engineered to Arts 22A–22D (special-category gate + safeguards).
- [ ] Complaints process (electronic route, 30-day acknowledgement, investigation, outcome) live before 19 June 2026.
- [ ] CMP reconfigured for new cookie exemptions; consent retained for non-exempt/profiling purposes.
- [ ] Marketing updated for extended soft opt-in; teams briefed on £17.5m/4% PECR fines.
- [ ] UK transfer risk assessments re-papered to the "not materially lower" test.
- [ ] Children's higher-protection duty embedded in DPbDD.
- [ ] DPIAs, RoPA, policies and training updated; commencement watch-list and EU/UK divergence register maintained.

# References

*All links verified live on 2026-07-11 (`sources_verified`) with HTTP 200.*

## Primary Sources

- [1] **Data (Use and Access) Act 2025 (c.18)**, contents (Royal Assent 19 June 2025). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/contents
- [2] **Data (Use and Access) Act 2025, s.80** (automated decision-making — inserting UK GDPR Arts 22A–22D). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/section/80
- [3] **The Data (Use and Access) Act 2025 (Commencement No. 6 and Transitional and Saving Provisions) Regulations 2026 (SI 2026/82)** — brings most Part 5 data-protection provisions into force on 5 February 2026. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2026/82/contents/made
- [4] **The Data (Use and Access) Act 2025 (Commencement No. 5) Regulations 2026 (SI 2026/31).** legislation.gov.uk. https://www.legislation.gov.uk/uksi/2026/31/made
- [5] **Data Protection Act 2018 (c.12)**, contents (the Act the DUAA amends). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/contents
- [6] **Data Protection Act 2018, s.9** (child's consent — age 13 for information-society services). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/9
- [7] **European Union (Withdrawal) Act 2018, s.3** (retention of the UK GDPR in domestic law). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/16/section/3
- [8] **Regulation (EU) 2016/679 (EU GDPR)**, consolidated text (base instrument for the UK GDPR). EUR-Lex. https://eur-lex.europa.eu/eli/reg/2016/679/oj

## Regulatory Guidance

- [9] **Data Use and Access Act 2025: plans for commencement** (DSIT staged commencement timetable; s.103 complaints scheduled ~19 June 2026). GOV.UK. https://www.gov.uk/guidance/data-use-and-access-act-2025-plans-for-commencement
- [10] **Data (Use and Access) Act 2025: data protection and privacy changes.** GOV.UK. https://www.gov.uk/guidance/data-use-and-access-act-2025-data-protection-and-privacy-changes
- [11] **The Data (Use and Access) Act 2025 — legislation we cover** (landing page). ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/
- [12] **The Data (Use and Access) Act 2025 — what does it mean for organisations?** ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/the-data-use-and-access-act-2025-what-does-it-mean-for-organisations/
- [13] **DUAA — summary of the changes: data protection.** ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/the-data-use-and-access-act-2025-duaa-summary-of-the-changes/data-protection/
- [14] **Statement on the commencement of the Data (Use and Access) Act (DUAA)** (5 February 2026; enforcement approach). ICO. https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/02/statement-on-the-commencement-of-the-data-use-and-access-act-duaa/
- [15] **Recognised legitimate interest** (guidance). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/lawful-basis/a-guide-to-lawful-basis/recognised-legitimate-interest/
- [16] **Guide to PECR** (cookies, direct marketing, penalties). ICO. https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/
- [17] **Commission renews decisions to allow the free and safe flow of personal data with the UK** (IP/25/3059, 19 December 2025; adequacy to 27 December 2031, assessing the DUAA). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_3059

## Standards

**Not Applicable** — the DUAA is domestic primary legislation and regulator guidance; no ISO/IEC/NIST/OWASP standard is specific to it. General privacy/security standards (ISO/IEC 27001, 27701) apply to implementation as under the UK GDPR (see `privacy-engineering-foundations`).

## Academic Sources

**Not Applicable** — this sub-topic relies on primary legislation and regulatory guidance. Peer-reviewed analysis of DUAA divergence and ADM explainability is emerging and will be cited as it matures.

# Further Reading

*Non-authoritative; provided for orientation only.*

- GOV.UK — Data (Use and Access) Act 2025 (collection). https://www.gov.uk/government/collections/data-use-and-access-act-2025
- ICO — Guide to lawful basis: legitimate interests. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/lawful-basis/a-guide-to-lawful-basis/legitimate-interests/

# Related Documents

- `uk-gdpr-foundations` — UK GDPR foundations & divergence (**parent; this document details its DUAA material**).
- `gdpr-foundations` — EU GDPR baseline (**prerequisite reading**).
- `uk-transfers` — UK international transfers (IDTA / UK Addendum; "data protection test" mechanics) (planned).
- `uk-childrens-code` — ICO Age-Appropriate Design Code (planned).
- `eprivacy-uk` — UK PECR / ePrivacy in depth (planned).
- `ai-act-foundations` — EU AI Act (contrast for ADM/AI governance divergence).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against legislation.gov.uk (DUAA c.18, SI 2026/82, SI 2026/31, DPA 2018), GOV.UK commencement/changes guidance, ICO DUAA guidance suite and European Commission adequacy sources. **Staged commencement timetable live-verified: most Part 5 data-protection provisions in force 5 February 2026 (SI 2026/82); s.103 complaints scheduled 19 June 2026.** | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch gate; commencement (SI 2026/82) verified; frozen in release 0.10.0. | Human reviewer |
