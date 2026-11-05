# Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)

- Source: NeXus Official Training — nxWarps — https://www.youtube.com/watch?v=WJwIek6M8z8 (2026-10-30)
- Host / generation: C4D (parts 1–2, cm) and Blender (parts 3–4, m); NeXus 2026.1 beta (G3: nxEmitter, nxWarp, nxExplosiaFX, nxFluids FLIP, nxMesher)
- Goal: precise, procedural shaping of noisy sims — roll a 2D stream into a 3D wave, route a "pipe" flow, bend/twist fire, spiral a FLIP jet.

## Warp basics (on a plane, C4D)
- Make the warp a child of the geometry, click **Fit to Parent** so its bounds match. Non-destructive, like a C4D/Blender deformer.
- **nxWarp Scroll**: Roll, Radius, Spacing (gap between turns), Direction (negative = crashing-wave curl).
- Every warp shares **Twist**, **Taper** (front/back), **Bulge** + **Position**.
- Three modes: **Deform** (moves display positions only, sim untouched), **Guide** (steers the actual sim; **Guide Strength**), **Flow** (traps particles inside a profile until they exit the end face).

## Steps
1. **2D sim → 3D wave (C4D):** nxEmitter flattened (height near 0), placed at the back of the warp; Birth Rate 50,000 (later 150,000); Display size 2; Full Lifespan off, Life 100, variation 20.
2. **nxTurbulence** (default Voronoi noise looks flame-like): Axis Direction Scale **Y = 0** to keep it flat; Octaves 3; lower Persistence to keep the big swirls.
3. **nxWarp Scroll** sized to enclose every particle (drag the handles); Radius 8, Spacing 1, then raise Radius and Roll; negative Direction. Optional: Y scale 15–40% for depth, then raise the warp height (default 1 cm) to contain it. **nxColor** gradient by Speed.
4. **Pipe routing (C4D):** Disc emitter r 15 cm, rate 15,000, life 300, + nxTurbulence + nxColor. **nxWarp Bend** rotated 90° to face the stream, Angle 90°.
5. **Guide mode**: particles really travel round the bend. 100% strength flattens turbulence; lower it for detail, but too low lets particles escape the bounds.
6. **Flow mode**: Profile Square (default) / Circle (tube) / Star / Custom (control spline); particles can only leave through the exit face.
7. Ctrl-drag a copy, rotate 180° and 90° → S-bend. Add a cube + **nxCollider** (scatter) after the exit: collisions work in Guide mode, not in Deform (particles aren't really there).
8. **nxGravity** with a small **Linear falloff** at the pipe exit so gravity only kicks in after the guide; collider Bounce 0, more Friction/Scatter.
9. **Fire (Blender):** nxExplosiaFX, sphere in Sources tab, coarser voxel size, Temperature Dissipation 3. Warp bounds = domain or slightly larger. Bend 90/180/360°; Twist ~800°.
10. **Helix**: Start Radius 0, Mid 0.5, End 1.5, Turns 3. Layer warps: copy the helix, switch the copy to Bend, enlarge its bounds to cover the already-deformed smoke, Angle 180–360°.
11. Guide mode on smoke steers the real sim but smooths it and stays inside the domain — use a low Guide Strength to keep the fiery detail.
12. **FLIP spiral (Blender):** tall nxFluids FLIP domain; sphere nxEmitter at the bottom, **Match Solver Resolution** → FLIP, direction +Z, speed 2.5; nxColor by Speed; nxTurbulence strength 16.
13. Attractor-style modifier with target at the top: Acceleration 0, Speed Limit huge, Force 20 — keeps a thin stream. FLIP **+Z wall = Kill**.
14. **Mapping** ▸ Particle Age layer → Turbulence **Strength**: full up to age 100, fading to ~0 by 200.
15. **nxWarp Twist** enclosing the column, Guide mode, Angle 500 → 2000 with Guide Strength lowered; raise the attract strength to hold the stream.
16. **nxMesher** emitter layer: Resolution 0.02, Radius 0.03–0.04 (0.025 too thin), Surface **Zhu-Bridson**.

## Gotchas
- The warp bounds must contain all particles/voxels; for a layered warp, size it to the output of the previous warp.
- Deform = fast and exact but not physical; Guide/Flow = physical, so colliders and forces downstream behave correctly.
- Beta 3 (same day) changed **Flow Reach** default to 0% — use 300% for the old Flow behaviour.

## Newest equivalent
This is the newest route (2026.1 beta); it replaces nxFollowGeo / xpFollowSpline-style stream shaping and force-only smoke steering.
