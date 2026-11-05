# Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)

- Источник: INSYDIUM tutorial — Sand Disintegration — https://www.youtube.com/watch?v=V4mwAf8tcLk (2025-04-30)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxFluids, nxColor, nxBlend, nxQuestion, nxWind, nxSpeed, nxKill, nxPush) + CPU-тег xpCollider, xpCache; Redshift
- Задача: песочный бюст трескается на куски вдоль движущегося фронта noise, куски осыпаются в сухую пыль и улетают из кадра.

## Исходная сцена
Бюст из Content Browser C4D, отмасштабированный до высоты ~113 cm (объём объекта определяет количество частиц), пол на Y −50, статичная камера рендера.

## Шаги
1. **xpEmitter ▸ Object** = бюст; Emission **Shot**, тип shot **Hexagonal**, скорость 0; черновой радиус **1 cm** (~62 тыс. частиц). Display ▸ цвет при рождении **чёрный**. [▶ 1:25](https://youtu.be/V4mwAf8tcLk?t=85)
2. **nxColor ▸ слой Gradient by Parameter**, градиент чёрный→белый, параметр **Field**. Вкладка Fields: **Random field** (noise Luka, scale ~1000; Remapping ▸ Contour **Curve**, поджать до ~0.2 / 0.8 для контраста) + **Linear field** в режиме **Multiply**, направление +Y, повёрнут (P ~33°, H ~85°). Ключи на Y линейного поля: 85 (F0) → −2.5 (~F39), чтобы белизна прошла сверху вниз. [▶ 10:24](https://youtu.be/V4mwAf8tcLk?t=624)
3. Blend mode слоя градиента → **Add**: став белой, частица уже не вернётся к чёрному, проходя через поле. [▶ 10:24](https://youtu.be/V4mwAf8tcLk?t=624)
4. **nxBlend**: режим Addition, только Color, radius 5, **Strength ~1000** → белое расползается по тёмным пятнам, пока всё не станет белым. [▶ 11:56](https://youtu.be/V4mwAf8tcLk?t=716)
5. **nxQuestion** (ниже nxColor): Color **Brightness > 0.5** у частицы → действие **Set Group = group 1** (сначала создайте xpGroup). [▶ 21:11](https://youtu.be/V4mwAf8tcLk?t=1271)
6. **nxWind**, **Groups Affected = group 1**, H −95°, P 55°; режим **Von Karman**, strength **625**, **Variation 190%** (>100% даёт часть отрицательных обратных порывов), частота турбулентности 40, Friction Velocity **0.13**. [▶ 14:43](https://youtu.be/V4mwAf8tcLk?t=883)
7. Пол: тег **xpCollider**, bounce 0, немного трения. [▶ 16:12](https://youtu.be/V4mwAf8tcLk?t=972)
8. **nxFluids** SPH, Fluid Type **Granular**, **Substeps 12**, Friction 100%, **Stability 5** (по умолчанию слишком высоко — весь бюст поднимается целиком), cohesion по умолчанию 10%. [▶ 18:31](https://youtu.be/V4mwAf8tcLk?t=1111)
9. **nxQuestion «Speed clamp»** — строго последним в стеке: Particle Group **< 1** (без группы = group 0) → **Set Speed 0**, чтобы трение не утягивало чёрные зёрна. [▶ 20:15](https://youtu.be/V4mwAf8tcLk?t=1215)
10. Экономия: **nxKill ▸ Outside Camera Field of View** с камерой рендера (можно добавить градусов запаса) — зёрна за кадром умирают и не тратят время на симуляцию и кэш. [▶ 22:43](https://youtu.be/V4mwAf8tcLk?t=1363)
11. Осыпание в пыль: nxFluids ▸ Mapping, три слоя **Distance** (SPH Friction, Stability, Cohesion), диапазон **5 → 100 cm**, кривая от полного значения к 0 (cohesion можно гасить чуть позже). Больший min distance (например 30 cm) — крупные куски летят дольше. [▶ 54:46](https://youtu.be/V4mwAf8tcLk?t=3286)
12. Усмирить края: **nxSpeed** после ветра, операция **Acceleration** с exponential 0 (ничего не делает) + **Clamp Max Speed 500 cm**. [▶ 33:00](https://youtu.be/V4mwAf8tcLk?t=1980)
13. Продакшн-разрешение: radius **0.225** → ~5.5 млн частиц (уменьшайте радиус маленькими шагами — количество растёт очень быстро). [▶ 33:58](https://youtu.be/V4mwAf8tcLk?t=2038)
14. Сломать hex-сетку: **отключите коллайдер**, в эмиссии **Jitter X/Y/Z = 0.225** (≤ радиуса), затем **nxPush** Particle Radius, полная сила, тысячи итераций (≈3 мин на кадр 1), чтобы убрать пересечения; потом **nxKill** box (size 100, Y −100, чтобы верх совпал с полом, убивать внутри границ) **после** push — удаляет зёрна, продавленные под пол. [▶ 36:40](https://youtu.be/V4mwAf8tcLk?t=2200)
15. Emitter ▸ **Initial State ▸ Set State**; тип эмиссии **Controlled Only**; выключите push и оба вспомогательных kill; **снова включите коллизии**. [▶ 42:17](https://youtu.be/V4mwAf8tcLk?t=2537)
16. **xpCache** с **Compress Cache on Build**: 500 F заняли ~20 мин (оценка сначала в часах, но к ~F200 большинство зёрен уже мертвы). Viewport: Dots, Level of Detail **1%**. [▶ 43:57](https://youtu.be/V4mwAf8tcLk?t=2637)
17. Доводка: **Stability 15** для более крупных кусков при 5.5 млн. Ключами уведите Variation ветра с 190% ниже 100% около F187, чтобы отставшие частицы ушли из кадра. [▶ 48:53](https://youtu.be/V4mwAf8tcLk?t=2933)
18. Slow motion: в кэше Playback **Hold** вкл., **Scale 50%** (сим с фиксированным числом частиц остаётся плавным даже на 1%). [▶ 55:43](https://youtu.be/V4mwAf8tcLk?t=3343)
19. Redshift: **Redshift Object tag ▸ Sphere instances**, шероховатый материал песка; bucket **512** (карта на 24 GB), adaptive threshold **0.02**, Random Noise Pattern вкл. (выключать только при denoise), EXR **16-bit float**; ~16 с/кадр в 720p, кадры 10–400. [▶ 29:47](https://youtu.be/V4mwAf8tcLk?t=1787)

## Подводные камни
- Порядок важен: nxColor → nxQuestion (группа) → силы → speed-clamp question последним; push перед kill.
- Если забыть снова включить коллайдер перед долгим кэшем — прогон насмарку.
- Fluid-частицы, рождённые с пересечением, разлетаются — после jitter всегда раздвигайте их.

## Как сейчас (новые инструменты)
Песок в NeXus 2026.1 **nxMPM** (материалы на эмиттер вроде Sand Dry / Sand Powder Fine, Momentum 0 для сухого зерна, Auto Sleep) заменяет SPH Granular; **nxBind** может держать бюст и отпускать по Falloff или **Color Brightness** с Chunks / Chunk Size — та же идея «рассыпающийся персонаж → nxMPM», что в тренинге 21 Oct 2026. Вместо полей C4D используйте слои nxFalloff; слой nxSpeed в 2026.1 называется Acceleration.
