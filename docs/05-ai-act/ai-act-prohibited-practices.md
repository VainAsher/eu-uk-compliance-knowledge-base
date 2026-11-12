---
id: ai-act-prohibited-practices
title: "EU AI Act: Prohibited Practices (Article 5)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: AI Act
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [ai-act-foundations, ai-act-high-risk, ai-act-gpai, gdpr-foundations, digital-omnibus]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [ai-act, prohibited-practices, article-5, unacceptable-risk, biometric, social-scoring, emotion-recognition, remote-biometric-identification, nudifier, csam, ai-omnibus]
legal_basis: Regulation (EU) 2024/1689 (Article 5; Articles 4, 99, 113; Recitals 28–46)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-act-prohibited-practices |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.14.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a Tier 2 **deep-dive** that details, article-by-article, the Article 5 material introduced at overview level in `ai-act-foundations`; it does not repeat that overview. **Live-verification note:** the Article 5 prohibitions have applied since **2 February 2025** [1][4]; the Commission's non-binding **Guidelines on prohibited AI practices** (C(2025) 884 final, 4 Feb 2025) interpret them [3]; and the **"AI Omnibus"** simplification package — **adopted** by the European Parliament (16 June 2026) and the Council (29 June 2026) — **adds a new Article 5 prohibition** on AI systems that generate or manipulate **non-consensual intimate imagery (NCII)** and **AI-generated child sexual abuse material (CSAM)** ("nudifier" ban), to apply from **2 December 2026**, subject to a safe harbour for adequate technical safeguards [6][7][8]. Confirm the Official Journal citation for the Omnibus before relying on its exact dates.

# Executive Summary

Article 5 of the EU AI Act (Regulation (EU) 2024/1689) is the Regulation's **red line**: it defines the AI practices whose risk to health, safety and fundamental rights is deemed **unacceptable**, and therefore **prohibits** them outright rather than permitting them subject to controls [1]. Unlike the high-risk regime, there is **no conformity-assessment route** back into legality — a prohibited practice may not be placed on the market, put into service or used at all [1][2]. The prohibitions, together with the AI-literacy duty (Art. 4), have applied since **2 February 2025**, ahead of most of the Regulation [1][4].

This document details each of the eight prohibitions in Article 5(1): (a) harmful **subliminal, manipulative or deceptive** techniques; (b) **exploitation of vulnerabilities** of age, disability or socio-economic situation; (c) **social scoring** leading to unjustified or decontextualised detrimental treatment; (d) **predictive policing of individuals based solely on profiling** or personality assessment; (e) **untargeted scraping** of facial images to build or expand facial-recognition databases; (f) **emotion recognition** in the **workplace and education**; (g) **biometric categorisation** inferring sensitive attributes; and (h) **real-time remote biometric identification** in publicly accessible spaces **for law enforcement**, permitted only under narrow, judicially-authorised exceptions [1][3]. It explains the **Commission's interpretive guidelines** [3], the **penalty ceiling** for breach — up to **€35 million or 7% of worldwide annual turnover** (Art. 99(3)) [1] — and the **new NCII/CSAM ("nudifier") prohibition** added by the adopted AI Omnibus, applicable from **2 December 2026** [6][7][8]. Throughout, it distinguishes **prohibition** (banned) from **high-risk** (permitted with obligations), because several biometric and profiling uses sit just across that line [1][2].

# Key Takeaways

- **Article 5 is an outright ban, not a graded obligation.** A practice within Art. 5 cannot be legitimised by documentation, oversight or conformity assessment — it must not be placed on the market, put into service or used [1][2]. *(Legal obligation.)*
- **In force since 2 February 2025.** Chapters I–II (including Art. 5) and the Art. 4 AI-literacy duty applied first; the penalty and governance machinery followed on 2 August 2025 (Art. 113) [1][4]. *(Legal obligation — in force.)*
- **Eight prohibitions in Art. 5(1)(a)–(h):** harmful manipulation; exploitation of vulnerabilities; social scoring; solely-profiling-based predictive policing; untargeted facial-image scraping; workplace/education emotion recognition; sensitive-attribute biometric categorisation; and real-time remote biometric identification (RBI) in public for law enforcement [1]. *(Legal obligation.)*
- **The prohibitions carry tightly-drafted carve-outs**, not loopholes: e.g. the predictive-policing ban spares assessments grounded in objective, verifiable facts; emotion recognition is allowed for medical or safety reasons; and real-time RBI is permitted only for enumerated serious purposes with **prior judicial/independent authorisation** and a fundamental-rights impact assessment (Art. 5(2)–(7)) [1][3]. *(Legal obligation.)*
- **The Commission's Guidelines on prohibited AI practices (C(2025) 884, 4 Feb 2025) are the primary interpretive aid** — over 130 pages of scope, examples and exclusions — but they are **non-binding**; only the CJEU can give an authoritative reading [3]. *(Regulatory interpretation.)*
- **Breach is the most severely penalised conduct under the Act:** up to **€35 million or 7% of total worldwide annual turnover**, whichever is higher (Art. 99(3)) [1]. *(Legal obligation.)*
- **New "nudifier" prohibition added by the adopted AI Omnibus:** AI systems that generate or manipulate **non-consensual intimate imagery** or **CSAM** become a further Art. 5 prohibited practice, applicable from **2 December 2026**, with a **safe harbour** where the system has adequate technical safeguards; adopted by Parliament (16 Jun 2026) and Council (29 Jun 2026), pending OJ publication [6][7][8]. *(Legal obligation — pending OJ publication.)*
- **Prohibition ≠ high-risk.** Many neighbouring uses (post/non-real-time RBI, emotion recognition outside work/education, non-sensitive biometric categorisation) are **not** banned but fall into the **high-risk** regime detailed in `ai-act-high-risk` [1][2]. *(Legal obligation.)*

# Purpose

This document supports three tasks the foundation document leaves open: (a) **screening** an AI system or use case against each Article 5 prohibition and its exceptions, so an organisation can assert with evidence that it operates no prohibited practice; (b) **distinguishing** a prohibited practice from a merely high-risk one, since the two regimes have entirely different consequences (ban vs. conformity); and (c) **tracking the moving boundary** of Article 5, in particular the newly-added NCII/CSAM prohibition. It is written for legal, compliance, product and trust-and-safety readers. It presupposes `ai-act-foundations` for the risk-tier overview and cross-refers `ai-act-high-risk` for the adjacent high-risk regime and `digital-omnibus` for the simplification package as a whole.

# Scope

**In scope:** The eight prohibitions in Article 5(1)(a)–(h) and their statutory exceptions; the procedural safeguards for real-time remote biometric identification (Art. 5(2)–(7)); the 2 February 2025 applicability date (Art. 113); the Commission's Guidelines on prohibited AI practices; the Art. 99(3) penalty for breach; the AI-Omnibus-added NCII/CSAM prohibition; and the demarcation between prohibited and high-risk practices.

**Out of scope (covered elsewhere):** The four-tier risk framework, GPAI regime and general penalty structure → `ai-act-foundations`; the high-risk classification and obligations that govern the *permitted* biometric/profiling uses → `ai-act-high-risk`; the GPAI/systemic-risk regime → `ai-act-gpai`; the AI Omnibus package in full (timeline postponements, SME relief) → `digital-omnibus`; Art. 50 transparency duties (deepfake/synthetic-content marking) → `ai-act-foundations`. Where a prohibited practice also processes personal data, the GDPR applies in parallel (see `gdpr-foundations`); this document does not restate GDPR duties.

**Assumptions:** The reader has read `ai-act-foundations`. "Placing on the market", "putting into service", "provider" and "deployer" bear their Art. 3 meanings. Dates for the AI Omnibus additions are the adopted-text dates and become binding only on Official Journal publication.

# Definitions

*Shared terms (AI system, provider, deployer, special category data, high-risk AI system) are in `GLOSSARY.md`. Only Article-5-specific terms are defined here, per sub-topic policy.*

| Term | Definition | Source |
|------|------------|--------|
| Prohibited AI practice | An AI practice listed in Art. 5 whose risk is deemed unacceptable; it may not be placed on the market, put into service or used — no conformity route exists. | [1] |
| Subliminal technique | A technique operating beyond a person's consciousness, or a purposefully manipulative or deceptive technique, that materially distorts behaviour by impairing informed decision-making (Art. 5(1)(a)). | [1][3] |
| Social scoring | Evaluation or classification of persons over time based on social behaviour or personal/personality characteristics, producing detrimental treatment in unrelated contexts or that is unjustified/disproportionate (Art. 5(1)(c)). | [1] |
| Emotion recognition system | An AI system for identifying or inferring emotions or intentions of natural persons on the basis of their biometric data (Art. 3(39)); prohibited in workplace/education subject to medical/safety exceptions (Art. 5(1)(f)). | [1] |
| Biometric categorisation system | An AI system assigning natural persons to categories on the basis of biometric data (Art. 3(40)); prohibited where it infers sensitive attributes (Art. 5(1)(g)). | [1] |
| Remote biometric identification (RBI) | An AI system identifying persons, typically at a distance, by comparing biometric data against a reference database, without active involvement; "real-time" where capture, comparison and identification occur without significant delay (Art. 3(41)–(42)). | [1] |
| Non-consensual intimate imagery (NCII) | Images, video or audio depicting an identifiable person's intimate parts or sexually explicit activity produced or manipulated without that person's consent; generation/manipulation by AI is a prohibited practice under the AI-Omnibus addition to Art. 5. | [7][8] |

# Background

The AI Act's architecture is **risk-based**: the greater the threat an AI practice poses to health, safety or fundamental rights, the heavier the legal response, escalating from no obligation (minimal risk) through transparency and high-risk duties to **outright prohibition** at the apex [1][2]. Article 5 is that apex. It reflects a political judgement — taken during the 2021–2024 negotiation and expanded late in the process to cover more biometric uses — that certain applications are so incompatible with Union values and the Charter of Fundamental Rights that no safeguard can render them acceptable [1]. Academic commentary on the draft Act noted that this list of "unacceptable" practices, and especially its manipulation and biometric limbs, would be among the most contested and hardest-to-interpret provisions, precisely because the prohibitions turn on open-textured concepts such as "material distortion" of behaviour and "significant harm" [10].

The prohibitions were **front-loaded** in the application timeline. Whereas most of the Act phases in across 2025–2028, Chapters I and II — which include Article 5 — and the Article 4 AI-literacy obligation became applicable on **2 February 2025**, six months after entry into force (Art. 113) [1][4]. To support consistent enforcement ahead of the penalty machinery (applicable 2 August 2025), the Commission published extensive **Guidelines on prohibited AI practices** on **4 February 2025** [3][4]. Most recently, the **AI Omnibus** simplification package (Commission proposal of 19 November 2025) — while chiefly *postponing* high-risk obligations — moved in the opposite direction on one point, **adding** a prohibition targeting AI "nudifier" tools that generate non-consensual intimate imagery and CSAM [5]. It completed the legislative procedure through trilogue and co-legislator adoption in June 2026 [6][7][8][9].

# Legal Framework

**OBLIGATION.** Prohibited practices are governed by **Article 5** (Chapter II) of Regulation (EU) 2024/1689, read with the definitions in Chapter I (Art. 3), the penalty rule in **Article 99(3)**, and the application-date rule in **Article 113** [1]. Article 5(1) enumerates the prohibited practices; Article 5(2)–(7) sets out the procedural conditions and safeguards that frame the single most qualified prohibition, real-time remote biometric identification for law enforcement [1].

The prohibition operates on the three "market" verbs used throughout the Act: a prohibited AI system may not be **placed on the market**, **put into service**, or **used** (Art. 5(1)) [1]. This is materially wider than the high-risk regime, which principally binds *providers* at market placement and *deployers* in use: Article 5 reaches **every operator** and every stage, and it has **no conformity assessment, no CE marking and no registration** — because these practices are not permitted at all [1][2]. Where an AI system's design straddles a prohibition and a lawful use, the Commission's Guidelines direct that the specific facts (purpose, context, effects) determine whether the prohibition bites [3].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 5(1)(a) | Ban on AI using subliminal, purposefully manipulative or deceptive techniques that materially distort behaviour and cause (or are likely to cause) significant harm. | [1] |
| Art. 5(1)(b) | Ban on AI exploiting vulnerabilities of age, disability or a specific social/economic situation to materially distort behaviour and cause significant harm. | [1] |
| Art. 5(1)(c) | Ban on social scoring — evaluating/classifying persons over time by social behaviour or personal characteristics, leading to detrimental treatment in unrelated contexts or that is unjustified/disproportionate. | [1] |
| Art. 5(1)(d) | Ban on assessing/predicting the risk of a person committing a criminal offence based **solely** on profiling or personality-trait assessment; exception where it supports a human assessment based on objective, verifiable facts directly linked to criminal activity. | [1] |
| Art. 5(1)(e) | Ban on creating or expanding facial-recognition databases through **untargeted scraping** of facial images from the internet or CCTV. | [1] |
| Art. 5(1)(f) | Ban on inferring emotions of natural persons in the **workplace** and **education** institutions; exception for medical or safety reasons. | [1] |
| Art. 5(1)(g) | Ban on **biometric categorisation** deducing/inferring race, political opinions, trade-union membership, religious/philosophical beliefs, sex life or sexual orientation; narrow exception for lawful labelling/filtering of lawfully acquired biometric datasets and law-enforcement categorisation. | [1] |
| Art. 5(1)(h) | Ban on **real-time remote biometric identification** in publicly accessible spaces for law-enforcement purposes, save three enumerated exceptions. | [1] |
| Art. 5(2)–(7) | Conditions/safeguards for the Art. 5(1)(h) exceptions: seriousness/necessity/proportionality test, Annex II serious-offence list, prior authorisation by a judicial or independent administrative authority, fundamental-rights impact assessment, registration and notification; Member-State enabling law. | [1] |
| Art. 5 (AI Omnibus addition) | New ban on AI systems that generate or manipulate non-consensual intimate imagery or CSAM ("nudifier" tools), subject to a safe harbour for adequate technical safeguards; applicable 2 Dec 2026. | [6][7][8] |
| Art. 4 | AI-literacy duty (applied 2 Feb 2025 alongside Art. 5). | [1][4] |
| Art. 99(3) | Penalty for breach of Art. 5 — up to €35,000,000 or 7% of total worldwide annual turnover, whichever is higher. | [1] |
| Art. 113 | Application dates — Chapters I–II (incl. Art. 5) apply from 2 Feb 2025. | [1][4] |

## Relevant Recitals

*Recitals are not binding but aid construction (Art. 296 TFEU practice); this is stated expressly.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 28 area | Rationale for prohibiting AI practices contrary to Union values and fundamental rights; the outright-ban tier. | [1] |
| Recital 29 area | Meaning of subliminal/manipulative/deceptive techniques and "material distortion" of behaviour (Art. 5(1)(a)–(b)); lawful persuasion and medical uses excluded. | [1] |
| Recital 31 area | Why social scoring is banned — decontextualised, unjustified or disproportionate detrimental treatment; contrast with lawful, context-bound evaluation. | [1] |
| Recital 42 area | Basis of the predictive-policing ban — presumption of innocence; persons should be judged on actual conduct, not profiling. | [1] |
| Recital 43 area | Untargeted facial-image scraping adds to mass-surveillance and fundamental-rights harm. | [1] |
| Recital 44 area | Concerns over emotion recognition's scientific reliability, especially in work/education power imbalances. | [1] |
| Recital 30 area | Biometric categorisation on sensitive grounds; scope of the labelling/filtering exception. | [1] |
| Recital 32–33 area | Necessity/proportionality and safeguards for real-time RBI; serious-harm justification and prior authorisation. | [1] |

## Relevant Case Law

**Not Applicable — no CJEU case law yet.** Article 5 has applied only since 2 February 2025 and no judgment has yet interpreted it; the Commission expressly reserves authoritative interpretation to the CJEU [3]. Interpretive weight currently rests on the Regulation's text and recitals, the Commission's Guidelines on prohibited AI practices [3], and — for the personal-data and biometric dimensions — GDPR/law-enforcement-directive case law (see `gdpr-foundations`). This section should be revisited once enforcement actions and references for preliminary rulings emerge. [1][3]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **Commission framework page:** presents the top tier as AI posing a "clear threat to the safety, livelihoods and rights of people", which is **banned**, and lists examples — social scoring, certain manipulative or exploitative systems, and certain biometric uses [2]. *(Regulatory interpretation.)*
- **Commission Guidelines on prohibited AI practices (C(2025) 884 final, 4 Feb 2025):** the principal interpretive instrument. Adopted the day AFTER Art. 5 became applicable, they give — across more than 130 pages — the Commission's reading of each prohibition, worked examples, and the boundary with lawful and high-risk uses; the Commission stresses they are **non-binding** and that only the CJEU can interpret the Act authoritatively [3]. Providers and deployers should treat them as the best available guide but not as a safe harbour. *(Regulatory interpretation.)*
- **"First rules now applicable" (2 Feb 2025):** the Commission confirmed that the prohibitions and the AI-literacy obligation were the first parts of the Act to bite, six months after entry into force [4]. *(Regulatory interpretation — in force.)*
- **Narrow construction of exceptions:** the Guidelines read the Art. 5 carve-outs (e.g. medical/safety emotion recognition; objective-fact-based criminal-risk assessment; real-time RBI exceptions) **restrictively**, consistent with their character as derogations from a fundamental-rights protection [3]. *(Regulatory interpretation.)*
- **AI Omnibus (adopted):** the co-legislators added an Art. 5 prohibition on AI tools generating/manipulating NCII or CSAM, with a **safe harbour** where the system carries adequate technical safeguards, applicable from 2 Dec 2026; adopted by Parliament (16 Jun 2026) and Council (29 Jun 2026), pending OJ publication [6][7][8]. This is the one point on which the Omnibus **tightens** rather than eases the Act. *(Legal obligation — pending OJ publication; verify OJ citation. Detailed in `digital-omnibus`.)*

# Technical Considerations

Each prohibition raises distinct engineering and product screening questions. The following details Art. 5(1)(a)–(h) and the Omnibus addition, with the discriminating test in each case.

- **(a) Harmful manipulation (subliminal/deceptive).** The ban targets AI deploying techniques beyond conscious perception, or purposefully manipulative/deceptive, that **materially distort** behaviour so a person takes a decision they would not otherwise take, causing or likely to cause **significant harm** [1]. The Guidelines distinguish this from lawful persuasion, personalisation and ordinary advertising; the discriminators are covertness/deception, material distortion, and significant (including psychological or financial) harm [3]. *(Legal obligation.)* **BEST PRACTICE:** review recommender, dark-pattern and "engagement-optimising" designs against these three elements.
- **(b) Exploitation of vulnerabilities.** Prohibits AI exploiting vulnerabilities due to **age, disability, or a specific social or economic situation** to materially distort behaviour and cause significant harm [1]. It overlaps with (a) but does not require covert technique — targeting the vulnerability suffices. *(Legal obligation.)* **BEST PRACTICE:** treat products aimed at children, older adults, disabled users or people in financial distress as high-sensitivity for this screen.
- **(c) Social scoring.** Prohibits evaluating/classifying persons **over time** by social behaviour or inferred personal characteristics where the resulting score causes **detrimental or unfavourable treatment in unrelated contexts**, or treatment that is **unjustified or disproportionate** [1]. It is not confined to public authorities — private social scoring is caught. The discriminator from lawful scoring (e.g. regulated credit assessment) is context-decoupling and disproportionality [1][3]. *(Legal obligation.)*
- **(d) Predictive policing of individuals.** Prohibits assessing or predicting the risk of a natural person committing a **criminal offence** based **solely** on **profiling** or on assessing personality traits [1]. The **exception**: systems that **support** a human assessment already grounded in **objective and verifiable facts directly linked to criminal activity** are not caught [1][3]. It does not cover place-based (geospatial) crime forecasting. *(Legal obligation.)*
- **(e) Untargeted facial-image scraping.** Prohibits creating or expanding **facial-recognition databases** through **untargeted scraping** of facial images from the **internet or CCTV** footage [1]. The discriminator is *untargeted*, mass collection to build a recognition database; targeted, lawful biometric processing is elsewhere regulated. *(Legal obligation.)* This limb directly addresses Clearview-style database building.
- **(f) Emotion recognition in workplace/education.** Prohibits AI to **infer emotions** of persons in **workplaces** and **education institutions**, except where deployed for **medical or safety** reasons (e.g. fatigue monitoring for safety) [1]. Emotion recognition **outside** these two settings is not banned but is **high-risk** (Annex III) and transparency-regulated (Art. 50) [1][2]. *(Legal obligation.)*
- **(g) Biometric categorisation on sensitive grounds.** Prohibits biometric categorisation that **deduces or infers** race, political opinions, trade-union membership, religious/philosophical beliefs, sex life or sexual orientation [1]. **Exception:** labelling/filtering of **lawfully acquired** biometric datasets (e.g. sorting images) and categorisation in the law-enforcement context, within limits [1]. Categorisation on **non-sensitive** attributes is not banned but may be high-risk/transparency-regulated. *(Legal obligation.)*
- **(h) Real-time remote biometric identification (RBI) in public for law enforcement.** Prohibits **real-time** RBI in **publicly accessible spaces** for **law-enforcement** purposes, save three exceptions: (i) targeted search for specific victims (abduction, trafficking, sexual exploitation) and missing persons; (ii) prevention of a specific, substantial and imminent threat to life/physical safety, or a genuine and present/foreseeable **terrorist** threat; and (iii) localising/identifying a suspect of an offence in the Annex II list punishable by a custodial maximum of at least four years [1]. Even then, Art. 5(2)–(7) require **necessity/proportionality**, a **fundamental-rights impact assessment**, **prior authorisation** by a judicial or independent administrative authority (with a narrow urgency exception), registration and notification, and enabling **national law** [1][3]. **Post** (non-real-time) RBI is not prohibited but is **high-risk** [1][2]. *(Legal obligation.)*
- **(Omnibus addition) NCII/CSAM generators.** The adopted AI Omnibus adds a prohibition on AI systems that **generate or manipulate** non-consensual intimate imagery or child sexual abuse material — "nudifier" tools — applicable from **2 December 2026** [6][7][8]. The prohibition bites where such output is a reasonably foreseeable, reproducible outcome and the system **lacks adequate technical safeguards** (data cleaning, refusal training, output filtering, prompt guardrails, abuse detection) — the **safe harbour** [7][8]. *(Legal obligation — pending OJ publication.)*

# Hosting Considerations

- **Hosts and infrastructure operators can be caught.** Because Art. 5 reaches "use" and "putting into service" by **any** operator — not only providers — an organisation that hosts, offers or operates a prohibited system on behalf of others may itself breach Art. 5 [1]. *(Legal obligation — assess the whole stack, not just first-party features.)*
- **No log-retention or conformity duty attaches to a prohibited practice** — unlike high-risk hosting there is no Art. 12 logging or registration obligation, because the practice is not permitted; the only compliant posture is **not to host it** [1][2]. *(Legal obligation.)*
- **Marketplace / app-store and API operators** should screen third-party AI offerings (especially image-generation and biometric tools) against Art. 5, with particular attention to the incoming NCII/CSAM prohibition and its safe-harbour condition [7][8]. *(EDITORIAL RECOMMENDATION.)*

# Game Hosting Considerations

- **Most game AI is untouched by Art. 5.** NPC behaviour, matchmaking and procedural generation are neither manipulative-to-the-legal-threshold nor biometric, so they fall outside the prohibitions [1][2]. *(Interpretation.)*
- **Watch three edges.** (i) **Manipulation/exploitation (Art. 5(1)(a)–(b))** — monetisation or engagement mechanics that covertly and materially distort behaviour and cause significant harm, especially to **minors** or users in financial distress, risk the ban rather than merely the consumer-law/high-risk regimes; (ii) **emotion recognition** used on players in an **education/serious-games** setting engages Art. 5(1)(f); (iii) **biometric categorisation** inferring sensitive traits from face/voice engages Art. 5(1)(g) [1][3]. *(Legal obligation once triggered.)*
- **User-generated-content and image tools:** in-game or platform image/video generators must be screened against the incoming **NCII/CSAM prohibition** and must carry the safe-harbour safeguards [7][8]. *(Legal obligation from 2 Dec 2026.)*

# AI Considerations

*This document is itself an AI-regulation deep-dive; the "AI Considerations" here concern interaction with adjacent regimes and the model/product stack.*

- **GDPR runs in parallel and independently.** A practice can be lawful-to-attempt under the GDPR yet still **prohibited** under Art. 5, and vice versa; the biometric limbs (e) and (g) and RBI (h) will almost always also engage GDPR Art. 9 (special-category data) and, for law enforcement, the Law Enforcement Directive [1]. Art. 5 is an **additional, absolute** bar, not a substitute for a lawful basis. *(Legal obligation.)*
- **GPAI and general-purpose image models.** The NCII/CSAM prohibition presses directly on **general-purpose generative models**: providers are expected to build guardrails (refusal training, content filtering, abuse detection) so that producing prohibited content is not a reasonably foreseeable, unguarded outcome — the safe harbour [7][8]. This dovetails with the GPAI regime in `ai-act-gpai`. *(Legal obligation — pending OJ publication.)*
- **Transparency regime is separate.** Art. 50 deepfake/synthetic-content **labelling** is a transparency duty, not an Art. 5 prohibition; NCII/CSAM generation is banned outright regardless of any labelling [1][7]. Do not conflate marking with permission. *(Legal obligation.)*
- **The prohibited/high-risk boundary is a design decision.** Emotion recognition, biometric categorisation and RBI can often be **re-scoped** to fall on the high-risk (permitted-with-obligations) side of the line — e.g. post rather than real-time RBI, non-sensitive rather than sensitive categorisation — but this must be a documented, deliberate design choice, not an afterthought [1][2][3]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Run an Article 5 prohibited-practice screen** over every AI system and use case, mapping each against (a)–(h) and the Omnibus addition, and record the conclusion. *(OBLIGATION — the prohibitions are in force.)* [1][4]
2. **Test each candidate against the discriminators, not the label** — for (a)/(b): covertness/vulnerability + material distortion + significant harm; for (c): context-decoupling/disproportionality; for (d): "solely profiling" vs. objective-fact-supported; for (f)/(g): setting and sensitive-attribute inference; for (h): real-time + public + law-enforcement. *(OBLIGATION.)* [1][3]
3. **Consult the Commission Guidelines (C(2025) 884)** for worked examples and boundary cases, but treat conclusions as provisional pending CJEU interpretation. *(BEST PRACTICE.)* [3]
4. **Construe exceptions narrowly and document their basis** — medical/safety emotion recognition, objective-fact criminal-risk assessment, lawful-dataset biometric labelling, and each RBI exception with its Art. 5(2)–(7) safeguards. *(OBLIGATION where relied upon.)* [1][3]
5. **For any real-time RBI use, build the full safeguard chain** — necessity/proportionality assessment, FRIA, prior judicial/independent authorisation, registration, notification, and confirm enabling national law exists. *(OBLIGATION.)* [1]
6. **Screen image/video/audio generation tools against the NCII/CSAM prohibition now** and implement safe-harbour safeguards (data cleaning, refusal training, output filtering, prompt guardrails, abuse detection) ahead of 2 Dec 2026. *(OBLIGATION from 2 Dec 2026; BEST PRACTICE to act now.)* [7][8]
7. **Where a use is high-risk rather than prohibited, route it into the high-risk programme** (`ai-act-high-risk`) — do not treat "not prohibited" as "unregulated". *(OBLIGATION.)* [1][2]
8. **Escalate any suspected prohibited practice to legal review before launch** — the €35m/7% ceiling makes this the highest-consequence AI compliance decision. *(EDITORIAL RECOMMENDATION.)* [1]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Operating a prohibited practice unknowingly (no Art. 5 screen) | Medium | Very High | Art. 5; Art. 99(3) (€35m/7%) [1] | Mandatory prohibited-practice screening in the AI intake process | Low |
| R2 | Manipulation/exploitation ban tripped by engagement or monetisation design, esp. minors | Medium | Very High | Art. 5(1)(a)–(b) [1][3] | Design review against distortion/harm discriminators; legal sign-off | Low |
| R3 | Private social scoring mis-scoped as lawful analytics | Low | High | Art. 5(1)(c) [1] | Context/proportionality assessment; avoid cross-context detriment | Low |
| R4 | Emotion recognition deployed in workplace/education without medical/safety basis | Low | High | Art. 5(1)(f) [1] | Restrict to permitted settings/purposes; document basis | Low |
| R5 | Biometric categorisation inferring sensitive attributes | Low | High | Art. 5(1)(g) [1] | Prohibit sensitive-attribute inference; confine to lawful labelling exception | Low |
| R6 | Real-time RBI used without full Art. 5(2)–(7) safeguards | Low | Very High | Art. 5(1)(h), (2)–(7) [1] | Safeguard chain (FRIA, prior authorisation, registration); or use post-RBI (high-risk) | Low |
| R7 | Image/video generator produces NCII/CSAM without safe-harbour safeguards | Medium | Very High | Art. 5 (Omnibus addition) [7][8] | Guardrails: refusal training, output filtering, abuse detection; act before 2 Dec 2026 | Medium |
| R8 | Treating "not prohibited" as "unregulated", missing high-risk duties | Medium | High | Art. 6, Annex III [1][2] | Route non-prohibited biometric/profiling uses into the high-risk programme | Low |
| R9 | Over-reliance on non-binding Guidelines as a safe harbour | Medium | Medium | Guidelines non-binding; CJEU authoritative [3] | Treat conclusions as provisional; conservative interpretation; monitor case law | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory & screen:** Extend the AI inventory (`ai-act-foundations`) with an Article 5 screen for every system/use case against (a)–(h) and the Omnibus addition. *Effort:* Medium.
- **Phase 1 — Adjudicate boundary cases:** For flagged systems, apply the discriminators and the Commission Guidelines; obtain legal sign-off; record the reasoning. *Effort:* Medium.
- **Phase 2 — Remediate or re-scope:** Retire prohibited uses; where possible re-design onto the high-risk (permitted) side and hand to the high-risk programme. *Effort:* Medium–High.
- **Phase 3 — NCII/CSAM safeguards:** For image/video/audio generation, implement safe-harbour safeguards ahead of 2 Dec 2026 and evidence them. *Effort:* Medium.
- **Phase 4 — RBI safeguard chain (if applicable):** For any lawful RBI exception, stand up FRIA, prior-authorisation and registration processes. *Effort:* High.
- **Phase 5 — Monitor:** Track Commission Guidelines updates, AI Omnibus OJ publication, national enabling laws and emerging CJEU case law. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No awareness of Art. 5; systems unscreened. | No prohibited-practice screen. |
| 2 | Managed | Ad-hoc screening of obvious cases (social scoring, RBI). | Partial screen; some legal review. |
| 3 | Defined | Every system screened against (a)–(h) + Omnibus addition; reasoning recorded; boundary cases adjudicated. | Screening register; documented adjudications. |
| 4 | Quantitatively Managed | Screening embedded in intake gates; NCII/CSAM safeguards evidenced; RBI safeguard chain (if used) operating. | Gate metrics; safeguard evidence; FRIA where relevant. |
| 5 | Optimising | Continuous monitoring of Guidelines/case law; conservative interpretation policy; integrated with GDPR and high-risk programmes. | Legal-watch cadence; integrated AI + data-protection governance. |

# Audit Questions

1. Is there an Article 5 prohibited-practice screen for every AI system and use case, with a recorded conclusion? *(Art. 5; in force since 2 Feb 2025 [1][4].)*
2. How are manipulation/exploitation risks (Art. 5(1)(a)–(b)) assessed in product and monetisation design, especially for minors and vulnerable users? *(Art. 5(1)(a)–(b) [1][3].)*
3. How do you distinguish any scoring/analytics from prohibited social scoring (Art. 5(1)(c))? *([1].)*
4. For any criminal-risk assessment, is it based solely on profiling, or does it support a human assessment grounded in objective, verifiable facts? *(Art. 5(1)(d) [1].)*
5. Do you create or expand facial-recognition databases by untargeted scraping? *(Art. 5(1)(e) [1].)*
6. Is emotion recognition used in any workplace or education setting, and on what medical/safety basis? *(Art. 5(1)(f) [1].)*
7. Does any biometric categorisation infer sensitive attributes, and does it fall within the labelling exception? *(Art. 5(1)(g) [1].)*
8. For any real-time RBI, are all Art. 5(2)–(7) safeguards (exception, FRIA, prior authorisation, registration, national law) in place? *(Art. 5(1)(h), (2)–(7) [1].)*
9. For image/video/audio generators, are NCII/CSAM safe-harbour safeguards implemented ahead of 2 Dec 2026? *(Omnibus addition [7][8].)*
10. How are non-prohibited but high-risk uses routed into the high-risk programme? *(Art. 6, Annex III [1][2].)*

# Implementation Checklist

- [ ] Article 5 screen completed for every AI system/use case (a)–(h) + Omnibus addition.
- [ ] Manipulation/exploitation design review (Art. 5(1)(a)–(b)) done, with minor/vulnerable-user focus.
- [ ] Scoring uses assessed against the social-scoring ban (Art. 5(1)(c)).
- [ ] Criminal-risk assessments confirmed not "solely profiling" (Art. 5(1)(d)).
- [ ] No untargeted facial-image scraping (Art. 5(1)(e)).
- [ ] Emotion recognition confined to permitted settings/purposes (Art. 5(1)(f)).
- [ ] Biometric categorisation avoids sensitive-attribute inference (Art. 5(1)(g)).
- [ ] Real-time RBI safeguard chain in place where any exception is relied on (Art. 5(1)(h), (2)–(7)).
- [ ] NCII/CSAM safe-harbour safeguards implemented for generation tools (by 2 Dec 2026).
- [ ] Non-prohibited biometric/profiling uses routed into the high-risk programme.
- [ ] Legal sign-off obtained for all boundary cases; Guidelines/case-law watch established.

# References

*All external links verified live on 2026-07-11 (`sources_verified`) using `curl` with a browser user-agent. The Council of the EU press release corroborating the 29 June 2026 final adoption is authoritative but its site (consilium.europa.eu) bot-blocks automated requests (HTTP 403); the same facts are cited via the European Parliament sources, which verify HTTP 200.*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act)** — full text incl. Art. 5 (prohibited practices), Arts. 3, 4, 99, 113 and Recitals 28–46. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj

## Regulatory Guidance

- [2] **Regulatory framework on AI / AI Act** (risk-tier overview; the prohibited "unacceptable-risk" tier). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai
- [3] **Commission publishes the Guidelines on prohibited artificial intelligence (AI) practices** (Commission Communication C(2025) 884 final, 4 Feb 2025; non-binding interpretation of Art. 5). European Commission. https://digital-strategy.ec.europa.eu/en/library/commission-publishes-guidelines-prohibited-artificial-intelligence-ai-practices-defined-ai-act
- [4] **First rules of the Artificial Intelligence Act are now applicable** (prohibited practices and AI-literacy duty applied 2 Feb 2025). European Commission. https://digital-strategy.ec.europa.eu/en/news/first-rules-artificial-intelligence-act-are-now-applicable
- [5] **Digital Omnibus on AI — regulation proposal** (Commission proposal of 19 Nov 2025; simplification package including the new NCII/CSAM prohibition). European Commission. https://digital-strategy.ec.europa.eu/en/library/digital-omnibus-ai-regulation-proposal
- [6] **AI Act: deal on simplification measures, ban on "nudifier" apps** (provisional agreement, 7 May 2026; new Art. 5 prohibition on NCII/CSAM generators). European Parliament press release. https://www.europarl.europa.eu/news/en/press-room/20260427IPR42011/ai-act-deal-on-simplification-measures-ban-on-nudifier-apps
- [7] **AI Act: EP approves simplification measures and "nudifier" app ban** (plenary adoption 16 June 2026, 423–57 with 174 abstentions; prohibition on AI generating NCII/CSAM, applicable 2 Dec 2026, with a technical-safeguards safe harbour). European Parliament press release. https://www.europarl.europa.eu/news/en/press-room/20260611IPR45207/ai-act-ep-approves-simplification-measures-and-nudifier-app-ban
- [8] **Artificial Intelligence: Council gives final green light to simplify and streamline rules** (Council final adoption, 29 June 2026; enters into force on the third day after OJ publication). Council of the EU. https://www.consilium.europa.eu/en/press/press-releases/2026/06/29/artificial-intelligence-council-gives-final-green-light-to-simplify-and-streamline-rules/
- [9] **Digital Omnibus on AI — Legislative Train Schedule** (procedural status of the package amending the AI Act, incl. the Art. 5 addition). European Parliament. https://www.europarl.europa.eu/legislative-train/package-digital-package/file-digital-omnibus-on-ai

## Standards

Not Applicable — the Article 5 prohibitions are outright bans, not conformity-assessed requirements, so no harmonised standards or ISO/IEC/NIST specifications operationalise them. Standards are relevant to the adjacent **high-risk** regime (see `ai-act-high-risk`) and to AI management systems (see `ai-governance-foundations`), not to prohibited practices.

## Academic Sources

- [10] **Veale, M. & Zuiderveen Borgesius, F. (2021), "Demystifying the Draft EU Artificial Intelligence Act" — Computer Law Review International 22(4), 97–112.** Analyses the "unacceptable-risk" prohibitions (manipulation, exploitation, social scoring, biometric limbs) and flags their open-textured drafting. Open-access preprint, arXiv:2107.03721. https://arxiv.org/abs/2107.03721 *(Analyses the draft text; article numbering and detail were revised in the final Regulation — cite alongside [1].)*

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- Article 5: Prohibited AI Practices — annotated text and recitals (artificialintelligenceact.eu). https://artificialintelligenceact.eu/article/5/
- European Commission — "Navigating the AI Act" FAQ. https://digital-strategy.ec.europa.eu/en/faqs/navigating-ai-act
- EU Artificial Intelligence Act — Implementation Timeline (Future of Life Institute). https://artificialintelligenceact.eu/implementation-timeline/

# Related Documents

- `ai-act-foundations` — the AI Act overview, risk tiers, penalties and timeline; this deep-dive **details its Article 5 material** (**prerequisite reading**).
- `ai-act-high-risk` — the adjacent high-risk regime governing the *permitted* biometric/profiling uses that sit just across the prohibition line.
- `ai-act-gpai` — GPAI regime; relevant to the NCII/CSAM safeguards expected of general-purpose generative models.
- `digital-omnibus` — the 2025–2026 simplification package that adds the NCII/CSAM prohibition and postpones high-risk dates.
- `gdpr-foundations` — parallel data-protection regime engaged by the biometric and profiling prohibitions.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Deep-dive on AI Act Article 5 prohibited practices (a)–(h) and the Art. 5(2)–(7) RBI safeguards; the 2 Feb 2025 applicability (Art. 113), the Commission Guidelines on prohibited AI practices (C(2025) 884, 4 Feb 2025), the Art. 99(3) penalty, and the prohibition/high-risk boundary. **Live-verified:** the AI Omnibus (adopted EP 16 Jun 2026; Council 29 Jun 2026) ADDS a new Art. 5 prohibition on AI systems generating/manipulating non-consensual intimate imagery and CSAM ("nudifier" ban), applicable 2 Dec 2026 with a technical-safeguards safe harbour; OJ publication pending. All external links checked HTTP 200 on 2026-07-11 (Council/Consilium 29 Jun release corroborated via EP sources, as consilium.europa.eu bot-blocks curl). | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 3 human gate; frozen in release 0.14.0. | Human reviewer |
