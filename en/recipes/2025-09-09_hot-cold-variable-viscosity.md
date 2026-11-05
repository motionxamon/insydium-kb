# Hot runny / cold gloopy fluid that re-melts on contact (groups + nxBlend + mapped viscosity)

- Source: Top Tip Tuesday — Variable Viscosity — https://www.youtube.com/watch?v=_k0LatnQQJw (2025-09-09)
- Host / generation: NeXus (nxFluids SPH, nxConstraints Viscosity layer, nxQuestion, nxBlend) — pre-FLIP era
- Goal: lava-like fluid: slow particles cool & thicken, hot splashes re-melt them.

## Base
Animated emitter onto colliders; **nxGravity 300**; **nxFluids SPH** Smoothing Radius **150%** (less splashy), substeps 8; **nxConstraints Viscosity** layer with high stiffness (the gloop).

## Steps
1. Emitter groups: **Hot** (group 1, first group only — born hot) and **Cold** (group 2). [▶ 1:59](https://youtu.be/_k0LatnQQJw?t=119)
2. nxQuestion:
   - `If Group = Cold → Set Color black` (low **Weight** → fades to black)
   - `If Speed < 25 cm/s → Set Group Cold` / `Else → Set Group Hot` (re-evaluated every frame)
3. **nxBlend** Color, **Addition**, Distance 15, **Strength 1000%** → white (hot) particles brighten black ones on contact = re-melting. [▶ 6:59](https://youtu.be/_k0LatnQQJw?t=419)
4. **nxConstraints Mapping ▸ Color Brightness → Viscosity layer Stiffness**: black = full stiffness, white ≈ 0 (sharp falloff). [▶ 7:59](https://youtu.be/_k0LatnQQJw?t=479)
→ Continuous heat/cool/re-melt cycle.

## Newer options
FLIP/APIC (Fused 2025.4) maps viscosity directly (see "Chocolate Set"); 2026.1 beta adds non-Newtonian Flow Index / Yield Stress.
