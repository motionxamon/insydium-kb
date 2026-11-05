# Skinning bat wings with a cloth membrane (C4D Bind heat map + Cloth + Cloth Belt)

- Source: Bite-Sized — Skinning Bat Wings — https://www.youtube.com/watch?v=7pn1nJKwxZs (2025-07-31)
- Host / generation: C4D native character + cloth tools only (follow-up to an earlier bat-wing rig video); no INSYDIUM objects
- Goal: arm mesh skinned to the rig, membrane simulated as cloth pinned to fingers and body.

## Base
Separate objects: arm/finger mesh and wing membrane (membrane must be separate for cloth); rig with joints + controller nulls; a short flap animation.

## Steps
1. Select joints: right-click root ▸ **Select Children**, Ctrl-click to deselect the nulls, Ctrl-select the arm mesh.
2. Character ▸ **Bind**, mode **Heat Map** (alternatives Distance, Volumetric), defaults → **Skin** deformer appears under the mesh.
3. Check with Character ▸ **Weight Tool** (select a joint to see/paint weights); defaults were fine here.
4. Membrane: pre-made point **selection sets** along fingers and wing edge + a second set at the body side.
5. Membrane ▸ Simulation Tags ▸ **Cloth** (defaults).
6. Simulation Tags ▸ **Cloth Belt** → Belt On = arm mesh, select the point set, **Set** (points recolor), influence 100%.
7. The body-side flap sags: add a hidden **Cylinder** (on Z, scaled down), **make it editable** (belts don't work on parametric objects), second Cloth Belt to it with the other point set.
8. Re-enable the **dynamics** tags on the finger joints from the rig; back to frame 0, play with Subdivision Surface on.
9. Preview a full pair with a **Symmetry** object.

## Newest equivalent
INSYDIUM route (2026.1 beta): nxConstraints cloth with **nxPin** (pin To Object) or nxDeformer driving the membrane; CPU xpClothFX in Fused. Native C4D cloth as shown is simplest for this.
