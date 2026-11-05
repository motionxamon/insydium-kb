# Уплотняем закэшированную адвекционную симуляцию спавном (xpCache + xpExplosiaFX Advection + xpSpawn)

- Источник: Top Tip Tuesday — xpCache Spawning — https://www.youtube.com/watch?v=XtaaaiKtl_w (2024-02-13)
- Хост / поколение: C4D; CPU X-Particles (xpExplosiaFX, xpCache, xpSpawn)
- Задача: переиспользовать старую закэшированную симуляцию дыма/частиц и закачать почти миллион новых адвектируемых частиц без пересчёта.

## Шаги
1. **xpExplosiaFX** по умолчанию + сфера с **xpExplosiaFX Source tag** (по умолчанию); смотрим канал Temperature.
2. Новый эмиттер на той же сфере (Object, polygon area): Rate, кадры **0–50**, lifespan 50 (вариация 20), **10/кадр**, скорость 0.
3. Вкладка **Advection** в xpExplosiaFX активна → дым двигает частицы.
4. **xpCache** во внешние файлы (кэширует и частицы, и дым).
5. **xpSpawn** (модификаторы Generate) ▸ **Add Emitter** → «emitter spawn»: Draw Emitter выкл., **Dots**, Gradient Parameter (фиолетовый пресет) по **Speed**, min 10 / max 200; скорость 0, lifespan 50 (вариация 25).
6. xpSpawn: спавн из позиций исходных частиц, остальное по умолчанию; количество 300 → **10/кадр**, затем **50** — заспавненные частицы адвектируются тем же закэшированным дымом.
7. Display ▸ **HUD** показывает ~900k частиц; поднимите количество спавна до миллионов и перекэшируйте.

## Как сейчас (новые инструменты)
**nxSpawn** (бета 2026.1) для дочерних частиц и GPU **nxExplosiaFX** (Fused 2025.4) для дыма; в Fused 2025 — действие Spawn в nxQuestion.
