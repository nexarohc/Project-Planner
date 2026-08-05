# 📖 NEXALIFE BIBLE — Volume 04

## The Complete Domain & Planner Universe

| Field | Value |
| --- | --- |
| Document ID | NLB-04 |
| Version | 1.1 |
| Status | Master Draft |
| Priority | ★★★★★ (Critical) |
| Supersedes | — |
| Last updated | 2026-08-05 |

---

## Purpose

Volume 03 defined **where things live** — ten Life Domains and one Universal Module Structure. This volume defines **what actually exists inside them**.

It is the master catalogue and the index for the rest of the NexaLife Bible. Its jobs are:

1. **Completeness** — make sure we have not silently omitted entire areas of life.
2. **Placement** — give every planner a home domain, so nothing floats.
3. **Identity** — give every planner a stable ID that later volumes can reference.
4. **Connection** — record which other domains each planner naturally touches, which is the raw material for the cross-domain graph (NLB-09).
5. **Sequencing** — mark what ships first, so an ambitious catalogue does not become an unbuildable one.

This volume is deliberately **wide and shallow**. It says what exists and why. It does not specify screens, schemas, or behaviour — those belong to the Universal Planner Engine (NLB-07) and the per-planner specifications that follow it.

---

## How to read this catalogue

### Entry ID scheme

```
PU-DD-NNN
   │   └── sequence within the domain
   └────── Life Domain number (01–10, per NLB-03)
```

IDs are permanent. If a planner is renamed, merged, or retired, its ID is retained and annotated — never reused.

### Tier

Every entry carries a build tier. This is the difference between a catalogue and a wish list.

| Tier | Meaning |
| --- | --- |
| **C** | **Core.** Part of the first coherent product. Without it, the domain doesn't work. |
| **E** | **Extended.** Clear value, well understood, scheduled after Core. |
| **F** | **Frontier.** Real but speculative, specialised, or dependent on integrations we don't yet have. |
| **M** | **Marketplace.** Better delivered by the community or a partner than by us. |

A tier is an estimate of sequence, not of importance. Tiers are revised as volumes 05–07 sharpen the picture.

### Links

The **Links** column lists other Life Domains this planner exchanges data with. `05` means Finance, `06` means Health, and so on. These links are proposals for NLB-09, not commitments.

### The Traceability Rule applies to every row

Per NLB-00 Article I, no row survives into a specification without answering *what real problem does this solve*. The **What it does** column is the short form of that answer. Rows that cannot be defended when their specification is written are struck from the catalogue, and their ID is retired.

---

## Catalogue summary

| Domain | Entries | Core | Extended | Frontier / Marketplace |
| --- | ---: | ---: | ---: | ---: |
| LD-01 Personal Life | 48 | 18 | 20 | 10 |
| LD-02 Education | 46 | 14 | 21 | 11 |
| LD-03 Career | 34 | 9 | 17 | 8 |
| LD-04 Business | 56 | 10 | 25 | 21 |
| LD-05 Finance | 42 | 12 | 20 | 10 |
| LD-06 Health | 46 | 12 | 21 | 13 |
| LD-07 Travel | 33 | 7 | 16 | 10 |
| LD-08 Family | 38 | 8 | 19 | 11 |
| LD-09 Creativity | 40 | 5 | 18 | 17 |
| LD-10 Community | 32 | 5 | 14 | 13 |
| LD-11 Sports & Athletics | 14 | 2 | 7 | 5 |
| LD-12 Technology & Engineering | 15 | 3 | 8 | 4 |
| LD-13 Real Estate & Property | 12 | 1 | 6 | 5 |
| LD-14 Agriculture | 11 | 0 | 4 | 7 |
| LD-15 Government & Public Service | 12 | 0 | 4 | 8 |
| LD-16 Science & Research | 13 | 1 | 6 | 6 |
| LD-17 Lifestyle & Home | 11 | 1 | 6 | 4 |
| **Total** | **503** | **101** | **236** | **166** |

The Core tier — roughly 100 planners, almost entirely inside LD-01–LD-10 — remains the real product boundary for v1. LD-11–LD-17 are professional and specialist domains: they carry almost no Core entries because they extend NexaLife beyond individual life management into vertical, often team- or credential-gated work. They matter to this volume for the same reason the rest of the catalogue does — completeness — but they are expected to be adopted later, and disproportionately through the Marketplace (NLB-15) rather than by us building each one directly.

---

# LD-01 — Personal Life

*The user's daily operating system. This domain is the front door: most users meet NexaLife here before they meet any other domain.*

### Time & Scheduling

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-01-001 | Daily Planner | The single view of today: tasks, events, focus blocks, habits | C | all |
| PU-01-002 | Weekly Planner | Week-level shaping and rebalancing of commitments | C | all |
| PU-01-003 | Monthly Planner | Month view for deadlines, cycles, and recurring obligations | C | all |
| PU-01-004 | Quarterly Planner | 90-day horizon connecting goals to weeks | E | 03, 04 |
| PU-01-005 | Annual Planner | Year shape: themes, seasons, major commitments | C | 03, 05, 07 |
| PU-01-006 | Life Planner | Multi-year horizon; the longest planning surface | F | 03, 05, 08 |
| PU-01-007 | Time Blocking Planner | Assigns work to concrete time, not just to lists | C | 02, 03, 04 |
| PU-01-008 | Schedule Template Planner | Reusable week shapes (term time, travel weeks, on-call) | E | 02, 03 |
| PU-01-009 | Availability Planner | Publishes when the user can be booked | E | 03, 04, 08, 10 |
| PU-01-010 | Calendar Hub | Unifies internal and external calendars into one truth | C | all |
| PU-01-011 | Recurrence & Cadence Planner | Governs anything that repeats, across every module | E | all |
| PU-01-012 | Deadline & Renewal Planner | Tracks expiries: documents, licences, warranties, contracts | E | 03, 05, 07, 08 |

### Goals & Growth

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-01-013 | Goal Planner | Defines goals, decomposes them, tracks progress | C | all |
| PU-01-014 | Personal OKR Planner | Objectives and key results for individuals | E | 03, 04 |
| PU-01-015 | Milestone Planner | Checkpoints along long-running goals | C | 02, 03, 06 |
| PU-01-016 | 90-Day Sprint Planner | Short, intense pushes against one objective | E | 02, 03, 06 |
| PU-01-017 | Bucket List | Long-horizon aspirations without deadlines | E | 07, 09, 10 |
| PU-01-018 | Vision Board | Visual expression of desired outcomes | E | 07, 09 |
| PU-01-019 | Life Wheel / Balance Planner | Scores satisfaction per domain; surfaces neglect | E | all |
| PU-01-020 | Personal Growth Planner | Deliberate self-development programmes | E | 02, 03 |
| PU-01-021 | Life Timeline | Chronological record of significant events | E | 08, 09 |
| PU-01-022 | Legacy Planner | Long-term intentions, wishes, and estate context | F | 05, 08 |

### Habits & Routines

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-01-023 | Habit Tracker | Daily/weekly habit adherence and streaks | C | 06, 02 |
| PU-01-024 | Routine Builder | Morning, evening, and situational routines | C | 06, 08 |
| PU-01-025 | Habit Stack Planner | Chains new habits onto established ones | E | 06 |
| PU-01-026 | Behaviour Change Planner | Structured programmes for hard changes | F | 06 |
| PU-01-027 | Accountability Planner | Pairs or groups commit to each other's goals | E | 10 |
| PU-01-028 | Streak & Recovery Planner | Handles breaks without destroying motivation | E | 06 |

### Reflection & Review

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-01-029 | Journal | Free-form daily writing | C | 06, 09 |
| PU-01-030 | Gratitude Journal | Structured positive reflection | E | 06 |
| PU-01-031 | Decision Journal | Records decisions and their reasoning for later review | E | 03, 04, 05 |
| PU-01-032 | Weekly Review | Guided close-out of the week | C | all |
| PU-01-033 | Monthly Retrospective | What worked, what didn't, what changes | E | all |
| PU-01-034 | Annual Review | Year-scale reflection feeding next year's plan | E | all |
| PU-01-035 | Mood & Energy Log | Tracks state over time; input to scheduling | E | 06 |
| PU-01-036 | Lessons Learned Library | Durable personal knowledge from experience | F | 02, 03 |

### Focus & Attention

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-01-037 | Focus Sessions | Timed, tracked deep-work sessions | C | 02, 03, 04, 09 |
| PU-01-038 | Pomodoro Timer | Interval work technique with logging | C | 02, 03 |
| PU-01-039 | Deep Work Planner | Protects and schedules uninterrupted blocks | E | 02, 03, 09 |
| PU-01-040 | Distraction Log | Captures interruptions to find patterns | F | 06 |
| PU-01-041 | Digital Well-being Planner | Screen time goals and boundaries | E | 06 |
| PU-01-042 | Energy Management Planner | Schedules demanding work against energy patterns | F | 06 |

### Life Administration

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-01-043 | Personal Dashboard | The cross-domain home surface | C | all |
| PU-01-044 | Errand & Chore Planner | Small-task management including location context | E | 08 |
| PU-01-045 | Personal Document Vault | Identity and important documents, securely held | C | 05, 06, 07 |
| PU-01-046 | Personal SOP Library | The user's own repeatable procedures | F | 03, 04 |
| PU-01-047 | Relationship & Contact Planner | Keeps important relationships from lapsing | E | 08, 10 |
| PU-01-048 | Values & Identity Planner | Names what matters; used to check goals against values | F | 10 |

---

# LD-02 — Education

*Everything related to learning, at any age and any level — formal study, self-teaching, and professional certification alike.*

### Study Planning

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-02-001 | Study Planner | Core study scheduling against real deadlines | C | 01, 06 |
| PU-02-002 | Semester / Term Planner | Whole-term structure of courses and assessments | C | 01 |
| PU-02-003 | Timetable Planner | Recurring class and lab schedule | C | 01 |
| PU-02-004 | Syllabus Tracker | Coverage against the official syllabus | E | — |
| PU-02-005 | Revision Planner | Spaced revision schedules ahead of assessment | C | 01 |
| PU-02-006 | Exam Planner | Exam dates, formats, seat plans, preparation runway | C | 01, 06 |
| PU-02-007 | Homework Planner | Short-cycle assigned work | C | 01, 08 |
| PU-02-008 | Assignment Planner | Longer coursework with intermediate milestones | C | 01 |
| PU-02-009 | Group Project Planner | Shared academic work with role assignment | E | 10 |
| PU-02-010 | Study Group Planner | Coordinating people, not just work | E | 10 |
| PU-02-011 | Tutoring Planner | Sessions, topics covered, and follow-ups | E | 05, 10 |
| PU-02-012 | Learning Path Planner | Ordered route through a subject from zero to competent | E | 03 |

### Knowledge Capture

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-02-013 | Notes | Structured note-taking bound to courses and topics | C | all |
| PU-02-014 | Flashcards | Spaced-repetition recall practice | C | — |
| PU-02-015 | Mind Maps | Visual relationships between concepts | E | 09 |
| PU-02-016 | Whiteboard | Free-form visual thinking space | E | 04, 09 |
| PU-02-017 | Concept Library | Durable atomic explanations the user has understood | E | — |
| PU-02-018 | Question Bank | Practice questions by topic and difficulty | E | — |
| PU-02-019 | Formula & Reference Sheets | Fast-access reference material | E | — |
| PU-02-020 | Summary Generator Workspace | Condensing source material into study form | E | — |
| PU-02-021 | Annotation Workspace | Marking up PDFs, papers, and slides | E | — |
| PU-02-022 | Glossary Builder | Per-subject terminology | F | — |

### Reading & Research

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-02-023 | Reading Planner | Reading lists with pacing and progress | C | 01 |
| PU-02-024 | Reading Log | What was read, when, and what came of it | E | 01 |
| PU-02-025 | Research Planner | Structures an investigation from question to findings | E | 04 |
| PU-02-026 | Literature Review Planner | Systematic survey of a field | F | — |
| PU-02-027 | Citation & Bibliography Manager | Sources, formats, and integrity | E | — |
| PU-02-028 | Thesis / Dissertation Planner | Long-form academic project management | E | 01, 03 |
| PU-02-029 | Lab & Experiment Planner | Protocols, runs, and results | F | — |
| PU-02-030 | Field Study Planner | Data collection away from the desk | F | 07 |
| PU-02-031 | Academic Submission Planner | Deadlines, formats, and submission tracking | F | — |

### Skills & Credentials

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-02-032 | Course Planner | Enrolled courses across providers | C | 03, 05 |
| PU-02-033 | Certification Planner | Credential requirements and renewal cycles | E | 03 |
| PU-02-034 | Language Learning Planner | Vocabulary, practice, and proficiency milestones | E | 07 |
| PU-02-035 | Skill Tree Planner | Skills as dependencies, showing what unlocks what | E | 03 |
| PU-02-036 | Practice Log | Deliberate practice with quality, not just quantity | E | 06, 09 |
| PU-02-037 | Coding Practice Planner | Problems, patterns, and repetition | E | 03 |
| PU-02-038 | Music Practice Planner | Pieces, techniques, and progression | M | 09 |
| PU-02-039 | Portfolio of Evidence | Proof of competence, assembled over time | F | 03, 09 |

### Teaching & Analytics

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-02-040 | Learning Analytics | Where time goes and what it produces | E | 01 |
| PU-02-041 | Grade Tracker | Marks, weightings, and required-to-pass maths | E | — |
| PU-02-042 | Curriculum Planner | For educators: designing a course | F | 04 |
| PU-02-043 | Lesson Planner | For educators: individual sessions | F | 04 |
| PU-02-044 | Class & Cohort Planner | For educators: managing a group of learners | F | 04, 10 |
| PU-02-045 | Assessment Designer | Building fair, aligned assessments | M | 04 |
| PU-02-046 | Homeschool Planner | Household-run education | M | 08 |

---

# LD-03 — Career

*The professional self: getting in, getting on, and getting better.*

### Direction

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-03-001 | Career Roadmap | Where the user is headed and the route there | C | 01, 02 |
| PU-03-002 | Career Change Planner | Managed transition between fields | E | 02, 05 |
| PU-03-003 | Skill Development Planner | Targeted capability building for a role | C | 02 |
| PU-03-004 | Skill Gap Analysis | Distance between current and target role | E | 02 |
| PU-03-005 | Mentorship Planner | Finding, meeting, and using mentors | E | 10 |
| PU-03-006 | Personal Brand Planner | How the user is seen professionally | F | 09, 10 |
| PU-03-007 | Sabbatical & Break Planner | Deliberate time away and return | F | 05, 07 |
| PU-03-008 | Retirement Transition Planner | Winding down a working life | F | 05 |

### Job Search

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-03-009 | Job Application Tracker | Every application and its state | C | 01 |
| PU-03-010 | Resume Builder | Tailored CVs per application | C | — |
| PU-03-011 | Cover Letter Workspace | Targeted letters without starting from blank | E | — |
| PU-03-012 | Portfolio Builder | Showing work, not just describing it | E | 09 |
| PU-03-013 | Interview Planner | Preparation, scheduling, and debriefs | C | 01 |
| PU-03-014 | Interview Question Bank | Rehearsal material by role and company | E | 02 |
| PU-03-015 | Company Research Planner | Structured due diligence on employers | E | — |
| PU-03-016 | Offer Comparison Planner | Comparing offers across more than salary | E | 05 |
| PU-03-017 | Salary Negotiation Planner | Preparing a defensible ask | E | 05 |
| PU-03-018 | Reference & Recommendation Tracker | Who will vouch, and for what | F | 10 |

### On the Job

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-03-019 | Work Task Planner | Day-to-day professional work | C | 01, 04 |
| PU-03-020 | Meeting Planner | Agendas, notes, and actions | C | 01, 04 |
| PU-03-021 | 1:1 Planner | Recurring manager and report conversations | E | 04 |
| PU-03-022 | Performance Review Planner | Evidence gathering before review season | E | — |
| PU-03-023 | Promotion Planner | Building and presenting a case | E | — |
| PU-03-024 | Achievement Log | Continuous record of wins, with evidence | C | 01 |
| PU-03-025 | Onboarding Planner | First 30/60/90 days in a role | E | — |
| PU-03-026 | Work-Life Boundary Planner | Protecting non-work life from work | E | 01, 06, 08 |
| PU-03-027 | Workload & Capacity Planner | Making overload visible before it bites | E | 01, 06 |
| PU-03-028 | Professional Development Budget | Spending an L&D allowance well | F | 02, 05 |

### Independent Work

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-03-029 | Freelance Client Planner | Clients, scope, and relationships | E | 04, 05 |
| PU-03-030 | Contract & Rate Planner | What is agreed and what it is worth | F | 04, 05 |
| PU-03-031 | Proposal Planner | Winning work | F | 04 |
| PU-03-032 | Time & Billing Tracker | Hours in, invoices out | E | 05 |
| PU-03-033 | Networking Planner | Deliberate professional relationship building | E | 10 |
| PU-03-034 | Conference & Event Planner | Professional events worth attending | F | 07, 10 |

---

# LD-04 — Business

*Running an organization. This domain scales from a solo founder to an enterprise deployment, and is where NexaLife earns revenue per seat rather than per person.*

### Strategy & Governance

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-04-001 | Business Plan Planner | The founding document, kept alive | E | 05 |
| PU-04-002 | Startup Planner | Zero-to-launch sequencing | E | 05 |
| PU-04-003 | Strategy Planner | Direction, bets, and trade-offs | E | — |
| PU-04-004 | OKR Planner | Company objectives cascaded to teams | C | 01, 03 |
| PU-04-005 | KPI Dashboard | The numbers that define health | C | — |
| PU-04-006 | Board & Investor Planner | Reporting and relationship cadence | F | 05 |
| PU-04-007 | Fundraising Planner | Rounds, pipeline, and diligence | F | 05 |
| PU-04-008 | Business Model Canvas | Structured model exploration | F | — |
| PU-04-009 | Competitive Intelligence Planner | Tracking the field over time | F | — |
| PU-04-010 | Risk Register | Named risks with owners and mitigations | E | — |

### Operations

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-04-011 | Project Planner | Multi-workstream delivery | C | 01, 03 |
| PU-04-012 | Task & Workflow Board | Team-level execution | C | 01, 03 |
| PU-04-013 | Sprint Planner | Iterative delivery cycles | E | — |
| PU-04-014 | Roadmap Planner | What ships when, and why | E | — |
| PU-04-015 | Resource Allocation Planner | People and capacity against demand | E | — |
| PU-04-016 | Capacity Planner | Whether the plan is physically possible | E | — |
| PU-04-017 | SOP Library | Repeatable operating procedures | E | 01 |
| PU-04-018 | Process Improvement Planner | Systematic operational refinement | F | — |
| PU-04-019 | Vendor Management Planner | Suppliers, terms, and performance | F | 05 |
| PU-04-020 | Procurement Planner | Buying things properly | F | 05 |
| PU-04-021 | Inventory Planner | Stock levels, reorder points | F | 05 |
| PU-04-022 | Supply Chain Planner | Upstream dependencies and lead times | M | — |
| PU-04-023 | Facilities Planner | Physical space and equipment | M | — |
| PU-04-024 | Incident & Escalation Planner | When things break | F | — |

### Commercial

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-04-025 | CRM | Customers and the relationships with them | C | 03 |
| PU-04-026 | Sales Pipeline Planner | Deals through stages | E | 05 |
| PU-04-027 | Lead Generation Planner | Filling the top of the funnel | E | — |
| PU-04-028 | Account Planner | Deliberate growth of key accounts | F | — |
| PU-04-029 | Quote & Proposal Planner | Priced offers to customers | F | 05 |
| PU-04-030 | Contract Lifecycle Planner | Agreements from draft to renewal | F | — |
| PU-04-031 | Customer Success Planner | Retention and expansion | F | — |
| PU-04-032 | Support Queue Planner | Inbound customer issues | M | — |
| PU-04-033 | Partnership Planner | Alliances and channel relationships | F | 10 |

### Marketing

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-04-034 | Marketing Planner | Overall marketing programme | E | 09 |
| PU-04-035 | Campaign Planner | Individual campaigns end to end | E | 09 |
| PU-04-036 | Content Calendar | What publishes where and when | E | 09 |
| PU-04-037 | Brand Planner | Identity, voice, and consistency | F | 09 |
| PU-04-038 | SEO Planner | Organic discovery work | M | 09 |
| PU-04-039 | Paid Media Planner | Budgeted acquisition | M | 05 |
| PU-04-040 | Product Launch Planner | Coordinated go-to-market | E | 09 |
| PU-04-041 | Community & Advocacy Planner | Turning users into advocates | F | 10 |
| PU-04-042 | Event & Webinar Planner | Owned events | F | 07, 10 |

### People

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-04-043 | HR Planner | The people function overall | E | — |
| PU-04-044 | Hiring Planner | Roles, pipelines, and decisions | E | 03 |
| PU-04-045 | Onboarding Planner | New joiners to productive | E | 03 |
| PU-04-046 | Team Directory & Org Planner | Who does what, and reports to whom | E | — |
| PU-04-047 | Performance Management Planner | Reviews and development at scale | F | 03 |
| PU-04-048 | Compensation Planner | Pay structure and review cycles | F | 05 |
| PU-04-049 | Leave & Absence Planner | Time off across a team | E | 01, 08 |
| PU-04-050 | Training & L&D Planner | Organizational capability building | F | 02 |
| PU-04-051 | Culture & Engagement Planner | Measuring and acting on how it feels to work here | M | 10 |

### Finance, Legal & Compliance

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-04-052 | Business Budget Planner | Departmental and company budgets | E | 05 |
| PU-04-053 | Invoicing & Receivables Planner | Getting paid | E | 05 |
| PU-04-054 | Payroll Planner | Paying people | M | 05 |
| PU-04-055 | Legal Matter Planner | Ongoing legal work and obligations | F | — |
| PU-04-056 | Compliance & Audit Planner | Regulatory obligations and evidence | F | — |

---

# LD-05 — Finance

*Money in, money out, money over time. The domain most likely to be trusted last and valued most.*

### Day-to-Day Money

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-05-001 | Budget Planner | Planned spending by category and period | C | 01 |
| PU-05-002 | Expense Tracker | What was actually spent | C | 01, 07, 08 |
| PU-05-003 | Income Tracker | What actually arrived | C | 03 |
| PU-05-004 | Cash Flow Planner | Timing of money in and out | C | 04 |
| PU-05-005 | Bill Planner | Obligations with due dates | C | 01, 08 |
| PU-05-006 | Subscription Tracker | Recurring charges, including forgotten ones | C | 01 |
| PU-05-007 | Account Overview | Balances across accounts in one place | C | — |
| PU-05-008 | Transaction Categorisation | Making raw transactions meaningful | E | — |
| PU-05-009 | Receipt Vault | Proof of purchase, retrievable | E | 01, 04 |
| PU-05-010 | Shared Expense Planner | Splitting costs with others | E | 08, 10 |
| PU-05-011 | Currency & FX Planner | Multi-currency life | E | 07 |
| PU-05-012 | Cash Envelope Planner | Envelope-style allocation | F | — |

### Saving & Goals

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-05-013 | Savings Planner | Deliberate accumulation | C | 01 |
| PU-05-014 | Savings Goal Planner | Money attached to a specific outcome | C | 01, 07, 08 |
| PU-05-015 | Emergency Fund Planner | Resilience before growth | E | — |
| PU-05-016 | Sinking Fund Planner | Saving for known irregular costs | E | 08 |
| PU-05-017 | Big Purchase Planner | Large one-off acquisitions | E | 07, 08 |
| PU-05-018 | Financial Independence Planner | Long-horizon freedom targets | F | 03 |

### Debt & Obligations

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-05-019 | Debt Planner | All debts, rates, and balances | C | — |
| PU-05-020 | Loan Planner | Individual loan schedules | E | — |
| PU-05-021 | Mortgage Planner | Housing debt over decades | E | 08 |
| PU-05-022 | Debt Payoff Strategy Planner | Avalanche, snowball, and comparisons | E | — |
| PU-05-023 | Credit Health Planner | Understanding and improving creditworthiness | F | — |

### Growth & Protection

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-05-024 | Investment Planner | Strategy and contributions | E | — |
| PU-05-025 | Portfolio Tracker | What is held and how it performs | E | — |
| PU-05-026 | Asset Register | Everything owned of value | E | 08 |
| PU-05-027 | Liability Register | Everything owed | E | — |
| PU-05-028 | Net Worth Planner | The difference, over time | E | 01 |
| PU-05-029 | Retirement Planner | Long-horizon sufficiency | E | 03 |
| PU-05-030 | Pension Planner | Scheme-specific tracking | F | 03 |
| PU-05-031 | Insurance Planner | Coverage, gaps, and renewals | E | 06, 07, 08 |
| PU-05-032 | Tax Planner | Obligations, deadlines, and deductions | E | 03, 04 |
| PU-05-033 | Tax Document Organiser | Evidence gathered before it is needed | E | 01 |
| PU-05-034 | Estate & Will Planner | What happens after | F | 08 |
| PU-05-035 | Charitable Giving Planner | Deliberate generosity | F | 10 |

### Analysis

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-05-036 | Financial Dashboard | The single financial picture | C | 01 |
| PU-05-037 | Spending Analytics | Patterns, trends, and outliers | E | — |
| PU-05-038 | Forecast Planner | Where current behaviour leads | E | 01 |
| PU-05-039 | Scenario Planner | What if income, cost, or rates change | F | 03, 08 |
| PU-05-040 | Financial Health Score | One number, explained | F | — |
| PU-05-041 | Cost of Goal Calculator | The real price of any planned goal | F | all |
| PU-05-042 | Financial Report Builder | Exportable statements | M | 04 |

---

# LD-06 — Health

*Body and mind. The domain with the highest trust requirements and the strictest data handling obligations (see NLB-14).*

### Movement

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-06-001 | Workout Planner | Structured training sessions | C | 01 |
| PU-06-002 | Training Programme Planner | Multi-week progressive programmes | E | 01 |
| PU-06-003 | Exercise Library | Movements, form, and substitutions | E | — |
| PU-06-004 | Activity Log | Everything done, from device or by hand | C | — |
| PU-06-005 | Running Planner | Distance, pace, and race preparation | E | 01, 10 |
| PU-06-006 | Strength Progression Planner | Load over time | E | — |
| PU-06-007 | Yoga & Mobility Planner | Flexibility and movement quality | E | — |
| PU-06-008 | Sports Planner | Team or individual sport commitments | F | 10 |
| PU-06-009 | Step & Movement Planner | Baseline daily activity | E | — |
| PU-06-010 | Rest & Deload Planner | Planned recovery inside training | F | — |

### Nutrition

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-06-011 | Meal Planner | What to eat, when | C | 05, 08 |
| PU-06-012 | Recipe Library | Reusable meals with nutrition data | E | 08 |
| PU-06-013 | Grocery Planner | Shopping derived from meal plans | E | 05, 08 |
| PU-06-014 | Nutrition Tracker | Intake against targets | E | — |
| PU-06-015 | Water Intake Tracker | Hydration | C | — |
| PU-06-016 | Dietary Restriction Planner | Allergies, intolerances, and choices | E | 08 |
| PU-06-017 | Supplement Planner | What is taken and why | F | — |
| PU-06-018 | Meal Prep Planner | Batch cooking logistics | F | 08 |
| PU-06-019 | Fasting Planner | Timed eating windows | M | — |

### Clinical

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-06-020 | Medical Record Vault | Personal health history, securely held | C | 01, 08 |
| PU-06-021 | Appointment Planner | Doctor, dentist, and specialist visits | C | 01, 08 |
| PU-06-022 | Medication Planner | Doses, timing, and adherence | C | 08 |
| PU-06-023 | Prescription & Refill Tracker | Never running out | E | 05 |
| PU-06-024 | Symptom Tracker | Patterns worth showing a clinician | E | — |
| PU-06-025 | Condition Management Planner | Living with a long-term condition | E | 08 |
| PU-06-026 | Test Result Tracker | Results over time, not in isolation | E | — |
| PU-06-027 | Vaccination Record | Immunisation history and due dates | E | 07, 08 |
| PU-06-028 | Care Team Directory | Everyone involved in the user's care | F | 08 |
| PU-06-029 | Recovery & Rehab Planner | Structured return after injury or illness | E | — |
| PU-06-030 | Health Insurance Planner | Coverage against actual care | F | 05 |

### Mind & Rest

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-06-031 | Sleep Planner | Schedule, duration, and quality | C | 01 |
| PU-06-032 | Sleep Log | Observed sleep over time | E | 01 |
| PU-06-033 | Mental Wellness Planner | Deliberate psychological maintenance | C | 01 |
| PU-06-034 | Mood Tracker | State over time with context | E | 01 |
| PU-06-035 | Meditation Planner | Practice and progression | E | 01 |
| PU-06-036 | Stress Management Planner | Identifying and reducing load | E | 01, 03 |
| PU-06-037 | Therapy Planner | Sessions, homework, and progress | F | — |
| PU-06-038 | Breathing & Relaxation Library | Short guided practices | M | — |
| PU-06-039 | Burnout Risk Planner | Early warning from workload and mood signals | F | 01, 03 |

### Measurement & Life Stages

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-06-040 | Health Dashboard | One picture of health | C | 01 |
| PU-06-041 | Weight & Body Composition Tracker | Change over time | E | — |
| PU-06-042 | Vitals Tracker | Blood pressure, heart rate, and similar | E | — |
| PU-06-043 | Device Sync Hub | Wearables and clinical devices into one record | E | — |
| PU-06-044 | Pregnancy Planner | Stage-aware guidance and appointments | F | 08 |
| PU-06-045 | Child Health Planner | Growth, milestones, and immunisations | F | 08 |
| PU-06-046 | Elder Care Planner | Supporting an ageing family member | F | 08 |

---

# LD-07 — Travel

*Movement through the world — short trips, long journeys, and living abroad.*

### Trip Planning

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-07-001 | Trip Planner | The container for a whole journey | C | 01, 05 |
| PU-07-002 | Itinerary Planner | Day-by-day plan on the ground | C | 01 |
| PU-07-003 | Destination Research Planner | Deciding where and when | E | — |
| PU-07-004 | Multi-City Route Planner | Complex routing across stops | E | — |
| PU-07-005 | Road Trip Planner | Driving routes, stops, and legs | E | — |
| PU-07-006 | Adventure & Outdoor Planner | Trekking, climbing, and remote travel | F | 06 |
| PU-07-007 | Group Trip Planner | Coordinating travel for several people | E | 08, 10 |
| PU-07-008 | Business Travel Planner | Travel with a work purpose and a policy | E | 03, 04 |

### Bookings & Logistics

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-07-009 | Flight Planner | Flights, connections, and changes | C | 05 |
| PU-07-010 | Accommodation Planner | Where to stay, and when it's confirmed | C | 05 |
| PU-07-011 | Ground Transport Planner | Trains, cars, and transfers | E | — |
| PU-07-012 | Booking Vault | Every confirmation in one retrievable place | C | 01 |
| PU-07-013 | Packing Planner | What to bring, per trip type | C | — |
| PU-07-014 | Packing Template Library | Reusable lists by trip archetype | E | — |
| PU-07-015 | Travel Document Planner | Passports, IDs, and their expiry dates | E | 01 |
| PU-07-016 | Visa Planner | Requirements, applications, and timelines | E | 01 |
| PU-07-017 | Travel Insurance Planner | Coverage for the specific trip | E | 05, 06 |
| PU-07-018 | Health & Vaccination Planner | Medical prerequisites for a destination | F | 06 |
| PU-07-019 | Pet Travel Planner | Bringing animals along | M | 08 |

### Money & On the Ground

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-07-020 | Travel Budget Planner | The cost of the trip, planned | C | 05 |
| PU-07-021 | Travel Expense Tracker | The cost of the trip, actual | E | 05 |
| PU-07-022 | Currency Planner | Exchange and local payment | E | 05 |
| PU-07-023 | Maps & Places Planner | Saved locations tied to the itinerary | E | — |
| PU-07-024 | Local Guide Workspace | Context, customs, and language basics | F | 02 |
| PU-07-025 | Reservation Planner | Restaurants, tickets, and timed entries | E | 01 |
| PU-07-026 | Offline Travel Kit | Everything needed without connectivity | E | — |
| PU-07-027 | Emergency & Safety Planner | Contacts, embassies, and contingencies | F | 06, 08 |

### After & Ongoing

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-07-028 | Travel Journal | The record of the experience | E | 01, 09 |
| PU-07-029 | Photo & Memory Planner | Organising what was captured | F | 09 |
| PU-07-030 | Travel Bucket List | Where to go, someday | E | 01 |
| PU-07-031 | Loyalty & Points Planner | Miles, status, and redemption | F | 05 |
| PU-07-032 | Relocation Planner | Moving to another country or city | F | 05, 08 |
| PU-07-033 | Digital Nomad Planner | Working while moving | M | 03, 05 |

---

# LD-08 — Family

*Shared life with the people closest to you. The domain where collaboration is the default rather than the exception.*

### Shared Coordination

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-08-001 | Family Dashboard | The household's shared picture | C | all |
| PU-08-002 | Shared Calendar | Everyone's commitments, visible | C | 01 |
| PU-08-003 | Shared Task Planner | Who is doing what | C | 01 |
| PU-08-004 | Chore Planner | Recurring household work, fairly divided | E | 01 |
| PU-08-005 | Family Goal Planner | Objectives held jointly | E | 01 |
| PU-08-006 | Family Meeting Planner | Regular household check-ins | F | — |
| PU-08-007 | Permission & Visibility Planner | Who in the family sees what | C | — |
| PU-08-008 | Family Budget Planner | Shared money | E | 05 |

### Children & Parenting

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-08-009 | Child Profile Planner | One place per child | E | 02, 06 |
| PU-08-010 | Parenting Planner | Deliberate approach, not just reaction | E | — |
| PU-08-011 | School Planner | Term dates, contacts, and requirements | E | 02 |
| PU-08-012 | Homework Support Planner | Helping without taking over | E | 02 |
| PU-08-013 | Activity & Club Planner | Extracurricular logistics | E | 01 |
| PU-08-014 | Childcare Planner | Coverage and arrangements | E | 05 |
| PU-08-015 | Child Milestone Tracker | Development over time | F | 06 |
| PU-08-016 | Allowance & Money Education Planner | Teaching children about money | F | 05 |
| PU-08-017 | Screen Time & Rules Planner | Household digital boundaries | F | 01 |
| PU-08-018 | Teen Independence Planner | Handing over responsibility gradually | M | — |

### Home

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-08-019 | Home Dashboard | The house as a managed thing | E | — |
| PU-08-020 | Home Maintenance Planner | Preventive upkeep on a schedule | E | 05 |
| PU-08-021 | Home Improvement Planner | Projects with budgets and phases | E | 05 |
| PU-08-022 | Shopping List | Household purchasing | C | 05, 06 |
| PU-08-023 | Meal & Household Menu Planner | Feeding a household, not a person | E | 06 |
| PU-08-024 | Inventory & Belongings Planner | What's owned and where it is | F | 05 |
| PU-08-025 | Warranty & Manual Vault | Documentation for things that break | F | 01 |
| PU-08-026 | Moving Planner | Relocating a household | F | 05, 07 |
| PU-08-027 | Garden Planner | Seasonal outdoor work | M | — |
| PU-08-028 | Home Security Planner | Access, keys, and contingencies | M | — |

### Events & Relationships

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-08-029 | Family Event Planner | Gatherings large and small | E | 10 |
| PU-08-030 | Birthday & Anniversary Planner | Never forgetting the ones that matter | C | 01 |
| PU-08-031 | Gift Planner | Ideas, budgets, and history | E | 05 |
| PU-08-032 | Holiday & Tradition Planner | Recurring seasonal occasions | E | 05, 07 |
| PU-08-033 | Celebration Budget Planner | The cost of occasions | F | 05 |
| PU-08-034 | Family Archive | Photos, documents, and history | F | 09 |
| PU-08-035 | Family Tree Planner | Ancestry and relationships | M | — |

### Pets & Care

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-08-036 | Pet Profile Planner | One place per animal | E | — |
| PU-08-037 | Pet Health Planner | Vet visits, medication, and vaccinations | E | 06, 05 |
| PU-08-038 | Pet Care Routine Planner | Feeding, walking, and grooming | F | 01 |

---

# LD-09 — Creativity

*Making things. The domain most likely to be extended by the marketplace, because creative workflows are highly specific.*

### Writing

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-09-001 | Writing Project Planner | Any long-form writing, from idea to done | C | 02 |
| PU-09-002 | Book / Manuscript Planner | Chapters, drafts, and structure | E | — |
| PU-09-003 | Story & Plot Planner | Narrative structure and arcs | E | — |
| PU-09-004 | Character & World Bible | Consistency across a long work | F | — |
| PU-09-005 | Blog & Article Planner | Shorter pieces on a cadence | E | 04 |
| PU-09-006 | Newsletter Planner | Recurring publication | E | 04, 10 |
| PU-09-007 | Screenplay Planner | Script structure and formatting | F | — |
| PU-09-008 | Poetry & Short Form Workspace | Small pieces, collected | M | — |
| PU-09-009 | Editing & Revision Planner | Draft passes with purpose | E | — |
| PU-09-010 | Submission & Publishing Planner | Getting work in front of people | F | 03 |

### Visual & Design

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-09-011 | Design Project Planner | Client or personal design work | E | 03, 04 |
| PU-09-012 | Photography Planner | Shoots, locations, and shot lists | E | 07 |
| PU-09-013 | Photo Library Planner | Organising and finding images | F | 07, 08 |
| PU-09-014 | Painting & Illustration Planner | Studio work and series | M | — |
| PU-09-015 | Portfolio Planner | Curating work for an audience | E | 03 |
| PU-09-016 | Moodboard & Reference Planner | Visual research | E | — |
| PU-09-017 | Brand Asset Planner | Consistent visual identity | F | 04 |
| PU-09-018 | Craft & Maker Planner | Physical making, materials, and steps | M | 05 |

### Audio & Video

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-09-019 | Video Project Planner | From concept to published | E | 04 |
| PU-09-020 | Filmmaking Planner | Pre-production through post | F | — |
| PU-09-021 | Shot List & Storyboard Planner | Visual planning before shooting | F | — |
| PU-09-022 | Podcast Planner | Episodes, guests, and publishing | E | 10 |
| PU-09-023 | Episode & Guest Planner | The recurring-show workflow | E | 10 |
| PU-09-024 | Music Project Planner | Writing and producing music | E | 02 |
| PU-09-025 | Songwriting Workspace | Lyrics, structure, and versions | M | — |
| PU-09-026 | Recording Session Planner | Studio time and takes | M | — |
| PU-09-027 | Live Performance Planner | Gigs, sets, and logistics | M | 07 |
| PU-09-028 | Streaming Planner | Live broadcast schedule and format | F | 10 |

### Publishing & Audience

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-09-029 | Content Calendar | Everything publishing, everywhere | C | 04 |
| PU-09-030 | Social Media Planner | Per-platform posting and cadence | E | 04, 10 |
| PU-09-031 | YouTube Channel Planner | Video channel as an ongoing project | E | 04 |
| PU-09-032 | Audience Analytics | Who is out there and what they respond to | E | 04 |
| PU-09-033 | Monetisation Planner | Turning creative work into income | F | 05, 03 |
| PU-09-034 | Collaboration & Credit Planner | Who did what, and who is owed | F | 10 |
| PU-09-035 | Rights & Licensing Planner | Ownership and permitted use | F | 04 |

### Practice & Ideas

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-09-036 | Idea Inbox | Capturing ideas before they evaporate | C | all |
| PU-09-037 | Creative Practice Planner | Showing up regularly | E | 01, 02 |
| PU-09-038 | Inspiration Library | Collected references and influences | E | 02 |
| PU-09-039 | Creative Block Planner | Structured ways through a stall | M | 06 |
| PU-09-040 | Project Archive | Finished work, retrievable later | F | 01 |

---

# LD-10 — Community

*Life with others beyond the household. This domain also carries the platform's network effects and its marketplace.*

### People & Groups

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-10-001 | Friends & Circles Planner | Deliberately maintaining friendships | E | 01, 08 |
| PU-10-002 | Group Planner | Any ongoing group of people | C | — |
| PU-10-003 | Club & Society Planner | Membership organisations | E | — |
| PU-10-004 | Team Planner | Groups organised around a shared activity | E | 06 |
| PU-10-005 | Membership & Dues Planner | Belonging that costs money | F | 05 |
| PU-10-006 | Directory & Roles Planner | Who is in a community, and what they do | E | — |

### Events & Gathering

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-10-007 | Event Planner | Organising a gathering end to end | C | 01, 08 |
| PU-10-008 | RSVP & Guest Planner | Who is coming | E | 08 |
| PU-10-009 | Venue & Logistics Planner | Where and how | F | 05 |
| PU-10-010 | Meetup Planner | Recurring informal gatherings | E | — |
| PU-10-011 | Volunteer Coordination Planner | Organising unpaid effort | F | — |
| PU-10-012 | Fundraiser Planner | Raising money for a cause | F | 05 |

### Challenges & Motivation

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-10-013 | Challenge Planner | Time-boxed shared efforts | C | 01, 06, 02 |
| PU-10-014 | League & Leaderboard | Friendly competition with standings | E | 06 |
| PU-10-015 | Accountability Group Planner | Small groups holding each other to plans | E | 01 |
| PU-10-016 | Streak & Team Goal Planner | Collective progress, not individual | E | 01, 06 |
| PU-10-017 | Rewards & Recognition Planner | Acknowledging contribution | F | — |

### Knowledge & Discussion

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-10-018 | Forum & Discussion Planner | Asynchronous community conversation | E | — |
| PU-10-019 | Q&A Planner | Questions matched to people who can answer | F | 02 |
| PU-10-020 | Community Knowledge Base | What the group knows, written down | E | 02 |
| PU-10-021 | Announcement Planner | Reaching a community without spamming it | F | — |
| PU-10-022 | Moderation Planner | Keeping a community healthy | F | — |
| PU-10-023 | Code of Conduct & Governance | The rules and how they're applied | F | — |

### Mentorship & Exchange

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-10-024 | Mentorship Planner | Structured mentoring relationships | E | 03, 02 |
| PU-10-025 | Skill Exchange Planner | Trading capability between people | F | 02 |
| PU-10-026 | Peer Review Planner | Structured feedback on each other's work | F | 02, 09 |
| PU-10-027 | Introduction & Referral Planner | Connecting people usefully | M | 03 |

### Marketplace

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-10-028 | Template Marketplace | Sharing and acquiring planner templates | C | all |
| PU-10-029 | Module Marketplace | Community-built planners and modules | E | all |
| PU-10-030 | Automation Marketplace | Shareable automation recipes | E | all |
| PU-10-031 | Creator Publishing Planner | For people who build for the marketplace | F | 09, 05 |
| PU-10-032 | Marketplace Earnings Planner | Revenue from published work | M | 05 |

---

# LD-11 — Sports & Athletics

*Competing and training, alone or in a team. Distinct from LD-06 Health because the driver here is performance against opponents or a clock, not personal wellbeing.*

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-11-001 | Training Planner | Structured training against a competitive calendar | C | 06 |
| PU-11-002 | Team Planner | Roster, positions, and team-level planning | E | 10 |
| PU-11-003 | Tournament & League Planner | Brackets, fixtures, and standings | E | 10 |
| PU-11-004 | Match / Fixture Planner | Preparation for a single game or race | E | 01 |
| PU-11-005 | Performance Analytics | Stats and trends over a season | C | 06 |
| PU-11-006 | Injury & Recovery Planner | Structured return to competition | E | 06 |
| PU-11-007 | Coaching Planner | For coaches: sessions and athlete development | F | 03 |
| PU-11-008 | Sport-Specific Playbook | Tactics and set plays | F | — |
| PU-11-009 | Officiating & Scorekeeping Planner | Running a match from the sidelines | M | — |
| PU-11-010 | Fan / Spectator Planner | Following a team or league | M | 10 |
| PU-11-011 | Esports Planner | Practice, scrims, and tournaments for competitive gaming | E | 12 |
| PU-11-012 | Fitness Testing Planner | Benchmarking athletic capability | F | 06 |
| PU-11-013 | Equipment & Gear Planner | Sport-specific equipment tracking | F | 05 |
| PU-11-014 | Youth Sports Planner | Managing a child's sporting commitments | F | 08 |

---

# LD-12 — Technology & Engineering

*Building and shipping technical work. This domain is where NexaLife itself would plan its own engineering, if it used itself.*

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-12-001 | Software Project Planner | End-to-end delivery of a software product | C | 04 |
| PU-12-002 | Sprint / Agile Planner | Iteration-based delivery | C | 04 |
| PU-12-003 | Release Planner | Coordinating what ships and when | E | 04 |
| PU-12-004 | Testing & QA Planner | Coverage and quality gates | E | — |
| PU-12-005 | Bug & Issue Tracker | Defects from report to resolution | C | — |
| PU-12-006 | Product Roadmap Planner | Where the product is headed | E | 04 |
| PU-12-007 | DevOps & Infrastructure Planner | Deployment, environments, and reliability | E | — |
| PU-12-008 | Architecture & Design Doc Workspace | Technical decisions, recorded and reasoned | E | 01 |
| PU-12-009 | Incident Response Planner | Handling and learning from outages | F | 04 |
| PU-12-010 | On-Call Planner | Rotation and coverage | F | 01 |
| PU-12-011 | Code Review Planner | Review queues and turnaround | F | — |
| PU-12-012 | API & Integration Planner | Tracking integration work and contracts | F | — |
| PU-12-013 | Tech Debt Planner | Making deferred work visible and prioritised | F | — |
| PU-12-014 | Hackathon Planner | Short, intense build events | M | 10 |
| PU-12-015 | Open Source Contribution Planner | Personal contribution tracking | M | 03 |

---

# LD-13 — Real Estate & Property

*Owning, renting, building, and maintaining property — as an occupant, a landlord, or a developer.*

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-13-001 | Property Portfolio Planner | Everything owned, in one place | C | 05 |
| PU-13-002 | Property Search Planner | Comparing and shortlisting properties | E | 05 |
| PU-13-003 | Purchase & Closing Planner | The transaction itself | E | 05 |
| PU-13-004 | Rental Management Planner | Landlord side: tenants, leases, rent | E | 05 |
| PU-13-005 | Tenant Planner | Tenant side: lease, deposit, obligations | E | 05 |
| PU-13-006 | Construction Planner | Ground-up building projects | F | 04 |
| PU-13-007 | Renovation Planner | Improvement projects on existing property | E | 05, 08 |
| PU-13-008 | Interior Design Planner | Space and furnishing plans | E | 09, 17 |
| PU-13-009 | Facility Management Planner | Ongoing operation of a building | F | 04 |
| PU-13-010 | Property Maintenance Schedule | Preventive upkeep across a portfolio | E | 08 |
| PU-13-011 | Real Estate Investment Analysis | Yield, appreciation, and comparison | F | 05 |
| PU-13-012 | Contractor & Vendor Planner | Who does the work | F | 04 |

---

# LD-14 — Agriculture

*Growing things, at any scale, from a kitchen garden to a working farm.*

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-14-001 | Crop Planner | Planting, rotation, and yield planning | E | — |
| PU-14-002 | Farm Operations Planner | The whole operation, coordinated | E | 04 |
| PU-14-003 | Livestock Planner | Animals, health, and breeding cycles | E | — |
| PU-14-004 | Irrigation Planner | Water scheduling against crop and weather | E | — |
| PU-14-005 | Harvest Planner | Timing and logistics of harvest | E | 05 |
| PU-14-006 | Equipment & Maintenance Planner | Machinery upkeep and scheduling | F | — |
| PU-14-007 | Farm Budget Planner | Costs and revenue specific to farming | F | 05 |
| PU-14-008 | Pest & Disease Planner | Monitoring and response | F | — |
| PU-14-009 | Weather-Dependent Task Planner | Work sequenced against forecasts | F | — |
| PU-14-010 | Market & Sales Planner | Selling produce or livestock | F | 04 |
| PU-14-011 | Small-Scale / Hobby Garden Planner | The home-garden version of the same idea | M | 01 |

---

# LD-15 — Government & Public Service

*Serving or navigating public institutions — running for office, running a public project, or coordinating a public response.*

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-15-001 | Public Project Planner | Municipal and civic projects | E | 04 |
| PU-15-002 | Campaign Planner | Election and advocacy campaigns | E | 04, 10 |
| PU-15-003 | Disaster & Emergency Response Planner | Coordinated response to a crisis | E | 08 |
| PU-15-004 | Public Health Programme Planner | Population-level health initiatives | E | 06 |
| PU-15-005 | Infrastructure Planner | Public works planning | F | 04 |
| PU-15-006 | Public Consultation Planner | Structured community input | F | 10 |
| PU-15-007 | Constituent Casework Planner | Tracking individual constituent issues | F | — |
| PU-15-008 | Policy Development Planner | Drafting and tracking policy through process | F | — |
| PU-15-009 | Grant & Public Funding Planner | Public-sector funding cycles | F | 05 |
| PU-15-010 | Regulatory Compliance Planner | Meeting public-sector obligations | F | 04 |
| PU-15-011 | Public Meeting Planner | Agendas, minutes, and public record | F | — |
| PU-15-012 | Volunteer Mobilisation Planner | Coordinating volunteers at scale | F | 10 |

---

# LD-16 — Science & Research

*Formal inquiry, from lab to publication. Distinct from LD-02 Education's research tools, which serve a student; this domain serves a researcher.*

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-16-001 | Research Project Planner | A study from question to conclusion | C | 02 |
| PU-16-002 | Laboratory Planner | Bench work, protocols, and scheduling | E | — |
| PU-16-003 | Clinical Trial Planner | Regulated, multi-phase trial management | F | 06 |
| PU-16-004 | Grant Planner | Applications, deadlines, and reporting | E | 05 |
| PU-16-005 | Publication Planner | Manuscripts through peer review | E | 02 |
| PU-16-006 | Patent Planner | Filing and prosecution timelines | F | — |
| PU-16-007 | Data Collection Planner | Structured, auditable data gathering | E | — |
| PU-16-008 | Literature Review Planner | Systematic survey of prior work | F | 02 |
| PU-16-009 | Collaboration & Co-Author Planner | Multi-institution research coordination | F | 10 |
| PU-16-010 | Conference & Symposium Planner | Presenting research to peers | F | 03, 07 |
| PU-16-011 | Ethics & IRB Approval Planner | Regulatory approval before work begins | F | — |
| PU-16-012 | Equipment & Reagent Inventory | Lab supplies and calibration schedules | M | — |
| PU-16-013 | Research Funding Portfolio | Multiple grants tracked together | F | 05 |

---

# LD-17 — Lifestyle & Home

*Personal style and the domestic environment — the parts of daily life that are about how things look and feel, not what they accomplish.*

| ID | Planner | What it does | Tier | Links |
| --- | --- | --- | --- | --- |
| PU-17-001 | Wardrobe Planner | What is owned, and what it can be worn with | C | 05 |
| PU-17-002 | Outfit & Capsule Planner | Deliberate outfit and capsule-wardrobe planning | E | — |
| PU-17-003 | Shopping Planner | Deliberate, budgeted purchasing | E | 05 |
| PU-17-004 | Home Decor Planner | Styling a living space | E | 13 |
| PU-17-005 | Seasonal Refresh Planner | Home and wardrobe changes with the seasons | E | — |
| PU-17-006 | Sustainability Planner | Personal environmental footprint and goals | E | 05 |
| PU-17-007 | Beauty & Grooming Planner | Routines and product tracking | F | 06 |
| PU-17-008 | Personal Style Profile | Preferences that inform recommendations elsewhere | F | 03, 09 |
| PU-17-009 | Decluttering & Minimalism Planner | Structured letting-go | F | 08 |
| PU-17-010 | Gift & Occasion Style Planner | Style-aware gift planning | M | 08 |
| PU-17-011 | Second-Hand & Resale Planner | Selling or sourcing pre-owned items | M | 05 |

---

## Cross-Domain Hubs

Some planners appear in one domain but are load-bearing for all of them. These are the seams where cross-domain intelligence actually happens, and they are the highest-priority items in the entire catalogue.

| Hub | Home | Why it is a hub |
| --- | --- | --- |
| Calendar Hub | PU-01-010 | Every domain writes time into it |
| Goal Planner | PU-01-013 | Every domain contributes progress to goals |
| Personal Dashboard | PU-01-043 | The single surface where domains meet |
| Document Vault | PU-01-045 | Documents belong to life, not to modules |
| Financial Dashboard | PU-05-036 | Almost every plan has a cost |
| Health Dashboard | PU-06-040 | Capacity constrains every other plan |
| Shared Calendar | PU-08-002 | Where individual and household plans reconcile |
| Idea Inbox | PU-09-036 | Capture must never require choosing a domain first |
| Template Marketplace | PU-10-028 | How the catalogue grows without us building it |

**Design consequence:** these nine must be specified before the planners that depend on them. A planner built before its hub will encode assumptions the hub then has to honour forever.

---

## Worked cross-domain examples

Volume 03 named three. Here they are against real catalogue IDs, which is how the cross-domain graph in NLB-09 will be validated.

**"I'm running a marathon in October."**

```
PU-01-013 Goal Planner          → creates the goal
PU-06-005 Running Planner       → generates a training programme
PU-06-011 Meal Planner          → adjusts intake to training load
PU-06-031 Sleep Planner         → raises the recovery target
PU-01-010 Calendar Hub          → places every session
PU-05-014 Savings Goal Planner  → race entry, travel, and kit
PU-07-001 Trip Planner          → travel to the race
PU-10-013 Challenge Planner     → optional: training with others
```

**"My exams start on the 12th."**

```
PU-02-006 Exam Planner          → anchors the date and format
PU-02-005 Revision Planner      → builds a spaced revision schedule
PU-01-007 Time Blocking Planner → protects the study blocks
PU-01-023 Habit Tracker         → suspends non-essential habits
PU-01-037 Focus Sessions        → tracks real study time
PU-06-031 Sleep Planner         → defends sleep against cramming
PU-06-036 Stress Planner        → watches for overload
```

**"We're taking the family to Spain in July."**

```
PU-07-001 Trip Planner          → the container
PU-08-002 Shared Calendar       → everyone's availability
PU-04-049 Leave Planner         → time off from work
PU-07-020 Travel Budget Planner → planned cost
PU-05-014 Savings Goal Planner  → funding it
PU-07-013 Packing Planner       → per person, per age
PU-07-015 Document Planner      → passport expiry checks
PU-08-003 Shared Tasks          → who does what before departure
```

Each arrow is a claim the data model must support. Volume 09 will either honour these or send this catalogue back for revision.

---

## What this volume deliberately does not do

- **It does not specify behaviour.** No screens, schemas, states, or rules. That is NLB-07 and the per-planner specs.
- **It does not commit a roadmap.** Tiers are a sequencing hypothesis to be tested against personas (NLB-05) and the PRD (NLB-06).
- **It does not guarantee every entry ships.** Roughly 415 entries exist here so the architecture is designed against the full shape of life. Entries that cannot satisfy the Traceability Rule when specified will be retired, ID retained.
- **It does not close the catalogue.** New entries are added by amendment, taking the next free ID in their domain.

---

## Open questions for later volumes

| # | Question | Resolved by |
| --- | --- | --- |
| 1 | Do users adopt by domain, or by individual planner? | NLB-05 Personas |
| 2 | What is the minimum coherent v1 — is 100 Core entries too many? | NLB-06 PRD |
| 3 | How much of a planner is configuration versus code? | NLB-07 Engine |
| 4 | Does every planner need a specialist AI, or do domains share one? | NLB-08 AI Universe |
| 5 | Can cross-domain links be declarative, or must each pair be hand-built? | NLB-09 Data Model |
| 6 | Where is the boundary between Core, Marketplace, and integration? | NLB-15 Marketplace |

Question 3 is the most consequential. If planners are largely configuration over a shared engine, this catalogue is achievable. If each planner is bespoke code, the Core tier alone is years of work and the catalogue must shrink. **NLB-07 should be written next.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-04 | Initial catalogue. 415 entries across 10 Life Domains, with build tiers, cross-domain links, and nine cross-domain hubs identified. |
| 1.1 | 2026-08-05 | Added 88 entries across seven new Life Domains (LD-11–LD-17: Sports & Athletics, Technology & Engineering, Real Estate & Property, Agriculture, Government & Public Service, Science & Research, Lifestyle & Home), following the NLB-03 v1.1 domain amendment. Total entries: 415 → 503. |

---

**End of Volume 04 (Version 1.1)**
