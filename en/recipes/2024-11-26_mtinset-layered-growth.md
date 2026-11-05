# Geometric "organic" growth from stacked insets (MeshTools mtInset layers + animated spherical field)

- Source: Top Tip Tuesday — Inset Growth — https://www.youtube.com/watch?v=1KQjzMfJXRw (2024-11-26)
- Host / generation: C4D; **MeshTools** (mtInset), Redshift Sun
- Goal: shot from the 2024 Black Friday advert — dense inset patterns spreading across a curved panel.

## Base
Plane 800×950 with Wrap deformer (spherical bend) + Displacer (animated noise).

## Steps
1. Alt-click **mtInset** on the plane: amount **100%** + small offset (triangulated, poked look).
2. Alt-nest another mtInset: amount animated 40 → 60 %, offset for edge glints.
3. Next: static 45 %, offset 1.
4. Next: wide animation 20 → 80 %, offset 1, limited by a **Spherical field**; animate the field size outward (100 → larger).
5. Keep stacking (45 %, 46 %, 48 %, offset 1) each using the same field → dense detail grows with the field.
6. Render with an animated **Redshift Sun**: the many edges catch shadows and highlights; simple reflective material.
