# Fast meadow of grass tufts and wildflowers (Taiao Grass + Grass Tuft preset + Preset Browser flowers)

- Source: Top Tip Tuesday — Taiao Grass Meadow — https://www.youtube.com/watch?v=6kNEj1CJbfQ (2023-05-02)
- Host / generation: C4D; Taiao (no particles); C4D materials
- Goal: realistic, light-weight meadow instanced on any ground object.

## Base
tfTerrain with a noise as rolling ground, basic material.

## Steps
1. INSYDIUM ▸ Taiao ▸ **Taiao Grass**; set the terrain as the surface to generate on → a **spline grass layer** appears instantly. Layer settings: density, type Spline / **Polygons** (adjustable blades) / custom object instances. [▶ 0:58](https://youtu.be/6kNEj1CJbfQ?t=58)
2. Realism comes from tufts of multiple blades: delete the spline layer and use the **Grass Tuft** preset (a Taiao Plant with a growth point + leaves shaped as blades). [▶ 1:40](https://youtu.be/6kNEj1CJbfQ?t=100)
3. Tuft materials: drop two different green materials in its Materials list for color variation. [▶ 2:18](https://youtu.be/6kNEj1CJbfQ?t=138)
4. Drag the Grass Tuft into Taiao Grass as a layer. On the tuft layer: clone method **Multi-Instances**, raise **Frequency**, **scale variation ~10%**, heading rotation **360** + **rotation variation 100%** so identical tufts all face differently. [▶ 3:05](https://youtu.be/6kNEj1CJbfQ?t=185)
5. Flowers: **Taiao Preset Browser** ▸ Flowers ▸ **Buttercup**; drag it in as another grass layer. [▶ 3:59](https://youtu.be/6kNEj1CJbfQ?t=239)
6. Thin flowers on the layer itself — **Frequency ~0.1%** (Global Density would also thin the grass); small scale variation; same 360 + 100% heading trick. [▶ 4:40](https://youtu.be/6kNEj1CJbfQ?t=280)
7. Repeat with **Daisy** (scale variation + heading trick). [▶ 5:32](https://youtu.be/6kNEj1CJbfQ?t=332)

## Gotchas
Global density affects every layer — control each species with its own layer Frequency.
