---
title: Security
summary: Security scanning, monitoring, App Check/Turnstile, CSP, Google Cloud owner steps, two-step sign-in
updated: 2026-11-14
sources: [notes, "#512", "#514", "#515", "#548", "#550", "#558", "#595", docs/security]
---

# Security

- Two-step sign-in for coaches; authenticator-app codes on staging for load-test coaches.
- Bot protection: Firebase **App Check with Cloudflare Turnstile** (custom provider), metrics first then enforce
  (#548). Every form gets Turnstile.
- CIS Google Cloud audit (2026-11-12) in `docs/security/`.
- Scans: nightly plus PR-level (`pr-security.yml`, `security-scan.yml`); shown in [MetHQ Monitor](methq-monitor.md).

## Open, high priority

- #512 auditing and alerting (nightly scan, breach monitoring, portal Security page)
- #514 breach and suspicious-activity monitoring with automatic lockout
- #515 Security page in the portal (scan results, events, lockouts, accepted risks)
- #558 owner steps in Google Cloud: scan read access, App Check key, functions account instead of Editor

## Open, medium

#550 full Content-Security-Policy (report-only first); #595 restrict the browser API key (staging first);
#381 HIPAA-ready MetabolicHQ (see [HIPAA](hipaa.md)).

## Related

[Engineering rules](../rules/engineering-rules.md) · [Research and privacy](research-and-privacy.md)
