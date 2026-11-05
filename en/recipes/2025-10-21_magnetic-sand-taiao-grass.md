# Fake magnetic sand / ferrofluid spikes (Taiao toGrass + stuck particles)

- Source: Top Tip Tuesday — Magnetic Sand — https://www.youtube.com/watch?v=TWZrrfN1URk (2025-10-21)
- Host / generation: C4D, Taiao toGrass + X-Particles emitter (CPU) + xpVertexMap
- Goal: iron-filing spikes that stand up, sway and lie down as an invisible magnet moves.

## Steps
1. Plane + **xpVertexMap** texture layer (Maxon noise shader), masked with a **Sphere field** (circular patch).
2. **toGrass**: Generate on = plane, **Selection Map = vertex map** (weight also drives density/length). Grass layer type **Polygon** blades (not splines), length ~65 with variation, **Segments 1** (rigid blades that only rotate, no bending).
3. toGrass **Forces**: wind + turbulence; set **Direction Object** = a cube (its +Z = wind direction) with a **Vibrate tag** on rotation → magnet motion. Fewer octaves = smoother turbulence; lower wind strength/frequency, larger turbulence scale → flat calm areas between "magnet" hits.
4. Grow-in: keyframe **Blade Height** 2 cm (frame 0) → full (frame 27).
5. Hide grass; **xpEmitter** Object = toGrass, Polygon Area, **Stick Particle to Source Object**, **Shot 200 000**, speed 0.
6. Color by motion: stuck particles have speed 0 → enable **Extended Data ▸ World Speed**, Display Gradient (Parameter) **Speed (World)** black→white, max ~200.
7. Ground layer: duplicate the emitter onto the plane using the same vertex map as Selection (gray instead of black in the noise to avoid holes).
