---
# ── YAML Front Matter ──────────────────────────────────────────────
id:                 # stable slug, e.g. gdpr-foundations
title:              # human-readable title
version: 0.1.0      # semver; bump on every approved revision
status: draft       # draft | in-review | approved | frozen | superseded
classification: public   # public | internal | restricted
jurisdiction:       # e.g. [EU], [UK], [EU, UK]
topic:              # one of the 16 programme topics
document_type: reference   # reference | guidance | checklist | policy | mapping
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
created:            # YYYY-MM-DD
updated:            # YYYY-MM-DD
review_due:         # YYYY-MM-DD (max 12 months from approval)
confidence:         # High | Medium | Low — evidence sufficiency, not tone
supersedes:         # id of prior doc, or Not Applicable
related:            # list of related doc ids
tags: []
legal_basis:        # primary instrument(s), e.g. Regulation (EU) 2016/679
sources_verified:   # YYYY-MM-DD every external link was last checked
---

<!--
AUTHORING RULES (delete this comment block in final output):
- Preserve section order exactly. Never silently omit a section — use "Not Applicable" with a one-line reason.
- Evidence over confidence: every factual claim carries an inline citation marker [n] resolving to the References block.
- Keep obligation / interpretation / best practice / editorial recommendation visibly distinct (see labels below).
- Prefer primary sources. Every external link must be live at sources_verified date.
-->

# Document Control

| Field | Value |
|-------|-------|
| Document ID | <id> |
| Version | <version> |
| Status | <status> |
| Classification | <classification> |
| Owner | Compliance Research Pipeline |
| Created | <date> |
| Last Updated | <date> |
| Review Due | <date> |
| Confidence | <High/Medium/Low> |
| Approved By | <pending human review> |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. Do not treat as legal advice.

# Executive Summary

<!-- 150–300 words. What this document covers, who it is for, and the 3–5 most important conclusions. Standalone — a reader should grasp the topic from this alone. -->

# Key Takeaways

<!-- 5–10 bullets. Each is a single, evidence-backed assertion with a citation marker. -->

# Purpose

<!-- Why this document exists and what decision or task it supports. -->

# Scope

**In scope:** …
**Out of scope:** …
**Assumptions:** …

# Definitions

<!-- Table of terms of art used in this document, with authoritative definitions and citation to source (statute/standard). -->

| Term | Definition | Source |
|------|------------|--------|

# Background

<!-- Historical and contextual framing. How did we get here; what problem does the law/standard address. -->

# Legal Framework

<!-- Overview of the governing instrument(s). State the legal obligation plainly, then interpretation separately. -->

## Relevant Articles

<!-- Table: Article → obligation summary → citation. -->

| Article | Obligation | Source |
|---------|------------|--------|

## Relevant Recitals

<!-- Recitals that inform interpretation. Recitals are not binding but aid construction — say so. -->

| Recital | Interpretive point | Source |
|---------|--------------------|--------|

## Relevant Case Law

<!-- Court judgments (CJEU, domestic courts, tribunals). Neutral citation, holding, relevance. "Not Applicable" if none. -->

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|

# Regulatory Interpretation

<!-- How regulators (EDPB, ICO, ENISA, Ofcom, CMA, etc.) interpret the framework. Label clearly as REGULATORY INTERPRETATION, distinct from statutory obligation. -->

# Technical Considerations

<!-- Engineering and architectural implications. -->

# Hosting Considerations

<!-- Cloud / infrastructure hosting implications. "Not Applicable" with reason if none. -->

# Game Hosting Considerations

<!-- Game-server / real-time / player-data specifics. "Not Applicable" with reason if none. -->

# AI Considerations

<!-- Implications for AI/ML systems, training data, automated decision-making, AI Act overlap. -->

# Operational Guidance

<!-- Actionable how-to for compliance and engineering teams. Distinguish OBLIGATION (must) from BEST PRACTICE (should) from EDITORIAL RECOMMENDATION (we suggest). -->

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|

# Implementation Roadmap

<!-- Phased plan: Phase 0 (foundations) → … . Include indicative effort and dependencies. -->

# Compliance Maturity Model

<!-- Levels 1–5 (e.g., Initial → Managed → Defined → Quantitatively Managed → Optimising) describing what each maturity level looks like for this topic. -->

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|

# Audit Questions

<!-- Questions an auditor/regulator would ask, each traceable to an obligation. -->

# Implementation Checklist

<!-- Actionable, checkbox items. -->

- [ ] …

# References

<!-- Every citation marker [n] used above resolves here. Classify each source. All links must be live at sources_verified. -->

## Primary Sources

<!-- Legislation, official consolidated texts, court judgments. -->

## Regulatory Guidance

<!-- EDPB, ICO, ENISA, NCSC, Ofcom, CMA, European Commission. -->

## Standards

<!-- ISO/IEC, NIST, OWASP, ETSI, CEN/CENELEC. -->

## Academic Sources

<!-- Peer-reviewed literature. "Not Applicable" if none. -->

# Further Reading

<!-- Non-authoritative but useful. Clearly non-binding. -->

# Related Documents

<!-- Cross-references to other repository documents by id. -->

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | <date> | Technical Writer (virtual agent) | Initial draft | pending |
