# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

- Package manager: pnpm
- Framework: Astro 5 (ESM)
- Dev server: localhost:4321 (default)

Commands
- Install deps: pnpm install
- Start dev server: pnpm dev
- Build: pnpm build (outputs to dist/)
- Preview built site: pnpm preview
- Astro CLI (extras): pnpm astro check (type- and config-check), pnpm astro -- --help

Notes on tests and linting
- No test runner or linter is configured in this repo. There are no package scripts for test or lint.

High-level architecture
- src/pages: File-based routing. .astro files here map to routes. For example, src/pages/index.astro → /.
- src/layouts: Shared page shells. Layout.astro applies global CSS and fonts and renders <slot /> for page content.
  - Global CSS imported in the layout: src/styles/global.css
  - Fonts imported via @fontsource-variable/fredoka
- src/components: Reusable .astro components (e.g., Welcome.astro). Import into pages or layouts as needed.
- src/assets: Static assets imported by components/pages (Astro handles optimized asset URLs).
- astro.config.mjs: Project configuration (currently minimal). Extend here for integrations, adapters, redirects, etc.
- tsconfig.json: Extends astro/tsconfigs/strict for strong typing. Includes .astro types.

Development workflow
- Add a new page by creating a .astro (or .md/.mdx if enabled later) under src/pages; the file path defines the route.
- Use a layout by importing from src/layouts and wrapping page content in the layout component.
- Keep shared UI in src/components and import where needed.
- Static assets can be placed in src/assets and imported; site-wide public files (served as-is) can go in public/.

