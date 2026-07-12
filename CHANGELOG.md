# Changelog

All notable changes to this repository. Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); the repository follows date-based releases (see `RELEASE_HISTORY.md`).

## [Unreleased]

*Nothing yet.*

## [0.17.0] — 2026-07-12

### Added (backlog loop — Cluster C; autonomous, workers self-ran all QA gates; auto-frozen on clean QA + orchestrator link re-verification)

- `docs/04-privacy-engineering/anonymisation-techniques.md` — anonymisation vs pseudonymisation; WP29 05/2014 three-criteria test; k-anonymity/l-diversity/t-closeness/differential privacy; **relative identifiability (Breyer; EDPS v SRB C-413/23 P, 2025)**; re-confirmed DUAA did not change the UK identifiability test.
- `docs/03-eprivacy/data-retention-caselaw.md` — the full CJEU line (Digital Rights Ireland → Tele2/Watson → La Quadrature I → Prokuratuur → SpaceNet → La Quadrature II C-470/21); **all ten ECLIs individually verified**; UK IPA 2016 divergence.
- `docs/08-digital-services/dsa-recommender-transparency.md` — DSA Arts. 27/38/26/28; non-profiling option; minors ad ban; TikTok/Meta addictive-design preliminary findings verified.
- `docs/09-digital-markets/dma-interoperability.md` — DMA Art. 7 messaging interoperability (E2EE safeguard, reference offer) + Art. 6(7); Apple Mar-2025 specification decisions; iMessage non-designation.
- `docs/10-nis2/nis2-transposition-tracker.md` — dated transposition snapshot (Medium; explicit "verify before relying"); Art. 41 deadline, reasoned opinions to 19 MS, CJEU referrals; IT D.Lgs 138/2024, DE NIS2UmsuCG.
- `docs/06-ai-governance/ai-model-risk-management.md` — AI Act Arts. 9/15/55; NIST AI RMF + GenAI profile; SR 11-7 → **SR 26-2 (17 Apr 2026)**, PRA SS1/23; red-teaming & dangerous-capability evals (Medium; the MRM↔AI crosswalk is a reasoned best-practice mapping).

### Changed

- `SOURCE_REGISTRY.md` — added 41 sources (incl. 12 CJEU data-retention judgments + the Charter and DRD as Primary; NIST SP 800-188; EDPB Pseudonymisation Guidelines 01/2025; SR 11-7/SR 26-2/SS1/23; UK AISI/Inspect; 5 arXiv evaluation papers).
- `GLOSSARY.md` — added 33 terms across anonymisation, DMA interoperability, data-retention doctrine, DSA recommender/profiling, AI model-risk-management, and NIS2 transposition.
- `MASTER_INDEX.md` — 6 catalogue rows, topic-coverage counts, knowledge-graph edges; `anonymisation-techniques` and `data-retention-caselaw` moved planned→approved.

## [0.16.0] — 2026-07-11

### Added (backlog loop — Cluster B; autonomous, workers self-ran all QA gates; auto-frozen on clean QA)

- `docs/01-gdpr/gdpr-ropa.md` — GDPR Art. 30 Records of Processing. **Live-verified the UK DUAA 2025 did NOT change Art. 30** (that was the dropped DPDI Bill); EU Art. 30(5) simplification recorded as *proposal only*.
- `docs/03-eprivacy/pecr-detail.md` — UK PECR marketing/cookies/enforcement; **DUAA PECR fine uplift to UK GDPR levels (£17.5m/4%)**, soft opt-in, charity exemption, cookie exemptions.
- `docs/04-privacy-engineering/privacy-threat-modelling.md` — LINDDUN (GO/PRO/MAESTRO) vs STRIDE; mapping into DPbDD (Art. 25) and DPIA (Art. 35). Backed by imec-DistriNet/KU Leuven + NIST Privacy Framework.
- `docs/11-dora/dora-oversight-framework.md` — DORA Arts. 31–44 CTPP oversight; delegated acts 2024/1502, 2024/1505, 2025/532; Lead Overseer powers.
- `docs/12-cybersecurity/cra-conformity-assessment.md` — CRA Art. 32 + **Annex VIII modules quoted verbatim**; important/critical product classes; notified bodies; AI-Act Art. 43 interplay.
- `docs/15-game-hosting/game-hosting-loot-boxes.md` — loot-box regulation (Medium): UK **not** under Gambling Act, NL Raad van State FIFA ruling (ECLI:NL:RVS:2022:690), BE/consumer-law routes.

### Changed

- **`docs/12-cybersecurity/cyber-resilience-act.md` → v1.0.1 (corrective patch).** Re-verified the CRA structural map verbatim against EUR-Lex (CELEX 32024R2847) while authoring `cra-conformity-assessment` and corrected three errors in the Legal Framework section: Chapter III is Arts. 27–34 (conformity, EU DoC, CE marking, conformity-assessment procedures); Chapter IV is Arts. 35–51 *Notification of conformity assessment bodies*; Annex VI is the *simplified* EU DoC and the conformity-assessment procedures live in Annex VIII (Annex VII = technical documentation). No obligation changed.
- `SOURCE_REGISTRY.md` — added `linddun` (imec-DistriNet/KU Leuven methodology).
- `GLOSSARY.md` — added LINDDUN, Lead Overseer, CE marking, simplified EU declaration of conformity, soft opt-in.
- `MASTER_INDEX.md` — 6 catalogue rows, topic-coverage counts, and knowledge-graph edges for Cluster B; `pecr-detail`/`privacy-threat-modelling` moved planned→approved.

## [0.15.0] — 2026-07-11

### Added (backlog loop — Cluster A; autonomous, workers self-ran all QA gates; auto-frozen on clean QA)

- `docs/07-data-act/data-act-cloud-switching.md` — Data Act Ch. VI/VIII; **Art. 29 charge-prohibition (12 Jan 2027) quoted verbatim** from EUR-Lex.
- `docs/08-digital-services/dsa-vlop-obligations.md` — Arts. 33–43; X €120m fine + **GC fee-annulment judgments (T-55/24, T-58/24)** + Art. 40 data-access delegated act.
- `docs/13-consumer-rights/dmcca-subscriptions.md` — DMCCA Part 4 Ch. 2 subscription regime (Spring 2027, PENDING-marked).
- `docs/06-ai-governance/ai-governance-iso-42001.md` — ISO/IEC 42001 AIMS implementation + AI-Act crosswalk (Medium: standard text paywalled).
- `docs/16-compliance-operations/compliance-audit-methodology.md` — ISO 19011 audit lifecycle + three-lines assurance.
- `docs/14-cloud-hosting/cloud-shared-responsibility.md` — shared-responsibility RACI matrix + assurance vehicles (Medium: EUCS unadopted, ISO editions shifting).

### Changed

- Corrected `iso-27018` registry entry to the **2025 edition** (flagged by the cloud worker; parent `cloud-hosting-foundations` still cites 2019 — noted for review cycle).

## [0.14.0] — 2026-07-11

### Added (third depth-layer sub-topic cluster — approved & frozen at v1.0.0; workers self-ran all three QA gates)

- `docs/05-ai-act/ai-act-prohibited-practices.md` — Art. 5 prohibited practices; verified the AI-Omnibus NCII/CSAM ("nudifier") addition.
- `docs/01-gdpr/gdpr-dsar.md` — data-subject rights & DSAR handling; **nine CJEU judgments**; DUAA subject-access changes (stop-the-clock, reasonable-and-proportionate search).
- `docs/10-nis2/nis2-incident-reporting.md` — significant-incident reporting; Implementing Reg 2024/2690 thresholds read from primary text (>€500k/5%; cloud/CDN >30 min).
- `docs/09-digital-markets/dma-obligations.md` — Arts. 5–7 obligation-by-obligation; current enforcement (Apple €500m/Meta €200m, Apple interop specification decisions) verified.
- `docs/02-uk-gdpr/uk-childrens-code.md` — the 15 AADC standards; DUAA s.81 children's-higher-protection duty.
- `docs/04-privacy-engineering/pets-catalogue.md` — technique-by-technique PETs catalogue with **eleven peer-reviewed academic sources**.
- Full-repo QA: `validate.py` **32/32, 0 issues**; markdownlint **CLEAN**; new-doc links **99/100 live**. Orchestrator spot-checked the NIS2 2024/2690 thresholds against the EUR-Lex text.

## [0.13.0] — 2026-07-11

### Added (Stage 10 — publication + RAG)

- **GitHub Pages site** (MkDocs Material): `mkdocs.yml` + `docs/index.md` (landing page with coverage stats, per-tier document list and the embedded knowledge graph), generated by `scripts/build_site.py` (tier-grouped nav from the catalogue).
- **`.github/workflows/pages.yml`** — regenerates the site and builds MkDocs (`--strict`), then deploys to GitHub Pages on push to `main`.
- **RAG export** — `scripts/build_rag.py` → `exports/rag/chunks.jsonl` (598 section-level chunks, ~222k tokens) + `manifest.json`, each chunk carrying document metadata.
- CI (`qa.yml`) now regenerates the RAG + site artefacts and staleness-checks `exports/`, `mkdocs.yml` and `docs/index.md`.

### Changed

- `validate.py` / `build_rag.py` skip the generated `docs/index.md` landing page.
- `build_graph.py` / `build_site.py` outputs made deterministic (no date stamp) so staleness checks pass on any CI run.

## [0.12.0] — 2026-07-11

### Added (knowledge-graph & compliance-mapping export)

- `scripts/build_graph.py` — generates machine-readable exports from the catalogue + front matter, and validates cross-references (fails on edges to non-existent, non-`(planned)` ids).
- `exports/` — `knowledge-graph.json` (26 nodes, 136 typed edges), `knowledge-graph.mmd` (Mermaid), `compliance-matrix.csv` + `.json`, `coverage.md`, and an `exports/README.md`.
- CI (`qa.yml`): runs `build_graph.py` on every push/PR (cross-reference gate) and fails if committed `exports/` are stale.

### Changed

- `scripts/README.md` — cross-reference validator moved from "recommended" to implemented.

## [0.11.0] — 2026-07-11

### Added (second depth-layer sub-topic cluster — approved & frozen at v1.0.0; parallel cluster; workers self-ran the QA validators)

- `docs/04-privacy-engineering/dpia-methodology.md` — DPIA methodology (Art. 35/36, WP248, ICO list & template, ISO 29134).
- `docs/05-ai-act/ai-act-gpai.md` — GPAI & systemic risk (Arts. 51–56; **GPAI Code of Practice published 10 Jul 2025**; 10²⁵ FLOP; GPAI **not** postponed by the AI Omnibus).
- `docs/03-eprivacy/digital-omnibus.md` — the Digital Omnibus package: **AI strand adopted** vs **data/ePrivacy strand proposed** (with an adopted-vs-proposed table). Confidence Medium.
- `docs/02-uk-gdpr/uk-transfers.md` — UK transfers: data bridges, IDTA/Addendum, TRA; **DUAA "data protection test" in force 5 Feb 2026** (SI 2026/82 reg. 2).
- `docs/03-eprivacy/cookie-consent-implementation.md` — cookie consent & CMPs; **EDPB Opinion 08/2024** (consent or pay) + **IAB Europe C-604/22** (TC String personal data).
- `docs/11-dora/dora-tlpt.md` — DORA threat-led penetration testing; **RTS on TLPT finalised** (Delegated Reg (EU) 2025/1190, in force 8 Jul 2025) + TIBER-EU alignment.
- Full-repo QA: `validate.py` **26/26 files, 0 issues**; `check_links.py` **237/238 live** (1 allowlisted).

## [0.10.1] — 2026-07-11

### Added (QA automation — the `scripts/README.md` toolchain, now implemented)

- `scripts/validate.py` — offline validator: front matter, the 23-section template structure, and citation integrity (`[n]` contiguity + resolution). CI-gating.
- `scripts/check_links.py` — network link checker over all docs + registries (GET via curl, bot-block allowlist).
- `.markdownlint.jsonc` — markdownlint config tuned to the house style.
- `.github/workflows/qa.yml` — CI: validator + markdownlint on push/PR; link check weekly + on dispatch.
- Rewrote `scripts/README.md` to document implemented vs. recommended tooling.

### Fixed (defects surfaced by the new validators)

- `docs/02-uk-gdpr/uk-gdpr-foundations.md` → **v1.0.1**: added in-text citations for refs [5] and [10] (listed but uncited — caught by `validate.py`).
- `docs/11-dora/dora-foundations.md` → **v1.0.1**: added in-text citation for ref [4] (listed but uncited).
- Repo-wide: `markdownlint --fix` normalized whitespace/emphasis (cosmetic; no content change).

## [0.10.0] — 2026-07-11

### Added (first depth-layer sub-topic cluster — approved & frozen at v1.0.0; parallel cluster)

- `docs/01-gdpr/gdpr-transfers.md` — GDPR International Transfers (Chapter V). SCCs/BCRs/adequacy/derogations; **EU-US DPF verified valid-but-contingent** (Latombe upheld at GC 3 Sep 2025; appeal C-703/25 P pending); UK IDTA/data-bridge.
- `docs/02-uk-gdpr/duaa-2025-detail.md` — DUAA 2025 detailed analysis. Recognised legitimate interests, ADM (Arts 22A–22D), complaints; **commencement verified** (Part 5 in force 5 Feb 2026 via SI 2026/82; s.103 due 19 Jun 2026).
- `docs/05-ai-act/ai-act-high-risk.md` — AI Act high-risk & conformity assessment. Annex III, Arts 8–15, CE marking, FRIA.
- `docs/12-cybersecurity/cyber-resilience-act.md` — CRA product cybersecurity. PDE classes, vulnerability reporting, phased dates (full application 11 Dec 2027).

### Changed (corrective maintenance — regulatory-change management)

- `docs/05-ai-act/ai-act-foundations.md` bumped **v1.0.0 → v1.1.0**: the **AI Omnibus is now FORMALLY ADOPTED** (EP plenary 16 Jun 2026; **Council final approval 29 Jun 2026** — orchestrator-verified via the Council press release). Updated the change gate, exec summary, key takeaways, background, regulatory interpretation, operational guidance, risk R5, audit Q7 and references [6][7]; the reform is no longer "provisional." First live regulatory-change correction to a frozen document.

### Added (Tier 4 cluster batch — all approved & frozen at v1.0.0; parallel cluster — final foundation tier)

- `docs/13-consumer-rights/consumer-rights-foundations.md` — Consumer Rights (EU & UK). CRD/UCPD/UCTD/DCD/SGD/Omnibus, CRA 2015, and DMCCA 2024 live-verified (consumer provisions in force 6 Apr 2025; subscription regime delayed to Spring 2027).
- `docs/14-cloud-hosting/cloud-hosting-foundations.md` — Cloud Hosting synthesis (Art. 28/32, transfers, NIS2, DORA, Data Act switching, ISO 27017/27018). EUCS confirmed not yet adopted. Confidence Medium (moving targets).
- `docs/15-game-hosting/game-hosting-foundations.md` — Game Hosting synthesis (children's data/AADC, PECR/SDKs, DSA, loot boxes, PEGI June-2026 changes). Confidence Medium.
- `docs/16-compliance-operations/compliance-operations-foundations.md` — Compliance Operations capstone (three lines, ISO 37301/31000, RoPA/DPIA, incident management across GDPR/NIS2/DORA). Ties together all 16 topics.

### Milestone

- **🏁 ALL 16 FOUNDATION TOPICS COMPLETE** — the full foundation layer of the knowledge base is approved & frozen (12 High confidence, 2 Medium).

### Quality

- Orchestrator re-verified all 69 links live; spot-checked DMCCA 2024 commencement (SI 2025/272, 6 Apr 2025); deduped overlapping consumer-law sources between #13 and #15.

## [0.8.0] — 2026-07-11

### Added (Tier 3 cluster batch — all approved & frozen at v1.0.0; parallel cluster)

- `docs/10-nis2/nis2-foundations.md` — NIS2 Foundations. Essential/important entities, Art. 21 measures, Art. 23 incident cascade (24h/72h/1-month), Art. 34 fines. Transposition status live-verified (CJEU referral of IE/ES/FR/NL, Jul 2026).
- `docs/11-dora/dora-foundations.md` — DORA Foundations. Five pillars, CTPP oversight; 17 Jan 2025 application + first RTS + 18 Nov 2025 CTPP designation live-verified.
- `docs/12-cybersecurity/cybersecurity-foundations.md` — Cybersecurity Foundations. ISO 27001/27002:2022, NIST CSF 2.0 (Govern function), OWASP Top 10:2025, zero trust, Cyber Resilience Act (Reg (EU) 2024/2847). Academic source: Saltzer & Schroeder (1975).

### Milestone

- **Tier 3 (security & resilience) complete** — NIS2, DORA, Cybersecurity approved & frozen. Topic coverage **12/16**.

### Quality

- Orchestrator re-verified all 34 links live; spot-checked NIS2 Art. 23 timeline and Art. 34 fines against the EUR-Lex raw enacting text (confirmed) and the DORA CTPP designation date.

## [0.7.0] — 2026-07-11

### Added (Tier 2 cluster batch — all approved & frozen at v1.0.0; produced by the parallel cluster)

- `docs/06-ai-governance/ai-governance-foundations.md` — AI Governance Foundations. ISO/IEC 42001, NIST AI RMF (+GenAI Profile), OECD Principles, operational assurance; 16 references, all links verified.
- `docs/07-data-act/data-act-foundations.md` — EU Data Act Foundations. Data access/sharing, IoT connected products, cloud switching; application 12 Sep 2025 live-verified.
- `docs/08-digital-services/dsa-foundations.md` — EU DSA Foundations. Platform tiers, VLOPs/VLOSEs, notice-and-action; X €120m fine (Dec 2025) live-verified.
- `docs/09-digital-markets/dma-foundations.md` — EU DMA Foundations. Gatekeepers (7 designated), do's/don'ts; Apple €500m/Meta €200m (Apr 2025) live-verified.

### Milestone

- **Tier 2 (digital & AI regulation) complete** — AI Act, AI Governance, Data Act, DSA, DMA all approved & frozen. Topic coverage 9/16.

### Quality

- Orchestrator re-verified all 39 links live; spot-checked DSA Arts. 49/52/56/74/76 and Recitals 9/12/22 against EUR-Lex enacting text before freeze.
- First batch produced via the **parallel cluster** model (4 documents concurrently).

## [0.6.0] — 2026-07-11

### Added

- `docs/05-ai-act/ai-act-foundations.md` — EU AI Act Foundations (**v1.0.0, approved & frozen**; first Tier 2 doc). Covers the four risk tiers, GPAI/systemic risk, governance (AI Office), penalties, and the phased timeline. **Live-verified** the AI Omnibus provisional agreement (7 May 2026) postponing high-risk to 2 Dec 2027 / 2 Aug 2028 — flagged as awaiting formal adoption. 6 references, all links verified live 2026-07-11.
- Source registry: AI Act ELI, EC AI framework, Digital Omnibus on AI, EP AI-omnibus deal, ISO/IEC 42001.
- Glossary: AI system, GPAI model, high-risk AI system, AI Office.

### Changed

- Introduced the **parallel cluster** production model (orchestrator + per-document worker agents) to speed foundation-doc production while retaining quality and the human gate.
- Document #5 approved at the human review gate and bumped 0.1.0 → 1.0.0.

## [0.5.0] — 2026-07-11

### Added

- `docs/04-privacy-engineering/privacy-engineering-foundations.md` — Privacy Engineering Foundations (**v1.0.0, approved & frozen**). Covers DPbDD (Art. 25), security of processing (Art. 32), privacy design strategies, PETs, and the ISO/NIST frameworks. 9 references across all four classes incl. an academic source (Hoepman). NIST Privacy Framework version status live-verified (v1.0 current; v1.1 in draft). All links verified live 2026-07-11.
- Source registry: EDPB Guidelines 4/2019, ICO DPbDD, ENISA PbD, NIST Privacy Framework, ISO/IEC 29100, Hoepman.
- Glossary: DPbDD, TOMs, PET, differential privacy.

### Milestone

- **Tier 1 (data-protection core) complete** — GDPR, UK GDPR, ePrivacy, Privacy Engineering all approved & frozen.

### Changed

- Document #4 approved at the human review gate (removed unsourced ISO/IEC 27018 citation) and bumped 0.1.0 → 1.0.0.

## [0.4.0] — 2026-07-11

### Added

- `docs/03-eprivacy/eprivacy-foundations.md` — ePrivacy Foundations (**v1.0.0, approved & frozen**). Covers the ePrivacy Directive as lex specialis to the GDPR, the Art. 5(3) cookie/consent rule, direct marketing (Art. 13), PECR transposition, Planet49, and the 2025 reform status (ePrivacy Regulation withdrawal + Digital Omnibus). 9 references, all links verified live 2026-07-11.
- Source registry: ePrivacy Directive, Planet49, PECR 2003, EDPB interplay opinion, EP legislative-train (reform + omnibus), ICO PECR, EC ePrivacy policy.
- Glossary: lex specialis, cookie rule (Art. 5(3)), PECR.

### Changed

- Document #3 approved at the human review gate (citation audit corrected ICO attributions) and bumped 0.1.0 → 1.0.0.

## [0.3.0] — 2026-07-10

### Added

- `docs/02-uk-gdpr/uk-gdpr-foundations.md` — UK GDPR Foundations (**v1.0.0, approved & frozen**). Covers the EUWA 2018 basis, UK GDPR/DPA 2018 relationship, key divergences (consent age 13), the Data (Use and Access) Act 2025 reforms, and the EU adequacy renewal to 2031. 11 references, all links verified live 2026-07-10.
- Source registry: EUWA 2018 s.3, DPA 2018 s.9, DUAA 2025, ICO/GOV.UK/EC adequacy sources.
- Glossary: UK GDPR, assimilated law, adequacy decision.

### Changed

- Document #2 approved at the human review gate and bumped 0.1.0 → 1.0.0.

## [0.2.0] — 2026-07-10

### Added

- `docs/01-gdpr/gdpr-foundations.md` — GDPR Foundations (**v1.0.0, approved & frozen**). Full 24-section document; 11 references (6 primary incl. 4 CJEU judgments, 3 regulatory, 2 standards), all links verified live 2026-07-10.
- `GLOSSARY.md` — shared authoritative definitions across the knowledge base (seeded with 11 GDPR terms).
- Source registry entries: Google Spain, Nowak, Breyer, Schrems II, EC legal-framework page, ISO/IEC 27701.
- Knowledge-graph edges from `gdpr-foundations` to four planned Tier 1/2 documents.

### Changed

- `ROADMAP.md` — adopted document-scoping policy (dedicated sub-topic docs over mega-documents); expanded GDPR into a planned document set.
- Document #1 approved at the human review gate and bumped 0.1.0 → 1.0.0.

## [0.1.0] — 2026-07-10

### Added

- Git version control (branch `main`) and `.gitignore` / `.gitattributes`.
- Full ~24-section `templates/document_template.md` (reconciled to bootstrap spec).
- Governance scaffolding: `AGENTS.md`, `ROADMAP.md`, `PROJECT_STATUS.md`, `PROJECT_HANDOVER.md`, `MASTER_INDEX.md`, `CHANGELOG.md`, `RELEASE_HISTORY.md`, `SOURCE_REGISTRY.md`.

### Changed

- Flattened nested `Compliance_Research_Bootstrap/` directory to repository root.

### Superseded

- Thin 15-section starter template replaced by the full specification.
