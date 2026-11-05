# Mixing gloopy paint colors (nxFluids SPH + nxConstraints Viscosity + nxBlend)

- Source: Top Tip Tuesday — nxBlend Paint Mix — https://www.youtube.com/watch?v=IG5GdX9U4lM (2024-03-05)
- Host / generation: C4D; NeXus GPU (nxFluids, nxConstraints, nxBlend, nxGravity) on xpEmitters
- Goal: three colored viscous streams whose colors mix where they meet but keep swirls.

## Base
xpEmitter Circle, −Y plane, Hexagonal, speed 0, radius 1 cm. **nxGravity 500**. **nxFluids SPH, substeps 4**.

## Steps
1. **nxConstraints**: Iterations 3, **Viscosity** layer (not Birth): up to 3 connections within 20 cm → gloopy. [▶ 1:14](https://youtu.be/IG5GdX9U4lM?t=74)
2. Emitter **Vibrate tag**: position, amplitude X 100 / Z 100, low frequency. [▶ 1:56](https://youtu.be/IG5GdX9U4lM?t=116)
3. Duplicate the emitter twice; change display color; bump each Vibrate tag's **seed** for different motion. [▶ 4:46](https://youtu.be/IG5GdX9U4lM?t=286)
4. **nxBlend**: blends Color by default (also scale, rotation, mass, radius). Default strength 10% is too weak → **200%**; distance 10 cm; max blend duration 300 F. [▶ 4:08](https://youtu.be/IG5GdX9U4lM?t=248)
5. Distance 40 cm = everything goes one milky color quickly; back to 10 cm keeps original colors away from contact zones. [▶ 5:02](https://youtu.be/IG5GdX9U4lM?t=302)
6. For marbled stripes: raise strength further, cut **max duration to ~20 F** — strong blend on first contact, then colors freeze. [▶ 5:45](https://youtu.be/IG5GdX9U4lM?t=345)

## Newest equivalent
FLIP/APIC with per-emitter **Mixer** viscosity (2026.1 beta) for the gloop; nxBlend unchanged for the color mix.
