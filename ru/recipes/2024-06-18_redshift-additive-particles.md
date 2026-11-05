# Аддитивный вид частиц в Redshift (Point Instances + материал только с эмиссией + Color User Data → Opacity)

- Источник: Top Tip Tuesday — Additive Particles — https://www.youtube.com/watch?v=KkTBqbnPwg8 (2024-06-18)
- Хост / поколение: C4D; xpEmitter + nxTurbulence (GPU); Redshift
- Задача: миллионы крошечных цветных частиц, которые складываются в молочный светящийся рендер.

## Симуляция
1. xpEmitter **Circle**, радиус диска 15, **cone angle 90**, **Ring Only** → плоская эмиссия кольцом.
2. **nxTurbulence** Voronoi, strength 50, scale 80%, **Octaves на максимум** для мелкой детализации, затем **Persistence 45%**, чтобы сохранить крупные завихрения.

## Рендер
3. Эмиттер ▸ **Redshift Object tag ▸ Particles: Point Instances** (самый эффективный вариант).
4. Redshift Standard Material: base color, reflection и все остальные каналы — weight **0**; **Emission weight 2**.
5. Одноцветный вариант: задайте цвет в **Geometry ▸ Opacity** → наложения складываются до белого.
6. Цвет частиц: нода **Color User Data**, preset **Particles ▸ Color** → в **Geometry Opacity**.
7. Уменьшаем: **Scale Multiplier** в Redshift Object сильно вниз (~0.05), затем увеличиваем количество частиц.
8. Закешированная версия на **100,000/кадр** (~4 миллиона живых частиц) → scale multiplier **0.015**.

## Подводные камни
- Инстансы пересобираются при каждом изменении масштаба — на миллионах точек это медленно.
- Аддитиву нужна плотность + крошечный масштаб; слишком крупные частицы просто выбивают всё в белое.
