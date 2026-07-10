---
id: gdpr-foundations
title: "GDPR: Foundations & Core Principles"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: GDPR (EU)
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-10
updated: 2026-07-10
review_due: 2027-07-10
confidence: High
supersedes: Not Applicable
related: [uk-gdpr-foundations, eprivacy-foundations, privacy-engineering-foundations]
tags: [gdpr, data-protection, privacy, eu-law, article-5, article-6, lawful-basis]
legal_basis: Regulation (EU) 2016/679
sources_verified: 2026-07-10
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | gdpr-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.2.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-10 |
| Last Updated | 2026-07-10 |
| Review Due | 2027-07-10 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-10 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. Organisations should obtain qualified legal counsel for specific circumstances.

# Executive Summary

The General Data Protection Regulation (Regulation (EU) 2016/679, "GDPR") is the European Union's primary data-protection instrument. It entered into force on 24 May 2016 and has applied directly across all Member States since **25 May 2018** [1][2]. As a Regulation it is binding in its entirety and directly applicable without national transposition, although it leaves defined margins for Member State law.

This document establishes the *foundations*: the material and territorial scope of the GDPR, its core definitions (personal data, processing, controller, processor), the seven data-protection principles in Article 5, and the six lawful bases for processing in Article 6 [1]. It also situates these within the accountability model that makes controllers responsible for demonstrating — not merely asserting — compliance [1].

The intended audience is compliance, legal, and engineering teams who need a single authoritative reference before engaging with more specialised topics (data-subject requests, international transfers, DPIAs, AI Act overlap). Three conclusions dominate. First, the GDPR is **principle-based**: obligations flow from Article 5, and every downstream control should trace to a principle. Second, **lawfulness is a gate**: no processing is permitted without a valid Article 6 basis, chosen before processing begins. Third, **accountability is operational**: Article 5(2) converts good intentions into an evidentiary burden the controller must be able to discharge on demand [1].

Foundational case law from the Court of Justice of the EU (Google Spain, Breyer, Nowak, Schrems II) confirms the broad construction of "personal data" and the robustness of data-subject rights, and is summarised in the Legal Framework section [3][4][5][6].

# Key Takeaways

- The GDPR has applied directly in all EU Member States since **25 May 2018**; it comprises 11 chapters, 99 articles and 173 recitals [1][2]. *(Legal obligation.)*
- **Seven principles** govern all processing: lawfulness/fairness/transparency, purpose limitation, data minimisation, accuracy, storage limitation, integrity & confidentiality, and accountability (Art. 5) [1]. *(Legal obligation.)*
- Processing requires at least one of **six lawful bases** (Art. 6(1)(a)–(f)); the basis must be identified before processing and cannot be swapped retrospectively to fix a problem [1]. *(Legal obligation / regulatory interpretation.)*
- "**Personal data**" is construed broadly; a dynamic IP address can be personal data where the controller has legal means to identify the individual (Breyer, C-582/14) [5]. *(Case law.)*
- Even exam scripts and examiner comments can be personal data (Nowak, C-434/16), illustrating the concept's reach [4]. *(Case law.)*
- **Accountability (Art. 5(2))** shifts the burden: controllers must be able to *demonstrate* compliance, not merely comply [1]. *(Legal obligation.)*
- The GDPR distinguishes **controllers** (determine purposes and means) from **processors** (act on the controller's instructions); the distinction drives who bears which obligations [1]. *(Legal obligation.)*
- Non-compliance can attract administrative fines up to **€20 million or 4% of total worldwide annual turnover**, whichever is higher (Art. 83(5)) [1]. *(Legal obligation.)*

# Purpose

This document is the entry point to the GDPR topic area. It supports:

- **Legal research** — a mapped index of the principles, lawful bases and anchor case law.
- **Compliance implementation** — a foundation on which DSAR handling, transfers, DPIA and records documents build.
- **Developer guidance** — plain-language framing of obligations that shape system design (privacy by design, minimisation, security).
- **Onboarding** — a single reference before staff engage specialised material.

It deliberately does *not* cover, in depth: data-subject rights procedures, international transfers (Chapter V), Data Protection Impact Assessments (Art. 35), or records of processing (Art. 30). Those are separate documents in the research backlog (see `PROJECT_STATUS.md`).

# Scope

**In scope:** Material and territorial scope; core definitions; the Article 5 principles; the Article 6 lawful bases; the controller/processor distinction; the accountability model; foundational CJEU case law; high-level enforcement architecture.

**Out of scope:** Special-category data mechanics (Art. 9) beyond definition; detailed rights procedures (Arts. 12–23); international transfers (Chapter V); DPIAs (Art. 35); the UK GDPR divergence (covered in `uk-gdpr-foundations`); sector-specific overlays (ePrivacy, AI Act, DSA).

**Assumptions:** The reader is a compliance, legal or engineering practitioner. Article references are to the consolidated text of Regulation (EU) 2016/679 as published on EUR-Lex [1].

# Definitions

| Term | Definition | Source |
|------|------------|--------|
| Personal data | Any information relating to an identified or identifiable natural person ("data subject"); an identifiable person is one who can be identified, directly or indirectly (Art. 4(1)). | [1] |
| Processing | Any operation performed on personal data — collection, recording, storage, use, disclosure, erasure, etc. (Art. 4(2)). | [1] |
| Controller | The natural/legal person that, alone or jointly, determines the purposes and means of processing (Art. 4(7)). | [1] |
| Processor | A natural/legal person that processes personal data on behalf of the controller (Art. 4(8)). | [1] |
| Consent | Any freely given, specific, informed and unambiguous indication of the data subject's wishes, by a statement or clear affirmative action (Art. 4(11)). | [1] |
| Special category data | Data revealing racial/ethnic origin, political opinions, religious/philosophical beliefs, trade-union membership; genetic, biometric, health, sex-life or sexual-orientation data (Art. 9). | [1] |
| Supervisory authority | An independent public authority established by a Member State to monitor GDPR application (Art. 4(21), Art. 51). | [1] |

# Background

Before the GDPR, EU data protection rested on **Directive 95/46/EC**, transposed unevenly across Member States, producing fragmentation and legal uncertainty for cross-border processing. The GDPR replaced the Directive with a directly applicable Regulation to harmonise rules, strengthen data-subject rights, and modernise the framework for the digital and cross-border economy [2][9].

Because the transition spanned the Directive-to-Regulation shift, much foundational case law (Google Spain, Breyer, Nowak) was decided under Directive 95/46/EC but remains authoritative for interpreting equivalent GDPR concepts, since the definitions were carried forward substantially unchanged [3][4][5]. The GDPR entered into force on 24 May 2016 (twenty days after OJ publication) and became applicable on 25 May 2018, giving organisations a two-year implementation window [1][2].

# Legal Framework

The GDPR is a Regulation of the European Parliament and of the Council. It is **binding in its entirety and directly applicable** in all Member States, though it contains "opening clauses" permitting or requiring national law on specific points (e.g., age of consent for information-society services, employment context). It comprises 11 chapters and 99 articles, preceded by 173 recitals that aid interpretation but are not themselves binding operative provisions [1].

The architecture, at a glance:

- **Chapter I** — General provisions (subject-matter, scope, definitions).
- **Chapter II** — Principles (Arts. 5–11), including lawful bases and conditions for consent and special-category data.
- **Chapter III** — Rights of the data subject (Arts. 12–23).
- **Chapter IV** — Controller and processor obligations (Arts. 24–43), including security, DPIA, and DPOs.
- **Chapter V** — Transfers to third countries (Arts. 44–50).
- **Chapters VI–VII** — Supervisory authorities and cooperation/consistency.
- **Chapter VIII** — Remedies, liability and penalties (Arts. 77–84).
- **Chapters IX–XI** — Specific situations, delegated acts, final provisions.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 2 | Material scope — applies to processing of personal data wholly/partly by automated means and to non-automated processing forming part of a filing system. | [1] |
| Art. 3 | Territorial scope — applies to controllers/processors established in the EU, and to those outside the EU offering goods/services to, or monitoring, data subjects in the EU. | [1] |
| Art. 4 | Definitions (personal data, processing, controller, processor, consent, etc.). | [1] |
| Art. 5(1)(a) | Lawfulness, fairness and transparency. | [1] |
| Art. 5(1)(b) | Purpose limitation. | [1] |
| Art. 5(1)(c) | Data minimisation. | [1] |
| Art. 5(1)(d) | Accuracy. | [1] |
| Art. 5(1)(e) | Storage limitation. | [1] |
| Art. 5(1)(f) | Integrity and confidentiality (security). | [1] |
| Art. 5(2) | Accountability — controller must demonstrate compliance. | [1] |
| Art. 6(1)(a)–(f) | Six lawful bases for processing. | [1] |
| Art. 9 | Prohibition on processing special categories, subject to exceptions. | [1] |
| Art. 24 | Responsibility of the controller — implement appropriate technical and organisational measures. | [1] |
| Art. 25 | Data protection by design and by default. | [1] |
| Art. 28 | Processor obligations and mandatory contract terms. | [1] |
| Art. 32 | Security of processing. | [1] |
| Art. 83 | Administrative fines (up to €20m or 4% of worldwide annual turnover). | [1] |

## Relevant Recitals

*Recitals are interpretive aids, not binding operative provisions [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 1 | Protection of personal data is a fundamental right (Art. 8 Charter). | [1] |
| Recital 26 | Identifiability is assessed by reference to means reasonably likely to be used; anonymous data falls outside the GDPR. | [1] |
| Recital 39 | Elaborates lawfulness, transparency and minimisation. | [1] |
| Recital 47 | Legitimate interests — reasonable expectations of the data subject; direct marketing may constitute a legitimate interest. | [1] |
| Recital 32 | Consent must be by clear affirmative act; pre-ticked boxes or inactivity do not constitute consent. | [1] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Google Spain SL v AEPD & Costeja González | CJEU (Grand Chamber), C-131/12, 13 May 2014, ECLI:EU:C:2014:317 | Search-engine operation is "processing"; operators may be required to de-index results — the "right to be forgotten". | Establishes broad reach of processing and the primacy of data-subject rights (now codified in Art. 17) [3]. |
| Breyer v Bundesrepublik Deutschland | CJEU (Second Chamber), C-582/14, 19 Oct 2016, ECLI:EU:C:2016:779 | A dynamic IP address is personal data for a website operator that has legal means to identify the individual via a third party. | Confirms the broad, relative construction of "personal data" (Recital 26) [5]. |
| Nowak v Data Protection Commissioner | CJEU (Second Chamber), C-434/16, 20 Dec 2017, ECLI:EU:C:2017:994 | Written answers in a professional exam, and examiner comments, are personal data. | Illustrates the expansive scope of "personal data" by content, purpose or effect [4]. |
| Data Protection Commissioner v Facebook Ireland & Schrems ("Schrems II") | CJEU (Grand Chamber), C-311/18, 16 July 2020, ECLI:EU:C:2020:559 | Invalidated the EU-US Privacy Shield; upheld Standard Contractual Clauses subject to case-by-case supplementary measures. | Foundational for transfers (Chapter V); demonstrates enforceability of GDPR safeguards against third-country access [6]. |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).** The European Data Protection Board (EDPB) issues guidelines, recommendations and best practices that, while not binding law, represent the consensus interpretation of EU supervisory authorities and are highly persuasive [8]. National authorities (e.g., the UK ICO for the UK GDPR, Ireland's DPC, France's CNIL) publish complementary guidance [7].

Key interpretive positions relevant to the foundations:

- **Lawful basis must be determined before processing** and documented; the ICO stresses that controllers cannot switch basis retrospectively to remedy a problem, and that consent is not automatically the "best" basis [7]. *(Regulatory interpretation.)*
- **Legitimate interests (Art. 6(1)(f))** requires a three-part test — purpose (identify the interest), necessity (is processing necessary), and balancing (against the data subject's rights) — reflected in Recital 47 and ICO/EDPB guidance [7][8]. *(Regulatory interpretation / best practice.)*
- **Consent** must meet the Art. 4(11) and Art. 7 conditions; the EDPB Guidelines on consent treat bundled consent and non-genuine choice as invalid [8]. *(Regulatory interpretation.)*
- The **accountability principle** is operationalised through records of processing (Art. 30), DPIAs (Art. 35), and demonstrable technical and organisational measures (Arts. 24, 32) [1][7]. *(Regulatory interpretation.)*

# Technical Considerations

The principles translate directly into system-design constraints:

- **Data minimisation (Art. 5(1)(c))** — collect and retain only what the purpose requires; prefer schemas that avoid optional over-collection; avoid "collect now, decide later." *(Best practice grounded in obligation.)*
- **Storage limitation (Art. 5(1)(e))** — implement retention schedules and automated deletion/anonymisation; time-to-live on records; documented retention rationale.
- **Integrity & confidentiality (Art. 5(1)(f), Art. 32)** — encryption in transit and at rest, access control, pseudonymisation, logging, and tested backup/restore. Align with ISO/IEC 27001 controls [10][11].
- **Data protection by design and by default (Art. 25)** — privacy-preserving defaults, minimisation baked into architecture, DPIA triggers in the SDLC.
- **Lawful-basis enforcement** — where consent is the basis, systems must record consent capture, scope and withdrawal, and must honour withdrawal as easily as it was given (Art. 7(3)).
- **Identifiability boundary (Recital 26)** — genuine anonymisation removes data from GDPR scope, but *pseudonymised* data remains personal data; teams frequently conflate the two [1][5].

# Hosting Considerations

- **Controller/processor allocation** — a hosting provider is typically a **processor**; an Art. 28 data-processing agreement with the mandatory terms is required, including sub-processor controls and assistance obligations. *(Legal obligation.)*
- **Location & transfers** — where hosting entails storage or access from outside the EEA, Chapter V transfer mechanisms apply; Schrems II requires assessing third-country government-access risk and supplementary measures [6]. *(Legal obligation / regulatory interpretation.)*
- **Security (Art. 32)** — infrastructure controls (tenant isolation, key management, patching, monitoring) should map to a recognised framework (ISO/IEC 27001, NIST CSF) [10][11].
- **Shared responsibility** — cloud shared-responsibility models must be reconciled with the controller/processor split; the customer usually remains controller and cannot outsource accountability. *(Editorial recommendation: document the responsibility matrix explicitly.)*

# Game Hosting Considerations

- **Children's data** — games frequently attract minors. Art. 8 sets conditions for consent to information-society services offered to children; the applicable age threshold (13–16) is set by Member State law, so multi-territory games face varying thresholds. Age-assurance and parental-consent flows are needed. *(Legal obligation.)*
- **Player identifiers & telemetry** — usernames, device IDs, IP addresses and in-game telemetry are typically personal data (cf. Breyer on IP addresses) [5]; minimisation and retention rules apply to matchmaking, anti-cheat and analytics data.
- **Real-time processing** — voice/chat moderation and anti-cheat may process personal (and sometimes special-category) data; lawful basis and transparency must be established.
- **UGC and third parties** — user-generated content and third-party SDKs (ads, analytics) create controller/processor and joint-controller questions that must be mapped. *(Editorial recommendation.)*

# AI Considerations

- **Training data** — using personal data to train models is "processing" and needs a lawful basis; purpose limitation (Art. 5(1)(b)) constrains reuse of data collected for another purpose. *(Legal obligation.)*
- **Automated decision-making** — Art. 22 gives data subjects rights regarding solely automated decisions producing legal or similarly significant effects; foundational to any AI system making consequential decisions. *(Legal obligation; detailed in a dedicated document.)*
- **Data minimisation vs. model appetite** — the tension between minimisation and data-hungry ML is a recurring compliance friction point; techniques include pseudonymisation, synthetic data and federated approaches. *(Best practice.)*
- **AI Act overlap** — the GDPR operates alongside the EU AI Act (Regulation (EU) 2024/1689); the two are complementary, and this overlap is addressed in the AI Act and AI Governance documents. *(Cross-reference.)*

# Operational Guidance

The following distinguishes **OBLIGATION** (the law requires), **BEST PRACTICE** (standards/regulator consensus), and **EDITORIAL RECOMMENDATION** (this pipeline suggests).

1. **Map your processing** — maintain records of processing activities (Art. 30). *(OBLIGATION for most organisations.)*
2. **Assign each processing activity a lawful basis** before it begins, and document the reasoning; for legitimate interests, complete and retain a Legitimate Interests Assessment. *(OBLIGATION + BEST PRACTICE.)* [7]
3. **Classify data** — flag special-category (Art. 9) and children's data for elevated controls. *(OBLIGATION.)*
4. **Trace every control to a principle** — build a matrix linking technical/organisational measures to Art. 5 principles to evidence accountability. *(EDITORIAL RECOMMENDATION.)*
5. **Operationalise rights** — build repeatable DSAR, erasure and objection workflows (detailed in a dedicated document). *(OBLIGATION.)*
6. **Contract with processors** — ensure Art. 28 terms are in place with every processor and sub-processor. *(OBLIGATION.)*
7. **Assess transfers** — inventory data flows leaving the EEA and apply Chapter V mechanisms with a transfer risk assessment. *(OBLIGATION.)* [6]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Processing without a valid lawful basis | Medium | High | Art. 6; Art. 83 fines [1] | Lawful-basis register; pre-processing sign-off | Low |
| R2 | Relying on invalid consent (bundled/pre-ticked) | Medium | High | Art. 4(11), Art. 7; Recital 32 [1][8] | Granular, affirmative consent UX; withdrawal parity | Low |
| R3 | Over-collection / indefinite retention | High | Medium | Art. 5(1)(c),(e) [1] | Minimisation review; retention schedule + auto-deletion | Medium |
| R4 | Misclassifying pseudonymised data as anonymous | Medium | High | Recital 26; Breyer [1][5] | Identifiability assessment; treat pseudonymised as personal | Low |
| R5 | Inadequate processor contracts | Medium | Medium | Art. 28 [1] | Standard DPA with mandatory clauses; sub-processor register | Low |
| R6 | Non-compliant international transfer | Medium | High | Chapter V; Schrems II [6] | Transfer mapping; SCCs + supplementary measures | Medium |
| R7 | Cannot demonstrate compliance on request | Medium | High | Art. 5(2) [1] | Documentation, ROPA, DPIAs, control-to-principle matrix | Low |

# Implementation Roadmap

- **Phase 0 — Discovery (foundations):** Inventory processing activities and data flows; classify data. *Depends on:* stakeholder access. *Effort:* Medium.
- **Phase 1 — Lawful basis & records:** Assign and document lawful bases; stand up the Art. 30 record. *Effort:* Medium.
- **Phase 2 — Rights & contracts:** Build DSAR/erasure workflows; put Art. 28 DPAs in place. *Effort:* Medium–High.
- **Phase 3 — Security & by-design:** Implement Art. 32 controls mapped to ISO/IEC 27001; embed Art. 25 in the SDLC. *Effort:* High.
- **Phase 4 — Transfers & accountability:** Transfer risk assessments; assemble the accountability evidence pack. *Effort:* Medium.
- **Phase 5 — Continuous improvement:** DPIA cadence, audits, training, metrics. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Ad hoc; no records; lawful bases undocumented. | No ROPA; reactive only. |
| 2 | Managed | Basic records exist; lawful bases assigned inconsistently. | Partial ROPA; some DPAs. |
| 3 | Defined | Documented processes for bases, rights, contracts, retention. | Complete ROPA; DSAR workflow; retention schedule. |
| 4 | Quantitatively Managed | Metrics on DSAR timeliness, incident rates, retention adherence. | KPIs; regular DPIAs; audit trail. |
| 5 | Optimising | Continuous improvement; privacy-by-design embedded; automated controls. | Automated deletion; control-to-principle matrix; independent assurance. |

# Audit Questions

1. Can you produce a record of processing activities (Art. 30) on demand? *(Traces to Art. 5(2), Art. 30.)*
2. For each processing activity, what is the documented lawful basis, and when was it fixed? *(Art. 6.)*
3. Where consent is relied upon, how is capture, scope and withdrawal recorded and honoured? *(Art. 7.)*
4. How is special-category and children's data identified and given elevated protection? *(Arts. 8, 9.)*
5. What retention periods apply, and how is deletion/anonymisation enforced? *(Art. 5(1)(e).)*
6. Are Art. 28 processor contracts in place with all processors and sub-processors? *(Art. 28.)*
7. Which data flows leave the EEA, and what Chapter V mechanism and supplementary measures apply? *(Chapter V; Schrems II [6].)*
8. How do you demonstrate that technical and organisational measures are appropriate (Art. 32)? *(Arts. 24, 32.)*

# Implementation Checklist

- [ ] Records of processing activities (ROPA) established and maintained (Art. 30).
- [ ] Lawful basis assigned and documented for every processing activity (Art. 6).
- [ ] Legitimate Interests Assessments completed where Art. 6(1)(f) is relied on.
- [ ] Consent mechanisms meet Art. 4(11)/Art. 7 (granular, affirmative, withdrawable).
- [ ] Special-category (Art. 9) and children's (Art. 8) data identified and protected.
- [ ] Retention schedule defined with automated deletion/anonymisation (Art. 5(1)(e)).
- [ ] Art. 28 data-processing agreements in place with all processors.
- [ ] International transfers mapped with Chapter V safeguards (Schrems II supplementary measures).
- [ ] Security measures implemented and mapped to a framework (Art. 32; ISO/IEC 27001).
- [ ] Data protection by design and by default embedded in the SDLC (Art. 25).
- [ ] Accountability evidence pack (control-to-principle matrix, DPIAs) assembled (Art. 5(2)).

# References

*All links verified live on 2026-07-10 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text.** EUR-Lex, CELEX 02016R0679-20160504. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504 — and ELI: https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [2] **"The GDPR applies in all Member States from 25 May 2018."** EUR-Lex news / official summary. https://eur-lex.europa.eu/content/news/general-data-protection-regulation-GDPR-applies-from-25-May-2018.html
- [3] **Google Spain SL v AEPD & Costeja González**, C-131/12, ECLI:EU:C:2014:317. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62012CJ0131
- [4] **Nowak v Data Protection Commissioner**, C-434/16, ECLI:EU:C:2017:994. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62016CJ0434
- [5] **Breyer v Bundesrepublik Deutschland**, C-582/14, ECLI:EU:C:2016:779. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62014CJ0582
- [6] **Data Protection Commissioner v Facebook Ireland & Schrems (Schrems II)**, C-311/18, ECLI:EU:C:2020:559. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:62018CJ0311

## Regulatory Guidance

- [7] **Guide to the UK GDPR / data-protection principles.** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/
- [8] **Guidelines, Recommendations & Best Practices.** European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/general-guidance/guidelines-recommendations-best-practices_en
- [9] **Legal framework of EU data protection.** European Commission. https://commission.europa.eu/law/law-topic/data-protection/legal-framework-eu-data-protection_en

## Standards

- [10] **ISO/IEC 27701** — Privacy Information Management System. ISO. https://www.iso.org/standard/71670.html
- [11] **ISO/IEC 27001:2022** — Information Security Management Systems. ISO. https://www.iso.org/standard/27001

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation, case law and regulatory guidance. Academic literature will be cited in analytical sub-topic documents (e.g., legitimate interests balancing, anonymisation techniques).

# Further Reading

*Non-authoritative; provided for orientation only.*

- EDPB — published guidelines index (topic-specific deep dives). https://www.edpb.europa.eu/
- European Commission — "Rules for business and organisations" data-protection portal. https://commission.europa.eu/law/law-topic/data-protection_en

# Related Documents

- `uk-gdpr-foundations` — UK GDPR & DPA 2018 divergence (planned, Tier 1 #2).
- `eprivacy-foundations` — ePrivacy Directive as lex specialis (planned, Tier 1 #3).
- `privacy-engineering-foundations` — implementing Arts. 25/32 in systems (planned, Tier 1 #4).
- `ai-act-foundations` — GDPR/AI Act interplay (planned, Tier 2 #5).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-10 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex, EDPB, ICO, Commission and four CJEU judgments. | — |
| 1.0.0 | 2026-07-10 | Editorial Reviewer (virtual agent) | Approved at human review gate; citation numbering made contiguous; frozen in release 0.2.0. | Human reviewer |
