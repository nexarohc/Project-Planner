# 📖 NEXALIFE BIBLE — Knowledge, Research & Personal Intelligence Operating System (KROS)

## Part 5 — Cognitive Workspace, Reasoning Tools, Knowledge Governance & The Research Command Center

| Field | Value |
| --- | --- |
| Document ID | NLB-KROS-005 |
| Series | Knowledge, Research & Personal Intelligence OS (Volume 31) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-12 |
| Parent | `NLB-KROS-001` |
| Dependencies | `NLB-06` · `NLB-08` · `NLB-NXOS-002` · `NLB-NXOS-005` · `NLB-KROS-003` · `NLB-KROS-004` |

---

## Purpose

Parts 1–4 covered researching, verifying, working, and automating. Part 5 covers the part in between: **thinking**. It specifies a workspace for reasoning that is not a chat window, the tools that make an argument inspectable, the governance layer that constrains what conclusions may rest on, and the top-level surface that ties all five parts together.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-SP-002`/`003`/`005` · `NLB-KROS-002` | Learning mechanics — adaptive curricula, spaced review, active recall, teach-back, practice generation, prerequisites, micro-learning, streaks, portfolios. This part does not restate them; the **skill graph and skill-gap analysis** below are the only additions, and they exist because they connect learning to `NLB-CWOS-001`'s career model rather than to a syllabus. |
| `NLB-KROS-003` | The knowledge workspace, encyclopedia, entity pages, comparison, briefs, and knowledge health/cleanup. |
| `NLB-KROS-001` | Research depth levels, stop conditions, saturation, coverage reporting, decision memory. The research modes below refine those levels; they do not replace them. |
| `NLB-NXOS-002` | Confidence scoring and the cognitive architecture the reasoning tools below express. |

---

## The Cognitive Workspace

Complex thinking needs somewhere to happen that is not a conversation transcript:

```
┌──────────────┬────────────────────┬──────────────┐
│  KNOWLEDGE   │      THINKING      │   ACTIONS    │
│  Sources     │  Question          │  Tasks       │
│  Notes       │  Hypotheses        │  Decisions   │
│  Documents   │  Evidence          │  Calendar    │
│  Memories    │  Alternatives      │  Deliverables│
└──────────────┴────────────────────┴──────────────┘
```

A chat log records what was said in order. It does not show which of five hypotheses is still live, which evidence supports which, or what the argument currently rests on — and that is exactly what a hard question requires you to hold. **The workspace's job is to make the state of the user's thinking visible**, not to produce more text about it.

**The thinking canvas** holds questions, ideas, evidence, hypotheses, arguments, counterarguments, and decisions as cards that can be moved and connected.

**Idea cards** carry title, description, evidence, related ideas, status, and confidence. **Hypothesis cards** carry the claim, supporting evidence, **counterevidence as a first-class field**, and status:

```
IDEA → HYPOTHESIS → TEST → EVIDENCE
     → SUPPORTED / REJECTED / UNCERTAIN
```

**Rejected and uncertain are real outcomes.** A workspace where hypotheses only ever get promoted is a workspace that manufactures conclusions, and Uncertain must remain a resting state — not a placeholder the system pressures the user to resolve.

---

## Reasoning Tools

### Argument maps

```
CLAIM
├── SUPPORT     Evidence A · Evidence B
└── CHALLENGE   Evidence C · Assumption D
```

Nexa checks the structure for **unsupported claims, logical jumps, missing evidence, contradictions, and ambiguous terminology** — the same class of check `NLB-KROS-004`'s reviewer applies to a report, applied here while the reasoning is still forming and still cheap to change.

### Challenging a position

**Counterargument mode** searches for credible objections on request. **Steelman mode** goes further and constructs the **strongest reasonable version of the opposing view** — not the version easiest to dismiss. An AI that only ever produces weak opposition is worse than one that produces none, because it leaves the user feeling tested when they have not been.

**Dialectic mode** works two positions toward common ground and a synthesis, where one exists. Where one does not, saying so is the correct output.

### Assumptions

**Detection** surfaces what a conclusion silently depends on: *"this assumes delivery time remains constant."* An **assumption register** (assumption · owner · evidence · impact · status) keeps them tracked rather than rediscovered, and connects to the assumptions `NLB-KROS-001`'s decision memory already records at decision time.

**Stress testing** asks the question that gets skipped: *"what happens if this assumption is wrong?"* Most decision failures are not reasoning failures — they are assumptions that were never examined because they never surfaced.

### Scenarios

Base / best / worst / expected / unexpected cases, with user-modifiable variables (price, demand, time, resources, risk, market conditions) and side-by-side comparison of how revenue, cost, risk, and time move across them.

**What-if** recalculates affected assumptions **where the necessary data exists** — and says plainly where it does not, rather than producing a number.

**Sensitivity analysis** identifies which variables actually matter:

```
HIGH     Demand
MEDIUM   Pricing
LOW      Packaging
```

This is the most useful output in the section, because it tells the user **where further research is worth doing** — feeding `NLB-KROS-003`'s decision-impact prioritization directly.

**Decision trees** lay out options and their branches, and **simulated outcomes are always presented as scenarios or estimates, never as predictions.** A number in a decision tree reads as a forecast regardless of how it was labelled, so the labelling has to be unmissable.

---

## Personal Knowledge Map

The user's own knowledge, rendered as territory:

```
                BUSINESS
     ┌─────────────┼─────────────┐
   SALES        FINANCE       RESEARCH
     │                            │
 MARKETING                     PHARMA
```

**Gaps are described structurally, never as judgment**: *"you have extensive knowledge of X but little connecting X to Y"* — a statement about the map, not about the person, per the no-shame principle running through the Bible.

**Connection discovery** proposes links the user hasn't drawn (*"these two projects may share the same supplier research"*), and **cross-domain insights** span projects, industries, topics, and decisions **where evidence supports the connection** — an unsupported cross-domain "insight" is just a coincidence with confidence attached.

**Skill graph and gap analysis** sit here rather than in the learning layer, because their purpose is connecting knowledge to a career target (`NLB-CWOS-001`) rather than to a syllabus:

```
GOAL     Advanced Analyst
CURRENT  Intermediate
GAPS     Statistics · Model evaluation · Automation
```

---

## Expression Control

**The analogy engine** explains a concept through another domain and **labels the analogy as an analogy** — an unlabelled analogy is received as a claim about how the thing actually works, and the failure shows up much later.

**Concept translation** renders the same material in beginner, professional, executive, or academic register, and where supported, in multiple languages.

**Terminology lock** is the professional's requirement: *"in this project, always use 'marketing authorization', never 'approval'."* Enforced across generated output, this prevents the vocabulary drift that `NLB-KROS-003`'s contextual definitions exist to detect.

**Style profile** records user-approved writing preferences (structure, formality, vocabulary, typical formats) — *concise, professional, evidence-based; avoid excessive jargon* — applied to generated documents. **Preferences are learned only from what the user approves**, never inferred silently from what they happened to write.

---

## Knowledge Import & Governance

**Import** ingests authorized documents, notes, spreadsheets, research, and structured data, and **reports honestly on what arrived**:

```
Imported 4,230 · Duplicates 127
Potential conflicts 43 · Unclassified 318
```

**Uncertain classifications go to a review queue before becoming knowledge.** An import that silently classifies 318 uncertain items is an import that quietly poisons the knowledge base, and the damage is discovered much later through wrong answers whose cause is untraceable.

**Portability** — the user's knowledge exports in standard formats where supported, per `NLB-07`'s data-portability guarantees. Knowledge accumulated over years is the user's asset, and a system that makes it hard to leave has made it risky to commit to.

### Governance

For organizations: policies, standards, owners, review cycles, permissions, audit.

**A knowledge policy engine** lets an organization constrain what conclusions may rest on: *"only approved regulatory sources may be used for regulatory conclusions."* **The pipeline checks policy before producing final output**, and where the standard cannot be met, it says so instead of quietly relaxing it:

> *"I found relevant information, but it does not meet your configured source policy."*

This is the organizational form of `NLB-KROS-002`'s binding scope control, and it fails the same way if softened — silently returning a result that looks compliant is the outcome the policy exists to prevent. A **compliance log** records project, policy, check, result, reviewer, and date.

---

## The Research Command Center

The top-level surface, where every part of this series meets:

```
┌──────────────────────────────────────────────┐
│         WHAT DO YOU WANT TO KNOW?            │
│  "Research the global opportunity for X."    │
├──────────────────────────────────────────────┤
│  Scope │ Sources │ Depth │ Time │ Output     │
├──────────────────────────────────────────────┤
│  RESEARCH PLAN                               │
│  12 tasks · 31 sources · 4 verification steps│
├──────────────────────────────────────────────┤
│  Evidence │ Conflicts │ Findings │ Actions   │
└──────────────────────────────────────────────┘
```

**The plan is shown before the work runs**, per `NLB-KROS-001` — and the control panel exposes depth, speed, sources, budget, freshness, verification level, and output format as things the user sets rather than things the system decides.

| Mode | Character |
| --- | --- |
| **Quick** | Minutes, limited sources |
| **Standard** | Balanced research and verification |
| **Deep** | Broad coverage, deeper cross-checking, structured synthesis |
| **Forensic** | Maximum configured verification for high-stakes questions |

**Forensic mode states its own limits.** Even maximum verification cannot guarantee completeness, and a mode named "forensic" invites exactly the over-trust that makes saying so necessary.

**Stopping** follows `NLB-KROS-001`'s conditions — sufficient evidence, budget reached, scope complete, or **diminishing returns**, reported plainly: *"the last 20 sources added little new information."*

**Completion is reported, never claimed**:

```
Scope coverage           87%
High-confidence claims   74%
Open questions           6
```

An **open question register** persists per project, and **research resumes from state**: *"continue from where we stopped"* picks up the plan, the sources already checked, and the questions still open.

**Continuity across surfaces** — chat → research → documents → tasks → calendar — carries the relevant context without the user re-establishing it, per `NLB-KROS-003`'s knowledge continuity.

---

## The Personal Intelligence Loop

```
QUESTION → RESEARCH → DECISION → TASK → CALENDAR
  → EXECUTION → OUTCOME → LEARNING
```

**Outcome capture closes it.** After an action, *"what happened?"* — recorded when the user provides or authorizes the information, linking decision → action → outcome → lesson, and feeding `NLB-KROS-001`'s decision memory.

```
KNOW → UNDERSTAND → DECIDE → ACT → OBSERVE → LEARN → UPDATE → KNOW
```

Almost every knowledge tool ever built implements the first half. **The loop only closes if outcomes are recorded against the reasoning that produced them** — which is why decision memory (Part 1) and outcome capture (here) are the same mechanism seen from both ends, and why a system without them accumulates information without ever accumulating judgment.

---

## Acceptance Criteria

Part 5 is architecturally complete when it supports: the cognitive workspace (three-pane knowledge/thinking/actions layout, thinking canvas, idea and hypothesis cards with counterevidence fields, hypothesis lifecycle with rejected and uncertain as terminal states); reasoning tools (argument maps with structural checks, counterargument and steelman modes, dialectic synthesis, assumption detection and register, assumption stress testing, scenario engine with variables and comparison, what-if bounded by available data, sensitivity analysis, decision trees with estimates never presented as predictions); the personal knowledge map (structural gap description without judgment, connection discovery, evidence-bounded cross-domain insight, skill graph and gap analysis); expression control (labelled analogies, register and language translation, terminology lock, approval-derived style profiles); import and governance (honest import reporting, review queue before commitment, portability, policy engine enforced before output with explicit refusal on unmet standards, compliance log); the research command center (visible plan, full control panel, four research modes with forensic mode stating its limits, diminishing-returns reporting, completion metrics rather than completion claims, open question register, resumable research state, cross-surface continuity); and the intelligence loop (decision → action → outcome → lesson, with outcome capture feeding decision memory).

---

## Principle

**Capture → Connect → Think → Research → Learn → Decide → Execute → Observe → Remember → Improve.**

> NexaLife should not merely answer questions. It should help the user turn information into understanding, understanding into decisions, decisions into action, and actions into accumulated judgment.

The last step is the one that distinguishes an intelligence system from a search engine — and it is the only one that requires the user's own outcomes rather than the world's information.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-12 | Initial cognitive workspace and governance specification, drawn from source Part 6. Establishes the three-pane thinking workspace, hypothesis cards with mandatory counterevidence and Uncertain as a resting state, argument maps with structural checking, steelman and dialectic modes, the assumption register and stress test, the scenario engine with sensitivity analysis feeding research prioritization, the personal knowledge map with judgment-free gap description, terminology lock and approval-derived style profiles, import with a pre-commitment review queue, the knowledge policy engine that refuses rather than silently relaxes a source standard, the research command center with four modes including forensic's stated limits, completion metrics rather than completion claims, resumable research state, and outcome capture closing the loop into decision memory. The learning material in the source part is not restated — it duplicates NLB-SP-002/003/005 and NLB-KROS-002 — except the skill graph and gap analysis, retained here because they connect to NLB-CWOS-001's career model rather than to a syllabus. |

---

**End of Part 5 (Version 1.0)**
