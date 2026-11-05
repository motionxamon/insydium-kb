# Paving terrain → exported height map → Redshift render-time displacement (TerraformFX noise operator + Redshift Displacement)

- Source: Top Tip Tuesday — Custom Displacement Maps — https://www.youtube.com/watch?v=ZEh3icEFM_g (2025-02-04)
- Host / generation: C4D; TerraformFX (terrain + Noise operator) + Redshift; no particles
- Goal: a detailed paving ground plane without heavy geometry, displacement matched to the terrain.

## Steps
1. TerraformFX terrain + **Noise operator**; turn fractal detailing off while shaping.
2. Noise type **Simplex → Cellular**, raise **Jitter** (Voronoi cells); return type **Cell → Distance Sub** for bevelled edges, not flat cliffs.
3. Warp ▸ fractal warping up for irregular stones.
4. Scale tool trick: Model mode scales altitude; **Object mode scales the noise itself**. Set operator **Gain to a round 25** and note it.
5. Terrain object: resolution **4000 × 4000** (= map size). Preview tab ▸ **Altitude** map ▸ **Write File**.
6. Disable the terrain; use a very low-poly plane (only ~10 segments).
7. Redshift material: **Texture** node (load the altitude map) → **Displacement** node → Output Displacement; raise roughness.
8. Plane ▸ **Redshift Object tag ▸ Geometry**: Override, Enable Tessellation, Smooth Subdivision off, **Displacement on**.
9. Tag ▸ Displacement: **Max Displacement = Displacement Scale = 25** (same as the gain) → matches the terrain exactly.

## Gotchas
The match only works if the Redshift scale equals the operator gain — keep it a round number.
