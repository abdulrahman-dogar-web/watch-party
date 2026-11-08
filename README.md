# Watch Party — Watch Together, In Sync

One room, one movie, two screens — perfectly in sync. Create a room, share the
6-letter code, and press play together. No screen-sharing lag, no stutter: the
video loads on each person's own device, only the timing travels between you.

**Live site:** https://abdulrahman-dogar-web.github.io/watch-party/

## How it works

1. **Create a room** — you get a short 6-letter room code (and a shareable link).
2. **Share the code** — your partner enters it on the home screen to join.
3. **Paste a video link** — a direct video file (MP4 / WebM), an HLS stream
   (.m3u8), or a free streaming site's page.
4. **Watch together** — play, pause, seek, speed changes and chat happen on
   both screens. Fullscreen works.

## Sync

Room state (video URL, play/pause, current time, speed, chat messages,
buffering flags, presence) lives in a shared server-side key-value store and
every client polls it every 1.5 seconds, so two different browsers/devices
stay in sync. The video itself streams on each person's own device from their
own internet — only the timing and chat travel through the server.

- If either side starts buffering, a warning appears in chat automatically
  ("X is buffering — their connection is catching up").
- Drift is measured on every poll and auto-corrected when it passes 0.8s.
- No signup. No account. No payment.

Backend: https://apps-backend-tahqeeq.vercel.app (`PUT/GET /v1/kv/wp:<CODE>`).

## One honest note

Netflix, Prime Video and similar paid platforms block other websites from
embedding their pages, so they can't play inside the Shared Browser tab — no
tool can change that. For those, use a direct video/stream link in the player
instead. Free streaming sites that allow embedding will open in the Shared
Browser tab.

## Run locally

Open `index.html` in any browser, or serve the folder:

```bash
python3 -m http.server
```

## Credit

© 2026 Mr. Abdul Rahman Dogar — MIT License.
