# EU & UK Compliance Knowledge Base

📖 **Rendered site:** <https://vainasher.github.io/eu-uk-compliance-knowledge-base/>

An autonomous multi-agent pipeline that produces a professional, evidence-based compliance knowledge base across 16 regulatory and technical topics (GDPR, UK GDPR, AI Act, Data Act, NIS2, DORA, ePrivacy, Consumer Rights, Digital Services, Digital Markets, AI Governance, Privacy Engineering, Cloud Hosting, Game Hosting, Cybersecurity, Compliance Operations).

**32 approved documents (~163k words)** — every factual claim carries a citation to a primary or authoritative source, and links, citations, structure and cross-references are checked automatically in CI. Deliverables are Markdown suitable for legal research, compliance implementation, developer guidance, AI retrieval (RAG) and audit support.

> **Golden rule — evidence over model confidence.** Every claim is backed by a citable primary or authoritative source.

## How it works

The repository is operated as a sequential multi-agent pipeline. See `AGENTS.md` for the agent roster and operating model.

```
PLAN → Research → Evidence → Draft → Fact Check → Counter Review →
Legal Challenge → Citation Audit → Link Validation → Editorial →
Formatting → Repository Updates → HUMAN REVIEW → Freeze → Next
```

## Repository map

| Path | Purpose |
|------|---------|
| `PROJECT_HANDOVER.md` | **Start here** — current state and next actions. |
| `PROJECT_STATUS.md` | Maturity, completed/pending work, known gaps. |
| `MASTER_INDEX.md` | Catalogue of all documents + knowledge graph. |
| `ROADMAP.md` | 16-topic sequencing and priorities. |
| `AGENTS.md` | Agent roster and operating model. |
| `SOURCE_REGISTRY.md` | Canonical authoritative sources. |
| `CHANGELOG.md` / `RELEASE_HISTORY.md` | Change tracking and releases. |
| `templates/document_template.md` | The mandatory ~24-section document template. |
| `docs/` | The knowledge base itself, organised `docs/<NN>-<topic>/`. |
| `prompts/` | Bootstrap and work-order prompts. |
| `scripts/` | Intended QA automation (not yet implemented). |

## Usage

1. Load `AGENTS.md` + governance files as context.
2. Provide a work order (`prompts/work_order.md`) scoping **one** document.
3. The pipeline researches, drafts, QAs, updates indexes, and stops for human review.
