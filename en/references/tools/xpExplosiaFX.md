# xpExplosiaFX — tool card

Mentioned in **13** recipes · 2023-03-29 → 2025-10-16 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpExplosiaFX** Solver size **50 × 1300 × 50** (tall, thin). Container options: **block all sides except the top**. [▶ 0:45](https://youtu.be/RkAB9dD0X5k?t=45) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- Fuel source: sphere r 5 cm at the bottom + **xpExplosiaFX Source tag**: Solid off (fills volume), Heat 200, Fuel 200, add **Pressure** to push gas up faster. [▶ 1:35](https://youtu.be/RkAB9dD0X5k?t=95) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- At frame 0, add a **Spline Wrap** deformer as a child of the xpExplosiaFX object, spline = Helix, axis **+Y**. The cached/simulated volume now follows the helix; Helix angles can be keyframed. [▶ 4:22](https://youtu.be/RkAB9dD0X5k?t=262) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- Material: Cycles 4D ▸ **xpExplosiaFX presets ▸ Burn** on the domain; render in Cycles real-time preview. [▶ 5:56](https://youtu.be/RkAB9dD0X5k?t=356) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- Default **xpExplosiaFX** + sphere with **xpExplosiaFX Source tag** (default); view Temperature channel. [▶ 0:24](https://youtu.be/XtaaaiKtl_w?t=24) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- xpExplosiaFX **Advection** tab active → the smoke moves the particles. [▶ 1:41](https://youtu.be/XtaaaiKtl_w?t=101) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- Emitter **Extended Data**: Temperature 1, Fuel 1; add **xpExplosiaFX Source tag** (default). [▶ 1:13](https://youtu.be/2YkjQgmo8Ic?t=73) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- xpExplosiaFX ▸ Advection ▸ **Advect Particles** on. [▶ 3:24](https://youtu.be/2YkjQgmo8Ic?t=204) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- Source emitter ▸ Modifiers tab: **exclude xpExplosiaFX** — otherwise it's advected by its own explosion and jitters. [▶ 4:05](https://youtu.be/2YkjQgmo8Ic?t=245) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- System Dynamics ▸ **xpExplosiaFX** (pink domain). Sphere ▸ Tags ▸ INSYDIUM ▸ **xpExplosiaFX Source** tag, defaults → instant smoke/fire. [▶ 1:16](https://youtu.be/_G2CwPw4OSY?t=76) — *[2023-08-15](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)*
- Re-enable the emitter; xpExplosiaFX ▸ **Advection** tab ▸ enable **Advect Particles**. [▶ 2:35](https://youtu.be/_G2CwPw4OSY?t=155) — *[2023-08-15](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)*
- **xpExplosiaFX**: shrink the domain with handles; Solver ▸ **Voxel Size 4 → 1 cm** (fuel particles are 2 cm). Display: Mode Temperature, **Grid** look, LOD ~**120%** + transparency (Display ▸ Grid ▸ Back shows voxels). [▶ 9:31](https://youtu.be/EAtbWdajZ4E?t=571) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*
- Shard emitter ▸ Tags ▸ **xpExplosiaFX Source** tag (defaults). Simulation ▸ **Gravity off** → no buoyancy. [▶ 17:32](https://youtu.be/EAtbWdajZ4E?t=1052) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*
- xpExplosiaFX ▸ **Advection** on (defaults) → particles swirl with the hidden sim. [▶ 14:43](https://youtu.be/EAtbWdajZ4E?t=883) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*

## All recipes (13)
- 2025-10-16 · [Feature notes: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2024-04-16 · [Bend a straight fire sim around a helix (xpExplosiaFX + C4D Spline Wrap)](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)
- 2024-02-13 · [Densify a cached advected sim by spawning (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-23 · [Text spline blown by an explosion (xpDynamics on a spline + xpExplosiaFX advection)](../../recipes/2024-01-23_xpdynamics-spline-advection.md)
- 2023-08-15 · [Millions of smoke-advected particles rendered additively (xpExplosiaFX Advect Particles, X-Particles material Add blend)](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)
- 2023-06-23 · [Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-04-14 · [Wispy particles squirting from a breaking crystal (cached xpShatter, xpExplosiaFX Source tag, Advection, inner-face emission, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Swapping in a high-detail smoke sim, final retime and Cycles 4D render setup (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Higher-res fire re-sim from spawned fuel particles (xpSpawn on infected groups, cache Include, finer xpExplosiaFX voxels)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Reveal a mesh only where smoke passes through it (Cycles 4D Point Density on the mesh, staggered xpExplosiaFX emitters)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
- 2023-03-29 · [Combining cached sub-scenes into one master build (xpCache Hold/Offset, Alembic speed, PolyFX + layered fields)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
