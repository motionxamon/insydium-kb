# Data Mapping basics: gravity by age/radius/brightness, cycling EFX fuel/smoke pulses (Mapping tab, Particle Console, Document Time + Cycle)

- Source: NeXus for Blender Quick Guide — Data Mapping — https://www.youtube.com/watch?v=s5JA_AADBnY (2026-06-29)
- Host / generation: Blender (NeXus for Blender, G3): nxEmitter, nxCollider, nxGravity, nxExplosiaFX; Mapping tab on modifiers
- Goal: animate modifier parameters procedurally per particle (age, radius, color) or over time, instead of keyframes.

## Base
- **Box** emitter, birth rate 10 → 250, speed 0, radius **0.04 ±0.03**; display **Circle Filled**, color mode **Noise** with a green-tint gradient.
- Big hidden plane as **nxCollider** (bounce 0, a little friction); **nxGravity** (default 9.8).

## Steps
1. Why not keyframes: keying gravity 0 → 9.8 (frames 30 → 76) only affects the start — later-born particles get full gravity. Clear the keys. [▶ 3:17](https://youtu.be/s5JA_AADBnY?t=197)
2. nxGravity ▸ **Mapping ▸ Add map ▸ Age** → parameter **Gravity Strength** (only Strength or Variation exist on this modifier). Range **20 → 50 frames**: zero gravity until 20 frames old, ramps to full by 50, stays full after. Each new particle replays it. [▶ 4:38](https://youtu.be/s5JA_AADBnY?t=278)
3. Read the graph: X = the source range (min→max), Y = parameter from 0 to its set value. [▶ 5:23](https://youtu.be/s5JA_AADBnY?t=323)
4. Switch source to **Radius**: find the range in the **Particle Console** (radius column, min/max at the bottom) → **0.01 → 0.08**; big particles fall faster, gravity immediate. [▶ 7:49](https://youtu.be/s5JA_AADBnY?t=469)
5. Switch source to **Color Brightness**, range **0 → 1**, with a black→white gradient on the emitter: black hover forever, white fall at full gravity, greys in between. [▶ 9:55](https://youtu.be/s5JA_AADBnY?t=595)
6. EFX: torus inside a taller **nxExplosiaFX**, added as source; voxel size **0.02**; Simplex noise length scale **5**, strength **50**. [▶ 12:08](https://youtu.be/s5JA_AADBnY?t=728)
7. EFX Mapping ▸ **Document Time** → parameter **Mesh (object) emission ▸ Fuel** (parameter list is grouped by source type: curve, particle, mesh). Ramp 20 → 50 frames, or shape the curve into a spike = one blast. [▶ 13:16](https://youtu.be/s5JA_AADBnY?t=796)
8. Curve end behaviour **Clamp → Cycle** repeats the blast; widen range to **0 → 70 frames** and lower emission for blast-then-settle pulses. [▶ 15:05](https://youtu.be/s5JA_AADBnY?t=905)
9. Add constant **Smoke 2** on the source, then a second Document Time map for **Mesh Smoke** with the opposite curve (also set to **Cycle**) → alternating fuel / smoke pulses. [▶ 16:42](https://youtu.be/s5JA_AADBnY?t=1002)
10. Simulation ▸ **Burning ▸ Smoke Production off** so smoke comes only from the mapped channel. [▶ 17:44](https://youtu.be/s5JA_AADBnY?t=1064)

## Gotchas
- A new map stays on Clamp — set Cycle on every layer that should repeat.
- Particle-data sources (age, radius…) are meaningless for object-emitted EFX channels; use Document Time.

## Newest equivalent
2026.1 beta: one Mapping layer can drive many targets, plus the **nxFalloff Modifier** (Remap, Curve, Cycle, memory layers) and per-layer falloffs for spatial control.
