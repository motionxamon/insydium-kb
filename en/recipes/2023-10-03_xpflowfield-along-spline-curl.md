# Particles flowing organically along a spline (xpFlowField Along Spline + Curl + To Spline layers)

- Source: Top Tip Tuesday — xpFlowField Spline Flows — https://www.youtube.com/watch?v=zA6fTkWvwwI (2023-10-03)
- Host / generation: C4D; **CPU xpFlowField** (Dynamics) — also drives NeXus/GPU setups in the same scene
- Goal: a custom velocity field so a fluid-looking particle stream follows a helix (or logo/text splines), fully procedural.

## Base
Emitter aligned to the start of a **Helix** spline.

## Steps
1. X-Particles ▸ Dynamics ▸ **xpFlowField**; resize its bounds to enclose the whole spline (particles only react inside). [▶ 0:41](https://youtu.be/zA6fTkWvwwI?t=41)
2. Delete the default **Random** layer. [▶ 1:10](https://youtu.be/zA6fTkWvwwI?t=70)
3. Add **Along Spline** layer, spline = Helix. [▶ 1:30](https://youtu.be/zA6fTkWvwwI?t=90)
4. Particles escape because flow-field strength defaults to **10%** → set **100%**, and new layers have **falloff on** (fades to 0 at 50 cm) → switch the layer falloff **off**. [▶ 2:16](https://youtu.be/zA6fTkWvwwI?t=136)
5. Lower **Cell Size** for more vectors / detail (slower, fine at this count). [▶ 2:43](https://youtu.be/zA6fTkWvwwI?t=163)
6. Add **Curl** layer: in **Normal** blend it overrides everything; keep Normal but **lower the layer strength** so Along Spline still contributes. [▶ 3:39](https://youtu.be/zA6fTkWvwwI?t=219)
7. Field mode **Direction → Velocity** (vectors now also set speed); raise Curl strength a bit. [▶ 4:07](https://youtu.be/zA6fTkWvwwI?t=247)
8. Add **To Spline** layer (Helix), falloff off, strength **~3%** — gently pulls particles back to the path. [▶ 4:55](https://youtu.be/zA6fTkWvwwI?t=295)
9. Hide the flow field; edit the helix (e.g. start radius) and the flow updates. [▶ 6:03](https://youtu.be/zA6fTkWvwwI?t=363)

## Gotchas
- New layers default to falloff on and the object strength to 10% — both cause leaks.

## Newest equivalent
Fused 2024.3: keyframable xpFlowField layers. NeXus 2026: **nxFlowField** (with a **Cyclic** layer in 2026.1); alternatives **nxFollowGeo** (multi-spline, Guide/Force, Fused 2025.4) or **nxWarp Path** (2026.1).
