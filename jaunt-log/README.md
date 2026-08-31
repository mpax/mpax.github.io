# Jaunt Log — Launch Page

Premium, outdoor-journal launch page for Jaunt Log (iPhone). Static HTML/CSS/JS, no build step.

## Run

Open `index.html` directly or serve the folder:

```bash
# from this directory
python3 -m http.server 8000
# then https://localhost:8000
```

Deployed on GitHub Pages under `m-pax.net/jaunt-log/` (the `mpax.github.io/jaunt-log` folder).

## Where to edit

| What | Where |
|------|-------|
| **Product copy** | `index.html` — search for section headings (`Every place has a story`, `Your adventures, mapped`, etc.) |
| **App Store URL** | `index.html` — `id="appStoreBtn"` → set `data-href="https://apps.apple.com/…"` and update the `href`. Remove the toast fallback once live. Remove mail waitlist if not needed. |
| **Waitlist / email** | `index.html` — `<form id="waitlist">` posts nowhere currently (toast only). Wire to your form provider (Formspark, Formspree, Mailchimp, etc.) or a backend endpoint. |
| **Contact email** | Search `contact@m-pax.net` in `index.html` and `privacy.html` |
| **Legal links** | Footer in `index.html` — `#licensesLink` shows toast; replace with real `licenses.html` when ready. `privacy.html` is the privacy page (mirrors in-app wording). |
| **Canonical / OG URL** | `<link rel="canonical">`, `og:url`, `og:image` in `<head>` — update domain if it changes. |
| **Favicon / OG image** | `images/branding/icon.png` is the source. Favicons at `images/branding/favicon-*.png` and `apple-touch-icon.png`. Regenerate with `sips -z …` if icon changes. |

## Images

```
images/
  branding/
    icon.png               # App icon (1254×1254) — also used for OG image
    icon-1024.png          # 1024 App Store size
    favicon-32.png / -16.png
    apple-touch-icon.png   # 180×180
  screenshots/             # ← Put real app screenshots here
    explore.png            # Explore / Map
    history.png            # History / Journey log
    detail.png             # Place / Jaunt detail
    progress.png           # Progress / badges
  photography/             # ← Outdoor photography (optimise, use < 300k per image)
  hero/                    # Hero-specific assets if needed
```

Placeholder iPhone UI in `index.html` is CSS-only and clearly marked `PLACEHOLDER — Replace with real Explore screenshot`. Swap the `.device-screen` blocks for `<img src="images/screenshots/…">` when screenshots are ready. Keep `loading="lazy"` and `alt` text.

## Design tokens

Derived from `Jaunt Log/DesignSystem/JauntColor.swift`:

- Forest `#1B3A26`, deep `#0F2018`, moss `#3C5C37`, sage `#9CAF88`, brass `#C8A96E`
- Parchment `#F5F0E6` / warm `#EDE6D3`, ink `#1A241E`
- Typography: `Instrument Serif` (display) + `Inter` (body) + `JetBrains Mono` (coords)

Edit `:root` in `index.html` `<style>` to adjust.

## Accessibility & performance

- Semantic HTML, skip link, focus-visible, keyboard nav, `prefers-reduced-motion` respected (route draw + float disabled).
- IntersectionObserver reveal; no heavy libs, no 3D, minimal JS.
- Images are lazy except hero icon; keep screenshots optimised and use responsive sizes if adding photography.

## SEO

Title, description, OG/Twitter, canonical and favicon are set in `<head>`. OG image currently points to `images/branding/icon.png` (1254×1254). Replace with a 1200×630 branded image for ideal social previews if desired.

## Checklist before launch

- [ ] Set real App Store URL on `#appStoreBtn`
- [ ] Replace CSS placeholder phones with real screenshots
- [ ] Add real outdoor photography if used (license-checked)
- [ ] Update contact email / legal links
- [ ] Wire waitlist form to provider (or remove section if app is live)
- [ ] Verify OpenStreetMap attribution is accurate for shipped data
- [ ] Test on iPhone, Android, tablet, desktop; test VoiceOver / keyboard; test reduced-motion
