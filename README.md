# Delna Davis — Portfolio (Static Build)

This is a converted, fully static version of the portfolio. The original
project was built with **TanStack Start**, which is a server-rendered
(SSR) framework — it expects a Node/Nitro server (or Cloudflare Worker) to
run at request time. Netlify's default static hosting doesn't run that
server, which is what caused the 404 errors.

## What changed

- Removed `@tanstack/react-start`, `@tanstack/react-router`,
  `@tanstack/router-plugin`, `nitro`, and the Lovable Vite/SSR plugin.
- Removed the SSR-only files: `server.ts`, `start.ts`, `router.tsx`,
  `routeTree.gen.ts`, and `routes/__root.tsx`.
- The page content (`routes/index.tsx`) is now a plain React component at
  `src/App.tsx`, mounted by `src/main.tsx` into a plain `index.html` — a
  standard client-side single-page app built by Vite.
- All visual design, copy, animations (Framer Motion / `motion`), images,
  and the full Tailwind v4 theme in `styles.css` are unchanged.
- Added `netlify.toml` and `public/_redirects` so Netlify serves the built
  `dist/` folder correctly with a SPA fallback.

## Local development

```bash
npm install
npm run dev
```

## Build

```bash
npm run build
```

This outputs static files to `dist/` — plain HTML, CSS, and JS, no server
required.

## Deploying to Netlify

1. Push this folder to a Git repo (or drag-and-drop the `dist/` folder
   after running `npm run build` into Netlify's "Deploy manually" box).
2. If connecting a repo, set:
   - Build command: `npm run build`
   - Publish directory: `dist`
   (Both are already pre-set in `netlify.toml`.)
3. Deploy — there is no server/runtime needed, so there's nothing left to
   cause a 404.
