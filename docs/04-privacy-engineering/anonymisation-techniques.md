---
id: anonymisation-techniques
title: "Anonymisation, Pseudonymisation & Re-identification Risk"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU, UK]
topic: Privacy Engineering
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
related: [privacy-engineering-foundations, pets-catalogue, dpia-methodology, gdpr-foundations, gdpr-transfers]
tags: [anonymisation, pseudonymisation, re-identification, recital-26, article-4, motivated-intruder, k-anonymity, differential-privacy, identifiability, breyer, edps-srb, privacy-engineering]
legal_basis: Regulation (EU) 2016/679, Article 4(1) & 4(5) and Recital 26
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | anonymisation-techniques |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.17.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**.

# Executive Summary

**Anonymisation** is the one operation that takes data out of the GDPR entirely: once information no longer relates to an identified or identifiable person, the data-protection principles do not apply (Recital 26) [1]. **Pseudonymisation**, by contrast, only reduces risk — pseudonymised data can still be attributed to a person using additional information, so it **remains personal data and fully in scope** (Art. 4(5), Recital 26) [1]. This document is the anonymisation-and-re-identification companion to `pets-catalogue`, which introduces the techniques, and to `dpia-methodology`, which consumes the residual-risk output; here we set the **legal threshold**, the **techniques**, the **attack model**, and the **governance of residual risk**.

The legal test is **relative, not absolute**. Data is anonymous only where re-identification is not possible by "all the means reasonably likely to be used" — judged in context, accounting for cost, time and available technology (Recital 26) [1]. The CJEU established this contextual reading in **Breyer** (C-582/14) and, in 2025, sharpened it in **EDPS v SRB** (C-413/23 P): the same dataset can be personal data in one party's hands and anonymous in another's, depending on that party's realistic means of re-identification [2][3]. The **Article 29 Working Party Opinion 05/2014 (WP216)** supplies the operational attack model — three risks that a robust anonymisation must defeat: **singling out, linkability and inference** [6]. The ICO adds the **"motivated intruder" test** as a practical benchmark for residual risk [8].

Three conclusions dominate. First, **anonymisation is a high, evidenced bar, not a label** — it requires a documented residual-risk assessment against the WP216 criteria, not a declaration [6][8]. Second, **no single technique guarantees anonymity**: generalisation, suppression, k-anonymity/l-diversity/t-closeness, perturbation, differential privacy and synthetic data each defeat some attacks and leave others, so they are combined and parameterised to risk [14][15][17][18][19][20]. Third, on the **UK position**, the Data (Use and Access) Act 2025 **did not change the identifiability test** — the reformulation proposed in the earlier DPDI Bill was dropped, so the "means reasonably likely" standard continues to govern UK law [4][9].

# Key Takeaways

- **Anonymous data is outside the GDPR** (Recital 26); **pseudonymised data is not** — it remains personal data because a re-identification path exists (Art. 4(5)) [1]. *(Legal obligation.)*
- The identifiability test is **relative and contextual**: judged by "all the means reasonably likely to be used", accounting for cost, time and technology, from the perspective of the party holding the data [1][2][3]. *(Legal obligation as interpreted.)*
- **EDPS v SRB (C-413/23 P, 4 Sep 2025)** confirms the relative approach — data pseudonymised and transferred may be anonymous **in the recipient's hands** if that recipient lacks realistic means to re-identify [3]. *(Case law.)*
- **Breyer (C-582/14)** first established that identifiability turns on the legal and practical means realistically available to obtain the additional data, not on a purely hypothetical possibility [2]. *(Case law.)*
- A robust anonymisation must defeat the **WP216 three criteria — singling out, linkability and inference**; if any remains reasonably possible, the data is not anonymous [6]. *(Regulatory interpretation.)*
- The **ICO "motivated intruder" test** benchmarks residual risk: would a reasonably competent person, motivated but without special skills or unlawful means, be able to re-identify? [8] *(Regulatory interpretation.)*
- **Techniques are complementary, not sufficient alone**: generalisation/suppression and **k-anonymity** bound singling-out; **l-diversity/t-closeness** address attribute inference; **perturbation** and **differential privacy** give quantified, composable guarantees; **synthetic data** must be leakage-tested [14][15][17][18][19][20]. *(Best practice / academic.)*
- **Differential privacy** is the only model giving a formal guarantee **independent of the adversary's background knowledge**, governed by the ε privacy budget; NIST SP 800-226 sets out how to evaluate a DP claim [16][20]. *(Standards / academic.)*
- **Standards operationalise de-identification**: **ISO/IEC 20889** classifies the techniques and their re-identification-risk properties; **NIST SP 800-188** provides a governance-and-release-model methodology [14][15]. *(Standards.)*
- **UK law is unchanged on identifiability**: the DUAA 2025 dropped the DPDI Bill's proposed identifiability reformulation; the "means reasonably likely" test still applies [4][9]. *(Legal position — verified.)*
- **The EDPB (Guidelines 01/2025)** frames pseudonymisation around a **"pseudonymisation domain"** and confirms pseudonymised data stays personal within it, while recognising its risk-reduction and transfer value [7]. *(Regulatory interpretation.)*

# Purpose

This document gives privacy, engineering, data-science and legal teams an **evidence-based method** for (a) deciding whether a given output is genuinely *anonymous* (out of scope) or merely *pseudonymised* (in scope); (b) selecting and parameterising de-identification techniques against a defined attack model; and (c) governing the *residual* re-identification risk that determines the legal characterisation. It operationalises the anonymisation/pseudonymisation boundary introduced in `gdpr-foundations` and `pets-catalogue`, and feeds the necessity and risk steps of a DPIA (`dpia-methodology`).

# Scope

**In scope:** The legal anonymisation threshold under Recital 26 and Article 4(1)/(5) (relative vs absolute identifiability; the "means reasonably likely" test; the motivated-intruder benchmark); the anonymisation/pseudonymisation distinction and its consequences; de-identification techniques (generalisation, suppression, k-anonymity, l-diversity, t-closeness, perturbation/noise, differential privacy, synthetic data); the re-identification attack model (singling out, linkability, inference); residual-risk governance and release models; the CJEU authority (Breyer; EDPS v SRB); and the UK (DUAA 2025) position on the identifiability test.

**Out of scope (covered elsewhere or in the backlog):** The full PET catalogue and the cryptographic/computational PETs (SMPC, HE, TEEs, federated learning, ZKPs) → `pets-catalogue`; the DPIA process that records the residual-risk finding → `dpia-methodology`; DPbDD and Article 32 security controls generally → `privacy-engineering-foundations`; the meaning of personal data and the Breyer/Nowak line at foundational level → `gdpr-foundations`; anonymisation as a route to easing restricted transfers → `gdpr-transfers`; privacy threat modelling (LINDDUN) → `privacy-threat-modelling` (planned).

**Assumptions:** The reader has read `gdpr-foundations` (personal data, identifiability, Recital 26) and `pets-catalogue` (the technique inventory). "Personal data", "pseudonymisation", "anonymous data", "k-anonymity", "differential privacy" and "synthetic data" carry their `GLOSSARY.md` meanings.

# Definitions

*Shared terms (personal data, pseudonymisation, anonymous data, k-anonymity, differential privacy, synthetic data) are defined in `GLOSSARY.md`. Only anonymisation-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Anonymisation | The process of rendering personal data such that the data subject is no longer identifiable by any means reasonably likely to be used, so the data falls outside the GDPR (Recital 26). | [1][6] |
| Re-identification | The process of restoring the link between a de-identified record and the individual it concerns, defeating the anonymisation. | [6][14] |
| Relative (contextual) identifiability | The principle that identifiability is assessed against the means reasonably likely to be used *by the specific party* holding the data, so the same data may be personal for one party and anonymous for another. | [1][2][3] |
| Singling out | The ability to isolate some or all records that identify an individual within a dataset. | [6] |
| Linkability | The ability to link at least two records concerning the same individual, within or across datasets. | [6] |
| Inference | The ability to deduce, with significant probability, the value of an attribute from other values in the dataset. | [6] |
| Motivated intruder test | The ICO benchmark asking whether a reasonably competent person, motivated to re-identify but without specialist skills or unlawful means, could do so. | [8] |
| Quasi-identifier | An attribute that is not a direct identifier but, in combination with others, can single out an individual (e.g. postcode + date of birth + sex). | [14][17] |
| Generalisation | Reducing the precision of data (e.g. age → age band, full date → year) to increase the number of indistinguishable records. | [6][14] |
| Suppression | Removing or masking values (cells, records or attributes) that would otherwise enable identification. | [6][14] |
| Perturbation (noise addition) | Altering values by adding calibrated random noise or micro-aggregation to obscure exact values while preserving statistical utility. | [6][14] |
| Pseudonymisation domain | The EDPB concept of the context in which pseudonymisation is intended to preclude attribution, and from which the attribution-enabling additional information is excluded. | [7] |

# Background

De-identification is older than data-protection law: **statistical disclosure control** techniques for releasing census and survey data without exposing respondents predate the GDPR by decades, and the field of **statistical disclosure limitation** produced the generalisation, suppression and perturbation methods still used today [14][15]. The academic turning point was **k-anonymity** (Sweeney, 2002), which formalised protection against *singling out* by requiring each record to be indistinguishable from at least *k−1* others on its quasi-identifiers [17]. Successive models — **l-diversity** (Machanavajjhala et al., 2007) and **t-closeness** (Li et al., 2007) — closed attribute-inference gaps k-anonymity left open [18][19]. A different paradigm arrived with **differential privacy** (Dwork, 2006), which replaced dataset-shape heuristics with a provable, quantified, composable guarantee [20][21].

The GDPR gave this technical field a legal centre of gravity. **Recital 26** makes genuine anonymisation the outer boundary of the Regulation, while **Article 4(5)** defines pseudonymisation as a distinct, in-scope risk-reduction measure [1]. The **Article 29 Working Party Opinion 05/2014 (WP216)** translated the legal test into an engineering attack model — singling out, linkability, inference — and assessed each technique against it, cautioning that "anonymisation" is frequently over-claimed [6]. The **ICO** developed the practical **motivated-intruder** benchmark (originating in its 2012 anonymisation code and continued in its current draft guidance) [8]. Two CJEU judgments then fixed the identifiability test as **relative**: **Breyer** (2016) and, decisively, **EDPS v SRB** (2025) [2][3]. Standards bodies followed with **ISO/IEC 20889** (de-identification terminology and technique classification) and **NIST SP 800-188** (a governance and release-model methodology) [14][15], and NIST added **SP 800-226** to evaluate differential-privacy claims [16].

# Legal Framework

Anonymisation and pseudonymisation have no single dedicated article; they turn on the **definition of personal data** and a single recital [1]. The load-bearing provisions are:

- **Article 4(1) — personal data:** any information relating to an identified or identifiable natural person; identifiability may be **direct or indirect**, in particular by reference to an identifier or to factors specific to the person [1].
- **Article 4(5) — pseudonymisation:** processing such that data can no longer be attributed to a subject **without additional information**, which is **kept separately** and subject to technical and organisational measures. This is the legal reason pseudonymised data remains personal data [1].
- **Recital 26 — the identifiability test:** to determine identifiability, account should be taken of **all the means reasonably likely to be used** — by the controller or another person — considering **cost, time and available technology**. The principles **do not apply to anonymous information**; pseudonymised data that could be attributed using additional information **is** data on an identifiable person [1].
- **Recital 28–29 — pseudonymisation's role:** pseudonymisation reduces risk and assists compliance but does not remove data from scope; the additional information should be kept separate [1].
- **UK position (assimilated law):** UK GDPR Art. 4(1)/(5) and Recital 26 mirror the EU text; the **Data (Use and Access) Act 2025 did not amend the identifiability test** — the reformulation proposed in the earlier DPDI Bill was dropped, so the "means reasonably likely" standard continues to apply, read with the DPA 2018 [4][5][9].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 4(1) | Definition of personal data; identifiability may be direct or indirect. | [1] |
| Art. 4(5) | Definition of pseudonymisation; additional information kept separately — data stays personal. | [1] |
| Art. 5(1)(c) | Data minimisation — de-identification implements the principle. | [1] |
| Art. 5(1)(f) / Art. 32 | Security; pseudonymisation named as a measure (context for its risk-reduction role). | [1] |
| Art. 25 | Data protection by design/default — pseudonymise as early as possible. | [1] |
| Art. 89(1) | Safeguards for research/statistics — anonymisation/pseudonymisation and minimisation. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the articles above.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 26 | Identifiability judged by all means reasonably likely to be used (cost/time/technology); anonymous data out of scope; pseudonymised data remains personal. | [1] |
| Recital 28 | Pseudonymisation reduces risk and assists controllers, but does not itself take data out of scope. | [1] |
| Recital 29 | Additional information enabling attribution should be kept separately with safeguards. | [1] |

## Relevant Case Law

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Breyer | CJEU, C-582/14, ECLI:EU:C:2016:779 | A dynamic IP address is personal data for a party who has the *legal means reasonably likely* to obtain the additional data needed to identify the person; identifiability is assessed on realistically available means, not mere hypothetical possibility. | Establishes the **relative/contextual** identifiability test underpinning anonymisation. [2] |
| EDPS v SRB | CJEU, C-413/23 P, judgment 4 Sep 2025 | Whether pseudonymised data transferred to a recipient is personal data must be assessed from the **recipient's** perspective and their realistic means of re-identification; the same data may be personal for the discloser yet anonymous for the recipient. Also confirms opinions/views can be personal data and that the information duty is judged at collection from the controller's standpoint. | Landmark confirmation of the **relative approach** to pseudonymised data and anonymisation. [3] |

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- **WP216 (Opinion 05/2014)** is the authoritative engineering reading of the Recital 26 test. It holds that a technique achieves anonymisation **only if it robustly prevents all three** of **singling out, linkability and inference**; where any remains reasonably possible, the result is at best pseudonymisation. It warns that anonymisation is frequently over-claimed and that **each technique carries residual risk** requiring case-by-case assessment [6]. *(Regulatory interpretation.)*
- The **ICO** frames anonymisation as **relative and risk-based**, not absolute, and applies the **"motivated intruder" test** — whether a reasonably competent person, motivated to re-identify but using no specialist skills or unlawful means, could succeed — as a practical benchmark for residual risk; it stresses documenting the assessment and reviewing it as context changes [8][9]. *(Regulatory interpretation.)*
- The **EDPB Guidelines 01/2025 on Pseudonymisation** introduce the **"pseudonymisation domain"**: the context in which additional attribution information is excluded. Within that domain data are pseudonymised (and personal); the guidelines confirm pseudonymisation's value for security, DPbDD and transfers while maintaining that pseudonymised data stays in scope [7]. *(Regulatory interpretation.)*
- **ENISA** treats pseudonymisation as a **spectrum** (counter, RNG, cryptographic hash, HMAC, encryption) whose re-identification resistance depends on the **adversary model** and secret management, and positions de-identification within "data protection engineering" as a design activity, not a compliance guarantee [11][12][13]. *(Technical/regulatory guidance.)*
- **NIST** cautions that a de-identification or differential-privacy claim is meaningful only with a **defined release model, threat model and documented parameters** (for DP: a stated ε, privacy unit, composition accounting and validated implementation); an unqualified "anonymised" or "differentially private" label is not evidence [15][16]. *(Standards interpretation.)*

# Technical Considerations

De-identification techniques map onto the WP216 attack model: each is strong against some of *singling out / linkability / inference* and weak against others, so they are combined and parameterised to the assessed risk [6][14].

- **Generalisation** — reduce precision (age → band, full postcode → district, timestamp → date). Raises the number of indistinguishable records, reducing singling-out; excessive generalisation destroys utility [6][14].
- **Suppression** — remove or mask outliers, rare quasi-identifier combinations, or whole attributes. Targets residual singling-out that generalisation leaves [6][14].
- **k-anonymity** — generalise/suppress quasi-identifiers so each record shares them with at least *k−1* others. Bounds **singling out**, but is vulnerable to **homogeneity** and **background-knowledge** attacks and gives no guarantee against inference [17][14]. *(Academic / standards.)*
- **l-diversity** — additionally require each equivalence class to contain ≥ *l* "well-represented" sensitive values, resisting **attribute inference** where a class is homogeneous [18]. *(Academic.)*
- **t-closeness** — require each class's sensitive-attribute distribution to stay within distance *t* of the overall distribution, closing the skewness/similarity gaps l-diversity leaves [19]. *(Academic.)*
- **Perturbation / noise addition / micro-aggregation** — alter values (add noise, swap, aggregate) to obscure exact records while preserving aggregate statistics; strength depends on the noise magnitude versus utility [6][14].
- **Differential privacy (DP)** — a randomised mechanism is **ε-differentially private** if adding/removing any one individual changes any output's probability by at most e^ε. Its guarantee holds **regardless of adversary background knowledge** and **composes** across queries (a cumulative **privacy budget**); **global/central** DP adds noise at a trusted curator, **local** DP at source. Small ε ⇒ stronger privacy/more noise; a large ε is near-meaningless. NIST SP 800-226 sets the evaluation criteria [20][21][16]. *(Standards / academic.)*
- **Synthetic data** — generate artificial records from a model fitted to real data; offers **no inherent guarantee** (over-fitted models memorise and leak, enabling membership-inference), so it must be **leakage-tested**, ideally generated under DP [10][15]. *(Best practice.)*

**Technique-to-attack coverage (indicative):**

| Technique | Singling out | Linkability | Inference | Formal guarantee? |
|-----------|--------------|-------------|-----------|-------------------|
| Generalisation / suppression | Reduced | Reduced | Weak | No [6][14] |
| k-anonymity | Bounded (≥k) | Reduced | No | No [17] |
| l-diversity | Bounded | Reduced | Partial | No [18] |
| t-closeness | Bounded | Reduced | Improved | No [19] |
| Perturbation / micro-aggregation | Reduced | Reduced | Reduced | No (technique-dependent) [6][14] |
| Differential privacy | Strong | Strong | Strong | **Yes (ε-bounded, composable)** [20][16] |
| Synthetic data | Depends | Depends | Depends | Only if DP-generated [15][10] |

The standards frame the workflow: **ISO/IEC 20889** classifies these as de-identification techniques with explicitly bounded assurance, and **NIST SP 800-188** structures the **governance** — choose a **release model** (release de-identified data; release synthetic data; or a query interface with output controls), set a threat model, and assess residual risk before release [14][15]. *(Standards.)*

# Hosting Considerations

- **Key/mapping segregation is decisive** — for pseudonymisation and any technique retaining a re-identification mapping, hosting must keep the key/lookup **separate from the protected data**, under distinct access control; co-locating key and data collapses the pseudonymisation domain and defeats the measure [1][7][11]. *(Legal obligation — Art. 32 read with Art. 4(5).)*
- **Relative identifiability across hosting parties** — because identifiability is contextual, a dataset may be **anonymous in a processor/recipient's hands** but personal for the controller who holds the key; the hosting and access architecture is therefore part of the anonymisation argument (cf. EDPS v SRB) [3][7]. *(Legal position as interpreted.)*
- **Anonymisation can ease transfers — but only if genuine** — truly anonymous data is outside Chapter V, but the exporter must evidence the Recital 26 assessment for the *recipient's* context before relying on it (see `gdpr-transfers`); a mislabelled "anonymous" export remains a restricted transfer [1][3]. *(Legal obligation.)*
- **UK context** — for UK controllers the assimilated UK GDPR Art. 4/Recital 26 and DPA 2018 apply; the DUAA 2025 leaves the identifiability test unchanged, and the ICO anonymisation guidance and motivated-intruder benchmark govern [4][5][8][9]. *(Legal position.)*

# Game Hosting Considerations

- **Aggregate and add DP to published player metrics** — leaderboards, heatmaps and "players like you" analytics released externally should use aggregation/k-anonymity or differential privacy to prevent singling-out of individual players, especially minors, where the motivated-intruder bar is easily met [6][17][20]. *(Best practice.)*
- **Telemetry is a re-identification risk** — high-dimensional behavioural telemetry (session times, locations, device fingerprints) forms rich **quasi-identifiers**; generalisation/suppression alone rarely anonymises it, so treat pseudonymised telemetry as personal data and assess residual linkability before any "anonymous analytics" claim [6][14]. *(Best practice grounded in obligation.)*
- **Children's data raises the bar** — for services likely to be accessed by children, the sensitivity and the ease of a motivated intruder make robust de-identification and conservative parameters essential before external release (see `game-hosting-foundations`, `uk-gdpr-foundations`) [8]. *(Regulatory expectation.)*

# AI Considerations

- **Training data is rarely anonymous** — datasets fitted for model training typically retain identifying structure; pseudonymisation leaves them in scope, and only robust de-identification (strong DP, tested synthetic data) can support an out-of-scope claim for the *inputs* [1][6][10]. *(Legal obligation as interpreted.)*
- **Models and outputs can memorise and leak** — trained models are vulnerable to **membership-inference** and **model-inversion** attacks, so a model derived from personal data is not automatically anonymous; **DP-SGD** training bounds the influence of any single record and is the auditable route to a guarantee [20][16][10]. *(Best practice.)*
- **Synthetic training/test data ≠ automatic anonymisation** — synthetic data used to train or evaluate AI must be leakage-tested (ideally DP-generated) before any anonymity claim, because generative models can reproduce real records [10][15]. *(Best practice.)*
- **Differential privacy for analytics/ML** — state ε, the privacy unit and composition accounting (NIST SP 800-226) so the guarantee is auditable rather than asserted [16][20]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** (must, per statute) / **BEST PRACTICE** (should, per standards/regulators) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Classify before you claim** — never treat pseudonymised or encrypted data as anonymous; before asserting data is out of scope, run and **document a Recital 26 assessment** against the means reasonably likely to be used. *(OBLIGATION.)* [1][6]
2. **Assess against the three WP216 criteria** — test the output for residual **singling out, linkability and inference**; if any remains reasonably possible, it is not anonymous. *(BEST PRACTICE reflecting the legal test.)* [6]
3. **Apply the motivated-intruder benchmark** — assess whether a reasonably competent, motivated person without special skills or unlawful means could re-identify; record the reasoning. *(BEST PRACTICE.)* [8]
4. **Assess identifiability for the specific recipient/context** — because the test is relative, evaluate re-identification means in the hands of the actual party who will hold the data (cf. EDPS v SRB). *(OBLIGATION as interpreted.)* [3]
5. **Choose techniques by the attack they must defeat** — generalisation/suppression + k-anonymity for singling-out; l-diversity/t-closeness for inference; perturbation/DP for quantified guarantees; combine where one is insufficient. *(BEST PRACTICE.)* [6][17][18][19][20]
6. **Parameterise and document** — record k/l/t values, noise/ε and privacy unit, the release model and threat model (ISO/IEC 20889; NIST SP 800-188/800-226). *(BEST PRACTICE.)* [14][15][16]
7. **Keep keys and mappings segregated** — pseudonymisation only reduces risk if the additional information is kept separate and access-controlled (Art. 4(5)/32). *(OBLIGATION.)* [1][7]
8. **Test synthetic data and models for leakage** — membership-inference/attribute-disclosure testing before any anonymity claim. *(BEST PRACTICE.)* [10][15]
9. **Govern residual risk over time** — re-assess as auxiliary data, technology and linkage opportunities evolve; an anonymisation valid today can decay. *(BEST PRACTICE.)* [6][8]
10. **Record the finding in the DPIA** — capture the technique, parameters, residual risk and characterisation (anonymous vs pseudonymised) as accountability evidence (see `dpia-methodology`). *(OBLIGATION for accountability.)* [1]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Treating **pseudonymised/encrypted** data as anonymous and out of scope | High | High | Art. 4(5); Recital 26 [1][6] | Recital 26 assessment; classify as personal data | Low |
| R2 | **Weak k-anonymity** broken by background-knowledge/homogeneity attack | Medium | High | Sweeney; WP216 [17][6] | Add l-diversity/t-closeness; raise k; residual-risk test | Low |
| R3 | **Inference/attribute disclosure** from a k-anonymous release | Medium | High | l-diversity/t-closeness literature [18][19] | l-diversity/t-closeness; utility-privacy review | Medium |
| R4 | **Differential privacy mis-parameterised** (ε too large; bad composition) | Medium | High | NIST SP 800-226 [16] | Documented ε/privacy unit; budget accounting; review | Low |
| R5 | **Synthetic data memorises** and leaks real records | Medium | High | ICO PETs; NIST 800-188 [10][15] | Leakage testing; DP-synthetic generation | Medium |
| R6 | **Linkage attack** combining the release with an auxiliary dataset | Medium | High | WP216 linkability [6] | Assess external datasets; suppress rare QIDs; DP | Medium |
| R7 | **Re-identification decay** as new auxiliary data/technology appears | Medium | High | Recital 26 (technology) [1][6] | Periodic re-assessment; controlled release models | Medium |
| R8 | **Key/mapping co-located** with pseudonymised data | Medium | High | Art. 4(5); Art. 32 [1][7] | Separate KMS/vault; segregated access | Low |
| R9 | **"Anonymous" export** that is a restricted transfer for the recipient | Low | High | Recital 26; EDPS v SRB [1][3] | Assess recipient context; transfer safeguards if personal | Low |
| R10 | Assuming a technique **discharges accountability** (no DPIA record) | Medium | Medium | Art. 5(2); Art. 35 [1] | Record technique/residual risk in DPIA | Low |

# Implementation Roadmap

- **Phase 0 — Boundary discipline:** Establish the rule that no output is called "anonymous" without a documented Recital 26 assessment; inventory current "anonymous"/pseudonymised claims. *Effort:* Low–Medium.
- **Phase 1 — Attack-model method:** Adopt the WP216 three-criteria assessment and the ICO motivated-intruder benchmark as the standard test; define who signs off. *Effort:* Medium.
- **Phase 2 — Technique toolkit:** Standardise generalisation/suppression, k-anonymity (+l-diversity/t-closeness) tooling with parameter guidance (ISO/IEC 20889). *Effort:* Medium.
- **Phase 3 — Quantified privacy:** Introduce differential privacy (global first) for analytics/ML with documented ε and composition accounting (NIST SP 800-226). *Effort:* High.
- **Phase 4 — Release governance:** Adopt NIST SP 800-188 release models (de-identified vs synthetic vs query interface) and leakage testing for synthetic data/models. *Effort:* High.
- **Phase 5 — Assurance:** Periodic re-identification-risk re-assessment, metrics, DPIA integration and independent review. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | "Anonymised" used loosely; pseudonymisation conflated with anonymisation; no residual-risk test. | Unassessed "anonymous" claims; keys co-located. |
| 2 | Managed | Basic de-identification (generalisation/suppression) applied ad hoc; some k-anonymity; assessments informal. | Some technique use; no documented threshold test. |
| 3 | Defined | WP216 three-criteria + motivated-intruder assessments documented; parameters (k/l/t) recorded; DPIA captures the finding. | Standard method; sign-off; parameter guidance. |
| 4 | Quantitatively Managed | Differential privacy with governed ε/budget; leakage testing for synthetic data/models; metrics on residual risk. | ε accounting; membership-inference tests; KPIs. |
| 5 | Optimising | Release-model governance (NIST 800-188); recipient-context assessments; continuous re-assessment and independent assurance. | Query-interface controls; periodic decay review; audit. |

# Audit Questions

1. For any data you treat as **anonymous**, where is the **Recital 26** assessment against the means reasonably likely to be used, and by whom was it signed off? *(Recital 26; Art. 4(1) [1][6].)*
2. How do you test outputs against **singling out, linkability and inference** before release? *(WP216 [6].)*
3. How is the **motivated-intruder** benchmark applied and recorded? *(ICO [8].)*
4. Where data is shared, how do you assess identifiability **in the recipient's hands** (relative approach)? *(Breyer; EDPS v SRB [2][3].)*
5. For **k-anonymised** releases, what are k/l/t, and how is inference/linkage residual risk handled? *(Sweeney; l-diversity; t-closeness [17][18][19].)*
6. Where **differential privacy** is used, what is ε, the privacy unit, and the composition accounting? *(NIST SP 800-226 [16].)*
7. How is **synthetic data** (or a trained model) tested for leakage before any anonymity claim? *(ICO PETs; NIST 800-188 [10][15].)*
8. How are pseudonymisation **keys/mappings** kept separate and access-controlled? *(Art. 4(5)/32; EDPB [1][7].)*
9. How do you **re-assess** anonymisation over time as auxiliary data and technology change? *(Recital 26 [1][6].)*

# Implementation Checklist

- [ ] No output labelled "anonymous" without a documented Recital 26 assessment.
- [ ] WP216 three-criteria (singling out / linkability / inference) test applied and recorded.
- [ ] Motivated-intruder benchmark documented for each release.
- [ ] Identifiability assessed for the specific recipient/context (relative approach).
- [ ] k/l/t parameters (and rationale) recorded for syntactic de-identification.
- [ ] Differential-privacy parameters (ε, privacy unit, composition) documented where DP is used.
- [ ] Synthetic-data and model outputs leakage-tested before any anonymity claim.
- [ ] Pseudonymisation keys/mappings segregated from data and access-controlled.
- [ ] Release model chosen (de-identified / synthetic / query interface) per NIST SP 800-188.
- [ ] Anonymisation/pseudonymisation characterisation and residual risk recorded in the DPIA.
- [ ] Periodic re-identification-risk re-assessment scheduled.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Articles 4(1), 4(5), 5, 25, 89 and Recitals 26, 28, 29. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj
- [2] **Breyer v Germany, C-582/14, ECLI:EU:C:2016:779** — identifiability turns on the means legally and practically reasonably likely to be used; establishes the relative test. CJEU / EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62014CJ0582
- [3] **EDPS v SRB, C-413/23 P (judgment 4 September 2025)** — pseudonymised data assessed from the recipient's realistic means of re-identification; the relative approach to personal data. CJEU / EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A62023CJ0413
- [4] **Data (Use and Access) Act 2025 (c.18)** — UK data-protection reform; did not amend the identifiability test (the DPDI Bill reformulation was dropped). legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2025/18/contents
- [5] **Data Protection Act 2018 (c.12)** — UK companion to the UK GDPR. legislation.gov.uk. https://www.legislation.gov.uk/ukpga/2018/12/contents

## Regulatory Guidance

- [6] **Opinion 05/2014 on Anonymisation Techniques (WP216).** Article 29 Data Protection Working Party (adopted 10 Apr 2014). The three-criteria test (singling out, linkability, inference) and technique analysis. European Commission. https://ec.europa.eu/justice/article-29/documentation/opinion-recommendation/files/2014/wp216_en.pdf
- [7] **Guidelines 01/2025 on Pseudonymisation.** European Data Protection Board (adopted 16 Jan 2025). The "pseudonymisation domain"; pseudonymised data remains personal within it. https://www.edpb.europa.eu/system/files/2025-01/edpb_guidelines_202501_pseudonymisation_en.pdf
- [8] **Introduction to anonymisation** (draft anonymisation, pseudonymisation and PETs guidance; relative/risk-based test; motivated-intruder benchmark). Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-sharing/anonymisation/introduction-to-anonymisation/
- [9] **What is personal data?** (identifiability; "means reasonably likely to be used"; direct/indirect identifiers). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/personal-information-what-is-it/what-is-personal-data/what-is-personal-data/
- [10] **Privacy-enhancing technologies (PETs)** — including synthetic data and differential privacy caveats. ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-sharing/privacy-enhancing-technologies/
- [11] **Pseudonymisation Techniques and Best Practices.** ENISA (2019). https://www.enisa.europa.eu/publications/pseudonymisation-techniques-and-best-practices
- [12] **Data Pseudonymisation: Advanced Techniques and Use Cases.** ENISA (2021). https://www.enisa.europa.eu/publications/data-pseudonymisation-advanced-techniques-and-use-cases
- [13] **Data Protection Engineering.** ENISA (2022). https://www.enisa.europa.eu/publications/data-protection-engineering

## Standards

- [14] **ISO/IEC 20889:2018 — Privacy enhancing data de-identification terminology and classification of techniques.** ISO/IEC. https://www.iso.org/standard/69373.html
- [15] **NIST SP 800-188 — De-Identifying Government Datasets: Techniques and Governance** (final, Sep 2023). NIST. https://csrc.nist.gov/pubs/sp/800/188/final
- [16] **NIST SP 800-226 — Guidelines for Evaluating Differential Privacy Guarantees** (2025). NIST. https://csrc.nist.gov/pubs/sp/800/226/final

## Academic Sources

- [17] **Sweeney, L. (2002). "k-anonymity: a model for protecting privacy."** International Journal of Uncertainty, Fuzziness and Knowledge-Based Systems 10(5). https://dataprivacylab.org/dataprivacy/projects/kanonymity/kanonymity.pdf
- [18] **Machanavajjhala, A., Kifer, D., Gehrke, J., Venkitasubramaniam, M. (2007). "l-diversity: Privacy beyond k-anonymity."** ACM Transactions on Knowledge Discovery from Data 1(1). https://personal.utdallas.edu/~muratk/courses/privacy08f_files/ldiversity.pdf
- [19] **Li, N., Li, T., Venkatasubramanian, S. (2007). "t-Closeness: Privacy Beyond k-Anonymity and l-Diversity."** IEEE ICDE 2007. https://doi.org/10.1109/ICDE.2007.367856
- [20] **Dwork, C. (2006). "Differential Privacy."** ICALP 2006, LNCS 4052, Springer. https://link.springer.com/chapter/10.1007/11681878_14
- [21] **Dwork, C., Roth, A. (2014). "The Algorithmic Foundations of Differential Privacy."** Foundations and Trends in Theoretical Computer Science 9(3–4). https://www.cis.upenn.edu/~aaroth/Papers/privacybook.pdf

# Further Reading

*Non-authoritative; provided for orientation only.*

- CJEU press release CP 107/25 — *EDPS v SRB* (C-413/23 P), summary of the judgment. https://curia.europa.eu/site/upload/docs/application/pdf/2025-09/cp250107en.pdf
- ICO — What are identifiers and related factors? https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/personal-information-what-is-it/what-is-personal-data/what-are-identifiers-and-related-factors/

# Related Documents

- `pets-catalogue` — **sibling**; the technique inventory (pseudonymisation, DP, synthetic data) this document assesses for anonymisation strength.
- `dpia-methodology` — consumes the residual-identifiability finding in its necessity and risk steps.
- `privacy-engineering-foundations` — **parent**; DPbDD and Art. 32 controls, and the PET concept.
- `gdpr-foundations` — personal data, identifiability and the Recital 26 boundary (Breyer/Nowak).
- `gdpr-transfers` — anonymisation as a route out of Chapter V, subject to the recipient-context test.

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Art. 4(1)/(5), Recitals 26/28/29), CJEU *Breyer* (C-582/14) and *EDPS v SRB* (C-413/23 P, live-verified via curia press release CP 107/25), WP29 Opinion 05/2014 (WP216), EDPB Guidelines 01/2025 on pseudonymisation, ICO anonymisation/personal-data guidance (motivated-intruder test), ENISA pseudonymisation/DP-engineering reports, ISO/IEC 20889, NIST SP 800-188 and SP 800-226, and the defining academic literature (Sweeney; Machanavajjhala; Li; Dwork; Dwork & Roth). UK DUAA 2025 position on the identifiability test verified: unchanged (DPDI reformulation dropped). | — |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster C); full-repo validator/link/lint suite green; frozen in release 0.17.0. | Orchestrator (QA-verified) |
