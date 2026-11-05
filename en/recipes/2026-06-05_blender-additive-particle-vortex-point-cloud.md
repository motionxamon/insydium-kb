# Additive particle vortex rendered as a point cloud (nxEmitter Disc Edge Only, nxTurbulence, nxRotate + Sphere falloff, Point Cloud export)

- Source: NeXus for Blender Official Training — Particle Vortex — https://www.youtube.com/watch?v=SLUkMBqGfZg (2026-06-05)
- Host / generation: Blender (NeXus for Blender, G3 nx objects in the NeXus Hierarchy, N-panel); render in Cycles (GPU) or Eevee via Geometry Nodes points
- Goal: millions of tiny glowing particles swirling out of a ring into a milky, nebula-like vortex with white-hot overlaps.

## Steps
1. NeXus panel ▸ Hierarchy ▸ **+ nxEmitter** (default square, fires +Y); delete the floor plane. [▶ 0:48](https://youtu.be/SLUkMBqGfZg?t=48)
2. Emitter: Shape **Disc**, enable **Edge Only** (thin emission line = finer detail), Angle **90°** so particles fire perpendicular to the edge. [▶ 1:13](https://youtu.be/SLUkMBqGfZg?t=73)
3. Birth Rate **100,000/s** for set-up; untick **Full Lifespan**, Lifespan **130 F**, Variation **30 F** (feathered, organic die-off). [▶ 2:08](https://youtu.be/SLUkMBqGfZg?t=128)
4. Display tab: draw size 3 → **1** (only the viewport point size, not the simulation radius); keep it small for this look. [▶ 3:56](https://youtu.be/SLUkMBqGfZg?t=236)
5. **+ nxTurbulence**: one default noise layer (INSYDIUM's own Voronoise-type noise; other noise types and stackable blended layers available). Strength **7**, Scale **100%** (20% = ultra-fine, larger = big swirls), raise Frequency for livelier motion. [▶ 5:21](https://youtu.be/SLUkMBqGfZg?t=321)
6. nxTurbulence **Axis Direction Scale**: Y **0** flattens the sim completely; **0.3** keeps a little depth while increasing overlaps (better additive veins). [▶ 5:57](https://youtu.be/SLUkMBqGfZg?t=357)
7. **+ nxRotate**: Rotate Speed 75° first, later **110°**. [▶ 9:40](https://youtu.be/SLUkMBqGfZg?t=580)
8. nxRotate ▸ Falloff tab ▸ **Create/Add** → switch Box to **Sphere**, scale it up, Offset ≈ **−2** for a long ramp — strong spin near the birth ring, then only turbulence outside. [▶ 9:37](https://youtu.be/SLUkMBqGfZg?t=577)
9. Emitter ▸ **Export tab ▸ Point Cloud** (Basic data = position is enough); turn off Show Particles in Display. [▶ 11:03](https://youtu.be/SLUkMBqGfZg?t=663)
10. The point cloud appears under the emitter in the Outliner with an auto Geometry Nodes tree (Named Attribute radius → points). Break the radius link and set Radius **0.003** by hand. [▶ 12:55](https://youtu.be/SLUkMBqGfZg?t=775)
11. Birth Rate → **1,000,000/s** (≈4–5 M live particles once they start dying). [▶ 13:59](https://youtu.be/SLUkMBqGfZg?t=839)
12. GN: **Set Material** node. Shader: delete Principled, **Emission** (green, low value) **+ Transparent BSDF** via **Mix Shader**, factor mostly toward transparent; Emission Strength 50 → **20–30** for white-hot overlaps. [▶ 15:09](https://youtu.be/SLUkMBqGfZg?t=909)
13. Render: **Cycles, GPU Compute** (instances real spheres at render time); Eevee shows the points as quads but works. [▶ 17:27](https://youtu.be/SLUkMBqGfZg?t=1047)
14. Banding/stepping from strong velocities: NeXus settings ▸ **Document ▸ Substeps 2** (raise until the stepping is gone). [▶ 19:27](https://youtu.be/SLUkMBqGfZg?t=1167)

## Gotchas
- Display size ≠ particle radius; the GN point radius is independent once the Named Attribute link is cut.
- Hide the modifier/falloff/emitter helpers before rendering.

## Newest equivalent
Same objects in NeXus 2026.1 beta (Blender + C4D). 2026.1 adds 16 nxFalloff modes (e.g. Torus/Cylinder suit a ring emitter) and per-layer falloff lists; nxWarp (Helix/Twist) is another way to shape the swirl. Particle Info node (Blender) can feed per-particle data to the shader.
