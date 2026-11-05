# Укорачивание трейлов до смерти частиц (xpTrailsMod через xpQuestion или action Change Trails)

- Источник: Top Tip Tuesday — Shrink Trails — https://www.youtube.com/watch?v=WqfbeF2OQOk (2023-04-04)
- Хост / поколение: C4D; CPU X-Particles (xpEmitter, xpTrail, xpTrailsMod, Questions/Actions)
- Задача: трейлы плавно втягиваются, а не пропадают, когда их частица умирает.

## Исходная сцена
Sphere emitter + **xpTrail** (Full Scene Trail выключен, **Trail Length 30**). Простой lifespan 110 F заставляет трейлы резко исчезать — трейл не может существовать без своей частицы, — поэтому оставьте полный lifespan.

## Шаги — способ A (настраиваемый)
1. Modifiers ▸ Control ▸ **xpTrailsMod** (операция **Shrink**). По умолчанию он всегда включён, так что трейлы укорачиваются раньше, чем вырастают, — ему нужен триггер.
2. Emitter ▸ Questions ▸ добавьте вопрос: **Particle Data ▸ Age**, каждый кадр, **greater than 110** кадров → **Activate Modifier**: xpTrailsMod.
3. Опции модификатора: Shrink / Expand / Grow / Pulse; **Interval** (например, 10 = укорачивать только каждый 10-й кадр → медленнее); высокий **Rate of Change** = почти мгновенно.
4. Убийство на нуле: в слот action модификатора (трейл дошёл до нуля) добавьте **Direct Action ▸ Change Life** (по умолчанию = kill).

## Шаги — способ B (быстрый)
5. Удалите модификатор и Change Life; на тот же вопрос Age > 110 добавьте **Direct Action ▸ Object Action ▸ Emitter/Generator ▸ Change Trails**, привяжите xpTrail, включите **Shrink Trails** и **Kill particles at zero**. Опций меньше, результат тот же.

## Как сейчас (новые инструменты)
Для GPU (nx) emitter пересоберите триггер по Age в **nxQuestion** — CPU-вопросы ненадёжно управляют GPU emitter; именно этот action укорачивания трейлов — функция CPU xpTrail.
