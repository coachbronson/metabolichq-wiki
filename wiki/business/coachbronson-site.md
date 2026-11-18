---
title: coachbronson.com
summary: The athlete site rebuild, audience, hosting situation, forms/embeds, Resend email capture, blog/newsletter automation, site admin
updated: 2026-11-18
sources: [notes, coachbronson-site README and CLAUDE.md, "coachbronson-site #25", "coachbronson-site #27", "coachbronson-site #28", "coachbronson-site #29", "mac-app #611", "mac-app #613", "mac-app #646", "coachbronson-site #30", "coachbronson-site #32–#39", "mac-app #672–#677", "mac-app #684", "mac-app #694–#696", scripts/split/README.md]
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
  deleted site name). It was deleted on Nov 17 by mac-app's one-time workflow **Delete old site address**, after the
  removal script's Hosting step had been skipped and a frozen pre-split copy kept being served (mac-app #695, #696). There is no `mptDeals` endpoint (mac-app #646 closed for this). (Previously, Nov 15: a 301
  redirect, with deals, sign-in and Resend kept shared.)
- Split steps and Cloud Shell scripts: coachbronson-site `scripts/split/` (setup, data copy, mailing-list export
  before MetabolicHQ revokes the site's Resend key). MetabolicHQ's side is mac-app #672–#677; the Google Cloud removal
  (`scripts/remove-coachbronson-site.sh`, mac-app #676) has been run, so the site's old functions, secrets and
  sign-in domains are gone from masters-collective-app (notes 2026-11-17). Deploy fixes after the split:
  coachbronson-site #32–#34. A frozen copy of the old site stays in branch `archive/site-before-split-2026-11-16`.
- **The one thing still shared:** the site sends email through MetabolicHQ's Resend key until it has its own account.
  The site's own Resend (sending from coachbronson.com) is **on hold until July 2027**, when the domain's DNS is
  back; the code is ready in draft coachbronson-site #35, with a reminder for Jul 1, 2027 (coachbronson-site #30
  comment, notes 2026-11-17).
- **Rebuild to-do** (coachbronson-site #30, `scripts/split/README.md`). Done: own project and deploy, its **own
  Turnstile widget**, and new form snippets sent to the hosting company (coachbronson-site #30 comment). Left: its own
  Resend account (on hold, above) and the mailing list import, its own partner deal images (built-in `DEFAULT_DEALS`
  for now), GA4 access, the Stripe 1:1 redirect to the new address, and what the /mpt page says once the coach
  marketplace exists. Search Console (`sc-domain:coachbronson.com`) is now read by
  `functions-runtime@coachbronson-site` (notes 2026-11-17).
- Cut-over in July 2027: add coachbronson.com to Hosting and to sign-in's authorized domains **in the site's own
  project** (README cut-over steps).
- Site functions run as `functions-runtime@coachbronson-site`, not the default compute account (coachbronson-site
  #27, #34). All site functions set `invoker: 'public'` explicitly, after a failed first create left `siteAdmin`
  closed (#36). The site portal sends its sign-in in an `X-Site-Auth` header, because Google's front door rejected
  Firebase tokens sent as `Authorization` (#37).
- Claude Code's built-in privacy plugin is off for this repo (owner's call, #39), as in mac-app.
- The site's own MPT page (`/mpt`) links out to metabolichq.app's trial checkout; its badge says "Provided by
  MetabolicHQ" (coachbronson-site #28). The Kiltz Health demo page was removed from the site (#38); MetabolicHQ's
  sales demo pages live on metabolichq.app (see [metabolichq.app site](../metabolichq/marketing-site.md#sales-demo-pages)). What it should say is to be decided once the coach marketplace
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

- **Resend** for email capture; still MetabolicHQ's sender until the site's own account is set up (on hold until
  July 2027). Every form has Turnstile, with the site's own widget (coachbronson-site #30 comment).
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
