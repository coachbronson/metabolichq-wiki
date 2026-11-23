---
title: Roadmap and backlog
summary: Where the backlog lives, priority rules, the current shape of open work, and the member/coach roadmap
updated: 2026-11-23
sources: [GitHub issues in mac-app, notes]
---

# Roadmap and backlog

- **Source of truth:** GitHub issues in `coachbronson/mac-app` labeled `backlog`. Pick work with the
  `mpt-backlog-picker` skill. Priority rules: [Engineering rules](../rules/engineering-rules.md#backlog-priorities).
- Lanes: `lane: features`, `lane: ops`, `lane: bugs`, `lane: rnd`. Other labels: `roadmap`, `needs-decision`,
  `client-request`, `priority: …`.

## Snapshot (2026-11-23)

95 open `backlog` issues: 68 features, 15 ops, 8 R&D, 3 bugs (#660, #666, #686; #678 has no lane); 14 on the roadmap
(#805, #710, #686, #681, #679, #678, #667, #666, #660, #620, #575, #512, #410, #162); 25 need a decision (#681 no
longer does: his six decisions came Nov 22). 8 high, 35 medium, 52 low, no critical.
Closed since 2026-11-22: **#320** release notes (#919, #920, #922) and **#321** status page (#917, #918), both from the
backlog; **#558** Google Cloud owner steps (not labeled `backlog`; Editor off the default accounts, follow-ups in
#940). New since Nov 22, outside the backlog: #927 scheduled workflows 6–9 hours late (bug, high, ops) and #928 move
every scheduled job to Google Cloud (high, ops; steps 1–6 merged Nov 22, both still open); #921 browser error
reporting (medium, ops, deferred); #940 least-privilege follow-ups after #558 (no labels). #678 (fixed by #740) and
#686 (fixed by #851) are still open.

**High priority:** #805 full functional audit after the code split (needs the owner's go-ahead; on the roadmap since
Nov 21; see [Acquisition readiness](acquisition-readiness.md#splitting-the-big-files-5)) · #575 release process after
beta · #512 security pending actions (lockout stage C around Nov 29, App Check) · #620 acquisition readiness (needs a
decision; §2, §4 and §5 nearly all done or accepted by Nov 22, #575 and #512 left; see
[Acquisition readiness](acquisition-readiness.md)) · #648 a clear Finances message for team coaches · #681
development and staging: PR previews, staging as a production mirror, a testing period before production
(decisions made Nov 22; build step 1 part 1 done, #946; see [Versions](versions.md#after-beta-575-high)) · #410 client groups: coach-made groups with assigned coaches and group
managers · #710 Your brand: an app name separate from the business name · outside the backlog: #927/#928 scheduled jobs (above).

**Medium (selection):** #382 client add-ons · #634 import a returning client's history from a MetabolicHQ export
(needs a decision) · #355 recipe/meal and history import from other nutrition apps · #356 recipes · #162 wearable sync
· #570 free coach marketplace · #358 coach custom reports · #602 progress photos · #603 save check-ins partway ·
#478 rep-max table · #479 suggested weights · #332 coach onboarding workflows · #256 MCP server · #174 integrations ·
#381 HIPAA-ready (deferred, owner Nov 22) · #657 end-to-end coverage of every button,
field and display (stages 1–2 done) · #660 e2e: Stripe Checkout sometimes shows Link + hCaptcha instead of the card
form (bug; test-mode card-only and a Link-screen step went in, #687, #688) · #666 food diary ‹ Back after changing
days can land on the wrong day (bug).

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
