# Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)

- Source: INSYDIUM Training — Particle Vorticity - Part 1 — https://www.youtube.com/watch?v=_W2ivetBEPo (2024-11-01)
- Host / generation: C4D; G2 — xpEmitter driven by NeXus GPU modifiers (nxGravity, nxFluids, nxVorticity, nxRotate, nxKill, nxFoam, nxColor) + CPU xpCollider tags, xpJoin, xpCache; TerraformFX tfRock
- Goal: fluid in a rock-filled cylinder that splashes, whirlpools and splashes again; only the generated foam particles are cached and rendered (render in Part 2).

## Base
- xpSystem stripped to the NeXus, Emitters and Utilities folders (no CPU modifiers/questions needed).
- **xpEmitter** in Box mode inside the cylinder: **Shot** on frame 1, **Hexagonal** grid, Speed 0.
- Water container = C4D cylinder made editable with its top polygons deleted; **tfRock** stones inside (high-res for render).
- Slow-mo planning: foam is born every frame, so a cache can't be retimed smoothly → simulate at **60 fps** (Ctrl+D Project ▸ FPS **and** Render Settings ▸ Output frame rate), play back at 30 fps in comp.

## Steps — fluid
1. Container: X-ray on; **xpCollider** tag with normals **inside**, Bounce 0.
2. **nxGravity** (default) + **nxFluids** (default mode), Substeps **4**.
3. **nxKill**: Volume **Object** = container, kill **outside**, **Only Born** → removes particles spawned outside the cylinder.
4. Cheap rock colliders: Ctrl-drag a copy of the tfRock null into Utilities, hide the high-res set, drop the copy's tfRock **Subdivisions to 1** (same shape, far fewer polys). Put the copy in an **xpJoin** and give the join one xpCollider tag (Bounce 0).
5. **Friction 0** on both collider tags so the liquid keeps its energy.
6. **nxVorticity** below the fluid solver: Strength **600%** already sustains swirls; raise **Radius** a little (bigger eddies). Very high strength (~1500%) boils the water — pair it with **Force Limit 20** to keep it strong but controlled.
7. **nxRotate**: Pitch **90°** so it spins around the cylinder axis; to centre it, parent it to the container, zero its coordinates, then move it back into the modifier stack. Keyframe **Rotate Speed 0 → 360 → 0** after the first splash settles (back to 0 at F442) — vorticity keeps the whirl alive afterwards.
8. Second splash: Ctrl-drag a copy of the emitter sideways, Shot on frame **589**.
9. Production resolution: both emitters Radius **3 → 2 cm**; vorticity is now far too strong → Strength ~**200%**. Judge with Hardware renders played in real time.
10. Timeline **800** frames; **xpCache** to external files, compressed (~5 min).

## Steps — foam
11. Turn off nxFluids, nxVorticity and nxRotate (fluid is cached); **keep nxGravity** — nxFoam needs gravity for buoyancy/advection. Hide the fluid emitters.
12. **nxFoam** + a new emitter for it ("emit foam"): **Crest rate 10**, **Air rate 10**; foam only from fluid particles at least **35 frames** old (with variation); Life **200** (with variation); Advection **Drag ~100** so foam sticks to the flow and traces the swirls. Foam emitter Display ▸ **Dots**.
13. **nxColor**: Gradient by Parameter, greyscale (black → white), mapped to **Speed**, max ~**380–400** → fast = white, slow = black (used for the render ramp).
14. **xpCache ▸ Build Cache ▸ Continue** (NOT Overwrite) → only the uncached foam emitter is simulated; existing fluid cache is untouched (~35 min, 3M+ foam particles at peak).
15. Viewport: foam emitter Display **LOD 15%**.

## Gotchas
- Vorticity strength must drop when particle radius drops (more particles → stronger effect).
- Foam particles are born after Age 35, so the first ~35 frames contain no foam.

## Newest equivalent
Fused 2025.4: **nxFluids FLIP/APIC** + the rewritten layer-based **nxFoam** (foam/bubbles/spray) and layered GPU modifiers. NeXus 2026.1: same chain with **nxEmitter/nxCollider/nxCache** objects (**nxConvert** migrates this G2 scene); FLIP & MPM respect collider group filters (Beta 3).
