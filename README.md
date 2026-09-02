# JSM-Video.com

**Free, private, browser-based video & audio converter.**

Convert, rotate, flip, mute, resize and compress media files entirely on the client.  
No uploads. No accounts. No watermarks.

Powered by [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) + native Web APIs.

## Features

- Video → Video / Audio (MP4, MOV, WebM, MKV, GIF, MP3, WAV, AAC, FLAC…)
- Rotate 90° / 180° / 270° and horizontal / vertical flip
- Remove audio track (mute)
- Resolution scaling + speed vs quality presets
- Fast remux when possible (no re-encode)
- Hardware-accelerated path for some MP4→WebM conversions
- Native WAV decode fallback (no 30 MB engine needed for pure audio)
- Dark / light theme, fully responsive
- Consent-mode analytics & ads (opt-in only)
- PWA-ready (manifest + icons)

## Privacy

Everything runs inside the user’s browser. Files never leave the device.  
See [privacy-policy.html](privacy-policy.html).

## Deploy on Cloudflare Pages

1. Push this repository to GitHub.
2. In Cloudflare Dashboard → Pages → Create project → Connect to Git.
3. Framework preset: **None** (static site).
4. Build command: leave empty (or `echo "static"`).
5. Build output directory: `/` (root).
6. Deploy.

After the first deploy, the `/ffmpeg/` worker files and `/assets/` icons are served correctly.

### Optional: larger FFmpeg core cache

The site loads the heavy `ffmpeg-core.wasm` from public CDNs (jsDelivr / unpkg) with local worker helpers.  
If you prefer full self-hosting, download `@ffmpeg/core` and `@ffmpeg/core-mt` and place the files under `/ffmpeg/`.

## Local development

Any static server works:

```bash
npx serve .
# or
python -m http.server 8080
```

Open `http://localhost:8080`.  
Note: `file://` protocol is blocked by the engine for security reasons.

## Project structure

```
/
├── index.html          # Main converter app
├── about.html
├── privacy-policy.html
├── terms.html
├── contact.html
├── articles/           # SEO content
├── assets/             # Logos, favicons, OG image
├── ffmpeg/             # worker.js, const.js, errors.js (required)
├── manifest.json
├── robots.txt
├── sitemap.xml
└── README.md
```

## License

Site code is provided as-is for the JSM-Video.com project.  
ffmpeg.wasm is MIT-licensed.

---

Built for people who value privacy and simple tools.
