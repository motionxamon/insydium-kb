# Sand logo reveal with only the hero grains simulated (nxFluids SPH Granular + static scatter from a vertex map)

- Source: INSYDIUM LIVE! — March 2023 - NeXus, TerraformFX & Taiao — https://www.youtube.com/watch?v=OVUcKWkhUFY (2023-03-16)
- Host / generation: C4D; G2 NeXus — xpEmitter + **nxGravity** + **nxFluids SPH Granular** on GPU (demo on an RTX 3080 Ti; a 1080 Ti handles it, just limited by VRAM); xpCollider tags; second CPU system for static particles
- Goal: a logo rises through a sand-filled crater (terrain from part-a); grains slide or crack off it, the rest of the landscape is static instanced grains.

## Steps
1. **xpSystem** emitter: shape **Cylinder**, Pitch **90°**, about **60 × 7**, speed 0; sits just above the crater collider.
2. Emission Mode **Simulate** (not "Simulate Legacy") → particles already exist on frame 0. **Shot**, Shot Type **Hexagonal** (packs denser than Regular → less settling gaps, more cohesive), Radius **1.5** (smaller = more particles).
3. Low-poly crater: **xpCollider** tag, bounce down, **Friction 100%**. Logo extrude also has a collider tag — add some friction so grains cling before the kick-back throws them off.
4. NeXus ▸ **nxGravity** strength **200**. NeXus ▸ **nxFluids**: solver **SPH** (only SPH has granular; PBD doesn't), fluid type **Granular**.
5. Emitter Display: color **Gradient Parameter** mapped to the granular value, preset gradient, **Auto** range. Square display + raise **Display Size Factor** so squares fill the gaps like spheres.
6. Grains need an accurate velocity solve: **Substeps ~9**.
7. Looks: Granular **Friction 100** = wet sand / packed snow — the mass holds and the logo lifts a whole slab; **Stability ~5** lets it crack into sticky chunks. For the final dry sand, friction way down.
8. Static set: new xpSystem with **Only Modifiers in Same System** (ignores the NeXus modifiers), Mode Simulate, speed 0, **Shot**; shape **Object** → high-res terrain, **Polygon Area**, count **100,000**; drop the **snow vertex map** into the object **Selection** field → grains only in the grooves.
9. Render: instance the same grain geometry on both systems so the static scatter and the sim read as one surface.

## Gotchas
- Keep the sim as small as possible even on big-VRAM GPUs: simulate only where the logo disturbs the sand.

## Newest equivalent
2026.1 beta: **nxMPM** sand (nxMaterial *Sand wet* / *Sand Dry*, Auto Sleep for resting grains) in an nxEmitter; nxScatter (Beta 3) for points on meshes → nxGenerator. Stable Fused 2025.4: nxFluids SPH Granular as here.
