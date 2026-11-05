# Обзор функций: переработанный nxQuestion и Data Mapping в NeXus (Fused 2023.3)

- Источник: INSYDIUM Fused Release Update — July 2023 - NeXus Control Sneak Peek — https://www.youtube.com/watch?v=_imkCRS1vqI (2023-07-03)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (GPU, Vulkan) — Fused 2023.3 (5 Jul 2023)
- Задача: запускать эффекты по данным частиц/сцены через логическую иерархию на GPU и привязывать любой параметр модификатора к данным частиц.

## nxQuestion — логика в виде иерархии объектов
- Questions и Actions — слои в одном объекте **nxQuestion**; Actions лежат дочерними под тем Question, на который отвечают. Пример: **Age = 30 F** → **Set Radius 10 cm**; переключите данные на **Distance Traveled 150 cm** — получится триггер по пройденному пути.
- У Actions есть **Weight** (плавный переход к значению вместо скачка) и **Delay**; вопросы/действия складываются без ограничений.
- **Fields** C4D можно использовать как источник вопроса; вопрос **Object Volume** ограничивает эффект внутренностью меша (рекурсивный спавн остаётся внутри букв).
- Слой **Loop**, например **Time Cycle** с включёнными Position + Velocity → частицы возвращаются в исходные позиции.
- Быстрый GPU-**поиск соседей** управляет рекурсивным ростом через спавн.
- Слой **Script**: свой GLSL-код (Vulkan). INSYDIUM даёт pre-prompt, чтобы ChatGPT писал скрипты (демо: цвет во времени + radius 3 → 40); код вставляется в пустой слой Script в nxQuestion.
- Слои **Variable** в режиме **User Data** → свой интерфейс в User Data C4D → по сути собственный GPU-модификатор (пример полёта стаями с 4 переменными).

## Data Mapping (новая вкладка Mapping у каждого модификатора и динамического модификатора)
- Добавляйте слои map: источник (Age, Color, Distance…) → параметр, форма задаётся кривой. Пример: **nxGravity** Color map → Strength гравитации, светлые частицы тянутся в полную силу.
- Слои складываются: **nxWind** с Color Brightness → Strength ветра плюс map **Distance** → Turbulence (в полную силу после **150 cm** пути).
- Для динамики тоже: **nxFluids SPH** Age map, категория SPH ▸ **Viscosity** 0 на 0.5 s → максимум на 0.6 s; дубликат — для **Surface Tension**.

## Что заменяет
CPU xpQuestion/xpAction и CPU Data Mapping на xp-модификаторах для GPU-эмиттеров. Сейчас: nxQuestion по-прежнему система логики (в 2026.1 добавлены Quill AI в Blender, Sleep/Bind); Mapping теперь поддерживает один слой → много целей и зацикливание (2025.4).
