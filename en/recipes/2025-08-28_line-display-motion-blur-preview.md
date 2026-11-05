# Preview render motion blur in the viewport (emitter Display: Lines, length Dependent on Speed)

- Source: Bite-Sized — Motion Blur Display Mode — https://www.youtube.com/watch?v=s6-7bXbXSqo (2025-08-28)
- Host / generation: C4D; X-Particles emitter display settings; Redshift motion blur
- Goal: see the streaky "warp tunnel" look while building, without rendering motion blur.

## Base
xpEmitter fired toward the Redshift camera; Emitter shape **Circle**, **Ring only** → a portal/light-speed tunnel. Seen as plain squares it reads as particles spraying outward.

## Steps
1. Reference render: Render Settings ▸ Redshift ▸ Advanced ▸ **Motion Blur on**, default **Movie** preset; view it in the Redshift RenderView IPR (it didn't show in the first quick render mode used in the video). Slow for look-dev.
2. Emitter ▸ **Display** ▸ editor display **Lines** (instead of Squares).
3. **Line Length** mode defaults to **Dependent on Speed** — fast particles draw long lines, slow ones short — matching how motion blur will smear them. Fast to draw.
4. Alternatives: **Dependent on Radius** (bigger particle = longer line) or **Fixed** length.

## Gotchas
Lines are viewport-only; the real blur still comes from the renderer's motion blur.
