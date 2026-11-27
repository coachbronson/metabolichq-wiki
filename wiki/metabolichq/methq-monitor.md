---
title: MetHQ Monitor
summary: Phone-friendly ops view at admin.metabolichq.app/monitor — tabs, Claude action menus, security and quality tiles
updated: 2026-11-27
sources: ["#1079", "#1080", "#1084", "#1103", "#1117", "#1037", "#1043", "#1051", "#1053", "#1058", "#1059", "#1066", "#1069", "#1079", "#977", "#988", notes, admin/monitor/, functions/monitor.js, mac-app CLAUDE.md, "#515", "#673", "#657"]
---

# MetHQ Monitor — admin.metabolichq.app/monitor/

A standalone page, fully usable on a phone, so Bronson can watch performance, security and usage when he's away from a
desktop. Kept separate from the portal so it needn't mix role-based access into the portal's logins.

- **Backlog** in list mode (no swim lanes), sortable by tag or date; open, edit, comment; shows priority.
- **Support**: reply from the phone.
- **Dashboards, not counters**: Money, Costs, Performance, Usage.
- **Security**: where each finding came from and when; every scan (daily and PR-level, not just nightly); charts by
  criticality, by category and a 30-night trend. Also security events, alerts, lockouts and accepted risks, with
  **Accept this risk** in each finding's ⋯ menu; phone alert links open this tab (#515). The portal's Security page
  is the desktop version ([Security](security.md)).
- **Quality** (the nightly tile): end-to-end results (a run with any failed journey or recorded bug now shows red,
  #657) and CodeRabbit questions (questions count as fixed once a PR
  linking the comment merges). Also **Claude jobs (last run)**, **Next reminders** and **Reminders sent**; a failed
  job or a reminder over an hour late shows under Needs attention (#983, #1037, #1058). The tile flags a client whose
  group coaches don't match their groups (#1059).
- **Service status** tile and page: Operational / Degraded / Incident, the words people see, every space or picked
  ones; saving or ending an incident asks first, since it emails coaches (#1043). See
  [Versions](versions.md#after-beta-575-done-nov-25).
- **Releases** (owner only, two-step): what's in each stage on the way to production (PR open, On staging,
  Promoting, Being watched, Live), each card's status, last action and next action as an Eastern clock time; ⋯ menus
  with Promote now (it asks first and lists what it takes along), Promote all on staging, Hold / Release the hold,
  Re-run smoke tests, links and Claude options (#977, #988). It updates by itself, Live lists the last 24 hours, the
  drift check sits under the heading, Being watched has Roll back and It's fine, and Feature switches have their ⋯
  menu and calendar (#1002, #1004, #1066, #1069; see [Versions](versions.md#after-beta-575-done-nov-25)). The live
  refresh no longer resets a half-filled Set a date form (#1079 fixed, #1080). A banner shows each running end-to-end
  run with a timer, expected finish and what started it, or says it can't tell when GitHub doesn't answer (#1084,
  #1103).
- **Content review**: the major version announcement draft (from 9.0; edit, then Send or Skip, #1051), plus MetHQ blog drafts and scheduled posts (Approve on a draft behind main queues it to merge once its tests
  pass, #1117); Review and Revise run against
  `content/blog/DRAFTING.md`. (Previously also coachbronson.com's newsletter and blog drafts, through that site's
  portal; removed in the split, #673. Those are now reviewed in the site's own portal.)
- Every alert or item has a context menu that starts a Claude session: "Fix this", "Look into this", or "Make this a
  backlog issue" — worded to fit the item's kind (features and O&M items aren't "find out what caused this").
- Uses the app's existing GitHub token, not a new one. Dependabot is on for mac-app.

## Related

[Coach portal](coach-portal.md) · [Engineering rules](../rules/engineering-rules.md) · [Security](security.md)
