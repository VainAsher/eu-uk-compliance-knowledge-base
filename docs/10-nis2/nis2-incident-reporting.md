---
id: nis2-incident-reporting
title: "NIS2: Significant-Incident Reporting"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: NIS2
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [nis2-foundations, dora-foundations, gdpr-foundations, cyber-resilience-act, cybersecurity-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [nis2, incident-reporting, significant-incident, article-23, early-warning, csirt, implementing-regulation-2024-2690, gdpr-breach, dora-incident-reporting]
legal_basis: Directive (EU) 2022/2555; Commission Implementing Regulation (EU) 2024/2690
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | nis2-incident-reporting |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.14.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. NIS2 is a **Directive**, so the binding reporting rules that apply to an entity are the **national transposition laws**, which may add national portals, formats and (permitted) stricter timelines; the Article 23 cascade and the Implementing Regulation (EU) 2024/2690 thresholds set the harmonised floor. The **significant-incident thresholds quoted here from Implementing Regulation (EU) 2024/2690 were live-verified against the EUR-Lex text on 2026-07-11**; always confirm the current national transposing law and any sector-specific reporting arrangements before relying on this document. See `nis2-foundations` for scope, entity classification and the wider obligation set.

# Executive Summary

This document is the deep dive on the **NIS2 significant-incident reporting regime**. It explains **what counts as a "significant incident"**, **who must report what, to whom and by when**, and how the NIS2 duty interacts with the **GDPR** personal-data-breach regime and the **DORA** financial-sector incident regime. It supports incident-response, legal and engineering teams building a reporting capability that survives contact with a live incident and a regulator's audit [1][5].

A **significant incident** is defined at two levels. **Article 23(3)** of Directive (EU) 2022/2555 sets the qualitative test: an incident is significant if it *has caused or is capable of causing severe operational disruption of the services or financial loss* for the entity, **or** *has affected or is capable of affecting other persons by causing considerable material or non-material damage* [1]. For eleven named digital-infrastructure, ICT-service-management and digital-provider entity types, **Commission Implementing Regulation (EU) 2024/2690** converts that test into **quantitative thresholds** — for example, a **direct financial loss above EUR 500 000 or 5% of annual turnover (whichever is lower)**, exfiltration of trade secrets, death or serious harm to a person, or availability, integrity and confidentiality thresholds specific to each service (e.g., a cloud service *completely unavailable for more than 30 minutes*) [2].

The heart of the regime is the **Article 23(4) reporting cascade**: an **early warning within 24 hours** of becoming aware of a significant incident, a fuller **incident notification within 72 hours**, an **intermediate report on request**, and a **final report within one month** of the notification (with a **progress report** if the incident is still ongoing) [1]. Reports go to the **CSIRT or the competent authority**; the CSIRT should respond **within 24 hours** of the early warning [1]. NIS2 runs **in parallel** with the GDPR (a personal-data breach still triggers **Art. 33/34**) and **defers to DORA as lex specialis** for financial entities, who report under DORA Art. 19 instead of NIS2 Art. 23 [1][3][4].

# Key Takeaways

- A **significant incident** is defined by the two-limb qualitative test in **Art. 23(3)** — severe operational disruption/financial loss to the entity, or considerable material/non-material damage to others [1]. *(Legal obligation.)*
- For **eleven digital entity types**, **Implementing Regulation (EU) 2024/2690** specifies **quantitative and qualitative thresholds**; the cross-sector triggers include **direct financial loss > EUR 500 000 or 5% of turnover (whichever is lower)**, trade-secret exfiltration, **death or serious harm to a person**, and suspected malicious unauthorised access capable of severe disruption [2]. *(Legal obligation for those entities — live-verified 2026-07-11.)*
- The **Art. 23(4) cascade** is fixed: **early warning ≤ 24 h**, **incident notification ≤ 72 h**, **intermediate report on request**, **final report ≤ 1 month**, plus a **progress report** for still-ongoing incidents [1]. *(Legal obligation.)*
- Reports are made to the **CSIRT or, where applicable, the competent authority**; the CSIRT should give a **response within 24 h** of the early warning, including mitigation guidance and, on request, technical support [1]. *(Legal obligation / recipient duty.)*
- **Trust service providers** have a **derogation**: significant incidents affecting their trust services are notified **within 24 hours** [1]. *(Legal obligation — sector-specific.)*
- Entities must, **where appropriate, notify recipients of their services** of significant incidents and of significant cyber threats and the remedies available (**Art. 23(1)–(2)**) [1]. *(Legal obligation.)*
- **Cross-border** incidents are shared by the CSIRT/competent authority/single point of contact with **other affected Member States and ENISA** (**Art. 23(6)**); regulators may **inform the public** (**Art. 23(7)**) [1]. *(Legal obligation on recipients.)*
- **Voluntary notification** of non-significant incidents, near misses and cyber threats is expressly permitted under **Art. 30**, without creating additional liability [1]. *(Best practice — enabled.)*
- **Parallel regimes:** a personal-data breach still triggers **GDPR Art. 33 (72 h) / Art. 34**; **financial entities report under DORA Art. 19**, not NIS2 Art. 23 (NIS2 Art. 4 lex specialis) — the three regimes have **different clocks, recipients and thresholds** [1][3][4]. *(Legal obligation — run each on its own terms.)*
- **Failure to report** is enforced through Arts. 32–34: supervisory measures and administrative fines to **≥ €10m or 2%** of worldwide turnover (essential) and **≥ €7m or 1.4%** (important) [1]. *(Legal obligation.)*

# Purpose

This document exists to make the NIS2 reporting duty operational. It supports: (a) **legal research** — pinning the exact triggers, deadlines, recipients and report contents to primary text; (b) **incident-response readiness** — a runbook, timeline and checklist teams can execute against the 24 h / 72 h / 1-month clock; and (c) **cross-regime coordination** — deciding, in the first hour of an incident, which of NIS2, GDPR and DORA apply and on which clocks. It is the sub-topic deep dive promised by `nis2-foundations`, which it details, and it is a sibling to `dora-foundations` (the financial-sector incident regime) and `gdpr-foundations` (personal-data breach notification).

# Scope

**In scope:** The meaning of "significant incident" under Art. 23(3) and the quantitative/qualitative thresholds in Implementing Regulation (EU) 2024/2690 for the covered digital entity types; the Art. 23(4) reporting cascade (early warning, incident notification, intermediate report, final report, progress report) and the special trust-service-provider timing; who reports to whom (CSIRT / competent authority) and recipient duties (Art. 23(5)–(7)); notification of recipients of services and of cyber threats (Art. 23(1)–(2)); cross-border and voluntary notification (Arts. 23(6), 30); the interplay with GDPR Art. 33/34 and DORA Art. 17–19; and supervision/penalties for reporting failures (Arts. 32–34). A reporting **runbook, timeline and checklist**, and a **NIS2 vs GDPR vs DORA comparison table**, are included.

**Out of scope (covered elsewhere):** The full **Art. 21 risk-management measures** and the technical/methodological requirements in Implementing Regulation (EU) 2024/2690 (control-by-control) → `nis2-foundations` and a planned `nis2-controls-mapping`; **scope, entity classification and registration** → `nis2-foundations` / planned `nis2-sectors`; the **national transposition comparison** → planned `nis2-transposition-tracker`; the **DORA incident-classification and reporting mechanics** in depth (RTS/ITS templates, exact DORA hour deadlines) → `dora-foundations` and planned DORA sub-topics; the **GDPR breach process** in depth → `gdpr-foundations`; **CRA product-vulnerability reporting** → `cyber-resilience-act`.

**Assumptions:** The reader has read `nis2-foundations` and understands the essential/important entity distinction and the Directive-vs-Regulation point (NIS2 binds through national transposition). Where personal data is involved the **GDPR applies in parallel**; where the entity is a financial entity, **DORA applies as lex specialis**.

# Definitions

*Shared terms (essential entity, important entity, significant incident, CSIRT) are in `GLOSSARY.md`. Reporting-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Significant incident | An incident that has caused or is capable of causing severe operational disruption of the services or financial loss for the entity, or that has affected or is capable of affecting other natural or legal persons by causing considerable material or non-material damage (Art. 23(3)). | [1] |
| Early warning | The first-stage notification under Art. 23(4)(a), due within **24 hours** of becoming aware of a significant incident, indicating (where applicable) whether the incident is suspected to be unlawful/malicious or could have cross-border impact. | [1] |
| Incident notification | The second-stage report under Art. 23(4)(b), due within **72 hours**, updating the early warning with an initial assessment including severity, impact and (where available) indicators of compromise. | [1] |
| Intermediate report | A status update the entity must provide **on request** of the CSIRT or competent authority (Art. 23(4)(c)). | [1] |
| Final report | The Art. 23(4)(d) report due **within one month** of the incident notification, containing a detailed description, severity/impact, root cause/threat type, applied mitigations and any cross-border impact. | [1] |
| Progress report | Where the incident is still ongoing when the final report is due, a report submitted at that time, with a final report following within one month of handling the incident (Art. 23(4)(e)). | [1] |
| Competent authority | The national authority designated under NIS2 Art. 8 to supervise and enforce; a permitted recipient of incident reports alongside the CSIRT. | [1] |
| Single point of contact (SPOC) | The national liaison designated under Art. 8(3) exercising a cross-border coordination function for incident information (Art. 23(6)). | [1] |
| Recipient of services | A user of the entity's service which the entity must, where appropriate, notify of a significant incident likely to adversely affect it, or of a significant cyber threat (Art. 23(1)–(2)). | [1] |
| Voluntary notification | Notification, under Art. 30, of incidents, cyber threats and near misses that are not significant (or by entities outside scope), without imposing additional obligations or liability. | [1] |

# Background

The original NIS Directive ((EU) 2016/1148) required incident notification but left the trigger ("substantial"/"significant" impact) and the timing to divergent national implementation, producing inconsistent, hard-to-aggregate reporting across the Union [1][5]. NIS2 responds by **harmonising the reporting duty into a single multi-stage cascade** with fixed outer deadlines and by empowering the Commission to fix **quantitative thresholds** for the most cross-border digital sectors, so that "significant" means the same thing for a cloud or DNS provider regardless of Member State [1][2][5]. Recital-level design (see `nis2-foundations`) makes the cascade deliberately staged: a **fast early warning** to enable rapid situational awareness and assistance, followed by **progressively complete information** as the entity's own understanding matures, so that speed does not come at the cost of accuracy [1]. The Implementing Regulation (EU) 2024/2690 — adopted **17 October 2024** and applicable from **18 October 2024** — is the first exercise of the Art. 23(11) power and specifies both the Art. 21 technical measures and the significant-incident thresholds for eleven digital entity types [2].

# Legal Framework

The reporting duty sits in **Chapter IV** of NIS2. **Article 23** is the operative provision; it is supported by **Article 30** (voluntary notification), **Article 35** (incidents entailing a personal-data breach), **Article 4** (relationship with sector-specific acts such as DORA), and the supervision/enforcement machinery in **Articles 32–34**. For eleven digital entity types the thresholds are specified by **Implementing Regulation (EU) 2024/2690**, adopted under **Art. 23(11)** [1][2].

The Article 23 structure:

- **Art. 23(1)** — the core duty: notify **the CSIRT or, where applicable, the competent authority**, without undue delay, of any **significant incident**; and, where appropriate, **notify recipients** of services of a significant incident likely to adversely affect the service.
- **Art. 23(2)** — where appropriate, notify recipients of a **significant cyber threat** and of any measures or remedies they can take.
- **Art. 23(3)** — the **definition** of a significant incident (two limbs).
- **Art. 23(4)** — the **cascade**: (a) early warning ≤ 24 h; (b) incident notification ≤ 72 h; (c) intermediate report on request; (d) final report ≤ 1 month; (e) progress report for ongoing incidents — with a **24-hour derogation for trust service providers**.
- **Art. 23(5)** — the **CSIRT/competent-authority response** within 24 h of the early warning (feedback, mitigation guidance, technical support, law-enforcement guidance where relevant).
- **Art. 23(6)** — **cross-border**: the SPOC/CSIRT/competent authority informs other affected Member States and **ENISA**.
- **Art. 23(7)** — the authority/CSIRT **may inform the public** (after consulting the entity) where public awareness is needed.
- **Art. 23(11)** — the Commission adopts **implementing acts** further specifying when an incident is significant (delivered as Implementing Regulation (EU) 2024/2690) [1][2].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 23(1) | Notify CSIRT/competent authority of significant incidents without undue delay; notify affected recipients where appropriate. | [1] |
| Art. 23(2) | Where appropriate, notify recipients of significant cyber threats and available remedies. | [1] |
| Art. 23(3) | Definition of a **significant incident** (two limbs). | [1] |
| Art. 23(4)(a) | **Early warning** within **24 hours** of awareness. | [1] |
| Art. 23(4)(b) | **Incident notification** within **72 hours** of awareness (initial assessment, severity, impact, IoCs). | [1] |
| Art. 23(4)(c) | **Intermediate report** on request of the CSIRT/competent authority. | [1] |
| Art. 23(4)(d) | **Final report** within **one month** of the incident notification (detailed description, root cause, mitigations, cross-border impact). | [1] |
| Art. 23(4)(e) | **Progress report** where the incident is still ongoing, plus a final report within one month of handling it. | [1] |
| Art. 23(4) (TSP derogation) | **Trust service providers** notify significant incidents affecting their trust services within **24 hours**. | [1] |
| Art. 23(5) | CSIRT/competent authority response within **24 hours** of the early warning (feedback, guidance, technical support). | [1] |
| Art. 23(6) | Cross-border information-sharing with other affected Member States and **ENISA** via the SPOC. | [1] |
| Art. 23(7) | Authority may **inform the public**, after consulting the entity. | [1] |
| Art. 23(11) | Commission implementing acts specifying significant-incident cases (→ Reg (EU) 2024/2690). | [1][2] |
| Art. 30 | **Voluntary notification** of non-significant incidents, near misses and cyber threats. | [1] |
| Art. 35 | Incidents **entailing a personal-data breach**: cooperation with, and information to, the GDPR supervisory authority. | [1][3] |
| Art. 4 | Relationship with sector-specific acts (**DORA** as lex specialis for financial entities). | [1][4] |
| Arts. 32–34 | Supervision and **administrative fines** for infringements, including reporting failures. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 101 area | The **multi-stage** reporting approach — early warning then progressively complete information — balances rapid response against report accuracy. | [1] |
| Recital 102 area | The 24 h early warning is to enable the CSIRT to offer **assistance/mitigation**, not to impose a heavy initial burden. | [1] |
| Recital 104 area | **Voluntary reporting** and information-sharing should be encouraged without additional liability (Art. 30). | [1] |
| Recital 6 / Art. 4 area | Where a sector-specific Union act (e.g., **DORA**) imposes at least equivalent reporting, it applies as **lex specialis**. | [1][4] |

## Relevant Case Law

**Not Applicable.** NIS2's reporting provisions are recent and bite through national transposition; there is no CJEU case law interpreting Art. 23 or Implementing Regulation (EU) 2024/2690 to date. The only NIS2 litigation so far concerns **enforcement of the transposition duty against Member States** (infringement actions under Art. 258/260 TFEU — see `nis2-foundations`), not the substance of the reporting cascade. Interpretive weight currently rests on the primary text and Commission/ENISA guidance [1][5][6].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames NIS2 reporting as a harmonised duty to notify **significant incidents** through a staged process, with the Implementing Regulation providing the sector detail for digital infrastructure and providers [5]. *(Regulatory interpretation.)*
- **ENISA's NIS2 Technical Implementation Guidance** maps the Art. 21 measures and, for the covered entities, aligns them with the **significant-incident parameters** of Implementing Regulation (EU) 2024/2690 — a practical reference for building detection and classification logic that feeds the reporting clock [6][7]. *(Regulatory guidance — supports, does not replace, national law.)*
- **Implementing Regulation (EU) 2024/2690** is the authoritative specification of "significant" for the eleven digital entity types. Its **Article 3** sets cross-cutting triggers (financial loss, trade-secret exfiltration, death/serious harm, suspected malicious unauthorised access), its **Article 4** aggregates **recurring incidents** (same root cause, at least twice in six months, collectively meeting the financial-loss threshold) into one significant incident, and its **entity-specific articles (5–14)** set availability/integrity thresholds per service [2]. *(Legal obligation for those entities; regulatory specification of Art. 23(3).)*
- **National transposition adds detail:** the CSIRT/competent authority split, the reporting **portal and format**, and any permitted stricter timing are set by each Member State's transposing law; the Art. 23 cascade and the Implementing Regulation thresholds are the **harmonised floor**, not the whole picture [1][5]. *(Regulatory interpretation — verify the national law.)*

# Technical Considerations

- **Detection-to-classification pipeline** — the reporting clock starts when the entity **becomes aware** of a significant incident, so detection must feed a **classification decision** quickly. Engineer automated signals (availability monitors, integrity/authenticity checks, unauthorised-access alerts) that map directly onto the Art. 23(3) limbs and the Implementing Regulation thresholds [1][2]. *(Best practice; obligation to report once significant.)*
- **Threshold instrumentation for digital entities** — covered entity types should instrument the **specific metrics** that make an incident significant: complete-unavailability timers (e.g., 30 minutes for cloud/CDN/DNS/managed services; 20 minutes for trust services), **limited-availability** user-percentage/absolute thresholds (>5% or >1 million EU users, whichever is smaller), and **integrity/confidentiality** compromise detection [2]. *(Legal obligation for those entities.)*
- **Report content readiness** — pre-build templates that capture what each stage needs: early warning (unlawful/malicious suspicion, cross-border flag); 72 h notification (severity, impact, indicators of compromise); final report (detailed description, **root cause/threat type**, mitigations, cross-border impact) [1]. *(Best practice.)*
- **Recurring-incident aggregation** — implement logic to detect **repeat incidents with a common root cause** (Art. 4 of the Implementing Regulation) that collectively cross the financial-loss threshold, since these become a single reportable significant incident [2]. *(Legal obligation for covered entities.)*
- **Clock and evidence discipline** — timestamp "awareness", preserve forensic evidence and log the decision trail; supervisory audit (Arts. 32–33) will test whether the 24 h / 72 h / 1-month deadlines were met and whether classification was reasonable [1]. *(Best practice.)*
- **Standards alignment** — align the process with **ISO/IEC 27035** (incident management) and **NIST SP 800-61** (incident handling) so the NIS2 stages sit inside a recognised lifecycle (detect → triage → respond → report → learn) [9][10]. *(Best practice.)*

# Hosting Considerations

- **Cloud, data-centre, CDN, DNS and managed/managed-security providers are exactly the entities the Implementing Regulation targets** — they must instrument the service-specific thresholds in Arts. 5–10 of Reg (EU) 2024/2690 and be able to fire an Art. 23 early warning within 24 hours of a qualifying outage or compromise [1][2]. *(Legal obligation — assess role.)*
- **Availability arithmetic is the operational crux** — "completely unavailable for more than 30 minutes" and "limited availability affecting >5% or >1 million EU users, whichever is smaller, for more than one hour" are **measurable SLIs**; hosting platforms should map these onto existing SLO monitoring so classification is automatic, not manual [2]. *(Best practice; obligation to report once crossed.)*
- **Multi-tenant blast radius and recipient notification** — where an incident is likely to adversely affect customers, the Art. 23(1) duty to **notify recipients** overlaps with contractual incident-notification SLAs; align the two so a single event does not produce inconsistent customer and regulator messaging [1]. *(Legal obligation + best practice.)*
- **Supply-chain propagation** — an in-scope customer's NIS2 duties flow down as contractual incident-cooperation and evidence obligations; hosts should expect to feed customers the data they need for their own Art. 23 reports [1]. *(Best practice — anticipate.)*

# Game Hosting Considerations

- **Pure game hosting is generally out of NIS2 scope** — online gaming is not an Annex I/II sector, so a studio or game-server operator is usually **not** obliged to report under Art. 23 by virtue of gaming alone (see `nis2-foundations`) [1][5]. *(Interpretation.)*
- **Infrastructure roles pull an operator in** — if the operator also runs **cloud, data-centre, CDN, DNS or managed-security** services, those activities are in scope and the Implementing Regulation thresholds apply to them regardless of the gaming context; a qualifying outage of that infrastructure is reportable [1][2]. *(Legal obligation — assess by activity.)*
- **Upstream dependency reporting** — even when out of direct scope, game hosts depend on in-scope cloud/CDN/DNS providers whose incidents will be reported (and whose recipient-notifications the host will receive); build intake for these so downstream player-facing decisions are informed [1]. *(Best practice.)*
- **Parallel player-data duties** — a security incident affecting player personal data still triggers **GDPR Art. 33/34** independently of NIS2, on the GDPR clock; do not treat "out of NIS2 scope" as "no reporting duty" [3]. *(Legal obligation.)*

# AI Considerations

- **AI systems are in the reporting perimeter** — where an in-scope entity operates AI/ML as part of its network and information systems, an incident affecting those systems (availability, integrity, unauthorised access, data compromise) can be a **significant incident** and is reported through the same Art. 23 cascade [1][2]. *(Legal obligation.)*
- **AI-assisted detection helps meet the clock** — anomaly detection and automated triage can shorten time-to-awareness and support the 24 h / 72 h deadlines, but automation must not **delay** the awareness timestamp or degrade report accuracy (the cascade rewards timely, then complete, information) [1]. *(Best practice.)*
- **Distinguish AI Act serious-incident reporting** — high-risk AI providers/deployers have a **separate** serious-incident reporting duty under the AI Act (a different regime, recipient and threshold); NIS2 reporting does not discharge it, and vice versa (see `ai-act-high-risk`). *(Cross-reference — parallel duties.)*
- **GDPR overlap for AI on personal data** — an AI-related security incident touching personal data triggers **GDPR Art. 33/34** in parallel with NIS2 [3]. *(Legal obligation — run both.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

## Reporting runbook (per significant incident)

1. **Detect and record "awareness"** — the moment a reasonable assessment concludes an incident may be significant, timestamp it; this starts the 24 h / 72 h clocks. *(OBLIGATION — foundational.)* [1]
2. **Classify against the thresholds** — apply Art. 23(3) and, for covered entities, the Implementing Regulation Arts. 3–14 thresholds (financial loss, malicious access, availability/integrity limits, recurring-incident aggregation). *(OBLIGATION.)* [1][2]
3. **Send the early warning ≤ 24 h** — to the CSIRT or competent authority; flag suspected unlawful/malicious cause and potential cross-border impact. *(OBLIGATION.)* [1]
4. **Notify recipients where appropriate** — tell affected service recipients (and, for cyber threats, the remedies) under Art. 23(1)–(2), coordinated with contractual SLAs. *(OBLIGATION where appropriate.)* [1]
5. **Send the incident notification ≤ 72 h** — update the early warning with severity, impact and indicators of compromise. *(OBLIGATION.)* [1]
6. **Engage the CSIRT response** — use the ≤ 24 h feedback, request mitigation guidance and technical support, and act on law-enforcement guidance if criminality is suspected. *(BEST PRACTICE — use the entitlement.)* [1]
7. **Provide intermediate reports on request** — supply status updates whenever the CSIRT/competent authority asks. *(OBLIGATION when requested.)* [1]
8. **Submit the final report ≤ 1 month** — detailed description, severity/impact, root cause/threat type, applied and ongoing mitigations, cross-border impact; if still ongoing, submit a **progress report** now and a final report within one month of handling. *(OBLIGATION.)* [1]
9. **Run parallel regimes** — if personal data is affected, run **GDPR Art. 33/34** on its own clock (following EDPB breach-notification guidance); if the entity is a financial entity, report under **DORA Art. 19**, not NIS2 (Art. 4 lex specialis). *(OBLIGATION.)* [1][3][4][8]
10. **Post-incident learning** — feed root cause into Art. 21 measures and update the runbook; consider **voluntary notification** (Art. 30) of near misses. *(BEST PRACTICE / EDITORIAL RECOMMENDATION.)* [1]

## Indicative timeline

```
T0        Awareness of a (potentially) significant incident  → start clocks, classify
≤ T0+24h  EARLY WARNING to CSIRT/competent authority (Art. 23(4)(a))
          [Trust service providers: 24h notification for TSP-affecting incidents]
≤ 24h     CSIRT/competent-authority RESPONSE (feedback + mitigation guidance) (Art. 23(5))
≤ T0+72h  INCIDENT NOTIFICATION (severity, impact, IoCs) (Art. 23(4)(b))
on request INTERMEDIATE REPORT (status updates) (Art. 23(4)(c))
≤ +1 month FINAL REPORT after the notification (root cause, mitigations, cross-border) (Art. 23(4)(d))
if ongoing PROGRESS REPORT now + FINAL REPORT within 1 month of handling (Art. 23(4)(e))
parallel   GDPR Art. 33 (≤72h) / Art. 34 where personal data breached; DORA Art. 19 for financial entities
```

## NIS2 vs GDPR vs DORA reporting — comparison

*Distinct regimes with different triggers, clocks and recipients; an incident can engage more than one.*

| Dimension | NIS2 (Art. 23) | GDPR (Arts. 33–34) | DORA (Arts. 17–19) |
|-----------|----------------|--------------------|--------------------|
| Trigger | **Significant incident** (Art. 23(3) + Reg 2024/2690 thresholds) [1][2] | **Personal-data breach** (Art. 4(12)) [3] | **Major ICT-related incident** (Art. 18 classification) [4] |
| Who reports | Essential/important entities [1] | Controller (processor → controller) [3] | Financial entities [4] |
| Recipient | **CSIRT or competent authority**; recipients of services [1] | **Supervisory authority**; data subjects (high risk) [3] | **Competent authority** (via ESA templates) [4] |
| Initial clock | **Early warning ≤ 24 h** of awareness [1] | Notify SA **≤ 72 h** of awareness (unless no risk) [3] | **Initial notification** on a short RTS/ITS clock [4] |
| Second stage | **Incident notification ≤ 72 h** [1] | Phased/supplementary info allowed (Art. 33(4)) [3] | **Intermediate report** [4] |
| Final stage | **Final report ≤ 1 month** (+ progress report) [1] | No fixed final-report deadline [3] | **Final report** (RTS/ITS timing) [4] |
| Notify affected people | Recipients of services where appropriate [1] | Data subjects where **high risk** (Art. 34) [3] | Clients where appropriate [4] |
| Relationship | Parallel to GDPR; **defers to DORA** (Art. 4) [1][4] | Parallel to NIS2/DORA [3] | **Lex specialis** for financial entities [4] |
| Max fines | ≥ €10m/2% (essential); ≥ €7m/1.4% (important) [1] | €20m/4% (Art. 83) [3] | Penalties/remedies by competent authority (Art. 50) [4] |

**Practical rule (EDITORIAL RECOMMENDATION):** in the first hour, ask three questions in parallel — *Is it a significant incident (NIS2)? Does it involve a personal-data breach (GDPR)? Are we a financial entity or serving one (DORA)?* — and start each applicable clock independently. Do not assume one report satisfies another; the recipients and deadlines differ [1][3][4].

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Missing the 24 h early-warning deadline | Medium | High | Art. 23(4)(a) [1] | Awareness timestamping; pre-drafted early-warning template; on-call routing | Low |
| R2 | Mis-classifying a significant incident as non-significant | Medium | High | Art. 23(3); Reg 2024/2690 [1][2] | Threshold-mapped detection; documented classification decision | Low |
| R3 | Covered digital entity not instrumented to the Reg 2024/2690 thresholds | Medium | High | Reg 2024/2690 Arts. 5–14 [2] | Availability/integrity SLIs mapped to thresholds; alerting | Medium |
| R4 | Failing to notify affected recipients of services | Medium | Medium | Art. 23(1)–(2) [1] | Recipient-notification playbook aligned with contractual SLAs | Low |
| R5 | Running only NIS2 and missing GDPR Art. 33 (72 h) or DORA Art. 19 | Medium | High | Arts. 4, 35 [1]; GDPR [3]; DORA [4] | Parallel-regime trigger check at T0; joint incident process | Low |
| R6 | Incomplete/late final report (weak root-cause or cross-border analysis) | Medium | Medium | Art. 23(4)(d)–(e) [1] | Forensic evidence discipline; final-report template; progress-report path | Low |
| R7 | Trust service provider applying 72 h instead of the 24 h derogation | Low | High | Art. 23(4) TSP derogation [1] | TSP-specific runbook; 24 h routing for TSP-affecting incidents | Low |
| R8 | Reporting failure escalating to supervision/fines | Low | High | Arts. 32–34 [1] | Audit-ready evidence trail; drills; management-body oversight | Low |

# Implementation Roadmap

- **Phase 0 — Applicability & mapping:** Confirm scope/tier (via `nis2-foundations`); identify the CSIRT/competent authority and national portal/format per Member State; decide whether DORA lex specialis applies. *Effort:* Medium.
- **Phase 1 — Classification design:** Encode Art. 23(3) and, for covered entities, the Reg 2024/2690 thresholds (incl. recurring-incident aggregation) into detection/triage logic. *Effort:* High.
- **Phase 2 — Report templates & routing:** Build early-warning, 72 h notification, intermediate, final and progress-report templates; wire on-call routing and recipient-notification playbooks. *Effort:* Medium.
- **Phase 3 — Cross-regime integration:** Add the GDPR Art. 33/34 and DORA Art. 19 triggers to the intake; define a single incident record feeding all applicable regimes. *Effort:* Medium.
- **Phase 4 — Drills & evidence:** Run tabletop exercises against the 24 h / 72 h / 1-month clock; verify timestamp, evidence-preservation and decision-log discipline. *Effort:* Medium.
- **Phase 5 — Monitor & improve:** Track national transposition specifics and any updates to the Implementing Regulation; feed lessons learned into Art. 21 measures. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No defined significant-incident classification or reporting path. | Ad-hoc response; deadlines unknown. |
| 2 | Managed | Art. 23 cascade documented; recipients and portal identified. | Runbook drafted; templates exist. |
| 3 | Defined | Threshold-mapped detection; 24 h/72 h/1-month workflow operational; recipient-notification playbook. | Classification logic live; drills started. |
| 4 | Quantitatively Managed | Metrics on time-to-report and classification accuracy; parallel GDPR/DORA triggers integrated. | KPIs on report timeliness; joint incident record. |
| 5 | Optimising | Continuous improvement; voluntary reporting/threat-sharing; audit-proven evidence trail. | Post-incident learning loop; independent assurance. |

# Audit Questions

1. How does the entity determine the moment of **"awareness"** that starts the 24 h / 72 h clocks, and is it timestamped and evidenced? *(Art. 23(4) [1].)*
2. How are incidents classified as **significant**, and (for covered entities) how are the Implementing Regulation (EU) 2024/2690 thresholds instrumented, including recurring-incident aggregation? *(Art. 23(3); Reg 2024/2690 [1][2].)*
3. Can the entity demonstrate delivery of the **early warning (≤ 24 h)**, **incident notification (≤ 72 h)**, **intermediate reports on request**, and **final report (≤ 1 month)**? *(Art. 23(4) [1].)*
4. If a **trust service provider**, is the **24 h** derogation applied to TSP-affecting incidents? *(Art. 23(4) [1].)*
5. How are **recipients of services** notified of significant incidents and cyber threats, and is this coordinated with contractual SLAs? *(Art. 23(1)–(2) [1].)*
6. How are **cross-border** incidents flagged for onward sharing with other Member States and ENISA? *(Art. 23(6) [1].)*
7. How are **parallel GDPR (Art. 33/34)** and **DORA (Art. 19)** duties triggered and run alongside NIS2, and how is Art. 35 cooperation handled for personal-data-breach incidents? *(Arts. 4, 35 [1]; [3]; [4].)*
8. What evidence would withstand **supervisory audit** of a reporting decision, including a decision not to report? *(Arts. 32–34 [1].)*

# Implementation Checklist

- [ ] CSIRT/competent authority, national portal and reporting format identified per Member State.
- [ ] Significant-incident classification encodes Art. 23(3) and (for covered entities) Reg 2024/2690 thresholds.
- [ ] Recurring-incident aggregation logic implemented (Reg 2024/2690 Art. 4).
- [ ] "Awareness" timestamping and evidence-preservation discipline in place.
- [ ] Early-warning (≤ 24 h) template and on-call routing operational.
- [ ] Incident-notification (≤ 72 h) template with severity/impact/IoCs.
- [ ] Intermediate-report path available on request; final-report (≤ 1 month) and progress-report templates ready.
- [ ] Trust-service-provider 24 h derogation handled where applicable.
- [ ] Recipient-of-services notification playbook aligned with contractual SLAs.
- [ ] Cross-border flagging (other Member States + ENISA) built into the flow.
- [ ] GDPR Art. 33/34 and DORA Art. 19 triggers integrated into a single intake; Art. 35 cooperation defined.
- [ ] Tabletop drills run against the 24 h / 72 h / 1-month clock; management-body oversight evidenced.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`). The Implementing Regulation (EU) 2024/2690 significant-incident thresholds were read from the EUR-Lex text on that date.*

## Primary Sources

- [1] **Directive (EU) 2022/2555 (NIS2 Directive)** — Art. 23 reporting obligations; Arts. 4, 30, 32–35. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj
- [2] **Commission Implementing Regulation (EU) 2024/2690** of 17 October 2024 — technical/methodological requirements for Art. 21(2) measures and **further specification of significant incidents** for DNS, TLD, cloud, data-centre, CDN, managed and managed-security service providers, online marketplaces/search engines/social-networking platforms and trust service providers (Arts. 3–14; recurring incidents Art. 4). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg_impl/2024/2690/oj
- [3] **Regulation (EU) 2016/679 (GDPR)** — Arts. 33–34 personal-data breach notification (parallel regime). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [4] **Regulation (EU) 2022/2554 (DORA)** — Arts. 17–19 ICT-related incident management, classification and reporting (lex specialis for financial entities under NIS2 Art. 4). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj

## Regulatory Guidance

- [5] **NIS2 Directive: securing network and information systems.** European Commission, Shaping Europe's Digital Future (reporting and risk-management overview). https://digital-strategy.ec.europa.eu/en/policies/nis2-directive
- [6] **NIS Directive 2 (NIS2) — topic page.** ENISA. https://www.enisa.europa.eu/topics/state-of-cybersecurity-in-the-eu/cybersecurity-policies/nis-directive-2
- [7] **NIS2 Technical Implementation Guidance** (cybersecurity risk-management measures aligned with the significant-incident parameters of Reg (EU) 2024/2690). ENISA. https://www.enisa.europa.eu/publications/nis2-technical-implementation-guidance
- [8] **EDPB Guidelines, Recommendations & Best Practices** (incl. personal-data breach notification guidance under GDPR Arts. 33–34). European Data Protection Board. https://www.edpb.europa.eu/our-work-tools/general-guidance/guidelines-recommendations-best-practices_en

## Standards

- [9] **ISO/IEC 27035-1:2023** — Information security incident management, Part 1: Principles and process (incident-handling lifecycle supporting the Art. 23 stages). ISO/IEC. https://www.iso.org/standard/78973.html
- [10] **NIST SP 800-61 Rev. 3** — Incident Response Recommendations and Considerations for Cybersecurity Risk Management. NIST. https://csrc.nist.gov/pubs/sp/800/61/r3/final

## Academic Sources

Not Applicable — this sub-topic relies on primary legislation (the Directive and its Implementing Regulation) and official regulatory/standards sources. Peer-reviewed analysis of incident-reporting effectiveness may be cited in future revisions.

# Further Reading

*Non-authoritative; provided for orientation only.*

- CSIRTs Network — the network of national CSIRTs designated under NIS2 (incident cooperation portal). https://csirtsnetwork.eu/
- European Commission — Cyber Resilience Act policy page (product-vulnerability reporting companion to entity incident reporting). https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act

# Related Documents

- `nis2-foundations` — parent reference; scope, entity classification, Art. 21 measures and the wider obligation set (this document details its Art. 23 material).
- `dora-foundations` — the financial-sector **lex specialis** incident regime (DORA Arts. 17–19); reported instead of NIS2 Art. 23 for financial entities.
- `gdpr-foundations` — parallel personal-data-breach regime (Art. 33/34); a security incident may trigger both.
- `cyber-resilience-act` — product-vulnerability/incident reporting for products with digital elements (companion, not substitute).
- `cybersecurity-foundations` — control frameworks (ISO/IEC 27001, NIST CSF) underpinning detection and response.
- `nis2-sectors` — Annex I/II sector-by-sector scope (planned).
- `nis2-transposition-tracker` — national reporting portals, formats and timing (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex primary text (Directive (EU) 2022/2555 Art. 23; Commission Implementing Regulation (EU) 2024/2690 Arts. 3–14) plus European Commission and ENISA guidance. **Significant-incident thresholds in Reg (EU) 2024/2690 live-verified on 2026-07-11** (financial loss > €500 000 or 5% turnover; service-specific availability/integrity thresholds; recurring-incident aggregation). Art. 23(4) cascade (24 h / 72 h / 1 month), the trust-service-provider 24 h derogation, and the Art. 23(5) CSIRT 24 h response confirmed against primary/authoritative sources. NIS2 vs GDPR vs DORA comparison built from Arts. 23/33-34/17-19. All 10 external links returned HTTP 200. | pending |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 3 human gate; frozen in release 0.14.0. | Human reviewer |
