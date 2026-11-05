# Lava that freezes and re-melts (animated Random field color → mapped nxWind strength + nxSpeed max speed, nxFluids)

- Source: Top Tip Tuesday — Lava Flow Fluids — https://www.youtube.com/watch?v=bslBFptQSSM (2024-07-16)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxWind Von Karman, nxColor, nxGravity, nxFluids, nxSpeed) + C4D Random field
- Goal: a blob of fluid that cools into ridges where a noise is black and flows again where it turns white.

## Base
Plane 1000×1000 with xpCollider (friction 20, bounce 0). xpEmitter **Cylinder** r 25 / h 50, Shot hexagonal, speed 0, radius 1.

## Steps
1. **nxWind** rotated along the flow, **Von Karman** mode, strength **250**, wind turbulence off for now.
2. **nxColor ▸ Gradient by Parameter**, grayscale (remove color knots), mapped to a **Field ▸ Random** field: Perlin, **scale 500**, **animation speed 25%**; Remapping ▸ contour curve for contrast.
3. nxWind ▸ **Mapping ▸ Color Brightness** → **Wind Strength**, range 0 (black) → 1 (white): black gets no wind.
4. **nxGravity** strength 200 (display off).
5. **nxFluids** default, **substeps 5**.
6. **nxSpeed** at the bottom: Incremental, speed 0, **Max Speed clamp 200**; Mapping ▸ Color Brightness → **Maximum Speed** → black particles are frozen, white flow → ridges form, then melt as the noise animates.
7. Looks: change the Random field noise (**Electric** = stalls then surges; **Displaced Voronoi** = big dark ridges). Lots of **surface tension** → bulbous tendrils.

## Newest equivalent
FLIP/APIC with variable/mapped viscosity (Fused 2025.4) or 2026.1 non-Newtonian (Yield Stress) and the Mixer — see "Hot/Cold Variable Viscosity"; drive it with an animated **nxFalloff Noise** instead of a C4D field.
