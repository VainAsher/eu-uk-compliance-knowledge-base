---
id: privacy-threat-modelling
title: "Privacy Threat Modelling (LINDDUN)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: Privacy Engineering
document_type: guidance
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [privacy-engineering-foundations, dpia-methodology, pets-catalogue, gdpr-foundations, ai-act-foundations]
tags: [privacy-threat-modelling, linddun, linddun-go, linddun-pro, linddun-maestro, stride, dfd, article-25, article-35, privacy-by-design, dpia, privacy-engineering]
legal_basis: Regulation (EU) 2016/679, Articles 25 & 35
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | privacy-threat-modelling |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.16.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**.

# Executive Summary

**Privacy threat modelling** is the systematic, design-stage activity of identifying, analysing and mitigating the ways a system can harm the privacy of the people whose data it processes — before that system is built. It is to *privacy* what security threat modelling (STRIDE) is to *security*: a structured elicitation method run over a model of the system, most often a **data-flow diagram (DFD)** [7][10]. The dominant, most mature method is **LINDDUN**, developed by the imec-DistriNet group at KU Leuven and recognised by NIST as a resource in the NIST Privacy Framework repository [2][7][12].

LINDDUN is an acronym for **seven privacy threat categories**: **L**inking, **I**dentifying, **N**on-repudiation, **D**etecting, **D**ata Disclosure, **U**nawareness (and Unintervenability), and **N**on-compliance [8][12]. Each category is the negation of a corresponding privacy property (e.g. *linkability* negates *unlinkability*; *identifying* negates *anonymity*), so eliciting the threat and selecting its mitigation are two sides of one design decision [12]. The method ships in three variants of increasing rigour: **LINDDUN GO** (a lightweight, card-based team brainstorming approach), **LINDDUN PRO** (a systematic, DFD-and-interaction-based analysis), and **LINDDUN MAESTRO** (an enriched, threat-specific architecture-model approach published in 2025) [7][9][14].

Three conclusions dominate. First, privacy threat modelling and security threat modelling are **complementary, not interchangeable**: STRIDE finds confidentiality/integrity/availability threats to the *system*, LINDDUN finds privacy threats to the *data subject* — including threats (linking, identifying, non-repudiation, detecting) that arise even when security is perfect [7][10][12]. Second, LINDDUN is **best practice, not a legal obligation** — but it directly operationalises two GDPR obligations that *are* binding: **data protection by design (Article 25)** and the **risk-assessment step of a DPIA (Article 35(7)(c))** [1]. Third, its output is only useful if it **feeds downstream artefacts**: mitigations should map to concrete PETs and to Hoepman's privacy design strategies, and the threat list should populate the DPIA risk register [3][15]. This document sets out the method, the variants, the STRIDE comparison, a worked mini-example, and the mapping into DPbDD and the DPIA.

# Key Takeaways

- **Privacy threat modelling** systematically elicits privacy harms from a system model (typically a DFD) at design time; **LINDDUN** is the most established method and is listed by **NIST** as a Privacy Framework resource [2][7][12]. *(Best practice.)*
- LINDDUN's **seven categories** — Linking, Identifying, Non-repudiation, Detecting, Data Disclosure, Unawareness (& Unintervenability), Non-compliance — each negate a **privacy property**, tying threat elicitation to mitigation [8][12]. *(Best practice / academic.)*
- LINDDUN splits into **hard-privacy** threats (Linking, Identifying, Non-repudiation, Detecting, Data Disclosure — about minimising data and exposure) and **soft-privacy** threats (Unawareness & Unintervenability, Non-compliance — about transparency, control and lawful governance) [8][12]. *(Best practice.)*
- Three variants exist: **LINDDUN GO** (lightweight card deck, low expertise), **LINDDUN PRO** (systematic DFD/per-interaction analysis), **LINDDUN MAESTRO** (enriched, threat-specific system model, 2025) [7][9][14]. *(Best practice.)*
- **LINDDUN differs from STRIDE**: STRIDE targets security properties (spoofing, tampering, repudiation, information disclosure, DoS, elevation) of the *system*; LINDDUN targets privacy properties for the *data subject*, catching threats that persist even in a perfectly secure system [7][10][12]. *(Best practice.)*
- Privacy threat modelling is **not itself a legal obligation**, but it is a recognised means of discharging **data protection by design (GDPR Art. 25)** and of performing the **risk assessment (Art. 35(7)(c))** inside a DPIA [1][5]. *(Best practice grounded in obligation.)*
- The method's **mitigations map to PETs and to Hoepman's privacy design strategies** (minimise, hide, separate, aggregate, inform, control, enforce, demonstrate), giving a repeatable path from threat to control [3][15]. *(Best practice.)*
- Threat-modelling output should **feed the DPIA**: LINDDUN threats become the identified risks scored for likelihood and severity under Art. 35(7)(c), and the mitigations become the Art. 35(7)(d) measures [1][6]. *(Best practice grounded in obligation.)*
- Privacy threat modelling belongs **in the SDLC** as a repeatable design-gate activity, re-run when the system or its data flows change — mirroring the "review on change" logic of Art. 25 and Art. 35(11) [1][4]. *(Best practice.)*

# Purpose

This document gives privacy, engineering, product and security teams an **evidence-based method** for finding privacy threats before they are built into a product, using LINDDUN, and for turning the results into compliance evidence. It supports three decisions: (a) *how* to run a privacy threat-modelling session and which LINDDUN variant to choose; (b) *how* the results map to PETs, Hoepman strategies and mitigations; and (c) *how* to feed those results into a DPIA (Art. 35) and into data protection by design (Art. 25). It is the threat-modelling layer beneath `privacy-engineering-foundations` and it supplies the risk step that `dpia-methodology` and `pets-catalogue` refer to.

# Scope

**In scope:** The discipline of privacy threat modelling and how it differs from security threat modelling (STRIDE); the LINDDUN framework and its seven threat categories; the LINDDUN GO / PRO / MAESTRO variants; the method steps (model the system with a DFD, elicit threats per category, prioritise, select mitigations); the mapping of LINDDUN output to PETs and to Hoepman's privacy design strategies; integration into a DPIA (Art. 35) and into privacy-by-design (Art. 25); a comparison table (LINDDUN vs STRIDE); a worked mini-example; and SDLC integration.

**Out of scope (covered elsewhere or in the backlog):** The DPbDD and Art. 32 obligations in general → `privacy-engineering-foundations`; the full DPIA process, screening and prior consultation → `dpia-methodology`; the technique-by-technique PET catalogue that mitigations draw on → `pets-catalogue`; anonymisation and re-identification-risk assessment → `anonymisation-techniques` (planned); the identifiability test for personal data → `gdpr-foundations`; general security threat modelling and secure-SDLC practice → `cybersecurity-foundations` (planned).

**Assumptions:** The reader has read `gdpr-foundations` (personal data, principles, accountability) and `privacy-engineering-foundations` (DPbDD, TOMs, Hoepman strategies, the PET concept). "Personal data", "pseudonymisation", "DPbDD", "PET", "DPIA" and "differential privacy" carry their `GLOSSARY.md` meanings.

# Definitions

*Shared terms (personal data, pseudonymisation, PET, DPbDD, DPIA, differential privacy) are defined in `GLOSSARY.md`. Only threat-modelling-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Privacy threat modelling | The systematic elicitation and analysis of potential privacy threats at the level of a system-model representation, to identify and mitigate them at design time. | [12][14] |
| LINDDUN | A privacy threat-modelling methodology and knowledge base (imec-DistriNet, KU Leuven) whose acronym names seven privacy threat categories. | [7][12] |
| Data-flow diagram (DFD) | A model of a system as external entities, processes, data stores and data flows crossing trust boundaries — the standard abstraction over which LINDDUN and STRIDE elicit threats. | [7][10] |
| Privacy property | A desirable privacy goal (e.g. unlinkability, anonymity, plausible deniability, undetectability, confidentiality, content awareness, policy/consent compliance); each LINDDUN category is the *negation* of such a property. | [12] |
| Hard-privacy threat | A LINDDUN threat about minimising data and exposure to adversaries — Linking, Identifying, Non-repudiation, Detecting, Data Disclosure. | [8][12] |
| Soft-privacy threat | A LINDDUN threat about the data subject's transparency, control and lawful governance — Unawareness & Unintervenability, Non-compliance (assumes an honest-but-imperfect controller). | [8][12] |
| Threat tree / threat-type catalogue | LINDDUN's reusable knowledge of how each threat category typically manifests, used to guide elicitation. | [7][12] |
| Mitigation strategy | A mapping from an identified privacy threat to a taxonomy of privacy-enhancing solutions (PETs) and design tactics that counter it. | [3][12][15] |
| LINDDUN GO | The lightweight, card-deck variant for structured team brainstorming, requiring minimal expertise. | [7][9][13] |
| LINDDUN PRO | The systematic variant that analyses each interaction between DFD elements against each threat category. | [7][10] |
| LINDDUN MAESTRO | The 2025 variant that enriches the system model with threat-specific abstractions for more guided, reproducible analysis. | [7][14] |

# Background

Threat modelling began in **security engineering**. Microsoft's **STRIDE** (Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege) formalised, from the late 1990s, the idea of walking a data-flow diagram element by element and asking what could go wrong for each category of threat [10]. STRIDE is powerful for security, but it is blind to a whole class of harms: a system can be perfectly secure — no spoofing, no tampering, no unauthorised disclosure — and still be a privacy disaster, because it *links* a person's actions across contexts, *identifies* them from supposedly anonymous data, makes their behaviour *detectable*, or leaves them *unaware* of what is happening to their data [12].

**LINDDUN** was created to fill that gap. Introduced by **Deng, Wuyts, Scandariato, Preneel and Joosen (2011)** in *Requirements Engineering*, it deliberately mirrored STRIDE's DFD-driven, per-category approach but replaced security threats with **privacy** threats, each defined as the negation of a **privacy property** drawn from the privacy-by-design and anonymity-terminology literature [12]. The original seven categories were **Linkability, Identifiability, Non-repudiation, Detectability, Disclosure of information, Unawareness, and Non-compliance**. The framework has since been maintained and modernised at **linddun.org**: the categories are now expressed as activities/gerunds (**Linking, Identifying, Non-repudiation, Detecting, Data Disclosure, Unawareness & Unintervenability, Non-compliance**), and the method has been packaged into three variants — **GO** (2020), the systematic **PRO**, and the enriched **MAESTRO** (2025) — to suit different levels of expertise and rigour [8][9][13][14]. LINDDUN is now referenced by **NIST** (Privacy Framework resource repository), **ISO/IEC 27550** on privacy engineering and other bodies as a leading privacy-threat-modelling approach [2][7][12].

# Legal Framework

Privacy threat modelling is a **methodology**, not a legal instrument: no GDPR article names LINDDUN or requires threat modelling by that name. Its legal relevance is that it is a recognised **means of complying** with two binding obligations [1]:

- **Article 25 — data protection by design and by default (DPbDD):** the controller must implement appropriate technical and organisational measures, *taking account of the risks of varying likelihood and severity for the rights and freedoms of natural persons*, to implement the data-protection principles effectively and integrate the necessary safeguards **from the design stage** [1]. Identifying those risks systematically is precisely what privacy threat modelling does; it is a structured way to *find* the risks Article 25 tells you to design against [1][5].
- **Article 35 — data protection impact assessment (DPIA):** where processing is likely to result in a high risk, the DPIA must contain "an assessment of the **risks to the rights and freedoms** of data subjects" (Art. 35(7)(c)) and "the **measures envisaged** to address the risks" (Art. 35(7)(d)) [1]. A LINDDUN analysis is a direct, auditable way to produce both — the threats are the risks; the mitigations are the measures (see `dpia-methodology`) [1][6].
- **Article 5 principles and Article 24 (controller responsibility):** the categories map onto Article 5 principles — data minimisation (Art. 5(1)(c)), integrity and confidentiality (Art. 5(1)(f)), lawfulness/transparency (Arts. 5(1)(a), 12–14) — so an elicited threat can be traced to the principle it endangers [1].

The obligations are **Article 25 and Article 35**; LINDDUN is the **best-practice technique** by which a controller discharges them. That distinction is preserved throughout this document with visible claim labels.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 5(1)(a) | Lawfulness, fairness and transparency — endangered by *Unawareness* and *Non-compliance* threats. | [1] |
| Art. 5(1)(c) | Data minimisation — endangered by *Linking*, *Identifying*, *Detecting*, *Data Disclosure* threats. | [1] |
| Art. 5(1)(f) | Integrity and confidentiality — overlaps with *Data Disclosure* (and with STRIDE information disclosure). | [1] |
| Art. 5(2) | Accountability — the threat-model record is accountability evidence. | [1] |
| Art. 24 | Controller's duty to implement risk-appropriate measures, reviewed and updated. | [1] |
| Art. 25(1) | Data protection by design — implement safeguards against identified risks from the design stage. | [1] |
| Art. 25(2) | Data protection by default — minimise amount, extent, retention, accessibility. | [1] |
| Art. 30 | Records of processing — the data inventory the DFD/threat model draws on. | [1] |
| Art. 32 | Security of processing — the *Data Disclosure* category and the STRIDE overlap live here. | [1] |
| Art. 35(7)(c) | DPIA risk assessment — populated by the elicited privacy threats. | [1] |
| Art. 35(7)(d) | DPIA mitigation measures — populated by the selected mitigations. | [1] |
| Art. 35(11) | Review the DPIA when risk changes — re-run the threat model on material change. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the articles above.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 75 | Illustrates the kinds of risk to rights and freedoms (discrimination, identity theft, loss of confidentiality, re-identification, profiling) that threat modelling seeks to surface. | [1] |
| Recital 76 | Risk should be assessed on an objective basis by reference to likelihood and severity — the two axes used to prioritise elicited threats. | [1] |
| Recital 78 | DPbDD examples — minimising processing, pseudonymising as soon as possible, transparency, enabling monitoring — align with LINDDUN mitigations. | [1] |
| Recital 84 | A DPIA should evaluate the origin, nature, particularity and severity of the risk — the output of a threat model. | [1] |
| Recital 90 | The DPIA should assess the risks and determine measures to mitigate them — the LINDDUN threat-to-mitigation step. | [1] |

## Relevant Case Law

Not Applicable — privacy threat modelling is an engineering **methodology**, elaborated through academic literature, the LINDDUN project and standards rather than through a distinct line of judgments. Case law bearing on the *substance* the method addresses — the meaning of personal data and identifiability (*Breyer*, C-582/14; *Nowak*, C-434/16) and automated decision-making (*SCHUFA*, C-634/21) — is treated in `gdpr-foundations`. [1]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **NIST** lists LINDDUN in the **NIST Privacy Framework** resource repository as a method that "provides support to systematically elicit and mitigate privacy threats in software architectures", mapping it to the Framework's risk-assessment subcategories (ID.RA-P) and noting the existence of the lighter **LINDDUN GO** variant [2]. This positions privacy threat modelling as an implementation technique for the *Identify* function of a recognised privacy-risk-management framework. *(Standards/regulatory interpretation.)*
- **ENISA**, in its privacy-by-design and **data-protection-engineering** work, situates privacy threat modelling among the engineering methods that bridge legal policy and system design, and treats the systematic identification of privacy risks as a building block of "privacy by design — from policy to engineering" [3][4]. *(Regulatory / technical guidance.)*
- The **EDPB Guidelines 4/2019 on Article 25** require that DPbDD measures be **effective** and grounded in an assessment of the risks to data subjects, implemented before processing and reviewed continually — a structured privacy threat model is a defensible way to evidence that the risk assessment underpinning DPbDD was actually done [5]. *(Regulatory interpretation.)*
- The **ICO's DPIA guidance** frames the DPIA as identifying and assessing risks to individuals and the measures to reduce them; a LINDDUN analysis is a recognised technique for producing the risk and measures content the ICO expects [6]. *(Regulatory interpretation.)*
- Consistent across these sources: privacy threat modelling is treated as **good engineering practice that operationalises accountability**, not as a standalone legal requirement — the obligation remains Articles 25 and 35 [1][2][5]. *(Regulatory interpretation of a legal obligation.)*

# Technical Considerations

This section sets out the method: the seven categories, the STRIDE contrast, the three variants, the method steps, and the mapping to PETs and Hoepman strategies.

## The seven LINDDUN categories (and the privacy property each negates)

Each category is the **negation of a privacy property**; eliciting the threat and choosing the mitigation are one decision [12]. The current (linddun.org) naming is given first, with the original 2011 term in brackets [8][12]:

| # | Category (current / original) | Privacy property negated | The threat, in one line |
|---|-------------------------------|--------------------------|-------------------------|
| L | **Linking** (Linkability) | Unlinkability | Data or actions can be associated to learn more about an individual or group. |
| I | **Identifying** (Identifiability) | Anonymity / pseudonymity | The identity behind data can be revealed. |
| N | **Non-repudiation** | Plausible deniability | A subject can be proven to have done/said something they should be able to deny. |
| D | **Detecting** (Detectability) | Undetectability / unobservability | The mere existence of a subject's data or action can be discerned (even without content). |
| D | **Data Disclosure** (Disclosure of information) | Confidentiality | Personal data is exposed to, or collected by, those who should not have it. |
| U | **Unawareness & Unintervenability** (Unawareness) | Content awareness / intervenability | The subject is unaware of, or unable to intervene in (access, correct, delete, object to), processing of their data. |
| N | **Non-compliance** | Policy & consent compliance | Processing does not conform to legal, regulatory or the controller's own policy requirements. |

LINDDUN groups the first five as **hard-privacy** threats (about minimising data and resisting adversaries) and the last two as **soft-privacy** threats (about transparency, control and lawful governance, assuming an honest-but-imperfect controller) [8][12].

## How privacy threat modelling differs from security threat modelling (STRIDE)

Both walk a **DFD** and elicit threats per category — the general threat-modelling process (define the system, identify threats, mitigate, validate) is common to both [11] — but they protect different things [7][10][12]:

- **STRIDE protects the system's security properties** for the *asset owner*: authentication (vs Spoofing), integrity (vs Tampering), non-repudiation (vs Repudiation), confidentiality (vs Information disclosure), availability (vs Denial of service), authorisation (vs Elevation of privilege) [10].
- **LINDDUN protects privacy properties for the *data subject*** — including harms that survive perfect security. Even a system with flawless STRIDE hygiene can *link* a user across sessions, *identify* them from quasi-identifiers, deny them *plausible deniability*, make their presence *detectable*, or leave them *unaware* and *unable to intervene* [12].
- They **overlap at one point**: LINDDUN *Data Disclosure* and STRIDE *Information disclosure* both concern confidentiality — but LINDDUN scopes it to *personal* data and the subject's interest, while STRIDE scopes it to any sensitive asset [12]. Note also the **inversion of "non-repudiation"**: in STRIDE non-repudiation is a *desired* security property (you *want* to prevent repudiation); in LINDDUN non-repudiation is a *threat* (a subject may need *plausible deniability*, e.g. a whistle-blower) [10][12].

A full comparison table is in *Operational Guidance* below.

## The three variants: GO, PRO, MAESTRO

The LINDDUN project ships three methods of increasing rigour and required expertise [7]:

- **LINDDUN GO** — a **lightweight, card-based** approach. A deck of cards represents the most common privacy threats with prompts and hotspots; a mixed team runs a structured brainstorming session over a lightweight system sketch. Low expertise, low adoption cost; ideal for early-stage or cross-functional teams and for building privacy awareness [7][9][13].
- **LINDDUN PRO** — a **systematic** approach built on a full **DFD**. Each **interaction** between DFD elements (source, flow, destination, data store) is examined against each applicable threat category using LINDDUN's threat-type knowledge, giving broad, reproducible coverage; supports both manual analysis and tool automation. Higher expertise and effort [7][10].
- **LINDDUN MAESTRO** — the **most advanced** approach (introduced 2025). It enriches the system description with **threat-specific abstractions**, so the analysis for each threat type is guided by exactly the model information relevant to it; the result is more focused, reproducible and less dependent on analyst assumptions. Validated on an industrial IoT home-automation case [7][14].

Editorial guidance: start with **GO** to build coverage and shared understanding, then apply **PRO** (or **MAESTRO**) to high-risk components where exhaustive, auditable coverage is needed for a DPIA. *(Editorial recommendation.)* [7][14]

## The method steps

Across variants, LINDDUN follows the same skeleton [7][12]:

1. **Model the system** — build a DFD: external entities, processes, data stores, data flows, and trust boundaries. The Article 30 records and existing architecture artefacts are the natural input [1][7].
2. **Elicit threats per category** — for each relevant element/interaction (PRO/MAESTRO) or each card (GO), ask whether each of the seven categories applies, using LINDDUN's threat-type catalogue/threat trees as prompts [7][12].
3. **Prioritise** — assess each candidate threat for **likelihood and severity** (Recital 76 axes), discard non-applicable ones, and rank the rest so effort goes to the highest risks [1][12].
4. **Select mitigations** — map each retained threat to a mitigation from LINDDUN's taxonomy of privacy-enhancing solutions, i.e. to **PETs** and design tactics (see next subsection) [3][12][15].
5. **Document and feed downstream** — record threats, decisions and residual risk, and feed them into the DPIA (Art. 35) and the DPbDD design (Art. 25) [1][6].

## Mapping mitigations to PETs and Hoepman strategies

LINDDUN's mitigation step connects naturally to the two other pillars of `privacy-engineering-foundations` — **Hoepman's eight privacy design strategies** and the **PET catalogue** [3][15]:

| LINDDUN threat | Primary Hoepman strategy | Illustrative PETs / tactics | Cross-ref |
|----------------|--------------------------|-----------------------------|-----------|
| Linking | Minimise, Separate, Aggregate | Pseudonymisation, unlinkable pseudonyms, data separation, aggregation, differential privacy | `pets-catalogue` |
| Identifying | Minimise, Aggregate, Hide | Anonymisation, k-anonymity, differential privacy, pseudonymisation | `pets-catalogue` |
| Non-repudiation | Hide, Minimise | Plausible-deniability designs, off-the-record protocols, avoid unnecessary non-repudiable logs | `pets-catalogue` |
| Detecting | Hide, Aggregate | Dummy traffic, constant-rate/padded traffic, unobservable storage/communication | `pets-catalogue` |
| Data Disclosure | Hide, Enforce | Encryption (in transit/at rest/in use), access control, TEEs, SMPC, homomorphic encryption | `pets-catalogue` |
| Unawareness & Unintervenability | Inform, Control | Transparency notices, privacy dashboards, consent and preference management, rights tooling (access/erasure/objection) | `privacy-engineering-foundations` |
| Non-compliance | Demonstrate, Enforce | Policy enforcement, retention automation, logging, DPIA, records of processing | `dpia-methodology` |

This preserves the "threat ↔ property ↔ strategy ↔ PET" chain that makes the output actionable and auditable [3][15].

# Hosting Considerations

- **Model the real infrastructure, not an idealised one** — the DFD must reflect actual hosting facts (regions, sub-processors, data stores, admin access paths) or the elicitation misses *Data Disclosure* and *Detecting* threats introduced by the platform itself; obtain the technical facts from the provider (processor assistance, `dpia-methodology`) [1][4]. *(Best practice grounded in Art. 32.)*
- **Trust boundaries are hosting boundaries** — each crossing into a cloud tenant, a managed service or a third-party API is a place to test every category; co-tenancy and provider administrative access are classic *Data Disclosure* hotspots addressed by encryption, key custody and TEEs (see `pets-catalogue`) [1]. *(Best practice.)*
- **Telemetry and logs are privacy threats too** — hosting/observability stacks that centralise logs and metrics create *Linking*, *Detecting* and *Non-repudiation* exposures; apply *minimise*/*hide* (sampling, pseudonymised identifiers, retention limits) [15]. *(Best practice.)*
- **Re-run on architecture change** — a migration, new region or new sub-processor changes the DFD and therefore the threat model; treat it as an Art. 35(11) trigger to re-run [1]. *(Best practice grounded in obligation.)*

# Game Hosting Considerations

- **Player telemetry is a linking/identifying magnet** — high-volume behavioural telemetry, matchmaking and analytics readily enable *Linking* and *Identifying* of players across sessions and titles; model these flows and mitigate with pseudonymised player IDs, aggregation and differential privacy on published metrics (leaderboards, heatmaps) [12][15]. *(Best practice grounded in Art. 25(2).)*
- **Detecting and presence data** — "online now", friend-presence and voice features create *Detecting* threats (a player's mere activity is observable); apply *hide*/*aggregate* and privacy-protective presence defaults, especially for likely-child users (see `game-hosting-foundations`, `uk-gdpr-foundations`) [12]. *(Best practice.)*
- **Non-repudiation vs anti-cheat** — anti-cheat and moderation want strong, non-repudiable evidence, which is in direct tension with the *Non-repudiation* privacy threat; threat modelling makes that trade-off explicit and scoped rather than accidental [12]. *(Best practice.)*
- **Unawareness for younger players** — children are less able to understand or intervene in processing; the *Unawareness & Unintervenability* category maps directly to Children's-Code transparency and control expectations [12]. *(Best practice grounded in Art. 25.)*

# AI Considerations

- **AI amplifies hard-privacy threats** — training and inference over personal data intensify *Linking*, *Identifying* and *Detecting* (e.g. re-identification, membership inference, model inversion); privacy threat modelling of the ML pipeline (data collection → training → inference → logging) surfaces these before deployment [12][14]. *(Best practice.)*
- **Model updates and models as attack surface** — federated-learning updates and trained models can leak training data; a LINDDUN pass over the pipeline flags where DP, secure aggregation or SMPC are needed (see `pets-catalogue`) [12][15]. *(Best practice.)*
- **MAESTRO and enriched models suit AI systems** — the threat-specific, model-enriched MAESTRO approach is well suited to complex AI architectures where generic DFDs under-specify the analysis [14]. *(Best practice.)*
- **Threat model feeds both the DPIA and the AI Act FRIA** — for AI processing personal data, the same elicited privacy threats populate the GDPR DPIA (Art. 35) and inform the AI Act Art. 27 fundamental-rights impact assessment; run them off one shared model (see `dpia-methodology`, `ai-act-foundations`) [1]. *(Best practice grounded in obligation.)*
- **Automated decision-making** — *Non-compliance* and *Unawareness & Unintervenability* threats map onto Art. 22 safeguards (human oversight, contest/appeal); model them explicitly for scoring/profiling features [1]. *(Best practice grounded in obligation.)*

# Operational Guidance

Labels: **OBLIGATION** (must, per statute) / **BEST PRACTICE** (should, per method/standards/regulators) / **EDITORIAL RECOMMENDATION** (we suggest).

**A. Run privacy threat modelling as a design-stage activity.**

1. **Build a DFD of the processing** — entities, processes, data stores, flows, trust boundaries; reuse the RoPA and architecture docs. *(BEST PRACTICE; supports the Art. 35(7)(a) "systematic description".)* [1][7]
2. **Choose the variant to the risk** — **GO** for early/cross-functional coverage and awareness; **PRO/MAESTRO** for exhaustive, auditable coverage of high-risk components. *(BEST PRACTICE / EDITORIAL RECOMMENDATION.)* [7][14]
3. **Elicit all seven categories** — force consideration of Linking, Identifying, Non-repudiation, Detecting, Data Disclosure, Unawareness & Unintervenability, Non-compliance for each relevant element/interaction. *(BEST PRACTICE.)* [12]

**B. Prioritise and mitigate.**
4. **Prioritise by likelihood and severity** — the Recital 76 axes; discard non-applicable threats with a recorded reason. *(BEST PRACTICE grounded in Art. 35 [1].)* [1][12]
5. **Map each threat to a mitigation** — to a Hoepman strategy and a concrete PET/tactic, with an owner and a residual-risk rating. *(BEST PRACTICE.)* [3][15]
6. **Do not treat a PET as a discharge of accountability** — record the residual risk; a mitigation reduces risk, it does not by itself prove compliance (see `pets-catalogue`). *(BEST PRACTICE grounded in Art. 5(2) [1].)* [1]

**C. Feed downstream and sustain.**
7. **Feed the DPIA** — the elicited threats become the Art. 35(7)(c) risks; the mitigations become the Art. 35(7)(d) measures. *(OBLIGATION to produce the DPIA content; BEST PRACTICE for using LINDDUN to do it.)* [1][6]
8. **Feed data protection by design** — carry mitigations into requirements, architecture and default settings (Art. 25). *(OBLIGATION for DPbDD; BEST PRACTICE for the technique.)* [1][5]
9. **Embed in the SDLC and review on change** — a design-gate activity, re-run when the system or data flows change (mirrors Art. 35(11)). *(BEST PRACTICE grounded in obligation.)* [1][4]

**Comparison: LINDDUN vs STRIDE.**

| Dimension | STRIDE (security) | LINDDUN (privacy) |
|-----------|-------------------|-------------------|
| Protects | The system / asset owner | The data subject |
| Property focus | Security (CIA + authN/authZ, non-repudiation) | Privacy (unlinkability, anonymity, plausible deniability, undetectability, confidentiality, awareness, compliance) |
| Categories | Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege | Linking, Identifying, Non-repudiation, Detecting, Data Disclosure, Unawareness & Unintervenability, Non-compliance |
| Model used | DFD, per element/interaction | DFD, per element/interaction (GO uses lightweight sketches) |
| "Non-repudiation" | A **desired** property (prevent repudiation) | A **threat** (subject may need plausible deniability) |
| Overlap | Information disclosure | Data Disclosure (personal data) |
| Legal hook (EU/UK) | GDPR Art. 32 (security) | GDPR Art. 25 (DPbDD) and Art. 35 (DPIA risk step) |
| Variants | STRIDE-per-element, STRIDE-per-interaction | LINDDUN GO, LINDDUN PRO, LINDDUN MAESTRO |
| Origin | Microsoft (late 1990s) | Deng et al., KU Leuven (2011) |

*Sources: STRIDE [10]; LINDDUN [7][8][12][14]; legal hooks [1].*

**Worked mini-example (illustrative).**

Consider a mobile fitness app with a **"friends nearby"** feature. Simplified DFD: *User device* → (location updates) → *Location service (process)* → *Location store (data store)*; *Friend device* → (nearby query) → *Location service*; *Analytics pipeline* reads the store. Running LINDDUN:

- **Linking** — persistent user IDs on every location update let the operator (or a breach) build a movement profile and link it across features. *Mitigation:* rotating pseudonyms, separate identifiers from location payloads (*minimise/separate*) [15].
- **Identifying** — home/work locations plus timing re-identify a user even without a name. *Mitigation:* coarsen/aggregate location; add spatial noise (differential privacy) for analytics (*aggregate*) [15].
- **Non-repudiation** — a non-repudiable log of "was at location X at time T" removes a user's plausible deniability. *Mitigation:* do not retain fine-grained non-repudiable location logs; minimise retention (*hide/minimise*) [15].
- **Detecting** — the "nearby" response reveals a friend's mere presence/activity. *Mitigation:* mutual-consent presence, coarse proximity buckets, dummy responses (*hide*) [12].
- **Data Disclosure** — location store or transit exposed to unauthorised parties. *Mitigation:* encryption in transit/at rest, strict access control (Art. 32) (*hide/enforce*) [1][15].
- **Unawareness & Unintervenability** — users unaware their location feeds analytics, or unable to turn it off/delete it. *Mitigation:* clear notice, granular opt-in default-off, dashboard with delete/disable (*inform/control*; Arts. 12–14, 25(2)) [1][15].
- **Non-compliance** — no lawful basis or retention policy for the analytics use. *Mitigation:* lawful basis, retention automation, record in the DPIA (*demonstrate/enforce*) [1][6].

Prioritising by likelihood/severity puts *Identifying*, *Data Disclosure* and *Unawareness & Unintervenability* top; the resulting threats and mitigations drop straight into the DPIA risk register (Art. 35(7)(c)/(d)) and the DPbDD design (Art. 25) [1][6]. *(Illustrative — not a substitute for a full DPIA.)*

# Risk Register

*Risks here are risks to the effectiveness of the privacy-threat-modelling activity itself (and thus to Art. 25/35 compliance).*

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | **No privacy threat modelling** — relying on STRIDE/security review only, missing linking/identifying/awareness harms | High | High | Art. 25 [1]; LINDDUN rationale [12] | Add LINDDUN to design gates; train teams | Low |
| R2 | **Inaccurate/stale DFD** — model does not reflect real data flows/hosting | Medium | High | Art. 35(7)(a) [1] | Reuse RoPA; version the DFD; re-model on change | Low |
| R3 | **Categories skipped** — soft-privacy (Unawareness/Non-compliance) ignored in favour of hard-privacy | Medium | Medium | LINDDUN completeness [8][12] | Force all seven categories; use GO cards/PRO checklist | Low |
| R4 | **Threats elicited but not mitigated** — findings not carried into design/DPIA | Medium | High | Art. 25, 35(7)(d) [1] | Owner + residual rating per threat; link to backlog | Low |
| R5 | **PET treated as compliance** — mitigation assumed to discharge accountability | Medium | Medium | Art. 5(2) [1]; `pets-catalogue` | Record residual risk; PET is a control not proof | Low |
| R6 | **One-off exercise** — not re-run when system/data flows change | High | Medium | Art. 35(11) [1] | SDLC trigger on change; periodic cadence | Medium |
| R7 | **Wrong variant for the risk** — GO used alone for high-risk processing needing exhaustive coverage | Medium | Medium | LINDDUN methods [7][14] | Escalate high-risk components to PRO/MAESTRO | Low |
| R8 | **Output not auditable** — no record linking threats to measures | Medium | Medium | Art. 5(2) [1] | Structured template; store with the DPIA | Low |

# Implementation Roadmap

- **Phase 0 — Foundations:** Train teams on privacy vs security threat modelling; adopt the LINDDUN GO deck; agree DFD conventions and a threat-model template. *Effort:* Low–Medium.
- **Phase 1 — Pilot:** Run LINDDUN GO on one or two in-flight features; capture threats→mitigations→residual risk; feed a live DPIA. *Effort:* Medium.
- **Phase 2 — SDLC integration:** Add a privacy-threat-modelling design gate; trigger on new/changed processing; define when to escalate to LINDDUN PRO. *Effort:* Medium.
- **Phase 3 — Systematic coverage:** Apply LINDDUN PRO (and MAESTRO for complex/AI systems) to high-risk components; enable tool support. *Effort:* High.
- **Phase 4 — Mitigation library:** Build a reusable threat→Hoepman-strategy→PET mapping and standard mitigations (see `pets-catalogue`). *Effort:* Medium.
- **Phase 5 — Assurance:** Metrics (coverage, mitigation closure, re-model currency); integrate with DPIA/FRIA; periodic review. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No privacy threat modelling; privacy risks found late or via security review only. | No DFDs; ad hoc privacy review. |
| 2 | Managed | LINDDUN GO used occasionally on some features; results not consistently actioned. | Some card sessions; partial mitigation. |
| 3 | Defined | Privacy threat modelling in the SDLC; all seven categories elicited; threats→mitigations recorded and fed to DPIAs. | Design gate; template; DPIA linkage. |
| 4 | Quantitatively Managed | LINDDUN PRO on high-risk components; metrics on coverage and mitigation closure; re-model on change. | KPIs; PRO/tool use; change triggers. |
| 5 | Optimising | MAESTRO/enriched models for complex and AI systems; reusable mitigation library; continuous assurance and DPIA/FRIA integration. | Threat-specific models; mitigation library; audit. |

# Audit Questions

1. Do you perform **privacy** threat modelling (not only security), and which method/variant (LINDDUN GO/PRO/MAESTRO)? *(Art. 25 [1][7].)*
2. Show a **DFD** and the elicitation covering **all seven** LINDDUN categories for a recent high-risk feature. *(LINDDUN completeness [8][12].)*
3. How were threats **prioritised** by likelihood and severity, and how were non-applicable ones justified? *(Recital 76 [1].)*
4. For each retained threat, what **mitigation** (Hoepman strategy / PET) was chosen, with owner and residual risk? *(Art. 25; `pets-catalogue` [1][15].)*
5. How does the threat-model output **feed the DPIA** risk and measures sections? *(Art. 35(7)(c)/(d) [1][6].)*
6. How is privacy threat modelling **triggered in the SDLC** and **re-run** when the system changes? *(Art. 35(11) [1].)*
7. For AI systems, how does the pipeline threat model inform both the **DPIA and the AI Act FRIA**? *(Art. 35 [1]; `ai-act-foundations`.)*
8. Where is the threat-model **record** kept as accountability evidence? *(Art. 5(2) [1].)*

# Implementation Checklist

- [ ] DFD produced for the processing (entities, processes, stores, flows, trust boundaries), reusing the RoPA.
- [ ] LINDDUN variant chosen to the risk (GO for coverage/awareness; PRO/MAESTRO for exhaustive high-risk analysis).
- [ ] All seven categories elicited for each relevant element/interaction (Linking, Identifying, Non-repudiation, Detecting, Data Disclosure, Unawareness & Unintervenability, Non-compliance).
- [ ] Threats prioritised by likelihood and severity; non-applicable threats recorded with reasons.
- [ ] Each retained threat mapped to a Hoepman strategy and a concrete PET/tactic, with owner and residual risk.
- [ ] Threats and mitigations fed into the DPIA (Art. 35(7)(c)/(d)) and into DPbDD design/defaults (Art. 25).
- [ ] Privacy threat modelling embedded as an SDLC design gate, triggered on new/changed processing.
- [ ] Threat-model record retained as accountability evidence and linked to the DPIA and RoPA.
- [ ] Re-model scheduled/triggered when the system, hosting or data flows change.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Articles 5, 24, 25, 30, 32, 35 and Recitals 75, 76, 78, 84, 90. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj

## Regulatory Guidance

- [2] **LINDDUN privacy threat modeling framework** (Privacy Framework Resource Repository — LINDDUN mapped to the ID.RA-P risk-assessment subcategories). NIST. https://www.nist.gov/privacy-framework/linddun-privacy-threat-modeling-framework
- [3] **Privacy and Data Protection by Design — from policy to engineering.** ENISA. https://www.enisa.europa.eu/publications/privacy-and-data-protection-by-design
- [4] **Data Protection Engineering.** ENISA (2022). https://www.enisa.europa.eu/publications/data-protection-engineering
- [5] **Guidelines 4/2019 on Article 25 — Data Protection by Design and by Default** (v2.0). European Data Protection Board (EDPB). https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-42019-article-25-data-protection-design-and_en
- [6] **Data Protection Impact Assessments (DPIAs).** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/data-protection-impact-assessments-dpias/

## Standards

*The LINDDUN project (imec-DistriNet, KU Leuven) is the authoritative, community-maintained methodology reference; treated here as a methodological framework alongside recognised standards. Microsoft STRIDE is the reference security-threat-modelling model.*

- [7] **LINDDUN Methods — GO, PRO and MAESTRO.** imec-DistriNet, KU Leuven. https://linddun.org/methods/
- [8] **The LINDDUN framework and the seven privacy threat types.** imec-DistriNet, KU Leuven. https://linddun.org/linddun/
- [9] **LINDDUN GO.** imec-DistriNet, KU Leuven. https://linddun.org/go/
- [10] **The STRIDE Threat Model.** Microsoft (Learn / archived guidance). https://learn.microsoft.com/en-us/previous-versions/commerce-server/ee823878(v=cs.20)
- [11] **Threat Modeling Process.** OWASP Foundation. https://owasp.org/www-community/Threat_Modeling_Process

## Academic Sources

- [12] **Deng, M., Wuyts, K., Scandariato, R., Preneel, B., Joosen, W. (2011). "A privacy threat analysis framework: supporting the elicitation and fulfillment of privacy requirements."** Requirements Engineering 16(1), 3–32. Springer. https://doi.org/10.1007/s00766-010-0115-7
- [13] **Wuyts, K., Sion, L., Joosen, W. (2020). "LINDDUN GO: A Lightweight Approach to Privacy Threat Modeling."** 2020 IEEE European Symposium on Security and Privacy Workshops (EuroS&PW), 302–309. https://doi.org/10.1109/EuroSPW51379.2020.00047
- [14] **Van Landuyt, D., Sion, L., Wuyts, K., Joosen, W. (2025). "LINDDUN MAESTRO: an architecture framework for privacy threat modeling."** Software and Systems Modeling. Springer. https://doi.org/10.1007/s10270-025-01342-w
- [15] **Hoepman, J.-H. (2014). "Privacy Design Strategies."** IFIP SEC 2014, Springer; arXiv:1210.6621. https://arxiv.org/abs/1210.6621

# Further Reading

*Non-authoritative; provided for orientation only.*

- LINDDUN PRO tutorial (v0). imec-DistriNet, KU Leuven. https://downloads.linddun.org/tutorials/pro/v0/tutorial.pdf
- LINDDUN — Why use LINDDUN. https://linddun.org/linddun/whyuselinddun/

# Related Documents

- `privacy-engineering-foundations` — **parent**; DPbDD (Art. 25), TOMs, Hoepman strategies and the PET concept (**prerequisite reading**).
- `dpia-methodology` — the DPIA whose risk (Art. 35(7)(c)) and measures (Art. 35(7)(d)) steps LINDDUN populates.
- `pets-catalogue` — the PETs that LINDDUN mitigations map to.
- `gdpr-foundations` — personal data, identifiability, Art. 5 principles.
- `ai-act-foundations` — the Art. 27 FRIA that shares inputs with the DPIA for AI systems.
- `anonymisation-techniques` — anonymisation/re-identification analysis feeding Identifying/Linking mitigations (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Arts. 5, 24, 25, 30, 32, 35; Recitals 75, 76, 78, 84, 90), NIST Privacy Framework LINDDUN resource, ENISA privacy-by-design/data-protection-engineering, EDPB Guidelines 4/2019, ICO DPIA guidance, the LINDDUN project (GO/PRO/MAESTRO methods and framework pages), Microsoft STRIDE, OWASP, and the peer-reviewed LINDDUN literature (Deng et al. 2011; Wuyts et al. 2020 LINDDUN GO; Van Landuyt et al. 2025 LINDDUN MAESTRO; Hoepman 2014). Current seven-category naming and the three variants live-verified against linddun.org. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster B); full-repo validator/link/lint suite green; frozen in release 0.16.0. | Orchestrator (QA-verified) |
