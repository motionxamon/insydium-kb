# Springy ribbons vs loose grains by color (nxConstraints Birth connections, Break mapped to Color Brightness)

- Source: Top Tip Tuesday — Particle Constraints Mapping — https://www.youtube.com/watch?v=SPsm-D_hero (2024-09-03)
- Host / generation: C4D; NeXus G2 (nxGravity, nxConstraints + NeXus Mapping) on an xpEmitter; xpCollider tags
- Goal: white particles stay linked by unbreakable springs, black ones fall free, greys in between.

## Base
- Floor plane **8000 × 8000 cm**, collider: bounce 0, some friction, some **Scatter**. Ram skull with a Vibrate tag (rotation), collider: bounce 0, a little friction.
- xpEmitter plane pointing **−Y**, **200 × 1500**; Rate, life **220** (var 30), **15,000/s**, speed 0.
- **nxGravity** Strength ~**500 cm**.

## Steps
1. Emitter Display ▸ Color **Shader ▸ Noise**: Global Scale ~**600**, low/high clip for contrast, Animation Speed **0.5** so emitted values change; darken until there's a black/white mix.
2. **nxConstraints ▸ Birth** connections: Iterations **3**, Connection Limit **12**, Radius **60 cm**, Break **None** first (all springy).
3. Break **Absolute**, threshold **300 cm** (never reached → looks unchanged).
4. **Mapping ▸ Color Brightness**: Category **Birth constraints**, Parameter **Break**, range 0 → 1 → black = 0 cm (snaps instantly), white = full 300 cm (never snaps).
5. Tweak the noise to shift the ratio: more white = more ribbons; greys = weaker links.

## Newest equivalent
Same layers in NeXus 2026 nxConstraints; 2026.1 Mapping lets one layer drive many targets, and **nxPin** can anchor groups if you need fixed ends.
