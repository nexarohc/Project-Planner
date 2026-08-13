# 📖 NEXALIFE BIBLE — Autonomous Execution & Action Orchestration System (AEAOS)

## Part 5 — Authorization Binding, Uncertain State & Substitution Control

| Field | Value |
| --- | --- |
| Document ID | NLB-AEAOS-005 |
| Series | Autonomous Execution & Action Orchestration System (Volume 32) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-13 |
| Parent | `NLB-AEAOS-001` |
| Dependencies | `NLB-10` · `NLB-NIC-002` · `NLB-NIC-003` · `NLB-AEAOS-001` · `NLB-AEAOS-003` · `NLB-FWOS-001` · `NLB-CPIOS-002` |

---

## Purpose

Part 1 established that an action must be verified before it is reported. Part 5 covers the three gaps that remain around it: **what an approval actually authorizes**, **what happens when the outcome is genuinely unknown**, and **what stops a system substituting something adjacent to what was approved.**

Every transactional domain — payments, bookings, purchases — fails in the same three places, which is why this is specified once here rather than per-domain.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-NIC-002` v1.2 | The Autonomy Ladder, delegation contracts, action risk classification, no dark autonomy, stop controls, the Representation Boundary. |
| `NLB-AEAOS-001` | Idempotency, verification, execution receipts, partial state, limits, intent preservation. |
| `NLB-AEAOS-003` | Connector states, web and device automation, transaction previews, binding purchase limits, provider-confirmed completion. |
| `NLB-CPIOS-002` | Pre-send checks, the Personal Data Vault, sharing preview, bulk confirmation. |
| `NLB-FWOS-001`/`002` | Money itself — accounts, budgets, transaction records, financial modelling. |
| `NLB-NIC-003` | Device modes, handoff, offline behaviour. |

---

## Approval Binding

An approval is not a mood. It attaches to specifics:

```
ACTION · TARGET · PARAMETERS · ACCOUNT · TIME
```

**A material change to any of them invalidates the approval.** If the price moves, the recipient changes, the date shifts, or the account differs from the one approved, the action returns for re-authorization rather than proceeding on the earlier consent.

**Old approvals never authorize new actions.** This is the replay problem, and it is how a system ends up doing something the user genuinely did agree to — just not to *this* instance of it. An approval that survives its parameters has become a standing permission nobody granted.

**Approvals expire.** An unbounded approval is one the user has stopped thinking about, and consent given for a situation stops meaning anything once the situation has moved on.

### Permission tiers are separate

Access and authority are different grants, and collapsing them is the most common permission error in this domain:

| Read | Act |
| --- | --- |
| View balance, view transactions | Create, approve, execute a payment |
| Search products, compare | Add to cart, place order, pay |
| Search availability, compare | Reserve, book, purchase |

> **Seeing money is not permission to move money.** Reading a calendar is not permission to change it, and searching for a hotel is not permission to book one.

**Destination changes are their own permission.** Modifying a beneficiary, payment destination, or delivery address is not an ordinary edit — it is the step that converts an authorized action into one that benefits someone else, and it carries confirmation independent of the transaction it enables. **A new destination is flagged as new** rather than treated as routine.

**Where an organization separates duties**, the identity preparing an action and the identity approving it are distinct, per `NLB-10`.

---

## Uncertain State

Part 1 requires that Nexa never report success without evidence. This specifies what it reports when evidence has not arrived.

**Unknown is a first-class terminal-pending state**, distinct from both success and failure:

```
SUBMITTED → UNKNOWN → verified success
                    → verified failure
```

> *"I submitted the request, but completion has not been confirmed."*

Neither *"done"* nor *"it failed"* is honest here, and both are actively harmful: the first leaves the user believing they have a booking; the second invites a retry that may duplicate a transaction that actually succeeded. **Unknown is the state where idempotency earns its place** (`NLB-AEAOS-001`), because it is precisely when a retry is most tempting and most dangerous.

**Unknown states are reconciled, not left standing.** The system re-checks and updates to verified success or verified failure when the provider's state becomes readable, and the receipt is amended with the resolution.

### The state ladder

Transactional domains have intermediate states that are routinely conflated:

```
SEARCH RESULT → OPTION SELECTED → SUBMITTED
              → PAYMENT AUTHORIZED → PROVIDER CONFIRMED
```

**These are five different facts.** A search result is not a booking, a submitted form is not a purchase, and an authorized payment is not a confirmed reservation. Reporting an earlier state in the language of a later one is the single most damaging thing an execution engine can do, because the user stops arranging the thing they now believe is arranged.

**Partial results are reported per component**, per Part 1: a trip where the flight confirmed and the hotel did not is reported exactly that way, because two of those are now real commitments and one is not.

---

## Substitution Control

**Nexa never silently changes what was approved.** Not the product, variant, seller, provider, price, delivery address, date, or conditions.

Substitution is the failure that feels most helpful in the moment. The approved item is unavailable, something close exists, and proceeding looks like initiative — but the user authorized a specific thing, and a near-match is a different thing they have not agreed to. **The correct response is to present alternatives and stop.**

**Exact identity is checked before acting.** *Model A*, *Model A Pro*, and *Model A 256GB* are different products; two suppliers with similar names are different suppliers (`NLB-KROS-012`). **Where parameters have drifted since approval, standing rules do not fire**:

> *"The variant differs from the one you approved. Purchase not executed."*

**A provider failure is not authorization for a substitute.** When the intended provider fails, an alternative is used only where it was already authorized — the same rule as `NLB-AEAOS-003`'s fallback, and it holds hardest under time pressure, which is exactly when the substitution looks most justified.

**Ambiguity stops execution.** Where five files, three contacts, or two "download" controls could be the intended target, Nexa asks rather than picking (`NLB-AEAOS-003`). Acting on the most likely candidate is right most of the time, and the residual is an action taken against the wrong target with full authorization behind it.

---

## Device Trust and Deferred Actions

**Devices are not equally private**, and trust is per-device: personal, trusted, shared, public, restricted. On a shared device, sensitive notifications are reduced, private information is not displayed, and sensitive actions carry additional authentication (`NLB-NIC-003`).

**Queued offline actions are re-validated before execution, never simply replayed on reconnect.** A purchase queued at one price, a booking queued against one availability, a message queued against one recipient — each may have gone stale while disconnected, and **a consequential queued action whose parameters no longer hold is surfaced rather than executed.** This is approval binding applied across a gap in time rather than a change in parameters.

**Scheduled actions get the same treatment**: a send scheduled five days ago is checked for stale content and changed recipients before it goes (`NLB-CPIOS-002`).

**Cross-device state conflicts are resolved by a named rule** — latest, user-confirmed, or a designated source of truth — never by silent overwrite.

---

## Acceptance Criteria

Part 5 is architecturally complete when it supports: approval binding (approval attached to action, target, parameters, account and time; material change invalidating it; no replay of old approvals onto new actions; expiry; separated read and act permission tiers; destination changes as an independent permission with new destinations flagged; and separation of duties where an organization requires it); uncertain state (Unknown as a first-class state distinct from success and failure, honest reporting of unconfirmed submissions, reconciliation to a verified outcome with an amended receipt, the five-state transactional ladder kept distinct, and per-component partial reporting); substitution control (no silent change to product, variant, seller, provider, price, address, date or conditions; exact identity checking; standing rules that do not fire on drifted parameters; provider failure never authorizing a substitute; and ambiguity stopping execution); and deferred actions (per-device trust levels with shared-device restrictions, re-validation of queued offline actions rather than replay, stale-check on scheduled actions, and named-rule conflict resolution).

---

## Principle

**Capability does not equal authority — and authority is bound to specifics.**

> An approval that outlives its parameters, a submission reported as a confirmation, and a substitution made in good faith are three different ways of doing something the user never agreed to. Each looks like helpfulness at the moment it happens.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-13 | Initial authorization binding specification, drawn from source Volume 47 Parts 8, 9, 11, 18, 20 and 21. Establishes **approval binding** to action, target, parameters, account and time with invalidation on material change and no replay onto new actions; separated read and act permission tiers with destination changes as an independent permission; **Unknown as a first-class action state** with reconciliation to a verified outcome, and the five-state transactional ladder distinguishing a search result from a provider confirmation; **substitution control** prohibiting silent change to any approved parameter, with exact identity checking, standing rules that do not fire on drift, and ambiguity stopping execution; and deferred actions with per-device trust levels, re-validation of queued offline actions, and stale-checked scheduled sends. Money remains with `NLB-FWOS-001`/`002`, the transaction surface with `NLB-AEAOS-003`, send safety with `NLB-CPIOS-002`, and the Autonomy Ladder with `NLB-NIC-002`. |

---

**End of Part 5 (Version 1.0)**
