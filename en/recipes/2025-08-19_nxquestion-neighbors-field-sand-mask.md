# Dynamic black/white mask on a sand sim → Redshift material blend (nxQuestion: Field AND Neighbors, Else)

- Source: Top Tip Tuesday — Advanced Color Animation — https://www.youtube.com/watch?v=1ISE9D2bmeQ (2025-08-19)
- Host / generation: NeXus (granular, flow field, nxQuestion) + Redshift
- Goal: sand turns black where it gathers along a spline in dense ridges; use the B/W value to mix two materials.

## Steps
1. Emitter Display can stay Gradient-by-Parameter (granular data) for viewport; for render set **Color Mode: Single Color white**. [▶ 0:36](https://youtu.be/1ISE9D2bmeQ?t=36)
2. **nxQuestion** → Action **Set Color black** with **Weight ~7%** → gradual fade instead of instant switch. [▶ 1:28](https://youtu.be/1ISE9D2bmeQ?t=88)
3. Fields tab: drag the spline in as a layer, **Distance mode ▸ Radius** (tube around the spline; raise radius for wider spread). [▶ 1:57](https://youtu.be/1ISE9D2bmeQ?t=117)
4. Question: `Field > 0` → Set Color (action as child). [▶ 2:18](https://youtu.be/1ISE9D2bmeQ?t=138)
5. Sub-question (child, Operator **AND**): `Particle Neighbors within 10 cm > 400–500` → only dense ridges darken. [▶ 3:45](https://youtu.be/1ISE9D2bmeQ?t=225)
6. Sibling question, Operator **Not / Else** → Set Color white, weight ~40% (recovers). [▶ 5:23](https://youtu.be/1ISE9D2bmeQ?t=323)
7. Redshift: **Color User Data** ▸ Particle Data ▸ Particle Color → **Material Blender** Blend Color; base = material A, Layer 1 = material B. [▶ 7:26](https://youtu.be/1ISE9D2bmeQ?t=446)

## Gotchas
- Neighbor thresholds scale with particle count: 2k/frame test vs 50k/frame production needs a far larger number.

## Related
"nxQuestion Fields", "Neighbor Search Color" recipes; 2026.1 beta falloffs (16 modes) give more field shapes.
