---
title: HIPAA — practice integration and HIPAA-ready MetabolicHQ
summary: The health-practice integration prospect and the idea of making MetabolicHQ fully HIPAA compliant
updated: 2026-11-19
sources: [notes, "#171", "#381"]
---

# HIPAA

## Practice integration prospect (#171)

- A health practice with HIPAA requirements wants MPT workout programming and client tracking built into **their**
  client-management app in **their** Google Cloud, under their HIPAA setup and insurance.
- He'd build it, with an integration plan their systems engineer can follow.
- Scope of the API: programming, workout logging, performance-progression and consistency reporting only. No
  one-on-one programming for their patients; a coach view on their side for engagement and progress.
- Tie into their existing community and gamification instead of bringing MPT's.
- All data belongs to the practice; MPT's research opt-in doesn't apply.

## HIPAA-ready MetabolicHQ (#381, medium)

None of his current or likely partner coaches are healthcare providers billing insurance, but he's considering full
HIPAA compliance for market positioning with clinical partners, plus a health-data privacy baseline.
Needs his decision (#381; deciding on it is also a #620 item).

- **Plan in the issue:** phase 1, a HIPAA-ready baseline now (sign-in on Identity Platform, which Google's BAA covers;
  health data only in BAA-eligible services and kept out of email and Zapier; MFA for coaches and admins; audit logs of
  health-data access; a breach response plan; consent and a consumer health data policy for Washington's MHMDA; a
  data inventory). Phase 2, per-space HIPAA mode once a covered-entity partner signs (Google Cloud BAA, Daily
  Healthcare for calls, and others) (#381).
- **Cost research (Nov 18, nothing decided):** the CIS mitigations are about $1–5/month plus Data Access audit logs
  ($0.50/GiB past 50 GiB per project per month, the one variable). Phase 2 is roughly $2,000+/month in vendor fees
  per clinical partner: Google Cloud BAA free, Daily Healthcare $500/month, a BAA email service and a wearables
  provider with a BAA (#381 comment).
- **BAA email options (researched):** Paubox Email API (BAA on every plan; free for 300/month, Pro from $104/month
  annual) or Amazon SES ($0.10 per 1,000 under the AWS BAA). Resend, Postmark and standard SendGrid don't sign BAAs
  (#381 comment). Wearables vendors: [Wearables](wearables.md).

## Related

[Research and privacy](research-and-privacy.md) · [Security](security.md)
