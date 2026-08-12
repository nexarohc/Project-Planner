# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 14 — Reasoning Validation, Competing Hypotheses & Option Generation

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-014 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-KROS-001` · `NLB-KROS-005` · `NLB-KROS-006` · `NLB-KROS-008` · `NLB-KROS-010` · `NLB-KROS-011` |

---

## Purpose

The series has specified how evidence is gathered, weighed, and turned into decisions. Part 14 covers the checks **on the reasoning itself** — whether the arithmetic holds, whether the sequence is possible, whether a rival explanation was ever entertained — and how options are generated before any of them is scored.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-KROS-005` | Argument maps and their structural checks, steelman and dialectic modes, the assumption register and stress test, scenarios and sensitivity analysis, decision trees, the policy engine. |
| `NLB-KROS-011` | Decision matrices, weighting and robustness, hard and soft constraints, opportunity cost, value of information, forecast ranges and calibration. |
| `NLB-KROS-010` | Decision records with reversibility, assumption monitoring, risk propagation, bottlenecks and dependencies. |
| `NLB-KROS-006` | Reasoning explained without exposing internal traces; counterfactual review distinguishing a bad decision from a good decision with a bad outcome. |
| `NLB-KROS-008` | Evidence-bound causal edges and impact analysis on change. |
| `NLB-KROS-001` | Epistemic status — observed fact, inference, assumption, speculation. |

---

## Consistency Validation

Reasoning fails quietly in four ways, and each has a mechanical check.

**Numerical.** Calculations are independently re-checked where practical. A conclusion resting on arithmetic nobody verified is a conclusion resting on nothing in particular, and the error is invisible because the surrounding prose is sound.

**Units.** Normalize → calculate → validate → format, always in that order. **Calculating across unlabelled or mixed units is the single most common source of confidently wrong numbers**, and it survives every other check in this volume because the result looks like a number and behaves like one.

**Temporal.** Impossible sequences are caught: an event cannot occur before a prerequisite that is genuinely mandatory. Dates that cannot coexist are a contradiction in the evidence, not a detail to smooth over.

**Constraint.** The output is checked against the constraints that governed the task, not only against the question — a result that answers well while violating a stated hard constraint (`NLB-KROS-011`) has failed.

### Causal language

Correlation is never presented as causation, and the claim is labelled at the strength the evidence supports:

```
CORRELATED → ASSOCIATED → LIKELY CONTRIBUTING → CAUSALLY ESTABLISHED
```

`NLB-KROS-008` requires causal *edges* to be evidence-bound. This is the same rule applied to prose, where it is far easier to breach: "because" is a cheap word, and a reader takes it at full strength regardless of what the evidence supported.

---

## Competing Hypotheses

A conclusion reached without rivals is a first guess that was never tested.

```
H1 · H2 · H3 → EVIDENCE TEST → RANK
```

**Hypotheses are ranked against evidence and updated as evidence arrives** — new evidence raises or lowers confidence in each, rather than confirming the one already favoured. Feeds `NLB-KROS-005`'s hypothesis cards.

**The falsification test** is the sharpest question available, and it is asked of every major hypothesis:

> *"What evidence would prove this wrong?"*

A hypothesis with no answer is not a strong hypothesis — it is an unfalsifiable one, and no amount of supporting evidence can strengthen it. Asking what would refute it also produces something immediately actionable: a specific thing to go and check.

**Discriminating evidence is prioritized.** Evidence that separates competing hypotheses is worth more than evidence that supports the leading one, however abundant the latter is. This differs from `NLB-KROS-011`'s value of information — that ranks by decision impact, this ranks by explanatory power — and both are needed, because the fact that would change your mind and the fact that would change your action are often not the same fact.

---

## Second-Order Effects

```
ACTION → DIRECT EFFECT → SECOND EFFECT → LONG-TERM EFFECT
```

Analysis that stops at the direct effect is analysis of the easiest part. The consequences that make a decision regrettable are usually one step further out — the direct effect is what was intended, and the second-order effect is what was not.

---

## Option Generation

**Options are generated before any is evaluated.** A system that scores the first plausible answer has not compared anything; the quality of a decision is bounded by the quality of the option set, and no weighting scheme recovers an option that was never listed.

```
GENERATE → PRUNE (hard constraints) → RANK (criteria) → RECOMMEND
```

**"Do nothing" and "defer" are legitimate options** and appear where they genuinely are. Their omission is a structural bias in most decision tooling: presented with three ways to act, a user chooses among three ways to act, and the possibility that acting is worse than waiting never enters the comparison.

**Material decisions carry alternatives**, not a single recommendation — with the trade-offs, and with what the recommendation gives up.

**Recommendations are traceable**: data → assumptions → criteria → analysis → recommendation, per `NLB-KROS-004`'s audit trail.

---

## Policy Exceptions and Rule Testing

`NLB-KROS-005` establishes the policy engine. Two additions:

**Rules support explicit exceptions** — `IF condition THEN action UNLESS exception` — because the exception exists in practice regardless, and an unstated one becomes an undocumented override applied inconsistently.

**Rules are tested against example scenarios before deployment**, exactly as workflows are (`NLB-CPIOS-002`'s simulation). A policy is a program; shipping one untested is shipping untested code with organizational authority behind it.

---

## Decision Sufficiency

A decision is adequately supported when it has relevant data, valid constraints, reasonable assumptions, sufficient evidence, and acceptable risk — **and where it does not, the missing element is named** rather than the decision being presented as ready.

**Decision speed tracks reversibility**, per `NLB-KROS-010`: a reversible decision can be made quickly on partial evidence because it can be unwound; an irreversible one warrants the delay. Applying uniform rigour to both is a failure in both directions — slow on what is cheap to undo, hasty on what is not.

**Recommendations go stale.** When the evidence beneath one changes, it is re-assessed rather than left standing, per `NLB-KROS-010`'s assumption monitoring and `NLB-KROS-008`'s impact analysis.

---

## Acceptance Criteria

Part 14 is architecturally complete when it supports: consistency validation (independent numerical re-checking, unit normalization before calculation, temporal-logic checks for impossible sequences, constraint checking against the governing requirements, and causal language labelled at the strength the evidence supports); competing hypotheses (rival generation, evidence-based ranking with updating, the falsification test applied to every major hypothesis, and prioritized discriminating evidence distinct from decision-impact ranking); second-order effect analysis; option generation (options generated before evaluation, pruning by hard constraint before ranking, "do nothing" and "defer" as first-class options, alternatives on material decisions, and traceable recommendations); policy exceptions and pre-deployment rule testing; and decision sufficiency (named missing elements, decision speed tracking reversibility, and re-assessment when underlying evidence changes).

---

## Principle

**Facts → Evidence → Assumptions → Hypotheses → Analysis → Options → Risks → Decision → Outcome → Learning.**

> A conclusion that was never tested against a rival, never checked for arithmetic, and never asked what would refute it is not a conclusion. It is the first thing that occurred to the system, written confidently.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-12 | Initial reasoning validation specification, drawn from source Part 18. Establishes numerical, unit, temporal and constraint consistency checks; causal language labelled at evidence strength; competing-hypothesis generation with the **falsification test** and **discriminating evidence** prioritized separately from decision-impact ranking; second-order effect analysis; option generation before evaluation with "do nothing" and "defer" as first-class options; policy exceptions and pre-deployment rule testing; and decision sufficiency with speed tracking reversibility. Decision matrices, constraints and calibration remain with `NLB-KROS-011`; argument maps, steelman mode and the policy engine with `NLB-KROS-005`; assumption monitoring and reversibility classification with `NLB-KROS-010`. |

---

**End of Part 14 (Version 1.0)**

**END OF THE KNOWLEDGE, RESEARCH & PERSONAL INTELLIGENCE OPERATING SYSTEM SPECIFICATION**
