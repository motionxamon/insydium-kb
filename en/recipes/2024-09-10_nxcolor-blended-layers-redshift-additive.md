# Multi-layer grayscale color → remapped additive flames (nxColor Age × Heading × Pitch, Redshift Color User Data)

- Source: Top Tip Tuesday — Particle Color Layers — https://www.youtube.com/watch?v=VHGhFAwDypM (2024-09-10)
- Host / generation: C4D; NeXus G2 (nxTurbulence, **nxColor** layers) on an xpEmitter; xpCache; **Redshift** (point instances, additive)
- Goal: swirly flame where color varies with direction, not just a flat age gradient.

## Base
xpEmitter Rectangle **50 × 0**; Rate, life **70** (var 15), **2,000/frame**, speed **100**, radius **3**. Top-down camera.
**nxTurbulence Wavy**, Strength **11**, Octaves max, Persistence **20** → fine detail plus big curls.

## Steps
1. Emitter: **Redshift Object tag ▸ Particles ▸ Point instances** (small scale).
2. RS Standard material: base color off, reflection off, Emission **2**. **Color User Data** (preset Particle ▸ Color) → **Geometry Opacity** = additive, black = invisible.
3. **nxColor** layer "age": Gradient by Parameter **Age**, grayscale black → white; move the white knot earlier.
4. In the material, insert a **Color Ramp** (particle color → alt input → opacity); load a colorful preset; add a black knot at the start so the emission line fades in.
5. Duplicate layer → "heading": parameter **Direction**, axis **Heading**; white knot pulled in, black knot lightened to grey; Blend **Multiply** over age.
6. Duplicate → "pitch": Direction axis **Pitch**, Multiply → extra color flashes.
7. Final: cache at **30,000/frame** (millions); lower the RS tag **Scale Multiplier** a lot — more additive particles need smaller render size.

## Gotchas
- A pure-black knot in a Multiply layer punches holes (fully transparent); keep it grey.

## Newest equivalent
nxColor in 2026.1 adds a **Cyclic** layer and per-layer falloffs; nxFalloff Modifier layers for extra masking.
