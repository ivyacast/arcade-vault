# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Stack gotchas

- Next.js 16.4.6 + React 19.3, App Router only (`app/`). Look up APIs in `node_modules/next/dist/docs/` rather than relying on memory.
- `next.config.ts` enables `cacheComponents` and `partialPrefetching`. Account for them when deciding caching/dynamic behavior and Suspense boundaries.
- Tailwind v4 is wired through the `@tailwindcss/turbopack` loader in `next.config.ts` (no `postcss.config`, no `tailwind.config`). Theme tokens live in `app/globals.css` under `@theme`.
- Import with the `@/*` alias (maps to repo root).

## Verifying changes

No test framework yet. After changes run:

```bash
npm run lint
npx tsc --noEmit
```
## Skills

Usa siempre su /frontend-design para diseñar la interfaz de usuario. 

## Design source

`resources/templates/` is a standalone prototype (React 18 UMD + in-browser Babel, global components, hash routing, localStorage). Treat it as the visual/UX reference to port into `app/` as typed Next.js components. Never import from it or carry over its globals, `window`/`location` hacks, or CDN scripts.

User-facing copy is in Spanish (matches the prototype).

## Workflow

Features follow Spec Driven Design: write the spec with `/spec`, then implement with `/spec-impl` (skills from `Klerith/fernando-skills`, see README).
