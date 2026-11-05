# Blooming trail flower (age-mapped nxTurbulence Curl Blend/Add + speed-mapped strength)

- Source: Top Tip Tuesday — Particle Trail Flower — https://www.youtube.com/watch?v=tMeuIDssUxI (2024-11-12)
- Host / generation: NeXus (nxTurbulence Curl, nxPush, nxSpeed, mapping) + xpTrail + Redshift
- Goal: shot from the 2024 Black Friday advert — three rings of particles curling into petals and settling.

## Steps
1. Three **ring** emitters (fast yellow 150, slower purple, slowest blue), radius variation.
2. Stack order: **nxTurbulence → nxPush → nxSpeed**.
   - nxPush: **Particle Radius** mode, full strength (no overlaps).
   - nxSpeed: **Incremental −25** → gradual slowdown.
   - nxTurbulence: **Curl**, scale ~200, more octaves, persistence ~31.
3. Blend vs Add: **Blend** mixes particle and noise velocity (100 % = noise only); **Add** sums them (too much = chaos).
4. Mapping ▸ **Age 0 → 90**: Curl **Blend** ramps in (raise first knot slightly so it starts later); second Age map for **Add**, coming in a bit earlier.
5. Mapping ▸ **Speed 0 → 75** → turbulence **Strength** → still particles get no noise and can stop.
6. Three **xpTrail** objects (one per emitter, colored) → Redshift render.
