# Stack selection

The stack is chosen by app type and constraints, not by habit. The bias runs toward the least machinery that serves the app: fewer moving parts, faster start, nothing to explain. A build step, a framework, and a component library each have to earn their place.

## Decision table

| App type | Default stack | Reach for more when |
|---|---|---|
| Static page: landing, essay, announcement | Single HTML file, vanilla CSS, minimal JS | Many pages sharing chrome → Astro or Eleventy |
| Content site: docs, blog, portfolio | Astro or Eleventy (content collections, zero JS by default) | Heavy interactivity per page → islands (Astro + Preact) |
| Interactive tool: calculator, converter, editor, explorable | Single HTML file, vanilla JS, maybe a `<canvas>` | State graph gets deep (5+ interacting stateful components) → Vite + Preact/React |
| Dashboard / instrument panel | Vanilla JS + SSE or WebSocket; charts hand-rolled in SVG/canvas | Dozens of stateful widgets, user-configurable layout → Vite + React |
| Data app: CRUD, tables, forms, auth | Vite + React (SPA) against an API | SEO or first-paint matters → SvelteKit / Next |
| Game / sim / creative canvas | Canvas2D or WebGL/WebGPU; Three.js for 3D; UI chrome as plain DOM overlay | Never add a framework for the game loop; frameworks are for the menus, and usually not even then |
| Realtime collaborative | Framework (React/Svelte) + WebSocket; CRDT (Yjs) if concurrent editing | — |
| Prototype needed today | Single HTML file, everything inline, CDN scripts pinned to exact versions | It survives a week → give it a real structure |

## The no-build bias

A single HTML file that opens anywhere, or a folder of static files behind any HTTP server, is the most durable artifact on the web. Prefer it until one of these is true:

- TypeScript across many files is genuinely paying for itself
- Components are reused enough that copy-paste is causing drift
- A dependency you actually need ships only as an npm package

"I might need it later" is not one of the conditions. Adding Vite later is an afternoon; removing a framework later is a rewrite.

## CSS strategy

- **Default: vanilla CSS with custom properties.** The Taste Contract compiles into `:root` tokens — ground, ink, accent, radius, spacing unit, durations, font stacks — and every rule below references tokens. This makes the contract enforceable: grep the stylesheet for raw hex values and raw px radii to find drift.
- **Tailwind** is acceptable in framework apps, on one condition: the theme is overridden before the first component is written — fonts, full color scale from the contract, radius scale, shadows. Unthemed Tailwind emits the exact look the ban list exists to catch.
- **Component libraries** (shadcn, MUI, Radix themes) only under Quiet Pro and real time pressure — and even then, retokened first. Never as a source of visual identity.
- Layout with grid/flex and `clamp()` for fluid type; container queries where components must adapt. No CSS resets beyond a few lines (`box-sizing`, margin zeroing) — heavy resets are dead weight.

## Fonts

- Google Fonts by `<link>` for tools and prototypes; self-host woff2 for products (one less third-party request, no layout shift from late swaps).
- Two families maximum, plus an optional mono for data. Variable fonts preferred — one file, all weights.
- Always declare fallback stacks that roughly match metrics, and `font-display: swap`.
- Check the render: if the fallback is showing (wrong metrics, missing weights), the taste didn't ship.

## Icons

- Inline SVG, always: copied from an open set (Lucide, Feather, Tabler) or drawn by hand for signature elements. Inline means CSS can color them with tokens.
- No icon fonts, no emoji-as-icons, no icon `<img>` requests per glyph.
- Stroke width consistent across the set; match it to the map (1.5px fine for Instrument, 2.5–3px chunky for Toybox).

## Serving and pairing

- Local tools: any static server or a small FastAPI/Express process; pick an uncommon fixed port and print it on start.
- Live-data UIs: SSE over WebSocket when traffic is one-directional — simpler to serve, reconnects for free.
- Ship the taste tokens as one `<style>` or one `tokens.css` regardless of stack, so a later restyle is a one-file change.
