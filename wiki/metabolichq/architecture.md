---
title: Architecture and infrastructure
summary: Repos, Firebase/Google Cloud projects, domains, data model, email, services, backups and deploys
updated: 2026-11-21
sources: [mac-app README, mac-app CLAUDE.md, coachbronson-site CLAUDE.md, CHANGELOG, notes, "#611", "#626", "#514", "coachbronson-site #27", "#567", "#667", "#668", "#672", "#676", "#684", "#695", "#696", "#620", "#724–#739", mac-app .firebaserc, #758, #762–#779, #780, #791, #794, #795, #809, "#815–#849", #829, #831, #833, #874, #878, functions/mail.js, .github/workflows/backup.yml, "#638"]
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

- **109 Cloud Functions** (`ops/function-endpoints.json`), each defined in an area file under `functions/` (`fn-<area>.js`, plus `base.js` for
  shared setup and `members.js` for the membership core). `functions/index.js` only re-exports them, so names and
  addresses are unchanged (split Nov 18–19, #718, #724–#739, #762–#779; CHANGELOG 2026-11-18, 2026-11-19). The 108th
  is `wearablesForgetWork` (#791); the 109th, `mailStuckWatch` (#829).
- `ops/function-names.json` and `ops/function-endpoints.json` record every function; each PR loads the server the way
  the deploy does and checks name, trigger, account, region, secrets, limits and schedule (#718, #758).
- The client app is split the same way (done Nov 20): 13 `public/js/page-*.js` files load in order after `app.js`,
  which keeps the app shell, and `public/js/start.js`, loaded last, starts the app (#815–#849). The coach portal's
  split started Nov 21: `admin/portal-platform.js`, with `admin/portal-start.js` loaded last (#874, #878). See
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
Circle is **not** part of the app.

## Deploys, backups and jobs

- Push to `main` → tests → deploy (`.github/workflows/deploy.yml`). Staging has its own deploy workflow.
- Deploy CLI `tools/firebase-cli` is on firebase-tools ^15; the test emulators (root `package.json`) stay pinned at
  14.23.0 until a 15.x release fixes their slowdown (#567 closed, #592, #667).
- A functions deploy that hits Cloud Run's per-minute read quota or Cloud Functions' per-minute change quota
  (HTTP 429) waits 60 s and retries once, on production and staging; any other failure fails at once (#668, #831,
  #833). Functions deploys on main run one at a time; if several wait, only the newest runs (#833).
- Backups: Firebase daily Firestore backups (14 weeks) + nightly JSON backup in GitHub Actions (30 days; cron 07:17 UTC, so 2:17 AM ET in winter, 3:17 AM in summer;
  `.github/workflows/backup.yml`). Cloud Storage files aren't in either backup layer (an open risk in the SSP, #638).
  Restore workflow can restore everything, one person or a path; dry run first.
- Nightly: review pass, CodeRabbit + Claude, in one ongoing Claude session (~12:06 AM ET; see
  [Engineering rules](../rules/engineering-rules.md#nightly-review-coderabbit--claude)), full end-to-end run (~2:13 AM ET, emails only when something needs
  action), 7 AM workout digest.
- Security jobs: **securityWatch** (every 5 min), **securityLogWatch** (every minute), **geoDbRefresh** (weekly
  country file) (#514; see [Security](security.md)).
- Daily retry jobs: **coachPayWork** also retries refused coach-site refunds and renewals (#794, #795);
  **wearablesForgetWork** (5:37 AM ET) finishes wearables deletions (#791). Both email a security alert after three
  failed tries.
- Any auto-update to servers/software must email him with release notes and wait for approval. OS security patches
  can install automatically.

## Related

[Engineering rules](../rules/engineering-rules.md) · [Coach portal](coach-portal.md) · [MetHQ Monitor](methq-monitor.md)
