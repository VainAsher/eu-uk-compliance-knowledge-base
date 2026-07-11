---
id: dsa-foundations
title: "EU Digital Services Act: Foundations & Platform Obligations"
version: 0.1.0
status: in-review
classification: public
jurisdiction: [EU]
topic: Digital Services
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [dma-foundations, ai-act-foundations, gdpr-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [dsa, digital-services-act, vlop, vlose, notice-and-action, intermediary-liability, content-moderation, platform-regulation]
legal_basis: Regulation (EU) 2022/2065
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dsa-foundations |
| Version | 0.1.0 |
| Status | in-review |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | *pending human review* |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. Enforcement under the DSA is **active and evolving**: the VLOP/VLOSE designation list changes as platforms cross or fall below the user threshold, and Commission proceedings are ongoing. Confirm the current designation list and the status of any enforcement action before relying on it.

# Executive Summary

The **EU Digital Services Act (Regulation (EU) 2022/2065**, "DSA") is the EU's horizontal rulebook for **intermediary services** — the ISPs, hosting providers, marketplaces, social networks and search engines that carry, store or index third-party content. Its purpose is a **safe, predictable and trustworthy online environment** in which fundamental rights are protected and illegal content and goods are handled through accountable, transparent processes, under **fully harmonised** EU-wide rules [1][3]. It **entered into force on 16 November 2022** and became **fully applicable to all in-scope entities on 17 February 2024** (Art. 93), with the heaviest tier already binding on designated platforms from mid-2023 [1][3].

The DSA imposes **cumulative, tiered obligations**: rules that apply to **all intermediary services** (points of contact, transparent terms, transparency reporting) are supplemented by additional duties for **hosting services** (notice-and-action, statements of reasons), then for **online platforms** (complaint handling, trusted flaggers, ad and recommender-system transparency, dark-pattern and minor-protection rules), and finally by the strictest regime for **Very Large Online Platforms (VLOPs)** and **Very Large Online Search Engines (VLOSEs)** — those with **45 million+ average monthly EU users** — including annual **systemic-risk assessments**, risk mitigation, **independent audits**, a researcher-data-access duty and a compliance function [1][3][4].

Enforcement is split: national **Digital Services Coordinators (DSCs)** supervise most providers under a **country-of-origin** principle, while the **European Commission** has exclusive powers over VLOP/VLOSE systemic obligations. Penalties reach **up to 6% of worldwide annual turnover** [1][3]. This is not theoretical: on **5 December 2025 the Commission issued its first DSA non-compliance fine — €120 million against X** — and in **October 2025 it issued preliminary findings against TikTok and Meta** for transparency and user-protection breaches [6][7].

# Key Takeaways

- The **DSA (Regulation (EU) 2022/2065)** entered into force **16 November 2022** and became **fully applicable on 17 February 2024** (Art. 93) [1][3]. *(Legal obligation — in force.)*
- Obligations are **tiered and cumulative** by service type: intermediary → hosting → online platform → VLOP/VLOSE; each tier inherits the ones below it [1][3]. *(Legal obligation.)*
- The DSA **preserves the conditional liability exemptions** (mere conduit, caching, hosting) inherited from the e-Commerce Directive and **bans general monitoring obligations** (Arts. 4–8) [1]. *(Legal obligation.)*
- **Hosting providers** must operate **notice-and-action** mechanisms (Art. 16) and give **statements of reasons** for content restrictions (Art. 17) [1]. *(Legal obligation.)*
- **Online platforms** must provide internal complaint handling, out-of-court dispute settlement, **trusted-flagger** priority (Art. 22), **advertising transparency** (Art. 26), **recommender-system transparency** (Art. 27), and must not use **dark patterns** (Art. 25) [1]. *(Legal obligation.)*
- **VLOPs/VLOSEs** (45m+ EU users, Art. 33) face **systemic-risk assessment** (Art. 34), **risk mitigation** (Art. 35), **independent annual audits** (Art. 37) and **vetted-researcher data access** (Art. 40) [1][3]. *(Legal obligation.)*
- Enforcement follows a **country-of-origin / Digital Services Coordinator** model, with the **Commission** exclusively supervising VLOP/VLOSE systemic duties; **fines reach up to 6% of worldwide annual turnover** (Arts. 52, 74) [1][3]. *(Legal obligation.)*
- Enforcement is **live-verified**: the Commission's list (last updated **10 July 2026**) shows **20+ designated VLOPs and two VLOSEs**; the **first fine (€120m against X)** issued **5 Dec 2025**, with **preliminary findings against TikTok and Meta** in October 2025 [4][6][7]. *(Confirmed, not asserted.)*

# Purpose

This document is the Tier 2 entry point for the DSA. It supports legal research (mapping the intermediary tiers and their obligations), compliance planning (identifying which tier a service occupies and the resulting duties), and product/engineering triage (notice-and-action design, transparency features, recommender and advertising disclosures). It sits alongside `dma-foundations` (the DSA's market-fairness sibling) and interacts with `gdpr-foundations` and `ai-act-foundations`.

# Scope

**In scope:** The DSA's purpose and scope; the definitions of the intermediary tiers; the liability regime and no-general-monitoring rule; the cumulative due-diligence obligations for intermediary services, hosting services, online platforms and VLOPs/VLOSEs; notice-and-action and illegal-content handling; advertising and recommender-system transparency at a foundational level; VLOP systemic-risk assessment and audits at a foundational level; the country-of-origin / Digital Services Coordinator enforcement structure; and penalties. Current VLOP/VLOSE designations and notable enforcement are **live-verified**.

**Out of scope (spun off to the research backlog):** The full VLOP **systemic-risk-assessment and mitigation** methodology (Arts. 34–35) → `dsa-vlop-risk-management`; **recommender-system transparency** and the profiling opt-out in depth (Arts. 27, 38) → `dsa-recommender-transparency`; the **trusted-flagger** regime and **out-of-court dispute settlement** mechanics (Arts. 21–22) → `dsa-trusted-flaggers`; **marketplace / trader-traceability (KYBC)** duties (Arts. 30–32) → `dsa-marketplaces`; the **DSA/DMA boundary** in depth → `dma-foundations`; the **Code of Practice on Disinformation** and crisis protocols (Arts. 45–48) → `dsa-codes-of-conduct`.

**Assumptions:** The reader understands the EU regulation/directive distinction. Where an intermediary processes personal data, the **GDPR applies in parallel** (see `gdpr-foundations`).

# Definitions

*Shared terms are in `GLOSSARY.md`. DSA-specific terms are defined here; deeper terms (trusted flagger, systemic risk) are deferred to the backlog documents above.*

| Term | Definition | Source |
|------|------------|--------|
| Intermediary service | A "mere conduit", "caching" or "hosting" service as defined in Art. 3(g). The three tiers of intermediary. | [1] |
| Hosting service | An intermediary service that stores information provided by, and at the request of, a recipient (Art. 3(g)(iii)). | [1] |
| Online platform | A hosting service that, at a recipient's request, **stores and disseminates information to the public**, unless that is a minor/ancillary feature of another service (Art. 3(i)). | [1] |
| VLOP / VLOSE | An online platform / online search engine designated by the Commission for having **≥ 45 million average monthly active EU recipients** (Art. 33). | [1][3] |
| Illegal content | Any information that, in itself or by reference to an activity, is not in compliance with EU or Member State law (Art. 3(h)). | [1] |
| Notice-and-action | The Art. 16 mechanism by which any person can notify a hosting provider of allegedly illegal content, triggering a duty to act in a timely, diligent, non-arbitrary manner. | [1] |
| Digital Services Coordinator (DSC) | The independent national authority each Member State designates to supervise DSA compliance and coordinate at EU level (Art. 49). | [1] |

# Background

The DSA modernises the **e-Commerce Directive (2000/31/EC)**, whose intermediary-liability "safe harbours" had governed online services since 2000 but predated social media, algorithmic feeds and large marketplaces. Divergent national content laws had fragmented the single market and left illegal content, counterfeit goods and systemic online harms inconsistently addressed. The EU's response, part of the **Digital Services Act package** alongside the Digital Market Act (DMA), keeps the liability exemptions but layers on **binding due-diligence obligations** scaled to a service's type and reach, under **fully harmonised** rules directly applicable across all Member States [1][3]. The DSA entered into force on **16 November 2022**; designation-related provisions applied from that date, the first VLOPs/VLOSEs were designated on **25 April 2023** (with their obligations following ~4 months later), and the regime became **fully applicable to all intermediaries on 17 February 2024** [1][3][5].

# Legal Framework

The DSA regulates providers of **intermediary services** offered to recipients established or located in the EU, **regardless of the provider's place of establishment** (Art. 2). Its architecture is **cumulative** — each tier adds to, rather than replaces, the tier beneath it [1]:

- **Chapter I** — subject matter, scope, definitions (Arts. 1–3).
- **Chapter II (Arts. 4–10)** — **liability** of intermediary providers: **mere conduit** (Art. 4), **caching** (Art. 5), **hosting** (Art. 6), the voluntary-investigation "Good Samaritan" clause (Art. 7), **no general monitoring obligation** (Art. 8), and **orders** to act against illegal content / to provide information (Arts. 9–10).
- **Chapter III** — **due-diligence** obligations, structured as nested sections:
  - **Section 1 — all intermediary services (Arts. 11–15):** points of contact (11–12), legal representatives (13), **terms and conditions** transparency (14), **transparency reporting** (15).
  - **Section 2 — hosting services (Arts. 16–18):** **notice-and-action** (16), **statement of reasons** (17), notification of suspected criminal offences (18).
  - **Section 3 — online platforms (Arts. 19–28):** micro/small exemption (19), internal complaint handling (20), out-of-court dispute settlement (21), **trusted flaggers** (22), measures against misuse (23), platform transparency reporting (24), **prohibition of dark patterns** (25), **advertising transparency** (26), **recommender-system transparency** (27), **protection of minors** (28).
  - **Section 4 — marketplaces (Arts. 29–32):** trader traceability / **know-your-business-customer** (30), compliance by design (31), right to information (32).
  - **Section 5 — VLOPs / VLOSEs (Arts. 33–43):** designation (33), **systemic-risk assessment** (34), **risk mitigation** (35), crisis response (36), **independent audit** (37), non-profiling recommender option (38), **enhanced ad repository** (39), **vetted-researcher data access** (40), compliance function (41), enhanced transparency reporting (42), supervisory fee (43).
- **Chapter IV (Arts. 49–88)** — **enforcement**: Digital Services Coordinators and the **country-of-origin** principle (Arts. 49, 56), penalties (52), enhanced Commission supervision of VLOPs/VLOSEs, and **Commission fines** up to 6% of worldwide turnover (74) and periodic penalty payments (76).

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 3 | Definitions (intermediary/hosting service, online platform, illegal content, recipient). | [1] |
| Arts. 4–6 | Conditional liability exemptions: mere conduit, caching, hosting (safe harbours). | [1] |
| Art. 8 | No general obligation to monitor or actively seek facts indicating illegal activity. | [1] |
| Arts. 9–10 | Compliance with orders to act against illegal content and to provide information. | [1] |
| Arts. 11–15 | Baseline duties for all intermediaries: contact points, legal rep, T&C transparency, transparency reports. | [1] |
| Art. 16 | Notice-and-action mechanisms for hosting services. | [1] |
| Art. 17 | Statement of reasons for content restrictions. | [1] |
| Arts. 20–22 | Online-platform complaint handling, out-of-court dispute settlement, trusted flaggers. | [1] |
| Art. 25 | Prohibition of dark patterns in online-interface design. | [1] |
| Art. 26 | Advertising transparency on online platforms. | [1] |
| Art. 27 | Recommender-system transparency (main parameters, options). | [1] |
| Art. 28 | Protection of minors (no profiling-based ads to minors). | [1] |
| Arts. 30–32 | Marketplace trader traceability (KYBC) and consumer information. | [1] |
| Art. 33 | VLOP/VLOSE designation threshold (≥ 45m average monthly EU users). | [1] |
| Arts. 34–35 | VLOP/VLOSE systemic-risk assessment and mitigation. | [1] |
| Art. 37 | Independent annual audit of VLOP/VLOSE compliance. | [1] |
| Art. 40 | Data access for vetted researchers and authorities. | [1] |
| Arts. 49, 56 | Digital Services Coordinators; country-of-origin jurisdiction; Commission powers over VLOPs. | [1] |
| Art. 52 | Penalties (Member State level): max 6% of annual worldwide turnover. | [1] |
| Art. 74 | Commission fines on VLOPs/VLOSEs: up to 6% of total worldwide annual turnover. | [1] |
| Art. 93 | Entry into force (16 Nov 2022) and full application (17 Feb 2024). | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited here from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 3 | The DSA's objective: a safe, predictable and trusted online environment protecting fundamental rights. | [1] |
| Recital 9 (area) | Full harmonisation — uniform, directly applicable rules to prevent single-market fragmentation. | [1] |
| Recital 12 (area) | The broad concept of "illegal content" (whatever is unlawful under EU or national law). | [1] |
| Recital 22 (area) | Conditions for the hosting exemption — expeditious action on obtaining actual knowledge. | [1] |

## Relevant Case Law

**Not Applicable at the foundational level.** The DSA is recent and there is no settled CJEU case law interpreting its substantive due-diligence obligations. Interpretive weight currently rests on the Regulation's text, Commission decisions and guidance. Challenges to VLOP/VLOSE **designation** have been brought before the General Court and enforcement decisions (e.g., the X fine) may be appealed; these are **emerging** and are tracked in the enforcement backlog rather than asserted here. [1][3]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (not statutory text).**

- The **European Commission** presents the DSA as delivering *"what is illegal offline should be illegal online,"* built on notice-and-action, transparency and accountability, under fully harmonised rules [3]. *(Regulatory interpretation.)*
- **Designation is dynamic:** the Commission designates VLOPs/VLOSEs as they cross the 45m threshold and can end designation when they fall below it. Its published list — **last updated 10 July 2026** — shows **20+ VLOPs** (including Amazon Store, Apple App Store, Booking.com, Facebook, Instagram, WhatsApp, Google Play/Maps/Shopping, YouTube, LinkedIn, Pinterest, Snapchat, TikTok, X, AliExpress, Temu, Shein, Wikipedia and several adult-content sites) and **two VLOSEs** (Google Search, Bing) [4]. *(Regulatory interpretation — verify the live list.)*
- **Notice-and-action and researcher access are enforcement priorities:** the Commission's **preliminary findings against TikTok and Meta (October 2025)** centred on inadequate **Art. 40 researcher data access**, and (for Meta) deficient illegal-content **notice mechanisms** and appeal processes said to involve dark patterns [7]. *(Regulatory interpretation — preliminary, not final.)*
- **First fine sets the tone:** on **5 December 2025** the Commission fined **X €120 million** — its first DSA non-compliance decision — for the deceptive design of the paid "blue checkmark", a non-compliant advertising repository, and barriers to researcher data access [6]. *(Legal fact — confirmed.)*
- **Country-of-origin with central VLOP oversight:** most providers answer to the **DSC of their Member State of establishment**, but the Commission holds **exclusive** enforcement over the VLOP/VLOSE **Section 5** systemic obligations [1][3]. *(Regulatory interpretation.)*

# Technical Considerations

- **Tier triage first** — determine whether a service is a mere-conduit/caching/hosting intermediary, an online platform (stores **and disseminates to the public**), a marketplace, and whether it approaches the 45m VLOP threshold; the tier drives every downstream obligation [1][3]. *(Legal obligation.)*
- **Notice-and-action pipeline** — hosting services must expose an accessible, electronic **Art. 16** notice mechanism, generate machine-readable **Art. 17 statements of reasons** for every restriction, and (for platforms) submit these to the **DSA Transparency Database** [1]. *(Legal obligation.)*
- **Advertising and recommender transparency** — platforms must label ads with who paid and why the user is targeted (Art. 26), disclose the **main parameters** of recommender systems and offer options (Art. 27); VLOPs must maintain a searchable **ad repository** (Art. 39) and a **non-profiling** recommender option (Art. 38) [1]. *(Legal obligation.)*
- **Dark-pattern avoidance** — online-interface design must not deceive or manipulate recipients (Art. 25); this constrains consent flows, default settings and friction in complaint/notice paths [1]. *(Legal obligation.)*
- **Researcher data access** — VLOPs/VLOSEs must build vetted-researcher access interfaces (Art. 40); the TikTok/Meta/X actions show this is scrutinised closely [1][6][7]. *(Legal obligation.)*

# Hosting Considerations

- **Safe harbour is conditional** — a hosting provider avoids liability only if it lacks actual knowledge of illegal content and acts **expeditiously** to remove/disable it upon obtaining knowledge (Art. 6); notice-and-action is the mechanism by which knowledge is acquired (Art. 16) [1]. *(Legal obligation — assess role.)*
- **No general monitoring** — providers cannot be required to generally monitor or actively seek facts indicating illegality (Art. 8), but this does not bar specific orders (Arts. 9–10) [1]. *(Legal obligation.)*
- **Logging and statements of reasons** — hosting operators must generate and retain **statements of reasons** for restrictions and support transparency reporting; retention must respect GDPR limits (see `gdpr-foundations`) [1][2]. *(Legal obligation.)*
- **Establishment and legal representative** — non-EU intermediaries serving EU users must designate a **legal representative** (Art. 13) and are supervised by the DSC of that representative's Member State [1]. *(Legal obligation.)*

# Game Hosting Considerations

- **UGC and chat can make a game an "online platform"** — if a game **stores and disseminates user content to the public** (public forums, mod hubs, shared creations, unmoderated public chat), the operator may be an online platform owing notice-and-action, complaint-handling and transparency duties; purely private/session chat is more likely a minor/ancillary feature outside Art. 3(i) [1]. *(Legal obligation — assess feature by feature.)*
- **Minor protection is acute** — games with large under-18 audiences engage **Art. 28** (no profiling-based advertising to minors; high privacy/safety by default) and heighten dark-pattern scrutiny of monetisation flows (Art. 25) [1]. *(Legal obligation.)*
- **Marketplaces for items/skins** — player-to-player trading or third-party trader storefronts can trigger **Section 4** trader-traceability (KYBC) duties (Arts. 30–32) [1]. *(Legal obligation — assess.)*
- **Scale awareness** — a very large game platform could approach the **45m EU-user** VLOP threshold, bringing systemic-risk assessment into scope; monitor active-user metrics [1][4]. *(Best practice.)*

# AI Considerations

- **Recommender and moderation AI** — algorithmic feeds and automated content moderation are squarely within **Arts. 25–27** (dark patterns, recommender transparency) and, for VLOPs, are a named **systemic-risk** vector under Art. 34; automated moderation decisions still require Art. 17 statements of reasons [1]. *(Legal obligation.)*
- **Overlap with the AI Act** — where an intermediary deploys AI (e.g., recommender or generative features), the **AI Act (Reg (EU) 2024/1689)** may apply in parallel, including Art. 50 transparency for AI-generated/synthetic content; see `ai-act-foundations` [1]. *(Cross-reference.)*
- **GDPR overlap** — recommender profiling and ad targeting process personal data, so the **GDPR applies in full** (lawful basis, DPbDD, Art. 22 automated-decision safeguards); Art. 26/28 DSA rules on profiling-based ads reinforce this [1][2]. *(Legal obligation.)*

# Operational Guidance

Labels: **OBLIGATION** / **BEST PRACTICE** / **EDITORIAL RECOMMENDATION**.

1. **Classify each service by tier** (intermediary / hosting / online platform / marketplace / VLOP-candidate) and by role. *(OBLIGATION — foundational.)* [1][3]
2. **Confirm safe-harbour posture** — ensure conduct fits the Art. 4–6 exemptions and that no general-monitoring is imposed. *(OBLIGATION.)* [1]
3. **Build notice-and-action (Art. 16) and statements of reasons (Art. 17)**, including submission to the DSA Transparency Database where required. *(OBLIGATION.)* [1]
4. **Publish transparent terms and transparency reports** (Arts. 14–15; 24 for platforms). *(OBLIGATION.)* [1]
5. **For online platforms:** stand up complaint handling, out-of-court dispute settlement, trusted-flagger priority, ad transparency, recommender transparency, dark-pattern review and minor protection (Arts. 20–28). *(OBLIGATION.)* [1]
6. **For marketplaces:** implement trader traceability / KYBC (Arts. 30–32). *(OBLIGATION where applicable.)* [1]
7. **If approaching 45m EU users:** prepare systemic-risk assessment, mitigation, independent audit, ad repository and researcher-access interfaces (Arts. 33–43). *(OBLIGATION once designated; BEST PRACTICE to pre-build.)* [1][4]
8. **Map your DSC / establishment** and prepare for Commission oversight if a VLOP. *(OBLIGATION.)* [1]
9. **Run DSA and GDPR compliance together** for ad targeting, profiling and moderation data. *(OBLIGATION + BEST PRACTICE.)* [1][2]
10. **Track live enforcement** (X, TikTok, Meta) for the Commission's evolving expectations on researcher access, ad repositories and notice design. *(EDITORIAL RECOMMENDATION.)* [6][7]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | Misclassifying a public UGC service as outside "online platform" | Medium | High | Art. 3(i) [1] | Documented feature-by-feature tier assessment | Low |
| R2 | Losing the hosting safe harbour by not acting expeditiously | Medium | High | Art. 6 [1] | Robust notice-and-action; SLA on takedown | Low |
| R3 | Non-compliant / missing notice-and-action or statements of reasons | Medium | High | Arts. 16–17 [1] | Build Art. 16/17 flows; DSA DB submission | Low |
| R4 | Dark patterns in consent/notice/monetisation UI | Medium | Medium | Art. 25 [1] | UX review against Art. 25; remove manipulative design | Low |
| R5 | Inadequate ad or recommender transparency | Medium | High | Arts. 26–27, 39 [1][6] | Ad labelling/repository; recommender disclosures | Medium |
| R6 | Inadequate vetted-researcher data access (VLOP) | Medium | Very High | Art. 40 [1][6][7] | Compliant researcher-access interface; legal review | Medium |
| R7 | Missing VLOP systemic-risk assessment/audit after designation | Low | Very High | Arts. 34–37; Art. 74 (6%) [1] | Pre-build risk/audit programme; compliance function | Medium |
| R8 | Marketplace without trader traceability (KYBC) | Medium | High | Arts. 30–32 [1] | Onboarding KYBC; trader information duties | Low |

# Implementation Roadmap

- **Phase 0 — Classification:** Map every service to its tier and role; identify VLOP proximity. *Effort:* Medium.
- **Phase 1 — Baseline intermediary duties:** Contact points, legal representative, transparent T&Cs, transparency reporting (Arts. 11–15). *Effort:* Medium.
- **Phase 2 — Hosting duties:** Notice-and-action (16), statements of reasons (17), suspected-offence notification (18), DSA Transparency Database. *Effort:* Medium.
- **Phase 3 — Online-platform duties:** Complaint handling, dispute settlement, trusted flaggers, ad/recommender transparency, dark-pattern remediation, minor protection (Arts. 20–28). *Effort:* High.
- **Phase 4 — Marketplace duties (if applicable):** Trader traceability/KYBC and consumer information (Arts. 30–32). *Effort:* Medium.
- **Phase 5 — VLOP/VLOSE readiness (if in scope):** Systemic-risk assessment, mitigation, audit, ad repository, researcher access, compliance function (Arts. 33–43). *Effort:* Very High.
- **Phase 6 — Enforcement monitoring:** Track DSC guidance and Commission decisions; adjust. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Services not classified; unaware of tier obligations. | No tier map; ad-hoc takedowns. |
| 2 | Managed | Tier classification done; basic notice-and-action exists. | Contact points; Art. 16 flow live. |
| 3 | Defined | Statements of reasons, transparency reports, complaint handling, ad/recommender transparency in place. | Arts. 15–17, 24–27 operational; DSA DB submission. |
| 4 | Quantitatively Managed | Metrics on moderation, appeals and transparency; dark-pattern and minor-protection controls tested. | KPIs on notices/appeals; UX audits. |
| 5 | Optimising | Integrated DSA + GDPR + (where relevant) VLOP systemic-risk governance with independent audit. | Risk assessments; Art. 37 audit; compliance function. |

# Audit Questions

1. How is each service classified across the intermediary/hosting/platform/marketplace/VLOP tiers, and who owns that assessment? *(Art. 3 [1].)*
2. Does the safe-harbour posture hold — is content acted on expeditiously on obtaining knowledge? *(Arts. 4–6 [1].)*
3. How do users submit notices (Art. 16), and are statements of reasons (Art. 17) generated and logged? *([1].)*
4. What transparency reports are published, and are they submitted to the DSA Transparency Database? *(Arts. 15, 24 [1].)*
5. For platforms: are complaint handling, out-of-court dispute settlement, trusted-flagger priority, ad and recommender transparency, and minor protection in place? *(Arts. 20–28 [1].)*
6. Have online interfaces been reviewed for dark patterns? *(Art. 25 [1].)*
7. For marketplaces: is trader traceability / KYBC implemented? *(Arts. 30–32 [1].)*
8. If designated (or near-threshold) as a VLOP/VLOSE: are systemic-risk assessment, mitigation, independent audit, ad repository and researcher-data-access delivered? *(Arts. 33–43 [1][4].)*
9. Which DSC has jurisdiction, and is the organisation prepared for Commission oversight of VLOP duties? *(Arts. 49, 56 [1].)*

# Implementation Checklist

- [ ] Every service classified by DSA tier and provider role.
- [ ] Safe-harbour conduct confirmed; no general-monitoring imposed.
- [ ] Notice-and-action mechanism (Art. 16) implemented.
- [ ] Statements of reasons (Art. 17) generated and submitted to the DSA Transparency Database.
- [ ] Terms transparency (Art. 14) and transparency reports (Arts. 15, 24) published.
- [ ] Platform duties live: complaints (20), dispute settlement (21), trusted flaggers (22), ad transparency (26), recommender transparency (27), minor protection (28).
- [ ] Online interfaces reviewed against the dark-pattern prohibition (Art. 25).
- [ ] Marketplace trader traceability / KYBC implemented where applicable (Arts. 30–32).
- [ ] VLOP/VLOSE programme scoped where in scope: risk assessment (34), mitigation (35), audit (37), ad repository (39), researcher access (40), compliance function (41).
- [ ] Competent DSC identified; Commission-oversight readiness for VLOP duties.
- [ ] Joint DSA + GDPR compliance for profiling, ad targeting and moderation data.

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`).*

## Primary Sources

- [1] **Regulation (EU) 2022/2065 (Digital Services Act).** EUR-Lex, ELI. https://eur-lex.europa.eu/eli/reg/2022/2065/oj
- [2] **Regulation (EU) 2016/679 (GDPR), consolidated text** (parallel application to personal-data processing by intermediaries). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504

## Regulatory Guidance

- [3] **The Digital Services Act package.** European Commission, Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/policies/digital-services-act-package
- [4] **Supervision of the designated VLOPs and VLOSEs under the DSA** (list of designated platforms/search engines; last updated 10 July 2026). European Commission. https://digital-strategy.ec.europa.eu/en/policies/list-designated-vlops-and-vloses
- [5] **Commission designates first set of Very Large Online Platforms and Search Engines** (IP/23/2413, 25 April 2023). European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_23_2413
- [6] **Commission fines X €120 million under the Digital Services Act** (first DSA non-compliance decision, 5 December 2025). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-fines-x-eu120-million-under-digital-services-act
- [7] **Commission preliminarily finds TikTok and Meta in breach of their transparency obligations under the DSA** (preliminary findings, October 2025). European Commission. https://digital-strategy.ec.europa.eu/en/news/commission-preliminarily-finds-tiktok-and-meta-breach-their-transparency-obligations-under-digital

## Standards

Not Applicable — the DSA is a regulatory instrument enforced through legislation and Commission decisions rather than voluntary technical standards. Related security and privacy standards (ISO/IEC 27001, ISO/IEC 27701) are treated in the security and privacy-engineering documents; any DSA audit-methodology standards will be added in `dsa-vlop-risk-management` if adopted.

## Academic Sources

Not Applicable — this foundational reference relies on primary legislation and Commission sources. Academic analysis (e.g., of dark-pattern and recommender-transparency enforcement) will be cited in the sub-topic documents.

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Commission — DSA: Very large online platforms and search engines. https://digital-strategy.ec.europa.eu/en/policies/dsa-vlops
- Digital Services Act — Wikipedia (overview and enforcement chronology; non-authoritative). https://en.wikipedia.org/wiki/Digital_Services_Act

# Related Documents

- `dma-foundations` — the Digital Markets Act, the DSA's market-fairness sibling in the DSA package (planned).
- `gdpr-foundations` — parallel data-protection regime for profiling, ad targeting and moderation data.
- `ai-act-foundations` — AI Act overlap for recommender/generative features and content transparency.
- `dsa-vlop-risk-management` — VLOP systemic-risk assessment, mitigation and audit in depth (planned).
- `dsa-recommender-transparency` — recommender-system transparency and profiling opt-out (planned).
- `dsa-trusted-flaggers` — trusted-flagger and out-of-court dispute-settlement regime (planned).
- `dsa-marketplaces` — marketplace trader-traceability (KYBC) duties (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; researched against EUR-Lex (Reg (EU) 2022/2065) and European Commission sources. Full-applicability date (17 Feb 2024), current VLOP/VLOSE designation list (Commission list updated 10 July 2026), the €120m X fine (5 Dec 2025) and the TikTok/Meta preliminary findings (Oct 2025) live-verified. All 7 external links returned HTTP 200. | *pending human review* |
