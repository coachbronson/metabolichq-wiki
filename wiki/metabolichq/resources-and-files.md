---
title: Resources and shared files
summary: Coach resource libraries, / linking and sharing rules, worksheets and timed release, private coach–client files
updated: 2026-11-27
sources: ["#1081", "#157", notes, CHANGELOG, "#1012", "#1045", "#1060", "#1062", "#156", "#491", "#410", "#431", "#332", "#860"]
---

# Resources and shared files

## Resources (#156, closed 2026-11-14; stage 3 in #607)

- On the **Files** page: clickable tiles per resource area (by topic or group), each opening its own file area.
  Managed in the coach portal; coaches can also work with libraries in the app.
- Linked by typing **`/`** (reads like a file directory). Linking to an individual client auto-shares the item; group
  links don't. If a coach shares something a client can't be given, the coach gets an error with the reason.
- Stage 2 shipped: **worksheets** and **timed release**. Worksheet answers are kept out of research releases; the
  assigned coach and head coaches read answers; no reminders yet.
- Stage 3 (#607, low): an MPT resource pack for Premium spaces, MPT Coach pointing to pack items, recipe collections
  once recipes exist.
- **A whole section comes out together** (drip content, #860, PR #1012, Nov 25): a collection's section can be timed
  once (on a date, or N days after the client joined), so a week's video, notes and worksheet arrive at once. Clients
  see an upcoming section locked, with its day and how many items are coming; the morning notice names the section.
  Coaches can make a video or link, notes or a worksheet straight into a section and move items and sections. His
  calls: video is an embedded link (YouTube, Vimeo, Loom), not an upload; no per-item overrides in a timed section;
  existing collections left as they are (#860).
- **‹ Files** in a collection goes to Files, and a client with more than one coach sees **‹ All folders** after
  opening a folder from the list (#1060, #1045, PR #1062, Nov 26).
- **Shared with a group** (v8.78.0, #410 stage B1, PR #1081, Nov 26): a collection's **Who sees it** lists the
  space's groups (head coaches: every group; other coaches: groups they coach or manage), shown as "Group: Masters
  (3 clients)". The server checks group membership when a client asks; clients who join get the usual "New in
  Resources" notice, and leaving takes the collection away at once. A form for one group is a worksheet shared this
  way (his call, Nov 26; #157).
- Later: timed release from enrollment/program start or "after the previous section" (#491), search in the `/` list (#431), coach-customizable onboarding workflows (#332).

## Shared files (coach ↔ client)

- A private folder per coach–client pair: only those two can see it (head coaches can't see other coaches' folders).
- A client with several coaches has a separate folder per coach. 1 GB per client.
- Files can be saved to the device and exported. A coach who's unassigned loses all access, including export.

## Related

[Messaging and community](messaging-and-community.md)
