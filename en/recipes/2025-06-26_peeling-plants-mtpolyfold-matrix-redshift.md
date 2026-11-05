# Plants growing on a peeling surface (mtPolyFold selection unfold + MoGraph Matrix + RS Object tag, Taiao plants)

- Source: Bite-Sized — Peeling Plants — https://www.youtube.com/watch?v=TGK5vMt8nj0 (2025-06-26)
- Host / generation: C4D; MeshTools **mtPolyFold**, Taiao plants (pre-animated), MoGraph Matrix, Redshift
- Goal: a capsule peels/unfolds from its base up, covered in small animated Taiao plants.

## Steps
1. Make a few small abstract animated **Taiao** plants (reset to frame 0).
2. Capsule → keep a hidden copy; make the other editable, select the base polygons ▸ **Store Selection**.
3. MeshTools ▸ **mtPolyFold**, capsule as child. Distribution **Random → Selection** (uses the stored set) so folding starts at the base. For irregular meshes switch direction from Clockwise to **Axis** (+Y).
4. Add some variation; keyframe the unfold from frame 0 to 150 so it peels all the way up.
5. Put the PolyFold under a **Subdivision Surface** (smoother surface for the clones) and hide it.
6. MoGraph ▸ **Matrix**, Mode **Object** = the Subdivision Surface; count ~2,000 (20,000 is too many).
7. Matrix ▸ **RS Object tag** ▸ Mode **Custom Objects**, pick the plants. Matrix Transform ▸ **Pitch −90°** so stems point outward.
8. **Random effector** on the Matrix: small position (2/2/2), heading rotation, **Uniform Scale**; tame the resulting size with the RS tag's **scale multiplier**.
9. Light with an RS Dome, warm background.

## Gotchas
- Matrices only render once the RS Object tag has objects assigned; press refresh on the Random effector after changes.
