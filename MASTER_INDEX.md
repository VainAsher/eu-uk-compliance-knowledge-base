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
| privacy-engineering-foundations | Privacy Engineering: Foundations, DPbDD | Privacy Engineering | 1 | EU, UK | 1.0.0 | approved | High | `docs/04-privacy-engineering/privacy-engineering-foundations.md` |
| ai-act-foundations | EU AI Act: Foundations, Risk Tiers & Timeline | AI Act | 2 | EU | 1.0.0 | approved | High | `docs/05-ai-act/ai-act-foundations.md` |
| ai-governance-foundations | AI Governance: Foundations, ISO/IEC 42001 & Operational Assurance | AI Governance | 2 | EU, UK | 1.0.0 | approved | High | `docs/06-ai-governance/ai-governance-foundations.md` |
| data-act-foundations | EU Data Act: Foundations, Data Access & Sharing | Data Act | 2 | EU | 1.0.0 | approved | High | `docs/07-data-act/data-act-foundations.md` |
| dsa-foundations | EU Digital Services Act: Foundations & Platform Obligations | Digital Services | 2 | EU | 1.0.0 | approved | High | `docs/08-digital-services/dsa-foundations.md` |
| dma-foundations | EU Digital Markets Act: Foundations & Gatekeeper Obligations | Digital Markets | 2 | EU | 1.0.0 | approved | High | `docs/09-digital-markets/dma-foundations.md` |
| nis2-foundations | NIS2 Directive: Foundations, Scope & Cybersecurity Obligations | NIS2 | 3 | EU | 1.0.0 | approved | High | `docs/10-nis2/nis2-foundations.md` |
| dora-foundations | DORA: Foundations & Digital Operational Resilience for Finance | DORA | 3 | EU | 1.0.0 | approved | High | `docs/11-dora/dora-foundations.md` |
| cybersecurity-foundations | Cybersecurity: Foundations, Frameworks & Controls | Cybersecurity | 3 | EU, UK | 1.0.0 | approved | High | `docs/12-cybersecurity/cybersecurity-foundations.md` |

## Topic coverage (16 programme topics)

| Topic | Documents | Status |
|-------|-----------|--------|
| GDPR (EU) | 1 | 1 approved; sub-topics in backlog |
| UK GDPR | 1 | 1 approved; sub-topics in backlog |
| AI Act | 1 | 1 approved; sub-topics in backlog |
| Data Act | 1 | 1 approved; sub-topics in backlog |
| NIS2 | 1 | 1 approved; sub-topics in backlog |
| DORA | 1 | 1 approved; sub-topics in backlog |
| ePrivacy | 1 | 1 approved; sub-topics in backlog |
| Consumer Rights | 0 | not started |
| Digital Services | 1 | 1 approved; sub-topics in backlog |
| Digital Markets | 1 | 1 approved; sub-topics in backlog |
| AI Governance | 1 | 1 approved; sub-topics in backlog |
| Privacy Engineering | 1 | 1 approved; sub-topics in backlog |
| Cloud Hosting | 0 | not started |
| Game Hosting | 0 | not started |
| Cybersecurity | 1 | 1 approved; sub-topics in backlog |
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
- `ai-act-foundations` → *operates alongside* → `gdpr-foundations`
- `ai-act-foundations` → *operationalised by* → `ai-governance-foundations`
- `ai-act-foundations` → *detailed by* → `ai-act-high-risk`, `ai-act-gpai`, `ai-act-prohibited-practices`, `digital-omnibus` (planned)
- `ai-governance-foundations` → *operationalises* → `ai-act-foundations`; *integrates with* → `gdpr-foundations`; *builds on* → `privacy-engineering-foundations`
- `data-act-foundations` → *complements* → `gdpr-foundations` (GDPR prevails on personal-data conflict); *adjacent to* → `ai-act-foundations`
- `dsa-foundations` → *sibling of* → `dma-foundations` (Digital Services package); *overlaps* → `ai-act-foundations`, `gdpr-foundations`
- `dma-foundations` → *complements* → `dsa-foundations`; *relates to* → `gdpr-foundations` (consent, Art. 5(2) DMA)
- `nis2-foundations` → *supersedes* → NIS Directive 2016/1148; *lex specialis defers to* → `dora-foundations` (finance); *parallel with* → `gdpr-foundations` (dual breach reporting)
- `dora-foundations` → *lex specialis to* → `nis2-foundations` (financial entities); *parallel with* → `gdpr-foundations`
- `cybersecurity-foundations` → *implements* → `nis2-foundations`, `dora-foundations`, `gdpr-foundations` (Art. 32); *complements* → `privacy-engineering-foundations`
- All three → *relate to* → Cyber Resilience Act (Reg (EU) 2024/2847) (planned `cyber-resilience-act`)
