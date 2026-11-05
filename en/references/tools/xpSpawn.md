# xpSpawn — tool card

Mentioned in **7** recipes · 2023-03-21 → 2024-03-12 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpSpawn** ▸ Add Emitter ("emitter spawn"); spawn at source particle position, Direction **Random Spherical**, spawned speed **Absolute** (taken from the new emitter). Spawn emitter speed **100** (var 80); spawn rate **75** per frame (var 15) instead of 300. [▶ 3:59](https://youtu.be/PpDwpKu8478?t=239) — *[2024-03-12](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)*
- **xpSpawn** (Generate modifiers) ▸ **Add Emitter** → "emitter spawn": Draw Emitter off, **Dots**, Gradient Parameter (purple preset) mapped to **Speed**, min 10 / max 200; speed 0, lifespan 50 (var 25). [▶ 3:22](https://youtu.be/XtaaaiKtl_w?t=202) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- xpSpawn: spawn from source particle positions, defaults otherwise; amount 300 → **10/frame**, then **50** — spawned particles are advected by the same cached smoke. [▶ 4:23](https://youtu.be/XtaaaiKtl_w?t=263) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- Sparks: **xpSpawn**, exclude it on the start emitter's Modifiers tab; new spawn emitter: lifespan 10 (var 5), speed 200 (var 150), **Lines** display, thin, orange; spawn 60 (var 20) per frame, default spherical direction. [▶ 5:56](https://youtu.be/sctuPLrOw60?t=356) — *[2024-01-16](../../recipes/2024-01-16_mtsplinefx-lightning.md)*
- Disable the cloth emitter's cache tag. **xpSpawn** (Generate) ▸ Add spawning emitter → "Emitter Spawn"; position = **Source Particle**, speed **Absolute** with emitter speed **0** (they're moved by advection only). [▶ 3:28](https://youtu.be/xoJcz9u3c8g?t=208) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)*
- xpSpawn: rate **10 per frame** (default 300/s is too many), **Spawn Once Only**, life Absolute → emitter life **15 F, variation 5**; **Groups Affected** = incubated + infected (spawn only where the burn is). **Offset 2–3 cm** so the 10 spawns don't sit on top of each other. Spawned **Radius 1.5**. [▶ 6:29](https://youtu.be/xoJcz9u3c8g?t=389) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)*
- **Fill the advection holes with xpSpawn**: Generate ▸ xpSpawn → create spawn emitter (pink while testing). Position = source particle, Direction relative to source, Speed **inherit × 0.5**, Spawn Number **10**/s. Inherit tab: **Color + Radius**. [▶ 18:09](https://youtu.be/isCt2UKxPtM?t=1089) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*
- Modifiers ▸ Generate ▸ **xpMultiSpawn** (unlike xpSpawn it needs no separate spawn emitter). Default level: 10 new per source particle at age 0, for one frame. [▶ 0:39](https://youtu.be/XwQyDoAPNa4?t=39) — *[2023-03-21](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)*

## All recipes (7)
- 2024-03-12 · [Cutting laser with sparks (mtRayline contact-point emitter + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2024-02-13 · [Densify a cached advected sim by spawning (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-16 · [Procedural forked lightning with sparks (mtSplineFX + xpSplineMesher + xpSpawn)](../../recipes/2024-01-16_mtsplinefx-lightning.md)
- 2023-06-23 · [Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-03-29 · [Higher-res fire re-sim from spawned fuel particles (xpSpawn on infected groups, cache Include, finer xpExplosiaFX voxels)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-21 · [Three generations of spawning from one emitter (xpMultiSpawn levels + groups for display)](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)
