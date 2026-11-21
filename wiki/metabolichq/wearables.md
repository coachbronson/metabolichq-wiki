---
title: Wearables and health-app sync
summary: Status of wearable/health-app sync — Open Wearables vs managed services, decisions on Oura and Samsung Health
updated: 2026-11-21
sources: [notes, CHANGELOG, "#162", "#381", "#816", "#817", "#819", "#821"]
---

# Wearables and health-app sync (#162)

**Status:** in development; the landing page lists it as "In development", not syncing.

- Started on **Open Wearables** (open-source, self-hosted on his Google Cloud). Wants its releases checked from its
  GitHub repo, emailed with release notes, and installed only after his approval.
- Found the per-brand effort of connecting each service through Open Wearables untenable (Nov 8); moving to a
  **managed service**. **Undecided between Terra** (API, ~$499/month) **and Junction** (he has an account) — still
  open as of 2026-11-14.
- Interested in Open Wearables' mobile SDKs for Apple Health, Google and Health Connect without Connect App fees.
- **Oura is out** (no commercial use allowed). Don't describe Oura as first or as a pilot.
- **Samsung Health** not used (can't scale right away), though he uses it himself.
- **BAA terms, if a clinical partner needs HIPAA** (researched Nov 18, nothing decided): Terra signs a BAA only on its
  enterprise tier (sales quote, not the ~$499 plan); Junction publishes no BAA terms (ask them); Sahha from its Pro
  tier at $1,499/month; self-hosted Open Wearables on Google Cloud would sit under Google's BAA (#381 comment; see
  [HIPAA](hipaa.md)).
- A connected device can always be disconnected: when connecting new devices closes (pilot list or "open to
  everyone" off, or a device type no longer offered), Settings still lists it with Disconnect under "Connecting new
  devices isn't available right now" (#816 item 4, #821).
- Only the server writes a person's link to their wearables-server account (security rules, #819). Account deletion
  removes their data there too (see [Research and privacy](research-and-privacy.md)) (#817).
- Device data rule: no raw device data into AI (see [Biometrics and signals](biometrics-and-signals.md)).

## Related

[Biometrics and signals](biometrics-and-signals.md)
