---
title: Engineering and working rules
summary: How Claude works on the app and site repos — plan first, branches, blast radius, testing, merging, issues, priorities
updated: 2026-11-14
sources: [notes, mac-app CLAUDE.md, coachbronson-site CLAUDE.md]
---

# Engineering and working rules

The repos' own `CLAUDE.md` files are authoritative; this page summarizes them plus Bronson's standing preferences.

## Before doing anything

- **Tell him the plan first and wait for his go-ahead** before building or changing things.
- **Check the live code on GitHub (mac-app) first** before mockups or app work; project copies may be stale.
- **Project the blast radius** of any change before making it — he doesn't want a fix that breaks something else.

## Branches and merging

- A separate branch for **every** app change (he runs several sessions at once). Branch names never start with `e2e`.
- Every PR has a **Blast radius** section: touches, depends on it (grep both repos — they share the Google Cloud
  project), could break, checked by, undo, risk.
- **Low risk** merges once tests pass, without waiting for his review. **Medium/high** waits for his OK.
- High = saved data/migrations, security rules, sign-in/sign-up, payments/Stripe, permissions/IAM/Google Cloud
  settings, keys, secrets, anything affecting every space, anything hard to undo. Try Cloud changes on staging first.
- Claude may start GitHub Actions workflows on mac-app itself — don't ask him to.

## Testing levels

| Level | When |
|---|---|
| Component (`npm test`, ~4 min) | Every PR; required to merge. Screen changes also get a quick offline look. |
| Area end-to-end | A change to how a feature works; before merge if it touches saved data or server code |
| Full end-to-end (~20–25 min) | Nightly, before a major version, before cross-cutting changes |
| None | Wording, styling, Help or change-log edits |

Load tests only at ≥250 regular users or before a big cross-area feature; staging only (#359).

## CodeRabbit

Reviews **once a night** (~12:06 AM ET) everything merged since the last review. Claude fixes easy low-risk findings
in one PR; anything risky or unclear becomes a question in the nightly report.

## Closing issues

Post a **"How this was resolved"** comment: what changed (PR link), what differed from the plan and why, extras in the
PR, checks run, what's left (link a follow-up issue). Write failures onto the issue as they happen.

## Backlog priorities

Every backlog issue gets exactly one priority label.
- **Critical**: real people hurt now, no workaround — data loss, privacy/security exposure, money wrong, sign-in or app
  down for a whole space, AI coach safety message or coach flag not firing. Tell him in chat right away.
- **High**: main task broken for some users with no good workaround; blocks a launch or partner commitment; legal
  wording; bad errors in client emails/notifications.
- **Medium**: bugs with workarounds, roadmap features, approved client suggestions, performance, portal workflow.
- **Low**: polish, wording, small layout, unroadmapped ideas, internal cleanup.
- Between two levels, pick the lower and say why. Approved Inbox suggestions default to medium. Add `needs-decision`
  when it depends on his call.

## Other standing rules

- Google Cloud steps he must do: give `gcloud` commands for Cloud Shell.
- Auto-updates email him with release notes and wait for approval.
- Don't bring up FatSecret (e.g. for barcode lookups) unless he raises it.
- Test sign-ups use "+" alias emails; remind him when a fresh one is needed.

## Related

[Architecture](../metabolichq/architecture.md) · [Writing and brand rules](writing-and-brand-rules.md)
