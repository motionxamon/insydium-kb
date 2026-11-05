# nxWind — tool card

Mentioned in **22** recipes · 2023-06-20 → 2026-08-11 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Optional motion: **nxWind** ▸ **Von Karman**, strength ~2.5, lots of variation, raise Turbulence ▸ Friction Velocity. [▶ 1:36](https://youtu.be/vglrHSL-uc4?t=96) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Any modifier ▸ **Groups Affected**: nxWind on group 2 only (tick = include, minus = exclude/invert). [▶ 7:12](https://youtu.be/P9O1SJhPeik?t=432) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- **nxWind** mode **Von Karman**, diagonal direction, Strength ~3500 with high variation, lower turbulence, add Friction Velocity. [▶ 5:25](https://youtu.be/zyN7ERz7yuw?t=325) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- **Mapping tab** on nxWind: Wind Strength ← **Color (Brightness)**, Range Min 0.5 → full strength at 0.9 → only light patches blow away; darker stay. [▶ 6:05](https://youtu.be/zyN7ERz7yuw?t=365) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- **nxWind** von Kármán mode, strength 800–1200, turbulence off; **Vibrate tag** rotation 360° all axes, frequency 5; Mapping ▸ Age step 150 → 151 (off then on). [▶ 5:46](https://youtu.be/u2MiqeckNaQ?t=346) — *[2025-06-10](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)*
- **nxWind** pointing up, **Groups Affected = group 2** → only infected particles blow away. [▶ 4:04](https://youtu.be/xGxf_IIIekY?t=244) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- **nxWind**, **Groups Affected = group 1**, H −95°, P 55°; mode **Von Karman**, strength **625**, **Variation 190%** (>100% gives some negative, back-blowing gusts), turbulence frequency 40, Friction Velocity **0.13**. [▶ 14:43](https://youtu.be/V4mwAf8tcLk?t=883) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxWind**; Taiao Plant ▸ Forces ▸ **Direction from Object** = the wind, so tree and particles share one direction. [▶ 3:03](https://youtu.be/zG0XcLByiG4?t=183) — *[2025-03-04](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)*
- nxWind: **Von Karman** mode, strong, turbulence ~50, friction velocity **2.3**; Groups Affected = **group 2**. [▶ 3:20](https://youtu.be/zG0XcLByiG4?t=200) — *[2025-03-04](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)*
- **nxWind** and **nxColor** (direction-based color) ▸ Groups Affected = **group 2** — nothing happens yet. [▶ 1:54](https://youtu.be/35Yxc9a2QOU?t=114) — *[2025-02-18](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)*
- **nxWind** rotated along the flow, **Von Karman** mode, strength **250**, wind turbulence off for now. [▶ 0:57](https://youtu.be/bslBFptQSSM?t=57) — *[2024-07-16](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)*
- nxWind ▸ **Mapping ▸ Color Brightness** → **Wind Strength**, range 0 (black) → 1 (white): black gets no wind. [▶ 2:50](https://youtu.be/bslBFptQSSM?t=170) — *[2024-07-16](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)*
- **nxWind** aimed along the flower, fan display off, **strength 2** (tiny particles). [▶ 4:39](https://youtu.be/ZgUIL-udXks?t=279) — *[2024-05-28](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)*
- nxWind mode Standard → **Von Karman** (realistic eddies even at defaults). [▶ 1:55](https://youtu.be/RRKxOyJVrO8?t=115) — *[2024-05-07](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)*

## All recipes (22)
- 2026-08-11 · [Liquid Fill preset with FLIP/APIC, mesh and separate foam emitter (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-06-22 · [Triggering modifiers by switching particle groups (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-02 · [Granular text blown apart by gusts mapped to animated Voronoi color](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2026-04-28 · [Spawned particles that grow and fade organically (nxScale Range curve + kill)](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)
- 2026-02-17 · [Recolor cached particles with nxColor (and speed-clamp by color)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-11-26 · [Feature notes: Fused 2025 liquids — GPU FLIP/APIC with viscosity, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-10-16 · [Feature notes: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2025-06-10 · [Fluid sphere: settle → boil → explode → slosh (initial state + age-mapped nxVorticity / nxWind)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2025-05-22 · [Paint-style peeling off a surface (nxInfectio groups + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-04 · [Leaves blown off a Taiao tree (Taiao emitter leaves + nxWind Von Karman + nxQuestion Field/Random + xpSpin mapped to Speed)](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)
- 2025-02-18 · [Peel-away volume disintegration (nxQuestion Neighbor Count → Group → nxWind/nxColor)](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)
- 2024-07-16 · [Lava that freezes and re-melts (animated Random field color → mapped nxWind strength + nxSpeed max speed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-05-28 · [Pollen from a Taiao flower's stamen tips (tiPlant custom object, xpJoin, layer selection, nxWind)](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)
- 2024-05-07 · [Realistic gusting leaves (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2024-03-15 · [Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2023-12-26 · [Natural falling snow (nxSpeed limit mapped to radius + second nxTurbulence Curl Blend mapped to radius)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-12-12 · [Infection-driven peel-away (nxInfectio Use Groups + nxWind/nxTurbulence on infected group + nxConstraints Distance break)](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)
- 2023-10-31 · [Kill stray foam outside an arbitrary container (nxKill + field Volume invert / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
- 2023-07-03 · [Feature notes: redesigned nxQuestion and NeXus Data Mapping (Fused 2023.3)](../../recipes/2023-07-03_feature-notes-nxquestion-data-mapping.md)
- 2023-06-26 · [Feature notes: new NeXus modifiers — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, nxBlend modes, nxFoam on caches, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-06-20 · [Polygon-by-polygon disintegration driven by particles (xpFragmenter Faces Polys, xpWind with linear field, xpTurbulence mapped to distance travelled)](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)
