# Animating particle size with the Range layer and its ease curve (nxScale Range)

- Source: NeXus for Blender Quick Guide — Scale Range — https://www.youtube.com/watch?v=o7b5SV4BqfM (2026-06-08)
- Host / generation: Blender (NeXus for Blender, G3); nxEmitter, nxScale
- Goal: particles that grow in, pulse or shrink over time instead of popping on at full size.

## Steps
1. Emitter **Display mode**: Points ignore radius — switch to **Circles** (or Circles Filled / Spheres) to see size.
2. Emitter **Radius** only sets the **birth** radius; changing it doesn't affect existing particles. Set it to **0**.
3. **nxScale** (layered, with blend modes) ▸ default **Range** layer: Start Radius **0**, End Radius **1 m**, time **0 → 100 frames**; add variation to end radius and/or timing.
4. **Ease curve**: X = time span (0–1), Y = start → end radius. Ease-in = stay small, grow late; ease-out = fast early growth then slow.
5. Bring the curve end back down to grow-then-shrink; a point without handles gives a clean peak; skew it for slow grow + snap off.
6. **Clamp mode: Repeat** loops the curve (repeating pulse).
7. Common use: short time span (e.g. **15 frames**) as a simple fade-in so particles don't snap on.

## Newest equivalent
Same layer in NeXus 2026.1 beta; each layer can also take its own nxFalloff, and the **nxFalloff Modifier** (Remap, Curve, Step…) can shape scale spatially.
