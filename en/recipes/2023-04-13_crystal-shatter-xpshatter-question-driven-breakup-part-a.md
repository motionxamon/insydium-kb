# Crystal that crumbles shard by shard (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)

- Source: NAB 2023 - INSYDIUM Training — Crystal Shatter - Part 1 — https://www.youtube.com/watch?v=75GHeuPO3rU (2023-04-13)
- Host / generation: C4D; CPU X-Particles (xpShatter, xpExplode, xpSpeed, xpRotator, xpSpin, xpFreeze, xpQuestion) + MeshTools Inset; viewport only
- Goal: a small faceted crystal (~14 cm) that breaks apart bit by bit, shards jetting out, orbiting and tumbling while one region stays intact. Part 2 adds advected particles: see 2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.

## Base: crystal model
1. C4D **Platonic**, Type **Octa**, made small; make editable (C), scale it up along Y so it's elongated.
2. INSYDIUM ▸ MeshTools ▸ **Inset** (Platonic as child): **Amount 100%** turns each face into a point, raise **Offset** to push the points out. Put that inside a second **Inset** with a small Offset only.
3. Top Inset ▸ Advanced ▸ **Optimize** (removes duplicate points and bad polys) before shattering.

## Steps
1. xpSystem; delete the default emitter. Generators ▸ **xpShatter**; Inset as child. Voronoi layer + Point Generator (40 points by default; Display ▸ Draw Shatter Points shows them).
2. Point Generator: Points **100 → 300**, Distribution **Normal (Gaussian)** with **Standard Deviation** for a mix of big and small shards; turning **Object Volume** off (bounding box instead) and raising the deviation gives a less even break.
3. Rough inner faces: Voronoi layer ▸ **Details** on. Defaults assume ~200 cm objects, so shrink everything: **Edge Length 2 → 0.5**, Noise **Electric**, **Global Scale ~1%**, **Strength ~0.1** (keep scale and strength roughly a factor of 10 apart).
4. xpShatter General ▸ **Add Emitter** → a control-only emitter with one particle per shard; **Auto Particle Radius** sizes each to its shard. Turn off Draw Emitter and Show Particles.
5. **xpExplode** (Motion): blasts away from the particle mass centre; strength down to **~5 cm** for this scale.
6. Trigger: Ctrl-copy the original Platonic, scale it (Object mode) to just enclose the crystal, key Scale at F0 and a much smaller scale near the end (timeline 300 F; drag the last key earlier for a faster break). Hide it.
7. Emitter ▸ Questions ▸ **Particle Position ▸ Inside Volume**, mode **outside**, Object = the animated Platonic, action **activate modifiers** → xpExplode. Scale the Platonic larger at F0 if some shards fire immediately.
8. Randomise: **Sub-question ▸ Other ▸ Random Probability**; 100% = same as before, a low value (~1%) releases shards a few at a time.
9. Project Settings (Ctrl+D) ▸ X-Particles ▸ **Subframe Steps 2** (small scale + fine speed control).
10. **xpSpeed**: Operation **Absolute**, **25 cm/s** (later 35); add it to the same question's modifier list. Mapping ▸ Speed vs **Distance Travelled**, range **0–30 cm**, curve: quick rise, dip, then accelerate again.
11. **xpRotator** after xpSpeed, rotated **90°** to the right axis; Mode **Force** (Velocity overrides other modifiers), **Attraction 0**, **Rotate Speed ~50°**; map Rotate Speed to Distance Travelled with an ease-in so orbiting starts after the jut-out. Order: explode → speed → rotator.
12. **xpSpin**: needs Emitter ▸ Extended Data ▸ General ▸ **Rotation** on, **Tangential**, **Persist Orientation off**. Spin: affect Rotation, Absolute, Time-oriented off, **1000°** per axis; map to Distance Travelled (**0–100 cm**) and lower the curve so it never reaches full value.
13. Keep part intact: **xpFreeze** (Control) + a small **Spherical field** over the region that should stay.
14. Lighter mesh for sim/cache and a broken-glass look: Details **Edge Length 1 cm**, **Strength 0.3**, **Smooth Normals off** (hard edges).

## Gotchas
- Everything is scaled down (14 cm object): Details noise, xpExplode strength and speeds all need much smaller values than the defaults.
- Fine Details edge length gives nice noise but very heavy shards; coarsen before caching.

## Newest equivalent
**nxShatter** (2026.1 beta: Voronoi/Glass, sub-fracture, triggers, driven by emitter or MPM damage) replaces xpShatter; release logic via **nxQuestion** (CPU questions don't reliably drive GPU emitters) and an **nxFalloff** instead of the scaling Platonic; nxSpeed / nxRotate / nxSpin with NeXus Mapping. Stable C4D (Fused 2025.4): xpShatter as shown.
