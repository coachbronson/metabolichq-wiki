---
title: Training (workouts, programs, swaps)
summary: Programs, workout logging, swaps and usual swaps, moving workouts, notifications, reports, exercise library
updated: 2026-11-28
sources: ["#1148", "#1174", "#1208", "#1212", "#1220", "#970", "#1009", "#1010", "#1017", "#1038", "#1052", "#930", notes, CHANGELOG, mac-app README, "#172", "#478", "#479", "#655", "#847", "#848", "#863", "#864"]
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

## Every day opens; Skip this workout

- Every day opens (#970, reported by him as critical Nov 24; PR #1009, Nov 25): a rest day is a card that opens, and a
  client can pick any day from today through "Show workouts for" (a coach any day). An empty day offers **+ Create
  custom workout**.
- **Skip this workout** (his addition): skips the whole programmed workout in one tap; the day says "You skipped …"
  with **Bring it back**, the week tags it Skipped, and the client's own workout for that day shows instead. The
  coach's views say "Skipped this day's programmed workout to do their own". Refused once anything that day is
  logged (#1009). A coach editing a one-on-one day keeps the client's own rows tagged as theirs, so a skip no
  longer hides them (#1010, PR #1148, Nov 27). (Previously a coach's edit dropped the tag.)
- The end-of-session wrap-up says the rating, effort and notes are shared with the coach (#1017, #1052).
- Habit streaks earn achievements under **Habits** (v8.87.0; see [My Daily Focus](my-daily-focus.md), #1174).
- Found by the audit (#805), open and low: Turn off swap → Turn off for good redraws Workouts over another page if
  you leave mid-change (#1208); a tap on the last week under Reports' "avg" label does nothing (#1212); the workout
  form's coach parts can no longer be reached in the app (#1220; programming moved to the portal).
- Requested (#1038, Nov 25): edit a session's start time and length when someone forgot to tap Start workout.

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
