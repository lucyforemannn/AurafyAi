# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AurafyAi is a static single-page landing page for a brand studio targeting content creators. It is a single self-contained file with no build system, package manager, or backend.

## Running the Project

There is no build step. To view the site locally:

```bash
python -m http.server 8000
# then open http://localhost:8000 in a browser
```

Or simply open `index.html` directly in a browser.

## Architecture

Everything lives in `index.html` (HTML, CSS, and JS are all embedded in a single ~1,400-line file):

- `<style>` block — all CSS, including custom properties, animations, and responsive styles
- `<body>` — semantic HTML sections: `#hero`, `#services`, `#process`, `#about`, `#contact`
- `<script>` block — vanilla JS at the bottom of the file

**External dependencies:** Google Fonts only (Cormorant Garamond, DM Sans). No npm packages, no frameworks.

## CSS Conventions

CSS custom properties (defined on `:root`) control the design system:

```css
--white, --off, --sand, --stone, --mist, --ink, --gold, --deep
```

Typography is fluid using `clamp()`. Animations use `@keyframes riseUp` (section reveals) and `@keyframes marquee` (infinite scrolling ticker). Scroll-triggered reveals are controlled by adding/removing the `.visible` class via IntersectionObserver.

## JavaScript Patterns

The script block handles:
- **Custom cursor** — a gold dot + trailing ring animated with `requestAnimationFrame`
- **Scroll reveals** — `IntersectionObserver` adds `.visible` to elements with `.reveal` class
- **Nav state** — adds `.scrolled` to `<nav>` once the user scrolls past the viewport height

All JS is vanilla DOM APIs; no libraries or frameworks are used.
