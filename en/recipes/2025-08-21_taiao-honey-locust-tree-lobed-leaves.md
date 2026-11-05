# Young honey locust tree (Taiao Plant 3 branch levels + Join meshing, Taiao Leaf lobed pinnate)

- Source: INSYDIUM Official Training — Taiao Honey Locust Tree — https://www.youtube.com/watch?v=uGQ2s-J1tog (2025-08-21)
- Host / generation: C4D; Taiao Plant (toPlant) + Taiao Leaf (toLeaf); standard viewport materials (any renderer)
- Goal: small tree with a hard-cut top, art-directed branch volume and compound leaves.

## Tip before modelling
Gather a winter (leafless) reference of the same species and sketch over the branch structure — summer photos hide it.

## Trunk
1. Taiao Plant ▸ trunk at default height (tree ≈ 12–15 ft); Global ▸ spline segments **5**; ring segments **24** (even quads); radius **~5**.
2. Modifier **Turbulence**, bias raised slightly (~0.1%) off the base; default noise is fine (scroll Seed to vary).

## Branches
3. Add **Branch**: **Branch on End off** (flat top). Count **15**, length variation, angle up + variation, **Gravity** modifier to pull them back down.
4. **Distribution curve** = silhouette of the crown seen from the side (x = along parent, y = how far out) — add knots to draw the volume.
5. **Branch length curve** along the parent: shorter at base and top, longer in the middle. Turbulence (bias off the base) + Gravity; re-raise angle and lower the base **angle bias** if they sag too much.
6. Add a second **Branch** layer (sub-laterals): count **5**, Branch on End off, angle up, length variation, weaker Turbulence + Gravity, distribution nearer the base.
7. Third level for leaves: Ctrl-drag-copy the sub-lateral layer under itself, shorten length a lot, soften turbulence.
8. Bark material on the trunk; enable the **propagate** button so all branch levels get it; **V tiles 6**.
9. Global ▸ Meshing type **Intersect → Join**, **Maximum join level 1** (only trunk + first laterals are welded — leaves hide the rest); subdivision 1.

## Leaf
10. Taiao Leaf: **10 length** segments, shape the profile, **Edge Noise**, 1 subdivision; **Midvein** with tapered tip and a small **petiole** offset.
11. Modifiers: **Fold** (shaped curve, out-and-around), **Furl**, light **Turbulence** (bias up).
12. Leaf type **Lobed**, no leaf on end (true to species), **count 18**; rachis profile thinner at the end, radius up a bit, length segments **40** (keep low for speed).
13. Leaflets: size variation + size bias curve, distribution variation, angle up with bias (rear ones less forward), **Twist** up, variation on everything. Rachis modifiers: Furl (droop) + Turbulence.

## Assemble
14. Last branch layer ▸ Add **Leaf**: Geometry **Basic → Custom**, link the leaf; size **0.5** + variation, count **8**, angle up + variation.
15. Everything stays procedural — e.g. shorten laterals/sub-laterals, raise distribution, count 10 to match reference.
