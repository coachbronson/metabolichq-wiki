---
title: Engineering and working rules
summary: How Claude works on the app and site repos — plan first, branches, blast radius, testing, merging, issues, priorities
updated: 2026-11-26
sources: ["mac-app #681", "mac-app #979", "mac-app #983", "mac-app #909", "mac-app #913", "mac-app #919", "mac-app #922", "mac-app #924", "mac-app #932", "mac-app #939", "mac-app #945", "mac-app #946", "mac-app #927", "mac-app #928", notes, mac-app CLAUDE.md, coachbronson-site CLAUDE.md, "mac-app #883", "mac-app #702", "mac-app #704", "mac-app #709", "mac-app #715", "mac-app #617", "coachbronson-site #26", "mac-app #657", "mac-app #660", "mac-app #664", "mac-app #550", "mac-app #671", "mac-app #677", #757, #782, #785, #786, #807, #816, #638, #868, #831, #833, #837, #839, #842, #850, #852, #873, "mac-app #881", #876, #893, #894, #896, #897, #899, #904]
---

# Engineering and working rules

The repos' own `CLAUDE.md` files are authoritative; this page summarizes them plus Bronson's standing preferences.

## Before doing anything

- **Tell him the plan first and wait for his go-ahead** before building or changing things.
- **Read this wiki's `index.md` first** in every session; both repos' CLAUDE.md say so, and say not to edit the wiki
  from app or site work (the nightly update picks changes up) (mac-app #617, coachbronson-site #26).
- **Check the live code on GitHub (mac-app) first** before mockups or app work; project copies may be stale.
- **Project the blast radius** of any change before making it — he doesn't want a fix that breaks something else.

## Branches and merging

- A separate branch for **every** app change (he runs several sessions at once). Branch names never start with `e2e`.
- Every PR has a **Blast radius** section: touches, depends on it (grep the whole repo), could break, checked by,
  undo, risk. Since the split, mac-app no longer searches coachbronson-site; the site's check still greps mac-app for
  anything that would tie the two together again (both CLAUDE.md, mac-app #677).
- **One area per PR** (his rule, Nov 16): one app area, the coverage index tool, the end-to-end runner/workflows, the
  portal, the site, or docs and rules. Different areas go in separate PRs unless one doesn't work without the other;
  then the PR names the areas and why. Each PR carries its own change-log entry and says which area it touches
  (mac-app CLAUDE.md, #664). Since Nov 22 that entry is its own file, `changelog/YYYY-MM/YYYY-MM-DD-<short-name>.md`,
  never `CHANGELOG.md` (now only an index) or the frozen month files, so two PRs never edit the same file; `node
  tools/changelog.mjs` reads a month back (#939).
- **Where code goes: the code map** (his rule, Nov 21): the app, the portal and the server were split out of three big
  files (#620), and new code must not pile back into one. mac-app's `docs/code-map.md` lists every script and what it
  holds; new code goes in the file for its area (`public/js/page-*.js`, `admin/portal-*.js`, `functions/fn-*.js`), a
  new area gets a new file, and the main files (`app.js`, `portal.js`) keep only the shared shell under size limits
  that only go down. `functions/index.js` only re-exports. **Keeping the map current is part of every PR**: a new,
  renamed or removed file changes its row, moved code updates both files' rows, and a shrunk main file lowers its
  limit. A component test (`test/codemap.test.mjs`) fails the PR when the map and the repo disagree. The map lives
  only in mac-app, so it can't go stale in two places (mac-app CLAUDE.md, #883).
- **MetabolicHQ is self-contained** (his call, Nov 16): nothing in mac-app links to, calls or shares a service,
  secret, key, account or data with Coach Bronson's own site (mac-app CLAUDE.md, #677).
- **Low risk** merges once tests pass, without waiting for his review. **Medium/high** waits for his OK.
- High = saved data/migrations, security rules, sign-in/sign-up, payments/Stripe, permissions/IAM/Google Cloud
  settings, keys, secrets, anything affecting every space, anything hard to undo. Try Cloud changes on staging first.
- Claude may start GitHub Actions workflows on mac-app itself — don't ask him to.
- **Releases go through staging first** (his rule, Nov 24, with the gate on): a merge deploys to staging, the smoke
  tests run there, and the change waits until it's promoted: low risk within 15 minutes of passing, medium and high
  24 hours after, each on its own clock, in merge order, or sooner with Promote now / Hold in Releases. The risk is
  the PR's "Risk:" line; none counts as high. Say "merged; on staging", not "live". Urgent fixes: label `incident`,
  the owner promotes after the smoke tests (mac-app CLAUDE.md, #979, #681). Details:
  [Versions](../metabolichq/versions.md#after-beta-575-done-nov-25).

## Testing levels

| Level | When |
|---|---|
| Component (`npm test`, ~4 min) | Every PR; required to merge. Screen changes also get a quick offline look. |
| Area end-to-end | A change to how a feature works; before merge if it touches saved data or server code |
| Full end-to-end (~20–25 min) | Nightly, before a major version, before cross-cutting changes |
| None | Wording, styling, Help or change-log edits |

**What "end-to-end" means** (notes, Nov 16, 2026): every function, button, field entry and display gets tested —
not just the main journeys. Each step checks there's no error pop-up or console error, and that what changed actually
saved and shows. To make that checkable, the app keeps an index of every function, button, field and display, updated
every time one is added or removed, and a test fails when something in the index has no end-to-end coverage. (Came out
of a card-level **Skip** on the workout screen crashing with "Cannot read properties of null (reading 'original')"
on Nov 16, 2026: no journey ever tapped it.)

- The **coverage index** `ops/ui-index.json` is generated by `node tools/ui-index.mjs`; regenerate and commit it in
  any PR that adds, removes or renames a button, field, link, screen section or server call, or changes a journey.
  **Known gaps** `ops/ui-gaps.json` only shrinks: something new ships with the journey step that tests it. How-to
  video scripts don't count as coverage (mac-app CLAUDE.md, #657).
- Since Nov 19 the index files each element under the function that really holds it; 330 gaps were renamed and the
  list went from 1,499 to 1,503, a one-time addition the owner OK'd (#757, #786).
- Since Nov 21 each **server call** counts as tested only through the control or screen that really triggers it
  (`tools/ui-calls.mjs`; `node tools/ui-index.mjs --why <name>` shows why) (#785, PR #873, with the owner's OK). The
  calls that had only looked tested got journey steps the same day: **305 of 320** server calls are tested (was 140
  of 321 under the old, looser matching). The 15 left: 13 functions nothing calls, kept until a **Dec 19, 2026
  review** with a tripwire (`apiUsage` logs any use; Actions → Function logs → match `unused-api-called`; owner's
  call, #876, #893), plus `accessLog` (#876) and `mfaFinish`, authenticator-app setup, to be tested on staging (#877)
  (#785 comments, CHANGELOG 2026-11-21).
- The index tool now reads templates the way JavaScript does (strings, comments, regular expressions, nested
  templates), checked against a real parser; that took 29 gaps off the list (1,503 → 1,475 with #845's bio step;
  #842, #845, #620).
- **A wrong test result is never a pass** (his rule, Nov 16): any false positive or false negative blocks (not
  treated or reported as passed, not merged on) until it's explained or fixed, written on the issue or PR. The
  end-to-end run now fails when any journey fails or a bug is recorded (it used to show green, #660). "Looks external"
  counts only once you've seen what the outside page did. The coverage index fails on any unsure reading (mac-app
  CLAUDE.md, #657, #660, #664).

- The end-to-end run can't check production hosts that are local test servers there (our other sites, the Firebase
  emulators). Enforcing the Content-Security-Policy showed two such gaps, so a change that depends on outside hosts
  is also checked in code and in a browser (mac-app #702, #704, #550).

- The CI functions emulator keeps one process per function ever called; after each journey the runner logs the count
  and free memory, and over 25 it reloads the functions so idle processes stop. Late-run deletes had been failing
  for lack of memory (#896, #897).
- A run doesn't start across midnight UTC: when 00:00 UTC is less than 55 minutes away (15 for one area), the
  workflow waits until 00:01 UTC, since journeys read "today" all through the run. The nightly run never waits
  (#899, #904). Steps read a confirmation toast only after waiting for it (#894).
- Runs finishing together no longer turn red over the shared `e2e-results` branch: the report push retries up to
  five times (#782). After a reload, the runner waits for the app's first page before tapping a menu (#807).
- A portal page in a journey counts as open only once its own content shows, not just its name in the side menu;
  the old wait hid a too-wide table in most runs (#850, #852).
- False negative explained and fixed (Nov 20): Stripe showed a US$600 package in Canadian dollars because the test
  machine was in Canada; the step now accepts a correctly converted price (#837, #839).
- Functions deploys on main go one at a time (only the newest waiting one runs) and retry once after 60 s on Cloud
  Functions' change quota as well as Cloud Run's read quota; staging retries the same way. Twelve merges in an hour on
  Nov 20 had made two deploys fail (#831, #833).

Load tests only at ≥250 regular users or before a big cross-area feature; staging only (#359). The load tests'
**restore** scenario (staging only) backs up all of staging, restores it and checks nothing is missing; pass rules:
backup under 30 minutes, full restore under 60 (#926).

## Type checking

The component tests include a type check (`test/typecheck.test.mjs`, `tools/typecheck.mjs`): TypeScript reads the
plain JavaScript of the server, app, portal, Monitor and site, with no build step. **Since Nov 22 no file has a type
error**, and `ops/type-baseline.json` only goes down, so any new type error fails the tests. Fix the code or add a
JSDoc type, never raise a count. Browser declarations: `tools/types/web.d.ts`; names scripts put on `window` are
declared automatically (mac-app CLAUDE.md, #909, #911–#913). It found one dead line (invite.js) and no other real
bugs (#913).

## Release notes

Every PR with a change a client or coach can see adds a plain one- or two-sentence note at the top of
`public/js/releasenotes.js` (date, who: clients / coaches / internal, kind: New / Improved / Fixed, version when it
bumps `APP_VERSION`), then rebuilds metabolichq.app/releases with `node tools/releases-page.mjs`. Written like Help:
what changed for the reader, no issue numbers or code. No note for changes nobody sees. A version bump without a
note, or an out-of-date page, fails `test/releasenotes.test.mjs` (his rule, Nov 22; mac-app CLAUDE.md, #919, #922).

## Scheduled jobs

A new timed job is a **scheduled Cloud Function** (`onSchedule`, `timeZone: 'America/New_York'`, in its area's
`fn-*.js`, logic in its own module). A job that needs a full build machine stays a workflow, started at its time from
Google Cloud, never by a `schedule:` line; `test/schedules.test.mjs` fails on any `schedule:` (his rule, Nov 22,
after GitHub ran them 6–9 hours late, #927; mac-app CLAUDE.md, #928, #932). See
[Architecture](../metabolichq/architecture.md#deploys-backups-and-jobs).

Since Nov 24 the same goes for **Claude's work**: every recurring Claude job and one-time reminder runs from
MetabolicHQ's Google Cloud scheduler (the "Claude job" workflow and `functions/reminders.json`), not Claude scheduled
tasks (his rule, #983). mac-app's jobs leave coachbronson-site out; the site has its own scheduler (#983).

## Nightly review (CodeRabbit + Claude)

Reviews **once a night** (~12:06 AM ET) everything merged since the last review, in one PR. **Two reviewers** (owner's
call, Nov 20): CodeRabbit, plus Claude's own review of the same diff on the same PR, one report for both, titles
starting `CodeRabbit:` or `Claude:`. Since Nov 24 Google Cloud starts the pass as a "Claude job" run (`nightlyReviewStart`,
#983, #986; previously one ongoing Claude session with its own wake-up; mac-app CLAUDE.md still describes that, to be
updated under #983). coachbronson-site's review now runs from the site's own scheduler (owner's decision, Nov 24, #983;
previously part of this pass). It checks this wiki without changing it. A quiet night in mac-app skips only mac-app's steps
(mac-app CLAUDE.md, #838, #881). Claude fixes easy low-risk findings in one PR; anything risky or unclear becomes a
question in the nightly report.
- Questions the owner OKs are grouped into issues and fixed one PR per fix: confirmed against the code first, a test
  that fails before the fix, a Blast radius section, and a link to the review comment (#751–#757, #816). For #816
  (Nov 20, twelve fixes) each PR also gets a full end-to-end run before merging (#816).

## System documentation: keep it current

Any significant change to security, components, operations, configuration, resources or the change process
updates the matching document in Google Drive › Documentation (see [System documentation](../metabolichq/system-documentation.md))
as part of the same work: SSP (security, roles, data types, outside services, secrets, risks), Configuration
Management Plan (config-controlled items and settings), Change Management Plan (approval, testing, staging, release,
rollback), Resource Management Plan (resources, services, plans, licenses, secrets), O&M Plan (monitoring, alerts,
jobs, backups, incidents, support), Detailed System Design (components, data flows, hosts, ports, interconnections,
diagrams), Engineer Onboarding Guide (code layout, setup, how to run and test, testing levels), Incident Response
Procedure (incident steps, with the O&M Plan) (#907, #924). Each PR's Blast radius has a **Docs to update** line. If the Drive connectors aren't in the session, it
goes under "What's left" on the issue. (Owner's rule, Nov 20; mac-app CLAUDE.md, #638, PR #868.)

## Status updates

Every status update (chat messages while waiting on a run or PR, progress notes on issues and PRs) starts with the
current time in Eastern from the machine (e.g. **8:41 PM Eastern, Tue Nov 17**) and gives the next check as a clock
time, not "in 30 minutes" (his rule, Nov 17; mac-app CLAUDE.md, #715).

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
- **Outside services** (Google Cloud, Firestore, Stripe, etc.): reach them through GitHub Actions workflows (repo
  secrets, keyless sign-in on staging) and MCP connectors. A small workflow just to get access (e.g. a read-only
  report) is the normal route; propose it as soon as a direct call fails. A credential saved in the session is a last
  resort. gcloud failing with CREDENTIALS_MISSING in a session is expected, not a broken key; don't retry it or ask
  him to look in a console. The read-only workflow is its own PR (workflows area, medium risk), built like
  `live-config.yml`: Run workflow only, read-only, a failed read fails the run (notes 2026-11-17; now in mac-app
  CLAUDE.md, #945; mac-app #550, #671, #943).
- **Try before saying it can't be done** (his rule, Nov 21; reaffirmed Nov 26): always actually try to connect to a
  repo, connector or other resource, and try the exact action needed (e.g. starting a workflow, not only a related
  read), before saying it can't be reached or done. A first refusal gets one more try. Order of routes: **GitHub
  Actions workflows first, then his cloud functions directly, then MCP servers and connectors, then session-level
  connections or credentials only as a last resort** (notes 2026-11-26: a blocked read of a repo's Actions variables was taken to mean deploys couldn't be
  started, when starting the deploy workflow worked).
- Auto-updates email him with release notes and wait for approval.
- Don't bring up FatSecret (e.g. for barcode lookups) unless he raises it.
- Test sign-ups use "+" alias emails; remind him when a fresh one is needed.
- Claude Code's built-in privacy plugin is off in both repos (his call, Nov 17): it refused shell commands on files
  holding his email address. Its job was keeping that address out of web requests (mac-app #709,
  coachbronson-site #39).

## Related

[Architecture](../metabolichq/architecture.md) · [Writing and brand rules](writing-and-brand-rules.md)
