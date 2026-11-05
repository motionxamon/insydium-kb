# Self-sustaining grow / push / shrink particle loop (nxAttract + nxPush + nxQuestion field + mapped nxRotate)

- Source: Top Tip Tuesday — Dynamic Push Particles — https://www.youtube.com/watch?v=v63KTwt6pI4 (2025-06-24)
- Host / generation: NeXus (nxAttract, nxPush, nxQuestion, nxRotate, nxSpeed, fields, mapping)
- Goal: abstract mograph — particles drift in, swell, shove each other out, shrink, return.

## Steps
1. Ring emitter larger than frame, Shot 30/F for 50 F, speed 0; Display Spheres, Gradient Random B/W.
2. **nxAttract**: Force 300, Acceleration 3000, **Speed Limit 250**.
3. **nxPush**: Distance mode **Particle Radius**, strength 100%, iterations ~20.
4. **nxQuestion** with a **Spherical field**: `Field > 0.7 → Add to Radius` (large amount, **low weight** = slow growth); `Field < 0.3 → Set Radius 1` (low weight).
5. nxAttract ▸ Fields: same sphere + **Invert** modifier → attraction only outside the core.
6. **nxRotate**: speed 360 × big multiplier; Mapping ▸ **Radius** 1 → 2 cm drives Rotation Speed (small = still).
7. **nxSpeed** last: Incremental 0, **Max speed 150**.
