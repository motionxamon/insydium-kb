# Uniform render size from a radius-driven sim (xpCache Custom Playback channels, Redshift particle spheres)

- Source: Top Tip Tuesday — xpCache Custom Playback — https://www.youtube.com/watch?v=c-JysAVC__w (2024-10-15)
- Host / generation: C4D; xpEmitter + NeXus G2 **nxPush** (Particle Radius mode); **xpCache**; **Redshift**
- Goal: keep the patterning that needs varied radii, but render every particle at the same size.

## Base
Particles born on top of each other with varied radii; emitter color = Gradient by Parameter **Radius** (2 → 6 cm). **nxPush** in Particle Radius mode pushes them into fluid-like clusters. Display **Squares** (+ **Force Display**) shows the pattern; Circles shows the real radii.

## Steps
1. Emitter ▸ **Redshift Object tag ▸ Particles ▸ optimized Spheres**; Scale Multiplier ~0.1 — but light/large particles still render bigger.
2. **xpCache ▸ Build Cache** (default, 200 F).
3. xpCache ▸ Playback ▸ **Custom**: tick only **Velocity** and **Color** — leave **Radius** off.
4. Now radius is read from the emitter: Emission ▸ Radius **1**, variation **0**.
5. Raise the RS Scale Multiplier back (e.g. 1 → **0.5**): all spheres identical, pattern intact.

## Gotchas
- Spheres can overlap where push spacing came from bigger cached radii; tune the render scale.
