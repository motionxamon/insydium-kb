# Plants growing on a peeling surface (mtPolyFold selection unfold + MoGraph Matrix + RS Object tag, Taiao plants)

- Source: Bite-Sized — Peeling Plants — https://www.youtube.com/watch?v=TGK5vMt8nj0 (2025-06-26)
- Host / generation: C4D; MeshTools **mtPolyFold**, Taiao plants (pre-animated), MoGraph Matrix, Redshift
- Goal: a capsule peels/unfolds from its base up, covered in small animated Taiao plants.

## Steps
1. Make a few small abstract animated **Taiao** plants (reset to frame 0).
2. Capsule → keep a hidden copy; make the other editable, select the base polygons ▸ **Store Selection**. [▶ 0:43](https://youtu.be/TGK5vMt8nj0?t=43)
3. MeshTools ▸ **mtPolyFold**, capsule as child. Distribution **Random → Selection** (uses the stored set) so folding starts at the base. For irregular meshes switch direction from Clockwise to **Axis** (+Y). [▶ 1:28](https://youtu.be/TGK5vMt8nj0?t=88)
4. Add some variation; keyframe the unfold from frame 0 to 150 so it peels all the way up. [▶ 2:05](https://youtu.be/TGK5vMt8nj0?t=125)
5. Put the PolyFold under a **Subdivision Surface** (smoother surface for the clones) and hide it. [▶ 2:45](https://youtu.be/TGK5vMt8nj0?t=165)
6. MoGraph ▸ **Matrix**, Mode **Object** = the Subdivision Surface; count ~2,000 (20,000 is too many). [▶ 2:45](https://youtu.be/TGK5vMt8nj0?t=165)
7. Matrix ▸ **RS Object tag** ▸ Mode **Custom Objects**, pick the plants. Matrix Transform ▸ **Pitch −90°** so stems point outward. [▶ 4:08](https://youtu.be/TGK5vMt8nj0?t=248)
8. **Random effector** on the Matrix: small position (2/2/2), heading rotation, **Uniform Scale**; tame the resulting size with the RS tag's **scale multiplier**. [▶ 4:55](https://youtu.be/TGK5vMt8nj0?t=295)
9. Light with an RS Dome, warm background.

## Gotchas
- Matrices only render once the RS Object tag has objects assigned; press refresh on the Random effector after changes.
