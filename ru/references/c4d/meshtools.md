# MeshTools (C4D, часть INSYDIUM Fused)

Источник: docs.insydium.ltd/meshtools/* (Fused 2025, проверено 2026-11-03). Пересказ.

**Концепция:** недеструктивные процедурные генераторы. Объект `mt*` ставится **родителем** исходной геометрии; можно вкладывать несколько друг в друга (порядок в иерархии = порядок операций). Почти все инструменты управляются через **Selection Map** (selection tag / vertex map), **Texture Source** (шейдер / texture tag / видео — в режиме Texture Tag нужен материал C4D) с **Tolerance** (порог яркости: меньше = больше площадь) или **C4D Fields**. Всё анимируется ключами → рост анимируется через field/шейдер/vertex map (например, из xpVertexMap). **Optimize** удаляет дублирующиеся точки.

| Инструмент | Что делает | Примечания |
|---|---|---|
| **mtInset** | процедурные внутренние выдавливания по полигонам | Inset Mode в % от полигона или фиксированной длиной, Variation, Offset, Twist, Shape; анимируйте offset/variation или шейдер → растущие tech-панели (Top Tip "inset growth") |
| **mtPolyScale** | уменьшает отдельные полигоны | Amount, Variation, Seed → эффекты растворения/появления |
| **mtPolyFold** | оригами-развёртка полигонов по пути | Unfold 100% плоско/0% сложено; Distribution Random/Selection/Texture; Remove Offset заставляет полигоны "исчезать" |
| **mtShellGen** | выдавливает полигоны в оболочки с корпусом/крышками | Thickness, Steps, Max Angle, Bevel |
| **mtSubDivider** | подразбивает там, где указывает карта/текстура | уровни, режим Bilinear Offset (смещение по оси, вероятность) |
| **mtSelect** | создаёт выделения точек/рёбер/полигонов по картам/текстурам | Hide Faces (сгенерированные или нет) → показ/скрытие анимированным шейдером |
| **mtDualGraph** | топология dual graph (ячейки в духе hex/voronoi) | Quads / Quads-Tris |
| **mtRemesh** | равномерный или адаптивный ремеш в треугольники | Features Angle (0° = ничего), Edge Length / Min-Max + Gradation; полезно перед cloth/симуляцией |
| **mtPointProject** | проецирует точки на коллайдеры лучами | Offset, Blend, Distance Falloff (shrink-wrap) |
| **mtEdgeSpline** | сплайны из меша: Standard / Curvature / **Contour** / **Outline** (toon-линии, зависящие от камеры) / Intersection | Join Segments |
| **mtShortestPath** | сплайны по рёбрам между начальными и конечными вершинами | от каждого старта → к каждому концу; Avoid; **Spline Growth** — скорость в % за кадр (рост схем/вен) |
| **mtSplineFX** | сплайн-связи между начальными и конечными объектами/частицами | Connection Origin/Points/Surface; Motion через noise; **Growth Start/End**; Gravity/Tension; **Forks** (количество/длина/угол) → процедурный **риг молний**; обход объектов |
| **mtSplineSample** | равномерно пересэмплирует сплайны | Uniform / Natural / Distance; Growth Start/End |
| **mtRayline** | сплайны-лучи (raycast), отражающиеся от коллайдеров | Shape Center/Circle/Line/Custom Object/**X-Particles** (лучи из частиц); Single Shot или отражения; Ray Count/Length; ключи на Start/End → **лазеры / световые лучи** (Top Tip "mtRayline Lasers", "Rayline Particles"); выключите Display Gradient |
| **mtFractal** | раскладывает дочерние клоны по фрактальным узорам: Tree (по умолчанию), Dragon, Fern, Fibonacci, Koch, Sphere | Clone Type Render Instance; Mesh center = один фрактал на полигон; Fern взрывается при росте итераций |

Сплайны из mtEdgeSpline/mtSplineFX/mtRayline рендерятся через Sweep, xpSplineMesher или hair/spline-объекты рендера. Сочетается с X-Particles: эмиссия с результата MeshTools или xpDynamics/cloth на мешах, созданных mt (Top Tip "dynamic MeshTools").
