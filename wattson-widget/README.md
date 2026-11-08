# Wattson widget feed

Daily GIF scenes for the Wattson home-screen widget app (Pixel 9 Pro).

- **Feed:** `feed.json` — the app checks it at random times (never a set
  schedule). Bump `version` every time new scenes are published; the phone
  only downloads when the version is newer than the one it has seen.
- **Frames:** `frames/*.webp.b64` — square 720x720 WebP, 4 per scene
  (Stargazing has 3), stored as base64 text. Why base64? GitHub's API
  tooling here can only upload text files, so the binary WebP bytes are
  stored base64-encoded and the app decodes them after download
  (see `WattsonFeed.java` — `.b64` URLs are decoded to `.webp` on the
  phone). The app downscales them to 640px RGB_565 on the way in.
- **App:** `app-debug.apk` — the Wattson Widget app itself (debug build).
  Download it on the phone and install it (allow install from this source).
  Tap the widget picture to open Muse; the play button opens the smooth
  in-app flipbook.
- **Feed URL (raw, works without GitHub Pages):**
  `https://raw.githubusercontent.com/MegaNerdZeke/My-Projects/main/wattson-widget/feed.json`
- **GitHub Pages URL (once Pages is enabled on this repo, root):**
  `https://MegaNerdZeke.github.io/My-Projects/wattson-widget/feed.json`

## Publishing a new daily scene (how Wattson does it)
1. Generate 4 square frames in the same style, WebP, 720x720.
2. Upload them to `frames/` (e.g. `frame_beach_1.webp` …).
3. Add a scene entry to `feed.json` and bump `version` by 1.
4. The phone picks the new scene up on its next random feed check —
   no app update needed.
