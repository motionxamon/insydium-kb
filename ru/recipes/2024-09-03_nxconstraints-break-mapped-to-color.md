# Пружинящие ленты и рассыпчатые гранулы по цвету (nxConstraints Birth connections, Break через маппинг на Color Brightness)

- Источник: Top Tip Tuesday — Particle Constraints Mapping — https://www.youtube.com/watch?v=SPsm-D_hero (2024-09-03)
- Хост / поколение: C4D; NeXus G2 (nxGravity, nxConstraints + NeXus Mapping) на xpEmitter; теги xpCollider
- Задача: белые частицы связаны неразрывными пружинами, чёрные падают свободно, серые — что-то среднее.

## Исходная сцена
- Плоскость пола **8000 × 8000 cm**, коллайдер: bounce 0, немного friction, немного **Scatter**. Череп барана с тегом Vibrate (вращение), коллайдер: bounce 0, чуть-чуть friction.
- Плоский xpEmitter, направленный в **−Y**, **200 × 1500**; Rate, life **220** (var 30), **15,000/s**, speed 0.
- **nxGravity** Strength ~**500 cm**.

## Шаги
1. Emitter Display ▸ Color **Shader ▸ Noise**: Global Scale ~**600**, low/high clip для контраста, Animation Speed **0.5**, чтобы значения при эмиссии менялись; затемняйте, пока не получится смесь чёрного и белого.
2. **nxConstraints ▸ Birth** connections: Iterations **3**, Connection Limit **12**, Radius **60 cm**, сначала Break **None** (всё пружинит).
3. Break **Absolute**, threshold **300 cm** (не достигается → визуально без изменений).
4. **Mapping ▸ Color Brightness**: Category **Birth constraints**, Parameter **Break**, диапазон 0 → 1 → чёрный = 0 cm (рвётся сразу), белый = полные 300 cm (не рвётся никогда).
5. Крутите noise, чтобы сместить соотношение: больше белого = больше лент; серые = более слабые связи.

## Как сейчас (новые инструменты)
Те же слои в nxConstraints NeXus 2026; в 2026.1 Mapping позволяет одним слоем управлять многими целями, а **nxPin** может закрепить группы, если нужны зафиксированные концы.
