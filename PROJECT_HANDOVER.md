# Project Handover

**Read this first.** This is the single source of truth for "what is going on and what to do next." Every work order begins by reading this file, then `PROJECT_STATUS.md`, `MASTER_INDEX.md`, `ROADMAP.md`, and `AGENTS.md`.

**Last updated:** 2026-07-10

## What this project is

An autonomous multi-agent pipeline that produces a professional, evidence-based compliance knowledge base across 16 topics (see `ROADMAP.md`). Deliverables are Markdown documents suitable for legal research, compliance implementation, developer guidance, AI retrieval (RAG), Wiki.js and GitHub publication, and audit support.

## Current state (snapshot)

- **Maturity:** Stage 4 — **Tiers 1–3 complete** (12 docs approved & frozen at v1.0.0; releases 0.2.0–0.8.0). Tier 4 is the final foundation tier.
- **Version control:** git on `main`, tags `v0.2.0`–`v0.8.0`. No remote yet.
- **Template:** `templates/document_template.md` reconciled to full spec.
- **Governance files:** all present, incl. `GLOSSARY.md`.
- **Editorial policy:** shared glossary + dedicated sub-topic documents (see `ROADMAP.md`).
- **Production model:** parallel cluster — orchestrator (owns control files, git, gate) + per-document worker agents (write own doc, return metadata). First batch (#6–#9) delivered 4 docs concurrently.

## What to do next

1. Run the **Tier 4 (sector, consumer & operations) cluster** — the final foundation tier: Consumer Rights (#13), Cloud Hosting (#14), Game Hosting (#15), Compliance Operations (#16).
2. Present the batch at the **human review gate**; on `APPROVE`, freeze and cut release 0.9.0.
3. After Tier 4: all 16 topics covered → move to Stage 5+ (backlog sub-topics, QA automation, knowledge graph, publication/RAG export). Consider `duaa-2025-detail`, `digital-omnibus`, `cyber-resilience-act` as high-value backlog docs.

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

## Control files to update after every approved document

`MASTER_INDEX.md` · `PROJECT_STATUS.md` · `PROJECT_HANDOVER.md` · `CHANGELOG.md` · `RELEASE_HISTORY.md` · `SOURCE_REGISTRY.md` · Known Gaps · Research Backlog · Cross-references · Knowledge Graph · Repository statistics.

## Hard rules

- One document per work order.
- Evidence over model confidence.
- Never skip a pipeline stage.
- Never continue past the human review gate automatically.
