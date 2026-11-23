---
title: Research opt-in, privacy and data ownership
summary: Citizen-science research opt-in, privacy policy versioning, data export and ownership, retention rules
updated: 2026-11-23
sources: ["#925", "#929", notes, public/js/config.js, "#319", #754, #790, #791, "#816", "#817", "#818", "#869", "#865"]
---

# Research opt-in, privacy and data ownership

## Research opt-in (citizen science)

- Goal: support research on nutrition, fitness and their effects on biometrics, health and performance.
- A separate yes/no choice with **nothing preselected** (everyone must pick), for all users including partner spaces
  (partner agreements cover it). An IRB will be used.
- MetabolicHQ doesn't do the research; it partners with researchers who do. No studies running yet (Nov 2026). The
  question itself now names MetabolicHQ (it's asked in every coach's space), not MPT; what's shared and the choice
  are unchanged, so `RESEARCH_VERSION` stays (#929).
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
- Only a real "not found" from the wearables server counts as already deleted (an outage or "API key not found" no
  longer does); deleting the same person again keeps the retry count and doesn't re-send the alert (#816 item 1, #817).
- The owner's MPT Coach report in the portal shows only when, the topic, the exercise and the pain/swap/note flags,
  never what clients asked or were told (#816 item 2, #818; see [MPT Coach](mpt-coach.md)).
- The Privacy Policy and Terms live at **metabolichq.app/privacy** and **/terms** since Nov 22 (old app addresses
  redirect) and describe **MetabolicHQ**, the platform owned and run by BD Solutions LLC, where each coach runs their
  own space; MPT is named as Coach Bronson's space, and "partner coaches" became "another coach on MetabolicHQ".
  What's collected, who sees it, retention, research, payments and liability are unchanged, so `PRIVACY_VERSION`
  stays; "Last updated" is Nov 22 (#925). (Previously they described "the MPT app, run by BD Solutions LLC doing
  business as Coach Bronson".)
- The privacy policy (wording only, so `PRIVACY_VERSION` is unchanged) points to
  **Settings → Your data** (Download my data, Delete my account, Who has viewed my data) and **Settings → Privacy &
  documents**, and lists Cloudflare Turnstile (sees IP address and browser details), USDA FoodData Central and Open
  Food Facts (only the search term or barcode is sent, from the server) as service providers (#869).
- **Trust page** at metabolichq.app/trust: privacy in brief, AI use, service providers, retention, export, backups
  (#319, #865; see [metabolichq.app site](marketing-site.md#trust-page-metabolichqapptrust-319-done-nov-20)).

## Data ownership

Coaches own their program and client data; export of client data and/or programming is always available. No import
tool for now (migration toolkits are a backlog idea, #167).

## Related

[Security](security.md) · [Biometrics and signals](biometrics-and-signals.md)
