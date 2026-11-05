# Tree roots two ways (Taiao Plant branch layers + gravity; Taiao Tree volume points from an emitter)

- Source: Bite-Sized — Taiao Tree Roots — https://www.youtube.com/watch?v=B8RCRJy6cek (2025-10-02)
- Host / generation: C4D; **Taiao Plant** and **Taiao Tree** + a plain **xpEmitter** as point source; C4D Landscape + spherical field
- Goal: add surface roots to a tree — quick procedural roots, or space-colonising roots spreading over the ground.

## Method A — inside Taiao Plant (simplest)
1. Plant (modified default tree) ▸ Plant Layers ▸ select **Trunk** ▸ **add Branch** layer; turn off **Branch on End**.
2. Distribution: move the spline knots so branches sit at the bottom of the trunk; add a knot for more volume.
3. Main: add length + variation; angle slightly down.
4. Modifiers ▸ **Gravity**: raise strength, add variation, tune weight → roots bend into the ground. Increase **profile width**.
5. Add a second Branch layer under it (length variation, angle, gravity) for finer sub-roots.
6. If Plant **Forces** are enabled the roots sway too — set the root layers' force **strength 0**.

## Method B — Taiao Tree over terrain
1. Add a C4D **Landscape** as ground.
2. **xpEmitter** ▸ Object: Landscape, **Polygon Area**; Emission **Shot** + **Simulate**, speed 0. Object ▸ Falloff: **Spherical field**, scaled to the root area.
3. Add **Taiao Tree** ▸ **Volume Points**: drop in the emitter → branches grow across the particle points on the ground. Put the growth object inside the tree base.
4. Scale the field/emitter to change spread; raise **trunk thickness** to blend with the plant; give it the bark material.
5. Tune **resolution** (detail) and **kill distance** (more/fewer roots); add the Landscape as an **Avoid object** so roots ride over the surface (approximate).

## Newest equivalent
For grown networks on GPU, **nxDendrite** (branches/network) or **nxBioLogic** (2026.1 beta) can create root-like growth from particles; Taiao stays the modelling route.
