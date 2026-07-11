---
id: ai-act-foundations
title: "EU AI Act: Foundations, Risk Tiers & Timeline"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: AI Act
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [gdpr-foundations, privacy-engineering-foundations, ai-governance-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [ai-act, eu-ai-act, gpai, high-risk-ai, prohibited-practices, ai-office, digital-omnibus]
legal_basis: Regulation (EU) 2024/1689
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | ai-act-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.6.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. The AI Act's timeline is **actively changing**: an "AI Omnibus" simplification package reached provisional agreement in May 2026 but was **not yet formally adopted** at this document's date — always confirm the current in-force dates before relying on them.

# Executive Summary

The **EU Artificial Intelligence Act (Regulation (EU) 2024/1689**, "AI Act") is the world's first comprehensive horizontal law on artificial intelligence. It **entered into force on 1 August 2024** and applies through a **phased timeline** [1][3]. It takes a **risk-based** approach, sorting AI systems into four tiers: **unacceptable risk** (prohibited), **high-risk** (strict obligations), **limited/transparency risk** (disclosure duties), and **minimal risk** (largely unregulated) [3]. It also imposes a separate regime on **general-purpose AI (GPAI) models**, with heightened duties for models posing **systemic risk** [3].

This document establishes the foundations: the risk tiers and what each requires, the GPAI regime, the governance architecture (the **European AI Office**, AI Board, Scientific Panel), the **penalty** structure, the **phased application timeline**, and the AI Act's **relationship with the GDPR**. As of this document's date, the following are already in force: **prohibited practices and AI literacy (from 2 February 2025)** and **GPAI and governance obligations (from 2 August 2025)** [3].

The most important — and most volatile — point concerns **high-risk timing**. Under the original text, most high-risk and transparency rules would apply from **2 August 2026**. However, the **"AI Omnibus"** simplification package (Commission proposal of 19 November 2025) reached a **provisional political agreement on 7 May 2026** to **postpone** high-risk obligations to **2 December 2027** (stand-alone listed use cases) and **2 August 2028** (AI as safety components in regulated products), and to shift AI-content transparency/watermarking to 2 December 2026 [4][5]. **That agreement still requires formal adoption by Parliament and Council** and is therefore treated here as a **proposal, not settled law** [5].

# Key Takeaways

- The **AI Act (Regulation (EU) 2024/1689)** entered into force **1 August 2024** and applies in phases; it is the first comprehensive horizontal AI law [1][3]. *(Legal obligation.)*
- It is **risk-based**: **unacceptable** (prohibited), **high-risk**, **limited/transparency**, and **minimal** risk [3]. *(Legal obligation.)*
- **Prohibited practices** (e.g., social scoring, certain manipulative AI, untargeted facial-image scraping, some biometric/emotion-recognition uses) and **AI literacy** duties apply from **2 February 2025** [3]. *(Legal obligation — in force.)*
- **GPAI model** obligations (transparency, copyright, technical documentation) and the **governance** framework apply from **2 August 2025**; GPAI models with **systemic risk** face additional risk-assessment and mitigation duties [3]. *(Legal obligation — in force.)*
- **High-risk** systems face the heaviest duties (risk management, data governance, logging, documentation, human oversight, robustness/cybersecurity, conformity assessment) [1][3]. *(Legal obligation.)*
- **Timeline in flux:** the **AI Omnibus** provisional agreement (7 May 2026) would postpone high-risk application to **2 Dec 2027 / 2 Aug 2028**, but **requires formal adoption** — treat as a proposal [4][5]. *(Proposal, not in force.)*
- **Penalties** are severe: up to **€35 million or 7% of worldwide annual turnover** for prohibited-practice breaches (Art. 99) [1]. *(Legal obligation.)*
- The AI Act **operates alongside the GDPR**; where AI processes personal data, both apply, and DPbDD (see `privacy-engineering-foundations`) remains required [1][2]. *(Legal obligation.)*

# Purpose

This document is the Tier 2 entry point for AI regulation. It supports legal research (mapping the risk tiers, GPAI regime and timeline), compliance planning (what applies now vs. later), and product/engineering triage (which tier a system falls into and the resulting obligations). It builds on `gdpr-foundations` and `privacy-engineering-foundations` and precedes `ai-governance-foundations`.

# Scope

**In scope:** The AI Act's purpose and scope; the four risk tiers and their core obligations; the GPAI regime (incl. systemic risk); governance (AI Office and bodies); penalties; the phased application timeline and the AI Omnibus amendments at a foundational level; the GDPR relationship.

**Out of scope (spun off to the research backlog):** The full high-risk obligations and conformity-assessment mechanics → `ai-act-high-risk`; the GPAI/systemic-risk regime and Code of Practice in depth → `ai-act-gpai`; the prohibited practices article-by-article → `ai-act-prohibited-practices`; the AI Omnibus package in detail → `digital-omnibus`; AI management systems and operational governance → `ai-governance-foundations`.

**Assumptions:** The reader has read `gdpr-foundations`. Personal-data processing by AI systems remains governed by the GDPR in parallel.

# Definitions

*Shared terms are in `GLOSSARY.md`. AI-Act-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| AI system | A machine-based system designed to operate with varying autonomy that, for explicit or implicit objectives, infers from inputs how to generate outputs (predictions, content, recommendations, decisions) that can influence environments (Art. 3(1)). | [1] |
| Provider | A person/body that develops an AI system or GPAI model, or has one developed, and places it on the market or puts it into service under its own name (Art. 3(3)). | [1] |
| Deployer | A person/body using an AI system under its authority (except personal non-professional use) (Art. 3(4)). | [1] |
| High-risk AI system | An AI system falling within Art. 6 and Annex I/III categories, subject to the Chapter III obligations. | [1][3] |
| GPAI model | A general-purpose AI model displaying significant generality, capable of performing a wide range of distinct tasks (Art. 3(63)). | [1] |
| Systemic risk | Risk specific to high-impact GPAI capabilities with significant effect on the EU market/society (Art. 3(65); Art. 51 threshold). | [1] |
| AI Office | The European Commission body overseeing GPAI and supporting AI Act implementation and enforcement. | [3] |

# Background

AI systems increasingly make or inform consequential decisions, creating risks to safety and fundamental rights that existing law addressed only partially. The EU responded with a **horizontal, risk-based** Regulation rather than sector-by-sector rules, aiming to protect health, safety and fundamental rights while supporting innovation and a single market for trustworthy AI [3]. The AI Act was adopted in 2024 with a deliberately **staggered application** to give providers, deployers and standards bodies time to prepare [1][3]. During 2025 the Commission launched a broader **simplification agenda** ("Digital Omnibus"), part of which — the **AI Omnibus** — proposes to adjust the AI Act's timeline and reduce administrative burden; that proposal was progressing through the legislature at this document's date [4][5].

# Legal Framework

The AI Act regulates AI along the value chain, placing most obligations on **providers**, with defined duties for **deployers**, importers and distributors [1]. Its structure:

- **Chapter I** — subject matter, scope, definitions (incl. the Art. 3(1) definition of "AI system").
- **Chapter II (Art. 5)** — **prohibited** AI practices.
- **Chapter III** — **high-risk** AI systems: classification (Art. 6, Annexes I & III) and obligations (risk management, data governance, technical documentation, record-keeping, transparency, human oversight, accuracy/robustness/cybersecurity, conformity assessment, registration).
- **Chapter IV (Art. 50)** — **transparency** obligations for certain systems (e.g., chatbots, deepfakes, synthetic content).
- **Chapter V** — **general-purpose AI models**, including systemic-risk models (Arts. 51–56).
- **Chapters VI–VII** — governance (AI Office, AI Board, Scientific Panel, Advisory Forum), national authorities, database.
- **Chapter XII (Arts. 99–101)** — **penalties**.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 3 | Definitions (AI system, provider, deployer, GPAI model, systemic risk). | [1] |
| Art. 5 | Prohibited AI practices (unacceptable risk). | [1] |
| Art. 6 + Annexes I, III | Classification rules for high-risk AI systems. | [1] |
| Arts. 8–15 | Core high-risk requirements (risk management, data governance, documentation, logging, transparency, human oversight, robustness/cybersecurity). | [1] |
| Art. 16 et seq. | Provider obligations for high-risk systems (incl. conformity assessment, registration). | [1] |
| Art. 50 | Transparency obligations (AI interaction disclosure; marking synthetic content/deepfakes). | [1] |
| Arts. 51–56 | GPAI models and systemic-risk obligations. | [1] |
| Art. 99 | Penalties — up to €35m or 7% of worldwide annual turnover for Art. 5 breaches; lower tiers for other breaches. | [1] |
| Art. 113 | Entry into force and staggered application dates. | [1] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 1 | Purpose — improve the internal market and promote trustworthy, human-centric AI while protecting health, safety and fundamental rights. | [1] |
| Recital 26–27 | Risk-based approach and proportionality across tiers. | [1] |
| Recital 60 area | Human oversight rationale for high-risk systems. | [1] |

## Relevant Case Law

Not Applicable at the foundational level — the AI Act is recent and its high-risk provisions are not yet fully applicable, so there is no established CJEU case law interpreting it. Interpretive weight currently rests on the Regulation's text, Commission guidance and (for personal data) GDPR case law (see `gdpr-foundations`). [1][3]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** frames the AI Act around four risk tiers and stresses that the **majority of AI systems are minimal risk** and unregulated; obligations concentrate on high-risk and prohibited categories [3]. *(Regulatory interpretation.)*
- **Transparency (Art. 50):** users must be told when they interact with AI (e.g., chatbots), and providers of generative AI must ensure AI-generated content is **identifiable** (labelling of deepfakes/synthetic content) [3]. *(Legal obligation, as interpreted.)*
- **GPAI:** providers must meet transparency and copyright duties; **systemic-risk** models require risk assessment and mitigation, supported by guidelines and a **Code of Practice** [3]. *(Regulatory interpretation.)*
- **Governance:** the **AI Office** (within the Commission), an **AI Board**, a **Scientific Panel** and an **Advisory Forum** oversee implementation and enforcement [3]. *(Regulatory interpretation.)*
- **Reform (AI Omnibus):** the Commission and co-legislators reached a **provisional agreement (7 May 2026)** to postpone high-risk application (to 2 Dec 2027 / 2 Aug 2028) and adjust content-transparency timing; this **requires formal adoption** and is not yet law [4][5]. *(Proposal — track, do not pre-implement the delay as certainty.)*

# Technical Considerations

- **Tier triage first** — determine each system's tier (prohibited / high-risk / limited / minimal); this drives every downstream obligation [1][3]. *(Legal obligation.)*
- **High-risk engineering controls** — risk-management system, **data governance** (representative, relevant, error-checked datasets), **logging/traceability**, technical documentation, **human oversight** hooks, and accuracy/robustness/**cybersecurity** by design (Arts. 8–15) [1]. *(Legal obligation.)*
- **Transparency features** — machine-readable marking of synthetic/AI-generated content and clear AI-interaction disclosure (Art. 50) [1][3]. *(Legal obligation.)*
- **GPAI documentation** — model technical documentation, training-data summaries and copyright compliance for GPAI providers [3]. *(Legal obligation.)*
- **Overlap with privacy engineering** — high-risk data-governance and logging duties should be built on the DPbDD and Art. 32 controls in `privacy-engineering-foundations`. *(Best practice.)*

# Hosting Considerations

- **Deployers vs providers** — hosting or offering an AI system may make an organisation a **deployer** (with human-oversight and use-monitoring duties) or, if branded/substantially modified, a **provider** (with the full high-risk obligations) [1]. *(Legal obligation — assess role.)*
- **Logging & retention** — high-risk systems require automatic **record-keeping**; hosting must retain logs appropriately while respecting GDPR retention limits [1]. *(Legal obligation.)*
- **Compute for GPAI** — hosting large models may engage GPAI/systemic-risk considerations for the model provider; infrastructure operators should clarify their role. *(Editorial recommendation.)*

# Game Hosting Considerations

- **Most game AI is minimal risk** — NPC behaviour, matchmaking and procedural generation typically fall in the **minimal-risk** tier with no specific AI Act obligations [3]. *(Interpretation.)*
- **Transparency triggers** — AI **chatbots/companions** and **generative** content in games engage Art. 50 disclosure/marking duties [1][3]. *(Legal obligation.)*
- **Watch for high-risk edges** — AI used for **biometric** features, emotion inference, or that could affect access to services may cross into higher tiers; assess carefully, especially where minors are involved. *(Best practice.)*

# AI Considerations

*This document is itself the AI-regulation foundation; the "AI Considerations" here concern interaction with other AI regimes.*

- **GDPR overlap** — where an AI system processes personal data, the **GDPR applies in full alongside** the AI Act; lawful basis, DPbDD, DPIAs and (for solely automated decisions) Art. 22 remain relevant [1][2]. *(Legal obligation.)*
- **AI governance/standards** — operationalising AI Act duties benefits from **ISO/IEC 42001** (AI management systems); covered in `ai-governance-foundations` [6]. *(Best practice.)*
- **Product-safety overlap** — high-risk AI embedded in regulated products interacts with EU sectoral/product-safety law (extended transition to 2 Aug 2028 under the AI Omnibus proposal) [4][5]. *(Cross-reference.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Inventory and triage AI systems** by risk tier and by role (provider/deployer). *(OBLIGATION — foundational.)* [1][3]
2. **Confirm no prohibited practices** are in use (in force since Feb 2025). *(OBLIGATION.)* [1][3]
3. **Deliver AI literacy** to staff working with AI systems. *(OBLIGATION — in force.)* [3]
4. **Meet GPAI duties** if you provide GPAI models (transparency, copyright, documentation). *(OBLIGATION — in force.)* [3]
5. **Prepare high-risk controls now** even though timing may shift — risk management, data governance, logging, oversight. *(BEST PRACTICE — obligation once applicable.)* [1]
6. **Implement Art. 50 transparency** for chatbots and synthetic content. *(OBLIGATION.)* [1][3]
7. **Track the AI Omnibus** — plan to the current legal dates; do not assume the delay until formally adopted. *(EDITORIAL RECOMMENDATION.)* [4][5]
8. **Run AI and GDPR compliance together** — DPIAs and DPbDD alongside AI Act conformity work. *(OBLIGATION + BEST PRACTICE.)* [1][2]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Operating a prohibited practice | Low | Very High | Art. 5; Art. 99 (€35m/7%) [1] | Prohibited-practice screening; legal review | Low |
| R2 | Misclassifying a high-risk system as minimal | Medium | High | Art. 6, Annex III [1] | Documented tier assessment; re-assess on change | Low |
| R3 | Missing GPAI provider obligations | Medium | High | Arts. 51–56 [1][3] | GPAI documentation, copyright, transparency | Low |
| R4 | No Art. 50 transparency for chatbots/deepfakes | Medium | Medium | Art. 50 [1][3] | AI-interaction disclosure; content marking | Low |
| R5 | Assuming the AI Omnibus delay is in force | Medium | High | Provisional agreement [4][5] | Plan to current legal dates; track adoption | Medium |
| R6 | Treating AI Act compliance as replacing GDPR | Medium | High | Parallel application [1][2] | Joint AI + data-protection programme | Low |
| R7 | Weak data governance/logging for high-risk | Medium | High | Arts. 10, 12 [1] | Data-quality controls; automatic logging | Medium |

# Implementation Roadmap

- **Phase 0 — Inventory & triage:** Catalogue AI systems; assign tier and provider/deployer role. *Effort:* Medium.
- **Phase 1 — Immediate compliance:** Prohibited-practice screening; AI literacy; GPAI duties (all already in force). *Effort:* Medium.
- **Phase 2 — Transparency:** Implement Art. 50 disclosures and synthetic-content marking. *Effort:* Medium.
- **Phase 3 — High-risk readiness:** Build risk-management, data-governance, logging, human-oversight and conformity processes ahead of the applicable date. *Effort:* High.
- **Phase 4 — Governance & standards:** Adopt ISO/IEC 42001; integrate with GDPR DPIAs/DPbDD. *Effort:* High.
- **Phase 5 — Monitor & adapt:** Track the AI Omnibus and Commission guidance; adjust dates/obligations. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | No AI inventory; unaware of tier obligations. | AI use unmapped. |
| 2 | Managed | AI inventory exists; prohibited-practice and literacy basics addressed. | Partial triage; literacy started. |
| 3 | Defined | Documented tier/role assessments; transparency and GPAI duties met. | Tier register; Art. 50 in place. |
| 4 | Quantitatively Managed | High-risk controls built and tested; metrics on oversight and data quality. | Conformity processes; KPIs. |
| 5 | Optimising | Integrated AI + data-protection governance; ISO/IEC 42001; proactive reform tracking. | AI management system; audits. |

# Audit Questions

1. Do you have an inventory of AI systems with tier and provider/deployer role assigned? *(Arts. 3, 6 [1].)*
2. How do you screen for and exclude prohibited practices? *(Art. 5 [1].)*
3. What AI literacy measures are in place for relevant staff? *(In force since Feb 2025 [3].)*
4. If you provide GPAI models, how do you meet transparency, copyright and documentation duties? *(Arts. 51–56 [1][3].)*
5. For high-risk systems, how are risk management, data governance, logging and human oversight implemented? *(Arts. 8–15 [1].)*
6. How do you meet Art. 50 transparency for chatbots and synthetic content? *(Art. 50 [1][3].)*
7. How are you tracking the AI Omnibus without pre-implementing unadopted timelines? *([4][5].)*
8. How are AI Act and GDPR obligations run together (DPIAs, DPbDD)? *([1][2].)*

# Implementation Checklist

- [ ] AI system inventory with tier + provider/deployer role.
- [ ] Prohibited-practice screening completed (Art. 5).
- [ ] AI literacy programme in place.
- [ ] GPAI provider obligations met where applicable (Arts. 51–56).
- [ ] High-risk controls scoped/built: risk management, data governance, logging, human oversight, robustness/cybersecurity.
- [ ] Art. 50 transparency (AI disclosure, synthetic-content marking) implemented.
- [ ] Conformity-assessment and registration path identified for high-risk systems.
- [ ] AI Omnibus timeline watch-list maintained (plan to current legal dates).
- [ ] Joint AI + GDPR compliance (DPIAs, DPbDD) established.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2024/1689 (Artificial Intelligence Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/1689/oj
- [2] **Regulation (EU) 2016/679 (GDPR), consolidated text** (parallel application to AI processing personal data). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504

## Regulatory Guidance

- [3] **Regulatory framework on AI / AI Act.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai
- [4] **Digital Omnibus on AI — regulation proposal.** European Commission. https://digital-strategy.ec.europa.eu/en/library/digital-omnibus-ai-regulation-proposal
- [5] **AI Act: deal on simplification measures, ban on "nudifier" apps** (provisional agreement 7 May 2026; new high-risk dates 2 Dec 2027 / 2 Aug 2028; awaiting formal adoption). European Parliament. https://www.europarl.europa.eu/news/en/press-room/20260427IPR42011/ai-act-deal-on-simplification-measures-ban-on-nudifier-apps

## Standards

- [6] **ISO/IEC 42001** — Artificial Intelligence Management System (AIMS). ISO. https://www.iso.org/standard/42001

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation and regulatory sources. Academic analysis (e.g., risk-tier critique, GPAI systemic-risk thresholds) will be cited in the high-risk and GPAI sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- EU Artificial Intelligence Act — Implementation Timeline (Future of Life Institute). https://artificialintelligenceact.eu/implementation-timeline/
- European Commission — "Navigating the AI Act" FAQ. https://digital-strategy.ec.europa.eu/en/faqs/navigating-ai-act

# Related Documents

- `gdpr-foundations` — parallel data-protection regime (**prerequisite reading**).
- `privacy-engineering-foundations` — DPbDD/security controls underpinning high-risk data governance.
- `ai-governance-foundations` — operationalising AI Act duties, ISO/IEC 42001 (planned, Tier 2 #6).
- `ai-act-high-risk` — high-risk obligations & conformity assessment (planned).
- `ai-act-gpai` — GPAI and systemic-risk regime (planned).
- `digital-omnibus` — the 2025–2026 simplification package (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Reg (EU) 2024/1689), European Commission and European Parliament sources; phased timeline and AI Omnibus provisional-agreement status live-verified. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at human review gate; frozen in release 0.6.0. First Tier 2 document. | Human reviewer |
