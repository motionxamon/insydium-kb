# Песочный logo reveal, где симулируются только «геройские» гранулы (nxFluids SPH Granular + статичный разброс по vertex map)

- Источник: INSYDIUM LIVE! — March 2023 - NeXus, TerraformFX & Taiao — https://www.youtube.com/watch?v=OVUcKWkhUFY (2023-03-16)
- Хост / поколение: C4D; G2 NeXus — xpEmitter + **nxGravity** + **nxFluids SPH Granular** на GPU (демо на RTX 3080 Ti; 1080 Ti тоже справится, ограничение только по VRAM); теги xpCollider; вторая CPU-система для статичных частиц
- Задача: логотип поднимается из кратера с песком (террейн из part-a); гранулы соскальзывают или откалываются, остальной ландшафт — статичные инстансированные гранулы.

## Шаги
1. Эмиттер в **xpSystem**: форма **Cylinder**, Pitch **90°**, примерно **60 × 7**, speed 0; чуть выше коллайдера кратера.
2. Emission Mode **Simulate** (не «Simulate Legacy») → частицы есть уже на кадре 0. **Shot**, Shot Type **Hexagonal** (пакует плотнее, чем Regular → меньше усадка, масса цельнее), Radius **1.5** (меньше = больше частиц).
3. Низкополигональный кратер: тег **xpCollider**, bounce снизить, **Friction 100%**. У экструда логотипа тоже тег коллайдера — немного friction, чтобы гранулы цеплялись, пока отыгрыш их не стряхнёт.
4. NeXus ▸ **nxGravity** strength **200**. NeXus ▸ **nxFluids**: солвер **SPH** (granular есть только в SPH, в PBD нет), fluid type **Granular**.
5. Display эмиттера: цвет **Gradient Parameter** по значению granular, градиент из пресета, диапазон **Auto**. Отображение Square + поднять **Display Size Factor**, чтобы квадраты закрывали зазоры как сферы.
6. Гранулам нужен точный расчёт скоростей: **Substeps ~9**.
7. Варианты: Granular **Friction 100** = мокрый песок / плотный снег — масса держится, логотип поднимает целый пласт; **Stability ~5** даёт растрескивание на липкие куски. Для финального сухого песка friction сильно вниз.
8. Статичный слой: новая xpSystem с **Only Modifiers in Same System** (игнорирует модификаторы NeXus), Mode Simulate, speed 0, **Shot**; форма **Object** → high-res террейн, **Polygon Area**, count **100,000**; snow vertex map кладём в поле **Selection** объекта → гранулы только в бороздках.
9. Рендер: на обе системы инстансим одну и ту же геометрию гранулы, чтобы статичный разброс и sim читались как одна поверхность.

## Подводные камни
- Даже на GPU с большим VRAM держите sim минимальным: симулируйте только там, где логотип тревожит песок.

## Как сейчас (новые инструменты)
Бета 2026.1: песок **nxMPM** (nxMaterial *Sand wet* / *Sand Dry*, Auto Sleep для улёгшихся гранул) в nxEmitter; nxScatter (Beta 3) — точки на мешах → nxGenerator. В стабильном Fused 2025.4 — nxFluids SPH Granular, как здесь.
