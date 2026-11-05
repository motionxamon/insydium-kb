# Realistic gusting leaves (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)

- Source: Top Tip Tuesday — Realistic Gusty Wind for NeXus Particles — https://www.youtube.com/watch?v=RRKxOyJVrO8 (2024-05-07)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxWind, nxGravity) + CPU xpGenerator
- Goal: leaves tumble and get kicked up by eddies and gusts (also works for dunes, confetti).

## Base
xpEmitter Rectangle, Rate 20/s, radius 5 (var 2), display plane filled. **nxGravity** 40, **nxWind** default blowing +Z; floor with xpCollider.

## Steps
1. Emitter ▸ Extended Data ▸ **Rotation: Random**; **Simple Spin** on, 6 per axis, variation 5. [▶ 1:36](https://youtu.be/RRKxOyJVrO8?t=96)
2. nxWind mode Standard → **Von Karman** (realistic eddies even at defaults). [▶ 1:55](https://youtu.be/RRKxOyJVrO8?t=115)
3. **Wind strength 30** so they mostly settle; art-direct with the turbulence settings. [▶ 2:34](https://youtu.be/RRKxOyJVrO8?t=154)
4. **Scale Distance 5000 cm** → larger gust influence. [▶ 2:52](https://youtu.be/RRKxOyJVrO8?t=172)
5. Raise **Friction Velocity** to strengthen gusts until some leaves kick up; settle on a moderate value. [▶ 2:52](https://youtu.be/RRKxOyJVrO8?t=172)
6. **xpGenerator** from the emitter, children = 4 single-polygon planes with alpha-cut leaf materials; **Multiple children ▸ Random**, clone type **Multi-Instance**. [▶ 5:02](https://youtu.be/RRKxOyJVrO8?t=302)
7. Cheap enough to push to **500/s**; lower Friction Velocity again for the denser crowd.

## Newest equivalent
NeXus 2026.1 **nxWarp** has a Wind gust wave warp; **nxGenerator** replaces xpGenerator on nxEmitters.
