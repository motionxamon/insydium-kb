# Лазерные лучи от частиц внутри сферы (mtRayline + nxConstraints Forces + xpTrail)

- Источник: Top Tip Tuesday — Rayline Particles — https://www.youtube.com/watch?v=t-gWrfo_NRk (2024-04-23)
- Хост / поколение: C4D; NeXus GPU (nxTurbulence, nxConstraints) на xpEmitter + MeshTools **mtRayline** + CPU xpTrail
- Задача: каждая частица выпускает луч, который останавливается на сфере; из точек контакта рождаются короткие изогнутые трейлы.

## Исходная сцена
Sphere (display tag Lines/isoparms, чтобы видеть внутренность). xpEmitter **Rectangle**, высота 1 cm (длинная тонкая полоса), **Shot 1000**, speed 0. **nxTurbulence Curl**: scale 70, frequency 10, additive velocity выкл.

## Шаги
1. **mtRayline**: Shape → **X-Particles**, перетащите эмиттер; Point Count **Custom (10) → All Points**.
2. Эмиттер **Extended Data ▸ Rotation: Tangential** — иначе все лучи смотрят в +Z.
3. Rayline: добавьте сферу как **collider**, увеличьте Ray Length, чтобы лучи всегда до неё доставали, включите **Single Shot** (стоп на первом контакте, без отражений).
4. Удерживайте частицы в полосах: слой **nxConstraints ▸ Forces**, repulsion выкл.; притяжение до 30 соседей в радиусе 35 cm (позже больше), min distance 5 → **0**, falloff **Flat**, высокая сила притяжения → длинные щупальца, которые расходятся и снова сливаются.
5. Успокойте суетливое кружение: уменьшите **rate of change** тангенциального вращения на эмиттере.
6. Rayline ▸ Points ▸ **Contact Points ▸ добавить эмиттер** (зелёные точки контакта становятся частицами).
7. **xpTrail** на этом новом эмиттере: length 10 кадров, var 5. Сплайн трейла → **B-spline, Natural** промежуточные точки для плавных кривых.
8. Скройте эмиттеры; рендерите с аддитивным материалом.

## Как сейчас (новые инструменты)
nxTrail (NeXus 2026) для трейлов из точек контакта; исходные частицы/constraints работают так же с nxEmitter. mtRayline по-прежнему основной инструмент для лучей.
