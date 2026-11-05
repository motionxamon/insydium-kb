# Pump more particles into a fluid without pressure blow-ups (nxFluids Check Density / Max Density)

- Source: Bite-Sized — Fluids Sims Check Density — https://www.youtube.com/watch?v=0b6vrPWXjQg (2025-03-27)
- Host / generation: C4D; xpEmitter + NeXus GPU nxFluids (SPH and PBD)
- Goal: a steady stream filling a tank fast, without the stream exploding sideways.

## Base
Container collider, gravity default, **nxFluids** default (SPH). xpEmitter spherical shape, **Rate** emission randomly inside the volume, **2,000/s**, speed 0 → clean stream.

## Steps
1. Raise Birth Rate to **10,000/s** → the stream bursts apart. Cause: newborns pile into the same volume each frame before older ones leave it, fluid density shoots up and the solver's pressure pushes them apart (correct solver behaviour).
2. nxFluids ▸ SPH ▸ enable **Check Density** (default **110%**) → newborns above that density are killed; the stream is calm again.
3. Trade-off: you no longer get the full 10,000/s. Raise **Max Density** to let more in: 130 = slightly wider stream, 160 = noticeably more particles, 200 = pressure spread returns. Demo settles on **130**.
4. **PBD** mode has the same Check Density option and behaves the same way (off = explosive birth, on = stable).

## Newest equivalent
For dense liquids today use nxFluids FLIP/APIC (Fused 2025.4); 2025.4.1 can color FLIP particles by particles-per-voxel and the 2026.1 beta adds Recolor by Density, handy for spotting over-packed emission.
