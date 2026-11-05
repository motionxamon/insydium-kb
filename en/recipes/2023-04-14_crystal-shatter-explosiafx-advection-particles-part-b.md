# Wispy particles squirting from a breaking crystal (cached xpShatter, xpExplosiaFX Source tag, Advection, inner-face emission, xpJoin collider)

- Source: NAB 2023 - INSYDIUM Training — Crystal Shatter - Part 2 — https://www.youtube.com/watch?v=EAtbWdajZ4E (2023-04-14)
- Host / generation: C4D; CPU X-Particles (xpExplosiaFX, xpCache, xpJoin, xpCollider tag); viewport only
- Goal: an invisible explosion driven by the shard particles advects tens of thousands of tiny particles born on the inner faces. Continues 2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.

## Steps
1. Shard emitter: xpShatter General ▸ **Auto Particle Radius off** → emitter radius **2 cm** for all (doesn't change the animation). Extended Data ▸ Physical: **Temperature 1, Fuel 1**.
2. **xpCache** ("Cache Shatter Objects"): external files, Compress, Build (300 F, ~15 s). Tweak (xpSpeed 35 → **28**) and rebuild/overwrite if needed.
3. **xpExplosiaFX**: shrink the domain with handles; Solver ▸ **Voxel Size 4 → 1 cm** (fuel particles are 2 cm). Display: Mode Temperature, **Grid** look, LOD ~**120%** + transparency (Display ▸ Grid ▸ Back shows voxels).
4. Shard emitter ▸ Tags ▸ **xpExplosiaFX Source** tag (defaults). Simulation ▸ **Gravity off** → no buoyancy.
5. Source tag ▸ **Velocity 300** → temperature keeps rolling on with the particles' motion. Then display Mode off (only used for advection, not rendered).
6. Emission geometry: duplicate xpShatter, delete its cache tag and its emitter link (static), rename "Shatter Advection Particles", **Shatter Selections ▸ Inner Faces** → polygon selection tag.
7. New emitter "Emitter Advection": Modifiers tab picker → **exclude** all shard modifiers (minus). Shape **Object** = static shatter, Selection = inner faces, **Polygon Area**; **Object Chain: Connected Objects** (default Any Object emits from one shard only). Shot on frame 1, **50,000**, Speed 0, **Radius 0.1**; display Dots.
8. xpExplosiaFX ▸ **Advection** on (defaults) → particles swirl with the hidden sim.
9. Duplicate the emitter: ~**4,000** shown as squares for chunkier specks.
10. Collisions: put the cached xpShatter under **xpJoin**, add an **xpCollider tag** to the join, **Bounce 0**, a little Friction → particles no longer leak through un-fractured geometry.
11. Final counts: large **6,000**, small **150,000**. Second xpCache, Inclusion **Include** only the two advection emitters (no need to cache xpExplosiaFX). Demo: 3 min 21 s, ~3 GB, 301 frames. Then disable modifiers, emitters, static shatter and xpExplosiaFX for playback.

## Gotchas
- Keep advection particles tiny: at the default 3 cm radius each one overlaps several shards at birth → endless collision work and a broken sim.

## Newest equivalent
GPU **nxExplosiaFX** (Fused 2025.4; Sources listed in the object, not tags) for the driving smoke, **nxShatter** (2026.1 beta) for the fracture, **nxCollider** objects in NeXus 2026. Stable C4D route is still this CPU xpExplosiaFX advection setup.
