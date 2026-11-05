# Viewport particle display types and rendering them (emitter Display tab + Display Render generator)

- Source: Top Tip Tuesday — NeXus Particle Display — https://www.youtube.com/watch?v=0x9Hidcw6Fw (2023-05-09)
- Host / generation: C4D; xpEmitter with nxTurbulence (G2 GPU) — works identically with CPU xpTurbulence; X-Particles material, standard renderer
- Goal: see real particle size/rotation in the viewport and render the display shapes as geometry.

## Steps
1. Emission: radius **5 cm**, variation **4 cm** (→ 1–9 cm).
2. Display tab: default **Squares** — like Dots, Ticks and Axes it ignores particle size. Display Size Factor (e.g. 500%) only scales them uniformly; set back to 100%.
3. Pick any type from **Box** downward (e.g. **Box Filled**, **Arrow**) to show true size.
4. Color mode **Single → Gradient Random**; Load Preset **Full Colors** for multicolor.
5. Arrows read best with rotation: Extended Data ▸ General ▸ **Use Rotation**, type **Tangential** (points along travel).
6. Rendering: Create ▸ Extensions ▸ **X-Particles Material** on the emitter renders only circles.
7. INSYDIUM ▸ X-Particles ▸ Generators ▸ **Display Render** (xpDisplayRender); link the emitter; **move the material from the emitter to the Display Render object** → arrows render. Switch display to **Pyramids** etc. and they render too.

## Gotchas
X-Particles material on raw particles always renders spheres/circles; only the generated object carries the display shape.

## Newest equivalent
NeXus 2026 nxEmitter has up to 8 display channels; for render geometry use nxGenerator (instancing) or nxMesher.
