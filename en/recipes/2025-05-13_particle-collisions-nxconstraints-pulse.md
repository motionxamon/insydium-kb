# Particle-to-particle collisions with pulsed "light" blasts (nxConstraints Collisions + subframe steps)

- Source: Top Tip Tuesday — Particle Collisions — https://www.youtube.com/watch?v=0JdFAE_dopk (2025-05-13)
- Host / generation: C4D; NeXus inside X-Particles (nxConstraints Collisions layer, nxGravity) + CPU xpCollider tag; Redshift (custom-object skulls)
- Goal: a tank of big balls stirred by pulses of small glowing particles — fluid-like residual motion, rendered as instanced skulls.

## Base
Cube (wireframe display) with **xpCollider, Normals Inside**, bounce/friction 0. **nxGravity 500**. Main emitter: Rate, **80 frames, 100/frame, speed 150, radius 5, variation 4**.

## Steps
1. Main emitter ▸ **No Intersection**, radius **12** (> largest particle) — overlapping births are killed, no popping. Lower it slightly later for more particles. [▶ 1:27](https://youtu.be/0JdFAE_dopk?t=87)
2. **nxConstraints ▸ Collisions** layer. Default collapses → **Iterations 10**. [▶ 2:14](https://youtu.be/0JdFAE_dopk?t=134)
3. Still some overlap: Ctrl+D ▸ **X-Particles ▸ Subframe Steps 3** → clean collisions (fast particles + strong gravity need subframes). [▶ 3:25](https://youtu.be/0JdFAE_dopk?t=205)
4. "Lights" emitter: circle with a C4D **Vibrate** tag (X/Y position); **Pulse** emission — 4 frames every 40, **start F150, end F400**, **500/frame**, life **50 ±10**, **radius 1, variation 1**. [▶ 5:34](https://youtu.be/0JdFAE_dopk?t=334)
5. Both emitters in the same constraints → pulses push through the pack. [▶ 6:07](https://youtu.be/0JdFAE_dopk?t=367)
6. Render: emitters instance a **skull as custom object** (works because it's roughly spherical); small ones get a glowing material. [▶ 7:04](https://youtu.be/0JdFAE_dopk?t=424)

## Gotchas
More particles later may need more iterations/subframes again.

## Newest equivalent
NeXus 2026: dedicated **nxPPCollisions** and **nxCollider** objects replace the Collisions layer / xpCollider tag; 2026.1 beta **nxSpawn** (Rate/Burst/Pulse) can generate the pulses.
