---
title: Video production
summary: How marketing and demo videos get made — the MetHQ demo video, Artlist voices, Riverside clean-up, real app footage, YouTube work
updated: 2026-11-16
sources: [notes, "mac-app #636", mac-app e2e/howto/, mac-app .github/workflows/transcripts.yml, CHANGELOG 2026-11-15]
---

# Video production

## MetHQ demo video ("A coaching day on MetabolicHQ")

- **Live** on the metabolichq.app homepage (2:36), self-hosted at `/video/methq-demo.mp4` (mac-app #636; see
  [metabolichq.app site](../metabolichq/marketing-site.md#demo-video-on-the-homepage-636)).
- Decided brief: a wide (16:9) video for coaches showing key features and benefits as "a day with MetHQ": works while
  you're not, easier data, connection, engagement, professionalism, own it (notes 2026-11-15).
- Script fixes from him: "achievements that celebrate showing up" (not "never under-eating"); the MPT Coach scene is
  5 AM in a hotel gym, not 10 PM (notes 2026-11-15).
- The live cut is narrated by Bronson's own recording, cleaned up in Riverside, over real app and portal footage
  (cut 9). (Previously: an AI voice-over and animated UI scenes in cut 1, then his cloned voice and headshot in cuts
  3–5.) (notes 2026-11-15)
- The in-app call scene uses two fictional AI-generated people; he asked not to use his likeness there
  (notes 2026-11-15).

## Real app footage

Film app and portal screens from the how-to demo app (mac-app `e2e/howto`: `seed.mjs` + `seed-coach.mjs`,
`serve.mjs`, `howto.record()`), never production data (notes 2026-11-15).

## Voice and audio

- **Riverside** (connected to Claude) is where he cleans up voice-overs: echo, flubs, normalizing, polish. Suggest or
  use it before fixing audio by hand (notes 2026-11-15).
- **Artlist** (AI voice, video, music) is connected to Claude. Voice-overs for the demo video are in the Artlist folder
  "MetHQ demo video" (notes 2026-11-15).
- His cloned Artlist voice is **"Coach Bronson v2"**, cloned from about 3.5 minutes of his Riverside short clips in
  Drive; it replaced the first clone (made from a 26 s clip). He prefers its neutral ("Best Fit") delivery at normal
  speed (notes 2026-11-15).
- In voice-over text write the brand as **"Metabolic H-Q"** so it isn't read as "metabolich" (notes 2026-11-15).
- Artlist's audio-driven video models won't take a real person's photo, so a lip-synced talking avatar of him needs
  HeyGen or real footage (notes 2026-11-15).

## YouTube

When he asks for something in YouTube, Claude does it from his cloud, not the chat session (chat sessions can't reach
Google APIs): GitHub Actions in mac-app hold the YouTube sign-in secrets and the Firebase service account, e.g.
`transcripts.yml` runs `scripts/transcripts.mjs`; `functions/youtube.js` syncs playlists. The YouTube API reads
captions, metadata and playlists but can't download a video's audio (notes 2026-11-15).

## Related

[Content and social](content-and-social.md) · [MetabolicHQ content](../metabolichq/methq-content.md) ·
[Help and how-to](../metabolichq/help-and-howto.md)
