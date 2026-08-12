# 📖 NEXALIFE BIBLE — Nexa Intelligence Core (NIC)

## Part 2 — Nexa Action Engine (NAE): Intelligent Task Execution & Workflow Automation

| Field | Value |
| --- | --- |
| Document ID | NLB-NIC-002 |
| Series | Nexa Intelligence Core (Volume 22) |
| Version | 1.2 |
| Status | Master Draft |
| Priority | ★★★★★ (Action & Automation Framework) |
| Supersedes | — |
| Last updated | 2026-08-12 |

---

## Purpose

This is where Nexa becomes an AI that gets work done, not just one that provides advice. The Nexa Action Engine (NAE) transforms user intentions into structured, multi-step workflows: instead of responding with information alone, Nexa coordinates authorized actions across the NexaLife platform and connected services.

**Architectural note.** Actions such as sending emails, placing orders, making payments, booking travel, or making phone calls depend on integrations, permissions, and platform capabilities defined elsewhere — the Connector Architecture (`NLB-12`), the User Consent and Permission Engine (`NLB-10`), and the Automation & Workflow Engine (`NLB-09`). This volume treats every such action as an **authorized capability that requires explicit user approval and a supported integration** — never as something Nexa can simply decide to do. Users remain in control of sensitive actions through permissions and approval checkpoints throughout.

---

## Action Philosophy

Nexa should understand the user's goal, break complex work into manageable steps, determine which steps can be automated, request approval when required, execute authorized actions reliably, and explain progress and outcomes. This is `NLB-NIC-001`'s orchestration model extended from *answering* to *acting*.

---

## Action Lifecycle

```
User Goal → Goal Analysis → Task Decomposition → Workflow Planning
  → Permission Check → User Approval (if required)
  → Execution → Verification → Completion Report
```

Every workflow instance runs through this lifecycle — it is the Study Planner's Assignment Workflow (`NLB-SP-001`) and LOUPE's Cross-Planner Automation (`NLB-21`) generalized into the single execution path every Nexa-initiated action follows.

---

## Action Types

| Category | Examples |
| --- | --- |
| Planner Actions | Create goals, update tasks, schedule events, generate plans, track habits |
| Document Actions | Generate reports, create presentations, draft proposals, build study notes, export summaries |
| Communication Actions | Draft emails, send emails, prepare messages, schedule meetings, create follow-up reminders — with user authorization and supported integrations |
| Calendar Actions | Create/update events, resolve conflicts, suggest meeting times, coordinate schedules |
| Research Actions | Collect sources, organize references, summarize findings, build reading lists, generate research outlines |
| File Actions | Organize folders, rename files, categorize documents, archive completed work, export planner data |
| Cross-Planner Actions | Update study and calendar together; connect fitness plans with travel; coordinate finance goals with purchases; link project milestones to business plans |

Sensitive actions (Communication and any action touching money, external sharing, or deletion) require confirmation unless the user has explicitly configured trusted automation, per the Approval Checkpoints below. Research Actions never relieve the user of responsibility for evaluating sources, consistent with `NLB-SP-002`'s Research AI guidance.

---

## Multi-Step Planning

**Worked example.** *"Help me prepare for my certification exam."* Nexa reviews available time, creates a study plan, schedules sessions, builds a revision calendar, generates a practice schedule, prepares reminders, and monitors progress. **Nexa presents the plan before execution wherever significant changes are involved** — the same "explain before you commit" discipline as `NLB-11`'s Decision Support, now applied to a plan that will actually write to the user's calendar and tasks, not just describe an option.

---

## Workflow Engine

Each workflow instance carries a goal, tasks, dependencies, conditions, permissions, progress state, completion criteria, and a rollback strategy where applicable — the same shape as the automation lifecycle in `NLB-09`, instantiated per user request rather than authored once as a reusable rule.

---

## Approval Checkpoints

Actions that normally require confirmation: sending emails, initiating phone calls, editing large amounts of user data, sharing files externally, booking travel, purchasing products, financial transactions, and deleting information. Users can configure trusted workflows where appropriate — the same "user can pre-authorize a class of action" mechanism `NLB-09` establishes for Approval Flows generally.

---

## The Autonomy Ladder

Approval Checkpoints answer *whether* a given action needs confirmation. This answers the prior question: **how much independence a capability has been granted at all.** Six levels, assigned per task type rather than globally:

| Level | Nexa may |
| --- | --- |
| **0** | Answer only |
| **1** | Suggest |
| **2** | Prepare and draft |
| **3** | Execute with per-instance approval |
| **4** | Execute predefined low-risk tasks without per-instance approval |
| **5** | Operate continuously under a standing delegation |

A single user typically runs several levels at once — research at 4, drafting at 2, sending at 3, anything financial stricter still. **Autonomy is granted per capability and never inherited**: a workflow trusted to monitor sources has not thereby been trusted to send messages.

**Level 5 is bounded, always.** Continuous operation remains constrained by explicit permissions, policies, budgets, and stop controls; it is not a state in which Nexa acts freely, only one in which it acts repeatedly.

### Delegation contracts

Every autonomous workflow carries an explicit contract, and **the forbidden list is stated rather than implied**:

```
PURPOSE      Monitor project
ALLOWED      Read sources · Analyze changes · Notify user
NOT ALLOWED  Send external messages · Change records · Spend money
BUDGET       7 days · 50 actions · no spending
ESCALATION   On conflict or confidence below threshold
```

Naming what a workflow may not do is what makes a delegation reviewable — a permission list alone leaves the boundary to inference, and inference is where autonomy quietly widens.

**Delegations expire and are renewed deliberately**: *"your market-monitoring delegation expires tomorrow — renew?"* An open-ended grant is one the user stops reconsidering.

**Action quotas** bound how much a workflow can do, so a misconfigured automation reaches a limit rather than running unbounded.

**Pause conditions** halt a workflow when confidence drops below threshold, sources conflict, scope changes, budget is exceeded, an unexpected action appears, or permissions change. Each of these means the situation is no longer the one the delegation was granted for.

### Oversight

**Action risk classification** — low (read, summarize), medium (create, modify), high (external action, commitment), critical (irreversible or high-impact) — sets confirmation strength, so a summary is not gated like a payment and a payment is never gated like a summary.

**No dark autonomy.** Nexa never conceals consequential autonomous activity. A **delegation centre** shows everything currently delegated and its state, and a complete autonomy log records what happened, why, when, which agent, which tools, what data, and what result.

**Stop is always available**, and after stopping, the state is reported plainly: *"stopped after completing 7 of 12 steps; no further actions were taken."* A stop control whose aftermath is unclear is not one users will rely on.

> Trust comes from transparency, control, evidence, reversibility, and consistency — not from a friendly personality.

---

## The Representation Boundary

Nexa acts on the user's behalf. It is never the user, and the distinction has to survive contact with third parties.

**Internally**, the framing is *"I am acting according to your approved workflow"* — never *"I am you."* A system modelling someone's preferences well enough to draft in their voice is close enough to the line that the line must be stated (`NLB-KROS-007`'s bounded digital twin).

**Externally, Nexa identifies itself where identification is required** — by law, by platform rule, or by the reasonable expectation of the person receiving the communication. A recipient who believes they are corresponding with a person, and is not, has been misled regardless of how accurate the content is; and the cost of that discovery falls on the user whose name is attached.

**Nexa never fabricates user approval.** It does not represent a draft as reviewed, an action as authorized, or a decision as made when the user has not made it. This is the outward-facing form of the no-dark-autonomy rule: the log protects the user's visibility, and this protects everyone else's.

Sensitive external communication runs draft → user review → send (`NLB-CPIOS-001`).

---

## Action History

Maintains requested action, time, outcome, user approvals, errors, and rollback availability, so users can review past actions — the Nexa-Action-specific view onto the platform Audit Log (`NLB-07`, `NLB-10`).

---

## Recovery

If execution fails, Nexa explains what happened, preserves completed steps, identifies failed steps, suggests recovery options, and resumes where possible — the same recovery discipline `NLB-09` requires of automation error handling generally, applied to a live, user-initiated action.

---

## Automation Rules

Users may define rules such as: after completing a study session, schedule the next revision; archive completed projects after 30 days; create a weekly learning report every Friday. Rules remain editable and disableable at any time — these are user-authored instances of `NLB-09`'s automation lifecycle, entered through conversation with Nexa rather than the Visual Workflow Builder.

---

## Long-Running Tasks

Supports workflows that continue over time: research projects, exam preparation, multi-week travel planning, job application tracking. Nexa tracks progress and resumes work as authorized — a long-running task is a workflow instance whose lifecycle spans many sessions, not a different kind of object.

---

## Proactive Assistance

With permission, Nexa may suggest rescheduling due to calendar conflicts, reminding about approaching deadlines, identifying duplicated work, or suggesting preparation for upcoming events. **Suggestions never become mandatory** — the Action Engine's application of `NLB-11`'s Proactive Assistance requirement.

---

## Context Awareness

Before acting, Nexa may consider the current planner, calendar, user preferences, existing goals, time available, and connected services. Recommendations remain transparent, per `NLB-NIC-001`'s Context Engine.

---

## Integration Layer

The Action Engine integrates with supported services — email providers, calendars, cloud storage, productivity tools, communication platforms, and future Marketplace extensions — through the Connector Architecture already defined in `NLB-12`. Each integration declares its supported actions, required permissions, and failure behavior; the Action Engine does not maintain a parallel integration model.

---

## Safety

The engine prevents duplicate execution, validates prerequisites, respects permissions, confirms irreversible operations, logs significant actions, and allows cancellation where practical — the concrete safeguards behind `NLB-NIC-001`'s Safety section, specific to actions that change state in the world rather than just producing a response.

---

## Auditability

Users can see what Nexa did, when it happened, which permissions were used, what data was affected, and whether the action succeeded — full transparency into every executed workflow, not just a summary.

---

## Accessibility

Action workflows support keyboard navigation, voice initiation where enabled, screen readers, localization, and mobile and desktop interfaces.

---

## Performance

Users receive immediate acknowledgement of requests, clear progress indicators, completion notifications, and meaningful error messages if problems occur — an action that appears to hang with no feedback is a defect regardless of whether it eventually succeeds.

---

## Extensibility

New action providers register their available actions, input requirements, output schema, permissions, error handling, and capability metadata — the same specialist/tool registration contract established in `NLB-06` and `NLB-NIC-001`, applied to action-taking capability specifically. This is what lets Nexa expand without the Action Engine itself being redesigned.

---

## Design Principle

Nexa should reduce the effort required to accomplish meaningful work while ensuring users remain informed, in control, and responsible for important decisions. **The Action Engine automates routine tasks, coordinates complex workflows, and provides transparent oversight — it does not act autonomously without user awareness.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.2 | 2026-08-12 | Additive (MINOR): the Representation Boundary — Nexa acts on the user's behalf and is never the user; it identifies itself externally where identification is required by law, platform rule, or the recipient's reasonable expectation; and it never fabricates user approval by representing a draft as reviewed, an action as authorized, or a decision as made. The outward-facing counterpart to the no-dark-autonomy rule. |
| 1.1 | 2026-08-12 | Additive (MINOR): the Autonomy Ladder added — six levels assigned per capability and never inherited, delegation contracts stating forbidden actions explicitly alongside allowed ones, expiration and deliberate renewal, action quotas, pause conditions, action risk classification driving confirmation strength, the no-dark-autonomy rule with a delegation centre and complete autonomy log, and reported state after a stop. Promoted here from the KROS source material because autonomy is platform-level: `NLB-KROS-007` applies this ladder to knowledge work rather than defining a second one. |
| 1.0 | 2026-08-05 | Initial Nexa Action Engine specification. Establishes the Action Lifecycle, seven Action Types, Approval Checkpoints, and Automation Rules — all built on the Connector Architecture (NLB-12) and Automation Engine (NLB-09) already specified, never a parallel system. |

---

**End of Part 2 (Version 1.0)**
