# Самоорганизующиеся «дышащие» кластеры сфер (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)

- Источник: INSYDIUM LIVE! — September 2023 – NeXus, Taiao & X-Particles — https://www.youtube.com/watch?v=uS_zr-Jf178 (2023-09-27)
- Хост / поколение: C4D; смешанно G1 CPU (xpColor, xpQuestion/Action) + G2 NeXus (nxPush, nxConstraints); рендер Cycles 4D
- Задача: тысячи сфер на закрученном торе, которые раздуваются и сжимаются по анимированному noise и органично собираются в кластеры — без модификаторов позиции, только констрейнты.

## Исходная сцена
Тонкий **Torus** в плоскости Z + деформер C4D **Twist** на 180°, затем **Current State to Object** (без живых деформеров). xpEmitter ▸ Object = тор, эмиссия с **polygon area**; **Shot**, **10,000** частиц, **Speed 0**, **Radius 1**; Display **Circles Filled**.

## Шаги
1. **xpColor** ▸ Shader = **Noise**, тип **Blistered Turbulence**, Global Scale **500%**, Animation Speed **0.3**; поднять Brightness/Contrast, чтобы белыми остались только яркие пятна — белые частицы будут расти, тёмные останутся маленькими. [▶ 20:03](https://youtu.be/uS_zr-Jf178?t=1203)
2. **xpQuestion**: Particle ▸ Color, **Brightness = 1** → Action **Change Radius** до **10**, Weight **2** (сглаживает изменение). [▶ 21:12](https://youtu.be/uS_zr-Jf178?t=1272)
3. Через Ctrl добавить второй question в режиме **Else** → Change Radius обратно на **1**, Weight 2 → сферы растут и сжимаются вслед за движением noise. [▶ 22:09](https://youtu.be/uS_zr-Jf178?t=1329)
4. **nxPush**: режим **Particle Radius**, максимальная сила; **Mapping: Color Brightness → Strength** (белые = полный push, чёрные = ноль) → сферы разлетаются небольшими группами. [▶ 22:36](https://youtu.be/uS_zr-Jf178?t=1356)
5. Отдельные сферы уплывают → **nxConstraints ▸ Bind** layer: Connection Limit **20**, большой радиус поиска Radius **300**, Break **None**. [▶ 23:38](https://youtu.be/uS_zr-Jf178?t=1418)
6. Пружины теперь борются с push → добавить слой **Friction** (≈20 связей, радиус ~80) для демпфирования; чем дольше играет сим, тем органичнее, почти как живое существо. [▶ 24:04](https://youtu.be/uS_zr-Jf178?t=1444)
7. Cycles 4D: INSYDIUM ▸ Cycles ▸ свет **Soft Box** над сценой; на эмиттер — Cycles тег **Instance** (сфера на каждую частицу); **Object material** (Principled BSDF) на эмиттер. [▶ 25:59](https://youtu.be/uS_zr-Jf178?t=1559)
8. Перетащить эмиттер в node editor → нода **Particle Info** (цвет частиц; Cloner/Matrix так же дают ноду Matrix Info). [▶ 26:24](https://youtu.be/uS_zr-Jf178?t=1584)
9. **Mix Shader** между базовым BSDF и **Emission**, управляемым **Blackbody** на **3000 K**; маска = **Ramp** от цвета частиц с узкой яркой полосой — двигая её, выбираете, какие частицы светятся; для сильного свечения поднять силу emission. [▶ 26:49](https://youtu.be/uS_zr-Jf178?t=1609)
10. Опционально **Subsurface** (Random Walk, жёлтый, ~**0.6**), чтобы свечение читалось внутри сфер. [▶ 29:01](https://youtu.be/uS_zr-Jf178?t=1741)

## Подводные камни
- Push и Bind мешают друг другу; именно Friction заставляет их успокоиться в «живые» сгустки.

## Как сейчас (новые инструменты)
Всё на GPU: **nxColor** (слоистый, 2025.4) или режим **nxFalloff Noise** для паттерна, **nxQuestion** Change Radius (CPU questions ненадёжно управляют GPU-эмиттерами), **nxPush** + **nxConstraints** как здесь. В NeXus 2026.1 (C4D/Blender) списки Falloff на каждом слое и Mapping (один слой → много целей) позволяют одним noise управлять и радиусом, и силой push.
