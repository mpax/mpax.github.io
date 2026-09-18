# Log4Paw — Launch Page

Premium, calm launch page for Log4Paw (iPhone). Static HTML/CSS/JS, no build step.
Mirrors the structure of `jaunt-log/` (launch page + standalone privacy page).

## Run

Open `index.html` directly or serve the folder:

```bash
# from this directory
python3 -m http.server 8000
# then http://localhost:8000
```

Deployed on GitHub Pages under `m-pax.net/log4paw/` (the `mpax.github.io/log4paw` folder).

## Where to edit

| What | Where |
|------|-------|
| **Product copy** | `index.html` — search for section headings (`Capture the moment`, `One tap when`, `A record your vet`, etc.) |
| **App Store URL** | `index.html` — the `.app-badge` blocks say “Coming soon”. Replace with a real App Store badge/link when live. The `Notify me` button is `mailto:contact@m-pax.net?subject=Log4Paw…` — replace with a waitlist provider if needed |
| **Screenshots** | `images/screenshots/today-light.png`, `today-dark.png` are real captures from `../log4paw/docs/screenshots/` (sample data). Add Trends / Care / Reports shots there and reference them in `#reports` when ready |
| **Contact email** | Search `contact@m-pax.net` in `index.html` and `privacy.html` |
| **Legal links** | Footer in `index.html` — `#licensesLink` shows toast; replace with real `licenses.html` when ready. `privacy.html` is the privacy page (mirrors in-app About & privacy wording) |
| **Canonical / OG URL** | `<link rel="canonical">`, `og:url`, `og:image` in `<head>` — update domain if it changes |
| **Favicon / OG image** | `images/branding/icon.png` is the Timer Ring app icon (1024). Favicons at `images/branding/favicon-*.png` and `apple-touch-icon.png`, generated with `sips -z`. Regenerate if the icon changes |
| **Effective date** | `privacy.html` — Effective 18 September 2026, Version 1.0 |

## Images

```
images/
  branding/
    icon.png               # Timer Ring app icon (1024×1024) — also used for OG image
    icon-1024.png          # 1024 App Store size (same source)
    favicon-32.png / -16.png
    apple-touch-icon.png   # 180×180
    og-image.png           # currently the icon; replace with 1200×630 branded image for ideal social previews if desired
  screenshots/
    today-light.png        # Today, light (real, sample data)
    today-dark.png         # Today, dark (real, sample data)
    today-xxxl.png         # Today, XXXL (available, not yet embedded)
  photography/             # ← unused (no stock photography; keep empty)
  hero/                    # ← unused (CSS-only device mock)
```

Hero uses a real capture (`images/screenshots/today-light.png`) inside the
iPhone frame — eager-loaded with a descriptive `alt`. The `#timer` section
reuses the same light shot plus the dark-mode shot below it.
Timer / Records / Medication diagrams remain CSS-only and clearly labelled.
Keep `loading="lazy"` (except hero) and `alt` text.

## Design tokens

Derived from `log4paw/log4Paw/log4Paw/DesignSystem/Log4PawColors.swift`
(spec §15 light values):

- Deep `#103F3A`, deep-2 `#0B2E2B`, accent `#176258`
- Coral `#EB6A53`, pressed `#C84F3B`, soft `#FADFD6`
- Mint `#DFF1E9` / pale `#EDF7F3`, paper `#F8FAF7`
- Ink `#16302E`, secondary `#506361`, border `#D9E2DE`
- Typography: `Instrument Serif` (display) + `Inter` (body) + `JetBrains Mono` (timer/coords)

Edit `:root` in `index.html` `<style>` to adjust. `privacy.html` uses the same tokens.

## Copy rules (must not break)

From `MedicalCopy.swift` + App Store notes — these strings appear verbatim
on the site and in-privacy page:

- `Owner-recorded observations. This report does not provide diagnosis or treatment advice.`
- `Log4Paw is a recording and reminder tool…`
- `Your records are stored on this iPhone. Log4Paw has no account or cloud service…`
- `Sharing sends a copy outside this iPhone…`

Forbidden marketing words: “medical-grade”, “detects”, “predicts”,
“prevents”, “keeps your pet safe”. Do not claim sync, collaboration or detection.

## Accessibility & performance

- Semantic HTML, skip link, focus-visible, keyboard nav, `prefers-reduced-motion` respected (float + pulse disabled)
- IntersectionObserver reveal; no heavy libs, minimal JS
- Images lazy except hero icon; keep screenshots optimised

## SEO

Title, description, OG/Twitter, canonical and favicon are set in `<head>`.
OG image currently points to the app icon (1024×1024).

## Checklist before launch

- [ ] Set real App Store URL (replace “Coming soon” badges)
- [ ] Add Trends / Care / Reports screenshots if desired
- [ ] Replace 1024 OG image with 1200×630 branded image (optional)
- [ ] Confirm legal entity + postal address in `privacy.html` §1
- [ ] Have privacy + medical-limitation wording legally reviewed against shipped build
- [ ] Wire or remove `Notify me` mailto
- [ ] Test on iPhone, Android, tablet, desktop; VoiceOver / keyboard; reduced-motion
