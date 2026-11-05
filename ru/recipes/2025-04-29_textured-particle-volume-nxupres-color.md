# Объёмное облако частиц, окрашенное UV-текстурой объекта (эмиттер с поверхности по текстуре + nxUpres Color + Initial State)

- Источник: Top Tip Tuesday — Textured Particle Volume — https://www.youtube.com/watch?v=N32nQXnqMLE (2025-04-29)
- Хост / поколение: C4D; NeXus внутри X-Particles (nxUpres, nxTurbulence) на xpEmitter; рендер в Redshift
- Задача: сплошная (заполненная) версия текстурированной модели из частиц, окрашенная по всему объёму и готовая к симуляции.

## Исходная сцена
Гриб из Content Browser (~10 cm, текстура по UV). Эмиттер с поверхности: режим Object, **Shot Random, 500,000 частиц, radius 0.04, speed 0**.

## Шаги
1. Эмиттер с поверхности ▸ Object ▸ эмиссия из **Texture**; вкладка Texture: перетащите тег текстуры модели, **Emit channel None** (везде), **Color channel = Color** → получается только окрашенная оболочка. [▶ 1:44](https://youtu.be/N32nQXnqMLE?t=104)
2. Дубликат → "emitter volume": **Shot Hexagonal** (заполняет объём с шагом радиуса частицы) + небольшой **Jitter** по X/Y/Z. У объёма есть глубина, но нет цвета (текстуры не могут окрасить объём). [▶ 2:54](https://youtu.be/N32nQXnqMLE?t=174)
3. **nxUpres**: Source = эмиттер с поверхности, Destination = объёмный эмиттер; снимите Velocity, отметьте **Color**. Каждая частица объёма смешивает цвета 3 ближайших частиц поверхности. Скройте частицы поверхности, шагните на один кадр. [▶ 4:12](https://youtu.be/N32nQXnqMLE?t=252)
4. Объёмный эмиттер ▸ **Initial State ▸ Set State**; Emission → **Controlled Only**. Отключите эмиттер поверхности и nxUpres. [▶ 5:35](https://youtu.be/N32nQXnqMLE?t=335)
5. Рендер: материал с **Color User Data (Particle Color)**, **Redshift Object tag ▸ Sphere instances**. Дальше симулируйте как угодно (в демо — nxTurbulence; подходит и для гранулярного рассыпания). [▶ 6:04](https://youtu.be/N32nQXnqMLE?t=364)

## Как сейчас (новые инструменты)
В NeXus 2026 та же схема (Initial State в nxEmitter, nxUpres). В 2026.1 beta nxEmitter также умеет эмитить из облаков точек / гауссовых сплатов, которые несут собственный цвет.
