---
title: System documentation
summary: Where the enterprise system documents live (SSP, config, change, resource, O&M, detailed design) and what each covers
updated: 2026-11-20
sources: ["#638", "#620", "#868", notes]
---

# System documentation

The full documents live in **Google Drive › Documentation** (folder `12gDgMAQDVP8vYBttR0YmZtInsewirAEP`), not in
this wiki. The wiki only points to them (owner's call, Nov 20, #638). They are written for an enterprise buyer,
auditor or new engineer, and support [Acquisition readiness](acquisition-readiness.md) (#620).

| Document | Covers | Last reviewed |
|---|---|---|
| [System Security Plan (SSP)](https://docs.google.com/document/d/1JCXrOTivA9QIUinGEJzqXHXhwS3s81jwhAhJKkFX-wU/edit) | System boundary, data types (incl. health data), roles and access, controls in place, open risks R1–R11 and planned controls | 2026-11-20 |
| [Configuration management plan](https://docs.google.com/document/d/1WzqvXqVJLVnC-whtHIc--gdAC4A7-U-4Va4esy3RmR8/edit) | What's under config control (in the repo and outside it), baselines, how config changes are made and recorded, drift detection | 2026-11-20 |
| [Change management plan](https://docs.google.com/document/d/1MleX6QdFwW8xEamny3fBqo6RUiC6vHS1OeIqmkGvVpw/edit) | Branch-per-change, blast radius, risk levels and approval, testing levels, staging gate, rollback, release notes | 2026-11-20 |
| [Resource management plan](https://docs.google.com/document/d/1VkLBUxfWAS74H-Tx2WidTGa6DH9dc_eZcOxDugwZDds/edit) | Google Cloud/Firebase resources, GitHub, third-party services and license inventory, secret names, capacity | 2026-11-20 |
| [O&M plan](https://docs.google.com/document/d/1-2ESI-k1sJ5RJNdUI09OGitxvIzKxUE2r3mt1tkLLmA/edit) | Monitoring and alerts, scheduled jobs, backup and restore, maintenance, incident procedure, support | 2026-11-20 |
| [Detailed System Design](https://docs.google.com/document/d/1vo86_tCDzbLNYM0QKQHw83O2UjKKd5eKNC39IV0eYbM/edit) | Components, data flows, ports and protocols, interconnections; Mermaid source of the diagrams in its appendix | 2026-11-20 |
| [Component diagram](https://drive.google.com/file/d/1qkUHVN8ZaTftbV9h9NhDr5UE5xwjXk2C/view) · [Data flow diagram](https://drive.google.com/file/d/1UWFMITu3WJLqeMODEXUs9JrX94zpPAr4/view) | Rendered PNGs | 2026-11-20 |

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

## Related

[Architecture](architecture.md) · [Security](security.md) · [Engineering rules](../rules/engineering-rules.md) ·
[Acquisition readiness](acquisition-readiness.md)
