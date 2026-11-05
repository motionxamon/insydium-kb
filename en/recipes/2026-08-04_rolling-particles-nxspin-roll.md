# Fake rigid-body rolling with nxSpin "Roll" layer

- Source: Top Tip Tuesday — Rolling Particles — https://www.youtube.com/watch?v=OFx-ALGOlAU (2026-08-04)
- Host / generation: C4D, NeXus (nxConstraints, nxSpin Roll layer, nxTurbulence) + xpGenerator
- Goal: hundreds of platonic solids tumbling inside a rotating box that look like a rigid-body sim but stay fully controllable particles.

## Scene tree
```
Rotating Cube (xpCollider tag)
xpEmitter (spherical particles inside the cube) + nxGravity
nxConstraints  — Iterations ≥3; layers: Collisions, Friction (Strength/Static/Kinetic 100%, small Radius, Connection Limit ~18)
nxSpin        — default Range layer → change to **Roll**
nxTurbulence  — Voronoi(default), high Strength, big Scale
xpGenerator   — Emitter, Use Multiple Child Objects: Randomly, Clone Type Multi-Instance
   └─ 3 Platonic primitives
```

## Steps
1. nxConstraints with a **Collisions** layer (≥3 iterations) → particles stop interpenetrating and roll. [▶ 1:12](https://youtu.be/OFx-ALGOlAU?t=72)
2. Instance non-spherical shapes with **xpGenerator** (random children, **Multi-Instance** = fastest). Problem: instances keep orientation and slide. [▶ 4:58](https://youtu.be/OFx-ALGOlAU?t=298)
3. **nxSpin** → switch the default **Range** layer to **Roll**: particles rotate according to speed and direction of travel → reads as rigid-body tumbling, without losing particle control (kill, color, modifiers). [▶ 3:19](https://youtu.be/OFx-ALGOlAU?t=199)
4. Add nxTurbulence for chaos; if it gets frantic, add a **Friction** constraints layer to damp contacts. [▶ 4:12](https://youtu.be/OFx-ALGOlAU?t=252)
5. Per-particle color (e.g. nxColor gradient by Speed, 0–300 cm/s) does **not** show with **Multi-Instance** (treated as one object) → switch xpGenerator to **Render Instances** (slower). [▶ 5:49](https://youtu.be/OFx-ALGOlAU?t=349)

## When to use
Roughly round objects, camera not too close. For accurate contact use xpBullet rigid bodies, or in the newest beta nxMPM / upcoming NeXus rigid bodies.
