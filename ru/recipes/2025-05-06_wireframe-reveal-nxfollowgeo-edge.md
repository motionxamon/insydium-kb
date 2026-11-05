# Проявление wireframe частицами (nxFollowGeo в режиме Edge + nxTurbulence + ограничение nxSpeed)

- Источник: Top Tip Tuesday — Wireframe Reveal — https://www.youtube.com/watch?v=RUhF1pju3Wk (2025-05-06)
- Хост / поколение: C4D; NeXus внутри X-Particles (nxFollowGeo, nxTurbulence, nxSpeed, nxAttract) + xpTrail для рендера
- Задача: частицы ползут по рёбрам модели и прорисовывают её wireframe.

## Шаги
1. Эмиттер: **width 50, height 0** (тонкая полоска), Display **Dots**, ставим вплотную к модели; **speed 0, radius 2**, эмиссия **90 кадров по 20,000/с**. [▶ 0:27](https://youtu.be/RUhF1pju3Wk?t=27)
2. **nxFollowGeo**: объект = голова волка, режим **Surface**, **Field of Vision 360°**, **Friction 1%**, **Distance 25**, чтобы захватить все частицы. [▶ 1:10](https://youtu.be/RUhF1pju3Wk?t=70)
3. Движение: **nxTurbulence** strength **40**, добавьте октав, снизьте persistence (мелкая детализация при сохранении крупных завихрений). [▶ 1:33](https://youtu.be/RUhF1pju3Wk?t=93)
4. Успокаиваем: **nxSpeed** ниже турбулентности, Accelerate с **Force 0**, **Max Speed 80 cm** — турбулентность сильная, но скорость ограничена. [▶ 2:34](https://youtu.be/RUhF1pju3Wk?t=154)
5. Режим nxFollowGeo **Surface → Edge**; поднимите параметр Edge, чтобы частицы плотнее липли к рёбрам → проявление wireframe. [▶ 3:05](https://youtu.be/RUhF1pju3Wk?t=185)
6. Арт-дирекшн: **nxAttract** между турбулентностью и скоростью; двигайте его, чтобы управлять направлением потока. [▶ 3:40](https://youtu.be/RUhF1pju3Wk?t=220)
7. Опционально: **xpTrail** на эмиттере для рендера переплетённых линий.

## Подводные камни
Порядок модификаторов важен: turbulence → attract → ограничение скорости последним.

## Как сейчас (новые инструменты)
2026.1 beta: слой nxSpeed называется **Acceleration**; в 2026.1 **nxWarp** (режимы Path/Flow) и 16 режимов nxFalloff дают больше контроля над направлением; в NeXus 2026 вместо xpTrail используйте **nxTrail**.
