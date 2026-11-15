---
title: MPT memberships and coupons
summary: MPT client pricing and trial, Stripe flow, coupons, launch targets, Masters Collective shutdown
updated: 2026-11-14
sources: [public/js/config.js, notes, CHANGELOG]
---

# MPT memberships and coupons

## Plan

- One plan: **Monthly $47.99** or **Annual $450** (save $125), **3-day free trial**. Live on the "Coach Bronson" Stripe
  account (a sandbox exists for testing).
- Paying approves the client automatically. Trial buttons go straight to Stripe, then a sign-in link is emailed.
- Includes nutrition tracking in the base membership.
- 1:1 coaching clients get MPT access as part of coaching (see [Offers](../business/offers.md)).

## Masters Collective — being shut down (2026-11-14)

Bronson is shutting the Masters Collective down, and it is to be wiped from the app and the sites. Until the removal
ships, the old flow is still in the code: Circle → Zapier → `circleMember` function → single-use `MC-…` code on the
Stripe coupon `masters-collective`, the Platform → Masters Collective portal page, `collective/{email}` records, and
mentions on metabolichq.app/mpt, Terms, Privacy and Help. Removal is a high-risk change (payments, saved data) and
waits on his go-ahead.

## Coupons

- Made on the portal **Payments** page (every space; moved from Maintenance).
- No share links that auto-apply a code. Codes stack on the free trial. Every code works on monthly and annual.

## Launch status and targets (Nov 10, 2026)

- Not launched to the public yet (0 paying members); he thinks it's ready.
- 12-month targets: ~250 paying members, ~10 partner coaches with ~15 clients each (the ~150 free Masters Collective
  members are out with the shutdown), ~75% of clients one-on-one with four 60-minute calls a month.
- Before opening: load testing (#359, done on staging) and error alerts.

## Test accounts

- For his own manual test sign-ups use "+" alias emails (e.g. `+test1`, `+test2`); remind him when a test needs a
  fresh one. Load tests use server-made tokens on `@example.com` addresses instead.
- Demo coach/client accounts with demo data: see [Casey Ruff](../people/casey-ruff.md) and
  [David Harper](../people/david-harper.md).

## Related

[Marketing site](marketing-site.md) · [Partner program](partner-program.md)
