# Exploding granular bust rendered as sand and as snow (nxFluids SPH Granular, nxExplode, stability mapped to Speed, xpOpenVDBMesher)

- Source: INSYDIUM Training — Granular Collapse — https://www.youtube.com/watch?v=fxJI8py9BzU (2025-05-07)
- Host / generation: C4D; G2 NeXus (nxFluids SPH Granular, nxGravity, nxExplode, nxPush, nxKill) inside an xpEmitter + CPU **xpOpenVDBMesher**, xpCollider, xpCache; Redshift
- Goal: a packed-sand bust cracks from an internal blast and crumbles in big and small chunks; same sim rendered as particle sand and as meshed SSS snow.

## Base
- C4D content-browser bust scaled up (Y ≈ 160 cm — volume drives particle count) on a cube floor.
- Floor **xpCollider**: Bounce 0, Friction 100% (later 20%).
- **xpEmitter** Shape Object (bust), Emission **Shot** on frame 1, Shot type **Hexagonal**, Speed 0, Radius **1.3** for drafts (~85k particles).
- Display ▸ Gradient Parameter = **Granular** data, max ~30, flame preset gradient.
- Ctrl+D ▸ X-Particles ▸ **Subframe steps 4** (fluid substeps only subdivide the fluid; this also subdivides gravity/explode).

## Steps — simulation
1. **nxGravity** (defaults) + **nxFluids** set to **SPH ▸ Granular**.
2. Wet clumpy sand: Granular **Friction 90**, solver **Substeps 3 → 12** (more friction iterations, structure holds its own weight).
3. **Stability** = speed check: particles separating faster than it lose friction. Lower to ~**4** so it cracks.
4. **nxExplode**: Centre = **This Modifier** (not particle mass centre), Timing **Scene Time = F5**. Fields ▸ **Spherical field**, Inner Offset 100%, radius ~15, inside the bust; move the field out of the modifier (Utilities folder) so you can move/aim the modifier (back and to the side) independently. Draft count needed a much higher speed (+300 variation).
5. Fake the rigid "standing" phase: nxGravity ▸ Mapping ▸ **Age** map F5–F7, strength 0 → full, so nothing settles before the blast.
6. Production: Radius **0.4** → just under 3 M particles (presenter suggests ~6 M for sand at this framing). xpCache (compress on build): ~27 min / 100 F. Same settings now blast too hard and fragment too fine.

## Steps — break the hexagonal grid (one-frame birth pass)
7. Disable modifiers and floor collisions (Collider ▸ uncheck Enable Collisions, keep the cube active). Emission ▸ **Jitter XY/Z 0.3** (just under radius).
8. **nxPush**: Distance = **Particle Radius**, Strength 100, **Iterations 1000**. Below it **nxKill**, Volume = Objects ▸ floor cube, Inside → kills grains pushed into the floor.
9. Run one frame, then Emitter ▸ Object ▸ **Initial State ▸ Set State** (~114 MB); Emission ▸ **Controlled only**. Disable push/kill, re-enable explode/fluids/gravity **and collisions**.

## Steps — controlled crumble
10. Collider friction **20%** (grains slide), nxExplode Speed **500**.
11. nxFluids ▸ Data Mapping ▸ **Speed** map, category SPH, parameter **Stability**, range **20–60 cm/s**, curve full → low: slow = big chunks, fast = fine debris. Re-cache. Display ▸ Dots + Force Display to inspect the cache.

## Steps — render
12. Sand: **Redshift Object tag** on emitter ▸ Particles ▸ **sphere instances**; standard material (orange tint, higher roughness) overrides granular colour.
13. Snow: **xpOpenVDBMesher** linked to the cache: Voxel Size **4 → 0.5**, Point Radius **10 → 1.9**; Filters ▸ delete Median, add **Curvature** (Strength 100, Iterations 2) — keeps cracks, slight roughness helps the SSS. Cache the mesher with **Build Cache ▸ Continue** (~10 min), then disable the emitter.
14. Snow material (one Standard node): rough reflections; **Transmission** with blue scatter colour, Depth 100, weight ~0.2; **SSS** light blue, weight 1, Scale 100, grey Radius to temper depth. Default material on the floor for reflections.
15. Render settings: 100 F, Bucket 512 (VRAM-dependent). Snow: **denoising on + Random Noise Pattern off**. Sand: denoising off (it would smear grains), lower threshold, Random Noise Pattern on. Pixel motion blur in post.

## Gotchas
- Jittered grains are born intersecting → explosive SPH; always push apart and kill floor intersections before Set State.
- Remember to re-enable floor collisions after the birth pass.
- Raising particle count changes the look (stronger blast, smaller fragments) — retune explode speed and stability.

## Newest equivalent
2026.1 beta: **nxMPM** Sand / Snow materials (via **nxMaterial** presets, Auto Sleep, material change by speed/damage) replace SPH granular; **nxBind** can hold the shape and release by age/speed; **nxMesher** (Fused 2025.4, GPU) replaces xpOpenVDBMesher. Stable Fused 2025.4: same SPH granular route with nxMesher.
