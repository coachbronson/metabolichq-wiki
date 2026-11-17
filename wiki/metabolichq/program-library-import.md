---
title: Program library import (2017–2018 programming)
summary: How his old programming library is converted into MPT program days, review-before-publish, import rules
updated: 2026-11-17
sources: [notes, skill mpt-program-import, CHANGELOG, "#653"]
---

# Program library import

## Source

His 2017–2018 programming library (Google Drive: Workout App → Programming folder). He works with Claude to import and
normalize it (previously ran imports himself). Skill: **`mpt-program-import`**.

## Main program rules

- Schedule starts **Sun Nov 8, 2026** with a rest day, going into the main group program.
- Partner workouts → single-person; partner work halved.
- Multi-exercise strength cells split into separate rows.
- Scaling levels (L1–L3/Rx+) removed (scaling lives in the app).
- He names each day's workout by hand.
- Notes referencing upcoming workouts are removed.
- Entry conventions (bullets, No Score warm-ups, bilateral defaults, barbell complexes): see
  [Programming conventions](../rules/programming-conventions.md).

## Review before publish

- The remaining 53 weeks are preloaded as **pending review** in the workout builder; published only after he
  approves (first batch: up to week 8). He can approve one at a time or a whole week from the Program calendar's
  workout menu (v8.68.0, #653; see [Coach portal](coach-portal.md)).
- Changes he makes to pending workouts before approving are checked so the import rules get updated.
- Weekly email listing anything not yet approved (workouts plus blogs, social posts, newsletters).

## Other programs

**MPT Body Weight Training** and **Machine Masters** are imported as templates, each under its own rule set (not the
main program's). Ideas under consideration: a workout-instructions field at the start of each day, hyperlinks in the
exercise field, a reusable workout-sheet template (#267).

## Related

[Training](training.md)
