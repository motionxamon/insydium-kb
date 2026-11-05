# xpFlowField — tool card

Mentioned in **7** recipes · 2023-03-29 → 2025-10-28 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpFlowField** sized to the container: — *[2025-10-28](../../recipes/2025-10-28_liquid-countdown-flowfield.md)*
- **xpFlowField** sized around it: delete default Random layer → **To Spline** layer, cell size 10, mode **Velocity 300**, falloff off. [▶ 4:13](https://youtu.be/D8XcG_EuvG8?t=253) — *[2025-07-15](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)*
- X-Particles ▸ Dynamics ▸ **xpFlowField**; resize its bounds to enclose the whole spline (particles only react inside). [▶ 0:41](https://youtu.be/zA6fTkWvwwI?t=41) — *[2023-10-03](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)*
- Dynamics ▸ **xpFlowField**: scale bounds to the text; Display Arrow (voxels to see all); **Cell size 15**. [▶ 1:07:33](https://youtu.be/uS_zr-Jf178?t=4053) — *[2023-09-27](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)*
- **xpFlowField**: flow **Along Spline**, link the splines, **falloff off**, cell size 40 → ~17–18 cm, **Strength ~40** (default too weak to reach the "1"). [▶ 32:05](https://youtu.be/OKRG2FUtXjc?t=1925) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- **xpExplosiaFX ▸ Modifiers**: add the xpFlowField so the smoke itself is pushed along the splines. Tighten the paths by scaling the spline points in. [▶ 38:54](https://youtu.be/OKRG2FUtXjc?t=2334) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- Isolation: System EFX ▸ **Only Modifiers in Same System** on. Grains emitter ▸ Modifiers ▸ **Exclude** the xpFlowField (it must still see the EFX advection). [▶ 42:18](https://youtu.be/OKRG2FUtXjc?t=2538) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- Spawn emitter ▸ Modifiers: switch **Exclude → Include** and list only xpExplosiaFX + xpFlowField (later xpScale) — spawn mod stays out to avoid recursive spawning. [▶ 46:01](https://youtu.be/isCt2UKxPtM?t=2761) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*
- Converging flow vectors made a thin smoke line along −Z → **xpFlowField Falloff ▸ Box field** over the centre, Remapping **Invert**, so streams pass through each other. [▶ 26:41](https://youtu.be/isCt2UKxPtM?t=1601) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*

## All recipes (7)
- 2025-10-28 · [Liquid countdown: fluid flowing along animated number splines (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2025-07-15 · [Sand that piles into a spline shape (granular SPH + xpFlowField To-Spline layer)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2023-10-03 · [Particles flowing organically along a spline (xpFlowField Along Spline + Curl + To Spline layers)](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)
- 2023-09-27 · [Living shatter countdown (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Reveal a mesh only where smoke passes through it (Cycles 4D Point Density on the mesh, staggered xpExplosiaFX emitters)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
