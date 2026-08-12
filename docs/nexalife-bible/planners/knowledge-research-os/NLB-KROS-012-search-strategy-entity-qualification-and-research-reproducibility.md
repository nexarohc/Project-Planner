# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 12 — Search Strategy, Entity Qualification, Verification Modes & Research Reproducibility

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-012 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-KROS-001` · `NLB-KROS-002` · `NLB-KROS-003` · `NLB-KROS-004` · `NLB-KROS-006` · `NLB-KROS-009` · `NLB-CWOS-002` |

---

## Purpose

Parts 1–4 specified how research is planned, verified, synthesized, and automated. Part 12 covers what is left: **how the searching itself is conducted and audited**, **how an entity earns a place in a result set**, and **how a completed research run is reproduced months later.**

### Scope boundaries

Its source material largely restated the series foundation:

| Already owned by | Covers |
| --- | --- |
| `NLB-KROS-001` | Research plans and objectives, depth levels, stop conditions and saturation, source ranking and deduplication, conflict surfacing, coverage reporting as estimates, claim decomposition, evidence hierarchy, snapshots and change detection, freshness states. |
| `NLB-KROS-002` | Question decomposition, scope binding, source requirements and exclusions, multi-agent orchestration with the output contract, consensus without false consensus, citation and bibliography handling, hallucination defense, the final report structure. |
| `NLB-KROS-003` | Entity resolution with match confidence and never-silent merging, normalization retaining originals, research templates, output schemas, export formats. |
| `NLB-KROS-004` | Agentic pipelines with planner and task graph, budgets and declared cost, the research cache and delta mode, claim and evidence registers, the end-to-end audit trail and exportable package. |
| `NLB-KROS-006` | Temporal reasoning, historical knowledge states, "I don't know" and evidence-first strictness modes. |
| `NLB-CPIOS-001` · `NLB-CWOS-002` | Document Q&A, contract clause review, and the regulated-adjacent posture on legal conclusions. |

---

## Search Strategy

The Bible has specified what research *checks*. It has not specified how it *looks* — and a flawless verification pipeline over a badly-shaped search returns confidently wrong coverage.

**Query diversity is required, not optional.** Multiple formulations of the same question, expanded through synonyms, industry terms, local terminology, abbreviations, and **historical names** — an organization that renamed in 2021 is invisible to a search using only its current name, and its absence looks identical to it not existing.

**Search iterates**: insufficient results → reformulate → search again; noisy results → filter → narrow. A single query returning little is a fact about the query, not about the world.

**Search-strategy bias is checked explicitly.** Does the strategy systematically exclude relevant alternatives — by language, by region, by source type, by the vocabulary of one industry segment? This is the failure that produces a clean, well-evidenced, thoroughly verified result set that is **structurally incomplete in the same direction every time**, and no amount of downstream verification detects it, because everything that made it into the set is genuinely correct.

**Stopping** follows `NLB-KROS-001`: objective satisfied, diminishing returns, or budget reached.

### Coverage claims

> *"I identified 146 qualifying entities from the sources searched."*

**not**

> *"These are all such entities."*

The second is only sayable where comprehensive coverage has actually been demonstrated, which is rare. Completeness is reported as a state — Complete / High coverage / Partial / Limited / Insufficient — never assumed from effort expended.

---

## The Research Log

Every non-trivial run maintains a record: queries issued, sources consulted, filters applied, decisions taken, verification steps, and **results rejected**.

**The rejected-result log is the part that matters and the part always omitted.** Recording *why* something was excluded — duplicate entity, inactive, wrong industry, insufficient evidence — is what makes a result set reviewable rather than merely presentable. Without it, the user cannot tell a rigorous exclusion from an accidental one, and re-running the research later re-litigates every judgment from scratch.

**Reproducibility follows from the log.** A complex run is reconstructable from its objective, queries, source set, filters, analysis, and date — the research instance of `NLB-KROS-009`'s context snapshots. Research that cannot be reproduced cannot be defended, and in professional work being unable to show how a conclusion was reached is functionally the same as not having reached it.

### Time-bounded research

An **information cut-off** can be set: *"what was known as of 1 January 2025?"*

**Later information must not contaminate the answer** unless the user asks for it. This is `NLB-KROS-006`'s temporal reasoning applied at the point of search rather than retrieval, and it is what makes an honest reconstruction of a past decision possible.

Every piece of evidence distinguishes **published date, event date, effective date, and retrieved date** where available. These routinely differ, and collapsing them is how a two-year-old regulation gets reported as this month's news.

---

## Entity Qualification

Business research fails in a specific way: **a company existing is not the same as a company qualifying.** A list assembled from existence alone looks like research and functions like noise.

Qualification is a conjunction, and each element carries its own evidence:

```
EXISTS + RELEVANT CAPABILITY + CURRENT ACTIVITY
       + RELEVANT NEED + CONTACTABILITY
```

**Confidence is stated per entity** — Verified / Probable / Potential / Unverified — and **entity status is explicit**: Active / Inactive / Acquired / Merged / Unknown. An acquired company presented as an active independent one is a wasted approach at best and an embarrassing one at worst.

**Disambiguation precedes deduplication.** *ABC Pharma*, *ABC Pharmaceuticals Ltd.* and *ABC Pharma India* may be one entity or three, and the question is settled on evidence rather than string similarity (`NLB-KROS-003`).

### The no-fabrication rule, stated concretely

Nexa never generates a company, contact, email address, procurement notice, regulatory approval, quotation, or source that does not exist. Where information cannot be found, the value is **"Not publicly available."**

`NLB-KROS-002` establishes this as a general principle. It is restated here because entity research is where the pressure to fabricate is highest — the output format is a table with empty cells, and a plausible filler is both easy to produce and impossible to distinguish from a real value downstream.

### Normalization that keeps the original

Names, dates, countries, units, currencies, product names, and organization types normalize to standard forms — *USA / United States / US* → **United States** — with the source value retained.

**Currency conversion records the original amount, the converted amount, the rate source, and the exchange date.** A converted figure with none of these is unusable six months later and unverifiable immediately.

**Validation** runs before analysis: missing values, impossible values, duplicates, conflicts, outliers.

---

## Ranking and Verification Modes

**Entity ranking uses transparent criteria with stated weights** — relevance, evidence, recency, capability, accessibility — and **explains the result**: *"Company A ranked first because it has stronger evidence of current activity and closer capability alignment."* Per `NLB-KROS-011`, an unexplained ranking is an oracle.

Two modes bound what may appear at all:

| Mode | Admits |
| --- | --- |
| **Strict verification** | Verified entities only. No estimates, no unverified leads, no duplicates, no placeholders. |
| **Exploratory** | Verified, potential, and hypothetical — **each explicitly labelled** |

**A user-defined standard binds the whole pipeline.** *"Only include officially verified companies"* is enforced at every stage, and where it cannot be met the run says so rather than quietly relaxing it — the entity-research instance of `NLB-KROS-005`'s policy engine.

**Exploratory mode is safe only because of the labelling.** Mixing verified and hypothetical entries is genuinely useful for early-stage thinking and genuinely destructive the moment the labels are lost — for instance, in an export.

---

## Reporting and Delivery

Reports follow `NLB-KROS-002`'s structure, with three additions:

**Recommendations connect to evidence** — finding → implication → option → recommendation — and carry their own support level: High / Moderate / Low / Exploratory. A recommendation whose support is not stated will be read as high.

**Limitations are disclosed, not buried**: missing public information, restricted databases, conflicting sources, historical gaps, unverified claims.

**A quality scorecard** reports source quality, coverage, verification, recency, and confidence as **estimated internal indicators** (`NLB-KROS-004`).

### Long-running research

Deep research runs asynchronously:

```
QUEUED → RUNNING → VERIFYING → SYNTHESIZING → COMPLETE
```

**Progress is legible, not a spinner**: *"cross-checking 37 entities"*, *"validating conflicting records."* A long opaque wait is indistinguishable from a hang, and a user who cannot see what a research run is doing has no basis for letting it continue.

**A research API** exposes start, status, results, evidence, and refresh to authorized systems, resolving against `NLB-KROS-009`'s Context API permissions — **evidence retrieval is a separate capability from result retrieval**, since a consumer that can read conclusions does not thereby need the underlying source material.

---

## Acceptance Criteria

Part 12 is architecturally complete when it supports: search strategy (multiple query formulations with synonym, local-terminology, abbreviation and historical-name expansion; iterative reformulation and narrowing; explicit search-strategy bias checking; coverage claims bounded to sources actually searched; completeness reported as a state); the research log (queries, sources, filters, decisions, verification steps, and a rejected-result log carrying reasons; reproducibility from objective, queries, sources, filters, analysis and date; information cut-offs that exclude later contamination; published/event/effective/retrieved dates kept distinct); entity qualification (existence plus capability, activity, need and contactability with per-element evidence; per-entity confidence; explicit entity status; evidence-based disambiguation before deduplication; the concrete no-fabrication rule with "not publicly available" as the missing-value form; normalization retaining originals and currency conversion recording rate source and exchange date; pre-analysis validation); ranking and modes (transparent weighted criteria with explained results; strict-verification and labelled exploratory modes; user-defined standards enforced pipeline-wide with explicit refusal rather than silent relaxation); and delivery (evidence-linked recommendations with stated support level, disclosed limitations, estimated quality scorecards, asynchronous execution with legible progress, and a research API where evidence retrieval is a distinct capability from result retrieval).

---

## Principle

**Question → Plan → Search → Verify → Cross-check → Analyze → Synthesize → Cite → Act.**

> NexaLife must never confuse finding information with establishing truth.

The search strategy is where that confusion begins. Everything downstream can be rigorous and the conclusion still wrong, because the thing that would have changed it was never looked for.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-12 | Initial search strategy and entity qualification specification, drawn from source Part 14. Establishes required query diversity including historical names, iterative reformulation, **explicit search-strategy bias checking** for structural incompleteness that downstream verification cannot detect, coverage claims bounded to sources searched, the research log with a **rejected-result log** carrying exclusion reasons, reproducibility from the log, information cut-offs preventing later contamination, entity qualification as a conjunction with per-entity confidence and explicit status, the no-fabrication rule restated concretely for entity tables, currency conversion recording rate source and exchange date, transparent weighted ranking with explanation, strict-verification and labelled exploratory modes, evidence-linked recommendations with support levels, and asynchronous research with legible progress and a research API separating evidence retrieval from result retrieval. Research planning, verification, synthesis and pipeline mechanics remain with `NLB-KROS-001`–`004`. |

---

**End of Part 12 (Version 1.0)**
