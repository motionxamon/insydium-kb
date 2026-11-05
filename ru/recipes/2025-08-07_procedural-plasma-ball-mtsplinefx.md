# Процедурный плазменный шар (nxFollowGeo + nxTurbulence на частицах, дуги mtSplineFX, ответвления от пересечений mtEdgeSpline)

- Источник: INSYDIUM Official Training — Plasma Ball — https://www.youtube.com/watch?v=UXqS-dqsHiM (2025-08-07)
- Хост / поколение: C4D; xpEmitter + GPU nxFollowGeo/nxTurbulence (G2), CPU xpGenerator, MeshTools mtSplineFX + mtEdgeSpline
- Задача: дуги молний от ядра к точкам, ползающим по стеклянной сфере, с ответвлениями; замените геометрию — и риг подстроится.

## Исходная сцена
Три объекта Instance, ссылающиеся на исходную геометрию: **Core**, сфера **Emission** (скрыта), сфера **Intersection** (крупнее). Смена ссылок в инстансах пересобирает риг. Таймлайн 30 s.

## Шаги
1. **xpEmitter** ▸ Object = инстанс Emission, **Polygon Area**; Emission **Shot**, количество **15**, speed 0, radius **40** (большой — нужен для пересечений); отображение Circle, белый.
2. **nxFollowGeo** с геометрией Emission, **Field of View 360**; **nxTurbulence** с noise **Voronoise** → точки блуждают по поверхности.
3. **mtSplineFX**: Start object = Core, End object = эмиттер; тип Connection **Origin → Points** (у эмиттера нет полезного origin) → по одной дуге на частицу.
4. Форма дуги: мелкий noise **0**, основной noise типа **Noise**, масштаб побольше для плавных дуг, скорость анимации **~20%**.
5. Цели для ответвлений: **xpGenerator** с редактируемой Sphere (**12 segments**), привязанный к эмиттеру → сфера на каждую частицу (скройте их).
6. **mtEdgeSpline** режим **Standard → Intersection**: geometry = инстанс Intersection, пересекающие объекты = генератор → кольца там, где сферы частиц режут внешнюю сферу; одноцветное отображение (ярко-жёлтый).
7. mtSplineFX ▸ Connections ▸ включите **Nearest Distance**, режим **Split** (ответвление из точки на основной дуге), Connect To = **custom object** = edge spline; количество **1**, подстройте distance/variation.
8. Проверка: замените три источника на объекты Platonic (core / emission / intersection, отмасштабированные) — риг обновляется.

## Подводные камни
Точки пересечения меняются каждый кадр, поэтому ответвления мерцают — держите их количество небольшим.

## Как сейчас (новые инструменты)
Тот же риг в Fused 2025.4 (у nxFollowGeo появились режимы Guide/Force). В бете 2026.1 пару xp можно заменить на nxEmitter + nxGenerator; часть MeshTools без изменений.
