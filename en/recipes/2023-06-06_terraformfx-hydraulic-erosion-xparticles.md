# Realistic mountains with particle rain erosion (tfNoise layers + tfErosion Hydraulic X-Particles mode)

- Source: Top Tip Tuesday — Hydraulic Erosion — https://www.youtube.com/watch?v=VhWfWcvuV4I (2023-06-06)
- Host / generation: C4D; TerraformFX (tfTerrain, tfNoise, tfErosion filter)
- Goal: carve channels and valley deposits into a noise landscape by simulating rain washing down the slopes.

## Steps
1. **tfTerrain** ▸ Add Operator ▸ **tfNoise** (detail): billowy type, **Octaves 12**, operator **Gain 4 cm**.
2. Second **tfNoise** (mountains): **Turbulence**, Octaves **12**, Scale **120%**, Gain **70**.
3. Add the **tfErosion** filter. Mode default **Thermal weathering** (smooth) → **Hydraulic**: *2D Particle* = fast maths approximation; ***X-Particles*** = full 3D particle sim, more settings, slower, better results — use it.
4. Defaults: **10,000** particles, life **30** frames, rolling downhill. Rain area Everywhere → **Above**, **30 cm** (only peaks get rain).
5. Erosion ▸ **Erode Life** curve: default ramps from 0 at birth; drag the first knot up so particles erode strongly from the start.
6. **Iterations 10** (repeat the sim; progress shown bottom-left) → channels appear.
7. Particles **20,000**; enable **Liquid** so particles interact like water (slower, more realistic).
8. Compare via the erosion operator **Blend** (0 = no erosion, full = eroded).
9. Final push (disable the filter while editing to avoid recalcs): Lifetime **55**, particles **30,000** → much deeper channels.

## Newest equivalent
Same tfErosion in Fused 2025.x; texture the result with the **Advanced Terrain Shader** / curvature channel (Fused 2024.2) and scatter with **tfDistribute**. See "TerraformFX animated terrain trough" (2024-11-19).
