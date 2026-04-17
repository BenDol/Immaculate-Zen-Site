# Immaculate Zen — Public Site

Static site for the Immaculate Zen music project. Hosts the public landing page,
Privacy Policy, and Terms of Service used for TikTok / X / Meta developer-app
reviews.

## Files

- `index.html` — landing page (brand, catalog preview, YouTube link)
- `privacy.html` — Privacy Policy (names TikTok scopes explicitly)
- `terms.html` — Terms of Service
- `styles.css` — shared styling
- `images/banner.png`, `images/profile.png` — branding

Plain HTML + CSS. No build step, no Jekyll, no Node — just static files.

## Deploying to GitHub Pages

### Option A — Dedicated repo (recommended for a clean public URL)

1. Create a new public GitHub repo, e.g. `immaculate-zen-site`.
2. Copy the contents of this folder into the repo root:
   ```
   cp -r site/* path/to/immaculate-zen-site/
   cd path/to/immaculate-zen-site
   git init && git add . && git commit -m "initial site"
   git branch -M main
   git remote add origin git@github.com:<your-user>/immaculate-zen-site.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: main / (root) → Save.**
4. Wait ~60 seconds. The site publishes at
   `https://<your-user>.github.io/immaculate-zen-site/`.

### Option B — Keep inside this repo and serve from `/site`

GitHub Pages can serve from a subfolder of the main repo:

1. Push this folder (the `site/` folder) to the remote.
2. On GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: main / `/docs`.**
3. Note: Pages only serves from `/` or `/docs` at the repo root — so if you use
   Option B, rename `site/` to `docs/` first. Otherwise use Option A.

### Option C — Custom domain

Once the site is live at the default `github.io` URL:

1. On GitHub: **Settings → Pages → Custom domain** → enter e.g.
   `immaculatezen.com`.
2. At your DNS provider, add a CNAME record pointing to
   `<your-user>.github.io`.
3. Enable "Enforce HTTPS" once GitHub provisions the certificate (takes a few
   minutes).

## Using with TikTok developer portal

When submitting the TikTok app for review, use URLs like:

- **Web/Desktop URL:** `https://<your-user>.github.io/immaculate-zen-site/`
- **Terms of Service URL:** `https://<your-user>.github.io/immaculate-zen-site/terms.html`
- **Privacy Policy URL:** `https://<your-user>.github.io/immaculate-zen-site/privacy.html`

All three must return HTTP 200 and load real content — TikTok reviewers actually
visit them.

## Updating the site

- Edit the HTML files directly. No build step.
- To refresh the recent-releases list, update the `<ul class="track-list">`
  block in `index.html`.
- To update branding, replace `images/banner.png` and `images/profile.png`.
- Bump the **Last updated** date on `privacy.html` and `terms.html` whenever
  either is revised — TikTok flags policies that look stale.
