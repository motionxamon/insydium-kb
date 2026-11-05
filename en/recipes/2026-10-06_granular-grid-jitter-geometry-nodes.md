# Break up the hex-grid look of a cached granular sim (Create Point Cloud + Geometry Nodes jitter)

- Source: Top Tip Tuesday — Grid Emission Offset — https://www.youtube.com/watch?v=M2yxZlZQBec (2026-10-06)
- Host / generation: Blender (NeXus for Blender 2026.0) — nxEmitter Hexagonal volume shot, nxFluids SPH Granular, nxCache; Cycles (GPU)
- Goal: a low-count sand-sculpture collapse whose regular hexagonal packing no longer shows at render time.

## Base
Suzanne lifted off the floor. **nxEmitter**: Object ▸ Suzanne, Emit From **Volume**, Emission **Shot**, Mode **Hexagonal** (tight, non-intersecting packing = stable grain start), **Subframe Emit off**, Speed 0. In Hex mode the count comes from the radius: default 0.03 m → ~14k; **0.015 m** → ~100k (demo only — production wants millions).

## Steps
1. Big plane + **nxCollider**: Bounce 0, decent Friction. **nxGravity** default. [▶ 3:18](https://youtu.be/M2yxZlZQBec?t=198)
2. **nxFluids** ▸ SPH ▸ Fluid Type **Granular**; Substeps: **Adaptive off**, **20**; Granular Friction **~70**. [▶ 3:55](https://youtu.be/M2yxZlZQBec?t=235)
3. Preview cracks: emitter Display ▸ Color **Gradient**, parameter **Granular**, Auto Scale off, range **0–20**. [▶ 4:36](https://youtu.be/M2yxZlZQBec?t=276)
4. **nxCache** ▸ Build Cache (~40 s here), then disable solvers/modifiers. [▶ 5:29](https://youtu.be/M2yxZlZQBec?t=329)
5. Emitter ▸ **Export ▸ Create Point Cloud** → auto Geometry Nodes setup (points from particles, particle radius → point radius) + material (Principled BSDF fed by **NeXus Particle Info** color). Cut the color link if you only used it for preview. [▶ 7:25](https://youtu.be/M2yxZlZQBec?t=445)
6. World: **Sky Texture** into Background, strength **~0.05**; rotate the sun to taste. [▶ 7:51](https://youtu.be/M2yxZlZQBec?t=471)
7. In the point-cloud GN tree, before output: **Set Position** ▸ Offset ← **Combine XYZ** of three **Random Value** (float, −1…1, a different Seed each) → **Vector Math ▸ Scale**. Scale 0 = visible grid; a very small value (**~0.01**) breaks the grid while keeping the shape. Group these nodes (Make Group) so one slider remains. Mute (M) to compare. [▶ 13:29](https://youtu.be/M2yxZlZQBec?t=809)
8. Rougher grains: **Instance on Points** with a low-poly **Ico Sphere**, Instance Scale ← the particle radius already used for the points, Rotation ← **Random Rotation**. Optionally vary scale or instance several hand-modelled faceted grains. [▶ 18:08](https://youtu.be/M2yxZlZQBec?t=1088)

## Gotchas
- Viewport particles are display-only; only the exported point cloud renders.
- Jitter works on the cache, so scrubbing/rendering stays near real time.

## Newest equivalent
2026.1 beta **nxMPM** (Sand, or **nxMaterial** ▸ Sand wet preset) is the newer GPU route to sand; the render-side jitter/instancing trick still applies to any point-cloud export.
