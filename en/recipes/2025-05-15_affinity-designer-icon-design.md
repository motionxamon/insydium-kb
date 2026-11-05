# Designing a NeXus-style tool icon in Affinity Designer (64 px grid, booleans)

- Source: Bite-Sized — Icon Design — https://www.youtube.com/watch?v=iq9bdSxOdGE (2025-05-15)
- Host / generation: Affinity Designer (INSYDIUM's own icon workflow; sheets go on to Photoshop for alpha); not an X-Particles technique
- Goal: build a new spin-modifier icon matching the NeXus icon sheet.

## Base
File ▸ New in **pixels**, 500 × 500 (save as your own template). **Insert Artboard** at document size with a **dark background** (helps when alphas come back from Photoshop). Preferences ▸ User Interface ▸ artboard background grey level to darken the surround.

## Steps
1. View ▸ **Show Grid**; View ▸ **Grid and Axis** ▸ Advanced: spacing **64 × 64**, uniform, no second axis, **Divisions 2** → a center mark in each 64 px icon cell. [▶ 2:09](https://youtu.be/iq9bdSxOdGE?t=129)
2. Rectangle from the cell center with Ctrl+Shift+Alt to fill the cell; orange fill (match the icon palette). [▶ 3:16](https://youtu.be/iq9bdSxOdGE?t=196)
3. **Rounded corner** via the red node handle (or slider). [▶ 3:46](https://youtu.be/iq9bdSxOdGE?t=226)
4. **Stroke** width **7**, order set to **behind** the fill so scaling doesn't eat into the shape. [▶ 4:13](https://youtu.be/iq9bdSxOdGE?t=253)
5. White circle from the center (snapping shows the center); color picker needs the extra click to apply the sampled color. [▶ 4:57](https://youtu.be/iq9bdSxOdGE?t=297)
6. Ring: duplicate the circle, scale it down from center, select both (V) ▸ **Subtract**. [▶ 7:02](https://youtu.be/iq9bdSxOdGE?t=422)
7. Cut a gap: Pen tool, Shift-constrained shape over the segment ▸ Subtract. [▶ 6:11](https://youtu.be/iq9bdSxOdGE?t=371)
8. Arrowhead: **Triangle** shape (Shift), rotate into place on the ring; select both ▸ **Add/Combine** into one element; scale down. [▶ 6:58](https://youtu.be/iq9bdSxOdGE?t=418)
9. Small white circle in the middle = the particle; keep separate or combine. Check the green/red snapping guides confirm it is centered. [▶ 7:14](https://youtu.be/iq9bdSxOdGE?t=434)
