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

## Local development (WSL / Windows)

Recommended: do all Ruby/Jekyll work inside Linux (WSL) – not on the Windows filesystem – for speed and fewer path issues.

1. Install WSL (Ubuntu) if you haven't:
   - In Windows PowerShell (admin): `wsl --install -d Ubuntu` then reboot if prompted.
2. Open Ubuntu (WSL) terminal.
3. Clone (or move) the repo into your Linux home directory (avoid `/mnt/c/...` for performance):
   ```bash
   cd ~
   git clone https://github.com/viggotw/viggotw.github.io.git
   cd viggotw.github.io
   ```
4. Install dependencies (minimal approach):
   ```bash
   sudo apt update
   sudo apt install -y build-essential ruby-full git
   gem install bundler
   ```
   (Optional) For finer Ruby version control use rbenv/asdf instead of `ruby-full`.
5. Install gems:
   ```bash
   bundle config set path vendor/bundle   # keeps gems inside the repo (optional)
   bundle install
   ```
6. Serve the site locally:
   ```bash
   bundle exec jekyll serve --livereload
   ```
   Then open http://localhost:4000 in a browser. If you want to test from outside WSL (rare), use `--host 0.0.0.0`.
7. Editing workflow:
   - Add / edit Markdown files in `_posts/`, `_links/`, etc.
   - Images into `assets/images/<slug>/` (create folder if needed).
   - Site auto-regenerates; refresh the browser.
8. Clean & rebuild if things look stale:
   ```bash
   bundle exec jekyll clean
   bundle exec jekyll serve
   ```
9. Update dependencies (infrequent): update versions in `Gemfile` then run `bundle update`.

Troubleshooting:
 - Missing gem error → run `bundle install` again.
 - Encoding/path issues on Windows → ensure you're working inside the WSL (Linux) path, not `/mnt/c`.
 - Port already in use → change with `--port 4001`.

## License

Personal website content © Viggo Tellefsen Wivestad.
Code snippets and templates may be reused with attribution.