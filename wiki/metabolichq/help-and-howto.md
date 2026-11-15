---
title: Help, how-to videos and support
summary: The app's Help page, tagged how-to videos, Ask MPT Coach, support tickets, review rules after e2e runs
updated: 2026-11-14
sources: [notes, mac-app CLAUDE.md, public/js/help.js, e2e/howto/]
---

# Help, how-to videos and support

- Everything lives on the app's **existing Help page** (no separate support page): Help topics plus how-to videos,
  tagged and searchable by topic/functional area. All spaces may see the MPT/Coach Bronson-branded videos.
- Version number at the bottom, labeled BETA; "Hosted by MetabolicHQ" mark beside it.
- **Ask MPT Coach** from Help (Premium spaces only; see [MPT Coach](mpt-coach.md)).
- Help topics: `public/js/help.js`. Video scripts: `e2e/howto/videos.py`; re-made by the "How-to videos" workflow.
- **After every full end-to-end run**, check Help and video steps against what changed; fix and re-make as needed
  (first job of the next working session after a nightly run).
- Support: main coaches open tickets to MetabolicHQ (free-tier tagged); replies in portal and email; Support is also
  answerable from [MetHQ Monitor](methq-monitor.md).
- Planned: tell suggesters when their request ships, and announce launches (#423); user-facing release notes (#320).

## Related

[Engineering rules](../rules/engineering-rules.md)
