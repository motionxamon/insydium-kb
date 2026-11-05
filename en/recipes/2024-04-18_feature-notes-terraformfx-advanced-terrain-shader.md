# Feature notes: TerraformFX Advanced Terrain Shader (TerraformFX 2024.2)

- Source: TerraformFX Sneak Peek – Advanced Terrain Shader, Release Update Coming Soon 2024.2 — https://www.youtube.com/watch?v=SYYZL_rJ3cc (2024-04-18)
- Host / generation: C4D; TerraformFX (tfTerrain operators); shader works in any renderer that supports C4D shaders
- Status: preview of **Fused 2024.2** (9 May 2024)

## What it does
New terrains come with a material whose Color channel holds the **Advanced Terrain Shader**: it mixes the terrain's data channels into black-and-white maps, then maps them onto colour palettes. Visible in the viewport.

## Layers and parameters
- **Terrain Layer**: blends data channels — **Altitude**, **Curvature**, **Ambient Occlusion**, plus large- and small-scale noise and Jitter → B/W map; enable palette colouring to map colours to it.
- **Post-processing** layers, e.g. **Normalize** (full colour range), **Curves** (contrast) and Jitter.
- **Palettes**: Surfaces (sand, rock, lava…) or **Countries** — a global list, each palette sampled from real satellite imagery (demo: Germany for grass).
- **Masking**: a mask terrain layer as a **child** of a colour layer (white = upper layer shows, black = lower); **Preview Current Layer** to inspect one map.
- **tfFlood** outputs a flood mask and difference map; **Add Flooded Layer** auto-creates flood colour + mask in the shader.
- **Agricultural Structures** layer: grid or random fields, count, size, irregularity, **furrows** (plough/crop lines), dirt roads between fields.
- **Terrain Operator** mask layer: link the terrain or any operator and mask by its data (Altitude, Slope) with inverted gradation curves → fields only in low, flat areas.
- **Bake/export** at any resolution: whole texture, all layers or selected layers, 8/16/32-bit TIFF.

## Newest equivalent
Still the TerraformFX texturing route in Fused 2025.4. In Redshift for C4D 2024+, raise the default 128×128 bake size for TerraformFX shaders. See "TerraformFX height map Redshift displacement" (2025-02-04).
