---
title: coachbronson.com
summary: The athlete site rebuild, audience, hosting situation, forms/embeds, Resend email capture, blog/newsletter automation, site admin
updated: 2026-11-17
sources: [notes, coachbronson-site README and CLAUDE.md, "coachbronson-site #25", "coachbronson-site #27", "coachbronson-site #28", "coachbronson-site #29", "mac-app #611", "mac-app #613", "mac-app #646", "coachbronson-site #30", "coachbronson-site #32–#34", "mac-app #672–#677", scripts/split/README.md]
---

# coachbronson.com

## Status

- Rebuilt from the ground up by Claude in repo `coachbronson/coachbronson-site`. It now deploys into its **own Google
  Cloud project, `coachbronson-site`**, at **coachbronson-site.web.app** (coachbronson-site #29, README). (Previously
  coachbronson.web.app, a Hosting site in MetabolicHQ's project.)
- **Can't move the domain yet**: his hosting company holds coachbronson.com under a contract with monthly payments
  until it ends, in **July 2027** (mac-app CHANGELOG 2026-11-14). Meanwhile the hosting company updates the existing pages (not a rebuild), adds his forms and images,
  adds MPT as the only new page, and drops the sport-specific pages. Cut-over checklist is in the site README.
- **Full split (his call, Nov 16):** MetabolicHQ is the base platform and is self-contained. The site uses no service,
  secret, key, account, sign-in or data shared with MetabolicHQ, and MetabolicHQ doesn't link to or call the site (both
  repos' CLAUDE.md; notes 2026-11-16). `coachbronson.web.app` is **deleted**, not redirected (Firebase never reuses a
  deleted site name). There is no `mptDeals` endpoint (mac-app #646 closed for this). (Previously, Nov 15: a 301
  redirect, with deals, sign-in and Resend kept shared.)
- Split steps and Cloud Shell scripts: coachbronson-site `scripts/split/` (setup, data copy, mailing-list export
  before MetabolicHQ revokes the site's Resend key). MetabolicHQ's side is mac-app #672–#677; the Google Cloud removal
  (`scripts/remove-coachbronson-site.sh`, mac-app #676) is still open. Deploy fixes after the split:
  coachbronson-site #32–#34.
- **Rebuild to-do** (coachbronson-site #30, `scripts/split/README.md`): its own Resend account and sender domain, the
  mailing list import, its own Turnstile widget (until then forms are refused), new form embeds on coachbronson.com
  (old snippets point at the deleted address), its own partner deals (built-in `DEFAULT_DEALS` for now), GA4 and Search
  Console access, Stripe 1:1 redirect to the new address, and what the /mpt page says once the coach marketplace
  exists. Until then the site still sends from metabolichq.app.
- Cut-over in July 2027: add coachbronson.com to Hosting and to sign-in's authorized domains **in the site's own
  project** (README cut-over steps).
- Site functions run as `functions-runtime@coachbronson-site`, not the default compute account (coachbronson-site
  #27, #34).
- The site's own MPT page (`/mpt`) links out to metabolichq.app's trial checkout; its badge and the Kiltz preview say
  "Provided by MetabolicHQ" (coachbronson-site #28). What it should say is to be decided once the coach marketplace
  exists (rebuild to-do). MetabolicHQ's MPT page is metabolichq.app/mpt (see
  [metabolichq.app site](../metabolichq/marketing-site.md)).

## Audience and offers

- Masters athletes in **CrossFit, HYROX, combat sports and tactical**; competing Masters ideal, seriously training
  non-competitors fit too. Coaches are no longer a target audience for this site.
- **Keto up front**: athletes curious about keto for its benefits; athletes already on keto get maintaining,
  adjusting/optimizing and support.
- One Coaching page covers all four sports (no per-sport pages).
- Offers: see [Offers](offers.md).

## Forms and email

- **Resend** for email capture; still MetabolicHQ's sender until the site's own account is set up (rebuild to-do).
  Every form has Turnstile (its own widget is on the to-do list).
- Form embeds (`/embed/`, now at coachbronson-site.web.app/embed/) let the hosting company paste the free-guide and contact forms on coachbronson.com without
  keys. The Masters Collective page and interest-list embed were removed with the Collective's shutdown
  (coachbronson-site #24). Only add new embed settings; never change an existing one's meaning.

## Content automation

- Blog: Claude drafts, he edits and approves each post; posts live in the site repo. **Drafting is paused** (blog and
  portal Blog tab stay). New posts not announced on Facebook/LinkedIn for now.
- Weekly **newsletter**: Thursday mornings, one main idea + latest blog post + one call to action, its own topic list
  with intents; includes one partner deal in rotation (the site's own list since the split); replaces separate blog-post emails.
- Drafts are reviewed in the site's own portal (/admin/), no longer in MetHQ Monitor (mac-app #673).
- Weekly site report email on **Fridays** (incl. newsletters, pending approvals). Daily drafting task keeps running.
- Site admin area (Google sign-in): blog review/approval with the next 4 topics and their intent, SEO (GA4, Search
  Console), leads/email list, site health. Blog covers auto-picked from his Drive photo folder.
- Publer is not used anywhere.

## Related

[Offers](offers.md) · [Content and social](content-and-social.md) · [Engineering rules](../rules/engineering-rules.md)
