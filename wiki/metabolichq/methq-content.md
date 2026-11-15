---
title: MetabolicHQ content and messaging
summary: MetHQ messaging framework, homepage "Replace your stack" structure, differentiators, social plan, blog rules and topic queue
updated: 2026-11-15
sources: [notes (Nov 12–13, 2026), MetabolicHQ homepage messaging preview artifact, mac-app content/blog/DRAFTING.md and blog-topics.md]
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
- Publer dropped (Nov 11); he approves each item; a social dashboard per brand is wanted.

## MetHQ blog (metabolichq.app/blog)

Rules in `mac-app/content/blog/DRAFTING.md`:
- Every other Monday, on the Mondays **between** coachbronson.com's posts (from Nov 23, 2026). Claude drafts, Bronson
  approves by merging (`hq-blog-draft` PRs); weekly email of anything awaiting approval.
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
  retention, coaching without spreadsheets, professional fitness coach.
- Queue (from coach complaints in Capterra/G2/App Store reviews and r/personaltraining): the app is part of your
  service; who owns your coaching history; the add-on tax at 5/15/45 clients; keto clients need more than a macro tracker;
  five apps, one client; clients feeling guilty for messaging; stop retyping call notes; reading glucose, ketones and GKI
  with training; the client overview that should exist; month to month as the default; coaching under your own brand;
  desktop for building, phone for coaching.

## Other marketing assets (artifacts)

MetHQ Promo Reel · MetHQ Comparison Chart · MetabolicHQ vs Everfit feature comparison · MetHQ Analytics report mockups ·
Zapier integration plan. Links: [Sources](../../sources/README.md).

## Related

[metabolichq.app site](marketing-site.md) · [Platform and brands](platform-and-brands.md) ·
[Content hub](../business/content-and-social.md)
