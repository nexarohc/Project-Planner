# 📖 NEXALIFE BIBLE — BucketList & Experience Operating System (BLOS)

## Part 1 — The BucketList Engine, Life Experiences & Adventure Planning

| Field | Value |
| --- | --- |
| Document ID | NLB-BLOS-001 |
| Series | BucketList & Experience Operating System (Volume 26) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Catalogue anchor | PU-01-017 Bucket List, PU-01-018 Vision Board, PU-07-030 Travel Bucket List (`NLB-04`) |
| Dependencies | `NLB-05` · `NLB-09` · `NLB-14` (Bucket List Platform) · `NLB-21` (LOUPE) · `NLB-HOS-*` · `NLB-FPOS-*` |

---

## Purpose

NexaLife should not only help people plan their lives — it should help them actually live them. BLOS is the subsystem for dreams, experiences, adventures, places, personal milestones, and things users want to accomplish, learn, experience, or do with other people.

**A bucket list should not be a static list of wishes. It should become an execution engine.**

**Relationship to `NLB-14`.** Community, Competitions & Achievement already established the Bucket List Platform as a shared capability (personal, shared, family, team, organization, and public inspiration lists; items carrying priority, target date, estimated cost, related planners, progress, notes, media, AI suggestions, and completion history). `NLB-14` defined *that* platform. BLOS is its full product specification — the dream→plan→fund→schedule→experience→memory pipeline that turns those data structures into an operating system.

---

## A First-Class Page

BucketList appears in main navigation alongside Home, Planner, Goals, Health, Fitness, Finance, Travel, Career, Learning, Relationships, Marketplace, and Nexa AI. **It is not hidden inside Goals or Travel** — a placement decision, since burying aspirations inside a task list is precisely what makes most bucket lists inert.

The landing page is inspirational but functional: a prompt (*"What do you want to experience?"*), an add action, counts (dreams / completed / in progress / waiting), and a "This Year" section surfacing near-term experiences.

---

## The BucketList Object

Natural language is the entry point — *"See the Northern Lights," "I want to learn to surf," "Take my parents on an international trip," "Run a marathon"* — which Nexa converts into a structured experience carrying:

Title · Description · Category · Priority · Difficulty · Estimated Cost · Location · Time Required · Target Date · People · Status · Progress · Dependencies · Memories · Notes · Privacy

**Categories** (default): Travel, Achievement, Relationships, Learning, Adventure, Creativity, Career, Financial, Contribution. **Custom collections** ("Things I want to do before 30," "Family BucketList," "Dream Trips") use tagging, so one item belongs to multiple collections **without duplicating the underlying item** — `NLB-07`'s One Source of Truth applied to aspirations.

**Status lifecycle**: Dream → Planned → Booked/Preparing → In Progress → Completed → Memory, plus Paused, Cancelled, and Deferred.

---

## Dream → Plan

This is the system's most important capability. *"I want to visit Japan"* flows:

```
DREAM → TARGET (2027) → BUDGET → TRAVEL PLAN (flights, hotels, activities)
  → FINANCE PLAN (savings) → CALENDAR (dates) → EXECUTION (book)
  → EXPERIENCE → MEMORY
```

**AI BucketList Planner** turns vague dreams into concrete steps (*"See the Northern Lights"* → choose destination, select travel window, estimate budget, check travel requirements, plan transport, choose accommodation, reserve activities, prepare equipment, travel, complete) — `NLB-NXOS-002`'s Goal Decomposition applied to lived experience rather than tasks.

**Dependency Engine** surfaces prerequisite chains (Climb Mountain → Fitness Preparation → Equipment → Travel Budget → Training → Trip) using the `Requires` and `Blocks` edge types from `NLB-NXOS-005`.

**Dream Readiness** shows exactly what remains (✓ budget, ✓ passport, ✓ dates, ✓ flights; ○ hotel, ○ activity bookings).

---

## Prioritization & Time Horizons

**Priority** levels — Must Do, High, Normal, Someday — prevent the BucketList from becoming an overwhelming wall of hundreds of dreams.

**Life Horizon** organizes across This Year / Next 3 Years / Lifetime. Optional life-stage milestones ("Before 25," "Before 30," "Before retirement") organize goals against horizons, and **the system never implies someone is "behind" for not completing an experience by a certain age** — an explicit rejection of the guilt-driven framing most life-goal products default to.

**Progress indicators** by category (Adventure, Learning, Relationships, Travel) are **visual summaries, not judgments about the user's life** — and deliberately *not* a single "life score," for the same reason `NLB-HOS-002` refuses a single health number.

---

## Discovery

**Experience Discovery** (*"Give me five unforgettable things I could do this year"*) considers budget, location, time, interests, fitness, existing BucketList, and travel plans. **Personalized Discovery** recognizes that a user who likes architecture and photography with a given budget needs a specific recommendation, not "Go to Paris."

**"Surprise Me"** generates an experience from chosen constraints (budget, time, distance, difficulty, solo/group) — accept, reject, or regenerate. This is `NLB-NXOS-002`'s planning applied with deliberate randomness, and connects to Part 2's Serendipity Engine.

**Local Adventures** ensure the system never assumes every experience requires international travel — *"Find something unforgettable within 100 km"* searches nature, sports, cultural experiences, food, events, adventure, workshops, and local attractions.

**Weekend Experience Engine** (*"What can I do this weekend?"*) considers calendar availability, budget, weather where available, location, interests, and existing BucketList.

**Time-aware** categorization (2 hours → local activity; 1 day → day trip; weekend → short adventure; 1 week → international or intensive; months → major achievement) makes the list actionable against real available time.

---

## Funding

BucketList integrates with Finance (`NLB-04`, LD-05): an item shows estimated cost, amount saved, and remaining. **Dream Funding** calculates a suggested monthly saving from cost and timeframe, but **the user controls whether the goal is actually added to their financial plan** — and per `NLB-04`'s Financial Advisor AI boundaries, the system **does not encourage financially irresponsible decisions.**

---

## Shared BucketLists

Experiences can be shared with friends, family, partner, or team, each participant seeing shared progress (budget, people, planning task completion). **Group Contributions** track who is responsible for what, budget contributions, booking tasks, and preparation — **no participant automatically sees another person's financial information**, per `NLB-10`.

**Couple Mode** and **Friend Group Mode** support shared private lists and collective decisions, with a **Voting System** (anonymous, named, private, or group-visible) for destination, activity, date, and budget.

---

## Memory Engine

A completed item does not disappear — **it becomes a Memory**, carrying completion date, photos, videos, people, and notes. Completed experiences feed a **Life Timeline** — one of the most emotionally important surfaces in NexaLife, and the BLOS contribution to `NLB-21`'s Universal Timeline.

**Memory Privacy** — Private / Shared / Friends / Public, **defaulting to private**, since a bucket list can reveal deeply personal aspirations.

**AI Memory Organization** answers *"Show me all my travel memories from 2027"* and can compose an optional narrative ("Your 2027 Adventure"), which **the user can edit or delete.**

---

## Cross-Planner Integration

BLOS is the clearest demonstration in the Bible of why LOUPE (`NLB-21`) and the Universal Knowledge Graph (`NLB-NXOS-005`) exist — a single dream legitimately touches five or six planners:

| Dream | Connects to |
| --- | --- |
| "Visit Japan" | Travel Planner → flights/hotels/transport/activities → Calendar → Finance |
| "Run a marathon" | FPOS training goal → Calendar sessions → HealthOS recovery → Finance (event budget) → Competition registration |
| "Speak Spanish conversationally" | Learning (curriculum, practice, lessons, milestones) → completion updates BucketList on user confirmation |
| "Speak at an international conference" | Career goals → networking → skill development → deadlines → Travel |
| "Buy my dream car" | Finance target cost → savings goal → purchase → Memory |

**The user should never need to manually recreate the same trip in five different parts of NexaLife** — the strongest single argument for the shared data model established in `NLB-07`.

**BucketList + Relationships** enables proactive-but-not-intrusive prompts: *"You and your brother added a hiking trip to your shared BucketList six months ago. Would you like to plan it?"* — per `NLB-11`'s Proactive Assistance constraints.

---

## Achievements & Balance

Completed experiences unlock achievements through `NLB-14`'s Achievement Engine (Mountain Explorer, First International Adventure, First Race, Five Countries, Family Adventure). **Achievements stay positive rather than competitive.**

Optional **experience streaks** can be disabled entirely: **the system never makes people feel pressured to constantly consume experiences.**

**Life Balance** shows variety across experience types as a **discovery tool, not a score.**

---

## Core Loop

```
DREAM → CAPTURE → PRIORITIZE → PLAN → FUND → SCHEDULE → PREPARE
  → EXPERIENCE → COMPLETE → REMEMBER → SHARE → INSPIRE → NEXT DREAM
```

---

## Philosophy

The BucketList must never become *"another checklist you feel guilty about not completing."* It should feel like **"a visual map of the life you want to experience."**

The ultimate NexaLife loop: **Plan your life → Live your life → Remember your life.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial BucketList Engine specification. Establishes the BucketList object and status lifecycle, the Dream→Plan pipeline, the Dependency Engine, prioritization and life horizons, discovery (including Surprise Me and local/weekend engines), dream funding, shared lists, and the Memory Engine — as the full product specification of the Bucket List Platform capability established in NLB-14. |

---

**End of Part 1 (Version 1.0)**
