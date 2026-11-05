# Particle motion blur in Redshift (custom shutter, Frame Position for dying particles)

- Source: Top Tip Tuesday — Particle Motion Blur Redshift — https://www.youtube.com/watch?v=VoFO8YcsQ5s (2025-03-18)
- Host / generation: C4D; any X-Particles / NeXus sim (cached via xpCache); Redshift
- Goal: correct, controllable motion blur on particles, including on the last frame before they die.

## Base
Five particles moving across frame, killed at frame 47. **Cache the sim first** — uncached particles don't blur properly.

## Steps
1. Render Settings ▸ **Redshift ▸ Advanced ▸ Motion Blur ▸ Enable**. [▶ 0:34](https://youtu.be/VoFO8YcsQ5s?t=34)
2. Shutter type **Custom** (most explicit control). **Frame Duration 5** = Redshift samples positions across 5 frames around the current one. [▶ 0:46](https://youtu.be/VoFO8YcsQ5s?t=46)
3. Start/End are 0–1 fractions of that window; set **Start 0, End 1** to use the full 5 frames (more blur). [▶ 2:04](https://youtu.be/VoFO8YcsQ5s?t=124)
4. **Frame Position** decides where the window sits: [▶ 1:43](https://youtu.be/VoFO8YcsQ5s?t=103)
   - **Center** (default) — half before, half after the current frame.
   - **Start** — current frame + following frames (blur shifts forward).
   - **End** — preceding frames + current frame (blur shifts back).
5. Render to the Picture Viewer (or final render) to check.

## Gotchas
- Motion blur **does not show in the Redshift IPR** — always test with a real render.
- With Start/Center, the last frame(s) before particles die have no future data → blur suddenly vanishes. For particles that die/disappear, use **Frame Position = End**; Center is fine otherwise.

## Newest equivalent
Renderer-side technique, unchanged by generation: the same settings apply to caches from **nxCache** (NeXus 2026.1 beta). See also 2026-09-29 (nxExplosiaFX motion blur in Redshift).
