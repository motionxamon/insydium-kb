# Data Mapping basics: gravity strength from radius, color brightness or a user value (xpGravity Mapping tab, Extended Data User Value)

- Source: Top Tip Tuesday — xpData Mapping — https://www.youtube.com/watch?v=QqtVVMajP5k (2023-07-04)
- Host / generation: C4D; G1 CPU X-Particles (xpEmitter, xpGravity Mapping)
- Goal: make particles fall at different speeds depending on their own data.

## Base
Particles with **xpGravity**, bouncing on a floor; emitter radius **20 cm**, variation **15** (→ 5–35 cm), Display color **Gradient Random**.

## Steps
1. xpGravity ▸ **Mapping** tab ▸ Add map. Parameter = **Gravity Strength** (any gravity parameter can be chosen).
2. Map To: Age → **Particle ▸ Radius**; Range Min **5**, Max **35** (computed from 20 ± 15).
3. Curve: X = radius range, Y = 0 → full strength. Default: big particles fall faster. Flip it (small = full, big = much less but not zero) → fake air drag on large particles.
4. Disable that map; add a new one mapped to **Color Brightness**: brightness 0 = no gravity, 100% = full → lighter particles fall faster. Raise the left knot a bit so dark ones still drop.
5. Custom data: emitter ▸ **Extended Data ▸ Physical Data ▸ User Value** **50**, variation **50** (0–100 per particle). New map → Gravity Strength to **User Value**; default 0–100 range already fits → low-value particles barely move.

## Gotchas
- Range must match the real data range, or the curve is squashed into part of it.

## Newest equivalent
NeXus modifiers have the same **Mapping** tab (Fused 2023.3+, looping in 2025.4; 2026.1 maps one layer to many targets) — use **nxGravity** Mapping or **nxDrag** for real air resistance (see "nxDrag realistic air resistance", 2025-02-11).
