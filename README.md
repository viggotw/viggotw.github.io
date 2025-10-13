# Teknobabbel website

Content repository for [teknobabbel.no](https://teknobabbel.no), built with **Jekyll** and hosted on **GitHub Pages**.

---

## Structure

| Folder / File | Purpose |
|----------------|----------|
| `_posts/` | Markdown **blog** entries (internal content). |
| `_links/` | External **link** entries (op-eds, columns, media). |
| `_publications/` | Academic publications (planned). |
| `assets/images/` | Images for posts and pages. |
| `assets/papers/` | PDFs for academic publications. |
| `index.md` | Homepage. |
| `writing_popular.md` | “Popular Writing” feed combining BLOG + LINK. |
| `courses.md`, `contact.md` | Additional static pages. |
| `_config.yml` | Site configuration. |

---

## Authoring checklist

1. Decide the type: **BLOG**, **LINK**, or later **PUBLICATION**.  
2. Create the file:
   - `_posts/YYYY-MM-DD-slug.md` for BLOG.
   - `_links/YYYY-MM-DD-slug.md` for LINK.
3. Add front matter fields (see templates below).
4. Write content (if BLOG) or just metadata (if LINK).
5. Commit and push → GitHub Pages rebuilds automatically.

---

## Front-matter templates

### BLOG
```yaml
---
title: "Post title"
date: 2025-10-13
summary: "Short 1–2 sentence description."
tags: [ai, software]
---
Main Markdown content here.
![Alt text](/assets/images/slug/hero.jpg)
More content...
```

### LINK
```yaml
---
title: "Newspaper column title"
date: 2025-03-22
summary: "Brief description of the article."
external_url: "https://example.com/article"
tags: [op-ed]
---
(No content needed; just metadata.)
```

## Maintenance tips

- Images → assets/images/<slug>/
- Keep summaries under 200 chars for clean list display.
- To preview locally, install Ruby + Bundler and run bundle exec jekyll serve.
- Custom domain is configured through the repository settings (teknobabbel.no).

## License

Personal website content © Viggo Tellefsen Wivestad.
Code snippets and templates may be reused with attribution.