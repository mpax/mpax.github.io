# TileArc: Habit Book — Launch Page

Anime habit tracker for iPhone (iOS 17+). Static HTML/CSS/JS, no build step.
Mirrors the structure of `log4pilot/` and `jaunt-log/` (launch page + standalone privacy page).

## Run

Open `index.html` directly or serve the folder:

```bash
# from this directory
python3 -m http.server 8000
# then http://localhost:8000
```

Deployed on GitHub Pages under `m-pax.net/tilearc/` (the `mpax.github.io/tilearc` folder).

## Where to edit

| What | Where |
|------|-------|
| **Product copy** | `index.html` — sections `#loop`, `#grid`, `#themes`, `#widget`, `#reminders`, `#pro`, `#privacy`, `#how` |
| **App Store URL** | `index.html` — `.coming-pill` blocks say “Coming soon”. Replace with real App Store badge/link when live. Launch-list CTA is `mailto:contact@m-pax.net?subject=TileArc%20launch%20list` |
| **Screenshots** | None yet — hero uses a live CSS/SVG dashboard demo + interactive Sakura/Shonen style switcher. Replace with real captures when TestFlight/App Store art exists |
| **Interactive demos** | `index.html` — inline `<script>`: seeded year-grid illustration, theme switcher (mirrors in-app style picker tokens), tap-to-fill widget demo |
| **Contact email** | Search `contact@m-pax.net` in `index.html` and `privacy.html` |
| **Canonical / OG URL** | `<link rel="canonical">`, `og:url`, `og:image` in `<head>` — `https://m-pax.net/tilearc/` |
| **Favicon / OG image** | `images/branding/icon.png` is the TileArc icon (1024, copied from `TileArc/TileArc/Assets.xcassets/AppIcon.appiconset/`). Favicons generated with `sips -z`. Regenerate if the icon changes |
| **Effective date** | `privacy.html` — Effective 30 October 2026, Version 1.0 |

## Images

```
images/
  branding/
    icon.png               # App icon 1024×1024 — also used for OG image
    icon-1024.png          # same source
    favicon-32.png / -16.png
    apple-touch-icon.png   # 180×180
    og-image.png           # currently the icon; replace with 1200×630 branded image for ideal social previews if desired
```

## Design tokens

Page theme mirrors the app's Appendix B tokens: Sakura `#F27D9D` / Shonen `#3D7BFF`, Plum Night `#2E2230` hero/footer, warm paper `#FBF7F2`. The in-phone demo re-skins via CSS custom properties using the verbatim light tokens for both themes (see `Tokens.swift` in the TileArc repo). Copy constraints kept from the app spec: free = 6 habits + widget free forever, Pro = Monthly/Yearly/Lifetime with store prices, terms line names the Apple cancellation surface.
