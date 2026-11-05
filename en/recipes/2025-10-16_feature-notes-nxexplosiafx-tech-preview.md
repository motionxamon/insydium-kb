# Feature notes: GPU nxExplosiaFX (Fused 2025 Tech Preview)

- Source: Fused 2025 Tech Preview — NeXus ExplosiaFX — https://www.youtube.com/watch?v=ePQeDy7XXlc (2025-10-16)
- Host / generation: C4D; NeXus GPU **nxExplosiaFX** (pre-release preview; shipped in Fused 2025.4, Dec 2025) + Redshift for renders
- Replaces: CPU **xpExplosiaFX** + per-object Source tags + project-settings tweaks — everything now lives in one object.

## Layout
- **Object tab**: burning, dissipation, buoyancy, diffusion, upscaling, **Forces** layers. **Sources**, **Dynamics** (Colliders, Modifiers, Particle Advection), **Mapping**, **Display** tabs.

## Sources (any number, no tags)
- Polygon objects (Surface / Volume), splines, xpEmitters (e.g. Pulse) all in one list; each type gets its own settings. Object **Velocity** transfer (e.g. 200%).
- Per channel (Smoke, Temperature, Fuel, Pressure): **Weight by** None / **Tag** (vertex map, animatable) / **Noise** (INSYDIUM GPU noises: strength, length scale, frequency; CPU shaders still allowed).
- Channel **Mode**: Set (default, amount per frame), Blend (several overlapping sources), **Add / Subtract per second** — e.g. a Volume sphere set to subtract smoke carves a hole (lower value = softer fade).
- **Fuel / Pressure frame limit**: quick blasts without keyframes (demo: 3 frames fuel, 10 frames pressure at 500 → blast rebounds off the floor).

## Simulation settings
- Burning (fuel only): **Ignition temperature 600** default (0 = fuel ignites by itself), **Burn rate** (saturates once all fuel burns per frame), **Temperature production**, **Smoke production** (thick smoke + low temperature can snuff flames), **Gas expansion** (~85 = big volatile explosion).
- **Diffusion** per channel (temperature ~100 → soft candle-like flames), **Dissipation** per channel (lower temperature dissipation = taller flames), **Buoyancy** per channel — strongly negative smoke buoyancy + fast temperature dissipation = sinking dry-ice smoke.
- **Upscaling** levels (1 = off): upsamples temperature and smoke on the base velocity → same motion/shape, far more detail, VRAM-efficient.

## Particle advection (Dynamics ▸ Particle Advection)
- **Advect particles**, velocity strength 100%; also advect channels **smoke, temperature, fuel, color** into particle data.
- Uses: color particles by temperature (emitter Display ▸ Gradient by parameter); nxQuestion age > 30 AND smoke < 0.1 → Kill (+ variation) so particles fade with the smoke.
- Mapping ▸ Particle Advect strength by **Age** (full until 40, zero by 50) frees embers from the flow.

## Colliders (Dynamics ▸ Colliders)
- Drag in objects; **Velocity scale** (100% default, 500% for stylised pushes); collider **Pressure** (600–1000) pushes fluid off the surface; **Inside normals** traps the sim inside a mesh (e.g. spiral Sweep tube).

## Forces (layered, in Object tab)
- Multiple **Vorticity / Turbulence / Wind** layers. Vorticity amplifies existing swirls (too high = cotton-wool smoke); each layer has inline strength mapping (smoke/temperature/fuel, velocity, time, **Position Y** 0–1 in the grid). Demo: Vorticity 20+ mapped strong-at-bottom + a second unmapped layer ~4.7.
- Turbulence injects motion: GPU noise type (Simplex), length scale (~370 demo), frequency, **Octaves** (0 = large soft gusts, leave detail to vorticity).
- Built-in **Wind** layer (default +Z) with movable wind object, strength, variation.

## Mapping tab
- Map emission strength for particle / spline / mesh sources, burning model and advection to particle or **scene** data (document time). Example: fuel fades in F30–60, shaped into a pulse, **Cycle** for repeating bursts.

## NeXus modifiers (Dynamics ▸ Modifiers)
- Drag in nx modifiers: **nxAttract** steers the plume (raise vorticity/turbulence to recover detail); **nxWind Von Karman** for gusts (friction velocity, turbulent strength) shared coherently with separate particle sims.

## Display
- Default **Volume ray marching** viewport: ray max steps, ambient light (heading, pitch, tint); smoke extinction (~100), tint, **albedo**, scatter **anisotropy** (backlit halos); fire **hot soot intensity** + **hot gas intensity** (Blackbody or manual color, e.g. blue gas flame).
- Diagnostics: **Volume slicing** per channel, **Speed** mode (shows speed max to guide mapping); HUD: voxel grid, **adaptive bounds**, velocity trails.
