# 📖 NEXALIFE BIBLE — Relationships & Social Life Operating System (RSOS)

## Part 1 — People Graph, Relationships, Family, Friends & Social Intelligence

| Field | Value |
| --- | --- |
| Document ID | NLB-RSOS-001 |
| Series | Relationships & Social Life Operating System (Volume 27) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Home domains | LD-08 Family, LD-10 Community (`NLB-03`) |
| Catalogue anchor | PU-01-047 Relationship & Contact Planner, PU-08-* (Family), PU-10-001–006 (People & Groups) in `NLB-04` |
| Dependencies | `NLB-10` · `NLB-12` · `NLB-14` · `NLB-21` · `NLB-NXOS-005` · `NLB-BLOS-*` |

---

## Purpose

A life is not made only of tasks, money, fitness, career, travel, and goals. A major part of it is **people**. RSOS helps users maintain meaningful relationships, remember important people and dates, spend quality time together, plan shared experiences, organize social commitments, build communities, and preserve meaningful memories.

**The system must support relationships, never manipulate them.** That constraint shapes every design decision below and is why several conventional social-product mechanics are explicitly rejected.

---

## The People Graph

At the center of RSOS is the People Graph — the relationships a user chooses to maintain inside NexaLife, spanning Family, Friends, Work, and Community. **It is private by default** (`NLB-10`).

This is not a new graph: Person nodes and `Participates In` / `Owned By` edges already exist in `NLB-NXOS-005`'s Universal Knowledge Graph. RSOS is the product surface that makes those nodes first-class and richly attributed.

**People are not contacts.** A contact is an address-book entry. A relationship profile can carry contact information, relationship type, important dates, shared experiences, shared BucketLists, conversations, events, notes, preferences, goals, and privacy permissions — **with the user deciding which information Nexa may store.**

---

## Relationships

**Types**: Family (parent, child, sibling, grandparent, relative), Friends (best/close/school/college friend), Professional (colleague, manager, client, partner, mentor, mentee), Community (teammate, club member, coach, organizer), plus **custom labels**.

**Contact Segmentation** — one person may hold several contexts simultaneously (friend + colleague + football teammate) **without creating duplicate records**, per `NLB-07`'s One Source of Truth.

**Relationship Strength is deliberately not scored.** Nexa displays objective interaction signals the user has chosen to track (last interaction, shared experiences, upcoming plans) but **never a "friendship score: 72%"** — such a number would be both misleading and unhealthy. This is the sharpest instance in the Bible of `NLB-14`'s rule that metrics measure meaningful participation, not manufactured engagement.

**Important People** can be starred, letting Nexa prioritize reminders rather than treating every contact equally. **Relationship Context** stores user-provided facts (*"John is my college roommate"*) enabling natural queries (*"When did I last meet my college roommate?"*).

---

## Contact & Communication Integration

**Import** from phone, Google, Microsoft, or other supported address books requires permission first. **Contact Matching** suggests merges for likely duplicates; **the user decides.**

**Phone integration** distinguishes *phone capability* from *permission to use it*. For *"Call Dad,"* Nexa verifies phone access, calling permission, and device state, and if permission is missing says so plainly. **Nexa never silently bypasses operating-system permissions** — the RSOS instance of `NLB-NIC-003`'s Phone Capabilities.

**Device reachability is stated honestly.** If the phone is unreachable, Nexa says *"Your phone isn't reachable right now. I'll keep this as a reminder"* — **the interface never pretends a call occurred.**

**Email and messaging integration** (finding messages, identifying invitations, surfacing plans, drafting replies, creating events) operates through `NLB-12`'s Connector Architecture with per-source authorization. **Nexa does not secretly read private conversations**, and sending requires appropriate authorization and confirmation.

---

## Dates & Occasions

Nexa tracks user-chosen birthdays, anniversaries, wedding dates, friendship and work anniversaries, and custom milestones (`NLB-04`, PU-08-030).

**Date Intelligence** offers optional actions — reminder, message draft, gift ideas, dinner planning, shared-memory suggestions — and **asks before sending anything.** The Birthday Assistant always includes *"Do Nothing"* as a first-class option.

**Gift Planning** considers user-provided interests, previous gifts, budget, occasion, relationship, and availability. **Nexa does not infer sensitive personal characteristics to make gift recommendations** — a specific application of the inference boundaries formalized in Part 2. **Gift History** prevents repetition.

---

## Shared Life

**Shared Experience Graph** — when two people participate in the same trip, event, competition, dinner, project, or BucketList experience, Nexa creates a shared memory connection.

**Shared BucketLists** and **Shared Goals** connect directly to `NLB-BLOS-*` and the platform Goal Planner, with **financial visibility individually controlled** — a shared savings goal never exposes one participant's finances to another.

**Family Hub** — an optional household space with family calendar, shared goals, trips, events, important dates, tasks, BucketList, and memories, each event carrying its own visibility settings. **Family Tasks** can be assigned to members.

**Responsibility Balancing** shows objective household workload distribution and may suggest redistribution — **it does not make moral judgments.**

**Family Decision Engine** and **Group Planning** collect votes and weigh preferences, availability, budget, and travel time to recommend compatible options.

---

## Scheduling Without Exposure

**Availability Matching** identifies common free windows from optionally shared availability while **keeping exact calendar details hidden.** When scheduling, Nexa says *"Alex isn't available"* — **never** *"Alex has a doctor's appointment."* This single rule is what makes social scheduling compatible with `NLB-10`'s permission model and with the health-data protections in `NLB-HOS-004`.

**Social Reminders** and **Connection Rhythms** (*"Remind me to check in with my grandparents every Sunday"*) become ordinary recurring reminders. From *"I don't want to lose touch with my college friends,"* Nexa can help create reminders, plans, or recurring calls — but **never automatically messages everyone.**

---

## Social Memory

Nexa remembers user-entered context (*"Alex loves hiking"*) to inform planning suggestions. **Every relationship memory is editable** — *"That's wrong, Sarah doesn't like hiking"* updates it immediately, per `NLB-NXOS-003`'s user-control guarantees.

**Private notes** ("Met at university," "Likes photography") **never automatically become visible to the other person.**

**Conversation Context** may identify actionable items from authorized communications (*"Let's meet next Saturday"* → *Create calendar event?*) but **does not act unless the user has enabled that behavior.**

---

## Social AI

**Social AI Assistant** answers *"Who haven't I spoken to recently?"* with factual intervals from authorized data — **presented as a signal, not a judgment.**

**Relationship Insights** observe patterns (*"Most of your recent social activities have been work-related"*), leaving the decision to the user.

**No Manipulative Social Engine.** RSOS must not use fear of losing friends, artificial guilt, engagement pressure, social ranking, popularity scores, or manipulative streaks. **The objective is meaningful connection** — this section is a binding constraint, not an aspiration, and it is why relationship strength is unscored above.

---

## Groups & Communities

**Friendship Groups** (college friends, teams, family, work friends, travel groups) can carry shared calendars, BucketLists, events, and integrated group chat where supported.

**Community discovery, join flow, moderation, and events** run on `NLB-14`'s Club System and Community structure — RSOS surfaces them for personal social life rather than redefining them.

**Cross-subsystem connections**: Social + BucketList (shared dreams with collective planning), Social + Travel (coordinating travelers without exposing private finances), Social + Fitness (running groups, teams, challenges via `NLB-FPOS-*`), Social + Learning (study groups, book clubs), Social + Career (mentors, clients, networking, follow-ups — **kept under separate visibility controls from personal relationships**).

---

## Relationship History

**Relationship Timeline** optionally records a private history (met → first trip → joined same club → marathon → shared BucketList), with **Important Moments** starred to feed the shared memory system.

**AI Social Planner** turns *"I want to spend more time with my family this month"* into realistic options from authorized calendar, availability, BucketList, and events.

---

## Core Principle

RSOS must never turn people into data points. **The data exists to help the person care better, not to calculate whether a relationship is "good enough."**

The loop: **Remember people → Make time → Share experiences → Create memories.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial People Graph and Social Intelligence specification. Establishes relationship profiles distinct from contacts, deliberately unscored relationship strength, honest phone/device capability reporting, privacy-preserving availability matching, and an explicit prohibition on manipulative social mechanics. |

---

**End of Part 1 (Version 1.0)**
