---
id: gdpr-transfers
title: "GDPR: International Data Transfers (Chapter V)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: GDPR (EU)
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [gdpr-foundations, uk-gdpr-foundations, privacy-engineering-foundations, eprivacy-foundations]
tags: [gdpr, international-transfers, chapter-v, adequacy, sccs, bcr, data-privacy-framework, schrems-ii, idta, uk-addendum]
legal_basis: Regulation (EU) 2016/679 (Arts. 44–50)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | gdpr-transfers |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.10.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. **Time-sensitive area:** the validity of the **EU-US Data Privacy Framework** is the subject of a **pending appeal before the Court of Justice (Case C-703/25 P)** and further legal pressure arising in mid-2026 — always confirm its current status before relying on it (see Executive Summary and Legal Framework). This document details Chapter V of `gdpr-foundations`.

# Executive Summary

Chapter V of the GDPR (Articles 44–50) governs the transfer of personal data to **third countries** (outside the EEA) and to international organisations. Its animating rule is that the level of protection guaranteed by the GDPR must **travel with the data**: a transfer is only lawful if the exporter uses one of the Chapter V mechanisms and the protection afforded to data subjects is not undermined [1]. This document details the Chapter V material introduced at foundation level in `gdpr-foundations` and goes deeper on each mechanism.

The transfer toolbox has a defined hierarchy [1]. First, an **adequacy decision** under **Article 45** — the Commission's finding that a country ensures an "essentially equivalent" level of protection — permits transfers with no further safeguard. Second, where there is no adequacy, **appropriate safeguards** under **Article 46** (chiefly the **2021 Standard Contractual Clauses**, **Binding Corporate Rules** under Art. 47, and approved codes/certifications) may be used, each providing enforceable rights and effective remedies. Third, the **Article 49 derogations** (consent, contract necessity, important public interest, etc.) are narrow, situational exceptions of last resort, not a routine basis for systematic transfers [1][11].

Since **Schrems II** (2020), Article 46 tools cannot be used mechanically: the exporter must run a **transfer impact assessment (TIA)** of the destination country's law and practice and, where protection falls short, add **supplementary measures** (technical, contractual, organisational) — or not transfer [2][11]. The **EU-US Data Privacy Framework (DPF)**, adopted by adequacy decision on **10 July 2023** [4], is the successor to the invalidated Safe Harbor and Privacy Shield. **As of this document's date it remains in force**: the General Court **dismissed** the first annulment challenge in **Latombe v Commission (3 September 2025)** [6], but that judgment is **under appeal to the Court of Justice (C-703/25 P, lodged 31 October 2025)** [7], and a June 2026 US Supreme Court development on FTC-commissioner removal has renewed doubts about the framework's redress architecture. Treat the DPF as **valid but contingent**. The document closes with the **UK regime** — UK adequacy regulations, the ICO's **International Data Transfer Agreement (IDTA)** and the **UK Addendum** to the EU SCCs [14][15].

# Key Takeaways

- Chapter V (Arts. 44–50) restricts transfers of personal data outside the EEA; **Article 44** makes clear that all its provisions must be applied so the GDPR-level of protection is **not undermined** [1]. *(Legal obligation.)*
- **Adequacy (Art. 45)** is the simplest route: transfers to a country/territory covered by a Commission adequacy decision need **no additional safeguard** [1][9]. *(Legal obligation.)*
- Absent adequacy, **appropriate safeguards (Art. 46)** — principally the **2021 SCCs** (Decision (EU) 2021/914), **BCRs (Art. 47)**, and approved codes/certifications — are required, each giving data subjects **enforceable rights and effective legal remedies** [1][5]. *(Legal obligation.)*
- **Schrems II** invalidated Privacy Shield and held that SCCs remain valid **only if** the exporter verifies essentially equivalent protection case-by-case and adds **supplementary measures** where needed [2][11]. *(Case law / regulatory interpretation.)*
- The **EU-US Data Privacy Framework** (adequacy decision of **10 July 2023**) is currently **in force**; it survived **Latombe v Commission** at the General Court (3 Sep 2025) but is **under appeal (C-703/25 P)** — treat its future as uncertain [4][6][7]. *(Legal obligation — live-verify.)*
- **Article 49 derogations** (explicit consent, contract necessity, important public interest, legal claims, vital interests, public register, compelling legitimate interests) are **exceptional and narrowly construed** — not a basis for large-scale, repetitive transfers [1][11]. *(Legal obligation / regulatory interpretation.)*
- A **transfer impact assessment (TIA)** is required before relying on Art. 46 tools; EDPB **Recommendations 01/2020** set out the six-step methodology and a supplementary-measures catalogue [11]. *(Regulatory interpretation / best practice.)*
- The **UK** operates a parallel regime: UK adequacy ("data bridges"), the **IDTA**, and the **UK Addendum** to the EU SCCs; the EU's adequacy decision for the UK was **renewed to 27 December 2031** [13][15][16]. *(Legal obligation.)*

# Purpose

This document is the Chapter V deep-dive supporting:

- **Legal research** — a mapped account of the Art. 44–50 mechanisms, the adequacy list, and the anchor case law (Schrems I/II, Latombe).
- **Compliance implementation** — choosing and documenting the right transfer mechanism, running TIAs, and applying supplementary measures.
- **Engineering triage** — identifying where data flows leave the EEA/UK (including cloud storage and remote access) and what controls follow.
- **Onboarding** — a single reference for transfer questions that arise across DSAR, hosting, and vendor-management work.

It assumes the reader has read `gdpr-foundations`. It does **not** re-explain core definitions (see `GLOSSARY.md`) or the Article 5/6 material.

# Scope

**In scope:** The general transfer principle (Art. 44); adequacy decisions (Art. 45) and the current list, including the EU-US DPF and its live status; appropriate safeguards (Art. 46) — the 2021 SCCs, BCRs (Art. 47), codes and certification; derogations (Art. 49); the Schrems II TIA/supplementary-measures requirement; and the UK transfer regime (UK adequacy/data bridges, IDTA, UK Addendum).

**Out of scope:** The GDPR foundations and Article 5/6 material (`gdpr-foundations`); the full UK GDPR/DPA 2018 divergence beyond transfers (`uk-gdpr-foundations`); processor-contract mechanics under Art. 28 (touched only where they intersect transfers); onward-transfer mechanics inside BCR schemes at clause level; and detailed encryption engineering (`privacy-engineering-foundations`).

**Assumptions:** Article references are to the consolidated text of Regulation (EU) 2016/679 on EUR-Lex [1]. "Third country" means a country outside the EEA. UK references are to the UK GDPR read with the DPA 2018.

# Definitions

*Shared terms are in `GLOSSARY.md`. Transfer-specific terms are defined here (kept short).*

| Term | Definition | Source |
|------|------------|--------|
| Restricted transfer | A transfer of personal data to a third country or international organisation that triggers Chapter V. | [1] |
| Adequacy decision | A Commission decision under Art. 45 that a third country/territory/sector ensures an essentially equivalent level of protection, permitting transfers without further safeguards. | [1][9] |
| Standard Contractual Clauses (SCCs) | Commission-approved model clauses providing Art. 46(2)(c) safeguards; the current modular set is Decision (EU) 2021/914. | [5] |
| Binding Corporate Rules (BCRs) | Supervisory-authority-approved intra-group data-protection rules enabling transfers within a corporate group (Art. 47). | [1] |
| Transfer impact assessment (TIA) | The Schrems II case-by-case assessment of whether the destination's law/practice ensures essentially equivalent protection, and what supplementary measures are needed. | [2][11] |
| Supplementary measures | Technical, contractual and organisational measures added to an Art. 46 tool to bring protection up to the EU standard. | [2][11] |
| Data bridge | UK government term for a UK adequacy determination permitting transfers without further safeguards (e.g., the UK Extension to the EU-US DPF). | [17] |

# Background

Under Directive 95/46/EC the EU already restricted transfers to "third countries" without adequate protection. The GDPR carried this forward and strengthened it, reflecting the **Charter of Fundamental Rights** (Arts. 7, 8, 47) and a line of CJEU authority insisting that data subjects retain **essentially equivalent** protection wherever their data goes [1][2].

The transatlantic dimension has been especially turbulent. The Commission's **Safe Harbor** adequacy decision was struck down in **Schrems I** (2015) [3]; its replacement, the **Privacy Shield**, was struck down in **Schrems II** (2020) [2]. Each time the CJEU found that US surveillance law and the absence of effective redress for EU data subjects prevented essential equivalence. In response the US enacted **Executive Order 14086** (2022) and created a two-layer redress mechanism culminating in the **Data Protection Review Court**; on that basis the Commission adopted the **EU-US Data Privacy Framework** adequacy decision on 10 July 2023 [4][10]. Predictably, the DPF was itself challenged — the **Latombe** litigation — making the current-status question a moving target that this document live-verifies [6][7].

# Legal Framework

Chapter V builds a **layered permission system**. Article 44 states the general principle; Articles 45–47 and 49 supply the specific gateways; Article 48 addresses foreign court/authority orders; Article 50 concerns international cooperation. The exporter must identify a valid gateway **before** the transfer and be able to evidence it [1].

The layers, in order of preference:

- **Article 45 — Adequacy.** Transfer to a country/territory/sector covered by a Commission adequacy decision. No further authorisation needed.
- **Article 46 — Appropriate safeguards.** Where there is no adequacy: SCCs, BCRs, approved codes of conduct, approved certification mechanisms, or (with authorisation) ad hoc clauses. Each must provide enforceable rights and effective remedies.
- **Article 47 — BCRs.** A specific Art. 46 route for intra-group transfers, approved by the lead supervisory authority via the consistency mechanism.
- **Article 49 — Derogations.** Exceptional, situation-specific gateways where neither adequacy nor safeguards are available.
- **Article 48.** Judgments/decisions of third-country courts or authorities are only enforceable grounds for transfer if based on an international agreement (e.g., MLAT).

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 44 | General principle — any transfer must comply with Chapter V so that the level of protection is **not undermined**; applies to onward transfers too. | [1] |
| Art. 45 | Transfers on the basis of an **adequacy decision**; sets the criteria the Commission assesses and provides for periodic review and amendment/repeal. | [1] |
| Art. 46 | Transfers subject to **appropriate safeguards** (SCCs, BCRs, codes, certification, ad hoc clauses) providing enforceable rights and effective remedies. | [1] |
| Art. 46(2)(c) | Standard data protection clauses **adopted by the Commission** — the 2021 SCCs (Decision (EU) 2021/914). | [1][5] |
| Art. 47 | **Binding Corporate Rules** — content requirements and the approval route via the consistency mechanism. | [1] |
| Art. 48 | Third-country court/authority orders are enforceable grounds only under an international agreement. | [1] |
| Art. 49 | **Derogations** for specific situations (explicit consent; contract; important public interest; legal claims; vital interests; public register; compelling legitimate interests). | [1] |
| Art. 50 | International cooperation for the protection of personal data. | [1] |

## Relevant Recitals

*Recitals are interpretive aids, not binding operative provisions [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 101 | Flows of personal data to and from third countries are necessary but must not undermine the level of protection; sets the frame for Chapter V. | [1] |
| Recital 103–104 | Adequacy — the Commission may decide a third country/territory/sector ensures an adequate (essentially equivalent) level of protection. | [1] |
| Recital 108–109 | Appropriate safeguards and the use of standard clauses/BCRs where adequacy is absent. | [1] |
| Recital 111–112 | Derogations must be construed **restrictively** and relate to occasional, non-systematic transfers. | [1] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Schrems I (Schrems v DPC) | CJEU (Grand Chamber), C-362/14, ECLI:EU:C:2015:650, 6 Oct 2015 | Invalidated the **Safe Harbor** adequacy decision; a supervisory authority must be able to examine transfer complaints even under an adequacy decision. | Establishes that adequacy decisions are reviewable and that surveillance access defeats adequacy [3]. |
| Schrems II (DPC v Facebook Ireland & Schrems) | CJEU (Grand Chamber), C-311/18, ECLI:EU:C:2020:559, 16 July 2020 | Invalidated the **Privacy Shield**; upheld the **SCCs** in principle but required exporters to assess destination law and apply **supplementary measures**, suspending transfers where equivalence cannot be ensured. | The foundational transfers judgment; source of the TIA/supplementary-measures duty [2]. |
| Latombe v Commission | General Court (Tenth Chamber, Extended), T-553/23, judgment 3 Sep 2025 | **Dismissed** the action to annul the EU-US DPF adequacy decision; ruled on the substance and upheld the 2023 Decision on the facts/law at adoption. | First judicial test of the DPF; confirms it stands at first instance [6]. |
| Latombe v Commission (appeal) | Court of Justice, **C-703/25 P**, appeal lodged 31 Oct 2025 (**pending**) | No ruling yet; seeks to set aside the General Court's judgment. | The DPF's continued validity is **not finally settled**; a merits reversal would be the third invalidation of a transatlantic framework [7]. |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **EDPB Recommendations 01/2020** set out the **six-step** transfer roadmap: (1) map transfers; (2) identify the Art. 46 tool; (3) assess whether the tool is effective in light of destination law/practice (the **TIA**); (4) adopt **supplementary measures** if needed; (5) take any procedural steps; (6) re-evaluate periodically [11]. The EDPB stresses that measures must be **effective in practice**, and that where problematic laws apply, only robust **technical** measures (e.g., strong encryption with keys held in the EEA, effective pseudonymisation) may suffice [11]. *(Regulatory interpretation.)*
- **Derogations are a last resort.** The EDPB (Guidelines 2/2018) reads Art. 49 restrictively: derogations are for **occasional, non-repetitive** transfers; "necessity" for a contract is interpreted strictly; and consent must be **explicit, specific and informed of the risks** of transferring without adequacy or safeguards [11][12]. *(Regulatory interpretation.)*
- The **European Commission** maintains and periodically reviews the **adequacy list**; adequacy decisions are living instruments that can be amended, suspended or repealed if protection deteriorates [9]. *(Regulatory interpretation.)*
- The **ICO** operates the UK equivalents: it publishes the **IDTA**, the **UK Addendum** to the EU SCCs, and a **transfer risk assessment (TRA)** tool that is methodologically distinct from (though compatible with) the EDPB TIA [14][15][18]. *(Regulatory interpretation.)*

## Adequacy — the current list (Art. 45)

As of this document's date, the Commission recognises (fully or partially) a set of third countries/territories including **Andorra, Argentina, Canada (commercial organisations), Faroe Islands, Guernsey, Israel, Isle of Man, Japan, Jersey, New Zealand, the Republic of Korea, Switzerland, the United Kingdom, the United States (commercial organisations certified under the DPF), and Uruguay** [9]. The **authoritative, current** list is the Commission's adequacy-decisions page — consult it directly, because entries are added and reviewed over time [9]. With the exception of the UK, these decisions do not cover the law-enforcement sector (Directive (EU) 2016/680) [9].

# Technical Considerations

- **Map the flows first** — a transfer occurs whenever personal data is sent to, **or made accessible from**, a third country, including remote support access, global admin consoles, and CDN/edge nodes; "no data at rest abroad" does not by itself avoid Chapter V [1][11]. *(Legal obligation / interpretation.)*
- **Supplementary measures are mostly technical** — where the Art. 46 tool alone is insufficient, the effective options are strong **encryption in transit and at rest with EEA-held keys**, effective **pseudonymisation**, and split/multi-party processing; access-in-the-clear by the importer generally defeats these protections [2][11]. *(Best practice grounded in obligation.)*
- **Key management is the crux** — a technical measure is only as good as key custody; keys accessible to the importer (or to the importer's jurisdiction) undermine the measure [11]. *(Best practice.)*
- **Instrument your data map** — maintain transfer records inside the Art. 30 RoPA (destinations, mechanism, TIA reference, supplementary measures) so the mechanism is evidenced on demand [1]. *(Legal obligation.)*

# Hosting Considerations

- **Cloud = transfers, usually** — most hyperscale and SaaS hosting entails at least remote access from outside the EEA; assess each provider's regions, sub-processors, and support-access model against Chapter V [1][2]. *(Legal obligation.)*
- **Provider transfer paperwork** — providers typically offer the **2021 SCCs** (and, for UK data, the **IDTA/UK Addendum**) in their DPAs; the customer, as exporter, still owns the **TIA** and cannot delegate that judgement [5][11][15]. *(Legal obligation.)*
- **DPF-certified importers** — where a US provider is on the **Data Privacy Framework List**, transfers to it can rely on Art. 45 adequacy instead of SCCs — but only while the DPF stands, and only for the certified entity/scope; keep an SCC fallback ready [4][19]. *(Legal obligation / editorial recommendation.)*
- **EEA data residency options** — provider "EU data boundary"/sovereign-cloud offerings reduce but do not always eliminate third-country access (e.g., global support); verify the access model, not just the storage region. *(Editorial recommendation.)*

# Game Hosting Considerations

- **Global player bases mean constant transfers** — matchmaking, telemetry, anti-cheat, voice/chat and crash reporting frequently route player data (usernames, device IDs, IP addresses) to third-country servers or vendors; each is a restricted transfer needing a Chapter V basis [1]. *(Legal obligation.)*
- **Third-party SDKs** — ads, analytics and crash SDKs often transfer to the US or elsewhere; inventory them and confirm their transfer mechanism (DPF certification or SCCs + TIA) [4][5][11]. *(Legal obligation.)*
- **Children's data raises the bar** — where minors are involved, rely-on-consent derogations are especially fragile and supplementary measures should be stronger; align with the ICO Children's Code where UK children are in scope. *(Best practice.)*
- **Live-ops latency vs. residency** — the pressure to place edge servers close to players must be reconciled with transfer rules; prefer EEA/adequate regions for identifiable player data where feasible. *(Editorial recommendation.)*

# AI Considerations

- **Training and inference transfers** — sending personal data to a third-country model provider (or a model hosted there) for training or inference is a restricted transfer; a Chapter V basis and TIA are required in addition to a lawful basis under Art. 6 [1][2][11]. *(Legal obligation.)*
- **US model APIs** — many foundation-model APIs are operated by US entities; check for **DPF certification** (Art. 45 route) or fall back to **SCCs + supplementary measures**, noting that clear-text prompt/response access by the importer weakens technical measures [4][11]. *(Legal obligation / interpretation.)*
- **AI Act runs in parallel** — Chapter V does not displace the EU AI Act; where an AI system processes personal data across borders, both regimes apply (cross-ref `ai-act-foundations`). *(Cross-reference.)*
- **Minimise before you transfer** — pseudonymise/aggregate training data before export where possible, reducing both transfer risk and lawful-basis exposure. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** (the law requires) / **BEST PRACTICE** (standards/regulator consensus) / **EDITORIAL RECOMMENDATION** (this pipeline suggests).

1. **Inventory all transfers** — build a transfer register (destination, importer, data categories, mechanism, TIA, supplementary measures) within the RoPA. *(OBLIGATION.)* [1]
2. **Prefer adequacy** — where the destination is covered by an adequacy decision (or DPF certification for the specific US importer), rely on Art. 45 and record the basis. *(OBLIGATION.)* [4][9]
3. **Use the 2021 SCCs correctly** — select the right **module** (C2C, C2P, P2P, P2C), complete the annexes, and integrate them with the Art. 28 DPA where the importer is a processor. *(OBLIGATION.)* [5]
4. **Run a TIA before relying on Art. 46** — follow the EDPB six-step method; document destination-law analysis and the equivalence conclusion. *(OBLIGATION + BEST PRACTICE.)* [11]
5. **Add supplementary measures** where the TIA shows a gap — prioritise strong encryption/pseudonymisation with EEA-held keys; if no measure suffices, **do not transfer**. *(OBLIGATION.)* [2][11]
6. **Treat Art. 49 derogations as exceptional** — do not use consent or contract necessity to justify routine, bulk transfers; document why a derogation genuinely applies. *(OBLIGATION.)* [1][11]
7. **For UK data, use UK tools** — the **IDTA**, or the **EU SCCs + UK Addendum**, plus a UK **TRA**; rely on UK data bridges (incl. the UK Extension to the DPF, made by SI 2023/1028) where available. *(OBLIGATION.)* [8][15][16][17]
8. **Keep a fallback and monitor the DPF** — because the DPF is under appeal (C-703/25 P), maintain SCC fallbacks for US flows and track the litigation. *(EDITORIAL RECOMMENDATION.)* [6][7]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Transferring with **no valid Chapter V mechanism** | Medium | High | Arts. 44–46 [1] | Transfer register; pre-transfer mechanism sign-off | Low |
| R2 | **Over-reliance on the DPF** if the CJEU invalidates it on appeal | Medium | High | C-703/25 P [6][7] | SCC fallback ready; monitor litigation; scenario plan | Medium |
| R3 | Using **SCCs without a TIA** / supplementary measures | Medium | High | Schrems II; Rec 01/2020 [2][11] | Mandatory TIA workflow; technical measures library | Low |
| R4 | **Misusing Art. 49 derogations** for systematic transfers | Medium | Medium | Art. 49; Rec restrictive reading [1][11] | Derogation gate with legal review; document occasional use | Low |
| R5 | **Ineffective supplementary measures** (importer holds keys/clear-text) | Medium | High | Rec 01/2020 [11] | EEA-held keys; pseudonymisation; access review | Medium |
| R6 | **UK/EU tool mismatch** (EU SCCs used for UK data without Addendum) | Medium | Medium | UK GDPR; IDTA/Addendum [15] | Use IDTA or SCCs+Addendum; jurisdiction check | Low |
| R7 | **Onward transfers** by the importer defeat protection | Medium | Medium | Art. 44 [1] | Onward-transfer clauses; sub-processor controls | Medium |
| R8 | **Stale mechanism** after an adequacy decision is amended/repealed | Low | High | Art. 45 review [9] | Periodic re-verification; adequacy-list watch | Low |

# Implementation Roadmap

- **Phase 0 — Transfer discovery:** Map every flow leaving the EEA/UK, including remote access and sub-processors. *Depends on:* data map/RoPA. *Effort:* Medium.
- **Phase 1 — Mechanism selection:** Assign a Chapter V basis per flow (adequacy/DPF → SCCs/BCRs → derogation); document rationale. *Effort:* Medium.
- **Phase 2 — TIAs & supplementary measures:** Run TIAs for Art. 46 flows; implement technical measures (encryption/pseudonymisation, key custody). *Effort:* High.
- **Phase 3 — UK alignment:** Apply IDTA/UK Addendum and TRAs for UK data; confirm data-bridge reliance where used. *Effort:* Medium.
- **Phase 4 — Contracts & BCRs:** Integrate SCCs with Art. 28 DPAs; for intra-group flows, evaluate BCRs. *Effort:* Medium–High.
- **Phase 5 — Monitor & re-verify:** Track adequacy changes and the DPF appeal; re-evaluate TIAs periodically. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Transfers unmapped; mechanisms ad hoc or absent. | No transfer register; SCCs unsigned. |
| 2 | Managed | Major transfers identified; SCCs in place but no TIAs. | Partial register; provider DPAs signed. |
| 3 | Defined | Documented mechanism per flow; TIAs run; UK tools applied. | Transfer register in RoPA; TIA library. |
| 4 | Quantitatively Managed | Supplementary measures verified effective; metrics on coverage/re-verification. | Key-custody controls; KPIs; periodic re-TIA. |
| 5 | Optimising | Automated transfer discovery; DPF/adequacy watch; scenario-tested fallbacks. | Continuous monitoring; rehearsed SCC fallback. |

# Audit Questions

1. Can you produce a transfer register mapping each third-country flow to a Chapter V mechanism? *(Arts. 44–46 [1].)*
2. For US flows, do you rely on **DPF certification** (verified on the DPF List) or SCCs — and is a fallback ready? *(Art. 45; [4][19].)*
3. Where SCCs/BCRs are used, where is the **TIA**, and what **supplementary measures** were applied? *(Schrems II; Rec 01/2020 [2][11].)*
4. Are the **correct 2021 SCC modules** selected and annexes completed for each relationship? *(Art. 46(2)(c); Decision 2021/914 [5].)*
5. For any **Art. 49 derogation**, what makes the transfer occasional/necessary, and who approved it? *(Art. 49 [1][11].)*
6. For **UK data**, do you use the **IDTA** or **SCCs + UK Addendum**, plus a UK **TRA**? *([15][16][18].)*
7. How do you monitor **adequacy changes** and the **DPF appeal (C-703/25 P)**? *([7][9].)*
8. How are **onward transfers** by importers controlled? *(Art. 44 [1].)*

# Implementation Checklist

- [ ] Transfer register built and embedded in the RoPA (destination, mechanism, TIA, measures).
- [ ] Adequacy/DPF reliance recorded where applicable, with DPF-List verification for US importers.
- [ ] 2021 SCCs executed with correct module and completed annexes; integrated with Art. 28 DPAs.
- [ ] TIA completed for every Art. 46 flow (EDPB six-step method).
- [ ] Supplementary measures implemented and verified (EEA-held keys; pseudonymisation).
- [ ] Art. 49 derogations gated, justified and documented as exceptional.
- [ ] UK flows use IDTA or SCCs + UK Addendum, with a UK TRA.
- [ ] SCC fallback prepared for US flows; DPF appeal (C-703/25 P) on the watch-list.
- [ ] Onward-transfer and sub-processor controls in place.
- [ ] Periodic re-verification cadence set for TIAs and adequacy status.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text — Chapter V, Arts. 44–50.** EUR-Lex, CELEX 02016R0679-20160504. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504 — ELI: https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [2] **Data Protection Commissioner v Facebook Ireland & Schrems ("Schrems II")**, C-311/18, ECLI:EU:C:2020:559. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:62018CJ0311
- [3] **Schrems v Data Protection Commissioner ("Schrems I")**, C-362/14, ECLI:EU:C:2015:650. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62014CJ0362
- [4] **Commission Implementing Decision (EU) 2023/1795 of 10 July 2023** on the adequate level of protection under the EU-US Data Privacy Framework. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dec_impl/2023/1795/oj
- [5] **Commission Implementing Decision (EU) 2021/914 of 4 June 2021** on standard contractual clauses for the transfer of personal data to third countries. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj
- [6] **Latombe v Commission**, General Court (Tenth Chamber, Extended), T-553/23, judgment of 3 September 2025. EUR-Lex, CELEX 62023TJ0553. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:62023TJ0553
- [7] **Latombe v Commission (appeal)**, Court of Justice, Case **C-703/25 P**, appeal lodged 31 October 2025 (pending) — OJ notice. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:C_202506610
- [8] **The Data Protection (Adequacy) (United States of America) Regulations 2023 (SI 2023/1028)** — UK Extension to the EU-US DPF ("UK-US data bridge"). legislation.gov.uk. https://www.legislation.gov.uk/uksi/2023/1028/contents/made

## Regulatory Guidance

- [9] **Adequacy decisions — international dimension of data protection** (current adequacy list and criteria). European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/adequacy-decisions_en
- [10] **EU-US data transfers / EU-US Data Privacy Framework** (adequacy background, EO 14086, Data Protection Review Court). European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/eu-us-data-transfers_en
- [11] **Recommendations 01/2020 on measures that supplement transfer tools** (six-step method; supplementary measures). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-012020-measures-supplement-transfer_en
- [12] **Guidelines, Recommendations & Best Practices** (incl. Guidelines 2/2018 on Art. 49 derogations). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/general-guidance/guidelines-recommendations-best-practices_en
- [13] **Commission renews adequacy decisions for the United Kingdom** (renewed to 27 December 2031; IP/25/3059). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_25_3059
- [14] **International transfers — guidance and resources.** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/
- [15] **What are standard data protection clauses (the UK IDTA and the Addendum)?** ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/appropriate-safeguards/what-are-standard-data-protection-clauses-the-uk-idta-and-the-addendum/
- [16] **How does the UK Extension to the EU-US Data Privacy Framework work?** ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/adequacy-regulations/how-does-the-uk-extension-to-the-eu-us-data-privacy-framework-work/
- [17] **UK-US data bridge: factsheet for UK organisations.** GOV.UK / DSIT. https://www.gov.uk/government/publications/uk-us-data-bridge-supporting-documents/uk-us-data-bridge-factsheet-for-uk-organisations
- [18] **Completing a transfer risk assessment (TRA).** ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/completing-a-transfer-risk-assessment/
- [19] **EU-U.S. Data Privacy Framework — Program Overview / DPF List.** U.S. Department of Commerce. https://www.dataprivacyframework.gov/Program-Overview

## Standards

Not Applicable — Chapter V compliance turns on legal mechanisms (adequacy, SCCs, BCRs, derogations) rather than a technical standard. Where supplementary measures require security controls (encryption, key management, pseudonymisation), those map to ISO/IEC 27001 and are treated in `privacy-engineering-foundations`.

## Academic Sources

Not Applicable — this reference relies on primary legislation, CJEU judgments, and regulatory guidance. Analytical sub-topics (e.g., surveillance-law equivalence, encryption efficacy as a supplementary measure) may cite peer-reviewed literature.

# Further Reading

*Non-authoritative; provided for orientation only.*

- IAPP — news and analysis tracking the Latombe litigation and DPF developments. https://iapp.org/
- European Commission — first periodic review of the EU-US DPF (Oct 2024), for functioning-in-practice context. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/eu-us-data-transfers_en

# Related Documents

- `gdpr-foundations` — parent foundation; this document **details** its Chapter V material (**prerequisite reading**).
- `uk-gdpr-foundations` — UK GDPR/DPA 2018 divergence, incl. UK transfer regime context (planned).
- `privacy-engineering-foundations` — encryption/pseudonymisation as supplementary measures (Arts. 25/32).
- `eprivacy-foundations` — parallel electronic-communications rules.
- `ai-act-foundations` — parallel AI regime for cross-border AI processing.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Ch. V; Decisions 2021/914 and 2023/1795), CJEU (Schrems I/II; Latombe T-553/23 and appeal C-703/25 P), EDPB Rec 01/2020, European Commission, ICO and GOV.UK. **EU-US DPF current status live-verified 2026-07-11.** | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch gate; EU-US DPF status independently confirmed; frozen in release 0.10.0. | Human reviewer |
