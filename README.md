# davidkircos.com

Personal website. Plain HTML and one CSS file — no build step, no dependencies, no framework.

A single page: about + career summary. The old blog posts (68 posts, 2016–2022, migrated from the previous Mezzanine site) were removed but live in git history — commit `14230b1` has all of them plus their images if they're ever wanted back.

## Structure

```
index.html   The whole site
style.css    The only stylesheet
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
