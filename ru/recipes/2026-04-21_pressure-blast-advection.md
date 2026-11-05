# Адвекция текста взрывом давления с 10 M частиц (nxExplosiaFX)

- Источник: Top Tip Tuesday — Pressure Blast — https://www.youtube.com/watch?v=N9SMgriCpAI (2026-04-21)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX как поле скоростей) + аддитивные точки Redshift
- Задача: буквы разлетаются наружу тонкими молочными струйками.

## Сетап EFX (только скорость, без горения)
1. Две копии текста: текст для рендера (скрыт) и редактируемый **sim text** (без крышек, внутренние дырки убраны).
2. Sources: sim text, **Emit From Volume**, **Fuel 0**, **Temperature 4800**, **Pressure 1400**.
3. Simulation ▸ Buoyancy: **Gravity off** (без подъёма шлейфа вверх).
4. Одиночный взрыв: **Mapping** источника → Source Mesh Object, Destination **Scene Time** (0–30 F) → Temperature с коротким пиком на кривой; скопируйте Ctrl-перетаскиванием → Pressure.
5. Colliders: тот же sim text → выталкивает жидкость наружу.
6. Солвер для плавной адвекции: Pressure Iterations ×2 (20) + больше точности; Advection **Max Substeps 6**; адвекцию smoke/temperature/velocity в **Fast** (глаже, меньше «огненной детализации»); понизьте dissipation температуры; **Adaptive Bounds off** (или больше дополнительных вокселей), чтобы частицы никогда не упирались в край границ; откройте стенку −Y.

## Частицы
7. xpEmitter от sim text, Polygon Area, **Shot**, lifespan 50 ±20, скорость 0. EFX ▸ Particle Advection: Mode **Position**, адвекция smoke/temperature/fuel выкл.
8. Количество: 10 k → 500 k → **10 M** (Display LOD 0.1). Живая симуляция всё ещё проигрывается вполне сносно.
9. Redshift Object tag ▸ Point instances с аддитивным материалом (emission + opacity); размер точки 1 → 0.1 (500 k) → **0.015** (10 M). Больше частиц, меньше точки = молочные струйки.
