# Fire emitted only by fast (or big) particles — EFX source mapping

- Source: Top Tip Tuesday — Particle Emission Map — https://www.youtube.com/watch?v=iPYPQGaz7zQ (2026-03-24)
- Host / generation: C4D, nxExplosiaFX (source Mapping) + CPU xpGravity Newton (orbits, scale by distance)
- Goal: particles orbiting a sphere leave fire trails only when they're above a speed (or radius) threshold — no keyframes.

## Steps
1. Particles orbit a sphere with **xpGravity Type Newton** (sphere as attractor; its scale option makes particles bigger near the sphere). [▶ 0:32](https://youtu.be/iPYPQGaz7zQ?t=32)
2. nxExplosiaFX: bigger domain → **Voxel 6**; Buoyancy **Gravity 0** (fluid stays in the orbit). [▶ 4:14](https://youtu.be/iPYPQGaz7zQ?t=254)
3. Sources: the emitter, **Temperature 0**, Fuel only (~42). Fuel won't burn without heat → Simulation ▸ Burning **Ignition Temperature 0**. [▶ 2:07](https://youtu.be/iPYPQGaz7zQ?t=127)
4. Negative **Velocity** on the source (fluid kicks back from particle direction); **Motion Gap Fill 10** for fast particles; raise **Burn Rate**, smoke production; raise smoke/heat **dissipation**. [▶ 3:10](https://youtu.be/iPYPQGaz7zQ?t=190)
5. **Mapping** tab on Sources: layer **Speed**, Source **X-Particles Emission Strength** (not Mesh Object!), target **Fuel**. Range 250–500 cm/s → slow particles emit nothing, fast ones full fuel. Invert the curve (e.g. 200–300) → only slowing particles burn. [▶ 5:37](https://youtu.be/iPYPQGaz7zQ?t=337)
6. Swap the layer to **Radius** (4–30 cm, from the gravity scaling) → only big particles near the sphere burn. [▶ 8:37](https://youtu.be/iPYPQGaz7zQ?t=517)

## Notes
Any channel (smoke, temperature, fuel, pressure) can be mapped to any particle data; mesh/spline emission strength, particle advection and burning settings are mappable too.
