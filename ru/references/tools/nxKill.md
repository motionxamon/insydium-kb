# nxKill — карточка инструмента

Встречается в **12** рецептах · 2023-10-31 → 2026-10-21 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Чистка шальных частиц: **nxKill**, Volume = Object (зомби), переключите иконку inside/outside, чтобы он убивал частицы **снаружи**. После первых кадров (~кадр 52) поставьте ключ **Enabled** off, чтобы потом не убивать оторвавшиеся частицы. [▶ 4:12](https://youtu.be/-QzOnmifveY?t=252) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- Пропорции подстраивай порогами random. nxKill Outside Camera FOV держит сцену лёгкой. — *[2026-05-05](../../recipes/2026-05-05_random-groups-scale-mapping.md)*
- **nxKill → Outside Camera FOV** (подключите камеру) → огромная экономия. [▶ 5:49](https://youtu.be/LPu79OH-yC0?t=349) — *[2026-01-27](../../recipes/2026-01-27_gpu-particle-advection-running-character.md)*
- Анимированный эмиттер, распыляющий на коллайдер-трубу; **nxGravity 400**; **nxFluids SPH** substeps 6 (взаимодействие частица–частица); границы **nxKill**. [▶ 0:27](https://youtu.be/_7bYCGydqXo?t=27) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- **nxKill ▸ Object**: убивать вне объёма «fluid kill» → вылетевшие частицы больше не тратят время. [▶ 3:50](https://youtu.be/q8Crdpa1XUw?t=230) — *[2025-07-08](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)*
- **nxKill** с боксом: **Volume ▸ Inside bounds** у аттрактора, чтобы частицы гибли по прибытии. Kill и аттрактор скройте. [▶ 2:07](https://youtu.be/K2Jb2lxzgSY?t=127) — *[2025-05-08](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)*
- **nxPush**: Distance = **Particle Radius**, Strength 100, **Iterations 1000**. Под ним **nxKill**, Volume = Objects ▸ куб пола, Inside → убивает зёрна, вдавленные в пол. [▶ 24:39](https://youtu.be/fxJI8py9BzU?t=1479) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- Экономия: **nxKill ▸ Outside Camera Field of View** с камерой рендера (можно добавить градусов запаса) — зёрна за кадром умирают и не тратят время на симуляцию и кэш. [▶ 22:43](https://youtu.be/V4mwAf8tcLk?t=1363) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Сломать hex-сетку: **отключите коллайдер**, в эмиссии **Jitter X/Y/Z = 0.225** (≤ радиуса), затем **nxPush** Particle Radius, полная сила, тысячи итераций (≈3 мин на кадр 1), чтобы убрать пересечения; потом **nxKill** box (size 100, Y −100, чтобы верх совпал с полом, убивать внутри границ) **после** push — удаляет зёрна, продавленные под пол. [▶ 36:40](https://youtu.be/V4mwAf8tcLk?t=2200) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxKill**: Volume **Object** = контейнер, убивать **снаружи**, **Only Born** → удаляет частицы, родившиеся вне цилиндра. [▶ 6:25](https://youtu.be/_W2ivetBEPo?t=385) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Способ A — **nxKill**: Volume **Outside Bounds**, Radius **0** (убивает всё), затем Fields ▸ перетащите коллайдер, режим слоя **Points → Volume**, Remapping ▸ **Invert** → гибнут только частицы снаружи капсулы. [▶ 3:52](https://youtu.be/MRrkMcNyU-w?t=232) — *[2023-10-31](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)*

## Все рецепты (12)
- 2026-10-21 · [Идущий персонаж рассыпается в песок (nxBind + отрыв по фоллоффу + nxMPM brittle)](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)
- 2026-05-05 · [Немного крупных, много мелких: случайные подгруппы + nxScale с маппингом по группе](../../recipes/2026-05-05_random-groups-scale-mapping.md)
- 2026-01-27 · [Дымчатый шлейф частиц за бегущим mocap-персонажем (EFX advection)](../../recipes/2026-01-27_gpu-particle-advection-running-character.md)
- 2025-09-16 · [Тянущиеся и рвущиеся волокна (nxConstraints Birth + трейлы по констрейнтам + xpTrailDeformer)](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)
- 2025-07-08 · [Бесконечная река / поток жидкости (открытый с одной стороны контейнер + эмиттер подпитки + nxKill)](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)
- 2025-05-08 · [Лента частиц, обёрнутая вокруг сплайна деформерами C4D (Spline Wrap + Twist на xpEmitter)](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-04-02 · [Вода, собирающаяся в капли (поверхностное натяжение nxFluids SPH + nxGravity по возрасту)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2023-12-26 · [Естественный падающий снег (ограничение nxSpeed, замапленное на радиус + второй nxTurbulence Curl с Blend, замапленным на радиус)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-10-31 · [Удаляем лишнюю пену за пределами контейнера произвольной формы (nxKill + инверсия Volume поля / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
