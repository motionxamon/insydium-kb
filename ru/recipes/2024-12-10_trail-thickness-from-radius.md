# Шлейфы, толщина которых следует за радиусом частиц (xpTrail Thickness: Use Radius Variable → кривые Redshift)

- Источник: Top Tip Tuesday — Varied Trail Thickness — https://www.youtube.com/watch?v=Lx6Sugl11TA (2024-12-10)
- Хост / поколение: NeXus (nxColor, nxScale) + CPU **xpTrail** + Redshift
- Задача: стеклянные цветные шлейфы, которые утолщаются и истончаются вслед за изменением размера частиц.

## Шаги
1. Эмиттер в режиме Defined, count 5, speed ~330; **nxColor** gradient-by-parameter от крупного поля Perlin random.
2. **xpTrail** с эмиттером → **Redshift Object tag ▸ Curves ▸ Capsules**, thickness 200 для первого просмотра.
3. Цвет: xpTrail ▸ Thickness & Color ▸ Trail Color **Per Vertex** (запоминает историю цвета); Redshift **Vertex Attribute ▸ пресет Curves ▸ Curve Color** → в transmission color стеклянного материала.
4. Ширина на каждый шлейф: thickness в Redshift обратно на 1; режим xpTrail Thickness **Use Particle Current** → каждый шлейф = размер своей частицы. Mesh subdivisions **Adaptive** (гладко).
5. Анимированная ширина: **nxScale** Set by Falloff с тем же random-полем; radius эмиттера 200, без вариации; xpTrail Thickness **Use Radius Variable** → ширина прорисовывается вдоль шлейфа.
6. Thickness factor **2** = точный диаметр частицы (считается от радиуса).

## Как сейчас (новые инструменты)
Шлейфы NeXus (GPU-шлейфы в стиле nxTrail, см. «NeXus Particle Trails»), где они доступны; доступ к данным для рендера остаётся прежним.
