# Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)

- Source: Top Tip Tuesday — Particle Neighbor Spawn — https://www.youtube.com/watch?v=nC1YyRrwY2g (2024-07-23)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxQuestion, nxSpeed, nxScale, nxColor, nxPush, nxTurbulence)
- Goal: a dozen seed particles inside text spawn branching networks that fill the letters with fluid-like motion.

## Base
Text primitive inside **xpJoin**, xpCollider tag set to keep particles inside, friction 35%. xpEmitter Object = the join, **Volume**, Shot **12** particles, speed 0.

## Steps
1. **nxQuestion** Q1: **If Particle Neighbors** within **4 cm** **less than 9** → **Action Spawn**, distance **0.2**, **new spawn emitter**, Inherit parent off, speed 25, radius 1. [▶ 1:33](https://youtu.be/nC1YyRrwY2g?t=93)
2. **nxSpeed** Incremental **−50** with variation → spawned particles slow to a stop. [▶ 2:06](https://youtu.be/nC1YyRrwY2g?t=126)
3. Q2 (new question below, searching all particles): neighbors in a somewhat larger radius **less than ~270** → Spawn, distance 0.2, its own new spawn emitter (speed 25, different color). Tune the two counts to change network shape. [▶ 2:38](https://youtu.be/nC1YyRrwY2g?t=158)
4. Set both spawn radii to **0**; display filled radius circles. **nxScale** change-over-time (slow), variation 5%, **Clamp to radius limit** + **within range**, max **1 cm**. [▶ 4:12](https://youtu.be/nC1YyRrwY2g?t=252)
5. Kill escapees: Q3 **Document ▸ Object Distance**, measure **Volume** of the text object; **> 0 = outside** (< 0 inside) → **Kill**. [▶ 4:49](https://youtu.be/nC1YyRrwY2g?t=289)
6. **nxColor** gradient by parameter (purple/magenta preset) mapped to **Age**. [▶ 5:48](https://youtu.be/nC1YyRrwY2g?t=348)
7. Motion: **nxPush** Particle Radius, **nxTurbulence** Voronoi strength 10 → motion changes neighbor counts, which changes spawning. Recolor by **Speed** for a different look. [▶ 7:02](https://youtu.be/nC1YyRrwY2g?t=422)

## Newest equivalent
NeXus 2026.1 **nxSpawn** (Rate/Burst/Pulse, sub-layers) replaces the nxQuestion Spawn action; volume containment via 16-mode nxFalloff (Object mode) on a kill layer.
