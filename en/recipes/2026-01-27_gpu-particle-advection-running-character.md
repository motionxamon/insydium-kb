# Wispy particle trail behind a running mocap character (EFX advection)

- Source: Top Tip Tuesday — GPU Particle Advection — https://www.youtube.com/watch?v=LPu79OH-yC0 (2026-01-27)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX, particle advection, nxKill FOV) + Redshift
- Goal: fluid streaks peel off a running character's legs and are carried backward by wind.

## Steps
1. EFX domain resized, **Voxel 2**. Source = **low-poly proxy** of the character (fast with Motion Gap Fill + Velocity from Object Motion) — see "Mocap Sim Proxy".
2. Buoyancy **Gravity off**; Dynamics ▸ Forces: add **Wind** (default 50) blowing backward.
3. Emit only from legs: source Temperature and Fuel **Weight by Tag** = polygon selection tag of the legs. **Pressure 0** (keep motion inheritance), **Motion Gap Fill** on. Temperature dissipation high.
4. Particles: xpEmitter Object = high-poly render character, Polygon Area, **Selection** = legs tag, speed 0, radius 1 ±, start at frame 5 (let the fluid establish), **Rate 50 000**.
5. EFX ▸ Particle Advection: add the emitter (defaults).
6. **nxKill → Outside Camera FOV** (link camera) → huge savings.
7. Redshift Object tag ▸ **Point Instances**, size ~0.03, simple white material → crisp wisps.
