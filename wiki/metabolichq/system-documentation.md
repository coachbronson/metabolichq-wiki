---
title: System documentation
summary: Where the enterprise system documents live (SSP, config, change, resource, O&M, detailed design) and what each covers
updated: 2026-11-25
sources: ["#681", "#960", "#983", "#975", "#985", "#950", "#952", "#955", "#956", "#958", "#962", "#638", "#620", "#868", "#876", "#893", "#907", "#909", "#321", "#924", "#926", "#928", "#558", "#940", "#946", mac-app CLAUDE.md, notes]
---

# System documentation

The full documents live in **Google Drive › Documentation** (folder `12gDgMAQDVP8vYBttR0YmZtInsewirAEP`), not in
this wiki. The wiki only points to them (owner's call, Nov 20, #638). They are written for an enterprise buyer,
auditor or new engineer, and support [Acquisition readiness](acquisition-readiness.md) (#620).

| Document | Covers | Last reviewed |
|---|---|---|
| [System Security Plan (SSP)](https://docs.google.com/document/d/11Abg3dJ8m-4QIg2aODJgqDUM-k6K6zne81bPWv6iTn8/edit) | System boundary, data types (incl. health data), roles and access, controls in place, open risks R1–R11 and planned controls | 2026-11-24 |
| [Configuration management plan](https://docs.google.com/document/d/1WzqvXqVJLVnC-whtHIc--gdAC4A7-U-4Va4esy3RmR8/edit) | What's under config control (in the repo and outside it), baselines, how config changes are made and recorded, drift detection (incl. the Live config report, #943) | 2026-11-24 |
| [Change management plan](https://docs.google.com/document/d/1MleX6QdFwW8xEamny3fBqo6RUiC6vHS1OeIqmkGvVpw/edit) | Branch-per-change, blast radius, risk levels and approval, testing levels, staging gate, rollback, release notes | 2026-11-24 |
| [Resource management plan](https://docs.google.com/document/d/1VkLBUxfWAS74H-Tx2WidTGa6DH9dc_eZcOxDugwZDds/edit) | Google Cloud/Firebase resources, GitHub, third-party services and license inventory, secret names, capacity | 2026-11-24 |
| [O&M plan](https://docs.google.com/document/d/1-2ESI-k1sJ5RJNdUI09OGitxvIzKxUE2r3mt1tkLLmA/edit) | Monitoring and alerts, scheduled jobs, backup and restore, maintenance, incident procedure, support | 2026-11-24 |
| [Detailed System Design](https://docs.google.com/document/d/1vo86_tCDzbLNYM0QKQHw83O2UjKKd5eKNC39IV0eYbM/edit) | Components, data flows, ports and protocols, interconnections; Mermaid source of the diagrams in its appendix | 2026-11-24 |
| [Engineer Onboarding Guide](https://docs.google.com/document/d/1ol4vmKjGY6vXOsT53uxVDttHOjrYc1kDsz5fGo8H6hQ/edit) | What the system is, where the code lives (the code map), setup, running and testing, making a change, releasing and undoing, day-to-day operations, a first week | 2026-11-24 |
| [Incident Response Procedure](https://docs.google.com/document/d/1QV6o_kHS-Q5uoEu_t8KbAMZbFCFbztmzL5H5i3T6txs/edit) | Roles and contacts, severity levels and response times, status-page and coach email templates, personal-data incident steps, write-up, incident log (mac-app issues labeled `incident`), quarterly practice | 2026-11-22 |
| [Component diagram](https://drive.google.com/file/d/1qkUHVN8ZaTftbV9h9NhDr5UE5xwjXk2C/view) · [Data flow diagram](https://drive.google.com/file/d/1UWFMITu3WJLqeMODEXUs9JrX94zpPAr4/view) | Rendered PNGs (the component diagram still says 109 functions and doesn't show Better Stack; re-render from the Mermaid source at the next diagram change, #893, #321) | 2026-11-20 |

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
- The documents table in mac-app CLAUDE.md now also names the Engineer Onboarding Guide (code layout, setup, how to
  run and test) and the Incident Response Procedure (incident steps, with the O&M plan) (#907, #924).

## Related

[Architecture](architecture.md) · [Security](security.md) · [Engineering rules](../rules/engineering-rules.md) ·
[Acquisition readiness](acquisition-readiness.md)
