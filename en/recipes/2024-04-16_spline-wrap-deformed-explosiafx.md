# Bend a straight fire sim around a helix (xpExplosiaFX + C4D Spline Wrap)

- Source: Top Tip Tuesday — Deforming Smoke and Fire — https://www.youtube.com/watch?v=RkAB9dD0X5k (2024-04-16)
- Host / generation: C4D; CPU **xpExplosiaFX** (pre-nxExplosiaFX); Cycles 4D render
- Goal: simulate a simple linear column of fire, then deform the whole volume with a C4D deformer into a helix glass tube.

## Steps
1. **xpExplosiaFX** Solver size **50 × 1300 × 50** (tall, thin). Container options: **block all sides except the top**.
2. Fuel source: sphere r 5 cm at the bottom + **xpExplosiaFX Source tag**: Solid off (fills volume), Heat 200, Fuel 200, add **Pressure** to push gas up faster.
3. Display: mode **Grid** (voxel view), level of detail 200.
4. Simulation: Sim speed raised (value garbled), **gravity stronger** (multiplies buoyancy), smoke buoyancy around −10.
5. Burning model **Custom**: Burn Rate 20 (flames live higher), **Ignition Heat 0**, Smoke from Heat 1.5.
6. At frame 0, add a **Spline Wrap** deformer as a child of the xpExplosiaFX object, spline = Helix, axis **+Y**. The cached/simulated volume now follows the helix; Helix angles can be keyframed.
7. Copy the Spline Wrap under a cylinder (glass material) so the tube matches.
8. Material: Cycles 4D ▸ **xpExplosiaFX presets ▸ Burn** on the domain; render in Cycles real-time preview.

## Gotchas
- Strong deformation stretches voxels — use more voxel detail the more you bend it.

## Newest equivalent
**nxWarp** (2026.1 beta) warps smoke directly with Helix / Path / Bend / Twist cages; GPU **nxExplosiaFX** (Fused 2025.4) for the sim itself.
