# Feature notes: mtPolyFold procedural folding and peeling (MeshTools 2024.2)

- Source: MeshTools Sneak Peek — Procedural Folding & Peeling Effects, Release Update Coming Soon — https://www.youtube.com/watch?v=EDxcs1zAXvQ (2024-04-29)
- Host / generation: C4D; MeshTools (procedural modelling, no particles)
- Status: preview of **Fused 2024.2** (9 May 2024); was available earlier in the INSYDIUM Fused open beta (register via the customer account)

## What it does
Any child object is split into strips that fold/peel away from **fold points**; animating the fold gives unfolding or peeling.

## Key parameters
- Fold points: **Random** (point count, seed), from a **texture tag/shader** (noise + **Tolerance** slider for how many points; a flipped gradient selects only the bottom polygons = clean peel from the base), or **Selection** mode with a polygon selection tag.
- **Fold Angle** (animate for unfold); **variation** adds offset between strips.
- **Angle Limit** of adjoining polygons: low = minimal folding, higher = more neighbouring polygons included.
- Direction: **Center** or **Clockwise** (interesting on round/spherical objects); point count 1 = the whole mesh unfolds in one strip.
- **Remove** folded polygons for wipe-on/off, timed by **Remove Offset**.
- Combines with the rest of MeshTools (e.g. mtShellGen for thickness).

## Newest equivalent
Shipped in Fused 2024.2; see "mtPolyFold abstract unfolding" (2024-08-06) and "Peeling plants with mtPolyFold" (2025-06-26).
