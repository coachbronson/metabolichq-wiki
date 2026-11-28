---
title: MetabolicHQ content and messaging
summary: MetHQ messaging framework, homepage "Replace your stack" structure, differentiators, social plan, blog rules and topic queue
updated: 2026-11-28
sources: ["#1125", "#1130", "#1149", "#679", "#1092", "#1101", "#1102", "#1104", "#1114", "#1116", "#1117", "#1120", "#1121", "#1122", "#1123", "#441", "#949", content/blog/posts/, notes (Nov 12–13, 2026), MetabolicHQ homepage messaging preview artifact, mac-app content/blog/DRAFTING.md and blog-topics.md, "#675", "#679"]
---

# MetabolicHQ content and messaging

## Audience

Coaches and small coaching businesses running one-on-one clients: keto, carnivore and low-carb coaches first, then
health, wellness, nutrition and fitness coaches and coaching teams. **Not athletes** (athlete content is
[coachbronson.com](../business/coach-bronson-content.md)). Speak to coaches who understand metabolic health and want the
best quality of life for clients, not just getting them skinny. The app is live and free to start: never "prelaunch".

## Messaging framework (Nov 13, 2026)

**One claim:** *"Run your whole coaching business from one place."* MetHQ replaces the stack of apps coaches juggle: one
login for the coach, one app for clients, data stays theirs.

**Five pillars**, rotated across website, blogs, newsletter and social:
1. **Get paid:** packages, Stripe checkout, website payment widgets, no platform fee.
2. **Deliver the coaching:** programming, in-app calls with AI-transcribed notes, scheduling, DMs, resources and
   worksheets, community.
3. **See the whole client:** training, macros + whole-food %, glucose/ketones/GKI/HRV, check-ins, signals.
4. **Grow as a team:** multi-coach, client assignment, limits per business (never per coach).
5. **Own it:** export, no lock-in, fundamentals included, free up to 5 clients.

**Core story:** founded by a coach of 20 years (and 25 in IT) frustrated by app companies ignoring coaches; built to
serve coaches, not monetize them; listen, answer every request, say plainly when something is hard or not possible.

**Underlying message:** most coaches run on spreadsheets and video-call software, can't connect data across sources,
push data entry onto clients, and have no intelligence correlating it. Content leans on FOMO about what technology and AI
could be doing for them, and on how low MetHQ makes the barrier.

**Grounding:** his book's concepts (adaptive economy, physiological resilience, fuel vs. function, macros over calories;
see [Coaching methods](../business/coaching-methods.md)). Show signals against each client's own normal, patterns (sleep
↔ effort, carbs ↔ next-morning glucose), a macro-based low-carb food diary, nutrition achievements that never reward
under-eating and nothing for weight loss.

**Differentiators** to lead with: whole-food %, metabolic biometrics next to training and nutrition, signals,
coach-first pricing (flat by client count, free team seats, no platform fee).

Proof from early partners (e.g. [Casey Ruff](../people/casey-ruff.md)) beats feature claims.

## Website: "Replace your stack" homepage (first focus)

Approved structure (preview: https://claude.ai/artifact/63NuNhNaa2pFLrXaJzRCvX):
1. **Hero:** "Built by a coach, for coaches" / "Run your whole coaching business from one place." Sub: programming,
   nutrition, biometrics, calls, messaging, payments and client files; one login, one client app, data stays yours.
   Main button **Apply to become a partner**; note "Free for up to 5 clients. No platform fee on your coaching payments."
   Sample client overview illustration (signals, consistency, 10-day macros, biometrics, whole-food %, transcribed note).
2. **Replace your stack:** "How many apps does it take to run a coaching business? We got it down to one." The eight
   tools it replaces (programming app, nutrition tracker, biometrics spreadsheets, scheduling, video calls + note-taker,
   messaging, shared drive, payment links), a stack-cost comparison (calculator idea) vs. MetHQ free up to 5, $149 up to
   15.
3. **Five jobs, one platform:** the five pillars as tiles with real screenshots.
4. **See your brand on it:** the branding try-out widget.
5. **Only on MetabolicHQ:** whole-food %, metabolic biometrics, signals.
6. **Coach first:** mission, fundamentals included, data never locked down, a client experience that adds no work.
7. Partner quote slot (real quotes only), closing CTA, "Training on your own? Try Metabolic Performance Training."

Footer shows city and state only (address rule).

## Social (MetabolicHQ accounts)

- Own Facebook, Instagram and LinkedIn accounts, separate from his athlete accounts. One pillar per post, 15–30 s screen
  recordings.
- Photorealistic character images (Imagen) of coaches voicing a problem MetHQ fixes, plus the client angle (no more
  juggling apps, files, emails and video tools; better reports about their own life).
- Images and captions in the Drive "MetabolicHQ Instagram" folder; file names by topic, numbered.
- **Auto-publishing, MetabolicHQ's own** (his call, Nov 26; CHANGELOG 2026-11-26): Instagram and the LinkedIn company
  page, **three posts a week (Mon, Wed, Fri)**. A post goes out at its time unless he pauses or rejects it
  (previously he approved each item). Same setup as coachbronson.com's but nothing shared: its own apps, keys,
  storage and scheduler ("MetabolicHQ is self-contained"). Instagram connects through Facebook Login for Business ("Unified
  login"), since Meta stopped offering Instagram login to new apps in late Oct 2026 (CHANGELOG 2026-11-27; previously
  Instagram Login);
  LinkedIn posts as the company page; a platform not connected yet makes a post wait, not fail. Staging never posts.
  Neither account was connected yet on Nov 26 (CHANGELOG 2026-11-26). The four social keys now reach production
  through Promote (they hadn't, Nov 27; CHANGELOG 2026-11-27). The two social Claude jobs couldn't sign in on their
  first run and can again (#1125, PR #1149; first run signed in).
- **The daily Claude job `hq-social-drafts`** (5:52 AM Eastern, started by Google Cloud) keeps the next week of
  posts planned and redoes ones he sent back: his ideas first, then unposted sets in Drive › MetabolicHQ Instagram,
  then the five pillars in rotation. Photos from Google's image model, slides at 1080×1350 with a real app screen,
  captions ending "Photos: AI-generated." The plan it follows is `content/social/SOCIAL.md` (CHANGELOG 2026-11-26).
- **Measured and reviewed** (his call, Nov 26: measure every post, review each week, adjust the plan; Instagram
  only): `socialStats` (6:21 AM daily) stores each post's numbers 24 hours and 7 days after it goes out. The Monday
  job `hq-social-review` (6:53 AM) reviews the week by funnel stage (new viewers, then follows, then saves and
  shares; sign-ups not measured yet), leaves suggestions on upcoming posts (never changing them by itself), picks one
  test for the week, writes **the plan for the week** in plain words (his ask: "this is the kind of reporting I want
  on the page"), and proposes edits to `content/social/LESSONS.md` as a PR; his merge is his OK. Starting targets:
  80% of reach from new viewers, 13 follows and 6 saves + shares per 1,000 new viewers; double down after two weeks
  at 2× median reach, cut after three below it (#1114, #1116, #1120).
- Run from the portal's **Platform → Social** (see [Coach portal](coach-portal.md#menu-shape)).

## MetHQ blog (metabolichq.app/blog)

Rules in `mac-app/content/blog/DRAFTING.md`:
- Every other Monday from Nov 23, 2026 (#675; previously described as the Mondays between coachbronson.com's posts;
  the dates didn't change). The daily go-live run works out what's due from the live
  metabolichq.app sitemap (no go-live log, nothing pushed, `contents: read`), builds the site from **the commit
  production runs** with only the blog posts and images from main, includes the site media, and checks the sitemap
  lists each post after the deploy (#679, #1122, both closed Nov 27, done in PR #1121 with his OK). (Previously it
  failed daily on "Save the go-live log" and deployed main's site past the staging gate.) First real go-live day
  with it: Mon Dec 7. A Run workflow option `build_only` builds without deploying. Claude drafts, Bronson approves
  (`hq-blog-draft` PRs, or **Approve** on the Content page); weekly email of anything awaiting approval.
- **Approve works on a draft that's behind main** (#1117, Nov 26): if GitHub can't merge at once, the draft is
  labeled `hq-blog-approved`, brought up to date, and `hqBlogMergeWork` (every 10 minutes) merges that exact commit
  once its tests pass. A draft waiting for a rewrite can't be approved. Draft PRs end with **Risk: low**, so a merged
  post isn't held 24 hours on staging (#1123).
- Coach's problem and real advice first; MetHQ comes in where it genuinely solves it, usually the last third, at most one
  short product section. 700–1,000 words, first person, coach to coach.
- One SEO keyword per post from real coach searches. CTA: `start` (default, free up to 5), `compare`, `premium`,
  `build`.
- **Product accuracy:** only what's live, checked against `site/llms.txt` and `site/index.html` (wearable sync is not
  live). Studies and stats web-checked and linked. Don't name competitors to criticize them; describe patterns with
  sources. Never invent coaches, clients or quotes.
- Covers: his Drive photo with the navy/teal MetHQ fade, logo, category tag, short title and one or two real app screens
  (`scripts/hq_cover.py`); a different photo every time, logged in `cover-images.json`.
- Published so far: AI vs. human coach, at-risk clients and signals, coaching-app revenue share, gamification and
  retention, coaching without spreadsheets, professional fitness coach. Approved Nov 24: "Your Online Coaching Tech
  Stack Is Costing You Clients" (dated Mon, Nov 23, #441) and "Who Owns Your Coaching History?" (goes live Mon,
  Dec 7, #949) (`content/blog/posts/`).
- Approved Nov 27: "The Add-On Tax: What Coaching Software Really Costs" (goes live Mon, Dec 21; its cover came from
  Drive; merged from the draft PR #1092, #983).
- Drafts are started at 7:10 AM Eastern by Google Cloud as a "Claude job" run (`hqBlogDraftsStart`, #983, #986;
  previously a Claude scheduled task).
- Queue (from coach complaints in Capterra/G2/App Store reviews and r/personaltraining): the app is part of your
  service; keto clients need more than a macro tracker;
  five apps, one client; clients feeling guilty for messaging; stop retyping call notes; reading glucose, ketones and GKI
  with training; the client overview that should exist; month to month as the default; coaching under your own brand;
  desktop for building, phone for coaching.

## Other marketing assets (artifacts)

MetHQ Promo Reel · MetHQ Comparison Chart · MetabolicHQ vs Everfit feature comparison · MetHQ Analytics report mockups ·
Zapier integration plan. Links: [Sources](../../sources/README.md).

## Related

[metabolichq.app site](marketing-site.md) · [Platform and brands](platform-and-brands.md) ·
[Content hub](../business/content-and-social.md)
