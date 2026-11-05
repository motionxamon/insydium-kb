# Динамическая ч/б маска на симуляции песка → смешивание материалов в Redshift (nxQuestion: Field AND Neighbors, Else)

- Источник: Top Tip Tuesday — Advanced Color Animation — https://www.youtube.com/watch?v=1ISE9D2bmeQ (2025-08-19)
- Хост / поколение: NeXus (granular, flow field, nxQuestion) + Redshift
- Задача: песок чернеет там, где собирается вдоль сплайна в плотные гребни; ч/б значение используем для смешивания двух материалов.

## Шаги
1. Display эмиттера во вьюпорте можно оставить Gradient-by-Parameter (данные granular); для рендера поставьте **Color Mode: Single Color белый**.
2. **nxQuestion** → действие **Set Color чёрный** с **Weight ~7%** → плавное затухание вместо мгновенного переключения.
3. Вкладка Fields: перетащите сплайн как слой, **Distance mode ▸ Radius** (трубка вокруг сплайна; увеличьте радиус для более широкого охвата).
4. Вопрос: `Field > 0` → Set Color (действие дочерним элементом).
5. Подвопрос (дочерний, Operator **AND**): `Particle Neighbors within 10 cm > 400–500` → темнеют только плотные гребни.
6. Соседний вопрос, Operator **Not / Else** → Set Color белый, weight ~40% (частицы восстанавливаются).
7. Redshift: **Color User Data** ▸ Particle Data ▸ Particle Color → Blend Color в **Material Blender**; base = материал A, Layer 1 = материал B.

## Подводные камни
- Пороги соседей зависят от количества частиц: при переходе от теста 2k/кадр к продакшену 50k/кадр число нужно сильно увеличить.

## Связанное
Рецепты «nxQuestion Fields», «Neighbor Search Color»; falloff-ы в 2026.1 beta (16 режимов) дают больше форм поля.
