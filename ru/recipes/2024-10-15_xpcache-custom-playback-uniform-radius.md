# Одинаковый размер на рендере при симуляции, завязанной на радиус (каналы xpCache Custom Playback, сферы частиц в Redshift)

- Источник: Top Tip Tuesday — xpCache Custom Playback — https://www.youtube.com/watch?v=c-JysAVC__w (2024-10-15)
- Хост / поколение: C4D; xpEmitter + NeXus G2 **nxPush** (режим Particle Radius); **xpCache**; **Redshift**
- Задача: сохранить узор, которому нужны разные радиусы, но отрендерить все частицы одного размера.

## Исходная сцена
Частицы рождаются друг на друге с разными радиусами; цвет эмиттера = Gradient by Parameter **Radius** (2 → 6 cm). **nxPush** в режиме Particle Radius расталкивает их в похожие на жидкость кластеры. Отображение **Squares** (+ **Force Display**) показывает узор; Circles — реальные радиусы.

## Шаги
1. Эмиттер ▸ **Redshift Object tag ▸ Particles ▸ optimized Spheres**; Scale Multiplier ~0.1 — но светлые/крупные частицы всё равно рендерятся больше. [▶ 2:48](https://youtu.be/c-JysAVC__w?t=168)
2. **xpCache ▸ Build Cache** (по умолчанию, 200 F). [▶ 3:49](https://youtu.be/c-JysAVC__w?t=229)
3. xpCache ▸ Playback ▸ **Custom**: отметьте только **Velocity** и **Color** — **Radius** оставьте выключенным. [▶ 4:22](https://youtu.be/c-JysAVC__w?t=262)
4. Теперь радиус берётся с эмиттера: Emission ▸ Radius **1**, вариация **0**. [▶ 4:48](https://youtu.be/c-JysAVC__w?t=288)
5. Верните RS Scale Multiplier (например, 1 → **0.5**): все сферы одинаковые, узор сохранён. [▶ 5:15](https://youtu.be/c-JysAVC__w?t=315)

## Подводные камни
- Сферы могут перекрываться там, где расстояние при push задавали более крупные закэшированные радиусы; подстройте масштаб на рендере.
