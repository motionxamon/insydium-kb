# Hot/cold variable-viscosity pour over a head (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + colour-mapped nxSpeed clamp)

- Source: INSYDIUM LIVE! — July 2023 – NeXus, Taiao, TerraformFX & MeshTools — https://www.youtube.com/watch?v=6WjDq_87uck (2023-07-05)
- Host / generation: C4D; G2 NeXus inside X-Particles (Fused 2023.3 Data Mapping + nxQuestion Document questions) — GPU
- Goal: hot runny liquid cools and sticks where it touches a wolf head, then re-melts when fresh hot liquid hits it; stragglers drip off.

## Base
xpEmitter Circle, radius **20 cm**, emitter plane **−Y**, emission **Hexagonal**, speed 0, particle radius **1 cm**, all white (colour = temperature, so no colour-by-speed). **nxGravity**; collider tags on wolf + floor.

## Steps
1. **nxFluids** SPH, defaults except **Viscosity 100**, **Surface Tension 40** (forms globules; not yet gloopy).
2. **nxConstraints** below nxFluids (hierarchy order matters: fluid solves first). Iterations **3** (host's usual starting point). **Viscosity** layer (not spring connections): Connection Limit **3**, Radius **20 cm** → already honey-like and fast; no need for huge substeps / viscosity iterations.
3. **nxQuestion** ▸ category **Document** ▸ **Object Distance** (wolf polygons) **< 3 cm** → **Set Color** full blue = cold. Remove friction from the wolf collider.
4. **nxBlend** (below gravity): Color, Distance **20 cm**, Strength **1000** (full), duration **40** frames (default 300) → blue/white mix = heat exchange. Heavy neighbour search, fast on GPU.
5. **nxSpeed** (keep the blend last in the stack): operation **Acceleration** with **Exponential off** (no speed change) and **Clamp Max Speed** on.
6. nxSpeed Mapping ▸ **Color ▸ Red channel → Max Speed**: red 0 (blue/cold) → 0 cm/s, red 1 (white/hot) → **10000** (never limits). Use red, not blue — white and blue both have full blue, only red spans 0–1.
7. Stragglers fix: emitter Groups ▸ two groups, mode **First Group Only**; nxSpeed Groups Affected so that **group 2 is not limited**.
8. Copy the distance question: **Object Distance > 11 cm** as child of a **Particle Age > 15 frames** question (operator **And**; 30 F was too long) → Action **Set Group 2**. Without the age gate every newborn lands in group 2 and the clamp disappears.
→ Cold gloop sticks, hot pours melt it, released particles drip to the floor.

## Newest equivalent
Fused 2025.4 **nxFluids FLIP/APIC** with variable viscosity mapping; 2026.1 beta adds non-Newtonian Flow Index / Yield Stress, Wall Friction and the per-group **Mixer**. Later Top Tip versions: "Hot/Cold Variable Viscosity" (2025-09-09), "Chocolate Setting" (2026-02-03). nxSpeed's layer is called **Acceleration** in 2026.1.
