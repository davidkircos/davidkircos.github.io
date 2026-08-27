# davidkircos.com

Personal website. Plain HTML and one CSS file — no build step, no dependencies, no framework.

The home page is a single page: about + resume. The old blog posts (68 posts, 2016–2022, migrated from the previous Mezzanine site) live under `archive/` — served at `/archive/` but not linked from the home page.

## Structure

```
index.html              Home page (about + resume)
style.css               The only stylesheet
CNAME                   Custom domain for GitHub Pages
archive/index.html      Index of all 68 archived blog posts
archive/<slug>/         One folder per archived post
archive/assets/         Images used by archived posts
```

## Preview locally

```
python3 -m http.server 8000
```

Then open http://localhost:8000

## Deploy

Hosted free on GitHub Pages, served from the `main` branch root. Deploys happen automatically:

```
git add -A && git commit -m "Update" && git push
```

Live about a minute later. No other steps.

## Pointing davidkircos.com at this site

When ready to switch the domain:

1. Add a file named `CNAME` (no extension) at the repo root containing exactly `davidkircos.com`, commit and push.
2. At your DNS provider, add these records:
   - `A` records for the apex `davidkircos.com` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` record for `www` → `davidkircos.github.io`
3. In the GitHub repo: Settings → Pages → check "Enforce HTTPS" (available a few minutes after DNS propagates).
