# Log4Pilot — Launch Page

Aviation-grade launch page for Log4Pilot (iPhone, iOS 17+). Static HTML/CSS/JS, no build step.
Mirrors the structure of `log4paw/` and `jaunt-log/` (launch page + standalone privacy page).

## Run

Open `index.html` directly or serve the folder:

```bash
# from this directory
python3 -m http.server 8000
# then http://localhost:8000
```

Deployed on GitHub Pages under `m-pax.net/log4pilot/` (the `mpax.github.io/log4pilot` folder).

## Where to edit

| What | Where |
|------|-------|
| **Product copy** | `index.html` — sections `#loop`, `#currency`, `#log`, `#prove`, `#privacy`, `#how` |
| **App Store URL** | `index.html` — `.coming-pill` blocks say “Coming soon”. Replace with real App Store badge/link when live. Launch-list CTA is `mailto:contact@m-pax.net?subject=Log4Pilot%20launch%20list` |
| **Screenshots** | `images/screenshots/today.png`, `compose.png`, `prove.png`, `more.png` are real App Store captures (1206×2622, sample data) from `../Log4Pilot/Log4Pilot/AppStore/`. `header-wide.png` available, not yet embedded |
| **Contact email** | Search `contact@m-pax.net` in `index.html` and `privacy.html` |
| **Canonical / OG URL** | `<link rel="canonical">`, `og:url`, `og:image` in `<head>` — `https://m-pax.net/log4pilot/` |
| **Favicon / OG image** | `images/branding/icon.png` is the Log4Pilot icon (1024, deep-teal + white aircraft + dashed circuit). Favicons generated with `sips -z`. Regenerate if the icon changes |
| **Effective date** | `privacy.html` — Effective 10 October 2026, Version 1.0 |

## Images

```
images/
  branding/
    icon.png               # App icon 1024×1024 — also used for OG image
    icon-1024.png          # same source
    favicon-32.png / -16.png
    apple-touch-icon.png   # 180×180
    og-image.png           # currently the icon; replace with 1200×630 branded image for ideal social previews if desired
  screenshots/
    today.png              # Today — currency cards (real)
    compose.png            # Log flight sheet (real)
    prove.png              # Prove — report builder (real)
    more.png               # More — directories + rule bundles (real)
    header-wide.png        # 12-wide marketing header (available)
```

Hero uses `today.png` inside the iPhone frame — eager-loaded with descriptive `alt`. Other shots lazy-loaded in `#log` / `#prove`.

## Design tokens

Derived from the App Store marketing (`00-header-12-wide.png`) + in-app UI:

- Abyss `#051B23`, deep `#0A3442`, deep-2 `#072833`, teal `#10707F`
- Gold `#E8B33D`, pressed `#C9962B`, soft `#F9E9BE`
- Paper `#F5F3EC`, surface `#FFFFFF`, ink `#0F222A`, secondary `#4B6470`, border `#D9E3E1`
- Current green / Not-current red pills match in-app status (colour + icon + text, never colour-only)
- Typography: `Instrument Serif` (display) + `Inter` (body) + `JetBrains Mono` (coords/rule bundles)

Edit `:root` in `index.html` `<style>` to adjust. `privacy.html` uses the same tokens.

## Copy rules (must not break — spec §§2.3, 19.5, 27)

- Never claim “FAA / EASA / CAA approved”. Use “formats designed to match …”.
- Currency outputs are informational, labelled with rule + version — never “you are legal to fly”.
- Verbatim disclaimer (hero-adjacent, `#how`, footer, every report footer, first engine use):
  `Log4Pilot computes currency and totals from your own entries using published rules. It is not legal advice and does not replace your logbook responsibilities or an instructor's or examiner's judgement.`
- Not an EFB; no planning/weather/navigation/filing claims. One pilot per install.
- Privacy: `Data Not Collected`. Pay-once copy: `Pay once. Your logbook is yours.` Viewing/searching/exporting/reporting/restoring never gated.

## Accessibility & performance

- Semantic HTML, skip link, focus-visible, keyboard nav, `prefers-reduced-motion` respected
- IntersectionObserver reveal; no heavy libs, minimal JS
- Images lazy except hero; screenshots ~300–700 KB each — consider WebP/AVIF if page weight matters

## Checklist before App Store submission

- [ ] Set real App Store URL (replace “Coming soon” pills + CTA)
- [ ] Confirm Bundle ID, App Store name, trademark clearance (§33 open decisions)
- [ ] Confirm free-allowance size + unlock price; update `privacy.html` §10 if different from hypothesis
- [ ] Replace 1024 OG image with 1200×630 branded image (optional but recommended)
- [ ] Confirm legal entity + postal address in `privacy.html` §1
- [ ] Have privacy + disclaimer wording legally reviewed against shipped build
- [ ] Verify privacy manifest / App Privacy labels match shipped build (currently Data Not Collected, no tracking)
- [ ] Test on iPhone, Android, tablet, desktop; VoiceOver / keyboard; reduced-motion; Airplane Mode
