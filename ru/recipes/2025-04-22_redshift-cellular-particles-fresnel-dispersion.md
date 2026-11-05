# Вид микроклеток в Redshift (светящиеся сферы с Fresnel-прозрачностью внутри стеклянного меша с дисперсией)

- Источник: Top Tip Tuesday — Redshift Cellular Particles — https://www.youtube.com/watch?v=t6WmbzfNxGU (2025-04-22)
- Хост / поколение: C4D; закэшированная симуляция X-Particles + CPU **xpOpenVDBMesher**; Redshift (инстансы сфер через object tag)
- Задача: светящиеся «клетки» с подсвеченным контуром, видимые сквозь преломляющую оболочку с цветовым расслоением.

## Исходная сцена
Закэшированная анимация клеток из частиц; на эмиттере **Redshift Object tag ▸ Particles ▸ Sphere instances**; xpOpenVDBMesher мешит те же частицы. В итоге свет не нужен (частицы светятся сами).

## Шаги
1. Материал частиц (Standard): **Base Color weight выключен, Reflection выключен, Emission weight 2** (позже поднимем). [▶ 1:22](https://youtu.be/t6WmbzfNxGU?t=82)
2. Нода **Fresnel**, **Use IOR выключен**, curve **3** → выход в **Geometry ▸ Opacity**: фронтально = прозрачно, по краям = непрозрачные кольца. [▶ 2:55](https://youtu.be/t6WmbzfNxGU?t=175)
3. Redshift tag ▸ у инстансов **Scale Multiplier 0.5**, чтобы сферы были внутри меша. [▶ 3:16](https://youtu.be/t6WmbzfNxGU?t=196)
4. **Color User Data** ▸ пресет **Particles ▸ Particle Color** → Emission Color (Ctrl-клик по кнопке порта, чтобы вывести вход). [▶ 3:42](https://youtu.be/t6WmbzfNxGU?t=222)
5. Материал мешера: Base Color выключен, **Transmission weight 1**, Reflection roughness 0, **IOR 1.1** (отражения только по краям). [▶ 4:55](https://youtu.be/t6WmbzfNxGU?t=295)
6. Магия: **Dispersion (Abbe) 0.1** — чем меньше, тем сильнее расслоение цвета (при 1 почти незаметно). [▶ 5:53](https://youtu.be/t6WmbzfNxGU?t=353)
7. Тонкая настройка: контур тоньше — Fresnel curve **5–7**, затем поднимите **Emission частиц до ~4–10** для компенсации. [▶ 6:14](https://youtu.be/t6WmbzfNxGU?t=374)

## Подводные камни
Частицы внутри меша рендерятся чёрными, пока материал мешера не станет прозрачным (transmission).

## Как сейчас (новые инструменты)
Замените xpOpenVDBMesher на GPU-**nxMesher** (Fused 2025.4; без мерцания, выводит цвет/скорость) — шейдинг в Redshift не меняется.
