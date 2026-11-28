---
title: Coaching calls and scheduling
summary: In-app video calls (Daily), scheduling calendar and sync, recording/transcription rules, AI draft notes
updated: 2026-11-28
sources: ["#1151", "#1160", "#1177", "#1178", "#410", "#1107", "#1095", notes, CHANGELOG v5.0, #755, #787, #857]
---

# Coaching calls (v5.0)

- Video inside MetabolicHQ via **Daily**. Join button from 10 minutes before until 30 minutes after a call. Tested live
  Nov 7, 2026.
- **Always recorded and transcribed** as part of the coaching terms: clients get a reminder each time they join (not a
  choice). A client who doesn't want recording doesn't get the call. (Previously a per-call record choice.)
- Video recording deleted once transcribed; full transcripts kept.
- A recording is never lost (a notice from Daily that fails to save is answered with an error, so Daily resends) and
  never transcribed twice (each queued recording is claimed by one run; a stale claim is retried after 15 minutes)
  (#755, #787).
- AI drafts call notes; the coach reviews and publishes them on the client's **Coaching notes** page (newest first,
  latest 3 on the overview; each note tagged manual or transcribed).
- Clients see only the call summary and action items. Client data export includes call summaries only.
- Planned (medium): structured **SOAP notes** (Subjective, Objective, Assessment, Plan) for practitioners, dated,
  private to the coaching team, with the Objective section able to pull in current data (#857; related #637, #381).

## Scheduling

- Coaches start scheduling with a normal calendar: individual dates or a repeating series. No calls-per-month setting.
- Clients can only reschedule or cancel. Cancellation cutoff set per coach. Lengths 30, 45 or 60 minutes.
- Calendar sync: a direct Google connection and a subscribe link for any calendar.
- Multi-coach spaces: the client picks their coach. Partner coaches schedule their own clients.
- Notifications and reminders for scheduling, moves and cancellations.
- **Group calls** (v8.81.0, #410 stage B4, PR #1107, Nov 26): **Calls → New call** schedules a call for a
  group with a **title clients see** (never the group's name). Clients in the group at the time see it, can join one
  room of up to 50, and can't reschedule or cancel it; only coaches move or cancel it.
- **Group calls are recorded, with AI notes for coaches only** (#1095, PR #1151, his calls Nov 27; on staging, then
  production): once recordings are connected, everyone who joins, coaches included, is told it's recorded and must
  agree to get in; nothing standing is saved, so the next join asks again and someone who said Not now can come back
  and agree. Each agreement is kept with the person (in their data download, deleted with their account). The
  recording is transcribed and the video deleted. The AI writes a **coaches-only** note (topics, questions, wins,
  flags with who said them, one-to-one follow-ups, actions), with no client summary and nothing on any client's
  records; the call's coach is notified. Portal: Calls → the call → **Call notes**, to read with the transcript, edit
  and save. Client Terms and Privacy Policy updated Nov 27. A group transcript stays when one participant deletes
  their account (the coaches' record of a shared call; his to change). Not yet tried on a real recorded group call
  (#1095 "How this was resolved"). (Previously not recorded, no call notes; his call Nov 26.)
- **New call's Client or group box** is a type-to-search box: typing narrows to clients and groups whose names hold
  every typed word; groups show "Group call · N clients" (#1177, PR #1178, Nov 27).

## Related

[Messaging and community](messaging-and-community.md) · [Coach portal](coach-portal.md)
