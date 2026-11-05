# Water clinging to an object rising out of a FLIP pool (nxSticky)

- Source: Top Tip Tuesday — Sticky FLIP — https://www.youtube.com/watch?v=brhdU9ibnow (2026-01-06)
- Host / generation: C4D, Fused 2025.4+ (nxFluids FLIP, nxSticky, xpCollider)
- Goal: lift a logo out of a tank; water sticks to it and drips off over time.

## Steps
1. Tank: nxGravity, nxFluids **FLIP**, Voxel 7, domain sized to the tank. Emitter Box, **Shot – Regular** (even per-voxel distribution) radius 1.5 → add **Jitter XY 1.5 / Z 1.5** (= radius) to break the grid look that would show in the mesh. [▶ 0:44](https://youtu.be/brhdU9ibnow?t=44)
2. Logo: **xpCollider tag**, Bounce 0, Friction 0. FLIP Solver Accuracy: substeps **Min 2 / Max 4**. [▶ 2:08](https://youtu.be/brhdU9ibnow?t=128)
3. **nxSticky**: Object = the logo; **Inherit Speed off** (released drops fall straight down). [▶ 3:03](https://youtu.be/brhdU9ibnow?t=183)
   - **Range** = search distance — keep low (15 cm) for speed (300 cm would test ~all 250 k particles).
   - **Tolerance** = actual stick distance — keep low (10 cm); high values make particles teleport onto the surface.
   - **Probability** < 100% for randomness.
   - **Sticky Time** 60 F + **Sticky Falloff** curve = staggered release. Shorter time = faster shedding; long time (150) with an immediate falloff = long dripping streams.
