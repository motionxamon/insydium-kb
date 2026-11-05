# Частицы, распускающиеся в щелях геометрии (соседи в nxQuestion + поле)

- Источник: Top Tip Tuesday — Neighbor Cracks — https://www.youtube.com/watch?v=Xe1seJC3g0k (2025-11-04)
- Хост / поколение: NeXus (nxQuestion Neighbors + Field, nxPush, слои nxColor) + Redshift
- Задача: пока поле проходит по скоплению сфер, частицы растут только в швах, где сферы соприкасаются.

## Шаги
1. Параметрические сферы внутри **xpJoin**; эмиттер Object = join, **Offset Origin 3 cm**, Polygon Area, **Shot 60 000**, скорость 0, **radius 0** (отображение Squares игнорирует радиус). [▶ 0:39](https://youtu.be/Xe1seJC3g0k?t=39)
2. nxQuestion: `Particle ▸ Neighbors (40 cm) > 420` → только частицы в швах (они видят точки двух поверхностей). Число подбирайте опытным путём (300 = почти все, 400–420 = только швы). [▶ 2:30](https://youtu.be/Xe1seJC3g0k?t=150)
3. Ограничение полем: добавьте Sphere field на **вкладку Fields в nxQuestion** (оно обязательно должно быть в списке!), затем `If Field > 0.5` (внутренний falloff) **AND** дочернее условие `Neighbors > 420` → actions. [▶ 3:04](https://youtu.be/Xe1seJC3g0k?t=184)
4. Actions: **Set Radius 3** с **Delay** (пружинистый рост). Display Circles/Spheres, чтобы видеть радиус. [▶ 4:30](https://youtu.be/Xe1seJC3g0k?t=270)
5. **nxPush** в режиме Particle Radius, сильный → выросшие частицы расталкивают друг друга. [▶ 5:28](https://youtu.be/Xe1seJC3g0k?t=328)
6. **nxColor** Gradient по **Radius** 2–6 (пресет turquoise→orange); процедурно приглушите насыщенность верхним слоем **Set Color gray** в режиме **Screen** (уменьшите его strength, чтобы вернуть насыщенность). [▶ 7:15](https://youtu.be/Xe1seJC3g0k?t=435)
7. Redshift Object tag → Sphere Instances. [▶ 6:46](https://youtu.be/Xe1seJC3g0k?t=406)
