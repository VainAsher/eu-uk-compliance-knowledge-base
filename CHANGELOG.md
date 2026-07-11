# Changelog

All notable changes to this repository. Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); the repository follows date-based releases (see `RELEASE_HISTORY.md`).

## [Unreleased]

### Added (in-review — awaiting batch human gate)
- `docs/06-ai-governance/ai-governance-foundations.md` — *(produced by parallel cluster; pending)*.
- `docs/07-data-act/data-act-foundations.md` — EU Data Act Foundations (v0.1.0, in-review). Data access/sharing, IoT connected products, cloud switching; application 12 Sep 2025 live-verified.
- `docs/08-digital-services/dsa-foundations.md` — EU DSA Foundations (v0.1.0, in-review). Platform tiers, VLOPs/VLOSEs, notice-and-action; X €120m fine (Dec 2025) live-verified.
- `docs/09-digital-markets/dma-foundations.md` — EU DMA Foundations (v0.1.0, in-review). Gatekeepers (7 designated), do's/don'ts; Apple €500m/Meta €200m (Apr 2025) live-verified.

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
