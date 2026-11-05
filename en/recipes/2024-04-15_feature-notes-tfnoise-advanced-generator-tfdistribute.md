# Feature notes: tfNoise Advanced Noise generator and tfDistribute (TerraformFX 2024.2)

- Source: TerraformFX Sneak Peek – Release Update Coming Soon 2024.2 — https://www.youtube.com/watch?v=qBAJGCLYdQo (2024-04-15)
- Host / generation: C4D; TerraformFX (tfTerrain operators)
- Status: preview of **Fused 2024.2** (9 May 2024)

## tfNoise ▸ Advanced Noise generator (old Maxon noises still available)
- A base **Noise Type** (translate/scale), then:
  - **Fractal sampling** adds detail: **FBM** (rocky), **Billow**, **Ridged** (sharp peaks); fewer Octaves → back to the base noise.
  - **Warping** warps the base noise using fractal sampling too; Strength gives rocky areas vs flat grassland. Fractal + warp together = eroded canyons.
  - A second warp option warps the fractal used in sampling as well (strong = swirls, low = subtle shaping).
- **Cellular** type: Jitter (Voronoi shapes); Return Type **Distance** + fractal warping = large detailed dunes; other return types = rock formations or paving; cycle seeds.
- **Macro** types (few parameters, quick landscapes): **Prairie** and **Mixed Macro**.
- **Gabor** type: custom surfaces (moon, rock textures).
- Every example is one tfNoise; mix with the other TerraformFX operators.

## tfDistribute (new filter) — rocks, shrubs, trees, custom objects
- Base shapes **Flat, Round, Cone, Spike**; Deformation and Structure for detail (distance detailing, not hero assets); elevation, size, variation; counts like 75,000 calculate fast.
- Restrict with filters: **Altitude** (with softening) and **Slope** (e.g. not on the flattest or steepest parts). Second tfDistribute with Cone, low deformation = trees.
- With the terrain material: **Add Rock Layer / Add Tree Layer** create editable material + mask layers automatically.
- **Custom objects from bitmaps** (e.g. a logo, 500 copies); **Surface** or **Intersect** placement (objects jut out as cliffs).
- Generates **object masks and object IDs** for rendering and particle sims.

## Newest equivalent
Shipped in Fused 2024.2 and still current in Fused 2025.4; see "tfNoise cellular sci-fi panels" (2025-06-12).
