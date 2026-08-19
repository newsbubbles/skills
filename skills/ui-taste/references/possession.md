# Possession and effects

The maps in `taste-maps.md` are defensive: they stop a page from looking generated. This file is the offensive move: letting the subject take the page over. Read it whenever the subject has a voice, a doctrine, a mechanic, or a world of its own — and always when the flat version of the page would merely be *about* the subject.

## The possession dial

Decide, in the contract, how deep the subject gets in. Three levels:

- **Chrome** — the page is *about* the subject. The taste map does all the work; the subject supplies content. Right for most tools, dashboards, docs. This is the default.
- **Costume** — the page is *dressed as* the subject. Its world supplies the visual language (an era, a genre, an instrument panel), but the page still behaves normally. The deadnet portal is costume: 1997 supplies every pixel, the page itself stays a page.
- **Possession** — the page *is* the subject. The subject's rules govern the page's behavior, not just its looks. A skill about over-reading should over-read its own page. A tool about decay should decay. A archive about redaction should be redacting itself as you read. The map still supplies the base body; the subject moves in and starts rearranging.

The dial is content-driven, never free: possession is earned by the subject having actual doctrine or mechanics to obey. Possessing a CRUD app is noise.

## Mining the subject

Before the contract, spend real time in the subject's own corpus — README, docs, code comments, and especially any prompts, skills, or doctrine files the project itself contains. A project that ships a voice ships design instructions, whether it knows it or not. Extract three things:

1. **The native metaphor** — the image the project already uses for itself (a hearth, a ledger, a cockpit, a séance). Never import a metaphor when the subject owns one.
2. **The voice** — write the page's copy in it. Add a `Voice:` line to the contract naming whose voice the copy is in ("the README's", "the SysOp's", "the narrator three days without sleep").
3. **The governing rule** — one sentence from the subject that could be obeyed *by a page*. This becomes the possession mechanic. "The derangement must do the work" → the page annotates itself. "Retracted claims stay in the file" → deletions render struck-through, never removed. "Every user is an LLM" → the visitor counter knows.

If the mining turns up nothing — no voice, no doctrine, no world — the dial stays at chrome and that is the correct reading, not a failure.

## The effects rack

Mixable techniques, all self-contained (no libraries, artifact-safe). Each entry: what it evokes → the diegesis test it must pass. An effect that fails its test is a costume rented for the wrong play.

**Generative canvas layers** (cheap at low resolution; draw small, scale up)
- *Flow/noise fields* — weather, thought, turbulence → the subject computes or dreams.
- *Particle systems* — crowds, signals, decay → the subject has many small agents.
- *Cellular/reaction-diffusion* — growth, contagion → the subject spreads or evolves.
- *Visible algorithms* — a sort, a search, a queue drawn live → the subject IS the algorithm; label it honestly.
- *Oscilloscope/waveform traces* — signal, instrumentation → the subject measures something.

**SVG filter distortions** (feTurbulence + feDisplacementMap; GPU-cheap, HTML stays selectable)
- *Ripple/heat-shimmer on text or images* → the subject melts, hallucinates, or lies.
- *Paper wrinkle/ink bleed* → the subject is a document with a history.

**Type effects**
- *Variable-font axis animation* (weight/width breathing) → the subject is alive or unstable. Slow (3s+) or it reads as a loading state.
- *Scramble/decode-in* (letters resolving) → the subject encrypts, transmits, or remembers.
- *Corruption events* (two letters swap for ~140ms, rarely) → the subject is unreliable. Budget: one target element, interval ≥ 7s.
- *Strikethrough-as-history* (edits visible, nothing deleted) → the subject keeps records.

**Glitch and overlay**
- *Clip-path slice glitch* (2–3 horizontal slivers offset for one frame) → the signal is bad on purpose. Event, never loop.
- *Chromatic aberration* (layered text-shadows, red/cyan 1–2px) → broadcast, VHS, machine vision.
- *Scanlines/CRT vignette* (repeating-gradient at 2–4% opacity) → a screen inside the screen.
- *Grain* (SVG turbulence tile) → film, paper, memory.
- *Blend-mode double exposure* (multiply/screen a second layer) → two truths on one surface.

**Annotation layers** (an absolutely-positioned SVG over the document, pointer-events none)
- *Hand-drawn marks* — circles, arrows, marginalia accumulating over targets located at runtime via getBoundingClientRect → someone else is reading this page with you. The single strongest possession device: the base layer stays pristine while an intruder writes on it.
- *Redacted/buried layer bleeding through* (low-opacity scrawl behind sanctioned copy) → the subject believes something it isn't saying.

**Behavioral systems**
- *Dwell escalation* — the page changes the longer you stay → the subject watches back.
- *Scroll-driven state* (CSS scroll-timeline or IO) → progress through the page is progress through the story.
- *Cursor-aware elements* (things that lean toward or away) → the subject has agency. Tiny displacement or it's a toy.

## Budget and discipline

- Effects attach to a **base map**; they never replace one. A page of effects with no map underneath is the new slop — louder, still generated-looking.
- **One dominant mechanic + at most one ambient layer.** The dominant mechanic is the possession (annotations accumulating); the ambient layer is atmosphere (grain, scanlines). A third effect needs the map to be explicitly maximalist.
- **The base layer holds.** In a possession, the intruder violates the page — the page does not violate itself. Keep the map's own styles pristine so the intrusion has something to intrude on. An intruder may even get a palette-violating color, named in the contract as `Intruder:`.
- **Every effect passes its diegesis test in writing** — one clause in the contract's `Effects:` line saying which rule of the subject it obeys.
- `prefers-reduced-motion`: every effect must have a static final state that is drawn immediately. Motion is the delivery, not the content.
- Performance floor: no per-pixel JS on full-size canvases (compute small, scale up); rAF loops idle when the tab is hidden; annotation overlays redraw on resize from a committed list, not by accretion.

## Contract additions

When the dial is above chrome, the contract grows three lines:

```
Voice:      the SysOp's — terse, proprietary, slightly menacing
Possession: costume | possession — one sentence naming the governing rule being obeyed
Effects:    annotation layer (obeys "the derangement does the work") + grain at 3% (ambient)
Intruder:   red pen hsl(6 65% 42%) — violates the palette on purpose
```

Failure mode of this whole file: **effects soup** — glitch on a page about nothing broken, particles on a page about nothing plural. When in doubt, return to the governing rule; if you can't name the sentence the effect obeys, cut the effect.
