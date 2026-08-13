# 📖 NEXALIFE BIBLE — Autonomous Execution & Action Orchestration System (AEAOS)

## Part 6 — Scheduling Execution, File Operations & Interface Targeting

| Field | Value |
| --- | --- |
| Document ID | NLB-AEAOS-006 |
| Series | Autonomous Execution & Action Orchestration System (Volume 32) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-13 |
| Parent | `NLB-AEAOS-001` |
| Dependencies | `NLB-21` · `NLB-CPIOS-001` · `NLB-CPIOS-002` · `NLB-AEAOS-001` · `NLB-AEAOS-003` · `NLB-AEAOS-005` · `NLB-KROS-003` · `NLB-KROS-008` |

---

## Purpose

Three execution surfaces carry failure modes the general rules don't cover: **the calendar**, where an action changes commitments to other people; **files**, where an action is often irreversible and bulk; and **interfaces**, where the target of an action has to be identified before it can be acted on.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-21` (LOUPE) | Prioritization, daily planning, time blocking, routines, focus periods, and cross-planner scheduling intelligence. This part covers only the **execution** of calendar changes. |
| `NLB-CPIOS-001` | Calendar actions, conflict detection, smart scheduling, meeting coordination, date-ambiguity confirmation, and the Commitment and Waiting-For trackers. |
| `NLB-KROS-003` · `NLB-KROS-008` | Document Q&A and comparison, entity resolution, duplicate detection, structural document understanding, and semantic diff. |
| `NLB-AEAOS-003` | Interface state validation, human-verification handling, session isolation, file operations at the connector level. |
| `NLB-AEAOS-005` | Approval binding, ambiguity stopping execution, and substitution control — all of which apply below. |

---

## Scheduling Execution

A calendar change is unlike most execution: it frequently **alters other people's commitments**, which makes it outward-facing in the sense of `NLB-NIC-002`'s Representation Boundary even when it looks like an internal edit.

**Important commitments are never moved silently.** External meetings, medical appointments, legal dates, and anything the user has marked protected require authorization to reschedule — automatic optimization operates on flexible items only, and **schedule locks** let the user pin blocks that optimization may not touch.

**Rescheduling shows its blast radius before it acts**: old time, new time, affected events, affected tasks, and who gets notified. **Cascade protection** stops one change producing a chain of consequential downstream moves without the user seeing the chain — the calendar is where a single approved edit most easily becomes ten unapproved ones.

**Impossible schedules are reported, not silently accepted.** Where travel time exceeds the gap between commitments, that is a conflict: *"20 minutes available, estimated travel 35."*

### Honest capacity

**When the work does not fit the time, the system says so and asks what gives:**

> *"Five hours of work remain and three hours are available. Which should be deferred?"*

A scheduler that silently compresses estimates, or quietly drops the overflow, produces a plan that looks achievable and is not. Presenting the shortfall as the user's choice is the only honest handling, and it is the moment the plan is worth the most.

**Scheduling is not completion.** A task placed in a calendar block is scheduled; it becomes complete only on evidence, per `NLB-AEAOS-001`. **Nexa never marks work done because its time slot elapsed** — the fastest way to make a planning system untrustworthy is to let it report progress that did not happen.

**Availability is shared at minimum resolution.** Negotiating a meeting exposes free/busy, not event details, and private commitments stay private while still constraining the search (`NLB-CPIOS-002`'s minimum-necessary principle).

---

## File Operations

Files are where execution is most often **irreversible, bulk, and easy to get slightly wrong.**

**Destructive actions are gated and counted**: *"you are about to permanently delete 1,284 files."* Bulk deletion, permanent deletion, overwriting, and mass moves each carry confirmation proportional to scale (`NLB-CPIOS-002`), and **reorganizations preview their effect** — what moves where, how many, and to which destinations — before anything moves.

**Ambiguous targets stop execution.** *"Send the latest quotation"* against five plausible files is a question, not a guess (`NLB-AEAOS-005`). The wrong file sent to a client is fully authorized, fully verified, and completely wrong.

**Integrity is verified after transfer or transformation** — size, completeness, and hash where available. A partially-copied file that reports success is worse than a failed copy, because the failure is discovered later by whoever opens it.

**Sync conflicts are surfaced, never resolved by overwrite.** Where two devices changed the same file, both versions are presented with a named resolution — keep one, merge, or review — per `NLB-AEAOS-005`.

**Redaction is verified against the output, not the intent.** Applying a redaction is not the same as producing a file from which the hidden content cannot be recovered; the check is on the exported artifact, and **a redaction that survives only visually is a disclosure that has already happened** (`NLB-KROS-004`'s redaction preview covers what will be hidden; this covers whether it actually was).

**Document generation validates before producing**: required fields, formats, attachments, dates, identifiers — and quality-checks the result for missing values, broken references, and inconsistent figures. **Interpretations of legal, financial or regulatory documents are labelled as AI-generated and requiring verification**, per the regulated-adjacent posture in `NLB-NXOS-004`.

---

## Interface Targeting

Where an action goes through a rendered interface, **the target must be identified semantically before it is acted on.**

**Semantic targeting over coordinates**: button labels, accessibility labels, and DOM semantics identify a control; fixed screen positions do not. A layout change silently redirects a coordinate-based click to whatever now occupies that position, and the action still reports success.

**Visual interpretation is the fallback**, used where structured interface information is unavailable — not the default.

**Multiple candidate targets stop execution**: *"I found two 'Download' controls — which one?"* This is `NLB-AEAOS-005`'s ambiguity rule applied where it bites hardest, because the two candidates usually look identical to the system and obviously different to the user.

**Sensitive screen content is excluded from capture.** Passwords, authentication codes, private messages and financial details are not captured, and where they appear during an authorized capture, **capture pauses** rather than proceeding and redacting afterwards — the safest handling of a credential is never to have recorded it.

**Clipboard contents carrying secrets are restricted and expire**, rather than persisting for whatever reads them next.

---

## Acceptance Criteria

Part 6 is architecturally complete when it supports: scheduling execution (protected commitments requiring authorization to move, schedule locks excluded from optimization, rescheduling previews showing affected events and notified parties, cascade protection, impossible-schedule detection against travel time, honest capacity reporting that presents the shortfall as the user's choice, scheduling never treated as completion, and minimum-resolution availability sharing); file operations (scale-proportional destructive-action gates with counts, reorganization previews, ambiguous targets stopping execution, post-transfer integrity verification, sync conflicts surfaced with named resolution, redaction verified against the exported artifact, and document generation validated before production with regulated interpretations labelled); and interface targeting (semantic identification preferred over coordinates, visual interpretation as fallback only, multiple candidate targets stopping execution, sensitive content excluded from capture with capture pausing rather than post-redacting, and expiring restricted clipboard handling).

---

## Principle

**Identify the target, show the blast radius, verify the result.**

> The calendar changes other people's commitments, files rarely come back, and an interface that moved will accept a click meant for something else — and all three report success either way.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-13 | Initial scheduling, file and interface execution specification, drawn from source Volume 47 Parts 13, 15, 16 and 19. Establishes protected commitments and schedule locks, rescheduling previews with cascade protection, impossible-schedule detection, **honest capacity reporting** presenting the shortfall as the user's choice, and the rule that scheduling is never completion; destructive-action gates with counts and reorganization previews, ambiguous file targets stopping execution, post-transfer integrity verification, sync conflicts surfaced rather than overwritten, and **redaction verified against the exported artifact rather than the intent**; and semantic interface targeting preferred over coordinates, with capture pausing on sensitive content rather than redacting afterwards. Prioritization and planning remain with `NLB-21`, calendar actions and conflict detection with `NLB-CPIOS-001`, document understanding with `NLB-KROS-003`/`008`, and interface state validation with `NLB-AEAOS-003`. |

---

**End of Part 6 (Version 1.0)**

**END OF THE AUTONOMOUS EXECUTION & ACTION ORCHESTRATION SPECIFICATION**
