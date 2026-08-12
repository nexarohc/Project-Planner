# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 3 — Knowledge Workspace, Personal Encyclopedia, Research Studio & Knowledge-to-Execution

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-003 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-07` · `NLB-08` · `NLB-09` · `NLB-10` · `NLB-NXOS-005` · `NLB-CWOS-002` |

---

## Purpose

Parts 1 and 2 defined how NexaLife researches and what it is allowed to claim. Part 3 defines **where the user does that work** — the interface, the workspace, the shared-knowledge layer, and the path from a finished conclusion to an action someone actually takes.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-08` | Global Search as a product surface, and the Universal Experience Framework this workspace is built inside. KROS specifies the *knowledge-specific* surfaces, not a second design system. |
| `NLB-07` | The search index, saved queries, and what permissions bound them. |
| `NLB-NXOS-005` | The Universal Knowledge Graph — node types, edge types, permission-aware traversal. This part specifies how a user **navigates and renders** that graph; it does not redefine it. |
| `NLB-10` | Identity, workspaces, roles, and the Permission Engine every access mode below resolves against. |
| `NLB-09` | Workflow triggers and recurrence. Knowledge triggers compile onto them. |

---

## The Universal Knowledge Interface

One surface for everything the user knows:

```
┌──────────────────────────────────────────────┐
│ 🔎  Ask anything about your knowledge…       │
├──────────────────────────────────────────────┤
│  Ask │ Research │ Analyze │ Create │ Review  │
├──────────────────────────────────────────────┤
│              INTELLIGENCE SPACE              │
│   Sources  ·  Evidence   ·  Knowledge        │
│   Projects ·  Decisions  ·  Learning         │
└──────────────────────────────────────────────┘
```

**Natural language is the primary interface**, not a fallback. *"Find everything related to this project"*, *"compare these"*, *"what am I missing?"* Slash shortcuts (`/research`, `/verify`, `/teach`, `/remember`) exist for users who prefer them and are never the only way to reach a capability.

**Commands resolve against current context** — *"compare this with the previous version"* while viewing a document, *"research its competitors"* while viewing a company. The context is shown, so the user can see what "this" resolved to before the work starts.

### Modes

| Mode | Shape |
| --- | --- |
| **Ask** | question → relevant knowledge → answer → sources |
| **Research** | question → plan → search → verify → synthesize (`NLB-KROS-001`) |
| **Analyze** | data → structure → patterns → conclusion |
| **Create** | knowledge → report, brief, presentation, checklist, SOP, proposal, study material |
| **Teach** | knowledge → learning experience (`NLB-KROS-002`) |
| **Review** | existing work → errors, gaps, contradictions, risks, missing evidence |

**Review mode is the one users skip and shouldn't.** Running finished work back through the system — *what does this assert without evidence?* — catches the failure that verification-on-the-way-in misses, because a document assembled from individually sound pieces can still argue something none of them support.

---

## The Knowledge Reader

Documents open in a reader where the AI is available **in place** rather than in a separate chat:

```
DOCUMENT
─────────────────────────────
  Highlight · Comment · Ask · Explain · Verify · Summarize
```

**Highlight-to-knowledge** sends a passage to a project, topic, research file, memory, or note — with its source document and location retained, so the saved fragment never becomes an orphan claim.

**Annotations** (notes, questions, highlights, tags, bookmarks) are the user's. **Suggested annotations** — *"this paragraph contains a key assumption"* — are proposals the user accepts or ignores; Nexa does not annotate a document on its own authority.

**Document chat** attaches a conversation to a document. **Multi-document chat** builds a temporary knowledge context from a selected set (*"compare these reports"*) that is scoped to the task and does not silently persist into later questions.

**Collections** group a project's documents; **smart collections** are queries (*"documents modified this month mentioning Project X"*) rather than folders.

**Reading list and progress** track to-read / reading / completed, with time-remaining **clearly labelled an estimate**. A **reading assistant** offers context and prerequisites before, definitions and explanations during, and summary, key lessons, and optional recall questions after.

---

## Personal Encyclopedia

The accumulated output of research, organized as reference rather than as history.

Each article carries **definition, key facts, related topics, sources, user notes, and a last-verified date** — the last of these being what separates an encyclopedia from a pile of old summaries. Articles are **versioned** as the underlying knowledge changes, so a superseded understanding remains inspectable rather than being overwritten.

A **personal glossary** holds industry terms, technical terms, acronyms, and internal terminology, with **contextual definitions** where a word means different things in different places: *"in this document, 'approval' refers to regulatory marketing authorization."* Ambiguous vocabulary is a common and invisible source of wrong conclusions, and resolving it per-context is cheaper than resolving it per-argument.

---

## Entity, Project & Topic Pages

The knowledge graph (`NLB-NXOS-005`) rendered as pages a person can read:

| Page | Gathers |
| --- | --- |
| **Entity** (company, product, regulation) | overview, products, markets, documents, contacts, research, decisions, timeline, sources |
| **Person** | contact, organization, meetings, emails, projects, notes, tasks — **only where authorized**, drawing on `NLB-RSOS-001`'s People Graph |
| **Project** | goal, status, tasks, people, documents, research, decisions, timeline, risks |
| **Topic** | overview, research, documents, learning, open questions, related topics |

**Navigation is traversal, not search.** Company → Product → Regulation → Document → Decision moves along real edges without re-querying at each step; a **graph explorer** expands, collapses, focuses, and filters by date, source, entity, project, confidence, and knowledge type. Every hop is permission-checked at the hop, per `NLB-NXOS-005`.

---

## Knowledge Spaces & Access

```
PRIVATE · PERSONAL · PROJECT · TEAM · PUBLIC
```

**Temporary spaces** (*"analyze these files"*) archive or dissolve on completion, per the user's setting — a workspace that quietly becomes permanent is how a one-off analysis of sensitive files turns into a permanent index of them.

**Private spaces** are the strong case: no external AI, no sharing, no indexing outside the workspace. **The capabilities actually available depend on device and configured providers, and are stated plainly rather than implied** — per `NLB-KROS-001`'s processing-location disclosure. A privacy guarantee the architecture cannot keep is worse than an honest limitation.

---

## Team Knowledge

For organizations, shared knowledge (policies, SOPs, projects, research, training) sits alongside personal knowledge without merging into it.

**A user's private memory is never part of shared organizational knowledge unless explicitly shared.** This is the single boundary most easily violated by a system that indexes everything a user touches, and it resolves against `NLB-10`'s Permission Engine rather than a KROS-local rule.

**Roles** — owner, editor, commenter, viewer. **Approval workflow** for knowledge that carries weight: draft → review → approved → published. **Official knowledge** can be designated by the organization and **ranks above unofficial internal material in search**, which is the practical mechanism that stops a stale personal note outranking the current policy.

**Ownership and review cycles** attach an owner, a reviewer, and a review date to every shared object (SOP: 90 days; policy: 180). On expiry the object becomes **Needs Review** — it does not disappear, and it does not silently keep presenting as current. *"This SOP has not been reviewed since 2024"* is shown at the point of use, not buried in an admin report. This extends `NLB-CWOS-002`'s SOP engine with a review lifecycle.

---

## Expert Copilot

Domain workspaces (business, pharmaceutical, regulatory, technical, market, academic) carry their own terminology, templates, sources, rules, and workflows. **Nexa supports domain work without representing itself as a certified professional**, per the regulated-adjacent posture in `NLB-NXOS-004`.

**Domain instructions persist within a project**: *"for this project, only use official regulatory sources"* remains in force for every subsequent query in that workspace rather than being re-stated each time — and each project may carry its own **source hierarchy**, since the ranking appropriate to regulatory research is not the one appropriate to market research.

---

## Research Studio

**Research templates** capture a repeatable investigation:

```
COMPANY DUE DILIGENCE
1 Identity · 2 Ownership · 3 Products · 4 Regulatory status
5 Manufacturing · 6 Markets · 7 Risks · 8 Evidence
```

A **template library** (company research, market research, supplier verification, competitor analysis, literature review, regulatory review) with **variables** (`{{company}}`, `{{country}}`, `{{product}}`) turns a well-run investigation into an asset rather than a one-time performance.

**Output schema is user-specified and preserved**: *"return a table with company, country, product, approval status and source."* The requested structure is what comes back — a system that reshapes the output to suit itself cannot be built on. Results **export** to spreadsheet, CSV, database, report, or presentation.

### Entity resolution

**Normalization** standardizes company names, countries, dates, units, currencies, and product names **while retaining the original values**. The normalized form is for querying; the original is what the source actually said, and losing it makes every downstream claim unverifiable.

**Merging is proposed, never automatic where uncertain.** `ABC Pharma Ltd` and `ABC Pharmaceuticals Limited` are probably one company; two companies genuinely sharing a name in different countries are not, and **stay separate**. Match confidence is shown (match / possible match / unknown), and a **normalization audit** reports what was merged, what remains a potential duplicate, and what is unresolved. Silent entity merging corrupts a research dataset in a way that is nearly impossible to detect afterwards.

---

## Comparison

A comparison builder holds options against user-chosen criteria (price, quality, risk, speed, evidence, plus any the user adds), and **each cell shows the evidence behind it**.

**Where an option has no data, the cell reads "Not available."** It is never filled with an estimate, an inference from a similar product, or a plausible number. A comparison table is read as fact regardless of how it was assembled, which is exactly why the gaps must be visible as gaps.

A **knowledge matrix** scales this to large projects, and coverage, risk, evidence, and progress render as a heatmap where the shape of what is *missing* is often the finding.

---

## Briefs & Question Generation

**Intelligence brief**, one action: executive summary, key findings, evidence, risks, **unknowns**, recommendations, sources. **Executive mode** compresses to five bullets, three risks, three actions, one recommendation; **deep-dive mode** adds methodology, evidence, analysis, limitations, and appendices. Both include the unknowns — that section is not the part that gets cut for brevity.

**Question generation** closes the loop: after research, *"what should I ask next?"* surfaces missing information, decision-critical questions, unresolved contradictions, and high-value directions.

**Questions are prioritized by impact, effort, uncertainty, and urgency**, and the highest-value ones are those most likely to **change the decision**:

```
HIGH     Current regulatory status   ← would change the decision
MEDIUM   Competitor pricing
LOW      Company history
```

**Research efficiency follows from this**: effort goes to questions that reduce decision-relevant uncertainty. Exhaustively documenting something that cannot change the outcome is not thoroughness — it is cost with no information gain, and it crowds out the question that mattered.

---

## Knowledge to Execution

```
KNOW → UNDERSTAND → DECIDE → ACT → MEASURE
```

Research that ends at a conclusion has done half its job. Reports close with **next actions** (verify X, contact Y, compare Z, review on date) carrying priorities P0–P3, routed to tasks and calendar through `NLB-CPIOS-001` — **confirmed, never auto-created.**

**Knowledge reminders** (*"review this research in 30 days"*) and **knowledge triggers** compile onto `NLB-09`:

```
IF    regulatory status changes
THEN  notify · refresh research
```

**Thresholds** keep monitoring proportionate (*"alert me only if price moves more than 10%"*), and **noise control** groups related updates into one digest rather than firing separately:

```
TODAY'S INTELLIGENCE
🔴 1 critical   🟠 3 important   🟢 7 minor
```

Digest timing is the user's (morning / evening / weekly / manual), all knowledge events collect in one place with clear priority, and **quiet mode silences notifications without stopping the monitoring underneath** — so the watch stays intact and the digest is complete when the user returns.

---

## Search Transparency

**Search explains itself**: *"this surfaced because 7 documents mention the same company and 3 contain the relevant product."* An unexplained ranking cannot be corrected by the user, and a knowledge base the user cannot correct drifts.

**Semantic expansion is visible and defeatable.** Results separate into exact matches, semantic matches, and related entities, with **exact search available** for users who need literal terms. Expansion that silently substitutes a related term is how a search for one product returns confident results about another.

**Filters** span source type, date, owner, tag, project, confidence, file type, and entity, with natural-language filtering (*"documents from last year mentioning Brazil but not Mexico"*) and **saved searches** per `NLB-07`.

**Ranking** weighs relevance, recency, authority, source quality, and user context, and **the user can override it** (newest / most authoritative / most relevant). **Private sources never appear in shared search results** without permission — checked per result, not per query.

---

## Knowledge Home & Continuity

The knowledge home opens on work in progress: continue learning, continue reading, active research, open questions, recent decisions, and **knowledge needing review**.

A **knowledge session** carries topic, sources, questions, notes, actions, and conclusion, and ends with *"here is what we established today."* A later session **resumes from the previous conclusion, open questions, sources, and next actions.**

**The user should not have to re-explain a project that is already authorized and already known.** Re-establishing context is the tax that makes people stop using a research tool for the long investigations it is best at.

---

## Acceptance Criteria

Part 3 is architecturally complete when it supports: interface (natural-language command bar, contextual commands, ask/research/analyze/create/teach/review modes); workspace (reader with in-place AI, highlight-to-knowledge, annotations, document and multi-document chat, collections, reading assistant); reference (personal encyclopedia with last-verified dates and versioning, glossary with contextual definitions, entity/person/project/topic pages, graph navigation and filters); spaces (private/personal/project/team/public, temporary spaces, honest capability disclosure); team knowledge (roles, approval workflow, official designation, ownership and review cycles, needs-review state, private-memory separation); research studio (domain workspaces and persistent instructions, templates with variables, preserved output schemas, export, normalization with retained originals, confidence-scored merging, disambiguation, audit); analysis (comparison with visible evidence and explicit "not available", knowledge matrix, briefs with unknowns, question generation, decision-impact prioritization); execution (next actions with priorities, reminders, triggers, thresholds, digests, quiet mode); and search (explainability, exact vs semantic separation, filters, saved searches, permission-checked results, overridable ranking).

---

## Principle

**Search → Understand → Connect → Research → Verify → Learn → Decide → Act → Review.**

> The interface should feel like a library, a research laboratory, a teacher, an analyst, and an expert workspace in one place.

But the property that makes it trustworthy is smaller and less impressive than any of those: **at every point the user can see where a piece of knowledge came from, how good it is, and what is still missing.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-12 | Initial knowledge workspace specification, drawn from source Part 4 (source Part 3 has not been received; if it arrives, it will be added as a later part of this series rather than renumbering this one). Establishes the universal knowledge interface and six modes, the reader with highlight-to-knowledge and suggested-but-not-applied annotations, the personal encyclopedia with last-verified dates and article versioning, entity/person/project/topic pages as rendered graph traversal, knowledge access modes with honest capability disclosure, team knowledge with review cycles and the private-memory boundary, the research studio with templates and entity resolution that never silently merges, evidence-aware comparison with explicit "not available", decision-impact research prioritization, knowledge-to-execution triggers and digests, and search explainability with defeatable semantic expansion. Scoped explicitly against NLB-07, NLB-08, NLB-09, NLB-10, and NLB-NXOS-005. |

---

**End of Part 3 (Version 1.0)**
