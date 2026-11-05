# xpTrail — tool card

Mentioned in **25** recipes · 2023-02-14 → 2026-03-31 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Circle emitter firing outward; xpTrail on the emitter. [▶ 0:10](https://youtu.be/HvX6qaVei1o?t=10) — *[2026-03-31](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)*
- Renderable lines: **xpTrail** → **Algorithm: Constraints → Birth** (instead of tracing paths). [▶ 3:27](https://youtu.be/_7bYCGydqXo?t=207) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- Constraints are straight point-to-point → soften: xpTrail Spline **Intermediate Points Uniform 8** + child **xpTrailDeformer** (formula on Y, small **Amplitude ~1 cm**, tuned Wavelength); use the deformer's spline so the ends don't move (0 at start/end, full in the middle). [▶ 5:12](https://youtu.be/_7bYCGydqXo?t=312) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- Example effect: emission 25/frame + **xpTrail** (length 25, variation 12) → light trails following the moves. [▶ 6:23](https://youtu.be/Qd_kEHZ-4JY?t=383) — *[2025-08-12](../../recipes/2025-08-12_mocap-pla-emission.md)*
- Elements: emitter particles (tendrils) → mtRayLine casts rays to an inner sphere → contact-point particles → xpTrail. [▶ 0:54](https://youtu.be/K560tf-sU0I?t=54) — *[2025-06-03](../../recipes/2025-06-03_redshift-rayline-additive-curves.md)*
- Render: **xpTrail**, Algorithm **Constraints**, type = the birth springs. [▶ 6:59](https://youtu.be/PIgXQtSgnMY?t=419) — *[2025-05-20](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)*
- Optional: **xpTrail** on the emitter for woven line renders. — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- **xpTrail** on the emitter. — *[2025-03-13](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)*
- xpTrail ▸ Thickness and Color ▸ **Trail Color Mode**: Particle Color recolors the whole trail at once; **Per Vertex** paints the color change on over time (not possible with C4D's Tracer). [▶ 8:00](https://youtu.be/W8E4taTkKag?t=480) — *[2025-03-13](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)*
- **xpTrail** with the emitter → **Redshift Object tag ▸ Curves ▸ Capsules**, thickness 200 for a first look. [▶ 1:37](https://youtu.be/Lx6Sugl11TA?t=97) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Color: xpTrail ▸ Thickness & Color ▸ Trail Color **Per Vertex** (remembers color history); Redshift **Vertex Attribute ▸ preset Curves ▸ Curve Color** → transmission color of a glass material. [▶ 3:01](https://youtu.be/Lx6Sugl11TA?t=181) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Per-trail width: Redshift thickness back to 1; xpTrail Thickness mode **Use Particle Current** → each trail = its particle's size. Mesh subdivisions **Adaptive** (smooth). [▶ 4:07](https://youtu.be/Lx6Sugl11TA?t=247) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Animated width: **nxScale** Set by Falloff with the same random field; emitter radius 200, no variation; xpTrail Thickness **Use Radius Variable** → width painted along the trail. [▶ 5:39](https://youtu.be/Lx6Sugl11TA?t=339) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Three **xpTrail** objects (one per emitter, colored) → Redshift render. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*

## All recipes (25)
- 2026-03-31 · [Burst particles that ease to an organic stop (nxSpeed Range + curl turbulence)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2025-09-16 · [Stretching and snapping fibres (nxConstraints Birth + constraint trails + xpTrailDeformer)](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)
- 2025-08-12 · [Clean particle emission from a mocap character (xpJoin → Alembic → PLA bake)](../../recipes/2025-08-12_mocap-pla-emission.md)
- 2025-06-03 · [Render mtRayLine rays + trails as additive gradient curves inside displaced glass (Redshift)](../../recipes/2025-06-03_redshift-rayline-additive-curves.md)
- 2025-05-20 · [Organic springy particle network (nxConstraints birth springs + Forces layers, nxQuestion group switch & pin)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-05-06 · [Particle wireframe reveal (nxFollowGeo Edge mode + nxTurbulence + nxSpeed limit)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-03-13 · [Surface-tangent swirl trails (C4D Field Force + Volume Builder Cross Product vectors + nxColor ▸ xpTrail Per Vertex in Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2024-12-10 · [Trails whose thickness follows particle radius (xpTrail Thickness: Use Radius Variable → Redshift curves)](../../recipes/2024-12-10_trail-thickness-from-radius.md)
- 2024-11-12 · [Blooming trail flower (age-mapped nxTurbulence Curl Blend/Add + speed-mapped strength)](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)
- 2024-10-01 · [Rendering constraint springs + glassy skin underwater (xpTrail Algorithm Constraints, xpOpenVDBMesher, Redshift Environment fog)](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)
- 2024-08-20 · [Stylised microscopic cells in a dish (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-06-04 · [Per-vertex colored trails rendered additively in Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)](../../recipes/2024-06-04_particle-color-trails-redshift-additive.md)
- 2024-04-23 · [Particle-driven laser rays inside a sphere (mtRayline + nxConstraints Forces + xpTrail)](../../recipes/2024-04-23_mtrayline-particle-lasers.md)
- 2024-03-26 · [Stylised wind-tunnel flow lines around a car (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-03-12 · [Cutting laser with sparks (mtRayline contact-point emitter + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2024-02-27 · [Spreading physics chain reaction (nxConstraints Birth + Collisions, nxScale/nxGravity mapped to Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2023-12-19 · [Swaying glass tendrils with particles on the tips (xpTendril + xpTrail Tendrils + xpSplineMesher + xpTrailTip tag)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-06-23 · [Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-06-12 · [Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-05-30 · [Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-19 · [Feature notes: mtRayline sneak peek (MeshTools raycast spline generator)](../../recipes/2023-04-19_feature-notes-mtrayline-sneak-peek-part-a.md)
- 2023-04-04 · [Shrink trails away before particles die (xpTrailsMod via xpQuestion, or Change Trails action)](../../recipes/2023-04-04_shrink-trails-on-age-xptrailsmod.md)
- 2023-02-14 · [Wiggly animated trails turned into tapered tubes (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
