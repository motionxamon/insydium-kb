# Превью рендерного motion blur во viewport (Display emitter: Lines, длина Dependent on Speed)

- Источник: Bite-Sized — Motion Blur Display Mode — https://www.youtube.com/watch?v=s6-7bXbXSqo (2025-08-28)
- Хост / поколение: C4D; настройки отображения emitter X-Particles; motion blur Redshift
- Задача: видеть смазанный вид «варп-туннеля» прямо в процессе работы, не рендеря motion blur.

## Исходная сцена
xpEmitter стреляет в сторону камеры Redshift; форма Emitter **Circle**, **Ring only** → портал/туннель скорости света. В виде обычных квадратиков это читается как частицы, разлетающиеся наружу.

## Шаги
1. Референсный рендер: Render Settings ▸ Redshift ▸ Advanced ▸ **Motion Blur on**, дефолтный preset **Movie**; смотрите в Redshift RenderView IPR (в первом быстром режиме рендера из видео он не отображался). Для look-dev медленно.
2. Emitter ▸ **Display** ▸ отображение в редакторе **Lines** (вместо Squares).
3. Режим **Line Length** по умолчанию **Dependent on Speed** — быстрые частицы рисуют длинные линии, медленные — короткие, — ровно так, как их размажет motion blur. Отрисовывается быстро.
4. Альтернативы: **Dependent on Radius** (крупнее частица = длиннее линия) или **Fixed** длина.

## Подводные камни
Линии видны только во viewport; настоящий blur по-прежнему даёт motion blur рендерера.
