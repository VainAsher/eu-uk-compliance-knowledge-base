---
id: eprivacy-foundations
title: "ePrivacy: Foundations, Cookies & Electronic Communications"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU, UK]
topic: ePrivacy
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-10
updated: 2026-07-10
review_due: 2027-07-10
confidence: High
supersedes: Not Applicable
related: [gdpr-foundations, uk-gdpr-foundations, privacy-engineering-foundations]
tags: [eprivacy, cookies, consent, direct-marketing, pecr, electronic-communications, lex-specialis]
legal_basis: Directive 2002/58/EC (as amended by Directive 2009/136/EC); PECR 2003 (UK)
sources_verified: 2026-07-10
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | eprivacy-foundations |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-10 |
| Last Updated | 2026-07-10 |
| Review Due | 2027-07-10 |
| Confidence | High |
| Approved By | *pending human review* |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The ePrivacy landscape is in flux: the 2017 ePrivacy Regulation proposal was **withdrawn** in 2025 and cookie rules are proposed to move into the GDPR via the "Digital Omnibus" — confirm the live legal position before relying on future-state provisions.

# Executive Summary

The **ePrivacy Directive (Directive 2002/58/EC**, as amended by Directive 2009/136/EC) governs privacy in the **electronic-communications** sector. It is the **lex specialis** to the GDPR: where it applies, its specific rules take precedence over the GDPR's general rules, while the GDPR fills gaps (for example, on the meaning and conditions of consent) [1][3]. Its best-known requirement is the **"cookie rule"** in Article 5(3): storing or accessing information on a user's device requires the user's **consent**, unless strictly necessary to provide a service the user requested [1].

This document establishes the foundations: confidentiality of communications (Art. 5), the cookie/consent rule (Art. 5(3)), traffic and location data, and unsolicited **direct marketing** (Art. 13). Because ePrivacy is a **Directive**, it is transposed into national law — in the UK by the **Privacy and Electronic Communications (EC Directive) Regulations 2003 ("PECR")** [7]. Foundational CJEU authority (**Planet49**, C-673/17) confirms that consent for cookies must be a genuine, active choice — a **pre-ticked box is not valid consent**, regardless of whether the stored data is personal [2].

Two forward-looking points are essential. First, the long-proposed **ePrivacy Regulation** (2017) that would have replaced the Directive was **formally withdrawn** by the European Commission (approved 16 July 2025; announced in the Official Journal 6 October 2025) as "outdated in light of recent legislation" [5]. Second, the Commission's **Digital Omnibus** package (late 2025) proposes to **move cookie-consent rules from the ePrivacy Directive into the GDPR** — but this is a *proposal*, not yet law [6]. Until any such reform is adopted, the Directive (and national laws such as PECR) remain in force.

# Key Takeaways

- The **ePrivacy Directive (2002/58/EC**, amended by 2009/136/EC) is the **lex specialis** to the GDPR for electronic communications; where both could apply, the specific ePrivacy rule prevails and the GDPR supplements it [1][3]. *(Legal obligation.)*
- **Article 5(3)** — storing or accessing information on a user's terminal (e.g., **cookies**) requires **consent**, unless strictly necessary for a service the user requested [1]. *(Legal obligation.)*
- **Consent** takes its meaning from the GDPR (Art. 4(11)): freely given, specific, informed, unambiguous, by clear affirmative action [3]. *(Legal obligation.)*
- **Planet49 (C-673/17)** — a **pre-ticked checkbox is not valid consent** for cookies, and this holds whether or not the stored/accessed data is personal data [2]. *(Case law.)*
- **Article 13** restricts **unsolicited direct marketing** by electronic means; unsolicited marketing generally requires prior consent, subject to the limited "soft opt-in" for existing customers [1]. *(Legal obligation.)*
- ePrivacy is a **Directive**, so obligations arise via national transposition — in the UK, **PECR 2003** [7]. *(Legal obligation.)*
- The **2017 ePrivacy Regulation proposal was withdrawn** (Commission approved 16 July 2025; OJ 6 October 2025) [5]. *(Legal/regulatory fact.)*
- The **Digital Omnibus** proposal (late 2025) proposes moving cookie rules into the GDPR, but is **not yet adopted** — the Directive/PECR remain in force [6]. *(Regulatory — proposal only.)*

# Purpose

This document is the entry point to the ePrivacy topic. It supports compliance teams implementing **cookie/consent** and **direct-marketing** controls, developers building consent-management and communications features, and legal researchers tracking the **ePrivacy/GDPR relationship** and the **reform trajectory**. It builds on `gdpr-foundations` (for the meaning of consent) and complements `uk-gdpr-foundations` (for the UK's PECR regime).

# Scope

**In scope:** The ePrivacy Directive's purpose and lex-specialis relationship to the GDPR; confidentiality of communications; the Art. 5(3) cookie/consent rule; traffic and location data at a foundational level; direct marketing (Art. 13); national transposition (PECR); the status of the ePrivacy Regulation and Digital Omnibus reform.

**Out of scope (spun off to the research backlog):** Detailed cookie-consent UX and consent-management platforms → `cookie-consent-implementation`; UK PECR in depth (marketing, fines, PECR/DUAA changes) → `pecr-detail`; data-retention and law-enforcement access case law (Digital Rights Ireland, Tele2/Watson, La Quadrature du Net) → `data-retention-caselaw`; the Digital Omnibus package as a whole → `digital-omnibus`.

**Assumptions:** The reader has read `gdpr-foundations`. Consent conditions are as defined there and in `GLOSSARY.md`.

# Definitions

*Shared terms (personal data, consent, controller, processor) are in `GLOSSARY.md`. Only ePrivacy-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| ePrivacy Directive | Directive 2002/58/EC on privacy and electronic communications, as amended by Directive 2009/136/EC. | [1] |
| Lex specialis | A specific law that prevails over a general law (here, ePrivacy over the GDPR) on the matters it specifically governs. | [1][3] |
| Cookie rule (Art. 5(3)) | The requirement to obtain consent before storing/accessing information on a user's terminal equipment, unless strictly necessary for a requested service. | [1] |
| Traffic data | Data processed for the purpose of conveying a communication on an electronic-communications network or billing for it (Art. 2(b)). | [1] |
| Location data | Data indicating the geographic position of a user's terminal equipment (Art. 2(c)). | [1] |
| Soft opt-in | Limited exception allowing marketing to existing customers about similar products, where an opt-out was offered at collection and in each message (Art. 13(2)). | [1] |
| PECR | Privacy and Electronic Communications (EC Directive) Regulations 2003 — the UK transposition of the ePrivacy Directive. | [7] |

# Background

The 2002 ePrivacy Directive "particularised and complemented" the earlier Data Protection Directive 95/46/EC for the electronic-communications sector, addressing risks specific to networks and services (confidentiality, cookies, unsolicited communications) [1]. The **2009 amendment (2009/136/EC)** strengthened the cookie rule, shifting it decisively towards a **consent** model [1]. When the GDPR replaced Directive 95/46/EC in 2018, the ePrivacy Directive's references to consent were read as references to **GDPR-standard consent**, tightening what "consent" requires for cookies and marketing [3].

The EU intended to modernise the regime with an **ePrivacy Regulation** (proposed 2017) that would apply directly and align enforcement with the GDPR [9]. That proposal stalled for years in inter-institutional negotiation and was ultimately **withdrawn** in 2025 [5]. Attention has shifted to folding ePrivacy's cookie rules into the GDPR through the **Digital Omnibus** simplification package [6].

# Legal Framework

The ePrivacy Directive applies to the processing of personal data in connection with the provision of **publicly available electronic-communications services** over public networks, and — importantly for the cookie rule — to the storing of / access to information on users' **terminal equipment** regardless of whether that information is personal data [1][2]. Because it is a Directive, the operative obligations for organisations arise under **national transposing law** (e.g., PECR in the UK) [7].

Relationship to the GDPR: the ePrivacy Directive is **lex specialis**. Where a matter is specifically governed by ePrivacy (e.g., cookie consent, confidentiality of communications, electronic marketing), the ePrivacy rule prevails; the GDPR continues to apply to questions ePrivacy does not specifically address, and supplies the **definition and conditions of consent** [1][3]. The EDPB has issued an opinion on this interplay [4].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 5(1) | Confidentiality of communications and related traffic data; prohibition on interception/surveillance without consent or legal authority. | [1] |
| Art. 5(3) | Consent required for storing/accessing information on terminal equipment (cookies and similar), unless strictly necessary for a requested service. | [1] |
| Art. 6 | Traffic data must be erased or anonymised when no longer needed for transmission, subject to billing/consent exceptions. | [1] |
| Art. 9 | Location data (other than traffic data) may be processed only when anonymised or with consent. | [1] |
| Art. 13 | Restrictions on unsolicited communications for direct marketing; prior consent generally required, with the Art. 13(2) "soft opt-in". | [1] |
| Art. 15 | Member States may restrict certain rights for national-security/law-enforcement purposes (basis for data-retention debates). | [1] |

## Relevant Recitals

*The Directive's recitals aid interpretation but are not binding operative provisions.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 24 | Terminal equipment and any information stored on it are part of the private sphere requiring protection ("spyware/cookies"). | [1] |
| Recital 25 | Cookies can be legitimate (e.g., analysing site effectiveness) but users must be informed and able to refuse. | [1] |
| Recital 66 (2009/136/EC) | Reinforced that storing/accessing information requires the user's consent, having been given clear information. | [1] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Planet49 (Verbraucherzentrale Bundesverband v Planet49) | CJEU (Grand Chamber), C-673/17, 1 Oct 2019, ECLI:EU:C:2019:801 | A **pre-ticked checkbox** does not constitute valid consent for cookies under Art. 5(3); this is independent of whether the stored/accessed data is personal data. | Sets the consent standard for cookies; aligns ePrivacy consent with GDPR-standard consent [2]. |
| *(Data-retention line)* | Digital Rights Ireland; Tele2/Watson; La Quadrature du Net | General/indiscriminate retention of communications data is generally incompatible with EU law (Art. 15 ePrivacy read with the Charter). | Foundational for Art. 15 / national retention laws — deferred to `data-retention-caselaw` (backlog). |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **EDPB** has clarified the **ePrivacy/GDPR interplay**: where processing triggers a specific ePrivacy rule, that rule applies, and supervisory competence/coordination follows accordingly [4]. *(Regulatory interpretation.)*
- The **ICO** (UK) enforces **PECR** alongside the UK GDPR, and treats cookie consent as requiring GDPR-standard consent; "strictly necessary" is interpreted narrowly (it does not cover analytics or advertising cookies) [8]. *(Regulatory interpretation.)*
- Consent must be **active**: reliance on pre-ticked boxes, "continue to browse" implied consent, or cookie walls that leave no genuine choice are treated as non-compliant, consistent with **Planet49** [2][8]. *(Regulatory interpretation / case law.)*
- **Reform status:** the Commission has **withdrawn** the ePrivacy Regulation proposal and is pursuing the **Digital Omnibus** route (moving cookie rules into the GDPR). Organisations should track this but must comply with the **current** Directive/PECR regime meanwhile [5][6]. *(Regulatory interpretation — proposal.)*

# Technical Considerations

- **Consent-before-set** — non-essential cookies/SDKs must not fire until the user has given consent; "strictly necessary" cookies (e.g., session, load-balancing, security) are exempt [1][8]. *(Legal obligation.)*
- **Granularity & symmetry** — provide granular purpose controls and make **rejecting** as easy as accepting; record consent (what, when, scope) and support withdrawal [2][8]. *(Best practice grounded in obligation.)*
- **Device access beyond cookies** — Art. 5(3) is technology-neutral: local storage, fingerprinting, pixel tags and SDK reads are in scope [1]. *(Legal obligation.)*
- **Traffic/location data** — minimise, anonymise or erase when no longer needed; gate value-added uses on consent (Arts. 6, 9) [1]. *(Legal obligation.)*
- **Marketing suppression** — maintain consent/opt-out and suppression lists to honour Art. 13; separate the "soft opt-in" path for existing customers [1]. *(Legal obligation.)*

# Hosting Considerations

- **Analytics & CDN cookies** — first-/third-party analytics and some CDN features set device storage and typically require consent unless strictly necessary; configure hosting/CDN so non-essential cookies are gated [1][8]. *(Legal obligation.)*
- **Log/traffic data** — server and network logs may constitute traffic data; apply retention and minimisation, and be aware of Art. 15/retention-law constraints [1]. *(Legal obligation; see `data-retention-caselaw`.)*
- **Controller responsibility** — the site/service operator (controller) remains responsible for third-party tags it deploys; contractual and technical controls over tag vendors are needed. *(Editorial recommendation.)*

# Game Hosting Considerations

- **Analytics, ads and telemetry SDKs** in games routinely store/read device information and fall under Art. 5(3); consent must be obtained before non-essential SDKs initialise [1]. *(Legal obligation.)*
- **Children** — combined with the low consent age and children's-code expectations (see `uk-gdpr-foundations`, `gdpr-foundations`), advertising/tracking SDKs in games likely to be used by children face heightened scrutiny. *(Legal obligation / best practice.)*
- **In-game messaging & marketing** — push notifications and promotional emails are electronic marketing subject to Art. 13 consent/soft-opt-in rules [1]. *(Legal obligation.)*

# AI Considerations

- **Tracking data for personalisation/AI** — behavioural data gathered via cookies/SDKs to train recommendation or ad-targeting models requires a valid Art. 5(3) consent for the collection layer, in addition to a GDPR basis for subsequent processing [1][3]. *(Legal obligation.)*
- **Consent as the gate** — because much AI personalisation depends on device-level tracking, ePrivacy consent is often the **binding constraint**, not the GDPR basis. *(Editorial note.)*
- No ePrivacy-specific AI regime exists; AI-specific obligations are covered in `ai-act-foundations` / `ai-governance-foundations` (backlog). *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Audit all device storage/access** (cookies, local storage, SDKs, pixels, fingerprinting) and classify each as strictly necessary or consent-required. *(OBLIGATION.)* [1]
2. **Deploy a compliant consent mechanism** — no non-essential storage before consent; reject as easy as accept; record and allow withdrawal. *(OBLIGATION + BEST PRACTICE.)* [2][8]
3. **Interpret "strictly necessary" narrowly** — analytics and advertising are not strictly necessary. *(OBLIGATION per ICO.)* [8]
4. **Govern marketing** — apply Art. 13: consent by default, soft opt-in only where its conditions are met; honour opt-outs and suppression. *(OBLIGATION.)* [1]
5. **Manage third-party tags** — inventory vendors, gate their loading on consent, and contract for compliance. *(BEST PRACTICE.)*
6. **Track reform** — monitor the Digital Omnibus proposal and any migration of cookie rules into the GDPR; do not pre-implement unadopted rules. *(EDITORIAL RECOMMENDATION.)* [5][6]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Non-essential cookies/SDKs firing before consent | High | High | Art. 5(3); Planet49 [1][2] | Consent-before-set; tag gating; audits | Low |
| R2 | Treating analytics/ads as "strictly necessary" | High | Medium | Art. 5(3); ICO [8] | Correct classification; DPIA of trackers | Low |
| R3 | Pre-ticked / implied consent or cookie walls | Medium | High | Planet49 [2] | Active, symmetric consent UX | Low |
| R4 | Unlawful direct marketing (no consent/soft opt-in) | Medium | Medium | Art. 13 [1] | Consent+suppression lists; soft-opt-in controls | Low |
| R5 | Excessive traffic/location data retention | Medium | Medium | Arts. 6, 9, 15 [1] | Minimise/anonymise; retention schedule | Medium |
| R6 | Pre-implementing withdrawn/unadopted reform | Low | Medium | Reform status [5][6] | Track official status; comply with current law | Low |

# Implementation Roadmap

- **Phase 0 — Tracker inventory:** Enumerate all device storage/access and marketing channels; classify. *Effort:* Medium.
- **Phase 1 — Consent platform:** Implement consent-before-set with granular, symmetric controls and consent records. *Effort:* Medium–High.
- **Phase 2 — Marketing controls:** Art. 13 consent/soft-opt-in workflows and suppression. *Effort:* Medium.
- **Phase 3 — Data lifecycle:** Traffic/location minimisation and retention aligned with Art. 15 constraints. *Effort:* Medium.
- **Phase 4 — Watch & adapt:** Monitor Digital Omnibus / national reforms; adjust when adopted. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Cookies set without consent; no tracker inventory. | Non-essential cookies fire on load. |
| 2 | Managed | Basic banner present; some gating; marketing opt-outs exist. | Consent banner; partial inventory. |
| 3 | Defined | Consent-before-set; granular controls; consent records; marketing governed. | Full tracker inventory; symmetric UX. |
| 4 | Quantitatively Managed | Metrics on consent rates, tag compliance, marketing suppression. | KPIs; periodic tracker audits. |
| 5 | Optimising | Automated tag governance; proactive reform tracking; vendor assurance. | Tag manager enforcing consent; contingency for reform. |

# Audit Questions

1. Do you have a complete inventory of cookies, SDKs and other device storage/access, classified by necessity? *(Art. 5(3) [1].)*
2. Are non-essential trackers blocked until consent is given, with reject as easy as accept? *(Planet49 [2]; ICO [8].)*
3. How is consent recorded, and how can users withdraw it? *(Consent conditions [3].)*
4. On what basis is any cookie treated as "strictly necessary"? *(Art. 5(3) [1].)*
5. How do you comply with Art. 13 for each marketing channel (consent vs soft opt-in)? *(Art. 13 [1].)*
6. What are your retention/anonymisation rules for traffic and location data? *(Arts. 6, 9 [1].)*
7. How do you monitor and control third-party tags? *(Operational.)*
8. How are you tracking the Digital Omnibus reform without pre-implementing unadopted rules? *([5][6].)*

# Implementation Checklist

- [ ] Complete tracker/marketing inventory with necessity classification.
- [ ] Consent-before-set enforced for all non-essential storage/access.
- [ ] Reject-all as prominent and easy as accept-all; no pre-ticked boxes.
- [ ] Consent records captured; withdrawal mechanism available.
- [ ] "Strictly necessary" classifications documented and defensible.
- [ ] Art. 13 marketing consent / soft-opt-in workflows and suppression lists in place.
- [ ] Traffic/location data minimisation and retention rules applied.
- [ ] Third-party tag governance (inventory, gating, contracts).
- [ ] Reform watch-list for the Digital Omnibus / national ePrivacy changes.

# References

*All links verified live on 2026-07-10 (`sources_verified`).*

## Primary Sources

- [1] **Directive 2002/58/EC (ePrivacy Directive), consolidated text** (as amended by Directive 2009/136/EC). EUR-Lex, CELEX 02002L0058-20091219. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219
- [2] **Planet49 (Verbraucherzentrale Bundesverband v Planet49 GmbH)**, C-673/17, ECLI:EU:C:2019:801. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:62017CJ0673
- [3] **Regulation (EU) 2016/679 (GDPR)**, consolidated text (definition/conditions of consent; general regime). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [7] **Privacy and Electronic Communications (EC Directive) Regulations 2003 (PECR)**, SI 2003/2426. legislation.gov.uk. https://www.legislation.gov.uk/uksi/2003/2426/contents

## Regulatory Guidance

- [4] **Opinion 5/2019 on the interplay between the ePrivacy Directive and the GDPR.** European Data Protection Board (EDPB). https://www.edpb.europa.eu/sites/default/files/files/file1/201905_edpb_opinion_eprivacydir_gdpr_interplay_en_0.pdf
- [5] **Proposal for a Regulation on Privacy and Electronic Communications — status: withdrawn** (Commission approved 16 July 2025; OJ 6 October 2025). European Parliament, Legislative Train Schedule. https://www.europarl.europa.eu/legislative-train/theme-connected-digital-single-market/file-jd-e-privacy-reform
- [6] **Digital Omnibus package** (proposal to move cookie rules into the GDPR; late 2025). European Parliament, Legislative Train Schedule. https://www.europarl.europa.eu/legislative-train/theme-a-new-plan-for-europe-s-sustainable-prosperity-and-competitiveness/file-digital-package
- [8] **Guide to PECR.** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/
- [9] **ePrivacy Regulation policy page.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/eprivacy-regulation

## Standards

*As per `gdpr-foundations` — ISO/IEC 27001:2022 and ISO/IEC 27701 apply to the underlying processing. No ePrivacy-specific standards are introduced at the foundational level.* Not Applicable (no distinct ePrivacy standards).

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation, case law and regulatory guidance. Academic analysis will be cited in the cookie-consent and data-retention sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Commission — ePrivacy Regulation policy overview. https://digital-strategy.ec.europa.eu/en/policies/eprivacy-regulation
- ICO — cookies and similar technologies guidance (within the Guide to PECR). https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/

# Related Documents

- `gdpr-foundations` — meaning/conditions of consent (**prerequisite reading**).
- `uk-gdpr-foundations` — UK regime and PECR context.
- `cookie-consent-implementation` — consent UX and CMPs (planned).
- `pecr-detail` — UK PECR in depth incl. DUAA changes (planned).
- `data-retention-caselaw` — Art. 15 retention line of cases (planned).
- `digital-omnibus` — the 2025 simplification package (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-10 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Directive 2002/58/EC, Planet49), EDPB, ICO, European Commission and European Parliament sources; reform status (ePrivacy Regulation withdrawal, Digital Omnibus) live-verified. | *pending human review* |
