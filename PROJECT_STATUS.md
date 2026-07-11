# Project Status

**Last updated:** 2026-07-11
**Maturity:** Stage 10 of 10 (all complete) — *32 approved documents, QA automation, knowledge-graph/compliance/RAG exports, and a MkDocs GitHub Pages site with a deploy workflow (releases through 0.14.0). Repo on a private GitHub remote (CI green); enable Pages / make public to go live. Ongoing work is depth (more sub-topic clusters) + review cycles.*

## Maturity model (repository level)

| Stage | Description | State |
|-------|-------------|-------|
| 0 | Bare starter kit | ✅ passed |
| 1 | Governance scaffolding + reconciled template + git | ✅ passed |
| 2 | First document approved & frozen | ✅ passed |
| 3 | Tier 1 foundations complete (4 docs) | ✅ passed |
| 4 | Tier 2 digital & AI complete | ✅ passed |
| 5 | Tier 3 security & resilience complete | ✅ passed |
| 6 | Tier 4 sector/consumer/ops complete | ✅ passed |
| 7 | Cross-references & knowledge graph populated | ✅ passed (graph + compliance matrix exported) |
| 8 | QA automation (lint/link/citation) implemented | ✅ passed |
| 9 | GitHub Pages publication pipeline | ✅ passed (MkDocs Material + deploy workflow) |
| 10 | RAG-ready export + audit dossier | ✅ passed (`exports/rag/` section-level chunks) |

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

- **Third depth-layer sub-topic cluster (#27–#32) approved & frozen at v1.0.0 (release 0.14.0).** 32 documents total; 10 of 16 topics now have depth docs.
- **All 10 maturity stages complete;** ongoing work is depth (more clusters) + review cycles. To publish the site, make the repo public / enable Pages (see `PROJECT_HANDOVER.md`).

## Pending / optional work

- **More depth sub-topic clusters** — remaining backlog per topic (see `ROADMAP.md`), e.g. `gdpr-ropa`, `ai-act-conformity`, `dora-oversight-framework`, `dsa-vlop-risk-management`, `data-act-cloud-switching`, `pecr-detail`, `anonymisation-techniques`, `privacy-threat-modelling`, `nis2-transposition-tracker`.
- **Review cycles** — refresh volatile items before `review_due` 2027-07-11 (AI Omnibus OJ publication, EU-US DPF appeal, Digital Omnibus data strand, revised ICO Children's Code).
- **Publication** — make the repo public / enable GitHub Pages to deploy the built site.
- **Optional QA extras** — glossary-consistency checker, `vale` prose linting.

## Known gaps

| Gap | Impact | Status |
|-----|--------|--------|
| ~~No automated link/citation validation~~ | — | ✅ Resolved (Stage 8): `validate.py` + `check_links.py` + CI. |
| ~~No case-law coverage~~ | — | ✅ Resolved: 15+ CJEU judgments cited across GDPR/DSA/DMA/DSAR docs. |
| ~~No glossary file~~ | — | ✅ Resolved: `GLOSSARY.md` (~120 terms). |
| ~~No CI/GitHub remote~~ | — | ✅ Resolved: private repo `VainAsher/eu-uk-compliance-knowledge-base`; CI green. |
| Site not yet live | Rendered site not publicly accessible | Make repo public / enable Pages (free-plan constraint). |
| Per-Member-State transposition detail (NIS2) | National specifics not enumerated | Planned `nis2-transposition-tracker`. |

## Repository statistics

| Metric | Value |
|--------|-------|
| Approved documents | 32 (16 foundations + 16 sub-topics) |
| Draft documents | 0 |
| Governance files | 9 |
| Topics covered | 16 / 16 ✅ (10 topics now have depth docs) |
| Sources in registry | see `SOURCE_REGISTRY.md` |
