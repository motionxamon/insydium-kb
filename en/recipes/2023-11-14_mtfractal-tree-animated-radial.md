# Animated high-poly fractal tree (mtFractal Tree mode, Multi-Instance, Levels + mtInset + mtShellGen)

- Source: Top Tip Tuesday — mtFractal Tree — https://www.youtube.com/watch?v=2U0MH6xdGAk (2023-11-14)
- Host / generation: C4D; **MeshTools** (mtFractal, mtInset, mtShellGen)
- Goal: an intricate fractal tree of copies that unfolds when animated, still smooth in the viewport.

## Steps
1. **mtFractal** with a tall **Cube** child; Core Shape **Tree** (default); Clone Type **Multi-Instance**.
2. **Steps** (default 3) add levels; **Branches** per step 2 → 3 for a 3D tree (explore at 4 steps / 2 branches). Growth and scale defaults kept.
3. Animate **Angle Open** (default 45°; 0 = closed, 180° = folded back at the base).
4. Animate **Radial** angle (0 = looks like a single branch) — at **6 steps / 4 branches** it folds out dramatically.
5. **Number of Copies**: 2 mirrors, 4 or 6 give evenly spaced copies (reset to 1).
6. **Levels**: add a level for **Step Level 2** to override angles just there (its angles start at 0), or switch its type **Angle → Branch** to set a per-step branch count (e.g. 2 vs 4 elsewhere). Levels stack.
7. Decorate: move the cube into **mtInset** (raise amount, enable the option that hides the inset faces → wireframe look), put the inset into **mtShellGen** (add thickness), then place the shell gen back into mtFractal.
8. Animate Radial; add steps/branches — viewport stays responsive thanks to multi-instances.
