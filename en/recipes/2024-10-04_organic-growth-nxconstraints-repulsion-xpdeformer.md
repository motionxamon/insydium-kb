# Organic wrinkle growth creeping over a statue (nxConstraints Forces repulsion + xpDeformer, vertex-map-driven nxQuestion groups)

- Source: INSYDIUM Training — Organic Growth - Part 1 — https://www.youtube.com/watch?v=eJXaD9gVMsE (2024-10-04)
- Host / generation: C4D; NeXus GPU (nxConstraints, nxQuestion, nxDrag) on an orange xpEmitter + **xpDeformer** and xpCollider tag; C4D Vertex Map + Fields; Alembic bake (Redshift render in Part 2)
- Goal: a bulging, wrinkling growth that spreads along an art-directed path over a stone bust, leaving the rest untouched.

## Base
- Bust model with existing wrinkles/hair detail (smooth meshes look less interesting). xpSystem with the CPU folders (Dynamics, Generators, Modifiers, Questions) deleted.
- Mesh scale matters: the demo bust is huge (over 5 m wide, 7 m tall); a smaller model (wolf head, ~half size) needs roughly **half** the constraint radii and less repulsion.

## Steps
1. **xpEmitter** ▸ Object, source = bust, emit from **Points** with **One Particle per Source Element**; Emission **Shot**, speed 0, radius 2 → one particle per vertex.
2. **xpDeformer** as a child of the bust; set its emitter link (nothing deforms until the emitter is assigned). Test with an nxTurbulence, then delete it.
3. **nxConstraints "birth"** ▸ Connections at Birth: Connection Limit 16, radius 40 cm, high Stiffness, **Break Type None** (default break is 50% stretch).
4. **nxConstraints "forces"** (below) ▸ **Forces** layer: Attraction radius **10 cm**, Repulsion radius **20 cm** (keep repulsion ≈2× attraction), Repulsion strength 30% → wrinkles/inflation.
5. Path: draw a spline in Front view over the areas to grow (beard, halo round the head), tweak depth in X-ray; spline interpolation **Uniform**.
6. Bust ▸ **Vertex Map** tag ▸ Use Fields; add a **Spherical Field** with **Align to Spline** tag, Position keyed 0% (F0) → 100% (F200), keys set to **Linear**. Add a **Decay** layer at 100% on top so painted weight stays; enlarge the field and raise Remapping Inner Offset for a crisper edge.
7. Emitter ▸ Groups: add 2 groups, emit into group 1 only. nxConstraints "forces" ▸ Groups Affected = **group 2**.
8. **nxQuestion** Q1: particle inside Field (Fields tab = the Vertex Map) → actions **Set Color** (yellow, for checking), **Set Group 2**, **Set Age 0** (once).
9. Q2: Group = 1 → **Set Speed 0**, so birth springs can't drag the untouched face.
10. Anti-collapse: copy the bust (no deformer/tags), make it invisible, add **xpCollider** tag with Bounce and Friction off.
11. **nxDrag** below the question: density = sea water, Strength **800%**, Mapping ▸ **Age** over 0–70 frames on the strength multiplier (the age reset in step 8 makes each region start free). Final: Strength 500%, repulsion raised to **50%**.
12. Bake: **Subdivision Surface** (1 level) around the bust ▸ Bake as **Alembic**, Selection Only, 300 frames, **Vertex Maps** checked in optional data.
13. On the Alembic: **Smoothing deformer**, Iterations 10 (50 to test), Fields = the baked vertex map → only the grown area is smoothed.

## Gotchas
- This is not a real soft body: push repulsion too far and folds intersect, which breaks refraction in the render — tune strength/radii and inspect late frames.
- Can't collide against the deformed mesh itself — use the hidden undeformed copy.
- Alembic = fixed point count, so playback can be retimed later.

## Newest equivalent
NeXus 2026.1 beta: **nxDeformer** (mesh follows particles, with tearing) replaces xpDeformer, **nxPin** can anchor the untouched points instead of Set Speed 0, and the **Wet**/Spline nxFalloff modes can drive the reveal; for procedural growth patterns see **nxBioLogic** (differential growth).
