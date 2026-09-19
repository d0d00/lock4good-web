# lock4good-web

The public website for the **Lock4Good** iOS app.

**Live**: https://d0d00.github.io/lock4good-web/

Currently a single-page placeholder. It will grow into the full project site.

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
| `index.html` | The entire site. No JavaScript, no external requests — no web fonts, no CDN, no analytics. |
| `icon.png` | App icon, 384×384, shown on the page. |
| `apple-touch-icon.png` | 180×180, used as favicon and home-screen icon. |
| `og.png` | 1200×630 link-preview card for LinkedIn / Slack / iMessage etc. |
| `app-store-badge-black.svg` | Apple's official "Download on the App Store" badge, shown in light mode. |
| `app-store-badge-white.svg` | Same badge, white variant, swapped in under `prefers-color-scheme: dark`. |
| `.nojekyll` | Stops GitHub's Jekyll pass from touching anything. |

The three PNGs are derived from `icon2.png` in the app repo, resized with `sips` (built into
macOS). The `og:image` URL in `index.html` is absolute — link scrapers ignore relative ones.

The two badge SVGs are Apple's unmodified artwork, pulled from
`tools.applemediaservices.com/api/badges/download-on-the-app-store/{black,white}/en-us` and committed
here so the page still makes no external requests. Apple's marketing guidelines apply: don't recolour
or restyle them, and keep them at least 40px tall. The App Store link is deliberately
`https://apps.apple.com/app/id6758275773` — no `/de/` and no `?l=`, so Apple redirects each visitor to
their own storefront and language.

## Related repos

- **App source**: `d0d00/Time2Give` (private; the name predates two renames)
- **Legal documents**: `d0d00/lock4good-legal` → https://d0d00.github.io/lock4good-legal/
  Privacy Policy and Terms live there, and those exact URLs are registered in App Store Connect and
  hardcoded in the app's Settings screen. **Do not move them here** without changing all three
  together.
