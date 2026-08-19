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
| `.nojekyll` | Stops GitHub's Jekyll pass from touching anything. |

All three images are derived from `icon2.png` in the app repo, resized with `sips` (built into
macOS). The `og:image` URL in `index.html` is absolute — link scrapers ignore relative ones.

## Related repos

- **App source**: `d0d00/Time2Give` (private; the name predates two renames)
- **Legal documents**: `d0d00/lock4good-legal` → https://d0d00.github.io/lock4good-legal/
  Privacy Policy and Terms live there, and those exact URLs are registered in App Store Connect and
  hardcoded in the app's Settings screen. **Do not move them here** without changing all three
  together.
