# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 10 — Project, Goal, Decision & Risk Intelligence

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-010 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-21` · `NLB-NXOS-005` · `NLB-KROS-001` · `NLB-KROS-005` · `NLB-KROS-007` · `NLB-KROS-008` · `NLB-KROS-009` · `NLB-CPIOS-001` · `NLB-RSOS-001` |

---

## Purpose

The knowledge graph (`NLB-NXOS-005`) says how things connect. Part 10 specifies the four structures a knowledge system needs to be **useful about work in progress**: what state a project is actually in, whether goals still align with what is being done, how a decision and its assumptions stay linked, and how a risk in one place reaches another.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-NXOS-005` v1.1 | Node and edge types, temporal edges, path finding, live/stored/historical values, permission-aware traversal. The graph shapes below are views over it, not new graphs. |
| `NLB-CPIOS-001` | The **Commitment Centre**, Follow-Up Centre, and Waiting-For Tracker. Open loops below draw on those rather than duplicating them. |
| `NLB-RSOS-001`/`002` | The People Graph, relationship context, interaction history, and relationship-side commitments. |
| `NLB-KROS-001` | Decision memory with reasoning and assumptions, source ranking, freshness. |
| `NLB-KROS-005`/`007` | Assumption registers, scenarios, the risk register with trend, reversibility analysis, pre- and post-mortems. |
| `NLB-KROS-008`/`009` | Impact analysis on source change; context hierarchy, blockers, contextual priority. |
| `NLB-21` | Cross-planner prioritization and daily planning. |

---

## Project Intelligence

A project view assembles goals, people, documents, tasks, decisions, risks, deadlines, and outcomes from the graph rather than storing them a second time.

**Project health is a state with a reason attached:**

| State | |
| --- | --- |
| On track · At risk · Blocked · Overdue · Completed | |

> *"At risk, because two critical tasks are overdue and the required approval is still pending."*

**The explanation is the feature; the label is only the index into it.** A health score without its reasoning cannot be argued with, cannot be acted on, and gets ignored the first time it disagrees with what the user can see — which is why this is never presented as an unquestionable number.

**Open loops** are surfaced across the project — pending replies, unfinished tasks, awaiting approvals, unresolved decisions, upcoming deadlines — drawing on `NLB-CPIOS-001`'s trackers.

**The next action is the deliverable, not the status.** A project view that reports state without producing *"reply to the supplier with the requested specification"* has described the problem and left the work. Where no action is possible, **the blocker is named**: *"waiting for the quotation."* Naming the blocker is what converts an idle project from a mystery into a decision.

**Ambiguous commitments are checked rather than assumed**: *"should I treat this as a commitment, or as a possibility?"* — the same candidate-not-fact discipline `NLB-CPIOS-001` applies to extracted commitments.

---

## Goal Intelligence

Goals connect down to milestones, tasks, actions, and outcomes, and Nexa tracks which work actually feeds which goal.

**Progress counts outcomes, not checkboxes.** Tasks completed is a measure of activity; a goal can be fully "on schedule" by that measure while nothing that matters has moved. Progress is reported against meaningful completed outcomes, in the descriptive-metrics tradition the Bible holds throughout.

**Goal conflict detection** surfaces incompatibility rather than letting it play out — Goal A requires reducing spend on a resource Goal B requires increasing (extending the conflict detection in `NLB-HOS-005`). Resource conflicts span time, money, people, equipment, attention (`NLB-KROS-007`), and dependencies.

**Goal drift** is the quieter failure: current activity diverging steadily from a stated goal without any decision to abandon it. Nobody notices, because each individual week looks reasonable. Detecting drift makes the divergence a choice — continue, re-scope, or drop the goal — rather than something discovered a quarter later.

**Periodic review** runs goal → progress → obstacles → changes → next action.

---

## Decision Intelligence

A decision is stored as a structure, not a line in a log:

```
QUESTION → OPTIONS → EVIDENCE → TRADE-OFFS
         → DECISION → OWNER → EXPECTED OUTCOME
```

with date, alternatives considered, and **assumptions** — the record `NLB-KROS-001`'s decision memory defines, now linked into the graph so it can be reached from the project, the people, and the evidence.

**Reversibility classification** — reversible / partially reversible / hard to reverse / irreversible — **sets how much confirmation Nexa seeks**, per `NLB-KROS-007`. It is the single most useful property of a decision and the one most often unrecorded.

### Assumption monitoring

```
DECISION
├── ASSUMPTION A
├── ASSUMPTION B
└── ASSUMPTION C
```

**When an assumption changes, the decisions resting on it are surfaced**: *"the assumption behind this decision has changed."*

This is `NLB-KROS-008`'s impact analysis applied to reasoning rather than to sources, and it closes the same gap from the other side. A decision made on a premise that has since failed is not visibly wrong — it looks exactly like a decision that is still sound, until the consequences arrive.

**Decision review** compares expectation against observation once enough time has passed: *"you decided this expecting X; the observed result was Y."*

### Bias checks

For consequential decisions, Nexa can surface missing evidence, confirmation-bias risk, overconfidence, unexamined assumptions, and alternative explanations.

**These are checks against the reasoning, never diagnoses of the person.** *"The evidence gathered so far all supports the preferred option — would you like a search for disconfirming evidence?"* is useful. *"You are exhibiting confirmation bias"* is a judgment the system is not entitled to make and that users correctly resent, and it destroys the willingness to run the check at all.

---

## Risk Intelligence

Risks attach to projects and decisions with cause, probability, impact, owner, and mitigation (`NLB-KROS-007`'s register), and **propagate along the graph**:

```
SUPPLIER DELAY → PRODUCT DELAY → CUSTOMER COMMITMENT → REVENUE RISK
```

**One risk reaching several projects is the case worth building for.** Risks assessed per project systematically understate shared exposure — the supplier appears as a moderate risk in four places rather than the serious concentrated risk it actually is.

**Early warning distinguishes a signal from a confirmed problem**: *"three recent events are consistent with the risk pattern you identified"* — a pattern match to verify, not an established fact (`NLB-KROS-007`).

---

## Domain Graph Views

Specialist research produces recurring shapes, each a view over the same graph with **source provenance retained on every external fact** (`NLB-NXOS-005`):

| View | Shape |
| --- | --- |
| **Organization** | People · products · documents · contracts · projects · events · timeline |
| **Competitive** | Company → products, markets, customers, competitors, suppliers, regulators |
| **Supply chain** | Raw material → manufacturer → distributor → customer → market |
| **Product** | Manufacturer · composition · regulatory status · markets · customers · documents |
| **Regulatory** | Product → country → regulator → registration → manufacturer → documents |

**Supply-chain risk indicators are observable, not inferred**: single-source dependency, delivery delays, capacity constraints, regulatory change. **Single-source dependency is the one worth naming explicitly** — it is visible in the graph structure itself, and it is the risk organizations most reliably fail to see until it fires.

---

## Alerts That Are Worth Receiving

Change detection produces volume; this is what makes it survivable.

**Significance is classified** — low / medium / high / critical — against configured rules and observable impact. Not every change is an alert.

**Deduplication before notification**: ten sources reporting one development produce **one** alert stating that ten sources report it — the source-deduplication rule from `NLB-KROS-001` applied to notification. Ten identical alerts do not convey ten times the confidence; they convey that the alerting is broken.

**Correlation groups related events** into a single item rather than a scattered set the user has to reassemble.

**Every significant alert answers five questions**:

```
WHAT CHANGED · WHY IT MATTERS · SOURCE · WHEN · WHAT YOU CAN DO
```

*"A project deadline moved forward three days; two dependent tasks are now at risk"* — with review, reschedule, and notify offered. An alert without the last two fields is an interruption rather than information, and users learn to dismiss those faster than they learn to act on them.

---

## Life and Work Domains

```
PERSONAL          WORK              SHARED
Goals             Projects          Calendar
Learning          Contacts          Documents
Planning          Tasks             Preferences
Knowledge         Business
```

**Personal information does not become available to work contexts automatically**, and crossing requires an explicit bridge — `NLB-KROS-009`'s project isolation applied to the largest boundary most people have.

**The life operating map** — goals → projects → commitments → tasks → outcomes — and the **attention map** show where authorized workload is concentrated. Both are **based on observable workload**, and neither infers anything about how the user feels about it.

---

## Acceptance Criteria

Part 10 is architecturally complete when it supports: project intelligence (assembled project views, health states that always carry their explanation, surfaced open loops, a produced next action, named blockers, checked-not-assumed commitments); goal intelligence (goal-to-outcome linkage, progress counted in outcomes rather than completed tasks, goal and resource conflict detection, goal drift detection, periodic review); decision intelligence (structured decision records linked into the graph, reversibility classification driving confirmation strength, assumption monitoring that surfaces decisions when a premise changes, decision review against expectation, and bias checks framed against the reasoning rather than the person); risk intelligence (registers with cause, probability, impact, owner and mitigation, propagation along the graph, cross-project concentration made visible, and early warnings distinguished from confirmed problems); domain graph views (organization, competitive, supply-chain, product and regulatory shapes with retained provenance and observable single-source dependency); alerts (significance classification, deduplication before notification, correlation, and the five-field alert); and domain boundaries (personal and work separated by default, explicit bridges, observable-workload maps).

---

## Principle

**Memory → Knowledge → Graph → Context → Decision → Action → Outcome → Learning.**

> Understand not only individual facts, but how people, projects, goals, decisions, commitments and outcomes connect **across time**.

The test is narrow: given a project, can the system say what state it is in, why, what is blocking it, and what the single next action is — with the evidence for each?

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-12 | Initial project, goal, decision and risk intelligence specification, drawn from source Part 12. Establishes explainable project health, produced next actions and named blockers, goal progress counted in outcomes rather than completed tasks, goal drift detection, structured decision records with reversibility driving confirmation strength, **assumption monitoring that surfaces decisions when a premise changes** (impact analysis applied to reasoning rather than sources), bias checks framed against the reasoning and never as diagnoses of the person, risk propagation with cross-project concentration made visible, domain graph views with retained provenance and observable single-source dependency, and alert significance classification with deduplication, correlation and the five-field alert. Graph mechanics — temporal edges, path finding, live/stored/historical values — were promoted to `NLB-NXOS-005` v1.1; commitments and waiting-for remain with `NLB-CPIOS-001`, the People Graph with `NLB-RSOS-001`, and prioritization with `NLB-21`. |

---

**End of Part 10 (Version 1.0)**

**END OF THE KNOWLEDGE, RESEARCH & PERSONAL INTELLIGENCE OPERATING SYSTEM SPECIFICATION**
