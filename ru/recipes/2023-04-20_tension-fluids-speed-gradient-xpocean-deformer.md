# Цвет по скорости и подложка жидкости, деформированная океаном (Gradient Parameter по Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)

- Источник: NAB 2023 - INSYDIUM Training — Tension Fluids- Part 2 — https://www.youtube.com/watch?v=VuevOvpbvJY (2023-04-20)
- Хост / поколение: C4D; SPH-симуляция NeXus из Part 1 + CPU xpOcean, xpOpenVDBMesher, xpJoin, xpCache
- Задача: раскрасить три красочные жидкости по скорости и пустить их по волнующейся поверхности океана, построенной из скрытых base-частиц.

## Шаги
1. Цветные эмиттеры: **Start Emit 100 → 15** (base быстро успокаивается). Display Dots. [▶ 0:44](https://youtu.be/VuevOvpbvJY?t=44)
2. Display ▸ Color Mode **Gradient Parameter**, параметр **Speed**: тёмно-фиолетовый на малой скорости, ещё темнее в среднем узле, белый на большой; поднять порог белого **100 → 150 cm/s**, чтобы белого было меньше. Для разнообразия в каждый эмиттер добавить узел cyan (сжав bias) или светлый приглушённый зелёный; переименовать эмиттеры. [▶ 1:34](https://youtu.be/VuevOvpbvJY?t=94)
3. **xpOcean** (Generators): снизить Wave Height и Time Scale, поднять **Wind Speed** для более длинной зыби, добавлять **Choppiness**, пока гребни не начнут заворачиваться. Материал для вьюпорта: без reflectance, шейдер **Fresnel** в Color, от глубокого синего к сероватому белому. [▶ 9:11](https://youtu.be/VuevOvpbvJY?t=551)
4. Переключить xpOcean **Type: Primitive → Deformer** (работает как любой деформер C4D — дочерним объектом или соседом). [▶ 10:28](https://youtu.be/VuevOvpbvJY?t=628)
5. Исключить **nxTurbulence** из base-эмиттера, чтобы подложка просто успокаивалась.
6. **xpOpenVDBMesher**, source = base-эмиттер, **Point Radius 5**. Поставить xpOcean соседом мешера в папке Generators → живой меш деформируется. Перенести материал на мешер. [▶ 12:11](https://youtu.be/VuevOvpbvJY?t=731)
7. Частицы тоже катятся по волнам: добавить деформер xpOcean в список **Modifiers** каждого цветного эмиттера (галочка = включён). [▶ 11:28](https://youtu.be/VuevOvpbvJY?t=688)
8. **xpCache** (overwrite): ~5 мин с плотным мешем. [▶ 15:22](https://youtu.be/VuevOvpbvJY?t=922)
9. После кэширования: **снять галочку xpOcean в Modifiers эмиттеров** (иначе кэшированные частицы деформируются дважды). [▶ 16:33](https://youtu.be/VuevOvpbvJY?t=993)
10. VDB-меш исчезает при скрабе: положить мешер внутрь **xpJoin** (Utilities), xpOcean — его сосед. Опустить Join на **Y −7 cm**, чтобы частицы лежали на поверхности. [▶ 17:37](https://youtu.be/VuevOvpbvJY?t=1057)
11. Display Squares + **Force Display**, **Display Size Factor 50%**. На рендере — эмиссионный шейдинг. [▶ 19:04](https://youtu.be/VuevOvpbvJY?t=1144)

## Как сейчас (новые инструменты)
**nxOcean** (бета 2026.1) со связкой с FLIP, foam/spray и плавающими объектами; **nxMesher** с **Blend into Ocean**; цвет по скорости — **nxColor** с Mapping. Стабильный Fused 2025.4: nxWave внутри FLIP-симуляции.
