---
title: Security
summary: Security scanning, monitoring, App Check/Turnstile, CSP, Google Cloud owner steps, two-step sign-in
updated: 2026-11-15
sources: [notes, "#512", "#514", "#515", "#548", "#550", "#558", "#595", "#322", "#613", CHANGELOG, docs/security]
---

# Security

- Two-step sign-in for coaches; authenticator-app codes on staging for load-test coaches.
- Bot protection: Firebase **App Check with Cloudflare Turnstile** (custom provider), metrics first then enforce
  (#548). Every form gets Turnstile.
  - Stage 1 (metrics only) went live on 2026-11-14 and was reverted the same hour: the invisible check timed out and
    the widget couldn't retry (#605, reverted by #606; #548). The owner then made a separate **Invisible** Turnstile
    widget just for App Check, its secret in Secret Manager (#548). Next try: remove the widget on timeout, don't
    hold start-up on it, and test on a preview link before production (#548).
- Browser API key restricted to the project's own sites, their custom domains and `*.metabolichq.app`, on staging
  then production (#595, closed 2026-11-15). A new partner coach custom domain means re-running the script (#595).
- Reporting: `/.well-known/security.txt` on metabolichq.app and app.metabolichq.app, plus a policy page at
  **metabolichq.app/security** (reply within 3 business days, good-faith testing rules, no bounty). Renew `Expires`
  before 2027-11-14; a test fails once it passes (#322, closed 2026-11-14). Legal review of the wording goes with the
  trust page (#319).
- The security scan counts `metabolichq.app`, `coachbronson.web.app` and `coachbronson.com` as ours; coachbronson.com
  stays on sign-in's authorized domains until it moves in July 2027 (owner's call, #613).
- CIS Google Cloud audit (2026-11-12) in `docs/security/`.
- Scans: nightly plus PR-level (`pr-security.yml`, `security-scan.yml`); shown in [MetHQ Monitor](methq-monitor.md).

## Open, high priority

- #512 auditing and alerting (nightly scan, breach monitoring, portal Security page)
- #514 breach and suspicious-activity monitoring with automatic lockout
- #515 Security page in the portal (scan results, events, lockouts, accepted risks)
- #558 owner steps in Google Cloud: scan read access, App Check key, functions account instead of Editor

## Open, medium

#548 App Check with Turnstile; #550 full Content-Security-Policy (report-only first);
#381 HIPAA-ready MetabolicHQ (see [HIPAA](hipaa.md)).

## Related

[Engineering rules](../rules/engineering-rules.md) · [Research and privacy](research-and-privacy.md)
