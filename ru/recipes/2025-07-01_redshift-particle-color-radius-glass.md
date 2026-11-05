# Рендер цвета и радиуса частиц как цвета ramp и веса стекла в Redshift (Change Range по xpConsole)

- Источник: Top Tip Tuesday — Rendering Particle Data — https://www.youtube.com/watch?v=7BzLibj9f8U (2025-07-01)
- Хост / поколение: закешированная сим NeXus/XP + Redshift (sphere instances через Object tag)
- Задача: абстрактные сферы: палитра из цвета частиц, крупные становятся стеклянными.

## Шаги
1. Студийный HDRI из Asset Browser; большая плоскость-фон (+Z, 4000×4000). [▶ 0:47](https://youtu.be/7BzLibj9f8U?t=47)
2. Эмиттер ▸ **Redshift Object tag ▸ Particles ▸ Sphere instances**. [▶ 1:17](https://youtu.be/7BzLibj9f8U?t=77)
3. Материал: **Color User Data** ▸ preset Particles ▸ Particle Color (случайный ч/б) → **Ramp** (палитра из пресета) → Base Color; низкий roughness. [▶ 2:26](https://youtu.be/7BzLibj9f8U?t=146)
4. Радиус: **Scalar User Data** ▸ preset Particles ▸ **Size** → **Change Range**. Старые min/max найдите через **xpConsole** (Data to Display ▸ Radius; двойной клик по колонке = min/max; здесь 1 → 104). [▶ 5:57](https://youtu.be/7BzLibj9f8U?t=357)
5. Ctrl-клик по **Weight** у Transmission, чтобы открыть его порт, подайте туда Change Range; настройте старый диапазон на **35 → 60**, чтобы стеклянными стали только крупные. [▶ 6:50](https://youtu.be/7BzLibj9f8U?t=410)
6. Материал фона = один цвет из ramp (скопируйте узел), roughness 1 → цельная палитра. [▶ 8:42](https://youtu.be/7BzLibj9f8U?t=522)
