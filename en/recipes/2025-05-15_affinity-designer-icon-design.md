# Designing a NeXus-style tool icon in Affinity Designer (64 px grid, booleans)

- Source: Bite-Sized — Icon Design — https://www.youtube.com/watch?v=iq9bdSxOdGE (2025-05-15)
- Host / generation: Affinity Designer (INSYDIUM's own icon workflow; sheets go on to Photoshop for alpha); not an X-Particles technique
- Goal: build a new spin-modifier icon matching the NeXus icon sheet.

## Base
File ▸ New in **pixels**, 500 × 500 (save as your own template). **Insert Artboard** at document size with a **dark background** (helps when alphas come back from Photoshop). Preferences ▸ User Interface ▸ artboard background grey level to darken the surround.

## Steps
1. View ▸ **Show Grid**; View ▸ **Grid and Axis** ▸ Advanced: spacing **64 × 64**, uniform, no second axis, **Divisions 2** → a center mark in each 64 px icon cell.
2. Rectangle from the cell center with Ctrl+Shift+Alt to fill the cell; orange fill (match the icon palette).
3. **Rounded corner** via the red node handle (or slider).
4. **Stroke** width **7**, order set to **behind** the fill so scaling doesn't eat into the shape.
5. White circle from the center (snapping shows the center); color picker needs the extra click to apply the sampled color.
6. Ring: duplicate the circle, scale it down from center, select both (V) ▸ **Subtract**.
7. Cut a gap: Pen tool, Shift-constrained shape over the segment ▸ Subtract.
8. Arrowhead: **Triangle** shape (Shift), rotate into place on the ring; select both ▸ **Add/Combine** into one element; scale down.
9. Small white circle in the middle = the particle; keep separate or combine. Check the green/red snapping guides confirm it is centered.
