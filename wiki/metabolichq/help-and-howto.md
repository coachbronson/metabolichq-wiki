---
title: Help, how-to videos and support
summary: The app's Help page, tagged how-to videos, Ask MPT Coach, support tickets, review rules after e2e runs
updated: 2026-11-16
sources: [notes, mac-app CLAUDE.md, public/js/help.js, e2e/howto/, "#616", "#618", "#645", "#649"]
---

# Help, how-to videos and support

- Everything lives on the app's **existing Help page** (no separate support page): Help topics plus how-to videos,
  tagged and searchable by topic/functional area. All spaces may see the MPT/Coach Bronson-branded videos.
- Version number at the bottom, labeled BETA; "Provided by MetabolicHQ" mark beside it (v8.66.3; previously
  "Hosted by", #618).
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
- Support: main coaches open tickets to MetabolicHQ (free-tier tagged); replies in portal and email; Support is also
  answerable from [MetHQ Monitor](methq-monitor.md).
- Planned: tell suggesters when their request ships, and announce launches (#423); user-facing release notes (#320).

## Related

[Engineering rules](../rules/engineering-rules.md)
