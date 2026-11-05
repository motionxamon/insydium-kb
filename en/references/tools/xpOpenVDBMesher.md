# xpOpenVDBMesher — tool card

Mentioned in **21** recipes · 2023-03-29 → 2026-10-27 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpOpenVDBMesher** with the copy as child → voxel size ~3 for a watertight hull; raise **Iso value** so thin parts (hands) stay. Make editable (C). [▶ 8:24](https://youtu.be/C0P7UtWroDo?t=504) — *[2026-10-27](../../recipes/2026-10-27_mocap-sim-proxy.md)*
- **xpOpenVDBMesher** with all three emitters. Vertex color needs a dense mesh → **Voxel Size 1**; **Point Radius 2** (less blobby). [▶ 1:44](https://youtu.be/oHF1dIMGtUs?t=104) — *[2025-09-30](../../recipes/2025-09-30_paint-mix-meshing-vertex-color.md)*
- **xpOpenVDBMesher** with the 3 emitters; **Voxel 1.5**; **Point Radius 4** (default 10 = ×10 particle radius, too blobby). [▶ 1:22](https://youtu.be/e49Ob7tPXfc?t=82) — *[2025-09-02](../../recipes/2025-09-02_openvdb-mesher-object-ids.md)*
- **xpOpenVDBMesher granular**: Voxel size **0.5**, Point Radius **1.9** (default 10× is bloated), Filters: delete Median, add **Curvature**, iterations **2** (SSS hides the rest). [▶ 42:43](https://youtu.be/Siw3tkJepaU?t=2563) — *[2025-05-14](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)*
- **xpOpenVDBMesher liquid** (duplicate): Voxel **0.6**, Point Radius ~**2**, Curvature **10** iterations. If splashes vanish: smaller voxels or larger Point Radius. [▶ 47:53](https://youtu.be/Siw3tkJepaU?t=2873) — *[2025-05-14](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)*
- Snow: **xpOpenVDBMesher** linked to the cache: Voxel Size **4 → 0.5**, Point Radius **10 → 1.9**; Filters ▸ delete Median, add **Curvature** (Strength 100, Iterations 2) — keeps cracks, slight roughness helps the SSS. Cache the mesher with **Build Cache ▸ Continue** (~10 min), then disable the emitter. [▶ 32:52](https://youtu.be/fxJI8py9BzU?t=1972) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- **xpOpenVDBMesher** with the emitter: default **Point Radius 10 = 10 × particle radius** (30 cm spheres). [▶ 1:17](https://youtu.be/-4wYDCnis9M?t=77) — *[2024-11-05](../../recipes/2024-11-05_openvdb-velocity-stretch-trails.md)*
- **xpOpenVDBMesher** on the spawn emitter: Voxel Size **3**, Point Radius **2**, **Filters** on (default). [▶ 3:25](https://youtu.be/jHu6mpJfEUQ?t=205) — *[2024-10-01](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)*
- **xpOpenVDBMesher**: source emitter, **Voxel size 1**, **Point Radius 3**, one **Curvature** filter, Iterations 4. [▶ 4:58](https://youtu.be/DCggkQ6Mu_w?t=298) — *[2024-04-02](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)*
- Low-poly dummy: **xpOpenVDBMesher** with the xpJoin; on the object entry set mesh mode **Surface → Points**; **Voxel size 6**; filters: remove default Median, add **Curvature** (a few iterations) + **Offset** (shrink until the real car just pokes through). **C** to make editable, name "dummy car", hide. [▶ 1:22](https://youtu.be/BGuwXsKofbo?t=82) — *[2024-03-26](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)*
- **xpOpenVDBMesher**, General ▸ drag in the cached emitter. Default result is blobby: **Point Radius 10 = 10 × particle radius** shell. [▶ 2:05](https://youtu.be/vbolWCL3KgY?t=125) — *[2023-11-28](../../recipes/2023-11-28_openvdb-mesher-detail-filters.md)*
- Generators ▸ **xpOpenVDBMesher**, drag the xpEmitter into its list. Voxel size **3** for more polygons. [▶ 2:09](https://youtu.be/fvS3h7uk35s?t=129) — *[2023-09-05](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)*
- Route 3 (organic/viscous look): **xpOpenVDBMesher** with the Spline Mesher as source; lower Voxel Size and raise the Spline Mesher radius so there is enough volume to mesh. [▶ 16:28](https://youtu.be/WeuXOmENNXA?t=988) — *[2023-06-12](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)*
- Mesh: **xpOpenVDBMesher** source = emitter; raise Voxel Size, lower Point Radius, add **Gaussian** smoothing filters. [▶ 20:26](https://youtu.be/dnyn6Lrj8-A?t=1226) — *[2023-06-08](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)*

## All recipes (21)
- 2026-10-27 · [Live low-poly sim proxy for a mocap character (fire / collisions)](../../recipes/2026-10-27_mocap-sim-proxy.md)
- 2025-11-26 · [Feature notes: Fused 2025 liquids — GPU FLIP/APIC with viscosity, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-09-30 · [Mesh a color-blending paint sim and render vertex color (xpOpenVDBMesher → Redshift)](../../recipes/2025-09-30_paint-mix-meshing-vertex-color.md)
- 2025-09-02 · [One mesh, a different material per emitter (xpOpenVDBMesher Object IDs → Redshift)](../../recipes/2025-09-02_openvdb-mesher-object-ids.md)
- 2025-06-17 · [Reveal a hidden logo only through fluid refractions (Redshift primary-ray off + lava material blender)](../../recipes/2025-06-17_fluid-mesh-reveal-secondary-rays.md)
- 2025-05-14 · [Water collapsing a snow sculpture (nxFluids SPH granular + liquid tag, age-mapped nxGravity, xpOpenVDBMesher)](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)
- 2025-05-07 · [Exploding granular bust rendered as sand and as snow (nxFluids SPH Granular, nxExplode, stability mapped to Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-22 · [Micro-cell look in Redshift (Fresnel-opacity emissive spheres inside a dispersive glass mesh)](../../recipes/2025-04-22_redshift-cellular-particles-fresnel-dispersion.md)
- 2025-01-21 · [Motion blur on a meshed fluid in Redshift (xpOpenVDBMesher Transfer Velocity → Redshift Object tag motion vectors)](../../recipes/2025-01-21_volume-mesh-motion-blur-redshift.md)
- 2024-11-05 · [Speed-stretched meshes and vertex color (xpOpenVDBMesher Point Radius, Transfer Velocity, Trails source)](../../recipes/2024-11-05_openvdb-velocity-stretch-trails.md)
- 2024-10-29 · [Slow-motion ramp on a meshed fluid (retime particle cache, then cache the mesher from retimed particles)](../../recipes/2024-10-29_retime-cached-meshes.md)
- 2024-10-01 · [Rendering constraint springs + glassy skin underwater (xpTrail Algorithm Constraints, xpOpenVDBMesher, Redshift Environment fog)](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)
- 2024-04-02 · [Beading water droplets (nxFluids SPH surface tension + age-mapped nxGravity)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2024-03-26 · [Stylised wind-tunnel flow lines around a car (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2023-11-28 · [Smooth fluid mesh that keeps thin tendrils (xpOpenVDBMesher Point Radius, Voxel Size, Curvature + Offset filters)](../../recipes/2023-11-28_openvdb-mesher-detail-filters.md)
- 2023-09-05 · [Gloopy fluid meshed with particle colors carried into the mesh (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)
- 2023-06-12 · [Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-20 · [Speed-gradient colours and an ocean-deformed fluid bed (Gradient Parameter by Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-03-29 · [Combining cached sub-scenes into one master build (xpCache Hold/Offset, Alembic speed, PolyFX + layered fields)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
