# Feature notes: Taiao overhaul — modifier stacks, growth animation, layered forces, toLeaf, toFlower (Fused 2023.3)

- Source: INSYDIUM Fused Release Update — July 2023 - Taiao Sneak Peek — https://www.youtube.com/watch?v=z3ZC4EI9LOk (2023-06-28)
- Host / generation: C4D; Taiao (INSYDIUM plant generator), Fused 2023.3 — not particle-based
- Goal: overview of the rebuilt Taiao plant, leaf and flower tools.

## toPlant
- **Per-layer modifier stacks**: Furling, Turbulence, Displacement, Twist… stacked procedurally on each plant layer; layers can be animated with **Fields**.
- **New growth system**: every plant layer grows individually; supports **keyframed leaves** and keyframed custom objects. Leaf trigger mode **Sequence** = animate bottom → top; or drive the growth with Fields.
- **Forces** rebuilt, fully layer-based: strength per plant layer and along trunk/branch length, Field control, **per-leaf bending**.

## toLeaf (new)
- Procedural leaf generator with realistic **vein** structures; same modifier stack (multiple folds, furling, turbulence).
- Single or **lobed** leaves; control of profile, orientation, distribution and size variation.

## toFlower
- Now a standalone object; flower parts are **layers**, several of one type allowed (two petal layers). **Copy** layers generate from a parent (e.g. stamen from a parent stamen). Each layer has its own modifier stack.

## Replaces
Old single-Furling Taiao workflow and hand-animated plant growth. Later: Fused 2024.2 added growth-point scatter and toLeaf venation presets (see recipes "Taiao Animated Custom Leaf Growth", "Taiao Leaf Procedural Veins").
