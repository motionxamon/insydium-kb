# Particle color at render time in Cycles and Eevee (nxEmitter Point Cloud export + Geometry Nodes attributes)

- Source: NeXus for Blender Quick Guide — Render Color — https://www.youtube.com/watch?v=Hx0g1V9-HqM (2026-06-15)
- Host / generation: Blender (NeXus for Blender, G3); nxEmitter Export, nxScale, nxPush, nxAttract, nxColor; Cycles + Eevee
- Goal: growing, packing spheres with random gradient colors that stay procedural in the render.

## Base
**nxEmitter** Sphere at minimum size, **Shot 100**, speed 0; Display mode **Spheres**. **nxScale** Range 0 → **0.4** (big variation) over ~8 frames; **nxPush** Distance Mode **Particle Radius**, full strength; **nxAttract** to centre (push/pull motion). **nxColor** Gradient by Parameter → **Random**, gradient e.g. Thermal.

## Steps
1. Emitter ▸ Display: Show Particles off (viewport-only GPU display, not rendered).
2. Emitter ▸ **Export ▸ Point Cloud**, step a frame → point cloud follows the particles with correct radius.
3. Attribute set **Basic** = rotation, velocity, color, radius (switch to **Custom** to pick other particle data). Check names in the Spreadsheet/data view: the color attribute is **"Color"** (capital C) — spelling must match exactly.
4. The auto Geometry Nodes tree already uses a Named Attribute "radius" → point radius.
5. Light: area light, **Track To** the emitter, Normalize off, strength ~150.
6. **Cycles**: points render as clean spheres automatically. New material ("color sphere"); in GN add **Set Material**; in the shader add **Attribute** node "Color" → Base Color. Live: nxColor gradient edits update the render.
7. **Eevee** draws points as diamonds → instance geometry: GN **Instance on Points** with a hidden smooth UV sphere (Object Info), pipe the radius attribute into **Scale**.
8. Instances render black until the shader Attribute node type is changed from **Geometry** to **Instancer**.

## Newest equivalent
NeXus 2026.1 beta adds a Blender **Particle Info node** for shaders/Geometry Nodes, which reads particle data directly.
