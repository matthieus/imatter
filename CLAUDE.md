# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A personal Jekyll blog ("I Matt(hieu Scholl)er") built on the **Minimal Mistakes** theme (`minimal-mistakes-jekyll` gem, currently 4.28.0). Hosted at `http://www.imatter.io`. Theme docs: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/

## Commands

```bash
bundle install                      # install gems after Gemfile changes
bundle exec jekyll serve            # dev server with live reload at http://localhost:4000
bundle exec jekyll serve --drafts   # also render files in _drafts/
bundle exec jekyll build            # one-off build into _site/
bundle update minimal-mistakes-jekyll   # bump theme version
```

`_config.yml` is **not** auto-reloaded — restart `jekyll serve` after editing it.

## Architecture

This repo intentionally contains very little: only site-specific content and config. Everything else (layouts, includes, sass, default assets, default `_data/navigation.yml` and `_data/ui-text.yml`) lives inside the `minimal-mistakes-jekyll` gem and is pulled in at build time.

To customize anything theme-provided, **copy the file from the gem into the same path here** and edit the local copy — Jekyll's theme-gem precedence makes the local file win. Locate the gem with `bundle info minimal-mistakes-jekyll`. Common override targets:

- `_layouts/` — page templates (`single`, `home`, `archive`, `splash`, `posts`, `categories`, `tags`, etc.)
- `_includes/` — partials (head, masthead, footer, author profile, etc.)
- `_sass/` and `assets/css/main.scss` — styling; skin is selected via `minimal_mistakes_skin` in `_config.yml`
- `_data/navigation.yml` — top nav links
- `_data/ui-text.yml` — translatable UI strings

Content lives in:

- `_posts/YYYY-MM-DD-title.md` — blog posts (date in filename is required)
- top-level `*.markdown` / `*.md` — standalone pages (e.g. `about.markdown`, `index.markdown`)
- `_drafts/` — unpublished drafts (not currently present; create as needed, render with `--drafts`)

### Source of post content

Post drafts are written and maintained in **`../aiiaii/blog/`** (sibling repo/directory), not in this repo. Filenames there use a numeric ordering prefix (e.g. `1 - Leaving LinkedIn and starting something.md`) and freeform titles; some are tagged `(draft)` or `(meta)` and should not be published. To publish a draft into this site, copy/adapt it into `_posts/` with the required `YYYY-MM-DD-title.md` filename and Minimal Mistakes front matter (`layout`, `title`, `date`, `categories`, etc.). Treat `../aiiaii/blog/` as the writing workspace and this repo as the publishing surface.

`permalink: /:categories/:title/` in `_config.yml` means each post's URL is built from its `categories:` front matter plus title.

## Front matter conventions

Posts and pages select a Minimal Mistakes layout via `layout:` (`single`, `home`, `page`, `archive`, `splash`, etc.). To avoid repeating front matter on every post, prefer setting site-wide defaults under `defaults:` in `_config.yml` (e.g. `layout: single`, `author_profile: true`, `read_time: true`, `comments: true`) rather than copying into each file. See the theme's quick-start guide for the canonical block.

For multi-author setups, author metadata goes in `_data/authors.yml` and is referenced by `author:` in post front matter; for this single-author site, top-level `author:` in `_config.yml` is sufficient.

## Notes

- `_site/`, `.jekyll-cache/`, `.jekyll-metadata`, `.sass-cache`, `vendor/` are build artifacts and are gitignored — never edit or commit them.
- `Gemfile.lock` **is** committed; update it via `bundle update` rather than hand-editing.
