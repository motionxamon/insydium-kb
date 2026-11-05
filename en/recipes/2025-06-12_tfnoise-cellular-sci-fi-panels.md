# Sci-fi panel / cityscape terrain (TerraformFX tfNoise Advanced, Cellular + Manhattan)

- Source: Bite-Sized — Sci-Fi Panels — https://www.youtube.com/watch?v=IsjrmNr63A4 (2025-06-12)
- Host / generation: C4D; TerraformFX (tfTerrain + tfNoise operator, Advanced noise mode)
- Goal: blocky, angular height patterns that read as sci-fi hull panels or a city grid.

## Steps
1. INSYDIUM menu ▸ **tfTerrain**; delete the default operators and material.
2. Add Operator ▸ **tfNoise** — it defaults to the newer **Advanced** mode (Maxon noises still available).
3. Noise type **Simplex → Cellular**; Distance function **Euclidean → Manhattan**.
4. Lower **Octaves**, lower **Lacunarity** (bigger features), tune **Persistence**; **Scale 250**.
5. **Jitter 0** = square blocks; raise Persistence for varied heights, Lacunarity for nested detail.
6. Raise Jitter for angular, irregular panels; **Gain** shifts the height offset; more Octaves = more detail.
