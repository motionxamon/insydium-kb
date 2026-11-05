# Feature notes: nxSpin layers, nxColor Noise/Neighbor gradient, nxDirection Direction Force (Fused 2025 preview, part 2)

- Source: Fused 2025 Tech Preview — Modifier Improvements Part 2 — https://www.youtube.com/watch?v=QzIbDaoIH4Q (2025-07-24)
- Host / generation: C4D; NeXus GPU modifiers (nx…) on xpEmitters + xpGenerator instancing; nxFluids PBD in the last demo
- Status: preview of the layered modifiers shipped in **Fused 2025.4** (Dec 2025)

## nxSpin (new layer-based rotation modifier)
- **Spin** layer, Spin Time **On Birth**: Spin Amount 0 with **360° variation** on all axes = random initial orientation (instanced sports balls).
- Second Spin layer, **Per Frame**: e.g. 10°/frame on Bank; switch Orientation **World → Particle** to spin on each particle's own axis. Amount 0 + variation = random direction and rate; small variation on the other axes adds wobble.
- **Range** layer: Spin Start → Spin End (0 → 360°) between Start/End frames (30 → 90), shaped by an ease curve; add a middle knot to spin out and back; variation on time/values; **Cycle** to loop. Small values on the other axes (20, var 10) for wobble.
- **Tangential** layer: aligns instances (rockets) to direction of travel; choose the axis, offset, variation; **Spin** option rolls them on their bank.

## nxColor
- New **Noise** layer: the INSYDIUM GPU noises (FBM, Voronoise, Cubic…) drive a gradient (default black→white for driving sims; swap for a heat-map look). Faster than C4D Fields (CPU).
- **Gradient by Parameter ▸ Neighbor**: each particle counts neighbours inside a radius (demo 25 cm); ≥ the max count (3,000) = white end, ≤ the min count = dark end. Dense core vs sparse edges; a stepped gradient gives topographic bands on a fluid.
- Clamped neighbour gradient = a crisp dark **surface/edge mask** to target modifiers (melting, disintegration). Layers blend: put the edge layer in **Multiply** over a colour layer, then a Noise layer in Multiply at low strength for variation.

## nxDirection (now layer-based)
- Keeps the previous direction modes; new **Direction Force** layer pushes particles along the object's +Z (Visible in Editor shows the arrow; rotate/animate the object to steer).
- **Twist Strength** 100% = counter-clockwise, negative (−200%) = clockwise; twist also pushes outward, so raise **Attract Strength** (300–400%) to pull back to the axis.
- Art-directed PBD stream: Twist −100%, Attract ~250% so tendrils break off, plus an nxTurbulence for natural flow; real-time in the viewport. Also suggested for smoke/fire.

## Newest equivalent
Shipped in Fused 2025.4; see "nxDirection art-directed liquid stream" (2026-03-17) and "Advanced spin control" (2026-06-09). For path-shaped streams in 2026.1 also consider nxWarp (Path/Helix/Flow).
