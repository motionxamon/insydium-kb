# Molten chocolate that sets on contact (APIC variable viscosity by color)

- Source: Top Tip Tuesday — Chocolate Set — https://www.youtube.com/watch?v=VCGNxYZt21k (2026-02-03)
- Host / generation: C4D, Fused 2025.4+ (nxFluids APIC, nxQuestion object distance, nxBlend, nxMesher) + Redshift
- Goal: chocolate pours over an ice-cream model, stiffens where it touches and stays glossy where it's still molten.

## Steps
1. Thin emitter sweeping across the collider; Project Settings **Subframe Steps 3** to stop stepping.
2. **nxFluids APIC**, Voxel **5**, small domain, **Viscosity 50** → ribbon folding.
3. Color = temperature: **nxQuestion** `Document ▸ Object Distance (mode Polygons, object = cube) < 3 cm → Set Color white` with **reduced Weight** (fades to white = cools gradually).
4. **nxBlend** Color, **Blend: Addition**, strength full, distance ~6 cm → white spreads into neighbours (cooling), never darkens.
5. nxFluids **Mapping ▸ Color Brightness → Viscosity** (source FLIP/APIC). Raise base viscosity to **150** and put the black knot at **1/3 (0.33)** → black keeps the original 50, white goes to 150 (sets).
6. Cache (≈1 min). **nxMesher**: Polygon Size 1.3, radius 1.6, Smoothing **Mean Curvature** 100%, 5 iterations (keeps ridges, removes flats). **Export Tags ▸ Transfer Color**.
7. Redshift chocolate: **Vertex Attribute (color map) → Ramp → Reflection Roughness** → molten = glossy, set = matte.

## Newest equivalent
2026.1 beta FLIP Mixer adds per-emitter/group viscosity, **Yield Stress / Flow Index** (non-Newtonian) and Recolor by Viscosity — the mapping trick still gives the most control.
