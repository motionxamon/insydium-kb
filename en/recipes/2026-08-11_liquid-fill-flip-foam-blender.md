# Liquid Fill preset with FLIP/APIC, mesh and separate foam emitter (NeXus Liquid Fill, nxFoam, nxMesher)

- Source: Top Tip Tuesday — Liquid Fill — https://www.youtube.com/watch?v=vglrHSL-uc4 (2026-08-11)
- Host / generation: Blender (NeXus for Blender 2026.0) — Liquid Fill preset: nxEmitter (Liquid Fill), nxFluids FLIP/APIC, nxMesher, nxFoam, nxCollider, nxWind
- Goal: a quickly set-up tank / filled-object liquid with surface foam ready for render.

## Steps
1. NeXus ▸ **Liquid Fill** → domain, nxGravity, and a folder with emitter, **nxFluids**, **nxMesher (off)**, group "foam" and **nxFoam (off)**. Plays as a tank out of the box. [▶ 0:59](https://youtu.be/vglrHSL-uc4?t=59)
2. Optional motion: **nxWind** ▸ **Von Karman**, strength ~2.5, lots of variation, raise Turbulence ▸ Friction Velocity. [▶ 1:36](https://youtu.be/vglrHSL-uc4?t=96)
3. Emitter: Object = domain, Volume, Emission Type **Liquid Fill**, references the nxFluids solver; **Resolution** (50 → 70/75) and **Fill Level** (30%, Show Fill Level). Resolution sets the solver voxel size **and** the particle count so particles-per-voxel stays right (wrong ratios collapse the liquid). Check via nxFluids Display ▸ voxel grid Back Only. [▶ 4:31](https://youtu.be/vglrHSL-uc4?t=271)
4. Solver type is linked: switching the emitter to **APIC** sets nxFluids to APIC too. [▶ 7:19](https://youtu.be/vglrHSL-uc4?t=439)
5. Fill another shape: swap the emitter object for a UV sphere; add **nxCollider** on it with **Inside normals**, Bounce 0, Friction 0 to contain it. [▶ 7:02](https://youtu.be/vglrHSL-uc4?t=422)
6. Mesh: enable **nxMesher** (pre-linked; auto polygon size ~0.027); raise Scale to **300** to close holes; Smoothing layer **Mean Curvature**, iterations **5** (10 loses droplets). Export ▸ **Transfer Velocity** for motion blur. [▶ 18:41](https://youtu.be/vglrHSL-uc4?t=1121)
7. Foam: enable **nxFoam**; solver type must match (**APIC**); Simulation Bounds = the sphere. Emitter display Points size 1 to see white water. [▶ 19:12](https://youtu.be/vglrHSL-uc4?t=1152)
8. Use only the **Surface Foam** layer; **Spawn After Age** default **30** frames → **4** for early foam. [▶ 13:44](https://youtu.be/vglrHSL-uc4?t=824)
9. Separate foam: instead of Output Group "foam", create a second emitter "foam", set Birth Rate **0**, and set the foam layer's **Output Emitter** to it (one emitter per white-water type possible). [▶ 15:59](https://youtu.be/vglrHSL-uc4?t=959)
10. Render: foam emitter ▸ Export ▸ **Create Point Cloud** (motion blur works automatically); liquid = mesher. [▶ 17:56](https://youtu.be/vglrHSL-uc4?t=1076)

## Newest equivalent
2026.1 beta adds non-Newtonian FLIP, Wall Friction, Mixer, nxMesher **Blend into Ocean** and **nxOcean** FLIP coupling.
