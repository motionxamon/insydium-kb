# Forget-me-not wildflower patch (Taiao Flower, Taiao Leaf, Taiao Plant custom parts + growth point)

- Source: INSYDIUM LIVE! — September 2023 – NeXus, Taiao & X-Particles — https://www.youtube.com/watch?v=uS_zr-Jf178 (2023-09-27)
- Host / generation: C4D; Taiao (no particles); standard C4D gradient materials (any renderer)
- Goal: a small five-petal wildflower, its leaf and a branching 45 cm stem, then scattered into a patch.

## Steps
1. **Taiao Flower** (wireframe on); disable Stamen and Petals to work on the base. **Pistil** width **1**, lower height; match the **Receptacle** (they blend into each other); bend its profile spline so it sits well on branches.
2. **Sepals**: count **5**, lower position, pull in. Default **Furling** modifier → shape Up, Bias towards the bottom = small arc. Geometry ▸ Profile: add points/tangents for a clean half-leaf shape.
3. Sepal modifiers: **Fold** (with a curve, fold angle closes them into a cone) + a second **Furling** to flare the tips back out.
4. **Petals**: count **5**, smaller and thinner profile; adjust the default Fold + Furling to separate them; Orientation **Twist** to stop overlap. The geometry profile is forgiving — add points as needed.
5. **Stamen**: count **5**, distribution **Whorled** (ring); reshape the profile into a half-circle and drop the height → tiny balls; radius ~**0.8**.
6. Materials: simple gradient materials dragged into each part's Materials tab (stamen, petal, pistil, receptacle).
7. **Taiao Leaf**: segments **12 × 4**; reshape the profile (add 2 points, round tangents); **Edge Noise**; enable **Veins** (mid vein, thinner, petiole offset). Modifiers: **Fold** with curve eased off at the tip + two **Furling** layers (gravity droop, turbulence with bias and reduced scale). Assign Leaf material to the leaf, stem material to Stalk + Mid Vein.
8. **Taiao Plant** ▸ **Trunk**: height **45** (real ones 45–60 cm), radius **0.3**; Global ▸ **Segment resolution 1** for smoother geometry. Stem material with the propagate-to-children button. Plant **Turbulence** (low strength, larger scale); cycle Seeds.
9. **Branch** layer: disable the end branch, **5** branches angled up with variation; **Length along Branch** curve so lower branches are longer. Modifiers: soft Turbulence (biased off the tip), Furling up, second Furling down — set its blend to **Add** or it overrides the first.
10. Second **Branch** layer (flower stalks): **7**, no end branch, angled up; **Gravity −250** (upwards) with variation + Furling at the tips for the droop.
11. **Add Part ▸ Custom Object** = the flower; smaller size + variation, Heading **360** with **100%** variation. Ctrl-drag the custom object into the end of each branch chain (and the trunk) to cap tips with a bigger flower.
12. Trunk ▸ **Leaves** part: no end leaf, Geometry mode **Custom** = Taiao Leaf; size smaller towards the top, orientation up + variation.
13. Scatter: **Add Part ▸ Growth Point**, drop the plant in, raise count/width, use variation → a patch of different plants.

## Gotchas
- Default Trunk/Branch values are tree-sized — scale everything down for small plants; low resolution on thin branches is fine at this size.

## Newest equivalent
Same Taiao objects today; Fused 2024.2 added growth-point scatter improvements and taLeaf venation + presets. For a whole meadow see "Taiao Grass Meadow" (2023-05-02).
