# Pollen from a Taiao flower's stamen tips (tiPlant custom object, xpJoin, layer selection, nxWind)

- Source: Top Tip Tuesday — Taiao Particles Emission — https://www.youtube.com/watch?v=ZgUIL-udXks (2024-05-28)
- Host / generation: C4D; Taiao (tiPlant, tiFlower) + xpEmitter + NeXus (nxWind, nxTurbulence)
- Goal: tiny pollen particles drift only from the bulbous ends of the stamens.

## Steps
1. **tiPlant** trunk layer = stem; drag a **tiFlower** into the trunk's **Custom Object** slot so it rides the stem (Furling modifier bends it all).
2. **xpJoin** with plant and flower as children; xpEmitter Object = the join, **Polygon Area**.
3. Emission: lifespan 120 (var 70), birth rate 300, speed 0, **radius 0.1**.
4. tiFlower ▸ Flower Layers ▸ **Stamen** layer button creates a **polygon selection** → drop it into the emitter's selection field.
5. Tips only: duplicate the stamen layer (Ctrl-drag). On the **emitting** one, edit the **Profile** curve so only the bulb remains (delete a point, drop one to 0). On the copy, clear the selection and keep it as the visible full stamen.
6. **nxWind** aimed along the flower, fan display off, **strength 2** (tiny particles).
7. Display **Dots**, Gradient by Parameter (Flame preset minus red/black) mapped to **Speed**, **Auto** range.
8. **nxTurbulence** Voronoi, strength **0.1**, scale **4%**.
