# Target EFX turbulence/vorticity to fuel or temperature (force mapping)

- Source: Top Tip Tuesday — EFX Forces Mapping — https://www.youtube.com/watch?v=BhLiQxdW7E4 (2026-01-13)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX Dynamics layers with Mapping) + Redshift
- Goal: angry, detailed flames while the smoke stays smooth.

## Base sim
Sphere source, Voxel 3.5; more temperature, slightly less fuel, **Pressure 15**; Ignition Temperature 0; more smoke production; higher heat & smoke dissipation; **negative Smoke Buoyancy** (rises with heat, then sinks → swirls).

## Measure channel ranges
- Display: **Volume Slicing → channel Fuel**, adjust Min/Max Fuel colors → here max ≈ 0.12–0.15. Burn Rate controls how long fuel lingers (0.3 = lingers).
- Temperature: Flame Emit Above T test → flames 1000–~2000.

## Forces (Dynamics ▸ Forces, switch off defaults first)
1. **Turbulence** strength **500** (normally explodes the sim) **mapped to Fuel 0–0.15** → violent only where unburnt fuel is.
2. **Vorticity** strength 20 **mapped to Temperature 1200–2000** → detailed flames, smoke doesn't get fuzzy.
3. Extra **Vorticity** strength ~1, unmapped → gentle smoke detail ("less is more", especially before upscaling).
4. Preview, then 1 level of **Upscaling** for render — mapped forces behave the same.
