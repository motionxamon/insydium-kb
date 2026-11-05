# Электрические дуги, кабели и искры от лазерного прожига (mtSplineFX + mtRayline + nxQuestion Spawn)

- Источник: INSYDIUM LIVE! — July 2023 – NeXus, Taiao, TerraformFX & MeshTools — https://www.youtube.com/watch?v=6WjDq_87uck (2023-07-05)
- Хост / поколение: C4D; MeshTools **mtSplineFX** и **mtRayline** (новые в Fused 2023.3) + G2 NeXus (nxQuestion, nxGravity) на xpEmitter
- Задача: молнии между мигающими частицами с искрами и заземлёнными ответвлениями; процедурные кабели; лазеры, которые спавнят искры в точке касания модели.

## A — Дуги между частицами (mtSplineFX)
1. Тор с тегом Vibrate; **emitter A** на торе, **emitter B** на плоскости пола (частицы мигают on/off).
2. **mtSplineFX** ▸ Objects: Start = emitter A, End = emitter B. Тип соединения **Points** (дефолтный **Origin** работает только для объектов, не для частиц).
3. Вкладка Spline **Points 100** (детализация). Motion: увеличить scale у **large noise**, затем добавить **small noise** для мелкого дрожания. Настроить отображение; белая центральная дуга.
4. Искры: **nxQuestion** только в списке модификаторов emitter B (emitter A исключён): **Age > 0** → **Spawn**, Inherit Parent off, количество побольше. **nxGravity** ~150 с вариацией 20. Spawn-эмиттер: отображение Lines, градиент Heat, Life **15** F, вариация **10**.
5. Заземлённые ответвления: Sphere, клонированная **xpGenerator** по emitter B (Scale = Source), собранная в один объект (в субтитрах: "XP join"); скрыть его. mtSplineFX ▸ Connections ▸ добавить слой **Fork** (count, length, angle, distribution — как в Taiao), count **2**, Connect To **Custom Object** = эта общая геометрия.
6. Включить вопрос и на emitter A — искры с обоих концов.

## B — Кабели
Цепочка соединений цилиндр → цилиндр (1→2→3), тип соединения **Surface**, количество по вкусу; выключить всю деформацию Motion, включить **Gravity** с небольшой вариацией → живые провисающие кабели.

## C — Искры в точках касания лазера (mtRayline)
1. **mtRayline** ▸ вкладка Object: добавить коллайдеры (волк, пол). Лучи отражаются, пока не кончится Ray Length (по умолчанию **500**). Включить **Single Shot** (одно касание, без отскоков).
2. Ключи на **Angle** 0 → **46** (середина сцены) → обратно, чтобы лучи прошлись по голове и полу. Display: точки выкл., лазерный градиент.
3. Вкладка Points: контактные точки ▸ **add emitter** ("emitter contact"), отображение None.
4. **nxQuestion**: вопрос **Emitter** = emitter contact (изолирует эффект, если эмиттеров несколько) → **Spawn**, Inherit Parent off, Velocity Random, Speed **64** (потом снижена), Radius **1**, count **20**, Distance **1**. nxGravity; отображение spawn — Dots, градиент по Age белый→чёрный. Уменьшить friction у коллайдера волка.
5. Всё процедурно: двигайте/анимируйте mtRayline (например, через родительский анимированный null) — искры следуют.

## Как сейчас (новые инструменты)
mtSplineFX и mtRayline по-прежнему актуальные инструменты MeshTools (см. рецепты "mtSplineFX Lightning", "mtRayline Particle Lasers"). Для спавна искр в 2026.1 beta action Spawn в nxQuestion заменяет **nxSpawn**.
