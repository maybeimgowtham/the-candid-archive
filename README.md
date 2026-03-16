# 📷 The Candid Archive

A beautiful, browser-based digital photobooth. Take 4 photos, pick a filter, and get a downloadable photo strip — no backend, no install, no account needed.

---

## ✨ Features

- **One-click auto-shoot** — press once, all 4 photos are taken automatically with a 3-second countdown between each
- **10 handcrafted filters** — each with its own pixel-level colour grading baked directly into the photo
- **Themed photo strips** — the strip background, border, and text colours all match the chosen filter
- **Instant PNG download** — your strip is stitched and exported as a full-resolution PNG
- **Cover-crop capture** — photos are never squished; they're cropped to fill like `object-fit: cover`
- **Blush hearts** — the Blush filter bakes soft pink hearts into every photo
- **Zero dependencies** — pure HTML, CSS, and vanilla JavaScript. No frameworks, no build step

---

## 🎨 Filters

| Filter | Vibe |
|---|---|
| Natural | Clean, true-to-life |
| Warm | Soft amber, afternoon sun |
| Cool | Icy blue, crisp and airy |
| Noir | High-contrast black & white |
| Blush | Rosy pink with baked hearts |
| Golden | Deep cinematic amber, crushed shadows |
| Polaroid | Lifted blacks, grain, light leak, vignette |
| Dreamy | Milky whites, highlight-only glow |
| 90s | Oversaturated, green-shifted, heavy grain |
| Lavender | Soft purple-blue, airy and gentle |

---

## 🚀 Getting Started

### Run locally

No build step needed. Just open the file:

```bash
open index.html
```

Or serve it with any static server:

```bash
npx serve .
# or
python3 -m http.server 3000
```

Then visit `http://localhost:3000`

### Deploy to Vercel

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → **New Project**
3. Import your GitHub repo
4. Vercel will auto-detect it as a static site
5. Hit **Deploy** — done

No configuration needed. `index.html` at the root is all Vercel needs.

### Deploy to Netlify

1. Drag and drop the project folder onto [netlify.com/drop](https://app.netlify.com/drop)
2. Or connect your GitHub repo from the Netlify dashboard

---

## 📁 Project Structure

```
the-candid-archive/
├── index.html        # The entire app — HTML, CSS, and JS in one file
├── README.md         # This file
├── LICENSE           # MIT License
└── .gitignore        # Standard web gitignore
```

Everything lives in `index.html`. There are no external assets, no npm packages, and no build process.

---

## 🛠 How It Works

| Step | What happens |
|---|---|
| 1. Land | User sees the intro screen |
| 2. Pick filter | Choose from 10 filters — previewed as colour swatches |
| 3. Booth | Camera opens, user clicks once — 4 photos taken automatically with countdowns |
| 4. Strip | Photos are stitched into a vertical strip with themed borders and footer |
| 5. Download | Canvas renders a full-res PNG and triggers browser download |

**Capture pipeline:**
- `getUserMedia` streams camera into a `<video>` element
- On capture, video frame is drawn to a hidden `<canvas>`
- Cover-crop logic ensures no distortion regardless of camera aspect ratio
- Pixel-level filter is applied directly to canvas `ImageData`
- Post-processing (vignette, grain, glow, light leak) drawn on top via canvas API
- `toDataURL('image/jpeg', 0.92)` saves each frame
- On completion, all 4 frames are composited into a strip canvas and exported as PNG

---

## 📸 Camera Permissions

The app requires camera access via `getUserMedia`. Browsers will prompt the user on first use. The app works best in:

- Chrome / Edge (desktop & Android)
- Safari (iOS 14.3+ and macOS)
- Firefox (desktop)

> **Note:** `getUserMedia` requires either `localhost` or an `https://` origin. It will not work on a plain `http://` domain.

---

## 📄 License

MIT — free to use, modify, and deploy.

---

## 🙌 Credits

Built with:
- [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) — Google Fonts
- [Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond) — Google Fonts
- [Space Mono](https://fonts.google.com/specimen/Space+Mono) — Google Fonts
- Canvas API — for all filter and strip rendering
- `getUserMedia` — for camera access
