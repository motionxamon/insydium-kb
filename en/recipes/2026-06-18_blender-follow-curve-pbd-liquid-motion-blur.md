# Liquid stream looping round a curve, meshed with motion blur (nxFollowGeo spline + nxFluids PBD + nxMesher Transfer Velocity)

- Source: NeXus for Blender Official Training — Follow Curve — https://www.youtube.com/watch?v=na6NGPw4XWM (2026-06-18)
- Host / generation: Blender (NeXus for Blender, G3); nxFollowGeo, nxFluids PBD, nxTurbulence, nxSpeed, nxMesher, nxCache; Cycles GPU
- Goal: turbulent, splashy water ribbon circling a Bezier circle, rendered with mesh motion blur.

## Steps
1. **nxEmitter** Sphere, radius **0.2**, direction **−Z**, Rate random **50,000/s**, particle radius **0.01**, emit for **120 frames**. Bezier circle rotated on X to face camera; emitter on its edge.
2. **nxFollowGeo** ▸ Object = Bezier circle (auto-detects spline vs polygon). **Release ▸ Spline End: Loop**. **Extended Data**: delete the default **Offset** layer (0.2 m ribbon offset) — the fluid solver handles spacing.
3. **nxFluids** solver **PBD** (copes best with heavy, unrealistic forces). Bulging at birth = too dense → tick **Density** check (kills particles born above the density threshold).
4. Emitter Display: smaller points, Color **Gradient by Speed**, Auto Scale off, max 0.04.
5. **nxTurbulence** (Voronoi) Scale 120, Strength 25.
6. **nxSpeed** placed **last** in the stack: Incremental layer with speed **0** used purely as a clamp, **Min 0.5, Max 4**.
7. nxFollowGeo tuning: overall **Strength 50%**; **Attract Strength** up = tighter to the curve and smoother; **Active Range 2.5** lets it break up and rejoin.
8. Turbulence pushed to Strength 35 → 45, Scale 130 for splashy kicks.
9. Fake surface tension in PBD: raise **External Pressure** and a little **Repulsion**; **Smoothing Radius** 115–125 = long tendrils (slower); settled on **105**.
10. **nxMesher** ▸ emitter layer: **Polygon Size 0.015**, **Radius 0.015**; Surface Type **Zhu-Bridson** (self-smoothing, fast) instead of Spheres. Alternative: Radius 0.025 + Mean Curvature smoothing 100%, 5 iterations (loses a bit of detail).
11. **Export Tags ▸ Transfer Velocity**, max speed **4** on each field (matches nxSpeed clamp) → vertex velocity attribute on the mesh.
12. Timeline 300 F, **nxCache** defaults ▸ Build Cache (~20–30 s), then disable the live objects.
13. Cycles GPU: noise threshold up, 1000 samples, no denoise; **Fast GI Approximation** for previews; **Motion Blur shutter 1 frame** (reads cached velocity automatically). Area lights (Normalize off; e.g. 50/40/30, Track To the nxFollowGeo at origin); Principled Transmission 1, roughness ~0, **IOR 1.33**; optional DOF (F-stop ~3.3) on the follow-geo object. **Lock Interface** before rendering.

## Gotchas
- Leaving nxSpeed Incremental at its default keeps accelerating particles.
- Too-small mesh radius vs polygon size drops particles from the mesh.

## Newest equivalent
2026.1 beta **nxWarp Path / Helix** (Guide or Flow mode) shapes streams along a path for particles, meshes and smoke; FLIP/APIC is the realistic liquid route if forces are gentler.
