# Layered liquids of different density (nxFluids tag density in SPH / radius in PBD)

- Source: Top Tip Tuesday — nxFluids Mixed Density — https://www.youtube.com/watch?v=4o0RR_tttIE (2024-02-20)
- Host / generation: C4D; NeXus GPU (nxFluids SPH/PBD, **nxFluids tag**, nxGravity)
- Goal: oil-on-water style separation — three emitters pouring into a flask settle in layers.

## Base
Lathe flask with xpCollider tag; default nxGravity; **nxFluids SPH, 7 substeps**. Three emitters (orange, blue, green), Regular emission, speed 300, radius 5, offset start times.

## Steps (SPH)
1. Select all emitters ▸ Tags ▸ INSYDIUM ▸ **nxFluids tag** (per-emitter fluid properties).
2. SPH tab **Density**: orange 200, blue 800, green 1600 → green sinks, orange floats.
3. Change green to 100 → it works its way up; 10 → rises to the top quickly.

## Steps (PBD)
4. Switch nxFluids to **PBD** — density isn't used; use **particle radius** instead: green 3, blue 5, orange 7. Larger particles float on smaller ones.

## Gotchas
- SPH needs all particles at the same radius for stability; PBD tolerates mixed radii.

## Newest equivalent
FLIP/APIC **Mixer** per emitter/group (density, viscosity, surface tension…) in the 2026.1 beta.
