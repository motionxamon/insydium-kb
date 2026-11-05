# Detailed field-triggered explosion via upres (nxUpres position + velocity, nxExplode, nxQuestion group switch)

- Source: Top Tip Tuesday — Particle Upres Explode — https://www.youtube.com/watch?v=rMKmeJ68yiE (2025-05-27)
- Host / generation: C4D; NeXus inside X-Particles (nxUpres, nxExplode, nxTurbulence, nxQuestion, nxColor) + C4D Fields
- Goal: a letter X of particles that bursts away smoothly where a growing, ragged field reaches.

## Base
Source emitter from text "X", **Shot 10,000, speed 0**, groups 1+2 **First Group Only**. nxTurbulence + nxExplode with Groups Affected **group 2** only. nxQuestion: inside field → action. Fields: animated **Spherical (Normal)** × **Random (Multiply)** for a broken edge.

## Steps
1. nxQuestion action **Set Color → Set Group 2** — field entry releases particles to turbulence/explode.
2. Duplicate emitter → "emitter dest": **50,000** particles, display size **50%**; Modifiers tab **exclude** turbulence and explode. Hide the source.
3. **nxUpres** (below the movement modifiers): Source = source emitter, Destination = dest; **Groups Affected group 2** so unreleased particles stay put.
4. Blend **Velocity + Position**, Strength very low (**~13%**).
5. Smooth jerkiness: closest-particle count **3 → 10** (smoother, slower).
6. **nxColor** gradient mapped to Speed. Move/animate nxExplode's centre live to redirect the blast.

## Newest equivalent
2026.1 beta: **nxFalloff** (Sphere + Noise, layered/remapped with nxFalloff Modifier) replaces the C4D field stack; **nxWarp** can add art-directed flow. nxUpres remains the detail-transfer tool.
