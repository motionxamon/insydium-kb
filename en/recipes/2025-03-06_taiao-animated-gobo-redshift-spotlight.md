# Looping plant-shadow gobo (Taiao wind loop render ▸ Redshift Spot Light texture)

- Source: Bite-Sized — Animated Gobos — https://www.youtube.com/watch?v=AEsbVRNUK3E (2025-03-06)
- Host / generation: C4D; Taiao plant with Forces; Redshift
- Goal: a seamlessly looping black-on-white plant silhouette used as an animated gobo across a wall.

## Steps
1. **Taiao** ▸ default plant/tree. Plant Layers ▸ Leaves: longer, thinner; Main tab **Count ~15**; Distribution: angle the leaves upward. [▶ 0:34](https://youtu.be/AEsbVRNUK3E?t=34)
2. Pure silhouette: Redshift material with no color and no reflections (black) on the plant; **Redshift Camera ▸ Background ▸ Override**, color **white**. [▶ 1:17](https://youtu.be/AEsbVRNUK3E?t=77)
3. Plant **Forces** tab ▸ enable (wind); lower wind strength, and on the Leaf level lower frequency and strength for slow, smooth sway. [▶ 1:45](https://youtu.be/AEsbVRNUK3E?t=105)
4. **Loop time** = timeline length (demo works in seconds: **3**) → seamless loop. [▶ 2:14](https://youtu.be/AEsbVRNUK3E?t=134)
5. Render cheaply: sampling ~0.5 with denoising, buckets **512 × 512**, output **1280 × 1280**, PNG sequence (~6.5 min). [▶ 2:40](https://youtu.be/AEsbVRNUK3E?t=160)
6. Shot scene: Light menu ▸ **Spot Light**, aim at the surface. Spot ▸ Texture: load the PNG sequence ▸ sequence options ▸ Animation ▸ Mode **Loop**, **Detect Frames**. [▶ 4:51](https://youtu.be/AEsbVRNUK3E?t=291)
7. Tune: exposure for shadow contrast, cone angle, Details ▸ enable **Softness affects Gobo**, softness ~**5** (15 and 8 were too soft); intensity ~3. [▶ 5:24](https://youtu.be/AEsbVRNUK3E?t=324)
8. Window blinds: add a Cloner of bars in front of the light for slat shadows on top of the plant. [▶ 6:13](https://youtu.be/AEsbVRNUK3E?t=373)
