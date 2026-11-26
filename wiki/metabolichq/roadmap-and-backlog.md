---
title: Roadmap and backlog
summary: Where the backlog lives, priority rules, the current shape of open work, and the member/coach roadmap
updated: 2026-11-26
sources: ["#410", "#575", "#603", "#681", "#970", "#1005", "#1007", "#1010", "#1016", "#1038", "#1079", "#983", GitHub issues in mac-app, notes]
---

# Roadmap and backlog

- **Source of truth:** GitHub issues in `coachbronson/mac-app` labeled `backlog`. Pick work with the
  `mpt-backlog-picker` skill. Priority rules: [Engineering rules](../rules/engineering-rules.md#backlog-priorities).
- Lanes: `lane: features`, `lane: ops`, `lane: bugs`, `lane: rnd`. Other labels: `roadmap`, `needs-decision`,
  `client-request`, `priority: …`.

## Snapshot (2026-11-26)

89 open `backlog` issues: 65 features, 15 ops, 8 R&D (#678 has no lane; no open `lane: bugs`); 16 on the roadmap
(#983, #864, #863, #861, #857, #805, #699, #679, #678, #667, #620, #602, #570, #512, #410, #162); 25 need a decision.
No critical, 5 high, 31 medium, 52 low.
**Added to the roadmap Nov 25:** #983, #864, #863, #861, #857, #699, #602, #570.
**Closed since 2026-11-25** (each "How this was resolved" read):
- **#970** (critical) every day opens, plus Skip this workout (#1009; see [Training](training.md)).
- **#575** release process after beta and **#681** development and staging: done, see
  [Versions](versions.md#after-beta-575-done-nov-25); follow-up #1005.
- **#1022** feature switches and **#1024** release messaging (both opened and closed Nov 25).
- **#603** check-ins saved partway with reminders, and **#1017** reflection notes (they stay shared); see
  [Biometrics and signals](biometrics-and-signals.md#check-ins).
- **#710** Name in the app and **#1033** who can change the brand; **#648** and **#1019** Finances for coaches who
  aren't the main coach; see [Coach portal](coach-portal.md#your-brand).
- **#856** phase angle and visceral fat; **#860** drip sections in Resources; **#1045**, **#1060** Files back buttons.
- **#660** Stripe Link screen in e2e (fixed by #687, #688; 297 passes since); **#686** closed as a duplicate of #850.
- Test-only: #1039, #1049, #1053.
**New:** #1038 edit a session's start time and length when Start workout wasn't tapped (features, no priority yet) ·
#1007 the coverage index over-counts a shared `data-goto` click (medium, ops) · not `backlog` yet: #1005 release watch
check and Roll back drill, #1010 a coach's edit drops a client's own-row tag (#970 follow-up), #1016 signals for phase
angle and visceral fat, #1079 Releases' live refresh resets a half-filled Set a date.

**In progress:** #410 client groups: stages A1–A4 done Nov 25–26 (v8.75.0–8.77.0); next is B, groups as an audience,
Resources first; the production backfill is due Nov 27 (see [Spaces and roles](spaces-and-roles.md#client-groups-410)).

**High priority:** #983 scheduled Claude jobs and reminders in Google Cloud (roadmap) · #805 full functional audit
after the code split (needs the owner's go-ahead; see
[Acquisition readiness](acquisition-readiness.md#splitting-the-big-files-5)) · #512 security pending actions
(lockout stage C around Nov 29, App Check) · #620 acquisition readiness (needs a decision; #575 done, #512 left) ·
#410 client groups (above). Outside the backlog: #927/#928 scheduled jobs.

**Medium (selection):** roadmap: #864 save a workout to a program or duplicate a program · #863 assign a program to
one client, a group or everyone · #861 delegated admin roles · #857 SOAP notes for practitioners · #699 change a
space's main coach (needs decisions) · #602 progress photos (needs a decision) · #570 free coach marketplace · #162
wearable sync. Others: #382 client add-ons · #634 import a returning client's history (needs a decision) · #355
recipe/meal and history import · #356 recipes · #358 coach custom reports · #478 rep-max table · #479 suggested
weights · #491 timed release from enrollment or the previous section · #332 coach onboarding workflows · #256 MCP
server · #742 MCP skill toolkit (needs a decision) · #746 coach-written waivers (needs a decision; see
[Partner program](partner-program.md#agreement-and-onboarding)) · #174 integrations · #381 HIPAA-ready (deferred,
owner Nov 22) · #657 end-to-end coverage of every button, field and display (known gaps down to 810, Nov 26) ·
#877 e2e for authenticator two-step on staging.

**Low (recent):** #667 test emulators to firebase-tools 15 (blocked on a fixed 15.x) · #678 security rules
`clientAcctOn()` error noise (fixed by #740, still open) · #679 MetHQ blog go-live run fails daily on "Save the
go-live log" (posts still go live) · #974 round robin call scheduling (needs a decision). Earlier: coach add-on
marketplace #633 and the GLP-1 companion module #628 (#629–#632); Challenges #639; Fasting tracker #640; AI progress
troubleshooting #642; Leads CRM and discovery calls #643; call prep brief #637; own equipment in a training location
#641; weight-plateau signal #644; MPT resource pack for Premium spaces #607.

The nightly update refreshes this snapshot; GitHub is always the live list.

## Roadmap shape (public)

- **Members:** remembered/usual swaps, health-app and wearable integrations, deeper nutrition and coaching.
- **Coach partners:** own branding, separate client space, coach dashboard (done); business metrics like
  retention/churn; automation connections (Zapier/Make/webhooks); cohort trend analysis with advanced AI
  ("Coming soon"). A "cohort" = a coach's whole client list; cohort reporting is for coaches (#158).
- Future ideas he named: AI-augmented holistic client analytics; client video self-recording with coach feedback
  (#155); alerts from metric combinations for coaches and clients (good and bad trends).

## Related

[Versions](versions.md) · [Coach portal](coach-portal.md)
