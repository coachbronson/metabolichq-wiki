---
title: Wearables and health-app sync
summary: Status of wearable/health-app sync — Open Wearables vs managed services, decisions on Oura and Samsung Health
updated: 2026-11-14
sources: [notes, CHANGELOG, "#162"]
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
- Device data rule: no raw device data into AI (see [Biometrics and signals](biometrics-and-signals.md)).

## Related

[Biometrics and signals](biometrics-and-signals.md)
