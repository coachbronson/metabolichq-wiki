---
title: Roadmap and backlog
summary: Where the backlog lives, priority rules, the current shape of open work, and the member/coach roadmap
updated: 2026-11-18
sources: [GitHub issues in mac-app, notes]
---

# Roadmap and backlog

- **Source of truth:** GitHub issues in `coachbronson/mac-app` labeled `backlog`. Pick work with the
  `mpt-backlog-picker` skill. Priority rules: [Engineering rules](../rules/engineering-rules.md#backlog-priorities).
- Lanes: `lane: features`, `lane: ops`, `lane: bugs`, `lane: rnd`. Other labels: `roadmap`, `needs-decision`,
  `client-request`, `priority: …`.

## Snapshot (2026-11-18)

86 open `backlog` issues: 59 features, 14 ops, 7 R&D, 3 bugs (#660, #666, #686; #410, #678 and #716 have no lane); 9
on the roadmap (#681, #679, #678, #667, #620, #575, #570, #512, #162); 23 need a decision. 7 high, 26 medium, 52 low,
no critical; #716 has no priority yet.
Closed since 2026-11-17: #550 full Content-Security-Policy, now enforced on all three sites; #711 Change the main
coach opened an empty support request. 5 opened since 2026-11-17 (#711 already closed). #410 raised from medium to
high.

**High priority:** #575 release process after beta · #512 security pending actions (lockout stage C around Nov 29,
App Check) · #620 acquisition readiness: raise platform maturity from beta (about 2 of 5) toward enterprise-grade
(needs a decision) · #648 a clear Finances message for team coaches · #681 development and staging: PR previews,
staging as a production mirror, a testing period before production (needs decisions; changes #575's staging gate) ·
#410 client groups: coach-made groups with assigned coaches and group managers (raised Nov 18) · **new** #710 Your
brand: an app name separate from the business name · #558 Google Cloud owner steps (not labeled `backlog`).

**Medium (selection):** #382 client add-ons · #634 import a returning client's history from a MetabolicHQ export
(needs a decision) · #355 recipe/meal and history import from other nutrition apps · #356 recipes · #162 wearable sync
· #570 free coach marketplace · #358 coach custom reports · #602 progress photos · #603 save check-ins partway ·
#478 rep-max table · #479 suggested weights · #332 coach onboarding workflows · #256 MCP server · #174 integrations ·
#319/#320/#321 trust page, release notes, status page · #381 HIPAA-ready · #657 end-to-end coverage of every button,
field and display (stages 1–2 done) · #660 e2e: Stripe Checkout sometimes shows Link + hCaptcha instead of the card
form (bug; test-mode card-only and a Link-screen step went in, #687, #688) · #666 food diary ‹ Back after changing
days can land on the wrong day (bug).

**New, medium:** #699 change a space's main coach: the Platform tool after support checks (needs decisions).

**New, low:** #686 owner's Spaces & coaches table wider than a 1366 px screen (bug). **New, no priority:** #716 nightly
scan flags a weakened Content-Security-Policy.

**Low (recent):** #667 test emulators to firebase-tools 15 (blocked on a fixed 15.x) · #678 security rules
`clientAcctOn()` error noise · #679 MetHQ blog go-live run fails daily on "Save the go-live log" (posts still go
live; the log is never saved). Earlier: coach add-on marketplace #633 and the GLP-1 companion module #628 (#629–#632); Challenges #639; Fasting
tracker #640; AI progress troubleshooting #642; Leads CRM and discovery calls #643; call prep brief #637; own
equipment in a training location #641; weight-plateau signal #644; wiki system documentation #638; MPT resource pack
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
