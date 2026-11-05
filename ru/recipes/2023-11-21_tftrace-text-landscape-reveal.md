# Логотип/текст из ландшафта, который вырастает в кадре (tfTrace + tfBlur + эрозия Snow + маскированный noise + tfAdjustment с linear field)

- Источник: Top Tip Tuesday — tfTrace Text Morph — https://www.youtube.com/watch?v=jQlOjJUVaoI (2023-11-21)
- Хост / поколение: C4D; **TerraformFX** (операторы tfTerrain) + xpJoin
- Задача: текст, который поднимается из реалистичного эродированного рельефа и анимированно проявляется, полностью процедурно.

## Исходная сцена
Объект **Text** с жирным шрифтом, Pitch **−90°** (лежит плашмя), в начале координат, Depth **−20**, чтобы экструзия шла вверх; поместите его внутрь **xpJoin** (X-Particles ▸ Utilities).

## Шаги
1. **tfTerrain**: отображение Object выключить, удалить операторы по умолчанию. Size **X 600 / Z 300**, сегменты **1000 × 500**. Спрячьте текст. [▶ 1:19](https://youtu.be/jQlOjJUVaoI?t=79)
2. **tfTrace** (высота по объектам через трассировку лучей): object = xpJoin. [▶ 1:40](https://youtu.be/jQlOjJUVaoI?t=100)
3. Гранёные крутые края → фильтр **tfBlur**, **Gaussian High Quality**, радиус побольше. [▶ 2:11](https://youtu.be/jQlOjJUVaoI?t=131)
4. Свет: опустите pitch солнца, поверните heading для света под конец дня. [▶ 2:24](https://youtu.be/jQlOjJUVaoI?t=144)
5. Сглаживаем основание: **tfErosion** в режиме **Thermal → Snow**, малый радиус (по умолчанию 15), больше итераций. [▶ 2:52](https://youtu.be/jQlOjJUVaoI?t=172)
6. Детализация: **tfNoise** Turbulence, octaves **5 → 12**, gain **~25**. [▶ 3:18](https://youtu.be/jQlOjJUVaoI?t=198)
7. Маскируем noise по буквам: tfNoise ▸ Masking ▸ Shader = **Terrain Operator Shader** (INSYDIUM ▸ TerraformFX), Split/Use Gradient выключить, operator = эрозия Snow (на её вкладке Preview видны данные высоты). [▶ 3:49](https://youtu.be/jQlOjJUVaoI?t=229)
8. **tfErosion** в режиме **Hydraulic 2D** (быстрый) для деталей стока. [▶ 4:44](https://youtu.be/jQlOjJUVaoI?t=284)
9. Анимация появления: **tfAdjustment**, Gain **0**, Masking ▸ **Linear field** — двигайте поле, чтобы проявлять/прятать текст. Ставится под гидравлической эрозией, чтобы при скрабе эрозия не пересчитывалась. [▶ 5:09](https://youtu.be/jQlOjJUVaoI?t=309)
10. Глобальный **tfNoise**, **Wavy Turbulence**, octaves 12, gain **~20**. [▶ 5:36](https://youtu.be/jQlOjJUVaoI?t=336)
11. Строку текста можно менять в любой момент (эрозия пересчитается). [▶ 5:51](https://youtu.be/jQlOjJUVaoI?t=351)

## Как сейчас (новые инструменты)
В TerraformFX 2024.2 появился **Advanced Terrain Shader** (с каналом кривизны) для текстурирования такого рельефа.
