# Feature notes: rewritten NeXus GPU core, per-layer GPU falloffs + Data Mapping, nxQuestion variations & neighbour search

- Source: Fused 2025 Tech Preview — Core Improvements — https://www.youtube.com/watch?v=7tXR_Fpk6mw (2025-09-11)
- Host / generation: C4D; NeXus (nx…) on xpEmitters (G2) — previewed ahead of **Fused 2025.4** (shipped Dec 2025)
- Goal: show what the new GPU core and the shared NeXus control tools add.

## Core rewrite
- Stripped down and rewritten: faster sims, less VRAM. Demo timings (old core → new): fluid + nxVorticity + nxRotate + many collision rocks, 501 F: **75 s → 60 s**; nxTurbulence + nxRotate + nxColor at 150,000 p/s, 501 F: **32 s → 26 s**; SPH granular + nxQuestion group switching + 2 colliders: **66 s → 56 s**.
- No more one-time pause on first playback (the old core compiled its GPU compute shaders then; C4D's native particles show a similar first-play stall).

## Layered modifiers + GPU falloffs (demo: nxScale, nxColor)
- **nxScale** stack of **Set Value** layers: base layer (radius ~3 + variation) → "noise" layer (15 cm) → "sphere" layer (~28 cm). Upper layers in **Normal** blend ignore what's below; switch them to **Max** so the base acts as a minimum size.
- Each layer has its own **Falloffs tab** (unlike C4D Fields, which are CPU and per object): **Noise** falloff using INSYDIUM GPU noises (e.g. Cubic), **Sphere** falloff (size/offset) that can be moved around live.
- **nxColor**: two **Gradient by Parameter** layers (blue and orange, both by Radius); mask the top one with a Noise falloff — clamp the noise black/white for crisp patches, raise frequency to animate faster.

## Data Mapping per layer
- Mapping tab ▸ **Age** map ▸ pick the **layer** and its parameter (e.g. "Radius Value" of the noise layer). Range 0–30 F = grow from 0 to full.
- New **clamp modes** (borrowed from Range layers) incl. **Cycle**: a rise-and-fall curve over ~40–60 F repeats → pulsing radius; give a second layer a different range (e.g. 20–60) to offset the pulses.

## nxQuestion
- **Variation on actions** (Set Radius 70 cm + variation; Set Color RGB variation ~0.1) and **on questions** (e.g. Age > 50 with variation 50 → staggered growth). Low action **Weight** = gradual blend instead of a snap.
- Category **Document ▸ Time > 120** → **Add Speed** (~70, variation ~30) = fake gravity; Speed > 150 → Set Color (low weight → fade) + **Set Display** (Planes Filled) + an unconditioned **Add Rotation** with variation → spinning planes.
- **Neighbour search with emitter filter**: question 1 Particle ▸ Emitter = Fox; AND question 2 **Neighbors** counting only Fox particles, **< 18–20** → surface particles. Action **Set Group** "fluid" — nxFluids + nxGravity affect only that group, so the shell peels off frame by frame (melting). Add a third AND neighbour check against a "stream" emitter (count > 5 within 20 cm radius) so only surface particles touched by the stream melt — the stream steers the erosion.

## Newest equivalent
All shipped in Fused 2025.4; NeXus 2026.1 beta extends falloffs to 16 modes plus the **nxFalloff Modifier** (Remap, Step, Freeze, Decay…), and Mapping can drive many targets from one layer.
