# 📖 NEXALIFE BIBLE — Autonomous Execution & Action Orchestration System (AEAOS)

## Part 2 — Multi-Agent Runtime, Delegation Limits & Agent Security

| Field | Value |
| --- | --- |
| Document ID | NLB-AEAOS-002 |
| Series | Autonomous Execution & Action Orchestration System (Volume 32) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-13 |
| Parent | `NLB-AEAOS-001` |
| Dependencies | `NLB-06` · `NLB-10` · `NLB-NXOS-004` · `NLB-NIC-004` · `NLB-KROS-002` · `NLB-KROS-004` |

---

## Purpose

`NLB-NXOS-004` defines **what an agent is** — registration, capability declaration, permissions, teams, lifecycle, kill switches. Part 2 defines **how a population of them behaves at runtime**: how work is allocated, what stops the population growing without bound, and why an agent cannot acquire authority by asking a colleague for it.

### Scope boundaries

| Already owned by | Covers |
| --- | --- |
| `NLB-NXOS-004` v1.1 | The registration schema, the capability declaration with its explicit CANNOT list, permissions granted independently of installation, agent teams with critic and verifier roles, dissent preservation, quality gates, lifecycle states, sandboxing, security-event monitoring, and three-scope kill switches with safe shutdown. |
| `NLB-KROS-002` | The agent output contract with its mandatory non-empty Uncertainties field, structured handoffs, and composite workflows. |
| `NLB-KROS-004` | The research pipeline planner, task graph, red-teaming before synthesis, and peer review. |
| `NLB-NIC-004` v1.1 | Tool registry and capability routing; data contracts and structured exchange between agents. |
| `NLB-06` | Model routing and orchestration. |

---

## Allocation

The supervisor decides **what to delegate, to whom, with what context, within what limits, and by when** — never handing over an open-ended request.

**Delegation is minimized.** A simple task is done, not delegated. Every agent added to a workflow costs coordination, context transfer, and a new failure surface; a population of specialists assembled for work one process could do is slower, more expensive, and harder to debug than the direct path.

**Specialists are preferred only where they measurably outperform** the general path. Otherwise the general path wins on simplicity.

### Orchestration modes

| Mode | Use |
| --- | --- |
| **Single** | Straightforward task |
| **Sequential** | Each stage depends on the previous |
| **Parallel** | Independent subtasks, synthesized after |
| **Hierarchical** | A supervisor coordinating specialists |
| **Debate** | Competing analyses before synthesis |
| **Review** | One produces, another validates |
| **Hybrid** | Complex work combining the above |

**The mode is a choice with a cost**, not a default. Debate and review buy reliability with latency and spend; single-agent buys speed by removing the check. Choosing debate mode for a lookup is as wrong as choosing single-agent for an irreversible decision.

### Temporary agents

A specialist configuration can be assembled for one task — *"a research agent scoped to Australian pharmaceutical distributors"* — and it carries **limited scope, limited data, limited permissions, and a defined lifetime**. Teams formed for an objective are dissolved when it completes.

A temporary agent that outlives its task is a standing capability nobody authorized, holding context nobody is reviewing.

**Selection may be competitive**: where several agents can serve, they can be compared on capability, cost, latency, and confidence, and the orchestrator picks the combination — with **performance history informing future selection** (`NLB-KROS-013`).

---

## Runtime Limits

A multi-agent system fails differently from a single one: not by stopping, but by **expanding**.

```
MAX AGENTS · MAX DELEGATION DEPTH · MAX TOOL CALLS
MAX TOKENS · MAX COST · MAX TIME
```

**Delegation depth is bounded.** Without a limit, an agent that cannot solve a problem delegates it, and the recipient does the same — producing a chain that consumes budget while doing no work, each link individually reasonable.

**Loop detection covers delegation, not only repetition.** Two agents handing the same task back and forth are looping even though neither repeats an action (`NLB-KROS-006`).

**Deadlock is detected and broken**: where agents cannot converge, the disagreement is identified, evidence is requested, the question is reassessed, and if it still will not resolve, **it escalates to a person** rather than continuing to circle.

**Agents terminate** on completion, impossibility, timeout, budget exhaustion, or user cancellation — and impossibility is a legitimate, reportable outcome.

---

## Agent Security

The distinctive risk of a multi-agent runtime, and the reason its security cannot be inherited from the single-agent case.

### No authority by association

**An agent cannot gain permission by asking another agent for it.** Every request resolves against `NLB-10`'s Permission Engine under the *requesting* agent's identity — never the identity of whichever agent happens to hold the capability.

Without this, least privilege becomes decorative: a narrowly-scoped agent simply asks a broadly-scoped one to act on its behalf, and the resulting action carries the broader agent's authority with none of its scrutiny. **Delegation moves work, never permission.**

**Negotiation between agents is bounded by the same rule.** Agents may allocate work among themselves; they **cannot negotiate away system policies, user permissions, security boundaries, or approval requirements** — those are not theirs to trade.

### Isolation

**Context is need-to-know per agent** — one agent does not inherit another's full context by working alongside it — and **information moves between agents only where the workflow and access policy permit** (`NLB-KROS-004`'s data minimization).

**Sensitive data reaches only agents that require it and are authorized for it.** Aggregation applies here too: a conclusion assembled from several agents' partial views inherits the sensitivity of its inputs (`NLB-KROS-013`).

**Agents never impersonate a user or another agent**, per `NLB-NIC-002`'s Representation Boundary, and external communication follows its disclosure requirements.

### Traceability

Every action identifies its originating agent, and the chain is auditable end to end:

```
USER → SUPERVISOR → AGENT → TOOL → RESULT
```

**Every output is traceable to the agent that produced it and the evidence beneath it.** In a single-agent system, "the system said so" is at least locatable. In a population, an untraceable output cannot be attributed, corrected, or learned from — and the agent that produced it will produce the same output again.

---

## Reconciling Multiple Outputs

**Disagreement between agents is a signal, not noise.** Conflicts are surfaced and resolved on evidence quality, source authority, specialization relevance, freshness, and independent verification — never by majority.

**Agreement is weak evidence.** Agents drawing on overlapping models and shared context produce correlated errors, so consensus reflects their common inputs at least as much as the world. Where consensus is used to raise confidence, **the agents must have received meaningfully independent inputs** — otherwise it measures nothing (`NLB-KROS-002`'s no-false-consensus rule).

**Final synthesis runs a fixed sequence**: agent outputs → conflict check → evidence check → quality review → synthesis → result. **Intermediate results may be cached and reused, subject to the freshness rules** in `NLB-KROS-004`.

---

## Failure and Escalation

```
FAILURE → RETRY → FALLBACK AGENT → HUMAN ESCALATION
```

**Escalation by capability** — basic → advanced → specialist → human — where each step is justified by the task exceeding the current level, not by the previous attempt having failed once.

**Escalation to a person happens on**: insufficient confidence, missing permissions, high stakes, contradictory information, or any state where continuing is unsafe. The message states **what happened, why it stopped, what is needed, and what can happen next** — and asks only what is necessary to continue.

**Agent health is tracked** (success rate, error rate, latency, resource use, feedback), versions are rollback-capable, and a degraded version is disabled rather than tolerated (`NLB-NXOS-004`).

---

## Acceptance Criteria

Part 2 is architecturally complete when it supports: allocation (bounded delegation with defined context, limits and deadlines; delegation minimization; specialist preference only on measured advantage; seven orchestration modes chosen against cost; temporary agents with limited scope, data, permissions and lifetime, dissolved on completion; competitive selection informed by performance history); runtime limits (caps on agent count, delegation depth, tool calls, tokens, cost and time; delegation-loop detection distinct from action-loop detection; deadlock detection with evidence request and human escalation; and termination on completion, impossibility, timeout, budget or cancellation); agent security (permission resolution under the requesting agent's identity so delegation moves work but never permission, negotiation bounded from trading away policy, need-to-know context isolation, sensitivity inheritance on aggregated conclusions, no impersonation, and end-to-end action-chain traceability); output reconciliation (evidence-based conflict resolution rather than majority, consensus discounted without input independence, and the fixed synthesis sequence); and failure handling (capability-based escalation, four-field escalation messages asking only what is necessary, tracked agent health, and version rollback).

---

## Principle

**One core → many specialists → controlled collaboration → verified result.**

> Delegation moves work, never permission. An agent that could acquire authority by asking another agent for it has no authority boundary at all — only an unenforced convention.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-13 | Initial multi-agent runtime specification, drawn from source Volume 47 Part 2. Establishes bounded allocation with delegation minimization, seven orchestration modes chosen against cost, temporary agents with defined lifetimes, competitive selection; runtime limits including **delegation depth** and delegation-loop detection distinct from action loops, plus deadlock detection with human escalation; **agent security** — permission resolution under the requesting agent's identity so delegation moves work but never permission, bounded inter-agent negotiation, need-to-know isolation and full action-chain traceability; and output reconciliation where disagreement resolves on evidence rather than majority and consensus is discounted without input independence. Agent definition, teams, lifecycle, sandboxing and kill switches remain with `NLB-NXOS-004`; the output contract with `NLB-KROS-002`; pipeline planning with `NLB-KROS-004`. |

---

**End of Part 2 (Version 1.0)**
