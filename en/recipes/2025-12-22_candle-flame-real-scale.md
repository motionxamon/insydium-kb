# Real-scale candle flame (nxExplosiaFX small-scale settings)

- Source: Top Tip Tuesday — Candle Simulation — https://www.youtube.com/watch?v=FPi_MrR0sGw (2025-12-22)
- Host / generation: C4D, Fused 2025.4 (nxExplosiaFX) + Redshift
- Goal: a believable ~15 cm candle flame with occasional gusts.

## Small-scale checklist (defaults are tuned for big scenes)
1. Shrink the domain around the wick; **Voxel Size 0.3 → 0.1**.
2. Sources: whole candle, **Fuel 1.5 Weight by Tag** = wick-tip polygon selection. **Pressure 0** (any pressure blows the flame apart at this scale).
3. Dynamics ▸ default **Turbulence strength ~0.05**, smaller length scale.
4. Simulation ▸ Buoyancy: **Temperature Buoyancy ~0.5** (otherwise a flamethrower).
5. **Temperature Diffusion ~6** → soft, rounded candle-flame shape.
6. Burning: Ignition Temperature 0, Burn Rate ↑, Gas Expansion 0, Smoke Production ~3. Smoke dissipation ↑. Keep the flame slightly *too big* — trim at render time.
7. Gusts: map turbulence strength to **Document Time** (in seconds — frames ÷ fps, e.g. 100/30 = 3.33 to 400/30 = 13.3); draw bumps on the curve, keep a small base value; overall strength ~0.09.
8. Redshift: temperature → **Ramp** in the flame material; move the black knot in to shorten the flame, white knot to lengthen.
