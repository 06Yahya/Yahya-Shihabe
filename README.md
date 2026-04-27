# Yahya Shihabe — Landing Page

Personal landing page linked from demo sites. Tells prospects who you are, what you build, and books a call.

---

## Deploy to Cloudflare Pages

### Option A — Drag and drop (fastest)

1. Go to [cloudflare.com](https://cloudflare.com) → **Workers & Pages** → **Create** → **Pages** → **Direct Upload**
2. Give the project a name (e.g. `yahya-shihabe`)
3. Drag the entire project folder into the upload area
4. Click **Deploy site**

Done. You get a URL like `yahya-shihabe.pages.dev`.

### Option B — Git (auto-deploy on push)

1. Create a GitHub repo and push this folder
2. Cloudflare Pages → **Connect to Git** → select the repo
3. Build settings:
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/`
4. Deploy

Every push to `main` auto-deploys.

---

## Add a custom domain

1. Cloudflare Pages → your project → **Custom domains** → **Set up a custom domain**
2. Enter your domain (e.g. `yahyashihabe.se`)
3. If the domain is already on Cloudflare DNS: it configures automatically
4. If not: add the CNAME record Cloudflare shows you at your registrar

---

## Swap the booking URL

When you have your Google Calendar Appointment Schedule link:

1. Open `index.html`
2. Find this line near the bottom of the file (inside `<script>`):

```js
const BOOKING_URL = 'https://calendar.app.google/REPLACE_ME';
```

3. Replace `https://calendar.app.google/REPLACE_ME` with your real URL
4. Save and re-deploy

All three booking buttons update from that one line.

### How to set up Google Calendar Appointment Schedule

1. Open [calendar.google.com](https://calendar.google.com)
2. Click **+ Create** → **Appointment schedule**
3. Title: e.g. "AI-samtal med Yahya — 20 min"
4. Duration: 20 minutes
5. Set your available hours (e.g. weekdays 09:00–17:00)
6. Add buffer time if needed (15 min after each meeting)
7. Click **Next** → **Save**
8. Click **Open booking page** → copy the URL from your browser
9. Paste that URL into `index.html` as described above

---

## Update demo URLs

The three demo links are hardcoded in `index.html`. Search for `onrender.com` to find them:

| Demo | Current URL |
|------|-------------|
| FriluftsByn | `https://friluftsbyn-chatbot.onrender.com` |
| LS Bygg & Snickeri | `https://ls-bygg-snickeri.onrender.com` |
| The Unit | `https://the-unit-chatbot.onrender.com` |

If a demo moves to a new URL, find and replace the old URL in `index.html`.

---

## Files

```
index.html     Main landing page (single file, no build step)
favicon.svg    YS monogram — browser tab icon
og.svg         OG image source (1200×630)
og.png         OG image for link previews (Slack, iMessage, LinkedIn)
README.md      This file
CLIENTS.md     Sales context (not served, internal only)
```

---

## Regenerate og.png

If you edit `og.svg`, re-export with:

```bash
# Export
sips -s format png og.svg --out og.png

# Compress (requires ImageMagick — brew install imagemagick)
magick og.png -colors 256 -dither Riemersma og.png
```

Target: under 300 KB.
