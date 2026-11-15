---
title: Coach portal
summary: The desktop management portal — menus, Platform vs space areas, client management, Backlog/roadmap, Costs, Performance
updated: 2026-11-14
sources: [notes, CHANGELOG v2.0, admin/portal.js]
---

# Coach portal (v2.0) — admin.metabolichq.app

- Desktop browser only (≥1024 px; landscape tablets OK), MetabolicHQ-branded. Each coach sees only their space.
- Bronson rebuilt the portal himself (done Nov 11, 2026).
- Next planned: a real Home for coaches.

## Menu shape

- **Platform** (Bronson only): Masters Collective, add-ons configuration, Costs, performance, backlog, and other
  platform services.
- **MPT** stacked under Platform, with exactly the same menu a partner coach gets (Get help stays in MPT). For MPT he
  wants Finances but not the Stripe Connect setup or manual pay-by selector.
- Partner coaches using Stripe have a Memberships page; every space has Payments (tiers, client counter, coupons).

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

## Costs and performance

- **Costs** (Platform): real cost sources in three stages — actuals and trends, Google Cloud billing export, then
  projections and budget alerts. Later: cost by space and per user (#467).
- **Performance dashboard**: load, performance, utilization, trends; alerts by email only.

## Related

[MetHQ Monitor](methq-monitor.md) · [Spaces and roles](spaces-and-roles.md) · [Roadmap and backlog](roadmap-and-backlog.md)
