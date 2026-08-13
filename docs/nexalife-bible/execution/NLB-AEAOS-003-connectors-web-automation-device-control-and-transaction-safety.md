# 📖 NEXALIFE BIBLE — Autonomous Execution & Action Orchestration System (AEAOS)

## Part 3 — Connectors, Web Automation, Device Control & Transaction Safety

| Field | Value |
| --- | --- |
| Document ID | NLB-AEAOS-003 |
| Series | Autonomous Execution & Action Orchestration System (Volume 32) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-13 |
| Parent | `NLB-AEAOS-001` |
| Dependencies | `NLB-10` · `NLB-12` · `NLB-NIC-003` · `NLB-NIC-004` · `NLB-AEAOS-001` · `NLB-CPIOS-001` · `NLB-CPIOS-002` · `NLB-FWOS-001` |

---

## Purpose

Part 1 specified how an action is verified. Part 3 specifies **how it actually reaches the world** — through connectors, through browsers, through devices — and the safety properties each of those surfaces demands.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-12` | The connector architecture, integration model, and service authentication. |
| `NLB-NIC-004` v1.1 | The tool registry, capability-based routing, authorization-bounded fallback, tool health, tool call preview. |
| `NLB-CPIOS-001`/`002` | The unified inbox, the pre-send check (attachment, recipient, account, sensitive data), wrong-account warnings, scheduled send, bulk confirmation, the Personal Data Vault, sharing preview, and form leak warnings. |
| `NLB-NIC-003` | Device modes, cross-device handoff, ambient behaviour, offline experience. |
| `NLB-FWOS-001`/`002` | Money itself — accounts, budgets, transaction records, the detected-versus-confirmed distinction. |
| `NLB-AEAOS-001` | Idempotency, verification, receipts, limits, and intent preservation, all of which apply to everything below. |

---

## Connector State

A connector is not binary. Its state is **connected / healthy / degraded / expired / revoked / failed**, and the state is visible before a workflow depends on it.

**Expired authorization pauses rather than fails.** Auth expiry mid-workflow is a routine, recoverable condition: the run pauses, preserves state, and requests reauthentication — it does not report the task as failed, and it certainly does not report it as done.

**Missing capability is stated as a requirement**: *"I need access to your calendar to do this"* — a request, not a silent omission of the step.

**Revocation is surgical.** Disconnecting a service removes its access without deleting unrelated Nexa data, and users can see exactly what each integration can reach (`NLB-10`).

**Multiple accounts per service are first-class**, and account choice resolves from explicit configuration and task context. **Where the correct account is genuinely ambiguous on a consequential action, Nexa asks** — extending `NLB-CPIOS-001`'s wrong-account warning from email to every connected service. Acting from the wrong identity is not a formatting error; it is a message from a person who did not send it.

---

## Web Automation

Where a task must be done through a website, three rules govern it.

**API first.** Where a reliable authorized API exists, it is used in preference to driving the interface. UI automation is fragile by construction — it depends on layout that changes without notice — and a fragile path to a real-world side effect is the worst combination in this volume.

**State is validated before acting.** Before a click or a submit, the interface is confirmed to be in the expected state; if it changed unexpectedly, the run **pauses and reassesses** rather than continuing against an assumption. A confident click on an unrecognized page is how automation buys the wrong thing.

**Human verification is respected, never circumvented.** Where a site requires a CAPTCHA or other human check, **Nexa stops and asks the user to complete it.** Attempting to defeat it is out of scope regardless of technical feasibility: the check exists to establish that a person is present, and defeating it makes a false statement to the service on the user's behalf.

**Site rules are honoured** — authentication requirements, rate limits, access restrictions, and the service's own terms. Sessions are maintained where permitted and **isolated per site and per account**, so one session never carries another's authority.

Completion follows Part 1: **the resulting state is verified**, and *"reservation confirmed"* is said only when the confirmation actually arrived.

---

## Device and File Operations

**Device routing** selects by capability, availability, preference, security, and current state, and a workflow can hand off between devices without losing execution state (`NLB-NIC-003`).

**File operations** — find, create, rename, move, organize, copy, archive — with **deletion behind confirmation rules** and duplicate detection across filename, metadata, content similarity, and hashes.

Deletion and overwriting deserve the same treatment as any irreversible action in Part 1: labelled before execution, never inferred from a vaguely-worded request.

---

## Transaction Safety

Money and bookings are where every property in this series is tested at once.

**A transaction preview states the whole shape before execution:**

```
FROM · TO · AMOUNT · CURRENCY · PURPOSE
```

**Limits are user-set and binding** — maximum price, allowed merchants, categories, frequency — and function as hard constraints under `NLB-KROS-011`: a purchase exceeding them is not made and not approximated. **Where a purchase cannot be made within the limits, that is the answer**, not a near-miss executed on the user's behalf.

**Financial execution sits high on the risk ladder** (`NLB-NIC-002`) and carries stronger confirmation regardless of how routine it appears. **Actual transfers and payments always require explicit authorization**; preparation, comparison, and drafting do not.

**Purchases and reservations are idempotent or they are not attempted.** A retried booking that produces two reservations, or a retried payment that sends money twice, is the most damaging expression of the duplication problem — which is why Part 1's idempotency requirement is load-bearing precisely here.

**Reservation is complete only on the provider's confirmation.** Submitting a form is not a booking.

**Credentials are used, never displayed.** Secrets are injected into the surfaces that need them and appear in no output, receipt, log, or summary (`NLB-AEAOS-001`), and stored credentials are not revealed on request without explicit, appropriate authorization.

---

## Multi-Service Workflows

A single objective often crosses several services, each with its own state:

```
SERVICE A ✓   SERVICE B ✓   SERVICE C ✗
```

**Per-service state is tracked independently and reported exactly** — never collapsed into one failure. When a trip books the flight and hotel but the car fails, the user needs to know precisely that, because two of the three are now real commitments.

**Recovery is offered as options**: retry, alternative service, manual completion, rollback, or continue with the remainder. The choice belongs to the user, since each carries a different cost.

**A fallback service does not inherit the primary's authorization.** If the intended provider fails, an alternative is used only where it is *already* authorized for that action — the failure of one path is not a reason to widen permissions, and it is exactly the moment when widening them looks most reasonable.

---

## Acceptance Criteria

Part 3 is architecturally complete when it supports: connector state (six visible states, expiry pausing with preserved state and a reauthentication request, capability gaps stated as requirements, surgical revocation, multi-account handling with ambiguity resolved by asking on consequential actions); web automation (API preferred over UI, interface state validated before acting with pause-on-unexpected-change, human verification respected rather than circumvented, site rules and rate limits honoured, per-site and per-account session isolation, and verified completion); device and file operations (capability-based routing, state-preserving handoff, duplicate detection, and deletion behind confirmation); transaction safety (full transaction preview, binding user-set limits treated as hard constraints with no near-miss execution, explicit authorization for transfers and payments, idempotent purchases and reservations, completion only on provider confirmation, and credentials used but never displayed); and multi-service workflows (independent per-service state, exact partial reporting, user-chosen recovery options, and fallback services never inheriting the primary's authorization).

---

## Principle

**If Nexa is authorized to do it, it should orchestrate the work — not just explain how.**

> The authorization is the boundary, the verification is the proof, and neither is negotiable because a service happened to fail or a site happened to ask whether a human was present.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-13 | Initial connector, web and transaction specification, drawn from source Volume 47 Part 3. Establishes six connector states with expiry pausing rather than failing, multi-account ambiguity resolved by asking; web automation preferring APIs over UI, validating interface state before acting, **respecting human verification rather than circumventing it**, honouring site rules, and isolating sessions per site and account; device routing and file operations with confirmation-gated deletion; **transaction safety** — full preview, binding limits as hard constraints, explicit authorization for payments, idempotent purchases and reservations, completion only on provider confirmation, and credentials never displayed; and multi-service workflows with independent per-service state, exact partial reporting, and **fallback services never inheriting the primary's authorization**. Connector architecture remains with `NLB-12`, tool routing with `NLB-NIC-004`, send safety and the data vault with `NLB-CPIOS-001`/`002`, device modes with `NLB-NIC-003`, and money itself with `NLB-FWOS-001`/`002`. |

---

**End of Part 3 (Version 1.0)**
