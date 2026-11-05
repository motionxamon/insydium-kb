# Шлейфы «взрыв-цветок» с толщиной от скорости и цветом по вершинам (nxTrail, nxScale + маппинг скорости в nxTurbulence)

- Источник: Top Tip Tuesday — Particle Trails — https://www.youtube.com/watch?v=I2ERiN8Vk2Q (2026-08-25)
- Хост / поколение: Blender (NeXus for Blender 2026.0) — nxSpeed, nxTurbulence, nxColor, nxScale, nxTrail; Eevee
- Задача: частицы разлетаются, закручиваются и замедляются до остановки, оставляя шлейфы, которые сужаются и меняют цвет по длине.

## Шаги
1. **nxEmitter**: **Disc**, только Edges, Angle **90°**, **Shot** из 200 (2,000 для финала), Speed **2.5**, вариация **1** (диапазон 1.5–3.5 m/s). [▶ 0:34](https://youtu.be/I2ERiN8Vk2Q?t=34)
2. **nxSpeed** ▸ дефолтный слой Incremental с **отрицательным** значением (**−0.04**) + вариация → мягкое торможение. [▶ 1:09](https://youtu.be/I2ERiN8Vk2Q?t=69)
3. **nxTurbulence** ▸ слой Voronoi, режим **Direction** (рулит, не добавляя скорости); подними strength (~49) и scale. [▶ 1:54](https://youtu.be/I2ERiN8Vk2Q?t=114)
4. Turbulence ▸ **Mapping ▸ карта Speed** → слой Voronoi Noise, параметр strength, диапазон **0–3.5** → быстрые частицы сильно закручиваются, медленные успокаиваются. [▶ 2:55](https://youtu.be/I2ERiN8Vk2Q?t=175)
5. Отображение **Circles Filled**; radius 0.05. [▶ 4:39](https://youtu.be/I2ERiN8Vk2Q?t=279)
6. **nxColor**: градиент Magma, параметр **Distance** (пройденное расстояние), max ~**5 m** (Speed 0–3.5 тоже работает; разверни градиент для перехода тёмный→светлый). [▶ 6:05](https://youtu.be/I2ERiN8Vk2Q?t=365)
7. **nxTrail** ▸ emitter. Вкладка Thickness ▸ Trail Color Mode **Per Vertex Color** (дефолтный Particle Color перекрашивает весь шлейф целиком) → цвет прорисовывается вдоль шлейфа. [▶ 13:33](https://youtu.be/I2ERiN8Vk2Q?t=813)
8. Режим Thickness **Use Radius Variable** → ширина шлейфа от радиуса частицы. [▶ 9:06](https://youtu.be/I2ERiN8Vk2Q?t=546)
9. Анимация радиуса: radius эмиттера 0; слой **nxScale** **Set Value** 0.05, вариация 60%, **Clamp to Radius Limit off**; Mapping ▸ карта Speed → **Radius Value**, диапазон 0–3.5; приподними нижний край кривой, чтобы медленные частицы сохраняли немного ширины → шлейфы сужаются, но не исчезают. [▶ 10:34](https://youtu.be/I2ERiN8Vk2Q?t=634)
10. Рендер: nxTrail Display **Lines → Splines** → автоматически создаются Geometry Nodes (Curve to Mesh) + материал с **атрибутом цвета шлейфа NeXus**; например, подай его в Emission color у Principled. [▶ 13:31](https://youtu.be/I2ERiN8Vk2Q?t=811)

## Подводные камни
- Режим Lines работает только во viewport на GPU; рендерится только Splines (и он медленнее — GN на CPU).
