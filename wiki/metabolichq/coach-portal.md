---
title: Coach portal
summary: The desktop management portal — menus, Platform vs space areas, client management, Backlog/roadmap, Costs, Performance
updated: 2026-11-26
sources: ["#410", "#575", "#648", "#710", "#1019", "#1022", "#1033", "#1035", "#1036", "#1065", "#1066", "#1068", "#1069", "#1073", "#1076", "#978", "#988", "#980", "#955", "#959", "#961", "#920", notes, CHANGELOG v2.0, CHANGELOG 2026-11-15, CHANGELOG 2026-11-17, admin/portal.js, "#515", "#623", "#645", "#648", "#652", "#653", "#675", "#683", "#686", "#850", "#851", "#874", "#875", "#878", "#882", "#895", "#898", "#900–#903", "#818", "#697", "#700", "#701", "#710", "#711", #755, #789]
---

# Coach portal (v2.0) — admin.metabolichq.app

- Desktop browser only (≥1024 px; landscape tablets OK), MetabolicHQ-branded. Each coach sees only their space.
- Bronson rebuilt the portal himself (done Nov 11, 2026).
- **Coach Home** shows a **What's new** card with clients' and coaches' new features, once (#1036), and a **Coming
  up** card with features turning on in the next 7 days (#1065). See [Versions](versions.md#after-beta-575-done-nov-25).
- A service status banner shows at the top during a Degraded or Incident status for the coach's space (#1043).

## Menu shape

- **Platform** (Bronson only): add-ons configuration, Costs, performance, backlog, and other
  platform services.
- **Staging tools** (staging only, owner only): Platform → Maintenance gets a **Staging inbox** (the emails staging
  kept instead of sending, shown in a sandbox) and a **Staging demo data** card (Reset demo data and Staging sign-in
  link links to the workflows); code in `admin/portal-staging.js` (#955, #959, #961).
- **Releases** (Platform, owner only, two-step): the stages from PR to production side by side, with Promote now,
  Promote all on staging, Hold and Re-run smoke tests in each card's ⋯ menu; the same cards as the Monitor's Releases
  page (`public/js/releaseskit.js`). It updates by itself; Live lists the last 24 hours; the drift check sits by
  Refresh; Being watched has Roll back and It's fine; a Feature switches section and turn-on calendar. No Help
  walkthrough, like the other owner-only pages (#978, #988, #1002, #1004, #1066, #1069; see
  [Versions](versions.md#after-beta-575-done-nov-25)).
- **Security** (Platform, owner only, two-step): scan results, security events, alerts, lockouts, accepted risks
  (#515; see [Security](security.md)).
- **Help**: a **?** at the top of every page and **Help** at the end of the menu (v8.67.0, #645). Tabs:
  **Coach portal** (how to use each page, coaching from the phone app) and **Client app** (what clients see in their
  Help, so a coach can walk a client through it). Opens on the topics for the current page; same search, chips and
  how-to videos as the app. A third tab, **What's new**, shows clients' and coaches' release notes; the version line
  under the menu opens it (#920). See [Help and how-to](help-and-howto.md).
- **MPT** stacked under Platform, with exactly the same menu a partner coach gets (Get help stays in MPT). For MPT he
  wants Finances but not the Stripe Connect setup or manual pay-by selector.
- Partner coaches using Stripe have a Memberships page; every space has Payments (tiers, client counter, coupons).
  Switching how clients pay right after turning sign-ups on or off now always shows the option picked (#976, #980).
- A coach who isn't the main coach (head or team coach) opening **Finances** sees a short card: revenue, payments and
  payouts are for the main coach (named), then Memberships (every client's for a head coach, their own clients' for a
  team coach). His calls (Nov 25): keep Finances in their menu, name the main coach, treat head coaches the same
  (#648, #1011). Their empty Memberships card doesn't ask them to set up packages (#1019, #1021).
- The portal and Monitor enforce their Content-Security-Policy (#697; see [Security](security.md)).
- The owner's Spaces & coaches table scrolls inside its card, so the page keeps its width at 1366 px (#850, #851).
  #686, the older issue for the same bug, is still open.
- Code: each menu group has its own script (`admin/portal-platform.js`, `-business`, `-content`, `-programming`,
  `-coaching`, `-space`, `-owner`); `admin/portal.js` is only the shell, Coach Home and the Spaces list, and the
  portal starts from `admin/portal-start.js` (#620 phase 2, #874, #878, #882, #895, #898, #900–#903; see
  [Acquisition readiness](acquisition-readiness.md)). The owner's email shown in the portal comes from `config.js`
  (#875).
- The MPT Coach report shows topics and flags, never question or answer text (#818; see [MPT Coach](mpt-coach.md)).

## Your brand

- **Business name** card (v8.69.0, #700): the main coach renames the space everywhere at once; team coaches see who
  can change it. A note reminds coaches who take payments to rename their Stripe account too. The card shows the
  space's own name (#1032).
- **Name in the app** (#710, PR #1032, Nov 25): editable in the brand editor, separate from the business name; a note
  past 13 characters. Renaming the business still sets it too.
- **Who can edit:** only the main coach and head coaches; other team coaches see the brand read-only with who to ask,
  plus the sign-up link and Get the app cards (#1033, PR #1046).
- **Change the main coach** card (v8.70.0, #701): **Contact support** opens a New request on Get help, filled in
  (Account & setup, subject "Change the main coach", and the questions support needs). Fixed on Nov 18 so the form
  stays filled when Get help redraws from the page cache (#711). The header's **Get help** always starts an empty
  request, even after an unsent "Change the main coach" one (#755, #789). See
  [Spaces and roles](spaces-and-roles.md#business-name-and-main-coach).

## Client groups

**Coaching → Groups** (`admin/portal-groups.js`; rules in [Spaces and roles](spaces-and-roles.md#client-groups-410)):
- Head coaches make, rename and delete groups and pick each group's coaches and managers; managers add and remove
  clients (#1035).
- **My groups** at the top lists the groups a coach coaches or manages, with their role, the client count, and links
  to Clients and Inbox filtered to that group (v8.77.0, #1076).
- **Clients** has a Group filter and tick boxes with **Add to group** / **Remove from group**; the Coach column shows
  group coaches as "(via group)"; Clients → Coach still edits only assigned coaches (#1035, #1073).
- **A client's page** shows their groups with **Change**, and "Coached through: <group> (coaches)" (#1035, #1076).
- **Inbox** has a Group filter over Messages, Signals, Workout comments and Help requests (#1076). The coach app's
  Clients has a Group filter too (#1076).
- The coach data export adds `client-data/groups.csv` (#1035).

## Program calendar and one-on-one workouts

- Right-click a workout (or its **⋯** on hover) on the **Program calendar** or **One-on-one workouts** for a menu:
  **Approve** (pending review only; it goes live and waits for Send update), **Approve all N pending this week**
  (after a confirm), **Edit** (or **Open**), **Copy**, **Delete** (after a confirm). A plain click still opens the day.
  An open pending workout has **Approve** at the top too (v8.68.0, #653).
- Tapping one Approve disables both until it finishes, and the calendar no longer redraws over another page after an
  approve or delete from the menu (#683, from the nightly CodeRabbit review).
- Pending review workouts come from the [program library import](program-library-import.md).

## Client management

- Overview per client across training, biometrics, check-ins and nutrition (see
  [Biometrics and signals](biometrics-and-signals.md)) and Coaching notes.
- Turn calories on/off per client; set macro targets.
- Inbox: app suggestions from every space come to Bronson only, with **Approve** (→ new backlog issue) or **Decline**
  (internal reason, archived).

## Backlog dashboard and roadmap

- Backlog = GitHub issues in mac-app labeled `backlog` (replaced his notepad list).
- Interactive roadmap, all drag and drop: month timeline (previous month + next 6), each month in 4 weeks; due date set
  by position; lanes **Features, Operations & Maintenance, Bugs & Fixes, Research & Development**; tiles show full
  titles; tray sortable by date, filter by user-submitted. Roadmap tag lives in metadata only.
- Dependencies many-to-many; he wants linking to work like Microsoft Project Gantt charts (current version felt
  unintuitive). Change priority from the dashboard.
- Every card shows its type badge (**Feature**, **O&M**, **Bug**, **R&D**, plus **Security** and/or **Enhancement**
  when tagged). **Show** chips filter one type across every lane (they replaced the tray's lane chips). A card's
  **Security** and **Enhancement** switches set the GitHub label without moving its lane (#623, CHANGELOG
  2026-11-15/16).

## Demo data

**Actions → Demo data → seed** fills a partner space so a demo coach sees every portal page working: Deals, Community
topics, a team coach who can't sign in, a program and calendar, one-on-one workouts, workout library, a worksheet,
free memberships, plus messages, calls, signals and Inbox items. It never replaces the space's own content; Payments,
Finances and Your brand stay the coach's own. **remove** takes it all away (#647, #652). See
[Spaces and roles](spaces-and-roles.md#demo-spaces).

## Costs and performance

- **Costs** (Platform): real cost sources in three stages — actuals and trends, Google Cloud billing export, then
  projections and budget alerts. Later: cost by space and per user (#467).
- **Performance dashboard**: load, performance, utilization, trends; alerts by email only.

## Related

[MetHQ Monitor](methq-monitor.md) · [Spaces and roles](spaces-and-roles.md) · [Roadmap and backlog](roadmap-and-backlog.md)
