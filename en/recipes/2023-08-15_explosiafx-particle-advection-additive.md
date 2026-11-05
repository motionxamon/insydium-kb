# Millions of smoke-advected particles rendered additively (xpExplosiaFX Advect Particles, X-Particles material Add blend)

- Source: Top Tip Tuesday — X-Particles Advection — https://www.youtube.com/watch?v=_G2CwPw4OSY (2023-08-15)
- Host / generation: C4D; G1 CPU X-Particles (xpExplosiaFX + Source tag, xpEmitter); C4D Standard renderer with X-Particles material
- Goal: fast-to-sim, fast-to-render wispy particle swirls driven by a fire sim's velocity field.

## Base
Sphere moved by a Vibrate tag; xpEmitter from the sphere, Speed **0**, Birth Rate **1,000 per frame**, Life **50**, variation **20**. Disable the emitter while building the sim.

## Steps
1. System Dynamics ▸ **xpExplosiaFX** (pink domain). Sphere ▸ Tags ▸ INSYDIUM ▸ **xpExplosiaFX Source** tag, defaults → instant smoke/fire.
2. Display: use **Grid** mode for a fast viewport preview; switching display to **Velocity** shows the voxel velocities that will push the particles. Turn the display off afterwards → sim solves faster.
3. Re-enable the emitter; xpExplosiaFX ▸ **Advection** tab ▸ enable **Advect Particles**.
4. Tame particles shooting out of the top: Simulation ▸ Dissipation ▸ add some **Heat dissipation**. Top of Simulation tab: raise **Turbulence strength** a little for more curl.
5. Material Manager ▸ Create ▸ Extensions ▸ **X-Particles material** on the emitter; hide the sphere.
6. Material Size ▸ Scale **0.5** (tiny points). Emitter Birth Rate → **10,000/frame**.
7. Material Color ▸ Modifiers ▸ **Speed**: slow = darkened blue, fast = darkened deep orange (kept dark because overlaps will add up).
8. Render Settings ▸ **X-Particles options** ▸ Blend Normal → **Add** for glowing overlaps.
9. Final: **20,000/frame** — >1M particles per frame; demo rendered 155 frames in about 2 min 50 s (max ~1 s per frame).

## Newest equivalent
**nxExplosiaFX** (GPU, Fused 2025.4) solves the smoke and can advect NeXus particles; in 2026.1 add **nxWarp** on the smoke, or on C4D 2025.3+ link with native Pyro. Render the points additively in Redshift (see "Redshift cached particle velocity glow", 2024-08-13). xpExplosiaFX remains the CPU fallback.
