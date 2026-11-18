---
title: Security
summary: Security events and sign-in alerts (alert-only), Security page, scanning, App Check/Turnstile, enforced Content-Security-Policy, staging account, open work
updated: 2026-11-18
sources: [notes, "#512", "#514", "#515", "#548", "#619", "#624", "#626", "#638", "#550", "#558", "#595", "#322", "#613", "#676", "#678", "#671", "#684", "#690–#693", "#697", "#702", "#704", "#708", "#716", CHANGELOG, docs/security]
---

# Security

- Two-step sign-in for coaches; authenticator-app codes on staging for load-test coaches.
- **All open security work lives in #512** (Pending actions), at the owner's request; #514 and #548 were closed into
  it on 2026-11-15.

## Monitoring and alerts (#514, alert-only)

- **Security events and alerts** (stage A, #619): job **securityWatch** runs every 5 minutes and emails the owner
  about unusual events (critical ones also push to his phone): a coach opening more than 40 clients' records in an
  hour, a coach deleting more than 10 clients in an hour, sign-up bursts (more than 25 in an hour, or more than 6 from
  one non-major email domain), a spike in blocked database reads/writes, and fake Stripe webhook calls. Space exports
  and deletions go on the timeline without an alert (CHANGELOG 2026-11-15).
- **Sign-ins and Google Cloud changes** (stage B, #624, #635; live on production): job **securityLogWatch** reads the sign-in request
  logs and Google Cloud audit logs every minute. Every coach's sign-in is recorded with method, device, country and
  network (first three parts of the address, never the full IP). Alerts: new country or device, repeated failed
  sign-ins or wrong two-step codes from one network, and Google Cloud changes not made by the deploy (IAM, service
  accounts or keys, hand-deployed rules or functions, sign-in settings, secrets). Read from logs, not a blocking
  sign-in function, so sign-in can't be slowed (owner's choice, #514).
- Countries come from MaxMind's free GeoLite2 file, downloaded weekly by **geoDbRefresh** and read on our own servers;
  addresses never go to an outside service (#624, #635).
- **Nothing locks yet.** Lockout and Unlock (stage C) come after two quiet alert-only weeks, around Nov 29, with the
  owner's OK; billing-change watching is added then (#512).

## Security page (#515, done)

Portal → Platform → **Security** (owner only, two-step): last night's scan check by check, open findings with age,
a 30-night trend, security events (90 days; All / Alerts only / Critical), alert history, lockouts ("not on yet"),
and accepted risks. **Accept this risk** takes a reason and a review date (up to a year); the nightly scan stops
counting that finding until then. On a phone the [MetHQ Monitor](methq-monitor.md)'s Security tab shows the same.
Alert links open the page on a computer and the Monitor tab on a phone (#515, CHANGELOG 2026-11-15).

## Bot protection: App Check with Turnstile (#512)

- Firebase **App Check with Cloudflare Turnstile** (custom provider; reCAPTCHA ruled out). Every form gets Turnstile.
- MetabolicHQ has its **own Turnstile widget** ("MetabolicHQ", its own hostnames only), used by the partner apply form,
  Custom Build form, brand preview, sign-in help and feedback page. The old widget was shared with coachbronson.web.app
  and was deleted in the split on Nov 17, which stopped those captchas until the new one went in (#684, CHANGELOG
  2026-11-17). Its secret is the `TURNSTILE_SECRET` GitHub secret.
- Stage 1 (metrics only) went live on 2026-11-14 and was reverted the same hour: the invisible check timed out and the
  widget couldn't retry (#605, reverted by #606). The owner then made a separate **Invisible** widget for App Check,
  its secret in Secret Manager (#548).
- Next (#512): stage 1 again with the fixes, tested on a preview link first; the owner registers the app in App Check;
  a week of metrics; then enforce one service at a time (Firestore, Storage, Auth, callable functions), each with
  the owner's OK. Turnstile is already allowed in the app's Content-Security-Policy, so stage 1 needs no CSP change
  (#550). (#548 closed as not done, moved to #512. Previously coachbronson-site's admin sign-in also had to be
  covered before Auth; the site now has its own project and sign-in, coachbronson-site #29.)

## Content-Security-Policy (#550, done)

- **All three sites enforce a full policy** (scripts, styles, fonts, images, connections, frames, workers, form
  targets) in the one header that also carries the framing rules: metabolichq.app (#693), the coach portal and MetHQ
  Monitor (#697), the app (#708, Nov 18). Violations still report to `/__csp` (counters in `ops/csp/seen`).
- **Styles allow `'unsafe-inline'`, scripts never** (owner's call; the screens use over 1,200 inline style
  attributes). `test/cspreport.test.mjs` fails if scripts get `'unsafe-inline'` or `'unsafe-eval'`, or if an inline
  `<script>` or handler comes back (#690–#692).
- Allowed because the report week showed they're needed: `apis.google.com` (Google sign-in), `www.google.com` for
  connections (the text-message two-step check), Turnstile on the app (#690, #691).
- The **CSP reports** workflow (by hand, read-only) summarizes the report counters by site, directive and source
  (#671).
- Two gaps the end-to-end run couldn't see, because production hosts are local test servers there: Vimeo, Loom and
  file-preview frames (#702) and SVG logos read with `fetch` of a `data:` URL in the brand editor (#704). Both fixed,
  each with a test. Before enforcing the app, its policy was also checked in code and in a browser (#550).
- Follow-up: the nightly scan should flag a live policy that loses `script-src`, allows unsafe scripts or falls back
  to report-only (#716, open).

## Other protections

- **Staging has its own deploy account** (`github-deploy@metabolichq-staging`, keyless sign-in from GitHub through
  Workload Identity Federation, only mac-app's workflows). The production deploy account no longer has access to
  staging (#626, #627).
- Browser API key restricted to the project's own sites, their custom domains and `*.metabolichq.app`, on staging
  then production (#595). A new partner coach custom domain means re-running the script (#595).
- Reporting: `/.well-known/security.txt` on metabolichq.app and app.metabolichq.app, plus a policy page at
  **metabolichq.app/security** (reply within 3 business days, good-faith testing rules, no bounty). Renew `Expires`
  before 2027-11-14; a test fails once it passes (#322). Legal review of the wording goes with the trust page (#319).
- The security scan counts only MetabolicHQ's own domains, so a coachbronson domain left on sign-in would show up as
  a finding. `scripts/remove-coachbronson-site.sh` (run once by the owner) took the site's functions, secrets, data
  and sign-in/API-key domains out of MetabolicHQ's project (#676, CHANGELOG 2026-11-17). Its Hosting-site step was
  skipped, so the old coachbronson.web.app address was deleted afterwards by the one-time workflow **Delete old site
  address** (#695, #696). (Previously the scan counted coachbronson.web.app and coachbronson.com as ours, #613.)
- CIS Google Cloud audit (2026-11-12) in `docs/security/`.
- Scans: nightly plus PR-level (`pr-security.yml`, `security-scan.yml`); shown on the Security page and in the Monitor.

## Open

- **High:** #512 pending actions (lockout stage C, App Check); #558 owner steps in Google Cloud (scan read access,
  App Check key, functions account instead of Editor).
- **Medium:** #381 HIPAA-ready MetabolicHQ (see [HIPAA](hipaa.md)).
- **No priority yet:** #716 scan check for a weakened Content-Security-Policy.
- **Low:** #678 security rules: `clientAcctOn()` throws when an account has no `clientAcct` field (access is still
  refused; noise in every e2e report; a rules change, so high-risk to fix) · #638 wiki documentation set (system security plan, config, change and resource management, O&M plan).

## Related

[Engineering rules](../rules/engineering-rules.md) · [Research and privacy](research-and-privacy.md)
