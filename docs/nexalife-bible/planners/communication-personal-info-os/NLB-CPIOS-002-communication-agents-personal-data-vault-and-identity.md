# 📖 NEXALIFE BIBLE — Communication & Personal Information Operating System (CPIOS)

## Part 2 — Communication Agents, Automation Safety, Personal Data Vault & Digital Identity

| Field | Value |
| --- | --- |
| Document ID | NLB-CPIOS-002 |
| Series | Communication & Personal Information OS (Volume 30) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Parent | `NLB-CPIOS-001` |

---

## Communication Agents

Part 1 handled the inbox. Part 2 introduces the agents that work it, the automation that processes it safely, and the personal-information layer it draws on.

```
                    COMMUNICATION AGENT
                            │
   ┌─────────┬──────────────┼──────────────┬─────────┐
   │         │              │              │         │
 EMAIL    MESSAGE         CALL          CONTACT   ALERT
 AGENT     AGENT          AGENT          AGENT    AGENT
```

Each registers under `NLB-NXOS-004`'s seven-field schema and holds one of five escalating permission levels:

| Level | Can |
| --- | --- |
| **View** | Read authorized information |
| **Analyze** | Summarize and classify |
| **Draft** | Prepare responses |
| **Execute** | Perform approved actions |
| **Autonomous** | Perform narrowly defined actions without per-instance approval |

**Default: View + Analyze.** Autonomy is granted deliberately, per capability, never inherited.

---

## Automation With a Rehearsal Step

Users build rules without code:

```
WHEN  Email contains "invoice"
IF    Amount < ₹10,000
THEN  Save receipt · Create expense
EXCEPT  Sender is unknown
```

What distinguishes this from ordinary mail filters is that **a rule is rehearsed before it runs**:

**Test mode** reports scope against real history — *"This rule would affect 14 messages from the last month"* — with reviewable examples.

**Simulation** shows exactly what would happen (14 matched · 9 archived · 14 labelled · 3 tasks created) and **performs no real actions.**

A rule that quietly archives the wrong 200 messages is discovered too late by definition. Simulation moves that discovery before execution, and is the single most important safety property in this volume.

**Versioning** (version, created, modified, creator, state), **rollback** (pause, undo recent actions where supported, restore prior version), and an **audit log** (rule, execution time, action, source message) make automation reversible and inspectable — the inbox instance of `NLB-09`'s Workflow History.

---

## Bulk Operations & Retention

**Bulk actions** across selected categories (archive, delete, mark read, label) with **confirmation proportional to scale** — *"This will delete 37 messages"* before proceeding.

**Archive over deletion** as the default disposition.

**Retention rules** are user-defined per category (newsletters: 90 days; receipts: 7 years; personal messages: never auto-delete), bounded by provider capability. **For work accounts, Nexa does not auto-delete records where organizational retention policies apply** — a legal-hold consideration that overrides user preference, and one an inbox assistant can easily violate by accident.

---

## Inbox Agent

```
COLLECT → CLASSIFY → SUMMARIZE → PRIORITIZE → PROPOSE ACTION
```

A **morning agent** surfaces what needs attention (*"7 important messages"*, ranked). An optional **Inbox Zero** workflow moves items through keep / reply / task / schedule / archive — but **the system never pressures the user toward an empty inbox.** Inbox Zero is a workflow some people like, not a standard of virtue.

---

## Personal Information Centre

Entirely new to the Bible, and the reason this volume covers *Personal Information* alongside communication: most of what an inbox needs — addresses, phone numbers, identity documents — is exactly what must never leak.

**Identity profiles** — Personal, Work, Business, Travel, Public — each exposing a different field set. *"Use my business profile for this form"* uses only fields authorized for that profile.

**Personal Data Vault:**

```
                     DATA VAULT
                          │
      ┌───────────────────┼──────────────────┐
   Identity            Finance            Travel
   Documents           Accounts           Passport
```

**Field-level permissions** are granular and asymmetric by design:

```
Phone         AI ✓   Form-fill ✓
Address       AI ✓   Form-fill ✓
Passport      AI ✗   Form-fill ⚠ confirm
Bank account  AI ✗   Form-fill ⚠ confirm
```

**Sensitive-field confirmation** is mandatory before inserting passport numbers, tax IDs, bank details, or identity numbers anywhere.

**Sharing preview** shows exactly which fields leave before they leave:

```
Recipient: Company X
Name ✓   Email ✓   Phone ✓   Address ✗   Passport ✗
```

**Data expiration** scopes a share to a transaction (*"allow my phone number for this booking only"*). **Change history** tracks what changed and when. **Change propagation** offers to update a changed detail across connected profiles — with a **preview of exactly which profiles will change**, and which won't.

**Identity consistency** detects conflicting name forms across profiles and asks which is correct **only where consistency actually matters** (travel documents, legal forms) rather than enforcing uniformity for its own sake.

**Addresses** — home, work, billing, shipping, temporary, family — with per-service defaults. **Nexa never automatically exposes the user's home address to unrelated recipients.**

---

## Forms

**Form-filling** identifies required fields and marks which need confirmation. **Final review** before submission shows every value being sent.

**Leak warning:** if a form requests a field not plausibly needed for its stated purpose, Nexa says so and **the user decides.** This is a small feature with outsized value — over-collection is the norm on the web, and a user filling a form quickly has no natural moment to notice it.

---

## Composition Tooling

**Signature manager** with per-context signatures and suggestion (*"This appears to be a business email — use your business signature?"*).

**Template library** with variables (`{{name}}`, `{{product}}`), and **unresolved-variable detection** blocking a send containing a literal `{{name}}` — the embarrassment this prevents is minor, the trust it protects is not.

**Bulk send** for legitimate user-controlled communication, with pre-send verification: recipient count, external-recipient count, sensitive-data scan, **per-recipient personalization check** (correct name, company, document, amount), and **duplicate-recipient detection**.

**Threading protection** verifies correct thread, recipient, and account on reply. **CC/BCC review** warns when the pattern is unusual for the user. **Attachment size** warnings, **cloud attachment mode** with **link expiration**, and **sharing revocation** where the provider supports it, with a record of what was shared, with whom, when, and until when.

---

## Security

**Communication Security Centre** surfaces suspicious links, sensitive emails, unknown senders, and expired sharing links.

**Phishing assistant** flags unknown senders, lookalike domains, urgent payment requests, suspicious links, and unexpected attachments — reporting **"potentially suspicious"** rather than claiming certainty. Overclaiming here trains users to ignore the warnings, which is worse than not warning at all.

**Link preview** shows destination and domain mismatch before opening. **Attachment safety** warns on risky file types and **never executes files automatically.**

**Spam learning** is explicitly user-taught (*always/never treat this sender as spam*), with **trusted senders** whitelisted and unknown contacts offered reply / block / save / ignore. **Block and mute centre** manages blocked senders and muted conversations.

---

## Boundaries & Focus

**Communication boundaries** per relationship class (work after 7 PM: do not disturb; friends: always allowed; unknown: muted).

**Focus protection** blocks promotions and newsletters during focus blocks while allowing VIP, calendar, and critical alerts — connecting to `NLB-SP-004`'s Focus Mode and `NLB-CWOS-001`'s work sessions.

**Batching windows** (review email at 9 AM, 1 PM, 5 PM) and **digital wellbeing** figures (messaging, email, meeting time) feed `NLB-HOS-006`'s digital wellness — **descriptive only**, including context-switching time (*"2h 18m switching between messaging and email"*).

---

## Assisted Group Communication

*"Tell everyone attending dinner that we're running 20 minutes late"* runs: identify the group → prepare the message → **show recipients** → confirm → send via chosen channel. Showing the recipient list before sending is the step that prevents the wrong group receiving a personal message.

**Event-driven drafts** — a flight delay proposes notifications to affected parties (family group, hotel, driver, meeting attendees), each drafted for approval.

**Meeting follow-up** produces decisions, tasks, and a recap email draft — approved before sending, per `NLB-RSOS-002`'s meeting intelligence.

---

## Knowledge & Context Control

Information extracted from communication can become searchable knowledge (*"Client prefers delivery on Mondays"*), stored **only if the user confirms**, with **source and confidence recorded** (source: email Aug 10 · status: user confirmed).

**Knowledge expires.** Nexa detects stale addresses, phone numbers, company roles, preferences, and meeting links, and asks for confirmation rather than acting on aging data. A **memory cleanup** view lists potentially outdated, duplicate, and unconfirmed entries.

The **Personal Knowledge Graph** connects people, companies, projects, events, documents, conversations, and commitments — contributing to `NLB-NXOS-005` rather than forming a separate graph.

### Context control

Users set how much context AI may use per task: current message → current thread → current person → current project → entire history.

**Minimum necessary context is the default principle.**

**Context preview** shows what is and isn't being used before a sensitive action:

```
Using:      ✓ Current email   ✓ Contact profile
Not using:  ✗ Private notes   ✗ Personal messages
```

Making the *exclusions* visible is what makes the guarantee credible — a list of what was used says nothing about what else was available.

**Agent isolation** keeps work and personal agents separate by default:

```
WORK AGENT       PERSONAL AGENT
├ Work email     ├ Personal email
├ Work calendar  ├ Personal calendar
└ Work contacts  └ Family
```

**Cross-domain requests require explicit bridging.** *"Find a time when my family and client are both free"* prompts for cross-domain permission rather than assuming universal access — the CPIOS instance of `NLB-HOS-005`'s cross-OS firewall, applied to the split between work and private life.

---

## Public Profile

A controlled public profile exposes name, professional role, business contact, and selected links. **Private information is never exposed automatically.**

---

## Acceptance Criteria

CPIOS is architecturally complete when it supports: agents (email, messaging, call, contact, notification) with graduated permissions; automation (no-code rules, simulation, versioning, rollback, audit); personal information (identity profiles, form filling, data vault, field permissions, expiration, change propagation); communication tooling (templates, bulk send, scheduling, translation, group messaging, meeting recaps); security (phishing, link and attachment warnings, sensitive-data warnings, sharing controls); knowledge (personal graph, context control, memory confidence, stale detection, cross-system search); and privacy (agent isolation, minimum-context default, context preview, cross-domain permission, full auditability).

---

## Principle

**Receive → Understand → Organize → Decide → Act → Remember.**

NexaLife should be powerful enough to handle communication, but controlled enough that **the user never loses awareness of what is being read, written, shared, or sent.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial communication agent and personal information specification. Establishes five graduated agent permission levels, rule simulation before execution with versioning and rollback, retention rules including legal-hold protection, the Personal Data Vault with field-level permissions and sharing preview, form leak warnings, bulk-send verification, phishing and link safety, and the minimum-necessary-context default with visible exclusions and agent isolation. |

---

**End of Part 2 (Version 1.0)**

**END OF THE COMMUNICATION & PERSONAL INFORMATION OPERATING SYSTEM SPECIFICATION**
