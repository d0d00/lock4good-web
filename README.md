# lock4good-web

The public website for the **Lock4Good** iOS app.

**Live**: https://d0d00.github.io/lock4good-web/

## How this deploys

This repo *is* the GitHub Pages source — served from the `main` branch, root directory. There is no
build step and no generator: **editing a file here and pushing is deploying it.** A push takes
1–2 minutes to go live.

This is deliberately different from the legal documents (see below), which are generated from
Markdown in a private repo and copied over by a script. That indirection exists only because those
sources are private, and it has already caused stale pages to sit live for months. Nothing here
needs it.

## Files

| File | What it is |
|---|---|
| `index.html` | Landing page. |
| `charities.html` | The eight charities selectable in the app, the GiveWell / effective-giving explainer, where the money goes, and the donations ledger. |
| `about.html` | About the maker. |
| `impressum.html` | Legal notice required by § 5 DDG. Details copied from the Terms' contact section. |
| `styles.css` | All styling, shared by every page. No web fonts, no CDN, no analytics, no JavaScript. |
| `me.webp` | Portrait on the About page, 480×480, square crop of the original photo (metadata stripped by `cwebp`). |
| `shots/*.webp` | App Store marketing images on the landing page, 642 px wide. |
| `icon.png` | App icon, 384×384, shown on the landing page. |
| `apple-touch-icon.png` | 180×180, used as favicon, header logo and home-screen icon. |
| `og.png` | 1200×630 link-preview card for LinkedIn / Slack / iMessage etc. |
| `app-store-badge-black.svg` | Apple's official "Download on the App Store" badge, shown in light mode. |
| `app-store-badge-white.svg` | Same badge, white variant, swapped in under `prefers-color-scheme: dark`. |
| `.nojekyll` | Stops GitHub's Jekyll pass from touching anything. |

**The header and footer are copied into every page.** With no generator, that is the price of having
several pages — when you change one, change all four.

**Bump `styles.css?v=N` in all four pages whenever `styles.css` changes.** GitHub Pages lets browsers
cache the stylesheet for 10 minutes, so without a new `?v=` a visitor can get new HTML with old CSS.
Inline SVGs also carry their own `width`/`height` so they stay small even then.

The three PNGs are derived from `icon2.png` in the app repo, resized with `sips` (built into
macOS). The `og:image` URLs are absolute — link scrapers ignore relative ones.

`shots/{limits,blocked,charity}.webp` are `AppStore_image{1,3,2}-6.5in-1284x2778.png` from
`Time2Give/build/asc-screenshots/`, made with `sips -Z 1389` then `cwebp -q 80`.

The two badge SVGs are Apple's unmodified artwork, pulled from
`tools.applemediaservices.com/api/badges/download-on-the-app-store/{black,white}/en-us` and committed
here so the page still makes no external requests. Apple's marketing guidelines apply: don't recolour
or restyle them, and keep them at least 40px tall. The App Store link is deliberately
`https://apps.apple.com/app/id6758275773` — no `/de/` and no `?l=`, so Apple redirects each visitor to
their own storefront and language.

## Copy rules

Wording about money must match the Terms: users **buy screen time**, and **we donate all profits we
make**. Never write "your money goes to charity" or suggest the user is donating. The site names the
charities only to identify them — no logos, no implied partnership.

## Recording a donation

The site promises that the year's profits are donated **at the end of each year**, and that each
donation is then published with its receipt. For each one:

1. Put the receipt in `receipts/`, named `YYYY-MM-DD-charity.pdf` (redact anything personal).
2. Add a row at the top of the ledger `<tbody>` in `charities.html` — the comment there shows the
   format — and delete the "No donations yet" row after the first one. That row names the first
   year ("end of 2026"); update it if that slips.

## Related repos

- **App source**: `d0d00/Time2Give` (private; the name predates two renames). The charity list comes
  from `ScreenLimit/ScreenLimit/Core/Models/Charity.swift` — if that changes, update `charities.html`.
- **Legal documents**: `d0d00/lock4good-legal` → https://d0d00.github.io/lock4good-legal/
  Privacy Policy and Terms live there, and those exact URLs are registered in App Store Connect and
  hardcoded in the app's Settings screen. **Do not move them here** without changing all three
  together.
