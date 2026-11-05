# Анимированные экструзии с подразбиением по полям (mtSubdivider + mtInset со слоями Fields)

- Источник: Top Tip Tuesday — Dynamic Subdivisions — https://www.youtube.com/watch?v=5g0K2rUBWlk (2024-06-25)
- Хост / поколение: C4D; только MeshTools (mtSubdivider, mtInset) + C4D Fields
- Задача: плоскость разбивается на плитки по noise, которые выдавливаются движущейся ступенчатой волной.

## Шаги
1. Плоскость с сегментами **1×1** → дочерний объект **mtSubdivider**, **levels 7**. [▶ 0:25](https://youtu.be/5g0K2rUBWlk?t=25)
2. Subdivider **Shader ▸ Noise**: **low clip 35** и пережат для контраста; уменьшите **Tolerance**; перебирайте seed. [▶ 0:50](https://youtu.be/5g0K2rUBWlk?t=50)
3. **mtInset** с subdivider в качестве дочернего: **Amount 33**, **Offset 100** → у каждого полигона появляется внутренний полигон, выдавленный наружу. [▶ 1:53](https://youtu.be/5g0K2rUBWlk?t=113)
4. Fields у Inset: поле **Linear**, длина 180, Remapping — контурная кривая с ease. Переключите **Sampling** у Inset с Per Point на **Centered** → внутренние полигоны остаются плоскими (ступеньки). [▶ 3:09](https://youtu.be/5g0K2rUBWlk?t=189)
5. Поле **Random** в режиме **Overlay**, чтобы разбить линейный переход. [▶ 3:40](https://youtu.be/5g0K2rUBWlk?t=220)
6. Анимация: тег **Vibrate** на linear field, rotation включён (большая амплитуда по heading, ~100 по остальным). [▶ 3:53](https://youtu.be/5g0K2rUBWlk?t=233)
7. Поле **Delay**, режим **Spring**, 30% → запаздывающее доводящее движение. [▶ 4:13](https://youtu.be/5g0K2rUBWlk?t=253)
8. Поле **Spherical** в режиме **Multiply** с плавной кривой, чтобы ограничить эффект центром. Уберите поля из фильтра viewport, чтобы их скрыть. [▶ 4:37](https://youtu.be/5g0K2rUBWlk?t=277)
9. Режимы Subdivider: **Bilinear** (по умолчанию), **Bilinear Offset** (случайная прямоугольная плитка), **Shards**, **Whirl** (внутренние + внешние полигоны; Strength даёт тонкие/толстые полосы) — всё анимируется. [▶ 5:35](https://youtu.be/5g0K2rUBWlk?t=335)
