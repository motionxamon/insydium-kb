# Анимированные экструзии с подразбиением по полям (mtSubdivider + mtInset со слоями Fields)

- Источник: Top Tip Tuesday — Dynamic Subdivisions — https://www.youtube.com/watch?v=5g0K2rUBWlk (2024-06-25)
- Хост / поколение: C4D; только MeshTools (mtSubdivider, mtInset) + C4D Fields
- Задача: плоскость разбивается на плитки по noise, которые выдавливаются движущейся ступенчатой волной.

## Шаги
1. Плоскость с сегментами **1×1** → дочерний объект **mtSubdivider**, **levels 7**.
2. Subdivider **Shader ▸ Noise**: **low clip 35** и пережат для контраста; уменьшите **Tolerance**; перебирайте seed.
3. **mtInset** с subdivider в качестве дочернего: **Amount 33**, **Offset 100** → у каждого полигона появляется внутренний полигон, выдавленный наружу.
4. Fields у Inset: поле **Linear**, длина 180, Remapping — контурная кривая с ease. Переключите **Sampling** у Inset с Per Point на **Centered** → внутренние полигоны остаются плоскими (ступеньки).
5. Поле **Random** в режиме **Overlay**, чтобы разбить линейный переход.
6. Анимация: тег **Vibrate** на linear field, rotation включён (большая амплитуда по heading, ~100 по остальным).
7. Поле **Delay**, режим **Spring**, 30% → запаздывающее доводящее движение.
8. Поле **Spherical** в режиме **Multiply** с плавной кривой, чтобы ограничить эффект центром. Уберите поля из фильтра viewport, чтобы их скрыть.
9. Режимы Subdivider: **Bilinear** (по умолчанию), **Bilinear Offset** (случайная прямоугольная плитка), **Shards**, **Whirl** (внутренние + внешние полигоны; Strength даёт тонкие/толстые полосы) — всё анимируется.
