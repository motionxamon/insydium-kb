# Показать меш только там, где сквозь него проходит дым (Point Density в Cycles 4D на меше, эмиттеры xpExplosiaFX со сдвигом)

- Источник: Maintenance Training — XP Countdown - Series 2 - Cycles 4D Point Density — https://www.youtube.com/watch?v=XNLOKgKCuvU (2023-03-29)
- Хост / поколение: C4D; CPU xpExplosiaFX + xpFlowField + xpCache; Cycles 4D (volume-нода Point Density)
- Задача: «1» проявляется как дым, заполняющий её объём, ~2 с (F120–180) — дым снаружи буквы невидим.

## Исходная сцена
Скопировать xpSystem EFX (и сплайны flow field в ту же папку) из сцены с advection в новый файл; удалить старые теги cache, переименовать domain/эмиттер в «smoke fill». Превью на **Voxel 4 см / радиус частиц 8**; продакшн — **2 см / 5 см**.

## Шаги
1. Быстрый тестовый свет в Cycles 4D: плоскость над сценой с материалом **Surface ▸ Emission**, strength **6**; открыть real-time preview. [▶ 4:48](https://youtu.be/XNLOKgKCuvU?t=288)
2. Create ▸ Volume preset **ExplosiaFX Smoke Basic** — назначить на **меш «1»**, а не на domain EFX. [▶ 5:53](https://youtu.be/XNLOKgKCuvU?t=353)
3. В нодах (для наглядности убрать color ramps): нода **Point Density** ▸ Object = domain EFX, пространство **World** → плотность читается из симуляции, но рисуется только внутри объёма меша. [▶ 7:13](https://youtu.be/XNLOKgKCuvU?t=433)
4. Усилить плотность через **Math ▸ Multiply** примерно до 50, чтобы заполнение читалось. [▶ 8:01](https://youtu.be/XNLOKgKCuvU?t=481)
5. Дыма на 60 кадров: продублировать эмиттер источника EFX (Ctrl-drag) и сдвинуть ключи анимации falloff эмиссии → 4, затем **5** волн со сдвигом. [▶ 11:36](https://youtu.be/XNLOKgKCuvU?t=696)
6. Последним двум эмиттерам Birth Rate **3000**/с — реальное количество намного меньше, потому что включена эмиссия без пересечений. [▶ 17:36](https://youtu.be/XNLOKgKCuvU?t=1056)
7. Проверять пересечения на продакшн-разрешении по кадрам (F140–180) в real-time preview. [▶ 18:34](https://youtu.be/XNLOKgKCuvU?t=1114)
8. **xpCache** во внешние файлы, режим **Include** — в списке только domain EFX; все 300 F ≈ 8 мин, ~8 GB в демо. Потом выключить эмиттеры и обрезать таймлайн до 220 F. [▶ 22:05](https://youtu.be/XNLOKgKCuvU?t=1325)

## Подводные камни
- Без пространства World выборка Point Density смещена и видны только случайные клочки.
- Проявление — это трюк рендера: видимый «внешний» дым рендерится отдельно (синий), а заполнение внутри получает свой цвет (зелёный) в композе.

## Как сейчас (новые инструменты)
Дым считать на GPU в **nxExplosiaFX** (Fused 2025.4), а такую же выборку плотности внутри меша делать в volume-шейдере текущего рендера; к тому же nxExplosiaFX даёт дефолтный Redshift-материал дыма для своего VDB (2026.1 beta).
