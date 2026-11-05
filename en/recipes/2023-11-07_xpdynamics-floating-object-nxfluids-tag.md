# Floating / sinking object in a NeXus fluid (xpDynamics tag + per-emitter nxFluids tag density)

- Source: Top Tip Tuesday — nxFluid Dynamic Objects — https://www.youtube.com/watch?v=3cWjs6bgjBI (2023-11-07)
- Host / generation: C4D; G2 nxFluids SPH + **CPU xpDynamics tag** (also works with X-Particles CPU fluids)
- Goal: a life ring that bobs on (or sinks into) a turbulent water body, moving as a rigid object.

## Base
Cube with **xpCollider** tag, Normal **Inside** (traps the water); **xpEmitter** Box emission, **Shot – Hexagonal**, radius **2 cm**; default gravity; **nxTurbulence**; **nxFluids SPH**, substeps **3 → 4**.

## Steps
1. On the torus: Tags ▸ X-Particles ▸ **xpDynamics** — births dynamic particles on every vertex.
2. Before playing, set the tag's **Radius = 2 cm** (same as the water) — SPH needs one radius for all particles or it becomes unstable.
3. **Update Points off** → no soft-body deformation, only position/rotation (rigid).
4. Water emitter ▸ **nxFluids tag** (per-emitter fluid settings), left default.
5. xpDynamics ▸ Properties ▸ **Add Emitter** → rename "emitter dynamic", Display ▸ Draw Emitter off, hide its particles; Ctrl-drag a copy of the nxFluids tag onto it.
6. Its nxFluids tag **Density 100** → ring floats; **3000** sinks; **200** floats back up.
7. Exclude **nxTurbulence** in the dynamic emitter's Modifiers list so only the water is stirred and pushes the ring.

## Gotchas
- Mismatched radii between water and dynamic particles break SPH.

## Newest equivalent
NeXus 2026.1 beta: **nxOcean** supports floating objects, and **nxMPM** (elastic/metal) or **nxPin** + nxConstraints give GPU solid bodies; GPU rigid bodies are announced but not shipped (Nov 2026).
