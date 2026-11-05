# Типы отображения частиц во viewport и их рендер (вкладка Display у эмиттера + генератор Display Render)

- Источник: Top Tip Tuesday — NeXus Particle Display — https://www.youtube.com/watch?v=0x9Hidcw6Fw (2023-05-09)
- Хост / поколение: C4D; xpEmitter с nxTurbulence (G2 GPU) — с CPU xpTurbulence работает точно так же; X-Particles material, стандартный рендер
- Задача: видеть во viewport реальный размер/вращение частиц и рендерить формы отображения как геометрию.

## Шаги
1. Эмиссия: radius **5 cm**, вариация **4 cm** (→ 1–9 cm). [▶ 1:02](https://youtu.be/0x9Hidcw6Fw?t=62)
2. Вкладка Display: по умолчанию **Squares** — как и Dots, Ticks и Axes, этот тип игнорирует размер частицы. Display Size Factor (например, 500%) лишь равномерно их масштабирует; верни на 100%. [▶ 0:54](https://youtu.be/0x9Hidcw6Fw?t=54)
3. Выбери любой тип начиная с **Box** и ниже (например, **Box Filled**, **Arrow**), чтобы видеть настоящий размер. [▶ 1:57](https://youtu.be/0x9Hidcw6Fw?t=117)
4. Режим цвета **Single → Gradient Random**; Load Preset **Full Colors** для разноцветности. [▶ 2:47](https://youtu.be/0x9Hidcw6Fw?t=167)
5. Стрелки лучше всего читаются с вращением: Extended Data ▸ General ▸ **Use Rotation**, тип **Tangential** (смотрят по направлению движения). [▶ 3:10](https://youtu.be/0x9Hidcw6Fw?t=190)
6. Рендер: Create ▸ Extensions ▸ **X-Particles Material** на эмиттере рендерит только круги. [▶ 3:44](https://youtu.be/0x9Hidcw6Fw?t=224)
7. INSYDIUM ▸ X-Particles ▸ Generators ▸ **Display Render** (xpDisplayRender); подключи эмиттер; **перенеси материал с эмиттера на объект Display Render** → стрелки рендерятся. Переключи отображение на **Pyramids** и т. п. — они тоже будут рендериться. [▶ 4:45](https://youtu.be/0x9Hidcw6Fw?t=285)

## Подводные камни
X-Particles material на «голых» частицах всегда рендерит сферы/круги; форму отображения несёт только сгенерированный объект.

## Как сейчас (новые инструменты)
У nxEmitter в NeXus 2026 до 8 каналов отображения; для геометрии на рендер используй nxGenerator (инстансинг) или nxMesher.
