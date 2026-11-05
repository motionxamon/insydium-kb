# Wispy fluid crawling over a torus (nxFollowGeo 360° FOV + friction, nxTurbulence, nxFluids)

- Source: Top Tip Tuesday — NeXus FollowGeo GPU Particle Fluids — https://www.youtube.com/watch?v=dLTdpbRiG68 (2024-05-14)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxFollowGeo — new in 2024.2, nxTurbulence, nxColor, nxFluids)
- Goal: particles that never leave the surface of an object, splashing along it like liquid.

## Steps
1. Torus, pipe radius 25. xpEmitter Object = torus, **Polygon Area**; Rate for 15 F, **7000/frame**, speed 0, radius 0.3.
2. **nxFollowGeo** with the torus (each linked object gets its own settings): **Field of View 360°** so particles always stick.
3. Add force: **nxTurbulence** Voronoi, strength 20.
4. nxFollowGeo **Friction 4%** → smoky, wispy flow.
5. **Offset** 10 → 5 cm; **Offset Variation** gives depth (2 cm shown), 0 = finest wisps.
6. **nxColor ▸ Gradient by Parameter** mapped to **Speed**; raise Max for fewer white particles (live feedback).
7. **nxFluids**, default solver, **substeps 4** → instant splashy surface fluid.
8. More **surface tension** → beading; give a little offset variation so beads have room to form.

## Newest equivalent
Fused 2025.4 nxFollowGeo adds multi-spline and Guide/Force modes; for heavier liquids use nxFluids FLIP/APIC + nxMesher.
