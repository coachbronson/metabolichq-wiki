---
title: Partner coach program
summary: Partner tiers and pricing, Premium (MPT Programming) add-on, agreement terms, onboarding, coach payments and packages
updated: 2026-11-20
sources: [notes, site/index.html, CHANGELOG, "#173", "#517", "#570", "#312", "#313", "#618", "#628", "#633", "#694", "#698", "#706", "#742", "#743", "#746", "#256", public/js/agreement-text.js, public/js/spaces.js, #751, #752, #792–#800]
---

# Partner coach program

## Who it's for

Health, wellness, nutrition and fitness coaches, starting in the keto/carnivore community. No certification needed,
no insurance needed (BD Solutions' own insurance covers it). Go-to-market: a few certified coaches and smaller coaches
from his network first, then Instagram/Facebook, a Facebook group later, then ads.

## Pricing (monthly, flat by client count)

| Clients | Price |
|---|---|
| up to 5 | Free (no support: Contact support off for coach and clients) |
| 6–15 | $149 |
| 16–45 | $239 |
| 46–70 | $319 |
| 71–95 | $399 |
| over 95 | Contact us |

- Tier follows client count automatically; nothing to choose. Card on file even on the free tier.
- Planned: a **coach add-on marketplace** (Add-ons section on Space settings; Premium moves onto it without changing
  price or access) and a second coach add-on, the GLP-1 companion at $57.99/month (#633, #628; see
  [Client add-ons](client-add-ons.md#coach-add-ons-planned)).
- **Premium = MPT Programming add-on, $199/month flat**, any tier, cancel anytime: Coach Bronson's programs, his demo
  videos, guided swaps and [MPT Coach](mpt-coach.md).
- Team coaches free. Month-to-month; on cancellation the plan runs to the end of the paid month, no proration.
- Fixed Stripe products/prices; no per-coach special terms or discounts.
- Paused or archived clients still count (they take resources). An active client is whoever the coach gives access.
- (Previously per-client $25/$22/$19/$16, then other flat tiers; 6–12-month terms with early-termination fee dropped.)

## Basic vs Premium

- **Basic**: the whole platform with the coach's own programming. The exercise *names* list and Coach Bronson's master
  exercise **video library** are in every space; coaches can replace videos in their own space without changing the
  master index. (v6.2; videos were briefly Premium-only.)
- **Premium**: MPT programming, MPT Coach, guided swaps / advanced tracker.
- AI-augmented analytics and cohort trends: "Coming soon", not a Premium add-on.

## Agreement and onboarding

- 100% self-service: the Get started form reads as package selection for purchase, with totals.
- E-sign in the app; PDF emailed to the coach and to Bronson. Payment details at signing, before the setup
  questionnaire; billing starts when the space goes live.
- MPT programming stays his property.
- **Going live** (Nov 19 fixes, #752): an invite link replaced by a newer invite can't be used to sign (#797). The
  space id and every coach email are held for 10 minutes before Stripe is called, so two go-lives at once can't
  double-charge a coach or share a space (`goLiveHolds`, #799). A retry resends the saved Stripe request, so it gets
  the same subscription back (`goLiveRequest`, #800). A space that went live is never reported as failed; a tidy-up
  step that fails is noted on the proposal's history (#798).
- **Client waiver:** every space uses MetabolicHQ's standard **Waiver and release** (agreement Schedule C,
  `public/js/agreement-text.js`, `WAIVER_VERSION` 2026-11-04), with the coach's business name filled in; it was based
  on his past waivers (Ultimate Ketogenic Fitness, The APEX Training System). It covers training risk only: risk,
  release, assumption of risk, health, rhabdomyolysis, covenant not to sue, minors, acceptance. Clients tick each part
  and type their full name; the record is kept per version and can't be changed. On per space (`features.waiver`, on
  by default, `public/js/spaces.js`). Coaches can't edit it; the PAR-Q readiness questions are a separate step (#746,
  code read Nov 18).
- Planned: **coach-written waivers** (#746, medium, needs decision): each space's own parts in the coach's words
  (credentials and scope of service, nutrition and diet risk), with MetabolicHQ's platform release always kept.
  Raised for newly certified carnivore coaches (Carnivore Coach International).
- Get-started journey and onboarding checklist, with feedback CTAs (positive and negative) and a testimonial ask.
- Only the main coach opens support tickets to MetabolicHQ; free-tier tickets are tagged free tier; replies in the
  portal and by email.
- Partner agreement must cover the research opt-in, the "Provided by MetabolicHQ" badge and client add-ons (no
  revenue share). Section 7.5 names the badge; agreement version **2026-11-15.1** (coaches who signed earlier keep
  the version they signed) (v8.66.3, #618).
- Planned: a coach add-on clause (month-to-month, cancel anytime, MetabolicHQ owns the modules, coach responsible for
  their own scope with health modules) for the coach add-on marketplace (#633).

## Coach payments and packages (#173, #517)

- Stripe Connect (Standard) is the only integrated processor; **no platform fee** on coach payments.
- Two pathways: coach bills elsewhere and sends a single-use access link (or grants access manually); or coach puts
  their **coaching packages** into MetHQ and buying one grants access automatically.
- Packages: up to 10 "What's included" lines; private packages hidden from the website packages table; program/coach
  assignment on purchase is immediate. Coaches can build payment widgets for their own websites.
- Plans: monthly/annual, other intervals, free trials, one-time/fixed-length. Clients self-manage in Stripe's billing
  portal. On tenancy end, client subscriptions cancel at period end.
- Partners' Payments page shows the tiers and a client counter.
- Stripe edge cases fixed Nov 19 (#751): turning off the only open package is refused before any Stripe change
  (#792); a resent Stripe event can't give back access from an expired one-time package (#793); a refused cancel or
  refund on a coach-site checkout is kept and retried daily, then alerts the owner (#794); when a space's ending is
  undone, a client's plan is marked renewing only once Stripe confirms it (#795); "I've already paid · check again"
  applies the newest payment that still gives access (#796).

## Ideas parked or later

- Custom development tier: his team customizes MetabolicHQ for one business; priced per project.
- Free coach marketplace / directory (#570); coach sales pages + custom domains (#523).
- MetabolicHQ affiliate program (#312) and coach-run affiliates (#313): low priority, needs decision.
- MetabolicHQ MCP server (#256), with a companion **MCP skill toolkit** (#742, medium, needs decision): ready-made
  skills (Agent Skills format, plus a plain-prompt version) so a coach's own AI assistant uses the data the right way:
  basics and house rules, building workouts in MetabolicHQ's entry format, client and cohort dashboards, nutrition
  analysis, check-in reviews and exports, versioned with the server's v1 tools. Zapier integration in development; CRM/automation integrations (#174).
- Prospects mentioned: a pitch to Dr. Robert Kiltz (Kiltz Health; demo page metabolichq.app/demos/kiltz/, #694); Dr.
  Philip Ovadia (I Fix Hearts; telehealth clinic Ovadia Heart Health, whose NPs and health coaches coach clinic
  members, I Fix Hearts wellness clients and employer wellness groups), sales call the week of Nov 16, demo page
  metabolichq.app/demos/ovadia/ (notes 2026-11-17, #698); **Carnivore Coach International** (Coach Peter; one
  certification course on Thinkific, Facebook and Skool support groups), demo the week of Nov 23, demo page
  metabolichq.app/demos/cci/ (#743). He's weighing hosting CCI's certified coaches on a CCI-branded portal vs an
  affiliate deal where CCI promotes MetabolicHQ for a percentage, and wants to help new graduates start their
  businesses and build credibility (notes 2026-11-18); a coach wanting to migrate from Everfit.
- Partner invites (email and invite page) say the coach runs their space "on MetabolicHQ" (#706).

## Related

[Spaces and roles](spaces-and-roles.md) · [Client add-ons](client-add-ons.md) · [Casey Ruff](../people/casey-ruff.md)
