# Basic bat-wing rig (C4D Joint tool, IK chains, pole vector, IK Dynamics, Mirror tool)

- Source: Bite-Sized — Rigging Bat Wings — https://www.youtube.com/watch?v=sDGgDroAl1E (2025-07-17)
- Host / generation: C4D native Character tools only (no INSYDIUM objects)
- Goal: a simple flappable bat-wing rig with springy finger bones, mirrored to both sides.

## Steps
1. Top view: **Joint tool**, Ctrl-click to place shoulder → humerus → radius/wrist (arm chain). Click off, then draw three separate 3-joint chains for main, middle and pinky fingers. Moving a joint repositions/scales its neighbours.
2. Name everything with a side prefix for mirroring: `R_shoulder`, `R_H` (humerus), `R_R` (radius), `R_W` (wrist), `R_mainfinger…`, `R_middlefinger…`, `R_pinky…`. Parent the finger chains under the wrist.
3. Select humerus + wrist (skip radius) ▸ Character ▸ **Create IK Chain** → IK tag + wrist goal null.
4. Controller: Cube ▸ make editable ▸ select all edges ▸ **Edge to Spline**; scale down, bright display colour, place at the wrist; name `R_wing_controller`, child of the shoulder; goal null → child of the controller.
5. Wrist joint ▸ **Transform Constraint** tag, rotation only, target = controller (rotate the controller to fix the flip) → fingers follow controller rotation.
6. **Pole vector**: null `pole` with a blue sphere display; drop it in the IK tag's Pole Vector field; Display ▸ pole line from **Joint** instead of Root. Stops elbow flipping.
7. Finger dynamics: Create IK Chain on each finger chain, **delete the generated goals**, select the three IK tags ▸ Dynamics ▸ **Enable** (works only on playback; Strength slider controls springiness).
8. Select shoulder ▸ **Mirror tool** ▸ Naming: replace `R_` with `L_` ▸ Mirror. Animate both controllers for a flap.

## Gotchas
- Dynamics only evaluate during playback — extend the timeline to test.
- No finger controls; this is a basic background-creature rig.
