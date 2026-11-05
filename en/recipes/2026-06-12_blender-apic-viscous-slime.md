# Viscous slime coiling over a head (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)

- Source: NeXus for Blender Official Training — Liquid Slime — https://www.youtube.com/watch?v=pz6LDGGeD5A (2026-06-12)
- Host / generation: Blender (NeXus for Blender, G3); GPU nxFluids **APIC**, nxGravity, nxCollider, nxMesher; Cycles GPU
- Goal: thick slime pouring onto a Suzanne, stretching, snapping and coiling on the floor, rendered with subsurface scattering.

## Base
Suzanne, Subdivision 1 applied, shade smooth, scale **0.3** (≈3 m is too big).

## Steps
1. **nxFluids** solver **APIC** (FLIP/APIC are bounded voxel solvers; PBD is boundless). APIC is the host's choice for highly viscous liquids. Shrink the bounds tightly around the action (fewer voxels). Display ▸ draw grid (back only) to see voxels; floor display off. [▶ 1:33](https://youtu.be/pz6LDGGeD5A?t=93)
2. **nxEmitter** Sphere radius **0.05** above the head, Rate **20,000**, speed 0, particle radius **0.006** (radius drives the mesh later). [▶ 4:08](https://youtu.be/pz6LDGGeD5A?t=248)
3. **nxGravity** (required in Blender — no scene gravity). [▶ 4:28](https://youtu.be/pz6LDGGeD5A?t=268)
4. nxFluids **Voxel size 0.02** for accuracy. [▶ 11:02](https://youtu.be/pz6LDGGeD5A?t=662)
5. **nxCollider**: Suzanne layer (bounce 0, a little friction, later less); plus a **cube** floor inside the bounds as its own layer (bounce 0, friction) — voxel solvers want volumetric colliders, not planes. [▶ 7:19](https://youtu.be/pz6LDGGeD5A?t=439)
6. **Viscosity ~75** → immediate coiling, slow stretch and fall. [▶ 7:52](https://youtu.be/pz6LDGGeD5A?t=472)
7. Wobble the emitter: keyframe Location X/Y, Graph Editor **Noise** F-modifier (scale up to calm it), copy to Y and offset → folds instead of one pile. [▶ 9:30](https://youtu.be/pz6LDGGeD5A?t=570)
8. Accuracy: Solver substeps **Min 2, Max 5**. [▶ 11:14](https://youtu.be/pz6LDGGeD5A?t=674)
9. **Surface Tension**: start tiny (0.1 → 0.5 → **2**) — tightens tendrils and drips; too much collapses everything into blobs. [▶ 13:28](https://youtu.be/pz6LDGGeD5A?t=808)
10. **nxMesher** ▸ emitter layer, wireframe + **Quads**. Test settings on hard frames (thin snapping strands). **Polygon Size 0.008**, **Radius 0.013** (a bit fat so smoothing can thin it; 0.012 lost particles). [▶ 17:36](https://youtu.be/pz6LDGGeD5A?t=1056)
11. Surface Type **Spheres** (keeps crisp creases); Zhu-Bridson smooths water nicely but artifacts on sharp angle changes. Add smoothing layer **Mean Curvature 100%, 5 iterations** (later **8**) — smooths flats, keeps creases. [▶ 19:28](https://youtu.be/pz6LDGGeD5A?t=1168)
12. Render Cycles GPU: plane aligned with hidden cube floor; three area lights with Track To Suzanne (key strong, soft fill, strong rim). Material: purple base, quite rough, **Subsurface Random Walk** weight 1, radius 1,1,1, scale ~1; **Coat** IOR ~1.4 for wetness. [▶ 21:22](https://youtu.be/pz6LDGGeD5A?t=1282)

## Gotchas
- Too-small mesher radius vs polygon size = flickering/missing mesh pieces.
- SSS/transmission hides some bumpiness — check in render before over-smoothing.

## Newest equivalent
2026.1 beta FLIP/APIC adds **non-Newtonian** settings (Flow Index, **Yield Stress**), **Wall Friction** and a Mixer for per-emitter viscosity; nxMesher gains **Detail Aware** smoothing. For jelly-like solids use **nxMPM**.
