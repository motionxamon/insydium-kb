# nxExplode — карточка инструмента

Встречается в **4** рецептах · 2024-12-17 → 2025-06-10 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxExplode** от позиции модификатора (не от центра масс), speed 1000 ± 800, ниже жидкости, **Scene time кадр 150**. [▶ 4:37](https://youtu.be/u2MiqeckNaQ?t=277) — *[2025-06-10](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)*
- Градиент **nxColor** по Speed. Двигайте/анимируйте центр nxExplode вживую, чтобы перенаправить взрыв. [▶ 5:49](https://youtu.be/rMKmeJ68yiE?t=349) — *[2025-05-27](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)*
- **nxExplode**: центр = **This Modifier** (а не центр масс частиц), Timing **Scene Time = F5**. Fields ▸ **Spherical field**, Inner Offset 100%, радиус ~15, внутри бюста; вынести field из модификатора (в папку Utilities), чтобы двигать/нацеливать модификатор (назад и вбок) отдельно. На черновом количестве частиц нужна гораздо большая скорость (+300 variation). [▶ 11:23](https://youtu.be/fxJI8py9BzU?t=683) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- Friction коллайдера **20%** (зёрна скользят), nxExplode Speed **500**. [▶ 30:32](https://youtu.be/fxJI8py9BzU?t=1832) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- **nxExplode** от **позиции модификатора** (не от центра масс), скорость 150 ± 100, **Speed at Start Only выкл.** (продолжает толкать). [▶ 1:10](https://youtu.be/bnaV15UoBRI?t=70) — *[2024-12-17](../../recipes/2024-12-17_particle-reveal-field-group-switch.md)*

## Все рецепты (4)
- 2025-06-10 · [Жидкая сфера: оседает → кипит → взрывается → плещется (initial state + nxVorticity / nxWind с маппингом по возрасту)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2025-05-27 · [Детализированный взрыв по полю через upres (nxUpres position + velocity, nxExplode, переключение групп через nxQuestion)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2024-12-17 · [Распад / проявление текста (nxQuestion field → смена группы → сброс возраста → задать lifespan)](../../recipes/2024-12-17_particle-reveal-field-group-switch.md)
