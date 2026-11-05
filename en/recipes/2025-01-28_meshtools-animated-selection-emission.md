# Emit from animated live selections (MeshTools Select + noise shader → xpEmitter + nxFollowGeo Edge mode)

- Source: Top Tip Tuesday — Custom Particle Emission — https://www.youtube.com/watch?v=AmfN_ZlpBcE (2025-01-28)
- Host / generation: C4D; MeshTools (Select object) + xpEmitter with NeXus G2 nxFollowGeo / turbulence; C4D spherical field
- Goal: particles born only from noisy, crawling polygon/edge patches on a model, revealed by a field.

## Base
xpEmitter on a wolf head + **nxFollowGeo** (Edge mode = wireframe crawl) + turbulence.

## Steps
1. INSYDIUM ▸ MeshTools ▸ **Select**; make the model its child. Default makes a polygon selection of everything (see it via Display ▸ Polygon Selection).
2. In the Select object use a **Noise shader**, raise Tolerance → only scattered polys; noise Animation Speed **0.4** → live animated selection.
3. xpEmitter ▸ Object: source = **the Select object** (not the model), Polygons, drop the polygon selection in; nxFollowGeo also uses the Select object.
4. Emission: emit on all frames with a shorter lifespan → continuous birth from the moving patches.
5. Edge version: nxFollowGeo **Edge mode, Edge 100%, offset 2 cm**; in Select switch polygon off, **Edge selection on**; emitter emit from **Edges** with the edge selection.
6. Select ▸ **Fields** tab: add a spherical field → selections (and births) only where the field is; animate it to reveal.

## Newest equivalent
Fused 2025.4 nxFollowGeo adds multi-spline + Guide/Force modes; in the 2026.1 beta nxFalloff modes and per-layer falloffs can gate effects without C4D fields.
