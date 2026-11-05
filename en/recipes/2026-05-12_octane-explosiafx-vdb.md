# Render nxExplosiaFX in Octane via OpenVDB

- Source: Top Tip Tuesday — Octane EFX — https://www.youtube.com/watch?v=gfcEhBMSgkI (2026-05-12)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX) + Octane
- Goal: smoke and fire in Octane that matches the EFX viewport.

## Steps
1. **xpCache** → EFX Format **OpenVDB**; channels **Smoke (density) + Temperature** only. Velocity only if you need motion blur or advection (≈3× file size).
2. Octane **VDB Volume** object → VDB tab → pick the first file → **Calculate** (finds all frames). It reports grid 0 = density, grid 1 = temperature; Grid mapping auto-assigns Absorption/Scatter = density, Emission = temperature.
3. **Flip Z**: VDB Volume Coordinates → Scale Z = −1 (axis convention differs from EFX).
4. Medium: switch preset **Fog → Fire**; edit in the Octane node editor:
   - **Texture Emission Power** ≈ 0.01 (default blows out); 0.1 = brighter, lights the floor.
   - **Volume Gradient** → Emission Ramp: set **Max ≈ 6500** (your sim's max temperature; default 35 clamps everything yellow). Add a **black knot** at the cool end → no glow in burnt-out smoke; use the "flame" preset or any color (violet = magic fire).
   - Volume Medium **Volume Step % ≈ 7** (lower = denser/more detail, slower).
5. Thin wispy smoke: new Volume Gradient (black→white, Max 1) → **Absorption Ramp + Scattering Ramp**; turn **Invert Absorption off**; move the black knot to ~0.5 subtly.

## Rule
Find the real temperature max of your sim (EFX Display ▸ Flame Emit Above T test) and type it into the gradient Max.
