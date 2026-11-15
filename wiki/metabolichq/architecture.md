---
title: Architecture and infrastructure
summary: Repos, Firebase/Google Cloud projects, domains, data model, email, services, backups and deploys
updated: 2026-11-14
sources: [mac-app README, mac-app CLAUDE.md, coachbronson-site CLAUDE.md, CHANGELOG, notes]
---

# Architecture and infrastructure

## Repositories

| Repo | What |
|---|---|
| `coachbronson/mac-app` | The app (`public/`), coach portal (`admin/`), MetHQ Monitor (`admin/monitor/`), metabolichq.app site (`site/`), Cloud Functions (`functions/`), scripts, tests, end-to-end journeys (`e2e/`), load tests (`load/`). |
| `coachbronson/coachbronson-site` | coachbronson.com: site, blog, newsletter, form embeds, site admin. Deploys into the **same** Google Cloud project. |
| `coachbronson/metabolichq-wiki` | This wiki. |

Bronson keeps no local copy of the repos; work happens in cloud Claude sessions.

## Google Cloud / Firebase

- Production project: **`masters-collective-app`** (Blaze plan). Staging: **`metabolichq-staging`** (testing, load
  tests; try Google Cloud setting changes there first).
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
| `masterscollective.app` | Owned (Squarespace); DNS forwarding; was the original app domain |
| `coachbronson.web.app` | New coachbronson.com site, until the domain moves (see [coachbronson.com](../business/coachbronson-site.md)) |

## Data model (short)

Spaces: one per coach business; MPT is `mpt`. `accounts/{uid}` says which space a person is in.
Shared platform data (group program `programDays/{date}_all`, exercises, videos, search cache) sits at the top level;
everything else lives under `spaces/{sid}/…` (users, logs, check-ins, biometrics, threads, signals, feed…).
Full layout: mac-app `README.md`. Security rules: `firestore.rules`, `storage.rules` (tested in `test/rules.test.mjs`).

## Email

- App email sends through **Resend** from `metabolichq.app` (verified Nov 2026). Each space sends as its program
  abbreviation (MPT → `mpt@metabolichq.app`). Resend stays on the Free plan for now.
- Earlier app emails went through his Zapier + Gmail setup.
- Demo/test account emails he sends himself go from his coachbronson.com Google account.
- Keep his mailing address out of email footers and anything public unless legally required (then city and state).

## Third-party services (Nov 2026 plan)

Zapier Pro, Resend Free, FatSecret Premier, USDA API, Daily (video, pay-as-you-go, with Daily transcription), Stripe
(standard rates; Connect Standard for coaches), Google Workspace Business Standard (1 seat), Gemini on Vertex AI
(MPT Coach), Cloudflare Turnstile (bot protection; App Check uses it, not reCAPTCHA), CodeRabbit, Dependabot.
Circle is **not** part of the app.

## Deploys, backups and jobs

- Push to `main` → tests → deploy (`.github/workflows/deploy.yml`). Staging has its own deploy workflow.
- Backups: Firebase daily Firestore backups (14 weeks) + nightly JSON backup in GitHub Actions (30 days, ~3:15 AM ET).
  Restore workflow can restore everything, one person or a path; dry run first.
- Nightly: CodeRabbit review pass (~12:06 AM ET), full end-to-end run (~2:13 AM ET, emails only when something needs
  action), 7 AM workout digest.
- Any auto-update to servers/software must email him with release notes and wait for approval. OS security patches
  can install automatically.

## Related

[Engineering rules](../rules/engineering-rules.md) · [Coach portal](coach-portal.md) · [MetHQ Monitor](methq-monitor.md)
