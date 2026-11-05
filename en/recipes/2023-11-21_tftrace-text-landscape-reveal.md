# Landscape logo/text that grows on (tfTrace + tfBlur + Snow erosion + masked noise + tfAdjustment with linear field)

- Source: Top Tip Tuesday — tfTrace Text Morph — https://www.youtube.com/watch?v=jQlOjJUVaoI (2023-11-21)
- Host / generation: C4D; **TerraformFX** (tfTerrain operators) + xpJoin
- Goal: text that rises out of a realistic eroded terrain and animates on, fully procedural.

## Base
Fat-font **Text** object, Pitch **−90°** (lie flat), at world origin, Depth **−20** so it extrudes upward; put it inside an **xpJoin** (X-Particles ▸ Utilities).

## Steps
1. **tfTerrain**: Object display off, delete default operators. Size **X 600 / Z 300**, segments **1000 × 500**. Hide the text. [▶ 1:19](https://youtu.be/jQlOjJUVaoI?t=79)
2. **tfTrace** (ray-traced height from objects): object = the xpJoin. [▶ 1:40](https://youtu.be/jQlOjJUVaoI?t=100)
3. Faceted steep edges → **tfBlur** filter, **Gaussian High Quality**, larger radius. [▶ 2:11](https://youtu.be/jQlOjJUVaoI?t=131)
4. Lighting: lower the sun pitch, rotate heading for late-day light. [▶ 2:24](https://youtu.be/jQlOjJUVaoI?t=144)
5. Blend the base: **tfErosion** set **Thermal → Snow**, small radius (default 15), more iterations. [▶ 2:52](https://youtu.be/jQlOjJUVaoI?t=172)
6. Detail: **tfNoise** Turbulence, octaves **5 → 12**, gain **~25**. [▶ 3:18](https://youtu.be/jQlOjJUVaoI?t=198)
7. Mask the noise to the letters: tfNoise ▸ Masking ▸ Shader = **Terrain Operator Shader** (INSYDIUM ▸ TerraformFX), Split/Use Gradient off, operator = the Snow erosion (its Preview tab shows the altitude data). [▶ 3:49](https://youtu.be/jQlOjJUVaoI?t=229)
8. **tfErosion** in **Hydraulic 2D** (fast) for runoff detail. [▶ 4:44](https://youtu.be/jQlOjJUVaoI?t=284)
9. Animate on: **tfAdjustment**, Gain **0**, Masking ▸ **Linear field** — move the field to draw the text on/off. Placed below the hydraulic erosion so scrubbing doesn't re-erode. [▶ 5:09](https://youtu.be/jQlOjJUVaoI?t=309)
10. Global **tfNoise**, **Wavy Turbulence**, octaves 12, gain **~20**. [▶ 5:36](https://youtu.be/jQlOjJUVaoI?t=336)
11. Change the text string any time (re-evaluates erosion). [▶ 5:51](https://youtu.be/jQlOjJUVaoI?t=351)

## Newest equivalent
TerraformFX 2024.2 adds the **Advanced Terrain Shader** (with curvature channel) for texturing this kind of relief.
