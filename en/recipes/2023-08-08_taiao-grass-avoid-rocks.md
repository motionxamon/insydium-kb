# Patchy grass on a terrain that culls or wraps around rocks (toGrass Avoid Objects Cull/Repel, tfRock)

- Source: Top Tip Tuesday — toGrass Avoid — https://www.youtube.com/watch?v=HiRKNNjygt0 (2023-08-08)
- Host / generation: C4D; Taiao (toGrass) + TerraformFX (tfTerrain with noise, tfRock)
- Goal: dense, length-varied grass only on the top of a 3D terrain, kept away from or bending around standing stones.

## Steps
1. INSYDIUM ▸ Taiao ▸ **toGrass**, drag the **tfTerrain** in as the generation object.
2. It also grows on the sides and underside: grass layer ▸ Generation: **Slope Max 89°** (removes vertical walls), **Height Min 0.1%** (removes the bottom).
3. Geometry tab: Spline → **Polygon object**; Width **0.5**, much taller height, a few more segments, some **Bend variation**.
4. Object tab top controls: use a **texture source** for **Length** (not density) → **Noise** shader; raise Low Clip / lower High Clip for contrast, then set its black to grey so dark areas are shorter but not stubs.
5. Density **100 → 300**.
6. Grass layer ▸ Materials: drag in two materials → randomly distributed per blade.
7. Rocks: INSYDIUM ▸ TerraformFX ▸ **tfRock**; copy the landscape material (slightly less brown); scale its size in Y for a standing-stone look; sink it into the ground.
8. toGrass ▸ **Avoid Objects**: drop the tfRock in; raise **Distance** to widen the gap. Turn off the avoid-object display to check.
9. Mode **Cull** (blades removed) vs **Repel** (edge blades bend and wrap round the stone — best with a small distance).

## Newest equivalent
Same Taiao tools in Fused 2025.x; Fused 2024.2 added Taiao growth-point scatter for more control over distribution. No NeXus replacement.
