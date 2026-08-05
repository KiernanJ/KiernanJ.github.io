# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website for Kiernan Jennings, hosted on GitHub Pages at `kiernanjennings.com`.
Hand-authored static HTML and CSS — no framework, no build system, no JavaScript, no backend,
and no third-party dependencies. The design is minimal and multi-page (one page per topic),
loosely modeled on Bandcamp's dense, functional, light-background aesthetic.

## Development

**Local preview:** Open any `.html` file with VS Code Live Server (configured for port 5501),
or run `python3 -m http.server` from the repo root. There is no build step.

**Deployment:** Push to `main`. GitHub Pages deploys to `kiernanjennings.com` via the CNAME file.

## Architecture

Five sibling pages, each a complete standalone HTML document:

- `index.html` — About: intro, focus areas, news
- `research.html` — research overview, directions, publications
- `projects.html` — software projects
- `cv.html` — education, technical skills, areas of practice
- `contact.html` — contact details
- `assets/css/style.css` — the site's only stylesheet

The header/nav and footer are duplicated verbatim in each page (no templating layer). **When
adding or renaming a page, update the `<nav class="site-nav">` block in every page**, and set
`aria-current="page"` on the link matching the current page — that attribute is what styles the
active nav item.

## Conventions

- Tabs for indentation, in both HTML and CSS.
- Colors, spacing, and the content max-width live in `:root` custom properties at the top of
  `style.css`. Change them there rather than hardcoding values.
- Reusable classes: `.wrap` (centered column), `.section` (labeled block), `.grid`/`.card`
  (card grid), `.entries` (dated list: news, education, publications), `.tag` (status chip,
  `.tag-live` for the green variant), `.btn`/`.btn-secondary`.
- `.grid` auto-fits to three columns at desktop width. Add `.grid-2` for card sets with an
  **even** count (research, projects) so the last card doesn't orphan on its own row; plain
  `.grid` suits sets of three. Adding or removing a card means rechecking which applies.
- Prefer HTML comments marking where real content goes over placeholder or invented content —
  several exist already (CV PDF link, undergraduate degree, LinkedIn/Scholar/ORCID rows).
