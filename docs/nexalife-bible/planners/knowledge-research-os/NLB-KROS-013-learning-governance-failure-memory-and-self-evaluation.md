# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 13 — Learning Governance, Failure Memory, Self-Evaluation & Derived-Data Protection

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-013 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.1 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-06` · `NLB-09` · `NLB-10` · `NLB-NIC-002` · `NLB-KROS-004` · `NLB-KROS-005` · `NLB-KROS-007` · `NLB-KROS-008` · `NLB-KROS-011` |

---

## Purpose

`NLB-KROS-004` established that Nexa may improve itself and that it may not modify its own safety boundaries. Part 13 specifies the **governance around that**: what a learned behaviour is made of, how failures are remembered so they are not repeated, how output is checked before delivery, and what protects a conclusion assembled from sensitive parts.

> Nexa should become more useful over time **without becoming less controllable.**

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-KROS-004` | Bounded self-improvement, feedback categories, learning from failure at the workflow level, evaluation and regression testing before deployment, and the prohibition on autonomous modification of safety boundaries. |
| `NLB-KROS-008` | The personalization boundary — one-time feedback never auto-promoted, persistent preferences confirmed not inferred, scoped corrections. |
| `NLB-KROS-007` | Preference confidence by origin (explicit / repeated / inferred) and scoped override. |
| `NLB-NIC-002` v1.1 | The Autonomy Ladder, delegation contracts, action risk classification, stop controls. The source material restates these; they are not redefined here. |
| `NLB-KROS-005` · `NLB-KROS-011` | Steelman and red-team reasoning; prediction calibration and error measurement. |
| `NLB-06` | Model routing and fallback. What this part adds is **learning from measured routing performance**, not a second router. |

---

## Anatomy of a Learned Behaviour

Nothing is learned anonymously. Every learned preference, rule, or workflow change carries:

```
SCOPE · PROVENANCE · VERSION · CONFIDENCE
APPROVAL STATUS · EXPIRATION
```

**Scope** is one of task, project, workspace, or user — and **a project-specific lesson stays with the project unless explicitly promoted.** Promotion from project lesson to organizational procedure is a deliberate act with a version attached (`NLB-KROS-004`), and demotion is equally explicit: active → outdated → archived.

**Preferences decay.** A preference that stops appearing loses confidence rather than persisting indefinitely, and is **reconfirmed rather than silently retired**: *"you previously preferred detailed reports — still?"*

**The current explicit request always wins** for the current task. A learned default is a default, not a constraint.

### Controls

A **learning dashboard** shows what has been learned and in what scope. Users can approve, edit, disable, or delete any of it; **"do not learn" mode** disables personalization for a session or task; and **reset is scoped** — resetting Project A leaves Project B untouched. Learned configuration is **exportable and importable**, per `NLB-KROS-004`'s portability guarantee.

**Learning is auditable**: what changed, why, from what source, when, and who approved it. **Rollback restores the previous behaviour** — the same guarantee `NLB-CPIOS-002` requires of automation rules, applied to what the system has taught itself.

---

## Correction Reconciliation

The sharpest new distinction in this part.

A user correcting a **preference** is authoritative — it is their preference. A user correcting an **external fact** is a claim, and it meets the evidence rather than overwriting it:

```
USER CLAIM  +  EXTERNAL EVIDENCE  →  RECONCILIATION
```

*"The company is a manufacturer, not a distributor"* corrects the current result immediately and **updates the stored classification only where the evidence supports it** — otherwise both are held, with their sources, as the conflicting record `NLB-KROS-001` requires.

**A system that lets any assertion overwrite verified evidence has no verification layer**, only a delay before the user's belief becomes the record. Corrections therefore carry their own provenance: correction, source, date, scope, confidence.

**Repeated dissatisfaction triggers investigation, not adjustment.** A system that keeps changing behaviour in response to negative feedback without diagnosing it will walk through the option space and land somewhere arbitrary — the user is dissatisfied for a reason, and the reason is the thing worth finding. Positive feedback likewise strengthens confidence in a workflow without ever overriding a later explicit instruction.

> **Learning is not truth.** A repeated user preference does not make a factual claim true, and a frequently-used model assumption never becomes evidence.

---

## Failure Memory

**Failures are classified** — data, tool, reasoning, permission, user input, external, system — because the right response differs entirely by class, and an undifferentiated "it failed" produces the same useless retry every time.

**Retries change strategy.** Attempt → failure → **diagnose** → strategy change → attempt. Repeating an identical failed action is not a retry; it is the same action, and it consumes budget while producing the same outcome (`NLB-KROS-006`'s loop protection).

**Known failures are remembered and surfaced before repetition**:

> *"This approach failed previously because the required data was unavailable. Try a different method?"*

This is the most immediately valuable mechanism here. Without it, a system re-attempts the same doomed approach indefinitely, each time in good faith — the user is the only component that remembers, which defeats the point of automating the work.

**Error taxonomy and trend** — factual, logical, temporal, contextual, calculation, source, execution, communication — with error rate tracked per measurable workflow and **recurring patterns surfaced**. A rising rate in one category is a diagnosable defect; an aggregate rate is not.

**Plans are versioned and diffable** alongside the context that produced them (`NLB-KROS-009`): plan v1 → new information → impact analysis → plan v2, with *"what changed in the plan?"* answerable.

---

## Self-Evaluation Before Delivery

`NLB-KROS-004` specifies peer review by a second process for research reports. This applies a lighter version to ordinary output.

```
DRAFT → CRITIQUE → CORRECTION → FINAL
```

**Self-critique checks the output against itself**: unsupported claims, missing requirements, contradictions, logical gaps, and unmet formatting constraints. Most delivered errors are visible in the draft to anyone who reads it as a critic rather than as its author.

**Adversarial review** asks the question that actually finds problems: *"what is the strongest reason this conclusion could be wrong?"* — and for high-value work, **red-team mode** runs a challenger analysis against the primary one before synthesis (`NLB-KROS-005`).

**Alternative hypotheses are considered before committing.** A conclusion reached without any competitor having been entertained is a first guess that survived unchallenged.

**Success criteria are set before complex work begins**: *"what would count as success here?"* Defining it afterwards means defining it around what was produced.

**Optimization is multi-metric.** Quality, speed, cost, and reliability are traded against each other explicitly, because improving one while quietly destroying another is the classic failure of any system that learns against a single measure.

---

## Routing That Learns

`NLB-06` owns model routing. What is added here is that **routing improves from measured performance**: task type → performance history → best route, benchmarked on accuracy, latency, cost, reliability, and user-reported quality.

**Routing explains itself** on request: *"routed to the reasoning model because this required multi-step analysis."* Cost-aware routing keeps trivial work off expensive paths, latency-aware routing serves urgent interactions where quality remains acceptable, and the user can override with **quality-first** at any time.

---

## Confidence Before Autonomous Action

Under `NLB-NIC-002`'s ladder, a workflow may be authorized to act. This is the runtime check on each act:

```
INTENT CONFIDENCE + PERMISSION CONFIDENCE + EXECUTION CONFIDENCE
```

**Below threshold, Nexa asks** — and where it cannot ask, the fallback is chosen by risk: do nothing, prepare a draft, or escalate. **The safe fallback is never "proceed anyway."**

**Repeated approval is not authorization.** A user approving the same action twenty times has approved it twenty times; converting that into standing permission is a grant the system awarded itself, and it is precisely the drift the delegation contract exists to prevent.

---

## Experimental Learning

New strategies are tested without replacing established behaviour:

**A/B workflow comparison** on measurable outcomes, inside a **learning sandbox isolated from production**, with guardrails stating scope, success criteria, maximum risk, and rollback mechanism before the experiment starts.

An experiment without a pre-declared rollback is not an experiment — it is a change with optimistic framing.

---

## Derived-Data Protection

**A conclusion inherits the sensitivity of what produced it.** Where a sensitive finding is assembled from several individually-permitted pieces, it is **not treated as unrestricted merely because it is newly generated.**

This is the aggregation problem, and it is easy to get wrong in exactly the systems this volume describes: each input passes its own permission check, the synthesis passes none, and a conclusion no single source would have permitted becomes freely readable. Learned information follows the authorization model of the data it came from (`NLB-KROS-004`, `NLB-10`).

---

## Governance Over Optimization

> **Optimize within boundaries — never optimize away the boundaries.**

Nexa may propose improvements to workflows it observes failing — *"this step repeatedly requires manual correction; I can validate the field before execution"* — as a structured proposal: problem, observed pattern, proposed change, expected benefit, risk, approval.

**It may not modify permissions, safety boundaries, or governance rules because doing so would improve a metric.** Any sufficiently capable optimizer will find that the constraints are what is costing it performance; the rule exists precisely because that reasoning will be correct and must still be refused.

**Personalization that materially changes behaviour is visible**, and *"why did you do that?"* is always answerable: *"because you approved this workflow for this project."*

---

## Acceptance Criteria

Part 13 is architecturally complete when it supports: learned-behaviour anatomy (scope, provenance, version, confidence, approval status, expiration; project lessons held to their project until explicitly promoted; preference decay with reconfirmation; current explicit requests overriding learned defaults; a learning dashboard with approve/edit/disable/delete, do-not-learn mode, scoped reset, portability, audit trail and rollback); correction reconciliation (preference corrections authoritative, factual corrections reconciled against evidence rather than overwriting it, correction provenance, and the learning-is-not-truth rule); failure memory (failure classification, strategy-changing retries, known failures surfaced before repetition, error taxonomy with per-category trend and rate, versioned and diffable plans); self-evaluation (draft-critique-correct passes, self-critique against unsupported claims and unmet requirements, adversarial review, red-team mode for high-value work, alternative hypotheses before commitment, success criteria set in advance, multi-metric optimization); routing that learns (benchmarked performance history, explained routing, cost- and latency-aware paths, user quality-first override); action confidence (intent, permission and execution confidence with a threshold that escalates, risk-chosen safe fallbacks that never default to proceeding, and repeated approval never becoming standing authorization); experimental learning (A/B comparison, sandbox isolation, pre-declared guardrails and rollback); derived-data protection (conclusions inheriting the sensitivity of their inputs); and governance over optimization (structured improvement proposals, and an absolute prohibition on optimizing away permissions, safety boundaries or governance rules).

---

## Principle

**Observe → Understand → Act → Measure → Critique → Learn → Improve.**

The system may learn preferences, workflows, and strategies. **Permissions, safety boundaries, and governance stay explicitly controlled** — and validated learning is always worth more than frequent learning.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.1 | 2026-08-12 | Additive (MINOR): repeated negative feedback triggers investigation rather than blind behavioural adjustment, and positive feedback strengthens workflow confidence without overriding later explicit instruction. |
| 1.0 | 2026-08-12 | Initial learning governance specification, drawn from source Part 15. Establishes the six-field anatomy of a learned behaviour with scoped promotion, preference decay and reconfirmation, learning dashboard/reset/rollback/audit; **correction reconciliation** distinguishing authoritative preference corrections from factual claims that must meet the evidence, with the learning-is-not-truth rule; failure memory with classification, strategy-changing retries and known-failure surfacing before repetition; self-evaluation with draft-critique passes, adversarial review, alternative hypotheses and pre-set success criteria; routing that learns from benchmarked performance (`NLB-06` still owns routing itself); action confidence thresholds with risk-chosen safe fallbacks and the rule that repeated approval never becomes standing authorization; sandboxed A/B experimentation with pre-declared rollback; **derived-data protection** against the aggregation problem, where a conclusion assembled from individually-permitted parts would otherwise become unrestricted; and governance over optimization. The autonomy ladder, feedback categories and bounded self-improvement are not redefined — they remain with `NLB-NIC-002` and `NLB-KROS-004`. |

---

**End of Part 13 (Version 1.1)**

**END OF THE KNOWLEDGE, RESEARCH & PERSONAL INTELLIGENCE OPERATING SYSTEM SPECIFICATION**
