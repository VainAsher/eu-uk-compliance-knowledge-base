# Project Status

**Last updated:** 2026-07-11
**Maturity:** Stage 8 of 10 — *QA automation live; 26 documents approved (16 foundations + 10 depth sub-topics; releases through 0.11.0). Publication/RAG still ahead.*

## Maturity model (repository level)

| Stage | Description | State |
|-------|-------------|-------|
| 0 | Bare starter kit | ✅ passed |
| 1 | Governance scaffolding + reconciled template + git | ✅ passed |
| 2 | First document approved & frozen | ✅ passed |
| 3 | Tier 1 foundations complete (4 docs) | ✅ passed |
| 4 | Tier 2 digital & AI complete | ✅ passed |
| 5 | Tier 3 security & resilience complete | ✅ passed |
| 6 | Tier 4 sector/consumer/ops complete | ✅ **current** |
| 7 | Cross-references & knowledge graph populated | 🟡 partial (knowledge graph populated; sub-topics pending) |
| 8 | QA automation (lint/link/citation) implemented | ✅ **current** |
| 9 | Wiki.js / GitHub publication pipeline | ⬜ |
| 10 | RAG-ready export + audit dossier | ⬜ |

## Completed work

- Flattened nested repository; initialised git on `main`.
- Reconciled `templates/document_template.md` to the full ~24-section specification.
- Created governance/control files: `AGENTS.md`, `ROADMAP.md`, `PROJECT_STATUS.md`, `PROJECT_HANDOVER.md`, `MASTER_INDEX.md`, `CHANGELOG.md`, `RELEASE_HISTORY.md`, `SOURCE_REGISTRY.md`, `GLOSSARY.md`.
- **Document #1 (GDPR Foundations) approved & frozen at v1.0.0 (release 0.2.0).**
- **Document #2 (UK GDPR Foundations) approved & frozen at v1.0.0 (release 0.3.0).**
- **Document #3 (ePrivacy Foundations) approved & frozen at v1.0.0 (release 0.4.0).**
- **Document #4 (Privacy Engineering Foundations) approved & frozen at v1.0.0 (release 0.5.0) — Tier 1 complete.**
- **Document #5 (AI Act Foundations) approved & frozen at v1.0.0 (release 0.6.0).**
- **Tier 2 batch (#6–#9: AI Governance, Data Act, DSA, DMA) approved & frozen at v1.0.0 (release 0.7.0) — Tier 2 complete.** First parallel-cluster batch.
- **Tier 3 batch (#10–#12: NIS2, DORA, Cybersecurity) approved & frozen at v1.0.0 (release 0.8.0) — Tier 3 complete.**
- **Tier 4 batch (#13–#16: Consumer Rights, Cloud Hosting, Game Hosting, Compliance Operations) approved & frozen at v1.0.0 (release 0.9.0) — 🏁 all 16 topics complete.**
- Adopted shared-glossary + sub-topic-scoping editorial policy; introduced parallel-cluster production (3 batches, 11 docs).

## In progress

- **Second depth-layer sub-topic cluster (#21–#26) approved & frozen at v1.0.0 (release 0.11.0).** 26 documents total.
- Remaining phases: knowledge-graph/compliance-mapping export, and publication/RAG (needs a git remote). Further sub-topic clusters can run any time.

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
| Approved documents | 26 (16 foundations + 10 sub-topics) |
| Draft documents | 0 |
| Governance files | 9 |
| Topics covered | 16 / 16 ✅ (7 topics now have depth docs) |
| Sources in registry | see `SOURCE_REGISTRY.md` |
