---
id: dma-interoperability
title: "DMA: Interoperability Obligations (Messaging & Core Platform Services)"
version: 1.0.0
status: approved
classification: public
jurisdiction: [EU]
topic: Digital Markets
document_type: reference
owner: Compliance Research Pipeline
authors:
  - Technical Writer (virtual agent)
related: [dma-foundations, dma-obligations, dsa-foundations, gdpr-foundations, cybersecurity-foundations]
created: 2026-07-11
updated: 2026-07-11
review_due: 2027-07-11
confidence: High
supersedes: Not Applicable
tags: [dma, digital-markets-act, interoperability, messaging, niics, article-7, article-6-7, end-to-end-encryption, reference-offer, gatekeeper, apple, whatsapp]
legal_basis: Regulation (EU) 2022/1925
sources_verified: 2026-07-11
---

# Document Control

| Field | Value |
|-------|-------|
| Document ID | dma-interoperability |
| Version | 1.0.0 |
| Status | approved (frozen in release 0.17.0) |
| Classification | public |
| Owner | Compliance Research Pipeline |
| Created | 2026-07-11 |
| Last Updated | 2026-07-11 |
| Review Due | 2027-07-11 |
| Confidence | High |
| Approved By | pending human review |

**Change gate:** This document was produced by the multi-agent pipeline and is subject to the human review gate. It is a research and implementation reference, **not legal advice**. It is a DMA sub-topic deep dive that expands the parent overviews `dma-foundations` and `dma-obligations`, concentrating on the two interoperability regimes: **messaging interoperability under Article 7** and **operating-system / hardware interoperability under Article 6(7)**. The interoperability landscape is **actively evolving** — phase-in deadlines mature over time, the Commission's Article 6(7) specification proceedings against Apple are being implemented and litigated, and reference offers change. The designation and enforcement facts below were **live-verified against European Commission and Court of Justice sources on 2026-07-11**; always re-confirm the current register, specification-decision status and phase-in timeline before relying on them.

# Executive Summary

The **EU Digital Markets Act (Regulation (EU) 2022/1925**, "DMA") contains two distinct interoperability duties that this document separates carefully. **Article 7** obliges gatekeepers designated for **number-independent interpersonal communications services (NIICS)** — messaging apps — to make the **basic functionalities** of their service interoperable, on request, with competing messaging providers, on a **phased timeline**: basic one-to-one text and file sharing from designation, **group chats within two years**, and **voice and video calls within four years** [1]. **Article 6(7)** is a different, "vertical" duty: gatekeepers designated for an **operating system or virtual assistant** must give third-party services and hardware makers **free, effective interoperability** with the same OS/hardware/software features the gatekeeper's own products use [1].

Article 7 is safeguarded by a **security clause**: the level of security, including **end-to-end encryption (E2EE)** where the gatekeeper already provides it, must be **preserved across the interoperable services** [1]. Interoperability is delivered through a **request-and-reference-offer mechanism** — the gatekeeper publishes a **reference offer** setting the technical terms (Art. 7(4)) and must answer a reasonable interoperability request **within three months** (Art. 7(5)) [1]. The scope of Article 7 is narrow: it binds only **designated NIICS**. In the September 2023 designations, Meta's **WhatsApp** and **Messenger** were designated as NIICS; Apple's **iMessage** was investigated but the Commission concluded on **13 February 2024** that it does **not** qualify as a gatekeeper service, so iMessage is **outside** Article 7 [4][5][7].

Article 6(7) has already generated the DMA's first interoperability enforcement: on **19 March 2025** the Commission adopted two **specification decisions** setting out the measures Apple must implement — one covering **nine iOS connectivity features** for connected devices, the other the **process** for handling developers' interoperability requests [6]. This document distinguishes throughout what is **in force** (the Art. 7 security duty, the reference-offer/request mechanism, basic 1:1 messaging, the Art. 6(7) duty and the Apple specification decisions) from what is **forward-looking** (the maturing Art. 7 group-chat and calls phases, and the ongoing implementation and litigation of the specification decisions).

# Key Takeaways

- **Article 7** binds only gatekeepers designated for a **NIICS** (messaging) CPS; it requires **basic functionalities** to be made interoperable with other messaging providers **on request** [1]. In the current register, Meta's **WhatsApp** and **Messenger** are the designated NIICS [5]. *(Legal obligation.)*
- The **phase-in (Art. 7(2))** is staged from the moment of designation: **(a)** 1:1 **text messaging** and **file/image/voice/video sharing** at designation; **(b)** **group** messaging and group file sharing **within two years**; **(c)** 1:1 and group **voice and video calls within four years** [1]. *(Legal obligation — later phases are forward-looking.)*
- **Security is a hard constraint (Art. 7(3)):** the level of security, **including end-to-end encryption where applicable, must be preserved across the interoperable services** — interoperability may not be used to force a gatekeeper to weaken its own security [1]. *(Legal obligation.)*
- Interoperability runs through a **reference offer** the gatekeeper must publish (Art. 7(4)) and a **request mechanism** requiring a response to a reasonable request **within three months** (Art. 7(5)); only **strictly necessary** personal data may be exchanged, engaging the GDPR in parallel [1][2]. *(Legal obligation.)*
- **iMessage is out of scope.** After a market investigation, the Commission decided on **13 February 2024** that Apple's iMessage (and Microsoft's Bing, Edge and Advertising) **do not qualify as gatekeeper services**, so iMessage is not subject to Article 7 [7]. *(Legal fact — verified.)*
- **Article 6(7)** is a separate duty: **free, effective interoperability** for third-party services and hardware with the **same OS/hardware/software features** used by the gatekeeper's own products (e.g. connectivity between iOS and non-Apple wearables) [1]. *(Legal obligation.)*
- The Commission **operationalised Art. 6(7) by specification**: on **19 March 2025** it adopted two decisions specifying Apple's measures — **nine iOS connectivity features** and the **interoperability-request process** — with staged implementation deadlines [6]. *(Legal fact — verified.)*
- **Enforcement to date is concentrated on Article 6(7)** (the Apple specification decisions), not on a dedicated Article 7 fine; the DMA's headline fines so far (Apple €500m, Meta €200m, 23 April 2025) concern **Articles 5(4) and 5(2)**, not the interoperability duties [6][9]. *(Legal fact — verified.)*

# Purpose

This document exists to give compliance, legal and engineering teams a **precise map of the DMA's two interoperability regimes** and their practical consequences. It supports three tasks: (1) advising a **designated NIICS gatekeeper** on what Article 7 requires, on what timeline, and how the security and reference-offer duties constrain implementation; (2) advising **third-party messaging providers, service developers and hardware makers** on the interoperability rights they can now request and how to invoke the request mechanism; and (3) reading the Commission's **Article 6(7) specification practice** against Apple as the working example of how OS/hardware interoperability is enforced. It is the planned deep dive that `dma-foundations` and `dma-obligations` defer to for interoperability mechanics.

# Scope

**In scope:** The **Article 7** NIICS/messaging interoperability regime — scope (which services are bound), the **Art. 7(2)** phase-in, the **Art. 7(3)** security / end-to-end-encryption safeguard, the **Art. 7(4) reference offer** and **Art. 7(5) request mechanism**, and data-minimisation limits; the **Article 6(7)** OS/hardware interoperability duty and the Commission's **19 March 2025 Apple specification decisions**; the interaction with Article 6(3)/(4) defaults and sideloading where it bears on interoperability; and enforcement of the interoperability duties, live-verified.

**Out of scope (covered elsewhere or in the backlog):**

- **Gatekeeper designation** criteria and the Art. 3 thresholds → parent `dma-foundations`.
- The **full Article 5/6 obligation set** (self-preferencing, steering, data portability, FRAND access) → `dma-obligations`; this document states only the interoperability-adjacent duties.
- **Full case histories and appeals** of the Apple, Meta and Alphabet proceedings → `dma-enforcement-cases` (planned); used here illustratively.
- **GDPR** consent, security and data-minimisation detail underpinning the Art. 7(3)/(5) data exchange → `gdpr-foundations` [2].
- **General cybersecurity control frameworks** (encryption engineering, key management) → `cybersecurity-foundations`; only the DMA-specific security duty is analysed here.

**Assumptions:** The reader has read `dma-foundations` and `dma-obligations` and understands gatekeeper designation, the CPS categories and the Article 5/6/7 architecture. Personal-data processing entailed by interoperability remains governed by the **GDPR** in parallel [2].

# Definitions

*Shared terms are in `GLOSSARY.md` (Gatekeeper, Core platform service, NIICS). Interoperability-specific terms are defined here.*

| Term | Definition | Source |
|------|------------|--------|
| Number-independent interpersonal communications service (NIICS) | An interpersonal communications service that does not connect with the public switched telephone network (e.g. many messaging apps); the class of CPS subject to the Art. 7 messaging-interoperability duty. | [1] |
| Basic functionalities | The core messaging features Art. 7 requires be made interoperable — 1:1 text messaging, sharing of images/voice/video/files, group messaging, and voice/video calls — introduced on the Art. 7(2) phased timeline. | [1] |
| Horizontal interoperability | Interoperability **between competing services of the same kind** (e.g. one messaging app exchanging messages with another); the Article 7 model. | [1] |
| Vertical interoperability | Interoperability **between a service/hardware and the platform features it runs on** (e.g. a third-party wearable accessing iOS connectivity features); the Article 6(7) model. | [1] |
| Reference offer | The published statement of the technical details and general terms and conditions under which a NIICS gatekeeper provides interoperability, including the security and encryption details (Art. 7(4)). | [1] |
| Request mechanism | The Art. 7(5) process by which a provider of a NIICS requests interoperability and the gatekeeper must comply with a reasonable request within three months. | [1] |
| End-to-end encryption (E2EE) | Encryption in which only the communicating end users can read the content; Art. 7(3) requires that the level of security, **including E2EE where the gatekeeper provides it**, be preserved across interoperable services. | [1] |
| Specification decision (Art. 6(7)/8) | A Commission decision under Art. 8(2) specifying the concrete interoperability measures a gatekeeper must implement to comply with Art. 6(7); first used against Apple on 19 March 2025. | [1][6] |

# Background

The DMA (Regulation (EU) 2022/1925) entered into force on 1 November 2022, applied from 2 May 2023, and its gatekeeper obligations became fully applicable on **7 March 2024** [1][8]. Interoperability was one of the Regulation's most contested design choices. Messaging markets are shaped by strong **network effects**: users cannot easily leave a dominant messenger because their contacts are locked inside it. Article 7 attacks that lock-in directly by forcing the largest messengers to open their **basic functionalities** to rivals, so a smaller messaging app can reach a gatekeeper's users without the user having to switch [1][4].

Two features distinguish the messaging duty from the rest of the DMA. First, it is **phased**: the legislator recognised that interoperable group chats and, still more, interoperable **calls** are far harder to deliver securely than 1:1 text, so Article 7(2) staggers them over two and four years from designation [1]. Second, it is **security-bounded**: because the leading messengers already offer end-to-end encryption, Article 7(3) makes clear that interoperability must **not** come at the price of weakening that protection [1]. Alongside the horizontal messaging duty sits the separate **vertical** duty in Article 6(7): opening the operating system's own hardware and software features to third parties so that, for example, a non-Apple smartwatch can integrate with an iPhone as deeply as an Apple Watch can. Because Article 6 duties may need operationalising for a given service, Article 8 lets the Commission adopt a **specification decision** — the route it took against Apple in March 2025 [1][6].

# Legal Framework

The interoperability duties live in **Chapter III** of the DMA. Article 7 is a self-standing regime for messaging; Article 6(7) sits within the list of "specifiable" Article 6 obligations, and Article 8 provides the specification mechanism that operationalises it [1].

- **Article 6(7) — vertical interoperability**: free, effective interoperability with, and access to, the same **hardware and software features accessed or controlled via the operating system or virtual assistant** as are available to the gatekeeper's own services and hardware [1].
- **Article 7 — horizontal (messaging) interoperability**: NIICS gatekeepers must make basic functionalities interoperable on request (7(1)); on the phased timeline (7(2)); preserving security including E2EE (7(3)); via a published reference offer (7(4)); answering a reasonable request within three months (7(5)); exchanging only strictly necessary personal data [1].
- **Article 8 — compliance and specification**: the gatekeeper must ensure and demonstrate compliance; the Commission may adopt a decision **specifying** the Article 6 or 7 measures required (the "regulatory dialogue") [1][6].
- **Enforcement**: non-compliance decisions (Art. 29), **fines** up to **10%** of worldwide turnover (20% for repeat infringement) (Art. 30), and **periodic penalty payments** up to **5%** of average daily worldwide turnover (Art. 31) apply to the interoperability duties as to any other [1].

## Relevant Articles

| Article | Obligation | Source |
|---------|------------|--------|
| Art. 6(3) | Allow easy changing of **defaults** and provide **choice screens** for default services — relevant where messaging/assistant defaults interact with interoperability. | [1] |
| Art. 6(4) | Allow third-party **app stores and sideloading** — the distribution counterpart that lets interoperable third-party clients reach users. | [1] |
| Art. 6(7) | **Vertical interoperability**: free, effective interoperability with, and access to, the same **OS/hardware/software features** (accessed or controlled via the OS or virtual assistant) as are available to the gatekeeper's own services and hardware. | [1][6] |
| Art. 7(1) | **Messaging interoperability on request**: a designated NIICS gatekeeper must make basic functionalities interoperable with other providers' NIICS upon request. | [1] |
| Art. 7(2) | **Phase-in**: (a) 1:1 text and file/image/voice/video **sharing at designation**; (b) **group** messaging and group sharing **within two years**; (c) 1:1 and group **voice and video calls within four years**. | [1] |
| Art. 7(3) | **Security safeguard**: the level of security, including **end-to-end encryption where applicable**, that the gatekeeper provides to its own end users must be **preserved across the interoperable services**. | [1] |
| Art. 7(4) | **Reference offer**: publish the technical details and general terms and conditions of interoperability, including security/encryption details, and keep it updated. | [1] |
| Art. 7(5) | **Request mechanism / timing**: comply with a **reasonable** interoperability request **within three months** of receiving it. | [1] |
| Art. 7(8) | The gatekeeper may take **strictly necessary and proportionate** measures to ensure interoperability does not compromise integrity, security or privacy — read together with 7(3). | [1] |
| Art. 8 | Gatekeeper must ensure/demonstrate compliance; Commission may **specify** Art. 6/7 measures (regulatory dialogue). | [1][6] |
| Art. 29 | **Non-compliance decision** finding a breach and ordering compliance. | [1] |
| Art. 30 | **Fines** up to **10%** of worldwide annual turnover; up to **20%** for repeat infringement. | [1] |
| Art. 31 | **Periodic penalty payments** up to **5%** of average daily worldwide turnover. | [1] |

## Relevant Recitals

*Recitals are not binding but aid interpretation of the enacting terms (Art. 296 TFEU); cited here from the primary text [1].*

| Recital | Interpretive point | Source |
|---------|--------------------|--------|
| Recital 64 area | Rationale for **messaging interoperability** — network effects in NIICS entrench dominant messengers; interoperability lowers switching costs and increases contestability. | [1] |
| Recital 64–65 area | The **phased** approach and the requirement to preserve the **level of security, including end-to-end encryption**, when opening basic functionalities. | [1] |
| Recital 57 area | **Vertical interoperability (Art. 6(7))** — effective interoperability with operating-system and hardware features prevents the gatekeeper reserving those features to its own complementary services. | [1] |

## Relevant Case Law

The interoperability duties are recent and there is **no CJEU judgment interpreting Articles 6(7) or 7 on the merits**. The most significant judgment to date concerns **designation**, and it touches messaging only at the admissibility stage:

| Case | Court / Citation | Holding | Relevance |
|------|------------------|---------|-----------|
| Apple v Commission | General Court, Joined Cases **T-1079/23, T-1080/23 and T-214/24**, judgment **8 July 2026** (Press release CP 96/26) | The General Court **confirmed** Apple's gatekeeper designation for the **App Store and iOS**; challenges concerning **iMessage** were held **inadmissible**. | Confirms who is bound by the Chapter III interoperability duties; it does not decide the scope of Arts. 6(7) or 7. Challenges to the Art. 6(7) specification decisions are emerging and are tracked in `dma-enforcement-cases` (planned). [3] |

*Appeals of, and challenges to, the Article 6(7) specification decisions are developing; they are tracked in `dma-enforcement-cases` (planned) rather than asserted here.* [3][6]

# Regulatory Interpretation

**REGULATORY INTERPRETATION (European Commission — not statutory text unless a specific obligation is cited).**

- **Article 7 has a narrow, designation-gated scope.** After market investigations, the Commission decided on **13 February 2024** that Apple's **iMessage** does **not** qualify as a gatekeeper service (nor Microsoft's Bing, Edge or Advertising), so it is not bound by Article 7; the designated NIICS in the register are Meta's **WhatsApp** and **Messenger** [5][7]. *(Regulatory interpretation / legal fact.)*
- **Article 6(7) is operationalised through specification.** On **19 March 2025** the Commission adopted two decisions specifying Apple's interoperability measures — one on **nine iOS connectivity features** for connected devices (smartwatches, headphones, TVs), the other on the **process** for handling developers' interoperability requests — with staged implementation deadlines; this is the DMA's "regulatory dialogue" applied to interoperability [6]. *(Regulatory interpretation of Arts. 6(7), 8.)*
- **Security is treated as a boundary condition, not an excuse.** The Commission's framing is that Article 7(3) requires interoperability to be delivered **without lowering** the gatekeeper's existing security, including E2EE — but it has also stressed that "security" cannot be invoked as a blanket justification to refuse interoperability that can be delivered safely [1][6]. *(Regulatory interpretation of Arts. 6(7), 7(3).)*
- **Interoperability enforcement so far runs through Article 6(7), not a dedicated Article 7 fine.** The Commission's broad DMA non-compliance investigations opened in **March 2024 (IP/24/1689)** targeted Apple's and Alphabet's Article 5/6 measures [10], and the DMA's first fines (**23 April 2025** — Apple €500m, Meta €200m) concern **Articles 5(4) and 5(2)**; the interoperability track itself has produced **specification decisions** and monitoring rather than penalties to date [6][9]. *(Regulatory interpretation / legal fact.)*
- **Verification note:** the designation register, the iMessage non-designation, and the status of the Article 6(7) specification decisions above were confirmed against the Commission's DMA portal and news service on **2026-07-11**; these are the items most likely to change and must be re-checked at each review [5][6][7]. *(Editorial recommendation.)*

# Technical Considerations

- **Article 7(2) — staged messaging surfaces.** 1:1 text and media sharing are the near-term surface; **group** functionality (2-year phase) and **voice/video calls** (4-year phase) are materially harder because group-key management and real-time media negotiation must work **across** two providers' stacks [1]. *(Legal obligation for NIICS gatekeepers.)*
- **Article 7(3) — cross-provider encryption is the core problem.** Preserving E2EE "across the interoperable services" means both providers must share a compatible key-exchange and message-protection scheme; the mainstream engineering answer is a common secure-messaging protocol layer. The **IETF Messaging Layer Security (MLS)** protocol (RFC 9420) provides E2EE group keying, and the IETF **MIMI** (More Instant Messaging Interoperability) working group is developing the content and transport format for interoperable messaging on top of it [11][12]. *(Best practice / editorial — these standards are not mandated by the DMA.)*
- **Article 7(4)/(5) — reference offer as the integration contract.** The reference offer is effectively the API/specification a requesting provider integrates against; teams should treat it as a versioned, testable interface with a defined onboarding and dispute path, and plan for the **three-month** response obligation [1]. *(Legal obligation for gatekeepers; integration surface for requesters.)*
- **Data minimisation by design.** Article 7 permits the gatekeeper to exchange only the personal data **strictly necessary** to provide effective interoperability; identifier mapping, contact discovery and metadata handling must be minimised and GDPR-lawful [1][2]. *(Legal obligation.)*
- **Article 6(7) — published, parity APIs.** Vertical interoperability requires the gatekeeper to expose the **same** OS/hardware features to third parties as to its own services; the Apple specification decisions concretise this as published APIs, staged betas and a request/dispute process rather than case-by-case discretion [1][6]. *(Legal obligation.)*
- **Abuse and integrity controls (Art. 7(8)).** Opening messaging widens the spam, phishing and malware surface; the gatekeeper may take **strictly necessary and proportionate** measures to protect integrity, security and privacy — proportionality is the litigated edge, mirroring the Art. 6(4) sideloading debate [1]. *(Legal obligation.)*

# Hosting Considerations

- **Interoperability is an infrastructure commitment.** A designated NIICS gatekeeper must run and scale **inter-provider gateways**, identifier-resolution services and the published reference-offer endpoints with production-grade availability; these become part of the hosting footprint and its resilience planning [1]. *(Legal obligation for gatekeepers.)*
- **No cloud CPS is designated.** Cloud computing is a CPS category, but **no cloud service is currently designated** as a gatekeeper CPS, so Article 6(7)/7 interoperability duties do not presently attach to hosting providers as gatekeepers [5]. *(Legal fact — verified.)*
- **Most hosting/messaging-platform providers are requesters, not gatekeepers.** Their practical interest is as **third-party providers** that can now request messaging interoperability (Art. 7) or OS/hardware interoperability (Art. 6(7)); they should build to the reference offer and published APIs and budget for the onboarding path. *(Interpretation.)*

# Game Hosting Considerations

- **In-game and companion messaging is only in scope if designated.** A game's chat or a companion messenger becomes an Article 7 obligation **only** where that service is itself a **designated NIICS** — a high bar that no game-adjacent service currently meets [1][5]. *(Legal fact — verified; assess designation status.)*
- **Article 6(7) helps companion hardware and cross-device play.** Where a game ecosystem relies on **connected devices** (controllers, headsets, wearables) that must integrate with a gatekeeper OS, Article 6(7) interoperability — as specified in the Apple connectivity-features decision — improves access to the underlying OS/hardware features on parity terms [1][6]. *(Legal obligation for gatekeepers — opportunity for developers.)*
- **Real-time gameplay networking is out of scope.** The DMA targets platform contestability and interoperability of communications and OS features, not game-server latency, matchmaking or netcode, which remain governed by GDPR and, where relevant, the AI Act. *(Interpretation.)*

# AI Considerations

- **Virtual assistants are an Article 6(7) interoperability surface.** "Virtual assistants" are a CPS category, and Article 6(7) expressly reaches features "accessed or controlled via the operating system **or virtual assistant**" — so a designated assistant must expose the same integration features to third parties as to the gatekeeper's own services [1]. *(Legal obligation for gatekeepers.)*
- **AI-mediated messaging must respect the security clause.** Where AI features (smart replies, summarisation, on-device models) sit inside a NIICS, they must not become a route to weaken the **E2EE preservation** required by Art. 7(3) — content exposed to server-side AI processing is in tension with end-to-end guarantees [1]. *(Legal obligation / interpretation; read with `gdpr-foundations` [2].)*
- **Parallel regimes.** The DMA governs **interoperability and market power**; the **GDPR** governs the **personal data** exchanged for contact discovery and message delivery; the **AI Act** governs AI **risk**. An AI feature inside an interoperable messenger can engage all three at once [1][2]. *(Interpretation.)*

# Operational Guidance

Labels: **OBLIGATION** (gatekeeper must) / **BEST PRACTICE** (should) / **EDITORIAL RECOMMENDATION** (we suggest).

1. **Confirm whether Article 7 applies at all.** Article 7 binds **only designated NIICS**. Verify designation status against the gatekeepers register before assuming any messaging service is in scope — iMessage, for example, is **not** [5][7]. *(OBLIGATION to assess.)*
2. **(NIICS gatekeeper) Publish and maintain the reference offer.** Treat it as a versioned technical interface with clear security/encryption terms, onboarding steps and a dispute path (Art. 7(4)). *(OBLIGATION.)* [1]
3. **(NIICS gatekeeper) Meet the phase-in and the three-month clock.** Deliver 1:1 text/media, then group (2-year phase), then calls (4-year phase); respond to a reasonable interoperability request within **three months** (Arts. 7(2), 7(5)). *(OBLIGATION.)* [1]
4. **Preserve security, including E2EE (Art. 7(3)).** Design cross-provider interoperability on a compatible secure-messaging protocol so encryption is not degraded; consider MLS (RFC 9420) and the emerging MIMI work as the technical baseline. *(OBLIGATION for the outcome; BEST PRACTICE for the specific standard.)* [1][11][12]
5. **Minimise personal data in interoperability.** Exchange only what is **strictly necessary** for effective interoperability and keep it GDPR-lawful (identifier mapping, contact discovery, metadata). *(OBLIGATION.)* [1][2]
6. **(OS/assistant gatekeeper) Deliver Article 6(7) on parity terms and to specification.** Expose the same OS/hardware features to third parties as to your own services, and implement any Art. 8 **specification decision** on its deadlines (as in the Apple case). *(OBLIGATION.)* [1][6]
7. **(Third-party providers) Invoke the request mechanism and log refusals.** Use the reference offer / request process to obtain messaging or OS interoperability, and document any refusal or degraded condition for complaint to the Commission. *(BEST PRACTICE.)* [1][4]
8. **Do not weaponise "security" (or use it as a shield).** Security/integrity measures under Arts. 7(3), 7(8) and 6(7) must be **strictly necessary and proportionate**; over-broad restrictions risk being read as circumvention. *(OBLIGATION / EDITORIAL RECOMMENDATION.)* [1][6]
9. **Maintain an interoperability watch-list.** Re-verify the register, the phase-in status and the specification-decision implementation at each review — they change. *(EDITORIAL RECOMMENDATION.)* [5][6]

# Risk Register

| ID | Risk | Likelihood | Impact | Basis | Mitigation | Residual |
|----|------|-----------|--------|-------|------------|----------|
| R1 | NIICS gatekeeper misses an Art. 7(2) phase deadline (group/calls) | Medium | High | Art. 30 fine up to 10% turnover [1] | Roadmap phases against designation date; deliver reference offer early | Medium |
| R2 | Interoperability delivered by weakening E2EE (breach of Art. 7(3)) | Medium | Very High | Art. 7(3); reputational + security harm [1] | Compatible secure-messaging protocol (e.g. MLS); preserve E2EE end-to-end | Medium |
| R3 | Reference offer inadequate or request-handling too slow (breach of Art. 7(4)/(5)) | Medium | High | Arts. 7(4), 7(5) (3-month limit) [1] | Versioned reference offer; SLA-backed request pipeline | Low |
| R4 | Excess personal-data exchange for interoperability (GDPR + Art. 7 breach) | Medium | High | Art. 7 data-minimisation; GDPR [1][2] | Strictly-necessary data only; DPIA; identifier minimisation | Low |
| R5 | Non-compliant/incomplete Art. 6(7) interoperability | Medium | Very High | Art. 8 specification decisions [1][6] | Deliver specified measures on deadline; parity APIs; dispute process | Medium |
| R6 | "Security" or "integrity" used to over-restrict interoperability (circumvention) | Medium | High | Arts. 7(3), 7(8), 6(7); enforcement practice [1][6] | Proportionality analysis; document necessity of each control | Medium |
| R7 | Assuming a service is in scope when it is not designated (wasted effort) | Low | Medium | Designation-gated scope; iMessage not designated [5][7] | Verify register before building | Low |
| R8 | Third-party requester under-uses interoperability rights | Medium | Medium | Arts. 6(7), 7 opportunities [1][4] | Invoke request mechanism; log refusals for complaint | Low |

# Implementation Roadmap

- **Phase 0 — Scope & posture:** Determine whether you are a **designated NIICS/OS gatekeeper** (obligation) or a **third-party requester** (opportunity); confirm against the register. *Effort:* Low–Medium.
- **Phase 1 (gatekeeper) — Reference offer & 1:1 messaging:** Publish the Art. 7(4) reference offer; deliver the Art. 7(2)(a) 1:1 text/media interoperability and stand up the three-month request pipeline. *Effort:* High.
- **Phase 2 (gatekeeper) — Group functionality:** Deliver the Art. 7(2)(b) group phase with cross-provider group keying, preserving E2EE. *Effort:* Very High.
- **Phase 3 (gatekeeper) — Calls:** Deliver the Art. 7(2)(c) voice/video-call phase (1:1 and group). *Effort:* Very High.
- **Phase 4 (OS/assistant gatekeeper) — Article 6(7):** Expose parity OS/hardware/assistant features; implement any Art. 8 specification decision on deadline. *Effort:* Very High.
- **Phase 5 — Requester enablement & monitoring:** For third parties, operationalise the request mechanism and build a complaint/evidence trail; for all, track phase-in status, specification decisions and case law. *Effort:* Ongoing.

# Compliance Maturity Model

| Level | Name | Description | Indicators |
|-------|------|-------------|-----------|
| 1 | Initial | Interoperability scope not assessed; ad-hoc response to requests. | No designation analysis; no reference offer. |
| 2 | Managed | Scope assessed; reference offer published; 1:1 messaging interoperable. | Art. 7(4) offer live; Art. 7(2)(a) delivered. |
| 3 | Defined | Request pipeline meets the 3-month clock; group phase delivered; Art. 6(7) parity APIs published. | Art. 7(2)(b) live; Art. 6(7) measures published. |
| 4 | Quantitatively Managed | E2EE-preserving interoperability outcome-tested with metrics; specification decisions delivered on time; calls phase on track. | KPIs on onboarding time, security parity, request throughput. |
| 5 | Optimising | Interoperability integrated with GDPR/security governance; proactive standards engagement (MLS/MIMI) and case-law tracking. | Cross-regime programme; standards participation; live watch-list. |

# Audit Questions

1. Has **designation status** been verified so that Article 7 is applied only to **designated NIICS**, and is the conclusion documented (e.g. that iMessage is out of scope)? *(Art. 7; [5][7].)*
2. For a NIICS gatekeeper, is there a published, current **reference offer** (Art. 7(4)) with clear security/encryption terms and an onboarding path? *(Art. 7(4) [1].)*
3. Is each **Art. 7(2) phase** delivered on time (1:1 at designation; group within 2 years; calls within 4 years), and is the **three-month** request-response obligation met? *(Arts. 7(2), 7(5) [1].)*
4. Is **E2EE and the overall security level preserved across interoperable services** (Art. 7(3)), and is that evidenced technically rather than asserted? *(Art. 7(3) [1].)*
5. Is only **strictly necessary personal data** exchanged for interoperability, with a GDPR lawful basis and a DPIA? *(Art. 7; GDPR [1][2].)*
6. For an OS/assistant gatekeeper, are **Article 6(7)** features exposed to third parties on **parity** terms, and is any **Art. 8 specification decision** delivered on its deadlines? *(Arts. 6(7), 8 [1][6].)*
7. Are security/integrity restrictions under Arts. 7(3), 7(8) and 6(7) **strictly necessary and proportionate**, with the necessity of each control documented? *(Arts. 7(3), 7(8), 6(7) [1][6].)*
8. Is an **interoperability watch-list** maintained (register, phase-in status, specification decisions)? *([5][6].)*

# Implementation Checklist

- [ ] Designation status verified; Article 7 applied only to designated NIICS (iMessage confirmed out of scope).
- [ ] (NIICS gatekeeper) Art. 7(4) reference offer published and kept current.
- [ ] (NIICS gatekeeper) Art. 7(2)(a) 1:1 text/media interoperability delivered.
- [ ] (NIICS gatekeeper) Art. 7(2)(b) group interoperability delivered (2-year phase).
- [ ] (NIICS gatekeeper) Art. 7(2)(c) voice/video-call interoperability delivered (4-year phase).
- [ ] Art. 7(5) three-month request-response pipeline operational.
- [ ] Art. 7(3) E2EE / security level preserved across interoperable services and tested.
- [ ] Interoperability data exchange minimised to strictly necessary; GDPR lawful basis + DPIA.
- [ ] (OS/assistant gatekeeper) Art. 6(7) parity interoperability delivered; any Art. 8 specification decision implemented on deadline.
- [ ] Security/integrity controls documented as strictly necessary and proportionate (Arts. 7(3), 7(8), 6(7)).
- [ ] (Third-party requester) Request mechanism invoked; refusals logged for complaint.
- [ ] Interoperability watch-list maintained (register, phase-in, specification decisions).

# References

*All links verified live (HTTP 200) on 2026-07-11 (`sources_verified`). consilium.europa.eu is bot-blocked to automated agents and is not cited here; Commission (EC) and EUR-Lex sources are used throughout.*

## Primary Sources

- [1] **Regulation (EU) 2022/1925 (Digital Markets Act).** EUR-Lex, ELI (Arts. 6(3)–(4), 6(7), 7, 8, 29–31). https://eur-lex.europa.eu/eli/reg/2022/1925/oj
- [2] **Regulation (EU) 2016/679 (GDPR), consolidated text** — parallel application to the personal-data exchange entailed by interoperability (data minimisation, security). EUR-Lex. https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02016R0679-20160504
- [3] **General Court judgment of 8 July 2026, Apple v Commission (Joined Cases T-1079/23, T-1080/23, T-214/24)** — designation upheld; iMessage challenges inadmissible; Press release CP 96/26. Court of Justice of the EU. https://curia.europa.eu/site/upload/docs/application/pdf/2026-07/cp260096en.pdf

## Regulatory Guidance

- [4] **About the Digital Markets Act.** European Commission. https://digital-markets-act.ec.europa.eu/about-dma_en
- [5] **DMA designated gatekeepers (gatekeepers portal)** — designated NIICS (WhatsApp, Messenger) and current register. European Commission. https://digital-markets-act.ec.europa.eu/gatekeepers-portal_en
- [6] **Commission provides guidance under the DMA to facilitate development of innovative products on Apple's platforms** — the two Article 6(7) specification decisions (DMA.100203 connected-device features; DMA.100204 interoperability-request process), 19 March 2025. European Commission. https://digital-markets-act.ec.europa.eu/commission-provides-guidance-under-digital-markets-act-facilitate-development-innovative-products-2025-03-19_en
- [7] **Commission closes market investigations on Microsoft's and Apple's services under the DMA** (13 February 2024) — iMessage, Bing, Edge and Microsoft Advertising do **not** qualify as gatekeeper services. European Commission. https://digital-markets-act.ec.europa.eu/commission-closes-market-investigations-microsofts-and-apples-services-under-digital-markets-act-2024-02-13_en
- [8] **Designated gatekeepers must now comply with all obligations under the DMA** (7 March 2024). European Commission. https://digital-markets-act.ec.europa.eu/designated-gatekeepers-must-now-comply-all-obligations-under-digital-markets-act-2024-03-07_en
- [9] **Commission finds Apple and Meta in breach of the Digital Markets Act** (23 April 2025; fines under Arts. 5(4) and 5(2), not the interoperability duties). European Commission — Shaping Europe's Digital Future. https://digital-strategy.ec.europa.eu/en/news/commission-finds-apple-and-meta-breach-digital-markets-act
- [10] **Commission opens non-compliance investigations against Alphabet, Apple and Meta under the DMA** — press release IP/24/1689. European Commission. https://ec.europa.eu/commission/presscorner/detail/en/ip_24_1689

## Standards

- [11] **RFC 9420 — The Messaging Layer Security (MLS) Protocol.** IETF (July 2023) — E2EE group-keying protocol relevant to preserving encryption across interoperable messaging; **not mandated by the DMA**. https://www.rfc-editor.org/rfc/rfc9420
- [12] **More Instant Messaging Interoperability (MIMI) working group.** IETF — develops the content/transport format for interoperable secure messaging on top of MLS; **not mandated by the DMA**, cited as the relevant standards effort. https://datatracker.ietf.org/wg/mimi/about/

## Academic Sources

Not Applicable — this obligation-level reference relies on primary legislation, Commission specification/enforcement sources and open IETF standards. Peer-reviewed analysis of messaging-interoperability security (the E2EE-versus-interoperability trade-off) will be cited in `dma-enforcement-cases` (planned) as the litigation develops.

# Further Reading

*Non-authoritative; provided for orientation only.*

- European Commission — DMA developer portal (interoperability). https://digital-markets-act.ec.europa.eu/developer-portal/interoperability_en
- Digital Markets Act — overview article (Wikipedia). https://en.wikipedia.org/wiki/Digital_Markets_Act

# Related Documents

- `dma-foundations` — parent overview: gatekeeper designation, CPS categories and the obligations at foundational level (**prerequisite reading**).
- `dma-obligations` — the article-by-article obligation deep dive; this document expands its Article 6(7) and Article 7 treatment (**prerequisite reading**).
- `dsa-foundations` — the Digital Services Act sibling in the DSA/DMA package (companion regime).
- `gdpr-foundations` — the data-minimisation and security standard for the personal data exchanged in interoperability (**prerequisite for the data aspects**).
- `cybersecurity-foundations` — encryption, key-management and security-control context for the Art. 7(3) security duty.
- `dma-enforcement-cases` — the Apple, Meta and Alphabet proceedings and the interoperability-specification litigation in depth (planned).

# Revision History

| Version | Date | Author | Change | Approved By |
|---------|------|--------|--------|-------------|
| 0.1.0 | 2026-07-11 | Technical Writer (virtual agent) | Initial draft; interoperability sub-topic deep dive researched against EUR-Lex (Reg (EU) 2022/1925, Arts. 6(7), 7, 8) and European Commission DMA sources. Article 7 phase-in (7(2)), security/E2EE clause (7(3)), reference offer (7(4)) and three-month request mechanism (7(5)), and Article 6(7) parity duty verified against the primary text. Designated NIICS (WhatsApp, Messenger), the 13 February 2024 iMessage non-designation, the 19 March 2025 Article 6(7) Apple specification decisions (DMA.100203/100204), the 23 April 2025 Apple/Meta fines (Arts. 5(4)/5(2)), and the 8 July 2026 General Court judgment were live-verified on 2026-07-11. All external links returned HTTP 200. | pending |
| 1.0.0 | 2026-07-12 | Editorial Reviewer (virtual agent) | Approved at the autonomous backlog gate (Cluster C); full-repo validator/link/lint suite green; frozen in release 0.17.0. | Orchestrator (QA-verified) |

</content>
</invoke>
