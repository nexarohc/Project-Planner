# 📖 NEXALIFE BIBLE — Volume 05

## Universal Planner Engine (UPE)

| Field | Value |
| --- | --- |
| Document ID | NLB-05 |
| Version | 1.0 |
| Status | Master Draft |
| Priority | ★★★★★ (Foundation) |
| Supersedes | — |
| Last updated | 2026-08-05 |

---

## Purpose

Volume 04 catalogued 503 planners across seventeen Life Domains, and that catalogue will keep growing. NexaLife cannot be engineered as 503 separate applications — it must be engineered as **one configurable engine** that every catalogued planner is an instance of.

The Universal Planner Engine (UPE) is that engine. A Study Planner, a Startup Planner, a Marathon Training Planner, and a Clinical Trial Planner are not different pieces of software. They are the same engine, configured differently.

This is the direct consequence of NLB-00 Article V (Universal Module Structure Conformance): consistency across hundreds of planners is only achievable if it is structural, not a style guide developers are asked to remember.

---

## Core Architecture

Every planner is produced by passing configuration through four layers:

```
Presentation Layer        →  what the user sees and touches (NLB-08)
        ↓
Planner Engine             →  this volume
        ↓
AI Orchestration Layer     →  specialist reasoning and delegation (NLB-06)
        ↓
Universal Data Layer       →  the shared source of truth (NLB-07)
```

Each layer has one responsibility and talks to its neighbours through a stable interface. A change inside one layer — a new widget type, a new AI specialist, a new storage backend — should never require changes in the layers above or below it, only a version bump on the interface if the contract itself changes.

---

## The Planner Object Model

Every planner, regardless of domain or catalogue tier, is represented as one configuration object. This is what "one engine, hundreds of planners" means concretely: a new planner is authored by producing a new object, not by writing new application code.

| Attribute | Purpose |
| --- | --- |
| Planner ID | Stable identity, independent of name (mirrors the `PU-DD-NNN` scheme in NLB-04) |
| Name & Description | User-facing identity |
| Category & Life Domain | Placement per NLB-03 |
| Owner | The user, team, or organization the planner belongs to |
| Visibility | Private, shared, organization, public template |
| Permissions | Role bindings — see Permission Model below |
| AI Configuration | Which specialists (NLB-06) this planner registers with Nexa |
| Page Set | Which Universal Pages are enabled, and any planner-specific pages |
| Widget Configuration | Which dashboard widgets are available and their defaults |
| Automation Rules | Trigger/action bindings scoped to this planner (NLB-09) |
| Analytics Configuration | Which base and planner-specific metrics apply |
| Calendar & Goal Integration | Bindings into the Calendar Hub and Goal Planner (NLB-04 hubs) |
| Notification Settings | Default channels and thresholds |
| Offline Settings | Which capabilities must work offline |
| Localization | Language, region, and format defaults |
| Version | The planner definition's own version, independent of user data |

A planner definition is data. It can be authored by NexaLife, by an organization, by a user, or by the Marketplace (NLB-15) — the engine does not distinguish between them at runtime.

---

## Universal Pages

Every planner inherits the same page set, satisfying NLB-03's Universal Module Structure. A planner may add pages specific to its domain, but may not remove a required page without a recorded exception (NLB-00 Article V).

| # | Page | Role |
| --- | --- | --- |
| 1 | Dashboard | Modular, widget-based overview |
| 2 | Planner Workspace | The primary working surface |
| 3 | Calendar | Time-bound items, synced with the Calendar Hub |
| 4 | Timeline | Chronological view across the planner's history |
| 5 | Tasks | Discrete units of work |
| 6 | Goals | Linked outcomes, synced with the Goal Planner |
| 7 | AI Assistant | The planner's registered specialists, in context |
| 8 | Analytics | Metrics scoped to this planner |
| 9 | Reports | Generated, shareable summaries |
| 10 | Documents | Files bound to this planner |
| 11 | Templates | Reusable starting points |
| 12 | Automations | Trigger/action rules scoped here |
| 13 | Notifications | Planner-scoped alerts and their settings |
| 14 | Collaboration | People with access, and their activity |
| 15 | Activity History | An auditable record of change |
| 16 | Search | Scoped to this planner, federated into Global Search (NLB-08) |
| 17 | Settings | Configuration surfaced to the owner |

---

## Dashboard Engine

The dashboard is the planner's front page, and it is entirely composed of widgets — no planner hand-builds its own dashboard layout in code.

**Supported widget classes**: KPI cards, progress rings, charts, tables, kanban boards, calendars, heatmaps, timelines, AI recommendation cards, alerts, recent-activity feeds, goal trackers, habit/streak trackers, notes, leaderboards, community updates.

Users can rearrange, resize, add, remove, and save layouts. A saved layout is itself an object the Marketplace can distribute — a "layout" is not fundamentally different from a "template."

---

## Universal Task Engine

Every planner can create tasks through one shared engine rather than a bespoke one. Tasks support: priorities, dependencies, recurrence, checklists, labels, attachments, comments, mentions, estimates vs. actuals, time tracking, reminders, AI-generated subtasks, and configurable workflow states.

Workflow states are planner-configurable (a Study Planner and a Software Project Planner do not want the same state machine) but are drawn from one underlying state-machine primitive, so automation (NLB-09) and analytics (this volume) can reason about "task state" uniformly across every planner.

---

## Universal Calendar Engine

**Views**: day, week, month, quarter, year, timeline, agenda.

**Capabilities**: drag-and-drop rescheduling, multi-timezone display, recurrence, resource scheduling, availability windows, shared calendars, and AI-assisted scheduling suggestions routed through Nexa (NLB-06).

Every planner's calendar items compose into the Calendar Hub (NLB-04, PU-01-010) rather than existing as an island — this is the engine-level mechanism behind the cross-domain scheduling examples in NLB-04 (the marathon goal, the exam schedule, the family trip).

---

## AI Integration Model

Every planner automatically connects to Nexa. A planner declares which specialist AI agents (NLB-06) it registers — for example, a Study Planner registers Tutor AI, Math AI, and Coding AI; a Business Planner registers CEO AI, Sales AI, and Marketing AI. Nexa coordinates across a planner's registered specialists, and across planners, when a request spans domains.

The engine's obligation here is narrow and specific: it must expose a stable registration contract so that any planner — built by NexaLife, an organization, or the Marketplace — can declare its specialists without the AI Orchestration Layer needing planner-specific code. The orchestration behaviour itself belongs to NLB-06.

---

## Automation Engine

Every planner supports event-driven automation through the shared engine specified in full in NLB-09. At the planner-engine level, this means every planner object exposes:

- A **trigger surface** — the events this planner type can emit (task completed, deadline approaching, goal reached, and so on).
- An **action surface** — the operations this planner type accepts (create task, update state, generate report, and so on).

NLB-09 defines the automation lifecycle, the trigger/action library, and the marketplace for workflows. This volume's responsibility is only to guarantee every planner exposes both surfaces consistently.

---

## Analytics Engine

Every planner automatically exposes a base set of analytics: completion rates, time spent, goal progress, trend analysis, AI-generated insights, forecasts, streaks, heatmaps, leaderboards, and performance summaries. Planners extend this base set with domain-specific metrics (e.g., a Finance planner adds net-worth trend; a Sports planner adds performance-versus-opponent) without redefining how the base metrics are computed.

---

## Template Engine

Templates may be built-in, user-created, team-scoped, Marketplace-sourced, or AI-generated. A template is a partially or fully populated Planner Object Model — the same object described above, pre-filled. Templates carry their own version, independent of the planner instances created from them, so a template update can be offered to existing users without silently overwriting their customizations.

---

## Permission Model

| Role | Typical scope |
| --- | --- |
| Owner | Full control, including deletion and ownership transfer |
| Administrator | Full control except ownership transfer |
| Manager | Manage content and members, not settings |
| Editor | Create and modify content |
| Contributor | Add content, limited modification of others' content |
| Commenter | Comment only |
| Viewer | Read-only |
| Guest | Time- or scope-limited access |

Permissions are granular and inherit downward (organization → workspace → planner → page → item) unless explicitly overridden at a lower level, consistent with NLB-00 Article VI.

---

## Search

Every planner supports keyword search, semantic AI search, filters, saved searches, and natural-language queries, and every planner's index feeds Global Search (NLB-08) — a planner never maintains an index the platform can't see into.

---

## Offline Support

Core planning functions continue without connectivity: viewing and editing tasks, calendar items, and notes created or cached locally. On reconnection, the engine synchronizes changes, detects conflicts, and either resolves them automatically (per NLB-07's conflict rules) or surfaces them for manual resolution — never silently discards either side.

---

## Localization

The engine supports multiple languages, regional calendars, time zones, number/date/currency formats, and right-to-left layouts as first-class configuration on the Planner Object Model, not as a later translation pass.

---

## Extensibility

The engine exposes extension points rather than requiring core changes, for:

- New planner types (new Planner Object Model instances)
- New dashboard widgets
- New automation triggers and actions (registered into NLB-09's library)
- New AI agents (registered into NLB-06)
- New report types
- New integrations
- New templates

This is the mechanism, not just the aspiration, behind NLB-00 Article V: a thousandth planner should be as cheap to add as the hundredth, because none of them require touching the engine itself.

---

## Performance Goals

The engine should aim for responsive interaction under normal load, efficient incremental synchronization, scalable data access as planner count and data volume grow, modular loading (a user's device only loads the planner components in active use), robust error handling, and production-grade observability. These goals are qualitative by design — see NLB-07 for why this volume does not commit to fixed numeric targets.

---

## Design Principle

**No planner should require changes to the Universal Planner Engine to exist.** Planners are assembled from reusable capabilities and extended through well-defined interfaces. If building a new planner requires a change to this engine, the gap belongs to this volume, not to a one-off exception in the planner.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial Universal Planner Engine specification. Establishes the four-layer architecture, the Planner Object Model, Universal Pages, and the shared Dashboard, Task, Calendar, Analytics, and Template engines. |

---

**End of Volume 05 (Version 1.0)**
