# Paving terrain → exported height map → Redshift render-time displacement (TerraformFX noise operator + Redshift Displacement)

- Source: Top Tip Tuesday — Custom Displacement Maps — https://www.youtube.com/watch?v=ZEh3icEFM_g (2025-02-04)
- Host / generation: C4D; TerraformFX (terrain + Noise operator) + Redshift; no particles
- Goal: a detailed paving ground plane without heavy geometry, displacement matched to the terrain.

## Steps
1. TerraformFX terrain + **Noise operator**; turn fractal detailing off while shaping. [▶ 0:22](https://youtu.be/ZEh3icEFM_g?t=22)
2. Noise type **Simplex → Cellular**, raise **Jitter** (Voronoi cells); return type **Cell → Distance Sub** for bevelled edges, not flat cliffs. [▶ 0:40](https://youtu.be/ZEh3icEFM_g?t=40)
3. Warp ▸ fractal warping up for irregular stones. [▶ 0:50](https://youtu.be/ZEh3icEFM_g?t=50)
4. Scale tool trick: Model mode scales altitude; **Object mode scales the noise itself**. Set operator **Gain to a round 25** and note it. [▶ 1:33](https://youtu.be/ZEh3icEFM_g?t=93)
5. Terrain object: resolution **4000 × 4000** (= map size). Preview tab ▸ **Altitude** map ▸ **Write File**. [▶ 2:39](https://youtu.be/ZEh3icEFM_g?t=159)
6. Disable the terrain; use a very low-poly plane (only ~10 segments). [▶ 2:56](https://youtu.be/ZEh3icEFM_g?t=176)
7. Redshift material: **Texture** node (load the altitude map) → **Displacement** node → Output Displacement; raise roughness. [▶ 3:26](https://youtu.be/ZEh3icEFM_g?t=206)
8. Plane ▸ **Redshift Object tag ▸ Geometry**: Override, Enable Tessellation, Smooth Subdivision off, **Displacement on**. [▶ 4:46](https://youtu.be/ZEh3icEFM_g?t=286)
9. Tag ▸ Displacement: **Max Displacement = Displacement Scale = 25** (same as the gain) → matches the terrain exactly. [▶ 5:11](https://youtu.be/ZEh3icEFM_g?t=311)

## Gotchas
The match only works if the Redshift scale equals the operator gain — keep it a round number.
