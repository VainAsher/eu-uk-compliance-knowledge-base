---
id: gdpr-dsar
title: "GDPR: Data-Subject Rights & Access Requests"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: GDPR (EU)
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [gdpr-foundations, uk-gdpr-foundations, duaa-2025-detail, gdpr-transfers, privacy-engineering-foundations]
tags: [gdpr, data-subject-rights, dsar, sar, right-of-access, article-15, erasure, right-to-be-forgotten, objection, automated-decision-making, duaa-2025]
legal_basis: Regulation (EU) 2016/679 (Arts. 12–23); Data Protection Act 2018; Data (Use and Access) Act 2025 (c.18)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | gdpr-dsar |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.14.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It covers **two regimes in parallel** — the EU GDPR and the UK GDPR — which have **diverged** on subject access since the **Data (Use and Access) Act 2025 (c.18)** commenced its data-protection provisions on **5 February 2026**. Where the UK position now differs (reasonable-and-proportionate searches; "stop-the-clock"; the legal-professional-privilege exemption), the divergence is flagged inline. Confirm the in-force status of any specific UK provision before relying on it [3][4][5][7].

# Executive Summary

Chapter III of the GDPR (Articles 12–23) confers the **data-subject rights** and sets the **modalities** by which controllers must honour them: transparency (Art. 12), the information duties (Arts. 13–14), the **right of access / DSAR** (Art. 15), rectification (Art. 16), **erasure / the "right to be forgotten"** (Art. 17), restriction (Art. 18), notification (Art. 19), **portability** (Art. 20), **objection** (Art. 21) and rights around **solely automated decisions and profiling** (Art. 22) [1]. This document details the Chapter III material introduced at foundation level in `gdpr-foundations` and adds a practical DSAR-handling workflow.

The **right of access** dominates operational compliance. On a valid request a controller must confirm whether it processes the individual's data and, if so, provide a **copy** of that data plus prescribed information (purposes, categories, recipients, retention, source, the existence of other rights, and whether solely automated decision-making occurs) — normally **within one month**, extendable by **two further months** for complex or numerous requests, and generally **free of charge** [1][18]. The Court of Justice has read the right broadly: the identity of **specific recipients** must be disclosed on request (C-154/21) [11]; "copy" means a **faithful reproduction** that may require document extracts (C-487/21) [12]; and a first copy of medical records is **free**, the requester's **motive irrelevant** (C-307/22) [13].

The **UK regime has diverged**. The **DUAA 2025** amended UK GDPR Article 15 to confirm controllers need only conduct a **"reasonable and proportionate" search** (new Art. 15(1A), s.78) [5], and amended Article 12 to insert **Article 12A** — a **"stop-the-clock"** rule under which the response period does not run while the controller awaits **identity confirmation, a fee, or reasonably-required clarification** (s.76) [4]. These provisions commenced on **5 February 2026** (SI 2026/82) [7]. The intended audience is DPOs, legal, privacy-engineering and support teams who operate rights processes across the EU and the UK. Three conclusions dominate: rights are **modality-bound** (how you respond is itself an obligation); the right of access is **broad but bounded** by others' rights and by the UK's new proportionality test; and **automated decision-making** (Art. 22) is now the sharpest EU–UK fault line (contrast `duaa-2025-detail`).

# Key Takeaways

- Chapter III rights must be facilitated **transparently and without undue delay**; Art. 12 sets the modalities (concise, intelligible, plain language; normally free; normally one month) that apply to **all** the rights [1][18]. *(Legal obligation.)*
- The **right of access (Art. 15)** requires confirmation of processing, a **copy** of the personal data, and eight categories of supplementary information; the copy of the first request is **free** and due **within one month** (extendable by two months) [1][18]. *(Legal obligation.)*
- A controller may refuse or charge for requests that are **manifestly unfounded or excessive**, and **bears the burden** of demonstrating that character (Art. 12(5)) [1][18]. *(Legal obligation.)*
- The CJEU construes access broadly: **specific recipients** must be named on request (C-154/21) [11]; **"copy"** can require reproductions of documents (C-487/21) [12]; a first medical-records copy is **free** and the **motive is irrelevant** (C-307/22) [13]. *(Case law.)*
- **Erasure (Art. 17)** — the "right to be forgotten" — is **not absolute**; it applies on defined grounds and is subject to exceptions (freedom of expression, legal obligation, public-interest, legal claims). Its origin is **Google Spain (C-131/12)**; de-referencing is generally **EU-wide, not global** (C-507/17) [8][16]. *(Legal obligation / case law.)*
- The **objection right (Art. 21)** to direct marketing is **absolute** — once exercised, the controller must stop; for other processing the controller may continue only on **compelling legitimate grounds** [1]. *(Legal obligation.)*
- **Solely automated decisions with legal or similarly significant effect (Art. 22)** are prohibited unless an exception applies, with safeguards; automated **credit scoring** can itself be a "decision" (C-634/21 SCHUFA) [14]. *(Legal obligation / case law.)*
- **UK divergence (DUAA 2025, in force 5 Feb 2026):** searches need only be **reasonable and proportionate** (Art. 15(1A), s.78) [5][7]; the clock **stops** pending identity/fee/clarification (Art. 12A, s.76) [4][7]; and a new **legal-professional-privilege exemption** (s.79) applies [6]. *(Legal obligation — UK; live-verified.)*

# Purpose

This document is the DSAR / data-subject-rights sub-topic deep-dive. It supports:

- **Legal research** — a mapped index of Chapter III rights, anchor CJEU case law, and the corresponding UK modifications.
- **Compliance implementation** — a repeatable DSAR-handling workflow, exemption analysis, and a checklist teams can operate under both regimes.
- **Developer / support enablement** — plain-language framing of what "confirm, copy, inform" means and how identity verification, third-party redaction and the one-month clock work in practice.

It **details** `gdpr-foundations` (which introduces Arts. 12–23 at overview level) and cross-references `duaa-2025-detail` for the full UK reform picture (recognised legitimate interests, Arts. 22A–22D, PECR). It does **not** restate the GDPR's scope, principles or lawful bases (see `gdpr-foundations`), nor the UK's constitutional/adequacy position (see `uk-gdpr-foundations`).

# Scope

**In scope:** Chapter III of the GDPR — transparency and modalities (Art. 12); the information duties (Arts. 13–14); the right of access / DSAR (Art. 15), including the deadline, the two-month extension, manifestly-unfounded/excessive requests, identity verification, third-party data and exemptions; rectification (Art. 16); erasure (Art. 17); restriction (Art. 18); notification (Art. 19); portability (Art. 20); objection (Art. 21) including direct marketing; automated individual decision-making and profiling (Art. 22); restrictions (Art. 23); the corresponding **UK GDPR / DUAA 2025** modifications; and a practical DSAR workflow and checklist.

**Out of scope (cross-referenced):** The GDPR's principles and lawful bases → `gdpr-foundations`; the full UK reform (recognised legitimate interests, Arts. 22A–22D detail, complaints duty, PECR) → `duaa-2025-detail` and `uk-gdpr-foundations`; international transfers (Chapter V) → `gdpr-transfers` / `uk-transfers`; DPIAs (Art. 35) → `dpia-methodology`. **DPA 2018 exemptions** (Schedules 2–4) are summarised, not exhaustively reproduced. Law-enforcement/intelligence-services access rights (DPA 2018 Parts 3–4) are noted only where the DUAA touched them.

**Assumptions:** The reader has read `gdpr-foundations` and, for UK-specific points, `uk-gdpr-foundations` / `duaa-2025-detail`. Article references are to the consolidated EU GDPR unless the text says "UK GDPR" [1]. UK provisions reflect the position on the `sources_verified` date, after DUAA commencement on 5 February 2026 [7].

# Definitions

*Shared terms (personal data, controller, processor, consent, special-category data) are in `GLOSSARY.md` and carry over. Only terms specific to this document are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Data-subject access request (DSAR / SAR) | A request by which a data subject exercises the Art. 15 right of access to obtain confirmation of processing, a copy of their personal data, and prescribed information. | [1][18] |
| Right to be forgotten | Shorthand for the right to erasure (Art. 17), originating in the CJEU's de-referencing case law (Google Spain). | [1][8] |
| Manifestly unfounded or excessive | The Art. 12(5) threshold at which a controller may charge a reasonable fee or refuse to act; the controller bears the burden of proof. | [1][18] |
| Solely automated decision | A decision based solely on automated processing (no meaningful human involvement) producing legal or similarly significant effects (Art. 22(1)). | [1][14] |
| Reasonable and proportionate search | The **UK-only** standard (UK GDPR Art. 15(1A), inserted by DUAA s.78) confining the access duty to what a proportionate search yields. | [5] |
| Stop-the-clock | The **UK-only** rule (UK GDPR Art. 12A, inserted by DUAA s.76) under which the response period does not run while the controller awaits identity confirmation, a fee, or reasonably-required clarification. | [4] |

# Background

Rights of access, rectification and objection existed under **Directive 95/46/EC**, but the GDPR strengthened and expanded them: it added the rights to **erasure** (codifying Google Spain), **restriction**, **portability**, and reinforced rules on **automated decision-making**, while imposing hard **modalities** — deadlines, plain-language transparency, and (as a default) no charge [1]. The animating idea is **control**: individuals should be able to see, correct, move, limit and stop processing of their data, and to understand automated decisions taken about them.

Because much of this built on the Directive, foundational case law (Google Spain; YS and Others; Nowak, C-434/16 — confirming exam scripts and examiner comments are personal data accessible under the right) decided under the old regime remains authoritative for the equivalent GDPR concepts [8][9][10]. Since 2018 the CJEU has issued a steady line of access judgments (C-154/21, C-487/21, C-307/22, C-634/21) that flesh out what "copy", "recipients", "free" and "decision" mean in practice [11][12][13][14].

The **UK** retained Chapter III on withdrawal from the EU (as the "UK GDPR", read with the DPA 2018), then began to edit it. The **DUAA 2025** made the first substantive changes to subject access — codifying the ICO's long-standing "reasonable and proportionate search" position and adding a statutory "stop-the-clock" — most of which commenced on **5 February 2026** [3][5][7]. This is the principal EU–UK divergence for day-to-day rights handling.

# Legal Framework

Chapter III is structured in five sections: **general modalities** (Art. 12), **information to be provided** (Arts. 13–14), **access, rectification and erasure** (Arts. 15–17 plus restriction 18, notification 19, portability 20), the **right to object and automated decisions** (Arts. 21–22), and **restrictions** (Art. 23) [1]. Two framing points govern the whole chapter. First, Article 12 is the **operating system** for every right: it fixes how requests are received, verified, timed, priced and answered. Second, most rights are **conditional** — they bite only in defined circumstances and yield to defined exceptions; only the objection to **direct marketing** (Art. 21(3)) is effectively absolute [1].

Distinguish throughout: **OBLIGATION** (what the law requires), **REGULATORY INTERPRETATION** (EDPB/ICO reading), **BEST PRACTICE** (standards/consensus), and **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

## Relevant Articles

*"Article" is the EU GDPR article unless marked "UK GDPR". UK modifications made by the DUAA 2025 are listed in the final rows.*

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 12(1)–(2) | Transparency & facilitation — information and communications must be concise, transparent, intelligible, in plain language; controllers must **facilitate** the exercise of rights. | [1] |
| Art. 12(3) | Respond **without undue delay** and **within one month**; extendable by **two further months** for complex/numerous requests (notify within the first month). | [1] |
| Art. 12(4) | If not acting, inform the data subject without delay and at latest within one month, with reasons and the right to complain / seek a remedy. | [1] |
| Art. 12(5) | Requests are normally **free**; where **manifestly unfounded or excessive**, the controller may charge a reasonable fee or refuse — and **bears the burden** of proving that character. | [1] |
| Art. 12(6) | Where there are reasonable doubts about identity, the controller may request additional information to confirm it. | [1] |
| Arts. 13–14 | Information duties — what must be told to data subjects when data is collected from them (13) or obtained otherwise (14), including purposes, lawful basis, recipients, retention and rights. | [1] |
| Art. 15(1)–(2) | **Right of access** — confirmation of processing; access to the data; and information on purposes, categories, recipients, retention, rights, source, and automated decision-making (incl. meaningful information about the logic, significance and consequences). | [1] |
| Art. 15(3) | Provide a **copy** of the personal data undergoing processing; further copies may attract a reasonable fee. | [1] |
| Art. 15(4) | The right to obtain a copy must **not adversely affect the rights and freedoms of others** (basis for third-party redaction). | [1] |
| Art. 16 | **Rectification** — correct inaccurate data and complete incomplete data without undue delay. | [1] |
| Art. 17 | **Erasure / right to be forgotten** — erase on defined grounds, subject to exceptions; if data was made public, take reasonable steps to inform other controllers. | [1] |
| Art. 18 | **Restriction of processing** — a "freeze" in defined situations (e.g. accuracy contested, processing unlawful, pending an objection). | [1] |
| Art. 19 | **Notification obligation** — communicate rectification/erasure/restriction to each recipient, unless impossible/disproportionate. | [1] |
| Art. 20 | **Data portability** — receive data provided to a controller in a structured, commonly used, machine-readable format and transmit it, where processing is by consent/contract **and** carried out by automated means. | [1] |
| Art. 21 | **Right to object** — object to processing based on public-task/legitimate-interests (controller must stop unless compelling legitimate grounds); the objection to **direct marketing (21(2)–(3))** is absolute. | [1] |
| Art. 22 | **Automated individual decision-making** — right not to be subject to a **solely** automated decision with legal/similarly significant effects, save exceptions (contract, law, explicit consent) with safeguards; special-category limits. | [1][14] |
| Art. 23 | **Restrictions** — Union/Member State law may restrict these rights for defined objectives (national security, crime prevention, etc.), subject to safeguards. | [1] |
| UK GDPR Art. 12A (DUAA s.76) | **UK — "stop-the-clock":** the "applicable time period" runs from the latest of request receipt, receipt of identity confirmation / requested information, or fee payment; time awaiting **reasonably-required clarification** does not count. | [3][4] |
| UK GDPR Art. 15(1A) (DUAA s.78) | **UK — reasonable-and-proportionate search:** the data subject is entitled only to what the controller can provide **based on a reasonable and proportionate search**. | [3][5] |
| DPA 2018 s.45A (DUAA s.79) | **UK — legal-professional-privilege exemption** from the access right, with a duty (subject to the privilege) to notify the data subject of reliance and their rights. | [3][6] |

## Relevant Recitals

*Recitals are interpretive aids, not binding operative provisions [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 59 | Modalities should facilitate the exercise of rights, including means for requests to be made electronically and free of charge. | [1] |
| Recital 63 | The access right lets a data subject be aware of, and verify, the lawfulness of processing; where a controller processes a **large quantity** of information, it may ask the subject to **specify** the request. | [1] |
| Recital 64 | Controllers should use all reasonable measures to **verify identity**, especially for online services. | [1] |
| Recital 65 | Basis of the right to erasure / right to be forgotten, and its limits where processing is necessary (e.g. freedom of expression, legal obligations, public interest). | [1] |
| Recital 66 | In the online environment, a controller that made data public should inform other controllers processing it of an erasure request. | [1] |
| Recital 68 | Basis of the portability right; it should not adversely affect the rights of others. | [1] |
| Recital 69–70 | Basis of the objection right; direct-marketing objection should be brought explicitly to the data subject's attention and offered free of charge. | [1] |
| Recital 71 | Automated decision-making/profiling should carry safeguards — the right to human intervention, to express a view, and to contest the decision. | [1] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Google Spain SL v AEPD & Costeja González | CJEU (Grand Chamber), C-131/12, ECLI:EU:C:2014:317 | Search-engine indexing is "processing"; individuals may require de-listing of results — the "right to be forgotten". | Origin of Art. 17 erasure/de-referencing [8]. |
| YS and Others | CJEU, C-141/12 & C-372/12, ECLI:EU:C:2014:2081 | The access right covers personal data in a legal analysis but **not the legal analysis itself**. | Bounds the scope of "personal data" disclosable under Art. 15 [10]. |
| Österreichische Post (RW) | CJEU (Third Chamber), C-154/21, ECLI:EU:C:2023:3 | Under Art. 15(1)(c) the data subject may require the **actual identity of recipients**, not merely categories, unless identifying them is impossible or the request is manifestly unfounded/excessive. | Sets the default: name recipients on request [11]. |
| Österreichische Datenschutzbehörde & CRIF | CJEU (First Chamber), C-487/21, ECLI:EU:C:2023:369 | "Copy" means a **faithful and intelligible reproduction**; providing extracts of documents (or whole documents) is required where indispensable to enable effective exercise of rights. | Defines the "copy" deliverable under Art. 15(3) [12]. |
| FT v DW (medical records) | CJEU (First Chamber), C-307/22, ECLI:EU:C:2023:811 | A patient is entitled to a **first copy of medical records free of charge**; the **motive** for the request is irrelevant. | Confirms "free first copy" and motive-neutrality [13]. |
| SCHUFA Holding (automated credit scoring) | CJEU (First Chamber), C-634/21, ECLI:EU:C:2023:957 | Automated establishment of a **credit score** that third parties draw strongly upon is itself a "decision" within Art. 22(1). | Extends Art. 22 to upstream scoring [14]. |
| GC and Others v CNIL | CJEU (Grand Chamber), C-136/17, ECLI:EU:C:2019:773 | De-referencing of **special-category** data requires balancing rights; a stricter test applies. | Refines erasure/de-referencing for sensitive data [15]. |
| Google LLC v CNIL | CJEU (Grand Chamber), C-507/17, ECLI:EU:C:2019:772 | A de-referencing order generally applies **EU-wide, not globally**. | Territorial limit of the right to be forgotten [16]. |
| TU and RE v Google | CJEU (Fourth Chamber), C-460/20, ECLI:EU:C:2022:962 | A search engine must de-reference where the requester shows the indexed content is **manifestly inaccurate**. | Practical trigger for de-listing [17]. |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).** The authoritative readings are the **EDPB Guidelines 01/2022 on the right of access** (adopted final in 2023) and, in the UK, the **ICO** right-of-access and DUAA guidance; the ICO's **individual-rights hub** gives per-right operational guidance across all of Chapter III [18][19][21][23].

- **Facilitation is the default posture.** The EDPB stresses that controllers should make rights **easy to exercise**, apply a **generous** reading of ambiguous requests, and not use identity checks or clarification as friction; a request need not mention "Article 15" or use any form [18]. *(Regulatory interpretation.)*
- **"Manifestly unfounded or excessive" is a high bar.** The EDPB and ICO treat refusal/charging as **exceptional**, assessed case-by-case, with the **controller bearing the burden**; a request is not excessive merely because it is broad or the data voluminous [18][19]. *(Regulatory interpretation of a legal obligation.)*
- **Clarification does not reset the clock (EU).** Under the EU GDPR, seeking clarification does **not** automatically pause the one-month period; the EDPB permits narrowing only where the controller genuinely processes a large quantity of data and asks the subject to specify (Recital 63), and even then time generally continues to run [1][18]. *(Regulatory interpretation — contrast the UK "stop-the-clock" below.)*
- **UK — "reasonable and proportionate" and "stop-the-clock".** The ICO has **updated its right-of-access guidance** to reflect the DUAA: controllers must make a **reasonable and proportionate** search (not an exhaustive one), and may **pause the response period** where they reasonably require identity confirmation, a fee, or clarification of scope — informing the requester promptly [19][21]. GOV.UK frames these as **codifying existing ICO practice** rather than lowering the substance of the right [22]. *(Regulatory interpretation of a UK legal obligation.)*
- **Automated decisions must be explained.** For Art. 22, the EDPB expects **meaningful information about the logic** and real safeguards (human review, the ability to contest); SCHUFA confirms scoring can trigger these duties upstream [14][18]. The **UK diverges** here — DUAA Arts. 22A–22D move to a permission-plus-safeguards model (see `duaa-2025-detail`) [21]. *(Regulatory interpretation; divergence.)*

# Technical Considerations

- **Data discovery / retrieval.** Honouring Art. 15 requires the ability to **locate all personal data** about an individual across production stores, backups, logs, email, ticketing and third-party processors. A **data map / RoPA** and identity-to-record linking are prerequisites; without them, one-month compliance is unrealistic. *(Best practice grounded in obligation.)*
- **Identity verification.** Build proportionate identity checks (Art. 12(6)/Recital 64) — stronger for sensitive datasets, lighter for low-risk — avoiding **over-collection** of new identity data purely to answer a request. In the **UK**, the response clock does not start until identity is confirmed (Art. 12A) [4]. *(Legal obligation.)*
- **Third-party redaction (Art. 15(4)).** Access must not adversely affect others' rights; implement **redaction/pseudonymisation** of third-party personal data in exported material, with a documented balancing decision rather than blanket withholding [1][18]. *(Legal obligation / best practice.)*
- **Copy production (C-487/21).** The deliverable is a **faithful, intelligible reproduction** — often structured exports plus, where necessary, extracts or whole documents; plain data dumps that the subject cannot understand may not satisfy the right [12]. *(Legal obligation.)*
- **Portability tooling (Art. 20).** Provide **structured, machine-readable** exports (e.g. JSON/CSV) for consent-/contract-based, automated processing; where feasible, support **direct controller-to-controller** transmission [1][20]. *(Legal obligation / best practice.)*
- **Rectification, erasure & restriction propagation (Arts. 16–19).** Changes must **cascade** to backups, replicas, caches, search indexes and downstream processors; implement suppression lists for erasure/objection so data is not re-ingested. Art. 19 notification to recipients should be automatable. *(Best practice grounded in obligation.)*
- **UK proportionality (Art. 15(1A)).** Record what a **reasonable and proportionate** search covered and why certain systems were out of scope — the burden to justify proportionality still sits with the controller [5][19]. *(Legal obligation — UK.)*

# Hosting Considerations

- **Processor assistance (Art. 28(3)(e)).** Hosting providers and SaaS processors must, by contract, **assist** the controller in responding to rights requests. Confirm the DPA obliges the processor to surface, export and delete personal data on instruction, within timeframes that let the controller meet the one-month deadline. *(Legal obligation.)*
- **Backups and immutability.** Erasure/rectification interacts awkwardly with immutable/WORM backups and long-retention object storage; document a **backup-cycle erasure policy** (suppress on restore; delete on next cycle) as the ICO/EDPB accept where immediate backup deletion is not feasible. *(Best practice.)*
- **Data location for retrieval.** Multi-region hosting and sharding complicate "find all data about X"; maintain an index of **where** a subject's data resides. Cross-border storage also engages Chapter V (see `gdpr-transfers`). *(Best practice.)*
- **Log and telemetry stores.** Access and erasure requests reach into logs, analytics and security telemetry that often hold identifiers (IP, device, account IDs); scope these into DSAR tooling and retention/erasure workflows. *(Legal obligation / best practice.)*

# Game Hosting Considerations

- **Player DSARs at scale.** Games generate high-volume, cross-service player data (accounts, telemetry, chat, purchases, anti-cheat, matchmaking). Build **self-service export/deletion** where possible; the UK **reasonable-and-proportionate** standard helps bound searches across sprawling telemetry, but the search rationale must be documented [5][19]. *(Legal obligation / best practice.)*
- **Children's requests.** Requests may come from or concern **children**; verify who is entitled to exercise the right (child vs. parent), apply age-appropriate, plain-language communication (Art. 12), and take special care over third-party data in shared social/chat features [1]. *(Legal obligation.)*
- **Objection to marketing / profiling.** In-game and cross-game **direct marketing** attracts the absolute objection right (Art. 21(3)); personalisation/ad profiling engages Art. 21(1) and, where consequential, Art. 22 [1]. *(Legal obligation.)*
- **Automated bans / moderation.** Solely automated **account bans, restrictions or matchmaking penalties** with significant effect can engage Art. 22 (EU) — provide human review and a contest route; note the **UK's** Arts. 22A–22D shift the analysis (see `duaa-2025-detail`) [14][21]. *(Legal obligation.)*

# AI Considerations

- **Access to profiling and ADM logic (Art. 15(1)(h)).** Where AI/ML makes solely automated significant decisions, the access right includes **meaningful information about the logic involved** and the significance/consequences — a live explainability requirement for model-driven decisions [1][18]. *(Legal obligation.)*
- **Scoring as a "decision" (SCHUFA, C-634/21).** An AI-generated **score** that others rely on can itself be an Art. 22 "decision", pulling upstream models into the safeguards regime [14]. *(Case law / legal obligation.)*
- **Training data and erasure.** Erasure/objection requests interact with models **trained on** personal data; suppression at the data layer is straightforward, but removing influence from trained weights is not — treat retraining/unlearning as an open risk and minimise personal data in training sets. *(Best practice / editorial recommendation.)*
- **Access requests against AI systems.** DSARs may seek inputs, outputs, inferences and derived data; **inferred data** about an identifiable person is personal data and in scope, subject to third-party-rights and trade-secret balancing [1][12]. *(Legal obligation.)*
- **EU–UK ADM divergence.** The EU Art. 22 prohibition-plus-exceptions model contrasts with the UK **Arts. 22A–22D** permission-plus-safeguards model — AI decisions about UK vs. EU subjects may need **different controls** (detailed in `duaa-2025-detail`) [21]. *(Editorial note / divergence.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**. A practical **DSAR workflow** follows.

1. **Recognise and log the request.** Any channel counts (email, phone, in-app, verbally); a request need not cite Article 15. Record receipt date and route it to the rights process. *(OBLIGATION.)* [1][18]
2. **Verify identity (proportionately).** Confirm the requester's identity using data you already hold where possible; escalate checks only for sensitive datasets (Art. 12(6)/Recital 64). **UK:** the clock does not start until identity is confirmed (Art. 12A). *(OBLIGATION.)* [1][4]
3. **Clarify scope where genuinely needed.** For large data volumes, you may ask the subject to specify (Recital 63). **EU:** time generally keeps running. **UK:** the clock **stops** while awaiting reasonably-required clarification (Art. 12A). *(OBLIGATION / interpretation.)* [1][4][19]
4. **Start (or re-start) the clock.** Respond **without undue delay** and within **one month**; extend by **two months** for complex/numerous requests, notifying within the first month with reasons (Art. 12(3)). *(OBLIGATION.)* [1]
5. **Search — proportionately.** Search the systems where the subject's data is reasonably likely to be. **UK:** the duty is expressly a **reasonable and proportionate** search (Art. 15(1A)); document scope and exclusions. *(OBLIGATION.)* [5][19]
6. **Assess exemptions.** Apply relevant DPA 2018 exemptions (e.g. crime, legal privilege, management forecasting, negotiations); **UK:** the DUAA added a **legal-professional-privilege** exemption (DPA 2018 s.45A, s.79). Record the basis for each withheld item. *(OBLIGATION.)* [2][6]
7. **Redact third-party data (Art. 15(4)).** Balance others' rights; redact or withhold third-party personal data unless they consent or it is reasonable to disclose. *(OBLIGATION.)* [1][18]
8. **Produce the copy.** Deliver a **faithful, intelligible** copy plus the Art. 15(1)(a)–(h) information; provide securely and, for the first copy, **free of charge** (C-487/21; C-307/22). *(OBLIGATION.)* [1][12][13]
9. **Handle refusal / fee properly.** Only refuse or charge where **manifestly unfounded or excessive**, with reasons and complaint/remedy rights (Art. 12(4)–(5)); keep the evidence. *(OBLIGATION.)* [1][18]
10. **Operate the other rights on the same rails.** Rectification (16), erasure (17), restriction (18), portability (20) and objection (21) share the Art. 12 modalities; **stop processing immediately** on a direct-marketing objection (21(3)). *(OBLIGATION.)* [1]
11. **Run distinct EU vs. UK playbooks.** Because the UK has diverged (searches, stop-the-clock, LPP, ADM), maintain **jurisdiction-aware** procedures rather than one global setting. *(EDITORIAL RECOMMENDATION.)* [4][5][21]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Missing the one-month deadline (poor data discovery) | High | High | Art. 12(3) [1] | Data map/RoPA; case-tracking with SLA; extension used correctly | Medium |
| R2 | Failing to disclose specific recipients on request | Medium | Medium | Art. 15(1)(c); C-154/21 [1][11] | Recipient registers; default to naming recipients | Low |
| R3 | Providing an unintelligible "data dump" that is not a proper copy | Medium | Medium | Art. 15(3); C-487/21 [1][12] | Structured, human-readable exports; document extracts where needed | Low |
| R4 | Over-withholding or under-redacting third-party data | Medium | High | Art. 15(4) [1] | Documented balancing; redaction tooling; QA review | Low |
| R5 | Wrongly refusing/charging as "manifestly unfounded or excessive" | Medium | High | Art. 12(5) [1][18] | Case-by-case test; evidence pack; senior sign-off | Low |
| R6 | Ignoring a direct-marketing objection | Medium | High | Art. 21(3) [1] | Immediate suppression lists; objection honoured across systems | Low |
| R7 | Non-compliant solely automated decisions without safeguards | Medium | High | Art. 22; C-634/21 [1][14] | Human review + contest route; Art. 22 mapping; ADM inventory | Medium |
| R8 | Erasure/objection not propagated to backups/processors | Medium | Medium | Arts. 17–19, 28 [1] | Suppression on restore; processor assistance clauses; Art. 19 notifications | Medium |
| R9 | Applying EU rules to UK requests (or vice-versa) after DUAA | Medium | Medium | Arts. 12A/15(1A); s.79 [4][5][6] | Jurisdiction-aware playbooks; updated templates; staff training | Low |

# Implementation Roadmap

- **Phase 0 — Discovery:** Map where personal data lives (systems, backups, logs, processors); build identity-to-record linking; inventory automated decisions (Art. 22). *Effort:* Medium.
- **Phase 1 — Rights process & SLAs:** Stand up a single intake for all Chapter III rights with case-tracking, one-month SLA, identity-verification and clarification steps (EU and UK variants). *Effort:* Medium.
- **Phase 2 — Access tooling:** Build search/export, third-party redaction and intelligible-copy production; templates for the Art. 15(1) information and for refusals/extensions. *Effort:* Medium–High.
- **Phase 3 — Other rights & propagation:** Implement rectification, erasure, restriction, portability and objection with cascade to backups/processors and Art. 19 notifications; direct-marketing suppression. *Effort:* Medium.
- **Phase 4 — UK divergence & ADM:** Add reasonable-and-proportionate search logging, Art. 12A stop-the-clock, the s.79 LPP exemption, and jurisdiction-aware ADM controls. *Effort:* Medium.
- **Phase 5 — Assurance:** Metrics (timeliness, volumes, refusal rates), periodic audit, staff training, and guidance-watch for ICO/EDPB updates. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Ad hoc; DSARs handled manually and often late; no data map. | Missed deadlines; no logging. |
| 2 | Managed | A documented process exists; identity/clarification steps inconsistent. | Basic case log; partial data map. |
| 3 | Defined | Single intake for all rights; templates; redaction; one-month SLA tracked; EU/UK variants. | Complete workflow; RoPA-linked search. |
| 4 | Quantitatively Managed | Metrics on timeliness, volumes, refusal rates; processor-assistance tested; ADM inventory maintained. | KPIs; audit trail; SLA dashboards. |
| 5 | Optimising | Self-service export/erasure; automated propagation and suppression; jurisdiction-aware, continuously improved. | Automation; low residual risk; independent assurance. |

# Audit Questions

1. Can you evidence, for a sample of DSARs, that each was answered **within one month** (or validly extended) from the correct start date? *(Art. 12(3); UK Art. 12A [1][4].)*
2. How do you **verify identity** proportionately, and (UK) how do you record that the clock started only on confirmation? *(Art. 12(6); Art. 12A [1][4].)*
3. When you seek **clarification**, on what basis, and (UK) how do you evidence the stop-the-clock pause? *(Recital 63; Art. 12A [1][4].)*
4. How do you decide what is a **reasonable and proportionate** search (UK) or a complete search (EU), and how is scope documented? *(Art. 15(1A); [5][19].)*
5. How do you disclose **specific recipients** and produce an **intelligible copy**? *(Art. 15(1)(c),(3); C-154/21; C-487/21 [11][12].)*
6. How do you balance and **redact third-party data**? *(Art. 15(4) [1].)*
7. On what evidence do you treat a request as **manifestly unfounded or excessive**? *(Art. 12(5) [1][18].)*
8. How are **erasure/objection** decisions propagated to backups and processors, and how do you honour **direct-marketing objections** immediately? *(Arts. 17–19, 21(3), 28 [1].)*
9. How do you identify **solely automated significant decisions**, and what safeguards (human review, contest) apply — distinguishing EU (Art. 22) from UK (Arts. 22A–22D)? *(Art. 22; C-634/21; [14][21].)*

# Implementation Checklist

- [ ] Data map / RoPA supports "find all data about an individual" across systems, backups, logs and processors.
- [ ] Single, multi-channel intake logs every Chapter III request with a receipt date.
- [ ] Proportionate identity-verification step (UK: clock starts on confirmation, Art. 12A).
- [ ] Clarification step defined (EU: time runs; UK: stop-the-clock recorded).
- [ ] One-month SLA tracked; two-month extension process with reasons and first-month notice.
- [ ] Reasonable-and-proportionate search scope documented (UK Art. 15(1A)); complete search evidenced (EU).
- [ ] DPA 2018 exemption analysis, including the DUAA legal-professional-privilege exemption (s.79), recorded per withheld item.
- [ ] Third-party redaction with documented balancing (Art. 15(4)).
- [ ] Intelligible copy plus Art. 15(1)(a)–(h) information delivered securely; first copy free.
- [ ] Rectification, erasure, restriction, portability and objection implemented with cascade to backups/processors and Art. 19 notifications.
- [ ] Direct-marketing objections honoured immediately via suppression lists (Art. 21(3)).
- [ ] Automated-decision inventory with human-review/contest safeguards; separate EU and UK ADM controls.

# References

*All links verified live on 2026-07-11 (`sources_verified`) with HTTP 200.*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** (Chapter III, Arts. 12–23; Recitals 59–71). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [2] **Data Protection Act 2018 (c.12)**, contents (UK exemptions and law-enforcement/intelligence rights). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/contents
- [3] **Data (Use and Access) Act 2025 (c.18)**, contents (Royal Assent 19 June 2025). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/contents
- [4] **DUAA 2025, s.76** (amends UK GDPR Art. 12 and inserts **Art. 12A** — "applicable time period" / stop-the-clock for identity, fee and clarification). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/section/76/enacted
- [5] **DUAA 2025, s.78** (inserts UK GDPR **Art. 15(1A)** — reasonable-and-proportionate search). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/section/78/enacted
- [6] **DUAA 2025, s.79** (inserts DPA 2018 **s.45A** — legal-professional-privilege exemption from access). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/section/79/enacted
- [7] **The Data (Use and Access) Act 2025 (Commencement No. 6 and Transitional and Saving Provisions) Regulations 2026 (SI 2026/82)** — brings most Part 5 data-protection provisions into force on 5 February 2026. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2026/82/contents/made
- [8] **Google Spain SL v AEPD & Costeja González**, C-131/12, ECLI:EU:C:2014:317. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62012CJ0131
- [9] **Nowak v Data Protection Commissioner**, C-434/16, ECLI:EU:C:2017:994. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62016CJ0434
- [10] **YS and Others**, C-141/12 & C-372/12, ECLI:EU:C:2014:2081. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62012CJ0141
- [11] **Österreichische Post (RW)**, C-154/21, ECLI:EU:C:2023:3. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62021CJ0154
- [12] **Österreichische Datenschutzbehörde & CRIF**, C-487/21, ECLI:EU:C:2023:369. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62021CJ0487
- [13] **FT v DW (medical records)**, C-307/22, ECLI:EU:C:2023:811. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62022CJ0307
- [14] **SCHUFA Holding (automated credit scoring)**, C-634/21, ECLI:EU:C:2023:957. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62021CJ0634
- [15] **GC and Others v CNIL**, C-136/17, ECLI:EU:C:2019:773. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62017CJ0136
- [16] **Google LLC v CNIL**, C-507/17, ECLI:EU:C:2019:772. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62017CJ0507
- [17] **TU and RE v Google (right to be forgotten — inaccurate content)**, C-460/20, ECLI:EU:C:2022:962. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62020CJ0460

## Regulatory Guidance

- [18] **Guidelines 01/2022 on data subject rights — Right of access.** European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-012022-data-subject-rights-right-access_en
- [19] **Right of access** (guide, updated for the DUAA). Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/individual-rights/right-of-access/
- [20] **Guidelines on the right to data portability (WP242 rev.01)**, Article 29 Working Party (EDPB-endorsed). European Commission newsroom. https://ec.europa.eu/newsroom/article29/items/611233
- [21] **The Data (Use and Access) Act 2025 — what does it mean for organisations?** ICO. https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/the-data-use-and-access-act-2025-what-does-it-mean-for-organisations/
- [22] **Data (Use and Access) Act 2025: data protection and privacy changes.** GOV.UK. https://www.gov.uk/guidance/data-use-and-access-act-2025-data-protection-and-privacy-changes
- [23] **Individual rights** (Guide to the UK GDPR — individual rights index). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/individual-rights/

## Standards

**Not Applicable** — data-subject-rights handling is governed by primary legislation and regulator guidance, not by an ISO/IEC/NIST/OWASP standard specific to it. General privacy-management standards (ISO/IEC 27701) support implementation and are covered in `privacy-engineering-foundations`.

## Academic Sources

**Not Applicable** — this operational sub-topic relies on primary legislation, CJEU case law and regulator guidance. Peer-reviewed analysis of DSAR practice and Art. 22 explainability will be cited in dedicated analytical documents as it matures.

# Further Reading

*Non-authoritative; provided for orientation only.*

- ICO — Guide to the UK GDPR (individual rights hub). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/individual-rights/
- EDPB — published guidelines index (rights-related deep dives). https://www.edpb.europa.eu/our-work-tools/general-guidance/guidelines-recommendations-best-practices_en

# Related Documents

- `gdpr-foundations` — GDPR foundations & core principles (**parent; this document details its Arts. 12–23 material**).
- `uk-gdpr-foundations` — UK GDPR foundations & divergence (**UK context for the DUAA modifications**).
- `duaa-2025-detail` — DUAA 2025 detailed analysis (**full UK reform: recognised legitimate interests, Arts. 22A–22D, complaints, PECR**).
- `gdpr-transfers` — International data transfers (Chapter V) — relevant to cross-border retrieval.
- `privacy-engineering-foundations` — implementing rights tooling, redaction and data mapping.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Arts. 12–23; nine CJEU judgments incl. C-154/21, C-487/21, C-307/22, C-634/21), EDPB Guidelines 01/2022, ICO right-of-access/DUAA guidance and GOV.UK. **UK DSAR changes live-verified on legislation.gov.uk: DUAA s.76 → UK GDPR Art. 12A "stop-the-clock" (identity/fee/clarification); s.78 → UK GDPR Art. 15(1A) reasonable-and-proportionate search; s.79 → DPA 2018 s.45A legal-professional-privilege exemption; commenced 5 February 2026 via SI 2026/82.** | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 3 human gate; frozen in release 0.14.0. | Human reviewer |
