---
name: ui-taste
description: Choose the stack and the visual direction for any web-facing build — apps, dashboards, landing pages, browser games, tools, prototypes, redesigns. Use whenever the user asks to build, redesign, restyle, or make a UI, page, site, or front-end for anything that renders in a browser, even when they say nothing about design or stack. This skill picks the stack by app type, infers a taste direction from the request, asks at most one small batch of questions up front, and locks a Taste Contract so the result looks deliberately designed instead of AI-default. Not for native mobile apps, TUI/CLI output, or pure backend work.
license: MIT
metadata:
  author: newsbubbles
  version: "0.1.0"
---

# UI Taste

Untamed model output converges on one look: Inter on white, indigo gradient, glass cards, 8px radii on everything. That look reads as "generated" because it is the average of everything. Taste is a decision, and an average is not a decision. This skill forces the decision early, once, and makes it checkable.

The core mechanism is the **Taste Contract**: a short structured artifact you write before any code. Prose intentions drift during a long build; a contract you can diff against the output does not.

## Flow

1. Read the request. Extract intent signals (table below). Pick ONE taste map and a stack.
2. High confidence → ask nothing. State your reading in one line — "Reading this as an internal instrument: dense, dark, data-first" — and proceed. The stated reading is the user's veto point; it costs them nothing if they agree.
3. Top two maps genuinely close, or the work is client/brand-facing → ask ONE batch of at most 3 questions (protocol below). This is the only time you ask. Decisions that surface mid-build get settled by the contract, not by new questions.
4. Write the Taste Contract.
5. Read your chosen map's full entry in `references/taste-maps.md` and the stack notes in `references/stacks.md`.
6. Build. First step of the build is compiling the contract into design tokens (`:root` custom properties). Every color, radius, duration, and font in the code must trace to a token.
7. Self-check against the contract and the ban list before presenting the result.

## Reading intent into taste

Extract four things from the request: **domain** (what the thing is), **audience** (who looks at it), **energy** (adjectives used or implied — calm, bold, serious, fun), and **constraints** (existing brand, deploy target, deadline). Then match:

| Signals in the request | Likely map |
|---|---|
| monitor, dashboard, admin, internal, ops, logs, pipeline | Instrument |
| landing, launch, marketing site, waitlist, product page | Editorial or Gallery |
| docs, blog, essay, writeup, explainer, newsletter | Editorial |
| research, findings, data story, paper, analysis, benchmark | Archival |
| game, arcade, score, play, sim with attitude | Arcade or Toybox |
| kids, cute, cozy, toy, fun little tool | Toybox |
| portfolio, showcase, studio, premium, luxury, fashion | Gallery |
| personal site, indie, zine, weird, punk, manifesto | Brutalist |
| consumer app, journal, habits, learning, onboarding flow | Tactile |
| enterprise, client deliverable, exec review, investor | Quiet Pro |

Modifiers, applied after the table:
- Existing brand assets (logo, palette, fonts in the repo) override the map's own color and type choices; keep the map's layout, density, and motion rules.
- Energy words shift the pick one notch: "bold/loud" moves toward Brutalist/Arcade; "calm/clean" toward Quiet Pro/Gallery; "warm/friendly" toward Tactile.
- Audience formality caps the weirdness: exec-facing work never gets Brutalist even if the domain suggests it.
- The user naming a specific aesthetic ("make it look like a terminal", "very editorial") is a direct order, not a signal. Obey it.

If nothing fits, invent a map: fill in the same parameter slots the existing maps use (see the end of `references/taste-maps.md`). The maps are a bias, not a cage.

## Question protocol

Default is zero questions. Ask only when signals genuinely conflict or the cost of a wrong guess is high (client-facing, existing brand, paid work). One batch, at the very beginning, never more than 3, drawn from this menu:

1. **Direction fork** — only when your top two maps are close. Describe both in plain adjectives, never in map names: "Two ways to take this: quiet and editorial, like a well-set magazine — or dense and technical, like a cockpit. Which fits?"
2. **Density** — compact vs airy. Only when the audience is unclear.
3. **Ground** — dark vs light. Only when the map doesn't already fix it.

Ask about stack only when a real constraint is unknowable from context (e.g., "does this need to run as a single HTML file with no server?"). Never ask the user to pick fonts, colors, or component styles — that is the job you were given.

## The Taste Contract

Write this before any code, exactly this shape, filled with specific values (never placeholders):

```
TASTE CONTRACT — <project name>
Map:       Instrument
Stack:     single-file HTML + vanilla JS, no build
Type:      Space Grotesk (display) / IBM Plex Mono (data, UI chrome)
Ground:    #0d1117 dark; ink #e6edf3
Accent:    hsl(158 64% 52%) — derived, see hue rule
Density:   compact — 4px base spacing unit
Shape:     2px radius, 1px hairline borders #2a3038, no shadows
Motion:    120ms ease-out on state change only; no entrance animations
Signature: live sparkline in the header + row-scan hover on tables
Never:     gradients, glass, emoji icons, entrance animations
```

Rules:
- One map, fully committed. Blending two maps averages back toward the default look — the exact failure this skill exists to prevent.
- The `Never` line carries the map's own failure mode plus anything from the ban list the build might otherwise drift into.
- The contract is the verdict. When a mid-build styling question comes up, the answer is whatever the contract implies — extend the contract in the same spirit rather than improvising.

## Uniqueness mechanisms

Same map must not produce the same page twice. Vary along these axes:

- **Accent hue, derived**: run the project name through a mixing hash, then remap around the AI-default indigo band:

  ```
  h = 5381; for each codepoint c: h = (h × 33 + c) mod 2³²   # djb2
  hue = h mod 295
  if hue ≥ 215: hue += 65      # skips 215–280 by remapping, not rotating
  ```

  Two linear formulas failed in the field before this one. `×7` put three real projects within 10° of each other (all teal — name-sums wrap in step). `×47` scattered better but its band rule ("if in 215–280, add 120") funneled every banded name into the same red zone — a rotation collapses a 65° band onto one color; the remap above spreads it across everything that remains. Linear maps of text cluster; mix properly. Brand assets or an explicit map rule override this. The point is not the formula — it is that the hue is a committed, specific, per-project choice rather than a reflex.
- **Display type is never** Inter, Roboto, Open Sans, Lato, or Poppins. System font stacks are allowed only where a map calls for them deliberately (Brutalist, Quiet Pro). Each map lists 2–3 display options — rotate between them across projects.
- **One signature element** from the map's menu, plus **one bespoke detail invented for this project** — a detail that could only belong to this app (a custom cursor for a drawing tool, tide-table numerals for a harbor app). The bespoke detail is where the page stops being a template.
- Don't reuse the previous project's font + hue pair.

## Ban list

These read as "generated" on sight. None may appear unless the chosen map explicitly calls for one:

- The indigo→violet gradient family (`#667eea → #764ba2` and relatives), or any 135° two-stop pastel gradient hero
- Glassmorphism: `backdrop-filter: blur` cards, translucent white borders
- Inter, Poppins, or Roboto as a display face
- Emoji as UI icons or list bullets
- Centered hero → two pill buttons → three feature cards, in that arrangement
- Uniform border-radius + soft drop shadow applied to every container
- `#6b7280`-style gray body text on white (low-contrast gray-on-white generally)
- Purple-tinted dark modes
- Default Tailwind palette or unthemed shadcn components
- Sparkle/rocket microcopy ("✨ Delightful", "Supercharge your…")
- Bento grids, unless the content is genuinely a grid of unlike-sized units — the layout is past its peak and reads as 2024

## Self-check

Before presenting, verify against the contract line by line:

1. Screenshot or render the result. Is every contract line *visible* — the fonts actually loaded (not a fallback), the accent present, the signature element in place?
2. Scan the ban list. Anything on it in the output?
3. Body text contrast ≥ 4.5:1; interactive targets ≥ 40px on touch-likely surfaces.
4. Does the page look like it was made by someone with an opinion? If a stranger saw it with the logo removed, could they tell it apart from a template?

If a chart/dataviz skill is available in the environment, it governs chart internals (scales, palettes for series, axes); the Taste Contract governs everything around the chart.

## References

- `references/taste-maps.md` — the nine maps in full parameter detail, current-era markers, and how to invent a new map. Read your chosen map's entry before building; skim the era markers if the request mentions "modern" or "current".
- `references/stacks.md` — stack selection by app type, the no-build bias, CSS/font/icon strategy. Read when the stack choice isn't obvious or the user has constraints.
