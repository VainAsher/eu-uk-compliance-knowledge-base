# Master Index

Catalogue of all knowledge-base documents. Updated by the Repository Maintainer after every approved document.

**Last updated:** 2026-07-10

## Legend

Status: `draft` · `in-review` · `approved` · `frozen` · `superseded`
Confidence: evidence sufficiency — `High` · `Medium` · `Low`

## Documents

| ID | Title | Topic | Tier | Jurisdiction | Version | Status | Confidence | Path |
|----|-------|-------|------|--------------|---------|--------|-----------|------|
| gdpr-foundations | GDPR: Foundations & Core Principles | GDPR (EU) | 1 | EU | 1.0.0 | approved | High | `docs/01-gdpr/gdpr-foundations.md` |
| uk-gdpr-foundations | UK GDPR: Foundations & Divergence from the EU GDPR | UK GDPR | 1 | UK | 1.0.0 | approved | High | `docs/02-uk-gdpr/uk-gdpr-foundations.md` |
| eprivacy-foundations | ePrivacy: Foundations, Cookies & Electronic Communications | ePrivacy | 1 | EU, UK | 1.0.0 | approved | High | `docs/03-eprivacy/eprivacy-foundations.md` |
| privacy-engineering-foundations | Privacy Engineering: Foundations, DPbDD | Privacy Engineering | 1 | EU, UK | 0.1.0 | in-review | High | `docs/04-privacy-engineering/privacy-engineering-foundations.md` |

## Topic coverage (16 programme topics)

| Topic | Documents | Status |
|-------|-----------|--------|
| GDPR (EU) | 1 | 1 approved; sub-topics in backlog |
| UK GDPR | 1 | 1 approved; sub-topics in backlog |
| AI Act | 0 | not started |
| Data Act | 0 | not started |
| NIS2 | 0 | not started |
| DORA | 0 | not started |
| ePrivacy | 1 | 1 approved; sub-topics in backlog |
| Consumer Rights | 0 | not started |
| Digital Services | 0 | not started |
| Digital Markets | 0 | not started |
| AI Governance | 0 | not started |
| Privacy Engineering | 1 | 1 in review; sub-topics in backlog |
| Cloud Hosting | 0 | not started |
| Game Hosting | 0 | not started |
| Cybersecurity | 0 | not started |
| Compliance Operations | 0 | not started |

## Knowledge graph (cross-references)

_Populated as documents are approved. Format: `doc-a → relationship → doc-b`._

- `gdpr-foundations` → *foundation for* → `uk-gdpr-foundations` (planned)
- `gdpr-foundations` → *lex generalis to* → `eprivacy-foundations` (planned)
- `gdpr-foundations` → *implemented by* → `privacy-engineering-foundations` (planned)
- `gdpr-foundations` → *interplays with* → `ai-act-foundations` (planned)
- `uk-gdpr-foundations` → *builds on / diverges from* → `gdpr-foundations`
- `uk-gdpr-foundations` → *detailed by* → `duaa-2025-detail`, `uk-transfers`, `uk-childrens-code` (planned)
- `eprivacy-foundations` → *lex specialis to* → `gdpr-foundations`
- `eprivacy-foundations` → *transposed in UK via PECR, relates to* → `uk-gdpr-foundations`
- `eprivacy-foundations` → *detailed by* → `cookie-consent-implementation`, `pecr-detail`, `data-retention-caselaw`, `digital-omnibus` (planned)
- `privacy-engineering-foundations` → *implements* → `gdpr-foundations`, `uk-gdpr-foundations`, `eprivacy-foundations`
- `privacy-engineering-foundations` → *detailed by* → `dpia-methodology`, `pets-catalogue`, `privacy-threat-modelling`, `anonymisation-techniques` (planned)
