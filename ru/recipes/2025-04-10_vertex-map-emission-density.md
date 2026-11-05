# Плотность эмиссии по процедурной vertex map (Vertex Map + Linear field ▸ xpJoin ▸ xpEmitter Selection)

- Источник: Bite-Sized — Vertex Map Emission — https://www.youtube.com/watch?v=yAZ7aY8Ed4Y (2025-04-10)
- Хост / поколение: C4D; CPU xpEmitter + утилита xpJoin; нативный тег Vertex Map и поля C4D
- Задача: облако частиц, плотность которого следует (анимируемому) весу вершин и сходит на нет там, где вес низкий.

## Шаги
1. Примитив Plane, **100 × 100** сегментов. Tags ▸ Other Tags ▸ **Vertex Map**; Use Fields включён по умолчанию — добавьте **Linear field** (красный = 0, жёлтый = 1). Анимируйте поле, если карта должна двигаться.
2. Поместите плоскость в **X-Particles ▸ Utilities ▸ xpJoin**; выключите **Hide Source**, чтобы снова видеть веса.
3. **xpEmitter ▸ Object**: Emitter Shape Object = join, Emit From **Polygon Area**; Emission ~**50,000**; Display **Dots**, чтобы читалось облако.
4. Вкладка Object эмиттера ▸ поле **Selection**: перетащите vertex map (принимает и выделения точек/рёбер/полигонов) → плотность следует весу.
5. **Vertex Map Threshold**: 50 → частиц нет там, где вес < 50%; верните 0 для мягкого градиента.
6. Больше контраста: Linear field ▸ Remapping ▸ Contour Mode **Curve**, сделайте сплайн круче → у большей части плоскости вес маленький, плотное облако только у верхнего края.

## Как сейчас (новые инструменты)
В C4D-бете NeXus 2026.1 **nxFalloffMap** запекает nxFalloff (16 режимов) в теги vertex map / vertex color, так что ту же эмиссию по весу можно строить на nxFalloff вместо полей C4D.
