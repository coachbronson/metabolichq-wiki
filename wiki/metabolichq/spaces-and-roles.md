---
title: Spaces, coaches and roles
summary: Multi-coach spaces, main coach vs team coaches, client assignment, coach vs client accounts, sign-up
updated: 2026-11-28
sources: [notes, "#1135", "#1151", "#1171", "#410", "#1081", "#1086", "#1107", "#1110", "#1112", "#1095", "#1099", "#1033", "#1035", "#1059", "#1073", "#1076", "#1032", mac-app README, CHANGELOG, "#404", "#647", "#652", "#699", "#700", "#701", "#710", "#711", #753, #755, #788, #803, #808, #810, #861, #825]
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
- **A client's coaches** = the coaches assigned to them (Clients → Coach) plus the coaches of their groups (see
  Client groups below). Group coaches are the client's coaches for everything: they see and work with the client,
  and the client sees, messages and books them, but never sees the group's name. A client covered by a group isn't
  Unassigned. Head coaches still see everyone (his decisions, Nov 25; v8.76.0, #1073).
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

## Client groups (#410)

Coach-made groups of clients (e.g. Masters, Competition prep), each with its coaches and managers. **#410 closed
Nov 26**: stages A1–A4, B1, B2, B4, C1 and C2 merged (v8.75.0–8.83.0); B3 dropped and B5 skipped (his calls, below;
#410 "How this was resolved").
- **Who does what:** head coaches create, rename and delete groups and choose each group's coaches and managers; a
  group's managers (always some of its coaches) add and remove its clients. A client can be in several groups. Only
  coaches see groups (his decisions, Nov 25; v8.75.0, #1035).
- Limits: 20 coaches and 2,000 clients per group, 200 groups per space (#1035).
- **Access through a group** (stage A3, v8.76.0, #1073): a group's coaches are its clients' coaches (above). Since a
  group's managers in effect give coaches access to client data, that's by design: he chose that managers run
  membership (#1073).
- **How it's kept:** every group change goes through the server callable `groups`, which checks the caller and keeps
  each client's server-only `groupCoaches` field in step; nobody in the app writes groups or that field (stage A2,
  #1059). His call: a callable, not a Firestore trigger, because the trigger's deploy needed three IAM grants the
  deploy account can't make (#1059). The MetHQ Monitor's Quality tile flags a client whose field doesn't match their
  groups (#1059).
- **Groups as an audience** (Nov 26): a Resources collection can be shared with a group (B1, v8.78.0, #1081, see
  [Resources and files](resources-and-files.md)); coaches message a whole group at once (B2, v8.79.0, #1086, see
  [Messaging and community](messaging-and-community.md)); group calls (B4, v8.81.0, #1107, see
  [Coaching calls](coaching-calls.md)); a group's own Community feed (C1, v8.82.0, #1110); Cohort reports by group,
  coaches only (C2, v8.83.0, #1112, see [Coach portal](coach-portal.md#client-groups)).
- **His calls on the plan (Nov 26):** B3, check-ins by group, dropped for one custom check-in per space (#157, see
  [Biometrics and signals](biometrics-and-signals.md#check-ins)); B4 kept simple, with recording and AI notes in
  #1095 (done Nov 27: everyone agrees on each join, notes for coaches only; see
  [Coaching calls](coaching-calls.md)); B5, onboarding by group, skipped until coach-built client onboarding (#332) exists; C2 coaches only, the
  outside-sponsor summary is #1099 (deferred to R&D, low, his call Nov 27: only matters if group coaching is sold
  to companies, gyms or teams) (#410).
- Still to do: run the **Group coaches backfill** on production once A2 is live (reminder Nov 27, 9:37 AM, #1072).
- "Group program" is now called **Shared program**, so it isn't mixed up with Groups (his call, Nov 25; #1035).
- Screens: see [Coach portal](coach-portal.md#client-groups).

## Business name and main coach

- Coaches must be able to change their business name themselves (his decision, Nov 17). Since 8.69.0 the main coach
  does it on **Your brand → Business name**: the space's own name (emails, sign-in help, calls, receipts, exports,
  Spaces, Monitor), the app header, the sign-up page and the email sender name change at once. The email address and
  the sign-up link (space id) stay the same. MetabolicHQ is emailed about each change and it's kept in the space's
  name history (`renameSpace`, `functions/rename.js`, #700). (Previously the brand editor's name changed only the app
  header and sign-up page.)
- **The name in the app is separate from the business name** (his decision, Nov 17): Your brand has an editable
  **Name in the app** (app header, sign-up page, home-screen icon); a note shows past 13 characters. He asked for the
  simple version: no rename checkbox, so renaming the business still sets the name in the app too, and it can be
  shortened after (#710, PR #1032, Nov 25).
- **Only the main coach and head coaches** (and the platform owner) can change a space's brand: name in the app,
  logo, colors, bio, home-screen icons. Other team coaches see it read-only, with who to ask. Enforced by the security
  rules; a space with no head coach on record keeps every coach as a head (his request; #1033, PR #1046).
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
  or on the last person's page (#404, v8.66.1). Since Nov 27 client view also shows what clients see on Files
  (Resources), Signals and Home's What's new card (#1135, v8.84.1–8.84.3).
- A client who went live as a partner coach of their own space but kept an active MPT client record: the "Delete
  people" workflow's **keep sign-in** mode removes only their records in the space and keeps their sign-in (now
  their coach sign-in) and coach invite (CHANGELOG 2026-11-27).
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
- Clients are on the **shared program** or **one-on-one** (`track = 'one'`): one-on-one clients see only their own
  programming, not the shared program. (Previously called "group program"; renamed Nov 25, #1035.)

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
