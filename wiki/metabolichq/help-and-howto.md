---
title: Help, how-to videos and support
summary: The app's Help page, tagged how-to videos, Ask MPT Coach, support tickets, review rules after e2e runs
updated: 2026-11-25
sources: ["#972", "#951", "#910", "#918", "#920", "#925", "#320", "#321", notes, mac-app CLAUDE.md, public/js/help.js, e2e/howto/, "#616", "#618", "#645", "#649", "#654", "#655", "#685", "#700", "#701", "#722", "#834", "#872", "#840", "#885"]
---

# Help, how-to videos and support

- Everything lives on the app's **existing Help page** (no separate support page): Help topics plus how-to videos,
  tagged and searchable by topic/functional area. All spaces may see the MPT/Coach Bronson-branded videos.
- Version number at the bottom, labeled BETA; "Provided by MetabolicHQ" mark beside it (v8.66.3; previously
  "Hosted by", #618). Under them, links to the **Privacy Policy** and **How your data is handled** (the Trust page,
  metabolichq.app/trust), each in a new tab; new FAQ answers for clients and coaches link the Trust page, and the Help
  journey checks both links and that searching "trust page" finds the FAQ (#319, #872). A **Status** link sits
  beside them, and the FAQ "Is the app down?" (in the app and the portal's Help) points to status.metabolichq.app,
  then your own connection, then Contact support (#321, #918).
- The version line reads "Version BETA 8.71.1 · What's new" and opens **What's new**, the release notes grouped by
  day; coaches see clients' and coaches' notes with Everything / For clients / For coaches chips. The portal's Help has
  a third tab, **What's new** (#320, #920; see [Versions](versions.md)).
- The Privacy Policy and Terms are site pages now (metabolichq.app/privacy and /terms); the app's old addresses
  redirect, so Help's links keep working (#925).
- **Ask MPT Coach** from Help (Premium spaces only; see [MPT Coach](mpt-coach.md)).
- Help topics: `public/js/help.js`. Video scripts: `e2e/howto/videos.py`; re-made by the "How-to videos" workflow.
- **Coach portal Help** (v8.67.0, #645): the same `help.js` feeds a ? on every portal page, with **Coach portal** and
  **Client app** tabs. Coach walkthroughs name their portal pages in a `portal` field. How-to video **Help in the
  coach portal** (`portal-help`, 32 s) and the end-to-end journey **Portal Help** (areas portal and messaging) came
  with v8.67.1 (#649).
- **After every full end-to-end run**, check Help and video steps against what changed; fix and re-make as needed
  (first job of the next working session after a nightly run). The review now covers the portal's Help too: a new
  portal page gets a coach walkthrough, and portal videos (`PO` in `videos.py`) are checked like the app's (mac-app
  CLAUDE.md rule 8, #649).
- Help review Nov 16 (v8.68.1): the Program calendar walkthrough explains pending review workouts and approving them
  from the workout menu; One-on-one workouts gets the same shortcut (#654). The "skip" how-to video taps card Skip, so
  its recording may show the old error and should be re-made (#655).
- Help review Nov 17: nothing to change (#685). The "Your brand and sign-up link" topic and the `your-brand` video
  steps were updated with the Business name and Change the main coach cards (#700, #701).
- Help review Nov 18 (v8.70.1): the Your brand walkthrough and video already matched; the coach portal walkthrough's
  menu list now says Your brand holds the sign-up link, business name, logo and colors. No MPT Coach changes (#722).
- Help review Nov 20: Help walkthroughs, portal Help and video scripts still matched (mostly code moves and the
  #816 fixes); MPT Coach's rules now say the owner's report shows no question or answer text (#834).
- Help review Nov 21: everything still matched, including the new Privacy Policy and Trust page links and their FAQ
  answers (#872). MPT Coach got test question 50: who can see my data and where to read how it's handled (#885).
- Help review Nov 22: Help, videos and MPT Coach still matched the portal moves, the Clients list fix (#891) and the
  tripwire (#910).
- Help review Nov 23 (v8.71.1, #951): a new client walkthrough **What's new in the app** (the version line at the
  bottom of Help is the way in; no Take me there button); the portal walkthrough **Help in the coach portal** now
  describes the What's new tab and the version line under the menu; MPT Coach test question 51 (where to see what
  changed). The portal Help video's steps are unchanged and it doesn't show the What's new tab (CHANGELOG 2026-11-23).
- Help review Nov 24: nothing to change; review marker moved to 5b65fe1 (#972).
- Code: Help, the FAQ and contact support are in `public/js/page-help.js` since the app split (#840).
- Support: main coaches open tickets to MetabolicHQ (free-tier tagged); replies in portal and email; Support is also
  answerable from [MetHQ Monitor](methq-monitor.md).
- Planned: tell suggesters when their request ships, and announce launches (#423). (User-facing release notes done
  Nov 22, #320.)

## Related

[Engineering rules](../rules/engineering-rules.md)
