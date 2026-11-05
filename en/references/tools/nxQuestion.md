# nxQuestion — tool card

Mentioned in **55** recipes · 2023-03-21 → 2026-10-20 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxQuestion** ▸ question **Neighbors**: search distance **0.1** (0.05 = every particle counts as surface), **less than 30**, variation 7. Test first with a Set Color action (yellow) — only the outer shell should light up. [▶ 6:14](https://youtu.be/yOPa8oM_KXE?t=374) — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- Ending: drag the last curve point outside the domain; flow field ▸ **Flag on Escape**; **nxQuestion**: if flag Escaped → Action **Kill Particle** (or set a short varied lifespan). [▶ 17:02](https://youtu.be/I9Fq5NPENdc?t=1022) — *[2026-09-22](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)*
- Die with the flame instead of a fixed lifespan: **nxQuestion** — Question *Age > 2 frames* (buffer: newborn particles have 0 temperature) **AND** child Question *Temperature < 1000* → **Action Kill**. [▶ 7:31](https://youtu.be/1ERTCdQAoF0?t=451) — *[2026-09-01](../../recipes/2026-09-01_efx-advection-data-questions.md)*
- **nxQuestion** ▸ Question layer: Particle category, **Age > 45** → child **Action** (default Set Color yellow to test) → switch to **Set Group = group 2**. Feather it: **Age 55, variation 20**. [▶ 9:17](https://youtu.be/P9O1SJhPeik?t=557) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- **nxQuestion**: — *[2026-05-05](../../recipes/2026-05-05_random-groups-scale-mapping.md)*
- Short-lived "source" particles stuck to the branches → nxQuestion **Spawn** action with no question = continuous spawning into a second emitter. [▶ 2:32](https://youtu.be/THuXYZmNZjQ?t=152) — *[2026-04-28](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)*
- Color = temperature: **nxQuestion** `Document ▸ Object Distance (mode Polygons, object = cube) < 3 cm → Set Color white` with **reduced Weight** (fades to white = cools gradually). [▶ 2:58](https://youtu.be/VCGNxYZt21k?t=178) — *[2026-02-03](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)*
- **nxQuestion**: Age > 0 → Action **Set Radius 5** (later **3**), Weight ≈ **10%** so radius eases in. [▶ 6:50](https://youtu.be/rDSSeIZUl08?t=410) — *[2025-11-06](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)*
- nxQuestion: `Particle ▸ Neighbors (40 cm) > 420` → only seam particles (they see points from two surfaces). Tune the count by trial (300 = almost all, 400–420 = seams only). [▶ 2:30](https://youtu.be/Xe1seJC3g0k?t=150) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- Gate with a field: add the Sphere field to the **nxQuestion Fields tab** (must be listed!), then `If Field > 0.5` (inner falloff) **AND** child `Neighbors > 420` → actions. [▶ 3:04](https://youtu.be/Xe1seJC3g0k?t=184) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- **nxQuestion**: `Color Brightness < 0.1 → Set Radius 0` (low weight = gradual shrink) / `> 0.7 → Set Radius 26` (low weight). [▶ 2:33](https://youtu.be/PTamR793O-k?t=153) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- nxQuestion: — *[2025-09-09](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)*
- **nxQuestion** → Action **Set Color black** with **Weight ~7%** → gradual fade instead of instant switch. [▶ 1:28](https://youtu.be/1ISE9D2bmeQ?t=88) — *[2025-08-19](../../recipes/2025-08-19_nxquestion-neighbors-field-sand-mask.md)*
- **nxQuestion** with a **Spherical field**: `Field > 0.7 → Add to Radius` (large amount, **low weight** = slow growth); `Field < 0.3 → Set Radius 1` (low weight). [▶ 3:38](https://youtu.be/v63KTwt6pI4?t=218) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*

## All recipes (55)
- 2026-10-20 · [Outside-in disintegration of a particle volume (nxQuestion Neighbors → Set Group, speed-mapped forces)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-09-22 · [Liquid stream steered along a helix spline (nxFlowField Along/To Spline + Turbulence, PBD, nxQuestion escape kill)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-09-15 · [Render NeXus particle data in Octane (color, radius → glass)](../../recipes/2026-09-15_octane-particle-data.md)
- 2026-09-01 · [Particle flames from nxExplosiaFX advection data (temperature-driven kill & color)](../../recipes/2026-09-01_efx-advection-data-questions.md)
- 2026-06-30 · [Start/stop a looping nxQuestion animation with the Break action](../../recipes/2026-06-30_nxquestion-action-break.md)
- 2026-06-23 · [Bubbles trapped inside a viscous FLIP liquid (neighbour search)](../../recipes/2026-06-23_viscous-bubble-rig.md)
- 2026-06-22 · [Triggering modifiers by switching particle groups (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-09 · [Random birth orientation + repeatable 360° spins (nxSpin + age reset)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-05-19 · [Pulsing particle speed / size with nxQuestion Math ▸ Wave](../../recipes/2026-05-19_nxquestion-sine-wave-pulsing.md)
- 2026-05-05 · [Few big, many small: random sub-groups + nxScale mapped by group](../../recipes/2026-05-05_random-groups-scale-mapping.md)
- 2026-04-28 · [Spawned particles that grow and fade organically (nxScale Range curve + kill)](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)
- 2026-04-14 · [Looping color waves triggered by contact (nxQuestion variable switch + nxBlend)](../../recipes/2026-04-14_nxquestion-looping-switch-color-waves.md)
- 2026-02-24 · [Kill particles by distance traveled (nxQuestion age reset + Set Life)](../../recipes/2026-02-24_custom-lifespan-by-distance.md)
- 2026-02-03 · [Molten chocolate that sets on contact (APIC variable viscosity by color)](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)
- 2025-11-26 · [Feature notes: Fused 2025 liquids — GPU FLIP/APIC with viscosity, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-11-06 · [Particles growing over a procedural wire mesh (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)
- 2025-11-04 · [Particles that bloom in the crevices of geometry (nxQuestion neighbours + field)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-16 · [Feature notes: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2025-10-07 · [Pulsing particles pushing each other while hugging a surface (collider attraction)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-09-11 · [Feature notes: rewritten NeXus GPU core, per-layer GPU falloffs + Data Mapping, nxQuestion variations & neighbour search](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-09-09 · [Hot runny / cold gloopy fluid that re-melts on contact (groups + nxBlend + mapped viscosity)](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)
- 2025-08-19 · [Dynamic black/white mask on a sand sim → Redshift material blend (nxQuestion: Field AND Neighbors, Else)](../../recipes/2025-08-19_nxquestion-neighbors-field-sand-mask.md)
- 2025-07-03 · [Feature notes: layered nxTurbulence, nxScale and the new nxLimit (Fused 2025 preview, part 1)](../../recipes/2025-07-03_feature-notes-layered-nxturbulence-nxscale-nxlimit.md)
- 2025-06-24 · [Self-sustaining grow / push / shrink particle loop (nxAttract + nxPush + nxQuestion field + mapped nxRotate)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-05-27 · [Detailed field-triggered explosion via upres (nxUpres position + velocity, nxExplode, nxQuestion group switch)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-05-20 · [Organic springy particle network (nxConstraints birth springs + Forces layers, nxQuestion group switch & pin)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-04 · [Leaves blown off a Taiao tree (Taiao emitter leaves + nxWind Von Karman + nxQuestion Field/Random + xpSpin mapped to Speed)](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)
- 2025-02-18 · [Peel-away volume disintegration (nxQuestion Neighbor Count → Group → nxWind/nxColor)](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)
- 2025-01-14 · [Randomised field-triggered dissolve (nxQuestion Field + Group + Math Random)](../../recipes/2025-01-14_nxquestion-random-math-dissolve.md)
- 2024-12-31 · [Firework sparks off hand-drawn text (nxScale + nxQuestion kill + nxSpeed clamp mapped to Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-12-17 · [Text disintegration / reveal (nxQuestion field → switch group → reset age → set lifespan)](../../recipes/2024-12-17_particle-reveal-field-group-switch.md)
- 2024-10-04 · [Organic wrinkle growth creeping over a statue (nxConstraints Forces repulsion + xpDeformer, vertex-map-driven nxQuestion groups)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-09-17 · [Non-intersecting particle branches inside a mesh (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-08-27 · [Field-triggered self-growing tendrils (nxQuestion Variable + Spawn + Set Age/Life, nxPush by radius)](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)
- 2024-07-23 · [Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-04-09 · [Trippy flat push patterns (nxPush + nxQuestion velocity lock + nxScale by field)](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)
- 2024-02-13 · [Densify a cached advected sim by spawning (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-02 · [Melting blob from the outside in (nxDrag hold + nxQuestion Neighbors → group switch + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-10-31 · [Kill stray foam outside an arbitrary container (nxKill + field Volume invert / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
- 2023-10-24 · [Grow at random rates, shrink with age, then die (nxScale Clamp within Range + Age map on Upper Radius Limit + nxQuestion kill)](../../recipes/2023-10-24_nxscale-random-growth-age-mapped-shrink.md)
- 2023-09-27 · [Self-organising "breathing" sphere clusters (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-09-12 · [Activate a fluid sim by moving particles into a new group (nxQuestion Field + Random math, Set Group)](../../recipes/2023-09-12_nxquestion-field-group-switch-random.md)
- 2023-08-29 · [Grow and recolor particles inside a field, revert outside (nxQuestion Field question, Set Color / Set Radius, Else)](../../recipes/2023-08-29_nxquestion-field-color-radius.md)
- 2023-08-22 · [Splashing rain rig (xpCollider Spawn on collision, xpJoin for many colliders)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-07-05 · [Hot/cold variable-viscosity pour over a head (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + colour-mapped nxSpeed clamp)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-07-05 · [Field-driven recursive growth with nxQuestion spawning (nxQuestion Neighbors + Spawn, nxPush, mapped nxTurbulence)](../../recipes/2023-07-05_nxquestion-recursive-growth-rig-part-a.md)
- 2023-07-05 · [Electric arcs, cables and laser burn sparks (mtSplineFX + mtRayline + nxQuestion Spawn)](../../recipes/2023-07-05_mtsplinefx-arcs-rayline-laser-sparks-part-c.md)
- 2023-07-03 · [Feature notes: redesigned nxQuestion and NeXus Data Mapping (Fused 2023.3)](../../recipes/2023-07-03_feature-notes-nxquestion-data-mapping.md)
- 2023-04-19 · [Interactive melt / re-harden rig driven by particle color (nxSpeed Clamp Max Speed mapping + nxQuestion fields + nxBlend + mapped SPH viscosity)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-04-13 · [Crystal that crumbles shard by shard (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)
- 2023-04-04 · [Shrink trails away before particles die (xpTrailsMod via xpQuestion, or Change Trails action)](../../recipes/2023-04-04_shrink-trails-on-age-xptrailsmod.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-21 · [Three generations of spawning from one emitter (xpMultiSpawn levels + groups for display)](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)
