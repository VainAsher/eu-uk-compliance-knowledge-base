---
id: digital-omnibus
title: "The EU Digital Omnibus: Simplification Package (2025–2026)"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU]
topic: ePrivacy
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
related: [eprivacy-foundations, ai-act-foundations, ai-act-high-risk, gdpr-foundations]
tags: [digital-omnibus, simplification, eprivacy, cookies, consent, ai-act, gdpr, data-act, ai-omnibus]
legal_basis: COM(2025) 836 (Digital Omnibus on AI, adopted) and COM(2025) 837 (Digital Omnibus Regulation, proposed); amending Regulation (EU) 2024/1689, Regulation (EU) 2016/679, Directive 2002/58/EC, Regulation (EU) 2023/2854
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | digital-omnibus |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | <pending human review> |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. This is a **fast-moving** topic. The package has **two distinct strands with different legal status**: the **Digital Omnibus on AI** (amending the AI Act) is **ADOPTED LAW** (European Parliament plenary 16 June 2026; Council final approval 29 June 2026; entry into force on the third day after Official Journal publication), whereas the **broader Digital Omnibus Regulation** (data-law simplification, including the cookie-consent migration into the GDPR) is a **PROPOSAL still in the ordinary legislative procedure** and is **not law**. Confirm the live position and the OJ citation before relying on any date or provision.

# Executive Summary

The **"Digital Omnibus"** is the European Commission's late-2025 digital-simplification package, tabled on **19 November 2025** as part of its 2025 work-programme simplification agenda [6][9][10]. It is not a single instrument but a **package of two separate legislative proposals**, and the single most important compliance point is that **they now have different legal status** [9][10].

The first strand — the **Digital Omnibus on AI** (COM(2025) 836; procedure 2025/0359(COD)) — amends the **AI Act (Regulation (EU) 2024/1689)** and has been **formally ADOPTED**: the European Parliament approved it in plenary on **16 June 2026** (423–57–174) and the Council gave final green light on **29 June 2026**; it enters into force on the **third day after Official Journal publication** [7][8][9]. It postpones the high-risk obligations (to **2 December 2027** for stand-alone Annex III systems and **2 August 2028** for AI embedded in regulated products), postpones AI-content marking/transparency to **2 December 2026** for systems already on the market, and adds a new **Article 5 prohibition on "nudifier"/non-consensual intimate-image and CSAM generators** [7][9]. These AI-specific effects are detailed in `ai-act-foundations` and `ai-act-high-risk`; this document cross-references them and does not restate the high-risk mechanics.

The second strand — the **Digital Omnibus Regulation** (COM(2025) 837; procedure 2025/0360(COD)) — is the **data-law** simplification proposal and remains **a PROPOSAL, not law** [10]. It would, among other things, **move the cookie-consent rules out of the ePrivacy Directive and into the GDPR**, expand the list of consent-exempt processing, introduce one-click / browser-level consent valid for six months, add a GDPR "legitimate interest" basis for AI training, consolidate the **Data Act** (absorbing the Data Governance Act, Open Data Directive and Free Flow of Non-Personal Data Regulation), and streamline DPIAs and breach reporting [10]. Because this strand is unadopted, **the ePrivacy Directive and national laws such as PECR remain fully in force** and organisations must **not** pre-implement the proposed cookie regime [3][10]. This document is the deep-dive deferred from `eprivacy-foundations` on the cookie-rule migration.

# Key Takeaways

- The **Digital Omnibus** (tabled 19 Nov 2025) is a **package of two proposals**, not one law: a **Digital Omnibus on AI** (COM(2025) 836) and a broader **Digital Omnibus Regulation** on data (COM(2025) 837) [6][9][10]. *(Regulatory fact.)*
- **ADOPTED — LAW:** the **Digital Omnibus on AI** was approved by the **European Parliament on 16 June 2026** and the **Council on 29 June 2026**; it enters into force on **OJ publication + 3 days** [7][8][9]. *(Legal fact — adopted.)*
- The AI strand **postpones high-risk application** to **2 December 2027** (stand-alone Annex III) and **2 August 2028** (AI embedded in regulated products), and postpones **AI-content marking** to **2 December 2026** for systems placed on the market before 2 August 2026 [7][9]. *(Legal obligation — adopted; detailed in `ai-act-high-risk`.)*
- The AI strand adds a **new Article 5 AI Act prohibition** on AI generating **non-consensual intimate/sexual imagery ("nudifiers") and child sexual abuse material** [7][9]. *(Legal obligation — adopted.)*
- **PROPOSED — NOT LAW:** the **Digital Omnibus Regulation** would **move cookie-consent rules from the ePrivacy Directive into the GDPR**, expand consent exemptions, and allow **one-click / browser-level consent valid for six months** — but it is **still in the ordinary legislative procedure** [10]. *(Proposal only.)*
- The data strand would also add a GDPR **"legitimate interest" basis for AI training/operation** (subject to conditions) and **streamline DPIAs and breach reporting** — again, **proposal only** [10]. *(Proposal only.)*
- The data strand would **consolidate the Data Act**, merging the **Data Governance Act, Open Data Directive and Free Flow of Non-Personal Data Regulation** into a restructured Data Act, with cloud-switching exemptions for small businesses — **proposal only** [4][5][10]. *(Proposal only.)*
- **Do not pre-implement the data strand.** Until it is adopted, the **ePrivacy Directive (2002/58/EC) and PECR remain in force**; consent-before-set for non-essential cookies still applies [3][10]. *(Editorial recommendation grounded in current law.)*

# Purpose

This document exists to give compliance, legal and engineering teams a **single, status-accurate** account of the Digital Omnibus package, so they can (a) act now on what is **adopted** (the AI-timeline and prohibition changes) and (b) **watch, but not pre-implement,** what is merely **proposed** (the cookie/GDPR/Data Act reforms). It is the deep-dive that `eprivacy-foundations` deferred on the cookie-rule migration, and it cross-references `ai-act-foundations` and `ai-act-high-risk` for the AI-Act-specific detail rather than duplicating it. It supports the decision *"what, if anything, must we change today, and what do we merely track?"*

# Scope

**In scope:** The origin and structure of the 2025 Digital Omnibus simplification agenda; the **adopted** Digital Omnibus on AI (what it changed and when it binds) at a cross-referencing level; the **proposed** Digital Omnibus Regulation (data strand) — the cookie-consent migration into the GDPR, consent-exemption expansion, one-click/browser consent, the GDPR "legitimate interest for AI" change, DPIA/breach-reporting streamlining, and the Data Act consolidation — with current legislative status; a clear **adopted-vs-proposed** table; and guidance on what organisations should and should **not** do now.

**Out of scope:** The full AI-Act high-risk mechanics and conformity chain → `ai-act-high-risk`; the AI-Act risk-tier overview, GPAI regime and penalties → `ai-act-foundations`; the foundational cookie/consent and direct-marketing rules → `eprivacy-foundations`; UK PECR in depth → `pecr-detail` (planned); the Data Act's substantive obligations → `data-act-foundations` (planned). This document does not restate those; it tracks the **change**.

**Assumptions:** The reader has read `eprivacy-foundations` (for the Art. 5(3) cookie rule and the lex-specialis relationship) and, for the AI strand, `ai-act-foundations`. "Consent" carries its GDPR meaning (Art. 4(11); see `GLOSSARY.md`).

# Definitions

*Shared terms (consent, personal data, cookie rule, high-risk AI system) are in `GLOSSARY.md`. Only package-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Digital Omnibus | The Commission's late-2025 digital-simplification package, tabled 19 Nov 2025, comprising the Digital Omnibus on AI and the (broader) Digital Omnibus Regulation. | [6][9][10] |
| Digital Omnibus on AI | The **adopted** amending Regulation (COM(2025) 836; 2025/0359(COD)) modifying the AI Act (and Reg (EU) 2018/1139) to postpone high-risk dates and add targeted measures. | [6][7][9] |
| Digital Omnibus Regulation | The **proposed** amending Regulation (COM(2025) 837; 2025/0360(COD)) simplifying the EU data acquis (GDPR, ePrivacy cookie rules, Data Act and related instruments). | [10] |
| Cookie-consent migration | The **proposed** relocation of the ePrivacy Directive Art. 5(3) consent rule into the GDPR, with expanded exemptions and one-click/browser-level consent. | [3][10] |
| Simplification agenda | The Commission's 2025 work-programme drive to reduce regulatory/administrative burden across the digital acquis, of which the Digital Omnibus is the flagship instrument. | [6][9][10] |

# Background

During 2025 the Commission launched a **digital-simplification agenda** in its work programme, aimed at reducing administrative burden and improving coherence across the EU's digital rulebook (GDPR, ePrivacy, the AI Act, the Data Act and the cybersecurity acquis) [6][9][10]. To prepare, it ran a **call for evidence from 16 September to 14 October 2025**, seeking views on the data acquis, **cookies and other tracking technologies**, cybersecurity incident reporting, smooth application of the AI Act, and electronic identification/trust services [10].

On **19 November 2025** the Commission tabled the package as **two distinct legislative proposals** [9][10]:

- the **Digital Omnibus on AI** — **COM(2025) 836**, procedure **2025/0359(COD)** — amending the AI Act and the civil-aviation Regulation (EU) 2018/1139 [6][9]; and
- the **Digital Omnibus Regulation** — **COM(2025) 837**, procedure **2025/0360(COD)** — restructuring and simplifying the **data** acquis [10].

The two strands then **diverged procedurally**. The AI strand moved quickly: Council general approach 13 March 2026, trilogue agreement 7 May 2026, Coreper 13 May 2026, IMCO/LIBE committees 2 June 2026, **Parliament plenary 16 June 2026**, and **Council final adoption 29 June 2026** [7][8][9][11]. The data strand advanced only through advisory stages by this document's date — the **European Economic and Social Committee opinion (18 March 2026)** and the **Committee of the Regions opinion (7 May 2026)** — and had **not** been adopted by the co-legislators [10].

The cookie-migration idea did not arise in a vacuum. The 2017 **ePrivacy Regulation** proposal, intended to replace the Directive, stalled for years and was ultimately **withdrawn** in 2025 [12][14]; the Digital Omnibus is the Commission's alternative route — folding cookie rules into the GDPR rather than enacting a standalone ePrivacy Regulation (see `eprivacy-foundations`) [10][14].

# Legal Framework

The Digital Omnibus operates by **amendment**: neither strand is a free-standing new regime; each edits existing instruments. Their legal status must therefore be read against the instruments they modify.

**Strand 1 — Digital Omnibus on AI (ADOPTED / LAW).** COM(2025) 836 amends **Regulation (EU) 2024/1689 (AI Act)** [1] and **Regulation (EU) 2018/1139**. Having been approved by the **European Parliament (16 June 2026)** and the **Council (29 June 2026)**, it is an **adopted** amending Regulation that enters into force on the **third day after Official Journal publication** [7][8][9]. Its principal legal effects (LAW, subject to OJ publication):

- **Postponed high-risk application** — stand-alone Annex III high-risk systems to **2 December 2027**; AI embedded as safety components in Annex I regulated products to **2 August 2028** [7][9]. *(Detailed in `ai-act-high-risk`.)*
- **Postponed AI-content marking (Art. 50)** — to **2 December 2026** for systems placed on the market before 2 August 2026 [9].
- **New Art. 5 prohibition** — AI practices generating **non-consensual intimate/sexual content ("nudifiers") and child sexual abuse material** [7][9].
- **Targeted simplifications** — a simplified, proportionate **registration** obligation for non-high-risk systems; reinstated **strict-necessity** standard for processing special-category data for bias correction; extended simplified **documentation** for medium-sized companies; reinforced **AI Office** powers; and removal of AI-enabled **machinery** products from direct high-risk applicability (handled instead via the Machinery Regulation) [9].

**Strand 2 — Digital Omnibus Regulation (PROPOSED / NOT LAW).** COM(2025) 837 is a **proposal** amending the **GDPR (Regulation (EU) 2016/679)** [2], the **ePrivacy Directive (2002/58/EC)** [3], the **Data Act (Regulation (EU) 2023/2854)** [4] and related data instruments including the **Data Governance Act (Regulation (EU) 2022/868)** [5]. As a proposal in the ordinary legislative procedure (2025/0360(COD)), it creates **no obligations and changes no existing rule** until adopted [10]. Its principal **proposed** changes:

- **Cookie-consent migration** — move the Art. 5(3) consent rule from the **ePrivacy Directive into the GDPR**, and **expand the list of processing activities exempt from consent**; consent nonetheless remains the **primary criterion** for accessing information on a user's device [3][10].
- **One-click / browser-level consent** — enable users to give **one-click consent valid for six months** or to set **browser/system-level saved preferences** [10].
- **GDPR "legitimate interest" for AI** — allow reliance on the GDPR **legitimate-interest** basis to use personal data for **training or operating AI systems/models**, subject to conditions [2][10].
- **Streamlined DPIAs and breach reporting** — reduce data-protection-impact-assessment and personal-data-breach-notification burden [2][10].
- **Data Act consolidation** — merge the **Data Governance Act, Open Data Directive and Free Flow of Non-Personal Data Regulation** into a single restructured **Data Act**; introduce cloud-switching exemptions for small businesses and model/standard contractual clauses [4][5][10].

## Relevant Articles

*This table maps the package to the provisions it amends. "Status" states whether the change is adopted law or a proposal.*

| Article / Instrument | Change and status | Source |
|---------|------------|--------|
| AI Act Art. 113 (application dates) | Postponed high-risk dates (2 Dec 2027 / 2 Aug 2028). **ADOPTED.** | [7][9] |
| AI Act Art. 50 (transparency/marking) | AI-content marking postponed to 2 Dec 2026 for pre-existing systems. **ADOPTED.** | [9] |
| AI Act Art. 5 (prohibited practices) | New prohibition on nudifier/CSAM generators. **ADOPTED.** | [7][9] |
| AI Act Arts. 10, 49 and registration/documentation provisions | Bias-data strict-necessity reinstated; simplified registration for non-high-risk; simplified SME/mid-cap documentation. **ADOPTED.** | [9] |
| ePrivacy Directive Art. 5(3) (cookie rule) | **Proposed** move of the consent rule into the GDPR; expanded exemptions. **PROPOSED — NOT LAW.** | [3][10] |
| GDPR (consent / lawful basis) | **Proposed** one-click/6-month consent; legitimate-interest basis for AI training. **PROPOSED — NOT LAW.** | [2][10] |
| GDPR Arts. 33–35 (breach notification, DPIA) | **Proposed** streamlining of breach reporting and DPIAs. **PROPOSED — NOT LAW.** | [2][10] |
| Data Act / DGA / Open Data / Free-Flow Regulation | **Proposed** consolidation into one restructured Data Act; SME cloud-switching exemptions. **PROPOSED — NOT LAW.** | [4][5][10] |

## Relevant Recitals

Not Applicable — as amending instruments (one adopted, one proposed), the Digital Omnibus texts do not yet have a stable, citable set of operative recitals suitable for interpretive reliance at this document's date; the authoritative recitals remain those of the **amended** instruments (AI Act, GDPR, ePrivacy Directive, Data Act), which are covered in their own documents [1][2][3][4]. Revisit on OJ publication of the AI strand and on any adoption of the data strand.

## Relevant Case Law

Not Applicable — the Digital Omnibus is a 2025–2026 legislative measure (one strand only just adopted, one still proposed); no court has interpreted it. The relevant interpretive case law is that of the **underlying** instruments — e.g. **Planet49** on cookie consent (see `eprivacy-foundations`) — which the package does not overrule [3].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames the Digital Omnibus as a **simplification** and burden-reduction exercise across the digital acquis, prepared through a 2025 call for evidence covering the data acquis, cookies, cybersecurity reporting, the AI Act and eID/trust services [6][10]. The Commission has also signalled a follow-on **"digital fitness check"** stage after the Omnibus adjustments [6]. *(Regulatory interpretation.)*
- **European Parliament (Legislative Train):** records the **AI strand** as having completed the legislative procedure (plenary 16 June 2026) with the co-legislators setting the **fixed** postponed dates and the new nudifier/CSAM prohibition, and reinstating the strict-necessity standard for bias-data processing [9]. *(Regulatory interpretation of the adopted text.)*
- **European Parliament (Legislative Train):** records the **data strand** (Digital Omnibus Regulation) as a **tabled proposal** that consolidates the data acquis, adds a GDPR legitimate-interest basis for AI, and **modernises the cookie policy** by moving consent into the GDPR with one-click/6-month or browser-level consent — advanced only through EESC (18 Mar 2026) and CoR (7 May 2026) opinions, i.e. **not adopted** [10]. *(Regulatory interpretation of a proposal.)*
- **Council of the EU:** corroborates the **AI strand's** final adoption on **29 June 2026** (final green light to simplify and streamline the AI rules) [8]. *(Regulatory corroboration; the Council site bot-blocks automated link checks — verify in browser.)*
- **Interpretation caution:** because the two strands share the "Digital Omnibus" name, there is a real risk of conflating an **adopted** AI-timeline change with a **proposed** cookie/GDPR change. Regulators and commentators consistently keep them separate; organisations should too [9][10]. *(Editorial note on interpretation.)*

# Technical Considerations

- **AI strand — re-baseline timelines, keep building.** Engineering teams preparing high-risk AI systems should re-plan to **2 Dec 2027 / 2 Aug 2028** and the **2 Dec 2026** content-marking date, but **not** treat obligations as removed — only deferred (see `ai-act-high-risk` for the control build) [7][9]. *(Legal obligation — adopted, subject to OJ publication.)*
- **AI strand — content-provenance work continues.** Watermarking/marking of AI-generated content (Art. 50) is postponed, not cancelled; retain provenance/marking on the roadmap [9]. *(Best practice grounded in adopted obligation.)*
- **Data strand — do NOT re-architect consent yet.** The proposed one-click/6-month consent and browser-level preferences are **not law**; consent-management platforms must continue to enforce **consent-before-set** for non-essential cookies under the current ePrivacy Directive/PECR [3][10]. *(Editorial recommendation grounded in current law.)*
- **Data strand — design for optionality.** Where feasible, build consent tooling that **could** later honour browser/system-level signals (e.g. a Global-Privacy-Control-style mechanism) without hard-coding the unadopted six-month rule — an architecture hedge, not a compliance step [10]. *(Editorial recommendation.)*
- **AI-training data basis.** The proposed GDPR legitimate-interest basis for AI training is **not** yet available; current AI training on personal data still needs a valid existing GDPR basis and, where device-level tracking is involved, ePrivacy consent (see `eprivacy-foundations`) [2][3][10]. *(Legal obligation — current law.)*

# Hosting Considerations

- **Cookie/tag infrastructure unchanged for now.** Hosting, CDN and tag-management configurations must still gate non-essential cookies/SDKs on consent under the current ePrivacy regime; the proposed exemption expansion is not in force [3][10]. *(Legal obligation — current law.)*
- **Data Act consolidation is a watch item for cloud providers.** The proposed merger of the DGA/Open Data/Free-Flow instruments into the Data Act, plus SME cloud-switching exemptions and standard cloud contractual clauses, could change cloud-switching and data-portability obligations — but only if adopted; the current **Data Act** regime and its cloud-switching duties continue to apply meanwhile [4][5][10][13]. *(Proposal only; track.)*
- **Log/breach tooling.** The proposed streamlining of breach reporting may later reduce notification workload, but current GDPR Art. 33 timelines and NIS2/DORA reporting duties remain unchanged; do not de-scope incident tooling [2][10]. *(Legal obligation — current law.)*

# Game Hosting Considerations

- **In-game tracking SDKs.** Analytics/ads/telemetry SDKs that read or write device information remain subject to Art. 5(3) consent under current law; the proposed cookie reform does not change this today, and heightened scrutiny applies where children are likely users (see `eprivacy-foundations`) [3][10]. *(Legal obligation — current law.)*
- **Generative and image tools in games.** The **adopted** AI-strand prohibition on **nudifier/CSAM generators** is directly relevant to user-generated-content and AI image features; games offering such tooling must ensure they cannot produce prohibited content [7][9]. *(Legal obligation — adopted; see `ai-act-high-risk`.)*
- **AI companions/chatbots.** Art. 50 transparency still applies; only its **marking** timing for pre-existing systems shifts (to 2 Dec 2026) under the AI strand [9]. *(Legal obligation — adopted.)*

# AI Considerations

- **This document is the ePrivacy-topic view of a package with a large AI component.** The AI-Act-specific effects (high-risk dates, Art. 50 marking, new Art. 5 prohibition, bias-data and registration simplifications) are authoritatively covered in **`ai-act-foundations`** (overview) and **`ai-act-high-risk`** (mechanics); this document records them as **adopted** and cross-refers rather than duplicating [1][7][9]. *(Cross-reference.)*
- **Legitimate interest for AI training (proposed).** The data strand's proposed GDPR change would ease reliance on legitimate interest for training/operating AI — a significant potential shift for AI/ML data pipelines, but **not law**; continue to document a current lawful basis and run DPIAs [2][10]. *(Proposal only.)*
- **Bias-data processing (adopted).** The AI strand **reinstated the strict-necessity standard** for processing special-category data for bias detection/correction under AI Act Art. 10 — relevant to fairness engineering for high-risk systems [9]. *(Legal obligation — adopted; detail in `ai-act-high-risk`.)*
- **Consent remains the AI-tracking gate.** Because much AI personalisation depends on device-level tracking, the **current** ePrivacy consent rule (not the proposed reform) is the binding constraint for such data collection today [3][10]. *(Legal obligation — current law.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Separate the two strands in every internal briefing.** Treat the **AI strand as adopted law** and the **data strand as a proposal**; never let the shared name blur the status. *(EDITORIAL RECOMMENDATION.)* [9][10]
2. **Act on the adopted AI dates.** Re-plan high-risk readiness to **2 Dec 2027 / 2 Aug 2028** and content-marking to **2 Dec 2026**, confirm the OJ citation, and keep building controls — obligations are deferred, not removed. *(OBLIGATION once in force; EDITORIAL on planning.)* [7][9]
3. **Confirm no prohibited AI generation.** Ensure image/UGC/AI features cannot generate non-consensual intimate imagery or CSAM (new Art. 5 prohibition). *(OBLIGATION — adopted.)* [7][9]
4. **Keep current cookie compliance unchanged.** Maintain consent-before-set for non-essential cookies/SDKs, reject-as-easy-as-accept, and consent records under the current ePrivacy Directive/PECR. *(OBLIGATION — current law.)* [3]
5. **Do NOT pre-implement the proposed cookie regime.** No six-month one-click consent, no reliance on expanded exemptions, no browser-level-only consent, until (and unless) adopted. *(EDITORIAL RECOMMENDATION grounded in current law.)* [10]
6. **Do NOT rely on a legitimate-interest-for-AI basis yet.** Keep a documented current GDPR basis and DPIAs for AI training on personal data. *(OBLIGATION — current law.)* [2][10]
7. **Maintain a regulatory-change watch.** Track the OJ publication of the AI strand and the Council/Parliament progress of the data strand; assign an owner and review at least quarterly. *(BEST PRACTICE.)* [8][9][10]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Treating the whole "Digital Omnibus" as adopted (conflating strands) | High | High | Two strands, different status [9][10] | Status-labelled briefings; adopted-vs-proposed table | Low |
| R2 | Pre-implementing the proposed cookie regime (breaching current ePrivacy/PECR) | Medium | High | Data strand not law [3][10] | Freeze consent changes to current law; watch-list | Low |
| R3 | Treating high-risk AI obligations as removed rather than deferred | Medium | High | Adopted postponement [7][9] | Keep building controls; plan to 2027/2028 | Low |
| R4 | Relying on exact AI dates before OJ publication | Medium | Medium | Entry into force = OJ + 3 days [8][9] | Confirm OJ citation; monitor | Low |
| R5 | Missing the new Art. 5 nudifier/CSAM prohibition in AI/UGC features | Medium | Very High | Adopted new prohibition [7][9] | Feature review; content filters; policy | Low |
| R6 | Assuming a legitimate-interest-for-AI basis is available | Medium | High | Proposal only [2][10] | Maintain current lawful basis + DPIA | Low |
| R7 | Data strand adopted with changes not tracked (late compliance) | Medium | Medium | Live procedure [10] | Quarterly regulatory-change review | Medium |

# Implementation Roadmap

- **Phase 0 — Status map:** Produce an internal one-pager separating the **adopted** AI strand from the **proposed** data strand; brief stakeholders. *Effort:* Low.
- **Phase 1 — Act on adopted AI changes:** Re-baseline high-risk timelines (2 Dec 2027 / 2 Aug 2028), content-marking (2 Dec 2026), confirm OJ citation, and screen AI/UGC features against the new Art. 5 prohibition. *Effort:* Medium. *Depends on:* `ai-act-high-risk`.
- **Phase 2 — Hold current data/ePrivacy compliance:** Confirm cookie/consent tooling remains compliant with the **current** ePrivacy Directive/PECR; explicitly decide **not** to pre-implement the proposed regime. *Effort:* Low.
- **Phase 3 — Watch & adapt (data strand):** Track the Digital Omnibus Regulation through Parliament/Council; prepare (do not deploy) options for cookie/consent and AI-training-basis changes. *Effort:* Ongoing.
- **Phase 4 — Adopt on adoption:** When/if the data strand is adopted, re-plan consent architecture, DPIA/breach processes and Data Act obligations to the final text. *Effort:* Medium–High (contingent).

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | "Digital Omnibus" treated as a single vague change; status unknown. | No strand distinction; rumours drive action. |
| 2 | Managed | Aware there are two strands; adopted AI dates noted. | Basic timeline note; ad-hoc tracking. |
| 3 | Defined | Adopted-vs-proposed documented; AI changes actioned; cookie compliance held to current law. | Status one-pager; owner assigned; no pre-implementation. |
| 4 | Quantitatively Managed | Change-watch with review cadence and impact assessments for each proposed change. | Quarterly review; impact log; contingency plans drafted. |
| 5 | Optimising | Continuous horizon-scanning; ready-to-deploy plans for the data strand; integrated AI + data-protection governance. | Pre-built options; fast adoption path; cross-team governance. |

# Audit Questions

1. Does the organisation distinguish the **adopted** Digital Omnibus on AI from the **proposed** Digital Omnibus Regulation in its compliance records? *([9][10].)*
2. Have high-risk AI timelines been re-baselined to **2 Dec 2027 / 2 Aug 2028** and content-marking to **2 Dec 2026**, with OJ publication confirmed? *([7][9].)*
3. Are AI/UGC/image features screened against the new **Art. 5 nudifier/CSAM prohibition**? *([7][9].)*
4. Is current **cookie/consent** compliance held to the existing ePrivacy Directive/PECR, with no premature adoption of the proposed regime? *([3][10].)*
5. Is the organisation avoiding reliance on a **legitimate-interest-for-AI** basis that is not yet law? *([2][10].)*
6. Is there a **regulatory-change watch** with an owner and cadence for both strands? *([8][9][10].)*
7. Are contingency plans for the data strand prepared **without** being deployed? *([10].)*

# Implementation Checklist

- [ ] Adopted-vs-proposed status one-pager produced and circulated.
- [ ] High-risk AI timelines re-baselined (2 Dec 2027 / 2 Aug 2028); OJ citation confirmed.
- [ ] AI-content marking re-planned to 2 Dec 2026 for pre-existing systems.
- [ ] AI/UGC/image features screened against the new Art. 5 nudifier/CSAM prohibition.
- [ ] Current cookie/consent compliance verified against ePrivacy Directive/PECR (no pre-implementation).
- [ ] No reliance placed on the proposed legitimate-interest-for-AI basis; current basis + DPIA maintained.
- [ ] Regulatory-change watch established for both strands (owner + quarterly review).
- [ ] Contingency (not deployed) options drafted for cookie/consent and Data Act changes.

# References

*All external links verified HTTP 200 on 2026-07-11 (`sources_verified`) using `curl … -A "Mozilla/5.0 …"`, except the Council of the EU press release [8], whose site (consilium.europa.eu) bot-blocks automated requests and returns 403 to some clients while serving the page normally in-browser; the same facts are corroborated here via European Parliament sources [7][9] that verify HTTP 200. The Commission `policies/digital-omnibus` slug was found to be a soft-404 and is deliberately not cited; the authoritative Commission item is the AI-proposal library page [6].*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [2] **Regulation (EU) 2016/679 (GDPR), consolidated text.** EUR-Lex, CELEX 02016R0679-20160504. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [3] **Directive 2002/58/EC (ePrivacy Directive), consolidated text** (as amended by Directive 2009/136/EC). EUR-Lex, CELEX 02002L0058-20091219. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219
- [4] **Regulation (EU) 2023/2854 (Data Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2023/2854/oj
- [5] **Regulation (EU) 2022/868 (Data Governance Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/868/oj

## Regulatory Guidance

- [6] **Digital Omnibus on AI — regulation proposal** (COM(2025) 836; targeted AI Act simplification; follow-on "digital fitness check" noted). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/library/digital-omnibus-ai-regulation-proposal
- [7] **AI Act: EP approves simplification measures and "nudifier" app ban** (plenary adoption 16 June 2026, 423–57–174; postponed high-risk dates; new Art. 5 prohibition). European Parliament press release. https://www.europarl.europa.eu/news/en/press-room/20260611IPR45207/ai-act-ep-approves-simplification-measures-and-nudifier-app-ban
- [8] **Artificial Intelligence: Council gives final green light to simplify and streamline rules** (Council final adoption, 29 June 2026; entry into force on the third day after OJ publication). Council of the EU. *(Bot-blocks automated checks — verify in-browser; corroborated by [7][9].)* https://www.consilium.europa.eu/en/press/press-releases/2026/06/29/artificial-intelligence-council-gives-final-green-light-to-simplify-and-streamline-rules/
- [9] **Digital Omnibus on AI — Legislative Train Schedule** (procedure 2025/0359(COD); Commission proposal 19 Nov 2025; trilogue 7 May 2026; Coreper 13 May 2026; plenary 16 Jun 2026; fixed dates 2 Dec 2027 / 2 Aug 2028; content-marking 2 Dec 2026; nudifier/CSAM prohibition; bias-data strict necessity). European Parliament. https://www.europarl.europa.eu/legislative-train/package-digital-package/file-digital-omnibus-on-ai
- [10] **Digital package / Digital Omnibus Regulation Proposal** (data strand; COM(2025) 837; procedure 2025/0360(COD); cookie-consent migration into the GDPR, one-click/6-month and browser-level consent, legitimate-interest-for-AI, DPIA/breach streamlining, Data Act consolidation; status: proposal — EESC 18 Mar 2026, CoR 7 May 2026). European Parliament, Legislative Train Schedule. https://www.europarl.europa.eu/legislative-train/theme-a-new-plan-for-europe-s-sustainable-prosperity-and-competitiveness/file-digital-package
- [11] **AI Act: deal on simplification measures, ban on "nudifier" apps** (trilogue provisional agreement, 7 May 2026). European Parliament press release. https://www.europarl.europa.eu/news/en/press-room/20260427IPR42011/ai-act-deal-on-simplification-measures-ban-on-nudifier-apps
- [12] **ePrivacy Regulation policy page** (context for the cookie-rule migration route following the ePrivacy Regulation's withdrawal). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/eprivacy-regulation
- [13] **Data Act (policy page)** (context for the proposed Data Act consolidation). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/data-act
- [14] **Proposal for a Regulation on Privacy and Electronic Communications — status: withdrawn** (Commission approved 16 July 2025; OJ 6 October 2025). European Parliament, Legislative Train Schedule. https://www.europarl.europa.eu/legislative-train/theme-connected-digital-single-market/file-jd-e-privacy-reform

## Standards

Not Applicable — the Digital Omnibus is a legislative simplification package; no ISO/IEC, NIST, ETSI or CEN-CENELEC standard governs it directly. Standards relevant to the amended instruments are cited in their own documents (e.g. CEN-CENELEC AI-Act standards in `ai-act-high-risk`).

## Academic Sources

Not Applicable — this is a live legislative-status document relying on primary legislation and official EU institutional sources; peer-reviewed analysis of the Omnibus was not yet available and is unnecessary for the status account. Academic critique of the underlying regimes is cited in `ai-act-high-risk` and `eprivacy-foundations`.

# Further Reading

*Non-authoritative or contextual; provided for orientation only.*

- European Commission — Shaping Europe's Digital Future (digital simplification landing). https://digital-strategy.ec.europa.eu/en
- `eprivacy-foundations` (this repository) — the current cookie/consent regime the data strand would amend.
- `ai-act-foundations` / `ai-act-high-risk` (this repository) — the AI-Act detail the AI strand amends.

# Related Documents

- `eprivacy-foundations` — **parent**; defers the cookie-rule migration to this document (**prerequisite reading**).
- `ai-act-foundations` — AI-Act overview recording the AI Omnibus adoption (v1.1.0); this document cross-refers it.
- `ai-act-high-risk` — high-risk mechanics and the amended application timeline in detail.
- `gdpr-foundations` — the GDPR into which the cookie rules would (proposed) migrate.
- `pecr-detail` — UK PECR in depth, incl. DUAA changes (planned).
- `data-act-foundations` — the Data Act consolidation the data strand proposes (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Deep-dive on the 2025–2026 EU Digital Omnibus. **Live-verified the two-strand split and their differing status:** the **Digital Omnibus on AI** (COM(2025) 836; 2025/0359(COD)) is **ADOPTED** (EP plenary 16 Jun 2026; Council 29 Jun 2026; entry into force OJ +3 days), while the **Digital Omnibus Regulation** (COM(2025) 837; 2025/0360(COD); cookie-consent migration into the GDPR, one-click/6-month consent, legitimate-interest-for-AI, DPIA/breach streamlining, Data Act consolidation) remains a **PROPOSAL** (EESC 18 Mar 2026, CoR 7 May 2026; not adopted). Sources: EUR-Lex (AI Act, GDPR, ePrivacy, Data Act, DGA), European Commission library page, European Parliament press releases and Legislative Train. All external links checked HTTP 200 on 2026-07-11; Council 29 Jun 2026 release corroborated via EP sources (consilium.europa.eu bot-blocks curl); Commission `policies/digital-omnibus` slug found to be a soft-404 and deliberately not cited. Confidence Medium given topic volatility. | — |
</content>
</invoke>
