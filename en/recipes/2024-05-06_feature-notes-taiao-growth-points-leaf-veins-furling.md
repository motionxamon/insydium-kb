# Feature notes: Taiao 2024.2 — growth-point scattering, toLeaf vein layers, furling Angle Bias spline

- Source: Taiao Sneak Peek — Final Sneak Peek, Release Update Coming Soon 2024.2 — https://www.youtube.com/watch?v=TZsJmCkC9Nw (2024-05-06)
- Host / generation: C4D; Taiao (toPlant, toLeaf, toFlow) — procedural plants, no particles
- Status: preview of **Fused 2024.2** (9 May 2024)

## toPlant ▸ Growth Point layer (scatter on scene objects)
- Put any object (leaf, mushroom, primitives, polygon objects) on a surface (log); **Multi-Instance** mode for efficiency; point count e.g. 1,000 → 5,000.
- Distribution: drop a **Vertex Map** tag into the selection link; add a **shader** (noise with Low Clip) for extra randomness — cycle seeds, adjust **Tolerance**.
- Object scale and rotation with variation.
- **Spacing** separation: **Kill** removes instances that are too close; **Push** pushes them apart instead.
- Several Growth Point layers can stack (leaves + mushrooms + flowers).

## toLeaf ▸ new vein layering system
- **Mid Vein** layer: radius, profile curve, **petiole offset** (stalk extension), optional parallel veins (vein count). Veins always sit on the leaf surface however it's deformed.
- **Per-vein modifier stack**: e.g. Turbulence and Bend on one vein only; a furling modifier just for the petiole extension.
- **Lateral Vein** layer, four structures: Pinnate, Arcuate (curved tips), **Palmate** (fan), **Dichotomous** (branching, Split Count). Vein count, profile spline, angle, offset/angle variation, distribution spline; own modifiers. Lateral layers can stack (third order veins: shorter, angled, offset).
- **Remove Intersections** — one button, works across all vein levels.
- New **leaf preset library** (real-world leaves) in the Taiao preset browser.

## Furling modifier (toFlow, toLeaf, toPlant)
- Angle and Bias remain, plus an **Angle Bias spline** — one furling modifier can now do reverse furls and S-bends (no need to stack several).
- toFlow only: **Layer Bias spline** to target individual petal layers → easy unfurling of multi-layer flowers.

## Newest equivalent
Shipped in Fused 2024.2; see "Taiao leaf procedural veins" (2025-02-25) and "Taiao umbrella plant palmate leaf" (2025-09-04). For simulated organic growth rather than modelled plants, NeXus 2026.1 adds nxBioLogic and nxDendrite.
