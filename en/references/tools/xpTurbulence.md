# xpTurbulence — tool card

Mentioned in **11** recipes · 2023-02-28 → 2024-02-06 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpTurbulence**: scale 150, strength 15. [▶ 3:25](https://youtu.be/3YmhMKdK0o4?t=205) — *[2024-02-06](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)*
- Motion ▸ **xpTurbulence** strength **18** (tendrils look fixed but are a constant stream of new particles). [▶ 1:32](https://youtu.be/M4z3kOU4YEw?t=92) — *[2023-12-19](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)*
- **xpTurbulence**: Scale **30**, Strength **8**. — *[2023-06-20](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)*
- **xpTurbulence** for wiggle. **xpTrail ▸ Algorithm: Tendrils** connections (not tracing the birth particle). **xpSplineMesher** on the trail: Subdivision 1, Size ▸ **Scale Spline** curve to taper to a point. [▶ 3:11](https://youtu.be/KBktASa5O2o?t=191) — *[2023-06-12](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)*
- Optional **xpTurbulence** (small scale, high strength) for jitter inside the clump. — *[2023-06-08](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)*
- **xpTurbulence** (Modifiers ▸ Motion): noise **FBM**, larger scale, Strength **~24** → wispy smoke. [▶ 4:02](https://youtu.be/iWET6SJpDhw?t=242) — *[2023-03-28](../../recipes/2023-03-28_vertex-speed-emission-xpvertexmap.md)*
- Optional baseline: **xpTurbulence** (Modifiers ▸ Motion), default settings — nice, but unrelated to the object's motion. Disable it while tuning. [▶ 1:30](https://youtu.be/pwEBS2tOgNw?t=90) — *[2023-03-14](../../recipes/2023-03-14_motion-inheritance-linear-rotational.md)*

## All recipes (11)
- 2024-02-06 · [Organic wobbling spiky ball (mtSubdivider + mtInset on an xpDynamics soft body)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2023-12-19 · [Swaying glass tendrils with particles on the tips (xpTendril + xpTrail Tendrils + xpSplineMesher + xpTrailTip tag)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-09-26 · [Big swirls plus fine detail (nxTurbulence Voronoi, Octaves, Persistence, Lacunarity)](../../recipes/2023-09-26_nxturbulence-octaves-persistence-lacunarity.md)
- 2023-06-20 · [Polygon-by-polygon disintegration driven by particles (xpFragmenter Faces Polys, xpWind with linear field, xpTurbulence mapped to distance travelled)](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)
- 2023-06-12 · [Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-09 · [Viewport particle display types and rendering them (emitter Display tab + Display Render generator)](../../recipes/2023-05-09_particle-display-modes-display-render.md)
- 2023-03-28 · [Emit only from the fastest-moving parts of a mesh (xpVertexMap Vertex Speed layer + texture emission)](../../recipes/2023-03-28_vertex-speed-emission-xpvertexmap.md)
- 2023-03-21 · [Three generations of spawning from one emitter (xpMultiSpawn levels + groups for display)](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)
- 2023-03-14 · [Particles that carry their emitter object's motion (Motion Inheritance linear + rotational, xpTurbulence)](../../recipes/2023-03-14_motion-inheritance-linear-rotational.md)
- 2023-02-28 · [Particle rotation basics (emitter Use Rotation: Set / Tangential / None + xpSpin random spin)](../../recipes/2023-02-28_particle-rotation-tangential-random-spin.md)
