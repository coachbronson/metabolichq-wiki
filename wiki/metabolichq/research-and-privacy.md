---
title: Research opt-in, privacy and data ownership
summary: Citizen-science research opt-in, privacy policy versioning, data export and ownership, retention rules
updated: 2026-11-20
sources: [notes, public/js/config.js, "#319", #754, #790, #791]
---

# Research opt-in, privacy and data ownership

## Research opt-in (citizen science)

- Goal: support research on nutrition, fitness and their effects on biometrics, health and performance.
- A separate yes/no choice with **nothing preselected** (everyone must pick), for all users including partner spaces
  (partner agreements cover it). An IRB will be used.
- MPT doesn't do the research; it partners with researchers who do. No studies running yet (Nov 2026).
- Worksheet answers are excluded from research releases. Doesn't apply to the [HIPAA practice integration](hipaa.md).
- The metabolichq.app citizen-science page lives in the footer menu, not the main menu.

## Privacy

- Privacy policy version is tracked (`PRIVACY_VERSION` in config.js); a meaningful change makes everyone agree again.
- Each person's log, settings and session times are private; their coach can see them.
- AI coach conversations private to the client. DM photos deleted after 72 hours. Call video deleted after
  transcription.
- **Account deletion** (Delete my account, or a coach deleting a client) also deletes the person's data on the
  wearables server. If that server doesn't answer, the deletion is kept as pending and a daily job retries it; the
  app and portal say the device data "is still being removed and will be gone within a few days" (#754, #791). A
  coach's deletion removes the client's sign-in first, so a failed try can simply be retried (#790); a client's own
  deletion keeps records-first, since they need their sign-in to retry (#754).
- Planned Trust page (privacy, AI use, subprocessors, retention; #319).

## Data ownership

Coaches own their program and client data; export of client data and/or programming is always available. No import
tool for now (migration toolkits are a backlog idea, #167).

## Related

[Security](security.md) · [Biometrics and signals](biometrics-and-signals.md)
