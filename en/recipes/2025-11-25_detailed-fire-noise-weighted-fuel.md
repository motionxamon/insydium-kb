# Detailed fire around a rotating logo (first GPU nxExplosiaFX tutorial)

- Source: Top Tip Tuesday — Detailed Fire — https://www.youtube.com/watch?v=WLqEdMEyd0M (2025-11-25)
- Host / generation: C4D, Fused 2025.4 beta → release (nxExplosiaFX) + Redshift
- Goal: gusty, detailed flames licking around a spinning logo.

## Steps
1. Domain resized, **Voxel 2.5** draft. Sources: logo, Surface emit with larger **Surface Width**; **Temperature 0**, fuel only → set Simulation ▸ Burning **Ignition Temperature 0** (default 600 needs heat). **Pressure 1** (calm). Colliders: same logo. [▶ 0:59](https://youtu.be/WLqEdMEyd0M?t=59)
2. Fuel **Weight by Noise** (67%, length scale 30, animated) → uneven, detailed emission; Fuel ~0.06. [▶ 3:00](https://youtu.be/WLqEdMEyd0M?t=180)
3. Burning: **Burn Rate 10**, Temperature Production ~6000 (taller flames), less smoke, **Gas Expansion 10**. [▶ 4:07](https://youtu.be/WLqEdMEyd0M?t=247)
4. Dissipation: Temperature **~63** (flames reach the top), smoke dissipation up. Smoke Buoyancy slightly negative. [▶ 4:49](https://youtu.be/WLqEdMEyd0M?t=289)
5. Dynamics: Turbulence **Simplex strength 30, Octaves 0**, lower frequency (big gusty swirls); Vorticity default 2 (high values look great at draft res but get fuzzy at fine res) **mapped to Position Y** (strong low, weaker high). [▶ 5:45](https://youtu.be/WLqEdMEyd0M?t=345)
6. Final **Voxel 1** (>300 M voxels), cache ~170 frames (~2 min). [▶ 8:23](https://youtu.be/WLqEdMEyd0M?t=503)
7. Scene file includes "fire basic" and "fire detail" (hollowed, glowing-edge stylised flame) Redshift materials. [▶ 8:59](https://youtu.be/WLqEdMEyd0M?t=539)
