# Feature notes: TerraformFX Advanced Terrain Shader — layers, satellite palettes, masks (Open Beta preview)

- Source: INSYDIUM LIVE! — February 2024 – Open Beta Preview, TerraformFX — https://www.youtube.com/watch?v=Foe7aTVhbYs (2024-02-21)
- Host / generation: C4D; TerraformFX (tf*) — not particles; shown in the open beta, shipped in Fused 2024.2. Works in any renderer that reads C4D shaders (demoed in Standard for instant viewport feedback).
- Goal: realistic, high-detail-looking terrain colour on a low-res tfTerrain without painting or baking.

## Setup
- Material ▸ Color ▸ Texture: INSYDIUM shaders ▸ TerraformFX ▸ **Advanced Terrain Shader**; click the thumbnail and dock the editor (its UI behaves like a plug-in). Drag the **tfTerrain** into its terrain link. New tfTerrains get the shader automatically.
- Photoshop-style **layer stack**, Normal blend by default (top layer hides the rest). Rename layers (base rock, snow…) to stay organised.

## Terrain layer — channels blended into a grayscale map
- **Slope** (threshold — e.g. 44% = steeper than that turns white), **Altitude** (negative = inverted), **Curvature** (convex white / concave black, great for detail), **Ambient Occlusion** (Radius: big = only peaks dark; small = fine channelling; Quality, Bias).
- **Variation** = large global noise with Scale (subtle colour variety across e.g. a meadow); **Jitter** = very fine noise — in small amounts fakes extra resolution and softens hard colour transitions.
- Toggle **Enable Palette Coloring** off to see the grayscale result; on, a palette maps black→white.

## Palettes
- Sampled from real satellite imagery, grouped by **country** (default Spain ▸ Spain 13; India, Congo, United Kingdom…) plus **Surfaces** at the bottom (Rock, Snow, Sand…).
- Right-click ▸ Favorites; **Export** to a C4D Gradient for use elsewhere. Select a sub-range, **Repeat** the palette, **Bias** towards dark/light end; **Normalize** toggle (off = darker, not using the full range).

## Masks and post-processing
- Any layer can be a mask: drag it under another layer as a child. Masks can themselves be masked (nest a second mask under the first).
- Mask sources shown: **Curvature** layer (mode: dents), **Terrain Operator** layer (link to the terrain or a single operator; Altitude / Slope / Curvature / Bumps / Dents), Object layer/mask (from tfDistribute, see part-b), C4D Fields.
- Layer post-processing: Brightness/Contrast, Gamma, **Gradation Curve** (presenter's choice — flip endpoints to invert, crush to add contrast). **Preview Current Layer** solos a layer.

## Examples demoed
1. Snowscape: Terrain layer "base rock" (Surfaces ▸ Rock, dark; less altitude, more curvature, little variation/jitter) → Terrain layer "snow" (Surfaces ▸ Snow) masked by a Curvature layer (dents) with a contrast curve → snow fills hollows, rock pokes through.
2. Yorkshire moorland: base rock → brown moor grass (United Kingdom palette) masked by Terrain Operator **Slope**, curve inverted so steep faces stay rock → **Agricultural Structures** layer (Grid or Random distribution, Count ~150, Irregularity) masked by inverted **Altitude**, with a child **Slope** mask so steep low ground gets no fields.

## Resolution
- Shader **Resolution: Auto** = terrain segments (demo terrain 1000×1000). Raise it (e.g. 1500) for close-ups without remeshing; default max 4000×4000, up to 8000 via settings; costs render time. Can be baked at high res.

## Replaces
Hand-built gradient/layer shaders driven by tf channels or vertex maps; in another renderer, feed the shader into colour, roughness and bump/normal nodes.

## Newest equivalent
Still the current TerraformFX texturing tool (Fused 2024.2 onward; no newer TerraformFX tools listed). With Redshift in C4D 2024+, raise the bake resolution for non-native shaders (default 128×128).
