# Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)

- Источник: INSYDIUM LIVE! — November 2023 – X-Particles, NeXus, Taiao, MeshTools & Cycles 4 — https://www.youtube.com/watch?v=qaso-gPGBnI (2023-11-16)
- Хост / поколение: C4D; G2 NeXus (nxTurbulence, nxAttract, nxBlend) вместе с CPU xpColor + полями из xpEmitter. Часть B из 3 (шот с туманностью Джона Хендерсона)
- Задача: потоки частиц закручиваются вокруг нескольких планет, затем по ним расползается белая «инфекция» — маска свечения для рендера.

## Шаги — орбиты
1. Два эмиттера в начале координат, Height **1 cm** (лента). Speed **250, Variation 50** (200–300); Radius 2, Variation 1. Display Gradient по **Speed + Auto**, чтобы читать симуляцию. [▶ 34:04](https://youtu.be/qaso-gPGBnI?t=2044)
2. **nxTurbulence** с настройками по умолчанию.
3. Принцип **nxAttract**: притяжение vs **Speed Limit** vs инерция частиц. Лимит по умолчанию 250; при 1000 частицы улетают далеко, прежде чем развернуться. [▶ 38:33](https://youtu.be/qaso-gPGBnI?t=2313)
4. Рабочий сетап: Attraction type **Force**, Force **150**, **Speed Limit 350** (выше самой большой скорости при рождении). Бросьте планеты (стандартные сферы) в список объектов — три планеты, 250 F. [▶ 40:32](https://youtu.be/qaso-gPGBnI?t=2432)
5. Каждая планета делит поток, поэтому включите второй эмиттер для плотности; двигайте планеты вживую, чтобы перебалансировать. [▶ 42:47](https://youtu.be/qaso-gPGBnI?t=2567)
6. Extended Data ▸ Rotation **Random**, spin 3° по каждой оси; Box display показывает ориентацию. [▶ 45:06](https://youtu.be/qaso-gPGBnI?t=2706)

## Шаги — инфекция
7. Display — один цвет, **чёрный**. xpSystem ▸ только модификаторы в той же системе; Ctrl-перетаскиванием дублируйте → система "infecting", эмиттеры по 15 частиц. [▶ 46:19](https://youtu.be/qaso-gPGBnI?t=2779)
8. Основная система: **xpColor** (CPU) Set Color белый (не Immediate). Эмиттеры-заразители ▸ Editing ▸ **Editable**, чтобы Fields видели их как точки; перетащите их в Fields у xpColor, режим **Max**, radius 3 → 5 (больше = быстрее распространение; больше заразителей тоже ускоряет). [▶ 49:05](https://youtu.be/qaso-gPGBnI?t=2945)
9. Сделайте заразителей белыми. **nxBlend**: режим **Addition** (передаются только более яркие значения), Distance 5, Strength 100, Color → плавное градиентное распространение. [▶ 50:51](https://youtu.be/qaso-gPGBnI?t=3051)
10. Затем чёрно-белый цвет используется в Cycles 4D как маска emission. [▶ 1:14:16](https://youtu.be/qaso-gPGBnI?t=4456)

## Бонус (из Q&A): пересечение объектов с xpDynamics
Включите **Push** (100) в каждом теге xpDynamics; если всё равно пересекаются — добавьте частиц (Distribution vertices + midpoints): сталкиваются частицы, а не полигоны.

## Подводные камни
- CPU-модификаторы xp и GPU-модификаторы nx работают вместе на одном эмиттере.

## Как сейчас (новые инструменты)
**nxColor** (2024.2) с nxFalloff (режимы Points/Object в 2026.1) вместо xpColor + полей C4D; **nxInfectio** для полноценного распространения (см. рецепт 2023-12-12). Орбиты: nxAttract без изменений; nxWarp Helix/Path может формировать потоки.
