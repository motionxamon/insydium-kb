# Дымчатая жидкость, ползущая по тору (nxFollowGeo с FOV 360° + friction, nxTurbulence, nxFluids)

- Источник: Top Tip Tuesday — NeXus FollowGeo GPU Particle Fluids — https://www.youtube.com/watch?v=dLTdpbRiG68 (2024-05-14)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxFollowGeo — новинка 2024.2, nxTurbulence, nxColor, nxFluids)
- Задача: частицы, которые никогда не покидают поверхность объекта и плещутся по ней, как жидкость.

## Шаги
1. Torus, pipe radius 25. xpEmitter: Object = тор, **Polygon Area**; Rate на 15 F, **7000/frame**, speed 0, radius 0.3. [▶ 0:31](https://youtu.be/dLTdpbRiG68?t=31)
2. **nxFollowGeo** с тором (у каждого подключённого объекта свои настройки): **Field of View 360°**, чтобы частицы всегда прилипали. [▶ 1:11](https://youtu.be/dLTdpbRiG68?t=71)
3. Добавь силу: **nxTurbulence** Voronoi, strength 20.
4. nxFollowGeo **Friction 4%** → дымчатый, тонкий поток. [▶ 1:57](https://youtu.be/dLTdpbRiG68?t=117)
5. **Offset** 10 → 5 cm; **Offset Variation** даёт глубину (показано 2 cm), 0 = самые тонкие струйки. [▶ 2:20](https://youtu.be/dLTdpbRiG68?t=140)
6. **nxColor ▸ Gradient by Parameter**, замапленный на **Speed**; подними Max, чтобы белых частиц было меньше (обратная связь вживую). [▶ 3:35](https://youtu.be/dLTdpbRiG68?t=215)
7. **nxFluids**, солвер по умолчанию, **substeps 4** → сразу получается плещущаяся поверхностная жидкость. [▶ 4:21](https://youtu.be/dLTdpbRiG68?t=261)
8. Больше **surface tension** → капли; дай немного offset variation, чтобы каплям было где сформироваться. [▶ 5:06](https://youtu.be/dLTdpbRiG68?t=306)

## Как сейчас (новые инструменты)
nxFollowGeo в Fused 2025.4 получил multi-spline и режимы Guide/Force; для более тяжёлых жидкостей используй nxFluids FLIP/APIC + nxMesher.
