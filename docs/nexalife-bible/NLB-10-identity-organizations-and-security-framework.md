# 📖 NEXALIFE BIBLE — Volume 10

## Identity, Organizations & Security Framework (IOSF)

| Field | Value |
| --- | --- |
| Document ID | NLB-10 |
| Version | 1.0 |
| Status | Master Draft |
| Priority | ★★★★★ (Critical Infrastructure) |
| Supersedes | — |
| Last updated | 2026-08-05 |

---

## Purpose

This is the last major platform foundation before individual planners are designed. Without it, NexaLife cannot safely support individuals, families, schools, businesses, or enterprises at once — which NLB-01 requires it to do.

This volume defines who users are, how they authenticate, what they can access, how organizations operate, how permissions are granted, how data stays secure, how privacy is protected, and how trust is maintained. Every module in the platform depends on it: the Permission Model in NLB-05, the Data Security section of NLB-07, and the Automation security rules in NLB-09 are all downstream views of the framework defined here.

---

## Design Philosophy

Security should be **invisible when possible, powerful when necessary, never annoying, always trustworthy.** Privacy is not an optional feature — it is a platform principle, per NLB-00 Article VI.

---

## Universal Identity System

Every person receives one unique NexaLife identity, carrying: profile, username, display name, avatar, bio, languages, time zone, country, devices, AI preferences, accessibility preferences, notification preferences, and privacy preferences. Users control what is visible to others — identity is a single object shared across every organization a person belongs to, not a separate account per workspace.

---

## Account Types

| Type | Typical holder |
| --- | --- |
| Personal | An individual using NexaLife for their own life |
| Student | Enrolled learner, education-domain defaults |
| Parent | Manages a Family workspace and child profiles |
| Teacher | Manages classes and cohorts |
| Creator | Publishes content and Marketplace assets |
| Professional | Career- and business-domain defaults |
| Small Business | Owns a business workspace |
| Enterprise User | Member of a larger organization |
| Organization Administrator | Administers an organization's workspaces and policies |
| Super Administrator | Platform-level operator |

A user may belong to multiple organizations under multiple account types while holding a single identity — a parent who is also an employee does not need two accounts.

---

## Authentication

Supported methods: email + password, passkeys, multi-factor authentication, organization single sign-on (SSO), trusted device management, and session management. Authentication balances convenience with security rather than defaulting to whichever is easier to build — this is the concrete form of the Design Philosophy above.

---

## Organization Architecture

```
Platform
  │
Organization
  │
Departments
  │
Teams
  │
Workspaces
  │
Projects
```

Organizations may define their own structure within platform limits — the hierarchy above is a ceiling, not a requirement that every organization use every level.

---

## Workspaces

Users create or join multiple workspaces — Personal, Family, School, University, Startup, Company, Research Lab, Sports Club, and so on. Each workspace has independent settings, members, and permissions, and maps naturally onto the Life Domains a user is active in (NLB-03): a Family workspace is the natural home for LD-08 planners, a Company workspace for LD-04.

---

## Role-Based Access Control

| Built-in role | Typical scope |
| --- | --- |
| Owner | Full control, including deletion and transfer |
| Administrator | Full control except ownership transfer |
| Manager | Manages content and members |
| Team Lead | Leads a team within a workspace |
| Editor | Creates and modifies content |
| Contributor | Adds content, limited modification of others' |
| Reviewer | Approves or rejects submitted work |
| Commenter | Comments only |
| Viewer | Read-only |
| Guest | Time- or scope-limited access |

This list matches NLB-05's Planner-level Permission Model by design — the planner engine's roles are this volume's roles, not a parallel scheme. Organizations may define custom roles on top of these. Permissions inherit downward through the Organization Architecture but are overridable at any lower level when a genuine exception exists.

---

## Permission Engine

Permissions can scope to the entire platform, an organization, a workspace, a planner, a dashboard, a calendar, a task, a goal, a document, an AI agent, an automation, the Marketplace, a community, a competition, a report, or a file. Every permission grant is **explicit and auditable** — nothing is implicitly permitted because it would be convenient.

---

## Privacy Controls

Users choose: public profile visibility, search visibility, friend requests, community participation, activity sharing, AI personalization, data export, and data deletion. Defaults favor user protection — a new user's data is private until they choose otherwise, never the reverse.

---

## Device Management

Users can view active devices, rename them, remove them, end sessions remotely, and receive alerts for new sign-ins.

---

## Security Dashboard

Displays active sessions, connected services, recent logins, MFA status, device history, security recommendations, and account recovery options in one place — the user-facing surface this volume owns, rendered through the Universal Components defined in NLB-08.

---

## Audit Logs

Tracks login attempts, permission changes, organization administration, automation execution, marketplace transactions, and sensitive configuration changes. This is the same Audit Log entity defined in NLB-07 — this volume is the primary producer and consumer of it, not a second logging system.

---

## Organization Administration

Administrators manage members, teams, roles, policies, shared planners, shared templates, shared AI agents, shared workflows, billing, licensing, and workspace settings — the organizational control surface that sits above individual workspace settings.

---

## Enterprise Features

Enterprise workspaces, department isolation, centralized administration, policy enforcement, identity federation, compliance reporting, data residency options where infrastructure supports them, and custom branding. These are extensions of the same architecture individuals use, per the same "one engine, many configurations" discipline as NLB-05 — not a separate enterprise system.

---

## Data Protection

Encryption in transit and at rest, backup and recovery, secure key management, retention policies, soft delete, and restore capabilities. This section is this volume's requirement on the Universal Data Platform; NLB-07's Data Security and Data Lifecycle sections are where it is actually implemented.

---

## User Consent

Nexa (NLB-06/NLB-11) must always respect explicit user consent — for connecting external accounts, accessing contacts, using location, reading connected files, accessing wearable data, or performing sensitive actions. Consent must be understandable, granular, and revocable at any time; a permission the user can't find how to revoke is not a valid permission.

---

## Account Recovery

Recovery codes, verified email, trusted devices, and — where appropriate — organization administrator recovery. Recovery processes are designed to minimize the risk of unauthorized access, since a recovery flow is also the most common attack surface for account takeover.

---

## Trust Center

A dedicated Trust Center lets users review privacy settings, security settings, connected accounts, data exports, permission history, AI data usage, and audit history in one place. The goal is transparency — everything this volume governs should be inspectable by the user it governs, not just by administrators.

---

## Compliance Architecture

The platform is designed so organizations can meet applicable regulatory and contractual requirements relevant to their jurisdiction and industry. Rather than hardcoding support for specific regulations into this volume, the architecture stays flexible enough to accommodate future compliance modules and reporting needs — the same "properties, not fixed targets" discipline NLB-07 applies to scale, applied here to regulation.

---

## Design Principle

Every security decision must answer:

1. Does it protect the user?
2. Does it preserve usability?
3. Is it transparent?
4. Can it scale?

If any answer is "no," the solution is redesigned.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial Identity, Organizations & Security Framework. Establishes Universal Identity, the Organization Architecture, Role-Based Access Control (aligned with NLB-05's role model), the Permission Engine, and the Trust Center. |

---

**End of Volume 10 (Version 1.0)**
