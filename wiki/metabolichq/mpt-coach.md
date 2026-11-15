---
title: MPT Coach (AI coach)
summary: Who gets the AI coach, what it answers, safety rules, privacy, limits, model, sources and paid extras
updated: 2026-11-14
sources: [notes, CHANGELOG v8.0, functions/coach/, "#383", "#326", "#254"]
---

# MPT Coach (v8.0)

## Who and what

- Named **MPT Coach**; neutral and labeled as AI.
- Available in the MPT space and partner spaces with the **MPT Programming add-on** only. Coaches can't change or turn
  it off. Clients only; coaches get no insight into AI output.
- Per-exercise **Ask** and a general chat. Answers exercises, scaling and progressions, equipment, swaps and how hard
  to go — from Coach Bronson's material (movement standards, scaling playbook, intensity principles, guided swaps, his
  video transcripts; see `functions/coach/`).
- Also answers **app help** from the Help content ("Ask MPT Coach" on the Help page).
- Offers swaps the client confirms with a tap (and "Always swap this").

## Safety

- Known/old limitations (e.g. knees, an old shoulder injury) → swaps that avoid them.
- New, sharp or worsening pain, or recovering from an injury → a **fixed safety message**.
- May explain effort/burn vs. pain that means stop.
- Pain alert to the coach only if the client chooses "let my coach know" → portal Inbox and email.

## Privacy and limits

- Conversations are private to the client; coaches can't read them. Kept while the client is active; deleted with the
  account; included in data export.
- **10 questions per client per day**, shared between training and app-help questions.
- Bronson gets an anonymized cross-space report. A counts-only summary for partner coaches is low-priority (#326).

## Model and sources

- Launched on **Gemini** (Vertex AI); test Claude on Vertex later.
- Training sources: Google Drive folder "AI Training" (Coaching and Training, Exercises and Movement, Scaling and
  Progression) and YouTube transcripts pulled by a server job.

## Ideas

- Paid add-on for extra daily questions (#383), possibly with an expert doctor or coach who helps build it and gets a %.
- Per-coach AI assistant tuned to each coach's methods (#254).

## Related

[Training](training.md) · [Client add-ons](client-add-ons.md)
