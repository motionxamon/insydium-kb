# Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)

- Источник: Maintenance Training — XP Countdown - Series 3 - Combining Scenes Part 1 — https://www.youtube.com/watch?v=j453vKa_ay4 (2023-03-29)
- Хост / поколение: C4D; CPU X-Particles (xpCache, xpOpenVDBMesher, xpExplosiaFX, ткань xpClothFX, xpShatter) + Alembic + MoGraph PolyFX/Plane effector
- Задача: собрать шоты обратного отсчёта «6 splash → 5 fill → 5 burn → появление 4» из отдельных закэшированных сцен и выстроить их тайминг.

## Исходная сцена
Все подсцены уже закэшированы (xpCache) и названы по шотам; splash запечён в Alembic (пакет с SDS + xpOpenVDBMesher в Boole). Новый мастер-файл сохранён в отдельной папке «render builds» с версиями в имени; на каждый шот — свой организационный null (6 splash, 5 fill, 5 burn, 4 crumble).

## Шаги
1. **Копирование между файлами**: на каждом **xpCache tag** включить **Copy Tag Data / Copy Cache Data**, затем Ctrl+C нужные объекты (mesher, cache object, эмиттеры; эмиттеры, результат которых уже смешен/закэширован, не нужны) и вставить в мастер. [▶ 4:08](https://youtu.be/j453vKa_ay4?t=248)
2. Splash слишком медленный → Alembic object ▸ Object ▸ **Speed 180%**. Добавить **Display tag ▸ Lines**, чтобы видеть сквозь него. [▶ 5:40](https://youtu.be/j453vKa_ay4?t=340)
3. На время подгонки тайминга выключить mesher (частицы проигрываются быстрее), потом включить обратно. [▶ 7:05](https://youtu.be/j453vKa_ay4?t=425)
4. Сдвиг закэшированного шота: **xpCache ▸ Object ▸ Playback ▸ Hold**, затем **Offset** (fill: +20 кадров, чтобы старт был около F30, а не F10). [▶ 7:37](https://youtu.be/j453vKa_ay4?t=457)
5. xpOpenVDBMesher во viewport может «залипнуть» на первом кадре → ключи на **Basic ▸ Visible in Editor/Renderer**: off на F29, on на F30. [▶ 24:53](https://youtu.be/j453vKa_ay4?t=1493)
6. Шот burn (xpExplosiaFX + ткань + PolyFX + Plane effector): тот же Hold/Offset; пробовали −58 → −53 → итог **−50**. Ключами выключить **Enabled** у Alembic и включить видимость null ткани на кадре передачи; при каждом изменении offset сдвигать эти ключи в **Dope Sheet**. [▶ 26:02](https://youtu.be/j453vKa_ay4?t=1562)
7. Тайминг оценивать через **Hardware (OpenGL) render** в Picture Viewer, 0–100 F при 30 fps — проигрыванию во viewport верить нельзя. [▶ 18:34](https://youtu.be/j453vKa_ay4?t=1114)
8. Цифра 4 (xpShatter): для сравнения снять **Display ▸ Draw Cut Edges**; удалить cache tag только у 4, задать **Offset 0.3 cm** — зазор между осколками (тени в швах в духе AO + видно внутренний цвет), затем xpCache **Build Cache ▸ Continue**, чтобы перекэшировать только недостающий объект. С тройкой так НЕ делать. [▶ 20:40](https://youtu.be/j453vKa_ay4?t=1240)
9. В мастере у кэша четвёрки **Playback ▸ Manual Time** (держит кадр 0, цифра статична); видимость null включается ключом, когда ткань рвётся. [▶ 24:08](https://youtu.be/j453vKa_ay4?t=1448)
10. Растворение ткани: Plane effector (масштаб) управляет PolyFX; falloff = **Linear field** + **Random field** в режиме **Overlay**, так что noise работает только внутри градиента линейного поля. Сузить градиент, анимировать позицию linear field ключами снизу вверх через ткань. [▶ 27:30](https://youtu.be/j453vKa_ay4?t=1650)
11. xpExplosiaFX ▸ Display **Fuel and Smoke**; в **Timeline F-Curve** потянуть Bezier-ручки на Y-ключах поля, чтобы куски исчезали только под огнём. [▶ 29:34](https://youtu.be/j453vKa_ay4?t=1774)

## Подводные камни
- Слияние даётся легко только благодаря аккуратным папкам, именам и кэшам; остальные шоты рендерятся по отдельности и собираются в композе.

## Как сейчас (новые инструменты)
G2/G3: **nxExplosiaFX** (Fused 2025.4) для горения, **nxMesher** вместо xpOpenVDBMesher, **nxShatter** (2026.1 beta) для четвёрки; у **nxCache** есть frame range. Форма растворения: 16 режимов **nxFalloff** + **nxFalloff Modifier** (Remap, Step, Curve, Delay, Grow) вместо стопки полей C4D.
