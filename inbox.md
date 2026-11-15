# Inbox: found outside the wiki

Lines Claude adds during work when it finds something the wiki lacks or has wrong. The nightly update files each one
into the wiki and removes it. Format: `- YYYY-MM-DD · what · source/reference`.

- 2026-11-15 · MetabolicHQ logo files live in Drive: `MetabolicHQ-logo.png` (full lockup, navy/teal on white),
  `MetabolicHQ-icon-512.png`, `MetabolicHQ-Central-Hub.svg`, `MetabolicHQ-LinkedIn-banner.png`, and
  `MetabolicHQ-promo-reel.mp4`. The logo is navy + teal, so it needs a white backing on navy backgrounds ·
  Google Drive (Drive search, 2026-11-15)
- 2026-11-15 · Decision: a wide (16:9) demo video for coaches on metabolichq.app, with an AI avatar and voice-over
  showing the key features and benefits as "a day with MetHQ" (works while you're not, easier data, connection,
  engagement, professionalism, own it). First cut made with an Artlist voice-over ("Mentor" voice) and animated UI
  scenes; avatar not added yet. Script fixes from him: "achievements that celebrate showing up" (not "never
  under-eating"), and the MPT Coach scene is 5 AM in a hotel gym, not 10 PM · notes (chat 2026-11-15)
- 2026-11-15 · Artlist (AI voice, video, music) is connected to Claude; voice-overs saved in the Artlist folder
  "MetHQ demo video" · notes (chat 2026-11-15)
- 2026-11-15 · Decision: when Bronson asks for something in YouTube, Claude does it from his cloud, not from the chat
  session (chat sessions can't reach Google APIs). The route is GitHub Actions in mac-app, which hold the YouTube OAuth
  secrets (`YOUTUBE_CLIENT_ID`/`YOUTUBE_CLIENT_SECRET`) and the Firebase service account: e.g. `transcripts.yml` runs
  `scripts/transcripts.mjs`; `functions/youtube.js` handles playlist sync. Note: the YouTube API reads captions,
  metadata and playlists but can't download a video's audio · notes (chat 2026-11-15); mac-app `.github/workflows/transcripts.yml`
- 2026-11-15 · Artlist now has Bronson's cloned voice, "Coach Bronson" (made from the 26 s Riverside "masters
  collective intro" clip in Drive; he approved Artlist's consent statement). Artlist's audio-driven video models won't
  take a real person's photo, so a lip-synced talking avatar of him needs HeyGen or real footage · notes (chat 2026-11-15)
- 2026-11-15 · MetHQ demo video cut 3: narrated in his cloned voice, first person, his headshot
  (Bronson_Horizontal_Headshot_Small.png) on the opening and closing; about 2:15 · notes (chat 2026-11-15)
- 2026-11-15 · Artlist voice "Coach Bronson v2" (cloned from 3.5 min of his Riverside short clips in Drive folder
  1QC4LTRBJ35UKQgUlrcDfKoo6CfP1CdII) replaces the first clone. He prefers its neutral ("Best Fit") delivery at normal
  speed; write the brand as "Metabolic H-Q" in voice-over text so it isn't read as "metabolich". MetHQ demo video is at
  cut 5 (2:25) · notes (chat 2026-11-15)
