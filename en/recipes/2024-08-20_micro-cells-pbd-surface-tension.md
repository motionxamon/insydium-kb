# Stylised microscopic cells in a dish (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)

- Source: Top Tip Tuesday — Micro Cells — https://www.youtube.com/watch?v=Z_JR2deKwqE (2024-08-20)
- Host / generation: C4D; NeXus G2 (nxGravity, nxTurbulence, nxFluids PBD, nxConstraints, nxColor) on an xpEmitter; xpTrail; xpCollider tag
- Goal: swirling, beading blobs of particles with hard edges and thin tendrils, like cells under a microscope.

## Base
- Dish: cylinder with top cap removed, **xpCollider** tag, Normals **Inside**, Friction **41 %**; black material.
- xpEmitter Circle, radius **50 cm**; emission **Shot Hexagonal**, shot time 1, full lifespan, speed 0, radius **1 cm**.

## Steps
1. **nxGravity** (default) settles the grid on the floor.
2. **nxTurbulence** Simplex, Strength **50**, Scale ~**70**, lower frequency (later raised strength a lot).
3. **nxFluids** solver **PBD** → particles interact. **External Pressure 100 %** → tighter blob borders and long thin tendrils when they separate.
4. PBD has no surface tension → **nxConstraints ▸ Surface Tension** layer, raise Iterations and Tension → beading globules.
5. **nxColor ▸ Gradient by Parameter: Speed**, preset gradient, max speed ~**9 cm** (15 was too high for these slow particles).
6. Skip the settling drop: on a good frame, emitter ▸ **Initial State ▸ Use Initial State + Set State**, then Emission mode **Controlled Only** so only the stored state loads.
7. Viewport: keep **Squares** display but raise **Display Size Factor** (cheaper than Circles).
8. Optional clustering: **nxConstraints ▸ Forces** layer, attraction 0, repulsion with smaller radius / higher strength → separate cell groups.
9. Bonus look: hide dish + particles, **xpTrail** (not full-scene trails), length ~20–50 frames → smooth swirling flow lines.

## Newest equivalent
2026.1 beta: nxEmitter Initial State (+ Keep Stored Age); **nxBioLogic** (particle life, Physarum) is an alternative for living/cellular patterns; PBD strengths changed in Beta 2, so re-tune old values.
