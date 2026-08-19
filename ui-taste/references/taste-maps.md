# Taste maps

Nine committed aesthetic positions. Each is a full set of parameters: pick one, load its entry, fill the Taste Contract from it. The parameters are deliberately concrete — fonts by name, durations in ms, radii in px — because "make it feel premium" drifts and `letter-spacing: -0.02em` does not.

Every map ends with its **failure mode**: the way that map goes wrong when pushed too far. Put that failure mode on the contract's `Never` line.

## Current-era markers (last reviewed 2026-08)

What separates a current page from a 2020–2023 page. The anti-list in SKILL.md is more durable than this list — trends rotate, slop tells persist. Revisit this section yearly.

- Type is the layout's main event: oversized display sizes (clamp up to 8–12vw for heroes), variable fonts with real weight/width axes, tight leading on display sizes (0.95–1.05).
- Grounds are warm, not pure: off-whites (`#faf7f2`, `#f4f1ea`), and dark modes with a hue bias (blue-black `#0d1117`, green-black `#0c1210`) rather than neutral `#111`.
- Texture is back in small doses: fine grain/noise overlays (2–4% opacity), paper tones, hairline rules.
- Monospace as an accent voice for anything technical: labels, timestamps, metadata in a mono face while body stays serif/sans.
- Editorial and print-derived layout: asymmetric grids, margin notes, rules between sections, visible structure.
- Sharp corners are a valid choice again; mixed radii (sharp containers, round pills) read as intentional.
- Motion is scroll-driven and micro: CSS `animation-timeline: scroll()`, View Transitions; entrance-animation cascades on page load read as dated.
- Numerals as decoration: big tabular figures, counters, indices (`01`, `02`) as visual anchors.
- The reaction against flat-minimal continues: either more raw (brutalist accents) or more tactile (soft shadows with real light logic), but not the 2019 flat-card grid.

---

## Instrument

**Essence**: a cockpit. The data is the decoration; chrome exists to be ignored.
**Fits**: dashboards, monitors, admin panels, dev tools, ops consoles, internal tools, anything with live numbers.

- **Type**: display — Space Grotesk, Archivo, or Instrument Sans; data and chrome — IBM Plex Mono, JetBrains Mono, or Geist Mono. Tabular numerals (`font-variant-numeric: tabular-nums`) everywhere numbers align.
- **Color**: dark ground with a hue bias (`#0d1117`, `#101418`, `#0c1210`); ink `#e6edf3`-class; one accent from the hue rule for live/primary; a fixed semantic trio (ok/warn/bad) that is NOT the accent. Light variant allowed for daytime tools: `#f2f2ef` ground, near-black ink.
- **Space**: compact. 4px base unit, 12–13px chrome text, 1.4 line-height. Density is respect for the operator.
- **Shape**: 0–2px radius, 1px hairline borders one step above ground, no drop shadows — elevation by border and ground shift.
- **Motion**: 100–150ms ease-out on state change only. Values that update should tick, not tween grandly. No entrance animations.
- **Texture**: none, or a 2% scanline/grain on the ground at most.
- **Layout**: fixed header with system status, dense grid of panels sized by importance, mono labels in ALL-CAPS 10–11px with wide tracking.
- **Signature moves**: live sparkline in the header; status LEDs (small dots with glow only when active); row-scan hover on tables; a tick-tape/log strip; big single-number panels with tiny mono captions.
- **Failure mode**: sci-fi cosplay — glows, scanlines everywhere, fake radar sweeps. It's a tool, not a movie prop.

## Editorial

**Essence**: a well-set magazine. Reading rhythm carries the page.
**Fits**: landing pages, essays, blogs, docs with narrative, newsletters, announcement pages.

- **Type**: display — Fraunces (with its SOFT/WONK axes), Newsreader, or Libre Caslon; body — Source Serif 4, Newsreader, or a quiet sans like Archivo at 17–19px, line-height 1.6–1.7, measure 60–70ch. Type scale ratio 1.25–1.333.
- **Color**: warm paper ground (`#faf7f2`, `#f6f2e9`); near-black ink (`#1a1613`); one accent used sparingly — links, rules, drop caps. Dark variant: warm dark brown-black, not gray.
- **Space**: airy. Generous margins; whitespace is the luxury good.
- **Shape**: sharp or barely rounded (0–4px); hairline rules (1px) as the main separator, not cards.
- **Motion**: near none. Slow underline-grow on links, gentle scroll-reveals at most (400ms, once).
- **Texture**: optional fine grain at 2–3%; paper feel.
- **Layout**: strong vertical rhythm, asymmetric grid with a wide text column and an active margin (notes, dates, numbers in the margin), section rules, real typographic hierarchy instead of boxes.
- **Signature moves**: drop caps; margin notes; pull quotes set large in the display face; ruled section headers with an index number; a masthead-style header.
- **Failure mode**: costume drama — so many serifs and flourishes it reads as a wine label. Keep the chrome modern even when the type is classical.

## Archival

**Essence**: a lab notebook typeset properly. Figures first, claims cited, ink on paper.
**Fits**: research writeups, data stories, benchmarks, technical reports, project postmortems.

- **Type**: body — Source Serif 4 or Spectral; UI/captions — IBM Plex Sans; data/figures — IBM Plex Mono. Caption style: mono, 12px, numbered ("Fig. 3 — ...").
- **Color**: paper ground (`#f7f5f0`); ink `#22201c`; one restrained accent (oxblood, prussian blue, forest — muted, ink-like) for links and figure highlights. Charts in grayscale + the accent.
- **Space**: measured. 65ch measure, figures allowed to break wide of the text column.
- **Shape**: sharp; figures get a 1px border and a caption, never a card shadow.
- **Motion**: none, except focus/hover affordances. Print doesn't animate.
- **Texture**: none needed; the paper tone is the texture.
- **Layout**: single text column with wide figures, numbered sections and figures, a real table of contents, footnotes/sidenotes.
- **Signature moves**: numbered figure captions; sidenotes in the margin; a summary box up top set in a bordered rule ("Abstract"); dated revision line in mono.
- **Failure mode**: unread-ability — walls of text with no figure rhythm. The figures are the argument; make them earn the layout.

## Gallery

**Essence**: a white-cube gallery or a fashion house. Few elements, exact placement, expensive silence.
**Fits**: portfolios, studios, premium products, photography, fashion, agencies.

- **Type**: display — Cormorant Garamond, Italiana, or a tight grotesk like Hanken Grotesk with `letter-spacing: -0.03em` at size; body small and quiet (14–15px). Huge size contrast between display and body — 6x or more.
- **Color**: monochrome-first — ivory or pure-white ground, deep black ink; accent optional and rare (one hue, used maybe twice per page). Or inverted: black ground, bone ink.
- **Space**: extreme. The page is 60% empty. One idea per viewport.
- **Shape**: sharp. No borders where spacing can separate; no shadows.
- **Motion**: slow and smooth — 500–800ms ease-in-out reveals, subtle parallax on imagery, a page-load fade that feels like lights coming up. This is the one map where entrance motion belongs.
- **Texture**: none, or imagery IS the texture.
- **Layout**: oversized display lines that break mid-word if elegant; images placed asymmetrically with intent; navigation reduced to a word or two, often mono, top corners.
- **Signature moves**: image reveals on scroll (clip-path grow); a huge name/wordmark that scrolls behind content; hover that swaps an image; index-style project lists (year, title, one line) that expand.
- **Failure mode**: emptiness without exactness — sparse but sloppy placement reads as unfinished, not expensive. Every position must look decided.

## Brutalist

**Essence**: raw structure shown proudly. The grid has visible bones; the defaults are the aesthetic, oversized.
**Fits**: personal sites, zines, indie tools, manifestos, event pages, anything with attitude.

- **Type**: display — Archivo Black, system Helvetica/Arial pushed to 900 weight at huge sizes, or a mono at display size; body — system stack or Courier-family mono, deliberately.
- **Color**: stark — white/near-white ground, pure black ink, and one loud accent (safety orange, acid green, signal red) used at full saturation. No mid-grays.
- **Space**: uneven on purpose — cramped clusters against big voids. Base unit still consistent underneath (8px) so it reads as intent, not accident.
- **Shape**: 0px radius; thick borders (2–4px solid black); hard offset shadows (`4px 4px 0 #000`) as the only shadow style.
- **Motion**: abrupt — instant state changes, or a marquee. Hover states that jump (translate 2px, shadow collapses).
- **Texture**: default-web artifacts used knowingly: visible `<hr>`, underlined links, table borders.
- **Layout**: visible grid lines (bordered cells), oversized index numbers, headers that take half the viewport, content that touches edges.
- **Signature moves**: a marquee strip; cell-border grid where every section is a boxed cell; cursor that changes per section; giant numbered list as navigation.
- **Failure mode**: unusable noise — brutalism still needs hierarchy and a consistent underlying unit. If everything shouts, restore order with the grid, not with softness.

## Tactile

**Essence**: warm and touchable — real-light shadows, rounded but grounded, human without being childish.
**Fits**: consumer apps, journaling, habit trackers, learning tools, onboarding flows, calm productivity.

- **Type**: display — Bricolage Grotesque or a friendly serif like Fraunces at low WONK; body — DM Sans or Instrument Sans, 16–17px.
- **Color**: warm neutrals (`#f5efe6`, `#efe9df`) with ink `#2b2622`; 2–3 supporting pastels-with-spine (muted terracotta, sage, ochre — saturation 35–55%, not nursery pastels); accent from the hue rule warmed to fit.
- **Space**: comfortable — 8px base, breathing room, cards that don't crowd.
- **Shape**: rounded 10–16px on containers, full-round on pills/avatars; shadows with real light logic — one soft ambient plus one directional (`0 1px 2px rgba(0,0,0,.06), 0 8px 24px rgba(40,30,20,.08)`), never a uniform halo.
- **Motion**: springy but small — 200–300ms with a slight overshoot (`cubic-bezier(.34,1.56,.64,1)`) on presses and toggles; things feel pushed, not faded.
- **Texture**: subtle paper grain on the ground; soft duotone illustration if any.
- **Layout**: card-based but with size variety; one warm hero element; friendly empty states.
- **Signature moves**: squircle-ish containers; a hand-drawn underline or highlight stroke on one key word; progress shown as something physical (a filling jar, a stacking pile); pressed-in (inset) states on active controls.
- **Failure mode**: mush — everything round, everything beige, no contrast or edge anywhere. Keep ink dark, keep one sharp element for spine.

## Toybox

**Essence**: chunky, saturated, springy — a good toy: bright but built solid.
**Fits**: games for broad audiences, kids' tools, playful utilities, party/quiz apps, cheerful demos.

- **Type**: display — Baloo 2, Fredoka, or Bungee for shouts; body — Nunito or DM Sans, generous sizes.
- **Color**: saturated primaries-plus (saturation 70–90%) on a light warm ground or a deep navy; 3–4 hues max, each owning a role; thick ink outlines (`#1a1a2e`-class, not pure black).
- **Space**: big — fat padding, big targets (48px+), nothing precious.
- **Shape**: very round (16–24px), or blob shapes; thick 2–3px outlines; hard candy shadows (offset, same-hue-darker, no blur).
- **Motion**: the star — bouncy spring on everything interactive (250–400ms overshoot), wobble on hover, squash-and-stretch on press, confetti-class rewards used at most once per session.
- **Texture**: flat fills with outline, or subtle top-light gradient inside shapes (same-hue, not two-hue).
- **Layout**: centered and obvious; one big verb per screen ("PLAY"); score/state huge.
- **Signature moves**: squash-and-stretch buttons; a mascot-like shape that reacts; tilted stickers/badges; sound-effect-style text pops ("+10!").
- **Failure mode**: clown car — too many hues and all of them shouting. Three hues with roles beat seven without.

## Arcade

**Essence**: dark room, glowing signal — the language of score screens and synthwave cabinets, applied with restraint.
**Fits**: games with edge, leaderboards, music/audio tools, sim visualizations, launch-countdown pages.

- **Type**: display — Chakra Petch, Bungee, or (sparingly, titles only) Press Start 2P; body/chrome — a clean mono like JetBrains Mono; ALL-CAPS labels with wide tracking.
- **Color**: near-black ground (`#0a0a12`); 1–2 neon accents (from the hue rule, saturation 90%+, lightness 55–65%) that GLOW (`text-shadow`/`box-shadow` same-hue); everything non-signal stays dim (`#3a3a4a`-class). The glow budget: at most 3 glowing elements per viewport.
- **Space**: theatrical — big scores, dead space as darkness.
- **Shape**: sharp or chamfered corners (`clip-path` cut corners); 1px neon borders on active elements only.
- **Motion**: snappy 100–150ms, plus juice on events — screen-shake (2–3px, 100ms) on impact, count-up numerals, a CRT flicker used once at load, not looped.
- **Texture**: optional scanline overlay at 2–3%; vignette at the edges.
- **Layout**: HUD grammar — corners hold persistent state (score, lives, status), center holds the action; leaderboard tables in mono with rank numerals huge.
- **Signature moves**: count-up score tick; insert-coin style blinking prompt (one element only); chamfered panel corners; per-rank medal glyphs drawn in SVG, not emoji.
- **Failure mode**: vaporwave soup — every element glowing, chromatic aberration, three fonts of nostalgia. Darkness is the ground; glow is the signal. Keep the ratio.

## Quiet Pro

**Essence**: deliberately conservative and exactly executed — the tailored suit. Restraint IS the taste; one distinctive detail proves it was chosen, not defaulted.
**Fits**: enterprise deliverables, exec/investor-facing pages, client work with no brand yet, B2B products, anything where weird costs trust.

- **Type**: Public Sans, Source Sans 3, or IBM Plex Sans — competent, licensed, not Inter; headings medium-weight (500–600, never 800), tight but not fashionable (`-0.01em`).
- **Color**: cool paper ground (`#fafbfc`) or true white; ink `#1c2024`; ONE accent (hue rule, but desaturated to 45–60%) used strictly for interaction — links, primary buttons, focus. Grays with a consistent hue bias, never mixed warm/cool.
- **Space**: even and predictable — 8px unit, consistent rhythm, nothing cramped, nothing showy.
- **Shape**: 4–6px radius uniformly; borders `1px` in a gray one step off the ground; shadows minimal and only on true overlays (menus, dialogs).
- **Motion**: 150–200ms ease-out, standard patterns only. Nothing bounces.
- **Texture**: none.
- **Layout**: classic and scannable — clear nav, real information hierarchy, tables that respect data (aligned numerals, units in headers).
- **Signature moves** (pick exactly one): perfect tabular numerals everywhere; a distinctive focus-ring treatment; section numbers in the left margin; one accent-colored rule under the page title. The single detail is load-bearing — it is the difference between chosen and defaulted.
- **Failure mode**: template smell — shipping what a component library emits untouched. Even here, every token must be decided.

---

## Inventing a new map

When no map fits (a horror game, a children's encyclopedia, a tax form), write a new one directly into the Taste Contract using the same slots: essence, type (2 faces max), color (ground/ink/accent strategy), space (base unit + density), shape (radius/border/shadow policy), motion (durations + easing + budget), texture, layout grammar, 2–3 signature moves, and its failure mode on the `Never` line. A new map must be as parametrically specific as the nine above — if a slot says "vibes", it isn't done. Reference material beats memory: if the user names a genre or era, look at what actually defines it visually before parameterizing.
