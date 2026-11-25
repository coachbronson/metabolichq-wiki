---
title: Roadmap and backlog
summary: Where the backlog lives, priority rules, the current shape of open work, and the member/coach roadmap
updated: 2026-11-25
sources: ["#666", "#960", "#970", "#974", "#976", "#983", GitHub issues in mac-app, notes]
---

# Roadmap and backlog

- **Source of truth:** GitHub issues in `coachbronson/mac-app` labeled `backlog`. Pick work with the
  `mpt-backlog-picker` skill. Priority rules: [Engineering rules](../rules/engineering-rules.md#backlog-priorities).
- Lanes: `lane: features`, `lane: ops`, `lane: bugs`, `lane: rnd`. Other labels: `roadmap`, `needs-decision`,
  `client-request`, `priority: …`.

## Snapshot (2026-11-25)

97 open `backlog` issues: 69 features, 16 ops, 8 R&D, 3 bugs (#970, #686, #660; #678 has no lane); 13 on the roadmap
(#805, #710, #686, #681, #679, #678, #667, #660, #620, #575, #512, #410, #162); 26 need a decision. **1 critical**,
9 high, 34 medium, 53 low. No priority changes on open issues since Nov 24.
Closed since 2026-11-24: **#666** food diary ‹ Back after changing days could land on the wrong day (bug, medium,
roadmap; fixed by #981) · **#960** staging demo data billing states in Stripe test mode (done by #982, #985; see
[Architecture](architecture.md#google-cloud--firebase)) · **#976** two flaky payments journeys (not `backlog`; one
was a real Payments page bug, fixed by #980; the Stripe return timeout now records why if it repeats).
New: **#970** clients can't open a day with nothing programmed, so training on that day can't be logged; every day
should open and offer **Add workout** (bug, **critical**, reported by Bronson Nov 24) · **#983** move every scheduled
Claude job and reminder into the Google Cloud scheduler (high, ops; parts 1–3 merged Nov 24, see
[Architecture](architecture.md#deploys-backups-and-jobs)) · **#974** round robin call scheduling across a space's
coaches, like Calendly Round Robin (low, features, needs a decision; after #643). Still open outside the backlog:
#927 and #928 scheduled jobs (high, ops), #921 browser error reporting (deferred). #678 (fixed by #740) and #686
(fixed by #851) are still open.

**Critical:** #970 Add workout on any day in the client view (above).

**High priority:** #805 full functional audit after the code split (needs the owner's go-ahead; on the roadmap since
Nov 21; see [Acquisition readiness](acquisition-readiness.md#splitting-the-big-files-5)) · #575 release process after
beta · #512 security pending actions (lockout stage C around Nov 29, App Check) · #620 acquisition readiness (needs a
decision; §2, §4 and §5 nearly all done or accepted by Nov 22, #575 and #512 left; see
[Acquisition readiness](acquisition-readiness.md)) · #648 a clear Finances message for team coaches · #681
development and staging: PR previews, staging as a production mirror, a testing period before production
(build steps 1–4 done; the staging gate is on since Nov 24; step 5, the drift check, left; see [Versions](versions.md#after-beta-575-high)) · #983 scheduled Claude jobs and reminders in Google Cloud (parts 1–3 done Nov 24) · #410 client groups: coach-made groups with assigned coaches and group
managers · #710 Your brand: an app name separate from the business name · outside the backlog: #927/#928 scheduled jobs (above).

**Medium (selection):** #382 client add-ons · #634 import a returning client's history from a MetabolicHQ export
(needs a decision) · #355 recipe/meal and history import from other nutrition apps · #356 recipes · #162 wearable sync
· #570 free coach marketplace · #358 coach custom reports · #602 progress photos · #603 save check-ins partway ·
#478 rep-max table · #479 suggested weights · #332 coach onboarding workflows · #256 MCP server · #174 integrations ·
#381 HIPAA-ready (deferred, owner Nov 22) · #657 end-to-end coverage of every button,
field and display (stages 1–2 done) · #660 e2e: Stripe Checkout sometimes shows Link + hCaptcha instead of the card
form (bug; test-mode card-only and a Link-screen step went in, #687, #688).

**Recent, medium:** #742 MCP skill toolkit for coaches' own AI assistants, companion to #256 (needs a decision) ·
#746 coach-written waivers, with MetabolicHQ's release kept (needs a decision; see
[Partner program](partner-program.md#agreement-and-onboarding)). Earlier: #699 change a space's main coach: the
Platform tool after support checks (needs decisions).

**Low, Nov 17–18:** #686 owner's Spaces & coaches table wider than a 1366 px screen (bug; fixed by #851, still open).

**Low (recent):** #667 test emulators to firebase-tools 15 (blocked on a fixed 15.x) · #678 security rules
`clientAcctOn()` error noise (fixed by #740) · #679 MetHQ blog go-live run fails daily on "Save the go-live log" (posts still go
live; the log is never saved). Earlier: coach add-on marketplace #633 and the GLP-1 companion module #628 (#629–#632); Challenges #639; Fasting
tracker #640; AI progress troubleshooting #642; Leads CRM and discovery calls #643; call prep brief #637; own
equipment in a training location #641; weight-plateau signal #644; MPT resource pack
for Premium spaces #607.

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
