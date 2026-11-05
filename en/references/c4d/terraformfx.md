# TerraformFX (C4D, part of INSYDIUM Fused)

Source: docs.insydium.ltd/terraformfx/* (Fused 2025, checked 2026-11-03). Paraphrased.

## Concept
- **tfTerrain** = parent object (size, segments — Lock Size/Segments Ratio, Display gradient preset Alpine, Tessellation Quads, Planet Radius for curvature, Set Selection adds top/bottom selection tags, Subdivide Bottom only if deforming/simulating). New terrains start with **tfNoise → tfGrid → tfFlood → tfErosionHydraulic** (delete what you don't need).
- Children = **operators**, evaluated in hierarchy order, all live/non-destructive.
  - **Generators** (create height): tfNoise (Maxon 14 noises, default Turbulence; Advanced Perlin/Simplex/Gabor/Cellular…; Octaves, Seed, Scale, Normalize, Warp), tfGradient, tfGrid (sculpt with **tfBrush**), tfFormula, tfGroup, tfShader, **tfSpline** (Stroke = ridge/road bed, Fill = plateau; Resample!), **tfTrace** (turn any 3D mesh into terrain by raycast — logos/letters as mountains).
  - **Filters** (modify height): tfAdjustment, tfBlur, tfClamp, tfCurve, tfDistribute, **tfErosion** (Hydraulic / Coastal / Snow / Thermal Weathering / Morphological), tfFlood (water level), tfFold, **tfHighpass** (keep fine detail — Radius 5%, Attenuate; "precise landscapes" Top Tip), tfSharpen, tfMirror, tfPath, tfQuantize (terraces), **tfRiver** (Settle Spline / Perlin Worm / secondary streams; Depth, Width, Inertia; Downhill Flow), tfWarp (brushable).
- **Operator tab (shared):** Blend 0–100%; generators: blend modes Normal (lowest generator overrides), Add, Subtract, Multiply (Gain 1), Lowest/Highest, Phoenix; Gain, Offset.
- **Masking tab (every operator):** Altitude min/max + soften, Slope min/max + soften, **C4D Fields** (Box/Linear/Radial; 3D Sampling), Shader (enable Tile + Seamless). Time Dependent = recompute every frame (animated terrains, "Terrain Flow" rolling landscape Top Tip).
- Preview tab: altitude/slope/difference maps per operator or global; **export maps as TIFF**.

## Erosion
- **tfErosionHydraulic** — 2D Particles (fast, heightmap) or 3D **X-Particles** mode (slower, deeper channels with more Iterations). Defaults: Particle Count 10 000, Radius 3 cm, Evaporation 1%, Max Erosion 50 cm (hard cap), Rain Everywhere / above / below / shader areas. Raise **Inertia** for defined channels. Change one setting at a time.
- **Thermal Weathering** — rock slides downhill: Iterations 5, Threshold slope, Sediment Transport/Deposit.
- Coastal (shorelines at flood level), Snow (accumulation), Morphological.

## Objects & utilities
- **tfRoad** — road along spline (Rail for banking, Width/Height, Auto Banking, Clone Along Road for lamps/barriers; profile Y faces rail).
- **tfRock** — procedural rocks or rockify a custom mesh (Basic Shape, Detail, Contrast — high cracks surface, Mutate).
- **tfRiverExport** — tfRiver points → segmented spline (for water meshes/particles).
- Commands, Presets, Grid Monitor, Preferences.

## Shading
- **Advanced Terrain Shader** — single shader with layer tree: layers combine slope, altitude, curvature, AO and noise into a grayscale that samples a color palette; siblings blend bottom-up; children mask parents. Link the tfTerrain; one material per terrain. **Redshift (C4D 2024 default) bakes standard shaders at 128×128 → raise bake resolution in Redshift settings.** Caches not saved → rebuild on scene open.
- **GradientUV Shader**, **Terrain Color Palette** (1 450+ presets), **Terrain Operator Shader** (isolate a single operator's map in a material), Ambient Occlusion & Curvature shaders, New Default Terrain Material.
- Combine with X-Particles: emit snow/trees from the terrain with Topology (height/slope) limits; xpScatter for vegetation; Taiao toGrass.
