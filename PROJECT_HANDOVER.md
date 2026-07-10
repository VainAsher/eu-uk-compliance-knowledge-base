# Project Handover

**Read this first.** This is the single source of truth for "what is going on and what to do next." Every work order begins by reading this file, then `PROJECT_STATUS.md`, `MASTER_INDEX.md`, `ROADMAP.md`, and `AGENTS.md`.

**Last updated:** 2026-07-10

## What this project is

An autonomous multi-agent pipeline that produces a professional, evidence-based compliance knowledge base across 16 topics (see `ROADMAP.md`). Deliverables are Markdown documents suitable for legal research, compliance implementation, developer guidance, AI retrieval (RAG), Wiki.js and GitHub publication, and audit support.

## Current state (snapshot)

- **Maturity:** Stage 2 — Document #1 (GDPR Foundations) approved & frozen at v1.0.0 in release 0.2.0.
- **Version control:** git initialised locally on branch `main`. No remote yet.
- **Template:** `templates/document_template.md` reconciled to full spec.
- **Governance files:** all present, incl. `GLOSSARY.md`.
- **Editorial policy:** shared glossary + dedicated sub-topic documents (see `ROADMAP.md`).

## What to do next

1. Produce **Document #2: UK GDPR Foundations** (`docs/02-uk-gdpr/uk-gdpr-foundations.md`) through the full pipeline, applying the sub-topic-scoping and glossary policy.
2. Present it at the **human review gate** and wait for a decision.
3. On `APPROVE`: freeze it, update all control files, then start Document #3 (ePrivacy) per `ROADMAP.md`.

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

## Control files to update after every approved document

`MASTER_INDEX.md` · `PROJECT_STATUS.md` · `PROJECT_HANDOVER.md` · `CHANGELOG.md` · `RELEASE_HISTORY.md` · `SOURCE_REGISTRY.md` · Known Gaps · Research Backlog · Cross-references · Knowledge Graph · Repository statistics.

## Hard rules

- One document per work order.
- Evidence over model confidence.
- Never skip a pipeline stage.
- Never continue past the human review gate automatically.
