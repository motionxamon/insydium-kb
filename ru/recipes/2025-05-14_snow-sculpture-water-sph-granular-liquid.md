# Вода размывает снежную скульптуру (nxFluids SPH granular + liquid tag, nxGravity с маппингом по Age, xpOpenVDBMesher)

- Источник: INSYDIUM Training — Snow and Water — https://www.youtube.com/watch?v=Siw3tkJepaU (2025-05-14)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (xpEmitter'ы + GPU nxFluids SPH, nxGravity, NeXus Mapping) + **CPU xpOpenVDBMesher** и xpCache; Redshift; After Effects для motion blur
- Задача: струя воды скользит по полу, врезается в гранулярный (снег/песок) бюст, и тот рассыпается кусками; обе жидкости взаимодействуют в одном солвере.

## Исходная сцена
Пол = куб 6000 × 6000 см; бюст из Content Browser C4D, отмасштабированный до ~160 см в высоту (после привязки скрыт).
- Ctrl+D Project Settings ▸ **X-Particles ▸ Subframe steps 4** (полная гравитация на частицах меньше сантиметра плюс очень быстрая вода).

## Шаги
1. **Emitter granular**: режим Object, форма = бюст; Emission **Shot** на первом кадре, сетка **Hexagonal**, скорость 0, черновой радиус **1.2 см** (~100k частиц; проверяйте через Display ▸ HUD).
2. **nxGravity** (по умолчанию). На пол — INSYDIUM **Collider tag**: bounce 0, **friction 90%**, чтобы гранулы цеплялись.
3. **nxFluids**: **SPH**, Fluid type **Granular**, Substeps **6** (×4 субфрейма сцены ≈ 24 на кадр — достаточно, ведь скульптуре не нужно стоять самой). Granular: Friction **90**, Stability **20** на черновике (5 — сильнее крошится на черновом размере).
4. Проверка во viewport: Display эмиттера ▸ Color **Gradient Parameter** по granular-значению (~30), синий → белый.
5. Подделываем устойчивость: nxGravity ▸ **Mapping** ▸ **Age → сила гравитации**, min/max возраста — окно в 2 кадра (сначала 28–30, потом **21–23**), чтобы гравитация включалась только при ударе воды. Пока подбираете тайминг воды, отключите маппинг.
6. **Emitter liquid**: форма Box, тонкий (~17 см в высоту), Direction **−X**, за кадром, низко у пола, наклонён по bank ~25° вниз, чтобы сначала плеснуть на пол; эмиссия Hexagonal, **тот же радиус, что у гранул** (SPH требует одинаковых радиусов, иначе взрывается), скорость **800**.
7. Один солвер на оба типа: на жидкий эмиттер — **nxFluids tag** ▸ SPH ▸ Fluid type **Liquid** (сам объект nxFluids остаётся Granular).
8. nxFluids ▸ **Check Density** включить (по умолчанию новорождённая частица с плотностью выше 110% от плотности жидкости удаляется) — рождение частиц друг в друге больше не даёт выброса.
9. Раздельное трение: продублируйте пол → *floor granular* (в **Exclusions** коллайдера — жидкий эмиттер, friction 90%) и *floor liquid* (исключает гранулярный эмиттер, friction **1%**, чтобы вода скользила).
10. Раздельная гравитация: гравитация с маппингом = *gravity granular*; дубликат *gravity liquid* с удалённым маппингом. Во вкладке **Modifiers** каждого эмиттера исключите (минусом) чужую гравитацию.
11. Вариация потока: **Vibrate tag** на жидком эмиттере — Regular pulse, Rotation вкл., Heading ~5°, Frequency 1.
12. Эмиссия жидкости только кадры **0–50** (снимите Emit all frames); оставшаяся вода продолжает толкать обрушение.
13. Продакшен: оба радиуса **0.4 см** (~3M гранул, ~6M частиц жидкости к кадру 50; на 24 GB VRAM влезало ~13–14M частиц жидкости). Верните Stability гранул к **20**, чтобы куски были похожего размера. Закешируйте тест на 40 кадров (~13 мин, 12 GB), перепроверьте тайминг гравитации, затем полные 120 F (~2 ч 40 мин). Viewport: Display **Dots**, Force display, Level of detail ~21%.
14. **xpOpenVDBMesher granular**: Voxel size **0.5**, Point Radius **1.9** (дефолтные 10× дают раздутость), Filters: удалите Median, добавьте **Curvature**, iterations **2** (остальное спрячет SSS).
15. **xpOpenVDBMesher liquid** (дубликат): Voxel **0.6**, Point Radius ~**2**, Curvature **10** iterations. Если брызги пропадают — уменьшите вокселы или увеличьте Point Radius.
16. Кеш мешей: xpCache ▸ Build ▸ **Continue** (не Overwrite) — читает закешированные частицы и добавляет меши (~1 ч 20 мин); затем скройте оба эмиттера.
17. Redshift: снег = SSS **weight 1**, лёгкий голубой scatter color, **Scale 100**, Radius серым значением, чтобы приглушить; поднимите roughness для плотного снега (меньше похоже на лёд). Вода = IOR **1.33**, Transmission 1, roughness ~0.
18. Рендер 1080p, порог unified sampling **0.02**, denoising выключен + random noise pattern, Bucket size **512** (~1 ч). After Effects: adjustment layer с **Pixel Motion Blur**, Shutter Samples **20**.

## Подводные камни
- Смешивание в SPH: у всех частиц один радиус и один объект nxFluids.
- Stability зависит от размера частиц — после уменьшения радиуса подстройте её заново.
- При добавлении мешей к существующему кешу частиц никогда не жмите Overwrite.

## Как сейчас (новые инструменты)
**nxMPM** (бета 2026.1) считает снег/песок и жидкость в одной мультиматериальной GPU-симуляции (пресеты nxMaterial вроде Snow packed/sticky; Auto Sleep с Wake Speed может держать скульптуру неподвижной до удара); в Fused 2025.4 мешируйте GPU-шным **nxMesher** вместо xpOpenVDBMesher. FLIP и MPM учитывают фильтры групп коллайдеров (Beta 3) — удобно для отдельных полов под каждую жидкость.
