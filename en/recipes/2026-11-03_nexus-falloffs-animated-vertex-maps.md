# Animated vertex maps from NeXus GPU falloffs → drive nxExplosiaFX emission

- Source: Top Tip Tuesday — NeXus Falloffs (final Top Tip, #196) — https://www.youtube.com/watch?v=qv6TE9WtFhg (2026-11-03)
- Host / generation: **NeXus 2026.1 beta** — Cinema 4D and Blender (both shown)
- Products: NeXus (nxFalloffMap / Vertex Maps, nxFalloff layers, nxExplosiaFX)
- Goal: an organic "burning edge" that spreads across a mesh, written to a vertex map, and used as a mask so smoke/fire only emits from that edge.

## Scene tree (C4D)
```
Plane (100×100 segments — vertex density = map detail)
  └─ Vertex Map tag (auto-created)
nxFalloffMap  (INSYDIUM ▸ NeXus ▸ Presets)  ← Objects: Plane
  Falloffs (evaluated bottom → top):
    Blur              (top; few iterations — softens)
    Curve             (crush up → boost edge to full weight)
    Invert  [Blend: Multiply]   → keeps only the partial-weight band = leading edge
    Grow #2  (Shape off, high Spread/Reach → fills the interior)
    Grow #1  (Spread ~30, Shape 100% with Simplex noise → organic edge)
    Sphere   (radius ~20 cm, offset ~15 cm, keyframed across the plane)
nxExplosiaFX domain (sized around the plane)
  Sources: Plane, Surface Width 2
    Smoke / Temperature / Fuel → Weight by: Tag → drag the vertex map
```

## Steps
1. Subdivide the target (more points = finer map). Add **nxFalloffMap**, drop the mesh into Objects — a vertex map is generated (all 0 / red).
2. Add a **Sphere** falloff, animate it (keyframe position from one side to the other over ~100 frames). That alone is an animated vertex map.
3. Add a **Grow** layer above it: weight spreads outward from the sphere. Lower **Spread** (~30) to slow it. Its **Shape** (100%) uses noise to break the front: set noise to **Simplex**, bigger scale, **Low Clip 0 / High Clip 100**, **Contrast 1** (removes the default heavy clipping).
4. The noise keeps animating inside the filled area → add a **second Grow** above with **Shape off** and high Spread/Reach so it fills solid behind the noisy front.
5. Leading-edge trick: add **Invert** above and set its blend to **Multiply** — only the in-between weights survive (a soft band at the front).
6. Add **Curve** and crush it up so that band reaches full weight; add **Blur** with low iterations to smooth.
7. Speed of the spread = Spread of the first Grow (e.g. 60 = faster).
8. Use it: nxExplosiaFX → Sources → the plane; for Smoke, Temperature and Fuel set **Weight by: Tag** and link the vertex map. Masked emission needs higher values: raise Fuel (e.g. 3) and **Burn Rate** so all fuel burns.

## Blender differences
- No menu object: select the mesh → **Object Data properties ▸ NeXus Vertex Maps** (move the panel to the top of the stack) → **New** → creates an attribute **`nx_field`** (rename or convert to a vertex group if you need one; not required for EFX).
- Add falloffs/modifier layers there (Sphere radius 0.2 m, offset −0.1 / 0.1 m). New layers are added **below** — move each one to the top manually. Grow Spread 0.3, etc. (0–1 instead of %).
- Preview: enable the attribute display in the viewport (blue → white instead of C4D red → yellow).
- nxExplosiaFX Sources: emit from the plane, Fuel ~0.2, Temperature ~3000; Smoke/Temperature/Fuel **Weight by: Attribute → nx_field**.

## Gotchas
- Evaluation is bottom-up: the order of Sphere → Grow → Grow → Invert → Curve → Blur matters.
- Masked emitters look weak — boost fuel/temperature and burn rate.
- Memory layers (Grow, Decay, Delay, Freeze) reset on frame 1 and when scrubbing backwards — play from the start.

## Also announced in this video (next NeXus beta, "very soon" as of 2026-11-03)
Unified GPU dynamics: **cloth** driven by the same nx modifiers as particles (nxTurbulence, nxGravity), **ropes/cords** anchored to joints, **rigid bodies**, colliders shared with particle sims, **cloth tearing + fraying splines**, cloth maps, and **two-way coupling with nxExplosiaFX** (smoke lifts the cloth, the cloth pushes smoke away).
