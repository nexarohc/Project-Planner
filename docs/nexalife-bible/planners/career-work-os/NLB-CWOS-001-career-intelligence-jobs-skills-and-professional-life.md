# 📖 NEXALIFE BIBLE — Career, Work & Professional Growth Operating System (CWOS)

## Part 1 — Career Intelligence, Jobs, Projects, Skills, Networking & Professional Life

| Field | Value |
| --- | --- |
| Document ID | NLB-CWOS-001 |
| Series | Career, Work & Professional Growth OS (Volume 29) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★★ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Home domain | LD-03 Career (`NLB-03`) |
| Catalogue anchor | PU-03-001 – PU-03-034 (`NLB-04`) |
| Dependencies | `NLB-05` · `NLB-09` · `NLB-10` · `NLB-12` · `NLB-21` · `NLB-RSOS-*` · `NLB-FWOS-*` |

---

## Purpose

CWOS manages the user's professional life from one unified environment: career planning, jobs, freelancing, projects, clients, skills, learning, networking, applications, interviews, work schedules, professional documents, income growth, and career transitions.

> **Turn a career from a collection of disconnected activities into an intelligent professional operating system.**

This is the MPSS-compliant (`NLB-15`) specification for `NLB-04`'s Career catalogue — PU-03-001 Career Roadmap through PU-03-034 Conference & Event Planner.

### Scope boundaries

Three neighbouring bibles overlap this domain, and the split is deliberate:

| Boundary | Owned by | CWOS's role |
| --- | --- | --- |
| Professional relationships | **CWOS** | `NLB-RSOS-001` explicitly defers professional contacts to CareerOS with separate visibility controls. CWOS owns recruiters, clients, mentors, and industry contacts; RSOS owns personal relationships. |
| Communication intelligence | **RSOS** (`NLB-RSOS-002`) | CWOS consumes the extraction/drafting/follow-up engine rather than reimplementing it; it adds career-specific routing (recruiter → job, client → project). |
| Career income | **FWOS** (`NLB-FWOS-*`) | CWOS produces income events and freelance profitability; FWOS owns budgeting, tax, and wealth. |
| Running an organization | Future Business OS (LD-04) | CWOS's Entrepreneur Mode (Part 2) is *career-scale* — validating an idea, tracking a side business becoming full-time. Organization-scale operations (CRM at scale, HR, payroll, compliance) belong to LD-04's own bible. |

---

## Career Architecture

```
                    CAREER OS
                        │
       ┌────────────────┼────────────────┐
       │                │                │
     CAREER           WORK             GROWTH
       │                │                │
     Goals           Projects          Skills
     Jobs            Clients           Learning
     Applications    Tasks             Network
     Interviews      Deliverables      Portfolio
```

---

## Professional Identity

**Master Profile** is the single source of truth — name, headline, summary, experience, skills, education, certifications, projects, achievements, portfolio, languages, interests. Resumes, CVs, external profiles, portfolios, applications, proposals, and bios all derive from it, and updating the master can optionally update dependents. This is `NLB-07`'s One Source of Truth applied to professional identity.

**Multiple Career Identities** support users pursuing more than one direction (e.g. pharmaceutical business development, AI consulting, freelance design), each with its own resume, bio, skills, portfolio, and job preferences — without duplicating the underlying experience records.

---

## Goals, Roadmap & Gap Analysis

Career goals cover next role, salary target, industry transition, leadership, remote work, freelance income, and entrepreneurship — instances of the platform Goal Planner (`NLB-04`, PU-01-013).

**Career Roadmap** sequences current role → required skills → required experience → target role.

**Gap Analysis** compares the user's profile against a target role and names the priority gap. **This is a development aid, not an employer's actual hiring score** — an important framing, since presenting it otherwise would imply knowledge of hiring outcomes the system does not have.

---

## Skills

**Skill Graph** connects related competencies (Negotiation → Sales, Leadership, Partnerships, Business Development), contributing Skill nodes to the Universal Knowledge Graph (`NLB-NXOS-005`).

**Levels** (Beginner → Developing → Working → Advanced → Expert) require **evidence** rather than self-assertion: a completed project, deal, certification, client feedback, work sample, or performance result. Claiming "Expert in negotiation" with nothing attached is a weaker record than the same claim backed by a closed deal — and the evidence is what later populates resumes and interview stories.

**Achievement Engine** converts accomplishments into structured Action → Scope → Result form (*"Expanded distribution" · "8 countries" · "New international revenue channel"*), with **the user confirming the final wording.**

---

## Jobs & Applications

**Discovery** spans full-time, part-time, remote, contract, freelance, consulting, internship, and executive roles, filtered by the user's stated preferences.

**Job Matching** compares an opportunity against the profile. **The score is an internal aid, not a prediction of hiring success** — Part 2 sharpens this into a hard phrasing rule.

**Pipeline**: Discovered → Saved → Researching → Applied → Screening → Interview → Offer → Accepted, with each application storing company, position, date, resume version, cover letter, contact, status, salary, and notes, plus a timeline. **Duplicate detection** prevents re-applying to a role already applied for.

**Cover Letter and Answer Assistants** draft from the user's *verified* experience. **They must not invent employers, achievements, certifications, skills, or results** — the Career-domain instance of `NLB-06`'s no-fabrication rule, and the one most likely to cause real harm if violated, since a fabricated resume claim follows the user into an interview.

**ATS Optimization** compares resume against job description and reports keyword coverage and gaps. **It does not recommend keyword stuffing or misleading claims.**

**Company Research** organizes overview, industry, products, leadership, culture, and recent news, sourced from reliable current sources where available, and compares against the user's own stated priorities (compensation, remote, growth, mission, travel, stability, learning).

---

## Interviews

**Interview Center** consolidates upcoming interviews. **Preparation** generates company and role briefings, likely questions, user-specific examples, and questions to ask.

**STAR Story Library** stores reusable Situation/Task/Action/Result narratives, surfaced by relevance when a question type arises (*"Tell me about a difficult negotiation"*). This is where the skill-evidence discipline pays off — stories are drawn from recorded reality, not improvised.

**Mock interviews** simulate recruiter, hiring manager, technical, executive, and client-presentation formats, with feedback on clarity, structure, specificity, and results.

**Interview Memory** records questions asked, interviewer interests, follow-up items, and promised next steps, feeding the **Follow-Up Engine** (*"You interviewed 4 days ago. Would you like to send a follow-up?"*) — which drafts but does not send.

---

## Offers

**Offer Center** captures base, bonus, equity, location, and joining date. **Comparison** weighs multiple offers across user-weighted factors, and **Total Compensation** distinguishes **guaranteed from variable** components — the Career equivalent of `NLB-FWOS-001`'s contribution-vs-market separation, and mandatory for the same reason: conflating them overstates what the user is actually being offered.

**Negotiation** support prepares talking points, market questions, counteroffer drafts, and non-cash alternatives. **The user decides what to send** (`NLB-NIC-002`).

---

## Transitions & Freelance Work

**Career Transition Mode** maps transferable skills, gaps, and a bridge plan (projects, courses, portfolio, networking) for a change of field.

**Career Experiments** test a path before committing — completing one freelance project in a target industry, then reviewing enjoyment, income, skill development, and market demand. This mirrors `NLB-HOS-005`'s Wellness Experiments: structured, small, and reviewed against reality rather than assumption.

**Freelance Workspace** tracks client projects (value, deadline, status). **Client CRM** maintains contact, project history, proposals, invoices, notes, and follow-ups, connecting to FWOS's business finance (`NLB-FWOS-002`). **Proposal Builder** drafts scope, deliverables, timeline, pricing, and terms **for user approval before sending.**

**Project Profitability** computes effective hourly rate net of expenses — the number freelancers most often fail to calculate, and the reason it's specified rather than left implicit.

---

## Time & Work

**Time tracking** connects work to the Calendar Hub: client work, learning, admin, networking. **Billable hours** and **Professional Time Audit** answer *"Where did my work time go this month?"*

**Workload View** and overload warnings (*"Your planned workload exceeds your weekly target by 8 hours"*) use the user's own configured limits, suggesting rescheduling rather than imposing it.

**Work Focus sessions** connect task, calendar, project, client, and time tracking — the Career instance of the Focus Mode pattern established in `NLB-SP-004`.

---

## Documents, Learning & Portfolio

**Professional Document Vault** stores resumes, certificates, portfolios, contracts, offer letters, performance reviews, and recommendation letters (`NLB-04`, PU-01-045).

**Certification Tracker** monitors completion and expiry. **Skill Development Plans** sequence course → project → certification → portfolio, and the **Learning → Project** connection is deliberate: learning that never becomes evidence doesn't advance a career.

**Learning ROI** compares cost and time against skill development, portfolio, and eligibility. **Nexa does not guarantee salary increases.**

**Portfolio Builder** creates project pages (problem, process, skills, results, screenshots, files, testimonials) with versions targeting employers, clients, investors, universities, or marketplaces.

The **Career Knowledge Graph** — Course → Skill → Project → Portfolio → Job → Career Goal — is CWOS's core intelligence structure, and its edges are the same `Requires` / `Contributes To` types formalized in `NLB-NXOS-005`.

---

## Networking

Professional contacts are categorized (recruiter, client, colleague, mentor, partner, industry expert, alumni) with role, company, last interaction, relationship, and notes.

**Networking reminders** (*"You haven't connected with this important contact in 90 days"*) **suggest, never force** — consistent with `NLB-RSOS-001`'s prohibition on guilt-driven relationship mechanics, which applies equally here.

**Relationship Memory**, **Network Map**, **Mentorship Mode**, and **Professional Events** (with post-event follow-up capture) complete the networking layer, sharing RSOS's data model while keeping professional visibility separate from personal.

---

## Intelligence & Decisions

**Career Intelligence Brief** (optional, weekly) summarizes relevant jobs, applications needing follow-up, skill milestones, networking opportunities, and upcoming interviews.

**Career Opportunity Graph** connects Skill → Job → Company → Contact → Interview → Offer → Career Goal — an intelligent career graph rather than a job board.

**Career Risk Monitor** flags declining skill relevance, industry contraction, heavy dependence on one client, expiring certifications, and ending contracts. **These are signals to review, not predictions.**

**Career Resilience** shows skills, portfolio, network, savings, and pipeline as separate dimensions — **no single score determines career decisions**, matching the multi-dimensional refusal in HealthOS and FWOS.

**Career + Finance**: a relocation or offer decision models salary difference, rent, travel, taxes, lifestyle, and savings impact through FWOS.

**Career + Life**: Career → Income → Time → Family → Health → Location → Life Goals. **A career decision is evaluated against the whole life, not salary alone** — LOUPE (`NLB-21`) in its most consequential application.

**Job Decision Simulator** and **Career Satisfaction Journal** (energy, enjoyment, growth, stress, meaning, compensation, balance) support decisions with the user's own recorded experience.

**Burnout prevention** flags sustained overload against configured limits — **a planning feature, not a medical diagnosis** (health escalation belongs to `NLB-HOS-*`).

---

## Reset, Automation & Privacy

**Career Reset** guides: Where am I? → What do I want? → What am I good at? → What does the market need? → What gaps exist? → What can I test? → What next? Producing 30-day / 90-day / 1-year action plans.

**Automation** covers low-risk administrative work only: job tracking, reminders, document organization, interview prep, follow-up reminders, portfolio updates.

**High-impact actions always require confirmation** — applying to a job, sending a proposal or message, accepting an offer, signing a contract. **The assistant prepares; the user decides.**

**Privacy** — resume access, job history, salary, employer and client information, and private notes are all separately controlled. **Employer separation**: on changing companies, personal career data remains the user's, while company-confidential information stays subject to applicable agreements. **Export and deletion** cover resumes, portfolios, skills, timeline, certifications, applications, and permitted contacts.

---

## Philosophy

Nexa does not define success as highest salary:

> **Career success = income + growth + freedom + meaning + life fit** — weighted differently by every user.

**Don't just help the user get another job. Help them build a career that supports the life they actually want.**

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Initial CWOS foundation. Establishes the master professional identity with multiple career identities, evidence-backed skill levels, the job pipeline with no-fabrication constraints on generated materials, interview preparation via the STAR library, offer comparison with guaranteed-vs-variable separation, freelance profitability, and the Career Knowledge Graph. States scope boundaries against RSOS, FWOS, and a future Business OS. |

---

**End of Part 1 (Version 1.0)**
