---
title: Versions and release history
summary: Version scheme, what each major version introduced, current version, release process after beta
updated: 2026-11-27
sources: ["#1081", "#1085", "#1086", "#1093", "#1107", "#1110", "#1112", "#410", "#575", "#603", "#681", "#1005", "#1017", "#1020", "#1022", "#1024", "#1025", "#1026", "#1035", "#1052", "#1073", "#1076", "#993", "#996", "#999", "#1004", "#1068", "#1069", CHANGELOG 2026-11-25, CHANGELOG 2026-11-26, "#666", "#681", "#960", "#967", "#971", "#973", "#975", "#976", "#977", "#978", "#979", "#983", CHANGELOG 2026-11-24, "#951", "#956", "#960", "#962", "#964", "#966", "#967", CHANGELOG 2026-11-23, "#919", "#920", "#922", "#925", "#928", "#939", "#946", CHANGELOG 2026-11-22, CHANGELOG, public/js/config.js, notes, "#575", "#320", "#645", "#649", "#653", "#654", "#655", "#681", "#700", "#701", "#722", "#620", #751–#755, #806, CHANGELOG 2026-11-20, CHANGELOG 2026-11-21, "#815–#849", "#865", "#872", "#874", "#878", "#880", "#883", "#891", "#893", "#897", "#902", "#904", "#905"]
---

# Versions and release history

- Shown as **BETA x.y.z** at the bottom of Help and in the portal sidebar (`APP_VERSION` in `public/js/config.js`).
- Major number = big feature area, middle = new features, last = fixes. Bump with every release.
- Current on main, 2026-11-27: **8.83.1** (Help review Nov 26, #1085; `APP_VERSION` in `public/js/config.js`).
  Merged is not live: medium- and high-risk changes wait 24 hours on staging, so release notes carry the day each is
  expected live (`public/js/releasenotes.js`). (Previously 8.77.0 on Nov 26; 8.71.1 from Nov 23, #951.)
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
- 2026-11-24: **the staging gate is on** (#681 build step 4, #971–#979): merges deploy to staging first, with smoke
  tests, Promote and the Releases page in the Monitor and the portal; the Staging inbox fix (#967); food diary ‹ Back
  keeps the day (#666, #981); Payments page shows the newest load (#976, #980); staging demo clients with real Stripe
  test-mode billing (#960, #982, #985); scheduled Claude jobs and the owner's reminders run from Google Cloud (#983,
  #984, #986, #989). No version bump.
- 2026-11-25: **#575 and #681 closed.** The drift check (#993, #994, #996, #1006), the post-deploy watch and Roll
  back (#999, #1004), Releases updating by itself (#1000–#1002, #1070, #1071), feature switches (#1064–#1066) and
  release messaging (#1036, #1040, #1042, #1043, #1051). Check-ins become a self check-in: 8.72.0 private notes
  (#1020), 8.73.0 save partway and Skip (#1025), 8.74.0 check-in reminders (#1026), 8.74.1 the wrap-up sheet says
  it's shared with the coach (#1052). 8.75.0 client groups stage A1 (#1035); groups A2 through the server (#1059).
  Also every day opens and Skip this workout (#970, #1009), phase angle and visceral fat (#856), drip sections in
  Resources (#860), Name in the app and who can change the brand (#710, #1033).
- 2026-11-26: 8.76.0 groups A3, a group's coaches are its clients' coaches (#1073); 8.77.0 groups A4, coach views by
  group (#1076); Files back buttons (#1060, #1045, #1062). 8.78.0 groups B1, Resources shared with a group (#1081);
  8.79.0 B2, message a group (#1086); 8.80.0 one custom check-in per space (#157, #1093); 8.81.0 B4, group calls
  (#1107); 8.82.0 C1, a group's own Community feed (#1110); 8.83.0 C2, Cohort reports by group (#1112); 8.83.1 Help
  review (#1085). **#410 client groups closed.** Also MetabolicHQ social media (#1101–#1104, #1114–#1116, #1120),
  blog Approve on a draft behind main (#1117, #1123), the Releases end-to-end banner (#1084, #1103), the demo video
  out of the repo (#1105, #1109), and more portal journeys for #657 (#1078, #1083, #1087, #1088, #1096, #1118).
- 2026-10-31 → 11-14: desktop layout, backups, achievements, reports, check-ins, video library, then the 2.0–8.x
  releases above, plus spaces (multi-coach), memberships, partner program, Monitor.

## After beta (#575, done Nov 25)

Continuous delivery, not scheduled releases (#575, closed Nov 25): the staging gate (#681), the post-deploy watch
and Roll back, feature switches (#1022), a public release page (#320) and release messaging (#1024). Left in #1005:
watch the first real watches on production, see the alert email arrive, do one Roll back drill, and review the
50-request floor after a week (#575 "How this was resolved").

**Development and staging area** (#681, closed Nov 25): a preview link on staging for every PR; staging as a true
mirror of production; seeded demo data reset weekly; the staging gate; the nightly drift check. His decisions
(Nov 22, #681):
- Low-risk changes go to production as soon as the staging smoke tests pass; medium- and high-risk changes wait on
  staging **24 hours**, then go on their own unless he taps **Promote** in the Monitor sooner.
- Urgent incident fixes skip the 24 hours once smoke tests pass (medium/high still need his OK).
- A waiting medium/high change holds back what merged after it.
- No partner coaches on staging or preview links yet; revisit when early-access coaches are chosen (#575).
- Staging data resets weekly by a scheduled Cloud Function, plus a reset link (portal Maintenance page).
- Full journeys against live staging, instead of the smoke tests, get their own issue when wanted (#681).

**How it works now (gate on since about 5:45 PM, Nov 24; #681, mac-app CLAUDE.md, #979):** a merge to main
deploys to staging, not production. The staging smoke tests run there (11 checks: app, portal and site load on phone
and desktop, a sign-in link email reaches the Staging inbox, a sign-in works, food search and MPT Coach answer;
`staging-smoke.yml`, #971). A scheduled function, `releasePromote`, checks every 15 minutes and starts **Promote**
(`promote.yml`), which deploys one exact commit that passed on staging (#971, #975):
- **Low risk:** within 15 minutes of its staging run passing. **Medium and high:** 24 hours after that, each on its
  own clock. The risk is the PR's Blast radius "Risk:" line; a PR without one counts as high (#975, #979).
- Changes go out **in merge order**; a low-risk change behind a waiting one waits with it. **Hold** stops a change and
  everything after it. A promote that failed is never retried on its own; the owner gets a security alert and a
  **Try again** on its card (#975, #988).
- "Merged" no longer means "live": status updates say "merged; on staging". An urgent fix is labeled `incident` and
  the owner promotes it once the smoke tests pass. Undo: delete the repository variable `RELEASE_GATE` (mac-app
  CLAUDE.md).

**The Releases page** (MetHQ Monitor on the phone, #977; portal Platform → Releases on a desktop, #978): stages PR
open, On staging, Promoting, Being watched, Live; **Promote now**, **Promote all on staging**, Hold, Release the hold,
Re-run smoke tests (#988).
- Staging cards say when each change goes live by itself ("Live 12:15 AM Thu", "In line · live …", "On hold",
  "Needs you"), and the Next line names the change it waits for (#995).
- **Live** lists everything that went live in the last 24 hours, newest first, each with the changes it took
  (owner, Nov 25; #1068, #1069).
- **It updates by itself:** every PR and workflow status change is posted to production's `releaseSignal` by the
  `release-signal.yml` workflow, signed in with the run's GitHub OIDC token (no stored secret), and the open page
  checks every 20 seconds and reloads when something moved; the scheduled watch and promote signal too (owner, Nov 25:
  "I have to keep hitting refresh"; #1000–#1002, #1070, #1071). The view loads in a few seconds (#1029, #1030).
- **Drift check:** `drift-check.yml` compares staging with production every night at 3:07 AM (started from Google
  Cloud, `driftCheckStart`): Firestore indexes and rules, Storage rules, functions and their settings, scheduled jobs
  and sign-in settings. Read only; a part it couldn't read never counts as a match. The one expected difference:
  text-message two-step codes are on production only (owner, Nov 23). Its status sits next to Refresh, with **Run it
  again** (#993, #994, #996, #1006, #1069).
- **Being watched** (owner's decisions, Nov 25; #999, #1004): for an hour after each deploy to production,
  `releaseWatch` (every 5 minutes) compares requests, server errors and the slowest 5% with the same length of time
  before. "Worse" needs 50 or more requests: server errors at least double, at least 1 point higher and 5 or more; or
  the slowest 5% at least 50% and 0.5 s slower. The first time it looks worse, the owner gets one email and the
  scheduled promote pauses. Its ⋯ menu has **Roll back** (puts back the previous version through Promote, holds the
  changes that came off, never undoes saved data; asks first) and **It's fine**. Nothing rolls back on its own.
- **Feature switches** section (#1066): see below.

**Feature switches** (#1022, closed Nov 25; merged with his OK, medium risk). His spec (Nov 25): only for feature
issues; a feature is on at deploy unless he uses its switch; just a turn-on date and an instant off; no staged
rollout, because MPT is a working coach space, not a test space (this replaced #575's MPT-first rollout).
- The switches are listed in `functions/features.json` (none yet; each feature PR that wants one adds it). Screens
  check `API.featureOn(key)`.
- In Releases, each switch's ⋯ menu: **Set a date** (Eastern, 9:00 AM by default, his choice), **Turn off now**,
  **Turn on now**; plus a turn-on calendar.
- Coaches get notices by email 7 days, 3 days and the day of a turn-on date (`featureWork`, daily 8:23 AM), Coach
  Home shows a **Coming up** card for the next 7 days, and the Monday digest has a Turning on soon section.
- A switched feature's release note stays hidden while it's off, and is dated the day it turns on.
- 30 days after a feature turned on, `featureWork` opens a backlog issue to take its switch out (his choice).
- Open: #1079, the Monitor's live refresh resets a half-filled Set a date form.

**Release messaging** (#1024, closed Nov 25; his decisions Nov 25):
- **What's new card** on the app's Home (clients) and the portal's Coach Home (coaches): new features (release notes
  of kind New) since the person last had the card, once. No "notable" flag: every feature counts as a change to how
  coaches work; Improved and Fixed go only to the What's new page, /releases and the digest (#1036).
- **Monday coach digest**, 8:17 AM Eastern, to every coach (main and team, every space, MPT too): last week's notes,
  For you and For your clients. A **Weekly MetabolicHQ updates** switch in Settings → Notifications turns it off
  (#1040). The first real one goes out Mon Nov 30.
- **Service status**: he sets Operational / Degraded / Incident in the MetHQ Monitor, for every space or the ones he
  picks. A banner shows in the app and the portal, and on the Trust page for every-space status (which keeps the
  Better Stack link). An incident emails the affected spaces' coaches when it starts and when it's resolved
  (#1042, #1043).
- **Major version announcement**: from 9.0, the Monitor's Content page has a draft email listing the new version's
  features; he edits it, then sends it to coaches (clients optional) or skips it (#1051).

## Related

[Architecture](architecture.md) · [Engineering rules](../rules/engineering-rules.md)
