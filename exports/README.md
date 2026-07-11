# Exports

Machine-readable artefacts generated from the knowledge base by
`python scripts/build_graph.py`. **Do not edit by hand** — regenerate after any
change to `MASTER_INDEX.md` or a document's front matter. CI fails if these are
stale (see `.github/workflows/qa.yml`).

| File | What it is | Use |
|------|------------|-----|
| `knowledge-graph.json` | `{nodes, edges}` — every document plus typed cross-reference edges (each edge tagged `known`/`planned`). | Graph databases, RAG relationship expansion, dependency analysis. |
| `knowledge-graph.mmd` | The same graph as a [Mermaid](https://mermaid.js.org/) diagram, grouped by tier (solid = doc↔doc, dashed = planned). | Paste into any Mermaid renderer / GitHub Markdown for a visual map. |
| `compliance-matrix.csv` | One row per document: id, title, topic, tier, jurisdiction, document_type, legal_basis, version, status, confidence, review_due, path. | Spreadsheets, audit evidence, coverage tracking. |
| `compliance-matrix.json` | The same matrix, structured. | Programmatic consumption / dashboards. |
| `coverage.md` | Human-readable summary: documents per topic, jurisdiction, confidence and tier. | Quick status snapshot. |

## Cross-reference validation

`build_graph.py` also acts as a cross-reference validator: it exits non-zero if
a knowledge-graph edge points at an id that is neither an existing document nor
marked `(planned)`. This catches broken `related:` links and stale graph entries.
