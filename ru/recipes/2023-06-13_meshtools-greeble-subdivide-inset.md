# Процедурные гриблы-панели (mtSubdivider на noise + mtInset с вариацией, скручиванием и сферическим полем)

- Источник: Top Tip Tuesday — MeshTools Greeble — https://www.youtube.com/watch?v=V2U7P7K1pws (2023-06-13)
- Хост / поколение: C4D; MeshTools (mtSubdivider, mtInset)
- Задача: превратить стандартную плоскость в плотную, неравномерную sci-fi детализацию из панелей — полностью процедурно и с возможностью анимации.

## Шаги
1. INSYDIUM ▸ MeshTools ▸ **mtSubdivider**; плоскость — дочерним объектом (объекты MeshTools работают со своими потомками). Subdivisions **5**.
2. Ограничьте, где идёт подразбиение: драйвером может быть материал, selection tag, vertex map, поле или **Shader** → выберите **Noise**, тип **Luka**, понизьте **High Clip**, Global Scale **300%** → подразбиение пятнами. [▶ 1:27](https://youtu.be/V2U7P7K1pws?t=87)
3. Протестируйте **mtInset** отдельно на простой плоскости: **Amount** = инсет в стиле inner extrude; добавьте **Variation**, **Offset** (выдавливает внутреннюю грань вверх) с вариацией. [▶ 2:02](https://youtu.be/V2U7P7K1pws?t=122)
4. **Divisions 6** на новых боковых гранях, затем **Twist** с вариацией — внутренние грани поворачиваются. [▶ 2:56](https://youtu.be/V2U7P7K1pws?t=176)
5. Цепочка: плоскость → внутрь mtSubdivider → внутрь mtInset → инсеты на неравномерно подразбитых полигонах. Меняйте **Seed** noise в сабдивайдере, чтобы перебирать варианты. [▶ 3:36](https://youtu.be/V2U7P7K1pws?t=216)
6. mtInset ▸ Fields: **Spherical field** → инсет получают только полигоны внутри; Remapping поля ▸ режим Contour/control **Curve** для более мягкого перехода. [▶ 4:39](https://youtu.be/V2U7P7K1pws?t=279)
7. mtInset ▸ **Advanced**: выберите, на какие значения влияет поле (по умолчанию Inset, Offset и Twist). Снимите галку Inset → всё остаётся с инсетом, а поле управляет только offset и twist. [▶ 4:46](https://youtu.be/V2U7P7K1pws?t=286)

## Как сейчас (новые инструменты)
В Fused 2025.x те же объекты MeshTools; в Fused 2024.2 добавились **mtPolyFold** и **mtPointProject** для дополнительной процедурной детализации. См. «mtInset layered growth» (2024-11-26).
