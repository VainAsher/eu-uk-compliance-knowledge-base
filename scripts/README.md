# QA toolchain

Automated quality gates for the knowledge base. The custom validators encode
the checks the pipeline previously did by hand (citation integrity, template
conformance, link liveness), so every batch self-checks.

## Implemented

| Tool | File | What it checks | Network |
|------|------|----------------|---------|
| **Document validator** | `scripts/validate.py` | YAML front matter (required fields, valid `status`/`confidence`/semver/dates); the 23 mandatory template sections present and in order; citation integrity (`[n]` markers contiguous, every marker resolves to a reference, every reference cited). | No |
| **Link checker** | `scripts/check_links.py` | Every `http(s)` URL in `docs/` + `SOURCE_REGISTRY.md`/`GLOSSARY.md`/`MASTER_INDEX.md` returns a live status via `curl` (GET, follows redirects). Known bot-blocking hosts (e.g. `consilium.europa.eu`) are allowlisted as WARN. | Yes |
| **Markdown lint** | `.markdownlint.jsonc` (via `markdownlint-cli2`) | Markdown hygiene, tuned to the house style (multiple H1 sections allowed; bare URLs and `[n]` citation markers allowed; `*asterisk*` emphasis). | No |
| **Graph / matrix export + cross-ref validator** | `scripts/build_graph.py` | Emits `exports/` (knowledge graph JSON + Mermaid, compliance matrix CSV/JSON, coverage report) from the catalogue + front matter. Exits non-zero on a knowledge-graph edge to a non-existent, non-`(planned)` id. | No |
| **CI** | `.github/workflows/qa.yml` | Runs the document validator + graph/cross-ref check + markdownlint on every push/PR (and fails if `exports/` is stale); runs the link checker weekly (cron) and on manual dispatch. | — |

### Running locally

```bash
pip install pyyaml
python scripts/validate.py            # offline: front matter + structure + citations
python scripts/build_graph.py         # regenerate exports/ + validate cross-references
python scripts/check_links.py         # network: all external links
npx markdownlint-cli2 "docs/**/*.md" "*.md"        # lint
npx markdownlint-cli2 --fix "docs/**/*.md" "*.md"  # auto-fix mechanical issues
```

`validate.py` and `check_links.py` exit non-zero on failure, so they gate CI.

## Design notes / gotchas encoded here

- **`[n]` are citation markers, not Markdown reference links** — `MD052` is
  disabled; `validate.py` audits them properly instead.
- **HEAD is unreliable** for link checking — several official servers
  (e.g. `nvlpubs.nist.gov`) answer `404` to HEAD but `200` to GET, so the
  checker uses GET.
- **Balanced parens in bare URLs** (e.g. Wikipedia `..._(European_Union)`) are
  preserved; only unbalanced trailing `)` (prose/Markdown) is trimmed.
- **Bot-block allowlist**: hosts in `check_links.py:BOT_BLOCK_HOSTS` are
  reported as WARN, not FAIL. Verify those in a browser.

## Not yet implemented (recommended next)

- **Glossary consistency checker** — assert every `SOURCE_REGISTRY` key referenced
  in a `GLOSSARY` entry exists, and flag glossary terms redefined inconsistently.
- **vale** — prose style/consistency (UK spelling, defined-term casing).
- **yamllint** — stricter YAML lint for front matter.
- **lychee** — a faster Rust link checker (alternative to `check_links.py`) if the
  URL set grows large.
