# Project Status

**Last updated:** 2026-07-11
**Maturity:** Stage 2 of 10 — *Tier 1 in progress: 3 of 4 foundation documents approved & frozen (release 0.4.0).*

## Maturity model (repository level)

| Stage | Description | State |
|-------|-------------|-------|
| 0 | Bare starter kit | ✅ passed |
| 1 | Governance scaffolding + reconciled template + git | ✅ passed |
| 2 | First document approved & frozen | ✅ **current** |
| 3 | Tier 1 foundations complete (4 docs) | ⬜ |
| 4 | Tier 2 digital & AI complete | ⬜ |
| 5 | Tier 3 security & resilience complete | ⬜ |
| 6 | Tier 4 sector/consumer/ops complete | ⬜ |
| 7 | Cross-references & knowledge graph populated | ⬜ |
| 8 | QA automation (lint/link/citation) implemented | ⬜ |
| 9 | Wiki.js / GitHub publication pipeline | ⬜ |
| 10 | RAG-ready export + audit dossier | ⬜ |

## Completed work

- Flattened nested repository; initialised git on `main`.
- Reconciled `templates/document_template.md` to the full ~24-section specification.
- Created governance/control files: `AGENTS.md`, `ROADMAP.md`, `PROJECT_STATUS.md`, `PROJECT_HANDOVER.md`, `MASTER_INDEX.md`, `CHANGELOG.md`, `RELEASE_HISTORY.md`, `SOURCE_REGISTRY.md`, `GLOSSARY.md`.
- **Document #1 (GDPR Foundations) approved & frozen at v1.0.0 (release 0.2.0).**
- **Document #2 (UK GDPR Foundations) approved & frozen at v1.0.0 (release 0.3.0).**
- **Document #3 (ePrivacy Foundations) approved & frozen at v1.0.0 (release 0.4.0).**
- Adopted shared-glossary + sub-topic-scoping editorial policy.

## In progress

- **Document #4: Privacy Engineering Foundations** (`docs/04-privacy-engineering/privacy-engineering-foundations.md`) — research, draft and QA **complete** (citation audit + evidence-hygiene fix; all 9 links verified 2026-07-11); **awaiting human review gate**. Completes Tier 1 on approval.

## Pending work

- Tier 1–4 topic documents per `ROADMAP.md` (16 topics, ≥16 documents).
- QA automation toolchain (`scripts/README.md` lists intended tools; none implemented).
- Knowledge graph / compliance-mapping artefacts.
- Publication pipeline (Wiki.js, GitHub Pages) and RAG export.

## Known gaps

| Gap | Impact | Planned resolution |
|-----|--------|--------------------|
| No automated link/citation validation | Manual checking only; risk of link rot | Stage 8 |
| No case-law coverage yet | Legal Framework sections rely on statute + guidance | Case Law Agent per document |
| No glossary file | Term consistency checked ad hoc | Introduce `GLOSSARY.md` in Tier 1 |
| No CI/GitHub remote | Version control is local only | Add remote when user provides one |

## Research backlog

- GDPR sub-topics: DSAR handling, International transfers (Chapter V), DPIAs (Art. 35), Records of processing (Art. 30).
- Cross-topic mapping: GDPR ↔ AI Act ↔ Data Act overlaps.
- Standards deep-dives: ISO/IEC 27001:2022, 27701, 42001; NIST CSF 2.0.

## Repository statistics

| Metric | Value |
|--------|-------|
| Approved documents | 3 |
| Draft documents | 1 (Doc #4 in production) |
| Governance files | 9 |
| Topics covered | 3 / 16 |
| Sources in registry | see `SOURCE_REGISTRY.md` |
