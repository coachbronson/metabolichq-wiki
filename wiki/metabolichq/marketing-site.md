---
title: metabolichq.app site and MPT page
summary: The coach landing page, MPT page for individuals, branding demo widget, sales demo pages, blog, research and trust pages
updated: 2026-11-27
sources: ["#1105", "#1109", "#1043", "#1064", "#908", "#917", "#922", "#925", "#320", "#321", notes, site/ in mac-app, CHANGELOG, "#322", "#611", "#618", "#636", "#672", "#692", "#693", "#694", "#698", "#703", "#704", "#743", "#744", "#745", "#747", #781, "#319", "#865", "#866", "#871", site/trust.html]
---

# metabolichq.app site

- Built by Claude on Firebase (in mac-app `site/`), replacing his web team's Squarespace plans.
- Audience: coaches and coaching businesses. Main button: **"Apply to become a partner"**. The app is live and coaches
  can sign up free now (it's not "prelaunch").
- Sells Basic and Premium (see [Partner program](partner-program.md)); shows real screens and what's coming.
- Pages: home, about, compare, research (citizen science, footer menu), security, trust, privacy, terms, releases,
  `/mpt`, blog. `llms.txt` for AI search.
- **Compare** (metabolichq.app/compare) has five products since Nov 22: CoachRx (OPEX Fitness) joined after
  TrueCoach, from coachrx.app and its help centre; "Not advertised" where no public mention was found (#908). The
  home page's compare call-out, FAQ and `llms.txt` name it too.
- **Privacy Policy and Terms** moved from the app host to **metabolichq.app/privacy** and **/terms** on Nov 22, with
  the site's header, menu and footer; the app's old addresses redirect (301), so app links, emails and bookmarks keep
  working. Same PR: both now describe MetabolicHQ, owned and run by BD Solutions LLC, with MPT as one coach's space
  (#925; see [Research and privacy](research-and-privacy.md#privacy)).
- **metabolichq.app/releases** (What's new): the release notes for clients and coaches, plain HTML built from the
  app's notes by `node tools/releases-page.mjs`; linked from the Trust page, sitemap and `llms.txt` (#320, #922). A
  feature behind a feature switch is left out while its switch exists (#1064).
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
- Self-hosted at `/video/methq-demo.mp4` (no YouTube); nothing plays until clicked. Since Nov 26 the file isn't in
  the repo: it's on mac-app's private `site-media` GitHub Release and the deploy fetches and checks it; the address is
  unchanged (#1105, #1109; see [Architecture](architecture.md)). Structured data has a VideoObject;
  `llms.txt` links it (CHANGELOG 2026-11-15). How it was made: [Video production](../business/video-production.md).

## Branding demo widget

Potential partners enter their website; it pulls logo and colors; they approve or enter their own. Sample screens are
built on the site (not the real app). The approved brand carries into partner sign-up/space setup. Has a captcha.
The sample screen shows the brand "on MetabolicHQ" (#707). SVG logos found on a coach's site load again under the
enforced policy (#704).

## Sales demo pages

- One-prospect concept pages live under `site/demos/<name>/` on metabolichq.app. They're a visual, content-only sales
  tool: their buttons and forms don't need to work (owner, Nov 17), so the coverage index leaves them out.
- **Every screen must show the app as it works today**; anything planned is marked "Coming" (owner, Nov 19; #781).
  So the pages show Home's daily quote (no coach tip), no lesson progress or worksheet due dates (items open "on day
  15" and so on, as timed release works), and call notes the AI drafts and the coach publishes (#781). A site test
  keeps each one noindex, out of the sitemap and free of links to Coach Bronson's sites (#694, CHANGELOG 2026-11-17).
- **metabolichq.app/demos/kiltz/**: Kiltz Health (moved from coachbronson-site's `/kiltz-preview`, #694,
  coachbronson-site #38).
- **metabolichq.app/demos/ovadia/**: Ovadia Heart Health, built on the Kiltz layout: the member app in their
  branding, a care-team view with clinic, I Fix Hearts wellness and employer groups in one space, and a mock sign-up
  page. Colors and the "OH" mark are placeholders (#698). Since #781: no group breathwork session (group calls aren't
  in the app); the care-team view, employer groups and per-group feeds are marked Coming (client groups, #410).
- **metabolichq.app/demos/cci/**: Carnivore Coach International. Each CCI graduate runs their own branded coaching
  business on MetabolicHQ with a CCI starter kit inside: the graduate's client app (carnivore food diary, transition
  lessons opening week by week, biometrics, waiver and readiness questions, packages and payments, calls and notes),
  their getting-started checklist and the pricing ladder from free. The "CCI Certified" coach directory, sales pages
  and referral share are marked Coming (#743, CHANGELOG 2026-11-18). In CCI's black (#2D2B2A, owner's call) and white
  with CCI's logo, supplied by the owner (#744, #745). No lab-tracking claims: lab results only reach a coach as a
  shared file, so the screen shows Biometrics (#744). It shows the real standard waiver and says coach-written
  waivers are coming (#746, #747). Since #781: no coach card or CCI Certified badge on Home (neither exists yet); the
  packages screen is the real **Choose a package** (What's included, **Continue to payment** to Stripe's checkout);
  the getting-started checklist is marked as example steps.
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

## Trust page (metabolichq.app/trust, #319, done Nov 20)

- Plain-words page on how MetabolicHQ handles data: what's collected and who sees it, where AI is used (MPT Coach on
  Gemini through Vertex AI, private to the client; AI-drafted call notes the coach checks; device readings never fed
  raw to AI), the service providers that receive personal data (the privacy policy's list, plus Cloudflare Turnstile,
  USDA FoodData Central and Open Food Facts), how long things are kept, data export, backups, the research choice and
  the partner agreement in brief (#865, #871, `site/trust.html`).
- The site's Trust, Research and MPT pages and `llms.txt` point to **Settings → Privacy & documents** for the research
  choice (previously Profile → Documents; #871).
- Linked from the app's Help (see [Help and how-to](help-and-howto.md)) (#872).
- Shows the owner's service status banner when it's set for every space, and keeps the Better Stack status link (his
  decision, Nov 25; #1024, #1043).
- What's left (#866, closed Nov 20 at the owner's request): the owner handles the legal review himself; the HIPAA line
  waits for #381 (the site test blocks any HIPAA wording on the page until then). An accessibility statement and a
  link from sign-up weren't carried anywhere (#866).
- Linked from it since Nov 22: the status page (an "Is everything working?" line and a Better Stack row in the
  providers table, #321, #917) and the release notes ("What changed lately", #922).

## MetHQ blog (metabolichq.app/blog)

Prepopulated with launch posts, each reviewed and approved before posting; a different cover photo for each article
whenever possible. Drive photos are coaching-oriented, so combine them with text/graphics for a tech web-app feel.

## Later

Search Console/Bing verification (#265). (Release notes and the status page shipped Nov 22, #320, #321.)

## Related

[Content and social](../business/content-and-social.md) · [Platform and brands](platform-and-brands.md)
