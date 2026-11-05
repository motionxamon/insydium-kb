# Песок, сдуваемый ветром с дюны (дюна через TerraformFX tfSpline + nxWind Von Karman, nxAvoid, nxTurbulence в ограниченной зоне)

- Источник: INSYDIUM Content Repository breakdown — Easy Desert Dunes and GPU Sand Particles — https://www.youtube.com/watch?v=0ZZRRg4WbBc (2024-03-15)
- Хост / поколение: C4D; TerraformFX + xpEmitter под управлением GPU-модификаторов NeXus (nxWind, nxAvoid, nxTurbulence) — G2; xpSplineMesher + xpCache; рендер в Cycles 4D
- Задача: дюна с острым гребнем при низком солнце, с гребня струится песок и подбрасывается на кромке.

## Террейн дюны
1. **tfTerrain** (удалите Hydraulic Erosion и tfGrid, выключите noise, скройте раскраску). Добавьте **tfSpline** над noise, подключите сплайн дюны.
2. tfSpline: **Resample off** (используются собственные промежуточные точки сплайна, иначе height field получается в точках); Radius **110**.
3. Кривые (по x — вдоль сплайна): кривые **Radius** и **Gain** опущены на обоих концах, чтобы дюна сходила на нет у краёв террейна; кривая **Falloff** опущена для чёткого гребня. Gain оператора **40 cm**.
4. Освещение tfTerrain: низкий **Pitch**, поверните **Heading**, чтобы наветренная сторона была освещена, а подветренная в тени.
5. Включите tfNoise: blend **Screen**, очень низкий gain (~0.1), Wavy Turbulence, крупнее scale, переберите seed → лёгкая рябь.
6. Продублируйте террейн дважды: **рендерная** копия с Segments **1500** → Make Editable (C) — заодно извлекается light rig; **симуляционная** копия с выключенным освещением, Segments **100** → Make Editable. Живой оригинал сгруппируйте (Alt+G) для правок.

## Частицы песка
7. **xpSystem**, низкополигональный террейн в Utilities. **xpEmitter** ▸ Object = низкополигональный террейн, эмиссия из **Texture**: материал C4D на террейне с noise **Luka**, сильный low/high clip, сплющенный Y scale (слоистые полосы), Animation Speed **0.2** (включите Animate Preview, чтобы видеть). Вкладка Texture = этот texture tag, Emit channel Color.
8. Emission: скорость 0, радиус 0.5, Birth Rate **100,000**, отображение Dots; Lifespan **150** (var 20); таймлайн 500 кадров. Вкладка Falloff: **Sphere** вокруг главной зоны.
9. **nxWind**, повёрнутый на 90°, чтобы дул по +X, режим **Von Karman** (естественные порывы), Strength **20 cm** (10 тоже подходит); турбулентные завихрения по умолчанию.
10. **nxAvoid** = низкополигональный террейн, detection distance 15; эмиттер ▸ **Origin Offset 2 cm**, чтобы частицы не рождались внутри поверхности.
11. Подброс на кромке: **nxTurbulence** тип Turbulence, Strength 10, Scale 90, Octaves **4**, Persistence **27**, Frequency **170**.
12. Своя зона: продублируйте сплайн дюны, подвиньте точки (вид Right, X-ray) вдоль гребня; **xpSplineMesher** с Caps, joins и vertex colours выключены. Бросьте его в **Fields** nxTurbulence слоем **Volume** и скройте → турбулентность только на гребне.
13. **xpCache** во внешние файлы: 500 кадров заняли ~3 мин 50 с, ~5 GB.

## Рендер (Cycles 4D)
14. Камера Cycles 4D с длинным объективом **100 mm** (вид с вертолёта). **Cycles Instance tag** на эмиттере: Segments сферы **8**, Size Multiplier **16%** (var 20%). Вместо light rig — **Cycles 4D Sky** (низкая elevation, поверните солнце). Скройте из рендера низкополигональный террейн и spline mesh; простые diffuse-материалы (песок на высокополигональном террейне, на частицах — чуть более шершавый).

## Как сейчас (новые инструменты)
В NeXus 2026.1 зону из spline mesh можно заменить режимом **Spline nxFalloff** на слое nxTurbulence, nxAvoid/коллизии — объектом **nxCollider**, кэш — **nxCache**; оседающий или насыпающийся песок сейчас делают пресетами sand в **nxMPM**.
