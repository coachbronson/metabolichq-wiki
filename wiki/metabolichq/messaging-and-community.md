---
title: Messaging, community and notifications
summary: Direct messages, multi-coach chats, photos, community feed, tagging and linking rules, push notifications, Deals
updated: 2026-11-27
sources: ["#410", "#1086", "#1110", notes, CHANGELOG, mac-app README, "#420", "#334"]
---

# Messaging, community and notifications

## Direct messages

- Clients message individual coaches by name. No set hours; coaches reply at their discretion. No AI in coach DMs.
- Text and photos; **photos deleted after 72 hours**.
- Coaches start a DM from a client's profile card or New message.
- Group chats are coaches-only additions: any chat can have more coaches added (by the client or any coach in it),
  never other clients. Coaches can be removed or leave; an added coach sees earlier messages.
- **Message the group** (v8.79.0, #410 stage B2, PR #1086): head coaches and a group's coaches write once to a whole
  group; each client gets an ordinary direct message from that coach in their own conversation, so replies come back
  one by one and nobody sees who else got it. No rules or server change.
- Planned: voice notes (#334).

## Community

- Community feed per space; feed topics managed from a **Community** menu in the portal (room for group management
  later). Round 2 ideas (#420): GIFs, media, link previews, scheduled posts, report.
- **A group's own feed** (v8.82.0, #410 stage C1, PR #1110, Nov 26): head coaches turn on **Own feed** on a group
  with a feed name its clients see (never the group's own name). Community shows **Everyone** and the client's group
  feeds as a switcher. Only the group's clients, its coaches and managers, and head coaches read and post there; the
  group's coaches and head coaches moderate. A client who leaves loses access and their posts stay. Group feeds have
  no workout posts, welcomes, topics or @mentions.
- Reactions other than 👏 now make a notice (they were refused by the rules; fixed in #1110).
- Circle is not integrated.

## Tagging and links

- `@` tagging in Community posts/comments.
- `/` resource linking for coaches in messages, comments, notes, and Community posts/comments (posting a resource in
  Community shares it with everyone who can see the post).
- Web addresses are clickable everywhere text appears.
- Coaches' Share menu in the app: Copy link / Send to client.

## Notifications

Web push for messages, calls, workouts and signals (per-person settings); notifications bell and Help in the header.
An install popup offers to add the app to the home screen (remembered once installed).

## Deals

Each space sets up its own Deals (not MPT-only). His affiliate links and discount codes: coachbronson.com/links.

## Related

[Resources and files](resources-and-files.md) · [Coaching calls](coaching-calls.md)
