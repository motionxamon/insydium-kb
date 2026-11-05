# Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)

- Источник: Maintenance Training — Dynamics - Constraints - Forces Tutorial — https://www.youtube.com/watch?v=dnyn6Lrj8-A (2023-06-08)
- Хост / поколение: C4D; CPU X-Particles (xpConstraints, xpCover, xpTurbulence, xpScale, xpOpenVDBMesher)
- Задача: частицы вырастают на MoText, собираются в комки за счёт сил притяжения/отталкивания и ползут к подвижной цели; мешируются как слизь/мёд.

## Исходная сцена
MoText «XP» bold, высота **400 cm**, глубина **80 cm**, Fillet Caps спереди и сзади (3 шага). Сдвинуть на **Z −40**, чтобы центр был в начале координат.

## Шаги
1. **xpEmitter ▸ Object**, Polygon Area, **Offset Origin 1 cm**; **Shot 500**, скорость 0; **Radius 6 cm, variation 6** → 0–12 cm. Display Circles Filled. [▶ 2:39](https://youtu.be/dnyn6Lrj8-A?t=159)
2. Включить **xpConstraints ▸ Forces**. Дефолтный радиус притяжения 20 cm слишком мал для логотипа в 400 cm → **Attraction Radius 400**, **Limit** связей **16 → 50**. [▶ 3:42](https://youtu.be/dnyn6Lrj8-A?t=222)
3. **xpCollider tag** на MoText: Bounce 0, Friction 25 (позже уменьшить, чтобы частицы проскальзывали). [▶ 4:47](https://youtu.be/dnyn6Lrj8-A?t=287)
4. Увеличить радиус/силу отталкивания; также включить **Collisions** в объекте Constraints, чтобы частицы не перекрывались. [▶ 5:37](https://youtu.be/dnyn6Lrj8-A?t=337)
5. Замапить **Repulsion** на **Radius** частицы (min 0, max 12 cm), кривая инвертирована: самые мелкие получают полное отталкивание → мелочь роится по краям комков. [▶ 6:20](https://youtu.be/dnyn6Lrj8-A?t=380)
6. **xpCover** (Motion modifiers): Target = Null (отображение star), Modifier Type Target, эффект Attract, **Speed Mode: Gravity**, Gravity Strength **10**. Двигая null, управлять потоком. Меньше **Acuteness of Turn** — пути дугой, с кружением; больше — прямо к цели. [▶ 9:54](https://youtu.be/dnyn6Lrj8-A?t=594)
7. Cover ▸ Mapping: **Gravity Strength по Radius** 0–12, кривая такая, что тянутся только частицы крупнее ~6 cm; мелкие следуют за ними благодаря констрейнтам. Слегка поднять силу. [▶ 13:23](https://youtu.be/dnyn6Lrj8-A?t=803)
8. По желанию **xpTurbulence** (маленький масштаб, большая сила) для дрожания внутри комка.
9. Вырастание: **xpScale** ▸ Set Value, **12 cm**; Mapping **Radius по Age** (0 → 90 кадров, укоротить рампу). [▶ 15:55](https://youtu.be/dnyn6Lrj8-A?t=955)
10. Вернуть случайность: эмиттер ▸ Extended Data ▸ Physical ▸ **Temperature 50, variation 50** (просто контейнер для числа, 0–100) → вторая карта в xpScale: **Radius по Temperature**. [▶ 17:35](https://youtu.be/dnyn6Lrj8-A?t=1055)
11. Меш: **xpOpenVDBMesher**, source = эмиттер; увеличить Voxel Size, уменьшить Point Radius, добавить фильтры сглаживания **Gaussian**. [▶ 20:26](https://youtu.be/dnyn6Lrj8-A?t=1226)

## Как сейчас (новые инструменты)
**nxConstraints** Forces + **nxCover** с NeXus Mapping и **nxScale** (слоёный, Fused 2025.4), меш — **nxMesher**. Для настоящих жидкостей — **nxFluids FLIP/APIC** с переменной вязкостью; для липких/упругих тел — **nxMPM** (бета 2026.1).
