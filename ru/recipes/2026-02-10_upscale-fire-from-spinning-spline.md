# Огонь от вращающегося сплайна логотипа + Upscaling для детализации

- Источник: Top Tip Tuesday — Upscale Fire — https://www.youtube.com/watch?v=irQZ4OI7Bhk (2026-02-10)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX) + Redshift
- Задача: настроить симуляцию огня в низком разрешении с быстрым проигрыванием, затем апскейлить для рендера с той же формой.

## Шаги
1. nxExplosiaFX → Sources: перетащите **анимированный сплайн логотипа** (принимаются сплайны, полигоны и частицы). **Voxel Size 2.7**. [▶ 0:33](https://youtu.be/irQZ4OI7Bhk?t=33)
2. Source **Velocity 200%** → жидкость наследует вращение сплайна и разлетается. **Motion Gap Fill 2** (быстрый источник: без ступенек, скорость точнее; симуляция медленнее). [▶ 5:40](https://youtu.be/irQZ4OI7Bhk?t=340)
3. Burning: **Burn Rate** выше (сжигать всё топливо), **Temperature Production** сильно ниже, меньше Fuel у источника, **Smoke Production 0.9**, **Gas Expansion ~7** (спокойнее), **Ignition Temperature 0**. [▶ 1:59](https://youtu.be/irQZ4OI7Bhk?t=119)
4. Dissipation: дым сильно выше, температура немного (пламя короче). [▶ 3:24](https://youtu.be/irQZ4OI7Bhk?t=204)
5. Forces: удалите стандартный **Turbulence** (крупные завихрения должны идти от скорости сплайна); **Vorticity** сильная, **mapped to Position Y** (сильная внизу → затухает с высотой) → чёткое пламя внизу, пышный дым выше. [▶ 4:09](https://youtu.be/irQZ4OI7Bhk?t=249)
6. Upscaling: 0 → **2** (≈2× вокселей, экономно по VRAM) → **4** (например, 136×210×130 → 544×840×520). Форма остаётся практически той же; появляется детализация. Проверяйте Memory Stats. Redshift дольше грузит большие сетки. [▶ 8:30](https://youtu.be/irQZ4OI7Bhk?t=510)

## Подводный камень
Не используйте upscaling, если нужен векторный motion blur при рендере (velocity не апскейлится) — см. «ExplosiaFX MotionBlur».
