# Анимированные vertex maps из GPU-фоллоффов NeXus → управление эмиссией nxExplosiaFX

- Источник: Top Tip Tuesday — NeXus Falloffs (final Top Tip, #196) — https://www.youtube.com/watch?v=qv6TE9WtFhg (2026-11-03)
- Хост / поколение: **NeXus 2026.1 beta** — Cinema 4D и Blender (показаны оба)
- Продукты: NeXus (nxFalloffMap / Vertex Maps, слои nxFalloff, nxExplosiaFX)
- Задача: органичная «горящая кромка», которая расползается по мешу, записывается в vertex map и служит маской, чтобы дым/огонь шёл только с этой кромки.

## Дерево сцены (C4D)
```
Plane (100×100 segments — vertex density = map detail)
  └─ Vertex Map tag (auto-created)
nxFalloffMap  (INSYDIUM ▸ NeXus ▸ Presets)  ← Objects: Plane
  Falloffs (evaluated bottom → top):
    Blur              (top; few iterations — softens)
    Curve             (crush up → boost edge to full weight)
    Invert  [Blend: Multiply]   → keeps only the partial-weight band = leading edge
    Grow #2  (Shape off, high Spread/Reach → fills the interior)
    Grow #1  (Spread ~30, Shape 100% with Simplex noise → organic edge)
    Sphere   (radius ~20 cm, offset ~15 cm, keyframed across the plane)
nxExplosiaFX domain (sized around the plane)
  Sources: Plane, Surface Width 2
    Smoke / Temperature / Fuel → Weight by: Tag → drag the vertex map
```

## Шаги
1. Подразбейте объект (больше точек = детальнее карта). Добавьте **nxFalloffMap**, закиньте меш в Objects — сгенерируется vertex map (всё 0 / красное).
2. Добавьте фоллофф **Sphere** и анимируйте его (ключи позиции от одного края к другому примерно за 100 кадров). Уже это — анимированная vertex map.
3. Добавьте над ним слой **Grow**: вес расползается от сферы наружу. Уменьшите **Spread** (~30), чтобы замедлить. Его **Shape** (100%) ломает фронт через noise: поставьте noise **Simplex**, масштаб побольше, **Low Clip 0 / High Clip 100**, **Contrast 1** (убирает сильный клиппинг по умолчанию).
4. Noise продолжает анимироваться внутри заполненной области → добавьте сверху **второй Grow** с **Shape off** и высокими Spread/Reach, чтобы он заливал сплошняком всё позади шумного фронта.
5. Трюк с передней кромкой: добавьте сверху **Invert** и поставьте его blend в **Multiply** — останутся только промежуточные веса (мягкая полоса на фронте).
6. Добавьте **Curve** и задерите её так, чтобы полоса дошла до полного веса; добавьте **Blur** с небольшим числом итераций для сглаживания.
7. Скорость распространения = Spread первого Grow (например, 60 = быстрее).
8. Применение: nxExplosiaFX → Sources → плоскость; для Smoke, Temperature и Fuel поставьте **Weight by: Tag** и привяжите vertex map. Для маскированной эмиссии нужны значения повыше: поднимите Fuel (например, 3) и **Burn Rate**, чтобы всё топливо сгорало.

## Отличия в Blender
- Объекта в меню нет: выделите меш → **Object Data properties ▸ NeXus Vertex Maps** (переместите панель наверх стека) → **New** → создаётся атрибут **`nx_field`** (переименуйте или сконвертируйте в vertex group, если она нужна; для EFX не обязательно).
- Фоллоффы/слои модификаторов добавляются там же (Sphere radius 0.2 m, offset −0.1 / 0.1 m). Новые слои добавляются **снизу** — каждый вручную перемещайте наверх. Grow Spread 0.3 и т. д. (0–1 вместо %).
- Превью: включите отображение атрибута во viewport (синий → белый вместо красного → жёлтого в C4D).
- nxExplosiaFX Sources: эмиссия с плоскости, Fuel ~0.2, Temperature ~3000; для Smoke/Temperature/Fuel **Weight by: Attribute → nx_field**.

## Подводные камни
- Вычисление идёт снизу вверх: порядок Sphere → Grow → Grow → Invert → Curve → Blur важен.
- Маскированные эмиттеры выглядят слабо — поднимайте fuel/temperature и burn rate.
- Слои с памятью (Grow, Decay, Delay, Freeze) сбрасываются на кадре 1 и при скрабе назад — проигрывайте с начала.

## Также анонсировано в этом видео (следующая бета NeXus, «очень скоро» на 2026-11-03)
Единая GPU-динамика: **cloth**, управляемая теми же nx-модификаторами, что и частицы (nxTurbulence, nxGravity), **верёвки/шнуры**, закреплённые на суставах, **rigid bodies**, коллайдеры, общие с симуляциями частиц, **разрывы ткани + сплайны бахромы**, cloth maps и **двустороннее взаимодействие с nxExplosiaFX** (дым поднимает ткань, ткань расталкивает дым).
