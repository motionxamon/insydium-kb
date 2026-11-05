# nxWarp — tool card

Mentioned in **29** recipes · 2023-02-14 → 2026-10-30 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxWarp Scroll** sized to enclose every particle (drag the handles); Radius 8, Spacing 1, then raise Radius and Roll; negative Direction. Optional: Y scale 15–40% for depth, then raise the warp height (default 1 cm) to contain it. **nxColor** gradient by Speed. [▶ 10:34](https://youtu.be/WJwIek6M8z8?t=634) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **Pipe routing (C4D):** Disc emitter r 15 cm, rate 15,000, life 300, + nxTurbulence + nxColor. **nxWarp Bend** rotated 90° to face the stream, Angle 90°. [▶ 11:17](https://youtu.be/WJwIek6M8z8?t=677) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **nxWarp Twist** enclosing the column, Guide mode, Angle 500 → 2000 with Guide Strength lowered; raise the attract strength to hold the stream. [▶ 35:40](https://youtu.be/WJwIek6M8z8?t=2140) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*

## All recipes (29)
- 2026-10-30 · [Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-09-22 · [Liquid stream steered along a helix spline (nxFlowField Along/To Spline + Turbulence, PBD, nxQuestion escape kill)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-07-09 · [Wispy explosion-advected point cloud (nxExplosiaFX Particle Advect, Fast velocity advection, time-mapped forces, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-06 · [Layered curl turbulence tendrils (nxTurbulence Curl + FBM + Voronoi layers, per-layer age mapping, nxSpeed clamp, nxScale fade-in)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-25 · [Fuel-burning fire and smoke rendered live in Cycles (nxExplosiaFX sources, forces, Adaptive Bounds, VDB Output Live)](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)
- 2026-06-18 · [Liquid stream looping round a curve, meshed with motion blur (nxFollowGeo spline + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-05 · [Additive particle vortex rendered as a point cloud (nxEmitter Disc Edge Only, nxTurbulence, nxRotate + Sphere falloff, Point Cloud export)](../../recipes/2026-06-05_blender-additive-particle-vortex-point-cloud.md)
- 2025-10-28 · [Liquid countdown: fluid flowing along animated number splines (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2025-08-14 · [Feature notes: nxFollowGeo spline modes, per-channel nxUpres, layered nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-07-24 · [Feature notes: nxSpin layers, nxColor Noise/Neighbor gradient, nxDirection Direction Force (Fused 2025 preview, part 2)](../../recipes/2025-07-24_feature-notes-nxspin-nxcolor-noise-nxdirection-force.md)
- 2025-05-27 · [Detailed field-triggered explosion via upres (nxUpres position + velocity, nxExplode, nxQuestion group switch)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-05-08 · [Wrapping a particle ribbon around a spline with C4D deformers (Spline Wrap + Twist on an xpEmitter)](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)
- 2025-05-06 · [Particle wireframe reveal (nxFollowGeo Edge mode + nxTurbulence + nxSpeed limit)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-03-13 · [Surface-tangent swirl trails (C4D Field Force + Volume Builder Cross Product vectors + nxColor ▸ xpTrail Per Vertex in Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2025-02-13 · [Deforming meshes and static particle clouds with a MoGraph Random effector (Deformer mode + xpEmitter Modifiers list)](../../recipes/2025-02-13_mograph-effector-deformation-particles.md)
- 2024-05-07 · [Realistic gusting leaves (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2024-04-22 · [Feature notes: nxFollowGeo, layered nxColor and nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-04-16 · [Bend a straight fire sim around a helix (xpExplosiaFX + C4D Spline Wrap)](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)
- 2024-03-26 · [Stylised wind-tunnel flow lines around a car (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2023-12-26 · [Natural falling snow (nxSpeed limit mapped to radius + second nxTurbulence Curl Blend mapped to radius)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-11-16 · [Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-10-03 · [Particles flowing organically along a spline (xpFlowField Along Spline + Curl + To Spline layers)](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)
- 2023-09-27 · [Living shatter countdown (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)
- 2023-08-15 · [Millions of smoke-advected particles rendered additively (xpExplosiaFX Advect Particles, X-Particles material Add blend)](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)
- 2023-06-12 · [Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Swapping in a high-detail smoke sim, final retime and Cycles 4D render setup (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-02-14 · [Wiggly animated trails turned into tapered tubes (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
