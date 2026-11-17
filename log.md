# Log

Newest at the top. Each entry: date, what changed, pages touched.

## Open questions for Bronson

- **Friday social slot**: the content strategy's fifth pillar (Fridays) was the Masters Collective. What replaces it
  (an MPT pillar, more proof posts, or four posts a week)?

- **Book draft fixes** (v5): duplicate Sport Specific chapters, three different fat targets, and other edits listed
  on [the book page](wiki/business/new-essentials-book.md). Which fat target is the one he wants?

## 2026-11-17 — Nightly update

Covered mac-app from `f57f5d7` to `16b37c2` (CHANGELOG 2026-11-16 late entries and 2026-11-17, version 8.68.2),
issues #567, #655, #668 closed and #646 closed for the full split, 9 new issues (#657, #660, #666, #667, #678, #679,
#681; #655 and #668 already closed), mac-app CLAUDE.md (self-contained, one area per PR, coverage index, a wrong test
result is never a pass), coachbronson-site #29 and #32–#34 (README, CLAUDE.md, `scripts/split/README.md`, to-do #30),
and the 5 inbox lines.

- coachbronson-site: rewritten for the full split: own project `coachbronson-site`, coachbronson-site.web.app,
  coachbronson.web.app deleted (not redirected), no `mptDeals`, rebuild to-do, cut-over in the site's own project.
- architecture: domains row, the site's project, removal PR #676, deploy CLI 15 vs emulators 14.23.0, Cloud Run quota
  retry (#668).
- marketing-site: MPT links stay on metabolichq.app/mpt (#672); the old "moves to coachbronson.com/mpt" line removed.
- security: scan/authorized-domains line now notes open #676; #678 under Open.
- methq-monitor: Content review is the MetHQ blog only (#673); Quality shows red on any failed journey.
- engineering-rules: one area per PR, self-contained MetabolicHQ, coverage index, a wrong test result is never a pass,
  outside services through workflows and MCP; blast-radius search no longer spans both repos.
- versions: current 8.68.2; Nov 16 timeline; #681 proposal under After beta.
- roadmap-and-backlog: snapshot refreshed (83 open, 5 high).
- coach-portal: Program calendar workout menu (#653, #683). program-library-import: approving from the menu.
- training: card Skip/Undo fix (#655). nutrition: #666 known bug; #355 corrected to medium. mpt-membership: trial
  cancel returns to metabolichq.app (#674). methq-content: Monday wording (#675), go-live log failure (#679).
  help-and-howto: Nov 16 Help review, skip video to re-make. coach-bronson-content: newsletter deals from the site's own
  list. natalie: mock-up address. index updated; inbox emptied.
- Removed the open question on coachbronson.com and sign-in: the site README's step 7 now refers to the site's own
  project, so it no longer contradicts #613.
- Noticed: the site's `content/NEWSLETTER.md` still says the deal comes from the MPT app's Deals, while its README says
  the built-in list; the wiki follows the README.

Last update covered: 2026-11-17.

## 2026-11-16 (in-session)

- Added the definition of end-to-end testing (every function, button, field and display; index of all of them kept
  current) to [Engineering rules](wiki/rules/engineering-rules.md). Source: notes.

## 2026-11-16 — Nightly update

Covered mac-app from `1fdafdb` to `f57f5d7` (CHANGELOG 2026-11-15 late entries and 2026-11-16, version 8.67.1),
issues #514, #515, #623, #626 closed and #548 moved into #512, 17 new issues, mac-app CLAUDE.md (read the wiki first;
Help review covers the portal), coachbronson-site #26–#28, and the 12 inbox lines.

- versions: current 8.67.1; 8.66.2–8.67.1 in the timeline.
- security: rewritten around what's live: security events and sign-in/Google Cloud alerts (alert-only), the Security
  page, staging's own deploy account (#626); open work now in #512 (lockout around Nov 29, App Check).
- coach-portal: Help ? on every page, Security page, Roadmap type badges and Show chips, demo data, #648.
- help-and-howto: "Provided by MetabolicHQ"; portal Help, its video and the review rule.
- methq-monitor, architecture: Security tab; staging account, security jobs, site functions account.
- platform-and-brands, partner-program, marketing-site: "Provided by" badge and agreement 7.5 (#618); logo files;
  homepage demo video (#636); coach add-on marketplace and GLP-1 companion plans (#633, #628).
- client-add-ons: new coach add-ons section; #382 header fixed to medium. biometrics-and-signals: planned signals.
- spaces-and-roles (new Demo spaces section), casey-ruff: demo data seeding (#647, #652) and Smitty Fitness.
- coachbronson-site: decided split into its own Google Cloud project (PRs open, awaiting his OK); #27, #28.
- New page: wiki/business/video-production.md (demo video, Artlist voice, Riverside, real footage, YouTube route).
- engineering-rules: read the wiki first. roadmap-and-backlog: snapshot refreshed (77 open). index, sources, content
  hub updated; inbox emptied.

Last update covered: 2026-11-16.

## 2026-11-15 — Wiki is a starting point; inbox added

- CLAUDE.md: new section saying the wiki is a starting point (memory, conversation and sources still count) and that
  anything found outside it goes in `inbox.md`; the nightly update now processes the inbox (step 3).
- New `inbox.md`, seeded with the logo files in Drive and the MetHQ demo video decisions.
- index.md: pointer to the inbox. (notes, chat 2026-11-15)

## 2026-11-15 — Nightly update

Covered mac-app from `a58bf06` to `1fdafdb` (CHANGELOG 2026-11-14 late entries and 2026-11-15, version 8.66.1),
issues #404, #595 and #322 closed, #548 progress, roadmap labels on #570 and #575, and coachbronson-site #24/#25.

- versions: current 8.66.1.
- security: App Check stage 1 reverted and the next plan (#548); API key restricted (#595 done); security.txt and
  /security page (#322); coachbronson.com counted as ours (#613).
- roadmap-and-backlog: snapshot refreshed (63 open).
- marketing-site, architecture: Coach Bronson links go to coachbronson.web.app via `COACHBRONSON_URL` (#611).
- coachbronson-site: domain contract ends July 2027; cut-over steps for MetabolicHQ (site #25, #613).
- spaces-and-roles: client view belongs to one account (#404).
- New open question: site README step 7 vs #613.

Last update covered: 2026-11-15.

## 2026-11-15 — Masters Collective wiped

Cleanup ran (mac-app #615): 3 memberships ended, 14 codes off, 18 records deleted; the unused coupon stays. Pages:
mpt-membership, platform-and-brands, offers, coachbronson-site.

## 2026-11-15 — Book

Ingested the book draft *The New Essentials of Sports Nutrition* v5 (Oct 12 2026). New page:
wiki/business/new-essentials-book.md. Changed: coaching-methods, books-and-research, sources, index.

## 2026-11-15 — Content and artifacts

Added the Content Strategy & 13-Week Calendar doc, the MetHQ homepage messaging preview, both blog drafting guides and
topic queues, and an index of all claude.ai artifacts. New pages: wiki/business/coach-bronson-content.md,
wiki/metabolichq/methq-content.md. Changed: content-and-social (now a hub), writing-and-brand-rules, sources, index.

## 2026-11-14 (evening) — Bronson's answers

- #156 closed with a resolution note; stage 3 moved to #607. Page: resources-and-files.
- Masters Collective is being shut down and wiped. Pages: platform-and-brands, mpt-membership, offers,
  content-and-social, coachbronson-site, coach-portal, messaging-and-community, index.
- Wearables: still undecided between Terra and Junction. Page: wearables.

Last update covered: 2026-11-14.

## 2026-11-14 — Wiki created

Built from Claude's memory notes (Workout App, social/website and S&C book projects), mac-app at commit `a58bf06`
(CHANGELOG through 2026-11-14, README, CLAUDE.md, version 8.65.0), coachbronson-site at `d1d1af7`, and the 68 open
backlog issues. Pages: everything in `index.md`.

Last update covered: 2026-11-14.
