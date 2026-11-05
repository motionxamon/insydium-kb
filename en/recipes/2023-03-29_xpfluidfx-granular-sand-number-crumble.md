# Sand number that crumbles into clumps (xpFluidFX Granular, Hexagonal fill, animated gravity falloff)

- Source: Maintenance Training — XP Countdown - Series 2 - xpFluidFX Granular — https://www.youtube.com/watch?v=SMO0CZcHa3k (2023-03-29)
- Host / generation: C4D; CPU X-Particles (xpFluidFX granular, xpGravity, xpKill, xpColor, xpCache) — pre-NeXus-granular / pre-MPM
- Goal: a MoText "3" filled with sand grains that cracks into clumps and falls backwards onto a "2" collider (later advected by smoke).

## Base
- MoText "3" (25 cm deep) moved to Z −12.5 so it lines up with the previous number; duplicate → "2" collider at Z +12.5 with **xpCollider** tag (low Bounce, high Friction), slightly scaled up so more of the 3 has a platform under it.
- xpSystem ▸ xpEmitter "emitter grains": Display Circles Filled + viewport **Ambient Occlusion** (to read clumps), HUD on.

## Steps
1. Emitter ▸ **Object** = the 3; emission type **Hexagonal** (fluid fill, no intersections), untick emit every frame, end frame 1, speed 0. [▶ 7:53](https://youtu.be/SMO0CZcHa3k?t=473)
2. Radius sets the count: 3 cm ≈ 800, 1.5 ≈ 6 400, 1.2 ≈ 13 000, 0.9 ≈ 30 000, **0.8 ≈ 43 000** (final). [▶ 30:50](https://youtu.be/SMO0CZcHa3k?t=1850)
3. Add **xpFluidFX**; switch to granular on the emitter: **Extended Data ▸ Fluid Data ▸ Fluid Type: Granular** → only Friction, Stability, Cohesion (all interdependent). [▶ 9:38](https://youtu.be/SMO0CZcHa3k?t=578)
4. xpFluidFX **Accuracy Fast → High** — granular needs many substeps/iterations or clumps never stiffen. [▶ 15:01](https://youtu.be/SMO0CZcHa3k?t=901)
5. **xpGravity** rotated 90° so it pulls to +Z (away from camera); **xpKill** box behind the scene removes fallen grains.
6. Animate the crumble: gravity **Falloff ▸ Box field**, keyframe its Z from below the letter to past it over ~40 F, F-curve **Linear**. [▶ 23:12](https://youtu.be/SMO0CZcHa3k?t=1392)
7. Collision friction: the emitter **Extended Data ▸ Physical Data ▸ Friction** is a per-particle multiplier of the collider's value (default 20%) → set 100%, then tune only on the collider tag (100 = grains stick, 70 → 90 at the final count). [▶ 32:12](https://youtu.be/SMO0CZcHa3k?t=1932)
8. Granular settings learned:
   - **Friction** (grain-grain): low = dry salt pouring, high = clumps; too high = rigid lumps that slide off whole.
   - **Stability**: how hard grains keep their shape — most change happens ~4–20; low = many small pieces, high = few big chunks.
   - **Cohesion**: springy hold across cracks; useful range ~10–30; too much = wobbly, jelly-like bounce.
   - Final direction: lower friction, more stability, cohesion first pushed high then settled at **30** (no visible bounce, more sand stays on the 2).
9. Color for render: **xpColor** ▸ Gradient by Parameter ▸ **3D Linear**, axis Z, Min −12.5 / Max 12.5, **Change on Birth Only**; gradient black → white so color can be remapped at render time and cracks show the lighter inner grains. [▶ 18:08](https://youtu.be/SMO0CZcHa3k?t=1088)
10. Test caches: **xpCache** internal, Data **Custom** = Velocity + Color only, compression off (~30–40 s per test). Rename the system "XP system grains". [▶ 33:52](https://youtu.be/SMO0CZcHa3k?t=2032)

## Gotchas
- Raising the particle count changes the physics — retune friction/stability/cohesion after every resolution jump.
- Some initial elastic bounce from cohesion can be skipped by starting the cached render a few frames in (frame 9 in the demo).

## Newest equivalent
**nxMPM** sand/snow materials (2026.1 beta, nxMaterial presets "Sand wet", per-emitter "Sand Dry") with nxFalloff-driven gravity; stable Fused route: **nxFluids SPH Granular** on the GPU. See recipes 2023-03-07 and 2026-07-28.
