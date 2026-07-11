---
id: cybersecurity-foundations
title: "Cybersecurity: Foundations, Frameworks & Controls"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: Cybersecurity
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [privacy-engineering-foundations, nis2-foundations, dora-foundations, gdpr-foundations]
tags: [cybersecurity, cia-triad, iso-27001, iso-27002, nist-csf, owasp, zero-trust, defence-in-depth, cyber-essentials, cyber-resilience-act]
legal_basis: Cross-cutting discipline — underpins Directive (EU) 2022/2555 (NIS2) Art. 21, Regulation (EU) 2022/2554 (DORA), Regulation (EU) 2016/679 (GDPR) Art. 32, Regulation (EU) 2024/2847 (Cyber Resilience Act)
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | cybersecurity-foundations |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.8.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. Note that most content here is **standards-based best practice**, not legal obligation; where a legal duty exists it is labelled and sourced. The Cyber Resilience Act is in its **phased transition** (full application 11 December 2027); confirm current application dates before relying on them [4][5].

# Executive Summary

**Cybersecurity** is the cross-cutting technical and organisational discipline of protecting information systems, networks and data against threats to their **confidentiality, integrity and availability** (the "CIA triad"). This document establishes the foundations of that discipline as it underpins the EU/UK legal regimes — it is the "how" of security that laws such as **NIS2 Art. 21** [2], **DORA** [3] and **GDPR Art. 32** [1] require but do not fully specify. It deliberately stays **distinct** from the law-specific documents (`nis2-foundations`, `dora-foundations`) and from `privacy-engineering-foundations` (which covers data-protection-by-design); this document covers the security **frameworks, standards and controls** those laws lean on.

It sets out: core concepts (CIA triad, defence-in-depth, least privilege, zero trust); the two dominant management frameworks — **ISO/IEC 27001:2022** (an auditable **Information Security Management System**, ISMS) with its companion control set **ISO/IEC 27002:2022** (93 controls in four themes) [10][11], and the **NIST Cybersecurity Framework (CSF) 2.0** (February 2024), whose **six Functions are Govern, Identify, Protect, Detect, Respond and Recover** — **Govern being the function newly elevated in the 2.0 release** [12][13][14]; UK **NCSC** guidance including **Cyber Essentials** (five technical controls) [7][8]; **ENISA**'s EU-level role [9]; **OWASP Top 10:2025** for application security [15]; and operational disciplines (vulnerability/patch management, incident response, supply-chain security).

Three conclusions dominate. First, **frameworks are best practice, not law** — but they are the recognised means of **discharging** the legal security duties in NIS2, DORA and the GDPR [1][2][3]. Second, the **product-security frontier is now regulated**: the **EU Cyber Resilience Act (Regulation (EU) 2024/2847)** imposes binding security requirements on products with digital elements, phased to **full application on 11 December 2027** [4][5]. Third, security is **risk-based and continuous**: controls must be selected, tested and improved against a live threat picture, not certified once and forgotten.

# Key Takeaways

- The **CIA triad** — confidentiality, integrity, availability — is the organising model of information security and the outcome that legal duties like **GDPR Art. 32** demand [1]. *(Best practice; the outcome is a legal obligation under Art. 32.)*
- **ISO/IEC 27001:2022** specifies an auditable **ISMS**; **ISO/IEC 27002:2022** provides the companion set of **93 controls** across **four themes** (organisational, people, physical, technological) [10][11]. *(Best practice / standard.)*
- **NIST CSF 2.0** (Feb 2024) organises cybersecurity into **six Functions: Govern, Identify, Protect, Detect, Respond, Recover**; **Govern** was **added as a core Function in 2.0** to place risk governance at the centre [12][13][14]. *(Best practice / standard — verified.)*
- **NCSC Cyber Essentials** defines a baseline of **five technical controls** (firewalls, secure configuration, security update management, user access control, malware protection); **Cyber Essentials Plus** adds independent technical audit [7]. *(Best practice / government scheme.)*
- **OWASP Top 10:2025** is the current consensus list of the most critical web-application security risks, led by **Broken Access Control (A01)** [15]. *(Best practice / standard.)*
- **Defence-in-depth, least privilege, fail-safe defaults and zero trust** are foundational architectural principles — the first three trace to Saltzer & Schroeder (1975); zero trust is codified in **NIST SP 800-207** [16][17]. *(Best practice / academic.)*
- Frameworks **operationalise legal duties**: NIS2 **Art. 21(2)** lists ten minimum risk-management measures, DORA imposes an ICT risk-management framework, and GDPR **Art. 32** requires security appropriate to the risk — all satisfiable through ISO 27001 / NIST CSF controls [1][2][3]. *(Legal obligation, met via best practice.)*
- The **Cyber Resilience Act (Regulation (EU) 2024/2847)** makes product cybersecurity a **legal obligation** for manufacturers of products with digital elements; it entered into force **10 Dec 2024** and applies fully from **11 Dec 2027** (reporting duties from 11 Sep 2026) [4][5]. *(Legal obligation — phased.)*

# Purpose

This document is the Tier 3 entry point for the **cybersecurity discipline** that sits beneath the EU/UK security laws. It supports: (a) security-programme design (which framework to adopt and how to structure controls); (b) mapping technical controls to legal duties (NIS2, DORA, GDPR Art. 32); and (c) engineering triage (application security, patching, incident response, supply-chain risk). It is the "controls and frameworks" counterpart to the law-specific `nis2-foundations` and `dora-foundations`, and to the data-protection-focused `privacy-engineering-foundations`.

# Scope

**In scope:** Core security concepts (CIA triad, defence-in-depth, least privilege, zero trust); the ISO/IEC 27001:2022 ISMS and ISO/IEC 27002:2022 controls at a foundational level; NIST CSF 2.0 and its six Functions; NCSC guidance and Cyber Essentials; ENISA's role; OWASP Top 10 for application security; the operational disciplines of vulnerability/patch management, incident response and supply-chain security at a foundational level; how these frameworks map to NIS2 Art. 21, DORA and GDPR Art. 32; the Cyber Resilience Act at a foundational level.

**Out of scope (spun off to the research backlog):** The NIS2 and DORA legal regimes in depth → `nis2-foundations`, `dora-foundations`; data-protection-by-design and PETs → `privacy-engineering-foundations`; zero-trust reference architecture and migration → `zero-trust-architecture`; incident-response playbooks and CSIRT operations → `incident-response-playbooks`; detailed ISO 27002 / NIST CSF / CIS control mappings → `security-controls-mapping`; the Cyber Resilience Act in detail (product categories, conformity assessment, CE marking) → `cyber-resilience-act`; application-security testing (SAST/DAST/SCA) and secure SDLC → `application-security`.

**Assumptions:** The reader understands basic IT/network concepts. Where personal data is involved, the GDPR and `privacy-engineering-foundations` apply in parallel. This document does not restate the NIS2 or DORA obligations in full — see their dedicated documents.

# Definitions

*Shared terms are in `GLOSSARY.md`. Only cybersecurity-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| CIA triad | The three core security objectives: **confidentiality** (only authorised access), **integrity** (accuracy and non-tampering) and **availability** (accessible when needed). GDPR Art. 32 names confidentiality, integrity, availability and resilience as required security properties. | [1] |
| Information Security Management System (ISMS) | A systematic, risk-based management framework of policies, processes and controls for protecting information, specified by ISO/IEC 27001. | [10] |
| Defence-in-depth | Layering independent controls so that the failure of one does not compromise the system; rooted in the security design principles of Saltzer & Schroeder. | [8][17] |
| Least privilege | The principle that every user, process and component should have only the minimum access rights needed for its function (Saltzer & Schroeder). | [17] |
| Zero trust | A security model that removes implicit trust based on network location and continuously verifies every access request per-resource; defined for architecture by NIST SP 800-207. | [16] |
| Vulnerability management | The continuous process of identifying, assessing, prioritising and remediating (e.g. patching) security weaknesses in systems and software. | [8] |
| Cyber Essentials | A UK government-backed baseline certification (NCSC) built on five technical controls; **Cyber Essentials Plus** adds independent technical verification. | [7] |
| Product with digital elements | A software or hardware product (and its remote data-processing solutions) whose intended/foreseeable use includes a data connection, regulated for cybersecurity by the Cyber Resilience Act. | [4][5] |

# Background

Information security as a discipline predates the internet, but its modern framing crystallised around the **CIA triad** and a body of **design principles** articulated in Saltzer & Schroeder's 1975 paper *The Protection of Information in Computer Systems* — economy of mechanism, fail-safe defaults, least privilege, complete mediation, and defence-in-depth thinking that still underpins practice today [17]. As systems networked and threats professionalised, organisations needed **repeatable, auditable** ways to manage security, giving rise to **management-system standards** (the ISO/IEC 27000 family) and **outcome frameworks** (the NIST Cybersecurity Framework) [10][12].

In parallel, the EU and UK moved security from voluntary good practice toward **legal duty**. The GDPR (2016) made "security of processing" a statutory obligation for personal data (Art. 32) [1]; **NIS2** (2022) imposed risk-management and incident-reporting duties on essential and important entities (Art. 21) [2]; **DORA** (2022) did the same for the financial sector's ICT risk [3]; and the **Cyber Resilience Act** (2024) extended binding cybersecurity requirements to **products** placed on the EU market [4][5]. None of these laws prescribes a complete control set — they demand *appropriate*, *risk-based* measures — which is precisely why the **frameworks and standards** in this document matter: they are the recognised means of meeting the legal outcome.

# Legal Framework

This document describes a **discipline**, not a single instrument. It nonetheless sits directly beneath several binding instruments, which it helps implement. The legal duties are stated in their dedicated documents; summarised here for mapping:

- **GDPR Art. 32 (security of processing)** — controllers/processors must implement TOMs appropriate to the risk, expressly including pseudonymisation, encryption, and confidentiality/integrity/availability/resilience, plus regular testing of effectiveness [1]. *(Legal obligation — personal data.)*
- **NIS2 Art. 21 (cybersecurity risk-management measures)** — essential and important entities must take appropriate, proportionate technical, operational and organisational measures; **Art. 21(2)** enumerates **ten minimum measures** (risk analysis and information-system security policies; incident handling; business continuity/backup/crisis management; supply-chain security; security in acquisition/development/maintenance incl. vulnerability handling; policies to assess effectiveness; cyber hygiene and training; cryptography/encryption; HR security, access control and asset management; multi-factor authentication and secured communications) [2]. *(Legal obligation — see `nis2-foundations`.)*
- **DORA (Regulation (EU) 2022/2554)** — financial entities must maintain an **ICT risk-management framework**, plus incident reporting, resilience testing and third-party risk management [3]. *(Legal obligation — see `dora-foundations`.)*
- **Cyber Resilience Act (Regulation (EU) 2024/2847)** — manufacturers of **products with digital elements** must meet essential cybersecurity requirements, handle vulnerabilities, and report actively exploited vulnerabilities and severe incidents [4][5]. *(Legal obligation — phased; see `cyber-resilience-act`.)*

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| GDPR Art. 32 | Security of processing — risk-appropriate TOMs; CIA + resilience; encryption/pseudonymisation; effectiveness testing. | [1] |
| NIS2 Art. 21(1) | Appropriate and proportionate technical, operational and organisational risk-management measures (all-hazards, proportionality). | [2] |
| NIS2 Art. 21(2) | Ten minimum measures (incl. incident handling, business continuity, supply-chain security, cryptography, MFA, vulnerability handling). | [2] |
| NIS2 Art. 23 | Incident-reporting obligations (early warning, notification, final report). | [2] |
| DORA Arts. 5–16 | ICT risk-management framework (governance, protection, detection, response, recovery, learning). | [3] |
| CRA Art. 13 + Annex I | Essential cybersecurity requirements for products with digital elements and vulnerability handling. | [4] |
| CRA Art. 14 | Reporting of actively exploited vulnerabilities and severe incidents (applies from 11 Sep 2026). | [4][5] |

## Relevant Recitals

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| GDPR Recital 83 | Security measures should be risk-based, guarding against accidental/unlawful destruction, loss, alteration or disclosure. | [1] |
| NIS2 Recital 79 area | Risk-management measures should follow an all-hazards approach and reflect the state of the art and relevant standards. | [2] |
| CRA Recital 1 area | Rationale — products with digital elements are a frequent vector of successful cyberattacks; horizontal product-security rules are needed. | [4] |

*Recitals are not binding but aid interpretation of the enacting articles.*

## Relevant Case Law

**Not Applicable.** Cybersecurity is a cross-cutting technical discipline rather than a single legal instrument, so there is no distinct body of case law interpreting "cybersecurity" as such. Enforcement turning on inadequate security measures arises under specific instruments — e.g. GDPR Art. 32 fines, and (in future) NIS2/CRA enforcement — and is addressed in the law-specific documents (`nis2-foundations`, `dora-foundations`) and in `privacy-engineering-foundations`. [1][2]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **ENISA** (the EU Agency for Cybersecurity) supports NIS2 implementation, publishes the annual **Threat Landscape**, maintains the CRA single reporting platform, and promotes the use of European/international standards to meet the legal risk-management duties [9]. *(Regulatory / technical guidance.)*
- The **UK NCSC** frames good security around accessible baselines: **Cyber Essentials** (five technical controls) for a common-threat baseline, and the **10 Steps to Cyber Security** for board-level programme structure — both explicitly best-practice guidance, not law, though widely referenced in procurement [7][8]. *(Regulatory / government guidance.)*
- The **European Commission** presents the CRA as introducing **mandatory** cybersecurity requirements across a product's lifecycle, with **security-by-design and by-default**, vulnerability handling and CE-marked conformity — phased so manufacturers can prepare (full application 11 Dec 2027) [5][6]. *(Regulatory interpretation of a legal obligation.)*
- Regulators consistently treat **standards as the means, not the end**: certifying to ISO/IEC 27001 or aligning to NIST CSF is strong evidence of appropriate measures, but does not by itself prove compliance with a specific legal duty on specific facts [2][10]. *(Regulatory interpretation.)*

# Technical Considerations

**Core principles (BEST PRACTICE, with academic roots):**

- **Defence-in-depth** — layer independent controls (network, host, application, data, identity) so no single failure is catastrophic [8][17].
- **Least privilege & fail-safe defaults** — grant minimum access; deny by default (Saltzer & Schroeder) [17].
- **Zero trust** — remove implicit network-location trust; authenticate and authorise every request per-resource with continuous verification (NIST SP 800-207) [16].
- **Complete mediation & secure defaults** — check every access; ship secure-by-default configurations (a CRA requirement for products) [4][17].

**Management frameworks:**

- **ISO/IEC 27001:2022 (ISMS)** — a certifiable management system: context, leadership, risk assessment/treatment, an applicability statement over Annex A controls, operation, and continual improvement (Plan-Do-Check-Act) [10].
- **ISO/IEC 27002:2022** — the companion guidance detailing **93 controls** grouped into **four themes**: **organisational (37), people (8), physical (14), technological (34)** — a consolidation of the 2013 edition's 114 controls/14 clauses, with new controls such as threat intelligence, secure coding and data leakage prevention [11].
- **NIST CSF 2.0** — a technology-neutral outcome framework of **six Functions** — **Govern** (risk governance, roles, policy, supply-chain risk — **the Function elevated to core status in the 2.0 release**), **Identify**, **Protect**, **Detect**, **Respond**, **Recover** — with Categories, Subcategories and Implementation Tiers/Profiles for tailoring [12][13][14].

**Application security:** map development against the **OWASP Top 10:2025**, whose current leading risks include **A01 Broken Access Control**, **A02 Security Misconfiguration**, **A03 Software Supply Chain Failures**, **A04 Cryptographic Failures** and **A05 Injection** [15]. Supply-chain failures rising into the top three reflects the growing weight of dependency and build-pipeline risk.

**Operational disciplines (foundational):** continuous **vulnerability and patch management** (inventory, scanning, risk-based prioritisation, timely remediation); **incident response** (prepare-detect-analyse-contain-eradicate-recover-learn), aligned to NIS2/CRA reporting timelines; and **supply-chain security** (SBOMs, supplier assurance, secure build pipelines) — each an explicit NIS2 Art. 21(2) measure [2][8].

# Hosting Considerations

- **Shared-responsibility model** — in IaaS/PaaS/SaaS, the provider secures the underlying platform while the customer remains responsible for configuration, identity, data and application security; **security misconfiguration (OWASP A02)** is a leading cloud failure mode [15]. *(Best practice.)*
- **Framework-aligned cloud controls** — map hosting controls to **ISO/IEC 27002:2022** technological controls (access control, cryptography, logging, network security) and to CSF **Protect/Detect** outcomes; cloud-specific extensions to the ISMS exist where PII is processed (see `privacy-engineering-foundations`) [11][12]. *(Best practice.)*
- **Zero trust for cloud** — identity-centric, per-request authorisation is well suited to distributed cloud estates; adopt NIST SP 800-207 tenets rather than perimeter assumptions [16]. *(Best practice.)*
- **Logging, resilience and backup** — availability and recoverability are explicit legal outcomes (GDPR Art. 32; NIS2 Art. 21(2) business continuity/backup); ensure immutable, tested backups and centralised logging [1][2]. *(Legal obligation, met via controls.)*

# Game Hosting Considerations

- **Availability and abuse resistance** — real-time game services are high-value **DDoS** targets; availability (the "A" of the triad) requires upstream mitigation, rate-limiting and capacity planning [1]. *(Best practice grounded in the Art. 32 availability outcome.)*
- **Application security for game backends** — account, entitlement and matchmaking services face the same **OWASP Top 10** risks (broken access control, injection, misconfiguration); apply secure-SDLC and dependency scanning [15]. *(Best practice.)*
- **Anti-cheat and telemetry as security-sensitive data** — protect anti-cheat and moderation pipelines with least privilege and strong access control; where they process personal data, GDPR Art. 32 applies in parallel [1]. *(Best practice / legal overlap.)*
- **Connected devices and the CRA** — game hardware, consoles and companion apps with digital elements may fall within the **Cyber Resilience Act**, engaging product-security and vulnerability-handling duties [4][5]. *(Legal obligation — assess product scope.)*

# AI Considerations

- **Securing AI systems** — AI/ML systems inherit all conventional security duties (access control, encryption, logging) and add attack surfaces: adversarial inputs, model/data poisoning, prompt injection and model theft. Treat the model, training data and pipeline as assets under the ISMS [10]. *(Best practice.)*
- **AI Act cybersecurity overlap** — high-risk AI systems must be accurate, robust and **cybersecure by design** (AI Act Arts. 8–15); the controls in this document are the means of meeting that duty — see `ai-act-foundations` and `ai-governance-foundations`. *(Cross-reference; legal obligation under the AI Act.)*
- **Supply-chain and provenance** — model and dependency provenance (SBOMs, signed artefacts) address OWASP A03 (software supply-chain failures) and the CRA's vulnerability-handling expectations for products embedding AI [4][15]. *(Best practice.)*
- **AI as a security tool** — AI assists detection (anomaly detection, triage) but introduces false-positive/adversarial risks; keep human oversight in Detect/Respond functions [12]. *(Editorial recommendation.)*

# Operational Guidance

Labels: **OBLIGATION** (where a cited law requires the outcome) / **BEST PRACTICE** (standards consensus) / **EDITORIAL RECOMMENDATION** (this pipeline's suggestion).

1. **Adopt a management framework** — implement **ISO/IEC 27001:2022** (ISMS) and/or align to **NIST CSF 2.0**; use ISO/IEC 27002:2022 as the control catalogue. *(BEST PRACTICE — and the recognised way to evidence NIS2/DORA/GDPR duties.)* [10][11][12]
2. **Start with a baseline** — achieve **Cyber Essentials** (five controls) as a minimum bar, then mature toward the fuller framework. *(BEST PRACTICE.)* [7]
3. **Run a risk-based control-selection** — assess risks, then select and justify controls in a Statement of Applicability; do not deploy controls blindly. *(BEST PRACTICE; proportionality is a legal requirement under NIS2 Art. 21(1).)* [2][10]
4. **Govern first (CSF 2.0)** — establish roles, policy, risk appetite and supply-chain governance under the **Govern** Function before optimising technical controls. *(BEST PRACTICE.)* [12][13]
5. **Operate vulnerability & patch management** — maintain asset inventory, scan continuously, prioritise by risk, patch to defined SLAs. *(OBLIGATION where NIS2/CRA apply — vulnerability handling.)* [2][4]
6. **Prepare incident response** — maintain a tested IR plan mapped to statutory reporting timelines (NIS2 Art. 23; CRA Art. 14 from 11 Sep 2026). *(OBLIGATION where those laws apply.)* [2][4][5]
7. **Secure the software supply chain** — require SBOMs, verify dependencies, secure build pipelines (OWASP A03). *(OBLIGATION under NIS2 Art. 21(2); BEST PRACTICE otherwise.)* [2][15]
8. **Embed application security** — test against the **OWASP Top 10:2025** across the SDLC. *(BEST PRACTICE.)* [15]
9. **Move toward zero trust** — adopt identity-centric, per-request authorisation per NIST SP 800-207. *(EDITORIAL RECOMMENDATION.)* [16]
10. **Assess CRA product scope** — if you make products with digital elements, plan for essential requirements and reporting ahead of the phased dates. *(OBLIGATION — phased to 11 Dec 2027.)* [4][5]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | No management framework → ad hoc, unevidenced security | High | High | NIS2 Art. 21; ISO 27001 [2][10] | Adopt ISO 27001 / NIST CSF; SoA | Medium |
| R2 | Unpatched known vulnerabilities exploited | High | High | NIS2 Art. 21(2); CRA [2][4] | Vulnerability/patch management to SLAs | Medium |
| R3 | Broken access control / misconfiguration in apps | High | High | OWASP A01/A02:2025 [15] | Secure SDLC; least privilege; config review | Medium |
| R4 | Software supply-chain compromise | Medium | High | OWASP A03; NIS2 Art. 21(2) [2][15] | SBOMs; dependency & build-pipeline security | Medium |
| R5 | No/late incident detection and response | Medium | High | NIS2 Art. 23; CSF Detect/Respond [2][12] | Logging/monitoring; tested IR plan | Medium |
| R6 | Weak encryption / key management | Medium | High | GDPR Art. 32; ISO 27002 [1][11] | Strong crypto; segregated key custody | Low |
| R7 | Product placed on EU market without CRA compliance | Medium | High | CRA Reg (EU) 2024/2847 [4][5] | CRA gap analysis; conformity path pre-2027 | Medium |
| R8 | Treating certification as full legal compliance | Medium | Medium | Regulatory interpretation [2][10] | Map controls to specific legal duties | Low |

# Implementation Roadmap

- **Phase 0 — Baseline & inventory:** Asset inventory; achieve Cyber Essentials; identify applicable laws (NIS2/DORA/GDPR/CRA). *Effort:* Medium.
- **Phase 1 — Govern & risk-assess:** Establish governance (CSF Govern), risk assessment and treatment, Statement of Applicability. *Effort:* Medium.
- **Phase 2 — Core controls (ISO 27002 themes):** Access control, cryptography, logging, network and endpoint security, HR and physical security. *Effort:* High.
- **Phase 3 — Operational disciplines:** Vulnerability/patch management, incident response, business continuity/backup, supply-chain assurance. *Effort:* High.
- **Phase 4 — Application & product security:** Secure SDLC against OWASP Top 10; CRA product-security programme where in scope. *Effort:* High.
- **Phase 5 — Assurance & improvement:** Certification (ISO 27001), continuous testing, metrics, zero-trust maturation. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Ad hoc, reactive security; no framework; unknown asset inventory. | Firefighting; no SoA; patching inconsistent. |
| 2 | Managed | Baseline controls in place (e.g. Cyber Essentials); some policies. | Five controls met; partial inventory. |
| 3 | Defined | ISMS/CSF adopted; risk-based control selection; IR plan documented. | ISO 27001 scope defined; SoA; tested backups. |
| 4 | Quantitatively Managed | Metrics on patch latency, incident MTTR, control effectiveness; regular testing. | KPIs; pentests; supply-chain assurance. |
| 5 | Optimising | Continuous improvement; zero-trust architecture; automated detection/response; certified. | ISO 27001 certified; ZTA; threat-informed defence. |

# Audit Questions

1. Which framework (ISO/IEC 27001, NIST CSF 2.0) structures your security programme, and where is the Statement of Applicability / Profile? *([10][12].)*
2. How is risk assessment performed, and how are controls selected and justified proportionately? *(NIS2 Art. 21(1) [2].)*
3. What is your vulnerability and patch-management process, including remediation SLAs? *(NIS2 Art. 21(2); CRA [2][4].)*
4. How do you detect and respond to incidents, and how does this meet statutory reporting timelines? *(NIS2 Art. 23; CRA Art. 14 [2][4][5].)*
5. How is the software supply chain secured (SBOMs, dependency and build-pipeline controls)? *(NIS2 Art. 21(2); OWASP A03 [2][15].)*
6. How is application security tested against the OWASP Top 10 across the SDLC? *([15].)*
7. Which Art. 32 measures (encryption, access control, resilience) are implemented, and how is effectiveness tested? *(GDPR Art. 32 [1].)*
8. If you make products with digital elements, what is your CRA readiness plan against the phased dates? *([4][5].)*

# Implementation Checklist

- [ ] Asset inventory maintained and classified.
- [ ] Baseline achieved (Cyber Essentials five controls) (NCSC).
- [ ] ISMS/CSF adopted; risk assessment and Statement of Applicability completed (ISO 27001 / NIST CSF 2.0).
- [ ] Govern Function established: roles, policy, risk appetite, supply-chain governance (CSF 2.0).
- [ ] Core ISO 27002 controls implemented (access control, cryptography, logging, network/endpoint).
- [ ] Vulnerability and patch management operating to defined SLAs.
- [ ] Incident-response plan documented, tested and mapped to reporting timelines (NIS2/CRA).
- [ ] Software supply-chain controls in place (SBOMs, dependency/build security).
- [ ] Application security tested against OWASP Top 10:2025 in the SDLC.
- [ ] Zero-trust roadmap defined (NIST SP 800-207).
- [ ] CRA product-security programme scoped where applicable.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Article 32 (security of processing), Recital 83. EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [2] **Directive (EU) 2022/2555 (NIS2)** — Articles 21 (risk-management measures) and 23 (incident reporting). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/dir/2022/2555/oj
- [3] **Regulation (EU) 2022/2554 (DORA)** — ICT risk-management framework (Chapter II). EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2554/oj
- [4] **Regulation (EU) 2024/2847 (Cyber Resilience Act)** — essential cybersecurity requirements, vulnerability handling and reporting for products with digital elements. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2024/2847/oj

## Regulatory Guidance

- [5] **The Cyber Resilience Act — summary of the legislative text** (entry into force 10 Dec 2024; reporting from 11 Sep 2026; full application 11 Dec 2027). European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/cra-summary
- [6] **Cyber Resilience Act** (policy overview). European Commission. https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act
- [7] **Cyber Essentials: overview** (five technical controls; Cyber Essentials Plus). NCSC (UK). https://www.ncsc.gov.uk/cyberessentials/overview
- [8] **10 Steps to Cyber Security.** NCSC (UK). https://www.ncsc.gov.uk/collection/10-steps
- [9] **ENISA publications** (EU Agency for Cybersecurity — threat landscape, NIS2/CRA support). ENISA. https://www.enisa.europa.eu/publications

## Standards

- [10] **ISO/IEC 27001:2022** — Information security management systems (ISMS) — Requirements. ISO. https://www.iso.org/standard/27001
- [11] **ISO/IEC 27002:2022** — Information security controls (93 controls in four themes). ISO. https://www.iso.org/standard/75652.html
- [12] **Cybersecurity Framework (CSF) 2.0** — six Functions: Govern, Identify, Protect, Detect, Respond, Recover. NIST. https://www.nist.gov/cyberframework
- [13] **The NIST Cybersecurity Framework (CSF) 2.0** (NIST CSWP 29, Feb 2024) — authoritative framework text. NIST. https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf
- [14] **NIST Releases Version 2.0 of Landmark Cybersecurity Framework** (Feb 2024; Govern added as a core Function). NIST News. https://www.nist.gov/news-events/news/2024/02/nist-releases-version-20-landmark-cybersecurity-framework
- [15] **OWASP Top 10:2025** — the ten most critical web-application security risks (current released version). OWASP Foundation. https://owasp.org/Top10/2025/
- [16] **NIST SP 800-207 — Zero Trust Architecture** (2020). NIST. https://csrc.nist.gov/pubs/sp/800/207/final

## Academic Sources

- [17] **Saltzer, J. H. & Schroeder, M. D. (1975). "The Protection of Information in Computer Systems."** *Proceedings of the IEEE*, 63(9), 1278–1308 — foundational security design principles (least privilege, fail-safe defaults, complete mediation, economy of mechanism). MIT (authoritative copy). https://web.mit.edu/Saltzer/www/publications/protection/

# Further Reading

*Non-authoritative; provided for orientation only.*

- OWASP Top Ten project home. https://owasp.org/www-project-top-ten/
- ENISA — National Cybersecurity Strategies / topics. https://www.enisa.europa.eu/topics/national-cyber-security-strategies

# Related Documents

- `privacy-engineering-foundations` — data-protection-by-design and Art. 32 controls for personal data (complementary).
- `nis2-foundations` — the NIS2 legal regime and Art. 21 duties in depth (planned).
- `dora-foundations` — the DORA ICT risk-management and resilience regime (planned).
- `gdpr-foundations` — GDPR principles incl. security (Art. 5(1)(f), Art. 32).
- `cyber-resilience-act` — product cybersecurity in detail (planned).
- `zero-trust-architecture` — zero-trust reference architecture and migration (planned).
- `incident-response-playbooks` — IR process and CSIRT operations (planned).
- `security-controls-mapping` — ISO 27002 / NIST CSF / CIS control mappings (planned).
- `application-security` — secure SDLC and OWASP in depth (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Art. 32, NIS2, DORA, CRA), European Commission CRA guidance, NCSC, ENISA, ISO (27001/27002:2022), NIST (CSF 2.0, SP 800-207), OWASP Top 10:2025 and Saltzer & Schroeder (academic). NIST CSF 2.0 six Functions incl. Govern, ISO 27001:2022 edition, and CRA number/status/dates live-verified. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at batch human review gate; NIST CSF 2.0, ISO 27001/27002:2022 and CRA (Reg (EU) 2024/2847) dates verified; frozen in release 0.8.0. | Human reviewer |
