# Water lily / lotus flower (Taiao Flower: petal layers, Fold, Furling, stamen rings)

- Source: Bite-Sized — Taiao Water Lily — https://www.youtube.com/watch?v=E1P088VK0lk (2025-10-23)
- Host / generation: C4D; **Taiao Flower** object (INSYDIUM ▸ Taiao ▸ Flower); no particles
- Goal: model a layered, slightly irregular water-lily bloom that can also be animated opening.

## Steps
1. Add **Taiao Flower**. Delete the **Sepal** layer, keep the **Pistil**, hide the **Stamen** for now. [▶ 0:28](https://youtu.be/E1P088VK0lk?t=28)
2. Petal ▸ Geometry: **Length segments ~25**, **Width segments 6**. Pull the tip down to a point, widen the base. [▶ 0:48](https://youtu.be/E1P088VK0lk?t=48)
3. Petal ▸ Modifiers: raise **Fold** a lot; on its **Bias spline** drop the end so the base stays flat and the fold grows towards the tip (add a knot for an organic curve). [▶ 1:44](https://youtu.be/E1P088VK0lk?t=104)
4. **Furling**: angle up for a boat-shaped petal; adjust its bias to flatten a little. [▶ 2:10](https://youtu.be/E1P088VK0lk?t=130)
5. Add a **Turbulence** modifier: **Vary Seed** (each petal different), more strength, bias ~1%, larger scale (lower scale value) — subtle only. [▶ 2:40](https://youtu.be/E1P088VK0lk?t=160)
6. Geometry ▸ **Edge Noise**: small amount, lower scale, to break the outline. [▶ 3:13](https://youtu.be/E1P088VK0lk?t=193)
7. Main ▸ **Layer count 5**, raise **Layer step** (vertical offset), **Layer rotation ~20–25°** so each row sits between the petals below; lower the top value of **Layer scale** so inner petals are smaller. [▶ 4:40](https://youtu.be/E1P088VK0lk?t=280)
8. Orientation: tilt inner petals up; **Angle twirl/bias** pulls the lower rows down — keyframe this to animate the bloom opening. Re-tune Layer step, and **Radius** to close the gap at the centre. [▶ 5:15](https://youtu.be/E1P088VK0lk?t=315)
9. Pistil: **Subdivisions 2** for a smooth bulb. [▶ 5:58](https://youtu.be/E1P088VK0lk?t=358)
10. Outer stamens: Distribution **Spiral → World** (ring), larger ring radius, higher count. Geometry: remove the two head points, **Height segments 20**, **Width segments 8**, high size variation. [▶ 7:09](https://youtu.be/E1P088VK0lk?t=429)
11. Stamen modifiers: two **Furling** layers — first curls in (low bias), second curls out → S-bend; plus Turbulence (vary seed, small size). [▶ 8:02](https://youtu.be/E1P088VK0lk?t=482)
12. Add a second Stamen layer for the inner ring: same geometry, World distribution, **Ring count 1**, smaller radius, Furling in with a small gap at the tip, slightly shorter, more variation + turbulence. [▶ 8:54](https://youtu.be/E1P088VK0lk?t=534)
13. Assign materials to each layer.

## Gotchas
- Captions say "failing/filling layer" — the modifier used for the stamen curls is Furling.
