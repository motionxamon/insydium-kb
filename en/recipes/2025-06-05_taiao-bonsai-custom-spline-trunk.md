# Procedural bonsai from a custom trunk spline (tiPlant custom spline + modifiers, tiLeaf, MeshTools Spline Sample, Redshift)

- Source: INSYDIUM Official Training — Taiao Bonsai — https://www.youtube.com/watch?v=_J9dbYtwkVY (2025-06-05)
- Host / generation: C4D; Taiao (tiPlant, tiLeaf) + MeshTools; Redshift
- Goal: a gnarly, fully procedural bonsai whose trunk shape is drawn by hand, with branching, sub-branches and translucent leaves.

## Trunk spline
1. Put the reference image in the Front view background and draw the silhouette with the **B-Spline** tool (smooth curves, no Bezier handles to manage). Push points in depth with the **Magnet** tool so it isn't flat.
2. **MeshTools ▸ Spline Sample** with the spline as input, Method **Distance** (demo value 5) for evenly spaced points (intermediate points stretch). Make editable (**C**) → trunk spline. Hide it / park it as a child.

## Trunk (tiPlant)
3. **tiPlant ▸ Plant Layers ▸ Trunk**, default size (scale the whole tree later). Drop the spline into the trunk's **Custom Spline** link.
4. Wireframe check (N~B): raise **Ring Segments** for even topology. Shape the **Radius** curve: a taper point at the end and a few random bulges.
5. Modifiers: **Displacer** with a Noise (more contrast, bigger scale); add **1 global subdivision** to fix the faceting; **Twist** ≈ 570; optional second **Displacer** set to **Add** with a dense noise at low strength for extra breakup.

## Branches
6. Add a **Branch** layer. If the result looks broken, switch **Branch on End** off — the trunk end radius is closed to nothing, so an end branch distorts it.
7. ~7+ branches; distribute some high, some low; angle up with variation, longer, thinner profile with variation.
8. Branch modifiers: **Turbulence** (bias off the end, smaller scale), **Twist** inherited from parent at full, light **Displacer** (thin branches exaggerate it — keep strength low).
9. Sub-branches: another Branch layer on the branch layer, Branch on End off, distribution further up, angled up, more length variation, smaller radius. Modifiers: **Gravity** negative (can go past 100) with variation, so tips droop; **Turbulence** (bias off end, tweak scale and seed).

## Leaf (tiLeaf)
10. **tiLeaf**: more subdivisions, **Thickness 1**, oval **Profile** (mid point stretched, blunt tip), a little edge noise.
11. Veins: **Mid vein** with thinner profile; **Lateral veins** thinner, angled up, **Offset** so they don't align, angle **Bias** (more angle near the top). Modifiers: **Bend**, **Fold** (shape curve, kept away from the tip), **Filling**.
12. On the last branch layer add a **Leaf** layer ▸ Geometry **Custom** ▸ drop the tiLeaf (child of the plant). Size 5, variation 10; Orientation angled up with variation; ~10 per branch.

## Redshift
13. Render settings ▸ Advanced: default light off; **Redshift Dome Light** with an HDR; Redshift Camera with background override (black).
14. Trunk material: bark color texture → color; tile with mapping V ≈ 6; low reflection; normal map with color space **raw** → **Bump Map** node (normal) → bump. On the trunk layer, use the **propagate** icon to push the material to all branch layers.
15. Leaf: use the Redshift **Material** (the one with translucency, not Standard): green diffuse, lighter/less saturated back-face/translucency color, some translucency weight. A **Sun & Sky** rig shows veins and shadows through the leaves.

## Gotchas
- Everything stays procedural — edit the trunk spline later and the tree follows.
