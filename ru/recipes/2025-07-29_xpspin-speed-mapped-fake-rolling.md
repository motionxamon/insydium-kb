# Фейковое качение несферических частиц (случайное вращение xpSpin, привязанное к Speed)

- Источник: Top Tip Tuesday — Particle Spinning — https://www.youtube.com/watch?v=rzvJhmq1jbE (2025-07-29)
- Хост / поколение: симуляция коллизий NeXus + модификатор **CPU xpSpin** + инстансинг объектов через Redshift
- Задача: черепа/коробки, которыми управляет симуляция коллизий сфер, кувыркаются при движении и замирают в покое.

## Шаги
1. Emitters ▸ **Extended Data ▸ Use Rotation** + случайный поворот при рождении (разнообразие ориентаций, без вращения).
2. **Simple Spin** у emitter крутит вечно, даже в покое — не используйте.
3. **xpSpin** (Modifiers ▸ Motion) ▸ **Randomize Spin**, unidirectional выкл. (±), ~5° по каждой оси.
4. Mapping ▸ Random Spin ← **Speed**: 0 ниже ~5–8 cm/s, полное на 15 cm/s → в покое вращения нет.
5. Redshift Object tag на emitters инстансит кастомную геометрию; теперь она кувыркается.

## Подводные камни
Коллизии остаются сферическими → углы угловатых форм слегка пересекаются.

## Как сейчас (новые инструменты)
Режим **nxSpin ▸ Roll** (см. «Rolling particles nxSpin Roll», 2026) даёт настоящее качение; для полноценных rigid bodies см. «Particle Rigid Bodies» или единые rigid bodies в следующей бете.
