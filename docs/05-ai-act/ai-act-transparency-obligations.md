---
id: ai-act-transparency-obligations
title: "EU AI Act: Transparency Obligations (Article 50)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: AI Act
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [ai-act-foundations, ai-act-prohibited-practices, ai-act-high-risk, ai-act-gpai, dsa-recommender-transparency, gdpr-foundations]
created: 2026-07-12
updated: 2026-07-12
review_due: 2027-07-12
confidence: High
supersedes: Not Applicable
tags: [ai-act, transparency, article-50, deepfake, synthetic-content, chatbot, emotion-recognition, biometric-categorisation, watermarking, c2pa, content-provenance, ai-office, digital-omnibus]
legal_basis: Regulation (EU) 2024/1689 (Article 50; Articles 3, 99, 113; Recitals 132–137)
sources_verified: 2026-07-12
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-act-transparency-obligations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.18.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-12 |
| Last Updated | 2026-07-12 |
| Review Due | 2027-07-12 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a Tier 2 **deep-dive** detailing Article 50 of the AI Act (the "limited/transparency-risk" tier introduced at overview level in `ai-act-foundations`); it does not repeat that overview and it is deliberately kept distinct from the **high-risk** transparency-to-deployer duty in Article 13 (a different obligation — see Scope). **Live-verification note:** Article 50 applies from the AI Act's **general application date of 2 August 2026** (Art. 113) [1]; the **"AI Omnibus"** simplification package — adopted by the European Parliament (16 June 2026) and the Council (29 June 2026) — **postpones the AI-content marking duties (Art. 50(2)/(4)) to 2 December 2026 for AI systems placed on the market before 2 August 2026**, a transitional grace rather than a change to the substantive rule [6][7][8]. Confirm the Official Journal citation for the Omnibus before relying on that transitional date.

# Executive Summary

**Article 50** of the EU AI Act (Regulation (EU) 2024/1689) is the operative provision of the Regulation's **transparency-risk tier**: it does not ban or heavily regulate the systems it covers, but requires that people are **told when they are dealing with, or looking at the output of, an AI system** [1][4]. It targets four situations: AI systems that **interact** with natural persons (e.g. chatbots); systems that **generate synthetic** audio, image, video or text; **emotion-recognition and biometric-categorisation** systems; and **deep fakes** and AI-generated **text on matters of public interest** [1]. The obligations are split between **providers** (Art. 50(1)–(2)) and **deployers** (Art. 50(3)–(4)) [1].

Two duties dominate the engineering agenda. First, **providers of generative AI must mark their outputs in a machine-readable format** as artificially generated or manipulated, using solutions that are "effective, interoperable, robust and reliable as far as technically feasible" (Art. 50(2)) [1]. The Act sets a **result**, not a technology: standards such as **C2PA / Content Credentials** and watermarking are best-practice means of meeting it, **not mandated** by the text [1][9][10]. Second, **deployers of deep-fake generators must disclose** that content is artificially generated or manipulated (Art. 50(4)), subject to **artistic/creative/satirical** and **law-enforcement** carve-outs and a lighter regime for **editorially-reviewed** content [1].

This document details each limb of Article 50, the **provider/deployer split**, the machine-readable-marking requirement and the standards landscape, the carve-outs, the manner/accessibility rule (Art. 50(5)), the **codes of practice and AI Office guidance** envisaged by Art. 50(7), the **penalty** for breach (up to **€15 million or 3%** of worldwide annual turnover under Art. 99(4)) [1], and the relationship to **GDPR** and **DSA** transparency [2][3]. The key timing point: Article 50 applies from **2 August 2026**, with a **narrow, pre-existing-systems marking postponement to 2 December 2026** under the adopted AI Omnibus [1][6][7][8].

# Key Takeaways

- **Article 50 is a disclosure regime, not a ban or a conformity regime.** It makes covered AI *usable* provided the right people are told the right thing at the right time; there is no conformity assessment and no CE marking attached to it [1][4]. *(Legal obligation.)*
- **Four triggers, split provider/deployer:** (1) provider — AI **interacting** with persons must disclose it is AI (50(1)); (2) provider — **synthetic** audio/image/video/text must be **machine-readable-marked** as artificial (50(2)); (3) deployer — **emotion-recognition/biometric-categorisation** systems must **inform exposed persons** (50(3)); (4) deployer — **deep fakes** and AI-generated **public-interest text** must be **disclosed** as artificial (50(4)) [1]. *(Legal obligation.)*
- **The marking duty sets a result, not a technology.** Art. 50(2) requires machine-readable, detectable marking "as far as technically feasible"; **C2PA/Content Credentials and watermarking are best practice, not legally mandated** — the AI Act is technology-neutral and points to codes of practice and standards to operationalise it [1][9][10]. *(Legal obligation as to result; standards are best practice.)*
- **The carve-outs are targeted, not general.** The interaction duty yields where AI use is **obvious** (50(1)); the deep-fake duty is lighter for **artistic/creative/satirical/fictional** works (disclose existence without spoiling the work) and does not apply to **editorially-reviewed** journalism, and there are **law-enforcement** exceptions across the limbs (50(1)–(4)) [1]. *(Legal obligation with statutory exceptions.)*
- **Disclosure must be clear, timely and accessible.** Information under 50(1) and (3) must be given "at the latest at the time of the first interaction or exposure", in a **clear and distinguishable** manner meeting **accessibility** requirements (Art. 50(5)) [1]. *(Legal obligation.)*
- **Codes of practice and AI Office guidance are the interpretive backstop.** Art. 50(7) tasks the **AI Office** with facilitating Union-level **codes of practice on detection and labelling** of artificially generated content; such a code is **forthcoming** and, when adopted, may be approved by Commission implementing act [1][5]. *(Regulatory mechanism — code not yet published.)*
- **Penalty is the middle tier.** Breach of Article 50 is an "other operator obligation" under **Art. 99(4)**: up to **€15,000,000 or 3%** of total worldwide annual turnover, whichever is higher — lower than the €35m/7% for prohibited practices, higher than nothing [1]. *(Legal obligation.)*
- **Article 50 ≠ Article 13.** Art. 50 is transparency **to end-users/affected persons**; the high-risk **Art. 13** transparency duty is **provider-to-deployer** (instructions for use). Do not conflate them — they cover different systems, different audiences and different content [1]. *(Legal obligation — scope distinction.)*
- **Timeline:** Article 50 applies from **2 August 2026** (Art. 113); the adopted **AI Omnibus** postpones the **marking** duties (50(2)/(4)) to **2 December 2026** only for systems **placed on the market before 2 August 2026** [1][6][7][8]. *(Legal obligation — confirm OJ citation for the transitional date.)*

# Purpose

This document supports three tasks the foundation document leaves open: (a) **classifying** a product against each Article 50 trigger and identifying whether the organisation carries the duty as a **provider** or a **deployer**; (b) **engineering** the two hard parts — clear AI-interaction disclosure and machine-readable marking/labelling of synthetic content — including the choice (not obligation) to adopt C2PA/watermarking; and (c) **placing Article 50 correctly among neighbouring regimes** — the high-risk Article 13 duty, the GDPR's automated-decision and information duties, and the DSA's platform-transparency rules. It is written for product, engineering, trust-and-safety, legal and compliance readers. It presupposes `ai-act-foundations` for the risk-tier overview and cross-refers `ai-act-high-risk`, `ai-act-gpai`, `dsa-recommender-transparency` and `gdpr-foundations`.

# Scope

**In scope:** Article 50(1)–(7) of Regulation (EU) 2024/1689 — the AI-interaction disclosure (50(1)), synthetic-content machine-readable marking (50(2)), emotion-recognition/biometric-categorisation notice (50(3)), deep-fake and public-interest-text disclosure (50(4)), the manner/timing/accessibility rule (50(5)), the without-prejudice clause (50(6)) and the codes-of-practice/AI-Office mechanism (50(7)); the relevant Art. 3 definitions (deep fake, emotion recognition, biometric categorisation); the standards landscape for marking (C2PA/Content Credentials, watermarking) as **best practice**; the Art. 99(4) penalty; the 2 August 2026 application date and the AI-Omnibus marking postponement; and the relationship to GDPR and DSA transparency.

**Out of scope (covered elsewhere):** The four-tier risk framework and timeline overview → `ai-act-foundations`; the **high-risk Article 13 transparency-to-deployer duty** (instructions for use, provider→deployer) and the Chapter III obligations generally → `ai-act-high-risk` — **this is a different obligation and is expressly not detailed here**; the GPAI provider transparency/documentation duties (Arts. 53, 55) → `ai-act-gpai`; the prohibited emotion-recognition and biometric uses (Art. 5) → `ai-act-prohibited-practices`; the DSA recommender/advertising transparency regime → `dsa-recommender-transparency`; GDPR transparency (Arts. 12–14) and automated-decision rules (Art. 22) → `gdpr-foundations`. Where covered AI processes personal data, the GDPR applies in parallel; this document does not restate GDPR duties.

**Assumptions:** The reader has read `ai-act-foundations`. "Provider", "deployer", "placing on the market" and "putting into service" bear their Art. 3 meanings. The AI-Omnibus marking-postponement date is an adopted-text date and becomes binding only on Official Journal publication.

# Definitions

*Shared terms (AI system, provider, deployer, remote biometric identification, prohibited AI practice) are in `GLOSSARY.md`. Only Article-50-specific terms are defined here, per sub-topic policy.*

| Term | Definition | Source |
|------|------------|--------|
| Deep fake | AI-generated or -manipulated image, audio or video content that resembles existing persons, objects, places, entities or events and would falsely appear to a person to be authentic or truthful (Art. 3(60)). | [1] |
| Emotion recognition system | An AI system for the purpose of identifying or inferring emotions or intentions of natural persons on the basis of their biometric data (Art. 3(39)). Its *use* in workplaces/education is separately prohibited (Art. 5); Art. 50(3) governs the notice duty where use is permitted. | [1] |
| Biometric categorisation system | An AI system assigning natural persons to specific categories on the basis of their biometric data, unless ancillary to another commercial service and strictly necessary for objective technical reasons (Art. 3(40)). | [1] |
| Synthetic content | Audio, image, video or text output that is artificially generated or manipulated by an AI system; the subject of the Art. 50(2) provider marking duty. | [1] |
| Machine-readable marking | A marking embedded in or attached to AI output that is detectable by automated means as artificially generated or manipulated, using solutions that are "effective, interoperable, robust and reliable as far as technically feasible" (Art. 50(2)). | [1] |
| Watermarking (AI content) | A technique embedding a signal (often imperceptible) into generated content to indicate its AI origin; a best-practice means of meeting Art. 50(2), not a legal requirement. | [1] |
| Content provenance (C2PA / Content Credentials) | Open technical specifications binding tamper-evident, cryptographically-signed metadata about an asset's origin and edit history; a best-practice means of meeting Art. 50(2) machine-readable marking, not mandated by the Act. | [9] |

# Background

The AI Act is **risk-based**: obligations scale with the threat an AI use poses to health, safety and fundamental rights [4]. Between the heavily-regulated **high-risk** tier and the unregulated **minimal-risk** tier sits a **transparency (or "limited") risk** category, addressed almost entirely by **Article 50** [1][4]. The rationale is informational asymmetry rather than direct harm: a person who does not know they are talking to a bot, or that an image is synthetic, cannot properly assess or contest what they see and hear. Article 50 therefore imposes a light-touch **duty to disclose**, leaving the underlying systems otherwise permitted [1][4]. Early academic analysis of the draft Act identified these transparency duties — particularly deep-fake labelling and bot disclosure — as a distinct, comparatively modest regulatory technique sitting apart from the prohibitions and the high-risk regime, and flagged the enforcement and definitional questions (what counts as a "deep fake", what is "obvious") that Article 50 would raise [11].

Article 50 sits in **Chapter IV** of the Regulation and applies from the **general application date of 2 August 2026** under Article 113 — after the prohibitions (2 February 2025) and the GPAI/governance provisions (2 August 2025), but before the main high-risk classification duty (2 August 2027) [1]. In late 2025 the Commission proposed the **"AI Omnibus"** simplification package (proposal of 19 November 2025), which the co-legislators adopted in June 2026 [6][7][8]. For transparency, its effect is narrow: it **postpones the machine-readable-marking duties to 2 December 2026 for AI systems already placed on the market before 2 August 2026**, giving pre-existing generators a short transitional runway; it does not weaken the substantive rule [6][7][8].

# Legal Framework

**OBLIGATION.** Transparency for certain AI systems is governed by **Article 50** (Chapter IV) of Regulation (EU) 2024/1689, read with the definitions in **Article 3** (deep fake, emotion recognition, biometric categorisation), the penalty rule in **Article 99(4)**, and the application-date rule in **Article 113** [1]. Article 50 allocates duties by role: **paragraphs (1)–(2) bind providers** (at the design/market-placement stage); **paragraphs (3)–(4) bind deployers** (at the use stage) [1]. Paragraph (5) sets the manner, timing and accessibility of disclosure; paragraph (6) is a **without-prejudice** clause preserving the Chapter III high-risk obligations and other Union/national transparency law; paragraph (7) establishes the **codes-of-practice / AI Office** mechanism [1].

Unlike the high-risk regime, Article 50 attaches **no conformity assessment, no CE marking and no registration** — the covered systems are lawful, and the only requirement is disclosure/marking done properly and in time [1]. Crucially, Article 50 is **distinct from Article 13**: Article 13 is a **high-risk** duty owed by a **provider to a deployer** (transparency and instructions for use so the deployer can operate the system correctly); Article 50 is owed to **end-users and affected natural persons** and covers a **different set of systems**. Conflating the two is a common and consequential error [1].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 50(1) | **Provider** duty: AI systems intended to **interact directly with natural persons** must be designed so persons are informed they are interacting with an AI system, **unless this is obvious** to a reasonably well-informed person; law-enforcement exception. | [1] |
| Art. 50(2) | **Provider** duty: providers of AI systems (incl. GPAI) generating **synthetic audio, image, video or text** must ensure outputs are **marked in a machine-readable format and detectable as artificially generated or manipulated**, with solutions "effective, interoperable, robust and reliable as far as technically feasible"; exceptions for assistive/editing functions not substantially altering input data, and for law-enforcement-authorised use. | [1] |
| Art. 50(3) | **Deployer** duty: deployers of an **emotion-recognition** or **biometric-categorisation** system must **inform the natural persons exposed** and process personal data per the GDPR/LED; law-enforcement exception. | [1][2] |
| Art. 50(4) | **Deployer** duty: deployers generating/manipulating **deep fakes** must **disclose** the content is artificially generated/manipulated; for AI-generated/manipulated **text published to inform the public on matters of public interest**, disclose unless human-reviewed under editorial responsibility. Carve-outs: **artistic/creative/satirical/fictional** works (disclosure limited so as not to hamper enjoyment); law enforcement. | [1] |
| Art. 50(5) | Information under (1) and (3) must be provided **at the latest at the time of the first interaction or exposure**, in a **clear and distinguishable** manner meeting the applicable **accessibility** requirements. | [1] |
| Art. 50(6) | Without prejudice to the **Chapter III (high-risk)** requirements and to other Union/national transparency obligations. | [1] |
| Art. 50(7) | The **AI Office** shall encourage and facilitate Union-level **codes of practice** on detection and labelling of artificially generated/manipulated content; the Commission may approve them (or set common rules) by **implementing act**. | [1][5] |
| Art. 3(39),(40),(60) | Definitions of emotion recognition system, biometric categorisation system, and deep fake. | [1] |
| Art. 99(4) | Penalty for breach of Art. 50 (an "other operator" obligation): up to **€15,000,000 or 3%** of total worldwide annual turnover, whichever is higher. | [1] |
| Art. 113 | Application dates — Chapter IV (incl. Art. 50) applies from the **general date, 2 August 2026**. | [1] |

## Relevant Recitals

*Recitals are not binding but aid construction (Art. 296 TFEU practice); this is stated expressly.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 132 area | Rationale for AI-interaction disclosure (Art. 50(1)) — natural persons should be aware they are interacting with an AI system, taking account of vulnerable persons; the "obvious" exception. | [1] |
| Recital 133 area | Marking of synthetic content (Art. 50(2)) — variety of techniques (watermarks, metadata, cryptographic provenance, logs, fingerprints); interoperability and technical feasibility; technology-neutrality. | [1] |
| Recital 134 area | Deep-fake and public-interest-text disclosure (Art. 50(4)); the artistic/creative-work proportionate-disclosure limb. | [1] |
| Recital 135 area | Codes of practice and AI Office facilitation of detection/labelling; support for enforceable, harmonised solutions (Art. 50(7)). | [1][5] |
| Recital 136 area | Relationship of Art. 50 transparency to the high-risk regime and to other Union transparency law (Art. 50(6)); no lowering of other obligations. | [1] |

## Relevant Case Law

**Not Applicable — no CJEU case law yet.** Article 50 does not apply until 2 August 2026, so no judgment has interpreted it; open-textured terms ("obvious", "deep fake", "matters of public interest", "as far as technically feasible") are as yet untested. Interpretive weight currently rests on the Regulation's text and recitals, forthcoming AI Office codes of practice and guidance [5], and — for the personal-data dimension of Art. 50(3) — GDPR case law (see `gdpr-foundations`). Revisit once AI Office guidance and enforcement practice emerge. [1][5]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **Commission framework page:** presents Article 50 as the **"transparency risk"** tier — for AI such as chatbots and generative systems, providers/deployers must ensure end-users **know when they are interacting with or viewing AI-generated content** (bots identified, deep fakes labelled) [4]. *(Regulatory interpretation.)*
- **Technology-neutral marking:** the Commission and the Act frame Art. 50(2) as a **result-based** duty. The recitals list several acceptable techniques — **watermarks, metadata identifiers, cryptographic provenance, logging, fingerprints** — without mandating any; the operative constraint is "as far as technically feasible", acknowledging that no marking method is yet fully robust to removal [1][4]. *(Regulatory interpretation — no specific standard is mandated.)*
- **AI Office role (Art. 50(7)):** the **AI Office** is charged with facilitating Union-level **codes of practice on detection and labelling** of artificially generated content, working with providers and standards bodies; such a code is a **forthcoming** deliverable and, when adopted, may be given effect by Commission implementing act [1][5]. Organisations should track it as the primary operational reference for compliant marking. *(Regulatory mechanism — code not yet published; treat as forthcoming.)*
- **Standardisation:** the AI Act's transparency duties are among the areas addressed by the **CEN-CENELEC** harmonised-standards work; watermarking/provenance solutions such as **C2PA / Content Credentials** are being adopted across industry as a practical means of meeting Art. 50(2), but they are **voluntary best practice**, not a legal mandate [9][10]. *(Regulatory interpretation / standards.)*
- **AI Omnibus (adopted):** the co-legislators **postponed the Art. 50(2)/(4) marking duties to 2 December 2026 for systems placed on the market before 2 August 2026** — a transitional easing for pre-existing generators, not a substantive change; adopted by Parliament (16 Jun 2026) and Council (29 Jun 2026), pending OJ publication [6][7][8]. *(Legal obligation — pending OJ publication; verify OJ citation. Detailed in `ai-act-foundations`.)*

# Technical Considerations

Article 50 raises two genuinely different engineering problems — **disclosure** (telling a person something clearly and in time) and **marking** (embedding a durable, machine-readable signal in generated content). The following addresses each limb.

- **(50(1)) AI-interaction disclosure.** Design chatbots, voice assistants and AI "companions" so the user is told they are dealing with an AI **at or before the first interaction** (Art. 50(5)) [1]. The duty yields only where AI use is **obvious** to a reasonably well-informed person — a high bar in consumer contexts; when in doubt, disclose. *(Legal obligation.)* **BEST PRACTICE:** a persistent, plain-language label ("You're chatting with an AI assistant") rather than a buried notice; account for vulnerable users and accessibility (Art. 50(5)).
- **(50(2)) Machine-readable marking of synthetic content — result, not technology.** Providers of generative systems must mark audio/image/video/**text** outputs so they are **detectable by automated means** as AI-generated/manipulated, using solutions "effective, interoperable, robust and reliable as far as technically feasible" [1]. The Act **does not name a technology**; candidate techniques include **C2PA/Content Credentials** (signed provenance metadata), **watermarking** (in-content signals, incl. text watermarking), cryptographic hashing/fingerprinting and logging [1][9]. *(Legal obligation as to result.)* **BEST PRACTICE:** adopt an **interoperable provenance standard (C2PA)** plus watermarking for robustness, track the forthcoming AI Office code of practice and CEN-CENELEC standards, and document the "technically feasible" judgement where marking is imperfect (e.g. short text) [1][9][10].
- **Text marking is the hard case.** Robust, tamper-resistant marking of **short text** outputs is not yet a solved problem; the "as far as technically feasible" qualifier is doing real work here [1]. *(Interpretation.)* **BEST PRACTICE:** apply provenance metadata where the delivery channel supports it, and record the limits of available text-watermarking rather than treating the duty as unmeetable.
- **(50(3)) Notice for emotion-recognition/biometric-categorisation.** Where such a system is deployed (and not otherwise prohibited under Art. 5), inform exposed persons **before exposure** and ensure a GDPR basis for the biometric processing [1][2]. *(Legal obligation.)*
- **(50(4)) Deep-fake and public-interest-text disclosure.** Attach a clear disclosure to synthetic media; for AI-generated public-interest **text**, disclose unless a human under editorial responsibility reviewed it [1]. *(Legal obligation.)* **BEST PRACTICE:** pair the human-facing disclosure with machine-readable provenance so the two duties (50(2) marking + 50(4) disclosure) are met by one pipeline.
- **Detection and downstream re-use.** Marking is only useful if platforms and tools can **read** it; interoperability (Art. 50(2)) is the point. Align with DSA-platform provenance efforts and provenance-preserving edit chains [1][3]. *(Best practice.)*

# Hosting Considerations

- **Role determines duty.** A host that merely runs infrastructure is usually neither provider nor deployer; but offering a **branded generative feature** can make an organisation a **provider** (Art. 50(2) marking) and operating such a system in a service can make it a **deployer** (Art. 50(4) disclosure) [1]. *(Legal obligation — assess role per feature.)*
- **Provenance must survive the pipeline.** Hosting/CDN/transcoding stages should be configured to **preserve** C2PA/provenance metadata and watermarks rather than strip them on re-encode or resize, or the marking duty is defeated in practice [1][9]. *(Best practice.)*
- **No conformity/registration overhead.** Unlike high-risk hosting, Art. 50 adds **no logging, conformity-assessment or registration** duty — the obligation is limited to disclosure/marking done correctly and in time [1]. *(Legal obligation — proportionate.)*

# Game Hosting Considerations

- **AI companions and NPC chat.** Conversational AI characters and AI "companions" that interact with players engage **Art. 50(1)** — players should be told they are talking to an AI at first interaction, in a clear and accessible way, with special care for **minors** [1]. *(Legal obligation.)*
- **Generative in-game content.** AI-generated art, voice, video or text produced by in-game or platform tools engages the **Art. 50(2)** provider marking duty and, for deep-fake-style output, the **Art. 50(4)** disclosure duty; wire provenance/marking into the generation pipeline [1][9]. *(Legal obligation.)*
- **Do not conflate with the Art. 5 line.** Emotion-recognition/biometric features on players may be **prohibited** (Art. 5) rather than merely transparency-regulated; screen against `ai-act-prohibited-practices` first, then apply Art. 50(3) notice only to *permitted* uses [1]. *(Legal obligation — sequence the analysis.)*

# AI Considerations

*This document is itself an AI-regulation deep-dive; the "AI Considerations" here concern interaction with adjacent AI and platform regimes.*

- **GDPR runs in parallel.** Art. 50(3) expressly requires GDPR/LED compliance for the biometric processing, and where any covered system processes personal data the GDPR's own **transparency (Arts. 12–14)** and **automated-decision (Art. 22)** duties apply **in addition** to Art. 50 — Art. 50 is a disclosure-of-AI duty, not a substitute for a lawful basis or GDPR information duties [1][2]. *(Legal obligation.)*
- **GPAI overlap.** Art. 50(2) applies to providers of **generative GPAI** systems; the GPAI provider transparency/documentation duties (Arts. 53, 55) are separate and additional — see `ai-act-gpai` [1]. The AI Office's Art. 50(7) content-labelling code of practice is distinct from the Art. 56 GPAI Code of Practice [1][5]. *(Legal obligation — keep the two codes distinct.)*
- **DSA transparency is a different axis.** The **DSA** requires **platform-level** transparency — recommender-parameter disclosure (Art. 27), ad repositories (Art. 39), non-profiling recommender options (Art. 38) — owed by online platforms, not the AI-origin disclosure Art. 50 requires of providers/deployers [1][3]. They stack: a platform hosting AI-generated content may owe **both** DSA platform duties and (as a deployer) Art. 50(4) disclosure — see `dsa-recommender-transparency` [1][3]. *(Legal obligation — cumulative, not alternative.)*
- **Art. 13 is not Art. 50.** The high-risk **Art. 13** transparency-to-deployer duty (instructions for use) is provider→deployer and belongs to `ai-act-high-risk`; it is not an end-user disclosure and must not be substituted for Art. 50 [1]. *(Legal obligation — scope distinction.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Classify every AI feature against the four Art. 50 triggers** (interaction / synthetic generation / emotion-recognition-or-categorisation / deep-fake-or-public-text) and record whether you carry the duty as **provider** (50(1)–(2)) or **deployer** (50(3)–(4)). *(OBLIGATION from 2 Aug 2026.)* [1]
2. **Implement clear AI-interaction disclosure** for chatbots/assistants/companions, shown **at or before first interaction**, in a clear, distinguishable, accessible manner (Art. 50(5)), unless AI use is genuinely obvious. *(OBLIGATION.)* [1]
3. **Build machine-readable marking into every generative pipeline** — treat Art. 50(2) as a **result** to achieve, adopt an **interoperable provenance standard (C2PA/Content Credentials)** and, where feasible, watermarking; document the "technically feasible" limits, especially for short text. *(OBLIGATION as to result; standards are BEST PRACTICE.)* [1][9][10]
4. **Attach deep-fake and public-interest-text disclosure** (Art. 50(4)), applying the **artistic/creative** proportionate-disclosure limb and the **editorial-responsibility** exception deliberately and on the record. *(OBLIGATION where triggered.)* [1]
5. **For emotion-recognition/biometric-categorisation, inform exposed persons and secure a GDPR basis** — but first confirm the use is not **prohibited** under Art. 5. *(OBLIGATION; screen against `ai-act-prohibited-practices` first.)* [1][2]
6. **Preserve provenance across hosting/CDN/edit chains** so marking is not stripped downstream. *(BEST PRACTICE grounded in the Art. 50(2) result.)* [1][9]
7. **Track the AI Office content-labelling code of practice (Art. 50(7)) and CEN-CENELEC standards** and align marking to them as they publish. *(BEST PRACTICE.)* [1][5][10]
8. **Do not confuse Art. 50 with Art. 13 or the DSA** — map each obligation to its audience (end-user vs deployer vs platform) so none is missed or double-counted. *(EDITORIAL RECOMMENDATION.)* [1][3]
9. **Plan to 2 August 2026, and treat the 2 December 2026 marking postponement as applying only to pre-existing systems** — new generators placed on the market from 2 August 2026 mark from day one. *(EDITORIAL RECOMMENDATION — confirm OJ citation.)* [1][6][7][8]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Chatbot/assistant deployed without AI-interaction disclosure | Medium | Medium | Art. 50(1); Art. 99(4) (€15m/3%) [1] | Persistent first-interaction AI label; accessibility-checked | Low |
| R2 | Generative outputs not machine-readable-marked | Medium | Medium | Art. 50(2) [1] | Provenance (C2PA) + watermarking in pipeline; document feasibility | Low |
| R3 | Treating a specific technology (e.g. C2PA) as legally mandated, or none as sufficient | Medium | Low | Result-based duty; technology-neutral [1][9] | Meet the *result*; record standard chosen and feasibility limits | Low |
| R4 | Deep fake/public-interest text published without disclosure | Medium | Medium | Art. 50(4) [1] | Disclosure UI + provenance; editorial-review log for the text exception | Low |
| R5 | Emotion-recognition/categorisation notice given, but the use is actually prohibited (Art. 5) | Low | Very High | Art. 5 / Art. 50(3) [1] | Screen against Art. 5 before applying Art. 50(3); legal sign-off | Low |
| R6 | Provenance/watermark stripped by hosting/transcoding | Medium | Medium | Art. 50(2) interoperability [1][9] | Provenance-preserving CDN/edit config; re-sign on transform | Medium |
| R7 | Confusing Art. 50 with Art. 13 (high-risk) — wrong audience, missed duty | Medium | Medium | Arts. 13, 50 [1] | Obligation-to-audience mapping; distinct workstreams | Low |
| R8 | Missing Art. 50 as a GDPR/DSA substitute (under-compliance) | Medium | High | Parallel/cumulative application [1][2][3] | Joint AI + GDPR + DSA transparency mapping | Low |
| R9 | Relying on the exact Omnibus marking date before OJ publication | Medium | Low | AI Omnibus adopted 29 Jun 2026 [6][7][8] | Plan to 2 Aug 2026; track OJ; treat 2 Dec 2026 as pre-existing-only | Low |

# Implementation Roadmap

- **Phase 0 — Classify & assign role:** Inventory AI features; map each to Art. 50(1)–(4) and to provider/deployer role. *Effort:* Low–Medium.
- **Phase 1 — Interaction disclosure:** Ship clear, accessible AI-interaction labels for all conversational/interactive AI (Art. 50(1), (5)). *Effort:* Low.
- **Phase 2 — Marking pipeline:** Integrate C2PA/Content Credentials and watermarking into generation; document feasibility limits (Art. 50(2)). *Effort:* Medium–High.
- **Phase 3 — Disclosure UX:** Deep-fake/public-interest-text disclosure with the artistic and editorial carve-outs handled on the record (Art. 50(4)). *Effort:* Medium.
- **Phase 4 — Emotion/categorisation notice:** After Art. 5 screening, add exposed-person notice and GDPR basis (Art. 50(3)). *Effort:* Medium.
- **Phase 5 — Standards & monitoring:** Align to the AI Office code of practice and CEN-CENELEC standards as published; provenance preservation across hosting; watch OJ for the Omnibus dates. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No Art. 50 classification; AI interactions/outputs unlabelled. | No disclosure or marking. |
| 2 | Managed | Ad-hoc chatbot labels; some deep-fake disclosure. | Partial 50(1)/50(4) coverage. |
| 3 | Defined | Every AI feature classified by trigger and role; interaction disclosure and content marking implemented; feasibility limits documented. | Classification register; marking in pipelines. |
| 4 | Quantitatively Managed | Provenance preserved end-to-end; disclosure UX tested for clarity/accessibility; emotion/categorisation notices post-Art. 5 screen. | Provenance metrics; accessibility tests; Art. 5 gate. |
| 5 | Optimising | Aligned to AI Office code of practice and CEN-CENELEC standards; integrated with GDPR and DSA transparency; monitored for OJ/date changes. | Standards alignment; unified transparency programme. |

# Audit Questions

1. Is every AI feature classified against Art. 50(1)–(4), with provider/deployer role recorded? *(Art. 50; applies 2 Aug 2026 [1].)*
2. Do interactive AI systems disclose they are AI at or before first interaction, clearly and accessibly? *(Art. 50(1), (5) [1].)*
3. How is synthetic output marked in a machine-readable, detectable format, and how are "technically feasible" limits documented? *(Art. 50(2) [1][9].)*
4. Is the marking approach technology-neutral (result met) rather than assuming a mandated standard or that none suffices? *(Art. 50(2) [1][9].)*
5. Are deep fakes and AI-generated public-interest text disclosed, with the artistic and editorial-responsibility carve-outs applied on the record? *(Art. 50(4) [1].)*
6. For emotion-recognition/biometric-categorisation, are exposed persons informed and is a GDPR basis in place — and was the use screened against Art. 5 first? *(Art. 50(3); Art. 5 [1][2].)*
7. Is provenance/marking preserved across hosting, CDN and edit chains? *(Art. 50(2) interoperability [1][9].)*
8. Are Art. 50, Art. 13 (high-risk) and DSA transparency duties mapped to their distinct audiences so none is missed or conflated? *(Arts. 13, 50; DSA [1][3].)*
9. Is the programme tracking the AI Office Art. 50(7) code of practice and the OJ publication of the AI Omnibus dates? *(Art. 50(7) [1][5][6][7][8].)*

# Implementation Checklist

- [ ] Every AI feature classified against Art. 50(1)–(4) with provider/deployer role assigned.
- [ ] AI-interaction disclosure shipped for all interactive AI (Art. 50(1), (5)).
- [ ] Machine-readable marking (C2PA/provenance + watermarking) integrated into generative pipelines; feasibility limits documented (Art. 50(2)).
- [ ] Deep-fake and public-interest-text disclosure implemented, with artistic/editorial carve-outs recorded (Art. 50(4)).
- [ ] Emotion-recognition/categorisation notice + GDPR basis, after Art. 5 screening (Art. 50(3)).
- [ ] Provenance/marking preserved across hosting/CDN/edit chains.
- [ ] Art. 50 vs Art. 13 vs DSA transparency mapped by audience; no conflation.
- [ ] AI Office code-of-practice and CEN-CENELEC standards watch established.
- [ ] Timeline planned to 2 Aug 2026; 2 Dec 2026 marking postponement treated as pre-existing-systems only (OJ pending).

# References

*All external links verified live on 2026-07-12 (`sources_verified`) using `curl` with a browser user-agent. The Council of the EU press release corroborating the 29 June 2026 final adoption is authoritative but its site (consilium.europa.eu) bot-blocks automated requests (HTTP 403); the same facts are cited via the European Parliament source [7], which verifies HTTP 200.*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act)** — full text incl. **Art. 50** (transparency obligations), Arts. 3(39)/(40)/(60), 99(4), 113 and Recitals 132–137. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [2] **Regulation (EU) 2016/679 (GDPR)** — parallel application to personal-data processing under Art. 50(3) and to AI systems generally. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [3] **Regulation (EU) 2022/2065 (Digital Services Act)** — platform-level transparency (recommenders, ads) that stacks with, and is distinct from, Art. 50. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2065/oj

## Regulatory Guidance

- [4] **Regulatory framework on AI / AI Act** (the "transparency risk" tier — chatbots identified, deep fakes labelled). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai
- [5] **The AI Office** (body charged under Art. 50(7) with facilitating codes of practice on detection/labelling of AI-generated content). European Commission. https://digital-strategy.ec.europa.eu/en/policies/ai-office
- [6] **Digital Omnibus on AI — regulation proposal** (Commission proposal of 19 Nov 2025; postpones Art. 50(2)/(4) marking to 2 Dec 2026 for pre-existing systems). European Commission. https://digital-strategy.ec.europa.eu/en/library/digital-omnibus-ai-regulation-proposal
- [7] **AI Act: EP approves simplification measures and "nudifier" app ban** (European Parliament plenary adoption, 16 June 2026; simplification package incl. the AI-content-marking postponement). European Parliament press release. https://www.europarl.europa.eu/news/en/press-room/20260611IPR45207/ai-act-ep-approves-simplification-measures-and-nudifier-app-ban
- [8] **Artificial Intelligence: Council gives final green light to simplify and streamline rules** (Council of the EU final adoption, 29 June 2026; enters into force on the third day after OJ publication). Council of the EU. https://www.consilium.europa.eu/en/press/press-releases/2026/06/29/artificial-intelligence-council-gives-final-green-light-to-simplify-and-streamline-rules/

## Standards

- [9] **C2PA — Coalition for Content Provenance and Authenticity (Content Credentials)** — open technical specifications for tamper-evident content provenance; a best-practice (not mandated) means of meeting Art. 50(2) machine-readable marking. C2PA. https://c2pa.org/
- [10] **CEN-CENELEC — Artificial Intelligence (AI Act harmonised standards work programme).** CEN-CENELEC. https://www.cencenelec.eu/areas-of-work/cen-cenelec-topics/artificial-intelligence/

## Academic Sources

- [11] **Veale, M. & Zuiderveen Borgesius, F. (2021), "Demystifying the Draft EU Artificial Intelligence Act" — Computer Law Review International 22(4), 97–112.** Situates the transparency duties (bot disclosure, deep-fake labelling) as a distinct regulatory technique and flags their definitional/enforcement questions. Open-access preprint, arXiv:2107.03721. https://arxiv.org/abs/2107.03721 *(Analyses the draft text; article numbering and detail were revised in the final Regulation — cite alongside [1].)*

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- Article 50: Transparency Obligations for Providers and Deployers — annotated text and recitals (artificialintelligenceact.eu). https://artificialintelligenceact.eu/article/50/
- EU Artificial Intelligence Act — Implementation Timeline (Future of Life Institute). https://artificialintelligenceact.eu/implementation-timeline/
- European Commission — "Navigating the AI Act" FAQ. https://digital-strategy.ec.europa.eu/en/faqs/navigating-ai-act

# Related Documents

- `ai-act-foundations` — the AI Act overview, risk tiers, penalties and timeline; this deep-dive **details its transparency-tier / Article 50 material** (**prerequisite reading**).
- `ai-act-prohibited-practices` — the Art. 5 bans on emotion recognition/biometric categorisation that must be screened **before** applying the Art. 50(3) notice duty.
- `ai-act-high-risk` — the **Article 13** transparency-to-deployer duty (a different obligation) and the Chapter III regime preserved by Art. 50(6).
- `ai-act-gpai` — GPAI provider transparency/documentation duties (Arts. 53, 55) and the distinct Art. 56 GPAI Code of Practice.
- `dsa-recommender-transparency` — platform-level DSA transparency that stacks with, and is distinct from, Art. 50.
- `gdpr-foundations` — parallel GDPR transparency (Arts. 12–14) and automated-decision (Art. 22) duties engaged by covered systems.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-12 | Technical Writer (virtual agent) | Initial draft. Deep-dive on AI Act **Article 50** transparency obligations: the four triggers and the **provider (50(1)–(2)) / deployer (50(3)–(4))** split; the machine-readable-marking **result** (Art. 50(2)) with **C2PA/watermarking as best practice, not mandated**; the manner/timing/accessibility rule (50(5)); the without-prejudice clause (50(6)); and the **codes-of-practice / AI Office** mechanism (50(7), code forthcoming). Article 3 definitions (deep fake, emotion recognition, biometric categorisation), the **Art. 99(4)** penalty (€15m/3%), the **Art. 13 vs Art. 50** distinction, and the GDPR/DSA relationships covered. **Live-verified:** Art. 50 applies from the general date **2 August 2026** (Art. 113, confirmed against primary source); the adopted **AI Omnibus** (EP 16 Jun 2026; Council 29 Jun 2026) postpones the marking duties to **2 December 2026 for systems placed on the market before 2 August 2026** — OJ publication pending. All external links checked on 2026-07-12 (consilium.europa.eu bot-blocks curl; 29 Jun facts corroborated via EP source [7]). | — |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster D, residual list); full-repo validator/link/lint suite green; frozen in release 0.18.0. | Orchestrator (QA-verified) |
