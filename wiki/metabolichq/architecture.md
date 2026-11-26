---
title: Architecture and infrastructure
summary: Repos, Firebase/Google Cloud projects, domains, data model, email, services, backups and deploys
updated: 2026-11-26
sources: ["#410", "#575", "#603", "#681", "#1022", "#1024", "#996", "#999", "#1000", "#1026", "#1040", "#1042", "#1051", "#1059", "#1064", "#1072", "#960", "#967", "#971", "#975", "#983", "#984", "#986", "#989", "#992", ops/function-endpoints.json, functions/reminders.json, "#950", "#952", "#953", "#955", "#956", "#958", "#962", "#965", "#967", "#915", "#921", "#926", "#928", "#930–#938", "#939", "#943", "#946", "#321", mac-app README, mac-app CLAUDE.md, coachbronson-site CLAUDE.md, CHANGELOG, notes, "#611", "#626", "#514", "coachbronson-site #27", "#567", "#667", "#668", "#672", "#676", "#684", "#695", "#696", "#620", "#724–#739", mac-app .firebaserc, #758, #762–#779, #780, #791, #794, #795, #809, "#815–#849", #829, #831, #833, #874, #878, #882, #893, #895, #898, #900–#903, functions/mail.js, .github/workflows/backup.yml, "#638"]
---

# Architecture and infrastructure

## Repositories

| Repo | What |
|---|---|
| `coachbronson/mac-app` | The app (`public/`), coach portal (`admin/`), MetHQ Monitor (`admin/monitor/`), metabolichq.app site (`site/`), Cloud Functions (`functions/`), scripts, tests, end-to-end journeys (`e2e/`), load tests (`load/`). |
| `coachbronson/coachbronson-site` | coachbronson.com: site, blog, newsletter, form embeds, site admin. Deploys into its **own** Google Cloud project, `coachbronson-site` (coachbronson-site #29). (Previously into MetabolicHQ's project.) |
| `coachbronson/metabolichq-wiki` | This wiki. |

Bronson keeps no local copy of the repos; work happens in cloud Claude sessions.

## Google Cloud / Firebase

- Production project: **`masters-collective-app`** (Blaze plan). It keeps this name and ID: no move or rename
  (owner, Nov 18, #620; see [Acquisition readiness](acquisition-readiness.md)). Staging: **`metabolichq-staging`** (testing, load
  tests; try Google Cloud setting changes there first). Staging workflows sign in as their own staging-only account
  through GitHub keyless sign-in; the production deploy key no longer reaches staging (#626).
- **Staging as a production mirror** (#681 build steps 1–3, done Nov 23): staging never sends email but keeps a full
  copy of each one (`stagingMail`), shown in the portal's **Staging inbox** (#950, #955; emails that take the Zapier route, which is
  every staging email, are read back from their `mailOutbox` document since #967, Nov 24); MPT Coach asks the real AI (staging's own bill), food search uses real
  USDA (its own key, `USDA_STAGING_API_KEY`) and barcodes the real Open Food Facts, except while load-test data is
  seeded (`ops/staging.loadTest`) (#950, #952, #965). Daily calls, Resend, Zapier, GitHub and Turnstile stay stand-ins.
  The deploy's sign-in settings steps now run for staging too, with authenticator-app two-step only, no text codes
  (#952). Workflows **Staging sign-in link** (a one-time link on the run page; #953, #954) and **Staging demo data**
  (seed, reset, status, add-client: fictional spaces Smitty Fitness and Peak Kettlebell, a year of history, plus MPT,
  10 demo clients each; #956, #957, #963), reset every Monday at 4:17 AM Eastern by `stagingDemoStart` (#958); the
  portal's staging tools live in `admin/portal-staging.js` (#959, #961). Each seed or reset also makes five clients
  with **real Stripe test-mode billing** (owner's choice, #960): MPT clients mid-trial, lapsed (past due, through a
  Stripe test clock) and canceled, and in Smitty Fitness a client on a paid package and one who used a coach-made
  coupon. They are their own kind of test client (`bill-…`, `billingDemo`), every Stripe object is tagged
  `metadata.demo = 'staging'`, and a run fails if a client's stored state doesn't match Stripe. Staging's deploy makes
  a second test-mode webhook for coaches' connected accounts (`stripeConnectWebhook`). MPT's Finances still leaves
  test-mode subscriptions out (#982, #985).
- **A preview of each PR** (#962): a PR that changes the app, portal or site gets a Firebase Hosting preview channel
  on staging, `pr-<number>`, built by `deploy.yml` target `preview` (screens only; server and rules changes aren't in
  it), with one PR comment holding the three links; expires after 7 days, deleted on close; not for forks or
  Dependabot. Sign in with Staging sign-in link → preview.
- coachbronson-site has its own project, `coachbronson-site` (coachbronson-site #29). Its leftovers in
  `masters-collective-app` (functions, secrets, data, sign-in and API-key domains) were removed by
  `scripts/remove-coachbronson-site.sh` (#676), and the old coachbronson.web.app Hosting site by the one-time
  workflow **Delete old site address** on Nov 17 (#695, #696). The one thing still shared: the site sends email
  through MetabolicHQ's Resend key until July 2027 (see [coachbronson.com](../business/coachbronson-site.md)).
  MetabolicHQ has its own Turnstile widget since the shared one was deleted (#684).
- Firebase Hosting, Authentication, Cloud Firestore, Cloud Functions, Storage.
- History: started as a Google Apps Script + "Workout App" Google Sheet; moved to Firebase **2026-10-30**. The sheet is
  no longer used.
- For steps Bronson must do himself in Google Cloud, give him `gcloud` commands for Cloud Shell, not console clicks.

## Domains

| Address | What |
|---|---|
| `metabolichq.app` | Landing page for coaches (+ `/mpt`, `/blog`, research and trust pages) |
| `app.metabolichq.app` | The app (clients and light coach tools) |
| `admin.metabolichq.app` | Coach portal (desktop, ≥1024 px) |
| `admin.metabolichq.app/monitor/` | MetHQ Monitor (phone-friendly ops view) |
| `masters-collective-app.web.app`, `masters-collective-admin.web.app`, `metabolichq-home.web.app` | Firebase default addresses of the app, coach portal and landing site; staging's are `metabolichq-staging`, `metabolichq-staging-admin`, `metabolichq-staging-home` (.web.app) (mac-app `.firebaserc`) |
| `masterscollective.app` | Owned (Squarespace); DNS forwarding; was the original app domain |
| `coachbronson-site.web.app` | Coach Bronson's own site, in its **own** Google Cloud project `coachbronson-site`; MetabolicHQ doesn't link to, call or share anything with it (mac-app CLAUDE.md, #672–#677; see [coachbronson.com](../business/coachbronson-site.md)). (Previously coachbronson.web.app in MetabolicHQ's project, linked through `COACHBRONSON_URL`, #611; that variable and its deploy step are gone, #672) |

## Data model (short)

Spaces: one per coach business; MPT is `mpt`. `accounts/{uid}` says which space a person is in.
Shared platform data (group program `programDays/{date}_all`, exercises, videos, search cache) sits at the top level;
everything else lives under `spaces/{sid}/…` (users, logs, check-ins, biometrics, threads, signals, feed…).
Full layout: mac-app `README.md`. Security rules: `firestore.rules`, `storage.rules` (tested in `test/rules.test.mjs`).

## Server code

- **139 Cloud Functions**: 74 callable, 26 HTTPS, 39 scheduled (`ops/function-endpoints.json`, Nov 26). Added Nov 25:
  `driftCheckStart` (#996), `releaseWatch` (#999), `releaseSignal` (#1000), `checkinReminders` (#1026), `coachDigest`
  (#1040), `serviceStatus` and `siteStatus` (#1042), `majorAnnounce` (#1051), `groups` (#1059), `features` and
  `featureWork` (#1064). (Previously 128 and 34 on Nov 25; 121 and 28 on Nov 23.) Each defined in an area file under `functions/` (`fn-<area>.js`, plus `base.js` for
  shared setup and `members.js` for the membership core). `functions/index.js` only re-exports them, so names and
  addresses are unchanged (split Nov 18–19, #718, #724–#739, #762–#779; CHANGELOG 2026-11-18, 2026-11-19). The 108th
  is `wearablesForgetWork` (#791); the 109th, `mailStuckWatch` (#829); the 110th, `apiUsage`, the tripwire that
  logs any use of 13 app functions nothing calls, until a Dec 19 review (#876, #893). Nov 22 added the 10 scheduled
  functions that took over GitHub's timed jobs (#928, see below).
- `ops/function-names.json` and `ops/function-endpoints.json` record every function; each PR loads the server the way
  the deploy does and checks name, trigger, account, region, secrets, limits and schedule (#718, #758).
- The client app is split the same way (done Nov 20): 13 `public/js/page-*.js` files load in order after `app.js`,
  which keeps the app shell, and `public/js/start.js`, loaded last, starts the app (#815–#849). The coach portal's
  split finished Nov 21: seven `admin/portal-*.js` files, one per menu group, with `admin/portal.js` kept as the
  shell (746 lines) and `admin/portal-start.js` loaded last (#874, #878, #882, #895, #898, #900–#903). mac-app's
  `docs/code-map.md` lists every script (#883). See
  [Acquisition readiness](acquisition-readiness.md#splitting-the-big-files-5).

## Email

- App email sends through **Resend** from `metabolichq.app` (verified Nov 2026). Each space sends as its program
  abbreviation (MPT → `mpt@metabolichq.app`). Resend stays on the Free plan for now.
- The other route is his Zapier + Gmail workflow "mpt-send-email": the app queues each message in `mailOutbox` and
  the workflow picks it up and reports it sent. MPT's own emails go that way until switched to Resend in the portal
  (Maintenance → Email sending); sign-in links and platform emails always go by Resend once it's set up
  (`functions/mail.js`).
- Only a picked-up message can be marked sent (#827). An hourly check, `mailStuckWatch`, emails him once (through
  Resend) about any message picked up over an hour ago and never reported sent; the app never re-sends it on its own
  (owner's choice, #816, #829).
- Demo/test account emails he sends himself go from his coachbronson.com Google account.
- Keep his mailing address out of email footers and anything public unless legally required (then city and state).

## Third-party services (Nov 2026 plan)

Zapier Pro, Resend Free, FatSecret Premier, USDA API, Daily (video, pay-as-you-go, with Daily transcription), Stripe
(standard rates; Connect Standard for coaches), Google Workspace Business Standard (1 seat), Gemini on Vertex AI
(MPT Coach), Cloudflare Turnstile (bot protection; App Check uses it, not reCAPTCHA), CodeRabbit, Dependabot.
Circle is **not** part of the app. Status page: **Better Stack** (free plan, owner's account) at
`status.metabolichq.app`, checking the app, portal and site every 3 minutes (#321).

## Deploys, backups and jobs

- **Staging gate on since Nov 24** (`RELEASE_GATE` = `on`): a push to `main` runs the tests, then deploys to
  staging and its smoke tests; production gets only a commit that **Promote** passes in. See
  [Versions](versions.md#after-beta-575-done-nov-25) (#681, #971, #975, #979).
- Push to `main` → tests → deploy (`.github/workflows/deploy.yml`). Since Nov 23 "Deploy to staging" runs the same
  `deploy.yml` with `target: staging` (only the project, sign-in and secrets differ; a test fails if they drift).
  Production now also deploys the Firestore indexes and Storage rules, without `--force`; staging also deploys
  metabolichq.app's site (metabolichq-staging-home.web.app) (#681 build step 1, #946). (Previously staging had its
  own copy of the steps, which fell behind and failed for about 5 days, #931.)
- **Live config report** (Run workflow only, read-only): compares production's Firestore indexes and overrides and
  live Firestore and Storage rules with the repo; on Nov 22–23 they matched (#943, #944, #681).
- Package names: `metabolichq` and `metabolichq-functions` (previously masters-collective-app and mpt-functions);
  the Google Cloud project keeps its name (#915).
- Deploy CLI `tools/firebase-cli` is on firebase-tools ^15; the test emulators (root `package.json`) stay pinned at
  14.23.0 until a 15.x release fixes their slowdown (#567 closed, #592, #667).
- A functions deploy that hits Cloud Run's per-minute read quota or Cloud Functions' per-minute change quota
  (HTTP 429) waits 60 s and retries once, on production and staging; any other failure fails at once (#668, #831,
  #833). Functions deploys on main run one at a time; if several wait, only the newest runs (#833).
- Backups: Firebase daily Firestore backups (14 weeks) + the nightly JSON backup, the scheduled function
  **`nightlyBackup`** (2:17 AM Eastern), which streams `mac-backup-YYYY-MM-DD.json.gz` into the private bucket
  `masters-collective-app-backups` (us-central1, public access prevented, files deleted after 30 days; staging:
  `metabolichq-staging-backups`; setup and undo in `docs/backup-bucket.md`) (#928 step 5, #937). (Previously a
  GitHub workflow at 07:17 UTC with the file kept as a 30-day download.) Restore takes a date and reads the bucket;
  it now reads and writes in parallel (`RESTORE_PARALLEL` 16) and a dry run lists documents that differ (#926). Cloud Storage files aren't in either backup layer (an open risk in the SSP, #638).
  Restore workflow can restore everything, one person or a path; dry run first.
- **Timed jobs run in Google Cloud** (owner's rule, Nov 22): GitHub started scheduled workflows 6–9 hours late from
  Nov 15 (#927), so every one moved (#928, steps 1–6 done Nov 22). Scheduled functions (Eastern time):
  `nightlyBackup` 2:17, `transcriptPull` 3:20, `purgeArchived` 3:41, `partnerBilling` 4:17, `morningDigest` 7:03.
  Jobs that need a full build machine stay GitHub workflows, started on time by starter functions with the
  fine-grained token `WORKFLOW_START_TOKEN` (mac-app only, Actions): `nightlyE2EStart` 2:13, `securityScanStart`
  2:47, `securitySettingsStart` 4:23, `hqBlogStart` 6:33, `wearablesStart` every hour at :23, `stagingDemoStart` Mondays 4:17 (#958), `releasePromote` every 15 minutes (#975), `driftCheckStart` 3:07 (#996). Added
  Nov 25 as scheduled functions: `releaseWatch` every 5 minutes (#999), `checkinReminders` every 15 minutes (#1026),
  `coachDigest` Mondays 8:17 (#1040), `featureWork` 8:23 (#1064). A start or job that
  fails saves a security alert for the owner; starters give up after 15 seconds (nightly review Nov 23, #948). Each
  moved workflow keeps "Run workflow"; `test/schedules.test.mjs` fails on any new `schedule:` (#930–#938).
- **Claude jobs and reminders run from Google Cloud too** (owner's rule, Nov 24, #983): no Claude scheduled tasks.
  The workflow **Claude job** (`claude-run.yml`, Run workflow only) runs Claude Code headless on one job's
  instructions in `ops/claude-jobs/<job>.md`, signed in with the owner's Claude subscription token and a fine-grained
  GitHub token (mac-app and this wiki), and emails the job's report to the owner (#984). Starts (Eastern):
  `nightlyReviewStart` 12:06 AM, `wikiUpdateStart` 4:41 AM, `hqBlogDraftsStart` 7:10 AM, `helpReviewStart` 7:45 AM
  (#986). One-time reminders are `functions/reminders.json` (add one with a PR); `reminderWork` checks every 15
  minutes, emails each due one once, can start a Claude job (started only once, even if the email is retried), and
  records it in `ops/reminders` (#989, #992). On the list: the Nov 27 9:37 AM Group coaches backfill on production
  (#410, #1072), the Nov 29 key clean-up check (job `key-cleanup`, which
  deletes nothing), the Dec 19 unused-function review (job `unused-functions-review`), the Jan 29 Riverside booking,
  and the Jul 1, 2027 move of coachbronson.com's email off MetabolicHQ's Resend. coachbronson.com's jobs run from its
  own scheduler in its own project (owner's decision, Nov 24, #983; coachbronson-site #41).
- Nightly: review pass, CodeRabbit + Claude, started by `nightlyReviewStart` (~12:06 AM ET; see
  [Engineering rules](../rules/engineering-rules.md#nightly-review-coderabbit--claude)), full end-to-end run (2:13 AM ET, emails only when something needs
  action), 7:03 AM workout digest.
- **Releases signals:** `release-signal.yml` posts each PR and workflow status change to production's
  `releaseSignal`, signed in with the run's GitHub OIDC token (no stored secret); the Releases pages reload when
  `ops/releaseSignal` moves (#1000–#1002, #1070, #1071). See [Versions](versions.md#after-beta-575-done-nov-25).
- Security jobs: **securityWatch** (every 5 min), **securityLogWatch** (every minute), **geoDbRefresh** (weekly
  country file) (#514; see [Security](security.md)).
- Daily retry jobs: **coachPayWork** also retries refused coach-site refunds and renewals (#794, #795);
  **wearablesForgetWork** (5:37 AM ET) finishes wearables deletions (#791). Both email a security alert after three
  failed tries.
- Any auto-update to servers/software must email him with release notes and wait for approval. OS security patches
  can install automatically.

## Related

[Engineering rules](../rules/engineering-rules.md) · [Coach portal](coach-portal.md) · [MetHQ Monitor](methq-monitor.md)
