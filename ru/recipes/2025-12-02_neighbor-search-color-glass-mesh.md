# Абстрактная жидкость с цветными полосами по числу соседей (поиск соседей в nxColor → mesh → стеклянная рампа)

- Источник: Top Tip Tuesday — Neighbor Search Color — https://www.youtube.com/watch?v=-GELMnDapCc (2025-12-02)
- Хост / поколение: C4D, Fused 2025.4 (тогда beta: режим nxColor Neighbor, nxMesher) + Redshift
- Задача: цветные полосы, текущие сквозь жидкость, в зависимости от того, насколько плотно окружена каждая частица.

## Шаги
1. Базовый сим жидкости (nxTurbulence + nxFluids + nxGravity), камера сверху. [▶ 0:34](https://youtu.be/-GELMnDapCc?t=34)
2. **nxColor** Gradient (Parameter) → **Neighbor**: radius 40 cm, диапазон 0–8000 соседей; пресет чёрный→белый (цвет — позже в рендере). [▶ 2:45](https://youtu.be/-GELMnDapCc?t=165)
3. Дублируем слой (сверху): интерполяция узлов рампы **Step**, radius **10**, диапазон 0–200, сдвигаем белый узел → чёрными остаются только частицы по **краю/периметру**. Ставим этому слою blend **Multiply** → чёрные контуры поверх мягкого градиента снизу. [▶ 2:45](https://youtu.be/-GELMnDapCc?t=165)
4. Кешируем (~80 s на 270 кадров). [▶ 4:35](https://youtu.be/-GELMnDapCc?t=275)
5. **nxMesher**: Polygon Size 1.5, radius 2.5, Smoothing **Mean Curvature** на максимум, 5 итераций; **Transfer Color** + color smoothing 5 (мягкие цветовые переходы). [▶ 5:22](https://youtu.be/-GELMnDapCc?t=322)
6. Стекло Redshift (Transmission 1): **Vertex Attribute** (color map) → **Ramp** со своими цветами → transmission color → анимированные полосы. [▶ 7:17](https://youtu.be/-GELMnDapCc?t=437)
