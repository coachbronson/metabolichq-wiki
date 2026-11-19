---
title: Acquisition readiness
summary: How mature MetabolicHQ would look to a buyer (#620), the owner's accepted risks, what's still open, and the code split
updated: 2026-11-19
sources: ["#620", CHANGELOG 2026-11-18, CHANGELOG 2026-11-19, "#718–#741"]
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

## Still open (Nov 18)

- §2: the project ownership note; Workspace, Resend and Zapier accounts under BD Solutions LLC; `package.json` name
  and description (#620).
- §3 security: #512 (lockout stage C around Nov 29, App Check), #558 step 4 (taking Editor off the default compute
  account) waits to **Nov 23**; SOC 2 readiness roadmap; decide on #381 (#620). Done: error alerting (#433), #515,
  #550 and #716.
- §4: #575 release process, #320 release notes, #321 status page, incident procedure, backup time at 10× data,
  second-region decision (#620).
- §5: split the big files (below), type checking, an architecture and engineer-onboarding guide, `cohortCache`
  review (#620).

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

**Next:** the rest of `index.js` (reports, wearables, owner tools, AI coach and others), tidy-up 1.7, then phase 2:
the portal, by menu group (#620).

Findings the smaller files let the scan see, fixed with the owner's OK: see [Security](security.md#code-scanning).

## Related

[Architecture](architecture.md) · [Security](security.md) · [Versions](versions.md) ·
[Roadmap and backlog](roadmap-and-backlog.md)
