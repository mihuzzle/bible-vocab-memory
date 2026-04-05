# Finnish → English Bible Vocabulary Memory Game

This is a small offline web app (PWA) generated from **Uskonnollinen_sanasto__laaja.xls**.

## What it does
- Memory game with postcard-style cards
- Match Finnish terms with English translations
- Optional category filter
- Works offline after first load (service worker cache)

## Files
- `index.html` – the game
- `data.json` – 1507 word/phrase pairs extracted from the Excel file
- `sw.js` – offline cache
- `manifest.webmanifest` + icons – installable on phone

## Run locally
### Option A (recommended): Simple local web server
Because browsers block `fetch()` from `file://` for security, run a tiny local server.

**On a computer:**
- Python 3: `python -m http.server 8000` in this folder
- Open `http://localhost:8000`

**On a phone:**
- Use any “local web server” app (e.g., *Simple HTTP Server*, *HTTP Server*, *KSWEB*)
- Point it to this folder and open the provided local URL

### Option B: Host it anywhere
Upload the folder to any static host (GitHub Pages, OneDrive static hosting, etc.).

## Install to home screen (offline)
- iOS Safari: Share → Add to Home Screen
- Android Chrome: Menu → Install app / Add to Home screen

---
Generated automatically.
