# nxPush — tool card

Mentioned in **25** recipes · 2023-02-21 → 2026-10-13 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxPush**: mode **Particle Radius**, maximum strength → spheres jostle apart as they grow. [▶ 7:23](https://youtu.be/rDSSeIZUl08?t=443) — *[2025-11-06](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)*
- **nxPush** Particle Radius mode, strong → grown particles shove each other. [▶ 5:28](https://youtu.be/Xe1seJC3g0k?t=328) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- **nxPush** Particle Radius mode, full strength, 10 iterations. [▶ 4:36](https://youtu.be/PTamR793O-k?t=276) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- …so use the collider's **Forces tab → Attraction**, Radius 100 cm, strength ~59 → particles hug the surface while pushing apart. (Avoid nxFollowGeo + nxPush — opposing forces.) [▶ 6:19](https://youtu.be/PTamR793O-k?t=379) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- **nxPush**: Distance mode **Particle Radius**, strength 100%, iterations ~20. [▶ 1:49](https://youtu.be/v63KTwt6pI4?t=109) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*
- **nxPush**: Distance = **Particle Radius**, Strength 100, **Iterations 1000**. Below it **nxKill**, Volume = Objects ▸ floor cube, Inside → kills grains pushed into the floor. [▶ 24:39](https://youtu.be/fxJI8py9BzU?t=1479) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- Break the hex grid: **disable the collider**, emission **Jitter X/Y/Z = 0.225** (≤ radius), then **nxPush** Particle Radius, full strength, thousands of iterations (≈3 min for frame 1) to undo overlaps; then **nxKill** box (size 100, Y −100 so its top sits on the floor, kill inside bounds) placed **after** the push to remove grains pushed below ground. [▶ 36:40](https://youtu.be/V4mwAf8tcLk?t=2200) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Disable gravity and fluids. Add **nxPush**: mode **Particle Radius**, **Strength 100**, **Iterations ~200** (all the separation must happen in a single frame; more particles → more iterations). [▶ 3:15](https://youtu.be/XwX71yF7O5M?t=195) — *[2025-04-01](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)*
- Bake it: emitter ▸ Object ▸ **Initial State ▸ Set State** after the push frame; Emission mode → **Controlled Only** so nothing new is emitted. Delete/disable nxPush. [▶ 6:19](https://youtu.be/XwX71yF7O5M?t=379) — *[2025-04-01](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)*
- Stack order: **nxTurbulence → nxPush → nxSpeed**. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*
- - nxPush: **Particle Radius** mode, full strength (no overlaps). — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*
- **nxPush**, Distance mode **Particle Radius** — then exclude it from the parent emitter (Modifiers tab, exclude list) so parents stay put. [▶ 4:28](https://youtu.be/WTMgHpdgOhY?t=268) — *[2024-09-17](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)*
- **nxPush** placed **below** the nxQuestion (order changes the look), Distance mode **Particle Radius**, Strength **100 %** → no initial blow-apart, tendrils extrude. [▶ 4:29](https://youtu.be/LB-aA-N-2b0?t=269) — *[2024-08-27](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)*
- **nxPush** in **Particle Radius** mode, more iterations. [▶ 1:09](https://youtu.be/nJpItCX8GlY?t=69) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*

## All recipes (25)
- 2026-10-13 · [Procedurally animate an emitter along a path with jdGeoFlow](../../recipes/2026-10-13_jidou-geoflow-emitter-path.md)
- 2026-06-30 · [Start/stop a looping nxQuestion animation with the Break action](../../recipes/2026-06-30_nxquestion-action-break.md)
- 2026-06-15 · [Particle color at render time in Cycles and Eevee (nxEmitter Point Cloud export + Geometry Nodes attributes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-05-19 · [Pulsing particle speed / size with nxQuestion Math ▸ Wave](../../recipes/2026-05-19_nxquestion-sine-wave-pulsing.md)
- 2025-11-06 · [Particles growing over a procedural wire mesh (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)
- 2025-11-04 · [Particles that bloom in the crevices of geometry (nxQuestion neighbours + field)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-07 · [Pulsing particles pushing each other while hugging a surface (collider attraction)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-07-03 · [Feature notes: layered nxTurbulence, nxScale and the new nxLimit (Fused 2025 preview, part 1)](../../recipes/2025-07-03_feature-notes-layered-nxturbulence-nxscale-nxlimit.md)
- 2025-06-24 · [Self-sustaining grow / push / shrink particle loop (nxAttract + nxPush + nxQuestion field + mapped nxRotate)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-05-07 · [Exploding granular bust rendered as sand and as snow (nxFluids SPH Granular, nxExplode, stability mapped to Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-04-01 · [Hide the hexagonal grid in granular sims (emitter Jitter + one-frame nxPush + Initial State)](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)
- 2024-11-12 · [Blooming trail flower (age-mapped nxTurbulence Curl Blend/Add + speed-mapped strength)](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)
- 2024-10-15 · [Uniform render size from a radius-driven sim (xpCache Custom Playback channels, Redshift particle spheres)](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)
- 2024-09-17 · [Non-intersecting particle branches inside a mesh (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-08-27 · [Field-triggered self-growing tendrils (nxQuestion Variable + Spawn + Set Age/Life, nxPush by radius)](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)
- 2024-07-30 · [MoGraph Matrix points as moving attraction targets (nxAttract Object mode + nxPush + nxScale age map)](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)
- 2024-07-23 · [Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-09 · [Particle radius drives color and glow in Redshift (Scalar User Data ▸ Change Range ▸ Ramp / Scalar Ramp)](../../recipes/2024-07-09_redshift-particle-size-color-emission.md)
- 2024-04-25 · [Feature notes: NeXus 2024.2 core rebuild — faster GPU solve and animated-geometry collisions](../../recipes/2024-04-25_feature-notes-nexus-2024-2-speed-collisions.md)
- 2024-04-09 · [Trippy flat push patterns (nxPush + nxQuestion velocity lock + nxScale by field)](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)
- 2023-09-27 · [Living shatter countdown (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)
- 2023-09-27 · [Self-organising "breathing" sphere clusters (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-07-05 · [Field-driven recursive growth with nxQuestion spawning (nxQuestion Neighbors + Spawn, nxPush, mapped nxTurbulence)](../../recipes/2023-07-05_nxquestion-recursive-growth-rig-part-a.md)
- 2023-02-21 · [Three ways to make particles collide with each other (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
