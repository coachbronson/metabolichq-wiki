---
title: System documentation
summary: Where the enterprise system documents live (SSP, config, change, resource, O&M, detailed design) and what each covers
updated: 2026-11-27
sources: [Drive › Documentation (each document's "Last reviewed" line, read Nov 27), "#410", "#575", "#603", "#1022", "#1024", "#1033", "#681", "#960", "#983", "#975", "#985", "#950", "#952", "#955", "#956", "#958", "#962", "#638", "#620", "#868", "#876", "#893", "#907", "#909", "#321", "#924", "#926", "#928", "#558", "#940", "#946", mac-app CLAUDE.md, notes]
---

# System documentation

The full documents live in **Google Drive › Documentation** (folder `12gDgMAQDVP8vYBttR0YmZtInsewirAEP`), not in
this wiki. The wiki only points to them (owner's call, Nov 20, #638). They are written for an enterprise buyer,
auditor or new engineer, and support [Acquisition readiness](acquisition-readiness.md) (#620).

| Document | Covers | Last reviewed |
|---|---|---|
| [System Security Plan (SSP)](https://docs.google.com/document/d/11Abg3dJ8m-4QIg2aODJgqDUM-k6K6zne81bPWv6iTn8/edit) | System boundary, data types (incl. health data), roles and access, controls in place, open risks R1–R11 and planned controls | 2026-11-26 |
| [Configuration management plan](https://docs.google.com/document/d/1WzqvXqVJLVnC-whtHIc--gdAC4A7-U-4Va4esy3RmR8/edit) | What's under config control (in the repo and outside it), baselines, how config changes are made and recorded, drift detection (incl. the Live config report, #943) | 2026-11-26 |
| [Change management plan](https://docs.google.com/document/d/1MleX6QdFwW8xEamny3fBqo6RUiC6vHS1OeIqmkGvVpw/edit) | Branch-per-change, blast radius, risk levels and approval, testing levels, staging gate, rollback, release notes | 2026-11-26 |
| [Resource management plan](https://docs.google.com/document/d/1VkLBUxfWAS74H-Tx2WidTGa6DH9dc_eZcOxDugwZDds/edit) | Google Cloud/Firebase resources, GitHub, third-party services and license inventory, secret names, capacity | 2026-11-26 |
| [O&M plan](https://docs.google.com/document/d/1-2ESI-k1sJ5RJNdUI09OGitxvIzKxUE2r3mt1tkLLmA/edit) | Monitoring and alerts, scheduled jobs, backup and restore, maintenance, incident procedure, support | 2026-11-26 |
| [Detailed System Design](https://docs.google.com/document/d/1vo86_tCDzbLNYM0QKQHw83O2UjKKd5eKNC39IV0eYbM/edit) | Components, data flows, ports and protocols, interconnections; Mermaid source of the diagrams in its appendix | 2026-11-26 |
| [Engineer Onboarding Guide](https://docs.google.com/document/d/1ol4vmKjGY6vXOsT53uxVDttHOjrYc1kDsz5fGo8H6hQ/edit) | What the system is, where the code lives (the code map), setup, running and testing, making a change, releasing and undoing, day-to-day operations, a first week | 2026-11-26 |
| [Incident Response Procedure](https://docs.google.com/document/d/1QV6o_kHS-Q5uoEu_t8KbAMZbFCFbztmzL5H5i3T6txs/edit) | Roles and contacts, severity levels and response times, status-page and coach email templates, personal-data incident steps, write-up, incident log (mac-app issues labeled `incident`), quarterly practice | 2026-11-25 |
| Component diagram · Data flow diagram | Rendered PNGs in [Drive › Documentation](https://drive.google.com/drive/folders/12gDgMAQDVP8vYBttR0YmZtInsewirAEP): "MetabolicHQ component diagram (2026-11-26, blog merges)" and "… data flow diagram (2026-11-26, blog merges)", which include groups, the custom check-in, Claude jobs' Drive account, MetabolicHQ social media and blog merges; the "(2026-11-26, social media)", "(2026-11-26, Claude jobs Drive)", "(2026-11-25, feature switches)" and older PNGs are superseded (Drive › Documentation, read Nov 27). Re-render from the Mermaid source in the Detailed System Design at the next diagram change | 2026-11-26 |

## Keeping them current

- **Owner's rule (Nov 20):** any significant change to security, components, operations, configuration, resources or
  the change process updates the matching document in the same work; see
  [Engineering rules](../rules/engineering-rules.md#system-documentation-keep-it-current) for which change goes
  where (mac-app CLAUDE.md, PR #868).
- Each document has a "Last reviewed" date. Review when a new outside service, function area, data type or role is
  added, and at least every quarter (#638).
- The nightly update flags drift: a function, secret or outside host in the code that these documents don't list
  (#638).
- Update this table's dates when a document is reviewed.
- Nov 21 review: the SSP, configuration, resource and O&M plans and the Detailed System Design now count 110
  functions (69 callable), with the new `apiUsage` tripwire; the O&M plan has a Maintenance line for the Dec 19
  unused-function review (#876, #893).
- Nov 22 review: type checking (#909; CMP pinned tools and type baseline, Change plan, Resource plan), the status page
  (#321; SSP, RMP, DSD, O&M, CMP), the Cohort cache limit and package names (#915, #916; O&M), the incident procedure
  (#924), backup timing at 10× data (#926; O&M section 3), scheduled jobs moved to Google Cloud and the backups
  bucket (#928; SSP, CMP, RMP, O&M, DSD: 118 functions then), Editor removed (#558; SSP R3 closed, CMP IAM baseline),
  the service-account list (#940, #942; SSP, CMP). SSP risks R7, R8, R10 and R11 match the owner's Nov 22 calls
  (#321, #620).
- Nov 23: the one shared deploy workflow (#946) updated the CMP's CI/CD row and the Change plan's staging section,
  with the #681 decisions (#681 comment).
- Nov 23: the staging work (#681) updated the SSP (staging's AI questions and email copies, who reads them,
  authenticator-only two-step, the `USDA_STAGING_API_KEY` secret), CMP (staging's sign-in settings from the deploy,
  the new workflows, the function count), Change plan (demo data and its reset, PR previews), RMP (staging AI cost,
  the new secret and scheduler job), O&M (`stagingDemoStart`) and DSD (staging's AI flow, the inbox, preview
  channels), as the PRs' Docs to update lines list (#950, #952, #955, #956, #958, #962); each document was edited
  on Nov 23 (Drive). #966 needed none.
- Nov 24: the staging gate (#681 step 4; Change plan: the gate on, the first gated merge, how to undo it; CMP:
  `RELEASE_GATE` on; earlier in the step SSP, O&M, DSD, RMP and Onboarding Guide), the billing demo clients (#960;
  O&M, RMP, Onboarding Guide, CMP, SSP) and the Claude jobs and reminders (#983; SSP, CMP, RMP, O&M), per those
  issues' comments. Dates are from those comments; Drive wasn't reachable from the nightly job to confirm them. The
  Incident Response Procedure wasn't changed.
- Nov 25: the release status signals (#575, PRs #1000–#1002; DSD data flow F12, ports, interconnections, both
  diagrams; SSP; CMP); release messaging (#1024; O&M, Incident Response Procedure, SSP, DSD); check-ins (#603; SSP,
  DSD, CMP, O&M, RMP, with the backups corrected to the `nightlyBackup` function writing to the private bucket);
  feature switches (#1022; O&M, Change plan, SSP, CMP, DSD, Onboarding Guide, RMP); groups A1 and A2 (#410; SSP,
  DSD, CMP, O&M, RMP, Onboarding Guide); the brand permission (#1033; SSP roles). Counts across them after these:
  139 functions (74 callable, 26 HTTPS, 39 scheduled; RMP, #1022) and 55 workflows (#410). Dates from the wiki
  inbox lines written by those sessions.
- Nov 26: groups A3 (#410, PR #1073; SSP roles and §5, DSD data model and F14, Onboarding Guide; O&M's Group coaches
  repair now treats a mismatch as urgent, since it can mean wrong access). A4 (#1076) needed none.
- The documents table in mac-app CLAUDE.md now also names the Engineer Onboarding Guide (code layout, setup, how to
  run and test) and the Incident Response Procedure (incident steps, with the O&M plan) (#907, #924).

## Related

[Architecture](architecture.md) · [Security](security.md) · [Engineering rules](../rules/engineering-rules.md) ·
[Acquisition readiness](acquisition-readiness.md)
