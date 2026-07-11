# Project Handover

**Read this first.** This is the single source of truth for "what is going on and what to do next." Every work order begins by reading this file, then `PROJECT_STATUS.md`, `MASTER_INDEX.md`, `ROADMAP.md`, and `AGENTS.md`.

**Last updated:** 2026-07-10

## What this project is

An autonomous multi-agent pipeline that produces a professional, evidence-based compliance knowledge base across 16 topics (see `ROADMAP.md`). Deliverables are Markdown documents suitable for legal research, compliance implementation, developer guidance, AI retrieval (RAG), Wiki.js and GitHub publication, and audit support.

## Current state (snapshot)

- **Maturity:** Stage 7 — 16 foundation topics + 4 depth sub-topics approved (releases 0.2.0–0.10.0). `ai-act-foundations` at v1.1.0 (AI Omnibus adoption correction).
- **Version control:** git on `main`, tags `v0.2.0`–`v0.10.0`. No remote yet.
- **Regulatory-change management proven:** the depth cluster surfaced that the AI Omnibus was adopted (Council 29 Jun 2026); a corrective v1.1.0 revision to the frozen `ai-act-foundations` was applied and re-frozen — the model for keeping frozen docs current.
- **Template:** `templates/document_template.md` reconciled to full spec.
- **Governance files:** all present, incl. `GLOSSARY.md` (~70 terms) and `SOURCE_REGISTRY.md` (~120 sources).
- **Editorial policy:** shared glossary + dedicated sub-topic documents (see `ROADMAP.md`).
- **Production model:** parallel cluster — orchestrator (owns control files, git, gate, independent link re-verification + spot-checks) + per-document worker agents. Three batches delivered 11 docs concurrently.

## What to do next (Stage 7+ — depth, quality, publication)

The foundation layer (one flagship doc per topic) is done. The natural next phases:

1. **High-value backlog sub-topics** — e.g. `duaa-2025-detail`, `digital-omnibus`, `cyber-resilience-act`, `gdpr-transfers`, `dpia-methodology`, `ai-act-high-risk`. Each topic's planned document set is in `ROADMAP.md`; the full backlog is in `PROJECT_STATUS.md`.
2. **QA automation** — implement the toolchain in `scripts/README.md` (markdownlint, yamllint, lychee/markdown-link-check, vale, a citation validator, glossary consistency checker) + CI.
3. **Knowledge-graph / compliance-mapping artefacts** — machine-readable cross-reference and control-mapping exports.
4. **Publication / RAG** — Wiki.js or GitHub Pages publication and a chunked RAG export. Provide a git remote when ready to publish.

Each of the above can be run as a parallel cluster (for sub-topic docs) or as focused orchestrator work (automation/publication). Present at the human gate before freezing/publishing.

## Parallel-cluster operating notes (for the orchestrator)

- Workers write ONLY their own doc file and RETURN metadata (index row, glossary terms, source rows, knowledge-graph edges, QA report). They do not touch shared files or run git.
- Orchestrator merges metadata serially, **independently re-verifies all links** (curl), spot-checks flagged article/recital numbers against enacting text, then freezes and commits.
- Retain the human gate: present each batch for APPROVE/REVISE before freezing.

## Open decisions for the human

- **Git remote / publication target** — none configured. Provide a GitHub repo URL when ready to publish.
- **Directory convention** — documents live under `docs/<NN>-<topic>/<slug>.md`. Confirm or change.
- **Depth per topic** — one flagship document per topic first, or full sub-topic breakdown immediately? (Currently: flagship first, sub-topics in backlog.)

## Editorial decisions on record

| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-07-10 | Flatten nested repo; git init on `main` | User instruction; enables version control. |
| 2026-07-10 | Full 24-section template adopted | Matches bootstrap spec; supersedes thin starter template. |
| 2026-07-10 | Roadmap sequenced Tier 1 (data-protection core) first | Later docs cross-reference GDPR foundations. |
| 2026-07-10 | Document #1 (GDPR Foundations) approved & frozen at v1.0.0 | Passed human review gate; confidence High, all links verified. |
| 2026-07-10 | Adopt shared `GLOSSARY.md` + dedicated sub-topic documents | User feedback at Doc #1 approval; keeps flagship docs focused, avoids repeated definitions. |
| 2026-07-10 | Document #2 (UK GDPR Foundations) approved & frozen at v1.0.0 | Passed human review gate; DUAA 2025 + adequacy facts live-verified. |
| 2026-07-11 | Document #3 (ePrivacy Foundations) approved & frozen at v1.0.0 | Passed human review gate; ePrivacy Regulation withdrawal + Digital Omnibus live-verified. |
| 2026-07-11 | Document #4 (Privacy Engineering) approved & frozen at v1.0.0 — **Tier 1 complete** | Passed human review gate; NIST PF version status live-verified. |
| 2026-07-11 | Document #5 (AI Act) approved & frozen at v1.0.0 | Passed human review gate; AI Omnibus provisional status live-verified. |
| 2026-07-11 | Adopt parallel-cluster production model | User request to speed up while retaining quality; orchestrator + worker agents. |
| 2026-07-11 | Tier 2 batch (#6–#9) approved & frozen at v1.0.0 — **Tier 2 complete** | Batch human gate ("approve with spot check"); DSA article/recital numbers verified against EUR-Lex. |
| 2026-07-11 | Tier 3 batch (#10–#12) approved & frozen at v1.0.0 — **Tier 3 complete** | Batch human gate ("APPROVE ALL"); NIS2 Art. 23/34 verified against EUR-Lex raw text. |
| 2026-07-11 | Tier 4 batch (#13–#16) approved & frozen at v1.0.0 — **🏁 all 16 topics complete** | Batch human gate ("APPROVE ALL"); DMCCA 2024 commencement verified (SI 2025/272). |
| 2026-07-11 | Depth sub-topics batch (#17–#20) approved & frozen; `ai-act-foundations` corrected to v1.1.0 | Batch gate ("APPROVE ALL + apply AI Act correction"); AI Omnibus adoption (Council 29 Jun 2026) verified. |

## Control files to update after every approved document

`MASTER_INDEX.md` · `PROJECT_STATUS.md` · `PROJECT_HANDOVER.md` · `CHANGELOG.md` · `RELEASE_HISTORY.md` · `SOURCE_REGISTRY.md` · Known Gaps · Research Backlog · Cross-references · Knowledge Graph · Repository statistics.

## Hard rules

- One document per work order.
- Evidence over model confidence.
- Never skip a pipeline stage.
- Never continue past the human review gate automatically.
