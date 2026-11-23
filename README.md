# Image Tools

Free, private, browser-based image utilities. Everything runs on your device — no sign-ups, no watermarks.

## Tools

| Tool | Description |
|------|-------------|
| [Image Converter](convert.html) | Convert images between PNG, JPEG, WebP, AVIF, GIF, BMP, TIFF, ICO and more. Resize and recompress on the fly, export as ZIP. |
| [Background Remover](background.html) | Remove image backgrounds with an on-device AI model and get a clean transparent PNG. No uploads or watermarks; the model is cached after the first run. |

## Features

- Entirely client-side — images never leave your browser
- Batch processing with ZIP export (JSZip)
- AI background removal via `@imgly/background-removal` (WASM/ONNX, runs locally)
- Installable PWA — `manifest.webmanifest` + `sw.js` for offline use

## Run locally

```bash
cd image
python3 -m http.server 8000
```

Open http://localhost:8000/convert.html or http://localhost:8000/background.html.

Note: the background remover downloads an AI model (~tens of MB) on first use, then caches it.

## Deploy to GitHub Pages

1. Push this folder to a new repository.
2. Enable **Pages** (Deploy from branch → `main` / root).
3. Available at `https://<user>.github.io/<repo>/convert.html` and `.../background.html`.

Any static host works (Netlify, Vercel, Cloudflare Pages). CDN dependencies load from jsDelivr, so an internet connection is needed on first load.

## Dependencies

Loaded from CDN at runtime:

- `jszip` — batch ZIP export
- `@imgly/background-removal` — on-device background removal (background.html only)

## Structure

```
image/
├── convert.html          # Format converter / resizer
├── background.html       # AI background remover
├── manifest.webmanifest  # PWA manifest
├── sw.js                 # Service worker (offline support)
└── icon.svg              # App icon
```

## License

MIT
