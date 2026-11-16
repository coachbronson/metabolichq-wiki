---
title: Biometrics, check-ins and signals
summary: Biometrics metrics, daily check-ins, signals and patterns from combined data, aging rules, AI-on-data rule
updated: 2026-11-16
sources: [notes, CHANGELOG, mac-app README, "#603", "#602", "#629", "#630", "#631", "#644"]
---

# Biometrics, check-ins and signals

## Biometrics (v3.0)

- Manual entry: body composition, HRV / HRV-CV, glucose / MAGE, ketones, GKI, HR / RHR. Wearable data later
  ([Wearables](wearables.md)).
- Home tile: the week's average glucose, ketones, HRV and RHR, with add-data.
- The Biometrics page shows every metric; no per-client coach toggles.
- Planned: progress photos with coach comments (#602); optional cycle tracking as an add-on (#165).

## Check-ins

Daily check-in plus a session reflection. Check-in lives on Home only (not in the menu). Planned: save a check-in
partway with an end-of-day reminder (#603); coach-customizable questions (#157).

## Signals (v7.0)

- Fixed rules on a person's **own normal** (no AI): readiness, training load, combinations of check-ins, training log
  and effort, food diary and biometrics (`public/js/signals.js`, run by `functions/signalwork.js`).
- Alerts **and** wins: e.g. not recovering, early illness, workouts feeling harder, stress, short sleep, protein low,
  losing lean mass, not reaching ketosis, keto-adapted, body recomposition, better blood sugar control.
- **Patterns** link things like sleep and effort, or carbs and next-morning glucose.
- Aging: clear from Home; wins/patterns leave Home after 3 days, others after 7; safety signals stay until
  acknowledged; Signals page shows 90 days (older hidden, not deleted).
- Coaches see every client's signals; the coach can mute kinds and set thresholds per client.
- Planned: a "same weight for weeks or lighter than usual: check in" signal (#644); protocol/medication logging and
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
