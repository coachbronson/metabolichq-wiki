# Inbox: found outside the wiki

Lines Claude adds during work when it finds something the wiki lacks or has wrong. The nightly update files each one
into the wiki and removes it. Format: `- YYYY-MM-DD · what · source/reference`.
- 2026-11-25 · System documents updated for the release status signals (#575, mac-app PRs #1000–#1002): Detailed System Design (data flow F12, ports, interconnections, both diagrams re-rendered: new component and data flow PNGs in Drive › Documentation, linked from the doc), System Security Plan and Configuration Management Plan — set their Last reviewed to 2026-11-25 in wiki/metabolichq/system-documentation.md · Google Drive › Documentation; mac-app #575 comments
- 2026-11-25 · Releases pages (portal Platform → Releases, MetHQ Monitor) now update by themselves: release-signal.yml posts every PR and run status change to production's releaseSignal (GitHub OIDC token, no secret), and the pages ask `releases` since every 20 s and reload when it moved; live 11:46 AM Nov 25 · mac-app PRs #1000, #1001, #1002; #575
