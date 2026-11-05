# Жидкая сфера: оседает → кипит → взрывается → плещется (initial state + nxVorticity / nxWind с маппингом по возрасту)

- Источник: Top Tip Tuesday — MoGraph Fluid Particles — https://www.youtube.com/watch?v=u2MiqeckNaQ (2025-06-10)
- Хост / поколение: NeXus (nxFluids SPH, nxVorticity, nxExplode, nxWind von Kármán) + тег C4D Vibrate
- Задача: появление логотипа/объекта с жидкостью, запертой в сфере вокруг коллайдера "X", вырезанного булевой операцией.

## Шаги
1. Hex-эмиттер 30 F, radius 2; **nxFluids SPH** substeps 4, Check Density; **nxGravity 700**; сферический коллайдер Normals Inside.
2. Дайте жидкости осесть → Emitter ▸ **Initial State ▸ Use State + Set State**; Emission ▸ **Controlled only** (новых частиц нет).
3. **nxVorticity**: radius 150, strength 2000, **limit 100** (vorticity накапливается); Mapping ▸ **Age 0 → 150** → сила нарастает = кипение.
4. **nxExplode** от позиции модификатора (не от центра масс), speed 1000 ± 800, ниже жидкости, **Scene time кадр 150**.
5. **nxWind** в режиме von Kármán, strength 800–1200, turbulence выключена; **тег Vibrate** rotation 360° по всем осям, frequency 5; Mapping ▸ Age ступенька 150 → 151 (выключено, затем включено).
6. Геометрия X: xpCollider Outside, bounce 0.

## Примечание
Age = кадры с момента загрузки state, поэтому маппинг по возрасту здесь заодно работает как таймер сцены.
