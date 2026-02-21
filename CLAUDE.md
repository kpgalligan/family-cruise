# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Astro 5 static site with React interactive components, Tailwind CSS 4, and Framer Motion animations. Built as a content-driven website template with contact form integration via Web3Forms.

## Commands

- `npm run dev` — Dev server at localhost:4321
- `npm run build` — Production build to `./dist/`
- `npm run preview` — Preview production build locally
- `npm run check` — Run all checks (type-check + lint + format:check)
- `npm run lint` / `npm run lint:fix` — ESLint
- `npm run format` / `npm run format:check` — Prettier
- `npm run type-check` — Astro type checking (`astro check`)

No test framework is configured.

## Architecture

**Component model:** Astro components (`.astro`) render as static HTML with zero JS. React components (`.tsx`) are used only for interactive features and require `client:*` directives (`client:load`, `client:idle`).

**Routing:** File-based via `src/pages/`. Pages include `/`, `/about`, `/contact`, `/features`, `/example` (MDX).

**Layout:** Single base layout at `src/layouts/Layout.astro` handles SEO metadata, Open Graph, and Twitter Card tags.

**Animations:** `src/components/ScrollReveal.tsx` wraps content in Framer Motion scroll-triggered animations with configurable direction, delay, and spring physics.

**Contact form:** `src/components/ContactForm.astro` uses Web3Forms (configured in `src/config/site.mjs`). Includes client-side validation, honeypot spam protection, and ARIA accessibility attributes.

**Site config:** `src/config/site.mjs` — central config for site title, URL, OG image, and Web3Forms access key.

## Code Style

- **Formatting:** Prettier with tabs, double quotes, semicolons, trailing commas (ES5), 80 char width
- **Linting:** ESLint with TypeScript strict, Astro, and React plugins
- **TypeScript:** Strict mode (extends `astro/tsconfigs/strict`)
- **Unused vars:** Prefix with underscore (`_`) to suppress warnings

## Build Optimizations

Production builds use lightningcss for CSS minification, terser for JS (strips console/debugger), auto-inlined stylesheets, and HTML compression. Configured in `astro.config.mjs`.
