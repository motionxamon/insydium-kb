# Particle radius drives color and glow in Redshift (Scalar User Data ▸ Change Range ▸ Ramp / Scalar Ramp)

- Source: Top Tip Tuesday — Particle Data in Redshift — https://www.youtube.com/watch?v=EQdOJuS6uv0 (2024-07-09)
- Host / generation: C4D; xpEmitter + NeXus (nxGravity, nxTurbulence, nxPush, nxScale 1–15 cm); Redshift
- Goal: color spheres by their radius on a ramp, and make only the biggest ones emit light.

## Steps
1. Emitter with **Redshift Object tag ▸ Particles: Sphere Instances**; Redshift Standard Material on the emitter, open node editor.
2. Add **Scalar User Data** (Utilities ▸ User Data); attribute via **Presets ▸ Particles ▸ Size**. Raw output is hard to read.
3. **Change Range** node: input = scalar data, **Old Min 1 / Old Max 15** (the sim's radius range) → small black, big white.
4. **Ramp** node: drop Change Range onto its thumbnail and pick **Alt Input**; load a gradient preset → Output into **Base Color**.
5. Glow: second branch into a **Scalar Ramp** (Alt Input), make the curve linear and crush the blacks until only the largest particles are white.
6. Standard material **Emission weight 2**; Ctrl-click the small button by Emission Color to expose the port, plug the Scalar Ramp in → only big particles glow, toggling as they resize.

## Gotchas
- Old Min/Max must match the actual particle radius range or the data looks flat.
