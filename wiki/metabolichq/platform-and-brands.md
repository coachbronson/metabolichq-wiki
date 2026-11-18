---
title: MetabolicHQ, MPT and the brands
summary: What MetabolicHQ is, how it relates to MPT and Coach Bronson, mission, positioning and branding
updated: 2026-11-18
sources: [notes, mac-app README, CHANGELOG, "#618", "#703", "#705", "#706", "#707", Google Drive]
---

# MetabolicHQ, MPT and the brands

## The three names

| Name | What it is |
|---|---|
| **MetabolicHQ** ("MetHQ", likely the official abbreviation) | The platform: a coaching-business app for health, wellness, nutrition and fitness coaches, starting in the keto/carnivore community. Owned by BD Solutions LLC. |
| **MPT — Metabolic Performance Training** | Coach Bronson's coaching program and his space on MetabolicHQ (space id `mpt`). Formerly "MAC" / "Coach Bronson Workouts". Shown under the Coach Bronson wordmark. |
| ~~Masters Collective~~ | **Shut down** (2026-11-15). Its app, portal and site pieces are removed and its records wiped; see [Memberships](mpt-membership.md). The Google Cloud project id `masters-collective-app` and the `masterscollective.app` domain are infrastructure names and stay. |

His main group program is called the **"Metabolic Performance Training" program** — not "MPT Strength & Conditioning".

As far as MetabolicHQ is concerned, **MPT is just another partner coach space**: his MPT menus must match a partner
coach's, so he sees what they see. Platform-level functions sit under **Platform** in the portal. (notes, Nov 11)

## Mission and positioning

- Built to **serve coaches rather than monetize them**: coach first, a good client experience that adds no work for
  the coach, fundamentals included instead of nickel-and-dimed add-ons, build what coaches actually ask for.
- Founded by a coach of 20 years frustrated by app companies ignoring coaches. Listen, answer every request, and say
  plainly when something is hard or not possible.
- Coaches **own their program and client data**; it is never locked down; export is always available.
- Platform focus is **one-on-one coaching** with a team approach; group programs stay but aren't the focus.
- Messaging framework (one claim, five pillars): see [Content and social](../business/content-and-social.md).
- MPT positioning for individuals: "Coach Bronson's Metabolic Performance Training is the premier functional fitness
  program for anyone following a ketogenic lifestyle."
- Differentiators he sees as unique: whole-food % reporting, cycle tracking (now a candidate add-on), signals measured
  against each client's own normal. He's looking for more.

## Branding

- MetabolicHQ: own logo, deep navy `#142B3D`, teal `#007F79`. The coach portal uses MetabolicHQ branding.
- Logo files are in Google Drive: `MetabolicHQ-logo.png` (full lockup, navy/teal on white), `MetabolicHQ-icon-512.png`,
  `MetabolicHQ-Central-Hub.svg`, `MetabolicHQ-LinkedIn-banner.png`, plus `MetabolicHQ-promo-reel.mp4`. The logo is
  navy and teal, so it needs a white backing on navy backgrounds (notes, Drive, 2026-11-15).
- Each coach space keeps its own look; only a "Provided by: [MetabolicHQ logo]" mark appears next to the version on
  the Help page (v8.66.3, #618).
- A **"Provided by MetabolicHQ" badge** must appear on partner coaches' sites (portal Your brand tile, partner
  agreement 7.5, onboarding checklist). coachbronson.com's MPT page footer carries it. It said "Hosted by" until
  v8.66.3; changed because many coaches' sites are hosted elsewhere. Badge file names and addresses didn't change, so
  placed badges switch on their own (#618; image cache fix v8.66.4, #621).
- Coach brand setup in the portal works like the website's branding demo widget (pull logo and colors from the
  coach's website, approve or edit); changes show the client sample first, before saving.
- A coach's own icon appears when their clients install the app on a phone home screen.
- **Partners run their spaces "on MetabolicHQ"**, not on MPT: MPT is Coach Bronson's own space (owner, Nov 17). The
  app header under a partner's brand, the installed app's description ("<business> on MetabolicHQ"), partner invites,
  the brand preview and the sales demo pages say so; MPT's own space is unchanged (#703, #705–#707, CHANGELOG
  2026-11-17). (Previously they said "on Metabolic Performance Training".)

## Related

[Architecture](architecture.md) · [Partner program](partner-program.md) · [Versions](versions.md) ·
[Marketing site](marketing-site.md)
