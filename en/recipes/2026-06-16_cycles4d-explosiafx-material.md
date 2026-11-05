# Render nxExplosiaFX in Cycles 4D (Principled Volume)

- Source: Top Tip Tuesday — Cycles4D EFX — https://www.youtube.com/watch?v=ZPLiuua0ffw (2026-06-16)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX cached) + Cycles 4D (Device: OptiX)
- Goal: smoke and fire from a cached EFX sim in Cycles, either stylised (emission color) or physical (blackbody).

## Smoke
Principled Volume (Cycles 4D material on the EFX object):
`Point Density (EFX Smoke, Normalize OFF) → Color Ramp (clip wisps / thicken) → Math Multiply (thickness, e.g. 15–20) → Density`

## Fire — option A: stylised emission
`Point Density (EFX Temperature) → Map Range (From 1000…6000 → To 0…1)`
- → Math Multiply (e.g. ×50) → **Emission Strength**
- → Color Ramp (any gradient: real flame, pink, blue/green magic fire) → **Emission Color**
- Optional extra Color Ramp before the multiply to clip flames to the hottest parts.

## Fire — option B: physical blackbody
- Map Range (1000…6000 → 0…1) → Multiply → **Blackbody Intensity**.
- Second Map Range with From = To (1000…6000 → 1000…6000) → **Temperature** (real Kelvin range, not normalised).

## Ranges (same rules as Redshift)
- EFX outputs real temperatures; **ambient temperature 300** causes a domain-wide haze → minimum must be at least 300, and **1000** matches the viewport (Flame Emit Above T).
- Render settings: renderer Cycles 4D (default is Redshift now), device OptiX if available.
