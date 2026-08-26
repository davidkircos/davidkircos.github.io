# davidkircos.com

Personal website and blog. Plain HTML and one CSS file — no build step, no dependencies, no framework.

Migrated from the old Mezzanine (Django) site: the About page is now the home page, plus all 68 blog posts (2016–2022) with images copied into `assets/` so nothing depends on external hosting.

## Structure

```
index.html            Home page (about + recent posts)
style.css             The only stylesheet
blog/index.html       Blog index, posts grouped by year
blog/<slug>/index.html  One folder per post (URLs match the old site)
happiness/index.html  Historical happiness-tracking page (linked from a post)
assets/               Images used by posts
```

## Writing a new post

1. Copy an existing post folder, e.g. `blog/cherish-every-moment/`, to `blog/my-new-post/`.
2. Edit `blog/my-new-post/index.html`: change the `<title>`, `<h1>`, date, and article content.
3. Add a line to `blog/index.html` under the current year (create the `<h2>` year heading if it doesn't exist yet), newest posts first:
   ```html
   <li><a href="my-new-post/">My New Post</a></li>
   ```
4. Optionally add it to "Recent posts" in `index.html` (keep that list to ~5).

Images go in `assets/<post-slug>/` and are referenced from a post as `../../assets/<post-slug>/photo.jpg`.

## Preview locally

```
python3 -m http.server 8000
```

Then open http://localhost:8000

## Deploy

Hosted free on GitHub Pages, served from the `main` branch root. Deploys happen automatically:

```
git add -A && git commit -m "New post" && git push
```

Live about a minute later. No other steps.

## Pointing davidkircos.com at this site

When ready to switch the domain:

1. Add a file named `CNAME` (no extension) at the repo root containing exactly `davidkircos.com`, commit and push.
2. At your DNS provider, add these records:
   - `A` records for the apex `davidkircos.com` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` record for `www` → `davidkircos.github.io`
3. In the GitHub repo: Settings → Pages → check "Enforce HTTPS" (available a few minutes after DNS propagates).

Old URLs like `/blog/skiing-into-the-night/` keep working — the folder structure mirrors the old site's URLs.
