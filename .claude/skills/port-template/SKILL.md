---
name: port-template
description: Port a screen from the resources/templates prototype (biblioteca, detalle, reproductor, auth, salon, nav) into the Next.js app/ directory as typed components. Use when implementing a UI screen that exists in the prototype.
---

Port the screen `$ARGUMENTS` from `resources/templates/` into the Next.js app.

1. Read the source: `resources/templates/$ARGUMENTS.jsx`, plus the parts of `styles.css`, `data.jsx`, and `app.jsx` (routing/state) it depends on. Note which fonts, CSS variables and data shapes it uses.
2. Before writing code, read the relevant guides in `node_modules/next/dist/docs/` (routing, layouts, Server vs Client Components, caching with `cacheComponents`). This Next.js version differs from training data.
3. Map the prototype to the App Router:
   - Hash routes (`{ name: "detalle", id }`) become real routes/segments under `app/` (e.g. `app/juegos/[id]/page.tsx`).
   - Keep components Server Components by default; add `"use client"` only for the interactive pieces (state, effects, event handlers, canvas/game loops).
   - Prototype data from `data.jsx` becomes a typed module (e.g. `lib/` or `app/_data/`) with exported TypeScript types.
   - Do not port `window`/`location.hash` hacks, `React` globals, or CDN/Babel scripts. localStorage access must stay inside client components.
4. Translate the styling to Tailwind v4 utilities. Put shared design tokens (colors, fonts) in `app/globals.css` under `@theme`. Load fonts with `next/font/google`, not `<link>` tags.
5. Keep all user-facing text in Spanish.
6. Verify: `npm run lint` and `npx tsc --noEmit`. Fix any errors before reporting back.
7. Summarize which files were created, any behavior intentionally not ported, and open questions.
