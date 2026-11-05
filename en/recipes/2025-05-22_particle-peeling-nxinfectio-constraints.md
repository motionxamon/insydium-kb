# Paint-style peeling off a surface (nxInfectio groups + nxWind/nxTurbulence + nxConstraints Distance)

- Source: Bite-Sized — Particle Peeling — https://www.youtube.com/watch?v=xGxf_IIIekY (2025-05-22)
- Host / generation: C4D; xpEmitter + NeXus GPU modifiers (nxInfectio, nxWind, nxTurbulence, nxConstraints)
- Goal: a coat of particles on a tube peels away in organic, stringy sheets from a seed point.

## Steps
1. **xpEmitter ▸ Object**: the tube, **Polygon Area**; Emission **Shot** in **Simulate** mode (particles exist on frame 0), speed 0, **100,000** particles. xpCollider tag on the tube.
2. **nxInfectio** ▸ **Add Seed Object**; move the seed to the tube's edge — infection spreads from there (default: plain circular growth).
3. Organic spread: emitter **Display ▸ Color Mode Shader ▸ Noise**, larger scale and more contrast with plenty of black — infection travels through white and avoids black (good for mold too).
4. nxInfectio mode **Fixed Value → Use Groups**; Ctrl-add an incubating and an infected group (group 2 = the ones to peel).
5. **nxWind** pointing up, **Groups Affected = group 2** → only infected particles blow away.
6. Optional **nxTurbulence** on group 2, Voronoi, strength ~10, larger scale (alone this gives a disintegration look).
7. Hold them together: **nxConstraints ▸ Distance** connection (not Birth — the particles already exist), group 2 only, **Connection Limit 50**, **Radius 250**; stiffness/breaking default → stringy peeling sheets.

## Newest equivalent
For a real mesh skin that tears as it peels, NeXus 2026.1 **nxDeformer** (mesh follows particles, tearing) or **nxPin** to anchor uninfected particles; select by falloff/groups in each layer's own falloff list.
