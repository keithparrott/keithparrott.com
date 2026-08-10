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

## Before you deploy

Update the placeholder domain in two spots:

- `astro.config.mjs` — `site: 'https://example.com'`
- `src/consts.ts` — `SITE_URL`

These are used for the RSS feed and canonical links, so they should match your real domain.

Also edit the bio text in `src/pages/index.astro` — it's a placeholder.

## Commands

| Command           | Action                                       |
| :----------------- | :-------------------------------------------- |
| `npm install`       | Install dependencies                          |
| `npm run dev`       | Start local dev server at `localhost:4321`    |
| `npm run build`     | Build the production site to `./dist/`        |
| `npm run preview`   | Preview the production build locally          |

## Deploying

`npm run build` produces a static `dist/` folder that can be hosted anywhere
(Netlify, Vercel, GitHub Pages, Cloudflare Pages, or any static file host).
No server or database required.
