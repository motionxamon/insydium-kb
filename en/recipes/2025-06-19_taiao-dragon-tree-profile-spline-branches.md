# Dragon tree house plant (Taiao Plant branches + Profile modifier spline, Taiao Leaf, Redshift)

- Source: INSYDIUM Official Training — Taiao Dragon Tree — https://www.youtube.com/watch?v=f6VqOjOtBH4 (2025-06-19)
- Host / generation: C4D; Taiao Plant / Leaf (modifiers: Gravity, Profile, Fold, Turbulence, droop layers); Redshift
- Goal: Dracaena-style plant — straight trunk, two upturned branches, half-moon leaf bases, long wavy leaves, dead lower leaves.

## Trunk and branches
1. **Taiao Plant** ▸ Trunk: Height **30 cm**, Radius 2–3, nearly straight with light taper; Global Settings ▸ **Segment Resolution 0.5**; raise Ring Segments.
2. Add **Branch**: turn off the end branch, Count **2**, Distribution **Spiral → Alternate**; add points on the position spline to place them close together near the top. Length ~25, little taper.
3. Branch Modifiers ▸ **Gravity** with **negative strength** (can go beyond −100) so branches bend up; raise Weight so they straighten along their length; tune Angle.

## Leaf stalks with a half-moon profile
4. Add a Branch to the branch: end branch off, Count **10**, distribution points push them to the top; angle out; profile tangent widened for a bulb at the base. Ring segments **12** on both branch levels.
5. Circle spline, Plane/axis **X**, make editable. Branch ▸ Modifiers ▸ **Profile**, drop the spline in; move points into a "smile" so bases hug the parent branch.
6. Profile **Bias**: drag the end down and curve it so the shape returns to a round section before the leaf.
7. Global Settings ▸ Subdivisions 1.
8. Two droop/bend modifier layers: first pulls the stalks in toward each other (bias at the bottom); second with **Blend Mode Add** bends them out; add variation.

## Leaf (Taiao Leaf)
9. Length **55**, segments **50 × 4**, Subdivision 1; profile spline with two extra points for a long blade; **Edge Noise**; **Mid vein** with a tapering profile.
10. Modifiers ▸ **Fold** with many random knots on its spline → wavy blade; **Turbulence** Scale 350, Strength 70, Bias 10; two more droop layers to lift the tips.
11. Leaf stalk ▸ **Leaf** layer: count 0, **Leaf on End**, Geometry **Custom** = the leaf; scale + size variation. Hide the joint by lowering vein radius, leaf position and the branch end scale.
12. Dead leaves: Ctrl-drag copy the leaf-stalk branch layer, delete its droop layers, move distribution lower, add a new downward droop layer, Count 6, smaller leaves.

## Redshift
- Leaves: legacy **RS Material** (for backlighting/translucency): leaf texture → diffuse and translucency colour, weight 1; low reflection, high roughness. Brown copy for dead leaves (second leaf material slot).
- Trunk: RS Standard, reflection off, normal map in **Raw** colour space → Bump Map node set to **Tangent Space Normal**.
- Branches: trunk material blended to green with **Material Blender**, blend = inverted ramp with noise; green subsurface. Leaf stalks: green with subsurface and some reflection.

## Newest equivalent
Still Taiao; toLeaf venation presets (2024.2) can replace the hand-built mid vein.
