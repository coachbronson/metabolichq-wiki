# Inbox: found outside the wiki

Lines Claude adds during work when it finds something the wiki lacks or has wrong. The nightly update files each one
into the wiki and removes it. Format: `- YYYY-MM-DD · what · source/reference`.
- 2026-11-20 · Nightly code review (owner): the fresh-session "Nightly CodeRabbit review" scheduled task is disabled. The pass now runs at ~12:06 AM ET in one ongoing Claude session that wakes itself each night. CodeRabbit still reviews mac-app, and Claude adds its own review of mac-app (in the same nightly-review PR and report, titles prefixed "Claude:") and of coachbronson-site (marker branch `claude-reviewed`, created at dc12429). The wiki gets a read-only check · chat 2026-11-20
- 2026-11-20 · Nightly JSON backup cron is 07:17 UTC: 2:17 AM Eastern in winter, 3:17 AM in summer (Architecture says ~3:15 AM ET) · mac-app .github/workflows/backup.yml
- 2026-11-20 · Gaps found writing #638 (in the SSP as open risks, no issues yet): production deploys with a long-lived JSON key (staging is keyless); Cloud Storage files aren't in either backup layer; secret rotation dates aren't recorded · #638 resolution comment
- 2026-11-20 · This repo is public on GitHub, but CLAUDE.md says "The repo is private" · GitHub repo settings
