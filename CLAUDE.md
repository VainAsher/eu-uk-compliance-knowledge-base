# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a **starter kit**, not an application. It bootstraps an agentic *documentation* workflow for compliance research. There is no build system, no test suite, and no source code — the deliverables are Markdown documents produced by following the prompts here. Do not look for `package.json`, a runtime, or CI; none exist yet.

## Core operating rule

**Evidence over model confidence.** Every claim in a produced document must be backed by a citable source, not by the model's prior knowledge. Prefer verifying against primary sources and flagging uncertainty over asserting plausible-sounding facts.

## Workflow

The intended usage (from `README.md` and `prompts/`):

1. `prompts/bootstrap.md` is loaded as the initial Claude Code context. It defines the multi-agent role: planning → research → evidence gathering → drafting → QA → citation audit → link validation → repository updates → human review.
2. `prompts/work_order.md` is then supplied to scope a single task. Its rules are binding:
   - **One document per work order** — do not draft multiple documents in one pass.
   - **Read `PROJECT_HANDOVER.md` first** (this file does not yet exist in the repo; it is expected to be created/maintained per project).
   - **Update indexes** after completing a document.
   - **Stop for human approval** before finalizing — this is a hard gate, not optional.

## Document structure

All produced documents follow `templates/document_template.md`. Preserve its exact section order and the YAML frontmatter (`id`, `title`, `version`, `status`). Notable required sections include Legal Framework, AI Considerations, Hosting Considerations, Risks, Audit Questions, and a References block split into Primary Sources / Regulatory Guidance / Standards / Academic Sources. End every document with a Revision History.

## Quality automation (aspirational)

`scripts/README.md` lists the QA toolchain the workflow expects but which is **not yet implemented**: markdownlint, yamllint, lychee and markdown-link-check (link validation), vale (style), a custom citation validator, a glossary consistency checker, and scheduled GitHub Actions. When adding automation, these are the intended tools. Citation and link validation are the highest-value checks given the evidence-over-confidence rule.
