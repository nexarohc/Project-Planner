# 📖 NEXALIFE BIBLE — NXOS: Nexa Operating Layer

## Part 4 — AI Agent Ecosystem

| Field | Value |
| --- | --- |
| Document ID | NLB-NXOS-004 |
| Series | NXOS — Nexa Operating Layer (Volume 23) |
| Version | 1.1 |
| Status | Master Draft |
| Priority | ★★★★★ (Specialist Registration Standard) |
| Supersedes | — |
| Last updated | 2026-08-12 |

---

## Purpose

Instead of one AI, NexaLife has hundreds of specialized ones. Those specialists already exist throughout this Bible — every Life Domain in `NLB-04` lists its own AI Specialists (Tutor AI, Nutritionist AI, Legal AI, CEO AI, and dozens more across 17 domains), and `NLB-SP-002` already gives 12 of them full responsibility definitions for the Study Planner alone. **This volume does not re-list them.** It defines the one registration schema every specialist — cataloged or future, platform-built or Marketplace-published — must satisfy, so that hundreds of independently authored specialists remain interoperable under one orchestrator (`NLB-06`) instead of each inventing its own shape.

---

## The Registration Schema

Every AI specialist declares:

| Field | Defines |
| --- | --- |
| Capabilities | What the specialist can actually do — the action and response types it supports |
| Knowledge Scope | What domain knowledge it draws on, and explicitly what it does *not* cover |
| Tool Access | Which platform tools (`NLB-06`'s Tool Execution Layer) it may call |
| Memory Scope | Which memory kinds and layers (`NLB-NXOS-003`) it can read or write |
| Permission Model | What user authorization it requires before acting, per `NLB-10` |
| Collaboration Rules | How it shares context with, and defers to, other specialists |
| Escalation Logic | When it hands a request to Nexa, to a human, or to a more specialized agent |

This schema is the same registration contract already required by `NLB-06`'s Specialist AI Ecosystem and `NLB-NIC-004`'s AI Tool Registry — this volume is where it is written out in full, once, so every future specialist (platform or third-party) is specified against the same seven fields rather than an ad hoc description.

---

## Worked Examples Against the Schema

**Doctor Assistant AI** (`NLB-04`, LD-06 Health)

- Capabilities: symptom pattern discussion, appointment prep, medical record summarization
- Knowledge Scope: general health information; explicitly *not* diagnosis or prescription
- Tool Access: Health Dashboard, Appointment Planner, Medical Record Vault
- Memory Scope: Planner Memory (Health), with explicit per-item consent for sensitive records
- Permission Model: highest sensitivity tier — see Sensitivity Tiers below
- Collaboration Rules: defers to Nutritionist AI and Fitness Coach AI for lifestyle recommendations
- Escalation Logic: escalates to "consult a licensed professional" framing whenever a request approaches diagnosis

**Legal AI** (`NLB-04`, LD-04 Business)

- Capabilities: contract organization, document review support, deadline tracking
- Knowledge Scope: general legal document structure; explicitly *not* jurisdiction-specific legal advice
- Tool Access: Document Vault, Legal Matter Planner
- Memory Scope: Workspace Memory, organization-scoped
- Permission Model: organization administrator authorization required for shared matters
- Collaboration Rules: coordinates with Compliance & Audit Planner specialists
- Escalation Logic: escalates to human legal counsel for anything jurisdiction-specific or binding

These two examples show why the schema, not a longer name list, is the actual contribution: a Psychology Coach, an Investment Research Assistant, an Architecture Assistant, or any future specialist is specified the same way, and Nexa's orchestrator (`NLB-06`) can reason about all of them uniformly without special-casing each one.

---

## Sensitivity Tiers

Not every specialist carries the same risk if wrong. Specialists are classified into tiers that determine default permission strictness and escalation aggressiveness:

| Tier | Examples | Default posture |
| --- | --- | --- |
| Advisory | Study Coach, Writing Coach, Travel Agent | Standard permission model; low escalation threshold |
| Regulated-adjacent | Doctor Assistant, Legal AI, Tax AI, Financial Advisor | Highest sensitivity; explicit non-diagnosis/non-advice framing required; frequent escalation to human professionals |
| Operational | DevOps AI, Coding AI, Automation-triggering specialists | Approval gates on any action with real-world side effects, per `NLB-NIC-002` |

Tiering is metadata on the Registration Schema (Permission Model field), not a separate system — it exists so a Marketplace-published specialist (`NLB-13`, `NLB-NIC-004`) can't quietly claim Advisory-level looseness while operating in Regulated-adjacent territory.

---

## Collaboration Rules in Practice

Collaboration Rules formalize what `NLB-06`'s Multi-Agent Collaboration and `NLB-NXOS-002`'s Multi-Agent Coordination already assume: a specialist knows which other specialists it commonly works alongside, what context it shares with them, and where its own authority ends. This is what keeps a "help me prepare for an exam while training for a marathon" request (`NLB-04`, `NLB-11`) from requiring Nexa to hand-code every possible specialist pairing — each specialist's own Collaboration Rules make the pairing discoverable.

---

## Escalation Logic in Practice

Escalation is not a fallback for failure — it is a designed outcome. A specialist escalates to Nexa when a request exceeds its Knowledge Scope, to another specialist when Collaboration Rules indicate a better fit, and to a human (the user, a professional, or an administrator) when the Sensitivity Tier requires it regardless of the specialist's own confidence. `NLB-NXOS-002`'s Human Approval Gates are the mechanism; this volume is where each specialist declares when it must trigger one.

---

## Marketplace-Published Specialists

Third-party specialists published through `NLB-13` and `NLB-NIC-004` must satisfy this same seven-field schema during certification. A specialist that cannot state its Knowledge Scope boundary or Escalation Logic does not pass review — the schema is what makes an AI Skill's certification (`NLB-NIC-004`) checkable rather than a matter of trusting the publisher's description.

---

## The Capability Declaration

Registration (above) says what an agent *is*. The capability declaration says what it may do — **and, explicitly, what it may not**:

```
CAN     ✓ Research companies  ✓ Compare suppliers  ✓ Generate reports
CANNOT  ✕ Send emails  ✕ Make purchases  ✕ Modify accounts
```

The negative list is the load-bearing half. A permission list alone leaves the boundary to inference, and an agent's limits are exactly what a user needs to see before granting it anything.

**Permissions are granted independently of installation.** Installing an agent confers no access to private data or external systems; discovery → capabilities → permissions → install → configure → **authorize** → activate keeps the two decisions separate, so "I want to try this" never doubles as "I trust this with my email."

**Dependencies are disclosed before activation** — a required agent, connector, data source, model, skill, or external service. An agent whose real reach is one hop away through an undisclosed dependency has not actually declared its capabilities.

**A permission change on update requires fresh review**: *"this update requests access to your email — review before enabling."* Silent permission growth across versions is the most reliable way an ecosystem loses the boundary it started with.

---

## Agent Teams

Multiple agents can work one objective under the orchestrator, with distinct roles — researcher, analyst, **critic**, writer, **verifier**, executor. The critic checks for missing evidence, logical errors, contradictions, and unsupported assumptions; the verifier checks only whether claims are supported by available evidence.

**Agent debate**: for selected questions, agents analyze independently and their conclusions are compared rather than merged.

**Consensus is not truth**, and the display says so:

```
Agent A → Supports   Agent B → Supports   Agent C → Challenges
Evidence → Mixed
```

**Dissent stays visible.** A minority conclusion that is dropped because it was outvoted has been discarded on the least relevant criterion available — agents agreeing tells you about the agents, and models sharing training data share their errors.

**Quality gates** run before final output — evidence, logic, policy, permissions, output — and a failed gate blocks with a reason: *"the report is not ready because two major claims remain unverified."*

---

## Agent Lifecycle & Stop Controls

Agents are marked **Active / Deprecated / Retired**, and staleness is surfaced: *"this agent has not been maintained for 11 months."* **Replacement recommendations favour narrower permission** — *"a newer agent provides the same capability with fewer permissions"* — which is the correct default for an ecosystem where permission creep is the usual drift.

**Sandbox before production**: agent → sandbox → test inputs → **tool simulation** → security review → production, per `NLB-13`'s Sandbox Model. Dangerous or external actions are simulated, never performed, during testing.

**Security events** are monitored: unexpected tool calls, permission escalation, repeated failures, anomalous behaviour.

**Kill switches at three scopes** — one agent, one workflow, all automation — available to the user and, in organizations, to an authorized administrator. Stopping is a **safe shutdown**, not an abort:

```
STOP NEW ACTIONS → FINISH SAFE OPERATIONS → CLOSE SESSIONS → SAVE STATE → REPORT
```

Killing an agent mid-write can leave worse damage than the behaviour being stopped. The sequence is what makes the control usable in the moment it is actually needed.


---

## Design Principle

A platform with hundreds of specialists stays coherent only if every specialist is legible the same way. **The value of this volume is the seven fields, not the roster** — the roster already lives in `NLB-04` and grows with every new planner; the schema is what keeps that growth from becoming chaos.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.1 | 2026-08-12 | Additive (MINOR): the capability declaration with an explicit CANNOT list, permissions granted independently of installation, disclosed dependencies, fresh review on permission-changing updates; agent teams with critic and verifier roles, agent debate, consensus explicitly not treated as truth, visible dissent, and quality gates before output; agent lifecycle states with staleness surfacing and replacement recommendations favouring narrower permission, sandbox-with-tool-simulation before production, security-event monitoring, and three-scope kill switches with a safe-shutdown sequence. Drawn from the KROS source material and placed here because the agent ecosystem is platform-level. |
| 1.0 | 2026-08-05 | Initial AI Agent Ecosystem specification. Establishes the seven-field specialist registration schema (Capabilities, Knowledge Scope, Tool Access, Memory Scope, Permission Model, Collaboration Rules, Escalation Logic) and three Sensitivity Tiers, worked through Doctor Assistant AI and Legal AI as examples rather than re-cataloging specialists already listed in NLB-04. |

---

**End of Part 4 (Version 1.0)**
