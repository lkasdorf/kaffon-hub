# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**EBD Interaktiv** is a self-contained, single-file HTML application for visualizing and filtering Entscheidungsbaumdiagramme (EBD) — decision tree diagrams used in German energy market processes (MaKo). Built by Leon Kasdorf.

## Running

No build step, no dependencies. Open `EBD_Interaktiv.html` directly in a browser.

## Architecture

The entire application lives in one HTML file (~1.4 MB) with embedded CSS, HTML, and JavaScript:

- **Data**: ~2,941 JSON records embedded as `const D = [...]` at the top of the `<script>` block. Each record has 16 fields: `ch`, `cn`, `ad`, `an`, `ebd`, `en`, `role`, `step`, `ps`, `pr`, `code`, `cl`, `eb`, `hint`, `jg`, `ng`.
- **Filtering**: Hierarchical cascading filters — selecting a Prozessbereich (chapter) narrows AD options, which narrows EBD options. `cascade()` manages this chain, `apply()` runs the full filter, `popSel()` populates dropdowns.
- **Rendering**: `render()` outputs paginated results (250/page) as dual-row table entries — a data row + a navigation row showing ja/nein branches. `detail()` opens a slide-out side panel.
- **Cluster coloring**: `rc()` maps cluster values (`Zustimmung`, `Ablehnung`, etc.) to CSS classes for color-coded rows.
- **Export**: CSV export via Blob/URL with semicolon delimiter.

## Conventions

- All UI text and variable names use German domain terminology (Prozessbereich, Rolle, Ebene, Prüfschritt, etc.)
- Sorting uses German locale: `localeCompare(b, 'de')`
- HTML escaping via `esc()` function for user-facing data
- No external dependencies — fully portable single file
