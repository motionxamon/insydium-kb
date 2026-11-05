# Перевёрнутое кристальное «дерево» (сплайновые ветки Taiao Plant + Custom Object, анимация стеком mtInset)

- Источник: INSYDIUM LIVE! — November 2023 – X-Particles, NeXus, Taiao, MeshTools & Cycles 4 — https://www.youtube.com/watch?v=qaso-gPGBnI (2023-11-16)
- Хост / поколение: C4D; Taiao Plant + MeshTools mtInset; блики от двух источников света (в финале Cycles 4D). Часть C из 3
- Задача: тысячи гранёных анимированных кристаллов, растущих из невидимых закрученных веток.

## Шаги
1. Taiao ▸ **Plant** ▸ **Trunk**: Radius 3, Height 90. [▶ 55:48](https://youtu.be/qaso-gPGBnI?t=3348)
2. Branch layer 1: длинные, направлены вверх; модификатор **Furling** загибает вниз при **Bias 0** (по умолчанию 50% — загиб начинается с середины). [▶ 56:44](https://youtu.be/qaso-gPGBnI?t=3404)
3. Branch layer 2: снимите end branch, немного angle/length, Furling (bias оставить). [▶ 57:16](https://youtu.be/qaso-gPGBnI?t=3436)
4. Branch layer 3 (носитель кристаллов): много веток (~90), вверх, без end branch. **Distribution** ▸ кривую Position поднимите до максимума у основания, чтобы ветки шли по всей длине родителя. Если первый furling слишком сильный — ослабьте. [▶ 58:57](https://youtu.be/qaso-gPGBnI?t=3537)
5. Global: Object Type **Spline** (без полигонов веток), Organ Mode **Multi Instances** для скорости во viewport. [▶ 1:00:10](https://youtu.be/qaso-gPGBnI?t=3610)
6. Layer 3 ▸ Add Part ▸ **Custom Object** (его вкладкой Profile можно слепить простые кристаллы, но здесь — настоящая геометрия). [▶ 1:00:28](https://youtu.be/qaso-gPGBnI?t=3628)
7. Кристалл: примитив Oil Tank — height/cap segments 1, rotation 6–7, r 2, h 20. Custom Object ▸ Main ▸ перетащите его; Materials ▸ **Phong angle 0** для граней. [▶ 1:02:21](https://youtu.be/qaso-gPGBnI?t=3741)
8. Plant pitch **180°** (переворачиваем растение вместо перевёрнутой камеры). Два источника света, красный + синий, для бликов. [▶ 1:03:56](https://youtu.be/qaso-gPGBnI?t=3836)
9. **mtInset** с oil tank в качестве дочернего: ключи Amount до **100% на F90**, Offset **−0.2** (вдавливает внутренние грани). Добавьте второй mtInset в стек (100%, Offset −0.2) → анимированный многогранный кристалл. В Custom Object ссылайтесь на верхний inset вместо бака. [▶ 1:07:28](https://youtu.be/qaso-gPGBnI?t=4048)
10. Custom Object Rotation **45°** → спиральное расположение. Layer 3 ▸ Distribution **Twist** с ключами 0 → 25° за шот. [▶ 1:08:43](https://youtu.be/qaso-gPGBnI?t=4123)
11. Вкладка Growth для каждого слоя: первый branch layer Growth **99.6 → 100%** даёт тонкий рост + параллакс (маленький диапазон, потому что всё растёт из него). У twist и growth есть значения Variation. [▶ 1:11:26](https://youtu.be/qaso-gPGBnI?t=4286)
12. Проверка во viewport: GGX reflectance с Dielectric Fresnel; DOF на камере.

## Подводные камни
- Мигающие эмиссионные «внутренние проволочки» в финале сделаны в Cycles 4D миксом metallic + emission с outline-шейдером — в видео не показано.

## Как сейчас (новые инструменты)
Тот же путь через Taiao/MeshTools и сегодня. Для варианта на частицах ветвящиеся структуры на GPU растят nxDendrite или **nxBioLogic** (2026.1, coral/growth с tube-мешами).
