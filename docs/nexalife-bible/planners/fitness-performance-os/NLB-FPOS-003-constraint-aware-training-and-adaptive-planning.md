# 📖 NEXALIFE BIBLE — Fitness & Performance Operating System (FPOS)

## Part 3 — Constraint-Aware Training, Equipment Adaptation & Plan Resilience

| Field | Value |
| --- | --- |
| Document ID | NLB-FPOS-003 |
| Series | Fitness & Performance Operating System (Volume 25) |
| Version | 1.0 |
| Status | Master Draft |
| Classification | Production Architecture Specification |
| Priority | ★★★★☆ |
| Supersedes | — |
| Last updated | 2026-08-05 |
| Parent | `NLB-FPOS-001`, `NLB-FPOS-002` |

---

## Scope note

Source material proposing a third parallel health volume contained training-side additions that belong to FPOS rather than HealthOS, per the boundary established in `NLB-HOS-003`. Its health-side additions went to `NLB-HOS-006`; the majority of it restated existing specifications and was not duplicated.

Parts 1 and 2 already cover workout generation, execution, logging, the exercise database with alternatives, adaptive workouts, progression, personal records, recovery, training readiness, sport modes, and the competition network. **This part adds one theme those parts left implicit: what happens when reality constrains the plan.**

---

## Why this part exists

A training plan fails far more often from friction than from being wrong — no barbell available, a hotel room instead of a gym, 25 minutes instead of 60, a missed Tuesday that quietly ends the week. `NLB-FPOS-001` established that workouts adapt; this part specifies the mechanisms, because "the plan adapts" is only credible if the adaptations are enumerated.

---

## Capacity Model

Plans are generated against the user's **actual** available time, stated up front:

```
AVAILABLE TIME
Weekdays   45 min/day
Weekend    90 min/day
```

A plan that doesn't fit the user's real week is not a plan. This makes explicit what `NLB-FPOS-001`'s onboarding collects, and it is the same discipline `NLB-HOS-005`'s One Life Planner applies to wellness generally.

---

## Equipment-Aware Planning

**Home Gym Mode** records available equipment:

```
Dumbbells ✓   Bench ✓   Resistance bands ✓   Pull-up bar ✓   Barbell ✗
```

Plans generate against that inventory automatically, rather than producing sessions the user cannot perform. **Exercise Substitution** (established in `NLB-FPOS-001`) draws from this inventory, always stating its reason and awaiting approval.

**Travel Workout Generator** takes a constraint set — *hotel room, 20 minutes, no equipment* — and produces a routine within it. Travel is the single most common cause of a broken training streak, and generating for it is more useful than logging its absence.

**Outdoor Fitness Mode** covers walking routes, running, cycling, and outdoor activity, with **location access requiring explicit permission** (`NLB-10`).

**Weather awareness**, where data is available, offers alternatives — indoor session, move the time, or continue anyway — with **the user choosing**, and forecasts distinguished from certainty per `NLB-BLOS-002`.

---

## Plan Resilience

**Minimum Viable Workout** — *"You only have 15 minutes"* produces a shortened version of the planned session rather than abandoning it. Preserving the habit matters more than preserving the session.

**Flexible Plan Engine** — a missed session offers explicit options rather than silent failure:

```
MISSED: Tuesday
  → Move to Wednesday
  → Shorten Thursday
  → Skip and continue
  → Replace with mobility
```

"Skip and continue" is a first-class option. A plan that treats every miss as debt to be repaid becomes unsustainable faster than one that lets a week simply be lighter.

**Recovery-Aware Planning** considers self-reported fatigue, soreness, sleep, and energy before suggesting intensity — **never presented as a medical assessment**, consistent with `NLB-FPOS-001`'s Training Readiness phrasing.

**Deload planning** provides configurable lower-volume periods for users following structured plans.

---

## Training Analytics

**Exercise Performance Analytics** track a lift's progression (weight, reps, sessions, best set) over time.

**Muscle Group Balance** visualizes training distribution across chest, back, legs, shoulders, and arms. **This is a training-distribution visualization, not a medical or postural assessment** — it shows what the user has trained, not what they should.

**Long-Term Roadmap** phases a training year (consistency → volume → strength → performance → evaluation), and **Training Journal Intelligence** summarizes trajectory (*"Your training volume has increased steadily for six weeks," "Your recent sessions have become shorter"*) as observation rather than verdict.

---

## Streaks

**Streak Protection.** A missed day produces *"Restart today?"* — never *"Your streak ended"* framed as failure. Streaks are optional and disableable, consistent with `NLB-14`'s Progression System and the no-shame principle shared across the Study Planner, HealthOS, BLOS, and FWOS.

---

## Revision History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | 2026-08-05 | Added the capacity model, equipment-aware and home-gym planning, travel workout generation, outdoor and weather-aware training, the flexible plan engine with minimum viable workouts, muscle-group balance visualization, and streak protection — the constraint-handling layer Parts 1–2 left implicit. |

---

**End of Part 3 (Version 1.0)**
