# Research Roadmap

Sequencing of the 16 programme topics. Ordered so that foundational instruments and cross-cutting concepts land first, since later documents cross-reference them. Sequencing is an **editorial recommendation** and may be changed via the `CHANGE ROADMAP` human-review action.

## Priority tiers

### Tier 1 — Foundations (data protection core)
These underpin almost everything else and are cited by later documents.

| Order | Topic | Lead instrument(s) | Rationale |
|-------|-------|--------------------|-----------|
| 1 | **GDPR (EU)** ✅ approved | Regulation (EU) 2016/679 | Root of the data-protection framework; referenced everywhere. |
| 2 | **UK GDPR** ✅ approved | UK GDPR + DPA 2018 | Post-Brexit divergence; builds directly on #1. |
| 3 | **ePrivacy** ✅ approved | Directive 2002/58/EC | Lex specialis to GDPR for communications/cookies. |
| 4 | **Privacy Engineering** ⏳ next | ISO 27701, GDPR Art. 25 | Implementation layer for #1–#3. |

### Tier 2 — Digital & AI regulation
| Order | Topic | Lead instrument(s) | Rationale |
|-------|-------|--------------------|-----------|
| 5 | **AI Act** | Regulation (EU) 2024/1689 | Flagship AI law; overlaps GDPR. |
| 6 | **AI Governance** | AI Act + ISO/IEC 42001 | Operationalising #5. |
| 7 | **Data Act** | Regulation (EU) 2023/2854 | Data access/sharing; interacts with GDPR. |
| 8 | **Digital Services** | Regulation (EU) 2022/2065 (DSA) | Platform obligations. |
| 9 | **Digital Markets** | Regulation (EU) 2022/1925 (DMA) | Gatekeeper obligations. |

### Tier 3 — Security & resilience
| Order | Topic | Lead instrument(s) | Rationale |
|-------|-------|--------------------|-----------|
| 10 | **NIS2** | Directive (EU) 2022/2555 | Baseline cybersecurity for essential/important entities. |
| 11 | **DORA** | Regulation (EU) 2022/2554 | Financial-sector operational resilience. |
| 12 | **Cybersecurity** | NIS2, ISO 27001, NIST CSF, NCSC | Cross-cutting technical security. |

### Tier 4 — Sector, consumer & operations
| Order | Topic | Lead instrument(s) | Rationale |
|-------|-------|--------------------|-----------|
| 13 | **Consumer Rights** | Consumer Rights Act 2015; Dir. 2011/83/EU | B2C obligations. |
| 14 | **Cloud Hosting** | GDPR, NIS2, ISO 27017 | Infrastructure compliance. |
| 15 | **Game Hosting** | GDPR (children/Art.8), DSA, PEGI | Sector specialisation of #14. |
| 16 | **Compliance Operations** | Cross-cutting | How to run the programme; ties everything together. |

## Backlog & known gaps

See `PROJECT_STATUS.md` → *Known Gaps* and *Research Backlog*.

## Document-scoping policy (editorial standard, 2026-07-10)

Confirmed with the user: **prefer narrowly-scoped, dedicated sub-topic documents over mega-documents.** Each topic opens with a focused *Foundations* document, then deeper areas are split into their own documents rather than bloating the flagship. Shared terms live in `GLOSSARY.md`, not repeated in full per document.

### GDPR (EU) — planned document set

| # | Document | Status |
|---|----------|--------|
| 1 | `gdpr-foundations` — Foundations & Core Principles | ✅ approved (v1.0.0) |
| — | `gdpr-dsar` — Data-subject rights & DSAR handling (Arts. 12–23) | backlog |
| — | `gdpr-transfers` — International transfers (Chapter V) | backlog |
| — | `gdpr-dpia` — Data Protection Impact Assessments (Art. 35) | backlog |
| — | `gdpr-ropa` — Records of processing (Art. 30) | backlog |
| — | `gdpr-lawful-basis` — Lawful bases in depth incl. legitimate-interests balancing | backlog |

The same split applies to every topic (e.g., NIS2 → foundations, incident reporting, supply-chain; AI Act → foundations, high-risk obligations, GPAI).

## Notes

- Documents may be produced out of order on request (`CHANGE ROADMAP`).
- The roadmap tracks topics and their planned document sets; `MASTER_INDEX.md` tracks individual documents.
