# Fire from a spinning logo spline + Upscaling for detail

- Source: Top Tip Tuesday — Upscale Fire — https://www.youtube.com/watch?v=irQZ4OI7Bhk (2026-02-10)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX) + Redshift
- Goal: design a fire sim at low res with fast playback, then upscale for render with the same shape.

## Steps
1. nxExplosiaFX → Sources: drag the **animated logo spline** (splines, polygons and particles are all accepted). **Voxel Size 2.7**. [▶ 0:33](https://youtu.be/irQZ4OI7Bhk?t=33)
2. Source **Velocity 200%** → fluid inherits the spline's spin and flies off. **Motion Gap Fill 2** (fast source: no stepping, better velocity; slower sim). [▶ 5:40](https://youtu.be/irQZ4OI7Bhk?t=340)
3. Burning: **Burn Rate** up (burn all fuel), **Temperature Production** way down, lower source Fuel, **Smoke Production 0.9**, **Gas Expansion ~7** (calmer), **Ignition Temperature 0**. [▶ 1:59](https://youtu.be/irQZ4OI7Bhk?t=119)
4. Dissipation: smoke up a lot, temperature a bit (shorter flames). [▶ 3:24](https://youtu.be/irQZ4OI7Bhk?t=204)
5. Forces: delete the default **Turbulence** (big swirls should come from the spline velocity); **Vorticity** strong, **mapped to Position Y** (strong at the bottom → fades with height) → crisp flames low, puffy smoke above. [▶ 4:09](https://youtu.be/irQZ4OI7Bhk?t=249)
6. Upscaling: 0 → **2** (≈2× voxels, VRAM-efficient) → **4** (e.g. 136×210×130 → 544×840×520). Shape stays virtually identical; detail appears. Check Memory Stats. Redshift needs longer to load big grids. [▶ 8:30](https://youtu.be/irQZ4OI7Bhk?t=510)

## Gotcha
Don't use upscaling if you need render-time vector motion blur (velocity isn't upscaled) — see "ExplosiaFX MotionBlur".
