# 📖 NEXALIFE BIBLE — NXOS: Nexa Operating Layer

## Part 2 — Cognitive Architecture

| Field | Value |
| --- | --- |
| Document ID | NLB-NXOS-002 |
| Series | NXOS — Nexa Operating Layer (Volume 23) |
| Version | 1.0 |
| Status | Master Draft |
| Priority | ★★★★★ (Reasoning Architecture) |
| Supersedes | — |
| Last updated | 2026-08-05 |

---

## Purpose

Very few products attempt to specify this: how Nexa actually reasons and coordinates specialized intelligence, without exposing internal implementation details or pretending certainty it doesn't have. `NLB-06` and `NLB-NIC-001` already establish *that* Nexa delegates to specialists, distinguishes facts from assumptions, and explains its recommendations. This volume specifies the **mechanism** behind those promises — how a goal actually becomes a decomposed plan, how confidence is estimated rather than asserted, and how a recommendation is checked before it reaches the user.

---

## Universal Reasoning Engine

Every request passes through goal decomposition, planning, multi-agent coordination, and reflection before a response is produced. This is the concrete pipeline behind the Universal Goal Engine already named in `NLB-NXOS-001`:

```
Request → Goal Decomposition → Planning → Specialist Coordination
  → Confidence & Evidence Check → Reflection → Response
```

---

## Goal Decomposition

Breaks a stated goal into the sub-goals and constraints it implies — the mechanism behind every "Worked example" already used throughout this Bible (the marathon, the conference, "Launch My Startup"). Decomposition identifies which Life Domains (`NLB-03`) and planners (`NLB-04`) a goal touches, feeding the Planning Engine below.

---

## Planning Engine

Produces an ordered plan — the specific sequencing decision behind `NLB-NIC-002`'s Multi-Step Planning and `NLB-21`'s Cross-Planner Automation. Plans are represented as **planning graphs**: nodes are steps, edges are dependencies, and the graph is what lets Nexa answer "why this order?" when asked to explain a schedule.

**Decision trees** support the narrower case: a small number of discrete choices with clear trade-offs (e.g., which of two study plans to follow), where a full planning graph would be overkill. Nexa selects the lighter mechanism when the decision genuinely is that simple, rather than defaulting to maximal machinery for every request.

---

## Multi-Agent Coordination

Routes sub-goals to the appropriate specialists and merges their outputs — this is `NLB-06`'s AI Orchestrator and `NLB-NIC-001`'s Multi-Agent Orchestration, restated here as the specific step in the reasoning pipeline where delegation happens. This volume adds nothing new to *how* delegation works; it fixes *where* it sits relative to decomposition and reflection.

---

## Confidence Scoring

Every factual claim or recommendation carries an internal confidence level, drawn from the quality and quantity of evidence behind it (see Evidence Tracking below), the specialist's own certainty, and whether the claim is being extrapolated beyond what the evidence directly supports. **Confidence is never rounded up to certainty for the sake of a cleaner-sounding answer** — this is the concrete mechanism that makes `NLB-06`'s "distinguish facts from estimates" and `NLB-SP-005`'s "readiness estimates are guidance, not guarantees" actually enforceable rather than aspirational.

---

## Evidence Tracking

Every recommendation records what it was based on — which planner data, which specialist, which user-provided fact, which external source. This is what powers Explainability (`NLB-06`, `NLB-11`): when a user asks "what information did you use," the answer comes from the evidence record attached to that specific recommendation, not from Nexa reconstructing its reasoning after the fact.

---

## Memory Retrieval

Determines which stored memories (session, short-term, long-term — per `NLB-NIC-001`, detailed further in `NLB-NXOS-003`) are relevant to the current request. Retrieval is scoped by permission first, relevance second — a memory the current context isn't authorized to use is never retrieved regardless of how relevant it would otherwise be.

---

## Context Prioritization

When multiple pieces of context compete (the active planner suggests one thing, the calendar suggests another, a stated preference suggests a third), Nexa prioritizes explicit, recent, user-stated information over inferred or older signals. Context Prioritization is itself explainable — "why did you assume I meant the Study Planner" has an answer, per the Context Fabric defined in `NLB-NXOS-001`.

---

## Reflection Engine

Before returning a response, Nexa checks it against the user's actual goal, the confidence and evidence behind it, and whether a human approval gate applies (below). This is a self-check step, not a second opinion from another model — its job is to catch a response that technically answers the question but misses what the user actually needed, or that overstates certainty Evidence Tracking doesn't support.

---

## Human Approval Gates

Any response or action that is sensitive, irreversible, or low-confidence passes through an approval gate before reaching the user unmediated, or before an action executes — the cognitive-layer trigger for `NLB-NIC-002`'s Approval Checkpoints. A gate fires on **low confidence** as much as on **sensitive action type** — an uncertain answer is flagged as uncertain, it is not executed or asserted with false confidence to avoid an awkward gate.

---

## Explainability

The output of Confidence Scoring and Evidence Tracking is what makes `NLB-06`'s and `NLB-11`'s Explainability requirement possible in practice: "why," "what evidence," and "what assumptions" all resolve to data this volume's pipeline already produces, not to a post-hoc justification generated after the fact.

---

## Continuous Learning Architecture

Nexa's recommendations improve from accepted suggestions, dismissed suggestions, explicit ratings, and corrected assumptions — per `NLB-NIC-001`'s Learning from Feedback. Learning updates personalization and future confidence calibration; **it never silently changes what counts as evidence or lowers the bar for what earns high confidence.**

---

## Design Principle

Nexa should reason in a way that is checkable, not just confident-sounding. **A good answer that cannot show its evidence is treated the same as a wrong one** — this is the standard the entire Cognitive Architecture exists to meet.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial Cognitive Architecture specification. Establishes the reasoning pipeline (decomposition → planning → coordination → confidence/evidence check → reflection), planning graphs and decision trees, and the confidence/evidence mechanics that make explainability enforceable rather than aspirational. |

---

**End of Part 2 (Version 1.0)**
