---
title: Roadmap and backlog
summary: Where the backlog lives, priority rules, the current shape of open work, and the member/coach roadmap
updated: 2026-11-27
sources: ["#157", "#512", "#983", "#1089", "#1090", "#1095", "#1097", "#1099", "#1100", "#1111", "#1113", "#1119", "#1122", "#410", "#575", "#603", "#681", "#970", "#1005", "#1007", "#1010", "#1016", "#1038", "#1079", "#983", GitHub issues in mac-app, notes]
---

# Roadmap and backlog

- **Source of truth:** GitHub issues in `coachbronson/mac-app` labeled `backlog`. Pick work with the
  `mpt-backlog-picker` skill. Priority rules: [Engineering rules](../rules/engineering-rules.md#backlog-priorities).
- Lanes: `lane: features`, `lane: ops`, `lane: bugs`, `lane: rnd`. Other labels: `roadmap`, `needs-decision`,
  `client-request`, `priority: …`.

## Snapshot (2026-11-27)

89 open `backlog` issues: 64 features, 16 ops, 8 R&D (#678 has no lane; no open `lane: bugs`); 13 on the roadmap
(#864, #863, #861, #857, #805, #699, #679, #678, #667, #620, #602, #570, #162); 26 need a decision.
No critical, 2 high, 32 medium, 53 low; #1038 and #1100 have no priority yet.
**Closed since 2026-11-26** (each "How this was resolved" read):
- **#410** client groups (all stages settled; see [Spaces and roles](spaces-and-roles.md#client-groups-410)) and
  **#157** one custom check-in per space (see [Biometrics and signals](biometrics-and-signals.md#check-ins)).
- **#983** Claude jobs and reminders all on MetabolicHQ's Google Cloud scheduler (see
  [Architecture](architecture.md)).
- **#512** security pending actions: done parts closed, lockout and App Check deferred (see
  [Security](security.md)).
- **#1079** Monitor Releases date form (fixed, #1080); **#1089** a test-only sign-in race; **#1097** closed as not
  needed (the Social page is back).
**New:** #1111 lockout and Unlock, deferred (low, ops, security) · #1113 App Check with Turnstile, deferred (low, ops,
security) · #1090 split the 36-journey portal end-to-end area (medium, ops) · #1100 exportable coach reports for
corporate wellness and medical/rehab providers (features, needs a decision; his request, Nov 26) · not `backlog`
yet: #1095 group call recording and AI notes, #1099 a sponsor summary of group reports (high risk), #1119 the Custom
check-in journey fails across midnight UTC (test-only), #1122 the blog go-live deploys main's site past the staging
gate (fixes for him to pick).

**High priority:** #805 full functional audit after the code split (needs the owner's go-ahead; see
[Acquisition readiness](acquisition-readiness.md#splitting-the-big-files-5)) · #620 acquisition readiness (needs a
decision; #575 and #512 done). (Previously also #983, #512 and #410, all closed Nov 26.) Outside the backlog:
#927/#928 scheduled jobs.

**Medium (selection):** roadmap: #864 save a workout to a program or duplicate a program · #863 assign a program to
one client, a group or everyone · #861 delegated admin roles · #857 SOAP notes for practitioners · #699 change a
space's main coach (needs decisions) · #602 progress photos (needs a decision) · #570 free coach marketplace · #162
wearable sync. Others: #382 client add-ons · #634 import a returning client's history (needs a decision) · #355
recipe/meal and history import · #356 recipes · #358 coach custom reports · #478 rep-max table · #479 suggested
weights · #491 timed release from enrollment or the previous section · #332 coach onboarding workflows · #256 MCP
server · #742 MCP skill toolkit (needs a decision) · #746 coach-written waivers (needs a decision; see
[Partner program](partner-program.md#agreement-and-onboarding)) · #174 integrations · #381 HIPAA-ready (deferred,
owner Nov 22) · #657 end-to-end coverage of every button, field and display (known gaps down to 605, `ops/ui-gaps.json` Nov 27) ·
#877 e2e for authenticator two-step on staging.

**Low (recent):** #667 test emulators to firebase-tools 15 (blocked on a fixed 15.x) · #678 security rules
`clientAcctOn()` error noise (fixed by #740, still open) · #679 MetHQ blog go-live run fails daily on "Save the
go-live log" (posts still go live; fix in PR #1121) · #974 round robin call scheduling (needs a decision). Earlier: coach add-on
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
