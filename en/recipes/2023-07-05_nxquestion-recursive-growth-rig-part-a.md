# Field-driven recursive growth with nxQuestion spawning (nxQuestion Neighbors + Spawn, nxPush, mapped nxTurbulence)

- Source: INSYDIUM LIVE! — July 2023 – NeXus, Taiao, TerraformFX & MeshTools — https://www.youtube.com/watch?v=6WjDq_87uck (2023-07-05)
- Host / generation: C4D; G2 NeXus inside X-Particles (Fused 2023.3: redesigned **nxQuestion**, new Mapping tab) — all GPU
- Goal: coral-like growth that sprouts from the edge of a particle block wherever a field touches it, curls along a vector field, and freezes after a set distance.

## Base
xpEmitter filling a box/grid with static **black** particles (display colour only; the question logic reads colour).

## Steps
1. **nxQuestion** ▸ Question 1: Particle Data ▸ **Field** + a small **Spherical field** placed on the block.
2. Child question (operator **And**): Particle ▸ **Neighbors** — fewer than **45** within **10 cm** (40 gives one edge row, 45 two rows) → Action **Set Color white**, value 100%. Result: only edge particles inside the field turn white.
3. Ctrl-add a sibling question below (stack executes top → bottom): Color ▸ **Brightness ≥ 1** → Action **Spawn** into a new spawn emitter; **Inherit Parent off**; Speed **0**, Radius **2**, Distance **1**.
4. **nxPush**: mode Particle Radius, Strength **100** → spawned beads push apart and the growth recurses.
5. Spawn emitter display: Circles filled, gradient by Age, **Heat** preset with the first knot set to white — newborns are white, so step 3 fires on them again (the recursion loop).
6. Order trick: nxPush **above** the question = blobby growth; **below** = thinner, tendril-like branching.
7. **nxTurbulence** Curl, Strength **1**, Scale **250**, Frequency **0** (static field to grow into). Mapping tab ▸ **Color Brightness → Strength**: black block particles get no force, white growth gets full force.
8. Freeze old growth: another bottom question, **Distance Traveled within 50–150** → **Set Speed 0** (with a little damping). Recursion continues from the white tips.
9. Move/animate the field to start growth elsewhere — fully interactive on the GPU (demo on RTX 3080 Ti / 2080).

## Newest equivalent
2026.1 beta: **nxBioLogic** (differential growth, coral, Physarum) is the dedicated growth solver; **nxSpawn** (On Age/Instant, 8 sub-layers) replaces the nxQuestion Spawn action; nxDendrite for branching networks. The nxQuestion approach still works in Fused 2025.4 and the 2026.1 beta.
