# AGENTS.md

## Stack

- Astro 5, Tailwind CSS 3, TypeScript (strict)
- Package manager: **Bun** (lockfile is `bun.lockb`)
- Dark mode via Tailwind `class` strategy — toggled by ThemeToggle component
- Font: Onest Variable (imported in Layout)
- View transitions enabled via `astro:transitions`

## Commands

```bash
bun run dev       # astro dev
bun run build     # astro build → dist/
bun run preview   # astro preview (serves dist/)
```

No lint, typecheck, test, or format commands exist. Only `astro` is configured.

## Site

- URL: `https://codigoespntaneo.com` (set in `astro.config.mjs`)
- Language: Spanish (`<html lang="es">`)
- Content is Jean Otero's developer portfolio — all copy is in Spanish

## Structure

```
src/
  pages/          — 2 pages: index (main site), components (design system reference)
  layouts/        — Layout.astro (single layout, all meta/SEO/OG here)
  components/     — All .astro, no framework components (React/Svelte/etc)
  components/icons/ — SVG icon components
public/
  projects/       — Project images (webp)
  favicon1.svg
```

## Conventions

- Components are pure Astro (no JSX frameworks)
- Projects, experience, and skills data are hardcoded arrays inside component files (not from CMS or content collections)
- Adding a project: edit `PROJECTS` array in `src/components/Projects.astro`, add image to `public/projects/`
- Adding experience: edit `EXPERIENCE` array in `src/components/Experience.astro`
- Adding a skill: edit `SKILLS` array in `src/components/TechStack.astro`
- Icons go in `src/components/icons/`, follow existing `.astro` SVG pattern
- Tailwind classes use the `dark:` variant for dark mode

## Gotchas

- `components.astro` is a design system / component catalog page — not part of the main site navigation
- Project images use relative paths (`./projects/juego.webp`) — must be served from `public/`
- The `og-image.png` referenced in Layout.astro head does not exist in `public/` — will 404 on social previews
- No env files or secrets needed — all content is static
- `dist/` is in `.gitignore` — do not commit build output
