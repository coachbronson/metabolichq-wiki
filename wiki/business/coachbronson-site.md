---
title: coachbronson.com
summary: The athlete site rebuild, audience, hosting situation, forms/embeds, Resend email capture, blog/newsletter automation, site admin
updated: 2026-11-16
sources: [notes, coachbronson-site README and CLAUDE.md, "coachbronson-site #25", "coachbronson-site #27", "coachbronson-site #28", "coachbronson-site #29", "mac-app #611", "mac-app #613", "mac-app #646"]
---

# coachbronson.com

## Status

- Rebuilt from the ground up by Claude in repo `coachbronson/coachbronson-site`, live at **coachbronson.web.app**.
- **Can't move the domain yet**: his hosting company holds coachbronson.com under a contract with monthly payments
  until it ends, in **July 2027** (mac-app CHANGELOG 2026-11-14). Meanwhile the hosting company updates the existing pages (not a rebuild), adds his forms and images,
  adds MPT as the only new page, and drops the sport-specific pages. Cut-over checklist is in the site README.
- The cut-over checklist now includes MetabolicHQ's side: set mac-app's `COACHBRONSON_URL` to
  `https://coachbronson.com` and deploy, and re-run the API-key script from mac-app #595 so the key allows the domain
  (coachbronson-site #25). coachbronson.com stays on Firebase sign-in's authorized domains meanwhile (mac-app #613).
- **Decided: the site moves into its own Google Cloud project, `coachbronson-site`** (notes 2026-11-15). Its
  temporary address becomes `coachbronson-site.web.app`; `coachbronson.web.app` becomes a 301 redirect and is never
  deleted (Firebase can't reuse a site name). Kept linked on purpose: the /mpt trial buttons, the "Provided by" badge,
  the newsletter's partner deal (through a new public mac-app `mptDeals` endpoint) and Resend sending from
  metabolichq.app. Steps and Cloud Shell scripts: coachbronson-site `scripts/split/`. Both PRs are open, waiting for
  his OK (coachbronson-site #29, mac-app #646). Until they merge, the site still deploys into MetabolicHQ's project.
- Site functions run as `functions-runtime`, not the default compute account (coachbronson-site #27, mac-app #558).
- The MPT page lives at `coachbronson.com/mpt` (see [metabolichq.app site](../metabolichq/marketing-site.md)); its
  badge and the Kiltz preview say "Provided by MetabolicHQ" (coachbronson-site #28).

## Audience and offers

- Masters athletes in **CrossFit, HYROX, combat sports and tactical**; competing Masters ideal, seriously training
  non-competitors fit too. Coaches are no longer a target audience for this site.
- **Keto up front**: athletes curious about keto for its benefits; athletes already on keto get maintaining,
  adjusting/optimizing and support.
- One Coaching page covers all four sports (no per-sport pages).
- Offers: see [Offers](offers.md).

## Forms and email

- **Resend** (free tier) for email capture, sending from metabolichq.app for now. Every form has Turnstile.
- Form embeds (`/embed/`) let the hosting company paste the free-guide and contact forms on coachbronson.com without
  keys. The Masters Collective page and interest-list embed were removed with the Collective's shutdown
  (coachbronson-site #24). Only add new embed settings; never change an existing one's meaning.

## Content automation

- Blog: Claude drafts, he edits and approves each post; posts live in the site repo. **Drafting is paused** (blog and
  portal Blog tab stay). New posts not announced on Facebook/LinkedIn for now.
- Weekly **newsletter**: Thursday mornings, one main idea + latest blog post + one call to action, its own topic list
  with intents; includes one MPT partner deal in rotation; replaces separate blog-post emails.
- Weekly site report email on **Fridays** (incl. newsletters, pending approvals). Daily drafting task keeps running.
- Site admin area (Google sign-in): blog review/approval with the next 4 topics and their intent, SEO (GA4, Search
  Console), leads/email list, site health. Blog covers auto-picked from his Drive photo folder.
- Publer is not used anywhere.

## Related

[Offers](offers.md) · [Content and social](content-and-social.md) · [Engineering rules](../rules/engineering-rules.md)
