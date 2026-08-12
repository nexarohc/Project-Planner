# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 2 — Research Agents, Knowledge Synthesis, Professional Learning & Intelligence Safety

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-002 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.1 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Parent | `NLB-KROS-001` |

---

## Intelligence Orchestrator

Knowledge work is not one process, and a single agent doing everything cannot show its working.

```
                         USER
                           ▼
                  INTELLIGENCE ORCHESTRATOR
       ┌───────────┬───────┼───────┬───────────┐
       ▼           ▼       ▼       ▼           ▼
   RESEARCH     ANALYST  TEACHER  WRITER    VERIFIER
       └───────────┴───────┼───────┴───────────┘
                           ▼
                    KNOWLEDGE GRAPH
```

Each agent registers under `NLB-NXOS-004`'s seven-field schema. The orchestrator is `NLB-06`'s, not a second one.

**Specialized agents**: Research (finds and evaluates), Verification (checks claims and sources), Analyst (compares and finds patterns), Teacher (explains), Writing (turns knowledge into documents), Librarian (organizes), Memory (maintains approved long-term knowledge), Review (checks conclusions for weakness).

---

## The Agent Output Contract

Every agent returns the same structure, and this is what makes the whole system auditable:

```
INPUT                What it was given
METHOD               How it worked
RESULT               What it found
EVIDENCE             What supports the result
UNCERTAINTIES        What it could not establish
RECOMMENDED NEXT     What would resolve the gaps
```

The **Uncertainties** field is mandatory and may not be empty by default. An agent that reports only findings hides its own limits; requiring it to state what it *couldn't* establish is what allows the next agent — or the user — to judge whether the result is usable.

**Handoffs** pass structured output, not prose: Research → *sources + claims* → Verification → *verified claims* → Analyst → *analysis*. Each stage's input is the previous stage's checked output.

**Composite workflows** are where the contract pays off. *"Research this market and tell me whether entering it makes sense"* runs:

```
Research → Verification → Market analysis → Risk analysis
    → Counterargument → Decision framework → Final report
```

The counterargument stage is deliberately placed *before* the decision framework, not after the recommendation. A challenge raised after a conclusion is written rarely changes it.

---

## Research Control

**Objective** is fixed before work starts: question, objective, scope, date range, geography, source requirements, output format.

**Scope control is binding.** Given *"only Indian pharmaceutical manufacturers with current regulatory evidence,"* **the agent must not silently broaden the criteria** — quietly relaxing a constraint to return more results is a failure mode that looks like success.

**Source requirements** (official only / government / academic / industry / any credible) and **exclusions** (forums, social media, unverified directories, sources older than N) are user-set.

**Question expansion** decomposes a question too broad to answer (*"research AI"* → definitions, categories, leading systems, use cases, costs, risks, regulation, outlook). **Clarification is requested only when it materially changes the result** — asking for its own sake wastes the user's attention.

**Multi-angle research** covers technical, commercial, legal, regulatory, operational, financial, competitive, and user perspectives as the subject warrants.

---

## Competitive & Market Intelligence

**Competitor profiles** (products, pricing, markets, customers, strengths, weaknesses, recent developments, differentiators), **market maps** (leader / challenger / niche), and **entity timelines**.

**Change detection** across research runs reports what moved and by how much, feeding `NLB-KROS-001`'s watchlists and change-only digests.

**Periodic research** — *"check this market every Monday"* — schedules a recurring research task on `NLB-09`'s recurrence model where the sources support it, producing a digest of new developments, important changes, and what held steady. The recurring run is what turns a one-time report into a monitored position; without it, every watchlist entry depends on the user remembering to ask.

---

## Verification in Depth

**Contradiction handling**: *"I found conflicting information"* followed by **both positions and their sources** — never a silent resolution.

**Regulatory status tracking** structures product → authority → application → approval → status → date, so a claim about approval is always attached to a specific authority, product, and date rather than floating free.

---

## Knowledge Synthesis

*"Read these 12 reports and tell me what they collectively say"*:

```
COMMON FINDINGS   3
DISAGREEMENTS     2
UNIQUE FINDINGS   7
OPEN QUESTIONS    4
```

**Consensus detection** identifies genuine agreement across independent sources — after deduplication (`NLB-KROS-001`), so shared origin isn't mistaken for agreement. **Outlier detection** flags unusual claims without dismissing them; an outlier is sometimes the only source that checked.

**No false consensus.** Where evidence is mixed: *"The sources do not establish a clear consensus."* Manufacturing a tidy answer from genuinely contested evidence is the most damaging thing a synthesis engine can do, because the output looks identical to a well-supported one.

**Literature review mode** (research question → papers → methods → findings → limitations → gaps), **paper comparison**, a **citation manager**, and **bibliography generation** (APA, MLA, Chicago, IEEE) — extending `NLB-04`'s PU-02-026/027 and PU-16-008.

---

## Research Writing

Outputs: executive summary, literature review, research memo, briefing, report, presentation outline, dashboard, or structured table.

**Research becomes structure, not just prose.** A presentation carries outline → slides → speaker notes → references, with the reference list generated from the same citations the research used rather than reassembled by hand. A set of researched entities becomes a table — company, country, product, status, **source, date** — where the last two columns are not optional: a structured extract that drops its provenance is indistinguishable from a list someone typed from memory, and it will be reused long after anyone remembers where it came from.

**Source-locked writing** is enforced: *"Write this report using only these 15 sources"* means **Nexa introduces no outside sources**, silently or otherwise.

**Source gap warning** — if the supplied sources don't support a requested claim: *"The provided sources do not establish this."* The user may then supply more sources, soften the claim, or drop it. What must not happen is the claim appearing anyway, supported by something the user didn't provide.

**Claim → source → passage** traceability is retained through to the final document.

---

## Professional Learning

`NLB-SP-002` and `NLB-SP-003` own learning mechanics — spaced repetition, active recall, mastery models, prerequisite graphs, flashcards, adaptive difficulty, learning paths. Those are not restated. This section covers only what **adult and professional** learning adds:

**Socratic mode** — rather than answering, Nexa asks *"What do you think happens next?"* and lets the user reason first. Available on request; a professional in a hurry wants the answer, and the mode is a choice rather than a default.

**Teach-back** — the user explains the concept back, and Nexa evaluates the explanation **against the source material** rather than against its own paraphrase. Explaining is where understanding is actually tested.

**Error notebook** — wrong answers become records (concept, the specific error, review date), and **personal error patterns** surface recurring confusions (*"you frequently conflate correlation and causation"*). Naming the pattern is more useful than correcting each instance.

**Explanation regeneration** — when an explanation fails, try a different form: analogy, visual, worked example, step-by-step, or technical.

**Interruption branching** — *"Wait, why?"* branches into the prerequisite concept and returns to the main thread without losing place.

**Expert / Beginner modes** — *"assume I know the basics"* or *"explain from zero"*, with skipping based on **demonstrated** knowledge rather than claimed familiarity.

**Exam vs Practice modes** — exam: no hints, timed, randomized, scored. Practice: hints, unlimited attempts, immediate explanation.

**Certification preparation** maps a supplied syllabus → topics → gaps → study plan → mock exams, with coverage per topic and post-exam review of weak areas.

**Time-boxed learning** is the defining constraint of adult study. *"I have 20 minutes a day"* is a hard budget, not a preference, and lessons are built to fit it — 5, 10, or 20 minutes, each a complete unit rather than a truncated one. A lesson that assumes an uninterrupted hour is unusable to the person this section is written for.

**Parallel curricula** — a professional typically runs several unrelated learning tracks at once (a language, a technical skill, a domain, a certification), where a student follows one syllabus. Each track keeps its own goal, pace, and progress, and **they are not merged into a single completion figure**; averaging unrelated tracks produces a number that describes nothing.

**Mastery is demonstrated, not clocked.** Time spent is not evidence of learning; understanding → explaining → applying → solving → creating is. Learning scores are **estimates**, never presented as measurements of ability.

---

## Intelligence Safety

The defining constraint of this volume.

**Hallucination defense** — *"I don't have enough evidence"* is always preferable to an invented answer. In research, a fabricated citation is worse than no answer at all, because it is indistinguishable from a real one until checked.

**Explicit unknown states** — Unknown / Unverified / Conflicting / Outdated / Estimated are all first-class, returnable results.

**Quality control before finalizing**: source check, date check, duplicate check, conflict check, citation check, gap check.

**Education mode** applies where a minor is the learner: age-appropriate explanation, a restricted source set, and the stronger safeguards `NLB-10` defines for minor accounts. It is a distinct mode rather than a tone setting, because the difference that matters is *which sources the research agent may reach*, not how the answer is phrased.

**Final intelligence report** structure, which puts the limits alongside the findings:

```
EXECUTIVE SUMMARY
WHAT WE KNOW
WHAT WE DON'T KNOW      ← never omitted
WHAT CHANGED
KEY RISKS
OPTIONS
RECOMMENDATION
EVIDENCE
NEXT ACTIONS
```

---

## Acceptance Criteria

KROS is architecturally complete when it supports: agents (specialized, orchestrated, with enforced output contracts and structured handoffs); research (planning, scope binding, exclusions, stop conditions, saturation, gap reporting, watchlists, change detection); verification (claim decomposition, evidence hierarchy, contradiction surfacing, precision in claims); synthesis (cross-document analysis, consensus and outlier detection, literature review, citations, source-locked writing); professional learning (Socratic, teach-back, error patterns, expert/beginner, exam/practice, certification); and safety (explicit uncertainty, evidence tracking, source transparency, hallucination defense, unknown states, auditability).

---

## Principle

**Research → Verify → Synthesize → Understand → Learn → Test → Apply → Update.**

> **NexaLife should never confuse confidence with truth.**

A serious intelligence system knows the difference between what it knows, what it believes, what the evidence suggests, and what remains unknown — and says which is which.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.1 | 2026-08-12 | Additive (MINOR): composite agent workflows with the counterargument stage placed before the decision framework; periodic/recurring research and digests; structured research outputs (presentation with generated references, entity tables carrying mandatory source and date columns); time-boxed learning and parallel curricula as the adult-learning constraints; Education mode for minor accounts scoped as a source restriction rather than a tone setting. |
| 1.0 | 2026-08-05 | Initial research agent and synthesis specification. Establishes the mandatory agent output contract with a non-empty Uncertainties field, binding scope control, consensus detection without false consensus, source-locked writing with gap warnings, professional-learning additions scoped against NLB-SP-002/003, and the intelligence safety layer including explicit unknown states and the "what we don't know" section in every final report. |

---

**End of Part 2 (Version 1.1)**
