# Управление тем, откуда объект эмитит (xpEmitter Polygon Area, Falloff, кривая Topology Height, Emit from Texture)

- Источник: Top Tip Tuesday — Emission Control — https://www.youtube.com/watch?v=GebrRmY2L4Q (2023-09-19)
- Хост / поколение: C4D; CPU **xpEmitter** (настройки эмиссии, не зависят от солвера)
- Задача: ограничить и сформировать эмиссию на торе с помощью falloff, высоты и анимированной текстуры.

## Исходная сцена
Эмиттер с модификаторами wind + turbulence.

## Шаги
1. Эмиттер Shape **Rectangle → Object**, перетащите **Torus**. Emit From **Polygon Center** (по умолчанию) → **Polygon Area** для равномерного распределения по поверхности.
2. Вкладка **Falloff**: форма **Infinite → Sphere**; двигайте её, чтобы эмиссия шла только внутри (потом верните Infinite).
3. Вкладка **Topology** ▸ **Height**: Min **0** (origin объекта, середина тора) / Max **50** (верх) → эмитит только верхняя половина. Slope и Curvature работают так же.
4. Отредактируйте **сплайн-кривую** topology: опустите первый узел → меньше частиц внизу = мягкий край; двигайте его, чтобы настроить затухание.
5. Случайные пятна: новый материал, Color ▸ шейдер **Noise** типа **Stupl**, Space **Texture → UV**, поднимите Low Clip / опустите High Clip для контраста, **Animation Speed 0.5**; включите **Animate Preview** в настройках viewport.
6. Emit From **Texture** → вкладка Texture, перетащите texture tag, используйте канал **Color** (остальные выкл.) → частицы рождаются только из светлых движущихся полос.

## Как сейчас (новые инструменты)
**nxFalloff** в NeXus 2026.1 (16 режимов, включая Curvature, Noise) может так же маскировать модификаторы уже после эмиссии; см. также рецепт 2023-12-05 про radius/speed/offset от текстуры.
