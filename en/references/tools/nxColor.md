# nxColor — tool card

Mentioned in **47** recipes · 2023-04-20 → 2026-10-30 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxWarp Scroll** sized to enclose every particle (drag the handles); Radius 8, Spacing 1, then raise Radius and Roll; negative Direction. Optional: Y scale 15–40% for depth, then raise the warp height (default 1 cm) to contain it. **nxColor** gradient by Speed. [▶ 10:34](https://youtu.be/WJwIek6M8z8?t=634) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **Pipe routing (C4D):** Disc emitter r 15 cm, rate 15,000, life 300, + nxTurbulence + nxColor. **nxWarp Bend** rotated 90° to face the stream, Angle 90°. [▶ 11:17](https://youtu.be/WJwIek6M8z8?t=677) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **FLIP spiral (Blender):** tall nxFluids FLIP domain; sphere nxEmitter at the bottom, **Match Solver Resolution** → FLIP, direction +Z, speed 2.5; nxColor by Speed; nxTurbulence strength 16. [▶ 30:13](https://youtu.be/WJwIek6M8z8?t=1813) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **nxColor** (group 2): gradient by parameter (Magma), mapped to Y direction. [▶ 8:44](https://youtu.be/yOPa8oM_KXE?t=524) — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- **nxColor**: Magma gradient, parameter **Distance** travelled, max ~**5 m** (Speed 0–3.5 also works; reverse gradient for dark→light). [▶ 6:05](https://youtu.be/I2ERiN8Vk2Q?t=365) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- Per-particle color (e.g. nxColor gradient by Speed, 0–300 cm/s) does **not** show with **Multi-Instance** (treated as one object) → switch xpGenerator to **Render Instances** (slower). [▶ 5:49](https://youtu.be/OFx-ALGOlAU?t=349) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- **nxColor** in Speed mode with just two colors (red fast / blue slow), max ~2 — only works in Velocity mode. [▶ 19:09](https://youtu.be/m2jeYLxuRog?t=1149) — *[2026-07-09](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)*
- In GN, drop the radius link and set point radius manually (~0.001). Shader: move particle color into **Emission** (strength 10), mix with a **Transparent** shader for an additive look; a **Hue/Saturation/Value** node tames the saturated colors without touching nxColor. [▶ 27:32](https://youtu.be/m2jeYLxuRog?t=1652) — *[2026-07-09](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)*
- - **nxColor**: Gradient by Speed, gradient preset **Magma**. — *[2026-07-06](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)*
- **nxColor** Gradient by Parameter (speed), adjust min/max. [▶ 11:53](https://youtu.be/P9O1SJhPeik?t=713) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- Third group + **nxGravity** with Groups Affected = group 3. New question (use **Outdent** so it's not a child): **Distance Travelled > 5 m, variation 1 m** → Set Group 3 (disable nxColor while testing a color action — it overrides). [▶ 15:49](https://youtu.be/P9O1SJhPeik?t=949) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- **Cycles**: points render as clean spheres automatically. New material ("color sphere"); in GN add **Set Material**; in the shader add **Attribute** node "Color" → Base Color. Live: nxColor gradient edits update the render. [▶ 10:04](https://youtu.be/Hx0g1V9-HqM?t=604) — *[2026-06-15](../../recipes/2026-06-15_blender-particle-color-to-render.md)*
- **xpColor** (CPU) with a Maxon **Noise shader: Cell Voronoi**, global scale ~330, strong low/high clip → patchy black/white per particle. (CPU modifier used because it samples Maxon shaders in full 3D; nxColor has GPU noises.) [▶ 1:18](https://youtu.be/zyN7ERz7yuw?t=78) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- Animate particle color: **nxColor** layer **Distance from Object** → animated Null; gradient e.g. orange (≥300 cm away) → yellow → green → blue (near). [▶ 4:36](https://youtu.be/KimysoJRI9I?t=276) — *[2026-03-10](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)*

## All recipes (47)
- 2026-10-30 · [Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-20 · [Outside-in disintegration of a particle volume (nxQuestion Neighbors → Set Group, speed-mapped forces)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-09-15 · [Render NeXus particle data in Octane (color, radius → glass)](../../recipes/2026-09-15_octane-particle-data.md)
- 2026-08-25 · [Flower-burst trails with speed-mapped thickness and per-vertex color (nxTrail, nxScale + nxTurbulence speed mapping)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-08-04 · [Fake rigid-body rolling with nxSpin "Roll" layer](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-07-09 · [Wispy explosion-advected point cloud (nxExplosiaFX Particle Advect, Fast velocity advection, time-mapped forces, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-06 · [Layered curl turbulence tendrils (nxTurbulence Curl + FBM + Voronoi layers, per-layer age mapping, nxSpeed clamp, nxScale fade-in)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-30 · [Start/stop a looping nxQuestion animation with the Break action](../../recipes/2026-06-30_nxquestion-action-break.md)
- 2026-06-22 · [Triggering modifiers by switching particle groups (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-15 · [Particle color at render time in Cycles and Eevee (nxEmitter Point Cloud export + Geometry Nodes attributes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-06-09 · [Random birth orientation + repeatable 360° spins (nxSpin + age reset)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-06-02 · [Granular text blown apart by gusts mapped to animated Voronoi color](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2026-03-31 · [Burst particles that ease to an organic stop (nxSpeed Range + curl turbulence)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2026-03-17 · [Art-directed gloopy liquid stream (PBD + nxDirection + nxMesher)](../../recipes/2026-03-17_nxdirection-art-directed-liquid-stream.md)
- 2026-03-10 · [Colored smoke driven by animated particle color (nxExplosiaFX color channel → Redshift)](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)
- 2026-02-24 · [Kill particles by distance traveled (nxQuestion age reset + Set Life)](../../recipes/2026-02-24_custom-lifespan-by-distance.md)
- 2026-02-17 · [Recolor cached particles with nxColor (and speed-clamp by color)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-12-02 · [Abstract liquid with neighbour-count color bands (nxColor neighbour search → mesh → glass ramp)](../../recipes/2025-12-02_neighbor-search-color-glass-mesh.md)
- 2025-11-04 · [Particles that bloom in the crevices of geometry (nxQuestion neighbours + field)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-14 · [City lights spreading along building edges (nxInfectio + groups)](../../recipes/2025-10-14_city-lights-edge-infection.md)
- 2025-09-11 · [Feature notes: rewritten NeXus GPU core, per-layer GPU falloffs + Data Mapping, nxQuestion variations & neighbour search](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-08-26 · [Particles → C4D rigid bodies, colored by nxColor (xpGenerator + Simulation tags + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-07-24 · [Feature notes: nxSpin layers, nxColor Noise/Neighbor gradient, nxDirection Direction Force (Fused 2025 preview, part 2)](../../recipes/2025-07-24_feature-notes-nxspin-nxcolor-noise-nxdirection-force.md)
- 2025-07-22 · [Hide a hard emission ring with a noisy opacity mask (nxColor layers + birth-rate spline)](../../recipes/2025-07-22_nxcolor-noise-opacity-emission-fade.md)
- 2025-05-27 · [Detailed field-triggered explosion via upres (nxUpres position + velocity, nxExplode, nxQuestion group switch)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-13 · [Surface-tangent swirl trails (C4D Field Force + Volume Builder Cross Product vectors + nxColor ▸ xpTrail Per Vertex in Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2025-03-11 · [Exact data-mapping ranges from live particle data (xpConsole min/max → nxColor / Mapping)](../../recipes/2025-03-11_xpconsole-exact-mapping-ranges.md)
- 2025-02-20 · [Seamless infinite loop from a rendered particle sim (After Effects duplicate + opacity crossfade)](../../recipes/2025-02-20_seamless-particle-render-loop-after-effects.md)
- 2025-02-18 · [Peel-away volume disintegration (nxQuestion Neighbor Count → Group → nxWind/nxColor)](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)
- 2024-12-10 · [Trails whose thickness follows particle radius (xpTrail Thickness: Use Radius Variable → Redshift curves)](../../recipes/2024-12-10_trail-thickness-from-radius.md)
- 2024-11-04 · [Rendering speed-colored foam as additive glow in Redshift, ACEScg into After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-09-17 · [Non-intersecting particle branches inside a mesh (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-09-10 · [Multi-layer grayscale color → remapped additive flames (nxColor Age × Heading × Pitch, Redshift Color User Data)](../../recipes/2024-09-10_nxcolor-blended-layers-redshift-additive.md)
- 2024-08-20 · [Stylised microscopic cells in a dish (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-07-23 · [Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-16 · [Lava that freezes and re-melts (animated Random field color → mapped nxWind strength + nxSpeed max speed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-06-04 · [Per-vertex colored trails rendered additively in Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)](../../recipes/2024-06-04_particle-color-trails-redshift-additive.md)
- 2024-05-21 · [Turbulent text reveal with particles (nxCover Edges + weak layer strength + Spring holding, nxColor by Direction)](../../recipes/2024-05-21_nxcover-turbulent-spline-reveal.md)
- 2024-05-14 · [Wispy fluid crawling over a torus (nxFollowGeo 360° FOV + friction, nxTurbulence, nxFluids)](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)
- 2024-04-22 · [Feature notes: nxFollowGeo, layered nxColor and nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-03-12 · [Cutting laser with sparks (mtRayline contact-point emitter + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2023-11-16 · [Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-09-27 · [Self-organising "breathing" sphere clusters (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-08-29 · [Grow and recolor particles inside a field, revert outside (nxQuestion Field question, Set Color / Set Radius, Else)](../../recipes/2023-08-29_nxquestion-field-color-radius.md)
- 2023-04-20 · [Speed-gradient colours and an ocean-deformed fluid bed (Gradient Parameter by Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
