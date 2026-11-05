# Feature notes: Jidou animation toolkit (jdDriver, jdAniMate, jdGeoRoll, jdFlowCam, jdGeoFlow)

- Source: Jidou - Tech Preview — https://www.youtube.com/watch?v=wfxpWHxZypQ (2025-12-08)
- Host / generation: C4D; Jidou suite (new in Fused 2025.4), INSYDIUM ▸ Jidou menu; not particle-based
- Goal: procedural motion-graphics animation (parameter drivers, start/end tweening, rolling, camera and object path moves) without hand keyframing.
- Tip: undock each Jidou tool into its own panel — the workflow is drag-and-drop between it and the Object Manager.

## jdDriver — drive anything with anything
- Drag objects into the driver list, then add parameters (menu or drag a parameter from the Attribute Manager); a child parameter is driven by its parent (e.g. cube X Pos → platonic Y Pos → torus Bank). Chains propagate limits, so re-parent to keep a branch independent.
- Per-parameter options: **Remap** (Min/Max, Include Zero) and **Clamp** (e.g. −150…150, −360…360). Works on any parameter (arc spline End Angle → Bend deformer Strength remapped 0–360).
- Built-in drivers, each with a waveform preview:
  - **Noise** — types Noise, Turbulence (octaves), Wavy Turbulence, Fractal Brownian Motion; Separate Seeds per parameter, Output Scale, Amplitude, Detail, Blend Loop, Auto Time.
  - **Wave** — Sine, Gaussian, Triangle, Ramp (sawtooth), Square, Pulse; Period, Phase, Offset, Amplitude, **Decay Rate** (dying bounce).
  - **Value** — slider with Step, Unit (Integer/Percent/Meter/Float/Degrees), Range min/max → build control rigs (robot arm joints with per-joint degree limits).
  - **Time** — start/end values over a time span with Speed, Start Time, Auto Time and a spline (presets: Linear, Gaussian = out-and-back loop).
  - **Color** — drives any colour swatch (object display colour, Redshift material colour); modes Time/Cycle/Random (Speed), two swatches or Gradient.
  - **Switch** — booleans (Enable on objects/lights): On time, Off time, Repeat Every (staggered blinking lights).
- Utilities: **Merge** (collects Value sliders into one control panel), **Sequencer** (Time drivers as offsettable/stretchable tracks; Offset Start/End stagger).

## jdAniMate — start/end tween
- Objects list ▸ **Store Start / Store End / Clear Stored**; ghost wireframe and path preview; Auto Time or a manual end (hold at the end); timing spline for easing; separate Position/Scale/Rotation **tracks** to offset each channel.
- Hierarchies and Cloners: random/sequenced **Variations** of position/rotation/scale per piece (assemble-from-parts); **Effect Position** includes the parent's motion → curved paths. Display ▸ **Export Spline** turns paths into splines.

## jdGeoRoll — rolling by handles
- Objects list (each gets a child **Handle**, Auto Size, colour), Colliders list (world Y=0 virtual floor by default, or any geometry e.g. a landscape), Gravity: World −Y / Local / Custom vector / **Object** (roll around another object's surface). Store Start for initial orientation. Move the handle → the object rolls/flops.

## jdFlowCam — procedural camera moves
- Add a standard or Redshift camera; **Connect Points** mode: add camera points; per point Focal Length, Focal Distance, orientation, **Weight** (time share), Tension, Slide, Ease, **Hold**, Spring, show cone. Motion (wobble with frequency), global easing spline, Up Vector.
- **Path** mode: Circle, Arc, Line (boom shots), Helix, Custom spline; alignment axis.
- **Target tag**: multiple targets with hold times and transition spline. **Banking**: automatic from path curvature (min/max, sensitivity, ease).
- Display: path/point colours, Export Spline (live), aspect guides (16:9, square, mobile; Ratio Fit or Absolute Size) for multi-format framing.

## jdGeoFlow — objects along flow points
- Same point options as jdFlowCam for geometry; set object axis and Align Axis to +Z for tangent following; **Deform** bends the object along the path; Paths mode and Banking; Export Spline.

## Replaces
Hand keyframing, XPresso/Set Driver rigs, Align-to-Spline tags and manual camera-rig splines. Fused 2025.4.1 adds Stop/Loop/Ping-Pong/Continue playback for jdFlowCam and jdGeoFlow (see also recipe 2026-10-13 jdGeoFlow emitter path).
