# nxExplosiaFX — tool card

Mentioned in **37** recipes · 2023-03-29 → 2026-11-03 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Use it: nxExplosiaFX → Sources → the plane; for Smoke, Temperature and Fuel set **Weight by: Tag** and link the vertex map. Masked emission needs higher values: raise Fuel (e.g. 3) and **Burn Rate** so all fuel burns. [▶ 12:29](https://youtu.be/qv6TE9WtFhg?t=749) — *[2026-11-03](../../recipes/2026-11-03_nexus-falloffs-animated-vertex-maps.md)*
- **Fire (Blender):** nxExplosiaFX, sphere in Sources tab, coarser voxel size, Temperature Dissipation 3. Warp bounds = domain or slightly larger. Bend 90/180/360°; Twist ~800°. [▶ 20:52](https://youtu.be/WJwIek6M8z8?t=1252) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- nxExplosiaFX: replace the high-poly in **Sources** and **Colliders** with the proxy; turn off hierarchy options → much faster sim and caching. [▶ 12:04](https://youtu.be/C0P7UtWroDo?t=724) — *[2026-10-27](../../recipes/2026-10-27_mocap-sim-proxy.md)*
- Disable nxExplosiaFX and the cache; add a Maxon **Volume Loader** and link the **first VDB frame** — it detects density, temperature, vel_x / vel_y / vel_z. [▶ 2:56](https://youtu.be/qZyBMJaN6ak?t=176) — *[2026-09-29](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)*
- nxExplosiaFX → **Dynamics ▸ Particle Advection** → drop the emitter in. [▶ 1:27](https://youtu.be/1ERTCdQAoF0?t=87) — *[2026-09-01](../../recipes/2026-09-01_efx-advection-data-questions.md)*
- - **nxExplosiaFX** domain about 20 × 12 × 6 m (slightly bigger than frame). Default voxel size kept at first → memory stats show ~3.3 GB estimated peak VRAM; voxel size raised (coarser) until under 1 GB — advection doesn't need a fine grid. — *[2026-07-09](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)*
- EFX: torus inside a taller **nxExplosiaFX**, added as source; voxel size **0.02**; Simplex noise length scale **5**, strength **50**. [▶ 12:08](https://youtu.be/s5JA_AADBnY?t=728) — *[2026-06-29](../../recipes/2026-06-29_blender-data-mapping-basics.md)*
- **nxExplosiaFX ▸ Object ▸ Sources**: add Suzanne. Default channels emit temperature 1000, fuel 0.2, pressure, smoke 0 — smoke still appears because burning fuel generates it. [▶ 2:02](https://youtu.be/RH6ukNvt-No?t=122) — *[2026-06-25](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)*
- Wall (cube) is an nxExplosiaFX **collider** so smoke rolls up it. [▶ 0:24](https://youtu.be/kGTKDlTTyxE?t=24) — *[2026-04-07](../../recipes/2026-04-07_soot-damage-vertex-map.md)*
- nxExplosiaFX: bigger domain → **Voxel 6**; Buoyancy **Gravity 0** (fluid stays in the orbit). [▶ 4:14](https://youtu.be/iPYPQGaz7zQ?t=254) — *[2026-03-24](../../recipes/2026-03-24_efx-emission-mapped-to-particle-data.md)*
- nxExplosiaFX **Solver tab → enable Color channel** (off by default to save memory). [▶ 1:26](https://youtu.be/KimysoJRI9I?t=86) — *[2026-03-10](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)*
- nxExplosiaFX → Sources: drag the **animated logo spline** (splines, polygons and particles are all accepted). **Voxel Size 2.7**. [▶ 0:33](https://youtu.be/irQZ4OI7Bhk?t=33) — *[2026-02-10](../../recipes/2026-02-10_upscale-fire-from-spinning-spline.md)*

## All recipes (37)
- 2026-11-03 · [Animated vertex maps from NeXus GPU falloffs → drive nxExplosiaFX emission](../../recipes/2026-11-03_nexus-falloffs-animated-vertex-maps.md)
- 2026-10-30 · [Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-27 · [Live low-poly sim proxy for a mocap character (fire / collisions)](../../recipes/2026-10-27_mocap-sim-proxy.md)
- 2026-09-29 · [nxExplosiaFX → OpenVDB → Redshift with vector motion blur](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)
- 2026-09-01 · [Particle flames from nxExplosiaFX advection data (temperature-driven kill & color)](../../recipes/2026-09-01_efx-advection-data-questions.md)
- 2026-07-21 · [Build a Redshift material for nxExplosiaFX that matches the viewport](../../recipes/2026-07-21_redshift-explosiafx-material.md)
- 2026-07-09 · [Wispy explosion-advected point cloud (nxExplosiaFX Particle Advect, Fast velocity advection, time-mapped forces, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-07 · [Additive glowing particles in Octane (1 M vs 10 M particles)](../../recipes/2026-07-07_octane-additive-particle-glow.md)
- 2026-06-29 · [Data Mapping basics: gravity by age/radius/brightness, cycling EFX fuel/smoke pulses (Mapping tab, Particle Console, Document Time + Cycle)](../../recipes/2026-06-29_blender-data-mapping-basics.md)
- 2026-06-25 · [Fuel-burning fire and smoke rendered live in Cycles (nxExplosiaFX sources, forces, Adaptive Bounds, VDB Output Live)](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)
- 2026-06-16 · [Render nxExplosiaFX in Cycles 4D (Principled Volume)](../../recipes/2026-06-16_cycles4d-explosiafx-material.md)
- 2026-05-26 · [Underwater splash bubbles (EFX advection + nxMesher + particle haze)](../../recipes/2026-05-26_underwater-splash-advection.md)
- 2026-05-12 · [Render nxExplosiaFX in Octane via OpenVDB](../../recipes/2026-05-12_octane-explosiafx-vdb.md)
- 2026-04-21 · [Pressure-blast text advection with 10 M particles (nxExplosiaFX)](../../recipes/2026-04-21_pressure-blast-advection.md)
- 2026-04-07 · [Soot deposits on walls from nxExplosiaFX smoke (xpVertexMap + Redshift)](../../recipes/2026-04-07_soot-damage-vertex-map.md)
- 2026-03-24 · [Fire emitted only by fast (or big) particles — EFX source mapping](../../recipes/2026-03-24_efx-emission-mapped-to-particle-data.md)
- 2026-03-10 · [Colored smoke driven by animated particle color (nxExplosiaFX color channel → Redshift)](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)
- 2026-02-10 · [Fire from a spinning logo spline + Upscaling for detail](../../recipes/2026-02-10_upscale-fire-from-spinning-spline.md)
- 2026-01-27 · [Wispy particle trail behind a running mocap character (EFX advection)](../../recipes/2026-01-27_gpu-particle-advection-running-character.md)
- 2026-01-13 · [Target EFX turbulence/vorticity to fuel or temperature (force mapping)](../../recipes/2026-01-13_efx-forces-mapping.md)
- 2025-12-30 · [Running man on fire (nxExplosiaFX: motion inheritance, noise-weighted fuel, upscaling budget)](../../recipes/2025-12-30_man-on-fire.md)
- 2025-12-22 · [Real-scale candle flame (nxExplosiaFX small-scale settings)](../../recipes/2025-12-22_candle-flame-real-scale.md)
- 2025-11-25 · [Detailed fire around a rotating logo (first GPU nxExplosiaFX tutorial)](../../recipes/2025-11-25_detailed-fire-noise-weighted-fuel.md)
- 2025-11-11 · [Dry ice smoke spilling over a logo (nxExplosiaFX negative buoyancy)](../../recipes/2025-11-11_dry-ice-sinking-smoke.md)
- 2025-10-16 · [Feature notes: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2025-03-18 · [Particle motion blur in Redshift (custom shutter, Frame Position for dying particles)](../../recipes/2025-03-18_redshift-particle-motion-blur-frame-position.md)
- 2024-04-16 · [Bend a straight fire sim around a helix (xpExplosiaFX + C4D Spline Wrap)](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)
- 2024-02-13 · [Densify a cached advected sim by spawning (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-23 · [Text spline blown by an explosion (xpDynamics on a spline + xpExplosiaFX advection)](../../recipes/2024-01-23_xpdynamics-spline-advection.md)
- 2023-08-15 · [Millions of smoke-advected particles rendered additively (xpExplosiaFX Advect Particles, X-Particles material Add blend)](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)
- 2023-04-14 · [Wispy particles squirting from a breaking crystal (cached xpShatter, xpExplosiaFX Source tag, Advection, inner-face emission, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Swapping in a high-detail smoke sim, final retime and Cycles 4D render setup (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Higher-res fire re-sim from spawned fuel particles (xpSpawn on infected groups, cache Include, finer xpExplosiaFX voxels)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Reveal a mesh only where smoke passes through it (Cycles 4D Point Density on the mesh, staggered xpExplosiaFX emitters)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
- 2023-03-29 · [Combining cached sub-scenes into one master build (xpCache Hold/Offset, Alembic speed, PolyFX + layered fields)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
