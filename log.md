# Log

Newest at the top. Each entry: date, what changed, pages touched.

## Open questions for Bronson

- **This wiki repo is public on GitHub** (repo settings; the rulebook said private and now says public). It links the
  system documents in Drive and describes security controls, scan exceptions and open risks. Keep it public, or make
  it private?

- **Friday social slot**: the content strategy's fifth pillar (Fridays) was the Masters Collective. What replaces it
  (an MPT pillar, more proof posts, or four posts a week)?

- **Book draft fixes** (v5): duplicate Sport Specific chapters, three different fat targets, and other edits listed
  on [the book page](wiki/business/new-essentials-book.md). Which fat target is the one he wants?

## 2026-11-21 — Nightly update

Covered mac-app from `218e79d` to `614f3eb` (CHANGELOG 2026-11-20 late entries and 2026-11-21, version still 8.70.1),
issues #319, #638, #816, #831, #847, #850, #853 and #866 closed (each "How this was resolved" read), 13 new backlog
issues (#856–#864, #866, #876, #877), 6 issues added to the roadmap, the #620 progress comments, mac-app CLAUDE.md
(two nightly reviewers, the system-documents rule, a quiet night skips only mac-app's steps), and the 4 inbox lines.
coachbronson-site: no commits since dc12429; no CLAUDE.md or README changes. Checked the O&M plan and Detailed System
Design in Drive against the new jobs and hosts (`mailStuckWatch`, Turnstile, USDA, Open Food Facts): they already list
them, so no document is behind.

- acquisition-readiness: phase 3 (client app) finished Nov 20, 3.3–3.13 (#815–#846), `start.js` (#849), app.js
  7,073 → 2,505 lines; phase 2 (portal) started Nov 21 (#874, #875, #878); #805 on the roadmap.
- architecture: 109 functions (`mailStuckWatch`, #829); the app split done and portal split begun; email: the Zapier
  route as it is in code (`functions/mail.js`) and the stuck-mail alert; deploys one at a time with the change-quota
  retry (#833); backup time 07:17 UTC and Storage not backed up (from the inbox); nightly review line.
- security: Nov 20 review fixes in rules (#819, #830), team invites (#825), CSP collector (#826); scan exceptions
  listing (#853–#855) and data.js scannable again (#867, #870); SSP open risks (from the inbox); owner handles legal
  review of public wording (#866).
- engineering-rules: "CodeRabbit" section is now "Nightly review (CodeRabbit + Claude)" (#838, #881, from the inbox);
  coverage index template fix (#842), #873/#876/#877, portal page wait (#852), Stripe-currency false negative (#839),
  deploy concurrency (#833).
- marketing-site: new Trust page section (#319, #865, #871, #866). research-and-privacy: wearables deletion (#817),
  owner report without conversation text (#818), privacy policy Settings paths and new providers (#869), Trust page.
  help-and-howto: Trust and policy links (#872), Nov 20 review (#834). mpt-coach: owner report (#818, #834).
- coach-portal: Spaces table fixed (#851), Platform pages file, owner email from config. training: late-load fix
  (#848), planned #863/#864. wearables: disconnect always works (#821), server-only link (#819). biometrics-and-signals:
  safety check slots (#820), planned #856/#859. partner-program: go-live retries (#828), refund and expiry fixes (#822,
  #823), MPT Programming keys (#824), custom builds idea (#862). spaces-and-roles: invites (#825), delegated admins
  (#861). nutrition (#858), resources-and-files (#860), coaching-calls (#857).
- versions: current 8.70.1 on Nov 21; Nov 20–21 timeline. roadmap-and-backlog: snapshot refreshed (97 open backlog,
  8 high, 14 on the roadmap).
- CLAUDE.md: says the repo is public (it is; from the inbox). Inbox emptied.
- Noticed: #686 is still open on GitHub though #851 fixed it (like #678 and #740).
- New open question: whether this repo should stay public.

Last update covered: 2026-11-21.

## 2026-11-20 — SSP replaced; link updated (mac-app #867)

The owner had the System Security Plan replaced with an updated copy (new link): §5 "Secure development" now says
every scanned file must be fully parsed (public/js/data.js was unscanned until mac-app #867; #870) and that the nightly
scan lists the lines each reviewed exception covers (#854). The old document is in Drive's trash. Last reviewed stays
2026-11-20. Pages: system-documentation (SSP link).

## 2026-11-20 — Rule: keep the system documents current

Owner's rule: significant changes to security, components, operations, configuration or resources update the
matching Drive document in the same work. Pages: engineering-rules (new section), system-documentation, CLAUDE.md
(nightly lint flags documents older than the change).

## 2026-11-20 — System documentation pointer (#638)

The #638 documents (SSP, configuration, change and resource management, O&M plan, detailed system design, diagrams)
went into Google Drive › Documentation, not the wiki (owner's call). Added a pointer page.

- New: system-documentation (links, what each covers, last-reviewed dates); index line added.
- security: #638 moved from Open to a pointer to the SSP.
- sources/README: Documentation folder added.

## 2026-11-20 — Nightly update

Covered mac-app from `ea7def7` to `218e79d` (CHANGELOG 2026-11-19 late entries and 2026-11-20, version still
8.70.1), issues #751–#757, #806 and #808 closed (each "How this was resolved" read), 3 new issues (#785, #805,
#816), #805 labeled backlog and high, the #620 progress comments, and the 1 inbox line. coachbronson-site: only the
automated newsletter send log (Nov 19); no CLAUDE.md or README changes in either repo.

- acquisition-readiness: phase 1 (server) finished Nov 19 (#762–#779), the endpoint check (#758), exceptions move
  with code (#768); phase 3 (client app) next by owner's direction, 3.1 and 3.2 done (#780, #809); the full
  functional audit after the split (#805).
- architecture: Server code rewritten (108 functions, `index.js` only re-exports, app split started); daily retry
  jobs `coachPayWork` and `wearablesForgetWork` (#791, #794, #795).
- security: Semgrep `--verbose` and 30 s per rule (#756, #759, #760), icon `nosniff` (#761), reviewed exceptions
  (#760, #783, #768); the Nov 20 review's twelve OK'd fixes under Open (#816).
- research-and-privacy: account deletion and the wearables server (#754, #790, #791). coaching-calls: recordings never
  lost or transcribed twice (#787). partner-program: go-live fixes (#752, #797–#800) and coach payment edge cases
  (#751, #792–#796). mpt-membership: resend, checkout flow, welcome post (#753). spaces-and-roles: client-account flag
  in one transaction (#803, #808), Getting started card (#788). coach-portal: Get help starts empty (#789).
- marketing-site: demo pages must match the app; CCI and Ovadia corrected (#781, from the inbox).
- engineering-rules: coverage index refiling (1,499 → 1,503, owner's OK, #786) and #785; e2e report push retry
  (#782) and `menuGo` wait (#807); how OK'd nightly questions are fixed (#751–#757, #816).
- versions: current 8.70.1 on Nov 20; Nov 19 timeline. roadmap-and-backlog: snapshot refreshed (88 open, 8 high).
  index: acquisition-readiness line. Inbox emptied.
- No new open questions.

Last update covered: 2026-11-20.

## 2026-11-19 — Nightly update

Covered mac-app from `0cc98d3` to `ea7def7` (CHANGELOG 2026-11-18 late entries and 2026-11-19, version 8.70.1),
issue #716 closed, 2 new issues (#742, #746), #570 taken off the roadmap, the #620 and #381 comments, and the 7 new
inbox lines. No coachbronson-site commits since #39; no mac-app CLAUDE.md or README changes.

- acquisition-readiness (**new**): #620's assessment, the owner's Nov 18 decisions (accepted risks, Stripe account
  and Google Cloud project stay, both QR-code copies kept), what's open, and the file split (phase 0 checks, phase 1
  server split #718–#741).
- architecture: fixed a stale Repositories row (the site deploys into its own project); project keeps its name
  (#620); Firebase default addresses (mac-app `.firebaserc`); new Server code section.
- security: #716 done (scan flags a weakened CSP); new Code scanning section (#720, #729, #730, #736, #737, #741);
  the `clientAcctOn()` rules fix (#740) replaces the #678 Open line.
- hipaa: #381's plan, cost research and BAA email options (nothing decided). wearables: vendors' BAA terms.
- marketing-site: CCI demo page (#743–#745, #747). partner-program: CCI prospect, the client waiver as it is in code,
  coach-written waivers (#746), MCP skill toolkit (#742).
- versions: current 8.70.1 (#722); Nov 18 timeline. help-and-howto: Nov 18 Help review.
- roadmap-and-backlog: snapshot refreshed (87 open, 7 high). index updated; inbox emptied.
- Noticed: the inbox held 9 lines from Nov 17 that the Nov 18 update had already filed (a session wrote back an old
  copy); they were checked against the pages and removed. #678 is still open on GitHub though #740 fixed it.
- No new open questions.

Last update covered: 2026-11-19.

## 2026-11-18 — Nightly update

Covered mac-app from `16b37c2` to `0cc98d3` (CHANGELOG 2026-11-17 late entries and 2026-11-18, version 8.70.0),
issues #550 and #711 closed, 5 new issues (#686, #699, #710, #711, #716), #410 raised to high, mac-app CLAUDE.md
(status updates say when), coachbronson-site #35–#39 and the #30 progress note, and the 11 inbox lines.

- security: new Content-Security-Policy section (enforced on all three sites, styles-only inline, #693/#697/#708,
  fixes #702/#704, follow-up #716); MetabolicHQ's own Turnstile widget (#684); the scan and removal-script line
  rewritten now that #676 ran and the old address is deleted (#695, #696); stale coachbronson-site App Check line
  replaced.
- coachbronson-site: removal script run, old address deleted Nov 17, Resend still shared (own Resend on hold until
  July 2027, draft #35), rebuild to-do progress (own Turnstile, new form snippets), `invoker: 'public'` (#36),
  `X-Site-Auth` (#37), Kiltz page removed (#38), privacy plugin off (#39).
- architecture: the site's leftovers removed, the one shared key, own Turnstile.
- marketing-site: CSP enforced; new Sales demo pages section (Kiltz, Ovadia; visual only, #694, #698, #703); brand
  widget "on MetabolicHQ" and SVG logo fix.
- spaces-and-roles (new Business name and main coach section) and coach-portal (new Your brand section): business
  name change (8.69.0, #700), Change the main coach via support (8.70.0, #701, #711), app name separate (#710),
  Platform tool (#699); portal CSP and #686.
- platform-and-brands: partners run their spaces "on MetabolicHQ" (#703, #705–#707). partner-program: Ovadia
  prospect and demo page; invites say on MetabolicHQ.
- versions: current 8.70.0; Nov 17 timeline. mpt-membership: test-mode trial is card only (#688). help-and-howto: Nov
  17 review, Your brand Help. engineering-rules: status-update rule (#715), e2e can't see local-only hosts, privacy
  plugin off. roadmap-and-backlog: snapshot refreshed (86 open, 7 high). index updated; inbox emptied.
- No new open questions.

Last update covered: 2026-11-18.

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
