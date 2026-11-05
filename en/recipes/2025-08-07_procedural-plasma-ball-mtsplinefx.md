# Procedural plasma ball (nxFollowGeo + nxTurbulence on particles, mtSplineFX arcs, mtEdgeSpline intersection forks)

- Source: INSYDIUM Official Training — Plasma Ball — https://www.youtube.com/watch?v=UXqS-dqsHiM (2025-08-07)
- Host / generation: C4D; xpEmitter + GPU nxFollowGeo/nxTurbulence (G2), CPU xpGenerator, MeshTools mtSplineFX + mtEdgeSpline
- Goal: lightning arcs from a core to points crawling over a glass sphere, with forks; swap the geometry and it adapts.

## Base
Three Instance objects referencing source geometry: **Core**, **Emission** sphere (hidden), **Intersection** sphere (larger). Swapping the instance links rebuilds the rig. Timeline 30 s.

## Steps
1. **xpEmitter** ▸ Object = Emission instance, **Polygon Area**; Emission **Shot**, amount **15**, speed 0, radius **40** (big — needed for intersections); display Circle, white.
2. **nxFollowGeo** with the Emission geometry, **Field of View 360**; **nxTurbulence** noise **Voronoise** → points wander over the surface.
3. **mtSplineFX**: Start object = Core, End object = emitter; Connection type **Origin → Points** (the emitter has no useful origin) → one arc per particle.
4. Arc shape: small noise **0**, main noise type **Noise**, larger scale for smooth arcs, animation speed **~20%**.
5. Fork targets: **xpGenerator** with an editable Sphere (**12 segments**) linked to the emitter → a sphere per particle (hide them).
6. **mtEdgeSpline** mode **Standard → Intersection**: geometry = Intersection instance, intersecting objects = the generator → rings where particle spheres cut the outer sphere; single-color display (bright yellow).
7. mtSplineFX ▸ Connections ▸ **Nearest Distance** on, mode **Split** (branch from a point along the main arc), Connect To = **custom object** = the edge spline; count **1**, tune distance/variation.
8. Proof: replace the three sources with Platonic objects (core / emission / intersection, scaled) — rig updates.

## Gotchas
Intersection points change every frame, so forks flicker — keep fork count low.

## Newest equivalent
Same rig in Fused 2025.4 (nxFollowGeo gained Guide/Force modes). In the 2026.1 beta an nxEmitter + nxGenerator could replace the xp pair; MeshTools part unchanged.
