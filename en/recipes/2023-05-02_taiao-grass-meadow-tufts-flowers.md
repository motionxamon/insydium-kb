# Fast meadow of grass tufts and wildflowers (Taiao Grass + Grass Tuft preset + Preset Browser flowers)

- Source: Top Tip Tuesday — Taiao Grass Meadow — https://www.youtube.com/watch?v=6kNEj1CJbfQ (2023-05-02)
- Host / generation: C4D; Taiao (no particles); C4D materials
- Goal: realistic, light-weight meadow instanced on any ground object.

## Base
tfTerrain with a noise as rolling ground, basic material.

## Steps
1. INSYDIUM ▸ Taiao ▸ **Taiao Grass**; set the terrain as the surface to generate on → a **spline grass layer** appears instantly. Layer settings: density, type Spline / **Polygons** (adjustable blades) / custom object instances.
2. Realism comes from tufts of multiple blades: delete the spline layer and use the **Grass Tuft** preset (a Taiao Plant with a growth point + leaves shaped as blades).
3. Tuft materials: drop two different green materials in its Materials list for color variation.
4. Drag the Grass Tuft into Taiao Grass as a layer. On the tuft layer: clone method **Multi-Instances**, raise **Frequency**, **scale variation ~10%**, heading rotation **360** + **rotation variation 100%** so identical tufts all face differently.
5. Flowers: **Taiao Preset Browser** ▸ Flowers ▸ **Buttercup**; drag it in as another grass layer.
6. Thin flowers on the layer itself — **Frequency ~0.1%** (Global Density would also thin the grass); small scale variation; same 360 + 100% heading trick.
7. Repeat with **Daisy** (scale variation + heading trick).

## Gotchas
Global density affects every layer — control each species with its own layer Frequency.
