# Plants riding a viscous fluid (editable particles → MoGraph Matrix → Cloner of Taiao plants)

- Source: Top Tip Tuesday — Fluid Plant Flow — https://www.youtube.com/watch?v=j8YPLZGWPBw (2024-10-08)
- Host / generation: C4D; cached NeXus viscous fluid + MoGraph + **Taiao**
- Goal: a flowing stream of foliage/flowers following a thick continuous fluid.

## Steps
1. Fluid should be thick and continuous (no splashy gaps).
2. **Matrix** ▸ Object mode = emitter, distribution **Vertex**, Align Clone off. Emitter ▸ **Editing ▸ Editable** on → matrix updates per frame.
3. Thin points: **Random effector** with position off, **Visibility** on; tune Min/Max (rename "random vis").
4. Plants: **Taiao preset browser** (preset pack from customer account; e.g. wood sorrel), Global ▸ **Organ mode Polygons**; fewer flowers (4) / leaves (~42), smaller radius.
5. **Cloner** Object mode = Matrix, **Multi-Instance**, align off; plant(s) as children (add a bright orange flower preset too).
6. **Plain effector**: position 0, rotation P 90 (upright), uniform scale −0.5. Second Random effector: big heading, small pitch/bank, scale −0.2.
