# Making terrains pop in the viewport (tfTerrain detail + two-light daylight rig)

- Source: Top Tip Tuesday — TerraformFX Light Rig — https://www.youtube.com/watch?v=-lLpDIbbDaA (2023-04-18)
- Host / generation: C4D; TerraformFX (no particles); C4D lights, basic viewport display
- Goal: detailed, golden-hour-lit landscape even in the plain viewport.

## Base
INSYDIUM ▸ TerraformFX ▸ **tfTerrain** (default noise + two erosion filters → delete the erosions). Object tab: color gradient off to judge the grayscale.

## Steps
1. Segments **500 → 1000** for more polygons. [▶ 1:02](https://youtu.be/-lLpDIbbDaA?t=62)
2. **tfNoise** ▸ Properties: **Octaves 14** = cheap extra fine detail; noise type **Stupl**; Operator tab **Gain 90**. [▶ 1:50](https://youtu.be/-lLpDIbbDaA?t=110)
3. tfTerrain ▸ Boundaries ▸ **Even Border** → flat sea-level edges, mound in the middle. [▶ 2:10](https://youtu.be/-lLpDIbbDaA?t=130)
4. Sun: C4D Light, orange (golden hour), type **Infinite** (shines along +Z), rotate down until it just grazes the horizon; **Soft Shadows**, shadow **Density 88%**, intensity **130%**. [▶ 3:15](https://youtu.be/-lLpDIbbDaA?t=195)
5. Sky fill: second light, blue, **Ambient Illumination**, low intensity → hazy shadows and scale. [▶ 3:37](https://youtu.be/-lLpDIbbDaA?t=217)
6. Viewport filter: hide lights.
7. Re-enable the terrain color display (altitude-mapped gradient): preset **Alpine → Atacama Desert**. [▶ 4:29](https://youtu.be/-lLpDIbbDaA?t=269)
8. Close-up detail: segments **3000**.
