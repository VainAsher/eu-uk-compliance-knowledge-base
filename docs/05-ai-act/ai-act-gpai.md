---
id: ai-act-gpai
title: "EU AI Act: General-Purpose AI Models & Systemic Risk"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU]
topic: AI Act
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [ai-act-foundations, ai-act-high-risk, ai-governance-foundations, gdpr-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [ai-act, gpai, general-purpose-ai, systemic-risk, code-of-practice, ai-office, foundation-models, article-53, article-55, flop-threshold]
legal_basis: Regulation (EU) 2024/1689 (Articles 3(63), 3(65)–(66), 51–56, 88–94, 101; Annexes XI, XII, XIII)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-act-gpai |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | <pending human review> |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a Tier 2 **deep-dive** that details the general-purpose AI (GPAI) and systemic-risk material introduced at overview level in `ai-act-foundations`; it does not repeat that overview. **Status note:** unlike the high-risk timeline, the GPAI regime is **already in force** — GPAI provider obligations apply from **2 August 2025** — and the **AI Omnibus** simplification package (adopted by the European Parliament on 16 June 2026 and the Council on 29 June 2026) **did not postpone** the GPAI obligations; it reinforced the AI Office's supervisory role over GPAI [1][3][9].

# Executive Summary

Chapter V of the EU AI Act (Regulation (EU) 2024/1689) creates a **model-level** regime that sits apart from the risk-tier classification applied to AI *systems*. It regulates **general-purpose AI (GPAI) models** — the foundation models (large language, multimodal and generative models) that display significant generality and can be integrated into countless downstream systems [1]. These obligations **entered into application on 2 August 2025** and are enforced centrally by the **European AI Office**, not by national market-surveillance authorities [1][3][7].

Every GPAI-model provider owes four baseline duties under **Article 53**: maintain **technical documentation** (Annex XI); give **information and documentation to downstream providers** who integrate the model (Annex XII); put in place a **policy to comply with EU copyright law** (including the Directive (EU) 2019/790 text-and-data-mining reservation); and publish a **sufficiently detailed summary of training content** using the AI Office template [1][3]. Free and open-source models are relieved of the documentation duties — **but not** of the copyright and training-summary duties, and **not at all** where the model has systemic risk [1][5].

A subset of models is designated **GPAI with systemic risk**. Under **Article 51**, a model is presumed to carry systemic risk when the cumulative training compute exceeds **10²⁵ floating-point operations (FLOP)** — a rebuttable presumption — or where the Commission so decides on Annex XIII criteria [1][3][5]. Such providers must additionally, under **Article 55**, perform **model evaluation including adversarial testing (red-teaming)**, **assess and mitigate systemic risks** at Union level, **track and report serious incidents** to the AI Office, and ensure **adequate cybersecurity** for the model and its physical infrastructure [1][3]. The **General-Purpose AI Code of Practice** — published **10 July 2025** and structured in three chapters (Transparency, Copyright, Safety and Security) — is the primary **voluntary** route to demonstrate compliance pending harmonised standards; major providers (Amazon, Anthropic, Google, IBM, Microsoft, Mistral AI, OpenAI and others) are signatories [4][6][10].

# Key Takeaways

- **GPAI is a model-level regime (Chapter V, Arts. 51–56)**, distinct from the system-level risk tiers; a single GPAI model may be integrated into thousands of systems across the value chain [1]. *(Legal obligation.)*
- **In force since 2 August 2025.** GPAI provider obligations apply now; the **AI Omnibus did not delay them** (contrast the postponed high-risk dates) [1][3][9]. *(Legal obligation — in force.)*
- **A GPAI model (Art. 3(63))** is one trained on large data at scale, displaying **significant generality** and capable of a **wide range of distinct tasks**, regardless of how it is placed on the market; the Commission's guidelines treat **~10²³ FLOP** training compute plus broad generative capability as an indicative threshold for "significant generality" [1][6]. *(Legal obligation, as interpreted.)*
- **Article 53 baseline (all GPAI providers):** technical documentation (Annex XI), downstream information (Annex XII), an EU **copyright policy**, and a public **training-content summary** on the AI Office template [1][3]. *(Legal obligation.)*
- **Open-source relief is partial.** Free/open-source GPAI models are exempt from the Art. 53 documentation duties, but **remain bound** by the copyright and training-summary duties, and the relief **does not apply** to systemic-risk models [1][5]. *(Legal obligation.)*
- **Systemic-risk presumption = 10²⁵ FLOP (Art. 51(2)).** It is **rebuttable**; the Commission may also designate a model on **Annex XIII** criteria, and providers must **notify** the Commission within **two weeks** of meeting (or foreseeing) the threshold (Art. 52) [1][3][5]. *(Legal obligation.)*
- **Article 55 (systemic-risk models):** state-of-the-art **model evaluation / adversarial testing**, **systemic-risk assessment and mitigation** at Union level, **serious-incident tracking and reporting** to the AI Office, and **cybersecurity** of the model and infrastructure [1][3]. *(Legal obligation.)*
- **The GPAI Code of Practice (published 10 July 2025)** and the Commission's **Guidelines (18 July 2025)** are the practical compliance route; the Code is **voluntary** and signing it is **not** a legal safe harbour, but adherence is treated as evidence of compliance pending harmonised standards [4][6][10]. *(Regulatory interpretation + best practice.)*
- **Central enforcement by the AI Office** with GPAI-specific powers (information requests, evaluations, measures) and fines up to **€15 million or 3% of worldwide annual turnover** (Art. 101); AI Office enforcement powers apply from **2 August 2026** [1][7]. *(Legal obligation.)*
- **Value-chain hinge:** GPAI providers feed the **downstream** providers who build high-risk systems; the Annex XII information duty is what lets those integrators meet their own Chapter III obligations — see `ai-act-high-risk` [1]. *(Legal obligation.)*

# Purpose

This document supports three tasks the foundation document leaves open: (a) **determining** whether a model is a GPAI model at all, and whether it crosses into **systemic risk**; (b) **implementing** the Article 53 baseline duties and the Article 55 systemic-risk duties, using the Code of Practice as the operational scaffold; and (c) **allocating responsibilities across the value chain** between the GPAI provider and the downstream system provider. It is written for legal, compliance, ML-engineering and safety readers at model developers and at organisations integrating third-party foundation models. It presupposes `ai-act-foundations` for the risk-tier overview and cross-refers `ai-act-high-risk` for the downstream system obligations and `ai-governance-foundations` for the operational management-system detail.

# Scope

**In scope:** the definition of a GPAI model (Art. 3(63)) and of systemic risk (Arts. 3(65)–(66)); the Article 53 provider obligations (technical documentation, downstream information, copyright policy, training-content summary) and the open-source relief; the authorised-representative duty (Art. 54); the systemic-risk classification route (Art. 51, the 10²⁵ FLOP presumption, Annex XIII) and the notification procedure (Art. 52); the Article 55 systemic-risk obligations; the Code of Practice and harmonised standards (Art. 56); the AI Office's role and GPAI enforcement/penalties (Arts. 88–94, 101); the application date (2 August 2025) and the transition for models already on the market; and the value-chain interaction with high-risk systems.

**Out of scope (covered elsewhere):** the four-tier system-level overview and penalty structure at large → `ai-act-foundations`; high-risk classification, the Art. 8–15 requirements and conformity assessment → `ai-act-high-risk`; Art. 50 transparency for AI-generated content (deepfake/synthetic-content marking is a **deployer/system** duty, distinct from the GPAI **model** regime) → `ai-act-foundations`; the AI Omnibus package as a whole → `digital-omnibus` (planned); operational AI management systems (ISO/IEC 42001, NIST AI RMF) → `ai-governance-foundations`; and GDPR duties where a GPAI model processes personal data → `gdpr-foundations`, `privacy-engineering-foundations`.

**Assumptions:** the reader has read `ai-act-foundations`. "Provider" throughout means the provider of the **GPAI model** (Art. 3(3)), which may differ from the provider of a downstream **system**. Where training or inference involves personal data, the GDPR applies in parallel and is not restated here.

# Definitions

*Shared terms (AI system, GPAI model, provider, deployer, high-risk AI system) are in `GLOSSARY.md`. Only GPAI-specific terms are defined here, per sub-topic policy.*

| Term | Definition | Source |
|------|------------|--------|
| General-purpose AI model | An AI model, including one trained with a large amount of data using self-supervision at scale, that displays **significant generality** and is capable of competently performing a **wide range of distinct tasks**, and that can be integrated into a variety of downstream systems — excluding models used for research/development/prototyping before release (Art. 3(63)). | [1] |
| General-purpose AI system | An AI system based on a GPAI model, which has the capability to serve a variety of purposes, both for direct use and integration in other systems (Art. 3(66)). | [1] |
| Systemic risk | A risk specific to the **high-impact capabilities** of GPAI models, having a significant impact on the Union market due to reach, or actual/reasonably foreseeable negative effects on public health, safety, security, fundamental rights or society, that can propagate at scale (Art. 3(65)). | [1] |
| High-impact capabilities | Capabilities that match or exceed those recorded in the most advanced GPAI models (Art. 3(64)); presumed where cumulative training compute exceeds 10²⁵ FLOP (Art. 51(2)). | [1] |
| Downstream provider | A provider of an AI system (including a general-purpose AI system) which integrates a GPAI model, whether the model is its own or sourced from another provider (Art. 3(68)). | [1] |
| Training-content summary | The "sufficiently detailed summary" of the content used to train a GPAI model that the provider must draw up and make publicly available, following the template provided by the AI Office (Art. 53(1)(d)). | [1][3] |

# Background

The AI Act was negotiated as a system-level, risk-based product-safety law. Between the Commission's 2021 proposal and the 2023–2024 trilogues, the rapid rise of **foundation models** — trained once, then adapted into innumerable downstream applications — exposed a gap: the risk of such a model cannot be assessed only where it is *deployed*, because the same model underlies many deployments and its capabilities (and failure modes) are set upstream at training time. The co-legislators responded by adding **Chapter V**, a **model-level** regime addressed to the entities that actually build the models, layered on top of the system-level tiers that the Commission presents as the AI Act's core structure [1][2].

The regime has two rings. The **outer ring** (Art. 53) applies to *every* GPAI model and is essentially about **transparency and lawful sourcing** — documentation up and down the value chain, a copyright policy, and a public training-content summary. The **inner ring** (Arts. 51, 55) applies only to the handful of models with **systemic risk** — the frontier models whose scale means a defect or misuse could cascade across the Union — and imposes **safety-engineering** duties: evaluation, red-teaming, risk mitigation, incident reporting and cybersecurity [1]. Because harmonised technical standards for these duties do not yet exist, the AI Office facilitated a co-regulatory **Code of Practice**, finalised on **10 July 2025**, three weeks before the obligations applied on **2 August 2025** [4][6]. The 2025–2026 **AI Omnibus** simplification package, which postponed the *high-risk* application dates, deliberately **left the GPAI timeline untouched** [3][9].

# Legal Framework

The GPAI regime is **Chapter V** of Regulation (EU) 2024/1689, comprising: **classification** (Arts. 51–52), **obligations of GPAI-model providers** (Arts. 53–54), **obligations of systemic-risk providers** (Art. 55), and the **codes of practice** mechanism (Art. 56). Definitions sit in Chapter I (Art. 3(63)–(66), (68)); governance and enforcement in Chapters VII and IX (the **AI Office**, and Arts. 88–94 on GPAI supervision); penalties in Chapter XII (Art. 101). The substantive detail is filled out by **Annex XI** (technical documentation for the AI Office), **Annex XII** (information for downstream providers), and **Annex XIII** (criteria for designating systemic risk) [1].

The regime is enforced **centrally**: Article 88 confers on the Commission (acting through the **AI Office**) **exclusive competence** to supervise and enforce Chapter V, displacing national market-surveillance authorities for GPAI models [1][7]. This is a structural difference from the high-risk regime, which is enforced by Member State authorities.

**OBLIGATION vs INTERPRETATION note.** The Regulation's text (Arts. 51–56, Annexes XI–XIII) is the **binding obligation**. The Commission's **Guidelines** on the scope of GPAI obligations (18 July 2025) and the **Code of Practice** (10 July 2025) are **not** binding law: the Guidelines express the Commission's interpretation, and the Code is a **voluntary** instrument that adherents may use to *demonstrate* compliance (Art. 56(5)) [4][6]. They are treated below as **regulatory interpretation** / **best practice**, never as the source of the obligation itself.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 3(63) | Definition of "general-purpose AI model" (significant generality; wide range of distinct tasks). | [1] |
| Art. 3(64)–(66) | Definitions of high-impact capabilities, systemic risk, and general-purpose AI system. | [1] |
| Art. 3(68) | Definition of "downstream provider". | [1] |
| Art. 51 + Annex XIII | Classification of a GPAI model as one **with systemic risk**: high-impact capabilities (evaluated by tools/benchmarks) or Commission decision; **presumption at >10²⁵ FLOP** cumulative training compute (rebuttable). | [1] |
| Art. 52 | Procedure: provider must **notify the Commission within two weeks** of meeting/foreseeing the threshold; may argue the presumption does not apply; Commission maintains a public list. | [1] |
| Art. 53(1)(a) + Annex XI | **Technical documentation** of the model (kept up to date; provided to the AI Office / national authorities on request). | [1] |
| Art. 53(1)(b) + Annex XII | **Information and documentation to downstream providers** integrating the model (to enable their compliance) while protecting IP/trade secrets. | [1] |
| Art. 53(1)(c) | **Policy to comply with Union copyright law**, in particular the text-and-data-mining rights reservation under Art. 4(3) of Directive (EU) 2019/790. | [1] |
| Art. 53(1)(d) | **Publicly available, sufficiently detailed summary** of training content, per the AI Office template. | [1][3] |
| Art. 53(2) | **Open-source relief** — models released under a free/open-source licence with public parameters are exempt from (a) and (b), **unless** they are systemic-risk models; (c) and (d) still apply. | [1] |
| Art. 54 | **Authorised representative** in the Union for non-EU GPAI providers. | [1] |
| Art. 55(1)(a) | **Model evaluation** with standardised protocols and tools, including **adversarial testing** (red-teaming), to identify and mitigate systemic risk. | [1] |
| Art. 55(1)(b) | **Assess and mitigate** possible **systemic risks at Union level**, including their sources. | [1] |
| Art. 55(1)(c) | **Track, document and report** serious incidents and possible corrective measures to the **AI Office** (and, as appropriate, national authorities) without undue delay. | [1] |
| Art. 55(1)(d) | Ensure an **adequate level of cybersecurity** for the model and its physical infrastructure. | [1] |
| Art. 56 | **Codes of practice** — AI Office facilitates their drawing-up; adherence is a means to demonstrate compliance pending harmonised standards. | [1] |
| Arts. 88–94 | AI Office **supervision and enforcement** of GPAI (monitoring, information requests, evaluations, power to request measures / restrict / recall). | [1][7] |
| Art. 101 | **Fines on GPAI providers** — up to **€15 million or 3%** of worldwide annual turnover. | [1] |
| Arts. 111(3), 113(b) | **Application 2 Aug 2025**; models placed on the market **before** that date must comply **by 2 Aug 2027**. | [1] |

## Relevant Recitals

*Recitals are not binding but aid construction (Art. 296 TFEU practice); this is stated expressly.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 97 | Concept and rationale of "general-purpose AI model"; generality and integration into downstream systems; distinction from AI systems. | [1] |
| Recital 98–99 | Indicators of "significant generality" and the range of distinct tasks; models with at least a billion parameters trained at scale as typical GPAI. | [1] |
| Recital 100 | Public training-content summary — purpose (facilitating rightsholders' exercise of rights) and appropriate level of detail. | [1] |
| Recital 104–106 | Copyright policy and the Art. 4(3) Directive (EU) 2019/790 text-and-data-mining reservation applying regardless of where training occurs. | [1] |
| Recital 110–111 | Systemic risk — high-impact capabilities, the 10²⁵ FLOP indicator, and the categories of systemic risk (incl. CBRN, offensive cyber, loss of control). | [1] |
| Recital 114–116 | Systemic-risk obligations — evaluation/adversarial testing, mitigation, incident reporting, cybersecurity — and codes of practice as a bridge to standards. | [1] |

## Relevant Case Law

**Not Applicable — no case law yet.** The GPAI regime is recent (in force from 2 August 2025) and enforced administratively by the AI Office; no CJEU or national judgment has yet interpreted Arts. 51–56. Interpretive weight currently rests on the Regulation's text, the Commission's Guidelines (18 July 2025), the Code of Practice, and — for copyright — the Directive (EU) 2019/790 framework and any future litigation on the text-and-data-mining reservation. This section should be revisited as enforcement and disputes emerge. [1][6]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **What counts as a GPAI model (Commission Guidelines, 18 July 2025).** The Commission reads "significant generality" as an indicative test: a model trained with **more than ~10²³ FLOP** of compute **and** able to generate language (text/audio), text-to-image or text-to-video is a strong candidate for GPAI status; the guidance also clarifies the **lifecycle** (when a model is "placed on the market"), how **fine-tuning / modification** by a downstream actor can make that actor a GPAI provider, and the **notification** duties [6]. Providers should treat these as the Commission's operational reading, not as the legal test (which is Art. 3(63)) [1][6]. *(Regulatory interpretation.)*
- **Systemic-risk classification (Commission Q&A and Guidelines).** The **10²⁵ FLOP** presumption is a **rebuttable** trigger; providers reaching or reasonably foreseeing it must **notify the Commission within two weeks**, and may argue that, exceptionally, their model does not present systemic risk despite the compute. The Commission may also designate a model **without** the compute threshold, on the Annex XIII criteria, including via alerts from the **Scientific Panel** [1][3][5]. *(Regulatory interpretation.)*
- **The Code of Practice as the compliance bridge.** The AI Office presents adherence to the **General-Purpose AI Code of Practice** (10 July 2025) as the primary way to **demonstrate** compliance with Arts. 53 and 55 until harmonised standards exist; non-signatories must demonstrate compliance by other, potentially more burdensome, means. Signing is **voluntary** and is **not** a legal safe harbour — the AI Office still assesses actual compliance [4][6][10]. *(Regulatory interpretation + best practice.)*
- **Training-content summary template.** The AI Office published a mandatory **template** for the Art. 53(1)(d) public summary, calibrated to be "sufficiently detailed" (a general description of data sources, types and provenance) while protecting trade secrets — narrower than a dataset-by-dataset disclosure [3][5]. *(Regulatory interpretation.)*
- **AI Omnibus did not touch GPAI.** The Commission's simplification package (adopted June 2026) postponed **high-risk** dates and eased documentation for SMEs, but the co-legislators **kept the GPAI obligations in force from 2 August 2025** and reinforced the AI Office's central role over GPAI [3][9]. *(Regulatory interpretation — confirmed.)*

# Technical Considerations

- **Decide GPAI status first, systemic risk second.** Run two gates. Gate 1 (Art. 3(63)): does the model display **significant generality** and perform a **wide range of distinct tasks** (indicatively >~10²³ FLOP + broad generative capability [6])? Gate 2 (Art. 51): does cumulative training compute exceed **10²⁵ FLOP**, or do capabilities otherwise match the most advanced models? If Gate 2 is met, the systemic-risk duties attach and the open-source relief falls away [1][6]. *(Legal obligation.)*
- **Instrument training compute now.** Because both gates and the notification duty (Art. 52) turn on **cumulative training FLOP**, providers must **measure and log** training compute as a first-class metric, including for foreseeability ("reasonably foreseen" to reach 10²⁵) — not reconstruct it after the fact [1][3]. *(Best practice supporting obligation.)*
- **Build the Annex XI / Annex XII documentation as pipeline outputs.** Annex XI (for the AI Office) and Annex XII (for downstream integrators) demand model architecture, training process, evaluation results, capabilities and limitations, and integration guidance; generate these from the MLOps pipeline (model cards, eval harness outputs, data statements) rather than retrofitting [1]. *(Legal obligation + best practice.)*
- **Evaluation and adversarial testing as a standing capability (Art. 55(1)(a)).** Stand up **red-teaming / adversarial evaluation** against the systemic-risk taxonomy (CBRN uplift, offensive cyber, loss of control, harmful manipulation, large-scale disinformation); the Code of Practice's Safety and Security chapter provides the operational model, including a **Safety and Security Framework** and **model reports** [1][10]. *(Legal obligation.)*
- **Serious-incident tracking (Art. 55(1)(c)) is a distinct pipeline.** It reports **model-level systemic-risk events** to the **AI Office** — separate from the Art. 73 serious-incident duty on high-risk **system** providers (which reports to market-surveillance authorities). Use the AI Office's **serious-incident reporting template** for GPAI systemic-risk models and wire in monitoring, triage and "without undue delay" escalation [1][8]. *(Legal obligation.)*
- **Cybersecurity of weights and infrastructure (Art. 55(1)(d)).** Protect **model weights** against exfiltration and the training/inference infrastructure against compromise; treat weight theft as a systemic-risk event. Map to the security baselines in `privacy-engineering-foundations` and the Code's security measures [1][10]. *(Legal obligation.)*
- **Copyright compliance is an engineering problem too (Art. 53(1)(c)).** Operationalise the Directive (EU) 2019/790 Art. 4(3) **TDM opt-out** — honour machine-readable reservations (e.g., robots.txt / TDM Reservation Protocol) at crawl time and record provenance so the copyright policy is auditable [1]. *(Legal obligation + best practice.)*

# Hosting Considerations

- **Hosting a model rarely makes you its provider — but modifying it can.** Serving or fine-tuning a third-party GPAI model may be a downstream activity; however, a **substantial modification** or fine-tuning that itself meets the GPAI threshold can make the modifier a **GPAI provider** for the changes (per the Commission Guidelines), with the corresponding Art. 53/55 duties for the modification [1][6]. *(Legal obligation — assess role.)*
- **Infrastructure operators may hold Art. 55(1)(d) obligations by proxy.** Where a systemic-risk model runs on a provider's own or contracted infrastructure, the **cybersecurity** duty covers the **physical infrastructure**; hosting arrangements should allocate weight-protection, access-control and incident-response responsibilities in contract [1][10]. *(Legal obligation + best practice.)*
- **Documentation access without IP leakage.** Hosting/serving pipelines must be able to surface the **Annex XI** documentation to the AI Office on request and the **Annex XII** package to downstream integrators, while protecting trade secrets and model weights (Art. 53(7)) [1]. *(Legal obligation.)*

# Game Hosting Considerations

- **Integrating a foundation model into a game makes you a downstream provider, not a GPAI provider.** A studio embedding a third-party LLM (NPC dialogue, companion chatbots, content generation) is typically a **downstream provider** relying on the model provider's **Annex XII** information; it does **not** inherit Art. 53/55 model-level duties, but must meet any **system-level** duties (e.g., Art. 50 transparency for AI interaction and synthetic content — see `ai-act-foundations`) [1]. *(Interpretation.)*
- **Self-hosted or heavily fine-tuned models can flip the role.** A studio that trains or substantially fine-tunes its own general-purpose model could itself become a **GPAI provider**; most game-specific fine-tunes will not display "significant generality" or approach the 10²⁵ FLOP systemic threshold, but the assessment should be documented [1][6]. *(Legal obligation once triggered.)*
- **Value-chain information hygiene.** Studios should **retain the Annex XII documentation** they receive from model providers — it is the evidence base for their own transparency and (where relevant) high-risk obligations, and for incident triage if the upstream model misbehaves [1]. *(Best practice.)*

# AI Considerations

*This document is itself an AI-regulation deep-dive; the "AI Considerations" here concern interaction with adjacent regimes and the operational stack.*

- **Operationalise Art. 55 via management systems.** The systemic-risk duties (evaluation, risk assessment, incident handling, cybersecurity) map onto **ISO/IEC 42001** (AI management system) and the **NIST AI RMF** Generative AI Profile; use them to make the Code of Practice's commitments auditable — detailed in `ai-governance-foundations`, not duplicated here [11]. *(Best practice.)*
- **GDPR runs in parallel over training and inference.** Where a GPAI model is trained on or processes **personal data**, GDPR lawful basis, purpose limitation, data-subject rights, DPbDD (Art. 25) and security (Art. 32) apply alongside Chapter V; the AI Act's training-content summary is **not** a GDPR record and does not discharge GDPR transparency (see `gdpr-foundations`, `privacy-engineering-foundations`) [1]. *(Legal obligation.)*
- **The GPAI regime is the upstream half of the high-risk value chain.** A high-risk system built on a GPAI model depends on the **Annex XII** information to meet its Art. 8–15 obligations; conversely, Art. 25(4) requires GPAI providers and downstream providers to cooperate. Read this document with `ai-act-high-risk` [1]. *(Cross-reference.)*
- **Copyright and content-provenance overlap.** The Art. 53(1)(c) copyright policy and the Code's Copyright chapter intersect with output-side provenance/watermarking obligations (Art. 50) and with the Directive (EU) 2019/790 regime; treat input lawfulness (TDM opt-out) and output labelling as separate but related workstreams [1][10]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Classify the model** against Art. 3(63) (GPAI?) and Art. 51 (systemic risk? >10²⁵ FLOP?), and **document** the reasoning; re-assess on further training or capability gains. *(OBLIGATION.)* [1][6]
2. **Measure and log cumulative training compute** as a governed metric, with a foreseeability trigger for the 10²⁵ FLOP notification. *(OBLIGATION-supporting; BEST PRACTICE.)* [1][3]
3. **Produce Annex XI technical documentation and Annex XII downstream information** as pipeline outputs, kept up to date and IP-protected. *(OBLIGATION.)* [1]
4. **Adopt and publish a Union copyright policy** honouring the Art. 4(3) Directive (EU) 2019/790 TDM reservation, with auditable crawl-time enforcement. *(OBLIGATION.)* [1]
5. **Publish the training-content summary** using the AI Office template. *(OBLIGATION.)* [1][3]
6. **Appoint an EU authorised representative** if established outside the Union (Art. 54). *(OBLIGATION where applicable.)* [1]
7. **If systemic risk: notify the Commission within two weeks** (Art. 52) and stand up **model evaluation / adversarial testing** (Art. 55(1)(a)). *(OBLIGATION.)* [1]
8. **Assess and mitigate Union-level systemic risks** across the taxonomy (CBRN, cyber, loss of control, manipulation, disinformation) (Art. 55(1)(b)). *(OBLIGATION.)* [1][10]
9. **Operate serious-incident tracking and reporting to the AI Office** using its template, "without undue delay" (Art. 55(1)(c)). *(OBLIGATION.)* [1][8]
10. **Secure the model weights and infrastructure** to an adequate cybersecurity level (Art. 55(1)(d)). *(OBLIGATION.)* [1]
11. **Sign / align to the GPAI Code of Practice** as the practical demonstration route, but treat it as evidence, not safe harbour, and keep the underlying compliance evidence. *(BEST PRACTICE; EDITORIAL RECOMMENDATION to sign.)* [4][10]
12. **Downstream integrators: capture and retain Annex XII information** and confirm which model-level duties remain with the upstream provider. *(BEST PRACTICE.)* [1]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Misjudging a model as non-GPAI (missing Art. 3(63)) | Medium | High | Art. 3(63); Guidelines [1][6] | Documented generality assessment; re-assess on retraining | Low |
| R2 | Missing the 10²⁵ FLOP systemic threshold / late notification | Medium | Very High | Arts. 51–52 [1] | Compute metering; foreseeability trigger; 2-week notification workflow | Low |
| R3 | Treating open-source as full exemption (esp. systemic-risk models) | Medium | High | Art. 53(2) [1][5] | Apply copyright + summary duties always; no relief if systemic risk | Low |
| R4 | Inadequate training-content summary or copyright policy | Medium | High | Art. 53(1)(c)–(d) [1][3] | AI Office template; TDM opt-out enforcement; provenance records | Medium |
| R5 | Weak model evaluation / no adversarial testing | Medium | Very High | Art. 55(1)(a) [1] | Standing red-team; Code of Practice Safety & Security framework | Medium |
| R6 | Systemic risks unassessed/unmitigated at Union level | Medium | Very High | Art. 55(1)(b) [1][10] | Risk taxonomy; mitigation gates; model reports | Medium |
| R7 | Serious incidents not tracked/reported to AI Office | Medium | High | Art. 55(1)(c) [1][8] | Incident pipeline; AI Office template; undue-delay escalation | Low |
| R8 | Model weights exfiltrated (cybersecurity failure) | Medium | Very High | Art. 55(1)(d) [1] | Weight protection; access control; treat as reportable incident | Medium |
| R9 | Downstream provider lacks Annex XII info to meet high-risk duties | Medium | High | Arts. 53(1)(b), 25(4) [1] | Provide/obtain Annex XII package; value-chain cooperation | Low |
| R10 | Treating Code of Practice signature as a legal safe harbour | Low | Medium | Art. 56; voluntary status [4][10] | Keep underlying evidence; map Code commitments to Arts. 53/55 | Low |

# Implementation Roadmap

- **Phase 0 — Classification & metering:** Assess GPAI status (Art. 3(63)) and systemic risk (Art. 51); instrument cumulative training-compute measurement and a foreseeability trigger. *Effort:* Medium. *Depends on:* `ai-act-foundations` triage.
- **Phase 1 — Article 53 baseline:** Annex XI documentation, Annex XII downstream package, copyright policy (TDM opt-out), training-content summary on the AI Office template; authorised representative if non-EU. *Effort:* Medium–High.
- **Phase 2 — Systemic-risk build (if applicable):** Notify the Commission (Art. 52); stand up model evaluation / adversarial testing, systemic-risk assessment and mitigation, and cybersecurity for weights/infrastructure. *Effort:* High.
- **Phase 3 — Incident & assurance:** Serious-incident tracking and reporting to the AI Office (template); adopt/align to the Code of Practice; map to ISO/IEC 42001 for auditability. *Effort:* High.
- **Phase 4 — Value-chain integration:** Operationalise Annex XII exchange with downstream providers and Art. 25(4) cooperation; support downstream high-risk conformity. *Effort:* Medium.
- **Phase 5 — Monitor & adapt:** Track AI Office guidance, harmonised standards, threshold review, and the Code's evolution; re-assess on retraining/capability change. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No GPAI classification; unaware whether Chapter V applies. | No Art. 3(63)/51 assessment; compute unmetered. |
| 2 | Managed | Model classified; compute metered; baseline docs started. | Draft Annex XI/XII; copyright policy drafted. |
| 3 | Defined | Article 53 baseline complete; training-summary published; role in value chain mapped. | Public summary; Annex XII exchange; authorised rep. |
| 4 | Quantitatively Managed | Systemic-risk duties operating with metrics; evaluations, incident pipeline and cybersecurity in place. | Red-team results; incident reports; weight-protection KPIs. |
| 5 | Optimising | Code of Practice aligned and mapped to ISO/IEC 42001; continual re-evaluation and value-chain assurance. | Signatory + evidence base; audited AIMS; re-assessment cycle. |

# Audit Questions

1. Is there a documented assessment of whether each model is a **GPAI model** (Art. 3(63)) and whether it has **systemic risk** (Art. 51), with cumulative training compute recorded? *(Arts. 3(63), 51 [1].)*
2. Where the 10²⁵ FLOP threshold was met or foreseeable, was the Commission **notified within two weeks** (Art. 52)? *(Art. 52 [1].)*
3. Are **Annex XI** technical documentation and the **Annex XII** downstream package produced, current and IP-protected? *(Art. 53(1)(a)–(b) [1].)*
4. Is there a **copyright policy** honouring the Art. 4(3) Directive (EU) 2019/790 TDM reservation, and is it enforced at crawl time? *(Art. 53(1)(c) [1].)*
5. Is the **training-content summary** published on the AI Office template? *(Art. 53(1)(d) [1][3].)*
6. For systemic-risk models, what **model evaluation and adversarial testing** is performed, and how are Union-level risks **assessed and mitigated**? *(Art. 55(1)(a)–(b) [1][10].)*
7. How are **serious incidents tracked and reported to the AI Office**, and within what timeframe? *(Art. 55(1)(c) [1][8].)*
8. What **cybersecurity** protects the model weights and physical infrastructure? *(Art. 55(1)(d) [1].)*
9. If relying on the **Code of Practice**, is the underlying compliance evidence retained (i.e., not treated as a safe harbour)? *(Art. 56 [4][10].)*
10. For **models placed on the market before 2 Aug 2025**, is there a plan to comply by **2 Aug 2027**? *(Art. 111(3) [1].)*

# Implementation Checklist

- [ ] GPAI status (Art. 3(63)) and systemic-risk (Art. 51) assessments documented; training compute metered.
- [ ] Commission notification workflow ready (Art. 52; two-week / foreseeability trigger).
- [ ] Annex XI technical documentation produced and kept current.
- [ ] Annex XII downstream information package produced and shared (IP-protected).
- [ ] Union copyright policy adopted; Art. 4(3) TDM opt-out enforced and provenance recorded.
- [ ] Public training-content summary published on the AI Office template.
- [ ] EU authorised representative appointed (non-EU providers).
- [ ] (Systemic risk) Model evaluation / adversarial testing operating.
- [ ] (Systemic risk) Union-level systemic-risk assessment and mitigation in place.
- [ ] (Systemic risk) Serious-incident tracking and reporting to the AI Office (template) operating.
- [ ] (Systemic risk) Cybersecurity for model weights and infrastructure implemented.
- [ ] Code of Practice adherence decided; underlying evidence retained; mapped to ISO/IEC 42001.
- [ ] Pre-2 Aug 2025 models: compliance plan to 2 Aug 2027.

# References

*All external links verified HTTP 200 on 2026-07-11 (`sources_verified`) using `curl … -A "Mozilla/5.0"`.*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act)** — full text incl. Arts. 3(63)–(66), 51–56, 88–94, 101, 111, 113 and Annexes XI, XII, XIII. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj

## Regulatory Guidance

- [2] **Regulatory framework on AI / AI Act** (four-tier overview; GPAI framing). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai
- [3] **General-purpose AI obligations under the AI Act** (Art. 53 baseline; 10²⁵ FLOP threshold; systemic-risk duties; application 2 Aug 2025; training-summary template). European Commission. https://digital-strategy.ec.europa.eu/en/factpages/general-purpose-ai-obligations-under-ai-act
- [4] **The General-Purpose AI Code of Practice** (published 10 July 2025; three chapters — Transparency, Copyright, Safety and Security; voluntary; signatories). European Commission. https://digital-strategy.ec.europa.eu/en/policies/contents-code-gpai
- [5] **General-Purpose AI Models in the AI Act — Questions & Answers** (systemic-risk classification, notification, open-source relief, training-summary scope). European Commission. https://digital-strategy.ec.europa.eu/en/faqs/general-purpose-ai-models-ai-act-questions-answers
- [6] **Guidelines on the scope of obligations for providers of general-purpose AI models** (Commission Guidelines, 18 July 2025; GPAI definition, lifecycle, notification). European Commission. https://digital-strategy.ec.europa.eu/en/library/guidelines-scope-obligations-providers-general-purpose-ai-models-under-ai-act
- [7] **The AI Office** (central supervision and enforcement of GPAI under the AI Act). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/ai-office
- [8] **AI Act: Commission publishes a reporting template for serious incidents involving general-purpose AI models with systemic risk** (Art. 55(1)(c)). European Commission. https://digital-strategy.ec.europa.eu/en/library/ai-act-commission-publishes-reporting-template-serious-incidents-involving-general-purpose-ai
- [9] **AI Act: EP approves simplification measures and "nudifier" app ban** (AI Omnibus plenary adoption 16 June 2026; GPAI obligations not postponed). European Parliament. https://www.europarl.europa.eu/news/en/press-room/20260611IPR45207/ai-act-ep-approves-simplification-measures-and-nudifier-app-ban
- [10] **EU AI Act — General-Purpose AI Code of Practice (Final Version)** (the co-regulatory instrument itself; Transparency, Copyright, Safety and Security chapters; Safety and Security Framework and model-report structure). AI Office multi-stakeholder process. https://code-of-practice.ai/

## Standards

- [11] **ISO/IEC 42001:2023 — Artificial intelligence — Management system (AIMS).** Operationalises the Art. 55 systemic-risk duties (evaluation, risk management, incident handling, security) in an auditable management system; see `ai-governance-foundations`. ISO/IEC. https://www.iso.org/standard/42001

## Academic Sources

Not Applicable — this deep-dive relies on the primary Regulation and authoritative Commission / AI Office sources and the co-regulatory Code of Practice. Peer-reviewed analysis of the GPAI systemic-risk threshold and foundation-model governance is emerging but was not required to establish the obligations stated here; it may be added on revision as the literature matures and enforcement produces contested questions.

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- Article 51 — Classification of GPAI models with systemic risk (annotated). EU Artificial Intelligence Act (artificialintelligenceact.eu). https://artificialintelligenceact.eu/article/51/
- EU Artificial Intelligence Act — Implementation Timeline (Future of Life Institute). https://artificialintelligenceact.eu/implementation-timeline/

# Related Documents

- `ai-act-foundations` — the AI Act overview, risk tiers, GPAI regime at overview level, penalties and timeline; this deep-dive **details its GPAI/systemic-risk material** (**prerequisite reading**).
- `ai-act-high-risk` — high-risk systems and conformity assessment; the **downstream** half of the value chain that consumes GPAI providers' Annex XII information (**sibling deep-dive**).
- `ai-governance-foundations` — operationalising Art. 55 duties via ISO/IEC 42001 and the NIST AI RMF Generative AI Profile; **cross-reference, not duplicated here**.
- `gdpr-foundations` / `privacy-engineering-foundations` — parallel data-protection duties where GPAI training/inference processes personal data.
- `digital-omnibus` — the 2025–2026 simplification package in full (planned); confirmed **not** to have postponed the GPAI obligations.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Deep-dive on the AI Act GPAI regime: GPAI definition (Art. 3(63)), Article 53 baseline obligations (Annex XI/XII documentation, copyright policy, training-content summary) and open-source relief, systemic-risk classification (Art. 51; 10²⁵ FLOP rebuttable presumption; Art. 52 notification), Article 55 systemic-risk duties (evaluation/adversarial testing, risk assessment/mitigation, serious-incident reporting, cybersecurity), the Code of Practice and AI Office role (Arts. 56, 88–94), penalties (Art. 101) and the value-chain link to high-risk. **Live-verified: GPAI Code of Practice PUBLISHED 10 July 2025 (voluntary; three chapters); Commission Guidelines 18 July 2025; 10²⁵ FLOP systemic-risk presumption (Art. 51(2)); GPAI obligations in application from 2 August 2025; AI Omnibus (adopted June 2026) did NOT postpone the GPAI obligations.** All external links checked HTTP 200 on 2026-07-11. | — |
