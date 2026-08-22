# Setting up the new site

## What changed

The old site was a single `README.md` rendered by the `jekyll-theme-minimal`
theme. This replaces it with a small custom Jekyll site: five pages, a blog, and
one stylesheet. No build tools, no Node, no gems to install — GitHub Pages builds
it for you on push.

## Files

```
_config.yml                 site settings — EDIT THIS FIRST
_layouts/default.html       shell: sidebar, nav, footer
_layouts/post.html          blog post wrapper
assets/css/main.css         all styling
assets/files/               CV PDF lives here
index.md                    home
research.md                 what you work on
publications.md             full publication list
writing.md                  blog index
cv.md                       CV page
_posts/                     blog posts, one file each
```

`Image/MunaProfile.jpeg` stays where it is — the layout points at it.

## Installing

1. Copy every file in this folder into the root of `munawira.github.io`,
   keeping the folder structure.
2. **Delete or replace the old `README.md`.** The new `_config.yml` excludes
   `README.md` from the build, so Jekyll will use `index.md` for the homepage.
   Keep a `README.md` if you want a repo description — it just will not be
   published anymore.
3. Commit and push to `main`. GitHub Pages rebuilds in about a minute.

## Before you push — three things to fix

In `_config.yml`:

- `scholar_url` — replace `REPLACE_ME` with your Google Scholar profile URL, or
  delete the line and remove the Scholar link from `_layouts/default.html`.
- `linkedin_url` — same.

Everywhere:

- `HOOP: Hint-based Out-of-Order Processing for GPGPUs` is my best guess at the
  full title from the acronym. Correct it in `index.md` and `publications.md`.
- Check the author list on PRISM and HOOP in `publications.md` — I listed you and
  Prof. Singh; add co-authors if there are any.
- Check the news dates. SBAC-PAD and ICCD are set to Aug 2026, the JPDC
  invitation to Jul 2026, Computing Frontiers to May 2026.

## Writing a post

Create a file in `_posts/` named `YYYY-MM-DD-some-slug.md`:

```markdown
---
title: "Your title here"
date: 2026-09-01
tags: [warp scheduling, accel-sim]
excerpt_text: "One sentence that appears in the post list."
---

Body in Markdown. Headings use ## and become serif subheads.
```

The layout is applied automatically. The post appears on `/writing/` and the
three most recent show on the homepage. URLs come out as
`munawira.github.io/writing/some-slug/`.

Two starter posts are included. Edit or delete them freely — they are written in
a plain first-person voice, but check the numbers against your own results before
publishing. The 40% stall figure and the load-induced share come from your PRISM
motivation data.

## Previewing locally (optional)

Not required, but if you want to see changes before pushing:

```bash
gem install bundler jekyll
bundle exec jekyll serve
```

Then open `http://localhost:4000`.

## Design notes

Two typefaces, both from Google Fonts and loaded in `_layouts/default.html`:
Newsreader for headings and lede text, IBM Plex Sans for body, IBM Plex Mono for
dates, venues, and labels.

The small striped mark under your name in the sidebar is a warp-issue trace —
teal blocks are issued cycles, short rust blocks are stalls. It is hand-written
markup in `_layouts/default.html`, so you can change the pattern or remove it.

Colours are defined once at the top of `main.css` as CSS variables. Changing
`--issue` changes every link and accent on the site.
