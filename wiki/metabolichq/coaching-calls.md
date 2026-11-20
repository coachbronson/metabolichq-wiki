---
title: Coaching calls and scheduling
summary: In-app video calls (Daily), scheduling calendar and sync, recording/transcription rules, AI draft notes
updated: 2026-11-20
sources: [notes, CHANGELOG v5.0, #755, #787]
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

## Scheduling

- Coaches start scheduling with a normal calendar: individual dates or a repeating series. No calls-per-month setting.
- Clients can only reschedule or cancel. Cancellation cutoff set per coach. Lengths 30, 45 or 60 minutes.
- Calendar sync: a direct Google connection and a subscribe link for any calendar.
- Multi-coach spaces: the client picks their coach. Partner coaches schedule their own clients.
- Notifications and reminders for scheduling, moves and cancellations.

## Related

[Messaging and community](messaging-and-community.md) · [Coach portal](coach-portal.md)
