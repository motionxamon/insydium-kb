# Засушливый террейн с сухим руслом и heightfield-скаттером (tfNoise Advanced, tfRiver, tfDistribute, tfFlood)

- Источник: INSYDIUM LIVE! — February 2024 – Open Beta Preview, TerraformFX — https://www.youtube.com/watch?v=Foe7aTVhbYs (2024-02-21)
- Хост / поколение: C4D; TerraformFX (open beta → Fused 2024.2: новый генератор noise, tfDistribute, Advanced Terrain Shader); шейдинг во viewport/Standard
- Задача: пустыня с дюнами, сухим руслом, разбросанными валунами, галькой, кустарником и мутными лужами — без скаттера настоящей геометрии.

## Исходная сцена
tfTerrain (по умолчанию 500×500 сегментов — держите низким на время итераций), удалите стандартные операторы erosion и grid; spline реки через террейн. В Advanced Terrain Shader удалите слой травы, base rock переключите на Surfaces ▸ **Sand**, Normalize выкл., немного Variation + Jitter.

## Шаги
1. **tfNoise** ▸ Properties ▸ режим **Advanced** (новые фрактальные noise; Maxon noises остались): **Simplex Fractal**, большой Scale, больше Gain, **Octaves ~3** для крупных гладких дюн. Noise — это объект, который можно двигать: сдвигайте его в 3D вместо перебора seed, чтобы ложбина совпала со spline реки.
2. Второй **tfNoise** (Advanced, **Cubic Fractal**): мелкий — поднять Lacunarity и Persistence, низкий Gain, включить фрактальный **Warp** → промоины, будто от воды.
3. **tfRiver** между двумя noise, режим Spline со spline реки: ровные кривые ширины/глубины, шире, глубже; уменьшите у него Strength noise (дюнам он не нужен).
4. **tfDistribute** «large rocks»: раскидывает **height-field бугры**, а не геометрию. Shape Flat / Round / Cone / Spike / Custom (любой объект, напр. логотип) — здесь Round. Count 1500 → **800**, Deform medium, поднять Elevation и Size. Слои распределения: Altitude / Slope / AO / Noise / Shader / Fields — **Altitude** с Min/Max, чтобы держать камни в нижнем русле.
5. Нажмите **Add Rock Layer**: шейдер получает **Object layer + Object mask**, связанные с distribute (источник маски: Altitude, Slope, Difference map или **Object IDs** для вариаций по камням). Выберите песчаную палитру скал.
6. tfDistribute «small rocks»: Size ~3, низкий Elevation, Count **50,000**, поднять минимум Altitude, чтобы камни взбирались на берега, плюс слой распределения **Noise** с мягкостью → естественные пятна.
7. tfDistribute «bush»: **Add Tree Layer**, Shape **Cone**, повыше, Altitude сдвинут на возвышенности; уменьшите blend слоя, чтобы немного рассыпать и в других местах; буро-зелёная палитра.
8. **tfFlood**: выравнивает самые низкие участки; поднимайте уровень, пока в русле не появятся лужи, **добавьте его слой** и выберите мутно-зелёную палитру. Слой использует flood как difference map и имитирует прозрачную преломляющую воду с «видимыми» камнями на дне.
9. Во время работы держите свет низко, чтобы читалась детализация; всё остаётся процедурным — измените размер террейна, и он перестроится.

## Подводные камни
- tfDistribute — для дальних/дрон/фоновых планов; на крупных планах инстансьте настоящие камни/деревья.

## Как сейчас (новые инструменты)
Те же инструменты актуальны (Fused 2024.2+). Более нового скаттера TerraformFX не заявлено; для настоящей инстанс-геометрии по террейну в 2026.1 beta есть nxScatter (точки на мешах → nxGenerator).
