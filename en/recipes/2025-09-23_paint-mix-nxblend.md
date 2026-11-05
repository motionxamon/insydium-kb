# Mixing paint from three colored emitters (nxBlend + speed mapping)

- Source: Top Tip Tuesday — Paint Mix Sim — https://www.youtube.com/watch?v=ldpeVYB30QA (2025-09-23)
- Host / generation: NeXus (nxFluids SPH, nxBlend, Mapping)
- Goal: three paint streams that blend where they meet but keep ribbons of pure color.

## Steps
1. Three emitters (green, orange, …) circling on a spline (Align to Spline), nxGravity, **nxFluids SPH**.
2. **nxBlend**: Color only (default), **Strength 1000%** (max), Distance **3 cm** (10 cm = muddy; 2 cm = blending only at seams).
3. **Max Blend**: keep the full timeline (300 F) — stopping at 60 F leaves grainy, unblended seams on old particles.
4. **Mapping ▸ Speed → Strength**: 20 → 50 cm/s; Y min knot **0.1** (always a little blending) → fast streams/impacts mix strongly, slow outer areas keep stripes.
5. Render: mesh and transfer color (next recipe "Paint Mix Meshing").
