# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 6 — Temporal Knowledge, Context Assembly, Answer Modes & Multi-Model Verification

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-006 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-06` · `NLB-NIC-003` · `NLB-NXOS-002` · `NLB-NXOS-003` · `NLB-NXOS-005` · `NLB-KROS-001` · `NLB-KROS-004` |

---

## Purpose

Part 6 covers four things the earlier parts assumed but never specified: **what the user knew at a past moment**, **how context is assembled before it reaches a model**, **how strictly an answer must be evidenced**, and **what happens when models disagree**.

### Scope boundaries

This part is deliberately narrow. Its source material covered a great deal of ground the Bible already owns:

| Already owned by | Covers |
| --- | --- |
| `NLB-NIC-003` | Cross-device handoff and continuity, ambient assistance, device-appropriate interaction, offline behaviour, universal notifications, screen and file context. KROS knowledge simply travels on it. |
| `NLB-NIC-002` | The action lifecycle, approval checkpoints, action history, recovery, and reversibility labelling. |
| `NLB-10` | Application and device permissions, the permission centre, temporary grants, and permission explanation. |
| `NLB-NXOS-003` | Memory types, confidence, importance, retention, expiration, the memory inspector, and ephemeral context. |
| `NLB-NXOS-005` | The knowledge graph — node types, edge types, traversal, graph queries. |
| `NLB-06` | Model routing, fallback, and model governance. Multi-model *verification* below is a research-specific application of it. |
| `NLB-07` | Sync, conflict resolution, backup, recovery, and portability. |
| `NLB-KROS-001` · `NLB-KROS-004` | Knowledge decay, refresh, change detection, source ranking, agent identity and logs, the governance dashboard. |

What follows is only what none of those establish.

---

## Temporal Knowledge

The most significant gap this part closes. Every earlier volume treats knowledge as a current state; this one treats it as a state **that had a history**.

**Temporal reasoning** means answering *"what was true when we made this decision?"* — not applying today's information to a decision made a year ago. Judging a past decision by present knowledge is the most common form of unfair hindsight, and a system that stores only current values makes it unavoidable.

**Historical snapshots** preserve the knowledge state at a point in time:

```
AS OF          June 2025
KNOWN          …
DECISION       …
SOURCES        …
```

**Time-travel research** — *"what did we know about this company six months ago?"* — reconstructs that state from the research snapshots (`NLB-KROS-001`) and article versions (`NLB-KROS-003`) already retained. This is why those two features record versions rather than overwriting: without them, the reconstruction is impossible.

**Decision context reconstruction** answers *"why did I choose this supplier?"* by linking the original research, the criteria, the alternatives considered, the decision, and the outcome — the retrieval face of decision memory.

**Counterfactual review** answers the harder question: *"would I have made the same decision with today's information?"* Comparing the historical and current knowledge states separates **a bad decision** from **a good decision that met bad luck**. Those two require opposite corrections, and conflating them is how people learn the wrong lesson from an outcome.

### Timelines and causality

Subjects carry timelines assembled from events extracted from authorized documents, with relationships between them:

```
EVENT A → caused → EVENT B → resulted in → EVENT C
```

**A causal edge is only drawn where evidence supports causation.** Sequence is not cause, and a timeline renders adjacency so persuasively that an unjustified arrow becomes an accepted fact almost immediately. Where the relationship is unestablished, the events remain merely ordered.

---

## Context Assembly

What reaches the model is a decision, and it should be a made one:

```
ALL KNOWLEDGE → RELEVANCE FILTER → TASK CONTEXT → MODEL
```

Selection weighs current task, recency, importance, relationship, explicit user instruction, and source quality. **More context is not better context** — irrelevant material degrades an answer and expands the exposure surface described in `NLB-KROS-004`'s minimization rules.

**Context is explained on request**: *"I used these five sources because they were most relevant."* An answer whose inputs cannot be enumerated cannot be corrected when it is wrong.

### Resolving conflicting sources

When sources disagree, the ordering is **authority → directness → recency → evidence → context** — deliberately *not* "newest wins." Recency is a factor, not a tiebreaker: a recent secondary article does not outrank an older primary record, and defaulting to the newest source is how a system quietly replaces good evidence with fresh evidence.

### Source requirements

Users state requirements (*"use at least three independent sources"*) and **Nexa reports whether the requirement was met** rather than silently returning what it found. Independence is judged after the deduplication rule in `NLB-KROS-001` — three reprints of one release are one source.

**Source diversity** is maintained where category monoculture would distort the answer.

**Failure is declared, not absorbed**: *"the requested primary source could not be accessed — continue with secondary sources?"* A research run that silently downgrades its own evidence standard produces a result the user believes is better-founded than it is.

---

## Answer Modes

The same question warrants different answers depending on what it will be used for. Beyond `NLB-KROS-003`'s task modes, two are **strictness settings** the user can impose:

| Mode | Behaviour |
| --- | --- |
| **"I don't know" mode** | Never guess. Where a claim cannot be established, return Unknown. |
| **Evidence-first mode** | Every material factual claim carries supporting evidence or is not made. |

Both exist because the correct trade-off is not universal: a professional preparing a regulatory submission and a person exploring an idea want opposite defaults, and neither should have to police the output manually.

**Confidence is expressed without false precision.** High / Moderate / Low / Unknown, and a confidence bar **never implies a calibrated probability unless the methodology actually produces one** — a rendered "80%" is read as a measurement no matter how it was derived.

**Presentation modes** — executive (answer, risks, action, source) and expert (methodology, assumptions, evidence, conflicts, analysis, conclusion) — change what is shown, never what was found.

**Mode transitions are confirmed where they cross into consequence**: *"this moves from research into execution. Continue?"* The boundary between investigating something and doing something is the one place an assistant must never cross on inference.

---

## Agent Runtime Safety

`NLB-KROS-004` established agent identity, permissions, and logs. This is what governs them while running.

**Observability at two depths**: most users see *"researching — 4 of 12 steps complete"*; expert view exposes the full workflow graph, tools in use, status, and errors. **Cost is visible** where external processing is charged, estimated before and actual after.

**Timeouts** bound every long-running agent. **Loop protection** is the one that matters most:

```
Repeated operation detected — workflow stopped for review.
```

An agent repeating an operation is not making progress, and without detection it consumes budget indefinitely while appearing busy. Stopping for review is correct; retrying more cleverly is not.

**Escalation** routes unresolved uncertainty to the user rather than resolving it by assumption — and in organizations, to an authorized **knowledge reviewer** (review / approve / reject / correct / archive) per `NLB-KROS-004`'s governance layer.

**Integration health is surfaced, and degradation is graceful**: *"calendar access is unavailable — scheduling actions are paused."* Knowledge work continues on what remains available; actions requiring a live service wait rather than failing silently or proceeding partially.

---

## Multi-Model Verification

For critical questions, outputs from multiple models can be compared, with a verifier reconciling them:

```
MODEL A · MODEL B · MODEL C → VERIFIER → FINAL
```

**Disagreement is reported, not averaged**: *"the models disagree on this point — here is the evidence."* Averaging two incompatible answers produces a third that no reasoning supports.

**No model authority.** A model's confidence does not override evidence. This is the sharpest statement of the principle running through the whole series — confidence is a property of the speaker, evidence is a property of the world, and only one of them is a reason to believe something. An ensemble that agrees is agreement among models, which is weaker than it feels: models trained on overlapping data share their errors the same way fifteen sites reprinting one press release share theirs.

---

## Acceptance Criteria

Part 6 is architecturally complete when it supports: temporal knowledge (reasoning about what was known when, historical snapshots, reconstructable past knowledge states, decision context reconstruction, counterfactual review, timelines with evidence-bound causal edges); context assembly (relevance filtering before the model, context explanation, conflict resolution ordered by authority before recency, source requirements reported against, diversity maintenance, declared source failure); answer modes ("I don't know" and evidence-first strictness settings, confidence without false precision, executive and expert presentation, confirmed research-to-execution transitions); agent runtime safety (two-depth observability, cost visibility, timeouts, loop detection with stop-for-review, escalation to user and knowledge reviewer, integration health with graceful degradation); and multi-model verification (ensemble comparison, reported disagreement, and no model authority over evidence).

---

## Principle

**Know what was known, choose what is relevant, state how sure, and never let confidence stand in for evidence.**

> A system that cannot reconstruct what it used to believe cannot help the user learn from what they used to decide.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-12 | Initial temporal knowledge and context assembly specification, drawn from source Part 7. Establishes temporal reasoning and historical knowledge snapshots, time-travel research, decision context reconstruction and counterfactual review, evidence-bound causal edges on timelines, the relevance filter and context explanation, source-conflict ordering that refuses "newest wins", reported source requirements and declared source failure, "I don't know" and evidence-first strictness modes, confidence without false precision, confirmed research-to-execution transitions, agent timeouts and loop detection, graceful integration degradation, and multi-model verification with reported disagreement and no model authority over evidence. The source part's cross-device, ambient, permission, memory, graph, model-routing and sync material is not restated — it is owned by NLB-NIC-003, NLB-NIC-002, NLB-10, NLB-NXOS-003, NLB-NXOS-005, NLB-06 and NLB-07 respectively. |

---

**End of Part 6 (Version 1.0)**
