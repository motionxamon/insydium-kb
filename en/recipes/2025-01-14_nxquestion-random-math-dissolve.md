# Randomised field-triggered dissolve (nxQuestion Field + Group + Math Random)

- Source: Top Tip Tuesday — Random Math Effects — https://www.youtube.com/watch?v=wO5-UoWNTkA (2025-01-14)
- Host / generation: C4D; NeXus G2 (nxFollowGeo, nxTurbulence, nxQuestion) on an xpEmitter; C4D spherical field
- Goal: text-hugging particles released by a moving field, then fading out at staggered times instead of all at once.

## Base
xpEmitter from a Connect/join of text → **nxFollowGeo** using the same join as surface + strong **nxTurbulence**. An animated spherical field sweeps across.

## Steps
1. Emitter ▸ Groups: Ctrl-click **Add Group** twice, mode **First Group Only** (all born into group 1).
2. nxFollowGeo ▸ Groups Affected: **group 1** only.
3. **nxQuestion** ▸ Field tab: add the animated sphere field.
4. Question 1: Particle **Field > 0** (anywhere inside) → Action **Set Group = group 2** → freed from FollowGeo, turbulence takes over.
5. Question 2: Particle **Group = 2** → Action **Set Age 0** (once only) + Action **Set Lifespan 45** frames.
6. Uniform 45 F looks like a snap, so add a child question under Q2 set to **And**: **Math ▸ Random**, Time Variation **Particle**, range **0–100**, condition **> 70**. Move both actions under this sub-question.
7. Each frame every particle draws a new number, so the age reset/lifespan triggers at different moments → soft, scattered fade.

## Newest equivalent
nxFalloff (16 modes in the 2026.1 beta, e.g. Sphere) can replace the C4D field; Fused 2025.4 added built-in variation to nxQuestion, which may save the random sub-question.
