---
title: Spaces, coaches and roles
summary: Multi-coach spaces, main coach vs team coaches, client assignment, coach vs client accounts, sign-up
updated: 2026-11-21
sources: [notes, mac-app README, CHANGELOG, "#404", "#647", "#652", "#699", "#700", "#701", "#710", "#711", #753, #755, #788, #803, #808, #810, #861, #825]
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
- In the data the main coach is `spaces/{sid}.coach`, the coach who signed the space up. It decides who opens support
  requests, renames the business, sees Finances and Payments and uses the client view (#699).
- A team-coach invite is made in one step: if two spaces invite the same email at once, the second is told the email
  already has an invite, instead of silently replacing the first (#816 item 10, #825).
- Planned (medium): **delegated admin roles** the main coach assigns on the Coaches page, so other coaches can help
  run the space; which permissions an admin gets is still to decide, billing likely staying with the main coach
  (#861).

## Business name and main coach

- Coaches must be able to change their business name themselves (his decision, Nov 17). Since 8.69.0 the main coach
  does it on **Your brand → Business name**: the space's own name (emails, sign-in help, calls, receipts, exports,
  Spaces, Monitor), the app header, the sign-up page and the email sender name change at once. The email address and
  the sign-up link (space id) stay the same. MetabolicHQ is emailed about each change and it's kept in the space's
  name history (`renameSpace`, `functions/rename.js`, #700). (Previously the brand editor's name changed only the app
  header and sign-up page.)
- **The name in the app must be separate from the business name** and not forced by it, since a business name may be
  too long for the app header (his decision, Nov 17). Today a rename also overwrites the app name; #710 (high) brings
  back an editable "Name in the app" and a rename checkbox.
- **Changing the main coach** (business sold, or something else happens) is not self-service: it needs MetabolicHQ
  support (his decision, Nov 17). Since 8.70.0 Your brand's **Change the main coach** card opens a pre-filled support
  request (#701; fixed so it stays filled in, #711). The Platform tool MetabolicHQ uses for the switch, with its
  checklist (agreement, Stripe Connect, billing, the old coach's role and conversations), is #699 (needs decisions,
  high risk).

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
- A coach's client-account flag is kept in two places (the space's user record and `accounts/{uid}`, which the
  security rules read); every path that turns it on or off, subscriptions and one-time packages, now writes both in
  one transaction (#803, #808, #810).
- A partner space's **Getting started** card belongs to its main coach: only the main coach can close or reopen it
  (#755, #788).

## Client sign-up

- Automated and seamless; no coach approval (previously sign-ups waited for approval).
- Partner coaches' clients count toward the coach's tier as soon as they sign up; open/closed sign-ups is the coach's
  only control.
- Google sign-in is the default; other emails (including Apple/iCloud) work too.
- MPT trial buttons go straight to Stripe (no login first), then a custom sign-in link is emailed. Partner sign-up
  links work the same way when Stripe is their processor; coaches see their own sign-up link in the portal.
- Clients are **group** or **one-on-one** (`track = 'one'`): one-on-one clients see only their own programming, not
  the group program.

## Demo spaces

- Demo coach spaces show the product with fictional clients: [Casey Ruff](../people/casey-ruff.md)'s Boundless Body
  Fitness, and **Smitty Fitness** (coach Bubba Smith, space `smitty-fitness`) on a test account with MPT Programming on
  (comp), seeded with all 10 demo clients (16 weeks) and every extra; no how-to-get-in email (notes 2026-11-15, #647).
- **Actions → Demo data → seed** fills a partner space so every app and portal page works: messages, Community,
  calls with AI notes, coaching notes, signals, Inbox items, a Start here collection, pending sign-ups, onboarding,
  Deals, Community topics, a team coach (Alex Morgan, can't sign in), a program and calendar, one-on-one workouts,
  workout library items, a worksheet and free memberships. It never replaces the space's own content; Payments,
  Finances and Your brand stay the coach's own. Everything is marked demo and **remove** deletes it. Demo addresses
  get no emails. The space's coach must have signed in once (#647, #652).
- `mpt_addon` with seed turns MPT Programming on (no charge) in a demo space. Cohort reports count demo clients only
  in spaces marked `demoData` (#647).

## Related

[Partner program](partner-program.md) · [Coach portal](coach-portal.md) · [Memberships](mpt-membership.md)
