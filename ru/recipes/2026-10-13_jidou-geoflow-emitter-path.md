# Процедурная анимация emitter по пути с jdGeoFlow

- Источник: Top Tip Tuesday — Jidou Emitter Control — https://www.youtube.com/watch?v=CaiS-kcvPKs (2026-10-13)
- Хост / поколение: C4D, Fused 2025.4.1+ (Jidou; режимы воспроизведения с 2025.4.1) + emitter NeXus (setup с nxPush)
- Задача: двигать emitter частиц по кругу/сплайну логотипа с Ease, циклами и noise — замена тегу Align to Spline из C4D без keyframe.

## Дерево сцены
```
jdGeoFlow (INSYDIUM ▸ Jidou)   Objects: xpEmitter   Mode: Path
  Path tab: Shape Circle (default) or Custom → flower/logo spline
xpEmitter (orange, nxPush setup — particles limited in Y)
```

## Шаги
1. Удалите тег Align to Spline, если он есть. Добавьте **jdGeoFlow**, перетащите emitter в его объекты, поставьте **Mode: Path** (не Connected Points). [▶ 1:56](https://youtu.be/CaiS-kcvPKs?t=116)
2. Вкладка Path: дефолтный **Circle** работает сразу; переключите на **Custom** и привяжите любой spline (логотип, цветок). [▶ 5:49](https://youtu.be/CaiS-kcvPKs?t=349)
3. Тайминг на вкладке Main: **Auto Time** = один проход на весь таймлайн. Выключите и задайте **End** (например, 200 кадров на оборот). [▶ 2:41](https://youtu.be/CaiS-kcvPKs?t=161)
4. **Easing curve** задаёт скорость вдоль пути (медленный старт → быстро и т. д.); linear = постоянная скорость. [▶ 3:24](https://youtu.be/CaiS-kcvPKs?t=204)
5. **Режимы цикла:** Stop (по умолчанию), **Ping-Pong**, Loop, **Continue** (продолжает лететь в последнем направлении — уходит из кадра). Циклы укладываются *в пределах* end time → если ставите 2 цикла, удвойте end time (400), чтобы скорость осталась прежней. [▶ 5:24](https://youtu.be/CaiS-kcvPKs?t=324)
6. **Вкладка Motion** → включите noise motion: амплитуда по осям (здесь X/Z 25 cm, Y 0, потому что частицы зажаты в плоскости) → органичное покачивание поверх анимации по пути. [▶ 6:45](https://youtu.be/CaiS-kcvPKs?t=405)
7. Birthrate emitter ~500 для финального вида.

## Примечания
- Работает с любым объектом, не только с emitter (для камер есть отдельный инструмент jdFlowCam).
- Комбинируйте с трейлами от nxPush/nxTurbulence, чтобы «рисовать» логотипы частицами.
