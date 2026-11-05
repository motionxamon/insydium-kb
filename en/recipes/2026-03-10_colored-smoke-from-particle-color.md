# Colored smoke driven by animated particle color (nxExplosiaFX color channel → Redshift)

- Source: Top Tip Tuesday — Color Smoke — https://www.youtube.com/watch?v=KimysoJRI9I (2026-03-10)
- Host / generation: C4D, nxExplosiaFX + nxColor (Distance from Object) + Redshift
- Goal: smoke tinted by whatever color the source particles currently have.

## Steps
1. Short-lived particles from a circle emitter + turbulence act as the EFX source.
2. nxExplosiaFX **Solver tab → enable Color channel** (off by default to save memory).
3. Sources → emitter → **Color 100%** (Color From: particles/object).
4. Preview: Display Draw Mode **Volume Slicing**, Display Channel **Color**. (The color is a tint; ray-marched view still shows smoke shape.)
5. Animate particle color: **nxColor** layer **Distance from Object** → animated Null; gradient e.g. orange (≥300 cm away) → yellow → green → blue (near).
6. Redshift volume material: existing `Volume Scalar Attribute (smoke) → Density`; add **Volume Color Attribute** (preset **EFX ▸ color**) → **Scatter Color**, Scale ~7 (raw color values are dark).

## Notes
Works with object color too. Same color channel can tint flames.
