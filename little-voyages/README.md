# Little Voyages — Launch Page

Family saving app for iPhone and iPad (iOS 17+). Static HTML/CSS/JS, no build step.
Mirrors the structure of `tilearc/` and `log4paw/` (launch page + standalone privacy page).

## Run

Open `index.html` directly or serve the folder:

```bash
# from this directory
python3 -m http.server 8000
# then http://localhost:8000
```

Deployed on GitHub Pages under `m-pax.net/little-voyages/` (the `mpax.github.io/little-voyages` folder).

## Where to edit

| What | Where |
|------|-------|
| **Product copy** | `index.html` — sections `#how` (3 steps), `#stories` (Pirate/Space/Magic + presets), `#screens`, `#parents` (parent gate), `#privacy`, `#faq` |
| **App Store URL** | `index.html` — the `.coming-pill` blocks say “Coming soon”. Replace with a real App Store badge/link when live. The launch-list CTA is `mailto:contact@m-pax.net?subject=Little%20Voyages%20launch%20list` — replace with a waitlist provider if needed |
| **Screenshots** | `images/screenshots/` are real App Store marketing captures from `LittleVoyages/LittleVoyages/Design/AppStore/` (iPhone + iPad). Page embeds the 4 iPhone shots; iPad shots are included in the folder for later use |
| **Contact email** | Search `contact@m-pax.net` in `index.html` and `privacy.html` |
| **Canonical / OG URL** | `<link rel="canonical">`, `og:url`, `og:image` in `<head>` — `https://m-pax.net/little-voyages/` |
| **Favicon / OG image** | `images/branding/icon.png` is the compass-coin app icon (1024, from `LittleVoyages/.../AppIcon.appiconset/`). Favicons generated with `sips -z`. Regenerate if the icon changes |
| **Effective date** | `privacy.html` — Effective 1 November 2026, Version 1.0 |
| **Main site links** | `../index.html` — nav menu, apps grid card, footer “Kids & Family” section |

## Images

```
images/
  branding/
    icon.png               # Compass-coin app icon (1024×1024) — also used for OG image
    icon-1024.png          # same source
    favicon-32.png / -16.png
    apple-touch-icon.png   # 180×180
    og-image.png           # currently the icon; replace with 1200×630 branded image for ideal social previews if desired
  screenshots/
    setup.png              # “One treasure, one number” (iPhone, from App Store set)
    picker.png             # “Pick your story” (iPhone)
    journey.png            # “Save. Spend. Watch it move.” (iPhone — also hero)
    trophy.png             # “Finish it, choose again” (iPhone)
    ipad-setup.png         # iPad setup (in folder, not yet embedded)
    ipad-journey.png       # iPad journey (in folder, not yet embedded)
```

Keep `loading="lazy"` (except hero) and `alt` text. Alt text mirrors the
in-app copy verbatim (e.g. “Saved £32 of £50 — 64%”).

## Design tokens

Page theme derived from the app icon and App Store art — deep navy `#0B2440`,
sea teal `#14918F`, coin gold `#E9B44C`, warm paper `#FAF6EE`. Edit `:root` in
`index.html` `<style>` to adjust.

## Copy constraints (from the app — do not drift)

- One active goal at a time; stories locked mid-voyage (“Finish your current voyage to choose a new story”)
- Kid UI is exactly two buttons: SAVE! / SPEND! Same rules in all three stories
- Every entry needs parent approval; spends can't exceed saved
- Parent gate = device lock (Face ID / Touch ID / passcode), no stored secret, fail-closed
- Whole pounds only, £1–£10,000 per goal
- No account, no analytics, no network — label is **Data Not Collected**
- Presets: Pirate (Scooter £50, Treasure toy £30, Seaside trip £60) · Space (Rocket toy £50, Moon base kit £40, Planetarium trip £60) · Magic (Potion set £50, Spell book £30, Magic show trip £60)
- iPhone + iPad, iOS/iPadOS 17+
