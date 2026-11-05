# Delayed offset rotations of edge splines (mtEdgeSpline Scale Offsets + Vibrate tag + XPresso)

- Source: Bite-Sized — EdgeSpline Offset — https://www.youtube.com/watch?v=2i4ui9lCuYo (2025-04-03)
- Host / generation: C4D; MeshTools **mtEdgeSpline**, XPresso (no particles)
- Goal: nested copies of a platonic's edge splines that follow its rotation with a controllable lag.

## Steps
1. **Platonic** as a child of **mtEdgeSpline** (mode **Standard** = one spline per edge); Display ▸ gradient off; hide the platonic.
2. **Scale Offsets**: count **5**, raise **Offset Size**; the offsets also have Rotation values — those get driven next.
3. Animation: platonic ▸ **Vibrate** tag, rotation on, **360°** on each axis, frequency **0.1**.
4. A **Null** named "Xpresso" as controller (room for user data) ▸ Programming Tags ▸ **XPresso**.
5. In XPresso: platonic node ▸ outputs **Coordinates ▸ Rotation H, P, B**; mtEdgeSpline node ▸ inputs via the blue port ▸ Object Properties ▸ offset **Rotation H, P, B** (vector, so pick the three components there).
6. Between each pair a **Math** node (Ctrl-drag to copy), function **Multiply**, second input = the control value.
7. Value **1** → each offset lags slightly behind the parent rotation; **2** → strongly scattered rotations; **−1** → reversed.

## Newest equivalent
Fused 2025.4.1 lets mtEdgeSpline handle n-gons, so the input mesh no longer has to be triangulated or quad-only.
