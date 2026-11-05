# Fuel-burning fire and smoke rendered live in Cycles (nxExplosiaFX sources, forces, Adaptive Bounds, VDB Output Live)

- Source: NeXus for Blender Official Training — Fire Sim — https://www.youtube.com/watch?v=RH6ukNvt-No (2026-06-25)
- Host / generation: Blender (NeXus for Blender, G3); GPU **nxExplosiaFX** voxel domain; Cycles GPU (Eevee also works)
- Goal: art-directed flames + smoke from a Suzanne, rendered without caching via the auto-generated Blender volume and preset material.

## Base
nxExplosiaFX domain (defaults: **voxel size 0.04 m, domain 4 m**), floor removed; small Suzanne at the bottom of the domain. Sources can be meshes, curves or particles; several sources can share one grid.

## Steps
1. **nxExplosiaFX ▸ Object ▸ Sources**: add Suzanne. Default channels emit temperature 1000, fuel 0.2, pressure, smoke 0 — smoke still appears because burning fuel generates it.
2. Two ways to drive the look: (a) emit only **Temperature + Smoke** (fuel off) — quick, no combustion; (b) emit **Fuel** and shape the result in **Simulation ▸ Burning** (smoke and temperature produced on combustion; too much smoke chokes the flame). Can mix both (fuel + a little extra smoke = thicker smoke). Pressure set to 1.
3. Break up emission: source **Weight By ▸ GPU Noise** — white areas emit fuel, black don't; animated noise gives licks; lower Strength adds greys for softer variation.
4. **Dynamics ▸ Forces** (defaults are Simplex turbulence + Vorticity; removed first to see the raw flow, then rebuilt):
   - **Turbulence** for large curls: test at Strength 50 to see it, then **Length Scale 10**, **Strength 25**.
   - **Vorticity** for fine detail (amplifies existing curls, doesn't add motion): too high = cotton-wool smoke; ~8 at default res.
5. Resolution: **Voxel size 0.02** (≈10× VRAM, much more detail). Finer grids need less vorticity → drop to **2**.
6. Hotter but not taller flames: Burning temperature up (8000 → 10000), then **Temperature Dissipation ~1.2** (2 = very low flames). **Smoke Dissipation**: 0.2 lingers; **1.5** keeps just enough smoke around the flames for scattering/absorption at render.
7. **Display ▸ Viewport HUD ▸ Draw Adaptive Bounds** to see where solving happens. **Solver ▸ Adaptive Bounds** channel thresholds: too high (e.g. smoke 1) = smoke pops out; default 0.01, **0.001** for production fades (bigger bounds, slower).
8. Framing: enlarge domain so its top is out of camera and sides don't clip (X/Y **4.5**, Z taller). Watch **Estimated Persistent / Peak VRAM** in Simulation — here peak went ~1.16 → 2.2 GB; keep peak well below card VRAM.
9. **Render tab ▸ VDB Output: Live** → temporary VDB sequence, auto Blender Volume object hooked to all channels, preset fire/smoke material; sim stays live (no cache needed). Alternatives: nxCache or VDB export + Blender volume import.
10. Preset material: Flame — hot soot intensity, direct emission strength, **Temperature Minimum** (default 1100; 3000 = only short hot core renders as flame). Smoke — Extinction (e.g. 200 = dense), Albedo, Anisotropy.
11. Cycles GPU: black world, area light (Normalize off, Track To Suzanne), Max Samples 1000 + GPU denoise; **Advanced ▸ Seed > 0** (fixed noise pattern suits denoising); **Light Paths ▸ Volume bounces 1**. **Render ▸ Lock Interface** for any NeXus render.

## Gotchas
- Burning settings do nothing unless fuel is emitted.
- Small domain/voxel changes multiply VRAM quickly.

## Newest equivalent
Same object in NeXus 2026.1 beta; add **nxWarp** (Deform/Guide/Flow) on the smoke for art-directed shapes and per-layer nxFalloffs on forces. C4D users get the same solver plus Pyro link (C4D 2025.3+).
