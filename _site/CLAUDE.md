# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal academic website for Taeyoon (Connor) Kwon, built with [Jekyll](https://jekyllrb.com/). Hosted as a GitHub Pages site at `Connoriginal.github.io` — pushing to `master` triggers automatic deployment.

## Development

```bash
jekyll serve        # local preview at http://localhost:4000
```

No build step beyond Jekyll. All external libraries (jQuery, Skeleton CSS, Font Awesome, Academicons) are vendored under `libs/external/`.

## Content architecture

**Almost all content updates go in `_data/` YAML files — not in HTML.**

| File | Purpose |
|------|---------|
| `_data/publications.yaml` | Papers list. Fields: `title`, `authors`, `venue`, `year`, `selected` (`y`/`n`), and optional links: `paper_pdf`, `demo`, `website`, `poster`, `video`, `code`, `data` |
| `_data/experience.yaml` | CV timeline entries. `category` must be `work` (renders left) or `school` (renders right) |
| `_data/main_info.yaml` | Name, title, email, profile pic path, CV path, social profile URLs |

**Layout flow:** `_layouts/default.html` wraps all pages with the shared header (photo, name, social icons), nav bar, and footer. `index.html` uses Liquid templates to iterate over `_data/` collections and render publications and the timeline.

The publications section has two tabs: **Papers** (all) and **Refereed Papers** (only entries with `selected: y`). Papers are grouped by `year` in descending order.

The CV PDF lives at `assets/cv/Taeyoon_s_CV.pdf`.

## Adding a publication

Add an entry to `_data/publications.yaml`. Minimal required fields:

```yaml
- title: "Paper Title"
  authors: "<b><u>Taeyoon Kwon</u></b>, Co-author Name"
  venue: "Conference Name Year"
  year: 2025
  paper_pdf: "https://arxiv.org/abs/..."
  selected: y   # or n to exclude from Refereed Papers tab
```

Use `<sup>‡</sup>` after author names for equal contribution, and `<b><u>Taeyoon Kwon</u></b>` to bold/underline the author's own name.
