# Рендер связей-пружин + стеклянная оболочка под водой (xpTrail Algorithm Constraints, xpOpenVDBMesher, туман Redshift Environment)

- Источник: Top Tip Tuesday — Rendering nxConstraints in Redshift — https://www.youtube.com/watch?v=jHu6mpJfEUQ (2024-10-01)
- Хост / поколение: C4D; NeXus G2 nxConstraints (риг усиков из рецепта 2024-08-27) + CPU **xpTrail** и **xpOpenVDBMesher**; **Redshift**
- Задача: сделать невидимые пружинные связи рендерящимися, обернуть усики органической стеклянной оболочкой и сымитировать подводную миниатюру.

## Шаги
1. На эмиттере, который создаёт связи: Display ▸ **Display Constraints** включить (нужно и для viewport, и для трейлов).
2. **xpTrail**: этот эмиттер, **Algorithm ▸ Constraints**, отметьте **Birth** (выберите тип связи) → трейлы становятся зелёными. Спрячьте эмиттер/constraints.
3. xpTrail ▸ **Redshift Object tag ▸ Curve ▸ Boxes**, Thickness ~**3**.
4. Spawn-эмиттер ▸ RS Object tag ▸ Particles: **sphere instances**, масштаб уменьшен до доли.
5. **xpOpenVDBMesher** на spawn-эмиттере: Voxel Size **3**, Point Radius **2**, **Filters** включены (по умолчанию).
6. Материал мешера: RS Standard, **Transmission weight 1**; IOR **0.95** (< 1 продаёт «подводность»); цвет Scatter светло-серый с **Depth** ~10 (1 = молочный, 30 = прозрачный); чуть шероховатости.
7. Render Settings ▸ Redshift ▸ Globals: **default light выключить**. Добавьте **Redshift Environment**: scattering выключен, **Attenuation 0.1**, **Fog emission** зелёный (освещает сцену + затухание по глубине). Внизу настроек volume scattering уменьшите его влияние на отражения, чтобы смягчить резкие края.
8. Standard-материалы на трейлы и частицы.
9. **Redshift Camera** ▸ Optical: выберите фокус на усике, низкое значение aperture, **Bokeh** включить → DOF как у миниатюры.

## Как сейчас (новые инструменты)
**nxMesher** (Fused 2025.4) для оболочки; в NeXus 2026 используйте nxTrail и nxSpawn для рига. Redshift в C4D 2024+ запекает ненативные шейдеры в 128×128 — повышайте, если используете шейдеры XP.
