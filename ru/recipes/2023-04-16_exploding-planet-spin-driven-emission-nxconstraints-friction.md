# Взрывающаяся планета: эмиссия с текстуры, зависящая от скорости вращения, и слипающиеся обломки (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)

- Источник: NAB 2023 — INSYDIUM Training — NeXus Friction - Part 1 — https://www.youtube.com/watch?v=6sdlTZsi9kQ (2023-04-16)
- Хост / поколение: C4D; G2 — функции CPU xpEmitter (эмиссия с текстуры, motion inheritance) + NeXus GPU **nxDrag** и **nxConstraints** (оранжевые эмиттеры)
- Задача: вращающаяся сфера срывает с себя полосатые потоки частиц только на пике скорости вращения; потоки тормозят и слипаются.

## Исходная сцена
- Sphere ▸ Type **Icosahedron**, Segments **100** (ровная топология).
- Материал на сфере: Color ▸ **Noise**, тип **Stupl**, Octaves **10**, Global Scale **230**, масштаб растянут по X и сжат по Y, **Low Clip** сильно поднят, **High Clip** опущен → тонкие белые полосы; перебирайте Seed для вариантов.
- Texture tag Projection **UVW → Spherical** (у примитива нет настоящих UV, иначе эмиссия не совпадёт с текстурой).
- Анимация (200 F): ключи вращения H **0° @ F0, 180° @ F60, 220° @ F120**; в Timeline переключите Dope Sheet → **F-Curve** и выгните кривую: медленно → очень быстро → медленно.

## Шаги
1. **xpSystem** («system motion») со своим **xpEmitter**: Emitter Shape **Object** = сфера, Emission Source **Texture** → во вкладке Texture укажите texture tag сферы (эмиссия со светлых участков Color channel, цвет частиц оттуда же). Speed **0**. [▶ 31:41](https://youtu.be/6sdlTZsi9kQ?t=1901)
2. Единицы Birth Rate **Per Second → Per Frame** (дело вкуса: точно знаешь, сколько рождается за кадр). [▶ 2:05](https://youtu.be/6sdlTZsi9kQ?t=125)
3. Emission ▸ **Motion Inheritance**: включить, linear выключить, **rotational включить** → частицы слетают по касательной. [▶ 10:32](https://youtu.be/6sdlTZsi9kQ?t=632)
4. Эмиссия от скорости вращения: сфера ▸ Programming Tags ▸ **Expresso**. Выход ноды сферы **Rotation Velocity** → **Calculate ▸ Range Mapper** → вход ноды эмиттера **Emission ▸ Birth Rate**. [▶ 25:35](https://youtu.be/6sdlTZsi9kQ?t=1535)
5. Range Mapper: Input Range **Degrees**; Input Lower **~150°/с** (пробовали 100 и 160), Input Upper **360°/с**; Output Lower 0, Output Upper большой (в демо **30,000**) → пока вращение медленное, ничего не рождается. [▶ 27:36](https://youtu.be/6sdlTZsi9kQ?t=1656)
6. **nxDrag**: Density **Water**, Strength multiplier **50**. Drag зависит от радиуса частицы (крупнее = сильнее тормозит): радиус эмиттера **2**, variation **0.5**. Display **Dots** для скорости вьюпорта. [▶ 27:54](https://youtu.be/6sdlTZsi9kQ?t=1674)
7. **nxConstraints ▸ слой Friction** (не пружинные connections): по умолчанию Friction 80, до **16** соседей в радиусе **30 cm** — тяжело для GPU, поэтому на этапе блокинга уменьшайте радиус и Connection Limit, а для финального cache поднимайте. [▶ 23:15](https://youtu.be/6sdlTZsi9kQ?t=1395)
8. Дублируйте эмиттер → **emitter big**: display Squares; своя копия Range Mapper (Ctrl-перетаскивание ноды) с Output Upper **500**. На original и big: Speed **1** с небольшой вариацией. [▶ 24:33](https://youtu.be/6sdlTZsi9kQ?t=1473)
9. Третья копия → **emitter detail**: Range Mapper Output Upper **5,000**; радиус **4** (потом **3**), variation **1** → сильно тормозящие частицы-заполнители. [▶ 27:25](https://youtu.be/6sdlTZsi9kQ?t=1645)
10. Под будущий инстансинг камней: все эмиттеры ▸ Extended Data ▸ **Use Rotation ▸ Simple Spin 1°**, вариация 1° по каждой оси (проверка через Display ▸ Boxes Filled). [▶ 30:21](https://youtu.be/6sdlTZsi9kQ?t=1821)
11. Все эмиттеры ▸ вкладка Texture: **Radius** тоже от Color channel → яркие полосы получают больший радиус, сильнее тормозят и слипаются цельнее. [▶ 31:12](https://youtu.be/6sdlTZsi9kQ?t=1872)

## Подводные камни
- Параметр, которым управляет Expresso, в эмиттере больше не редактируется (значение откатывается).
- UVW-маппинг на примитиве без UV смещает эмиссию с текстуры — используйте Spherical.
- Слишком сильный drag оставляет неподвижное «гало» частиц: уменьшите радиус на detail-эмиттере или силу nxDrag.

## Как сейчас (новые инструменты)
Те же слои есть в NeXus 2026 (**nxEmitter** + nxDrag + nxConstraints Friction; **nxConvert** переносит xpEmitter в C4D 2026.1 Beta 3). Эмиссию, зависящую от вращения, проще держать процедурной через Mapping/nxFalloff вместо Expresso. Для сыпучих слипающихся обломков альтернатива friction constraints — материал Sand в **nxMPM** (2026.1 beta).
