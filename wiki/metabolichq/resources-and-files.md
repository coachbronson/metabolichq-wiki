---
title: Resources and shared files
summary: Coach resource libraries, / linking and sharing rules, worksheets and timed release, private coach–client files
updated: 2026-11-28
sources: ["#1131", "#1135", "#1081", "#157", notes, CHANGELOG, "#1012", "#1045", "#1060", "#1062", "#156", "#491", "#410", "#431", "#332", "#860"]
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
- **Drip for existing clients** (v8.84.0, #491, PR #1134, closed Nov 27): two more release rules for items and
  sections, beside "on a date" and "N days after joining". **Days after being added**: each client counts from the
  day they were added to that collection (named or through a group); taken out and added back keeps their first day;
  clients already in a collection started from the day it shipped. **After an earlier item**: once the client opens
  it (or sends it, for a worksheet), plus any days set; picked with **Waits for…**. A rule that waits for itself or
  loops is refused on save. Clients see "Opens after you open/send “…”"; the portal's client Files tab says what
  each waiting item waits for. His calls, Nov 27: coaches add clients (named or by group); late joiners on
  date-based collections see everything so far; one notice per collection per day; programs kept out ("started
  their program" moved to R&D, #1131). The "added" day is a server-only record (`spaces/{sid}/resEnroll`), deleted
  with the client's account (#491 "How this was resolved").
- **Client view** (a coach's View as a client) shows Resources on Files: every collection in the space, as a client
  added today sees it (timed sections locked, drafts hidden, worksheets read-only) (v8.84.1, #1135, PR #1136; his
  call, Nov 27).
- Later: search in the `/` list (#431), drip from a client's program start (R&D, #1131), search in the `/` list (#431), coach-customizable onboarding workflows (#332).

## Shared files (coach ↔ client)

- A private folder per coach–client pair: only those two can see it (head coaches can't see other coaches' folders).
- A client with several coaches has a separate folder per coach. 1 GB per client.
- Files can be saved to the device and exported. A coach who's unassigned loses all access, including export.

## Related

[Messaging and community](messaging-and-community.md)
