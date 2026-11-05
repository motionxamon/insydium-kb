# Few big, many small: random sub-groups + nxScale mapped by group

- Source: Top Tip Tuesday — Random Data Control — https://www.youtube.com/watch?v=5OHld9QtCzI (2026-05-05)
- Host / generation: NeXus (nxQuestion Random, nxScale Range + Mapping, nxKill FOV) — C4D & Blender
- Goal: one emitter, one scale modifier, but a controllable distribution: mostly small particles, some medium, very few huge.

## Steps
1. Emitter radius 0 (Display: Spheres to see real size). **Groups tab**: create 3 groups, mode **First Group Only**. [▶ 2:37](https://youtu.be/5OHld9QtCzI?t=157)
2. **nxQuestion**:
   - `If Math ▸ Random (Time Variation: None, 0–10000) < 100` → Set Color yellow + **Set Group 2**
   - copy: `Random within 2000–2020` → Set Color pink + **Set Group 3** (even rarer)
   - change the Random **Seed** to reshuffle who's picked.
3. **nxScale** Range layer: radius 0 → End 60 cm with large variation. [▶ 7:21](https://youtu.be/5OHld9QtCzI?t=441)
4. **Mapping**: add **Group** map → Map Layer: Range, parameter **Radius End**, Range Min 1 / Max 3; spline preset **Linear**; knots at X 0 (group 1), 0.5 (group 2), 1 (group 3) with Y ≈ low / 0.5 / 1 → group 1 tiny, group 2 ~30 cm, group 3 up to 60 cm, all still varied. [▶ 7:02](https://youtu.be/5OHld9QtCzI?t=422)
5. Tune proportions via the random thresholds. nxKill Outside Camera FOV keeps it light.

## Takeaway
Math ▸ Random with **Time Variation None** = a fixed per-particle random number — the cleanest way to pick percentages of a particle cloud. Map more params (Variation, End Time) per group the same way.
