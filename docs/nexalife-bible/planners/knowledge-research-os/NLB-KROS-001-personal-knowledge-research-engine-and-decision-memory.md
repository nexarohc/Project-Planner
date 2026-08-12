# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 1 — Personal Knowledge Base, Research Engine, Verification & Decision Memory

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-001 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Home domains | LD-02 Education, LD-16 Science & Research (`NLB-03`) |
| Catalogue anchor | PU-02-023–031 (research), PU-16-001–013 (`NLB-04`) |
| Dependencies | `NLB-06` · `NLB-07` · `NLB-NXOS-002` · `NLB-NXOS-003` · `NLB-NXOS-005` · `NLB-CPIOS-002` |

---

## Purpose

KROS turns NexaLife from a system that retrieves information into one that can **research, verify, connect, and remember conclusions** — and, critically, keep track of how much it actually knows.

> NexaLife should not merely know things. It should know what the user is trying to accomplish with that knowledge — and how well the evidence supports it.

### Scope boundaries

This volume deliberately does **not** re-specify four things that already exist:

| Already owned by | Covers |
| --- | --- |
| `NLB-NXOS-005` | The Universal Knowledge Graph — node types, edge types, permission-aware traversal. KROS contributes Research and Decision nodes to it; it does not build a second graph. |
| `NLB-NXOS-003` | The memory system — kinds, ranking, compression, forgetting. KROS adds *research-specific* decay rules, not a second memory store. |
| `NLB-NXOS-002` | Confidence scoring and evidence tracking as a platform mechanism. KROS applies them to external sources. |
| `NLB-SP-002/003` | Learning mechanics for **students** — spaced repetition, active recall, mastery models, prerequisite graphs, flashcards. Part 2 covers only what adult/professional learning adds on top. |

**What is genuinely new here is research methodology**: how sources are ranked, how conflicts are surfaced, how a claim is verified, when to stop researching, and how a conclusion is remembered along with the reasoning that produced it.

---

## Architecture

```
                    KNOWLEDGE OS
                         │
       ┌─────────────────┼─────────────────┐
    CAPTURE          UNDERSTAND         CONNECT
       │                 │                 │
   Documents          Summaries          Ideas
   Web                Concepts           People
   Notes              Facts              Projects
   Media              Evidence           Decisions
       └─────────────────┼─────────────────┘
                       APPLY
              Learn → Decide → Create → Act
```

---

## Universal Knowledge Search

*"Find everything I have about the Brazil project"* searches authorized documents, notes, emails, messages, calendar, tasks, saved research, and web references — federating `NLB-CPIOS-001`'s communication search and `NLB-08`'s Global Search rather than duplicating either.

**Every result shows its source** (document, email, web, note, meeting) and the original remains inspectable.

---

## Epistemic Status

The foundation of this volume. Every piece of knowledge carries an explicit status:

| Status | Meaning |
| --- | --- |
| **Fact** | Directly supported by a source |
| **Interpretation** | A reasoned conclusion from facts |
| **Assumption** | Not confirmed; being treated as true provisionally |
| **User opinion** | The user's own viewpoint |
| **Unknown** | Not established — a first-class state, not an absence |
| **Unverified** | Claimed but not checked |
| **Conflicting** | Sources disagree |
| **Outdated** | Was true; may no longer be |

Most systems collapse these into "information." Keeping them distinct is what lets a user act on a conclusion without inheriting hidden assumptions — and it is the applied form of `NLB-NXOS-002`'s Confidence Scoring.

---

## Source Ranking

Research prioritizes evidence by type:

```
1. Primary sources
2. Official / issuing-body sources
3. Regulatory & government sources
4. Academic sources
5. Reputable secondary sources
6. Community discussion
7. Unverified sources
```

**Source deduplication** is essential and frequently missed: fifteen sites reprinting one press release are **one** source, not fifteen confirmations. Treating repetition as corroboration is the most common way automated research manufactures false confidence.

**Conflict detection** surfaces disagreement rather than silently picking a winner:

```
Source A   $12M
Source B   $15M
Primary    $14.2M   ← and why the others differ
```

**Date awareness** applies to every result — publication date, last-updated date, effective date, and whether the information is historical or current. Asked about 2022, **Nexa does not silently substitute current information.**

---

## Research Engine

**Research plans** are proposed before work begins (market size → competitors → regulation → pricing → demand → risks), and **the user can modify the plan** — the cheapest possible moment to correct a misaimed investigation.

**Depth and budget** are explicit: Quick / Standard / Deep / Exhaustive, with an optional time budget (*"spend up to 10 minutes"*) the agent optimizes source selection within.

**Stop conditions** prevent unbounded research: stop after N verified results, after exhausting official sources, or on **source saturation** — *"additional searches are no longer producing materially new evidence."* Knowing when to stop is a research skill, and it needs to be specified rather than left to run.

**Coverage reporting** is honest about its own limits:

```
Source diversity     92%
Primary evidence     88%
Recency              95%
Cross-verification   81%

Question coverage    ~87%   ·   Known gaps: 3
```

These are **internal quality indicators, explicitly estimates** — never a claim of completeness.

**Open questions are tracked and reported**: *"Two major questions remain unanswered"* rather than presenting partial research as finished.

---

## Verification

**Claims are decomposed before they are answered.** *"Is this company FDA approved?"* becomes: which company, which product, which facility, which approval type, current status. A vague question answered vaguely is how regulatory misinformation propagates.

**Precision in claims** — not *"the company is approved"* but *"the available evidence indicates Product X received approval on [date]."*

**Evidence hierarchy** for regulated subjects:

```
Primary regulatory record → Official company record → Official database
  → Reputable secondary source → Unverified claim
```

**Evidence matrix** makes support visible per claim:

```
CLAIM          SOURCE A   SOURCE B   SOURCE C
Market size       ✓          ✓          —
Approval          ✓          —          ✓
Pricing           —          ✓          ✓
```

**Claim-level citations** keep every significant claim traceable to its source passage.

**Bias check and counterargument mode** — Nexa can offer: *"Would you like me to search specifically for evidence that contradicts this conclusion?"* and produce structured counterarguments against the user's own stated conclusion. This is the antidote to research that only confirms, and it should be offered rather than waited for.

---

## Knowledge Decay

Different knowledge ages at different rates, and treating them identically is a correctness bug:

| Decays fast | Decays slowly |
| --- | --- |
| Prices, stock data, availability | Historical facts |
| Regulatory status | Mathematical concepts |
| Job openings, contacts, roles | Established scientific principles |

Knowledge carries a suggested **review interval** (price data: 7 days; regulation: 30 days; historical fact: none), and on reaching it Nexa asks *"This information may be stale — refresh it?"* rather than continuing to serve it as current.

**Freshness state** — Current / Recent / Aging / Outdated — is shown alongside results.

---

## Research Snapshots & Change Detection

Research is **saved as a dated snapshot** (topic, date, source count) and **versioned** when repeated, with differences highlighted:

```
OLD   Approval active
NEW   Approval expired
IMPACT  High
```

**Watchlists** monitor entities (a company, market, product, regulation) with alert intensity the user sets — All changes / Major only / Critical only / None — and **material-change defaults** (product launch, regulatory action, leadership change, acquisition, major pricing move, market entry).

**Change-only reporting** replaces re-reading a full report: *"Only these 4 things changed since last week."*

---

## Decision Memory

The most underused idea in this volume, and the one with the longest payoff.

A decision is recorded with its **reasoning**, not just its outcome:

```
DECISION   Choose Supplier A
REASON     Lower cost + faster delivery
ASSUMED    Delivery estimate holds; price stable 6 months
DATE       Aug 12
REVIEW     Dec 2026
```

At the review date, Nexa surfaces it and captures the **outcome against expectation**:

```
EXPECTED   Lower cost
ACTUAL     18% lower
RESULT     Successful
```

Recording *why* a decision was made — and what was assumed — is what makes it possible to learn from it later. Without the reasoning, a past decision teaches nothing; with it, the user can see which of their assumptions actually hold. This connects to `NLB-04`'s Decision Journal (PU-01-031) and gives it a mechanism.

**Lesson memory** captures post-project learning (what worked, what failed, what changed, what to repeat, what to avoid), and **playbooks/SOPs** turn repeated knowledge into reusable procedure with versioning — extending `NLB-CWOS-002`'s SOP engine to research and decisions.

---

## Documents

**Document Q&A** over PDFs, documents, spreadsheets, and presentations, extracting key points, tables, dates, entities, decisions, tasks, and risks.

**Comparison** across two versions reports additions, deletions, and modifications; for contracts, it reports which clauses changed (price, term, delivery, liability) — **Nexa does not represent itself as a lawyer**, per the Regulated-adjacent posture in `NLB-NXOS-004`.

**Summary levels**: one-line / executive / detailed / section-by-section. A **question generator** produces what the user should ask before signing.

**Document-derived actions** route to tasks and calendar per `NLB-CPIOS-001`, always confirmed.

---

## Knowledge Base & Hygiene

Saved research, notes, decisions, lessons, references, and ideas organize into **collections** and **tags** (suggested, never forced).

**Knowledge health** reports duplicates, outdated items, unverified claims, and unlinked entries. A **cleanup agent** proposes merges, refreshes, missing tags, and links — **user-approved**, per `NLB-NXOS-003`'s user-control guarantees.

**Memory types** (fact, preference, lesson, decision, goal, idea, reference, procedure) and **priority** (critical / important / normal / temporary) determine retention; temporary memories expire, with the user asked whether to archive or delete.

---

## Processing Transparency

Where a task runs matters when the input is sensitive:

**Local mode** for search, summaries, personal notes, and private document processing where device capability allows. **Cloud mode** for deep research, large documents, and complex reasoning.

**Disclosure before external processing** is mandatory: *"This task requires cloud processing. Your selected document will be sent to the configured AI provider."* The user should never discover after the fact that a private document left the device.

**Model selection** (Fast / Balanced / Deep / Private) may be automatic based on complexity, privacy settings, cost, and latency — **with user override**, per `NLB-06`'s Model Routing.

**Cost visibility** where external AI incurs charges, and **source-by-source AI access** (this drive yes, that folder no), with a **knowledge audit log** recording query, sources accessed, and time.

---

## Principle

**Capture → Verify → Understand → Connect → Learn → Apply → Remember.**

The objective is not an AI that answers questions. It is a personal intelligence layer that becomes more useful over time **because the user can inspect, correct, and control what it believes.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial KROS foundation. Establishes explicit epistemic status (including Unknown as a first-class state), source ranking with deduplication and conflict surfacing, the research engine with plans/budgets/stop conditions/saturation, claim decomposition and the evidence hierarchy, counterargument mode, knowledge decay with review intervals, research snapshots and change detection, decision memory recording reasoning and assumptions, and processing-location disclosure. Scoped explicitly against NXOS-002/003/005 and NLB-SP-002/003. |

---

**End of Part 1 (Version 1.0)**
