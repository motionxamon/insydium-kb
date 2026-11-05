# Water jet eroding clumpy sand (nxFluids SPH Granular + Mixer liquid, nxBlend color → mapped granular settings)

- Source: Top Tip Tuesday — Sand & Water Mix — https://www.youtube.com/watch?v=yp5579on6J8 (2026-09-08)
- Host / generation: Blender (NeXus for Blender 2026.0) — nxFluids SPH (Granular + Mixer), nxBlend, nxFluids Mapping, nxCollider
- Goal: a granular torus drop hit by a liquid stream that softens and washes away the sand it touches.

## Steps
1. Floor plane + torus (both hidden). **Sand nxEmitter**: Object ▸ torus, **Volume**, **Shot**, **Hexagonal**, Speed 0; Display Spheres, Gradient by **Granular**, Auto Scale off 0–20.
2. **nxGravity**; **nxCollider** on plane, Bounce 0, some Friction.
3. **nxFluids** ▸ **SPH** (needed to mix granular + liquid), main Fluid Type **Granular** — set the sand up in the main panel, liquid in the Mixer. Substeps **Adaptive off, 15**; Friction **100**.
4. More grains: sand radius **0.015 m** (Hex count follows radius; 7k at default is too few).
5. **Water nxEmitter**: Sphere, radius 0.2, placed along Y; **Rate** + Hex mode; direction **−Y**, speed **3.5**. **Radius 0.015 — must match the sand**; mixed radii make SPH explode.
6. nxFluids ▸ **Mixer** ▸ add the water emitter as **Liquid**. Enable **Check Density** to kill over-dense births (stops the explosive start).
7. Separate colliders: water emitter ▸ Modifiers ▸ set the sticky collider to **minus (ignore)**; add a second collider (same plane, Bounce 0, Friction ~3) and have the sand emitter ignore it. Rename emitters/colliders sand/liquid.
8. Tag contact: sand Single color black (value 0), water white (value 1).
9. **nxBlend** ▸ Color, mode **Addition**, Distance **0.04 → 0.07**, Strength **500%** (can exceed 100) → white creeps through wet sand; set a max/stop frame (148, then **110**) to keep solid black lumps.
10. nxFluids ▸ **Mapping** ▸ three **Color Brightness** maps → **Friction**, **Stability**, **Cohesion**, curves inverted (black = full, white ≈ 0) so wet grains crumble and wash away.

## Gotchas
- Equal radius across SPH emitters is essential.
- High friction suits sand but makes liquid sticky — hence per-emitter collider ignore lists.

## Newest equivalent
2026.1 beta **nxMPM** handles sand + liquid as materials, with **material change by age/speed/stretch/damage** (Mixer); FLIP Mixer adds per-group viscosity/yield stress.
