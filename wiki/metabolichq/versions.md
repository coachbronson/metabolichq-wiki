---
title: Versions and release history
summary: Version scheme, what each major version introduced, current version, release process after beta
updated: 2026-11-24
sources: ["#951", "#956", "#960", "#962", "#964", "#966", "#967", CHANGELOG 2026-11-23, "#919", "#920", "#922", "#925", "#928", "#939", "#946", CHANGELOG 2026-11-22, CHANGELOG, public/js/config.js, notes, "#575", "#320", "#645", "#649", "#653", "#654", "#655", "#681", "#700", "#701", "#722", "#620", #751–#755, #806, CHANGELOG 2026-11-20, CHANGELOG 2026-11-21, "#815–#849", "#865", "#872", "#874", "#878", "#880", "#883", "#891", "#893", "#897", "#902", "#904", "#905"]
---

# Versions and release history

- Shown as **BETA x.y.z** at the bottom of Help and in the portal sidebar (`APP_VERSION` in `public/js/config.js`).
- Major number = big feature area, middle = new features, last = fixes. Bump with every release.
- Current on 2026-11-24: **8.71.1** (Help review Nov 23: a What's new walkthrough in Help, #951; CHANGELOG 2026-11-23;
  `APP_VERSION` in `public/js/config.js`). (Previously 8.71.0 from Nov 22, #920.)
- **Release notes** for people who use it: `public/js/releasenotes.js` (104 notes backfilled from 5.0), shown on
  **What's new** in the app (tap the version at the bottom of Help), in the coach portal (Help → What's new, or the
  version under the menu) and publicly at **metabolichq.app/releases**. Clients see their own notes; coaches see
  clients' and coaches'; internal notes are never shown. Every visible change adds one (#320, #919, #920, #922; see
  [Engineering rules](../rules/engineering-rules.md#release-notes)).
- Full detail: mac-app's change log, one file per entry under `changelog/` since Nov 22 (`CHANGELOG.md` is the
  index; #939).

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
- 2026-11-17: 8.69.0 coaches change their business name on Your brand (#700); 8.70.0 Change the main coach card that
  opens a support request (#701). Same day: Content-Security-Policy enforced on metabolichq.app and the portal
  (#693, #697), then the app on Nov 18 (#708).
- 2026-11-18: 8.70.1 Help review (#722). Same day: `functions/index.js` split into area files with no behaviour
  change (#724–#739; see [Acquisition readiness](acquisition-readiness.md)).
- 2026-11-19: server split finished (#762–#779); app split started (#780, #809); the Nov 19 nightly review's fixes for
  payments, partner sign-up, memberships, privacy and calls (#751–#755, #787–#804); a page tapped right after a
  refresh stays open (#806, #811, #814). No version bump.
- 2026-11-20: the app split finished (3.3–3.13, #815–#846; `start.js`, #849); the Nov 20 nightly review's 13 fixes
  (#816, #817–#830); Trust page at metabolichq.app/trust and Help links to it (#865, #872); deploys one at a time
  (#833); late Workouts load fixed (#848). No version bump.
- 2026-11-21: the portal split, start to finish (#874–#903, tidy-up #905); report names escaped (#880); server calls
  matched to their triggers and nearly all tested (#785, #873, #884–#892); the unused-function tripwire `apiUsage`
  (#893); the code map (#883); the coach app's Clients list no longer goes blank for a client with no name or email
  (#891); the e2e runner's emulator-memory and midnight-UTC fixes (#897, #904). No version bump.
- 2026-11-22: 8.71.0 What's new and release notes (#919, #920, #922); status page linked from Trust and Help (#917,
  #918); Privacy Policy and Terms moved to metabolichq.app and worded for MetabolicHQ (#925); type checking with no
  type errors (#909–#913); every scheduled job moved to Google Cloud (#928, #930–#938); CoachRx on the Compare page
  (#908); change log one file per entry (#939).
- 2026-11-23: one deploy workflow for production and staging (#946); 8.71.1 Help review (#951); staging as a
  production mirror, demo data reset weekly, and a staging preview of each PR (#681, #950–#965); the owner's first
  sign-in without two-step shows the set-up screen (#964, #966).
- 2026-10-31 → 11-14: desktop layout, backups, achievements, reports, check-ins, video library, then the 2.0–8.x
  releases above, plus spaces (multi-coach), memberships, partner program, Monitor.

## After beta (#575, high)

Continuous delivery, not scheduled releases: staging gate, feature switches, rollback, a user-facing release page
(done Nov 22, #320) and release messaging/alerts for changes. A Monitor review step for release notes comes with
#575 (mac-app CLAUDE.md).

**Development and staging area** (#681, high, roadmap): a preview link on staging for every PR; staging as a true
mirror of production (same deploy workflow, test-mode services, a catch-all inbox, a drift check); seeded demo data
and no real client data on staging (an anonymized copy only with his OK each time). His decisions (Nov 22, #681):
- Low-risk changes go to production as soon as the staging smoke tests pass; medium- and high-risk changes wait on
  staging **24 hours**, then go on their own unless he taps **Promote** in the Monitor sooner.
- Urgent incident fixes skip the 24 hours once smoke tests pass (medium/high still need his OK).
- Waiting changes are promoted together (the latest main); a waiting medium/high change holds back what merged
  after it.
- No partner coaches on staging or preview links yet; revisit when early-access coaches are chosen (#575).
- Staging data resets weekly by a scheduled Cloud Function, plus a reset button in the Monitor.

Build steps 1–3 done Nov 23 (#681 comments): staging as a mirror (#946, #950, #952–#955), seeded demo data reset
weekly and on demand (#956–#959, #963; the reset link is on the portal's Maintenance page, not the Monitor: staging
can't start GitHub workflows itself), and a preview of each PR (#962). The owner checked on staging: MPT Coach's real
answers, barcode and food lookups (#965), and owner sign-in with two-step (#966); the Staging inbox showed "No emails
yet" and its fix is #967 (open). Left: step 4, the testing period, Promote and the Releases view (the gate itself);
step 5, the drift check (the Live config report, #943, is its start); #960, billing edge cases in the demo data
(Stripe test mode; needs a decision).

## Related

[Architecture](architecture.md) · [Engineering rules](../rules/engineering-rules.md)
