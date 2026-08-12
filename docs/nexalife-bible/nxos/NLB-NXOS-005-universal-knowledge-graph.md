# 📖 NEXALIFE BIBLE — NXOS: Nexa Operating Layer

## Part 5 — Universal Knowledge Graph

| Field | Value |
| --- | --- |
| Document ID | NLB-NXOS-005 |
| Series | NXOS — Nexa Operating Layer (Volume 23) |
| Version | 1.1 |
| Status | Master Draft |
| Priority | ★★★★★ (Connected Data Architecture) |
| Supersedes | — |
| Last updated | 2026-08-12 |

---

## Purpose

Everything becomes connected: users, projects, goals, skills, notes, documents, emails, AI conversations, meetings, planners, habits, contacts, books, research, courses, health, finance, and travel all link together. **Nexa never searches folders. It searches knowledge.**

This is not a new data model. `NLB-07` already established One Source of Truth and a Relationship Model; `NLB-21` already named the Universal Life Graph that lets a marathon goal touch Health, Nutrition, Calendar, Finance, and Travel simultaneously. This volume gives that graph a formal structure — node types, edge types, and traversal rules — so "everything links together" is a specific, checkable architecture rather than a slogan.

---

## Node Types

Every entity in the Universal Data Platform (`NLB-07`) that can participate in the graph is one of these node types:

| Node type | Examples |
| --- | --- |
| Person | User, contact, mentor, collaborator |
| Goal | Any entry in the Goal Planner (`NLB-04`, PU-01-013) |
| Project | Research project, business project, creative project |
| Skill | A competency in a Learning Path (`NLB-SP-003`) or Career Roadmap |
| Content | Note, document, whiteboard, flashcard, email, AI conversation |
| Event | Meeting, calendar item, milestone |
| Planner | Any catalogued planner instance (`NLB-04`) |
| Habit | Entry in the Habit Tracker |
| Resource | Book, course, article, reference |
| Domain Object | Health record, financial account, travel booking — the domain-specific entities each Life Domain (`NLB-03`) contributes |

This list is not closed — new node types register the same way new entities register with the Universal Data Platform in `NLB-07`, which is what lets the graph grow as new domains and planners (`NLB-03` v1.1's LD-11–17, and any future domain) come online.

---

## Edge Types

Nodes connect through typed edges, not a single generic "related to" link — the edge type is what makes traversal meaningful rather than merely possible:

| Edge type | Meaning | Example |
| --- | --- | --- |
| Requires | A prerequisite relationship | Fractions → Algebra (`NLB-SP-003`'s Prerequisite Engine) |
| Contributes To | Progress on one feeds another | A completed course contributes to a Career goal |
| Scheduled In | Time-bound placement | A study session scheduled in the Calendar Hub |
| Owned By | Access and responsibility | A project owned by a user or team |
| Referenced By | Citation or mention | A note referenced by a research project |
| Blocks | A dependency that prevents progress | An incomplete task blocks a milestone |
| Participates In | Involvement without ownership | A mentor participates in a mentee's goal |
| Derived From | Provenance | An AI-generated summary derived from a document |

Edges carry the same versioning and audit guarantees as the nodes they connect, per `NLB-07`.

---

## Worked Traversal

**"What does the user need to do before their conference next month?"** is a graph query, not a search: start at the Event node (the conference), follow `Scheduled In` to the Calendar, follow `Requires` and `Blocks` to outstanding Travel, Finance, and Documents nodes, follow `Contributes To` back to any Career or Business goal the conference serves. The result is the same unified plan `NLB-11` and `NLB-NXOS-001` already describe conversationally — this volume is what makes it a graph traversal Nexa can actually execute rather than a pattern Nexa happens to recognize.

---

## Ranking & Relevance

When a traversal returns many connected nodes, relevance ranking favors recency, explicit user priority, proximity in the graph (fewer hops), and confidence in the edge itself (an AI-inferred `Derived From` edge ranks below a user-created `Owned By` edge). This mirrors `NLB-NXOS-003`'s Memory Ranking, applied to graph traversal rather than memory retrieval — the two share the same ranking philosophy because memories are themselves graph nodes.

---

## Permission-Aware Traversal

A traversal never crosses an edge the requester isn't authorized to see — `NLB-10`'s Permission Engine is checked at every hop, not only at the starting node. This is what keeps a shared Workspace's knowledge graph from leaking one member's private planner content to another simply because a query happened to traverse through it.

---

## Indexing & Search

The graph is indexed for both keyword and semantic search, feeding `NLB-08`'s Global Search and `NLB-NXOS-003`'s vector-search memory retrieval from the same underlying index — there is one search substrate, not a separate one per feature.

---

## Growth Without Redesign

New Life Domains (`NLB-03`), new planners (`NLB-04`), and new Marketplace assets (`NLB-13`) contribute new node and edge types without requiring the graph itself to be redesigned — the same extensibility discipline `NLB-05` requires of the Planner Engine, applied here to the data it connects.

---

## Temporal Edges

An edge is not necessarily true forever. Every relationship may carry a validity interval:

```
Person A ──WORKED_WITH──> Company B     valid 2024–2026
```

Without this, a graph answers *"who works with whom"* using facts that stopped being true, and the error is invisible because the edge looks identical either way. Temporal validity is also what lets `NLB-KROS-006`'s time-travel research reconstruct the graph **as it stood** at a past date rather than only as it stands now.

**Edges carry provenance and confidence** — the source that supports the relationship, and whether it is Confirmed / Strong / Probable / Possible / Unknown. An inferred edge is retained as an inference, never promoted to a confirmed one by repeated traversal.

---

## Path Finding

*"How are these two companies connected?"* is a path query, and **the answer is the chain, not the verdict**:

```
Company A → Person X → Organization B → Project C
```

Asserting "they are connected" without the path is unusable: the user cannot judge whether the connection is meaningful, and cannot spot the hop that is wrong. Path results carry the evidence for each edge, at the zoom level requested — high-level relationships, detailed relationships, or source evidence.

**A path is not a cause.** Where evidence does not establish causation, the connection is labelled correlation or hypothesis, per `NLB-KROS-008`'s evidence-bound causal edges — a rendered arrow is read as causation regardless of how the underlying edge was typed.

---

## Live, Stored & Historical Nodes

Three kinds of node value are kept distinguishable, because they age differently and mislead differently:

| Kind | Meaning |
| --- | --- |
| **Live** | Read from an authorized source at query time |
| **Stored** | Retrieved and retained; carries published / updated / retrieved / verified dates |
| **Historical** | Known to describe a past state |

A stored value presented as live is the most common graph error in practice. Nodes therefore surface freshness alongside the value and warn where it has aged past its configured requirement (`NLB-KROS-001`).

**Authorized live-source changes propagate**: source update → graph update → dependency check → affected workflows and subscribers, feeding `NLB-KROS-008`'s impact analysis.

---

## Design Principle

The measure of this graph is not how much it stores, but how directly a real question — "what do I need to do before X" — can be answered by walking it. **If a connection cannot be traversed to answer a real question, it is not doing its job, regardless of how complete the graph looks.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.1 | 2026-08-12 | Additive (MINOR): temporal edges with validity intervals (which is what lets NLB-KROS-006 reconstruct the graph as it stood at a past date), edge provenance and confidence with inferred edges never promoted by traversal, path finding that returns the chain and its evidence rather than a verdict and refuses to render correlation as causation, and the live/stored/historical node distinction with freshness surfaced and authorized live-source changes propagating into NLB-KROS-008's impact analysis. Drawn from the KROS source material and placed here because the graph is platform-level. |
| 1.0 | 2026-08-05 | Initial Universal Knowledge Graph specification. Formalizes NLB-07's Relationship Model and NLB-21's Universal Life Graph into explicit node types, edge types, permission-aware traversal, and a worked query example. |

---

**End of Part 5 (Version 1.0)**
