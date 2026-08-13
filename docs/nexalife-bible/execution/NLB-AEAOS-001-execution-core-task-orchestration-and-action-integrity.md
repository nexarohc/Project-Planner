# 📖 NEXALIFE BIBLE — Autonomous Execution & Action Orchestration System (AEAOS)

## Part 1 — Execution Core, Task Orchestration & Action Integrity

| Field | Value |
| --- | --- |
| Document ID | NLB-AEAOS-001 |
| Series | Autonomous Execution & Action Orchestration System (Volume 32) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-13 |
| Dependencies | `NLB-09` · `NLB-10` · `NLB-12` · `NLB-NIC-002` · `NLB-NXOS-004` · `NLB-NIC-004` · `NLB-KROS-004` · `NLB-CPIOS-002` |

---

## Purpose

`NLB-NIC-002` establishes **that** Nexa acts, the lifecycle an action follows, and the autonomy under which it is permitted. AEAOS specifies the **runtime**: what happens between "approved" and "done", and — the part that decides whether any of this can be trusted — **how the system knows an action actually succeeded.**

> Nexa should distinguish between *thinking about doing something* and *actually doing something.* Only verified execution qualifies as completion.

### Scope boundaries

This series does not re-derive the action model. It specifies the execution layer beneath it.

| Already owned by | Covers |
| --- | --- |
| `NLB-NIC-002` v1.2 | The Action Lifecycle, action types, approval checkpoints, action history, recovery discipline, **the Autonomy Ladder** (six levels, delegation contracts, quotas, pause conditions, action risk classification, no dark autonomy, stop controls), and the **Representation Boundary**. All are applied here, never redefined. |
| `NLB-09` · `NLB-NXOS-006` | Triggers, conditions, the rule notation, the visual workflow builder, approval flows, error handling, workflow history. Execution plans compile onto these. |
| `NLB-CPIOS-002` | Rule simulation and dry run, versioning, rollback, audit logging. |
| `NLB-KROS-004` | The research pipeline planner, task graphs, parallel execution, dependency management, and declared cost budgets. This part generalizes them from research to action. |
| `NLB-NIC-004` v1.1 | The tool registry, capability-based routing, authorization-bounded fallback, tool health. |
| `NLB-10` · `NLB-12` | The Permission Engine and the connector architecture every authorization check resolves against. |

---

## The Execution Graph

An objective becomes a graph, not a list:

```
OBJECTIVE → UNDERSTAND → PLAN → AUTHORIZE
          → EXECUTE → VERIFY → REPORT
```

Every workflow instance carries tasks, dependencies, current state, required permissions, outputs, errors, and recovery paths. **Independent branches run concurrently; dependent tasks wait for information rather than proceeding on assumptions** (`NLB-KROS-004`).

**Task states are more granular than success and failure**, and the distinction matters more than it looks:

| Terminal | Transitional |
| --- | --- |
| Completed · Failed · Cancelled | Created · Planned · Ready · Running · Paused |
| | **Blocked** · **Waiting** |

**Waiting is not failing.** *Waiting for user*, *waiting for an external event*, and *waiting for approval* are healthy states with a known resolution; reporting them as failures teaches users to ignore failure reports, and reporting a real failure as "waiting" hides it indefinitely. A blocked task always names **what is blocking it, why, and what would unblock it.**

**Dependencies are inferred, not assumed** — a hotel cannot be booked before travel dates are confirmed — and the planner determines what runs in parallel, what must be sequential, and what needs verification before the next stage begins.

---

## Action Integrity

The four properties that separate an execution engine from a system that merely emits requests.

### Idempotency

**Repeated execution of the same instruction must not produce repeated effects.** A retried workflow does not create five identical calendar events, send the same email twice, or place a second order.

This is the single most consequential requirement in the volume. Retry is the standard response to failure, network calls fail ambiguously by nature — a timeout tells you the response was lost, never whether the action happened — and without idempotency every recovery mechanism in this series becomes a duplication mechanism.

**Duplicate detection runs before creation or sending**, independently of retry: the same message about to go to the same recipient, an event matching one that already exists.

### Verified completion

**Nexa never reports "done" without evidence that it is.** Verification draws on the API response, the resulting application state, a confirmation page, device state, a returned document, or explicit user confirmation — and a **reservation is complete only when the booking system confirms it**, not when the form was submitted.

A false success is worse than a clean failure by a wide margin. A failure is visible and recoverable in the moment; a false success is discovered when someone arrives at a hotel with no booking.

### Exact partial state

When five actions were required and the fourth failed:

```
A ✓   B ✓   C ✓   D ✗   E not executed
```

**The report states precisely that**, never "the workflow failed." The user's next move depends entirely on which parts already happened, and a generic failure forces them to check every one by hand — the exact work the automation was meant to remove.

**Transactional grouping** applies where the underlying services support it, so a multi-part change either lands or does not. Where they do not, the partial state is reported rather than papered over.

### Reversibility, stated in advance

Actions are labelled **undo available / partially reversible / cannot be undone** before execution, per `NLB-NIC-002`'s risk classification. An irreversible action carries that warning at the point of approval, not in the receipt.

---

## Execution Receipts

Every significant action produces a structured record:

```
REQUEST · ACTION · SERVICE · ACCOUNT · AUTHORIZATION
TIMESTAMP · RESULT · VERIFICATION · REFERENCE
```

Receipts make *"what did Nexa actually do?"* answerable without inference, and they chain back through plan and authorization to the original request (`NLB-NIC-002`'s audit trail).

**Where no authorized tool can safely perform a task, Nexa says so** — it does not report the task as complete, and it does not substitute a different action that was not asked for. *"I can't do this because…"* is a valid outcome; a quiet substitution is not.

---

## Intent Preservation

The failure mode specific to capable execution systems.

**Scope is fixed at authorization** — goal, tools, data, time window, permitted actions — and **execution that requires anything outside it pauses, explains, and asks.**

> *"Find hotels"* must not become *"book a hotel, cancel the existing reservation, update the calendar, and message everyone."*

Each of those steps is individually defensible as helpful. Together they are a different task than the one authorized, and the user discovers it after the fact. **Drift detection** watches for actions diverging from the stated objective and stops to reassess rather than continuing on momentum.

**Autonomy never escalates silently.** A workflow authorized at one level does not move to a higher one because the higher level would be more convenient (`NLB-NIC-002`).

---

## Failure and Recovery

```
FAILURE → DIAGNOSE → RECOVER → RETRY → VERIFY
```

**Retries change strategy rather than repeating** (`NLB-KROS-013`), and retry policy accounts for error type, **retry safety**, maximum attempts, delay, and **duplication risk** — with exponential backoff for transient external failures. An action that is not safe to retry is not retried; it is escalated.

**Escalation is bounded**: retry → fallback → notify the user. Silent indefinite retrying is the behaviour that burns budget and hides problems.

### Limits

Every workflow carries limits, because an execution engine without them fails expensively:

```
MAX COST · MAX TOOL CALLS · MAX EXECUTION TIME
MAX ACTIONS · MAX MESSAGES · MAX FILES
```

**Loops always have bounds.** An unbounded loop in a system with real-world side effects is not a performance problem; it is an incident.

**Expected cost is estimated before expensive execution**, and exceeding a limit **pauses and asks** rather than stopping dead or continuing regardless (`NLB-KROS-004`).

---

## User Control

The control surface for a running workflow: **pause, resume, stop, cancel, retry, modify, approve** — plus the global stop from `NLB-NIC-002`.

The semantics matter as much as the buttons:

| Control | Behaviour |
| --- | --- |
| **Pause** | No new actions start; workflow state is preserved intact |
| **Resume** | Continues **from the last verified state** — never replaying completed actions |
| **Cancel** | Stops pending actions, blocks new ones, preserves history, **names what already completed**, and attempts rollback where appropriate |

**Resume that replays is worse than no resume**, because it converts an interruption into duplicated side effects — which is why resume depends on verification having recorded what actually finished.

**The user can always interrupt**, within technical limits, and the state after an interruption is reported plainly.

---

## Observability

Active tasks, tool calls, failures, latency, and resource usage are visible while running — *"waiting on flight search, 2 of 7 steps complete"* rather than an opaque delay.

**Notifications are reserved for what needs a person**: important failures, required approvals, completed high-value actions, unexpected changes, critical blockers. **Low-risk approved work executes silently and is logged** — an execution engine that narrates every step is one users stop reading.

**Credentials stay isolated.** Passwords, tokens, and API keys are used without being displayed in ordinary output, and never appear in receipts, logs, or summaries.

---

## Acceptance Criteria

Part 1 is architecturally complete when it supports: the execution graph (tasks with dependencies, permissions, outputs, errors and recovery paths; inferred prerequisites; parallel and sequential execution; blocked and waiting states distinguished from failure with named blockers); action integrity (idempotent execution, pre-action duplicate detection, verified completion against a named verification source, exact partial-state reporting, transactional grouping where supported, and reversibility labelled before execution); execution receipts chaining to authorization and request, with an explicit no-capable-tool outcome; intent preservation (scope fixed at authorization, pause-explain-ask on scope expansion, drift detection, and no silent autonomy escalation); failure and recovery (strategy-changing retries accounting for retry safety and duplication risk, backoff, bounded escalation, and mandatory limits on cost, calls, time, actions and loop iterations with pause-and-ask on breach); user control (pause preserving state, resume from last verified state without replay, cancellation reporting what already completed, and always-available interruption); and observability (live task and resource visibility, notifications reserved for what needs a person, silent logged execution of low-risk work, and credential isolation from all output).

---

## Principle

**Intent → Plan → Authorize → Orchestrate → Execute → Verify → Recover → Report.**

> An execution engine is only as trustworthy as its verification layer. Everything else in this volume assumes the system can tell the difference between an action it attempted and an action that happened.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-13 | Initial execution runtime specification, drawn from source Volume 47 Part 1. Establishes the execution graph with waiting and blocked distinguished from failure; **action integrity** — idempotency, pre-action duplicate detection, verified completion against a named source, and exact partial-state reporting; execution receipts and the explicit no-capable-tool outcome; **intent preservation** with scope fixed at authorization and drift detection; bounded failure escalation with retry-safety and duplication risk; mandatory execution limits; and pause/resume/cancel semantics where resume continues from the last verified state rather than replaying. The Action Lifecycle, Autonomy Ladder and Representation Boundary remain with `NLB-NIC-002`; triggers and workflow mechanics with `NLB-09`; simulation, versioning and rollback with `NLB-CPIOS-002`; task graphs and budgets with `NLB-KROS-004`; tool routing with `NLB-NIC-004`. |

---

**End of Part 1 (Version 1.0)**
