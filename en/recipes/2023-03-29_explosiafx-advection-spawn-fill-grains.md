# Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)

- Source: Maintenance Training — XP Countdown - Series 2 - xpExplosiaFX Advection 02 — https://www.youtube.com/watch?v=isCt2UKxPtM (2023-03-29)
- Host / generation: C4D; all CPU X-Particles (xpExplosiaFX, xpFlowField from splines, xpFluidFX granular, xpSpawn, xpScale, xpQuestion/Change Life action, xpCache); hardware OpenGL preview
- Goal: refine the "2" grains crumble so EFX plumes pull spiky tendrils out while the number stays readable, then fade the sand as the smoke dissipates.

## Base
Previous video's scene: xpFluidFX granular grains on a "2" collider; xpFluidFX keyframed off at F75→76 so the EFX advection takes over; EFX particles follow spline-driven **xpFlowField** arcs. Grains display Dots for faster playback.

## Steps
1. Keyframe **xpGravity** off at the same frame as xpFluidFX (75 on, 76 off) — otherwise grains sag the moment the fluid solver stops.
2. Push the EFX source object a little deeper into the grains so plumes grab edge particles.
3. **Fill the advection holes with xpSpawn**: Generate ▸ xpSpawn → create spawn emitter (pink while testing). Position = source particle, Direction relative to source, Speed **inherit × 0.5**, Spawn Number **10**/s. Inherit tab: **Color + Radius**.
4. Time it with **Mapping** (not keyframes): parameter Spawn Number, source **Scene Time**, range **75 → 116**; curve rises right away then tapers to 0 by F116.
5. Spawn emitter ▸ Modifiers: switch **Exclude → Include** and list only xpExplosiaFX + xpFlowField (later xpScale) — spawn mod stays out to avoid recursive spawning.
6. Spawn modifier **Falloff ▸ Box field** around the number so grains already falling away don't spawn (saves compute).
7. Gotcha: EFX source particles got stuck on the grains' "2" collider → collider tag **Exclusions** = EFX source emitter.
8. Tighter arcs: point-select the few-point flow-field splines and scale them in.
9. Converging flow vectors made a thin smoke line along −Z → **xpFlowField Falloff ▸ Box field** over the centre, Remapping **Invert**, so streams pass through each other.
10. Production res: EFX **Voxel Size 6 → 2 cm** (1 cm advised for final quality); source particle radius 8 (var 2) → **5**. Display Smoke only, LOD 80.
11. EFX Simulation ▸ **Smoke Dissipation** keyed 0 at F130 → 0.5 at F150 (small values go far). **Vorticity 15%**, radius **2.5** for finer curls (too much = furry).
12. Fade the sand: **xpScale** Radius Change negative (default +0.2 cm/s grows radii → fluid pressure blasts grains apart), Variation **75%**. Show it with Display Circles Filled (Dots don't show radius).
13. Kill shrunk grains: emitter **Questions ▸ Particle Radius = 0** → **Action ▸ Change Life (Kill)**; drag the same question into the spawn emitter and add xpScale to its Include list. HUD count now drops.
14. Map Radius Change by **Scene Time 120 → 160** (age differs between grains and spawned particles); lower the max (≈ −0.1) and ease the curve so grains vanish gradually.
15. Variations: change the EFX emitter **Advanced ▸ Seed**. Stronger tendrils: scale the EFX source smaller and overlap it more with the grains.
16. **xpCache** (unique object names first), 220 F → ~6.5 min, ~5 GB in the demo; on cached emitters tick **Force Display** to change display mode. Judge timing with a **Hardware OpenGL** render (720p, frame rate = project 30 fps).

## Gotchas
- Separate systems + collider tags: always check exclusions, or particles from the other system collide.
- Mapping by Scene Time keeps spawning/fading in sync across emitters with different particle ages.

## Newest equivalent
GPU **nxExplosiaFX** (Fused 2025.4) with **Dynamics ▸ Particle Advection**, **nxSpawn** (2026.1 beta) or nxQuestion Spawn for the fill, nxScale + nxQuestion Kill for the fade; **nxWarp** Path/Flow (2026.1 beta) can shape the smoke streams instead of a spline flow field; sand itself via nxMPM. See 2026-09-01 and 2023-08-15.
