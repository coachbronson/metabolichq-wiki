---
title: Versions and release history
summary: Version scheme, what each major version introduced, current version, release process after beta
updated: 2026-11-17
sources: [CHANGELOG, public/js/config.js, notes, "#575", "#320", "#645", "#649", "#653", "#654", "#655", "#681"]
---

# Versions and release history

- Shown as **BETA x.y.z** at the bottom of Help and in the portal sidebar (`APP_VERSION` in `public/js/config.js`).
- Major number = big feature area, middle = new features, last = fixes. Bump with every release.
- Current on 2026-11-17: **8.68.2** (8.68.0 workout menu on the Program calendar, #653; 8.68.1 Help review; 8.68.2
  card Skip/Undo fix, #655; CHANGELOG 2026-11-16; `APP_VERSION` in `public/js/config.js`). Changes on Nov 17 so far
  didn't bump the version.
- Full detail: `CHANGELOG.md` in mac-app (newest at the bottom of each day).

| Major | Area |
|---|---|
| 1.0 | Training (workouts, logging, timers, history, reports) |
| 2.0 | Coach portal |
| 3.0 | Biometrics |
| 4.0 | Nutrition (food diary, macros) |
| 5.0 | Coaching calls on video in the app (Daily) |
| 6.0 | Coaches write their own programming; MPT Programming becomes an add-on |
| 7.0 | Signals from combinations of a client's numbers |
| 8.0 | MPT Coach (AI coach) |

A major version gets a full end-to-end test before rollout.

## Timeline

- 2026-10-29: first in-app session form on the Google Sheet version.
- 2026-10-30: moved to Firebase; change log moved into the repo.
- 2026-11-14/15: 8.66.0 Masters Collective removed (#608); 8.66.1 account switch fix (#404).
- 2026-11-15: 8.66.2 Help review (#616); 8.66.3 "Provided by MetabolicHQ" instead of "Hosted by" (#618); 8.66.4
  badge images cache fix (#621); 8.67.0 Help in the coach portal (#645); 8.67.1 portal Help video (#649).
- 2026-11-16: 8.68.0 Program calendar workout menu: Approve, Approve all pending this week, Edit, Copy, Delete (#653);
  8.68.1 Help review (#654); 8.68.2 workout screen card Skip/Undo crash fixed (#655).
- 2026-10-31 → 11-14: desktop layout, backups, achievements, reports, check-ins, video library, then the 2.0–8.x
  releases above, plus spaces (multi-coach), memberships, partner program, Monitor.

## After beta (#575, high)

Continuous delivery, not scheduled releases: staging gate, feature switches, rollback, a user-facing release page
(#320) and release messaging/alerts for changes.

**Proposed: development and staging area** (#681, high, needs his decisions): a preview link on staging for every
PR; staging as a true mirror of production (same deploy workflow, test-mode services, a catch-all inbox, a drift
check); seeded demo data and no real client data on staging (an anonymized copy only with his OK each time); changes
wait on staging for a testing period or his sign-off before going to production, possibly split by risk. It would
change #575's staging gate, which today promotes once smoke tests pass. Open decisions are listed on #681.

## Related

[Architecture](architecture.md) · [Engineering rules](../rules/engineering-rules.md)
