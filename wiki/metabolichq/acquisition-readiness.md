---
title: Acquisition readiness
summary: How mature MetabolicHQ would look to a buyer (#620), the owner's accepted risks, what's still open, and the code split
updated: 2026-11-23
sources: ["#620", "#381", "#558", "#575", "#907", "#909–#916", "#320", "#321", "#921", "#924", "#926", "#928", "#939", "#940", CHANGELOG 2026-11-18, CHANGELOG 2026-11-19, "#718–#741", CHANGELOG 2026-11-20, CHANGELOG 2026-11-21, #750, #758, #762–#780, #805, #809, "#815–#878", "#882", "#895", "#898", "#900–#905", CHANGELOG 2026-11-22]
---

# Acquisition readiness (#620, high)

- **Goal:** raise MetabolicHQ from beta (about **2 of 5**, "late prototype / early beta", assessed Nov 15) toward
  enterprise-grade, as a large software firm would judge it in a purchase review (#620).
- **Done when:** the assessment is re-run and every area scores at least 3. Team and Business traction are left out
  (accepted risk, owner, Nov 18; #620).

## Owner's decisions (Nov 18)

- **Accepted risk, not part of #620:** the public launch and paying-member track record (§1), and all of §6,
  dependence on one person and IP (contract engineer, license inventory, legal review of AI-written code, unit-cost
  report) (#620).
- **Stripe:** the "Coach Bronson" Stripe account is the only account and won't change (#620).
- **Google Cloud project stays** `masters-collective-app`, same name and ID, no move and no display-name change. It's
  back-end only: sign-in shows the app's own address, and a project transfers to a buyer with its ID unchanged. Added
  instead: write down who owns the project, its organization, billing account and owner access, flagging anything
  held by a personal account rather than BD Solutions LLC (#620). (Previously the plan was a new, neutrally named
  project.)
- **QR-code library:** keep both copies (`public/js/qrcode.js`, `admin/qrcode.js`), because each site loads scripts
  only from itself; a test fails if they ever differ (#620, #718).

## Owner's decisions (Nov 22)

- **Accepted risk, not changing:** project ownership as written in docs/, and the Workspace, Resend and Zapier
  accounts staying where they are rather than moving to BD Solutions LLC (#620).
- **Deferred:** SOC 2 and HIPAA (#381): not on the table now, may come back, no work needed; #381 stays open (#620).
- **One region** (us-central1): a second region or regional disaster recovery isn't needed now (accepted risk, may be
  revisited) (#620).
- **Error alerting:** server errors were already alerted (Google Cloud alerts in `ops/alerts/`, uptime checks,
  performance watch); browser error reporting is deferred to #921 (medium, ops) (#620).
- Order for the rest of §4: incident procedure, then backup timing at 10× data, then the release process (#575) (#620).

## Status by section (Nov 23)

- §2: done or accepted. Package names are `metabolichq` and `metabolichq-functions` (#915); ownership and accounts
  are accepted risk (above).
- §3 security: **#558 done Nov 22**: no service account of ours holds Editor in production or staging (see
  [Security](security.md#google-cloud-accounts)); follow-ups in #940. Still open: #512 (lockout stage C around
  Nov 29, App Check). SOC 2 and #381 deferred. Done earlier: error alerting (#433), #515, #550 and #716 (#620).
- §4: done Nov 22: release notes (#320), status page (#321, status.metabolichq.app), the Incident Response
  Procedure (#924), backup timing at 10× data (#926: on staging with 85,176 documents, backup 222 s and full restore
  143 s against limits of 30 and 60 minutes). Second region: not now. Left: the release process (#575), which waits
  on #681's staging work (see [Versions](versions.md#after-beta-575-high)).
- §5: done Nov 22: the big-file split (below), type checking (#909–#913: no type errors anywhere; see
  [Engineering rules](../rules/engineering-rules.md#type-checking)), the Engineer Onboarding Guide (#907; see
  [System documentation](system-documentation.md)), the `cohortCache` review (#916: reads only the last 200 days of
  workout logs, warns past 5 minutes). Also: the change log is one file per entry (#939), and scheduled jobs run in
  Google Cloud (#928). Next: the full functional audit (#805, below).

## Splitting the big files (§5)

Split by functional area, matching the testing areas, one area per PR. It makes the code easier and safer to
maintain; by itself it doesn't make anything faster (#620 comment, Nov 18).

**Rules for every split PR** (#620): moves only, never edited in the same PR; a before-and-after check that no
top-level function is lost or doubled and the deployed function names stay identical; every test or tool that reads
the old file updated and checked for a false pass; coverage index regenerated; full end-to-end run before merging;
one split PR open at a time, merged the same day; owner's OK per phase for medium and high risk.

**Phase 0, safety checks (done Nov 18):**
- `ops/function-names.json` lists all 107 deployed Cloud Functions; a test fails if the exported set changes, since a
  renamed function is deleted at deploy and breaks its webhook, link or schedule (#718).
- `node tools/move-check.mjs` proves a PR only moved code: lost, new, changed, doubled or unloaded code fails (#719).
  It also fails a test whose search text moved out of the file it reads (#728), after two false passes in #726, and
  skips files a move creates (#731).
- The security scan checks server functions in every file under `functions/` (#720); a file Semgrep couldn't fully
  check is now a finding (#729).
- Coverage index: known gaps follow code that moves to another file (#721); inner helpers are named by their parents
  (`showMembers.draw`), never by number (owner's choice, #723). That one-time change grew `ops/ui-gaps.json` from
  1,467 to 1,499 entries, all existing untested places that same-named helpers had hidden (owner's OK, #620).

**Phase 1, server (`functions/index.js`), Nov 18:** down from about 4,000 lines to about 1,100. Shared setup in
`functions/base.js` (#724); calls, video and push in `fn-calls.js`, `fn-push.js` (#725); metabolichq.app forms in
`fn-site.js` (#726); partner invites in `fn-invites.js` (#727); space admin in `fn-spaces.js` (#732); privacy in
`fn-privacy.js` (#733); membership core in `members.js` (#734); coach payments in `fn-payments.js` (#735); sign-up
and memberships in `fn-signup.js` (#738); a partner's steps after signing in `fn-partner.js` (#739). Every step kept
all 107 functions unchanged and passed the full end-to-end run (58/58) (#620). The order changed so sign-up and coach
payments wouldn't import from each other in a circle (#620 comment, Nov 18).

**Phase 1 finished Nov 19** (1.7b–1.7q and a tidy, #762–#779): the rest moved into `fn-files.js`, `fn-biometrics.js`,
`fn-coach.js`, `fn-food.js`, `fn-ops.js`, `fn-coupons.js`, `fn-github.js`, `fn-messaging.js`, `fn-install.js`,
`fn-youtube.js`, `fn-portal.js`, `fn-mptprogramming.js`, `fn-announce.js`, `fn-mail.js`, `fn-signinhelp.js` and
`fn-csp.js`. `functions/index.js` is now about 100 lines: shared start-up and re-exports, no functions of its own
(#778, #779). Each step passed its own full end-to-end run (58/58) (#620 comment, Nov 19).
- A step whose run was red only because the report push collided, and one whose runner stopped reporting, were
  explained or re-run before merging, never counted as passed (#620 comments, Nov 19).
- Every PR now loads the server the way the deploy does and checks each function's trigger, account, region,
  secrets, limits and schedule against `ops/function-endpoints.json` (`tools/function-endpoints.mjs`, #758). The move
  check closed three more ways to be fooled (#750).
- A reviewed Semgrep exception keyed to the old file has to move with its code: one didn't in 1.7c and the scan
  flagged it (#768). Each move now checks `scripts/security/allow.json` first (#620 comment, Nov 19).

**Phase 3, the client app, finished Nov 20** (owner's direction, Nov 19; #620): 13 page files now hold the page
code, each a plain script loaded in order after `app.js`: `page-signals.js` (3.1, #780), `page-files.js` (3.2, #809),
`page-coachai.js` MPT Coach (3.3, #815), `page-calls.js` calls and messages (3.4, #832), `page-community.js` (3.5,
#835), `page-biometrics.js` check-in, Library, Achievements, Biometrics (3.6, #836), `page-reports.js` (3.7, #837),
`page-help.js` (3.8, #840), `page-clients.js` (3.9, #841), `page-parq.js` (3.10, #843), `page-home.js` (3.11, #844),
`page-profile.js` (3.12, #845) and `page-account.js` memberships, two-step sign-in, your data (3.13, #846).
`public/js/app.js` went from 7,073 lines to 2,505 (#620 comment, Nov 20). Each step passed a full end-to-end run
(58/58) (#620).
- What stays in `app.js` is the app shell: start-up and the sign-in gate, the space, navigation, Workouts itself,
  the exercise videos and sheet/video player, the profile and client view, and live space refreshes (#620 comment,
  Nov 20). Four shared helpers stayed when Reports moved, because other pages use them (#837).
- The app now starts from its own last script, `public/js/start.js`, so every page file is loaded before it starts
  (#849, CHANGELOG 2026-11-20).
- The coverage index tool misread templates inside templates; it was fixed before 3.10, with the owner's go-ahead
  (#842). Saving a bio on Profile had never been tested; 3.12 added a real journey step instead of a gaps entry (#845).
- Found along the way: a Workouts day that answered late could draw over another page (#847, fixed by #848; see
  [Training](training.md)).

**Phase 2, the coach portal, finished Nov 21** (#620 comments, Nov 21): `admin/portal.js` went from 6,701 lines to
**746**, and is now only the portal shell (page cache, gates, `start()`, the menu, Back and Forward, shared helpers
including `fnBase`, Yes/No, shared clicks), Coach Home and the Spaces list. 2.1 the portal starts from
`admin/portal-start.js`, loaded last (#874); the owner's email comes from `config.js` instead of being written into
the portal five times (#875). The pages moved, unchanged, into one file per menu group:

| File | Holds | PR |
|---|---|---|
| `portal-platform.js` | Costs, Backlog (Roadmap, Claude sessions), Blog, Performance, Security | 2.2, #878 |
| `portal-business.js` | Payments, Finances and Memberships, Deals, MPT coupons | 2.3, #882 |
| `portal-content.js` | Resources, Community | 2.4, #895 |
| `portal-programming.js` | Your offer, exercise videos, Program calendar and One-on-one editor, Workout library | 2.5, #898 |
| `portal-coaching.js` | Clients and a client's page (with its Notes tab), welcome note, Signals, Cohort, Inbox and Messages, Coaching calls | 2.6, #900; 2.9, #903 |
| `portal-space.js` | Coaches, Your data, Your brand, Space settings, Help (?), Support | 2.7, #901 |
| `portal-owner.js` | Partner coaches, Tools and Maintenance (wearables, video, mail cards), AI coach test lab, Programs, Add-ons, MPT Coach report | 2.8, #902 |

- Every step was moves only (`tools/move-check.mjs`), had its row in mac-app's `docs/code-map.md` with `portal.js`'s
  limit lowered, gave the same offline portal output as main, and passed a full end-to-end run (62 of 62, 0 bugs)
  before merging (#620 comment, Nov 21).
- Where a move showed a control had only been counted as tested through another one (the access-link and Sign-up
  link Copy buttons), a real journey check was added, never a gaps entry; the gaps list stayed at 1,157 (#882, #901).
- Tidy-up (#905): the Coaches page and wearables-card buttons have their own click handlers beside their pages. Left
  as is on purpose, with the code map saying where: the Tools pages' shared button handler (in `portal-space.js`;
  moving it would change the order of click handlers) and `busy()` (moving it would push `portal.js` past its limit)
  (#620 comment, Nov 21).
- Found on the way, both fixed: the CI functions emulator ran out of memory late in full runs (#896, #897), and a run
  crossing midnight UTC failed the "today" journeys (#899, #904). See [Engineering rules](../rules/engineering-rules.md#testing-levels).
- Where new code goes from now on: [Engineering rules](../rules/engineering-rules.md) → the code map (#883).

**After the split:** a full functional audit (#805, high, needs the owner's go-ahead): an inventory of every screen
control, function, data field, role, integration, key and use case, the expected result written before each test,
tests in layers up to staging and real devices, an independent re-check, and a finish line (no high issues open,
`ops/ui-gaps.json` at zero or explained, three green nights in a row). Until then, problems the owner finds are
logged as `audit-intake` issues, as the audit's answer key. Open decision: where the inventory Sheet lives (#805).
Added to the roadmap Nov 21 (#805).

Findings the smaller files let the scan see, fixed with the owner's OK: see [Security](security.md#code-scanning).

## Related

[Architecture](architecture.md) · [Security](security.md) · [Versions](versions.md) ·
[Roadmap and backlog](roadmap-and-backlog.md)
