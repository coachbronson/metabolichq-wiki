---
title: Biometrics, check-ins and signals
summary: Biometrics metrics, daily check-ins, signals and patterns from combined data, aging rules, AI-on-data rule
updated: 2026-11-27
sources: ["#157", "#1093", notes, "#1013", "#1014", "#1016", "#1017", "#1020", "#1025", "#1026", "#1052", "#1054", CHANGELOG 2026-11-25, CHANGELOG, mac-app README, "#603", "#602", "#629", "#630", "#631", "#644", "#820", "#856", "#859"]
---

# Biometrics, check-ins and signals

## Biometrics (v3.0)

- Manual entry: body composition, HRV / HRV-CV, glucose / MAGE, ketones, GKI, HR / RHR. Wearable data later
  ([Wearables](wearables.md)).
- Home tile: the week's average glucose, ketones, HRV and RHR, with add-data.
- The Biometrics page shows every metric; no per-client coach toggles.
- **Phase angle** (degrees, higher is better) and **visceral fat** under Add data → More metrics (#856, PRs #1013,
  #1014, Nov 25). Visceral fat has a **Level / Amount / Area** choice, as the scale or scan reports it: a level (BIA
  scales such as Tanita, InBody, Omron), an amount in the person's weight unit (DEXA) or an area in cm² (some InBody
  models); his choice of a level/amount toggle, with Area added for InBody (#856). Each is its own metric with its own
  tile and chart; Amount and Area tiles show once logged. Coaches see them in the app and the portal. Signals for them
  are #1016; syncing them from BIA scales is #162.
- **When was this taken?** on Add data is a dropdown: Not set, fasted and the other times, plus **After waking** and
  **Before bed** (#1054). Fasted-glucose logic still uses only fasted.
- Planned: progress photos with coach comments (#602, on the roadmap since Nov 25); optional cycle tracking as an
  add-on (#165).

## Check-ins

Daily check-in plus a session reflection. Check-in lives on Home only (not in the menu).

- **A custom check-in per space** (v8.80.0, #157 closed Nov 26, PR #1093): head coaches make **one** custom
  check-in for their whole space on **Space settings → Daily check-in**, starting from the default (the 8 ratings
  and hours slept). They can reword, reorder or remove questions, change the words for 1 and 5, and add questions
  of six types (rating 1–5, number with a unit, yes/no, choice, short answer, long answer), up to 30. **Save and use
  it** replaces the default for every client; **Use the default** goes back at any time and keeps the questions to
  turn on again. Other coaches see which one is used but can't change it. Coaches read the answers on a client's
  Check-ins tab and the day views; both data exports get `checkin_answers`. Built-in ratings a form keeps still feed
  trends, readiness, signals and cohort reports; each answer stores the question as asked (#157 "How this was
  resolved").
- **No forms by group** (his call, Nov 26): one check-in per space, no per-group or per-coach forms. A form for one
  group is a Resources worksheet shared with the group. That dropped #410 stage B3, check-ins by group (#157, #410).

- **A self check-in**, for the client's own awareness, not a report to the coach (his call, Nov 25; #603). The
  "your coach sees it" wording is gone (#1025).
- **Notes are private** (v8.72.0, #1020): each note is its own item with its time, under **Your notes**; **Share with
  coach** / **Stop sharing** per note; delete but not edit. Coaches see only shared notes (portal Check-ins tab,
  overview, day view, the coach app's day view; the coach export leaves out unshared notes). Notes written before
  were moved and marked shared, since they were written under "your coach sees it" (#1020).
- **Save partway and Skip** (v8.73.0, #1025): each question has Skip; a check-in with questions left is unfinished;
  Home shows "Unfinished · N left · Finish" or "Checked in today ✓". No separate draft: a check-in is saved, not sent
  (his call, #603).
- **Check-in reminders** (v8.74.0, #1026): Settings → Check-in reminders, the days (none by default) and the time
  (8 PM by default) in the phone's time zone. A phone notification on those days when today's check-in isn't done,
  and any day for one saved unfinished; never at or after 11 PM, once a day, never showing answers
  (`checkinReminders`, every 15 minutes).
- **Session reflection notes stay shared** with the coach and with their workout (his call, Nov 25, #1017); the
  wrap-up sheet says "Shared with your coach: your rating, effort and notes." (v8.74.1, #1052).

## Signals (v7.0)

- Fixed rules on a person's **own normal** (no AI): readiness, training load, combinations of check-ins, training log
  and effort, food diary and biometrics (`public/js/signals.js`, run by `functions/signalwork.js`).
- Alerts **and** wins: e.g. not recovering, early illness, workouts feeling harder, stress, short sleep, protein low,
  losing lean mass, not reaching ketosis, keto-adapted, body recomposition, better blood sugar control.
- **Patterns** link things like sleep and effort, or carbs and next-morning glucose.
- Aging: clear from Home; wins/patterns leave Home after 3 days, others after 7; safety signals stay until
  acknowledged; Signals page shows 90 days (older hidden, not deleted).
- Coaches see every client's signals; the coach can mute kinds and set thresholds per client.
- Safety signals are checked right after a client saves a reading (up to 30 times an hour; the hourly job covers the
  rest). Each check reserves its slot first, and a closed space's clients are skipped (#816 item 5, #820).
- Planned: a "same weight for weeks or lighter than usual: check in" signal (#644); a signal that tells the coach
  when a client's progress would make a good testimonial (#859, medium); protocol/medication logging and
  GLP-1 signals with a dose-change adjustment window, part of the GLP-1 coach add-on (#629–#631; see
  [Client add-ons](client-add-ons.md#coach-add-ons-planned)).

## Rule for device data and AI

Device data never goes raw into an LLM or ML. AI may help define the relationships and algorithms the data is judged
by, and may analyze the outputs of those equations.

## Portal client overview

Highlights every category: training (consistency, recovery), biometrics (glucose, GKI, ketones, RHR), check-ins (last
10 days' averages and count), nutrition (last 10 days' macro averages and % whole food), plus coaching notes.

## Related

[Nutrition](nutrition.md) · [Coach portal](coach-portal.md) · [Research and privacy](research-and-privacy.md)
