# Жидкий обратный отсчёт: жидкость течёт по анимированным сплайнам цифр (xpFlowField + nxFoam)

- Источник: Top Tip Tuesday — Liquid Countdown — https://www.youtube.com/watch?v=C_fXmAUTb2Q (2025-10-28)
- Хост / поколение: C4D, жидкости/пена NeXus + CPU **xpFlowField** + MeshTools **mtSplineSample**
- Задача: вода в коробке закручивается в цифры 5-4-3-2-1.

## Шаги
1. Куб-контейнер с **xpCollider Normals: Inside**. Box-эмиттер того же размера, **Shot – Regular**, radius 3, full life. nxGravity; **nxFluids SPH** substeps 4, viscosity 4.
2. Текстовый сплайн с цифрами на ключах → равномерно пересэмплируем: **mtSplineSample** (дочерний объект = текст), Close, режим **Distance**, плюс сглаживание → равный шаг точек = равномерные векторы потока.
3. **xpFlowField** по размеру контейнера:
   - Слой **Along Spline** (линкуем spline-sample) → векторы вдоль контуров.
   - Сверху слой **To Spline** (притяжение к контурам) с уменьшенной силой (Normal blend) → смешиваем.
   - Affect: **Velocity**, speed ~160 (возможны также Direction-only или Acceleration). По желанию слой/модификатор турбулентности для хаоса.
4. **Кешируем** жидкость (170 кадров, быстро), затем отключаем flow field, spline sample и fluids (эмиттер и гравитацию оставляем — пене нужна гравитация).
5. **nxFoam** → **Add Emitter** (отображение Dots); оставляем только слой **Crest** (убираем Aerate/пузыри), снижаем crest rate, **After Age 7**, life ~70 → мелкая детализация на закешированной жидкости.

## Как сейчас (новые инструменты)
В 2026.1 beta есть GPU **nxFlowField** (Blender/NeXus 2026) и **nxWarp Path/Flow** для направления частиц по формам.
