---
title: MetHQ Monitor
summary: Phone-friendly ops view at admin.metabolichq.app/monitor — tabs, Claude action menus, security and quality tiles
updated: 2026-11-17
sources: [notes, admin/monitor/, functions/monitor.js, mac-app CLAUDE.md, "#515", "#673", "#657"]
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
  linking the comment merges).
- **Content review**: MetHQ blog drafts and scheduled posts only; Review and Revise run against
  `content/blog/DRAFTING.md`. (Previously also coachbronson.com's newsletter and blog drafts, through that site's
  portal; removed in the split, #673. Those are now reviewed in the site's own portal.)
- Every alert or item has a context menu that starts a Claude session: "Fix this", "Look into this", or "Make this a
  backlog issue" — worded to fit the item's kind (features and O&M items aren't "find out what caused this").
- Uses the app's existing GitHub token, not a new one. Dependabot is on for mac-app.

## Related

[Coach portal](coach-portal.md) · [Engineering rules](../rules/engineering-rules.md) · [Security](security.md)
