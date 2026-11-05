# nxFoam — карточка инструмента

Встречается в **7** рецептах · 2023-06-23 → 2026-08-11 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- NeXus ▸ **Liquid Fill** → домен, nxGravity и папка с эмиттером, **nxFluids**, **nxMesher (выкл.)**, группой «foam» и **nxFoam (выкл.)**. Сразу работает как бак. [▶ 0:59](https://youtu.be/vglrHSL-uc4?t=59) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Пена: включите **nxFoam**; тип солвера должен совпадать (**APIC**); Simulation Bounds = сфера. Display эмиттера Points size 1, чтобы видеть белую воду. [▶ 19:12](https://youtu.be/vglrHSL-uc4?t=1152) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- **nxFoam** → **Add Emitter** (отображение Dots); оставляем только слой **Crest** (убираем Aerate/пузыри), снижаем crest rate, **After Age 7**, life ~70 → мелкая детализация на закешированной жидкости. [▶ 7:38](https://youtu.be/C_fXmAUTb2Q?t=458) — *[2025-10-28](../../recipes/2025-10-28_liquid-countdown-flowfield.md)*
- Выключите nxFluids, nxVorticity и nxRotate (жидкость закэширована); **nxGravity оставьте** — nxFoam нужна гравитация для плавучести/адвекции. Спрячьте эмиттеры жидкости. [▶ 27:07](https://youtu.be/_W2ivetBEPo?t=1627) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **nxFoam** + новый эмиттер для неё («emit foam»): **Crest rate 10**, **Air rate 10**; пена только от частиц жидкости возрастом от **35 кадров** (с вариацией); Life **200** (с вариацией); Advection **Drag ~100**, чтобы пена прилипала к потоку и прорисовывала завихрения. У эмиттера пены Display ▸ **Dots**. [▶ 29:47](https://youtu.be/_W2ivetBEPo?t=1787) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **nxFoam** на кэш ▸ **Add Emitter** (отображение Dots). Рождение после возраста **60 → 10**, **Crest 0**, **Aerated ~20**, **Min Impact 0 / Max Impact 10** → пена от ударов. [▶ 1:21](https://youtu.be/MRrkMcNyU-w?t=81) — *[2023-10-31](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)*

## Все рецепты (7)
- 2026-08-11 · [Preset Liquid Fill с FLIP/APIC, мешем и отдельным эмиттером пены (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2025-10-28 · [Жидкий обратный отсчёт: жидкость течёт по анимированным сплайнам цифр (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2024-11-04 · [Рендер пены с цветом по скорости как аддитивного свечения в Redshift, ACEScg в After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2023-10-31 · [Удаляем лишнюю пену за пределами контейнера произвольной формы (nxKill + инверсия Volume поля / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
- 2023-06-26 · [Обзор функций: новые модификаторы NeXus — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, режимы nxBlend, nxFoam на кэшах, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
