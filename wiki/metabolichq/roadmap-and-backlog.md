---
title: Roadmap and backlog
summary: Where the backlog lives, priority rules, the current shape of open work, and the member/coach roadmap
updated: 2026-11-28
sources: ["#620", "#1174", "#1197", "#1163", "#1173", "#1185", "#1217", "#1153", "#1140", "#1131", "#1214", "#1215", "#1141", "#1154", "#1157", "#157", "#512", "#983", "#1089", "#1090", "#1095", "#1097", "#1099", "#1100", "#1111", "#1113", "#1119", "#1122", "#410", "#575", "#603", "#681", "#970", "#1005", "#1007", "#1010", "#1016", "#1038", "#1079", "#983", GitHub issues in mac-app, notes]
---

# Roadmap and backlog

- **Source of truth:** GitHub issues in `coachbronson/mac-app` labeled `backlog`. Pick work with the
  `mpt-backlog-picker` skill. Priority rules: [Engineering rules](../rules/engineering-rules.md#backlog-priorities).
- Lanes: `lane: features`, `lane: ops`, `lane: bugs`, `lane: rnd`. Other labels: `roadmap`, `needs-decision`,
  `client-request`, `priority: …`.

## Snapshot (2026-11-28)

110 open `backlog` issues (113 open issues in all): 67 features, 25 ops, 10 R&D, 7 bugs (#678 has no lane); 24 on
the roadmap; 33 need a decision. No critical, 2 high, 38 medium, 68 low; #1038 and #1100 have no priority yet.
**Roadmap** (he added 13 items on Nov 27: #643, #640, #630, #533, #532, #358, #356, #334, #332, #256, #174, #167,
#155; #620 and #679 left it by closing): #864, #863, #861, #857, #805, #699, #678, #667, #643, #640, #630, #602, #570,
#533, #532, #358, #356, #334, #332, #256, #174, #167, #162, #155. #256 (MCP server) moved from R&D to features.

**Closed since 2026-11-27** (each "How this was resolved" read):
- **#620** acquisition readiness, about 3 of 5 (see [Acquisition readiness](acquisition-readiness.md)).
- **#1174** My Daily Focus (see [My Daily Focus](my-daily-focus.md)); **#491** Resources drip for existing clients
  and **#1135** client view (see [Resources and files](resources-and-files.md)).
- **#1095** group call recording and coaches-only AI notes; **#1177** New call search (see
  [Coaching calls](coaching-calls.md)). **#1016** body comp signals (see
  [Biometrics and signals](biometrics-and-signals.md)). **#1010** Skip keeps a client's own rows (see
  [Training](training.md)).
- **#679** and **#1122** the blog go-live (see [MetabolicHQ content](methq-content.md)); **#1125** social jobs sign
  in again.
- Rules: **#1141** issue labels (and its test issue #1146), **#1154** naming work, **#1156** build the workflow,
  **#1157** the yearly audit (see [Engineering rules](../rules/engineering-rules.md)). **#927/#928** scheduled jobs in
  Google Cloud (done Nov 22, closed Nov 27). **#1119** a test-only midnight-UTC fix.

**New since 2026-11-27:** mostly the audit's findings (#805): #1197 the nightly review stops after opening its PR
while its run shows green (**high**, bugs) · #1163 release notes dated Dec 1–10 (medium, bugs) · #1185 the site loads
Cloudflare's captcha on open (medium, bugs) · #1173 production still holds the site's four `SITE_*` secrets (medium,
needs a decision) · #1217 the deal card names Coach Bronson on a partner's deals (medium, needs a decision) · #1153
the 0.75% server error rate (medium, ops) · low: #1164, #1165, #1166, #1170, #1182, #1193 (decisions or documents),
#1168, #1208, #1212 (bugs), #1211, #1218, #1220 (tidy-ups). Others: #1140 review competitor websites (medium, R&D) ·
#1131 Resources drip from a program start (low, R&D, needs a decision) · #1214 re-make the My Daily Focus videos
(low) · #1215 habit achievements for habits clients write themselves (low, needs a decision). Re-labeled: #1099 a
sponsor summary of group reports to R&D, low (his call Nov 27); #1005 release watch follow-ups labeled medium, ops (it had no labels).

**High priority:** #805 the 2026 full functional audit (under way since Nov 27; see
[Acquisition readiness](acquisition-readiness.md)) · #1197 the nightly review job. (Previously also #620, closed
Nov 27.)

**Medium (selection):** roadmap: #864 save a workout to a program or duplicate a program · #863 assign a program to
one client, a group or everyone · #861 delegated admin roles · #857 SOAP notes for practitioners · #699 change a
space's main coach (needs decisions) · #602 progress photos (needs a decision) · #570 free coach marketplace · #162
wearable sync. Others: #382 client add-ons · #634 import a returning client's history (needs a decision) · #355
recipe/meal and history import · #356 recipes · #358 coach custom reports · #478 rep-max table · #479 suggested
weights · #332 coach onboarding workflows · #256 MCP
server · #742 MCP skill toolkit (needs a decision) · #746 coach-written waivers (needs a decision; see
[Partner program](partner-program.md#agreement-and-onboarding)) · #174 integrations · #381 HIPAA-ready (deferred,
owner Nov 22) · #657 end-to-end coverage of every button, field and display (untested controls and displays 507, `ops/ui-gaps.json`, Nov 28, #805) ·
#877 e2e for authenticator two-step on staging.

**Low (recent):** #667 test emulators to firebase-tools 15 (blocked on a fixed 15.x) · #678 security rules
`clientAcctOn()` error noise (fixed by #740, still open) · #974 round robin call scheduling (needs a decision). Earlier: coach add-on
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
