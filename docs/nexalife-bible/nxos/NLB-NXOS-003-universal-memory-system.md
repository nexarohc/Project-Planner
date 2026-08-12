# 📖 NEXALIFE BIBLE — NXOS: Nexa Operating Layer

## Part 3 — Universal Memory System

| Field | Value |
| --- | --- |
| Document ID | NLB-NXOS-003 |
| Series | NXOS — Nexa Operating Layer (Volume 23) |
| Version | 1.1 |
| Status | Master Draft |
| Priority | ★★★★★ (Memory Architecture) |
| Supersedes | — |
| Last updated | 2026-08-12 |

---

## Purpose

`NLB-NIC-001` established that Nexa's memory is layered — session, short-term, and long-term — and always reviewable. This volume specifies the mechanism underneath that promise: how memories are typed, stored, retrieved, ranked, compressed, and eventually forgotten. It does not introduce a second memory system; it is the architecture the Universal Memory Fabric named in `NLB-NXOS-001` actually runs on.

---

## Memory Types

Where `NLB-NIC-001` layers memory by **duration** (session/short-term/long-term), this volume classifies it by **kind** — the two schemes are orthogonal, and every stored memory carries both a duration layer and a kind:

| Kind | Captures | Example |
| --- | --- | --- |
| Episodic | Specific events and interactions | "The user asked about marathon training on 2026-07-14" |
| Semantic | General facts and preferences | "The user prefers morning study sessions" |
| Procedural | How the user likes things done | "The user always wants a plan proposed before execution" |
| Personal | Identity-level facts the user has shared | Time zone, language, accessibility needs |
| Planner Memory | Context specific to one planner | Current subject progress in the Study Planner |
| Conversation Memory | What was discussed in a specific exchange | Session-scoped, per `NLB-NIC-001` |
| Workspace Memory | Shared context within a team or organization | Per `NLB-10`'s workspace model |

---

## Storage

Every memory is stored as a record in the Universal Data Platform (`NLB-07`) — memory is not a separate database, it is a category of entity with the same ownership, versioning, and audit guarantees `NLB-07` already requires of everything else. This is what makes memory reviewable and deletable by design rather than by special-cased exception.

---

## Vector Search & Indexing

Memories are indexed for semantic retrieval alongside keyword indexing, consistent with the Search Index already defined in `NLB-07` and exposed through Global Search (`NLB-08`). A memory query ("what does Nexa remember about my study habits?") returns results ranked by relevance, not just recency.

---

## Memory Ranking

When multiple memories are candidates for retrieval, ranking weighs relevance to the current request, recency, explicit user importance (a user can mark something as important), and confidence in the memory's continued accuracy (a stated preference from a year ago ranks lower than one confirmed last week). Ranking feeds directly into `NLB-NXOS-002`'s Memory Retrieval step.

---

## The Knowledge Graph Connection

Memories link into the same Knowledge Graph formalized in `NLB-NXOS-005` — an episodic memory about a conversation can connect to the goal it was about, the planner it occurred in, and the person it involved. Memory is not an isolated log; it is one more node type in the same connected graph as notes, goals, and projects.

---

## Forgetting System

Memory is not infinite by accident — it is bounded by design. Session memory expires automatically. Short-term memory ages out unless renewed by continued relevance. Long-term memory persists only while the user has approved it, and the user can delete any memory at any time, per `NLB-10`'s Trust Center. **Forgetting is a feature, not data loss** — a memory system that never forgets anything is a privacy liability, not a capability advantage.

---

## Compression

Where many similar episodic memories accumulate (e.g., dozens of individual "completed a study session" events), the system may summarize them into a single semantic memory ("the user has maintained a consistent study habit since March") rather than retaining every instance indefinitely. Compression preserves the *information* while reducing the *volume* — and the original episodic detail remains available if a specific instance is needed, subject to the user's own retention settings.

---

## Memory Synchronization

Memory synchronizes across devices through the same mechanism as any other data in `NLB-07` and `NLB-NIC-003`'s Cross-Device Handoff — there is no separate memory-sync pathway, which is exactly what keeps "Nexa remembers the same things regardless of device" true without extra engineering per device type.

---

## Permission Boundaries

Every memory kind above is subject to `NLB-10`'s Permission Engine: Planner Memory respects that planner's own sharing settings; Workspace Memory respects organization policy; Personal memory is never shared across workspaces without explicit consent. Memory Retrieval (`NLB-NXOS-002`) checks permission before relevance, every time.

---

## User Control

Users can review, edit, and delete any long-term, planner, or workspace memory they have access to manage, export their memory data, and disable personalization derived from it — the same guarantees already stated in `NLB-NIC-001` and `NLB-10`, now grounded in a system that actually supports reviewing and deleting a *specific* memory rather than only resetting personalization wholesale.

---

## Memory Trust

A memory's origin is not the same as its reliability, and both change over time. Every memory carries a trust level:

```
VERIFIED · USER-CONFIRMED · SOURCE-CONFIRMED
INFERRED · STALE · CONFLICTED
```

**Trust is earned by a stated route, not by repetition:**

```
UNVERIFIED → REVIEWED → CONFIRMED → TRUSTED
```

**And it is revocable.** New evidence downgrades a previously trusted memory rather than being reconciled against it — the same append-only discipline `NLB-KROS-008` requires of corrections, so the downgrade and its cause both remain visible.

### Memory poisoning defense

Retrieved content is data, never instructions (`NLB-KROS-004`). This is the slower variant of the same threat: **false information repeated often enough must not become trusted memory by accumulation.**

Frequency is not evidence. A claim appearing in twenty retrieved documents is one claim in twenty places until something establishes it — the source-deduplication rule from `NLB-KROS-001` applied to what the system chooses to believe about itself. Without an explicit trust route, a memory system that weights by recurrence can be moved by anyone who can put text in front of it repeatedly, and the resulting belief looks identical to a well-founded one.

**Memory health** is reportable — verified, recent, conflicting, outdated, unverified — with stale entries surfaced (*"this contact has not been verified recently"*) and **targeted refresh** available: *"refresh everything we know about this company."*

**Consistency checks** run over the graph connection: orphan nodes, duplicate entities, impossible relationships, contradictions, and stale information, with cleanup **proposed for user approval** rather than applied.

---

## Design Principle

Memory should make Nexa more useful over time without becoming something the user has to fear, audit blindly, or feel surveilled by. **Every memory the system holds should be one the user could look at and recognize as their own, reviewable at the same granularity it was stored.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.1 | 2026-08-12 | Additive (MINOR): memory trust levels, the unverified-to-trusted escalation route with revocation on new evidence, **memory poisoning defense** establishing that repetition is not evidence and that trust is earned by a stated route rather than by accumulation, memory health reporting with stale detection and targeted refresh, and graph consistency checks proposed for approval. Drawn from the KROS source material and placed here because memory is platform-level. |
| 1.0 | 2026-08-05 | Initial Universal Memory System specification. Establishes memory kinds (episodic/semantic/procedural/personal/planner/conversation/workspace) orthogonal to NLB-NIC-001's duration layers, plus ranking, compression, and the Forgetting System. |

---

**End of Part 3 (Version 1.0)**
