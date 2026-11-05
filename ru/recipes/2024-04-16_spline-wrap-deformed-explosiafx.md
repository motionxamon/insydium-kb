# Изгибаем прямую симуляцию огня по спирали (xpExplosiaFX + C4D Spline Wrap)

- Источник: Top Tip Tuesday — Deforming Smoke and Fire — https://www.youtube.com/watch?v=RkAB9dD0X5k (2024-04-16)
- Хост / поколение: C4D; CPU **xpExplosiaFX** (до nxExplosiaFX); рендер Cycles 4D
- Задача: просимулировать простой прямой столб огня, затем деформировать весь объём деформером C4D в стеклянную трубку-спираль.

## Шаги
1. Размер солвера **xpExplosiaFX** **50 × 1300 × 50** (высокий, узкий). Опции контейнера: **закрыть все стороны, кроме верха**. [▶ 0:45](https://youtu.be/RkAB9dD0X5k?t=45)
2. Источник топлива: сфера r 5 cm внизу + **xpExplosiaFX Source tag**: Solid выкл. (заполняет объём), Heat 200, Fuel 200, добавьте **Pressure**, чтобы газ быстрее шёл вверх. [▶ 1:35](https://youtu.be/RkAB9dD0X5k?t=95)
3. Display: режим **Grid** (отображение вокселей), level of detail 200. [▶ 2:01](https://youtu.be/RkAB9dD0X5k?t=121)
4. Simulation: скорость симуляции поднята (значение в видео неразборчиво), **гравитация сильнее** (умножает плавучесть), плавучесть дыма около −10. [▶ 2:23](https://youtu.be/RkAB9dD0X5k?t=143)
5. Модель горения **Custom**: Burn Rate 20 (пламя живёт выше), **Ignition Heat 0**, Smoke from Heat 1.5. [▶ 3:15](https://youtu.be/RkAB9dD0X5k?t=195)
6. На кадре 0 добавьте деформер **Spline Wrap** дочерним к объекту xpExplosiaFX, spline = Helix, ось **+Y**. Закэшированный/симулированный объём теперь следует спирали; углы Helix можно анимировать keyframe-ами. [▶ 4:22](https://youtu.be/RkAB9dD0X5k?t=262)
7. Скопируйте Spline Wrap под цилиндр (материал стекла), чтобы трубка совпадала. [▶ 5:33](https://youtu.be/RkAB9dD0X5k?t=333)
8. Материал: Cycles 4D ▸ **xpExplosiaFX presets ▸ Burn** на домен; рендер в real-time превью Cycles. [▶ 5:56](https://youtu.be/RkAB9dD0X5k?t=356)

## Подводные камни
- Сильная деформация растягивает воксели — чем сильнее гнёте, тем больше нужно детализации вокселей.

## Как сейчас (новые инструменты)
**nxWarp** (бета 2026.1) деформирует дым напрямую клетками Helix / Path / Bend / Twist; GPU **nxExplosiaFX** (Fused 2025.4) — для самой симуляции.
