---
title: Security
summary: Security events and sign-in alerts (alert-only), Security page, scanning, App Check/Turnstile, enforced Content-Security-Policy, staging account, open work
updated: 2026-11-27
sources: ["#1111", "#1113", "#1110", "#1033", "#1046", "#1059", "#1073", "#1000", "#1020", "#989", "#952", "#964", "#966", "#940", "#941", "#942", "#928", notes, "#512", "#514", "#515", "#548", "#619", "#624", "#626", "#638", "#550", "#558", "#595", "#322", "#613", "#676", "#678", "#671", "#684", "#690–#693", "#697", "#702", "#704", "#708", "#716", "#717", "#720", "#729", "#730", "#736", "#737", "#740", "#741", CHANGELOG, docs/security, #756, #759, #760, #761, #768, #783, #816, "#817–#830", #853, #854, #855, #866, #867, #870]
---

# Security

- Two-step sign-in for coaches; staging's two-step is authenticator-app codes only, no text codes (#952). When start-up
  is refused for the owner's email (no account record yet), the app shows the two-step set-up or "Sign in again"
  screen instead of a raw permission error; the rules didn't change (#964, #966).
- **#512 closed Nov 26** (nightly scan #513, monitoring stages A and B #514, Security page #515 done). Its two open
  parts are **deferred** (his call, Nov 26: not enough real usage yet to know what normal looks like): automatic
  lockout and Unlock (#514 stage C) in **#1111**, and App Check with Turnstile in **#1113**; both security, priority
  low, high risk when built (#512 "How this was resolved"). (Previously all open security work lived in #512.)

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

## Bot protection: App Check with Turnstile (deferred, #1113)

- Firebase **App Check with Cloudflare Turnstile** (custom provider; reCAPTCHA ruled out). Every form gets Turnstile.
- MetabolicHQ has its **own Turnstile widget** ("MetabolicHQ", its own hostnames only), used by the partner apply form,
  Custom Build form, brand preview, sign-in help and feedback page. The old widget was shared with coachbronson.web.app
  and was deleted in the split on Nov 17, which stopped those captchas until the new one went in (#684, CHANGELOG
  2026-11-17). Its secret is the `TURNSTILE_SECRET` GitHub secret.
- Stage 1 (metrics only) went live on 2026-11-14 and was reverted the same hour: the invisible check timed out and the
  widget couldn't retry (#605, reverted by #606). The owner then made a separate **Invisible** widget for App Check,
  its secret in Secret Manager (#548).
- **App Check was never turned on**: `public/js/firebase.js` has no site key and still uses reCAPTCHA, and no
  function enforces it (#512, #1113). Turnstile on the public forms (#684) is separate and done.
- **Deferred to #1113** (his call, Nov 26: not enough usage for a week of metrics to mean anything). When built:
  stage 1 again with the fixes, tested on a preview link first; the owner registers the app in App Check;
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
  (#671). The collector keeps up to 2,000 report kinds; once full, a new kind replaces the one seen longest ago, and
  a report over 20,000 bytes is refused even without a size header (#816 item 12, #826).
- Two gaps the end-to-end run couldn't see, because production hosts are local test servers there: Vimeo, Loom and
  file-preview frames (#702) and SVG logos read with `fetch` of a `data:` URL in the brand editor (#704). Both fixed,
  each with a test. Before enforcing the app, its policy was also checked in code and in a browser (#550).
- The nightly scan flags (medium, on the Security page and Monitor) a live policy that limits no scripts, a script
  rule that allows `'unsafe-inline'`, `'unsafe-eval'`, `*`, `https:`, `http:` or `data:`, and a site sending only a
  report-only policy. Styles are not judged (#716, #717, CHANGELOG 2026-11-18).

## Other protections

- **Staging has its own deploy account** (`github-deploy@metabolichq-staging`, keyless sign-in from GitHub through
  Workload Identity Federation, only mac-app's workflows). The production deploy account no longer has access to
  staging (#626, #627).
- Browser API key restricted to the project's own sites, their custom domains and `*.metabolichq.app`, on staging
  then production (#595). A new partner coach custom domain means re-running the script (#595).
- Reporting: `/.well-known/security.txt` on metabolichq.app and app.metabolichq.app, plus a policy page at
  **metabolichq.app/security** (reply within 3 business days, good-faith testing rules, no bounty). Renew `Expires`
  before 2027-11-14; a test fails once it passes (#322). The owner is handling legal review of the public wording
  (security and Trust pages) himself (#866).
- The security scan counts only MetabolicHQ's own domains, so a coachbronson domain left on sign-in would show up as
  a finding. `scripts/remove-coachbronson-site.sh` (run once by the owner) took the site's functions, secrets, data
  and sign-in/API-key domains out of MetabolicHQ's project (#676, CHANGELOG 2026-11-17). Its Hosting-site step was
  skipped, so the old coachbronson.web.app address was deleted afterwards by the one-time workflow **Delete old site
  address** (#695, #696). (Previously the scan counted coachbronson.web.app and coachbronson.com as ours, #613.)
- CIS Google Cloud audit (2026-11-12) in `docs/security/`.
- Security rules: `clientAcctOn()` now reads the client-account field with a default of false, so accounts without it
  get a clean "no" instead of a rules error. Access is unchanged (owner's OK, #740, CHANGELOG 2026-11-18).
- Security rules, Nov 20 nightly review (owner's OK): only the server writes a person's `wearables` link, so it can't
  be pointed at another wearables account (#819); a new MPT client's "waiting" record accepts only the normal sign-up
  fields, so nobody can start it with free access, a demo flag or a billing plan (#816, 13th item, #830).
- Security rules, Nov 25–26: only a space's main coach and head coaches (and the owner) write its brand (#1033,
  #1046); a coach reads only the check-in notes a client shared (#1020); groups and each client's `groupCoaches` are
  written only by the server's `groups` callable, and a client's coaches include their group coaches (`coachesOn`;
  #1059, #1073; see [Spaces and roles](spaces-and-roles.md#client-groups-410)). A group's own Community feed
  (`groupFeeds/{gid}/posts`) is read and posted to only while it's on, by the group's active clients, its coaches
  and managers, and head coaches; a client's `feeds` field is server-only (#1110). Custom check-in forms
  (`spaces/{sid}/config/checkin`) are written only by the `checkinForm` callable (#1093). Also fixed: the notices
  rule refused reactions other than 👏 (#1110).
- `releaseSignal` takes status changes only with a GitHub OIDC token from this repository's release-signal workflow
  on main (no stored secret; #1000). MetabolicHQ social media's `socialJob` takes only the Claude job workflow's
  OIDC token the same way, so no `SOCIAL_JOB_KEY` exists; `socialJob` and `socialCallback` are reviewed public
  endpoints (CHANGELOG 2026-11-26).
- Team-coach invites are created in one step, so two spaces can't take over the same email's invite; withdrawing
  checks ownership in the same step (#825).

## Google Cloud accounts

- **No service account of ours holds Editor** in production or staging (Nov 22, done by the owner, staging first;
  #558 closed). In production only Google's own `cloudservices` agent keeps Editor. The default compute account keeps
  only the four roles it needs to build functions (Cloud Build builder, Artifact Registry writer, Logs writer, Storage
  object viewer); the 12 older scheduler jobs now call their functions as `functions-runtime`; the security scan
  closed both "Editor on the whole project" findings (#558).
- Follow-ups done the same night (#940): staging's `github-deploy` has production's deploy roles instead of Editor;
  the production compute account's unused project-wide Token Creator is gone (`functions-runtime` signs as itself);
  production's deploy account can no longer act as staging's `functions-runtime`; the old site deploy account
  `github-deploy-727` (last used Nov 15) and a one-time key on Firebase's admin account are disabled, to be deleted
  around Nov 29 with the owner's OK. The first production builds under the new roles passed (116 and 118 functions,
  no permission errors; #940 closed Nov 23). Left: deleting `github-deploy-727` and the Firebase key after the owner's
  OK at the Nov 29 reminder (now in `functions/reminders.json`: on Nov 29 at 10 AM Eastern it emails the owner and
  starts the `key-cleanup` Claude job, which checks nothing broke and deletes nothing, #989), then 727 comes off `ops/cloud-accounts.json` (#940).
- `ops/cloud-accounts.json` lists every service account in production and staging: what uses it, why, its
  project-wide roles and whether it may have a key. The nightly scan checks production against it and flags any
  unlisted account, role or key, a missing role, a listed account that's gone, or one that should be disabled but
  isn't (#942). Owner's ask: keep track of which accounts are used by which services and why (#940).
- `WORKFLOW_START_TOKEN`: a fine-grained GitHub token that can only start workflows in mac-app, used by the
  starter functions (#928, #936).

## Code scanning

- Scans: nightly plus PR-level (`pr-security.yml`, `security-scan.yml`); shown on the Security page and in the Monitor.
- The check that every callable or web function checks who is calling reads every file under `functions/`, so moved
  functions stay checked; a deployed function it can't find is its own finding (#720).
- A file Semgrep couldn't fully check (timeout, memory, parse error, too big) is a medium finding, "Semgrep couldn't
  fully check <file>" (#729). Semgrep runs `--verbose`, so skipped and timed-out files are listed, not hidden (#759),
  and gets 30 seconds per rule and file (was 5), so the biggest files are now checked fully; a parse error names the
  line (owner's OK, #756, #760).
- The function check also reads other ways of writing a function and reports any deployed function it can't inspect;
  the Content-Security-Policy check covers `script-src-elem` and `script-src-attr` (#756, #759).
- Found once code moved into smaller files (#620), fixed with the owner's OK: the signed-agreement download always
  sends a fixed file type with `nosniff`, as an attachment (#730); the Stripe Checkout logo is sent with `nosniff`
  (#736).
- Found once Semgrep could finish the server's main file: the coach's home-screen icon is now sent with `nosniff`
  (#761).
- Reviewed exceptions in `scripts/security/allow.json`, each with a test that keeps it to that one function: the
  packages table's open CORS (on purpose, public data only, #737), the Checkout logo's Semgrep data-flow warning
  (#741), the server warnings found with the longer timeout (#760), and the client app's three (two fixed regex
  patterns, one escaped `insertAdjacentHTML`; owner's decision Nov 19, #783). An exception names its file, so it moves
  with code that moves (#768).
- The nightly scan lists, for each reviewed exception, how many findings it hid and where (rule, file, line). Its
  first listing showed exceptions left behind by the #620 moves; they now name the files the code is in, and the five
  that covered nothing are gone (#853, #854, #855). A made-up stand-in key in a test is listed in `.gitleaksignore`
  with its reason (#855).
- `public/js/data.js` (the app's data layer) was unscanned until Nov 20: a variable named `using` (a keyword in newer
  JavaScript) made Semgrep's parser give up on the file. It was renamed, a test keeps any scanned file from using that
  name, and the scan log now says why Semgrep couldn't check a file (#867, #870). Its 10 new findings are of kinds
  already reviewed (CHANGELOG 2026-11-20).

## Open

- **Low, deferred:** #1111 automatic lockout and Unlock, #1113 App Check with Turnstile (#512 closed Nov 26). (#558,
  the Google Cloud owner steps, closed Nov 22.)
- Deleting the two disabled accounts' leftovers around Nov 29 (#940, see above). Browser error reporting deferred to #921 (medium).
- Nov 22 scan: sign-in still allowed from a leftover PR preview domain (medium finding, #558 resolution).
- **Medium:** #381 HIPAA-ready MetabolicHQ, deferred with SOC 2 (owner, Nov 22; see [HIPAA](hipaa.md)).
- **Gaps written into the SSP as open risks** (no issues yet): production deploys use a long-lived JSON service
  account key (staging is keyless); Cloud Storage files aren't in either backup layer; secret rotation dates aren't
  recorded (#638 resolution).
- (Done Nov 20: the nightly review's twelve fixes plus a 13th, each with a full end-to-end run, #816, #817–#830.)
- **System Security Plan** (#638, done Nov 20): in Google Drive, with the open risks list; see
  [System documentation](system-documentation.md).

## Related

[Engineering rules](../rules/engineering-rules.md) · [Research and privacy](research-and-privacy.md)
