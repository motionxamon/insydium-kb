# Living, flowing terrain trough (TerraformFX: animated tfNoise scale + tfGradient + cellular furrows + tfBlur)

- Source: Top Tip Tuesday — Terrain Flow — https://www.youtube.com/watch?v=c_lxDUv1lis (2024-11-19)
- Host / generation: C4D; **TerraformFX** (tfTerrain, tfNoise, tfGradient, tfBlur) + Redshift
- Goal: shot from the 2024 Black Friday advert — an undulating canyon that keeps morphing.

## Steps
1. **tfTerrain** (start 1000×1000 segments for speed).
2. **tfNoise ▸ Advanced**: base **Perlin**, scale 130, gain ~100 cm; fractal **Billow**, more octaves, persistence ~85, lower lacunarity; **Fractal warping ~90**.
3. Animate base scale **130 → 220** over the shot, set keys to **Linear** (Show Track ▸ linear) → constant flowing motion.
4. Trough: **tfGradient ▸ Linear**, gain 220, rotate 90° Y to face camera, width 2000; edit the **profile spline** into a U (add a low point in the middle).
5. Furrows: second tfNoise **Cellular**, jitter 100 %, fractal warping on, **negative gain −20** (cuts in).
6. Raise terrain segments to **3000×3000**; **tfBlur ▸ Gaussian** to smooth facets.
7. Redshift: a **Curvature** node colors the furrows two-tone; Sun + Sky + DOF.
