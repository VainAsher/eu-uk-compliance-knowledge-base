---
id: uk-transfers
title: "UK GDPR: International Data Transfers"
version: 0.1.0
status: in-review
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
related: [uk-gdpr-foundations, duaa-2025-detail, gdpr-transfers, gdpr-foundations, cloud-hosting-foundations]
tags: [uk-gdpr, international-transfers, adequacy, data-bridges, idta, uk-addendum, tra, data-protection-test, duaa-2025, uk-us-data-bridge]
legal_basis: UK GDPR (Chapter V, Arts. 44–50, as amended); Data Protection Act 2018; Data (Use and Access) Act 2025 (c.18)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | uk-transfers |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. **Two time-sensitive items — live-verified 2026-07-11:** (1) the UK international-transfer rules were **materially amended by the Data (Use and Access) Act 2025**, whose transfer provisions (**s.85 and Schedules 7–9**) came into force on **5 February 2026**, introducing a statutory **"data protection test"** ("not materially lower"); and (2) the **UK-US data bridge** is an *extension* of the **EU-US Data Privacy Framework**, whose validity is under appeal to the Court of Justice (**Latombe**, C-703/25 P). Confirm both before relying on them. This document details the UK transfer regime introduced at foundational level in `uk-gdpr-foundations` and contrasts with the EU regime in `gdpr-transfers`.

# Executive Summary

This document details how the **UK GDPR** restricts transfers of personal data outside the United Kingdom, and the mechanisms available to make such transfers lawful. It is the UK counterpart to `gdpr-transfers` (which covers EU GDPR Chapter V): the architecture is deliberately parallel, but the UK operates its **own adequacy list**, its **own model contracts**, and — since **5 February 2026** — its **own statutory transfer test** [1][5][7].

The UK regime rests on the same three-tier logic as the EU's. A transfer is permitted if (a) the destination is covered by **UK adequacy regulations** — informally "**data bridges**" — made by the Secretary of State [15]; or (b) the exporter puts in place **appropriate safeguards**, principally the ICO's **International Data Transfer Agreement (IDTA)** or the **UK Addendum** to the EU Standard Contractual Clauses [16]; or (c) a narrow **Article 49 derogation** applies [1]. Where a safeguard is used, the exporter must also carry out a risk assessment — the ICO's **Transfer Risk Assessment (TRA)**, now referred to in UK legislation as the **"data protection test"** [18].

Three UK-specific points dominate. First, the **Data (Use and Access) Act 2025 (DUAA)** rebuilt the statutory basis for transfers: it **repealed** the old DPA 2018 transfer sections, inserted a new **Article 44A** approval framework, and set a single **"data protection test"** — protection in the destination must be **"not materially lower"** than under UK law — for both adequacy regulations and exporter assessments [5][6][18]. This wording replaces the EU's Schrems II standard of **"essentially equivalent"** and the ICO's former term "sufficiently similar" [11][15]. Second, the current **data bridges** include the EEA, the countries the UK carried over from the EU adequacy list, Gibraltar, the Republic of Korea, and — for the US — the **UK Extension to the EU-US Data Privacy Framework** (live since 12 October 2023) [15][17][19]. Third, in the reverse direction, **EU→UK adequacy** was **renewed to 27 December 2031**, having been assessed against the DUAA reforms [21].

# Key Takeaways

- The **UK GDPR restricts transfers** of personal data to third countries and international organisations; the general principle (Art. 44) requires that the level of protection is **not undermined**, and applies to onward transfers [1]. *(Legal obligation.)*
- The **DUAA 2025 rebuilt the transfer regime**: it **repealed** DPA 2018 ss.17A–18, inserted a new **Article 44A** ("transfers approved by regulations"), and its transfer provisions (**s.85, Schedules 7–9**) came into force on **5 February 2026** via **SI 2026/82** [4][5][6][7]. *(Legal obligation — in force.)*
- The DUAA sets a single statutory **"data protection test"**: the destination's standard of protection must be **"not materially lower"** than under UK law — replacing the EU/Schrems II threshold of **"essentially equivalent"** and the ICO's former "sufficiently similar" [5][6][15][18]. *(Legal obligation / regulatory interpretation.)*
- **UK adequacy regulations ("data bridges")** currently cover the EEA, the EU-legacy adequate countries (e.g. Andorra, Argentina, Canada (PIPEDA, commercial), Faroe Islands, Guernsey, Isle of Man, Israel, Japan (APPI, PIHBOs), Jersey, New Zealand, Switzerland, Uruguay), **Gibraltar**, the **Republic of Korea**, and the **US (UK Extension to the EU-US DPF)** [15][17]. *(Legal obligation.)*
- Absent adequacy, the UK **appropriate safeguards** are principally the ICO **IDTA** (a standalone UK contract) or the **UK Addendum** to the EU SCCs, both issued under **s.119A DPA 2018** and laid before Parliament on **2 February 2022** [13][16]. *(Legal obligation.)*
- Before relying on a safeguard, exporters must complete a **Transfer Risk Assessment (TRA)** — now the statutory **"data protection test"** — for which the **ICO's own risk-based TRA tool** is an alternative to (not a copy of) the EDPB's **Schrems II** transfer-impact methodology [18][23]. *(Regulatory interpretation / obligation.)*
- The **UK-US data bridge** (UK Extension to the EU-US DPF) lets UK exporters transfer to US importers **certified and listed** on the DPF List, under **Art. 45 UK GDPR**, without further safeguards — but only for FTC/DoT-eligible organisations and with special handling for sensitive/criminal-offence data [17][19][22]. *(Legal obligation.)*
- The UK-US bridge is an **extension of the EU-US DPF** and therefore **contingent on that framework's continued validity**, which is under appeal (**Latombe**, C-703/25 P); keep an IDTA/Addendum fallback [9][12][17]. *(Legal obligation — live-verify.)*
- In the reverse direction, **EU→UK adequacy was renewed to 27 December 2031** after the Commission assessed the DUAA — but this is conditional and reviewable, making UK divergence a watch-item [21]. *(Regulatory / legal.)*

# Purpose

This document is the UK international-transfers deep-dive. It supports:

- **Legal research** — a mapped account of the UK GDPR Chapter V mechanisms as amended by the DUAA, the current data-bridge list, and the new "data protection test".
- **Compliance implementation** — choosing and documenting the right UK transfer mechanism (data bridge → IDTA/Addendum → derogation), completing a TRA/data-protection-test, and managing US flows.
- **Engineering triage** — identifying where UK personal data leaves the UK (including remote access and cloud sub-processors) and which paperwork follows.
- **EU/UK programme design** — running the UK regime alongside, and distinct from, the EU regime in `gdpr-transfers`.

It assumes the reader has read `uk-gdpr-foundations` (constitutional basis, DPA 2018, DUAA overview) and, for the EU baseline, `gdpr-transfers`. It does **not** re-explain EU Chapter V mechanics except where a contrast is load-bearing.

# Scope

**In scope:** The UK GDPR restricted-transfer rules (Arts. 44–50 as assimilated and amended); the DUAA 2025 transfer reforms (new Art. 44A, the "data protection test", the repeal of DPA 2018 ss.17A–18); UK adequacy regulations / data bridges and the current list; the IDTA and the UK Addendum to the EU SCCs; the ICO Transfer Risk Assessment (TRA) and how it differs from the EU TIA; the UK-US data bridge and its dependence on the EU-US DPF; and EU→UK adequacy.

**Out of scope:** EU GDPR Chapter V mechanics in the round (`gdpr-transfers`); the general UK GDPR/DPA 2018 divergence beyond transfers (`uk-gdpr-foundations`); the DUAA's non-transfer reforms — recognised legitimate interests, Arts. 22A–22D ADM, PECR (`duaa-2025-detail`); law-enforcement transfers under DPA 2018 Part 3 and DUAA Schedule 8 (noted only where they frame the general-processing regime); and encryption engineering for supplementary measures (`privacy-engineering-foundations`).

**Assumptions:** "UK GDPR" means Regulation (EU) 2016/679 as assimilated under EUWA 2018 s.3 and read with the DPA 2018 [1][2][3]. "Restricted transfer" and "third country" mean a destination outside the UK. Article numbers are to the UK GDPR (which mirror the EU GDPR's numbering except where the DUAA inserts new provisions such as Art. 44A).

# Definitions

*Shared terms are in `GLOSSARY.md` (restricted transfer, SCCs, BCRs, TIA, IDTA, adequacy decision, data bridge). Only UK-transfer-specific terms are narrowed here.*

| Term | Definition | Source |
|------|------------|--------|
| Data bridge | UK government's informal term for a **UK adequacy regulation** — a Secretary of State determination that a country/territory/sector or international organisation provides protection **not materially lower** than UK law, permitting transfers without further safeguards. | [15][20] |
| Data protection test | The DUAA-introduced statutory standard for transfers: whether the destination's protection is **"not materially lower"** than under UK law. It governs both **adequacy regulations** (the Secretary of State's assessment) and the **exporter's own assessment** (the TRA) when relying on Art. 46 safeguards. | [5][6][18] |
| International Data Transfer Agreement (IDTA) | The ICO's **standalone** UK Article 46 model contract, issued under s.119A DPA 2018; an alternative to the EU SCCs + UK Addendum. | [13][16] |
| UK Addendum | The ICO's **addendum** that bolts onto the EU SCCs (Decision (EU) 2021/914) so they can be relied on for UK restricted transfers. | [10][16] |
| Transfer Risk Assessment (TRA) | The UK exporter's assessment of whether the appropriate-safeguard mechanism will be effective given the destination's law and practice; since the DUAA it is referred to in legislation as the **"data protection test"**. | [18] |
| UK Extension to the EU-US DPF | The US-facing data bridge: an Art. 45 route allowing transfers to US organisations **certified to the UK Extension** and on the **DPF List**. | [17][19] |

# Background

Before Brexit, UK transfers were governed by EU GDPR Chapter V and the Commission's adequacy decisions and SCCs. On assimilation, the UK "onshored" both the Chapter V text and the **then-existing EU adequacy decisions**, so day-one UK adequacy covered the same countries the EU recognised, plus the EEA [2][15]. Because the EU SCCs (2010/2021) were EU instruments, the UK needed its own model contracts: the ICO issued the **IDTA** and the **UK Addendum** under s.119A DPA 2018, laying them before Parliament on **2 February 2022** [13][16].

The transatlantic route followed the EU's. After Schrems II invalidated Privacy Shield, the US built a new redress architecture (Executive Order 14086, the Data Protection Review Court) that underpinned the Commission's **EU-US Data Privacy Framework** adequacy decision of 10 July 2023 [9][11]. The UK then negotiated a **UK Extension** to that framework; the Secretary of State made **SI 2023/1028**, and from **12 October 2023** UK organisations could transfer to UK-Extension-certified US importers under Art. 45 UK GDPR [8][17][19].

The most significant UK-only development is the **Data (Use and Access) Act 2025**. Rather than tinker at the edges, its transfer provisions **replaced the statutory scaffolding**: DPA 2018 ss.17A–18 (adequacy regulations, standard clauses, safeguards) were repealed, a new **Article 44A** ("transfers approved by regulations") was inserted into the UK GDPR, and a single **"data protection test"** was adopted [4][5][6]. These provisions were commenced on **5 February 2026** by **SI 2026/82** [7]. The Commission had already assessed the DUAA when it **renewed EU→UK adequacy to 27 December 2031** in December 2025 [21].

# Legal Framework

The UK transfer regime is a **layered permission system**, mirroring EU Chapter V but sitting in assimilated UK GDPR text as amended by the DUAA. The exporter must identify a valid gateway **before** transferring and be able to evidence it [1].

The layers, in order of preference:

- **Adequacy — UK adequacy regulations ("data bridges") (Art. 45, and new Art. 44A).** Transfer to a country/territory/sector or international organisation covered by regulations the Secretary of State has made applying the **data protection test**; no further authorisation needed [5][6][15].
- **Appropriate safeguards (Art. 46).** Where there is no data bridge: the **IDTA**, the **EU SCCs + UK Addendum**, UK Binding Corporate Rules (Art. 47), or approved codes/certifications — each providing enforceable rights and effective remedies, and each requiring a **TRA / data protection test** [6][16][18].
- **Derogations (Art. 49).** Exceptional, situation-specific gateways (explicit consent, contract necessity, important public interest, legal claims, vital interests, public register, compelling legitimate interests) — narrowly construed, not for routine bulk transfers [1][17].

The DUAA's mechanism is **amendment-in-place**: **Schedule 7** rewrites the general-processing transfer rules (inserting Art. 44A and recasting Art. 46), **Schedule 8** does the same for law-enforcement processing (DPA 2018 Part 3), and **Schedule 9** makes consequential amendments and — critically — **repeals DPA 2018 ss.17A, 17B, 17C and 18** and adjusts s.119A [5][6][13]. The consolidated effect must therefore be read in the **amended** UK GDPR and DPA 2018, not in the DUAA alone.

## Relevant Articles

*"Article" means the UK GDPR article (as assimilated and amended); DPA/DUAA provisions are named where relevant.*

| Provision | Obligation / effect | Source |
|-----------|---------------------|--------|
| UK GDPR Art. 44 | General principle — every transfer must comply with Chapter V so the level of protection is **not undermined**; applies to onward transfers. | [1] |
| UK GDPR Art. 45 | Transfers on the basis of **adequacy regulations** (data bridges) — no further safeguard needed. | [1][15] |
| UK GDPR **Art. 44A** (inserted by DUAA Sch. 7) | New framework for **transfers approved by regulations**: the Secretary of State may make adequacy regulations applying the **data protection test**; provides for monitoring/review. | [5][6] |
| UK GDPR Art. 46 (as amended) | Transfers subject to **appropriate safeguards** (IDTA; EU SCCs + UK Addendum; BCRs; codes; certification), each requiring the exporter to be satisfied the **data protection test** is met. | [1][6][16] |
| UK GDPR Art. 47 | **UK Binding Corporate Rules** — intra-group safeguard, approved by the ICO. | [1] |
| UK GDPR Art. 49 | **Derogations** for specific situations; exceptional and narrowly construed. | [1] |
| DPA 2018 **s.119A** | Power of the Commissioner to issue **standard data protection clauses** — the legal basis for the IDTA and the UK Addendum. | [13][16] |
| DPA 2018 ss.17A–18 (**repealed** by DUAA Sch. 9) | Former statutory basis for adequacy regulations, standard clauses and safeguards — now removed and re-based in the amended UK GDPR. | [5][6] |
| DUAA **s.85 + Schedules 7–9** | The operative transfer reforms; **in force 5 February 2026** (SI 2026/82). | [5][6][7] |

## Relevant Recitals

*The UK GDPR retains the EU GDPR's recitals as interpretive aids (Recitals 101–116 frame Chapter V — see `gdpr-transfers`) [1]. The DUAA does not add UK-specific recitals; its transfer provisions are construed against the **Act's own text, Schedules and Explanatory Notes** and ICO guidance rather than new recitals.* **Not Applicable** as a distinct UK set — interpretation of the "data protection test" rests on the statutory wording and ICO guidance [6][18].

## Relevant Case Law

*Pre-2021 CJEU transfer authority (notably **Schrems II**) is assimilated case law: it remains persuasive for the assimilated Chapter V concepts, subject to UK courts' power to depart, but the DUAA's "not materially lower" test is a **statutory** standard that displaces the EU "essentially equivalent" formula for UK purposes going forward [1][11]. Post-2020 CJEU decisions (including the **Latombe** litigation) are **not binding** in the UK but are **materially relevant** because the UK-US data bridge is built on the EU-US DPF [11][12].*

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Schrems II (DPC v Facebook Ireland & Schrems) | CJEU (Grand Chamber), C-311/18, ECLI:EU:C:2020:559, 16 July 2020 | Invalidated Privacy Shield; upheld SCCs in principle but required a case-by-case assessment of destination law and **supplementary measures**. | Assimilated authority behind the UK TRA duty; the DUAA now expresses the assessment as the statutory **"data protection test"** [1][11]. |
| Latombe v Commission (appeal) | Court of Justice, **C-703/25 P**, appeal lodged 31 Oct 2025 (**pending**) | No ruling yet; seeks to set aside the General Court's dismissal of the challenge to the EU-US DPF adequacy decision. | If the EU-US DPF falls, the **UK-US data bridge** (an extension of it) is undermined — a live contingency for UK exporters [9][12]. |
| *(UK-domestic transfer case law)* | — | None yet on the DUAA transfer provisions (in force Feb 2026). | Not Applicable — early disputes likely surface first as ICO guidance/enforcement [6]. |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).** The authoritative UK readings are the **ICO** international-transfers guidance suite (re-issued in January 2026 to reflect the DUAA) and **DSIT/GOV.UK** materials [14][15][16][17][18][20].

- **The "data protection test" is the new UK standard.** The ICO states that the UK assesses whether a destination has "a level of data protection that is **'not materially lower'** than provided for by UK law", and that "**prior to the Data (Use and Access) Act (DUAA), we referred to this standard as 'sufficiently similar'**" [15]. The ICO also confirms that a **Transfer Risk Assessment (TRA) "is now referred to in UK legislation as a 'data protection test'"** [18]. *(Regulatory interpretation of a legal standard.)*
- **Two applications, one test.** The same "not materially lower" threshold is applied by the **Secretary of State** when making adequacy regulations (Art. 44A) and by the **exporter** when relying on Art. 46 safeguards (the TRA) — a deliberately unified UK standard [5][6][18]. *(Regulatory interpretation.)*
- **The ICO TRA tool is an alternative approach, not the EDPB method.** The ICO offers its **own risk-based TRA tool** as an alternative route to the EDPB's Schrems II transfer-impact methodology; an exporter may use either, but the ICO tool is designed to be more proportionate and focuses on whether the transfer poses a real risk of harm to people, rather than on abstract legal equivalence [18][23]. *(Regulatory interpretation.)*
- **Data bridges are living instruments.** The ICO frames adequacy regulations as reviewable; the US bridge in particular is **partial** (only the UK Extension to the DPF) and carries **special handling** for sensitive and criminal-offence data because the DPF "Choice" principle does not map exactly onto UK Art. 9 special categories [17][19]. *(Regulatory interpretation.)*
- **EU→UK adequacy is conditional.** The Commission renewed UK adequacy to **27 December 2031** having assessed the DUAA, but adequacy is periodically monitored and can be suspended if UK protection deteriorates — so DUAA divergence (including the softer-sounding transfer test) is a standing watch-item [21]. *(Regulatory interpretation.)*

## Adequacy — the current UK data-bridge list (Art. 45 / Art. 44A)

As of this document's date, UK adequacy regulations ("data bridges") cover, per the ICO's adequacy-regulations guidance [15]:

- **The EEA** — all EU member states plus **Iceland, Norway and Liechtenstein** (full adequacy), and EU/EEA institutions, bodies, offices and agencies.
- **Full adequacy:** **Andorra, Argentina, Faroe Islands, Gibraltar, Guernsey, Isle of Man, Israel, Jersey, New Zealand, the Republic of Korea (South Korea), Switzerland, and Uruguay**.
- **Sector/partial adequacy:** **Canada** (only where PIPEDA applies — private-sector commercial activities) and **Japan** (only transfers to PIHBOs within the APPI).
- **Partial adequacy — United States:** only personal data transferred under the **UK Extension to the EU-US Data Privacy Framework** (the "UK-US data bridge"), to importers certified and on the DPF List [17][19].

The **authoritative, current** list is the ICO adequacy-regulations page and the underlying regulations — consult them directly, because entries are added and reviewed over time [15]. The UK list **largely tracks, but is distinct from, the EU adequacy list**: the UK has since added its own determinations (e.g. the Republic of Korea and the US bridge) and could add or remove entries independently of the Commission's list [24].

# Technical Considerations

- **Map UK flows first.** A restricted transfer occurs whenever UK personal data is sent to, **or made accessible from**, outside the UK — including remote admin/support access, global consoles, and CDN/edge nodes; "stored only in the UK" does not by itself avoid Chapter V [1][14]. *(Legal obligation / interpretation.)*
- **Record the mechanism in the RoPA.** Maintain per-flow records (destination, importer, data categories, mechanism — data bridge / IDTA / Addendum / derogation, TRA reference) so the basis is evidenced on demand (Art. 30) [1]. *(Legal obligation.)*
- **Supplementary measures remain relevant under the TRA.** Where a TRA/"data protection test" identifies a gap, the exporter should add technical measures — strong **encryption in transit and at rest with UK/EEA-held keys**, effective **pseudonymisation**, split processing — mirroring the Schrems II logic even though the UK test is framed around risk of harm rather than abstract equivalence [11][18][23]. *(Best practice grounded in obligation.)*
- **Jurisdiction-tag the data.** Because the UK test ("not materially lower") and the EU test ("essentially equivalent") differ, systems handling both UK- and EU-origin data should assess UK-origin exports against the UK test and EU-origin exports against the EU test, not a single global rule [5][18]. *(Best practice.)*

# Hosting Considerations

- **Cloud usually means transfers.** Most hyperscale/SaaS hosting entails at least remote access from outside the UK; assess each provider's regions, sub-processors and support-access model against the UK regime [1][14]. *(Legal obligation.)*
- **Use UK paperwork for UK data.** Provider DPAs commonly offer the **EU SCCs + UK Addendum**; some offer the standalone **IDTA**. Either is valid, but the EU SCCs **alone are not** valid for UK restricted transfers — they need the Addendum [16]. *(Legal obligation.)*
- **DPF-certified US importers.** Where a US provider is certified to the **UK Extension** and on the **DPF List**, transfers to it can rely on the **UK-US data bridge** (Art. 45) instead of an IDTA/Addendum — but verify the specific entity/scope and keep a fallback because the bridge is contingent on the EU-US DPF [17][19][22]. *(Legal obligation / editorial recommendation.)*
- **The exporter owns the TRA.** A provider can supply the contract, but the **customer, as exporter, owns the TRA / "data protection test"** and cannot delegate that judgement [16][18]. *(Legal obligation.)*
- **EU→UK residency is lawful.** Hosting EU personal data in the UK remains lawful under EU→UK adequacy (to 27 December 2031) without additional safeguards, subject to that decision's continued validity [21]. *(Legal.)*

# Game Hosting Considerations

- **Global player bases mean constant UK-out transfers.** Matchmaking, telemetry, anti-cheat, voice/chat and crash reporting frequently route UK player data (usernames, device IDs, IP addresses) to third-country servers or vendors; each needs a UK Chapter V basis — a data bridge, IDTA/Addendum + TRA, or a derogation [1][16][18]. *(Legal obligation.)*
- **Third-party SDKs.** Ads, analytics and crash SDKs often transfer to the US or elsewhere; inventory them and confirm the mechanism (UK-US bridge for a UK-Extension-certified US importer, otherwise IDTA/Addendum + TRA) [17][19]. *(Legal obligation.)*
- **Children's data raises the bar.** Where UK children are in scope, consent-based derogations are fragile and TRAs should weigh the heightened risk of harm; align with the ICO Children's Code and the DUAA children's higher-protection duty (see `duaa-2025-detail`, `uk-childrens-code`) [18]. *(Best practice.)*
- **Latency vs. residency.** Pressure to place edge servers near players must be reconciled with the transfer rules; prefer UK/adequate regions for identifiable player data where feasible. *(Editorial recommendation.)*

# AI Considerations

- **Training/inference transfers.** Sending UK personal data to a third-country model provider (or a model hosted abroad) for training or inference is a restricted transfer; a UK Chapter V basis **and** a TRA/"data protection test" are required in addition to a lawful basis [1][18]. *(Legal obligation.)*
- **US model APIs.** Many foundation-model APIs are operated by US entities; check for **UK-Extension DPF certification** (Art. 45 route via the data bridge) or fall back to **IDTA/Addendum + TRA**, noting that clear-text prompt/response access by the importer weakens technical measures [17][19][23]. *(Legal obligation / interpretation.)*
- **The UK test may ease some AI transfers relative to the EU.** The "not materially lower" / risk-based TRA is intended to be more proportionate than the EU's "essentially equivalent" analysis, but the outcome is not automatically more permissive and remains untested — document the assessment either way [5][18][23]. *(Editorial recommendation.)*
- **Minimise before transfer.** Pseudonymise/aggregate training data before export where possible, reducing both transfer risk and lawful-basis exposure [18]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** (the law requires) / **BEST PRACTICE** (standards/regulator consensus) / **EDITORIAL RECOMMENDATION** (this pipeline suggests).

1. **Inventory UK-out transfers** — build a transfer register within the RoPA (destination, importer, data categories, mechanism, TRA). *(OBLIGATION.)* [1]
2. **Prefer a data bridge** — where the destination is covered by UK adequacy regulations (or the US importer is UK-Extension-certified on the DPF List), rely on Art. 45 and record the basis. *(OBLIGATION.)* [15][17][19]
3. **Use UK safeguards for UK data** — the **IDTA**, or **EU SCCs + UK Addendum**; never rely on bare EU SCCs for UK restricted transfers. *(OBLIGATION.)* [16]
4. **Complete a TRA / "data protection test"** before relying on an Art. 46 safeguard — use the ICO's risk-based TRA tool **or** the EDPB method, and document the "not materially lower" conclusion. *(OBLIGATION + BEST PRACTICE.)* [18][23]
5. **Add technical measures** where the TRA shows a gap (encryption with UK/EEA-held keys, pseudonymisation); if no measure suffices, do not transfer. *(OBLIGATION.)* [11][18]
6. **Treat Art. 49 derogations as exceptional** — do not use consent or contract necessity to justify routine, bulk transfers; document why a derogation genuinely applies. *(OBLIGATION.)* [1]
7. **Manage US flows actively** — verify UK-Extension certification and scope on the DPF List, handle sensitive/criminal-offence data per the factsheet, and keep an IDTA/Addendum fallback against the Latombe appeal. *(OBLIGATION + EDITORIAL RECOMMENDATION.)* [12][17][19][22]
8. **Re-base to the DUAA regime** — confirm your transfer paperwork and TRAs reflect the amended UK GDPR (in force 5 Feb 2026), and separate UK-origin (UK test) from EU-origin (EU test) assessments. *(OBLIGATION.)* [5][7][18]
9. **Monitor EU→UK adequacy** — renewed to 2031 but reviewable; hold a contingency plan should divergence threaten it. *(EDITORIAL RECOMMENDATION.)* [21]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Transferring UK data with **no valid Chapter V mechanism** | Medium | High | Arts. 44–46 [1] | Transfer register; pre-transfer mechanism sign-off | Low |
| R2 | Using **bare EU SCCs** for UK data without the UK Addendum | Medium | Medium | s.119A; Addendum [16] | Use IDTA or SCCs+Addendum; jurisdiction check | Low |
| R3 | Relying on a safeguard **without a TRA / "data protection test"** | Medium | High | Art. 46 as amended; TRA [6][18] | Mandatory TRA workflow; documented conclusion | Low |
| R4 | **Over-reliance on the UK-US data bridge** if the EU-US DPF is invalidated on appeal | Medium | High | Latombe C-703/25 P [9][12] | IDTA/Addendum fallback; monitor litigation | Medium |
| R5 | Treating the DUAA transfer changes as "future" when in force since **5 Feb 2026** | Medium | Medium | SI 2026/82 [7] | Re-base paperwork/TRAs to amended law | Low |
| R6 | Applying the **UK "not materially lower" test to EU-origin data** (which needs "essentially equivalent") | Medium | High | DUAA test vs EU standard [5][11] | Separate UK-origin and EU-origin assessments | Low |
| R7 | **Mishandling sensitive/criminal-offence data** under the US bridge (DPF "Choice" ≠ Art. 9) | Medium | Medium | UK-US factsheet [19] | Identify/flag sensitive data on transfer; extra safeguards | Low |
| R8 | **Onward transfers** by the importer defeat protection | Medium | Medium | Art. 44 [1] | Onward-transfer clauses; sub-processor controls | Medium |
| R9 | **EU→UK adequacy lapse** at review due to divergence | Low | High | Adequacy to 2031, reviewable [21] | Divergence register; contingency plan | Medium |

# Implementation Roadmap

- **Phase 0 — Transfer discovery:** Map every UK-out flow, including remote access and sub-processors. *Depends on:* RoPA/data map. *Effort:* Medium.
- **Phase 1 — Mechanism selection:** Assign a UK Chapter V basis per flow (data bridge → IDTA/Addendum → derogation); record rationale. *Effort:* Medium.
- **Phase 2 — TRAs / data protection tests:** Run a TRA for each Art. 46 flow (ICO tool or EDPB method); implement technical measures where needed. *Effort:* High.
- **Phase 3 — US flows:** Verify UK-Extension certification/scope on the DPF List; implement sensitive-data handling; prepare IDTA/Addendum fallback. *Effort:* Medium.
- **Phase 4 — DUAA re-basing:** Confirm paperwork/TRAs reflect the amended UK GDPR (5 Feb 2026); split UK-origin vs EU-origin assessments. *Effort:* Medium.
- **Phase 5 — Monitor & re-verify:** Track the Latombe appeal, EU→UK adequacy reviews, and new/updated data bridges; re-evaluate TRAs periodically. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | UK-out transfers unmapped; mechanisms ad hoc or absent; still using bare EU SCCs. | No transfer register. |
| 2 | Managed | Major transfers identified; IDTA/Addendum in place but no TRAs. | Partial register; provider DPAs signed. |
| 3 | Defined | Documented mechanism per flow; TRAs/"data protection tests" run; US flows verified on the DPF List. | Transfer register in RoPA; TRA library. |
| 4 | Quantitatively Managed | Technical measures verified; UK-origin vs EU-origin assessments separated; metrics on coverage/re-verification. | Key-custody controls; KPIs; periodic re-TRA. |
| 5 | Optimising | Automated transfer discovery; data-bridge/DPF/adequacy watch; rehearsed IDTA fallback. | Continuous monitoring; tested contingency. |

# Audit Questions

1. Can you produce a register mapping each UK-out flow to a UK Chapter V mechanism? *(Arts. 44–46 [1].)*
2. For UK data under safeguards, do you use the **IDTA** or **EU SCCs + UK Addendum** (never bare SCCs)? *(s.119A [13][16].)*
3. Where a safeguard is used, where is the **TRA / "data protection test"**, and does it document the "not materially lower" conclusion? *(Art. 46 as amended; TRA [6][18].)*
4. For US flows, is the importer **UK-Extension-certified and on the DPF List**, and how is sensitive/criminal-offence data handled? *([17][19][22].)*
5. Do your transfer records reflect the **DUAA regime in force since 5 February 2026** (amended UK GDPR / new Art. 44A)? *([5][7].)*
6. How do you separate **UK-origin** (UK test) from **EU-origin** (EU "essentially equivalent") transfer assessments? *([5][11].)*
7. How do you monitor the **Latombe appeal** and the continued validity of the UK-US bridge? *([9][12].)*
8. How are **onward transfers** by importers controlled? *(Art. 44 [1].)*

# Implementation Checklist

- [ ] UK-out transfer register built and embedded in the RoPA (destination, mechanism, TRA).
- [ ] Data-bridge reliance recorded where applicable (incl. DPF-List verification for US importers).
- [ ] IDTA or EU SCCs + UK Addendum executed for safeguard-based flows; bare EU SCCs eliminated.
- [ ] TRA / "data protection test" completed for every Art. 46 flow (ICO tool or EDPB method).
- [ ] Technical measures implemented and verified where a TRA shows a gap (UK/EEA-held keys; pseudonymisation).
- [ ] Sensitive/criminal-offence data handling configured for the UK-US bridge.
- [ ] Art. 49 derogations gated, justified and documented as exceptional.
- [ ] Paperwork/TRAs re-based to the amended UK GDPR (5 Feb 2026); UK-origin vs EU-origin assessments separated.
- [ ] IDTA/Addendum fallback prepared for US flows; Latombe appeal (C-703/25 P) on the watch-list.
- [ ] EU→UK adequacy (to 2031) monitored with a contingency plan.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (UK GDPR base text), Chapter V, Arts. 44–50** — consolidated text (article numbering assimilated into UK law under EUWA 2018 s.3). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [2] **European Union (Withdrawal) Act 2018, s.3** (retention/assimilation of the UK GDPR). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/16/section/3
- [3] **Data Protection Act 2018 (c.12)**, contents (read together with the UK GDPR). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/contents
- [4] **Data (Use and Access) Act 2025 (c.18)**, contents (Royal Assent 19 June 2025). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/contents
- [5] **Data (Use and Access) Act 2025, s.85** (transfers of personal data to third countries and international organisations). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/section/85
- [6] **Data (Use and Access) Act 2025, Schedule 7** (transfers of personal data to third countries etc: general processing — inserts UK GDPR Art. 44A; recasts Art. 46; the "data protection test"). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/schedule/7
- [7] **The Data (Use and Access) Act 2025 (Commencement No. 6 and Transitional and Saving Provisions) Regulations 2026 (SI 2026/82), reg. 2** — brings s.85 and Schedules 7–9 into force on 5 February 2026. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2026/82/regulation/2/made
- [8] **The Data Protection (Adequacy) (United States of America) Regulations 2023 (SI 2023/1028)** — UK Extension to the EU-US DPF ("UK-US data bridge"). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2023/1028/contents/made
- [9] **Commission Implementing Decision (EU) 2023/1795 of 10 July 2023** on the adequate level of protection under the EU-US Data Privacy Framework (the framework the UK Extension builds on). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dec_impl/2023/1795/oj
- [10] **Commission Implementing Decision (EU) 2021/914 of 4 June 2021** on standard contractual clauses (the EU SCCs the UK Addendum bolts onto). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj
- [11] **Data Protection Commissioner v Facebook Ireland & Schrems ("Schrems II")**, CJEU C-311/18, ECLI:EU:C:2020:559. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:62018CJ0311
- [12] **Latombe v Commission (appeal)**, Court of Justice, Case **C-703/25 P**, appeal lodged 31 October 2025 (pending) — OJ notice. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:C_202506610
- [13] **Data Protection Act 2018, s.119A** (Commissioner's power to specify standard clauses — basis for the IDTA and UK Addendum). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/section/119A

## Regulatory Guidance

- [14] **International transfers — guidance and resources.** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/
- [15] **Adequacy regulations** (the current UK data-bridge list; the "not materially lower" standard). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/adequacy-regulations/
- [16] **What are standard data protection clauses (the UK IDTA and the Addendum)?** ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/appropriate-safeguards/what-are-standard-data-protection-clauses-the-uk-idta-and-the-addendum/
- [17] **How does the UK Extension to the EU-US Data Privacy Framework work?** ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/adequacy-regulations/how-does-the-uk-extension-to-the-eu-us-data-privacy-framework-work/
- [18] **Completing a transfer risk assessment (TRA)** (now referred to in UK legislation as the "data protection test"; ICO TRA tool). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/completing-a-transfer-risk-assessment/
- [19] **UK-US data bridge: factsheet for UK organisations.** GOV.UK / DSIT. https://www.gov.uk/government/publications/uk-us-data-bridge-supporting-documents/uk-us-data-bridge-factsheet-for-uk-organisations
- [20] **Data (Use and Access) Act 2025: data protection and privacy changes** (incl. the transfers "data protection test"). GOV.UK. https://www.gov.uk/guidance/data-use-and-access-act-2025-data-protection-and-privacy-changes
- [21] **Commission renews decisions to allow the free and safe flow of personal data with the UK** (IP/25/3059, 19 December 2025; EU→UK adequacy to 27 December 2031, assessing the DUAA). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_3059
- [22] **EU-U.S. Data Privacy Framework — Program Overview / DPF List.** U.S. Department of Commerce. https://www.dataprivacyframework.gov/Program-Overview
- [23] **Recommendations 01/2020 on measures that supplement transfer tools** (the EDPB Schrems II six-step method — contrast for the UK TRA). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-012020-measures-supplement-transfer_en
- [24] **Adequacy decisions — international dimension of data protection** (the EU adequacy list — contrast with the UK data-bridge list). European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/adequacy-decisions_en

## Standards

**Not Applicable** — UK transfer compliance turns on legal mechanisms (data bridges, IDTA/Addendum, derogations) and the statutory "data protection test", not a technical standard. Where a TRA requires security controls (encryption, key management, pseudonymisation), those map to ISO/IEC 27001 and are treated in `privacy-engineering-foundations`.

## Academic Sources

**Not Applicable** — this reference relies on primary legislation, an assimilated CJEU judgment, and UK regulatory guidance. Analytical questions (e.g. whether "not materially lower" is genuinely a lower bar than "essentially equivalent") may cite peer-reviewed literature as it matures.

# Further Reading

*Non-authoritative; provided for orientation only.*

- ICO — International transfers: making a restricted transfer (overview and decision tree). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/
- IAPP — news and analysis tracking the Latombe litigation and UK data-bridge developments. https://iapp.org/

# Related Documents

- `uk-gdpr-foundations` — UK GDPR/DPA 2018 foundations and divergence (**parent; this document details its transfer material**).
- `duaa-2025-detail` — the DUAA 2025 in depth (the "data protection test" sits within its wider reforms).
- `gdpr-transfers` — EU GDPR Chapter V (**the EU-side sibling; contrast the "essentially equivalent" standard and EU SCCs**).
- `gdpr-foundations` — EU GDPR baseline (prerequisite reading).
- `cloud-hosting-foundations` — hosting/sub-processor transfer implications.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against legislation.gov.uk (UK GDPR/DPA 2018; DUAA c.18 s.85 + Sch. 7–9; SI 2026/82 reg. 2; SI 2023/1028; DPA 2018 s.119A), EUR-Lex (Decisions 2023/1795 and 2021/914; Schrems II; Latombe appeal C-703/25 P), ICO international-transfers suite, GOV.UK and European Commission. **Live-verified 2026-07-11:** DUAA transfer provisions (incl. the "data protection test") in force 5 February 2026; current UK data-bridge list incl. the UK-US data bridge; UK-US bridge's dependence on the EU-US DPF (Latombe appeal); EU→UK adequacy renewed to 27 December 2031. | — |
