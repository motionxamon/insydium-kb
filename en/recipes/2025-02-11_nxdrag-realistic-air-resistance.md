# Realistic air resistance on a blast (nxDrag density, coefficient, radius, speed, mass)

- Source: Top Tip Tuesday — Realistic Drag Force — https://www.youtube.com/watch?v=Q5xA2nFPiIM (2025-02-11)
- Host / generation: C4D; NeXus G2 nxDrag + nxTurbulence on xpEmitters
- Goal: a violent particle blast that decelerates into near slow motion, and an understanding of what drives drag.

## Base
Fast-blasting xpEmitter + **nxTurbulence** (detailed but chaotic) + **nxDrag** to tame it. Test rig: "circles" emitter with equal speed, mixed radii (small red, large green).

## Steps
1. Reset nxDrag to defaults: small particles already outrun big ones — drag is radius-dependent.
2. **Density** (the medium): presets Air, CO2, Helium, Mercury… or Custom value. Helium = almost no effect; denser (e.g. **Ethanol**) = massive.
3. **Drag Coefficient** (shape aerodynamics): default **Sphere**; other presets or Custom — higher = less aerodynamic, more drag.
4. **Radius** (emitter): stands in for surface area; bigger particles get more drag.
5. **Speed**: faster particles are hit harder.
6. **Mass** (Extended Data ▸ Physical Data): e.g. Mass 3, variation 3 — lighter particles are slowed more.
7. Balance the five to dial the "blast then hang" look; equalise radius (e.g. 1) to isolate other factors.

## Gotchas
If drag seems to do nothing, check medium density first — a light medium hides the coefficient changes.

## Newest equivalent
nxDrag carries over unchanged to NeXus 2026 (G3).
