---
title: metabolichq.app site and MPT page
summary: The coach landing page, MPT page for individuals, branding demo widget, sales demo pages, blog, research and trust pages
updated: 2026-11-18
sources: [notes, site/ in mac-app, CHANGELOG, "#322", "#611", "#618", "#636", "#672", "#692", "#693", "#694", "#698", "#703", "#704"]
---

# metabolichq.app site

- Built by Claude on Firebase (in mac-app `site/`), replacing his web team's Squarespace plans.
- Audience: coaches and coaching businesses. Main button: **"Apply to become a partner"**. The app is live and coaches
  can sign up free now (it's not "prelaunch").
- Sells Basic and Premium (see [Partner program](partner-program.md)); shows real screens and what's coming.
- Pages: home, about, compare, research (citizen science, footer menu), security, `/mpt`, blog. `llms.txt` for AI search.
- **metabolichq.app/security** says how to report a security problem; `/.well-known/security.txt` points to it
  (#322). A Security link is in every page's footer (CHANGELOG 2026-11-14).
- The site **enforces** its Content-Security-Policy (the first of the three sites, #693); its inline scripts are now
  files under `site/js/` (#692). See [Security](security.md#content-security-policy-550-done).
- Website messaging comes first in the messaging plan: a "Replace your stack" home section (see
  [Content and social](../business/content-and-social.md)).

## Demo video on the homepage (#636)

- **See it in 2½ minutes** section right under the hero plays "A coaching day on MetabolicHQ" (2:36). Bronson narrates
  a coaching day over the real app and portal, filmed from the how-to demo spaces (no real client data). Subtitles
  are burned in, so it works muted. Hero button **▶ Watch the demo (2½ min)** scrolls down and starts it.
- Self-hosted at `/video/methq-demo.mp4` (no YouTube); nothing plays until clicked. Structured data has a VideoObject;
  `llms.txt` links it (CHANGELOG 2026-11-15). How it was made: [Video production](../business/video-production.md).

## Branding demo widget

Potential partners enter their website; it pulls logo and colors; they approve or enter their own. Sample screens are
built on the site (not the real app). The approved brand carries into partner sign-up/space setup. Has a captcha.
The sample screen shows the brand "on MetabolicHQ" (#707). SVG logos found on a coach's site load again under the
enforced policy (#704).

## Sales demo pages

- One-prospect concept pages live under `site/demos/<name>/` on metabolichq.app. They're a visual, content-only sales
  tool: their buttons and forms don't need to work (owner, Nov 17), so the coverage index leaves them out. A site test
  keeps each one noindex, out of the sitemap and free of links to Coach Bronson's sites (#694, CHANGELOG 2026-11-17).
- **metabolichq.app/demos/kiltz/**: Kiltz Health (moved from coachbronson-site's `/kiltz-preview`, #694,
  coachbronson-site #38).
- **metabolichq.app/demos/ovadia/**: Ovadia Heart Health, built on the Kiltz layout: the member app in their
  branding, a care-team view with clinic, I Fix Hearts wellness and employer groups in one space, and a mock sign-up
  page. Colors and the "OH" mark are placeholders (#698).
- Partners show "on MetabolicHQ" / "Provided by MetabolicHQ", not on MPT (#703). Prospects:
  [Partner program](partner-program.md#ideas-parked-or-later).

## MPT page (for individuals)

- MPT is promoted as an all-in-one training, nutrition and lifestyle tracker for individuals, with call-outs on the HQ
  site. Membership only (no one-on-one coaching offered there).
- MPT's page is **metabolichq.app/mpt**. The "For individuals", "MPT for individuals", "Explore MPT →" and "Join MPT
  as an individual →" links on the home, About, Compare, Research and Security pages and in the blog open it in the
  same tab; nothing on metabolichq.app links to Coach Bronson's own site (#672, CHANGELOG 2026-11-17). (Previously the
  links went to coachbronson.web.app/mpt/ through the repo variable `COACHBRONSON_URL`, #611; that swap step is gone.)
- MPT is one coach space like any other, ahead of the coach marketplace (mac-app CLAUDE.md, Nov 16).
- The site end-to-end journey checks these links and that none points at coachbronson.web.app (#672).
- Footer carries the "Provided by MetabolicHQ" badge (previously "Hosted by", #618; coachbronson-site #28).

## MetHQ blog (metabolichq.app/blog)

Prepopulated with launch posts, each reviewed and approved before posting; a different cover photo for each article
whenever possible. Drive photos are coaching-oriented, so combine them with text/graphics for a tech web-app feel.

## Later

Trust page (#319), public status page (#321), Search Console/Bing verification (#265).

## Related

[Content and social](../business/content-and-social.md) · [Platform and brands](platform-and-brands.md)
