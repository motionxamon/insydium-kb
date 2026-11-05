# Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)

- Источник: Top Tip Tuesday — NeXus Gloopy Liquid — https://www.youtube.com/watch?v=mWdb1K0R0FU (2023-05-30)
- Хост / поколение: C4D; G2 NeXus (nxConstraints, nxGravity на оранжевом xpEmitter) + CPU xpTrail, xpOpenVDBMesher, xpJoin + xpCollider
- Задача: тянущаяся, нитевидная жидкость, льющаяся на вибрирующие сферы, собранная из частиц, связанных пружинами.

## Исходная сцена
Сферы с тегами Vibrate внутри **xpJoin** с одним тегом **xpCollider**. xpEmitter **Circle**, плоскость **−Y**, **Ring Only**, **Cone Angle 90** (сначала разлёт наружу). **nxGravity 200 cm**.

## Шаги
1. **nxConstraints**, Iterations **3**. Добавьте констрейнт **Connection**, нажмите **B** = связи **Birth** (вместо distance/custom).
2. По умолчанию до 8 связей в пределах 40 cm → поставьте **3** связи, Radius **30** → частицы слипаются.
3. Emitter Display ▸ **Display Constraints**, чтобы видеть жёлтые пружины.
4. Пружины рвутся при Break **50% relative**: поднимите до **200**. Stiffness **80% → 23%** → длинные тянущиеся нити.
5. Generators ▸ **xpTrail**, привяжите эмиттер, **Algorithm: Constraints**, тип **Birth** → зелёные трейлы вдоль пружин; скройте эмиттер.
6. Generators ▸ **xpOpenVDBMesher**, мешит **трейл** (трейл скройте). Слишком комковато → xpTrail ▸ Spline options ▸ **Intermediate Points Uniform 10** → гладкие нити.
7. Материал на мешере. Фильтры: уберите Median, добавьте **Gaussian** (width 1; 2 было слишком мягко), затем фильтр **Offset**, чтобы слегка утончить.

## Как сейчас (новые инструменты)
Вязкую жидкость сейчас делают через **nxFluids FLIP/APIC** с переменной вязкостью или неньютоновскую жидкость в 2026.1 (Flow Index, Yield Stress) + GPU **nxMesher**; либо SPH + nxConstraints Viscosity (см. "Three gloops with three viscosities", 2025-08-05). Для нитевидных тяжей по-прежнему подходят nxConstraints + **nxTrail**; коллизии — через **nxCollider** в NeXus 2026.
