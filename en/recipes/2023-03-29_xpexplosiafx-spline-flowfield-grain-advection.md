# Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)

- Source: Maintenance Training — XP Countdown - Series 2 - xpExplosiaFX Advection 01 — https://www.youtube.com/watch?v=OKRG2FUtXjc (2023-03-29)
- Host / generation: C4D; all **CPU (G1)**: xpExplosiaFX + Source tag, xpFlowField, xpFluidFX granular grains from the previous episode (live, not cached)
- Goal: the "2" made of granular particles is blown apart by a colored smoke burst whose wisps arc forward along splines onto a "1".

## Base
- Grains scene saved as a new scene/folder (with its own cache folder); grains must stay **live** to be advected. Timeline 300 F; the "2" reads clearly by ~F70, so the blast starts ~F75–80.

## Steps
1. **Source mesh**: copy the "2" collider, remove its collider tag, MoText caps **None** (sides only). Quick editable single mesh: put it in a **Connect** object and press **C**.
2. New **xpSystem** ("System EFX", own icon color); emitter shape **Object** → source mesh, Emit From **Polygon Area**, **Invert** normal direction (MoText normals point inward).
3. Keep **Rate** mode and use the emitter **Object ▸ Falloff ▸ Box**: thin box that only emits where it overlaps the mesh. Keyframe its Y from **F76 → F85**, set the F-curve keys to **linear** = a fast sweeping blast.
4. **xpExplosiaFX** domain (room for the arc toward the "1"); **Voxel Size 6** while blocking. Emitter gets an **xpExplosiaFX Source tag**; emitter Extended Data ▸ Physical **Fuel 1**.
5. Display: **Grid** mode (or Slices ~80, Resolution ~150) for a clearer read.
6. Simulation tab: **gravity removed** (no buoyancy — stylised, follows paths). Source tag **Velocity 300%** so smoke keeps moving with the particles instead of lingering.
7. Paths: in the Right ortho view draw one **Bezier** arc with the Pen; **Cloner Radial, 9 clones**, small radius so they converge; **Connect** + **C** → one spline object ("splines").
8. **xpFlowField**: flow **Along Spline**, link the splines, **falloff off**, cell size 40 → ~17–18 cm, **Strength ~40** (default too weak to reach the "1").
9. Emitter tuning (Display **Circles** to see radius): Lifespan ~60 F + variation; Speed **130**, variation **30**; Birth Rate 1000 → **300**; **No Intersection** on (avoids doubled-fuel blobs); Radius **8** (with variation) at this voxel size — drop to ~4–5 once voxels get finer.
10. **xpExplosiaFX ▸ Modifiers**: add the xpFlowField so the smoke itself is pushed along the splines. Tighten the paths by scaling the spline points in.
11. Isolation: System EFX ▸ **Only Modifiers in Same System** on. Grains emitter ▸ Modifiers ▸ **Exclude** the xpFlowField (it must still see the EFX advection).
12. **xpExplosiaFX ▸ Advection ▸ Advect Particles**: only **Velocity 100**, all other channels (smoke, burn, temperature, color, UV) 0.
13. Keyframe Advection Velocity **0** until the blast starts (~F76–77), then **100** a few frames later.
14. Keyframe the **xpFluidFX Enabled** checkbox off right as the blast starts (~F77–78) — two velocity solvers on the same particles fight.
15. EFX emitter ▸ Modifiers ▸ **Exclude** the xpExplosiaFX, otherwise the source particles get advected by their own smoke and stop following the flow field.

## Gotchas
- **Adaptive Bounds** starts as a box that freezes advected grains inside it before the smoke exists — turning it off works but is slow; the keyed Velocity 0 is the fix.
- Two systems cross-talk by default: every emitter sees every modifier in the scene unless isolated (step 11).

## Newest equivalent
Fused 2025.4: GPU **nxExplosiaFX** (sources listed in its Sources tab) for the smoke; grains via nxFluids SPH Granular or **nxMPM** sand (2026.1 beta). For art-directed paths the 2026.1 beta's **nxWarp** (Path / Flow) bends particles and smoke; nxFollowGeo multi-spline guides particles in Fused 2025.4. whats-new does not document GPU smoke advecting other particles, so the CPU advection route above stays the reference for that hand-off.
