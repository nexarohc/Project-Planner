# 📖 NEXALIFE BIBLE — Communication & Personal Information Operating System (CPIOS)

## Part 1 — Unified Communications, Inbox Intelligence & Personal Information Flow

| Field | Value |
| --- | --- |
| Document ID | NLB-CPIOS-001 |
| Series | Communication & Personal Information OS (Volume 30) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Home domain | Cross-cutting; anchors to LD-01 Personal Life (`NLB-03`) |
| Dependencies | `NLB-07` · `NLB-09` · `NLB-10` · `NLB-12` · `NLB-NIC-002` · `NLB-NXOS-003` · `NLB-RSOS-002` |

---

## Purpose

CPIOS is NexaLife's unified layer for handling digital communication — email, messages, calls, contacts, notifications, attachments, and the personal information that flows through them.

> **Turn communication from an endless stream into an organized, actionable information system.**

### Boundary against RSOS

`NLB-RSOS-002` already defines communication intelligence **in service of relationships**: drafting a message to a friend, remembering what was discussed with a person, tracking commitments made to someone. That stays there.

CPIOS owns communication **as a system**: the inbox as a queue to be triaged, rules that process it, safety checks before anything leaves, multi-account handling, and the personal-information vault those messages draw on. The split is *who the communication is about* (RSOS) versus *how the volume of it is managed* (CPIOS). Where they meet — drafting a reply — RSOS supplies relationship context and CPIOS supplies the send-safety layer.

---

## Architecture

```
                       COMMUNICATION OS
                              │
       ┌──────────────────────┼──────────────────────┐
       │                      │                      │
     RECEIVE               UNDERSTAND               ACT
       │                      │                      │
   Email                   Summarize              Reply
   Messages                Extract                Forward
   Calls                   Classify               Schedule
   Notifications           Prioritize             Archive
```

---

## Unified Inbox

One interface across email, messages, notifications, missed calls, and follow-ups, switchable between unified and per-source views. **Every item shows its source** (✉ email, 💬 message, 📞 call, 📅 calendar, 📄 document) — **Nexa never hides where information originated**, which matters because trust in a triaged inbox depends entirely on being able to check its work.

**Priority tiers** — Critical / Important / Normal / Low / Noise — are user-configurable, and **the user can override any AI classification.** **VIP contacts** (family, key clients, managers, emergency contacts) can raise notification priority independently of content.

**Smart Inbox** groups by required action rather than by folder: needs reply, waiting for reply, read later, receipts, newsletters, promotions.

---

## From Message to Action

```
READ → UNDERSTAND → ACTION? → Reply / Schedule / Task / Save / Archive
```

**Action extraction** identifies tasks (*"Please send the quotation by Friday"* → task + due date), including **multiple actions in a single message**, with the user selecting which to create. **Deadline extraction** offers reminders.

**Date ambiguity is surfaced, not guessed.** *"Let's meet next Friday"* resolves from context, and **Nexa asks for confirmation when the ambiguity matters** — a wrong assumption here produces a missed meeting, which is exactly the failure the feature exists to prevent.

**Decision and commitment extraction** capture *"We agreed to move the meeting to Friday"* and *"I'll send it tomorrow"*, the latter feeding the **Commitment Centre** — which is the same commitment tracking `NLB-RSOS-002` defines, sourced here from the inbox rather than from conversation.

**Follow-Up Centre** and the **Waiting-For Tracker** cover both directions: what the user owes, and what the user is owed (*"Client approval — sent Aug 8"*), with follow-up prompts only on requests the user explicitly tracked.

---

## Thread Intelligence

Long threads collapse to a summary (topic, participants, decision, open items) and a **timeline** showing how the thread actually moved — request → quotation → questions → answers → waiting. This is the single highest-value transformation in CPIOS: a 40-message thread's *state* is usually four lines, and everything else is transport.

---

## Drafting & Send Safety

Replies are drafted with configurable **tone** (professional, friendly, concise, formal, warm, assertive, diplomatic) and **length** (short / standard / detailed), using thread context. **Nexa does not invent facts absent from the conversation** — the no-fabrication rule from `NLB-06`, applied where a fabricated detail becomes a written commitment to another person.

**Default: never send without user approval** (`NLB-NIC-002`).

### The pre-send check

This is CPIOS's most distinctive contribution, and it catches the errors people actually make:

| Check | Catches |
| --- | --- |
| Attachment | *"I've attached the quotation"* with nothing attached |
| Recipient | Content that appears intended for someone else |
| Account | Sending a client email from a personal account |
| Sensitive data | Passwords, financial details, identity documents, medical records |
| Amounts & dates | Figures and dates inconsistent with the thread |

Each is a **warning the user can override**, not a block. The value is in the moment of attention, not in refusing to send.

**Send delay** (an optional 30-second buffer), **undo send**, **scheduled send**, and a **scheduled message centre** with cancellation complete the safety layer.

---

## Organization at Volume

**Classification** into personal, work, finance, shopping, travel, health, government, education, newsletters, promotions, and notifications, with custom categories. **Automatic labelling** proposes labels the user can accept, reject, or always apply.

**Newsletter Centre** identifies recurring senders with unread counts and unsubscribe candidates. **The unsubscribe assistant requires user approval** — unsubscribing is an outbound action with a real consequence (losing something the user wanted), so it never happens automatically.

**Promotional cleanup** proposes bulk archive/delete for mail unopened in 90 days.

**Digests** replace notification storms: a morning digest, a combined communication digest (email, messages, missed calls, upcoming meetings), and an optional evening review (replied / waiting / unresolved / scheduled).

**Analytics** — volume, response time by category, unresolved threads — are **descriptive metrics**, not performance targets. *"You received 84 items today"* is information; framing it as a score would make the user responsible for other people's volume.

---

## Notifications & Devices

**Notification intelligence** groups by source; **priority rules** route by type (emergency contact → immediate; calendar → important; newsletter → silent; promotion → batch); **batching** collapses low-priority alerts into one.

**Quiet hours** with configurable exceptions (emergency contacts, critical calendar events, selected apps), per `NLB-21`'s Notification Orchestration.

**Device and read-state synchronization** — reading on a laptop marks read on the phone — built on `NLB-07`'s sync model and `NLB-NIC-003`'s cross-device continuity.

---

## Multiple Accounts

Personal, work, business, and other accounts each carry **independent permissions**, including **per-account AI access** — a private account can be excluded from AI entirely while work mail is fully available.

**Multi-account search** returns results labelled by source account. **Account switching** shows the active account, and a **wrong-account warning** fires before sending client mail from a personal address, offering send / switch / cancel.

---

## Contacts & Attachments

**Contact intelligence** links a person to their email, messages, calls, meetings, tasks, and memories — only where authorized, and drawing on the People Graph (`NLB-RSOS-001`) rather than a second contact store.

**Merging** detects duplicates across phone, email, contacts, calendar, and CRM, with **user confirmation**. **Enrichment** uses only user-authorized sources — **never scraping or inferring sensitive information.** **Source tracking** and **change history** record where a contact detail came from and when it changed.

**Attachment Centre** provides a unified view by type (invoices, contracts, travel, images) with search and **duplicate detection** (`invoice_0326.pdf` vs `invoice-final.pdf`), the user deciding what to merge or delete.

**Document-derived actions** — a document containing *"sign and return by Friday"* proposes a task; an invitation proposes a calendar event; a scanned business card or QR contact proposes a contact, **all confirmed before saving.**

---

## Calls

Where device and platform integrations permit: call logs, **call notes** (topic, decision, follow-up), **call summaries**, and **voicemail intelligence** (duration, summary, suggested action).

**Transcription requires legal support and appropriate consent from participants**, with recording status **clearly indicated in the interface**. **No covert recording, ever** — Nexa respects local recording law, platform restrictions, consent requirements, and user settings. Users control whether transcripts are stored, stored temporarily, or deleted after summarization.

**Missed-call intelligence** flags VIP misses with call back / message / remind options.

---

## Group Conversations

Long group chats summarize to participants, decisions, and open items. **Noise filtering** answers *"show me only decisions from this chat"*, and **group chat search** answers *"when did we decide the trip date?"* — the recurring problem being that group chats bury decisions in volume rather than losing them.

---

## Cross-System Automation

Communication is where most cross-domain automation actually originates:

| Source | Routes to |
| --- | --- |
| Hotel/flight confirmation | TravelOS → Calendar → Documents |
| Order confirmation | ShoppingOS → delivery tracking |
| Receipt | `NLB-FWOS-001` → expense → category → budget |
| Bill (amount, due date, provider) | Bill reminder |
| Subscription charge | Recurring expense record |

These compile onto `NLB-NXOS-006`'s rule notation and `NLB-09`'s lifecycle. **Consequential actions require user confirmation** — a detected transaction is a *proposal* to record, never a recorded fact, per `NLB-FWOS-001`'s detected-vs-confirmed distinction.

---

## Command Centre

*"Handle my inbox"* produces an actionable queue — urgent, reply, schedule, tasks, archive, review — with counts. **The user approves the actions**; Nexa produces the plan, not the outcome.

---

## Principle

**Capture → Understand → Prioritize → Act → Remember.**

NexaLife should not become another inbox. It should become the intelligent layer connecting communication to the rest of the user's life.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial CPIOS foundation. Establishes the unified inbox with source transparency, action/decision/commitment extraction, thread summarization, the pre-send safety check (attachment, recipient, account, sensitive data), multi-account handling with per-account AI access, contact and attachment intelligence, consent-bound call handling, and communication-originated cross-system automation. States the boundary against NLB-RSOS-002. |

---

**End of Part 1 (Version 1.0)**
