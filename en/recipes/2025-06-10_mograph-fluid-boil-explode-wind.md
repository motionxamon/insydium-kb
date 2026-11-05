# Fluid sphere: settle → boil → explode → slosh (initial state + age-mapped nxVorticity / nxWind)

- Source: Top Tip Tuesday — MoGraph Fluid Particles — https://www.youtube.com/watch?v=u2MiqeckNaQ (2025-06-10)
- Host / generation: NeXus (nxFluids SPH, nxVorticity, nxExplode, nxWind von Kármán) + C4D Vibrate tag
- Goal: logo/object reveal with fluid trapped in a sphere around a boolean-cut "X" collider.

## Steps
1. Hex emitter 30 F, radius 2; **nxFluids SPH** substeps 4, Check Density; **nxGravity 700**; sphere collider Normals Inside.
2. Let it settle → Emitter ▸ **Initial State ▸ Use State + Set State**; Emission ▸ **Controlled only** (no new particles).
3. **nxVorticity**: radius 150, strength 2000, **limit 100** (vorticity accumulates); Mapping ▸ **Age 0 → 150** → strength builds = boiling.
4. **nxExplode** from the modifier position (not mass center), speed 1000 ± 800, below the fluid, **Scene time frame 150**.
5. **nxWind** von Kármán mode, strength 800–1200, turbulence off; **Vibrate tag** rotation 360° all axes, frequency 5; Mapping ▸ Age step 150 → 151 (off then on).
6. X geometry: xpCollider Outside, bounce 0.

## Note
Age = frames since state load, so age mapping doubles as a scene timer here.
