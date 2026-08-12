# 📖 NEXALIFE BIBLE — Relationships & Social Life Operating System (RSOS)

## Part 3 — Family Coordination, Occasions, Shared Money & the Life-Memory Layer

| Field | Value |
| --- | --- |
| Document ID | NLB-RSOS-003 |
| Series | Relationships & Social Life OS (Volume 27) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★☆ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Parent | `NLB-RSOS-001`, `NLB-RSOS-002` |

---

## Scope note

Source material arrived proposing a "Family, Relationships & Social Life Operating System" as a separate volume. Reviewed against what exists, the large majority — the People Graph and person profiles, relationship types and custom categories, important people, contact import and duplicate merging, phone/email/message integration with permission gating, important dates and the birthday assistant, gift planning and gift history, relationship memory with correction, communication preferences and logs, the family hub with shared calendar and tasks, responsibility balancing, group planning and availability matching with privacy-preserving output, social scheduling, check-ins and connection rhythms, the social AI assistant, relationship insights, message drafting with tone control, conversation and action extraction, commitment tracking, follow-up intelligence, communities and moderation, graduated automation levels, notification batching and quiet mode, the prohibition on manipulative social mechanics and on inferring sensitive characteristics, and export/deletion — is **already specified across `NLB-RSOS-001` and `NLB-RSOS-002`**, with the legacy/memory-archive material overlapping `NLB-BLOS-002`.

This part captures only what was genuinely absent: shared-money mechanics between people, occasion and tradition machinery, structured family coordination, difficult-conversation support, and the life-memory/legacy layer.

---

## Shared Money Between People

`NLB-FWOS-*` owns the user's own finances. What neither it nor `NLB-RSOS-002`'s social budget covers is money **owed between people**, which is a relationship problem as much as a financial one.

**Group Gifts** — a target amount, contributor list, and per-person share, with contribution status tracked openly (who has paid, who hasn't). Visibility here is deliberate: the point of a group gift is coordination, and hiding who has contributed defeats it. Contributors are named only within the group organizing the gift.

**Expense Settlement** — after a shared event or trip, who paid what resolves into who owes whom:

```
HOTEL      A paid ₹12,000
FOOD       B paid  ₹4,000
TRANSPORT  C paid  ₹3,000
           ↓
A owes B ₹1,200 · C owes B ₹800
```

Splits may be equal or custom, and the split rule is stated rather than assumed. **Nexa calculates and presents; it does not move money between people** — settlement is a computation, and any actual transfer runs through `NLB-FWOS-002`'s two-step money action.

**Family Expense Approval** — for shared household budgets, a requested expense carries amount, requester, and reason, and awaits approval from whoever holds that authority. This is `NLB-10`'s permission model applied to a household rather than an organization.

**Family Subscriptions** — shared services tracked with cost, user count, and actual usage (*"₹1,200/month · 4 users · last used by 3"*), feeding `NLB-HOS-006`'s subscription-audit pattern. **Household Renewal Centre** surfaces upcoming insurance, utility, and school-fee renewals.

---

## Occasions & Traditions

**Celebration Planner** works backward from a date rather than reminding on the day, when it is too late to act:

```
EVENT: Birthday
30 days before  → Gift planning
14 days before  → Invitation
 7 days before  → Purchase
 1 day before   → Reminder
```

**Celebration Budget** connects the occasion to `NLB-FWOS-001` (gift, food, decor, travel → total), and **Event Checklists** provide templates per occasion type (wedding, birthday, graduation, festival, family reunion, dinner).

**RSVP Tracking** covers both directions — the user's own RSVP, gift, travel, and accommodation status for an event they're attending; and invited/yes/maybe/no counts for one they're hosting. **Invitations** are drafted for review and delivered through supported channels; **change management** prepares updated invitations when details shift, again for approval.

**Family Traditions** are recorded and recur automatically (*"Every Diwali we visit grandparents"* → annual reminder). **Relationship Seasonality** captures the natural calendar of a person's year — a family celebration in January, a friend's birthday in April, the annual trip in August — so planning starts when it usually starts rather than when a deadline arrives.

**Task Rotation** — recurring household responsibilities rotate on a schedule (Week 1 → A, Week 2 → B, Week 3 → C), extending `NLB-RSOS-001`'s responsibility balancing from *showing* the distribution to *cycling* it.

---

## Structured Family Coordination

**Family Meeting Mode** — a structured agenda (budget, travel, household, upcoming events) producing recorded decisions and assigned tasks. **Meeting Minutes** capture what was decided and who owns each follow-up, so household decisions don't evaporate between conversations.

**Family Projects** — home renovation, a family trip, a wedding, relocation, education planning — each becomes a shared project with a task board, documents (quotes, tickets, contracts, receipts, invitations), and per-person access control. This reuses the Universal Task Engine (`NLB-05`) rather than introducing a household-specific one.

**Group Food Planning** aggregates dietary preferences across a group (*6 people: 2 vegetarian, 1 no seafood, 3 no restriction*) into compatible options — and connects to `NLB-HOS-003`'s dietary restriction handling, where an unstated allergy is treated as a real risk rather than a preference.

**Family Travel Preferences** — food, room, activity, and accessibility needs per member, with sensitive information (accessibility needs, medical requirements) requiring explicit authorization to share even within a family.

---

## Difficult Conversations

A category no other volume covers, and one where an AI assistant can do real harm if built carelessly.

**Difficult-Conversation Mode** structures preparation rather than scripting outcomes:

```
WHAT HAPPENED
WHAT I WANT
WHAT I NEED TO SAY
WHAT I SHOULD LISTEN FOR
WHAT OUTCOME I WANT
```

The fourth line matters most: it is the only one that treats the conversation as two-sided, and it is what keeps the feature from becoming a tool for winning arguments.

**De-escalation posture** — Nexa favours clear communication, specific facts, respectful language, listening, and boundaries over inflammatory framing.

**Apology Assistant** helps draft acknowledgment, responsibility, and repair — **without excuses**, since an apology that argues its own case is not one.

**Emotional context safety.** Nexa must not manipulate recipients, generate deceptive emotional claims, impersonate the user without permission, manufacture false memories, or escalate interpersonal conflict. This extends `NLB-RSOS-002`'s inference boundaries from *what Nexa may know* to *what Nexa may say on the user's behalf.*

**Gratitude and Appreciation** — an optional gratitude log and reminders for thanks the user intended to give (*"You wanted to thank Sarah after the project"*).

**Social Boundary Planner** — user-set constraints (no events after 9 PM, one free weekend per month, no calls during work blocks) that scheduling respects, plus **Quiet Social Mode** pausing social reminders during vacation or recovery. Overload detection reports the count (*"8 social commitments this week"*) and offers keep / reschedule / decline — **Nexa does not decide which relationship to deprioritize.**

---

## Life-Memory & Legacy Layer

`NLB-BLOS-002` owns experience memories — what the user did. This layer owns **relational and generational** memory: what a family knows about itself.

**Memory Vault & Event Pages** — photos, videos, stories, notes, and audio, with major events getting a dedicated page (people, photos, expenses, notes). **Automatic albums** group by event, date, location, or participants **for user review before final organization**, consistent with `NLB-RSOS-002`'s memory-confirmation pattern.

**Family Story Archive** preserves the things that are lost when nobody writes them down — how grandparents met, the story behind a family business, a first family trip. **Life Story Mode** organizes personal memory chronologically (childhood → school → university → career → family → today).

**Memory Conflicts** are surfaced, not silently resolved:

```
Birthday: Aug 25  ·  Birthday: Sep 4
Conflict detected — which is correct?
```

The user decides, and the correction is recorded — the relationship-data instance of `NLB-HOS-005`'s reconciliation discipline.

**Future Letters & Time-Locked Memories** — private letters written for a child, partner, parent, or future self, stored with an intended open date. **The user retains full control over access, modification, and deletion at all times**, and a time lock is a user-set intention, never a mechanism that removes their own access to their own writing.

**Digital Legacy** — the user specifies what a designated contact may access (photos: family access; letters: selected person; private journal: no access). A **Legacy Contact** may be named as a digital-archive contact.

**Boundary:** this is organization and preservation, **not legal instrument creation**. NexaLife does not transfer account ownership or legal assets, and does not produce valid estate documents — the same line `NLB-FWOS-002` draws around estate planning and `NLB-HOS-004` around clinical protocols.

---

## Contextual Access

The most useful privacy mechanism in this part, and applicable well beyond relationships.

Rather than granting an AI standing access to a person's information, access can be scoped **to a single task**:

```
TASK        Plan a birthday gift for Mom
ACCESS      Birthday + gift history
GRANTED     06:42
EXPIRES     On task completion
```

Every such grant is recorded in a **Relationship Audit Log** showing person, data accessed, reason, time, and permission state. This is `NLB-NXOS-003`'s memory-permission model narrowed from *persistent scope* to *per-task scope*, and it is the right default for data about **third parties** — people who are not NexaLife users and never consented to anything.

**Never-automate categories**, unless explicitly configured and supported: sensitive personal messages, relationship conflicts, medical information, financially significant commitments, private photographs, and legal documents.

**Location sharing** is event-scoped and self-expiring (*"Family dinner · sharing ON · expires 9:30 PM"*), with optional safety features (share destination, arrival and return reminders, trusted contact) under user control. Nexa **does not continuously monitor contacts or reveal another person's location** without their authorization.

---

## Principle

**AI assists the relationship. It never becomes the relationship.**

Technology should help people be more present with each other — not make human connection more automated.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Added shared-money mechanics between people (group gifts, expense settlement, family expense approval), occasion and tradition machinery (celebration planning backward from date, RSVP, task rotation, seasonality), structured family coordination (meetings, projects, group food planning), difficult-conversation support with emotional-context safety, the life-memory and legacy layer, and per-task contextual access with audit logging. Scoped to new material only; the remainder of the proposed parallel volume restated NLB-RSOS-001/002 and NLB-BLOS-002. |

---

**End of Part 3 (Version 1.0)**
