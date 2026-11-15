---
title: metabolichq.app site and MPT page
summary: The coach landing page, MPT page for individuals, branding demo widget, blog, research and trust pages
updated: 2026-11-15
sources: [notes, site/ in mac-app, CHANGELOG, "#322", "#611"]
---

# metabolichq.app site

- Built by Claude on Firebase (in mac-app `site/`), replacing his web team's Squarespace plans.
- Audience: coaches and coaching businesses. Main button: **"Apply to become a partner"**. The app is live and coaches
  can sign up free now (it's not "prelaunch").
- Sells Basic and Premium (see [Partner program](partner-program.md)); shows real screens and what's coming.
- Pages: home, about, compare, research (citizen science, footer menu), security, `/mpt`, blog. `llms.txt` for AI search.
- **metabolichq.app/security** says how to report a security problem; `/.well-known/security.txt` points to it
  (#322). A Security link is in every page's footer (CHANGELOG 2026-11-14).
- Website messaging comes first in the messaging plan: a "Replace your stack" home section (see
  [Content and social](../business/content-and-social.md)).

## Branding demo widget

Potential partners enter their website; it pulls logo and colors; they approve or enter their own. Sample screens are
built on the site (not the real app). The approved brand carries into partner sign-up/space setup. Has a captcha.

## MPT page (for individuals)

- MPT is promoted as an all-in-one training, nutrition and lifestyle tracker for individuals, with call-outs on the HQ
  site. Membership only (no one-on-one coaching offered there).
- The MPT page moves onto coachbronson.com (`/mpt`) and `metabolichq.app/mpt` redirects to it.
- Until coachbronson.com moves (July 2027), the "MPT for individuals" and Coach Bronson links on the site and every
  MetHQ blog post go to **coachbronson.web.app**. Pages keep coachbronson.com in the source; deploys swap in the repo
  variable `COACHBRONSON_URL`. In July: set it to `https://coachbronson.com` (#611, CHANGELOG 2026-11-14).
  (Previously the links pointed straight at coachbronson.com/mpt/.)
- Footer carries the Hosted-by badge.

## MetHQ blog (metabolichq.app/blog)

Prepopulated with launch posts, each reviewed and approved before posting; a different cover photo for each article
whenever possible. Drive photos are coaching-oriented, so combine them with text/graphics for a tech web-app feel.

## Later

Trust page (#319), public status page (#321), Search Console/Bing verification (#265).

## Related

[Content and social](../business/content-and-social.md) · [Platform and brands](platform-and-brands.md)
