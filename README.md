# keith-parrott-site

Personal site: a home page and a blog for posts and book reviews. Built with
[Astro](https://astro.build), Markdown content, no JS framework, minimal CSS.

## Writing a post

Add a new Markdown file to `src/content/blog/`, e.g. `src/content/blog/my-post.md`:

```md
---
title: "Your title"
description: "One sentence for the RSS feed and page meta description."
pubDate: 2026-08-09
tags: ["book-review"]   # optional; use "book-review" to get the "Book review" badge
---

Write the post in Markdown here.
```

Fields:

- `title`, `description`, `pubDate` — required
- `updatedDate` — optional, shown next to the pub date if set
- `tags` — optional array of strings; `book-review` gets a badge on listings
- `draft: true` — optional, excludes the post from all pages and the RSS feed

The URL is derived from the filename, so `src/content/blog/my-post.md` becomes `/blog/my-post/`.

Also edit the bio text in `src/pages/index.astro` — it's a placeholder.

## Commands

| Command           | Action                                       |
| :----------------- | :-------------------------------------------- |
| `npm install`       | Install dependencies                          |
| `npm run dev`       | Start local dev server at `localhost:4321`    |
| `npm run build`     | Build the production site to `./dist/`        |
| `npm run preview`   | Preview the production build locally          |

## Deploying (GitHub Pages)

Site domain: `www.keithparrott.com`.

Deploys automatically via `.github/workflows/deploy.yml` on every push to
`main`. One-time setup, in the GitHub repo's **Settings → Pages**:

1. Under "Build and deployment", set **Source** to "GitHub Actions".
2. Under "Custom domain", enter `www.keithparrott.com` and save (this writes
   the same value already committed in `public/CNAME`).
3. At your DNS provider, add a `CNAME` record: `www` → `<github-username>.github.io`.
4. Once DNS propagates, check "Enforce HTTPS" in the same Pages settings page.

If you also want the bare `keithparrott.com` (no `www`) to work, add `A`
records for the apex domain pointing at GitHub Pages' IPs
(185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153), or set
up a redirect at your registrar.
