# Build a Redshift material for nxExplosiaFX that matches the viewport

- Source: Top Tip Tuesday — Redshift ExplosiaFX — https://www.youtube.com/watch?v=udP2NcPK3xw (2026-07-21)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX) + Redshift
- Goal: correct smoke density and fire temperature ranges in Redshift, plus ramp controls for wispy smoke and flame tails.

## Measure first (EFX Display ▸ Flame)
- **Flame Emit Above T** = 1000 by default → fire starts at 1000.
- Raise it until flames disappear → max temperature (here ≈3000 → use 3500).
- EFX Simulation ▸ **Ambient Conditions** has ambient temperature **300** — causes a red glow over the whole domain if not clipped.

## Node tree (Redshift material on the EFX object)
```
Volume Scalar Attribute (preset EFX ▸ smoke) — Old Max ≈ 7 (EFX smoke isn't 0–1 like Pyro)
   → RS Ramp (cubic bias; black knot ~0.1 removes wisps) → Standard Volume ▸ Scatter/Density
Volume Scalar Attribute (preset EFX ▸ temperature) — Old Min 1000, Old Max 3500, New 0–1
   → RS Ramp (shape flame tails) → Change Range (0–1 → 0–3500) → Standard Volume ▸ Emission ▸ Temperature
Standard Volume → Output Volume
```

## Steps
1. Use **Standard Volume** (not the Volume or Pyro Volume node) for maximum control.
2. Don't use the volume's built-in preset channels — read channels with **Volume Scalar Attribute** nodes.
3. Smoke: preset **EFX ▸ smoke** → Density. Set **Old Max ~5–10** (start 7) to match viewport thickness. Add a **Ramp**: move the white knot left to thicken, black knot slightly right (0.1) to strip wisps.
4. Fire: Emission mode Temperature (blackbody). Second Scalar Attribute, preset **EFX ▸ temperature**, Old Min **1000** (not 0 or 300), Old Max 3500 → Temperature. Emission **Scale** 10–20 for glowing smoke (more noise → more samples).
5. Ramp on temperature: map to 0–1 first, ramp, then **Change Range** back to 0–3500 — a ramp fed straight into Temperature makes the fire vanish.

## Key idea
Always find and enter the real **smoke** and **temperature ranges** of your sim; defaults assume Pyro's 0–1.
