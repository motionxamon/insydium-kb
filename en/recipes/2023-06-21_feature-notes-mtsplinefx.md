# Feature notes: mtSplineFX procedural spline generator (MeshTools, Fused 2023.3)

- Source: INSYDIUM Fused Release Update — July 2023 - mtSplineFX Sneak Peek — https://www.youtube.com/watch?v=NFFC34-hyjI (2023-06-21)
- Host / generation: C4D; MeshTools **mtSplineFX** (new in Fused 2023.3)
- Goal: procedural connecting splines for cables, lightning/electricity, animated HUD/FUI elements.

## Connections
- Drag objects into **Start** and **End** lists → connecting splines; connect to object **Origin**, **Points** or **Surface**. Multiple start/end objects, each toggleable; fully procedural.
- Inputs: polygon objects, splines, generators (MoGraph Cloners), X-Particles emitters.

## Motion & shape
- Noise-driven motion with a choice of noise types: Amplitude, Scale, animation Speed; layer a **small noise** for detail; **Falloff curve** maps the effect along the spline length.
- **Growth** tab for animating on; **Gravity**: Strength, Variation, Bias, Tension → hanging wires and cables.
- **Avoid** tab: avoid objects (an animated sphere pushes the splines aside).

## Forks and extra connections
- **Fork** layers: Length, Length Variation, Angle, falloff-driven noise, distribution along the parent; connect forks to the End object or a **Custom** object; animate in sequence with Growth.
- Child (duplicated) Fork layers fork from forks.
- **Nearest Distance** connections: link a new object to points along existing splines (Position slider, Max count).

## Replaces
Hand-built Tracer/Spline rigs and spline-dynamics cable setups. Still current in Fused 2025.x (see recipes "mtSplineFX Lightning", "Procedural Plasma Ball").
