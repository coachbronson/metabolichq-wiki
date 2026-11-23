---
title: Training (workouts, programs, swaps)
summary: Programs, workout logging, swaps and usual swaps, moving workouts, notifications, reports, exercise library
updated: 2026-11-23
sources: ["#930", notes, CHANGELOG, mac-app README, "#172", "#478", "#479", "#655", "#847", "#848", "#863", "#864"]
---

# Training

## Programs

- **Group program**: the "Metabolic Performance Training" program, shared at platform level. When it changes, every
  space's group clients get a **system message** ("Program updates"), not a Coach Bronson message.
- **One-on-one programming**: private to the client (and their coach). Partner coaches write their own group and
  one-on-one programming (v6.0); MPT programs come with the Premium add-on.
- **Template programs** a client starts on a date they pick (Profile → My program, start up to 30 days ahead, Day 1 on
  that date): **MPT Body Weight Training** (from his UKF bodyweight sample) and **Machine Masters** (his machine-only
  handout; no videos yet, the handout's pictures come later). At the end of a program, ask if they want something
  more challenging.
- Every workout has scaling and equipment options, so no minimum equipment or experience level is promised.
- Program loading and import rules: [Program library import](program-library-import.md).
- Planned (backlog, medium, Nov 20): assign a program to an individual, a group or everyone, at creation or after
  (#863, with client groups #410); save a workout to an existing or new program, and duplicate a program (#864).

## Logging and the workout screen

- Cards by type (Warm-up, Strength, Metcon, Accessory, Cool-down), timers (For Time, AMRAP, EMOM, Tabata), session
  timer with a 2.5-hour limit, weight carry-forward, per-side / alternating reps, units from Profile, PR references.
- Clients can build their own workouts (visible only to them).
- A card's **Skip** and **Undo** (e.g. the whole Warm-up) crashed with "reading 'original'" and didn't save until
  8.68.2 fixed it (#655). An end-to-end journey now uses every button, field and display on the workout screen
  (#657 stage 2).
- A workout day that loads slowly no longer draws over a page opened meanwhile, and of two days opened quickly
  the newer one shows; only the newest load draws, and only while Workouts is open. It was the intermittent
  "Self-start program" end-to-end failure on Nov 20 (#847, #848, CHANGELOG 2026-11-20).
- Desktop layout for 1024 px+ with mouse/trackpad; phones and tablets get the phone layout.

## Swaps

- **Swap** or **Skip** an exercise per day; the programmed workout never changes.
- **Usual swaps (#172)**: an "Always swap this" checkbox that applies every time that exercise is programmed, at any
  location, plus a one-tap way to do the programmed exercise for one day. Turning one off asks permanent or temporary
  (temporary = that day). MPT Coach swaps also offer "Always swap this". Training locations in Profile only guide
  suggestions. Location-scoped swaps only if usage shows the need.
- Guided swaps recommended from each client's preferences are complete. Swap standards: see
  [Programming conventions](../rules/programming-conventions.md).

## Moving a workout

Clients can move a day's workout up to 7 days back or ahead (every space, no setting). Onto a day that already has a
workout: client chooses to keep or skip the existing one. Coaches moving workouts for clients is out.

## Notifications

"Send update" button with a running count of unsent workouts, plus a daily digest at 7:03 AM Eastern
(the scheduled function `morningDigest` since Nov 22; GitHub had been sending it in the afternoon, #927, #930). Group program → everyone in
the group; custom work → only that client.

## Reports, history, achievements

- Client Reports: four tabs — **Progress** (with consistency), **Training** (Strength | Metcons switch, 4/12/All
  weeks), **Readiness**, **Nutrition**.
- History tables for strength and metcons; achievements.
- Backlog: estimated 1RM/3RM/5RM table (#478), suggested weights (#479), PDF download of a day (#413).

## Exercise library

Built-in exercise list with abbreviations and fuzzy matching; Coach Bronson's master video library (every space);
YouTube playlist sync; video tags can be audited and locked (skill `mpt-video-tags`).

## Related

[MPT Coach](mpt-coach.md) · [Biometrics and signals](biometrics-and-signals.md) ·
[Programming conventions](../rules/programming-conventions.md)
