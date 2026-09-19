# HomeLesson — Launch Page

Premium, calm launch page for HomeLesson (iPhone + iPad). Static HTML/CSS/JS, no build step.
Mirrors the structure of `log4paw/` and `jaunt-log/` (launch page + standalone privacy page).
Built for App Store review: public Support URL + Privacy Policy URL with review info on-page.

## Run

Open `index.html` directly or serve the folder:

```bash
# from this directory
python3 -m http.server 8000
# then http://localhost:8000
```

Deployed on GitHub Pages under `m-pax.net/homelesson/` (the `mpax.github.io/homelesson` folder).

- Support URL: `https://m-pax.net/homelesson/`
- Privacy Policy URL: `https://m-pax.net/homelesson/privacy.html`

## Where to edit

| What | Where |
|------|-------|
| **Product copy** | `index.html` — search for section headings (`One app for the whole`, `Start timing`, `Every subject`, `step by step`, `Proof without`) |
| **App Store URL** | `index.html` — the `.app-badge` blocks say “Coming soon”. Replace with a real App Store badge/link when live. The `Notify me` button is `mailto:contact@m-pax.net?subject=HomeLesson…` — replace with a waitlist provider if needed |
| **Screenshots** | `images/screenshots/iphone-*.png` + `ipad-*.png` are real captures from `../../HomeLesson/Design/AppStore/` (sample data). Re-copy when marketing art changes |
| **Review box** | `index.html` — `#how .review-box` lists Bundle ID, version, support/privacy URLs, demo steps. Keep in sync with App Store Connect |
| **Contact email** | Search `contact@m-pax.net` in `index.html` and `privacy.html` |
| **Legal links** | Footer in `index.html` — `#licensesLink` shows toast; replace with real `licenses.html` when ready. `privacy.html` is the privacy page (mirrors in-app Settings → About & privacy wording) |
| **Canonical / OG URL** | `<link rel="canonical">`, `og:url`, `og:image` in `<head>` — update domain if it changes |
| **Favicon / OG image** | `images/branding/icon.png` is the app icon (1024). Favicons at `images/branding/favicon-*.png` and `apple-touch-icon.png`, generated with `sips -z`. Regenerate if the icon changes |
| **Effective date** | `privacy.html` — Effective 19 September 2026, Version 1.0 |

## Images

```
images/
  branding/
    icon.png               # App icon (1024×1024) — also used for OG image
    icon-1024.png          # 1024 App Store size (same source)
    favicon-32.png / -16.png
    apple-touch-icon.png   # 180×180
    og-image.png           # currently the icon; replace with 1200×630 branded image for ideal social previews if desired
  screenshots/
    iphone-01-today.png    # Today — timer hero, schedule, recent (real)
    iphone-02-topics.png   # Topics — confidence pills + option picks (real)
    iphone-03-subjects.png # Subjects — hours + confidence list (real)
    iphone-04-records.png  # Records — portfolio builder (real)
    ipad-01-today.png      # iPad equivalents (real)
    ipad-02-topics.png
    ipad-03-subjects.png
    ipad-04-records.png
```

Hero uses a real capture (`images/screenshots/iphone-01-today.png`) inside the
iPhone frame — eager-loaded with a descriptive `alt`. The `#timer`, `#subjects`
and `#records` sections reuse the matching iPhone + iPad shots below them.
Keep `loading="lazy"` (except hero) and `alt` text.

## Design tokens

Derived from `HomeLesson/HomeClass/HomeClass/DesignSystem/HomeLessonColors.swift`
(spec §15 light values):

- Ink `#22303C`, soft `#5A6B7A`, line `#E5DED2`
- Paper `#FAF7F1` / warm `#F2EDE2`, surface `#FFFEFB`
- Indigo brand `#3A5BA0`, deep `#2C467E` / ink `#1A2A4A`
- Amber `#D9963B` (timer/key CTA), deep `#B57A25`, soft `#F7E8CF`
- Leaf `#4E7C4E`, soft `#E4EDDF`, clay `#B8473D`
- Typography: `Instrument Serif` (display) + `Inter` (body) + `JetBrains Mono` (timer/coords)

Edit `:root` in `index.html` `<style>` to adjust. `privacy.html` uses the same tokens.

## Copy rules (must not break)

From the shipped app (`OnboardingView`, `SettingsView`, `SubjectsView`,
`GuidedPathView`, `PortfolioSnapshot`) + App Store notes — these strings appear
verbatim on the site and privacy page:

- `Records stay private unless you export them.`
- `Tracked by parent — never a grade, prediction or assessment.`
- `Parent-recorded home-education log. Generated from the parent's own records. This is not an assessment by any awarding body or local authority.`
- Five promises: `One app for the whole of home education.` / `Proof without paperwork` / `Know what's covered` / `Guided GCSE maths` / `Reliable and private`

Forbidden marketing words: “assesses”, “grades”, “predicts”, “exam-ready”,
“sync”, “AI tutor”, “auto-marks”. Do not claim accounts, cloud sync,
collaboration, or curriculum approval / exam-board endorsement.
Guided vs self-planned must stay visibly different; self-planned subjects must
never imply coverage they do not have.

## App Store review checklist

- [ ] Support URL resolves: `https://m-pax.net/homelesson/`
- [ ] Privacy URL resolves: `https://m-pax.net/homelesson/privacy.html`
- [ ] Review box (§how) matches App Store Connect (bundle `net.m-pax.HomeClass`, v1.0, no login, airplane-mode demo)
- [ ] Screenshots in Connect match the app and the site (no placeholder UI)
- [ ] Age rating reflects parent-held utility with user-entered photos
- [ ] Privacy section of `privacy.html` (§16 table) matches Connect data-collection answers (none)
- [ ] Legal review of `privacy.html` §§11–12 (GDPR, Age Appropriate Design Code, COPPA) for launch jurisdictions
