---
id: ai-model-risk-management
title: "AI Model Risk Management & Evaluation"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: AI Governance
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: Medium
supersedes: Not Applicable
related: [ai-governance-foundations, ai-governance-iso-42001, ai-act-foundations, ai-act-high-risk, ai-act-gpai, privacy-threat-modelling]
tags: [model-risk-management, model-validation, model-evaluation, red-teaming, adversarial-robustness, benchmarking, drift-monitoring, model-cards, system-cards, sr-11-7, ss1-23, nist-ai-rmf, iso-23894, ai-act-art-9, ai-act-art-15, ai-act-art-55]
legal_basis: Regulation (EU) 2024/1689 (AI Act) Arts. 9, 15, 55 — operationalised via ISO/IEC 23894, NIST AI RMF, and model-risk-management supervisory practice (PRA SS1/23; Fed SR 11-7 lineage)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-model-risk-management |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.17.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | Medium |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a Tier 2 **deep-dive** on the model risk management (MRM) and model-evaluation methodology introduced at overview level in `ai-governance-foundations` (its parent). It does not restate the EU AI Act's risk-tier scheme (`ai-act-foundations`), the high-risk conformity mechanics (`ai-act-high-risk`) or the GPAI regime (`ai-act-gpai`); it details the **techniques** by which those obligations are met and evidenced. **Standards / supervisory-instrument warning:** the instruments relied on here evolve. Editions and versions were **live-verified on 2026-07-11** — EU AI Act (Reg (EU) 2024/1689), NIST AI RMF **1.0** (Jan 2023) + Generative AI Profile (**NIST AI 600-1**, 26 Jul 2024), ISO/IEC 23894:**2023**, ISO/IEC 42001:**2023**, PRA **SS1/23** (May 2023, effective May 2024). Note that the US **SR 11-7** lineage was **revised and superseded by SR 26-2 on 17 April 2026**; both are described below because SR 11-7 is the source of the discipline this document maps to AI [7][8][9].

# Executive Summary

**Model risk management (MRM)** is the discipline of identifying, measuring, validating, monitoring and governing the risk that a model produces incorrect or misused outputs that lead to adverse decisions [7][8]. It originated in banking — US Federal Reserve/OCC guidance **SR 11-7 (2011)** and the UK PRA's **SS1/23 (2023)** — and its core primitives (independent validation, "effective challenge", ongoing monitoring, a model inventory) map directly onto the obligations the EU AI Act now imposes in law on high-risk and general-purpose AI (GPAI) systems [1][7][8]. This document is the practical bridge between that mature financial discipline and modern AI/generative-AI (GenAI) evaluation.

Three legal anchors matter under the **EU AI Act (Regulation (EU) 2024/1689)**. **Article 9** requires a continuous, lifecycle **risk-management system** for high-risk AI. **Article 15** requires appropriate **accuracy, robustness and cybersecurity**, including resilience to errors and to adversarial attacks (data poisoning, evasion, model-confidentiality attacks). **Article 55** requires providers of **GPAI models with systemic risk** to perform **model evaluation, including adversarial testing (red-teaming)**, to assess and mitigate systemic risk, ensure cybersecurity and report serious incidents [1]. These are **binding law**. The methods that satisfy them — the **NIST AI RMF** and its **Generative AI Profile**, **ISO/IEC 23894** (AI risk management), model validation practice, benchmarking, red-teaming, adversarial-robustness testing, drift monitoring, and documentation via **model cards** and **system cards** — are **voluntary frameworks and consensus techniques**, load-bearing but not themselves law [1][2][12][13][16].

The core message: MRM gives AI governance a rigorous, auditable evaluation spine. The most important disciplines are **independent validation with genuine effective challenge**, **evaluation across benchmarks and adversarial red-teaming**, **continuous post-deployment monitoring for drift and incidents**, and **documentation that travels with the model** [7][8][12][19]. Confidence is **Medium**: the law and the MRM instruments are firmly sourced, but the AI-Act-to-MRM mapping is a reasoned best-practice crosswalk, not an official one, and GenAI evaluation science is young and contested [20][23].

# Key Takeaways

- **MRM is a mature banking discipline now generalised to AI.** SR 11-7 (2011) and PRA SS1/23 (2023) define model risk and require development rigour, **independent validation** and **governance** — the template modern AI evaluation reuses [7][8]. *(Best practice; the banking versions are supervisory obligations for regulated firms.)*
- **"Effective challenge" is the heart of validation:** critical analysis by objective, competent, independent parties with authority and incentive to change the model — the antidote to over-reliance on a single team's confidence [8]. *(Best practice.)*
- **AI Act Art. 9 makes a lifecycle risk-management system a legal obligation** for high-risk AI: iterative identification, estimation and evaluation of risks, adoption of risk measures, and **testing** against pre-defined metrics and thresholds [1]. *(Legal obligation.)*
- **AI Act Art. 15 makes accuracy, robustness and cybersecurity legal obligations**, expressly including resilience to **adversarial** manipulation — data/model poisoning, adversarial (evasion) examples, and confidentiality attacks [1]. *(Legal obligation.)*
- **AI Act Art. 55 obliges providers of GPAI models with systemic risk to run model evaluations including adversarial testing (red-teaming)**, mitigate systemic risk, ensure cybersecurity and report serious incidents; the **GPAI Code of Practice** operationalises this pending harmonised standards [1][2][3]. *(Legal obligation + voluntary code.)*
- **Evaluation is plural, not a single number.** Robust practice combines **capability/quality benchmarks** (e.g. HELM's multi-metric approach), **red-teaming** (manual and automated/model-generated), **adversarial-robustness** testing, and, for frontier models, **dangerous-capability / extreme-risk** evaluations [20][21][22]. *(Best practice.)*
- **Static evaluation is insufficient; models drift.** Continuous monitoring of inputs, performance and outcomes (back-testing) is required to catch data/concept drift and emerging failure — the "ongoing monitoring" leg of validation [7][8][12]. *(Best practice; Art. 9/Art. 72 monitoring duties for high-risk.)*
- **Documentation must travel with the model.** **Model cards** (intended use, metrics, limitations, disaggregated performance) and **system cards** are the consensus artefacts that make evaluation auditable and support AI Act technical documentation [13][19]. *(Best practice; supports the Art. 11 obligation.)*
- **The UK route is regulator-led.** There is no horizontal UK AI statute; the PRA's SS1/23 governs model risk for banks, and the **AI Security Institute (AISI)** conducts state-backed frontier-model evaluations (and publishes the open-source **Inspect** framework) rather than certifying compliance [6][10][11]. *(Regulatory interpretation.)*

# Purpose

This document supports engineering, data-science, model-validation, risk and compliance teams who must (a) build a **model risk management** capability for AI systems; (b) design an **evaluation programme** — benchmarks, red-teaming, adversarial-robustness testing and drift monitoring — proportionate to risk; (c) run **independent validation** with effective challenge and produce auditable **model/system cards**; and (d) map all of this onto the **EU AI Act** obligations in Arts. 9, 15 and 55 and onto voluntary frameworks (NIST AI RMF, ISO/IEC 23894). It presupposes `ai-governance-foundations` (the framework landscape), `ai-act-foundations` and `ai-act-high-risk` (the law), and `ai-act-gpai` (the GPAI systemic-risk regime this document's evaluation methods serve).

# Scope

**In scope:** The MRM lifecycle (identification/inventory, measurement, validation, monitoring, governance); the banking MRM lineage (SR 11-7 / SR 26-2; PRA SS1/23) and its generalisation to AI/GenAI; independent model validation and effective challenge; conceptual-soundness review, outcomes analysis and back-testing; model-evaluation methods (capability and quality benchmarking, manual and automated red-teaming, adversarial-robustness testing, dangerous-capability/extreme-risk evaluation); drift and performance monitoring; documentation (model cards, system cards, evaluation reports); and how these operationalise AI Act Arts. 9, 15 and 55 and the GPAI Code of Practice, with reference to NIST AI RMF, its Generative AI Profile and ISO/IEC 23894.

**Out of scope (covered elsewhere):** The AI Act risk tiers, timeline and penalties → `ai-act-foundations`; high-risk classification and conformity-assessment mechanics → `ai-act-high-risk`; the GPAI systemic-risk classification threshold and Code of Practice detail → `ai-act-gpai`; the AI management system (AIMS) clauses and certification → `ai-governance-iso-42001`; privacy/security threat modelling (LINDDUN, STRIDE) → `privacy-threat-modelling`; GDPR DPIA methodology → `dpia-methodology`. Fairness/bias auditing and explainability are touched on only where they are evaluation targets; a dedicated treatment is a separate backlog item.

**Assumptions:** The reader has read `ai-governance-foundations` and `ai-act-foundations`. "Model" is used in the broad supervisory sense (SR 11-7 / SS1/23): a quantitative method, system or approach that applies statistical, economic, financial, or mathematical theories, techniques and assumptions to process inputs into outputs — which expressly includes AI/machine-learning models [7][8]. Where an AI system processes personal data, the GDPR applies in parallel (see `dpia-methodology`).

# Definitions

*Shared terms (AI system, GPAI model, high-risk AI system, human oversight, GPAI systemic risk, trustworthy AI) are in `GLOSSARY.md`. Only MRM/evaluation-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Model risk | The potential for adverse consequences (financial loss, harm, poor decisions, reputational or legal damage) from decisions based on incorrect or misused model outputs; it arises from fundamental errors and from use outside a model's intended purpose. | [7][8] |
| Model risk management (MRM) | The governance, policies, controls and lifecycle processes an organisation uses to identify, measure, monitor and mitigate model risk. | [7][8] |
| Effective challenge | Critical analysis by objective, informed parties who are independent of model development, technically competent, and have the authority and incentive to identify limitations and require change. | [8] |
| Model validation | The set of processes and activities that verify a model works as intended: evaluation of conceptual soundness, ongoing monitoring, and outcomes analysis (including back-testing). | [7][8] |
| Benchmark (model evaluation) | A standardised task-and-metric suite for measuring model capability, quality or safety; robust practice reports **multiple** metrics across many scenarios rather than a single score (e.g. the HELM approach). | [21] |
| Red-teaming (AI) | Structured adversarial testing that deliberately elicits harmful, unsafe or policy-violating model behaviour; performed manually and, increasingly, with automated/model-generated adversarial inputs. | [22] |
| Adversarial robustness | A model's resilience to inputs crafted to cause failure or manipulation — data/model poisoning, evasion (adversarial examples), and model-confidentiality/extraction attacks. | [1][13] |
| Model / concept drift | Degradation of model performance over time as production data or the input-output relationship diverges from the training distribution; detected by ongoing monitoring and back-testing. | [7][12] |
| Model card | A short, standardised document accompanying a trained model that states intended use, evaluation data, metrics, **disaggregated** performance and known limitations. | [19] |
| System card | Documentation describing an assembled AI **system** (model(s) plus surrounding safeguards, filters and human oversight), its evaluations and residual risks — broader than a single model card. | [13] |
| Dangerous-capability / extreme-risk evaluation | Evaluation designed to detect whether a (frontier) model possesses capabilities that could enable large-scale harm (e.g. cyber-offence, CBRN uplift) or dangerous propensities such as deception. | [20] |

# Background

Model risk management is a **banking** invention. As statistical and quantitative models spread through pricing, capital, credit and trading, supervisors saw that a wrong or misused model could cause losses as surely as a bad loan. The US Federal Reserve and OCC codified the response in **SR 11-7, "Supervisory Guidance on Model Risk Management" (4 April 2011)**, which defined *model* and *model risk* broadly, and set three pillars: (1) robust model **development, implementation and use**; (2) sound model **validation**; and (3) **governance, policies and controls** — with **"effective challenge"** as the connective idea [8]. The UK's Prudential Regulation Authority issued its own principles-based expectation in **Supervisory Statement SS1/23, "Model risk management principles for banks" (May 2023, effective 17 May 2024)**, built on five principles: model identification and risk classification; governance; development, implementation and use; **independent validation**; and model-risk mitigation — and, critically, it expressly brings **AI/machine-learning models within scope** [7]. *(The US guidance has since moved on: SR 11-7 and SR 21-8 were revised and superseded by the inter-agency **SR 26-2, "Revised Guidance on Model Risk Management" (17 April 2026)**, which keeps the same primitives but adopts a more explicitly risk-based, proportionate posture for larger banks [9].)*

Two forces pulled this discipline out of banking and into AI generally. First, **machine learning and generative AI** introduced failure modes — drift, opacity, bias, hallucination, prompt injection, jailbreaks, data leakage and dangerous emergent capabilities — that a single accuracy figure cannot capture, prompting a research field of **model evaluation**: multi-metric benchmarking (e.g. **HELM** [21]), **red-teaming** (manual and automated/model-generated [22]), sociotechnical evaluation [23], and **dangerous-capability / extreme-risk** evaluation for frontier models [20]. Second, **regulation made evaluation mandatory**: the EU AI Act turned risk management (Art. 9), robustness/cybersecurity (Art. 15) and — for GPAI with systemic risk — model evaluation and adversarial testing (Art. 55) into legal obligations [1]. In the UK, the **AI Security Institute (AISI)** now performs state-backed frontier-model evaluations and maintains the open-source **Inspect** evaluation framework, giving the UK a technical, testing-led posture rather than a statutory one [10][11]. This document sits where the banking discipline, the AI-evaluation science and the AI Act meet.

# Legal Framework

Model risk management is, in itself, **best practice** — a discipline and a set of supervisory expectations. Its legal force comes from two directions: **prudential regulation** for regulated financial firms (binding on them), and the **EU AI Act** for AI providers/deployers generally. This section states the binding obligations plainly and keeps the voluntary methods distinct.

- **EU AI Act (Regulation (EU) 2024/1689)** — binding EU law. For **high-risk** AI it requires a **risk-management system (Art. 9)** and **accuracy, robustness and cybersecurity (Art. 15)**; for **GPAI models with systemic risk** it requires **model evaluation including adversarial testing, systemic-risk assessment and mitigation, cybersecurity and serious-incident reporting (Art. 55)**, with the **GPAI Code of Practice (Art. 56)** as an approved means of demonstrating compliance pending harmonised standards [1][2]. These duties are the reason AI providers must operate MRM-grade evaluation.
- **UK prudential regulation** — the PRA's **SS1/23** is a supervisory statement binding in practice on the banks, building societies and PRA-designated investment firms within its scope; it is **not** a horizontal AI law, but it is the UK's most developed *model-risk* rulebook and it covers AI/ML models [7]. The US **SR 11-7 → SR 26-2** guidance plays the equivalent role for US banking supervision [8][9].
- **Voluntary frameworks and techniques** — **ISO/IEC 23894** (AI risk-management guidance), the **NIST AI RMF** and its **Generative AI Profile**, benchmarking, red-teaming, adversarial-robustness testing and model/system cards are **not law**; they are the recognised means of meeting the above in an auditable way [12][13][16][19].

## Relevant Articles

*The AI Act articles are stated fully in `ai-act-high-risk` and `ai-act-gpai`; listed here as the obligations MRM and model evaluation operationalise.*

| Article | Obligation | Source |
|---------|------------|--------|
| AI Act Art. 9 | Establish, implement, document and maintain a **continuous, iterative risk-management system** across the high-risk AI lifecycle: identify/estimate/evaluate risks, adopt risk-management measures, and **test** against pre-defined metrics and thresholds. | [1] |
| AI Act Art. 15 | Design high-risk AI for appropriate **accuracy** (declared in the instructions for use), **robustness** (resilience to errors, faults, inconsistencies; redundancy) and **cybersecurity** (resilience to data/model poisoning, adversarial examples/evasion, and confidentiality attacks). | [1] |
| AI Act Art. 55 | Providers of **GPAI models with systemic risk** must perform **model evaluation including adversarial testing (red-teaming)**, assess and mitigate systemic risks, ensure an adequate level of **cybersecurity**, and track and report **serious incidents**. | [1] |
| AI Act Art. 56 | The **GPAI Code of Practice** as a means for providers to demonstrate compliance with Arts. 53 and 55 pending harmonised standards. | [1][2] |
| AI Act Art. 72 | Post-market **monitoring** by providers of high-risk AI — the legal hook for ongoing performance/drift monitoring. | [1] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| AI Act Recital 65 area | The risk-management system is a **continuous iterative process** run throughout the lifecycle, requiring regular review and updating — recitals aid construction but are not binding. | [1] |
| AI Act Recital 76 area | Cybersecurity of high-risk AI must address **AI-specific** attack vectors (data poisoning, model poisoning, adversarial examples, confidentiality attacks) — informs the reading of Art. 15. | [1] |
| AI Act Recital 114 area | GPAI systemic-risk providers should perform **adversarial testing / red-teaming** and risk assessment; interpretive support for Art. 55. | [1] |

## Relevant Case Law

**Not Applicable.** No court has yet construed AI Act Arts. 9, 15 or 55; the high-risk and GPAI obligations have staggered application dates in 2025–2027 (as amended by the Digital Omnibus — see `ai-act-foundations`), so no CJEU judgment interprets them. The MRM supervisory instruments (SR 11-7 / SR 26-2, PRA SS1/23) are prudential guidance, not statutes construed by courts. Interpretive weight rests on the Regulation's text and recitals, forthcoming Commission guidance and harmonised standards, and supervisory practice [1][7][8].

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **European Commission / AI Office:** treats model evaluation and adversarial testing as central to GPAI systemic-risk compliance; the **GPAI Code of Practice** (final text published 10 July 2025) contains a **Safety and Security** chapter operationalising Art. 55 — model evaluations, red-teaming, systemic-risk assessment and incident reporting — and the Commission's **guidelines on the scope of GPAI obligations (18 July 2025)** clarify who must comply [2][3][4]. *(Regulatory interpretation + voluntary code.)*
- **PRA (UK):** SS1/23 frames model risk as a risk discipline in its own right, expects a firm-wide **model inventory** and **risk-tiering**, **independent validation** proportionate to tier, and board-level accountability; it explicitly anticipates **AI/ML models** and stresses ongoing monitoring as models and data evolve [7]. *(Regulatory interpretation; binding on in-scope firms.)*
- **US banking agencies:** SR 11-7's "effective challenge" and three-pillar structure remain the reference model; **SR 26-2 (2026)** retains them while emphasising **proportionality** and a **risk-based** application scaled to a bank's model materiality and complexity [8][9]. *(Regulatory interpretation; binding on in-scope US banks.)*
- **ICO (UK):** expects organisations using AI to assess risks (including accuracy, bias and explainability), test and monitor models, and document decisions — framed as existing data-protection obligations rather than new AI-specific ones [5]. *(Regulatory interpretation.)*
- **UK Government (DSIT) and AISI:** the "pro-innovation" approach declines a horizontal statute; the **AI Security Institute** supplies capability by **testing** frontier models and open-sourcing evaluation tooling (**Inspect**), not by certifying compliance — so evaluation practice, not a certificate, is the UK yardstick [6][10][11]. *(Regulatory interpretation.)*
- **Interpretive caution:** conformance to NIST AI RMF, ISO/IEC 23894 or a banking MRM standard is **evidence of diligence, not a legal safe harbour** under the AI Act; regulators assess actual compliance with Arts. 9/15/55, for which a validation report or benchmark score is supporting — not conclusive — proof [1][12][16]. *(Regulatory interpretation.)*

# Technical Considerations

This section sets out the MRM lifecycle and the evaluation toolkit. Unless an AI Act article is cited, the practices described are **best practice** (framework/consensus), not legal obligations.

**1. Identification and inventory.** Maintain a firm-wide **model inventory** recording each model's purpose, owner, materiality/risk tier, data, dependencies, and AI Act role (provider/deployer) and tier. SS1/23 Principle 1 (identification and risk classification) and SR 11-7 both make this the precondition for every other control; it is also what makes AI Act Art. 9 risk management and Art. 11 documentation tractable [1][7][8]. *(Best practice; supports legal obligation.)*

**2. Measurement (risk assessment).** Apply a structured AI risk-assessment method — **ISO/IEC 23894** (an AI-specific application of ISO 31000) and the **NIST AI RMF** *Map/Measure* functions [12][14] — to estimate and evaluate risks (performance, robustness, security, bias, misuse, systemic) against pre-defined metrics and thresholds, as Art. 9 requires for high-risk systems [1][16]. Terminology should follow **ISO/IEC 22989** to keep assessments interoperable [18]. *(Best practice; Art. 9 measurement is a legal obligation for high-risk.)*

**3. Independent validation (the core).** Validation, per SR 11-7, has three components, all transferable to AI [8]:

- **Conceptual-soundness review** — is the design, methodology, data and assumption set appropriate for the intended use? For ML this includes data-provenance and representativeness review, leakage checks, and target/label validity.
- **Ongoing monitoring** — confirm the model still works in production (see §5).
- **Outcomes analysis / back-testing** — compare model outputs against actual outcomes or held-out ground truth.

The decisive quality condition is **effective challenge**: validators must be **independent** of development, technically competent, and empowered to force change [8]. SS1/23 Principle 4 requires validation **proportionate to the model's risk tier** and independent of the development team [7]. *(Best practice; independent validation is a supervisory obligation for regulated firms.)*

**4. Evaluation methods (measurement, made concrete).** No single metric suffices; combine:

- **Capability & quality benchmarks** — standardised task suites reporting **multiple** metrics (accuracy, calibration, robustness, fairness, efficiency, toxicity) across many scenarios, in the spirit of **HELM**, rather than one leaderboard number [21].
- **Red-teaming** — structured adversarial probing to elicit harmful or policy-violating behaviour; increasingly **automated** using models to generate adversarial inputs at scale, complementing manual expert red teams [22]. Art. 55 makes adversarial testing a **legal** obligation for GPAI-systemic-risk providers [1].
- **Adversarial-robustness testing** — evaluate resilience to **data/model poisoning**, **evasion (adversarial examples)**, prompt injection/jailbreaks and **model-extraction/confidentiality** attacks — the exact vectors Art. 15 names [1].
- **Dangerous-capability / extreme-risk evaluation** — for frontier/GPAI models, test for capabilities (e.g. cyber-offence, CBRN uplift) and propensities (e.g. deception) that could enable large-scale harm [20].
- **Sociotechnical evaluation** — assess the model **in context** (with its safeguards, users and deployment), because harm is a property of the system and its use, not the model alone [23].

*(Benchmarking/red-teaming are best practice generally, and a legal obligation under Art. 55 for GPAI systemic-risk providers [1].)*

**5. Monitoring (models drift).** Static pre-deployment evaluation decays. Instrument production for **input drift** (distribution shift), **performance/outcome drift** (via back-testing against ground truth), **calibration** and **incident** signals, with thresholds that trigger revalidation or rollback — the "ongoing monitoring" leg of validation and the substance of AI Act Art. 72 post-market monitoring [1][7][12]. *(Best practice; Art. 72 monitoring is a legal obligation for high-risk providers.)*

**6. Governance and documentation.** Wrap the above in clear roles (a Three-Lines split of ownership / oversight / independent validation), policies, a validation-report standard, and change control. Produce **model cards** (intended use, evaluation data, disaggregated metrics, limitations [19]) and **system cards** (the assembled system, its safeguards and residual risk [13]) as pipeline outputs, so that AI Act Art. 11 technical documentation and Art. 15 accuracy declarations are by-products rather than retrofits [1]. The **NIST AI RMF Playbook** supplies concrete, function-level actions to populate this governance layer [15]. *(Best practice; supports Art. 11 legal obligation.)*

# Hosting Considerations

- **Where models are hosted shapes who can evaluate them.** For a **self-hosted / open-weights** model the deployer can run white-box evaluations, adversarial-robustness and drift monitoring directly; for a **hosted API / foundation-model** dependency, the deployer is often limited to **black-box** evaluation and must rely on the provider's **model/system card** and evaluations — allocate these responsibilities explicitly in the AI value chain (mirroring the shared-responsibility model) [1][13][19]. *(Best practice; the provider/deployer split is a legal question under the AI Act.)*
- **Monitoring and logging must live in the hosting environment.** Drift metrics, evaluation results and inference logs needed for outcomes analysis and Art. 12 record-keeping should be captured where the model runs, honouring GDPR storage-limitation and security where personal data is involved (see `dpia-methodology`) [1]. *(Best practice; Art. 12 logging is a legal obligation for high-risk.)*
- **Evaluation compute is a real dependency.** Adversarial testing and dangerous-capability evaluations of large models are compute- and expertise-intensive; budget for a dedicated, isolated evaluation environment separate from production [20][22]. *(Best practice.)*

# Game Hosting Considerations

- **Most game AI is minimal-risk**, so full MRM-grade validation is rarely mandatory; a **proportionate** evaluation baseline (regression benchmarks, output filtering, abuse monitoring) is appropriate, concentrating effort on higher-impact features [7][12]. *(Best practice.)*
- **Player-facing GenAI (NPC dialogue, UGC/content tools)** should be red-teamed for toxicity, prompt-injection, jailbreaks and unsafe content, and monitored for drift as models are swapped or fine-tuned — apply the NIST **Generative AI Profile** controls [13][22]. *(Best practice.)*
- **Escalation triggers.** Anti-cheat, matchmaking or recommendation models that materially affect access, spend or fairness — and any biometric/emotion features — can cross into higher-risk tiers, at which point Art. 9/Art. 15 duties and formal independent validation become material [1]. *(Legal obligation once triggered.)*

# AI Considerations

*This document is itself about AI evaluation; the "AI Considerations" here concern how MRM interlocks with the AI-regulation and standards stack.*

- **MRM operationalises AI Act Arts. 9/15/55.** Independent validation and testing satisfy the Art. 9 "testing against metrics and thresholds" duty; adversarial-robustness testing satisfies the Art. 15 cybersecurity/robustness duty; model evaluation and red-teaming satisfy the Art. 55 GPAI duty [1]. The mapping is a **best-practice crosswalk**, not an official one — harmonised European standards (CEN-CENELEC) and the GPAI Code of Practice will formalise expectations [2][4]. *(Best practice; underlying duties are legal.)*
- **Classic MRM needs AI-specific extension.** SR 11-7/SS1/23 assume relatively stable, interpretable models; ML adds **drift**, opacity, **adversarial** manipulation, and — for GenAI — hallucination, jailbreaks and **emergent dangerous capabilities**. Extend validation with data-centric checks, continuous monitoring, red-teaming and (for frontier models) dangerous-capability evaluation [13][20][22]. *(Best practice.)*
- **Evaluation is sociotechnical.** Benchmarks measure the model; **safety is a property of the system in use**. Combine model-level benchmarks with system-level and human-oversight evaluation to avoid a false sense of assurance from a good benchmark score [21][23]. *(Best practice.)*
- **Sits inside the AIMS.** In an ISO/IEC 42001 management system, this MRM/evaluation capability populates the Clause 6 risk assessment and the Annex A life-cycle **verification/validation** and **event-logging** controls; it is the technical engine of the management shell described in `ai-governance-iso-42001` [16][17]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** (AI Act / prudential duty) / **BEST PRACTICE** (framework/consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

1. **Build a model inventory and risk-tier it.** Every model with purpose, owner, data, dependencies, AI Act role/tier and materiality. Without it you cannot scope validation or Art. 9 risk management. *(BEST PRACTICE; supports OBLIGATION.)* [1][7][8]
2. **Stand up independent validation with real effective challenge.** Separate validators from developers; give them competence, authority and the mandate to block deployment. *(BEST PRACTICE; OBLIGATION for regulated firms via SS1/23.)* [7][8]
3. **Validate on all three legs:** conceptual soundness (design, data, assumptions), ongoing monitoring, and outcomes analysis/back-testing. *(BEST PRACTICE.)* [8]
4. **Design a proportionate evaluation battery:** multi-metric benchmarks, manual + automated red-teaming, adversarial-robustness tests (poisoning, evasion, extraction), and — for frontier/GPAI — dangerous-capability and sociotechnical evaluation. *(BEST PRACTICE; OBLIGATION for GPAI-systemic-risk via Art. 55, and for high-risk robustness via Art. 15.)* [1][20][21][22][23]
5. **Set metrics and thresholds up front, and test against them** — the Art. 9 discipline — with clear pass/fail gates and documented residual risk. *(OBLIGATION for high-risk via Art. 9; BEST PRACTICE otherwise.)* [1][12]
6. **Instrument continuous monitoring** for input/performance/outcome drift with revalidation and rollback triggers; treat this as Art. 72 post-market monitoring for high-risk. *(OBLIGATION for high-risk via Art. 72; BEST PRACTICE otherwise.)* [1][7][12]
7. **Document with model cards and system cards** generated by the pipeline; make them the source for Art. 11 technical documentation and the Art. 15 accuracy declaration. *(BEST PRACTICE; OBLIGATION-adjacent via Arts. 11, 15.)* [1][13][19]
8. **Adopt a recognised method and map it to the law:** ISO/IEC 23894 + NIST AI RMF (and Generative AI Profile) crosswalked to Arts. 9/15/55. *(BEST PRACTICE.)* [1][12][13][16]
9. **For GPAI systemic-risk providers, follow the GPAI Code of Practice Safety & Security chapter** for model evaluation, red-teaming, systemic-risk assessment and serious-incident reporting. *(OBLIGATION via Art. 55; the Code is a voluntary means of demonstrating it.)* [1][2][3]
10. **Use shared, open evaluation tooling where possible** (e.g. AISI's Inspect) to make evaluations reproducible and auditable, and to align with emerging state-of-the-art. *(EDITORIAL RECOMMENDATION.)* [11][15]

## Mapping table — banking MRM ↔ AI evaluation ↔ EU AI Act

*Best-practice crosswalk (not an official mapping). AI Act articles are legal obligations; the MRM/evaluation elements are means of meeting and evidencing them [1][7][8].*

| MRM primitive (SR 11-7 / SS1/23) | Modern AI/GenAI technique | EU AI Act hook |
|----------------------------------|----------------------------|----------------|
| Model inventory & risk classification | AI system inventory + risk tiering | Art. 9 risk management; Art. 11 documentation [1][7] |
| Robust development, implementation & use | Data-centric checks; leakage/representativeness review | Art. 10 data governance; Art. 9 [1][8] |
| Conceptual-soundness validation | Design/data/assumption review; benchmarking (HELM-style) | Art. 9 testing; Art. 15 accuracy [1][21] |
| Effective challenge / independent validation | Independent eval team; red-team vs blue-team | Art. 9; Art. 14 oversight [1][8] |
| Outcomes analysis / back-testing | Held-out & production ground-truth comparison | Art. 9; Art. 72 monitoring [1][8] |
| Ongoing monitoring | Drift/calibration/incident monitoring | Art. 72 post-market monitoring [1][12] |
| — (new for AI) | Adversarial-robustness testing (poisoning, evasion, extraction) | Art. 15 robustness & cybersecurity [1] |
| — (new for GenAI) | Red-teaming + dangerous-capability evaluation | Art. 55 GPAI model evaluation & adversarial testing [1][20][22] |
| Governance, policies & documentation | Model cards / system cards; validation reports | Art. 11 documentation; Art. 17 QMS [1][13][19] |

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | No model inventory; models untracked and unvalidated | High | High | AI Act Art. 9; SS1/23 P1 [1][7] | Firm-wide inventory with risk tiers and owners | Medium |
| R2 | Validation not independent; no effective challenge | Medium | High | SR 11-7; SS1/23 P4 [7][8] | Separate, empowered validation function with authority to block | Low |
| R3 | Over-reliance on a single benchmark score | Medium | High | Multi-metric evaluation needed [21] | Benchmark battery + red-teaming + sociotechnical eval | Medium |
| R4 | Adversarial vulnerabilities untested (poisoning, evasion, extraction) | Medium | High | AI Act Art. 15 [1] | Adversarial-robustness testing in the eval battery | Medium |
| R5 | GPAI systemic risk under-evaluated (no red-teaming) | Medium | High | AI Act Art. 55 [1][2] | Follow GPAI Code Safety & Security chapter; red-team | Medium |
| R6 | Model drift undetected post-deployment | High | High | AI Act Art. 72; validation monitoring [1][12] | Continuous drift/outcome monitoring; revalidation triggers | Low |
| R7 | Documentation absent; not audit-ready | Medium | High | AI Act Art. 11 [1] | Auto-generated model cards / system cards / eval reports | Low |
| R8 | Treating a framework/benchmark as a legal safe harbour | Medium | High | Frameworks are evidence, not conformity [1][16] | Map methods to actual Art. 9/15/55 duties; keep audit trail | Low |
| R9 | Classic MRM applied unchanged to GenAI (misses hallucination/jailbreak/emergent capability) | Medium | High | AI-specific failure modes [13][20] | Extend validation with GenAI red-teaming & capability evals | Medium |
| R10 | Black-box dependency on a third-party model with opaque evaluations | Medium | Medium | Value-chain allocation [1][13] | Contract for model/system cards; run black-box evals; monitor | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory & tiering:** Build the model/AI-system inventory; classify by risk/materiality and AI Act role/tier. *Effort:* Medium. *Depends on:* `ai-act-foundations` triage; `ai-governance-foundations` operating model.
- **Phase 1 — Governance & standards:** Stand up the validation function (independent, with effective challenge); adopt ISO/IEC 23894 + NIST AI RMF; define a validation-report and model-card standard. *Effort:* Medium–High.
- **Phase 2 — Validation & evaluation:** Run conceptual-soundness review; build the evaluation battery (benchmarks, red-teaming, adversarial-robustness) with pre-set metrics/thresholds; add dangerous-capability evals for frontier/GPAI. *Effort:* High.
- **Phase 3 — Monitoring:** Instrument drift/outcome/incident monitoring with revalidation and rollback triggers (Art. 72). *Effort:* High.
- **Phase 4 — Documentation & assurance:** Auto-generate model/system cards and evaluation reports; map to Arts. 9/11/15/55; for GPAI-systemic-risk, align to the GPAI Code Safety & Security chapter. *Effort:* Medium–High.
- **Phase 5 — Continual improvement:** Track evaluation science, AISI/Inspect tooling, harmonised standards and Code updates; re-validate on material change. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No MRM; models deployed without independent validation or monitoring. | No inventory; single-metric sign-off. |
| 2 | Managed | Inventory and basic validation exist; ad hoc evaluation. | Model inventory; some pre-deployment testing. |
| 3 | Defined | Independent validation with effective challenge; documented evaluation battery and thresholds. | Validation reports; benchmarks + red-teaming; model cards. |
| 4 | Quantitatively Managed | Continuous drift/outcome monitoring with metrics; adversarial and (where relevant) capability evals operating. | Drift dashboards; adversarial-robustness KPIs; revalidation triggers. |
| 5 | Optimising | MRM integrated with the AIMS and AI Act mapping; sociotechnical + frontier evaluation; continual improvement. | Art. 9/15/55 crosswalk maintained; GPAI Code alignment; open eval tooling. |

# Audit Questions

1. Is there a complete model/AI-system inventory with risk tiers, owners and AI Act role/tier? *(AI Act Art. 9; SS1/23 P1 [1][7].)*
2. Is model validation **independent** of development, with genuine **effective challenge** and authority to block deployment? *(SR 11-7; SS1/23 P4 [7][8].)*
3. Does validation cover conceptual soundness, ongoing monitoring **and** outcomes analysis/back-testing? *([8].)*
4. What evaluation battery is run — benchmarks, red-teaming, adversarial-robustness — and are metrics and thresholds set in advance? *(Art. 9; Art. 15 [1][21][22].)*
5. For GPAI models with systemic risk, is model evaluation **including adversarial testing** performed and documented, per Art. 55 and the GPAI Code? *(Art. 55 [1][2].)*
6. Are adversarial/cybersecurity attack vectors (poisoning, evasion, extraction) tested, per Art. 15? *(Art. 15 [1].)*
7. Is production monitoring for drift/outcomes/incidents in place, with revalidation triggers (Art. 72)? *([1][12].)*
8. Are model cards / system cards and evaluation reports generated and retained to support Art. 11 documentation? *([13][19]; Art. 11 [1].)*
9. Is the MRM method mapped to a recognised framework (ISO/IEC 23894, NIST AI RMF) and to the AI Act, and treated as evidence rather than a safe harbour? *([12][16].)*

# Implementation Checklist

- [ ] Model/AI-system inventory built and risk-tiered (role, tier, materiality).
- [ ] Independent validation function established with effective challenge and stop authority.
- [ ] Conceptual-soundness review standard defined and applied.
- [ ] Evaluation battery defined: multi-metric benchmarks + manual/automated red-teaming + adversarial-robustness tests.
- [ ] Dangerous-capability / sociotechnical evaluation applied to frontier/GPAI systems.
- [ ] Pre-defined metrics and thresholds with pass/fail gates (Art. 9).
- [ ] Adversarial/cybersecurity vectors tested: poisoning, evasion, extraction (Art. 15).
- [ ] GPAI systemic-risk providers aligned to the GPAI Code Safety & Security chapter (Art. 55).
- [ ] Continuous drift/outcome/incident monitoring with revalidation & rollback triggers (Art. 72).
- [ ] Model cards / system cards / validation reports auto-generated and retained (Art. 11).
- [ ] Method mapped to ISO/IEC 23894 + NIST AI RMF and crosswalked to Arts. 9/15/55.
- [ ] Evaluation tooling and standards watch-list maintained (AISI/Inspect; CEN-CENELEC; Code updates).

# References

*All external links verified live on 2026-07-11 (`sources_verified`) using `curl -L -A "Mozilla/5.0 (compliance-link-checker)"`. NIST PDFs answer GET (not HEAD). Bank of England and US Federal Reserve pages serve 200 to a browser user-agent. arXiv abstract titles were confirmed against the cited papers. ISO clause/control text and the full text of SR 11-7 / SR 26-2 / SS1/23 reside in the source documents themselves.*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** EUR-Lex, ELI (Arts. 9, 11, 15, 55, 56, 72; Recitals on lifecycle risk management, AI-specific cybersecurity and GPAI adversarial testing). https://eur-lex.europa.eu/eli/reg/2024/1689/oj

## Regulatory Guidance

*Includes prudential supervisory guidance (PRA, US banking agencies), which is binding on regulated firms, and the GPAI Code of Practice (a voluntary co-regulatory instrument).*

- [2] **General-Purpose AI Code of Practice — final text** (published 10 July 2025; Safety and Security chapter operationalising Art. 55). AI Office multi-stakeholder process. https://code-of-practice.ai/
- [3] **The General-Purpose AI Code of Practice.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/contents-code-gpai
- [4] **Guidelines on the scope of obligations for providers of general-purpose AI models under the AI Act** (18 July 2025). European Commission. https://digital-strategy.ec.europa.eu/en/library/guidelines-scope-obligations-providers-general-purpose-ai-models-under-ai-act
- [5] **Artificial intelligence — guidance for organisations.** ICO (UK). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/artificial-intelligence/
- [6] **A pro-innovation approach to AI regulation.** UK Government (DSIT), GOV.UK. https://www.gov.uk/government/publications/a-pro-innovation-approach-to-ai-regulation
- [7] **Supervisory Statement SS1/23 — Model risk management principles for banks** (May 2023; effective 17 May 2024; AI/ML models in scope). Bank of England / Prudential Regulation Authority. https://www.bankofengland.co.uk/prudential-regulation/publication/2023/may/model-risk-management-principles-for-banks-ss
- [8] **SR 11-7 Attachment — Supervisory Guidance on Model Risk Management** (4 April 2011; model risk, three pillars, effective challenge). Board of Governors of the Federal Reserve System / OCC. https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107a1.pdf
- [9] **SR 26-2 — Revised Guidance on Model Risk Management** (17 April 2026; supersedes SR 11-7 and SR 21-8; risk-based, proportionate). Federal Reserve / OCC / FDIC. https://www.federalreserve.gov/supervisionreg/srletters/sr2602.htm
- [10] **AI Security Institute (AISI)** — state-backed frontier-model evaluation and testing. UK Government. https://www.aisi.gov.uk/
- [11] **Inspect — an open-source framework for large language model evaluations.** UK AI Security Institute. https://inspect.aisi.org.uk/

## Standards

- [12] **Artificial Intelligence Risk Management Framework (AI RMF 1.0), NIST AI 100-1** (Jan 2023; Govern/Map/Measure/Manage). NIST. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf
- [13] **AI RMF: Generative Artificial Intelligence Profile, NIST AI 600-1** (26 July 2024; GenAI risks, red-teaming, content integrity). NIST. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf
- [14] **AI Risk Management Framework (AI RMF 1.0) — overview.** NIST. https://www.nist.gov/itl/ai-risk-management-framework
- [15] **NIST AI RMF Playbook.** NIST AI Resource Center (AIRC). https://airc.nist.gov/airmf-resources/playbook/
- [16] **ISO/IEC 23894:2023 — Artificial intelligence — Guidance on risk management.** ISO/IEC. https://www.iso.org/standard/77304.html
- [17] **ISO/IEC 42001:2023 — Information technology — Artificial intelligence — Management system (AIMS).** ISO/IEC. https://www.iso.org/standard/42001
- [18] **ISO/IEC 22989:2022 — Artificial intelligence — Concepts and terminology.** ISO/IEC. https://www.iso.org/standard/74296.html

## Academic Sources

- [19] **Mitchell, M. et al., "Model Cards for Model Reporting"** (FAT* 2019; arXiv:1810.03993). https://arxiv.org/abs/1810.03993
- [20] **Shevlane, T. et al., "Model evaluation for extreme risks"** (2023; arXiv:2305.15324) — dangerous-capability evaluation for frontier models. https://arxiv.org/abs/2305.15324
- [21] **Liang, P. et al., "Holistic Evaluation of Language Models (HELM)"** (2022; arXiv:2211.09110) — multi-metric, many-scenario benchmarking. https://arxiv.org/abs/2211.09110
- [22] **Perez, E. et al., "Red Teaming Language Models with Language Models"** (EMNLP 2022; arXiv:2202.03286) — automated/model-generated red-teaming. https://arxiv.org/abs/2202.03286
- [23] **Weidinger, L. et al., "Sociotechnical Safety Evaluation of Generative AI Systems"** (2023; arXiv:2310.11986) — evaluating models in context. https://arxiv.org/abs/2310.11986

# Further Reading

*Non-authoritative or secondary; provided for orientation only.*

- NIST AI Resource Center (AIRC) — Playbook, crosswalks and evaluation resources. https://airc.nist.gov/airmf-resources/playbook/
- UK AI Security Institute — research and frontier-model testing publications. https://www.aisi.gov.uk/work

# Related Documents

- `ai-governance-foundations` — **parent**; the framework landscape (ISO/IEC 42001, NIST AI RMF, OECD Principles) this document deepens for model risk and evaluation (**prerequisite reading**).
- `ai-governance-iso-42001` — the AIMS shell whose Clause 6 risk assessment and Annex A verification/validation controls this MRM capability populates.
- `ai-act-foundations` — the EU AI Act overview, risk tiers and timeline (the law this document operationalises).
- `ai-act-high-risk` — the high-risk Arts. 9/15 duties this evaluation methodology satisfies.
- `ai-act-gpai` — the GPAI systemic-risk regime and Art. 55 model-evaluation / adversarial-testing obligations.
- `privacy-threat-modelling` — LINDDUN/STRIDE threat modelling that complements adversarial-robustness and security evaluation.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft. Deep-dive on AI model risk management and evaluation: the MRM lifecycle (inventory, measurement, independent validation with effective challenge, monitoring, governance); the banking MRM lineage (Fed SR 11-7, superseded 17 Apr 2026 by SR 26-2; PRA SS1/23) generalised to AI/GenAI; evaluation methods (multi-metric benchmarking/HELM, manual + automated red-teaming, adversarial-robustness, dangerous-capability and sociotechnical evaluation); drift monitoring; documentation via model/system cards; and a banking-MRM ↔ AI-evaluation ↔ EU AI Act (Arts. 9/15/55/72) mapping table. Binding law kept distinct from voluntary frameworks. Model Cards arXiv ID corrected to 1810.03993 during source verification. All external links verified on 2026-07-11 (Bank of England / Federal Reserve serve 200 to a browser UA; arXiv titles confirmed against papers). | — |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster C); full-repo validator/link/lint suite green; frozen in release 0.17.0. | Orchestrator (QA-verified) |
