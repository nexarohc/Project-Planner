# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 9 — Context Hierarchy, Scoped Instructions, Context Snapshots & The Personal Context API

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-009 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-07` · `NLB-10` · `NLB-12` · `NLB-21` · `NLB-NIC-003` · `NLB-NXOS-003` · `NLB-KROS-006` · `NLB-KROS-008` · `NLB-CPIOS-002` |

---

## Purpose

Part 6 specified how context is **assembled** for a single task. Part 9 specifies how context is **governed** across many: which layer wins when two instructions conflict, how long an instruction lasts, how a past run's context is reconstructed, and what a third-party application may ask for.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-KROS-006` | The relevance filter, context explanation, and source-conflict ordering for a single task. |
| `NLB-CPIOS-002` | Minimum-necessary-context as the default, context preview with **visible exclusions**, and agent isolation between work and personal. This part generalizes those to projects and applications. |
| `NLB-NIC-003` | Cross-device continuity, handoff, and device-appropriate output. |
| `NLB-NXOS-003` | Memory kinds, importance, retention, expiration, review, and resurfacing. |
| `NLB-KROS-004`/`008` | Memory correction and forget scoping; downstream impact analysis; the one-time-feedback boundary. |
| `NLB-21` | Task dependencies, blockers, and cross-planner prioritization. **Contextual priority** below is the input this part adds. |
| `NLB-10` · `NLB-12` | Identity, the Permission Engine, and the connector architecture the Context API resolves against. |

---

## The Context Hierarchy

Context is layered, and the layers are ranked:

```
1  Current message
2  Current conversation
3  Current task
4  Current project
5  Recent activity
6  Long-term memory
7  General knowledge
```

**A higher layer is never silently overridden by a lower one.** A long-term preference does not quietly outrank what the user just said — and the failure this prevents is the one users find most maddening, because the system appears to ignore explicit instruction in favour of something it inferred months ago.

### Authority when instructions conflict

```
CURRENT USER INSTRUCTION
  → AUTHORIZED PROJECT / ORGANIZATION POLICY
    → USER PREFERENCE
      → GENERAL DEFAULT
```

Subject always to safety and system constraints, which sit outside this ordering entirely.

**Personal preference and organizational policy are distinct kinds**, not two entries on one list. A user's preferred tone is theirs to set; an organization's approved-source rule is not theirs to override, and collapsing the two makes the second unenforceable (`NLB-KROS-005`'s policy engine).

**Collisions are detected before acting where the outcome differs materially** — a conflict discovered after the work is a conflict discovered too late.

---

## Scoped and Expiring Instructions

Every contextual instruction carries a scope:

```
MESSAGE · CONVERSATION · TASK · PROJECT · WORKSPACE · USER · ORGANIZATION
```

*"For this project, use a formal tone"* applies to that project and ends with it. *"Remember this until Friday"* stops being active context on Friday, rather than lingering as a preference nobody remembers setting.

**Context decays.** Yesterday's temporary instruction does not become a standing preference by surviving the night — the same boundary `NLB-KROS-008` draws for one-time feedback, applied to instructions rather than corrections.

**Context is explained on demand**: *"why did you use this format?"* → *"because you configured it for this project."* An unexplained behaviour is one the user can only work around, never fix.

**A context inspector** shows what influenced an answer *and what did not*, per `NLB-CPIOS-002` — the exclusions are what make the report checkable.

---

## Context Modes

**Fresh start** runs a conversation with no long-term personal memory — current conversation only. This matters more than it looks: without it, a user who wants an unbiased read on something has no way to get one, because every answer is shaped by accumulated context they cannot fully see.

**Project mode** loads that project's documents, instructions, memory, tasks, and decisions. **Workspace mode** adds organizational policy, brand rules, approved sources, terminology, and security requirements.

**Context templates** package a recurring setup — *"my research context"*: preferred sources, depth, output format, citation style, verification requirements — activated by name.

**Layers stack** where compatible: personal + project + task + temporary instruction, resolved by the authority ordering above.

---

## Project Isolation

```
PROJECT A  ╳  PROJECT B
```

**A private project does not leak into another.** Cross-project use requires an explicit **context bridge** — *"use the methodology from Project A for Project B"* — authorized, and carrying only what the user named. This is `NLB-CPIOS-002`'s agent isolation generalized: the default is separation, and combination is a deliberate act.

**Project disambiguation is asked, not guessed.** Where a topic exists in three projects and the signals are weak: *"which project should I associate this with?"* Filing work under the wrong project is quiet and compounding — the error is invisible until someone looks for the work where it should have been.

---

## Situational Awareness

Beyond individual facts, Nexa tracks the state of things: who, what, when, where, why, status, next action.

**Task states** — not started, in progress, **blocked**, waiting, completed, cancelled — with **blocker detection**: *"this cannot progress because approval is still pending."* A task sitting idle for a recoverable reason is the most common form of silent project failure.

**Contextual priority** is the useful consequence: **a task that looks low-priority alone can be the highest-priority thing the user could do, because three others wait on it.** Priority computed per-task rather than across the dependency graph systematically mis-ranks exactly the work that unblocks everything else. This feeds `NLB-21`'s prioritization rather than replacing it.

**References resolve against context** — *"that report"*, *"the supplier we discussed"*, *"the meeting from last Tuesday"*, and pronouns generally. **Where ambiguity remains, Nexa asks rather than guessing**, and **relative dates are confirmed when a mistake would be consequential**: *"you said Friday — do you mean August 14?"* (`NLB-CPIOS-001`). Timezone follows the relevant event or location, not the device.

---

## Context Snapshots

Before a complex workflow, the context is captured: task, project, goals, constraints, data sources, permissions, deadlines.

**Snapshots make a past run reconstructable** — which is what allows a workflow to be debugged, audited, reproduced, and learned from. Without it, *"why did it do that?"* is unanswerable, because the inputs no longer exist in the form the system saw them.

**Context is versioned with a change log** — *"project deadline moved from September 10 to September 18"* — and **diffed on request**: *"what changed since yesterday?"*

This is the same discipline as `NLB-KROS-008`'s append-only correction history and `NLB-KROS-006`'s historical knowledge snapshots, applied to the situation rather than the knowledge. All three exist so that a past state can be recovered rather than inferred.

---

## Uncertainty and Assumptions

**Context confidence** is tracked as High / Moderate / Low / Ambiguous, and low confidence resolves one of two ways **according to the risk of the task**:

| Risk | Response |
| --- | --- |
| Low | **Safe assumption, disclosed**: *"I'll assume the latest version, since it's the active project document."* |
| High | **Clarification first** |

Disclosure is what makes the assumption safe. An undisclosed assumption is indistinguishable from a fact in the output, and it is the reader — often later, often someone else — who pays for the difference.

**Assumptions are logged** (assumption, reason, confidence, impact) into `NLB-KROS-005`'s register, and **high-impact assumptions are confirmed before proceeding**.

---

## Memory in Context

Retrieval weighs semantic relevance, temporal relevance, project relevance, importance, confidence, and recency, and **recall explains itself**: *"you chose this approach before, on this project."*

Recalled memory carries origin, date, scope, confidence, and confirmation status (`NLB-NXOS-003`).

**Supersession preserves history**: new information supersedes old, and **the old remains available for historical reference** rather than being erased — the requirement `NLB-KROS-006`'s temporal reasoning depends on.

**Conflicting memories are surfaced, not silently resolved**: *"I have two records — the newer says X, the older says Y."*

**No silent personalization.** Nexa does not convert conversation into permanent memory on its own initiative; recurring patterns are *proposed* — *"this looks like a recurring preference — save it?"* — and a **memory review centre** lets the user edit, delete, expire, or promote what is held.

---

## The Personal Context API

Authorized applications can request context through a controlled interface — the significant new surface in this part, and the one with the largest failure potential.

**Capabilities are separately granted:**

```
READ BASIC CONTEXT · READ PROJECT CONTEXT
READ MEMORY · WRITE MEMORY · TRIGGER WORKFLOW
```

**Responses are filtered to the request.** An application asking *"what is the user's preferred report format?"* receives that answer — **not the memory graph it was drawn from.** Over-return is the defining API privacy failure: it is invisible to the user, convenient for the developer, and permanent once the data has left.

**Access is audited** (*"App X accessed Project Y context at 10:42"*), **revocable immediately**, and **expiring by default** — a permission granted once for one purpose should not still be live a year later because nobody revisited it.

**Consent states four things**: what is accessed, why, for how long, and who receives it. A consent screen that answers only the first is a notification, not a consent.

---

## Acceptance Criteria

Part 9 is architecturally complete when it supports: the context hierarchy (seven ranked layers, higher never silently overridden, explicit authority ordering, personal preference and organizational policy as distinct kinds, collision detection before acting); scoped instructions (seven scopes, expiry, decay, explanation on demand, an inspector showing exclusions); modes (fresh start without long-term memory, project mode, workspace mode, named context templates, compatible stacking); isolation (default project separation, authorized context bridges carrying only what was named, asked-not-guessed disambiguation); situational awareness (task states with blocker detection, contextual priority computed across the dependency graph, reference and pronoun resolution that asks when ambiguous, confirmed relative dates, event-correct timezones); snapshots (captured pre-workflow context, reconstructable past runs, versioning, change log, diff); uncertainty (tracked context confidence, risk-proportionate safe assumption with mandatory disclosure, logged assumptions, confirmation of high-impact ones); memory in context (explained recall with provenance, history-preserving supersession, surfaced conflicts, no silent personalization, a review centre); and the Personal Context API (separately granted capabilities, responses filtered to the request, audited access, immediate revocation, expiring grants, and consent stating what, why, how long, and who).

---

## Principle

**Understand the situation, use only what the task requires, and never let inferred context outrank what the user just said.**

> More context is not better intelligence. **Relevant context beats maximum context** — and minimum necessary data, explicit authorization, and user control are what keep the difference honest.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-12 | Initial context governance specification, drawn from source Part 11. Establishes the seven-layer context hierarchy with explicit authority ordering and personal preference held distinct from organizational policy, scoped and expiring instructions with context decay, fresh-start/project/workspace modes and named context templates, default project isolation with authorized context bridges, blocker detection and contextual priority computed across the dependency graph, context snapshots making past runs reconstructable and diffable, context confidence with risk-proportionate safe assumptions that must be disclosed, history-preserving memory supersession with surfaced conflicts and no silent personalization, and the Personal Context API with separately granted capabilities, request-filtered responses, audit, immediate revocation, expiring grants, and four-part consent. Single-task context assembly remains with `NLB-KROS-006`, cross-device continuity with `NLB-NIC-003`, memory mechanics with `NLB-NXOS-003`, and task prioritization with `NLB-21`. |

---

**End of Part 9 (Version 1.0)**
