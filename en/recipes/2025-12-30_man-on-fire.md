# Running man on fire (nxExplosiaFX: motion inheritance, noise-weighted fuel, upscaling budget)

- Source: Top Tip Tuesday — Man On Fire — https://www.youtube.com/watch?v=jNrr7gboaHo (2025-12-30)
- Host / generation: C4D, Fused 2025.4 (first GPU EFX release) + Redshift
- Goal: flames streaming off a running mocap character.

## Steps
1. Source = **low-poly** running character (render the high-poly). Voxel **2** for draft.
2. Buoyancy **Gravity off**; Forces: add **Wind** 150 with **100% variation** (gusty); +Z default direction (Add Wind Object to rotate it).
3. Sources: **Surface Width 0**, Temperature 1200, more Fuel, Fuel **Weight by Noise** (GPU noise, high strength = high contrast, length scale ~20) → patchy flames; some **Pressure** (pushes fuel off the surface, adds noise); **Velocity from Object Motion 100%** (>100% exaggerates the kick).
4. Burning: Temperature Production ~2000, **Burn Rate** up, Smoke Production 2 (thin wisps), Gas Expansion 3, Ignition Temperature 0.
5. Dissipation: tune temperature dissipation = flame length.
6. Final: Voxel **1.3**, then **Upscaling 3**. Budget from Memory Stats: an RTX 3090 handles ≈ **550 M voxels** (here base 148 M → ×2 = 296 M → ×3 OK, ×4 too much).
