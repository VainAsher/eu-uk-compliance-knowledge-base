# Changelog

All notable changes to this repository. Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); the repository follows date-based releases (see `RELEASE_HISTORY.md`).

## [Unreleased]

### Added
- `docs/02-uk-gdpr/uk-gdpr-foundations.md` — UK GDPR Foundations (v0.1.0, **in review**). Covers the EUWA 2018 basis, UK GDPR/DPA 2018 relationship, key divergences (consent age 13), the Data (Use and Access) Act 2025 reforms, and the EU adequacy renewal to 2031. 11 references, all links verified live 2026-07-10.
- Source registry: EUWA 2018 s.3, DPA 2018 s.9, DUAA 2025, ICO/GOV.UK/EC adequacy sources.
- Glossary: UK GDPR, assimilated law, adequacy decision.

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
