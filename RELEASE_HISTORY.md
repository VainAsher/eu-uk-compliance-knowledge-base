# Release History

Frozen snapshots of the knowledge base. A release is cut when a batch of documents reaches `frozen` status. Detailed changes are in `CHANGELOG.md`.

| Release | Date | Highlights | Docs frozen |
|---------|------|-----------|-------------|
| 0.17.0 | 2026-07-12 | **Backlog loop Cluster C** (autonomous): anonymisation & re-identification risk, data-retention CJEU case law (10 judgments), DSA recommender/advertising transparency, DMA interoperability (Arts. 6(7)/7), NIS2 transposition tracker, AI model risk management & evaluation. Registry gains 41 sources (incl. the full data-retention case line); glossary +33 terms. **16/16 topics now have ≥2 depth docs.** | 50 |
| 0.16.0 | 2026-07-11 | **Backlog loop Cluster B** (autonomous): GDPR RoPA (Art. 30), UK PECR detail, privacy threat modelling (LINDDUN), DORA CTPP oversight framework, CRA conformity assessment, game-hosting loot boxes. **Corrective patch:** `cyber-resilience-act` → v1.0.1 (CRA Chapter III/IV + Annex VI/VIII structure re-verified against EUR-Lex and corrected). Registry gains `linddun`. | 44 |
| 0.15.0 | 2026-07-11 | **Backlog loop Cluster A** (autonomous): Data Act switching, DSA VLOP obligations, DMCCA subscriptions, ISO 42001 AIMS, compliance-audit methodology, cloud shared-responsibility. 15/16 topics now have depth docs. | 38 |
| 0.14.0 | 2026-07-11 | Third depth sub-topic cluster: AI Act prohibited practices, GDPR DSAR, NIS2 incident reporting, DMA obligations, UK Children's Code, PETs catalogue. Registry gains 9 CJEU judgments + 11 academic works. | 32 |
| 0.13.0 | 2026-07-11 | **Publication + RAG (Stage 10):** MkDocs Material GitHub Pages site (`build_site.py` + `pages.yml`) and a section-level RAG export (`build_rag.py` → `exports/rag/`, 598 chunks). | 26 |
| 0.12.0 | 2026-07-11 | Knowledge-graph & compliance-mapping export (`build_graph.py` + `exports/`): graph JSON/Mermaid, compliance matrix CSV/JSON, coverage report; cross-reference gate in CI. | 26 |
| 0.11.0 | 2026-07-11 | Second depth sub-topic cluster: DPIA methodology, AI Act GPAI, Digital Omnibus, UK transfers, cookie consent, DORA TLPT. Workers self-ran QA validators; full repo 26/26 clean. | 26 |
| 0.10.1 | 2026-07-11 | **QA automation:** document validator + link checker + markdownlint + CI. Fixed 2 citation defects the validator caught (uk-gdpr, dora → v1.0.1); repo-wide lint normalization. | 20 |
| 0.10.0 | 2026-07-11 | First depth sub-topic cluster: GDPR transfers, DUAA detail, AI Act high-risk, CRA. **Corrective revision:** `ai-act-foundations` → v1.1.0 (AI Omnibus adopted 29 Jun 2026). | 20 (incl. 1 revised) |
| 0.9.0 | 2026-07-11 | Tier 4 cluster batch frozen: Consumer Rights, Cloud Hosting, Game Hosting, Compliance Operations. **🏁 ALL 16 foundation topics complete.** | 16 (cumulative) |
| 0.8.0 | 2026-07-11 | Tier 3 cluster batch frozen: NIS2, DORA, Cybersecurity (v1.0.0 each). **Tier 3 complete; 12/16 topics.** | 12 (cumulative) |
| 0.7.0 | 2026-07-11 | Tier 2 cluster batch frozen: AI Governance, Data Act, DSA, DMA (v1.0.0 each). **Tier 2 complete; 9/16 topics.** First parallel-cluster batch. | 9 (cumulative) |
| 0.6.0 | 2026-07-11 | AI Act Foundations frozen (v1.0.0) — first Tier 2 doc. Parallel cluster model introduced. | 5 (cumulative) |
| 0.5.0 | 2026-07-11 | Privacy Engineering Foundations frozen (v1.0.0). **Tier 1 (data-protection core) complete: 4/4.** | 4 (cumulative) |
| 0.4.0 | 2026-07-11 | ePrivacy Foundations frozen (v1.0.0): cookie rule, direct marketing, PECR, Planet49, 2025 reform status. Tier 1 now 3/4. | 3 (cumulative) |
| 0.3.0 | 2026-07-10 | UK GDPR Foundations frozen (v1.0.0): DUAA 2025 reforms + EU adequacy to 2031. Tier 1 now 2/4. | 2 (cumulative) |
| 0.2.0 | 2026-07-10 | First knowledge-base document frozen: GDPR Foundations (v1.0.0). Added shared GLOSSARY; sub-topic scoping policy. | 1 |
| 0.1.0 | 2026-07-10 | Repository bootstrap: git, full template, governance scaffolding. | 0 |

## Notes

- **0.2.0** freezes `gdpr-foundations` at v1.0.0 (approved at the human review gate). Frozen documents are locked at their stated version; further changes cut a new document version and a new release.
- **0.1.0** establishes the operating model and control-file set.
