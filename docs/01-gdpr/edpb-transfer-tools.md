---
id: edpb-transfer-tools
title: "GDPR Transfer Tools: SCCs, BCRs & Transfer Impact Assessments"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: GDPR (EU)
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-12
updated: 2026-07-12
review_due: 2027-07-12
confidence: High
supersedes: Not Applicable
related: [gdpr-transfers, uk-transfers, gdpr-foundations, cloud-shared-responsibility, anonymisation-techniques]
tags: [gdpr, international-transfers, sccs, bcr, tia, supplementary-measures, schrems-ii, docking-clause, idta, uk-addendum, european-essential-guarantees]
legal_basis: Regulation (EU) 2016/679 (Arts. 46–47); Commission Implementing Decision (EU) 2021/914
sources_verified: 2026-07-12
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | edpb-transfer-tools |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.18.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-12 |
| Last Updated | 2026-07-12 |
| Review Due | 2027-07-12 |
| Confidence | High |
| Approved By | <pending human review> |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is the practitioner deep-dive on the Article 46 **toolbox** and sits beneath two approved siblings: `gdpr-transfers` (EU Chapter V overview, adequacy and the EU-US Data Privacy Framework) and `uk-transfers` (the UK regime). Adequacy and the DPF are **not** re-explained here at length — see those documents. **Live-verified point (2026-07-12):** the Commission's **additional SCC module for importers already subject to GDPR Art. 3(2)** is still **not adopted** — it remains a consultation/draft initiative; do not rely on it (see AI Considerations and Operational Guidance) [11][12].

# Executive Summary

Where no adequacy decision covers a destination [14], **Article 46 GDPR** requires the exporter to put in place **appropriate safeguards** that provide data subjects with enforceable rights and effective legal remedies [1]. This document is the operational manual for the three Article 46 instruments most organisations actually use: the **2021 Standard Contractual Clauses (SCCs)** adopted by Commission Implementing Decision (EU) 2021/914 [3]; **Binding Corporate Rules (BCRs)** under Article 47 [1]; and the **Transfer Impact Assessment (TIA)** and supplementary-measures methodology that **Schrems II** made mandatory for every Article 46 tool [2][7].

Three mechanics dominate. First, the **2021 SCCs are modular**: one Decision contains four modules — controller-to-controller (Module One), controller-to-processor (Module Two), processor-to-processor (Module Three) and processor-to-controller (Module Four) — selected by the parties' roles, populated through annexes, and joined by a **docking clause** that lets new parties accede over time [3]. The clauses carry their own built-in TIA obligation (Clause 14) and rules on public-authority access (Clause 15) [3]. Second, **BCRs** are supervisory-authority-approved intra-group rules whose mandatory content is fixed by Article 47(2) and detailed in the EDPB's **Recommendations 1/2022** for controller BCRs (which replace the WP256/WP257 referentials); approval runs through a **lead supervisory authority** and the **Article 63/64 consistency mechanism**, with a binding EDPB opinion before national authorisation [8][9][10]. Third, the **TIA** follows the EDPB **six-step** method of **Recommendations 01/2020**, benchmarked against the **European Essential Guarantees** of **Recommendations 02/2020**; where destination law or practice defeats the tool, only **effective supplementary measures** (technical, contractual, organisational) can save the transfer — and where none suffices, the transfer must not proceed [7][8].

For UK-origin data the toolbox differs: the exporter uses the ICO **International Data Transfer Agreement (IDTA)** or the **UK Addendum** to the EU SCCs, and runs a **Transfer Risk Assessment** (now the statutory "data protection test") — treated in full in `uk-transfers` and summarised here for selection purposes [15][16].

# Key Takeaways

- **Article 46 tools all now carry a case-by-case duty.** Since **Schrems II**, an SCC, BCR or other Art. 46 safeguard is lawful only if the exporter verifies that the destination affords essentially equivalent protection and, where it does not, applies effective **supplementary measures** [2][7]. *(Case law / regulatory interpretation.)*
- **The 2021 SCCs are a single modular Decision.** Decision (EU) 2021/914 contains **four modules** (C2C, C2P, P2P, P2C); the parties select the module matching their roles, complete the **Annexes** (parties, description of transfer, technical/organisational measures, sub-processors), and may add optional clauses [3]. *(Legal obligation.)*
- **The docking clause enables accession.** Clause 7 (the "docking clause") lets an entity that is not an original signatory join the same SCCs later, avoiding a fresh contract per new party [3]. *(Legal obligation.)*
- **The SCCs embed the TIA.** Clause 14 requires the parties to warrant they have **no reason to believe** local laws prevent the importer from meeting the clauses, and Clause 15 governs the importer's response to **public-authority access requests** — so the TIA is contractual, not merely regulatory guidance [3][7]. *(Legal obligation.)*
- **BCR content is prescribed by Art. 47(2).** BCRs must be legally binding, apply to every group member, and contain the elements listed in Art. 47(2)(a)–(n); the EDPB's **Recommendations 1/2022** (controller BCRs) give the mandatory referential and application form, replacing WP256 rev.01 [1][9]. *(Legal obligation / regulatory interpretation.)*
- **BCR approval runs through the consistency mechanism.** The **lead supervisory authority** assesses the application and submits a draft decision to the **EDPB for a binding opinion under Art. 64** before the competent authority authorises the BCRs [8][10]. *(Legal obligation.)*
- **The TIA is a six-step method.** EDPB **Recommendations 01/2020** set the roadmap (map → identify tool → assess → supplement → formalise → re-evaluate); **Recommendations 02/2020** (European Essential Guarantees) supply the yardstick for surveillance-law assessment [7][8]. *(Regulatory interpretation.)*
- **Supplementary measures must be effective in practice.** Robust **encryption** with keys held outside the importer's jurisdiction and effective **pseudonymisation** can rescue a transfer; importer access to data **in the clear** generally cannot be cured by contractual or organisational measures alone [7]. *(Regulatory interpretation / best practice.)*
- **UK data needs UK tools.** Use the ICO **IDTA** or the **EU SCCs + UK Addendum**, plus a **Transfer Risk Assessment / "data protection test"** — never bare EU SCCs for UK restricted transfers (detail in `uk-transfers`) [15][16]. *(Legal obligation.)*
- **PENDING — the Art. 3(2) SCC module is not yet adopted.** The Commission's planned additional SCCs for **importers already directly subject to GDPR** under Art. 3(2) remain a **draft/consultation** initiative as at this document's date; today the 2021 SCCs plus a bespoke solution are the only options for that gap [11][12]. *(Live-verify.)*

# Purpose

This document is the toolbox-level companion to `gdpr-transfers`. It supports:

- **Compliance implementation** — selecting the correct SCC module, completing the annexes, wiring in the docking clause, structuring a BCR application, and running a defensible TIA.
- **Legal research** — a mapped reading of the operative clauses of Decision (EU) 2021/914, Article 47(2), and the EDPB transfer recommendations.
- **Engineering triage** — deciding which supplementary measures are effective for a given data flow and importer access model.
- **EU/UK dual operation** — choosing between the EU SCCs, the UK IDTA and the UK Addendum for the same vendor.

It assumes the reader knows the Chapter V hierarchy (adequacy → Art. 46 safeguards → Art. 49 derogations) from `gdpr-transfers`, and it does **not** re-explain adequacy decisions or the EU-US Data Privacy Framework beyond what is needed to position the tools.

# Scope

**In scope:** The mechanics of the 2021 SCCs (four modules, module selection, annex population, the docking clause, Clauses 14–15 and the local-law/access provisions); Binding Corporate Rules (Art. 47(2) content, BCR-C vs BCR-P, the lead-SA + Art. 64 approval route); the Transfer Impact Assessment methodology (EDPB Recommendations 01/2020 six steps and Recommendations 02/2020 European Essential Guarantees); the technical/contractual/organisational supplementary-measures catalogue; and the UK IDTA/Addendum selection at summary level.

**Out of scope (cross-referenced):** The Chapter V overview, adequacy list and derogations (`gdpr-transfers`); the UK statutory regime, the DUAA "data protection test" and data bridges in full (`uk-transfers`); the substance of the EU-US Data Privacy Framework (`gdpr-transfers`); the engineering of encryption/pseudonymisation as controls (`anonymisation-techniques`, `privacy-engineering-foundations`); and the cloud provider/customer allocation of transfer paperwork (`cloud-shared-responsibility`).

**Assumptions:** Article references are to the consolidated GDPR on EUR-Lex [1]. "Exporter"/"importer" bear the meanings in Decision (EU) 2021/914 [3]. UK references are to the UK GDPR read with the DPA 2018 and DUAA 2025 (see `uk-transfers`).

# Definitions

*Shared terms (SCCs, BCRs, TIA, IDTA, restricted transfer, adequacy decision) are in `GLOSSARY.md`. Only toolbox-specific or narrowed usages are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| SCC module | One of the four role-based variants inside Decision (EU) 2021/914 — Module One (C2C), Two (C2P), Three (P2P), Four (P2C) — selected according to the exporter's and importer's controller/processor status. | [3] |
| Docking clause | Clause 7 of the 2021 SCCs, an optional provision allowing an entity that is not an original signatory to accede to the existing clauses as exporter or importer by completing the annex. | [3] |
| Transfer Impact Assessment (TIA) | The Schrems II case-by-case assessment of whether the chosen Art. 46 tool is effective given the destination's law and practice, following the EDPB six-step method. | [2][7] |
| European Essential Guarantees (EEG) | The four benchmarks (clear/precise/accessible rules; necessity and proportionality; independent oversight; effective remedies) used to judge whether third-country surveillance law is compatible with the EU standard. | [8] |
| Supplementary measures | Technical, contractual or organisational measures added to an Art. 46 tool to raise protection to the EU standard where the TIA finds a gap. | [7] |
| BCR-C / BCR-P | Controller Binding Corporate Rules and Processor Binding Corporate Rules — the intra-group Art. 47 instruments for group-internal transfers by, respectively, controllers and processors. | [1][9] |

# Background

Standard contractual clauses and BCRs predate the GDPR. Under Directive 95/46/EC the Commission issued three sets of SCCs (2001, 2004 controller-to-controller, and 2010 controller-to-processor), and the Article 29 Working Party developed BCR referentials (WP256 for controller BCRs, WP257 for processor BCRs). The GDPR carried these tools into **Article 46** (appropriate safeguards) and **Article 47** (BCRs) and put BCR approval on a statutory footing through the consistency mechanism [1].

Two events reshaped the toolbox. First, **Schrems II** (16 July 2020) held that SCCs remain valid in principle but cannot be used mechanically: the exporter must assess the destination's law and, if the SCCs alone cannot ensure essentially equivalent protection, add supplementary measures or suspend the transfer [2]. The EDPB responded with **Recommendations 01/2020** on supplementary measures (the six-step method, adopted in final form on 18 June 2021) and **Recommendations 02/2020** on the European Essential Guarantees (adopted 10 November 2020) [7][8]. Second, the Commission modernised the clauses themselves: **Commission Implementing Decision (EU) 2021/914 of 4 June 2021** replaced the legacy SCCs with a single **modular** Decision that folds the Schrems II duty into the contract and, for processor relationships, also satisfies Article 28 [3].

A known gap remains. The 2021 SCCs assume the **importer is not itself subject to the GDPR**. Where an importer is directly caught by **Article 3(2)** (e.g., because it targets or monitors EU data subjects), the 2021 clauses do not fit neatly, and the EDPB pressed the Commission for a dedicated set. The Commission has consulted on such an additional module but, as at this document's date, has **not adopted** it [11][12].

# Legal Framework

Article 46(1) states the core rule: absent an adequacy decision, a transfer may proceed only if the exporter has provided **appropriate safeguards** and **on condition that enforceable data-subject rights and effective legal remedies** are available [1]. Article 46(2) then lists the safeguards that need **no specific supervisory-authority authorisation** — including standard clauses adopted by the Commission (Art. 46(2)(c)), standard clauses adopted by a supervisory authority (Art. 46(2)(d)), BCRs (via Art. 47), approved codes of conduct and approved certification mechanisms. Article 46(3) covers **ad hoc** clauses and administrative arrangements, which **do** require authorisation. Article 47 sets the content and approval regime for BCRs [1].

The two workhorses — SCCs and BCRs — are treated below. Both must be read with the overarching Article 44 principle that the level of protection must **not be undermined**, including on onward transfer, and with the Charter rights (Arts. 7, 8, 47) that Schrems II applied [1][2][6].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 46(1) | Appropriate safeguards required absent adequacy, **and** enforceable rights + effective remedies for data subjects. | [1] |
| Art. 46(2)(c) | **Standard contractual clauses adopted by the Commission** — the 2021 SCCs (Decision (EU) 2021/914). | [1][3] |
| Art. 46(2)(d) | Standard clauses adopted by a supervisory authority and approved by the Commission (the legal family the UK IDTA/Addendum belongs to domestically). | [1] |
| Art. 46(3)(a) | **Ad hoc** contractual clauses — valid only with supervisory-authority authorisation. | [1] |
| Art. 47(1) | BCRs must be **legally binding**, apply to and be enforced by every group member, and expressly confer **enforceable rights** on data subjects. | [1] |
| Art. 47(2)(a)–(n) | The mandatory **content** of BCRs (structure, data flows, binding nature, principles, rights, liability, complaints, training, audit, cooperation, etc.). | [1] |
| Art. 47(3) | The EDPB may specify the **format and procedures** for BCR exchange between controllers, processors and supervisory authorities. | [1] |
| Art. 49 | Derogations — the last-resort route where no Art. 46 tool is used (detail in `gdpr-transfers`). | [1] |
| Arts. 63–64 | The **consistency mechanism** and binding **EDPB opinion** through which BCRs are approved. | [1][10] |

## Relevant Recitals

*Recitals are interpretive aids, not binding operative provisions [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 108 | Appropriate safeguards should compensate for the lack of data-protection in a third country, including enforceable rights and effective remedies. | [1] |
| Recital 109 | Controllers/processors should be encouraged to use SCCs; they may add further clauses provided they do not contradict the standard clauses. | [1] |
| Recital 110 | BCRs should cover all group members and the whole processing chain; the approval regime is set out. | [1] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Schrems II (DPC v Facebook Ireland & Schrems) | CJEU (Grand Chamber), C-311/18, ECLI:EU:C:2020:559, 16 July 2020 | SCCs remain valid, but the exporter must assess destination law and apply **supplementary measures**, suspending the transfer where equivalence cannot be ensured; Privacy Shield invalidated. | The source of the TIA/supplementary-measures duty that now conditions every Art. 46 tool [2]. |
| Latombe v Commission (appeal) | Court of Justice, **C-703/25 P**, appeal lodged 31 Oct 2025 (**pending**) | No ruling yet; seeks to set aside the General Court's dismissal of the challenge to the EU-US DPF adequacy decision. | Relevant because a DPF invalidation would push US flows back onto SCCs + TIA — keep an SCC fallback (detail in `gdpr-transfers`) [5]. |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **The six-step TIA is the EDPB's operative method.** Recommendations 01/2020 direct the exporter to (1) **know your transfers** (map them, including onward transfers); (2) **identify the transfer tool** relied on; (3) **assess** whether that tool is effective in light of the destination's law and practice; (4) **adopt supplementary measures** where step 3 shows a gap; (5) take any **procedural/formal steps** the measures require; and (6) **re-evaluate** at appropriate intervals [7]. *(Regulatory interpretation.)*
- **The European Essential Guarantees are the yardstick for step 3.** Recommendations 02/2020 distil CJEU/ECtHR case law into four guarantees: processing based on **clear, precise and accessible rules**; **necessity and proportionality** relative to legitimate aims; an **independent oversight** mechanism; and **effective remedies** for the individual. A destination's surveillance regime is assessed against these, not against a general impression of "risk" [8]. *(Regulatory interpretation.)*
- **Effectiveness is judged in practice, not on paper.** The EDPB stresses that a supplementary measure counts only if it actually prevents the identified access; where problematic laws give authorities access to data in the clear, **contractual and organisational measures alone will not suffice** and the exporter must rely on strong technical measures or not transfer (Recommendations 01/2020, Annex 2 use cases) [7]. *(Regulatory interpretation.)*
- **BCR guidance was rebuilt post-Schrems II.** The EDPB's **Recommendations 1/2022** on controller BCRs merge the old referential (WP256 rev.01) and application form (WP264) into one instrument, add a Schrems II transfer-assessment element, and specify the mandatory minimum content and the application form submitted to the BCR Lead [9]. *(Regulatory interpretation.)*
- **The Commission provides authoritative operational Q&A.** The Commission's SCC pages and BCR page explain module selection, the "no further authorisation" status of the 2021 SCCs, and the consistency-mechanism approval route for BCRs [10][11][13]. *(Regulatory interpretation.)*
- **UK divergence in the tools.** The ICO issues the **IDTA** (a standalone UK contract) and the **UK Addendum** (bolted onto the EU SCCs), and treats the exporter's Transfer Risk Assessment as the statutory **"data protection test"** — a risk-based alternative to the EDPB method (full treatment in `uk-transfers`) [15][16]. *(Regulatory interpretation.)*

## The 2021 SCC modules and how to select them

| Module | Relationship | Typical use | Key feature |
|--------|--------------|-------------|-------------|
| Module One | Controller → Controller (C2C) | Sharing customer data with an independent third-country controller (e.g., a joint-marketing partner). | Purpose-limitation and transparency obligations on the importer as an autonomous controller. |
| Module Two | Controller → Processor (C2P) | The most common SaaS/cloud case: EU controller instructs a third-country processor. | **Doubles as an Art. 28 DPA** — the clauses include the Art. 28(3) processor terms. |
| Module Three | Processor → Processor (P2P) | An EU processor sub-contracts to a third-country sub-processor on the controller's behalf. | Passes the controller's documented instructions down the chain. |
| Module Four | Processor → Controller (P2C) | A third-country controller receives data from an EU processor acting on that controller's instructions. | Applies only to what the EU processor adds; lighter obligations. |

**Selection rule:** identify each party's status (controller or processor) **for the specific transfer**, then pick the module that matches exporter→importer roles. Complete **Annex I** (parties, description of the transfer, competent supervisory authority), **Annex II** (technical and organisational security measures) and, for processor modules, **Annex III** (list of sub-processors) [3]. Optional docking (Clause 7) and choice of governing-law/forum clauses are configured at signature [3].

# Technical Considerations

- **Populate Annex II with real controls, not boilerplate.** Annex II must describe the **technical and organisational measures** the importer applies; regulators and courts read it as the security baseline the importer warrants, and it is also the natural place to record supplementary technical measures identified by the TIA [3][7]. *(Legal obligation grounded.)*
- **Match the supplementary measure to the access risk.** Where the TIA shows a risk of government access, the effective options are **strong encryption in transit and at rest with keys held outside the importer's jurisdiction**, effective **pseudonymisation** where the additional information stays in the EEA, and split or multi-party processing; the control must defeat the specific access identified, not merely exist [7]. *(Best practice grounded in obligation.)* See `anonymisation-techniques`.
- **Key custody is decisive.** A technical measure is only as strong as key management: keys accessible to the importer, or to the importer's authorities, collapse the protection [7]. *(Best practice.)*
- **Onward transfers inherit the burden.** Clause 8.7 (processor modules) restricts onward transfers to parties bound by the clauses or another Chapter V basis; wire sub-processor onboarding to a docking-clause or fresh-SCC step so the chain never breaks Art. 44 [1][3]. *(Legal obligation.)*
- **Record the tool in the RoPA.** Store per-flow which module/BCR is used, the TIA reference and the supplementary measures, so the mechanism is demonstrable on demand (see `gdpr-ropa`) [1]. *(Legal obligation.)*

# Hosting Considerations

- **Module Two is the default cloud case.** Most hyperscale/SaaS transfers are controller-to-processor; the provider offers Module Two SCCs inside its DPA, and those clauses also discharge the customer's Art. 28 obligations — but the **customer still owns the TIA** and cannot delegate that judgement [3][7]. *(Legal obligation.)* See `cloud-shared-responsibility`.
- **Sub-processor chains use Module Three + docking.** Where the provider sub-contracts (support, storage tiers, CDN), Module Three governs processor-to-sub-processor flows; the **docking clause** is the clean way to add new sub-processors without re-papering [3]. *(Legal obligation.)*
- **DPF-certified importers can sidestep SCCs.** If the US provider is on the **Data Privacy Framework List** for the relevant data, the transfer can rely on adequacy instead of SCCs — but only while the DPF stands and only for the certified scope; keep a Module Two SCC fallback ready (DPF substance in `gdpr-transfers`) [4][5][17]. *(Legal obligation / editorial recommendation.)*
- **Check the access model, not just the region.** "EU data boundary" offerings reduce but rarely eliminate third-country **access** (global support, admin consoles); the TIA must address remote access, which is itself a transfer [3][7]. *(Best practice.)*

# Game Hosting Considerations

- **Vendor SDKs drive module choice.** Ads, analytics, anti-cheat and crash-reporting SDKs are usually third-country **processors** (Module Two) or independent **controllers** (Module One); classify each SDK's role before selecting the module [3]. *(Legal obligation.)*
- **Telemetry pipelines need docking discipline.** Player telemetry often fans out to multiple downstream processors; use Module Three with the docking clause and a maintained sub-processor annex so live-ops vendor churn does not create unpapered transfers [3]. *(Best practice grounded in obligation.)*
- **Identifiers still need a TIA.** Usernames, device IDs and IP addresses are personal data; routing them to a third-country importer triggers the full TIA even for "just telemetry" [1][7]. *(Legal obligation.)*
- **Children raise the effectiveness bar.** Where minors' data is in scope, weak or purely contractual supplementary measures are hard to justify; prefer strong technical measures or EEA/adequate-region processing (align with the UK Children's Code where UK children are involved). *(Best practice.)*

# AI Considerations

- **Model providers are importers too.** Sending personal data to a third-country model provider for training or inference is a restricted transfer; select Module One or Module Two by the provider's role and run a TIA, noting that **clear-text prompt/response access** by the importer weakens technical measures [3][7]. *(Legal obligation.)*
- **The Art. 3(2) gap bites for global AI vendors.** Many AI vendors are **directly subject to GDPR** under Art. 3(2); the 2021 SCCs were not designed for that case and the dedicated additional module is **still unadopted**, so parties currently rely on the 2021 SCCs adapted, direct-compliance representations, or a bespoke Art. 46(3)(a) arrangement (which needs authorisation) — document the choice and track the Commission initiative [3][11][12]. *(Live-verify / editorial recommendation.)*
- **Minimise before export.** Pseudonymise or aggregate training data before transfer where feasible, which both reduces transfer risk and strengthens the TIA's effectiveness analysis [7]. *(Best practice.)* See `anonymisation-techniques`.
- **AI Act runs in parallel.** The transfer tools do not displace the EU AI Act obligations for cross-border AI processing (cross-ref `gdpr-foundations` and the AI-Act documents). *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** (the law requires) / **BEST PRACTICE** (standards/regulator consensus) / **EDITORIAL RECOMMENDATION** (this pipeline suggests).

1. **Classify the parties, then pick the module** — determine controller/processor status for the specific flow and select Module One, Two, Three or Four accordingly. *(OBLIGATION.)* [3]
2. **Complete every annex properly** — parties and transfer description (Annex I), real security measures (Annex II), sub-processors (Annex III); do not leave placeholder text. *(OBLIGATION.)* [3]
3. **Configure the docking clause** where new parties are foreseeable, so accession does not require a new contract each time. *(BEST PRACTICE.)* [3]
4. **Integrate Module Two/Three with Art. 28** — treat the processor-module clauses as the DPA; do not sign a conflicting separate DPA. *(OBLIGATION.)* [3]
5. **Run the six-step TIA before relying on the tool** — map, identify, assess against the European Essential Guarantees, supplement, formalise, re-evaluate; document the equivalence conclusion. *(OBLIGATION + BEST PRACTICE.)* [7][8]
6. **Apply effective supplementary measures** where the TIA finds a gap — prioritise strong encryption/pseudonymisation with keys outside the importer's reach; if no measure is effective, **do not transfer**. *(OBLIGATION.)* [7]
7. **For intra-group transfers, evaluate BCRs** — where SCCs multiply across many group entities, BCR-C/BCR-P can be more efficient; build the Art. 47(2) content and file through the lead SA and the Art. 64 consistency route. *(EDITORIAL RECOMMENDATION / OBLIGATION once chosen.)* [1][9][10]
8. **For UK data, use UK tools** — the **IDTA** or **EU SCCs + UK Addendum**, plus a Transfer Risk Assessment / "data protection test"; never bare EU SCCs (detail in `uk-transfers`). *(OBLIGATION.)* [15][16]
9. **Track the Art. 3(2) SCC module and the DPF appeal** — do not rely on an unadopted instrument, and keep SCC fallbacks for US flows against the Latombe appeal. *(EDITORIAL RECOMMENDATION.)* [5][11][12]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | **Wrong SCC module** selected for the parties' roles | Medium | Medium | Decision (EU) 2021/914 [3] | Role classification per flow; module-selection checklist | Low |
| R2 | **Incomplete or boilerplate annexes** (esp. Annex II security) | High | Medium | Clauses + Annex II [3] | Populate with real controls; legal + security sign-off | Low |
| R3 | **SCCs signed without a TIA** / supplementary measures | Medium | High | Schrems II; Rec 01/2020 [2][7] | Mandatory TIA workflow; technical-measures library | Low |
| R4 | **Ineffective supplementary measures** (importer holds keys/clear-text) | Medium | High | Rec 01/2020 use cases [7] | Keys outside importer's reach; pseudonymisation; access review | Medium |
| R5 | **Broken onward-transfer chain** (new sub-processor unpapered) | Medium | High | Art. 44; Clause 8.7 [1][3] | Docking-clause process; sub-processor annex maintenance | Low |
| R6 | **BCR content gaps** against Art. 47(2) / Rec 1/2022 | Medium | Medium | Art. 47(2); Rec 1/2022 [1][9] | Use the EDPB referential/application form; pre-submission review | Low |
| R7 | **UK/EU tool mismatch** (bare EU SCCs for UK data) | Medium | Medium | UK IDTA/Addendum [15][16] | Use IDTA or SCCs + UK Addendum; jurisdiction check | Low |
| R8 | **Relying on the unadopted Art. 3(2) SCC module** | Low | Medium | Consultation only [11][12] | Use current tools; track adoption; document interim choice | Low |
| R9 | **Over-reliance on the DPF** for US flows if invalidated on appeal | Medium | High | Latombe C-703/25 P [5] | Module Two SCC fallback; monitor litigation | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory & classify:** Map Art. 46 flows and classify each party's controller/processor role. *Depends on:* RoPA/data map. *Effort:* Medium.
- **Phase 1 — Instrument selection:** Choose SCC module (or BCR for intra-group; IDTA/Addendum for UK) per flow and record the rationale. *Effort:* Medium.
- **Phase 2 — Paper & annex:** Execute the clauses, complete Annexes I–III, configure docking and governing law; integrate processor modules with Art. 28. *Effort:* Medium.
- **Phase 3 — TIA & supplementary measures:** Run the six-step TIA against the European Essential Guarantees; implement and verify technical measures. *Effort:* High.
- **Phase 4 — BCR programme (if applicable):** Build Art. 47(2) content, file with the lead SA, manage the Art. 64 opinion. *Effort:* High.
- **Phase 5 — Monitor & re-verify:** Re-evaluate TIAs, track the Art. 3(2) module and the DPF appeal, refresh sub-processor annexes. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Legacy or mismatched SCCs; annexes blank; no TIA. | Wrong/2010 SCCs in use; no transfer register. |
| 2 | Managed | 2021 SCCs signed for major vendors; module sometimes mis-selected; TIAs ad hoc. | Provider DPAs signed; annexes partial. |
| 3 | Defined | Correct module per flow; annexes complete; six-step TIA documented; UK tools applied. | Module checklist; TIA library; docking process. |
| 4 | Quantitatively Managed | Supplementary measures verified effective; key custody controlled; BCRs where efficient; metrics on coverage. | Key-management controls; KPIs; periodic re-TIA. |
| 5 | Optimising | Automated party/role classification and sub-processor tracking; live watch on the Art. 3(2) module and DPF appeal; rehearsed fallbacks. | Continuous monitoring; tested SCC fallback for US flows. |

# Audit Questions

1. For each Art. 46 flow, which **SCC module** (or BCR) is used, and does it match the parties' controller/processor roles? *(Decision (EU) 2021/914 [3].)*
2. Are **Annexes I–III** fully completed, including a genuine description of technical and organisational measures? *([3].)*
3. Where new parties join, is the **docking clause** (or a fresh SCC) used so onward transfers stay papered? *(Art. 44; Clause 7/8.7 [1][3].)*
4. Where is the **TIA** for each tool, and does it assess the destination against the **European Essential Guarantees**? *(Schrems II; Rec 01/2020; Rec 02/2020 [2][7][8].)*
5. What **supplementary measures** were applied, and how is their effectiveness (esp. key custody) evidenced? *(Rec 01/2020 [7].)*
6. For any **BCRs**, do they contain the Art. 47(2) elements and follow the EDPB **Recommendations 1/2022**, approved via the lead SA and the Art. 64 opinion? *(Arts. 47, 63–64; Rec 1/2022 [1][9][10].)*
7. For **UK data**, do you use the **IDTA** or **SCCs + UK Addendum** with a Transfer Risk Assessment? *([15][16].)*
8. How are the **unadopted Art. 3(2) SCC module** and the **DPF appeal** tracked so reliance stays current? *([5][11][12].)*

# Implementation Checklist

- [ ] Each Art. 46 flow mapped with the parties' controller/processor roles classified.
- [ ] Correct 2021 SCC module selected (One/Two/Three/Four) per flow.
- [ ] Annex I (parties/transfer), Annex II (security measures) and Annex III (sub-processors) completed — no placeholders.
- [ ] Docking clause configured where new parties are foreseeable; onward-transfer (Clause 8.7) controls in place.
- [ ] Processor modules integrated with Art. 28 (no conflicting separate DPA).
- [ ] Six-step TIA completed and documented, benchmarked against the European Essential Guarantees.
- [ ] Supplementary measures implemented and their effectiveness (key custody) verified; transfer stopped where none suffices.
- [ ] BCRs (if used) built to Art. 47(2) / Recommendations 1/2022 and approved via the lead SA + Art. 64 opinion.
- [ ] UK flows use the IDTA or EU SCCs + UK Addendum with a Transfer Risk Assessment.
- [ ] Art. 3(2) SCC module and the DPF/Latombe appeal on the watch-list; SCC fallback prepared for US flows.

# References

*All links verified live (HTTP 200/redirect) on 2026-07-12 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text — Arts. 44–49 (esp. 46–47) and Recitals 108–110.** EUR-Lex, CELEX 02016R0679-20160504. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504 — ELI: https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [2] **Data Protection Commissioner v Facebook Ireland & Schrems ("Schrems II")**, C-311/18, ECLI:EU:C:2020:559. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:62018CJ0311
- [3] **Commission Implementing Decision (EU) 2021/914 of 4 June 2021** on standard contractual clauses for the transfer of personal data to third countries (the four modules; docking clause; Clauses 14–15). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dec_impl/2021/914/oj
- [4] **Commission Implementing Decision (EU) 2023/1795 of 10 July 2023** on the adequate level of protection under the EU-US Data Privacy Framework (context for DPF-certified importers). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dec_impl/2023/1795/oj
- [5] **Latombe v Commission (appeal)**, Court of Justice, Case **C-703/25 P**, appeal lodged 31 October 2025 (pending) — OJ notice. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:C_202506610
- [6] **Charter of Fundamental Rights of the European Union** (Arts. 7, 8, 47). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:12012P/TXT

## Regulatory Guidance

- [7] **Recommendations 01/2020 on measures that supplement transfer tools** (the six-step method; supplementary-measures use cases; v2.0 adopted 18 June 2021). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-012020-measures-supplement-transfer_en
- [8] **Recommendations 02/2020 on the European Essential Guarantees for surveillance measures** (adopted 10 November 2020). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-022020-european-essential-guarantees_en
- [9] **Recommendations 1/2022 on the Application for Approval and on the elements and principles to be found in Controller Binding Corporate Rules (Art. 47 GDPR)** — final version 2.0 (replaces WP256 rev.01 / WP264). European Data Protection Board. https://www.edpb.europa.eu/system/files/2023-06/edpb_recommendations_20221_bcr-c_v2_en.pdf
- [10] **Binding Corporate Rules (BCR)** — approval via the consistency mechanism (Arts. 63–64) and the EDPB opinion. European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/binding-corporate-rules-bcr_en
- [11] **Standard Contractual Clauses (SCC)** — Commission overview of the 2021 modular clauses and the planned additional set for importers subject to the GDPR. European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en
- [12] **Standard contractual clauses for the transfer of data to third-country controllers and processors subject to the GDPR** (Art. 3(2) importers) — initiative/consultation page (**not yet adopted** as at 2026-07-12). European Commission — Have Your Say. https://ec.europa.eu/info/law/better-regulation/have-your-say/initiatives/14404-Standard-contractual-clauses-for-the-transfer-of-data-to-third-country-controllers-and-processors-subject-to-the-GDPR_en
- [13] **New Standard Contractual Clauses — Questions and Answers overview** (module selection; "no further authorisation" status). European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/new-standard-contractual-clauses-questions-and-answers-overview_en
- [14] **Adequacy decisions — international dimension of data protection** (the adequacy route that removes the need for Art. 46 tools; contrast). European Commission. https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/adequacy-decisions_en
- [15] **What are standard data protection clauses (the UK IDTA and the Addendum)?** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/appropriate-safeguards/what-are-standard-data-protection-clauses-the-uk-idta-and-the-addendum/
- [16] **Completing a transfer risk assessment (TRA)** (the UK "data protection test"; ICO TRA tool). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/completing-a-transfer-risk-assessment/
- [17] **EU-U.S. Data Privacy Framework — Program Overview / DPF List.** U.S. Department of Commerce. https://www.dataprivacyframework.gov/Program-Overview

## Standards

Not Applicable — the transfer toolbox turns on legal instruments (SCCs, BCRs, TIAs) rather than a technical standard. Where supplementary measures require security controls (encryption, key management, pseudonymisation), those map to ISO/IEC 27001 and are treated in `anonymisation-techniques` and `privacy-engineering-foundations`.

## Academic Sources

Not Applicable — this implementation-focused deep-dive relies on primary legislation, the Schrems II judgment, and EDPB/Commission/ICO guidance. Analytical questions (e.g., the efficacy of encryption as a supplementary measure) may cite peer-reviewed literature in future revisions.

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Commission — standard-clauses implementing texts and annex templates (for drafting the SCC annexes in practice). https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en
- IAPP — practitioner analysis of SCC module selection, BCR approvals and the Art. 3(2) SCC initiative. https://iapp.org/

# Related Documents

- `gdpr-transfers` — **parent/sibling**; the EU Chapter V overview (adequacy, DPF, derogations) that this toolbox sits beneath (**prerequisite reading**).
- `uk-transfers` — **UK-side sibling**; the IDTA/Addendum and the "data protection test" in full.
- `gdpr-foundations` — EU GDPR baseline (controller/processor distinction, Art. 3 scope).
- `cloud-shared-responsibility` — how transfer paperwork is split between cloud provider and customer.
- `anonymisation-techniques` — pseudonymisation/encryption as supplementary measures.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-12 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Arts. 46–47; Decision (EU) 2021/914; Decision (EU) 2023/1795; Charter; Schrems II; Latombe appeal C-703/25 P), EDPB Recommendations 01/2020, 02/2020 and 1/2022 (BCR-C), the European Commission SCC/BCR pages and Q&A, the Art. 3(2) SCC consultation initiative, and the ICO IDTA/Addendum and TRA guidance. **Live-verified 2026-07-12:** the additional SCC module for Art. 3(2) importers remains unadopted (consultation stage). All external links checked live on 2026-07-12. | — |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster D, residual list); full-repo validator/link/lint suite green; frozen in release 0.18.0. | Orchestrator (QA-verified) |
