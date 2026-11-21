---
title: Coach portal
summary: The desktop management portal — menus, Platform vs space areas, client management, Backlog/roadmap, Costs, Performance
updated: 2026-11-21
sources: [notes, CHANGELOG v2.0, CHANGELOG 2026-11-15, CHANGELOG 2026-11-17, admin/portal.js, "#515", "#623", "#645", "#648", "#652", "#653", "#675", "#683", "#686", "#850", "#851", "#874", "#875", "#878", "#818", "#697", "#700", "#701", "#710", "#711", #755, #789]
---

# Coach portal (v2.0) — admin.metabolichq.app

- Desktop browser only (≥1024 px; landscape tablets OK), MetabolicHQ-branded. Each coach sees only their space.
- Bronson rebuilt the portal himself (done Nov 11, 2026).
- Next planned: a real Home for coaches.

## Menu shape

- **Platform** (Bronson only): add-ons configuration, Costs, performance, backlog, and other
  platform services.
- **Security** (Platform, owner only, two-step): scan results, security events, alerts, lockouts, accepted risks
  (#515; see [Security](security.md)).
- **Help**: a **?** at the top of every page and **Help** at the end of the menu (v8.67.0, #645). Two tabs:
  **Coach portal** (how to use each page, coaching from the phone app) and **Client app** (what clients see in their
  Help, so a coach can walk a client through it). Opens on the topics for the current page; same search, chips and
  how-to videos as the app. See [Help and how-to](help-and-howto.md).
- **MPT** stacked under Platform, with exactly the same menu a partner coach gets (Get help stays in MPT). For MPT he
  wants Finances but not the Stripe Connect setup or manual pay-by selector.
- Partner coaches using Stripe have a Memberships page; every space has Payments (tiers, client counter, coupons).
- Team coaches opening Finances get an error box today; a clear message is planned (#648, high).
- The portal and Monitor enforce their Content-Security-Policy (#697; see [Security](security.md)).
- The owner's Spaces & coaches table scrolls inside its card, so the page keeps its width at 1366 px (#850, #851).
  #686, the older issue for the same bug, is still open.
- Code: the Platform pages (Costs, Backlog with Roadmap and Claude sessions, Blog, Performance, Security) are in
  `admin/portal-platform.js`, and the portal starts from `admin/portal-start.js` (#620 phase 2, #874, #878). The
  owner's email shown in the portal comes from `config.js` (#875).
- The MPT Coach report shows topics and flags, never question or answer text (#818; see [MPT Coach](mpt-coach.md)).

## Your brand

- **Business name** card (v8.69.0, #700): the main coach renames the space everywhere at once; team coaches see who
  can change it. A note reminds coaches who take payments to rename their Stripe account too. The brand editor shows
  the name read-only for now; a separate, editable app name is planned (#710, high).
- **Change the main coach** card (v8.70.0, #701): **Contact support** opens a New request on Get help, filled in
  (Account & setup, subject "Change the main coach", and the questions support needs). Fixed on Nov 18 so the form
  stays filled when Get help redraws from the page cache (#711). The header's **Get help** always starts an empty
  request, even after an unsent "Change the main coach" one (#755, #789). See
  [Spaces and roles](spaces-and-roles.md#business-name-and-main-coach).

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
