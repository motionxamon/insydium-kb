# Procedural leaf with layered veins (Taiao Leaf: Midvein, Lateral veins pinnate/dichotomous)

- Source: Top Tip Tuesday — Taiao Leaf Veins — https://www.youtube.com/watch?v=eRnivIKK52M (2025-02-25)
- Host / generation: C4D; Taiao Leaf object (venation system); standard / Redshift / Octane materials; no particles
- Goal: a shaped, curled leaf with realistic, attached vein structures and separate materials.

## Steps
1. Leaf ▸ Geometry: **6 width / 10 length** segments, 1 subdivision; enable the **profile** shape and pull base and tip to points; add **Edge Noise**.
2. Leaf modifiers: **Fold**, **Furl** near the base, second Furl the other way → S-curve.
3. Main tab: switch Geometry → **Veins** (node-layer view). Add **Midvein**; profile spline tapers it to the tip; **Petiole offset** extends a stem.
4. Midvein modifiers: **Furl Petiole** (curl the stem, adjust bias) + **Turbulence** (low strength) for irregularity.
5. With the midvein selected add a **Lateral Vein** layer. Structures: Reticulate, **Pinnate** (default), Palmate, Dichotomous. Adjust Angle, angle twirl/bias toward the tip, offset, angle variation.
6. Lateral layer has its own modifiers: Turbulence; use its profile to droop veins toward the edge.
7. Materials tab: leaf, midvein and vein materials assigned per part (any render engine).
8. **Dichotomous**: repeated splits (levels, split count) → fanning veins; widen them; Main ▸ **Remove Intersections** stops veins where they meet.

## Gotchas
Veins stay attached through all leaf modifiers (fold/furl/turbulence) — shape first, then vein.
