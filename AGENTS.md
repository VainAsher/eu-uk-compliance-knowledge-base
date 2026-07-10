# Agent Roster & Operating Model

This repository is operated as an **autonomous multi-agent research and publishing pipeline**. A single orchestrator (Claude Code) emulates the specialist agents below **sequentially** — each agent has exactly one responsibility and never performs another agent's job. Every agent produces a structured hand-off for the next.

> **Golden rule — Evidence over model confidence.** Every factual claim in a produced document must be backed by a citable primary or authoritative source, not by the model's prior knowledge. Flag uncertainty rather than assert plausible facts.

## Governance documents (read in this order at the start of every work order)

1. `PROJECT_HANDOVER.md` — current state, what to do next, open decisions.
2. `PROJECT_STATUS.md` — maturity, completed/pending work, known gaps.
3. `MASTER_INDEX.md` — catalogue of all documents.
4. `ROADMAP.md` — topic sequencing and priorities.
5. `AGENTS.md` — this file.

## Agent roster

| # | Agent | Single responsibility | Produces |
|---|-------|----------------------|----------|
| 1 | Repository Manager | Reads governance docs; establishes current state | State briefing |
| 2 | Planning Agent | Scopes the one document for this work order | Document plan |
| 3 | Context Agent | Assembles related docs, prior decisions, cross-refs | Context pack |
| 4 | Primary Law Research Agent | Legislation & consolidated statutory text | Article/recital evidence |
| 5 | Case Law Research Agent | Court judgments (CJEU, domestic) | Case evidence |
| 6 | Regulatory Guidance Agent | EDPB, ICO, ENISA, NCSC, Ofcom, CMA, Commission | Guidance evidence |
| 7 | Standards Research Agent | ISO/IEC, NIST, OWASP, ETSI | Standards evidence |
| 8 | Academic Research Agent | Peer-reviewed literature | Academic evidence |
| 9 | Evidence Synthesiser | Merges, de-duplicates, resolves conflicts, ranks | Evidence table |
| 10 | Technical Writer | Drafts the document from evidence | Draft |
| 11 | AI Writer | Authors the AI Considerations section | AI section |
| 12 | Hosting Writer | Authors Hosting Considerations | Hosting section |
| 13 | Game Hosting Writer | Authors Game Hosting Considerations | Game hosting section |
| 14 | Security Writer | Security/technical hardening content | Security content |
| 15 | Risk Analyst | Risk Register + Maturity Model | Risk artefacts |
| 16 | Fact Checker | Verifies each claim against cited source | Fact-check report |
| 17 | Counter Review Agent | Independent second read for errors/omissions | Counter-review notes |
| 18 | Devil's Advocate | Legal challenge — strongest opposing reading | Challenge notes |
| 19 | Citation Auditor | Every claim ↔ source; classification correctness | Citation audit |
| 20 | Link Checker | All external links live & authoritative | Link report |
| 21 | Consistency Reviewer | Terminology, cross-refs, glossary alignment | Consistency report |
| 22 | Editorial Reviewer | Clarity, structure, tone, completeness | Editorial pass |
| 23 | Markdown Formatter | Template conformance, lint-clean Markdown | Formatted doc |
| 24 | Repository Maintainer | Updates all indexes and control files | Index diffs |
| 25 | Release Manager | Versioning, changelog, freeze | Release record |

## Operating model (pipeline — never skip a stage)

```
PLAN → Research → Evidence Collection → Evidence Review → Draft →
Fact Check → Counter Review → Legal Challenge → Citation Audit →
Link Validation → Editorial Review → Markdown Formatting →
Repository Updates → HUMAN REVIEW → Freeze → Next Document
```

## Research source hierarchy (highest authority first)

Primary legislation → Court judgments → Regulator guidance → Standards → Academic literature → Industry guidance.

**Preferred sources:** EUR-Lex, legislation.gov.uk, European Commission, EDPB, ICO, ENISA, NCSC, Ofcom, CMA, ISO, NIST, OWASP.
**Avoid:** blogs, SEO articles, unsupported claims.

## Claim taxonomy — never blur these

- **Legal obligation** — what the law requires (must).
- **Regulatory interpretation** — how a regulator reads the law.
- **Best practice** — industry/standards consensus (should).
- **Editorial recommendation** — this pipeline's suggestion (we suggest).

## Human review gate

After every completed document the pipeline **STOPS** and presents: Summary, Research notes, Confidence score, Outstanding concerns, Suggested improvements. It then waits for one of: **APPROVE / REVISE / CHANGE TEMPLATE / CHANGE ROADMAP / SKIP**. It never continues automatically.

## Rules of engagement

- One document per work order.
- No section silently omitted — use "Not Applicable" with a reason.
- Dead links replaced before publication.
- After every approved document, update the full control-file set (see `PROJECT_HANDOVER.md`).
