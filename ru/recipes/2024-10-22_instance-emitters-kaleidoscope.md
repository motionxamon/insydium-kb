# Клонирование и отражение эмиттеров для калейдоскопа (режим Instance у xpEmitter + MoGraph Cloner)

- Источник: Top Tip Tuesday — Cloning Particle Emitters — https://www.youtube.com/watch?v=tantnHiZWE4 (2024-10-22)
- Хост / поколение: C4D; форма эмиттера X-Particles **Instance** + NeXus nxTurbulence / nxSpeed
- Задача: одна симуляция — много отражённых радиальных копий.

## Шаги
1. Базовый эмиттер: rectangle 30×0, rate 2000, life 60, speed 50; отображение dots, Gradient по **Direction (bank)**.
2. **nxTurbulence** strength 15 с **масштабом по оси Y 0** (плоское движение).
3. Если положить базовый эмиттер в Cloner, клонируется только форма, а не частицы.
4. Новый эмиттер ▸ Shape **Instance** → базовый эмиттер; базовый спрячьте. Такой instance-эмиттер клонируется **по-настоящему**.
5. Отражение: объект C4D **Instance** от instance-эмиттера, scale X **−1**, та же позиция; сгруппируйте оба (Alt+G).
6. **Cloner Radial**, count 11, null как дочерний → калейдоскоп.
7. Варианты: turbulence Voronoi, больше octaves, низкий persistence; **nxSpeed** (без ускорения) **max 50** при очень сильной турбулентности → медленно меняющиеся узоры.
