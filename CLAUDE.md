# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**kaffon-hub** is a static HTML portal for hosting and sharing interactive tools. No build step, no dependencies — open any HTML file directly in a browser or access via GitHub Pages at `https://lkasdorf.github.io/kaffon-hub/`.

## Repository Structure

- `index.html` — Landing page with links to all tools (dark theme, Kaffon branding)
- `pages/` — Self-contained HTML tools (each file includes embedded CSS, JS, and data)
- `assets/` — Kaffon logos (SVG)

## Adding a New Page

1. Place the HTML file in `pages/`
2. Add a new `<li>` entry in `index.html` inside `<ul class="links">` with:
   - Link to `pages/<filename>.html` with `target="_blank" rel="noopener"`
   - Title, description, and `.link-meta` div with "Hinzugefügt" and "Aktualisiert" dates (format: TT.MM.JJJJ)
3. Add a row in `README.md` under "Gehostete Seiten" with the GitHub Pages link: `https://lkasdorf.github.io/kaffon-hub/pages/<filename>.html`
4. When updating an existing page, change only the "Aktualisiert" date in `index.html`

## Conventions

- All UI text uses German domain terminology
- Pages are fully self-contained single-file HTML applications (no external dependencies)
- Sorting uses German locale: `localeCompare(b, 'de')`
- Line endings enforced as LF via `.gitattributes`
- `.claude/` directory is gitignored
