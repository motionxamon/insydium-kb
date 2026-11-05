# Feature notes: nxFollowGeo spline modes, per-channel nxUpres, layered nxSpeed Range

- Source: Fused 2025 Tech Preview — Modifier Improvements Part 3 — https://www.youtube.com/watch?v=8QT_cE61U2Y (2025-08-14)
- Host / generation: C4D; NeXus (nx…) on xpEmitters (G2) — previewed ahead of **Fused 2025.4** (Dec 2025)
- Goal: precise art-directed flow of chaotic sims, more controllable upres, procedural speed animation.

## nxFollowGeo — dedicated spline options (replaces CPU xpFollowSpline / xpSplineFlow)
- Drop a spline into the object link → spline-specific settings appear (polygon objects still work).
- Nothing happens until **Activate Range** > 0. Two strengths: **Attract** (pull to the spline) and **Follow** (push along the tangent).
- **Guide** mode: tight, exact path (logos, text reveals). **Force** mode: same strengths but blends with other forces — keep a strong nxTurbulence for a noisy, organic stream. Parametric/animated splines update live.
- **Multiple splines in one modifier**, each with its own settings; a stream entering another spline's activate range splits off; streams still collide/splash as fluid.
- **Extended ▸ Offset** (e.g. 38 cm) — flat ribbon; **Offset Blend** 0 → 100% switches plane, 50% → torus-like tube; an offset curve along spline length tapers it (thin → full mid-way → thin).
- **Extended ▸ Twists** (e.g. 5 twists, radius 35) with its own length curve. Bigger twist radius needs more Attract, then more Follow to smooth. Mix Offset + Twist for twisting ribbons.
- **Release**: Spline End (also by falloff or time); On Release: Do Nothing, Kill, Loop, Reverse, **Change Group** (e.g. to a group that nxGravity alone affects → stream drops and splashes).

## nxUpres — separate strength per channel
- Same setup: cached source emitter + destination emitter (same settings, higher rate e.g. 20,000/s, speed 0, radius 0, no color animation). Each destination particle blends from its nearest (here 10) source particles.
- Sliders for **Velocity, Position, Color, Radius, Mass** instead of one strength + checkboxes. Low Color = subtle tint, high = match source. Low Velocity + high Position = vein/tendril look. Radius channel passes animated source radius (needs a display mode that shows radius, e.g. Spheres).
- Keep the source's nxTurbulence in the scene for extra detail that stays coherent with the source.

## nxSpeed — layer system
- Layers (incremental speed, acceleration…) with blend modes; **Range** layer does almost everything: start/end value, start/end time, ease curve, variation, **Cycle**.
- Burst-and-settle: flip the curve so particles start at end value (e.g. 150) and decay to the start value over 60 F; start value ~1 cm + variation as a resting jiggle; time variation staggers the stop.
- Pulsing: curve 0 → peak → 0 with **Cycle** (repeats every 60 F; e.g. 90 cm). Don't use time variation while cycling if you want obvious pulses.

## Newest equivalent
Shipped in Fused 2025.4. In the 2026.1 beta **nxWarp** (Path, Helix, Flow modes) also shapes streams, and the nxSpeed layer is renamed **Acceleration** (Beta 3).
