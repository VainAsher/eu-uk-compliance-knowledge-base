---
id: pets-catalogue
title: "Privacy-Enhancing Technologies: A Catalogue"
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
related: [privacy-engineering-foundations, dpia-methodology, gdpr-foundations, anonymisation-techniques, ai-act-foundations]
tags: [pets, privacy-enhancing-technologies, differential-privacy, pseudonymisation, k-anonymity, homomorphic-encryption, smpc, federated-learning, zero-knowledge-proofs, synthetic-data, privacy-engineering]
legal_basis: Regulation (EU) 2016/679, Articles 25, 32 & Recital 26
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | pets-catalogue |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.14.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | Human reviewer — 2026-07-11 |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**.

# Executive Summary

**Privacy-enhancing technologies (PETs)** are technical measures that minimise the personal data processed, or protect it while it is processed, so that data-protection principles can be met without abandoning the analytical or operational value of the data [1][2]. This document is the technique-by-technique catalogue promised by the parent reference `privacy-engineering-foundations`, which introduces PETs (pseudonymisation, encryption, differential privacy, aggregation) only at a foundational level [7]. Here each technology is examined on four axes: **what it is**, its **formal guarantee and its limits**, its **GDPR relevance** (data minimisation under Article 25, security under Article 32, and — critically — whether it produces *anonymous* or merely *pseudonymised* data), and its **engineering maturity**.

The catalogue covers **pseudonymisation and tokenisation**; the syntactic anonymisation models **k-anonymity, l-diversity and t-closeness**; **differential privacy** (global vs local, and the meaning of the ε privacy budget); **synthetic data**; **secure multi-party computation (SMPC)**; **homomorphic encryption**; **trusted execution environments (TEEs)**; **federated learning**; **zero-knowledge proofs (ZKPs)**; and **encryption in transit, at rest and in use**. It draws the primary techniques from the peer-reviewed literature that defined them [13][14][15][16][17][18][19][20][21], and grounds the legal and selection guidance in ENISA and ICO output [2][3][4][5][6] and in ISO/IEC and NIST standards [9][10][11][12].

Three conclusions dominate. First, **most PETs do not, by themselves, anonymise** — pseudonymisation, encryption, SMPC, TEEs and federated learning all leave the data in scope of the GDPR, and only techniques that provide a demonstrable, quantified identifiability guarantee (well-parameterised differential privacy; robustly generated synthetic data; strong k-anonymity/aggregation) can approach the Recital 26 anonymisation threshold [1][2][6]. Second, **PETs are controls, not compliance** — they reduce risk and evidence Article 25/32, but do not discharge the accountability obligation or replace a DPIA [1][2][7]. Third, **maturity varies enormously**: pseudonymisation and encryption are production-grade, while homomorphic encryption and general-purpose SMPC remain computationally expensive and use-case specific — so PET selection must be risk-driven, not fashion-driven [2][3].

# Key Takeaways

- A **PET** minimises or protects personal data; PETs help meet **Article 25 (data protection by design and by default)** and **Article 32 (security)** but do not, on their own, discharge accountability [1][2][7]. *(Best practice grounded in obligation.)*
- The **anonymisation/pseudonymisation line (Recital 26; Art. 4(5))** is decisive: *pseudonymised* data remains personal data and in scope; only *anonymous* data — no longer attributable by means reasonably likely to be used — falls outside the GDPR [1][6]. *(Legal obligation.)*
- **Pseudonymisation and tokenisation** are expressly named risk-reduction measures (Arts. 25(1), 32(1)(a)), but keep the data in scope because a re-identification key exists [1][4][5]. *(Legal obligation / best practice.)*
- **k-anonymity, l-diversity and t-closeness** are *syntactic* models that bound re-identification by generalisation/suppression; each fixes a weakness in the prior model but none gives a formal, composable guarantee against a strong adversary [13][14][15]. *(Best practice / academic.)*
- **Differential privacy (DP)** gives a formal, quantified, composable guarantee governed by a **privacy budget ε** (smaller ε = stronger privacy, more noise); it exists in a **global/central** model (trusted curator) and a **local** model (noise added at source) [16][17][9]. *(Best practice / academic.)*
- **SMPC, homomorphic encryption, TEEs and federated learning** enable computation on data without centralising the raw records, supporting minimisation — but the **inputs/outputs and models can still be personal data**, so they are not automatic anonymisation [2][3][18][19][21]. *(Best practice.)*
- **Encryption** (in transit, at rest, and increasingly *in use*) is the baseline confidentiality control named in Article 32(1)(a); encrypted personal data held by a party with the key remains personal data [1][12]. *(Legal obligation / best practice.)*
- **PET maturity is uneven**: pseudonymisation, tokenisation and encryption are established; DP, synthetic data, TEEs and federated learning are maturing; general SMPC and homomorphic encryption remain performance-constrained — regulators warn PETs are **not a silver bullet** [2][3]. *(Regulatory interpretation.)*
- **Selection is risk-driven**: choose the PET by the risk it must address (identifiability, confidentiality, or collaborative computation), assess residual risk in a **DPIA**, and combine PETs where a single technique is insufficient [2][3][4]. *(Best practice.)*

# Purpose

This document gives privacy, engineering, data-science and compliance teams an **evidence-based catalogue** to select, justify and correctly characterise privacy-enhancing technologies. It supports three decisions: (a) *which* PET (or combination) addresses a given privacy risk; (b) *whether* a chosen PET renders data anonymous or leaves it pseudonymised and in scope; and (c) *how mature* and operationally realistic each option is. It operationalises the PETs overview in `privacy-engineering-foundations` and feeds the necessity, risk and mitigation steps of a DPIA (`dpia-methodology`).

# Scope

**In scope:** The definition and legal framing of PETs under GDPR Articles 25 and 32; the anonymisation/pseudonymisation boundary (Recital 26); a technique-by-technique catalogue (pseudonymisation and tokenisation; k-anonymity/l-diversity/t-closeness; differential privacy; synthetic data; SMPC; homomorphic encryption; TEEs; federated learning; zero-knowledge proofs; encryption in transit/at rest/in use); an ENISA/ICO-grounded selection guide; and a maturity/selection matrix.

**Out of scope (covered elsewhere or in the backlog):** The DPbDD and Article 32 obligations in general → `privacy-engineering-foundations`; the full anonymisation methodology and re-identification-risk assessment → `anonymisation-techniques` (planned); DPIA process → `dpia-methodology`; privacy threat modelling (LINDDUN) → `privacy-threat-modelling` (planned); detailed key-management and cryptographic-control mappings → `cybersecurity-foundations` / `privacy-controls-mapping` (planned); the AI Act's data-governance duties → `ai-act-foundations` / `ai-act-high-risk`.

**Assumptions:** The reader has read `gdpr-foundations` (personal data, identifiability, Recital 26) and `privacy-engineering-foundations` (DPbDD, TOMs, the PET concept). "Personal data", "pseudonymisation", "anonymous data" and "differential privacy" carry their `GLOSSARY.md` meanings.

# Definitions

*Shared terms (personal data, pseudonymisation, anonymous data, PET, differential privacy, TOMs) are defined in `GLOSSARY.md`. Only technique-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Tokenisation | A form of pseudonymisation that substitutes a data element (e.g. a card number) with a non-sensitive surrogate ("token"), with the mapping held in a secured token vault. | [4][5] |
| k-anonymity | A dataset property: every record is indistinguishable from at least *k−1* others on its quasi-identifiers, so no individual can be singled out below a group of size *k*. | [13] |
| l-diversity | A strengthening of k-anonymity requiring each equivalence class to contain at least *l* "well-represented" values of each sensitive attribute, resisting attribute disclosure. | [14] |
| t-closeness | A further strengthening requiring the distribution of a sensitive attribute in each class to be within distance *t* of its distribution in the whole table. | [15] |
| Differential privacy (ε-DP) | A formal guarantee that the presence or absence of any one individual changes the probability of any output by at most a factor of e^ε; ε is the "privacy budget". | [16][17][9] |
| Global (central) DP | The trusted-curator model: a trusted party holds the raw data and adds calibrated noise to query results/aggregates. | [9][17] |
| Local DP | Each individual perturbs their own data *before* it leaves their device, so the collector never sees raw values (e.g. randomised response). | [9][17] |
| Synthetic data | Artificial data generated from a model of a real dataset's statistical properties, intended to preserve utility while (ideally) not corresponding to real individuals. | [2][3] |
| Secure multi-party computation (SMPC) | Cryptographic protocols letting several parties jointly compute a function over their inputs while keeping each input private from the others. | [3][18] |
| Homomorphic encryption (HE) | Encryption allowing computation directly on ciphertext, producing an encrypted result that decrypts to the correct plaintext output. | [3][19] |
| Trusted execution environment (TEE) | A hardware-isolated, attestable enclave in which code and data are protected from the rest of the host, enabling "confidential computing". | [2][3] |
| Federated learning (FL) | A distributed machine-learning approach that trains a shared model by exchanging model updates, not raw data, which stays on local devices/silos. | [21][22] |
| Zero-knowledge proof (ZKP) | A protocol by which a prover convinces a verifier that a statement is true while revealing nothing beyond the truth of the statement. | [20] |
| Encryption in use | Protection of data while it is being processed in memory (e.g. via TEEs or HE), complementing encryption in transit and at rest. | [2][3] |

# Background

The idea that technology can protect privacy rather than only threaten it dates to the 1990s coinage of "privacy-enhancing technologies", but the field matured as two research strands converged: **statistical disclosure control** (how to release useful data without re-identifying individuals) and **cryptography** (how to compute without disclosing inputs). The statistical strand produced **k-anonymity** (Sweeney, 2002) and its successors **l-diversity** (Machanavajjhala et al., 2007) and **t-closeness** (Li et al., 2007), each answering an attack the previous model left open [13][14][15]. A more ambitious answer came from **differential privacy** (Dwork, 2006), which replaced dataset-shape heuristics with a provable, quantified guarantee and became the dominant formal notion of privacy in analytics [16][17].

The cryptographic strand is older still: **secure computation** was framed by Yao in 1982 [18]; **zero-knowledge proofs** by Goldwasser, Micali and Rackoff in 1985 [20]; and **fully homomorphic encryption** — long a "holy grail" — was first realised by Gentry in 2009 [19]. **Federated learning** (McMahan et al., 2017) then applied the "move computation, not data" principle to machine learning at scale [21]. The GDPR gave this technical field a legal centre of gravity by naming **pseudonymisation** and **encryption** in Articles 25 and 32 and by making genuine **anonymisation** the boundary of its own application (Recital 26) [1]. Regulators and standards bodies followed with practitioner guidance: ENISA on pseudonymisation and data-protection engineering [3][4][5], the ICO with dedicated **PETs guidance** [2], NIST with evaluation criteria for differential privacy [9], and ISO/IEC with a de-identification taxonomy [10].

# Legal Framework

PETs have no single "PET article"; they are the technical means by which several GDPR obligations are met [1]. The load-bearing provisions are:

- **Article 5(1)(c) — data minimisation:** personal data must be adequate, relevant and limited to what is necessary. PETs that reduce what is collected, centralised or exposed (federated learning, local DP, aggregation) implement this principle directly [1].
- **Article 5(1)(f) & Article 32 — integrity, confidentiality and security:** appropriate technical measures for a level of security appropriate to the risk, **expressly naming pseudonymisation and encryption** (Art. 32(1)(a)), plus confidentiality, integrity, availability and resilience [1].
- **Article 25 — data protection by design and by default:** controllers must implement appropriate measures — **pseudonymisation is given as the example** — to embed the principles effectively (Art. 25(1)), and to ensure only necessary data is processed by default (Art. 25(2)) [1].
- **Article 4(5) — definition of pseudonymisation:** processing such that data can no longer be attributed to a subject **without additional information kept separately and secured** — the legal reason pseudonymised data stays personal [1].
- **Recital 26 — the identifiability test:** the principles do not apply to anonymous information; identifiability is judged by "all the means reasonably likely to be used"; **pseudonymised data that could be attributed using additional information is data on an identifiable person** [1].
- **Article 89(1) — safeguards for research/statistics:** requires appropriate safeguards, **naming pseudonymisation**, and the data-minimisation principle, for archiving, research and statistical processing — a common home for PETs [1].

DPbDD and Article 32 operationalise the **accountability** (Art. 5(2)) and **security** (Art. 5(1)(f)) principles established in `gdpr-foundations`; the anonymisation boundary is elaborated in `gdpr-foundations` and `privacy-engineering-foundations`.

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 4(5) | Definition of pseudonymisation (additional information kept separately). | [1] |
| Art. 5(1)(c) | Data minimisation — PETs reduce data collected/exposed. | [1] |
| Art. 5(1)(f) | Integrity and confidentiality (security) principle. | [1] |
| Art. 5(2) | Accountability — PETs evidence but do not replace it. | [1] |
| Art. 25(1) | Data protection by design — pseudonymisation named as the example measure. | [1] |
| Art. 25(2) | Data protection by default — minimise amount, extent, retention, accessibility. | [1] |
| Art. 32(1)(a) | Security of processing — pseudonymisation and encryption named expressly. | [1] |
| Art. 89(1) | Safeguards for research/statistics — pseudonymisation and minimisation. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the articles above.*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 26 | Identifiability judged by means reasonably likely to be used; anonymous data is out of scope; pseudonymised data remains personal data. | [1] |
| Recital 28 | Pseudonymisation can reduce risks to data subjects and help controllers meet their obligations, but does not by itself take data out of scope. | [1] |
| Recital 29 | Pseudonymisation measures should be possible within the same controller when the additional information is kept separately. | [1] |
| Recital 78 | DPbDD examples — minimising processing, pseudonymising as soon as possible, transparency, enabling monitoring. | [1] |
| Recital 83 | Security — risk-based measures against accidental/unlawful destruction, loss, alteration or disclosure. | [1] |

## Relevant Case Law

Not Applicable. The choice and characterisation of PETs is a technical and interpretive matter driven by the GDPR text, regulator guidance and standards, not by a distinct line of judgments. The **relative/contextual identifiability** test that determines whether a PET output is anonymous or pseudonymised is, however, informed by CJEU authority on the meaning of personal data (*Breyer*, C-582/14; *Nowak*, C-434/16), which is treated in `gdpr-foundations`. [1]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **ICO's dedicated PETs guidance** frames PETs as technologies that "can help you demonstrate a data protection by design and by default approach", grouping them by function — reducing identifiability (e.g. differential privacy, synthetic data), hiding/protecting data during processing (e.g. homomorphic encryption, SMPC, TEEs, federated learning), and splitting or minimising data — while warning that PETs are **not a silver bullet**, that their **maturity and effectiveness vary**, and that a PET must be assessed for residual re-identification and security risk before reliance [2]. *(Regulatory interpretation.)*
- The ICO advises using PETs **as part of**, not instead of, a DPIA and broader accountability measures, and cautions that some PETs are **computationally costly or immature** and can introduce their own risks (e.g. poor DP parameter choices, weak synthetic-data generation) [2]. *(Regulatory interpretation.)*
- **ENISA** treats pseudonymisation as a spectrum of techniques with differing re-identification resistance (counter, RNG, hash, HMAC, encryption-based) and stresses that the **choice of technique and secret must match the adversary model**; it also positions PETs within "data protection engineering" as design building blocks, not compliance guarantees [3][4][5]. *(Regulatory / technical guidance.)*
- Both regulators, and **ENISA's design-by-default work**, agree that pseudonymisation and encryption **reduce but do not remove** GDPR scope, and that anonymisation is a **high, context-dependent bar** requiring the residual re-identification risk to be remote given all means reasonably likely to be used [1][6][7]. *(Regulatory interpretation of a legal test.)*
- **NIST** provides an evaluation framework for **differential privacy guarantees**, cautioning that a DP claim is meaningful only with a stated ε, a defined "privacy unit", correct composition accounting, and validated implementation — an unqualified "differentially private" label is not evidence [9]. *(Standards interpretation.)*

# Technical Considerations

This section is the catalogue. Each technique is assessed on **what it is**, **guarantee and limits**, **GDPR relevance**, and **maturity**. A consolidated view is in the Compliance Maturity Model.

## The anonymisation vs pseudonymisation line (read first)

Every entry below turns on one distinction. Under **Recital 26** and **Article 4(5)**, data is **anonymous** — and outside the GDPR — only if a subject can no longer be identified by "all the means reasonably likely to be used" by the controller or another person; otherwise it is **pseudonymised** and remains **personal data**, fully in scope [1][6]. The test is **relative and contextual**: the same output can be anonymous in one party's hands and personal in another's if that party holds the additional information (cf. `gdpr-foundations` on *Breyer*) [1]. Consequences for PET selection: (a) techniques that retain a reversible mapping or key (pseudonymisation, tokenisation, encryption, TEEs) **cannot** produce anonymous data for the party holding the key; (b) techniques that *transform* the data to bound identifiability (strong k-anonymity/aggregation, well-parameterised differential privacy, robust synthetic data) **may** reach anonymisation, but only after a documented residual-risk assessment [2][6]. *(Legal obligation as interpreted.)*

## Pseudonymisation and tokenisation

- **What it is.** Replacing identifying fields with pseudonyms (via counters, random tokens, keyed hashes/HMAC, or encryption), keeping the re-identification mapping separate and secured (Art. 4(5)). **Tokenisation** is the vault-based variant common in payments [4][5].
- **Guarantee and limits.** Reduces linkability and the impact of a breach, but is **reversible by design** by whoever holds the mapping/key; naive hashing of low-entropy identifiers is vulnerable to dictionary/brute-force attacks, so ENISA recommends keyed constructions (HMAC) or encryption with proper secret management [4][5].
- **GDPR relevance.** The archetypal Article 25(1)/32(1)(a) measure and named in Article 89(1); **pseudonymised data remains personal data** (Recital 26/28) [1]. A recurring compliance error is treating it as anonymisation.
- **Maturity. Established** — production-grade and ubiquitous; the main risk is weak technique or key handling, not immaturity [4][5]. *(Legal obligation / best practice.)*

## k-anonymity, l-diversity and t-closeness

- **What it is.** *Syntactic* de-identification of tabular data. **k-anonymity** generalises/suppresses quasi-identifiers so each record shares its quasi-identifier values with at least *k−1* others [13]. **l-diversity** additionally requires each such group to hold ≥ *l* well-represented sensitive values [14]. **t-closeness** requires each group's sensitive-value distribution to stay within *t* of the overall distribution [15].
- **Guarantee and limits.** They bound **singling-out** (k) and **attribute disclosure** (l, t), but give **no formal guarantee against an adversary with background knowledge or auxiliary datasets**, and do not **compose** safely across multiple releases; k-anonymity is vulnerable to homogeneity and background-knowledge attacks (the very attacks l-diversity and t-closeness were designed to blunt), and high k/strict t can destroy utility [13][14][15]. ISO/IEC 20889 catalogues these as de-identification models with explicitly bounded assurance [10].
- **GDPR relevance.** A well-parameterised, context-assessed k-anonymised (ideally l-diverse/t-close) release **can** support an anonymisation argument under Recital 26, but only after residual-risk analysis; weak parameters leave the data personal [1][6][10].
- **Maturity. Established** as a method, with mature tooling; but treated by regulators as necessary-not-sufficient and increasingly complemented by differential privacy [2][10]. *(Best practice / academic.)*

## Differential privacy (global vs local, ε)

- **What it is.** A **formal, mathematical** definition of privacy: a randomised mechanism is **ε-differentially private** if adding or removing any single individual's record changes the probability of any output by at most a factor of e^ε [16][17]. Noise (e.g. Laplace/Gaussian) is calibrated to the query's sensitivity. In the **global/central** model a trusted curator adds noise to results; in the **local** model each person perturbs their own data before sending it, so no raw data is centralised [9][17].
- **Guarantee and limits.** Unlike syntactic models, DP's guarantee holds **regardless of the adversary's background knowledge** and **composes** (repeated queries consume a cumulative **privacy budget**). The budget is **ε**: **smaller ε ⇒ stronger privacy, more noise, less utility**; large ε renders the guarantee near-meaningless. Local DP needs far more data/noise than global DP for the same utility. NIST warns a DP claim is only as good as its stated ε, defined privacy unit, correct composition accounting, and validated implementation [9][16][17].
- **GDPR relevance.** DP directly serves **data minimisation** and can support an **anonymisation** argument for *outputs* when ε and the privacy unit are conservative and documented — but the underlying dataset remains personal data, and a poorly chosen ε does not anonymise [1][2][9].
- **Maturity. Maturing** — deployed at scale by large data holders and national statistical offices (which document DP use for official-statistics releases), with growing tooling, but requires scarce expertise to parameterise correctly [2][8][9]. *(Best practice / academic.)*

## Synthetic data

- **What it is.** Artificial records generated from a model (statistical or, increasingly, generative-AI) fitted to a real dataset, intended to preserve aggregate utility while not mapping to real individuals [2][3].
- **Guarantee and limits.** Offers **no inherent formal guarantee**: a model that overfits can memorise and leak real records, and synthetic data can still enable membership-inference or attribute-disclosure attacks. Assurance depends on the generation method and evaluation; combining generation with **differential privacy** ("DP-synthetic data") provides a quantifiable bound [2][3][9]. Utility and privacy trade off.
- **GDPR relevance.** Robustly generated, evaluated synthetic data **may** be anonymous and out of scope; but the **training process uses personal data** and the output must be tested for leakage before that claim is made [2][6].
- **Maturity. Maturing** — active adoption for testing, ML and data sharing, but privacy assurance methods are still consolidating; the ICO cautions against assuming synthetic ⇒ anonymous [2][3]. *(Best practice.)*

## Secure multi-party computation (SMPC)

- **What it is.** Cryptographic protocols (secret sharing, garbled circuits) that let multiple parties jointly compute a function over their combined inputs while each input stays private from the others [3][18].
- **Guarantee and limits.** Provides strong **input privacy** against defined adversary models (semi-honest or malicious), but the **agreed output can still reveal or be personal data**, protocols add communication/computation overhead, and correctness depends on non-collusion assumptions and careful implementation [3][18].
- **GDPR relevance.** Enables collaborative analytics/linkage with **minimised data exposure** (Art. 5(1)(c), Art. 25) and reduces the need to pool raw data with third parties; the **inputs and outputs remain personal data** in the hands that can attribute them [1][2].
- **Maturity. Emerging-to-maturing** — real deployments exist (e.g. cross-organisation statistics), but general-purpose SMPC is performance-limited and specialist [2][3]. *(Best practice.)*

## Homomorphic encryption (HE)

- **What it is.** Encryption schemes allowing computation **directly on ciphertext**; the decrypted result equals the result of the same computation on the plaintext. **Fully homomorphic encryption (FHE)**, first realised by Gentry (2009), supports arbitrary computation [3][19].
- **Guarantee and limits.** Strong confidentiality: the compute party never sees plaintext. But FHE carries **very high computational and storage overhead**, "partially" homomorphic variants support only limited operations, and key management is critical; the **result and the input are personal data** to the key holder [3][19].
- **GDPR relevance.** Supports **encryption in use** and outsourced/third-party processing with minimal exposure (Art. 32); it does **not anonymise** — it protects confidentiality [1][2].
- **Maturity. Emerging** — practical for narrow, well-bounded computations; general FHE remains too costly for most production workloads [2][3]. *(Best practice.)*

## Trusted execution environments (TEEs)

- **What it is.** Hardware-isolated, **attestable** enclaves that protect code and data in use from the rest of the host, underpinning "confidential computing" [2][3].
- **Guarantee and limits.** Provide **confidentiality and integrity in use** with far lower overhead than HE/SMPC, but rely on **trust in the hardware vendor** and are exposed to side-channel and micro-architectural attacks; data inside the enclave is plaintext to the enclave, so this is a **security**, not an anonymisation, control [2][3].
- **GDPR relevance.** A strong **Article 32** measure for processing sensitive data on untrusted infrastructure and a route to **encryption in use**; the data **remains personal data** [1][2].
- **Maturity. Maturing** — broadly available from major cloud and CPU vendors, though attestation and side-channel hardening require care [2][3]. *(Best practice.)*

## Federated learning (FL)

- **What it is.** Distributed machine learning that trains a shared model by exchanging **model updates** (gradients/weights) computed locally, so raw training data stays on devices or in institutional silos [21][22].
- **Guarantee and limits.** Reduces raw-data centralisation, but **model updates can leak** training data (gradient-inversion, membership-inference), so FL is typically combined with **differential privacy** and/or **SMPC/secure aggregation** for a meaningful guarantee; it adds systems complexity and can be attacked via poisoning [21][22].
- **GDPR relevance.** Advances **data minimisation** and can keep data local (helpful for special-category or cross-border data), but the **updates and the trained model may be personal data**, so FL alone is not anonymisation [1][2][22].
- **Maturity. Maturing** — production use in mobile/keyboard and healthcare settings, with active research on its privacy hardening [2][22]. *(Best practice.)*

## Zero-knowledge proofs (ZKPs)

- **What it is.** Protocols letting a prover convince a verifier that a statement is true (e.g. "this user is over 18", "this credential is valid") **without revealing any underlying data** beyond the statement's truth [20].
- **Guarantee and limits.** Provide **completeness, soundness and zero-knowledge** under cryptographic assumptions; enable powerful **data minimisation** (attribute proofs, age assurance, selective disclosure). Limits are implementation complexity, proving cost for some schemes, and the fact that the **claim being proven** may still be personal data in context [20].
- **GDPR relevance.** A direct **minimisation/DPbDD** enabler — proving eligibility without disclosing identity or the raw attribute (Arts. 5(1)(c), 25) — increasingly relevant to age assurance and verifiable credentials [1][2].
- **Maturity. Emerging-to-maturing** — mature in specific domains (e.g. some digital-identity and blockchain systems), still specialist for general use [2]. *(Best practice.)*

## Encryption in transit, at rest, and in use

- **What it is.** The baseline confidentiality control: TLS and equivalents protect data **in transit**; disk/database/field encryption protects data **at rest**; TEEs and HE protect data **in use** [1][2][12].
- **Guarantee and limits.** Protects confidentiality (and, with authenticated encryption, integrity) against parties without the key; strength depends on **algorithm choice, key management and rotation** (ISO/IEC 27002 cryptographic controls). Encrypted personal data held by a party **with** the key remains personal data; loss of key control is the dominant risk [1][12].
- **GDPR relevance.** **Named expressly in Article 32(1)(a)**; encryption at rest/in transit is a de facto expectation, and encryption in use extends protection to processing [1][12].
- **Maturity. Established** for transit/at rest (universal); **emerging/maturing** for in use (via TEEs/HE) [2][3][12]. *(Legal obligation / best practice.)*

## ENISA/ICO selection guide — which PET for which risk

Match the **risk** to the PET's **function**, then validate residual risk in a DPIA [2][3][4]:

| Primary risk to address | Candidate PETs | GDPR function |
|-------------------------|----------------|---------------|
| Records can be linked/attributed by the holder | Pseudonymisation, tokenisation, encryption at rest | Security & risk reduction (Art. 32); *stays personal data* |
| Re-identification in a data **release/publication** | k-anonymity (+ l-diversity/t-closeness), differential privacy, DP-synthetic data | Reduce identifiability toward anonymisation (Recital 26) |
| Repeated **queries/analytics** over sensitive data | Global or local differential privacy | Quantified, composable minimisation |
| **Collaboration/linkage** across organisations without pooling raw data | SMPC, federated learning (+ secure aggregation/DP) | Data minimisation (Art. 5(1)(c)) |
| **Processing on untrusted infrastructure** | TEEs, homomorphic encryption | Encryption/confidentiality in use (Art. 32) |
| **Proving an attribute** (age, eligibility) without disclosure | Zero-knowledge proofs | Minimisation / DPbDD (Art. 25) |
| Data **in transit / at rest** confidentiality | TLS, disk/field encryption | Security baseline (Art. 32(1)(a)) |

This function-first mapping mirrors the goal-oriented *privacy design strategies* (notably *minimise*, *hide* and *aggregate*), which classify PETs by the data-protection outcome they serve [23]. Editorial guidance: **combine** PETs (e.g. federated learning + secure aggregation + differential privacy) where one technique leaves residual risk; never present a PET as anonymisation without a documented Recital 26 assessment [2][6]. *(Editorial recommendation.)*

# Hosting Considerations

- **Confidential computing in the cloud** — TEEs and, for narrow workloads, homomorphic encryption let controllers process sensitive personal data on shared/untrusted infrastructure while limiting the provider's access; assess attestation, side-channel exposure and the **shared-responsibility** split (see `cloud-hosting-foundations`) [2][3]. *(Best practice grounded in Art. 32.)*
- **Key custody is the control that matters** — for pseudonymisation, tokenisation and encryption, hosting must keep the re-identification key/mapping or KMS **separate from the protected data** and under controlled access; co-locating key and ciphertext defeats the measure [1][4][5]. *(Legal obligation — Art. 32.)*
- **Data locality via minimisation PETs** — federated learning, local DP and SMPC can keep raw data in-region, easing transfer and localisation constraints (see `gdpr-transfers`), though model updates/outputs may still constitute a transfer of personal data [1][22]. *(Best practice.)*
- **Provider-managed PET services** — where a host offers managed DP, confidential-computing or tokenisation services, the controller must still evidence correct parameters and residual risk; a managed PET does not transfer accountability [2]. *(Editorial recommendation.)*

# Game Hosting Considerations

- **Pseudonymise player analytics** — separate durable account identifiers from behavioural/telemetry payloads via pseudonymisation or tokenisation, holding the mapping separately; high-volume game telemetry is a strong minimisation target [1][4]. *(Best practice grounded in Art. 25(2).)*
- **Aggregate and add DP to published metrics** — leaderboards, heatmaps and "players like you" analytics released externally should use aggregation/k-anonymity or differential privacy to prevent singling-out of individual players, especially minors [2][13][16]. *(Best practice.)*
- **Zero-knowledge age assurance** — ZKP-based age/eligibility proofs can satisfy child-protection expectations (see `game-hosting-foundations`, `uk-gdpr-foundations`) while minimising the identity data collected from players [1][2][20]. *(Best practice grounded in Art. 25.)*
- **Confidential processing of moderation/anti-cheat data** — often sensitive; TEEs and strong encryption (in transit/at rest/in use) plus strict retention apply the *hide* strategy [1][2][3]. *(Best practice.)*

# AI Considerations

- **PETs address the minimisation-vs-model-appetite tension** — the central AI privacy conflict (see `privacy-engineering-foundations`) is mitigated by **differential privacy** (DP-SGD training), **federated learning**, **synthetic data** and **SMPC/HE** for privacy-preserving training and inference [2][3][9][21]. *(Best practice.)*
- **Model updates and models can be personal data** — federated learning and DP reduce, but do not automatically remove, the risk that gradients or a trained model leak training data (membership-inference, gradient inversion); combine FL with DP/secure aggregation for a real guarantee [21][22]. *(Best practice.)*
- **Differential privacy for training/analytics** — provides a bounded, documentable guarantee on the influence of any single training record; state ε, the privacy unit and composition accounting (NIST criteria) so the claim is auditable [9][16][17]. *(Best practice.)*
- **AI Act data-governance overlap** — high-risk AI **data-governance** duties (representative, relevant, error-checked data) and the GDPR's minimisation are complementary; PETs are a shared implementation layer (see `ai-act-foundations` / `ai-act-high-risk`) [1]. *(Cross-reference.)*
- **Synthetic training data ≠ automatic anonymisation** — synthetic data used to train or test AI must be leakage-tested (ideally DP-generated) before any out-of-scope claim [2][3]. *(Best practice.)*

# Operational Guidance

Labels: **OBLIGATION** (must, per statute) / **BEST PRACTICE** (should, per standards/regulators) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Start from the risk, not the technology** — identify whether the risk is identifiability, confidentiality, or collaborative computation, then select the PET(s) by function using the selection guide. *(BEST PRACTICE.)* [2][3]
2. **Never assume a PET anonymises** — for any claim that data is out of scope, run and document a **Recital 26** residual-identifiability assessment against means reasonably likely to be used. *(OBLIGATION.)* [1][6]
3. **Keep keys and mappings separate** — pseudonymisation/tokenisation/encryption only reduce risk if the re-identification material is segregated and access-controlled (Art. 32). *(OBLIGATION.)* [1][4]
4. **Parameterise DP explicitly** — record ε, the privacy unit, composition/budget accounting and the noise mechanism; treat an unqualified "differentially private" label as unproven. *(BEST PRACTICE.)* [9][16]
5. **Test synthetic data and model updates for leakage** — membership-inference/attribute-disclosure testing before relying on synthetic-data or FL privacy claims. *(BEST PRACTICE.)* [2][3][21]
6. **Combine PETs where one is insufficient** — e.g. FL + secure aggregation + DP; SMPC + DP on outputs. *(EDITORIAL RECOMMENDATION.)* [2][22]
7. **Right-size to maturity and cost** — prefer established PETs (pseudonymisation, encryption, aggregation) for baseline needs; reserve HE/SMPC for cases that justify their overhead. *(BEST PRACTICE.)* [2][3]
8. **Record PET decisions in the DPIA** — capture the PET, its guarantee, residual risk and why it is adequate, as accountability evidence (see `dpia-methodology`). *(OBLIGATION for accountability; BEST PRACTICE for the register.)* [1][2]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Treating pseudonymised/encrypted data as **anonymous** and out of scope | High | High | Recital 26; Art. 4(5) [1][6] | Recital 26 identifiability assessment; classify as personal data | Low |
| R2 | **Weak pseudonymisation** (naive hash of low-entropy IDs) reversed | Medium | High | ENISA pseudonymisation guidance [4][5] | Keyed/HMAC or encryption-based; segregated secrets | Low |
| R3 | **Differential privacy mis-parameterised** (ε too large; bad composition) | Medium | High | NIST SP 800-226 [9] | Documented ε/privacy unit; budget accounting; review | Low |
| R4 | **Synthetic data memorises** and leaks real records | Medium | High | ICO PETs guidance [2] | Leakage testing; DP-synthetic generation | Medium |
| R5 | **Federated learning updates leak** training data | Medium | High | FL privacy literature [21][22] | Secure aggregation + DP; poisoning defences | Medium |
| R6 | **Key/mapping co-located** with protected data | Medium | High | Art. 32 [1] | Separate KMS/token vault; access control | Low |
| R7 | Choosing an **immature/over-costly PET** (general FHE/SMPC) where a simpler control suffices | Medium | Medium | ICO/ENISA maturity caution [2][3] | Right-size to risk; pilot before scaling | Low |
| R8 | **TEE side-channel / vendor-trust** compromise | Low | High | Confidential-computing guidance [2][3] | Attestation; patching; layered controls | Medium |
| R9 | Assuming a PET **discharges accountability** (no DPIA) | Medium | High | Art. 5(2); Art. 35 [1] | PET recorded in DPIA; treat as control not proof | Low |

# Implementation Roadmap

- **Phase 0 — Baseline PETs:** Apply pseudonymisation/tokenisation and encryption (transit/at rest) with segregated key management across in-scope processing. *Effort:* Medium.
- **Phase 1 — Minimisation by design:** Introduce aggregation and, for external releases, k-anonymity/l-diversity/t-closeness with residual-risk assessment. *Effort:* Medium.
- **Phase 2 — Quantified privacy:** Adopt differential privacy (global first; local where data stays on-device) for analytics/ML, with documented ε and composition accounting. *Effort:* High.
- **Phase 3 — Collaborative & in-use protection:** Pilot federated learning + secure aggregation, SMPC, TEEs (and HE for narrow workloads) where raw-data pooling or untrusted infrastructure is unavoidable. *Effort:* High.
- **Phase 4 — Advanced minimisation:** Deploy ZKP-based attribute proofs (e.g. age assurance) and DP-synthetic data for sharing/testing. *Effort:* Medium–High.
- **Phase 5 — Assurance:** Leakage testing, PET effectiveness metrics, DPIA integration and periodic re-assessment of parameters and maturity. *Effort:* Ongoing.

# Compliance Maturity Model

*This model doubles as the maturity/selection matrix: it states each PET's primary GDPR function and engineering maturity.*

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | PETs ad hoc or absent; pseudonymisation/anonymisation conflated; encryption patchy. | No PET inventory; "anonymous" claims unassessed. |
| 2 | Managed | Baseline PETs (pseudonymisation, encryption) in place but keys/mappings poorly segregated. | Encryption present; weak key custody; no DP. |
| 3 | Defined | PETs selected by risk/function; Recital 26 assessments documented; aggregation/k-anonymity for releases. | Selection guide used; DPIA records PETs. |
| 4 | Quantitatively Managed | Differential privacy with governed ε/budget; leakage testing for synthetic data/FL; metrics on PET effectiveness. | ε accounting; membership-inference tests; KPIs. |
| 5 | Optimising | PETs combined and automated; confidential computing/SMPC/ZKP where justified; continuous parameter and maturity review. | Layered PETs; secure aggregation + DP; audit. |

**PET selection matrix (function × maturity):** pseudonymisation, tokenisation, encryption in transit/at rest — *security/risk reduction*, **Established** [1][4][12]; k-anonymity/l-diversity/t-closeness — *identifiability reduction*, **Established** [10][13][14][15]; differential privacy, synthetic data, TEEs, federated learning — *minimisation/identifiability/in-use*, **Maturing** [2][3][9][21]; SMPC, homomorphic encryption, ZKPs, encryption in use — *collaborative/in-use/minimisation*, **Emerging** [2][3][18][19][20]. *(Best practice grounded in obligation.)*

# Audit Questions

1. For any data you treat as **anonymous**, where is the **Recital 26** residual-identifiability assessment (means reasonably likely to be used)? *(Recital 26; Art. 4(5) [1][6].)*
2. How are **re-identification keys/token mappings** kept separate from the protected data, and who can access them? *(Art. 32 [1][4].)*
3. Where **differential privacy** is used, what is ε, the privacy unit, and the composition/budget accounting? *(NIST SP 800-226 [9].)*
4. How is **synthetic data** or a **federated model** tested for leakage before any privacy claim? *(ICO PETs guidance [2].)*
5. How did you **select** each PET against the specific privacy risk, and where is that recorded? *(Art. 25 [1][2].)*
6. For **SMPC/HE/TEE** use, what adversary/trust model and residual risks were assessed? *(ENISA/ICO [2][3].)*
7. How are PETs recorded in the **DPIA**, and how do you evidence they are controls rather than a substitute for accountability? *(Art. 5(2), Art. 35 [1][2].)*
8. How do you review PET **parameters and maturity** over time as attacks and tooling evolve? *([2][9].)*

# Implementation Checklist

- [ ] PET inventory mapping each in-scope processing operation to its PET(s) and GDPR function.
- [ ] Recital 26 identifiability assessment documented for any "anonymous" output.
- [ ] Pseudonymisation/tokenisation uses keyed/encryption-based techniques with segregated secrets.
- [ ] Encryption in transit and at rest applied; encryption in use (TEE/HE) evaluated for sensitive workloads.
- [ ] External releases protected by aggregation/k-anonymity (+ l-diversity/t-closeness) with residual-risk analysis.
- [ ] Differential privacy parameters (ε, privacy unit, composition) documented where DP is used.
- [ ] Synthetic-data and federated-learning outputs leakage-tested before reliance.
- [ ] SMPC/HE/TEE trust and adversary models assessed; PETs combined where one is insufficient.
- [ ] PET decisions, guarantees and residual risk recorded in the DPIA and accountability evidence.
- [ ] Periodic review of PET parameters, effectiveness and maturity.

# References

*All links verified live on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2016/679 (GDPR), consolidated text** — Articles 4(5), 5, 25, 32, 89 and Recitals 26, 28, 29, 78, 83. EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2016/679/oj

## Regulatory Guidance

- [2] **Privacy-enhancing technologies (PETs).** Information Commissioner's Office (ICO). https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-sharing/privacy-enhancing-technologies/
- [3] **Data Protection Engineering.** ENISA (2022). https://www.enisa.europa.eu/publications/data-protection-engineering
- [4] **Pseudonymisation Techniques and Best Practices.** ENISA (2019). https://www.enisa.europa.eu/publications/pseudonymisation-techniques-and-best-practices
- [5] **Data Pseudonymisation: Advanced Techniques and Use Cases.** ENISA (2021). https://www.enisa.europa.eu/publications/data-pseudonymisation-advanced-techniques-and-use-cases
- [6] **Introduction to anonymisation** (draft anonymisation, pseudonymisation and PETs guidance — spectrum of identifiability). ICO. https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/data-sharing/anonymisation/introduction-to-anonymisation/
- [7] **Privacy and Data Protection by Design — from policy to engineering.** ENISA. https://www.enisa.europa.eu/publications/privacy-and-data-protection-by-design
- [8] **The PET Guide** — UN Committee of Experts on Big Data and Data Science for Official Statistics (privacy-enhancing technologies for official statistics). United Nations. https://unstats.un.org/bigdata/task-teams/privacy/guide/

## Standards

- [9] **NIST SP 800-226 — Guidelines for Evaluating Differential Privacy Guarantees** (2025). NIST. https://csrc.nist.gov/pubs/sp/800/226/final
- [10] **ISO/IEC 20889:2018 — Privacy enhancing data de-identification terminology and classification of techniques.** ISO/IEC. https://www.iso.org/standard/69373.html
- [11] **ISO/IEC 27701 — Privacy Information Management System (PIMS).** ISO/IEC. https://www.iso.org/standard/71670.html
- [12] **ISO/IEC 27002:2022 — Information security controls** (incl. cryptographic controls / key management). ISO/IEC. https://www.iso.org/standard/75652.html

## Academic Sources

- [13] **Sweeney, L. (2002). "k-anonymity: a model for protecting privacy."** International Journal of Uncertainty, Fuzziness and Knowledge-Based Systems 10(5). https://dataprivacylab.org/dataprivacy/projects/kanonymity/kanonymity.pdf
- [14] **Machanavajjhala, A., Kifer, D., Gehrke, J., Venkitasubramaniam, M. (2007). "l-diversity: Privacy beyond k-anonymity."** ACM Transactions on Knowledge Discovery from Data 1(1). https://personal.utdallas.edu/~muratk/courses/privacy08f_files/ldiversity.pdf
- [15] **Li, N., Li, T., Venkatasubramanian, S. (2007). "t-Closeness: Privacy Beyond k-Anonymity and l-Diversity."** IEEE ICDE 2007. https://doi.org/10.1109/ICDE.2007.367856
- [16] **Dwork, C. (2006). "Differential Privacy."** ICALP 2006, LNCS 4052, Springer. https://link.springer.com/chapter/10.1007/11681878_14
- [17] **Dwork, C., Roth, A. (2014). "The Algorithmic Foundations of Differential Privacy."** Foundations and Trends in Theoretical Computer Science 9(3–4). https://www.cis.upenn.edu/~aaroth/Papers/privacybook.pdf
- [18] **Yao, A. C. (1982). "Protocols for Secure Computations."** 23rd IEEE Symposium on Foundations of Computer Science (FOCS). https://doi.org/10.1109/SFCS.1982.38
- [19] **Gentry, C. (2009). "Fully homomorphic encryption using ideal lattices."** ACM STOC 2009. https://doi.org/10.1145/1536414.1536440
- [20] **Goldwasser, S., Micali, S., Rackoff, C. (1989). "The Knowledge Complexity of Interactive Proof Systems."** SIAM Journal on Computing 18(1) (orig. STOC 1985). https://people.csail.mit.edu/silvio/Selected%20Scientific%20Papers/Proof%20Systems/The_Knowledge_Complexity_Of_Interactive_Proof_Systems.pdf
- [21] **McMahan, B., Moore, E., Ramage, D., Hampson, S., Agüera y Arcas, B. (2017). "Communication-Efficient Learning of Deep Networks from Decentralized Data" (federated learning).** AISTATS 2017; arXiv:1602.05629. https://arxiv.org/abs/1602.05629
- [22] **Kairouz, P., McMahan, H. B., et al. (2021). "Advances and Open Problems in Federated Learning."** Foundations and Trends in Machine Learning; arXiv:1912.04977. https://arxiv.org/abs/1912.04977
- [23] **Hoepman, J.-H. (2014). "Privacy Design Strategies."** IFIP SEC 2014, Springer; arXiv:1210.6621. https://arxiv.org/abs/1210.6621

# Further Reading

*Non-authoritative; provided for orientation only.*

- Royal Society — *Privacy Enhancing Technologies* report (adoption and use cases). https://royalsociety.org/news-resources/projects/privacy-enhancing-technologies/
- ISO/IEC 29134:2023 — Guidelines for privacy impact assessment (PET decisions feed the PIA/DPIA). https://www.iso.org/standard/86012.html

# Related Documents

- `privacy-engineering-foundations` — **parent**; introduces PETs, DPbDD (Art. 25) and Art. 32 controls (**prerequisite reading**).
- `gdpr-foundations` — personal data, identifiability and the Recital 26 anonymisation/pseudonymisation line.
- `dpia-methodology` — the DPIA that records PET selection, guarantee and residual risk.
- `anonymisation-techniques` — anonymisation methodology and re-identification-risk assessment (planned).
- `ai-act-foundations` / `ai-act-high-risk` — AI data-governance duties that PETs help implement.
- `privacy-threat-modelling` — LINDDUN threats that PET selection mitigates (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (GDPR Arts. 4(5), 5, 25, 32, 89; Recital 26), ICO PETs and anonymisation guidance, ENISA pseudonymisation/data-protection-engineering reports, NIST SP 800-226, ISO/IEC 20889/27701/27002, and the defining peer-reviewed literature (Sweeney; Machanavajjhala; Li; Dwork; Dwork & Roth; Yao; Gentry; Goldwasser–Micali–Rackoff; McMahan; Kairouz; Hoepman). ICO PETs-guidance currency and all external links live-verified. | — |
| 1.0.0 | 2026-07-11 | Editorial Reviewer (virtual agent) | Approved at sub-topics batch 3 human gate; frozen in release 0.14.0. | Human reviewer |
