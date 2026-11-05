# Leaves blown off a Taiao tree (Taiao emitter leaves + nxWind Von Karman + nxQuestion Field/Random + xpSpin mapped to Speed)

- Source: Top Tip Tuesday — Taiao Particle Leaves — https://www.youtube.com/watch?v=zG0XcLByiG4 (2025-03-04)
- Host / generation: C4D; Taiao plant + xpEmitter with NeXus G2 nxWind / nxQuestion and CPU **xpSpin**; C4D spherical field
- Goal: leaves ride the tree's wind animation, then get torn off at random and tumble away.

## Steps
1. Taiao Plant Layers ▸ Leaf layer type **Basic geometry → Emitter**, link an xpEmitter → one particle per leaf, still following the wind. Display **Plane**. [▶ 0:35](https://youtu.be/zG0XcLByiG4?t=35)
2. For render, instance leaf geometry with your renderer's tag or an **xpGenerator**. [▶ 0:54](https://youtu.be/zG0XcLByiG4?t=54)
3. Emitter ▸ Extended Data: **Use Rotation** on, mode None (just enables rotation). [▶ 1:10](https://youtu.be/zG0XcLByiG4?t=70)
4. **xpSpin** ▸ Random Spin **10/10/10**; Mapping: map Random Spin to **Speed 0–50 cm** → still leaves don't spin, fast ones spin fully. [▶ 1:45](https://youtu.be/zG0XcLByiG4?t=105)
5. Groups: two groups, **First Group Only**. [▶ 2:27](https://youtu.be/zG0XcLByiG4?t=147)
6. **nxWind**; Taiao Plant ▸ Forces ▸ **Direction from Object** = the wind, so tree and particles share one direction. [▶ 3:03](https://youtu.be/zG0XcLByiG4?t=183)
7. nxWind: **Von Karman** mode, strong, turbulence ~50, friction velocity **2.3**; Groups Affected = **group 2**. [▶ 3:20](https://youtu.be/zG0XcLByiG4?t=200)
8. **nxQuestion** ▸ Field tab: spherical field. Question: Particle **Field > 0** → **Set Group 2**. [▶ 3:53](https://youtu.be/zG0XcLByiG4?t=233)
9. Child **And** question: **Math Random −100…100**, per frame, **> 85**; move the action under it → only some leaves in the field release each frame. [▶ 4:44](https://youtu.be/zG0XcLByiG4?t=284)

## Gotchas
Without the random sub-question every leaf inside the field drops at once.

## Newest equivalent
Swap CPU xpSpin for **nxSpin** (layered in Fused 2025.4) so the whole emitter stays on NeXus; in the 2026.1 beta the release field can be an nxFalloff.
