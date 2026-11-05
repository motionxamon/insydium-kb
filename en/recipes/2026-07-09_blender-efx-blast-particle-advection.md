# Wispy explosion-advected point cloud (nxExplosiaFX Particle Advect, Fast velocity advection, time-mapped forces, Cycles)

- Source: NeXus for Blender Official Training — Particle Advection — https://www.youtube.com/watch?v=m2jeYLxuRog (2026-07-09)
- Host / generation: Blender (NeXus for Blender, G3): nxEmitter ×2, GPU nxExplosiaFX, nxColor; Cycles render via exported point cloud
- Goal: a short particle blast drives an EFX velocity field that pushes millions of tiny emissive particles into a soft, milky outward burst, colored by speed.

## Base
- **Blast emitter**: Disc, radius 0.2, direction rotated 90° so particles shoot out flat in the disc plane; 5,000/s, speed 2 with variation, radius with variation; emit frames 0–6; lifespan 6 ±3 frames. This one only seeds the fluid (later hidden).
- **nxExplosiaFX** domain about 20 × 12 × 6 m (slightly bigger than frame). Default voxel size kept at first → memory stats show ~3.3 GB estimated peak VRAM; voxel size raised (coarser) until under 1 GB — advection doesn't need a fine grid.

## Steps
1. EFX **Sources**: pick the blast emitter. Turn **Fuel off** and **Pressure 0** (no combustion needed — the smoke is never rendered); emit Smoke 1 plus some Temperature. [▶ 3:22](https://youtu.be/m2jeYLxuRog?t=202)
2. Simulation ▸ **Buoyancy ▸ Gravity off** so the puff doesn't rise. [▶ 4:36](https://youtu.be/m2jeYLxuRog?t=276)
3. Source **Velocity** transfer: 100% gives motion, can go past 100% — **500%** for a real blast. [▶ 4:56](https://youtu.be/m2jeYLxuRog?t=296)
4. Duplicate the emitter → rename "advect": birth **per frame ~250,000**, speed 0, tiny radius with no variation, emit for slightly fewer frames than the blast (avoids static stragglers), lifespan 100 ±40. [▶ 6:23](https://youtu.be/m2jeYLxuRog?t=383)
5. EFX **Dynamics ▸ Particle Advect**: add the advect emitter. [▶ 7:07](https://youtu.be/m2jeYLxuRog?t=427)
6. Fast sources outrun the grid → Object ▸ **Solver**: **Min substeps 4, Max 6**. [▶ 8:05](https://youtu.be/m2jeYLxuRog?t=485)
7. Smoother result: Solver ▸ advection methods — leave Smoke/Temperature on **Accurate**, set **Velocity to Fast** (less noisy, keeps the shape; too smooth for rendering fire but ideal here). [▶ 9:51](https://youtu.be/m2jeYLxuRog?t=591)
8. Forces (Dynamics): **Vorticity** cranked high, then **Mapping ▸ Document Time** with a linear-inverse curve over 0.2→0.5 s (full strength early, gone by ~frame 15). **Simplex** large and strong, mapped over 0→2.5 s, end knot raised so a little swirl persists. **FBM** turbulence for detail: frequency near zero, length scale 0.2, strength 1–2, also time-mapped (~2 s) with a small persisting tail. [▶ 11:50](https://youtu.be/m2jeYLxuRog?t=710)
9. Particle Advect **mode**: **Velocity** (default) = fluid velocity added to particle's own, particles keep flying after leaving the grid, and have speed data; **Position** = follows the flow more exactly but overrides other motion, stops at the domain bounds, no speed. [▶ 17:08](https://youtu.be/m2jeYLxuRog?t=1028)
10. **nxColor** in Speed mode with just two colors (red fast / blue slow), max ~2 — only works in Velocity mode. [▶ 19:09](https://youtu.be/m2jeYLxuRog?t=1149)
11. Optional feather-in: Mapping ▸ **Particle Age** → *ExplosiaFX ▸ Particle Advect ▸ Advection Strength*, 1→5 frames ramps 0→full. [▶ 22:45](https://youtu.be/m2jeYLxuRog?t=1365)
12. Raise advect count to **2 M per frame** (~8 M total) — GPU display still plays fast. [▶ 20:34](https://youtu.be/m2jeYLxuRog?t=1234)
13. Advect emitter ▸ **Export ▸ Point Cloud**: auto-builds a Geometry Nodes setup (points from particles, radius via the **NeXus Particle Info** node) and a material. Hide the GPU particles. [▶ 24:49](https://youtu.be/m2jeYLxuRog?t=1489)
14. In GN, drop the radius link and set point radius manually (~0.001). Shader: move particle color into **Emission** (strength 10), mix with a **Transparent** shader for an additive look; a **Hue/Saturation/Value** node tames the saturated colors without touching nxColor. [▶ 27:32](https://youtu.be/m2jeYLxuRog?t=1652)
15. Cycles, GPU, max samples ~800 (draft), GPU denoise, fixed noise seed, **Lock Interface** on; 200 frames. [▶ 30:46](https://youtu.be/m2jeYLxuRog?t=1846)
16. Second pass for more energy: blast emitter 5,000 → **20,000/s**, FBM strength 2 with a non-zero tail, stronger late Simplex. [▶ 33:02](https://youtu.be/m2jeYLxuRog?t=1982)

## Gotchas
- Accurate velocity advection + noise = fuzzy, cotton-wool particles; switch Velocity to Fast before adding vorticity.
- Point cloud geometry slows viewport playback (millions of points) — hide it while tweaking.
- Test-render early; motion reads differently than in the viewport.

## Newest equivalent
2026.1 beta: **nxWarp** also works on smoke for extra shaping, and in C4D the same EFX setup can exchange with native Pyro (C4D 2025.3+). Same NeXus engine, so this recipe carries over 1:1 to C4D nxExplosiaFX (cm units ×100).
