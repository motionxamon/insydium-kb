# Трейлы с цветом по вершинам, аддитивный рендер в Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)

- Источник: Top Tip Tuesday — Particle Color Trails — https://www.youtube.com/watch?v=gXGQ4H_MS5k (2024-06-04)
- Хост / поколение: C4D; xpEmitter + xpStrangeAttractors + xpTrail (CPU) + nxTurbulence, nxColor (GPU); Redshift
- Задача: трейлы аттрактора Лоренца, цвет которых прорисовывается со временем, в рендере — светящиеся аддитивные кривые.

## Симуляция
1. xpEmitter **Rectangle** шириной 0 (тонкий и высокий), Rate на 120 F, 300/s. xpTrail по умолчанию.
2. **xpStrangeAttractors** (по умолчанию Lorenz): ограничьте **max speed ~105**, strength **28%**, чтобы могли действовать другие силы.
3. **nxTurbulence** Voronoi, strength 28, **scale 450**.

## Цвет
4. Слой **nxColor ▸ Time Dependent**: на **75 F**, потом reverse; загрузите пресет black-violet, удалите чёрный ключ градиента, перераспределите остальные.
5. Поставьте всем ключам value (яркость) **50%** — во вьюпорте выглядит тускло, зато аддитивная яркость остаётся ровной.

## Рендер
6. **Redshift Object tag на xpTrail ▸ Curves: Boxes**, толщину поменьше.
7. Redshift Standard Material: base/reflection/transmission/coat 0, **Emission 2**.
8. Нода **Vertex Attribute**, пресет **Curves ▸ Curve Color** → **Geometry Opacity**.
9. xpTrail ▸ Thickness & Color ▸ **Trail Color Mode: Per Vertex** (Particle Color красит весь трейл текущим цветом).
10. Redshift Camera ▸ Lens Effects ▸ переопределение **Bloom**: threshold 1, intensity 400.

## Подводные камни
- Цвет трейлов не виден во вьюпорте; проверяйте в окне рендера.

## Как сейчас (новые инструменты)
В NeXus 2026 для трейлов — **nxTrail** на nxEmitter; аналога xpStrangeAttractors в nx не указано.
