# Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)

- Источник: Black Friday Breakdown — Crystal Spawn — https://www.youtube.com/watch?v=yqfkRKgW1Mo (2023-11-16)
- Хост / поколение: C4D; смесь G1 CPU (xpFollowSurface, xpAttractor, xpAvoid, xpTrail, xpSplineMesher, xpJoin, xpCache) + G2 NeXus (nxQuestion, nxScale); террейн TerraformFX; рендер Cycles 4D
- Задача: управляющие частицы ползут по террейну, останавливаются, натыкаясь на чужие трейлы, и оставляют за собой дорожку растущих стеклянных кристаллов, подсвеченных скрытым светящимся мешем трейлов.

## Исходная сцена — три копии одного террейна TerraformFX (удалите TF grid + hydraulic erosion, отключите gradient display и свет)
- **render**: Segments 1500 × 1500; тип noise переключён на Wavy Turbulence (подберите seed).
- **Sim High**: тот же noise, Segments 100 × 100 (быстро для расчёта частиц).
- **Sim Low**: дубликат Sim High с **Gain noise вдвое меньше (25 cm)**, опущенный так, чтобы пересекался с высоким — кристаллы сидят на высоком, трейлы на низком, что потом даёт контраст в свете.

## Шаги — управляющая симуляция
1. xpSystem; квадратный эмиттер сбоку от террейна, широкий и плоский. Emission **Shot, 30** частиц; **No Intersection radius ~16 cm**; Speed 150, Variation 60. Display Arrows filled; Extended Data ▸ Rotation **Tangential**. [▶ 5:08](https://youtu.be/yqfkRKgW1Mo?t=308)
2. Террейны-генераторы нужно обернуть в **xpJoin**, чтобы использовать их как поверхность (по одному join на каждый sim-террейн). [▶ 7:06](https://youtu.be/yqfkRKgW1Mo?t=426)
3. **xpFollowSurface** → join от Sim Low, **Pull 99%**, увеличьте Distance (с 10 cm по умолчанию высокие частицы не цепляются). [▶ 7:58](https://youtu.be/yqfkRKgW1Mo?t=478)
4. **xpAttractor** с дальней стороны (Acceleration ~50, strength пониже), чтобы протянуть поток через террейн; скройте его иконку. [▶ 35:41](https://youtu.be/yqfkRKgW1Mo?t=2141)
5. **xpTrail** на эмиттер. **xpAvoid** ▸ object = трейл, On Detection **Freeze** → частицы замирают, а не пересекают чужие пути. Переименуйте эмиттер в "control". [▶ 10:48](https://youtu.be/yqfkRKgW1Mo?t=648)
## Шаги — кристаллы
6. **nxQuestion** без вопроса, только action, переключённый на **Spawn**; **Add Emitter** создаёт "crystals"; 5 в кадр. [▶ 13:25](https://youtu.be/yqfkRKgW1Mo?t=805)
7. Эмиттер кристаллов ▸ Modifiers: исключите follow surface, attractor и avoid. Настройки nxQuestion: не наследовать значения родителя, speed 0, Spread **17 cm** (боковой разброс = ширина дорожки кристаллов). [▶ 13:56](https://youtu.be/yqfkRKgW1Mo?t=836)
8. Дублируйте xpFollowSurface → join от Sim High, **Pull 100%** (никаких кадров над поверхностью при рождении); исключите его из управляющего эмиттера. [▶ 21:55](https://youtu.be/yqfkRKgW1Mo?t=1315)
9. Остановка спавна у замерших: добавьте вопрос **Flags ▸ Frozen** → action **Break** (прерывает цикл вопросов). [▶ 18:02](https://youtu.be/yqfkRKgW1Mo?t=1082)
10. **nxScale**: задайте значение Radius 4.5; Mapping ▸ слой **Age** (0–30 F) на Radius; кривая резко вверх, перелёт и возврат = пружинистое «выскакивание». [▶ 19:40](https://youtu.be/yqfkRKgW1Mo?t=1180)
11. **xpSplineMesher** на трейл, vertex colors + joints выключены, size 1.5. **xpCache** (внешние файлы, 90 F); затем отключите управляющий эмиттер и трейл. [▶ 23:17](https://youtu.be/yqfkRKgW1Mo?t=1397)
## Шаги — лук в Cycles 4D
12. Выключите оба sim-террейна для рендера (Ctrl+Alt по «светофорам»). Point light. [▶ 25:40](https://youtu.be/yqfkRKgW1Mo?t=1540)
13. Эмиттер кристаллов ▸ Cycles **Instance tag** ▸ object = Cylinder (6 rotation segments, r 2, h 20, fillet на cap ~0.2), спрятанный под землёй. Size Multiplier 20 + большой size variation; Heading offset 360 + 100% variation, Pitch/Bank 9°. Всё настраивается на закэшированных частицах. [▶ 26:24](https://youtu.be/yqfkRKgW1Mo?t=1584)
14. Материал: Surface Extended ▸ группа **Glass Dispersion**; небольшой Roughness, IOR 2.2. Fireflies → Render Settings ▸ Integrator **Clamp Direct / Indirect 3**. [▶ 33:34](https://youtu.be/yqfkRKgW1Mo?t=2014)
15. Свет: тёплый жжёно-оранжевый point light держите низко, чтобы он только бликовал в кристаллах; дубликат с другой стороны, ниже/мягче (солируйте каждый свет, чтобы оценить вклад). Cycles camera + lock превью позволяют свободно двигать вид в редакторе. [▶ 35:47](https://youtu.be/yqfkRKgW1Mo?t=2147)
16. Spline mesher получает материал **Emission** + Cycles **Object tag** с выключенной видимостью для камеры — он освещает пол и кристаллы, оставаясь невидимым. Тоньше меш = резче свет: удалите его cache tag, включите обратно трейл, size 0.5. Тёмно-синий, приглушённый, strength ~7. [▶ 37:38](https://youtu.be/yqfkRKgW1Mo?t=2258)
17. Camera tag: небольшой aperture radius, Focus Distance пипеткой на главный кристалл. [▶ 41:31](https://youtu.be/yqfkRKgW1Mo?t=2491)

## Подводные камни
- Объекты-генераторы (TF terrain) нужно положить в xpJoin, иначе xpFollowSurface их не примет.
- От fireflies в ярком стекле избавляют именно значения clamp; света остаётся всего два.

## Как сейчас (новые инструменты)
nxFollowGeo + nxAttract + nxAvoid на GPU; **nxSpawn** (2026.1 Beta 3, Rate в кадр, свои sub-layers) вместо action Spawn в nxQuestion; nxScale с Mapping; nxTrail и nxCache в NeXus 2026. Рендер — Redshift/инстансинг C4D через nxGenerator вместо Cycles 4D.
