# Bubbles trapped inside a viscous FLIP liquid (neighbour search)

- Source: Top Tip Tuesday — Viscous Bubble Rig — https://www.youtube.com/watch?v=fP-g5fC1PHs (2026-06-23)
- Host / generation: C4D, Fused 2025.4+ (nxFluids FLIP, nxQuestion neighbour search, nxMesher, nxScale) + Redshift
- Goal: from the same fluid particles, pick a random set that renders as bubbles, never at the surface.

## Setup
1. Emitter Groups tab: create **two groups** (Ctrl-click Create Group twice), mode **First Group Only** → all particles start in group 1 (honey); group 2 = bubbles.
2. nxQuestion:
   - `If Math ▸ Random (Time Variation: None, 0–20000) < 400` (per-particle fixed number → random sample; raise to 6000 while testing)
   - **AND** `Particle ▸ Neighbors (radius 10 cm) > 400` → only particles deep inside (surface particles have fewer neighbours)
     - Actions: Set Color yellow (debug) + **Set Group → Group 2**
   - `Else → Set Group → Group 1` (if a bubble drifts to the surface it turns back into liquid)
3. Mesh only the honey: **nxMesher** (group 1). Bubbles: **Redshift Object tag** on the emitter → Particles → sphere instances, Groups = group 2, bubble material.
4. Bubble sizes: **nxScale**, Groups Affected = group 2, layer **Set Value** (clamp off), radius 0.5 with lots of variation.
5. Tune bubble count by the Random threshold.

## Notes
- Calibrate the neighbour radius to scene scale (a 10 cm sphere ≈ search zone here) and the count threshold until no yellow particles touch the surface.
- Neighbour search needs nxFluids in the scene.
