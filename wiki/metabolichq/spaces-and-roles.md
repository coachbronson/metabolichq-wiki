---
title: Spaces, coaches and roles
summary: Multi-coach spaces, main coach vs team coaches, client assignment, coach vs client accounts, sign-up
updated: 2026-11-15
sources: [notes, mac-app README, CHANGELOG, "#404"]
---

# Spaces, coaches and roles

## Spaces

- Each coaching business is a **space**. MPT was the first (`mpt`). Partner coaches each get one.
- As system manager, Bronson does **not** see inside partner spaces.
- Client limits are per coaching business, not per coach.
- Coaching calls, Community and Deals are on in every space by default; a custom config can turn one off, but that's
  not the norm.
- A single **Space settings** page in the portal holds space-wide defaults (e.g. whether clients set their own macro
  targets, whether calories show).

## Coaches

- **Main coach** = the account holder of a space (not just Bronson). A space can have several coach-level people.
- Main coach can assign clients to specific coaches. New sign-ups go to the main coach first and default there.
  Clients see who their coach is.
- Every coach still sees everyone in workout comments and community.
- The main coach sees all information for clients assigned to other coaches, **except** those clients' conversations
  with their other coach.
- Team coaches are free (no seat charge).

## Coach accounts vs client accounts

- Coaches are separate from clients. The coach's phone app is a **minimized coach portal**, not a client view with
  extras (no "Today's workout" tile; no portal link on phones; resource libraries available).
- The main coach gets a free, full **client view** switch. Client view belongs to the account that turned it on;
  Sign out turns it off and puts the tab back on Home, so the next account in that tab never opens in client view
  or on the last person's page (#404, v8.66.1).
- Team coaches are blocked from client functions (so free seats aren't used as free client accounts). A team coach
  who wants a client account subscribes through their own space's client sign-up with their coach email — no "+"
  aliases (not universal). They're billed and counted like any client, filed under the main coach, and reach it via
  the client view switch. Main coaches can give their coaches coupon codes.

## Client sign-up

- Automated and seamless; no coach approval (previously sign-ups waited for approval).
- Partner coaches' clients count toward the coach's tier as soon as they sign up; open/closed sign-ups is the coach's
  only control.
- Google sign-in is the default; other emails (including Apple/iCloud) work too.
- MPT trial buttons go straight to Stripe (no login first), then a custom sign-in link is emailed. Partner sign-up
  links work the same way when Stripe is their processor; coaches see their own sign-up link in the portal.
- Clients are **group** or **one-on-one** (`track = 'one'`): one-on-one clients see only their own programming, not
  the group program.

## Related

[Partner program](partner-program.md) · [Coach portal](coach-portal.md) · [Memberships](mpt-membership.md)
