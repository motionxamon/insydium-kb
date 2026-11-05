# nxScale — tool card

Mentioned in **26** recipes · 2023-03-29 → 2026-09-15 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Animate radius: emitter radius 0; **nxScale** layer **Set Value** 0.05, 60% variation, **Clamp to Radius Limit off**; Mapping ▸ Speed map → **Radius Value**, range 0–3.5; lift the curve's low end so slow particles keep some width → trails taper but never vanish. [▶ 10:34](https://youtu.be/I2ERiN8Vk2Q?t=634) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- Fade in the emission edge: display **Circles Filled** (Points ignore radius); **nxScale ▸ Range**: radius start 0 → end ~0.001 (0.01 for viewport tests), over 8 frames with 50% variation; longer (e.g. 25 frames) = softer feathering. Skip when the emission shape (logo/text) should read crisply. [▶ 17:36](https://youtu.be/U937aVtRzMA?t=1056) — *[2026-07-06](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)*
- **nxScale** (layered, with blend modes) ▸ default **Range** layer: Start Radius **0**, End Radius **1 m**, time **0 → 100 frames**; add variation to end radius and/or timing. [▶ 2:46](https://youtu.be/o7b5SV4BqfM?t=166) — *[2026-06-08](../../recipes/2026-06-08_blender-nxscale-range-ease-curve.md)*
- **nxScale** Range layer: radius 0 → End 60 cm with large variation. [▶ 7:21](https://youtu.be/5OHld9QtCzI?t=441) — *[2026-05-05](../../recipes/2026-05-05_random-groups-scale-mapping.md)*
- **nxScale Range**: Y axis = Radius Start→End, X axis = Start→End time; draw the curve up then down → grow-and-shrink over the particle's life. [▶ 6:02](https://youtu.be/THuXYZmNZjQ?t=362) — *[2026-04-28](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)*
- **nxScale** ▸ Object: **Set Value**, Radius **60 cm**. [▶ 1:12](https://youtu.be/AMCR5ciL7fw?t=72) — *[2025-04-24](../../recipes/2025-04-24_nexus-data-mapping-age-group-curves.md)*
- **nxScale** below gravity: negative change over time (Min −0.2, lots of variation), **Clamp Limit off** → sparks shrink to nothing. [▶ 2:52](https://youtu.be/PYtRwy_bbCE?t=172) — *[2024-12-31](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)*
- Animated width: **nxScale** Set by Falloff with the same random field; emitter radius 200, no variation; xpTrail Thickness **Use Radius Variable** → width painted along the trail. [▶ 5:39](https://youtu.be/Lx6Sugl11TA?t=339) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Spawn at radius 0 instead, then **nxScale ▸ Value over time**, small rate + variation, clamp **0 → 1.5** → particles grow after birth. [▶ 5:27](https://youtu.be/WTMgHpdgOhY?t=327) — *[2024-09-17](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)*
- **nxScale** (below nxPush — order matters): **Set Value** radius 3, **Mapping ▸ Age** 0→80 F on radius; curve rises from 0 quickly to full then shrinks by 80 F. [▶ 1:41](https://youtu.be/nJpItCX8GlY?t=101) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*
- Set the emitter radius to **0** so nxScale does all sizing (otherwise they pop on at 3 cm). [▶ 1:52](https://youtu.be/nJpItCX8GlY?t=112) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*
- **nxAttract** below nxScale, **Object** mode, drop the Matrix in → each Matrix point acts as a separate target; each particle goes to its **nearest** point. Target display off. [▶ 4:28](https://youtu.be/nJpItCX8GlY?t=268) — *[2024-07-30](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)*
- Set both spawn radii to **0**; display filled radius circles. **nxScale** change-over-time (slow), variation 5%, **Clamp to radius limit** + **within range**, max **1 cm**. [▶ 4:12](https://youtu.be/nC1YyRrwY2g?t=252) — *[2024-07-23](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)*
- **nxScale**: operation **Set by Falloff**, clamping off; Fields ▸ **Random field** — yellow = radius 0, red = emitter max radius (6). [▶ 2:51](https://youtu.be/IuaZtmg5O8o?t=171) — *[2024-04-09](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)*

## All recipes (26)
- 2026-09-15 · [Render NeXus particle data in Octane (color, radius → glass)](../../recipes/2026-09-15_octane-particle-data.md)
- 2026-08-25 · [Flower-burst trails with speed-mapped thickness and per-vertex color (nxTrail, nxScale + nxTurbulence speed mapping)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-07-06 · [Layered curl turbulence tendrils (nxTurbulence Curl + FBM + Voronoi layers, per-layer age mapping, nxSpeed clamp, nxScale fade-in)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-23 · [Bubbles trapped inside a viscous FLIP liquid (neighbour search)](../../recipes/2026-06-23_viscous-bubble-rig.md)
- 2026-06-15 · [Particle color at render time in Cycles and Eevee (nxEmitter Point Cloud export + Geometry Nodes attributes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-06-09 · [Random birth orientation + repeatable 360° spins (nxSpin + age reset)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-06-08 · [Animating particle size with the Range layer and its ease curve (nxScale Range)](../../recipes/2026-06-08_blender-nxscale-range-ease-curve.md)
- 2026-05-05 · [Few big, many small: random sub-groups + nxScale mapped by group](../../recipes/2026-05-05_random-groups-scale-mapping.md)
- 2026-04-28 · [Spawned particles that grow and fade organically (nxScale Range curve + kill)](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)
- 2026-03-31 · [Burst particles that ease to an organic stop (nxSpeed Range + curl turbulence)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2025-09-11 · [Feature notes: rewritten NeXus GPU core, per-layer GPU falloffs + Data Mapping, nxQuestion variations & neighbour search](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-07-03 · [Feature notes: layered nxTurbulence, nxScale and the new nxLimit (Fused 2025 preview, part 1)](../../recipes/2025-07-03_feature-notes-layered-nxturbulence-nxscale-nxlimit.md)
- 2025-04-24 · [Reading the Data Mapping curve: radius by age and by group (nxScale ▸ Mapping)](../../recipes/2025-04-24_nexus-data-mapping-age-group-curves.md)
- 2024-12-31 · [Firework sparks off hand-drawn text (nxScale + nxQuestion kill + nxSpeed clamp mapped to Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-12-10 · [Trails whose thickness follows particle radius (xpTrail Thickness: Use Radius Variable → Redshift curves)](../../recipes/2024-12-10_trail-thickness-from-radius.md)
- 2024-09-17 · [Non-intersecting particle branches inside a mesh (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-07-30 · [MoGraph Matrix points as moving attraction targets (nxAttract Object mode + nxPush + nxScale age map)](../../recipes/2024-07-30_matrix-points-nxattract-targets.md)
- 2024-07-23 · [Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-09 · [Particle radius drives color and glow in Redshift (Scalar User Data ▸ Change Range ▸ Ramp / Scalar Ramp)](../../recipes/2024-07-09_redshift-particle-size-color-emission.md)
- 2024-04-09 · [Trippy flat push patterns (nxPush + nxQuestion velocity lock + nxScale by field)](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)
- 2024-02-27 · [Spreading physics chain reaction (nxConstraints Birth + Collisions, nxScale/nxGravity mapped to Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-10-24 · [Grow at random rates, shrink with age, then die (nxScale Clamp within Range + Age map on Upper Radius Limit + nxQuestion kill)](../../recipes/2023-10-24_nxscale-random-growth-age-mapped-shrink.md)
- 2023-08-29 · [Grow and recolor particles inside a field, revert outside (nxQuestion Field question, Set Color / Set Radius, Else)](../../recipes/2023-08-29_nxquestion-field-color-radius.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
