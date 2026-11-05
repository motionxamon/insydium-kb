# Brush-painted mountain ranges (tfTerrain + tfNoise multiplied by TF Grid Generator brush)

- Source: Top Tip Tuesday — TerraformFX Mountain Range — https://www.youtube.com/watch?v=szRmPLMOZq4 (2023-05-23)
- Host / generation: C4D; TerraformFX (no particles); viewport lighting from the 2023-04-18 light-rig tip
- Goal: art-direct exactly where detailed peaks and ridges appear by painting them in.

## Base
Default **tfTerrain** from the INSYDIUM menu; delete the default filters, keep the **tfNoise**. Terrain color off. Segments **500 → 1000** on both axes. Sun (infinite, shadows) + blue low-power ambient light from the light-rig tip.

## Steps
1. **tfNoise** ▸ Properties: turbulence type → **Stupl** (swirly detail).
2. tfTerrain ▸ Add Operator ▸ **TF Grid Generator** — control points that add altitude; noise is computed first, then the grid altitude is added on top.
3. Reset the grid, raise control points to **25 × 25** (X/Z), hide the points.
4. Switch on **Brush mode**: airbrush **Elevate**, more strength, smaller radius; click-hold to raise ridges. Elevate random strength/intensity/scale add natural unevenness.
5. Grid operator **Mode: Add → Multiply** — where the grid is 0 the noise is cancelled, so detail appears only where you painted. Paint/snake ridges to taste (e.g. match a reference image).
6. Fix mistakes procedurally: brush **Smooth** mode to soften a peak, then back to Elevate.
7. Valleys not dead flat: Elevate with a **large radius and very low strength**, dab lightly over flat areas.
8. Final detail: terrain segments up to **3000**.

## Gotchas
In Add mode the painted ridges just sit on top of noise everywhere; Multiply is what makes the brush a mask.

## Newest equivalent
Same TerraformFX workflow today; for rendering detail see the 2024.2 Advanced Terrain Shader / curvature channel (recipe 2025-02-04 for height-map displacement).
