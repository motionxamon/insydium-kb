# Wrapping a particle ribbon around a spline with C4D deformers (Spline Wrap + Twist on an xpEmitter)

- Source: Bite-Sized — Deforming Particles — https://www.youtube.com/watch?v=K2Jb2lxzgSY (2025-05-08)
- Host / generation: C4D; G2 xpEmitter + GPU nxTurbulence, nxAttract, nxKill; native C4D deformers as children of the emitter
- Goal: a thin noisy stream of particles that precisely follows a helix spline and twists around itself, fully procedural and animatable.

## Steps
1. **xpEmitter** + **nxTurbulence**: Noise **Voronoise**, Strength **40**; axis direction scale **Y = 0** → a flat ribbon. [▶ 0:42](https://youtu.be/K2Jb2lxzgSY?t=42)
2. Keep it heading +Z: **nxAttract** target ahead of the stream, Mode **Velocity**, Acceleration **10**, Speed Limit **400**, Force **50**. [▶ 1:25](https://youtu.be/K2Jb2lxzgSY?t=85)
3. **nxKill** with a box: **Volume ▸ Inside bounds** at the attractor so particles die on arrival. Hide kill and attractor. [▶ 2:07](https://youtu.be/K2Jb2lxzgSY?t=127)
4. **Spline Wrap** deformer as a **child of the emitter**: Axis **+Z**; it auto-sizes to the emitter, so enlarge the bounding size (+Z length and width) by eye until it encloses the whole stream. [▶ 3:10](https://youtu.be/K2Jb2lxzgSY?t=190)
5. Drop the **Helix** into the Spline link field → the ribbon follows the helix exactly. Animate helix Start Radius / End Angle for live changes. [▶ 7:44](https://youtu.be/K2Jb2lxzgSY?t=464)
6. Self-twist: **Twist** deformer, coordinates **Pitch 90°** (−90° twists from the wrong end), child of the emitter, centered on the stream; enlarge its **Y bounding size**, set **Unlimited**, then dial the twist angle. [▶ 7:00](https://youtu.be/K2Jb2lxzgSY?t=420)
7. Combine: put Spline Wrap **below** the Twist (both children of the emitter) → twisted ribbon wrapped on the helix (bigger helix radii make it read better). [▶ 7:30](https://youtu.be/K2Jb2lxzgSY?t=450)

## Gotchas
- Deformer order under the emitter matters (twist first, then wrap).
- The bounding box must contain all particles, or parts stay undeformed.

## Newest equivalent
**nxWarp** (2026.1 beta) does this natively: Path or Helix warps in Deform/Guide mode, shared Twist parameter, warps stack; stable route = nxFollowGeo spline mode with Twists.
