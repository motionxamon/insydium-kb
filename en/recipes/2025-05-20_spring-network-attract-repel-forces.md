# Organic springy particle network (nxConstraints birth springs + Forces layers, nxQuestion group switch & pin)

- Source: Top Tip Tuesday — Particle Forces — https://www.youtube.com/watch?v=PIgXQtSgnMY (2025-05-20)
- Host / generation: C4D; NeXus inside X-Particles (nxConstraints, nxQuestion, nxDrag) + C4D Fields + xpTrail
- Goal: a flower-shaped mesh of linked particles that inflates where a field passes, with pinned edges.

## Base
Extrude cap from a 3-petal Flower spline; emitter Object/polygon area, **Shot 10,000**. Groups **initial** + **repulsion**, mode **First Group Only**. nxQuestion: inside a moving field → colour red + **Set Group repulsion**.

## Steps
1. **nxConstraints "birth"**: birth springs, search **40 cm**, **Limit 6**, **Stiffness 90**, breaking **None**. Emitter ▸ Display ▸ **Display Constraints** to see them. [▶ 1:57](https://youtu.be/PIgXQtSgnMY?t=117)
2. Same object ▸ add **Forces** layer: attraction beyond ~20 cm, repulsion within ~10 cm, **Limit 32** → push-pull wobble. [▶ 2:42](https://youtu.be/PIgXQtSgnMY?t=162)
3. Order: group-change question at the top of the stack. **nxQuestion "pin"** last (after constraints), Groups Affected **initial**: if Field value > 0 → **Set Speed 0**. Field = the Flower spline, Distance mode **Radius 20** → perimeter locked. [▶ 3:47](https://youtu.be/PIgXQtSgnMY?t=227)
4. **nxConstraints "repel"** below birth: Forces layer radius **80/80**, ~**20% more repulsion**, Groups Affected **repulsion** → particles inflate as the field converts them. [▶ 5:27](https://youtu.be/PIgXQtSgnMY?t=327)
5. Optional: **nxDrag** last, Multiplier **~100,000** to settle after the blast. [▶ 6:07](https://youtu.be/PIgXQtSgnMY?t=367)
6. Render: **xpTrail**, Algorithm **Constraints**, type = the birth springs. [▶ 6:59](https://youtu.be/PIgXQtSgnMY?t=419)

## Newest equivalent
2026.1 beta: **nxPin** anchors particles by falloff/group (cleaner than speed-0 pinning); **16 nxFalloff modes** incl. Spline replace C4D fields; NeXus 2026 uses **nxTrail**.
