# nxMesher — tool card

Mentioned in **44** recipes · 2023-02-14 → 2026-10-30 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxMesher** emitter layer: Resolution 0.02, Radius 0.03–0.04 (0.025 too thin), Surface **Zhu-Bridson**. [▶ 37:52](https://youtu.be/WJwIek6M8z8?t=2272) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- One **nxMesher** per emitter. Water: emitter layer, Surface **Zhu-Bridson**, Polygon mode **Quads**, smaller Polygon Size, Radius 0.025. [▶ 16:52](https://youtu.be/jItRyLgdjPg?t=1012) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- Motion blur on the changing-topology meshes: nxMesher ▸ Export ▸ **Transfer Velocity**. [▶ 28:43](https://youtu.be/jItRyLgdjPg?t=1723) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- **nxMesher**: emitter layer, polygon size ~0.01, Surface **Zhu-Bridson**, radius ~0.015. [▶ 18:58](https://youtu.be/I9Fq5NPENdc?t=1138) — *[2026-09-22](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)*
- NeXus ▸ **Liquid Fill** → domain, nxGravity, and a folder with emitter, **nxFluids**, **nxMesher (off)**, group "foam" and **nxFoam (off)**. Plays as a tank out of the box. [▶ 0:59](https://youtu.be/vglrHSL-uc4?t=59) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Mesh: enable **nxMesher** (pre-linked; auto polygon size ~0.027); raise Scale to **300** to close holes; Smoothing layer **Mean Curvature**, iterations **5** (10 loses droplets). Export ▸ **Transfer Velocity** for motion blur. [▶ 18:41](https://youtu.be/vglrHSL-uc4?t=1121) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- **nxMesher** ▸ Emitter layer: radius **0.08**, coarser polygon size, surface type **Zhu-Bridson** (Spheres suits viscous folding). [▶ 12:35](https://youtu.be/eeigvIYA19Q?t=755) — *[2026-07-02](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)*
- Motion blur (optional — real macro shots rarely show it): nxMesher ▸ **Export Tags ▸ Transfer Velocity** (max 10 here) + Cycles Motion Blur. [▶ 33:35](https://youtu.be/eeigvIYA19Q?t=2015) — *[2026-07-02](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)*
- **nxMesher** ▸ emitter layer: **Polygon Size 0.015**, **Radius 0.015**; Surface Type **Zhu-Bridson** (self-smoothing, fast) instead of Spheres. Alternative: Radius 0.025 + Mean Curvature smoothing 100%, 5 iterations (loses a bit of detail). [▶ 12:13](https://youtu.be/na6NGPw4XWM?t=733) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **nxMesher** ▸ emitter layer, wireframe + **Quads**. Test settings on hard frames (thin snapping strands). **Polygon Size 0.008**, **Radius 0.013** (a bit fat so smoothing can thin it; 0.012 lost particles). [▶ 17:36](https://youtu.be/pz6LDGGeD5A?t=1056) — *[2026-06-12](../../recipes/2026-06-12_blender-apic-viscous-slime.md)*
- Mesh with **nxMesher Zhu-Bridson** (smooth without smoothing layers), transfer particle color to a vertex color tag; smoothing iterations blend color patches. [▶ 5:31](https://youtu.be/pbO2aDK4to8?t=331) — *[2026-03-17](../../recipes/2026-03-17_nxdirection-art-directed-liquid-stream.md)*
- Cache (≈1 min). **nxMesher**: Polygon Size 1.3, radius 1.6, Smoothing **Mean Curvature** 100%, 5 iterations (keeps ridges, removes flats). **Export Tags ▸ Transfer Color**. [▶ 8:33](https://youtu.be/VCGNxYZt21k?t=513) — *[2026-02-03](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)*
- **nxMesher**: radius **0.8**, Polygon Size **0.2** (removes fold artifacts); Smoothing **Gaussian** (Influence Range **0.8**, not the default 5 cm — too slow), strength full; second layer **Mean Curvature** 5–10 iterations (removes faceting/striping, check folds survive). **Transfer Color**. [▶ 9:18](https://youtu.be/uadAsfGPo1Y?t=558) — *[2025-12-16](../../recipes/2025-12-16_viscous-folding-ribbon.md)*
- **nxMesher** radius 1.3, Polygon Size 1, **Zhu-Bridson** (smooth without smoothing layers) → water material. [▶ 10:12](https://youtu.be/S4Bfw_hb9AI?t=612) — *[2025-12-09](../../recipes/2025-12-09_crown-splash-nxsplash.md)*

## All recipes (44)
- 2026-10-30 · [Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-27 · [Live low-poly sim proxy for a mocap character (fire / collisions)](../../recipes/2026-10-27_mocap-sim-proxy.md)
- 2026-10-07 · [Water, rubber gummies and sand in one solve, meshed and rendered (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-09-22 · [Liquid stream steered along a helix spline (nxFlowField Along/To Spline + Turbulence, PBD, nxQuestion escape kill)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-08-18 · [nxMesher export tags: emitter IDs, particle color, velocity motion blur (Redshift)](../../recipes/2026-08-18_nxmesher-export-tags.md)
- 2026-08-11 · [Liquid Fill preset with FLIP/APIC, mesh and separate foam emitter (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-07-02 · [Macro water splash with thin sheets (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)
- 2026-06-23 · [Bubbles trapped inside a viscous FLIP liquid (neighbour search)](../../recipes/2026-06-23_viscous-bubble-rig.md)
- 2026-06-18 · [Liquid stream looping round a curve, meshed with motion blur (nxFollowGeo spline + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-12 · [Viscous slime coiling over a head (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2026-05-26 · [Underwater splash bubbles (EFX advection + nxMesher + particle haze)](../../recipes/2026-05-26_underwater-splash-advection.md)
- 2026-03-17 · [Art-directed gloopy liquid stream (PBD + nxDirection + nxMesher)](../../recipes/2026-03-17_nxdirection-art-directed-liquid-stream.md)
- 2026-03-03 · [Soft-serve ice cream swirl (nxFluids APIC, viscosity, gravity mapped by age)](../../recipes/2026-03-03_flip-apic-soft-serve-ice-cream.md)
- 2026-02-03 · [Molten chocolate that sets on contact (APIC variable viscosity by color)](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)
- 2025-12-16 · [Viscous folding ribbon (FLIP from a thin spinning emitter)](../../recipes/2025-12-16_viscous-folding-ribbon.md)
- 2025-12-09 · [Art-directed crown splash (FLIP + nxSplash handles)](../../recipes/2025-12-09_crown-splash-nxsplash.md)
- 2025-12-02 · [Abstract liquid with neighbour-count color bands (nxColor neighbour search → mesh → glass ramp)](../../recipes/2025-12-02_neighbor-search-color-glass-mesh.md)
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
- 2024-05-14 · [Wispy fluid crawling over a torus (nxFollowGeo 360° FOV + friction, nxTurbulence, nxFluids)](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)
- 2024-04-02 · [Beading water droplets (nxFluids SPH surface tension + age-mapped nxGravity)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2024-01-02 · [Melting blob from the outside in (nxDrag hold + nxQuestion Neighbors → group switch + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-11-28 · [Smooth fluid mesh that keeps thin tendrils (xpOpenVDBMesher Point Radius, Voxel Size, Curvature + Offset filters)](../../recipes/2023-11-28_openvdb-mesher-detail-filters.md)
- 2023-11-20 · [Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-09-05 · [Gloopy fluid meshed with particle colors carried into the mesh (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)
- 2023-06-12 · [Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-05-09 · [Viewport particle display types and rendering them (emitter Display tab + Display Render generator)](../../recipes/2023-05-09_particle-display-modes-display-render.md)
- 2023-04-20 · [Speed-gradient colours and an ocean-deformed fluid bed (Gradient Parameter by Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-04-19 · [High-tension paint tendrils floating on a fluid bed (nxFluids SPH, nxFluids tag density, per-emitter nxConstraints Forces, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-19 · [Interactive melt / re-harden rig driven by particle color (nxSpeed Clamp Max Speed mapping + nxQuestion fields + nxBlend + mapped SPH viscosity)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-03-29 · [Combining cached sub-scenes into one master build (xpCache Hold/Offset, Alembic speed, PolyFX + layered fields)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
- 2023-02-14 · [Wiggly animated trails turned into tapered tubes (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
