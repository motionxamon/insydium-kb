# Миллионы частиц, адвектируемых дымом, с аддитивным рендером (xpExplosiaFX Advect Particles, X-Particles material Add blend)

- Источник: Top Tip Tuesday — X-Particles Advection — https://www.youtube.com/watch?v=_G2CwPw4OSY (2023-08-15)
- Хост / поколение: C4D; G1 CPU X-Particles (xpExplosiaFX + Source tag, xpEmitter); стандартный рендер C4D с X-Particles material
- Задача: быстрые в симуляции и рендере тонкие завихрения частиц, которые движет поле скоростей огненной симуляции.

## Исходная сцена
Сфера, которую двигает тег Vibrate; xpEmitter со сферы, Speed **0**, Birth Rate **1,000 per frame**, Life **50**, вариация **20**. Пока собираете симуляцию, отключите эмиттер.

## Шаги
1. System Dynamics ▸ **xpExplosiaFX** (розовый домен). Сфера ▸ Tags ▸ INSYDIUM ▸ тег **xpExplosiaFX Source**, по умолчанию → сразу дым/огонь.
2. Display: для быстрого превью во вьюпорте используйте режим **Grid**; если переключить отображение на **Velocity**, видно скорости вокселей, которые будут толкать частицы. Потом выключите отображение → симуляция считается быстрее.
3. Включите эмиттер обратно; xpExplosiaFX ▸ вкладка **Advection** ▸ включите **Advect Particles**.
4. Чтобы частицы не улетали вверх: Simulation ▸ Dissipation ▸ добавьте немного **Heat dissipation**. Вверху вкладки Simulation немного поднимите **Turbulence strength** для большего закручивания.
5. Material Manager ▸ Create ▸ Extensions ▸ **X-Particles material** на эмиттер; скройте сферу.
6. Material Size ▸ Scale **0.5** (крошечные точки). Birth Rate эмиттера → **10,000/frame**.
7. Material Color ▸ Modifiers ▸ **Speed**: медленные = приглушённый синий, быстрые = приглушённый тёмно-оранжевый (тёмные, потому что пересечения будут складываться).
8. Render Settings ▸ **X-Particles options** ▸ Blend Normal → **Add** для светящихся пересечений.
9. Финал: **20,000/frame** — больше 1M частиц на кадр; в демо 155 кадров отрендерились примерно за 2 мин 50 с (максимум ~1 с на кадр).

## Как сейчас (новые инструменты)
**nxExplosiaFX** (GPU, Fused 2025.4) считает дым и может адвектить частицы NeXus; в 2026.1 добавьте **nxWarp** на дым, а в C4D 2025.3+ можно связать с нативным Pyro. Точки рендерьте аддитивно в Redshift (см. «Redshift cached particle velocity glow», 2024-08-13). xpExplosiaFX остаётся запасным CPU-вариантом.
