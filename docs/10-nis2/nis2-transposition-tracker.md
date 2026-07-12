---
id: nis2-transposition-tracker
title: "NIS2: National Transposition Tracker & Divergence"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: NIS2
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [nis2-foundations, nis2-incident-reporting, dora-foundations, cybersecurity-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
tags: [nis2, transposition, member-states, divergence, infringement, cjeu, registration, sanctions, management-liability, tracker]
legal_basis: Directive (EU) 2022/2555; Commission Implementing Regulation (EU) 2024/2690
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | nis2-transposition-tracker |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.17.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. **This is a dated snapshot of a fast-moving legislative process — verify before relying.** NIS2 is a **Directive**, so the rules that bind any organisation are the **national transposition laws**, not the Directive text; those laws are being adopted at different times and with material national divergences. The transposition deadline was **17 October 2024** (Art. 41), most Member States missed it, and enforcement is live: the Commission issued reasoned opinions to **19 Member States on 7 May 2025** and, on **8–9 July 2026, referred Ireland, Spain, France and the Netherlands to the Court of Justice** [1][5][6]. Individual-state status below is drawn from the Commission's own **state-of-play page (last updated 1 July 2025)** [4] plus later official confirmations; **any status not tied to an official source is marked "status as of 2026-07; verify"** and must be confirmed against the relevant national gazette/competent authority before use.

# Executive Summary

This document is a **transposition tracker**: a sourced, dated snapshot of **which EU Member States have turned the NIS2 Directive (Directive (EU) 2022/2555) into national law**, and of the **axes along which those national laws diverge**. It exists because NIS2 is a **Directive** — it binds Member States as to the result but takes legal effect against organisations only through **national transposition** (Art. 41), so an entity operating in several Member States faces **several different NIS2 regimes with different registration portals, thresholds, supervisors, sanctions and management-liability rules** [1][7].

The single most important fact is that **transposition is late and uneven**. The deadline was **17 October 2024**; most Member States missed it. The Commission opened infringement proceedings (letters of formal notice, November 2024), escalated to **reasoned opinions against 19 Member States on 7 May 2025**, and on **8–9 July 2026 referred Ireland, Spain, France and the Netherlands to the Court of Justice** with a request for financial penalties [5][6]. A number of large economies transposed only in **late 2025 / 2026** — Germany's **NIS2 implementation act (NIS2UmsuCG / BSIG)** applies from **6 December 2025** [9] — while **France and the Netherlands** were, at this document's date, still finalising their laws [6].

Because the value of this document is an **honest snapshot rather than a false-precision table**, individual-state status is tied to official sources where available and otherwise flagged for verification. Confidence is **Medium**: the *legal framework* for transposition (Arts. 41, 26, 3(4), 34) and the *enforcement milestones* are High-confidence and firmly sourced, but the *per-state enactment detail* is volatile and, for several states, could not be confirmed from a primary source as at 2026-07 and is marked accordingly. Read this alongside `nis2-foundations` (scope and obligations) and `nis2-incident-reporting` (the Article 23 reporting cascade).

# Key Takeaways

- NIS2 is a **Directive**: it binds through **national transposition** (Art. 41), so a multi-country entity faces **as many NIS2 regimes as the Member States it operates in**, diverging on registration, thresholds, supervision, sanctions and management liability [1][7]. *(Legal obligation / interpretation.)*
- The **transposition deadline was 17 October 2024** (Art. 41(1)); most Member States missed it, and the Directive applies against organisations only via the transposing statute [1]. *(Legal obligation.)*
- **Enforcement is live:** letters of formal notice (Nov 2024) → **reasoned opinions to 19 Member States (7 May 2025)** → **CJEU referrals of Ireland, Spain, France and the Netherlands (8–9 July 2026)** with a request for lump-sum and daily penalties [5][6]. *(Confirmed against official sources.)*
- The **Commission's state-of-play page is the authoritative but dynamic index** of who has notified transposition; it was **last updated 1 July 2025** and must be re-checked, not memorised [4]. *(Regulatory interpretation.)*
- **Adopted examples are firmly sourced:** **Italy** transposed via **Decreto Legislativo 138/2024** (in force 16 October 2024) [3][10]; **Germany's NIS2UmsuCG/BSIG** applies from **6 December 2025** with registration by **6 March 2026** [9]. *(Legal fact — sourced.)*
- **The eight Member States not among the 7 May 2025 reasoned-opinion recipients** — Belgium, Croatia, Greece, Italy, Lithuania, Malta, Romania and Slovakia — had by that date **notified transposition measures** to the Commission (a proxy for "adopted", not a guarantee of complete/correct transposition) [4][5]. *(Interpretation from the enforcement selection.)*
- **National laws diverge on defined axes:** entity **identification/registration** (portals and deadlines), **scope/thresholds**, **supervisory architecture**, **sanction ceilings**, and **management-body/CEO liability** (some states add director disqualification or personal fines) [1][9]. *(Interpretation.)*
- The **harmonised floor still holds:** Art. 3 classification, the Art. 3(4) national list (due 17 April 2025), Art. 26 jurisdiction, Art. 34 sanction minima, and the **Implementing Regulation (EU) 2024/2690** thresholds for digital entities apply in every Member State regardless of transposition timing [1][2]. *(Legal obligation.)*
- **Confidence is Medium and the snapshot is dated:** per-state enactment detail is volatile; **verify each Member State against its national gazette/competent authority** before relying on any row here [4]. *(Editorial caution.)*

# Purpose

This document supports three tasks. First, **legal and compliance planning** — telling a multi-jurisdiction organisation, for each Member State it operates in, whether a NIS2 transposing law is in force and where to find it. Second, **divergence analysis** — identifying the axes (registration, thresholds, supervision, sanctions, management liability) on which national laws differ, so a group can design a compliance baseline plus per-country deltas. Third, **enforcement-risk monitoring** — tracking the Commission's infringement pipeline so a group understands where the legal position is still unsettled. It is the national-comparison sub-topic promised by `nis2-foundations` and `nis2-incident-reporting`, and it deliberately stops short of a full country-by-country legal analysis (that is per-jurisdiction work), giving instead a **sourced, dated state-of-play with an explicit verification caveat**.

# Scope

**In scope:** The Directive's transposition provisions (Art. 41 deadline; Art. 3/Art. 3(4) identification and national listing; Art. 26 jurisdiction; Art. 34 sanction minima); the **status of national transposition** as at 2026-07, tied to official sources where available; the **Commission infringement timeline** (formal notices, reasoned opinions, CJEU referrals); the **axes of national divergence**; and the practical implications of divergence for multi-country compliance. A **per-Member-State snapshot table** and a **divergence-axes table** are included.

**Out of scope:** A full legal analysis of any single national law (deferred to per-jurisdiction work); the substantive **Article 21 risk-management measures** and **Article 23 reporting cascade** → `nis2-foundations` and `nis2-incident-reporting`; the **Implementing Regulation (EU) 2024/2690** technical detail (covered in `nis2-incident-reporting`); the **DORA** financial-sector lex specialis → `dora-foundations`; and sector-by-sector Annex I/II scope → planned `nis2-sectors`.

**Assumptions:** The reader has read `nis2-foundations` and understands the essential/important distinction, the size-cap rule, and the Directive-vs-Regulation point. **This document is a snapshot**: legislative status changes weekly, so every per-state row is a starting point for verification, not a settled conclusion.

# Definitions

*Shared terms (essential entity, important entity, significant incident, CSIRT, lex specialis) are in `GLOSSARY.md`. Transposition-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Transposition | The process by which a Member State gives effect to an EU Directive in national law; under Art. 41 NIS2, Member States had to **adopt and publish** the measures by **17 October 2024** and apply them from **18 October 2024**. | [1] |
| Notification of transposition | A Member State's formal communication to the Commission of the national measures transposing a Directive; the Commission's assessment of whether this is **complete and correct** is separate and may follow later. | [1][4] |
| Letter of formal notice | The first stage of an EU infringement procedure (Art. 258 TFEU): the Commission's formal request for a Member State's observations on a suspected breach (here, non-communication of transposition). | [5] |
| Reasoned opinion | The second infringement stage: a formal Commission statement of the alleged breach requiring the Member State to comply within a set period (typically two months) or face referral to the Court of Justice. | [5] |
| Court of Justice referral | The Commission's action bringing a Member State before the CJEU for failure to fulfil a Treaty obligation; for non-communication of transposition the Commission may request **lump-sum and daily penalty payments** (Art. 260(3) TFEU). | [6] |
| National competent authority | The authority designated by a Member State under NIS2 to supervise and enforce the transposing law (e.g., BSI in Germany; ACN in Italy). | [1][9][10] |
| State-of-play (transposition) | The Commission's **dynamic** record of which Member States have notified transposition; authoritative but time-stamped and subject to change. | [4] |

# Background

The original NIS Directive left Member States wide latitude, producing fragmented national regimes. NIS2 (Directive (EU) 2022/2555) was designed to raise and **harmonise** the baseline, but it remains a **Directive**: Article 41 required Member States to adopt and publish transposing measures by **17 October 2024** and to apply them from **18 October 2024** [1]. In practice the deadline was **widely missed**. The Commission's response has followed the standard infringement escalation [5][6]:

- **November 2024** — letters of formal notice to the Member States that had not communicated full transposition.
- **7 May 2025** — **reasoned opinions to 19 Member States** (Bulgaria, Czechia, Denmark, Germany, Estonia, Ireland, Spain, France, Cyprus, Latvia, Luxembourg, Hungary, the Netherlands, Austria, Poland, Portugal, Slovenia, Finland and Sweden) for failing to notify full transposition [5].
- **8–9 July 2026** — **referral of Ireland, Spain, France and the Netherlands to the Court of Justice**, with a request for financial penalties, for continued failure to transpose [6].

Meanwhile national laws have been arriving on very different timelines. Some Member States transposed on or near the deadline (for example, **Italy** via **Decreto Legislativo 138/2024**, in force 16 October 2024 [3][10]); several large economies transposed only in **late 2025/2026** (for example, **Germany's NIS2UmsuCG/BSIG**, applying from **6 December 2025** [9]); and, at this document's date, **France and the Netherlands** were still finalising their laws [6]. The result is a patchwork that this tracker records as a **dated snapshot**.

# Legal Framework

The transposition provisions and the harmonised elements that survive divergence are set by the Directive itself; the binding operational rules are the **national laws** [1].

- **Art. 41 (Transposition)** — Member States adopt and publish the measures by **17 October 2024** and apply them from **18 October 2024**; they communicate the text to the Commission [1].
- **Art. 3 (Essential/important entities)** and **Art. 3(4)** — Member States classify entities and establish a **list of essential and important entities** (and of entities providing domain-name registration services), with the first list due by **17 April 2025** [1].
- **Art. 26 (Jurisdiction and territoriality)** — as a rule an entity is under the jurisdiction of the Member State of its **establishment**; certain digital providers (DNS, TLD, cloud, data-centre, CDN, managed/managed-security providers, online marketplaces/search engines/social platforms) are deemed under the jurisdiction of the Member State of their **main establishment** in the EU, which reduces (but does not eliminate) multi-country overlap [1].
- **Art. 34 (Administrative fines)** — sets **minimum maxima**: for essential entities at least **€10 million or 2%** of worldwide annual turnover (whichever is higher), and for important entities at least **€7 million or 1.4%** [1]. National laws may set higher ceilings and add periodic penalties.
- **Implementing Regulation (EU) 2024/2690** — directly applicable in all Member States; it fixes technical/methodological requirements and **significant-incident thresholds** for defined digital entities, so this layer does **not** diverge by transposition [2].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 41(1) | Adopt and publish transposing measures by **17 October 2024**; apply from **18 October 2024**. | [1] |
| Art. 41(2) | Communicate the text of the transposing measures to the Commission. | [1] |
| Art. 3(1)–(3) | Classify entities as **essential** or **important**. | [1] |
| Art. 3(4) | Establish and maintain a **national list** of essential/important entities (and domain-name registration providers); first list by **17 April 2025**. | [1] |
| Art. 26 | Jurisdiction — establishment rule generally; **main-establishment** rule for specified digital providers. | [1] |
| Art. 27 | Registration information submitted (for certain digital providers) to feed the ENISA registry. | [1] |
| Art. 34 | Administrative fines — floors of **≥ €10m/2%** (essential) and **≥ €7m/1.4%** (important). | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 4 area | The Directive seeks to remove divergences by setting minimum rules — but as a Directive it still depends on national transposition, which reintroduces variation in detail. | [1] |
| Recital 128 area | Member States' transposition and the communication of measures to the Commission; the basis for the Commission's state-of-play monitoring. | [1] |

## Relevant Case Law

**Emerging, not settled.** There is no CJEU case law interpreting NIS2's substantive obligations. The only NIS2 litigation to date is the Commission's **infringement actions against Member States for non-transposition** — the referrals of Ireland, Spain, France and the Netherlands to the Court of Justice (8–9 July 2026) under Art. 258/260 TFEU, which concern the **duty to transpose**, not the meaning of the entity obligations [6]. These are tracked here as **enforcement events**, and any judgment (including any financial penalty) should be treated as a future development to verify [6]. [1]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text) — and a DATED SNAPSHOT.**

The **Commission's transposition state-of-play page is the authoritative index** of who has notified transposition, but it is **dynamic** and was **last updated 1 July 2025** at this document's verification date [4]. The reasoned-opinion list (7 May 2025) and the CJEU referrals (8–9 July 2026) are firm, sourced enforcement milestones [5][6]. **ENISA** additionally maintains topic-level material tracking NIS2 implementation and national cooperation, useful for cross-checking the Commission index [8]. Everything else below is a **best-effort snapshot**; rows not tied to an official source are marked **"verify"**.

## Per-Member-State snapshot (status as of 2026-07)

*Categories are derived from official signals: (A) referral to the CJEU [6]; (B) inclusion in the 7 May 2025 reasoned opinion, i.e. **not** having notified full transposition on that date [5]; (C) **absence** from the reasoned-opinion list, i.e. transposition measures notified to the Commission by that date [4][5]. Category is **not** a substitute for checking the national gazette.*

| Member State | Snapshot status (2026-07) | Basis / note | Source |
|--------------|---------------------------|--------------|--------|
| Belgium | Transposed (early) | Not in the reasoned-opinion list; national NIS2 framework reported in force from 18 Oct 2024 — **verify law reference in the Moniteur belge** | [4][5] |
| Croatia | Transposed | Not in the reasoned-opinion list | [4][5] |
| Greece | Transposed | Not in the reasoned-opinion list | [4][5] |
| Italy | Transposed | **Decreto Legislativo 138/2024**, in force 16 Oct 2024 (ACN competent authority) | [3][10] |
| Lithuania | Transposed | Not in the reasoned-opinion list | [4][5] |
| Malta | Transposed | Not in the reasoned-opinion list | [4][5] |
| Romania | Transposed | Not in the reasoned-opinion list | [4][5] |
| Slovakia | Transposed | Not in the reasoned-opinion list | [4][5] |
| Germany | Transposed (late) | Reasoned opinion May 2025; **NIS2UmsuCG/BSIG applies from 6 Dec 2025**, registration by 6 Mar 2026 (BSI) | [5][9] |
| Austria | Reasoned opinion May 2025 | Progressing since; **status as of 2026-07; verify** | [5] |
| Bulgaria | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Cyprus | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Czechia | Reasoned opinion May 2025 | Cybersecurity Act reported adopted 2025; **status as of 2026-07; verify** | [5] |
| Denmark | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Estonia | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Finland | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Hungary | Reasoned opinion May 2025 | National framework reported in force; **status as of 2026-07; verify** | [5] |
| Latvia | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Luxembourg | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Poland | Reasoned opinion May 2025 | Amendment to the Act on the National Cybersecurity System in progress; **status as of 2026-07; verify** | [5] |
| Portugal | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Slovenia | Reasoned opinion May 2025 | **status as of 2026-07; verify** | [5] |
| Sweden | Reasoned opinion May 2025 | Cybersecurity Act progressing; **status as of 2026-07; verify** | [5] |
| Ireland | **Referred to CJEU (8–9 Jul 2026)** — not transposed | National Cyber Security Bill in progress at referral | [6] |
| Spain | **Referred to CJEU (8–9 Jul 2026)** — not transposed | Draft law in progress at referral | [6] |
| France | **Referred to CJEU (8–9 Jul 2026)** — not transposed | Bill passed first reading (National Assembly, Dec 2025); not yet in force | [6] |
| Netherlands | **Referred to CJEU (8–9 Jul 2026)** — not transposed | Cyberbeveiligingswet adopted by the Tweede Kamer (2026); not yet in force at referral | [6] |

*The four CJEU-referred states were the clearest laggards at 2026-07; the "reasoned opinion" cohort is the volatile middle where several states (notably Germany) have since transposed — each **must be re-checked** against [4] and the national competent authority.* [4]

## Axes of national divergence

*Even where NIS2 sets a harmonised floor, national laws diverge on the following axes — the practical reason a group needs per-country deltas, not one EU policy.*

| Axis | NIS2 floor (same everywhere) | Where national laws diverge | Source |
|------|------------------------------|-----------------------------|--------|
| Entity identification & registration | Art. 3 classification; Art. 3(4) national list (due 17 Apr 2025); Art. 27 registration for some digital providers | Self-registration **portals and deadlines** differ (e.g., Germany registration by 6 Mar 2026); some states self-identify, others operate authority-led identification | [1][4][9] |
| Scope & thresholds | Size-cap (medium/large) + in-scope-regardless-of-size cases; Reg 2024/2690 thresholds for digital entities | National **add-ons** — extra sectors, wider public-administration scope, lower size thresholds in places | [1][2] |
| Supervisory architecture | Ex-ante + ex-post for essential (Art. 32); ex-post for important (Art. 33) | **Single national authority vs sectoral authorities**; differing audit, certification and conformity-assessment regimes (some recognise ISO/IEC 27001 or national frameworks as evidence) | [1][4][11] |
| Sanctions | Art. 34 floors: ≥ €10m/2% (essential); ≥ €7m/1.4% (important) | Exact **ceilings, periodic penalties and criminal exposure** vary by Member State | [1] |
| Management-body / CEO liability | Art. 20 approval, oversight and training; liability for infringements | Some states add **director disqualification** (reported in the Netherlands) or **personal fines** on management (reported in Germany) | [1][9] |

## Standards and reference frameworks

Several transposing laws point entities to recognised frameworks (for example national baseline schemes, or **ISO/IEC 27001**) as a way to evidence the Art. 21 measures; using such a framework eases multi-country audits but **does not by itself satisfy any national law** [11]. *(Best practice.)*

# Technical Considerations

- **Treat NIS2 as N regimes, not one** — build a compliance baseline from the harmonised floor (Art. 3 classification, Reg 2024/2690 thresholds) and maintain **per-country deltas** for registration, supervision, sanctions and management-liability variations [1][2][4]. *(Best practice.)*
- **Instrument registration per Member State** — track each national **registration portal and deadline** (they differ; e.g., Germany's 6 March 2026 registration cut-off) and the Art. 3(4) national listing where applicable [1][9]. *(Legal obligation where transposed.)*
- **Use main-establishment analysis to reduce overlap** — for in-scope digital providers, Art. 26 concentrates jurisdiction at the **main establishment**, so a group should determine where its cybersecurity decisions are taken to identify the lead competent authority/CSIRT [1]. *(Legal obligation for those entities.)*
- **Do not wait for transposition to build controls** — the Art. 21 measures and Reg 2024/2690 thresholds are stable across states, so engineering can proceed even where the national law is not yet in force; only the **registration, reporting-portal and supervisory** wiring is state-specific [1][2]. *(Best practice.)*

# Hosting Considerations

- **Cloud, data-centre, CDN, DNS and managed-security providers benefit most from Art. 26** — the main-establishment rule means such a provider is primarily supervised by **one** Member State's authority rather than all, but it must still identify **which** and register there [1]. *(Legal obligation — assess main establishment.)*
- **Multi-region hosting spans multiple transposition states** — a provider with establishments in several Member States should map, per establishment, whether the transposing law is in force and which authority/CSIRT applies, using the Commission state-of-play as the entry point [4]. *(Best practice.)*
- **Customer-driven propagation is state-agnostic** — in-scope customers impose supply-chain security and incident-cooperation requirements regardless of where transposition stands, so hosts should prepare for these before their own national law lands [1]. *(Best practice.)*

# Game Hosting Considerations

- **Gaming is not an Annex I/II sector**, so a studio or game-server operator is generally out of NIS2 scope by virtue of gaming alone — and transposition timing does not change that (see `nis2-foundations`) [1][7]. *(Interpretation.)*
- **Infrastructure roles remain the trigger** — where a game host also runs cloud/CDN/DNS/managed-security services, those activities are in scope, and the operator must identify the **relevant Member State's** transposing law and registration route via Art. 26 main establishment [1]. *(Legal obligation — assess by activity.)*
- **Upstream providers may be in different transposition states** — a game host's cloud/CDN suppliers may be regulated under an already-in-force national law while the host's own state lags; plan supplier assurance around the supplier's regime, not the host's [4]. *(Best practice.)*

# AI Considerations

- **AI systems ride the same transposition patchwork** — where an in-scope entity operates AI/ML systems, the applicable duties are those of the **national transposing law**, so the same AI system may be governed by different NIS2 regimes across states [1][4]. *(Legal obligation / interpretation.)*
- **AI Act overlap is uniform, NIS2 detail is not** — the AI Act is a **Regulation** (directly applicable and uniform), whereas NIS2's entity duties vary by transposition; an organisation should not assume NIS2 compliance is identical across the states where its AI operates (see `nis2-foundations`) [1]. *(Cross-reference.)*
- **Registration and reporting wiring is state-specific for AI incidents too** — an AI-related significant incident is reported through the **national** CSIRT/portal of the applicable Member State, on the harmonised Art. 23 clock detailed in `nis2-incident-reporting` [1][2]. *(Legal obligation.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Enumerate your Member States** — list every Member State in which the group has an establishment or in-scope activity; this defines the set of transposition regimes to track. *(OBLIGATION — foundational.)* [1]
2. **Check the Commission state-of-play first, then the national source** — use the Commission page [4] as the index, then confirm the **actual transposing statute and competent authority** in each state's gazette/authority. *(OBLIGATION where transposed; BEST PRACTICE to monitor where not.)* [4]
3. **Register per state and meet the national list** — complete each national **registration** and any Art. 3(4) listing by the applicable national deadline (deadlines differ — e.g., Germany 6 March 2026). *(OBLIGATION where transposed.)* [1][9]
4. **Resolve jurisdiction via Art. 26** — for digital providers, determine the **main establishment** to identify the lead competent authority and avoid duplicative registration. *(OBLIGATION for those entities.)* [1]
5. **Build a baseline-plus-deltas control model** — implement the harmonised Art. 21 / Reg 2024/2690 layer once, then layer per-country deltas for supervision, sanctions and management liability. *(BEST PRACTICE.)* [1][2]
6. **Track the divergence axes that carry personal exposure** — especially **management-body/CEO liability** (director disqualification, personal fines in some states); brief the board accordingly. *(OBLIGATION / EDITORIAL RECOMMENDATION.)* [1][9]
7. **Monitor the infringement pipeline** — for laggard states (currently the CJEU-referred four), watch for the law's entry into force and any CJEU penalty, and be ready to switch on obligations quickly. *(EDITORIAL RECOMMENDATION.)* [6]
8. **Re-verify on a cadence** — because this snapshot ages quickly, re-check status at least quarterly and before any go-live in a given Member State. *(EDITORIAL RECOMMENDATION.)* [4]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Relying on the Directive where the national law is not yet in force or differs | High | High | Directive character; Art. 41; uneven transposition [1][4] | Confirm the transposing statute per state; baseline-plus-deltas model | Medium |
| R2 | Missing a national **registration** deadline (they differ by state) | Medium | High | Art. 3(4); national portals [1][9] | Per-state registration tracker with deadlines and owners | Low |
| R3 | Treating this dated snapshot as current | Medium | High | Volatile legislative process [4] | Quarterly re-verification; check Commission page + national source before reliance | Low |
| R4 | Under-briefing the board on **management-liability** divergence (disqualification/personal fines) | Medium | High | Art. 20; national add-ons [1][9] | Board briefing on per-state liability; documented oversight | Low |
| R5 | Duplicative or wrong-authority registration for digital providers | Medium | Medium | Art. 26 main-establishment rule [1] | Main-establishment analysis; single lead authority | Low |
| R6 | Assuming uniform sanctions across states | Low | Medium | Art. 34 sets floors, not ceilings [1] | Per-state penalty mapping | Low |
| R7 | Acting on an unverified per-state row in this tracker | Medium | High | Rows marked "verify" [4] | Never rely on a "verify" row without national confirmation | Low |

# Implementation Roadmap

- **Phase 0 — Footprint mapping:** Enumerate Member States of establishment/activity and in-scope entity types. *Effort:* Low.
- **Phase 1 — Status verification:** For each state, confirm transposition status via the Commission page [4] and the national gazette/authority; record the statute and competent authority. *Effort:* Medium.
- **Phase 2 — Registration & jurisdiction:** Determine Art. 26 main establishment; complete national registrations and Art. 3(4) listings by each deadline. *Effort:* Medium.
- **Phase 3 — Baseline controls:** Implement the harmonised Art. 21 / Reg 2024/2690 layer group-wide. *Effort:* High.
- **Phase 4 — Per-country deltas:** Layer supervision, sanction and management-liability variations; brief the board. *Effort:* Medium.
- **Phase 5 — Monitor & re-verify:** Track the infringement pipeline and re-verify status on a quarterly cadence. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No view of which national NIS2 laws apply. | No footprint map; Directive assumed uniform. |
| 2 | Managed | Footprint mapped; transposition status checked per state. | Per-state status register exists. |
| 3 | Defined | Registrations completed; baseline controls plus per-country deltas implemented. | National registrations done; delta matrix maintained. |
| 4 | Quantitatively Managed | Divergence tracked with metrics; board briefed on liability variations; re-verification cadence enforced. | Delta KPIs; quarterly re-verify; board records. |
| 5 | Optimising | Automated monitoring of transposition/enforcement feeds compliance; rapid switch-on for laggard states. | Change-triggered updates; integrated NIS2/DORA governance. |

# Audit Questions

1. For each Member State of operation, has the applicable **transposing statute** (or its absence) been confirmed against an official source, and when? *(Art. 41; state-of-play [1][4].)*
2. How is the group's **registration** completed per state, and are the (differing) national deadlines tracked with owners? *(Art. 3(4) [1][9].)*
3. How was **jurisdiction** determined for in-scope digital providers, and is registration concentrated at the main establishment? *(Art. 26 [1].)*
4. How does the group maintain a **baseline-plus-deltas** model that separates the harmonised floor from national variations? *(Arts. 21, 34; Reg 2024/2690 [1][2].)*
5. Has the board been briefed on **management-liability divergence** (e.g., director disqualification, personal fines) in the relevant states? *(Art. 20 [1][9].)*
6. How is the **infringement pipeline** monitored for laggard states, and what is the switch-on plan when their laws enter into force? *(CJEU referrals [6].)*
7. How often is this **status re-verified**, and is reliance on any "verify"-flagged row prohibited without national confirmation? *(State-of-play volatility [4].)*

# Implementation Checklist

- [ ] Member-State footprint enumerated (establishments and in-scope activities).
- [ ] Transposition status confirmed per state against the Commission page and the national gazette/authority.
- [ ] Transposing statute and competent authority/CSIRT recorded per state.
- [ ] Art. 26 main-establishment analysis completed for digital providers.
- [ ] National registrations and Art. 3(4) listings completed by each national deadline.
- [ ] Harmonised baseline (Art. 21 / Reg 2024/2690) implemented group-wide.
- [ ] Per-country delta matrix (supervision, sanctions, management liability) maintained.
- [ ] Board briefed on management-liability divergence.
- [ ] Infringement pipeline monitored; switch-on plan for laggard states.
- [ ] Quarterly re-verification cadence in place; reliance on unverified rows prohibited.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`). This is a **dated snapshot**: the Commission state-of-play page [4] was last updated 1 July 2025 at that date and is dynamic — re-check before relying on any per-state status.*

## Primary Sources

- [1] **Directive (EU) 2022/2555 (NIS2 Directive)** — Arts. 41 (transposition), 3/3(4) (classification and national list), 26 (jurisdiction), 27 (registration), 34 (fines). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj
- [2] **Commission Implementing Regulation (EU) 2024/2690** — technical/methodological requirements and significant-incident thresholds for defined digital entities (directly applicable in all Member States). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_impl/2024/2690/oj
- [3] **Italy — Decreto Legislativo 4 September 2024, n. 138** (transposition of NIS2; in force 16 October 2024). Gazzetta Ufficiale della Repubblica Italiana. https://www.gazzettaufficiale.it/eli/id/2024/10/01/24G00155/sg

## Regulatory Guidance

- [4] **NIS2 Directive transposition in EU countries** (state-of-play of Member State transposition; **last updated 1 July 2025** — dynamic). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/nis-transposition
- [5] **Commission calls on 19 Member States to fully transpose the NIS2 Directive** (reasoned opinions, 7 May 2025; names the 19 states). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-calls-19-member-states-fully-transpose-nis2-directive
- [6] **Commission refers Ireland, Spain, France and the Netherlands to the Court of Justice for failing to transpose the cybersecurity rules** (IP/26/1499, 8–9 July 2026; request for lump-sum and daily penalties). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_26_1499
- [7] **NIS2 Directive: securing network and information systems** (policy overview — Directive character and 18 sectors). European Commission. https://digital-strategy.ec.europa.eu/en/policies/nis2-directive
- [8] **NIS Directive 2 (NIS2) — topic page.** ENISA. https://www.enisa.europa.eu/topics/state-of-cybersecurity-in-the-eu/cybersecurity-policies/nis-directive-2
- [9] **NIS-2 (BSIG / NIS2-Umsetzungsgesetz)** — Germany's national transposition; obligations apply from 6 December 2025, registration by 6 March 2026. Bundesamt für Sicherheit in der Informationstechnik (BSI). https://www.bsi.bund.de/dok/nis-2
- [10] **NIS (Decreto Legislativo 138/2024)** — Italy's national authority page (ACN as competent authority; 18 sectors). Agenzia per la Cybersicurezza Nazionale (ACN). https://www.acn.gov.it/portale/nis

## Standards

- [11] **ISO/IEC 27001:2022** — Information security management systems; recognised in several transposing laws as evidence for the Art. 21 measures. ISO. https://www.iso.org/standard/27001

## Academic Sources

Not Applicable — this tracker relies on primary legislation, official national gazettes/authorities and European Commission enforcement sources. Peer-reviewed analysis of NIS2 transposition divergence may be cited in future revisions.

# Further Reading

*Non-authoritative; provided for orientation only. Independent transposition trackers are useful for triangulation but must be checked against official sources.*

- ECSO — NIS2 Directive Transposition Tracker. https://ecs-org.eu/activities/nis2-directive-transposition-tracker/
- Wavestone — NIS2 transposition status across European countries. https://www.wavestone.com/en/insight/nis-2-european-countries-transposing-directive/

# Related Documents

- `nis2-foundations` — parent reference; scope, entity classification, Art. 21 measures, and the wider obligation set (explains the harmonised layer this tracker complements).
- `nis2-incident-reporting` — the Art. 23 reporting cascade and Implementing Regulation (EU) 2024/2690 thresholds (the reporting layer that is harmonised across transposition states).
- `dora-foundations` — the financial-sector **lex specialis** under NIS2 Art. 4 (a Regulation, so uniform, unlike NIS2's transposed rules).
- `cybersecurity-foundations` — control frameworks (ISO/IEC 27001, NIST CSF) underpinning the Art. 21 measures referenced across national laws.
- `nis2-sectors` — Annex I/II sector-by-sector scope analysis (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Transposition **legal framework** (Arts. 41, 3(4), 26, 34) sourced to EUR-Lex [1] and Reg (EU) 2024/2690 [2]. **Enforcement milestones live-verified**: reasoned opinions to 19 Member States (7 May 2025) [5]; CJEU referrals of Ireland, Spain, France and the Netherlands (IP/26/1499, 8–9 July 2026) [6]; Commission state-of-play page last updated 1 July 2025 [4]. **Adopted examples sourced**: Italy (D.Lgs 138/2024, Gazzetta Ufficiale [3]; ACN [10]); Germany (NIS2UmsuCG/BSIG from 6 Dec 2025, BSI [9]). Per-state snapshot built by category from the reasoned-opinion selection and state-of-play; **rows without a primary source are flagged "status as of 2026-07; verify"**. Confidence **Medium** given legislative volatility. All 11 external links returned HTTP 200. | pending |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster C); full-repo validator/link/lint suite green; frozen in release 0.17.0. | Orchestrator (QA-verified) |

</content>
</invoke>
