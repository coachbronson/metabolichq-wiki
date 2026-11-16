---
title: Roadmap and backlog
summary: Where the backlog lives, priority rules, the current shape of open work, and the member/coach roadmap
updated: 2026-11-16
sources: [GitHub issues in mac-app, notes]
---

# Roadmap and backlog

- **Source of truth:** GitHub issues in `coachbronson/mac-app` labeled `backlog`. Pick work with the
  `mpt-backlog-picker` skill. Priority rules: [Engineering rules](../rules/engineering-rules.md#backlog-priorities).
- Lanes: `lane: features`, `lane: ops`, `lane: bugs`, `lane: rnd`. Other labels: `roadmap`, `needs-decision`,
  `client-request`, `priority: …`.

## Snapshot (2026-11-16)

77 open `backlog` issues: 57 features, 12 ops, 7 R&D, no bugs (one, #410, has no lane); 6 on the roadmap (#575,
#570, #567, #550, #512, #162); 21 need a decision. 4 high, 24 medium, 49 low, no critical. Closed since 2026-11-15:
#514, #515, #623, #626 (done), #548 (moved into #512). 17 opened since 2026-11-15. #355 moved from high to medium and
off the roadmap.

**High priority:** #575 release process after beta · #512 security pending actions (lockout stage C around Nov 29,
App Check) · #620 acquisition readiness: raise platform maturity from beta (about 2 of 5) toward enterprise-grade
(needs a decision) · #648 a clear Finances message for team coaches · #558 Google Cloud owner steps (not labeled
`backlog`).

**Medium (selection):** #382 client add-ons · #634 import a returning client's history from a MetabolicHQ export
(needs a decision) · #355 recipe/meal and history import from other nutrition apps · #356 recipes · #162 wearable sync
· #570 free coach marketplace · #358 coach custom reports · #602 progress photos · #603 save check-ins partway ·
#478 rep-max table · #479 suggested weights · #410 client groups · #332 coach onboarding workflows · #256 MCP server
· #174 integrations · #319/#320/#321 trust page, release notes, status page · #550 CSP · #381 HIPAA-ready.

**New, low:** coach add-on marketplace #633 and the GLP-1 companion module #628 (#629–#632); Challenges #639; Fasting
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
