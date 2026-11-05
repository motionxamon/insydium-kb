# Recolor cached particles with nxColor (and speed-clamp by color)

- Source: Top Tip Tuesday — Color Post Cache — https://www.youtube.com/watch?v=cG7K452FWwc (2026-02-17)
- Host / generation: NeXus (nxFluids SPH Granular, nxWind Von Karman, nxColor, nxSpeed + Mapping, xpCache)
- Goal: use color as a simulation driver, cache, then recolor for the final look without re-simming.

## Sim (color drives motion)
1. Particles fall (nxGravity) and are blown by **nxWind Von Karman** with strength variation.
2. **nxFluids SPH → Granular**; in the Substeps twirl-down **turn Adaptive off** for grains (keep adaptive for liquids).
3. **nxColor** Noise layer: **Turbulence** noise, scale 200, lower frequency → animated black/white patches.
4. **nxSpeed** *last* in the stack: layer **Incremental**, Speed Value 0 (no change), **Max Speed clamp 70**. **Mapping**: Color → **Speed Max** of that layer → black particles can't move (0), white move freely (70). → flowing, patchy movement (same idea as the lava-flow tips).
5. Cache (xpCache).

## Recolor post-cache
6. Some nx modifiers (incl. **nxColor**) still evaluate on cached particles. Disable the sim color modifier; add a new nxColor:
   - Gradient (Parameter) by Speed (blue slow → white fast), or
   - **Time Dependent** layer with a client palette preset, Time to Completion 50 F, **Reverse** → cycles colors.
   - Layer **Blend: Screen** to combine the new palette with the cached black/white values.
