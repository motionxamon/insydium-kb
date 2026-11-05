# Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)

- Source: Black Friday Breakdown — Particle Splash — https://www.youtube.com/watch?v=t-1ZIIRF8Jg (2023-11-20)
- Host / generation: C4D; G2 — xpEmitter + GPU **nxGravity / nxFluids (SPH)**, CPU xpCollider/xpJoin/xpCache; TerraformFX + MeshTools; Cycles 4D render
- Goal: several separately simmed coloured splashes crashing through rocks over pentagon steps on a sand-covered slope.

## Base
tfTerrain with a downhill slope (500 segments, kept for render), pentagon steps = Cylinders with 5 rotation segments, 4 **tfRock** objects as invisible splash "bashers".

## Steps
1. Optimise collision geo: copy the terrain → **mtRemesh** (Delaunay), raise Edge Length until shape just holds → C, keep only the polygon object ("terrain sim"); delete polygons outside the camera view. tfRocks Subdivisions → 0.
2. **xpCollider** tag on terrain sim (Bounce 0, Friction 0). Steps and rocks each go in an **xpJoin** (one collider tag per join); rocks Bounce 10, Friction 5. Display colour black for all colliders.
3. Emitter: Shape **Box** (thin, low), tilted towards the rocks, Direction **−Z**; Emission **Shot**, Shot type **Hexagonal**; Radius 7 (HUD ≈16,000 particles for draft).
4. **nxGravity** 981 → **60** (weak gravity fakes slow motion). **nxFluids SPH**, Substeps 5.
5. Viewport colour: Gradient Parameter by **Speed**, 0–120 (later 140); Square display, smaller size factor.
6. Shape the splash: taller emitter = more particles = bigger force; nxFluids **Viscosity 15**, **Surface Tension 10** (bigger-scale water with beaded tendrils); emitter Speed 150 → **100**. Move/rotate rocks to open gaps → sheets and squirts of liquid.
7. Final res Radius **0.5** (count grows very fast) → **xpCache** (external files, Compress on build) — 35 s in the demo.
8. Next splash: duplicate the emitter (delete its cache tag), reshape/move, new colour, disable the cached emitter; Build Cache ▸ **Continue** caches only the new one (Override re-sims all; with both live they interact).
9. Sand: colliders off, new emitter "sand" from the render terrain (Polygon Area), Shot, Random, Speed 0, **1,000,000**, Simulate mode (born at frame 0), Dots display; emitter **Falloff Sphere** radius 300 → feathered density. Cache **one frame**, then cache tag playback override **Hold** and restore the 90-frame range.
10. Cycles 4D: two soft boxes (key 20, rim 3, warm tint), protected camera. Terrain: Principled BSDF, black base, tune Specular/Roughness. **Cycles 4D Instance tag** on each emitter (sand: fewer segments, Size 50%, Size Variation 60, Size Multiplier 20 → 10; splashes ~70%). Particle material = **Translucent BSDF** + black Principled (specular) via an **Add Shader**; orange/blue copies per splash. Steps: rough specular Principled + Cylinder **Fillet** caps for edge highlights. Hide rocks. DOF on the camera tag, focus on a step.

## Gotchas
- SPH: every particle in the fluid sim must share the same radius or it goes unstable.
- Separately cached splashes pass through each other — sim together if the camera sees them overlap.
- Beauty wants ~4 million smaller sand grains; ~6–7 layered splashes.

## Newest equivalent
Fused 2025.4: nxFluids **FLIP/APIC** with surface-tension tendrils, **nxSplash** for crowns and GPU **nxMesher** if meshing. NeXus 2026.1 beta (G3): nxEmitter + **nxCollider** objects + **nxCache** (frame range); in Blender the same via NeXus Hierarchy.
