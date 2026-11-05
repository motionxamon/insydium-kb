# nxSpeed — tool card

Mentioned in **21** recipes · 2023-04-13 → 2026-08-25 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxSpeed** ▸ default Incremental layer with a **negative** value (**−0.04**) + variation → gentle slow-down. [▶ 1:09](https://youtu.be/I2ERiN8Vk2Q?t=69) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- - **nxSpeed**: default layer is incremental (+1.5 m/s per s) → set increment **0**, clamp **max speed ~1** so turbulence strength can go very high without runaway acceleration. — *[2026-07-06](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)*
- **nxSpeed** placed **last** in the stack: Incremental layer with speed **0** used purely as a clamp, **Min 0.5, Max 4**. [▶ 6:17](https://youtu.be/na6NGPw4XWM?t=377) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **Export Tags ▸ Transfer Velocity**, max speed **4** on each field (matches nxSpeed clamp) → vertex velocity attribute on the mesh. [▶ 14:58](https://youtu.be/na6NGPw4XWM?t=898) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **nxSpeed** *below* turbulence → **Range** layer: Speed Start 0 / End 300 over 0–60 frames. **Flip the ease curve** so it starts at full speed (300) and ends at 0 → shoot out then stop, with an ease-in to the stop. [▶ 3:20](https://youtu.be/HvX6qaVei1o?t=200) — *[2026-03-31](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)*
- **nxSpeed**: Incremental +0, **Max speed ~65** (calms it). [▶ 4:24](https://youtu.be/D8XcG_EuvG8?t=264) — *[2025-07-15](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)*
- **nxSpeed** last: Incremental 0, **Max speed 150**. [▶ 6:45](https://youtu.be/v63KTwt6pI4?t=405) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*
- Calm it: **nxSpeed** below the turbulence, Accelerate with **Force 0**, **Max Speed 80 cm** — strong turbulence but clamped speed. [▶ 2:34](https://youtu.be/RUhF1pju3Wk?t=154) — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- Tame the wild edges: **nxSpeed** after the wind, operation **Acceleration** with exponential 0 (does nothing) + **Clamp Max Speed 500 cm**. [▶ 33:00](https://youtu.be/V4mwAf8tcLk?t=1980) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxSpeed** last in the stack: Operation Acceleration with value **0**, enable **Clamp Max Speed** ~400 cm. [▶ 4:22](https://youtu.be/PYtRwy_bbCE?t=262) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- nxSpeed ▸ **Mapping ▸ Radius map** (range 0–3 cm) → parameter **Clamp Max Speed**; small sparks get a lower speed cap. Lift the curve's low end so they never fully stop. [▶ 5:16](https://youtu.be/PYtRwy_bbCE?t=316) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- **nxTurbulence** placed *above* nxSpeed (so the clamp wins): Curl, strong, low persistence, higher octaves → big wavy swirls. Speed cap up to ~500. [▶ 6:34](https://youtu.be/PYtRwy_bbCE?t=394) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- Stack order: **nxTurbulence → nxPush → nxSpeed**. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*
- - nxSpeed: **Incremental −25** → gradual slowdown. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*

## All recipes (21)
- 2026-08-25 · [Flower-burst trails with speed-mapped thickness and per-vertex color (nxTrail, nxScale + nxTurbulence speed mapping)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-07-06 · [Layered curl turbulence tendrils (nxTurbulence Curl + FBM + Voronoi layers, per-layer age mapping, nxSpeed clamp, nxScale fade-in)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-18 · [Liquid stream looping round a curve, meshed with motion blur (nxFollowGeo spline + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-09 · [Random birth orientation + repeatable 360° spins (nxSpin + age reset)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-03-31 · [Burst particles that ease to an organic stop (nxSpeed Range + curl turbulence)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2026-02-17 · [Recolor cached particles with nxColor (and speed-clamp by color)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-08-14 · [Feature notes: nxFollowGeo spline modes, per-channel nxUpres, layered nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-07-15 · [Sand that piles into a spline shape (granular SPH + xpFlowField To-Spline layer)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2025-06-24 · [Self-sustaining grow / push / shrink particle loop (nxAttract + nxPush + nxQuestion field + mapped nxRotate)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-05-06 · [Particle wireframe reveal (nxFollowGeo Edge mode + nxTurbulence + nxSpeed limit)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2024-12-31 · [Firework sparks off hand-drawn text (nxScale + nxQuestion kill + nxSpeed clamp mapped to Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-11-12 · [Blooming trail flower (age-mapped nxTurbulence Curl Blend/Add + speed-mapped strength)](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)
- 2024-10-22 · [Clone and mirror emitters for a kaleidoscope (xpEmitter Instance mode + MoGraph Cloner)](../../recipes/2024-10-22_instance-emitters-kaleidoscope.md)
- 2024-07-23 · [Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-16 · [Lava that freezes and re-melts (animated Random field color → mapped nxWind strength + nxSpeed max speed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-06-11 · [Statue crumbling into sand as an infection spreads (nxInfectio groups + nxFluids SPH Granular + nxSpeed Max Speed 0)](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)
- 2023-12-26 · [Natural falling snow (nxSpeed limit mapped to radius + second nxTurbulence Curl Blend mapped to radius)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-07-05 · [Hot/cold variable-viscosity pour over a head (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + colour-mapped nxSpeed clamp)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-04-19 · [Interactive melt / re-harden rig driven by particle color (nxSpeed Clamp Max Speed mapping + nxQuestion fields + nxBlend + mapped SPH viscosity)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-04-13 · [Crystal that crumbles shard by shard (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)
