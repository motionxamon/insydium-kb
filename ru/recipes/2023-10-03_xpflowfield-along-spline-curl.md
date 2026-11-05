# Частицы, органично текущие вдоль сплайна (слои xpFlowField Along Spline + Curl + To Spline)

- Источник: Top Tip Tuesday — xpFlowField Spline Flows — https://www.youtube.com/watch?v=zA6fTkWvwwI (2023-10-03)
- Хост / поколение: C4D; **CPU xpFlowField** (Dynamics) — в той же сцене управляет и сетапами NeXus/GPU
- Задача: своё поле скоростей, чтобы поток частиц, похожий на жидкость, шёл по спирали (или по сплайнам логотипа/текста), полностью процедурно.

## Исходная сцена
Эмиттер выровнен по началу сплайна **Helix**.

## Шаги
1. X-Particles ▸ Dynamics ▸ **xpFlowField**; растяните его границы на весь сплайн (частицы реагируют только внутри). [▶ 0:41](https://youtu.be/zA6fTkWvwwI?t=41)
2. Удалите стандартный слой **Random**. [▶ 1:10](https://youtu.be/zA6fTkWvwwI?t=70)
3. Добавьте слой **Along Spline**, spline = Helix. [▶ 1:30](https://youtu.be/zA6fTkWvwwI?t=90)
4. Частицы улетают, потому что сила flow field по умолчанию **10%** → поставьте **100%**; к тому же у новых слоёв **falloff включён** (затухает до 0 на 50 cm) → выключите falloff слоя. [▶ 2:16](https://youtu.be/zA6fTkWvwwI?t=136)
5. Уменьшите **Cell Size** — больше векторов / деталей (медленнее, но на таком количестве нормально). [▶ 2:43](https://youtu.be/zA6fTkWvwwI?t=163)
6. Добавьте слой **Curl**: в режиме смешивания **Normal** он перекрывает всё; оставьте Normal, но **снизьте силу слоя**, чтобы Along Spline тоже работал. [▶ 3:39](https://youtu.be/zA6fTkWvwwI?t=219)
7. Field mode **Direction → Velocity** (векторы теперь задают и скорость); слегка поднимите силу Curl. [▶ 4:07](https://youtu.be/zA6fTkWvwwI?t=247)
8. Добавьте слой **To Spline** (Helix), falloff выкл., strength **~3%** — мягко притягивает частицы обратно к траектории. [▶ 4:55](https://youtu.be/zA6fTkWvwwI?t=295)
9. Скройте flow field; меняйте спираль (например, start radius) — поток обновляется. [▶ 6:03](https://youtu.be/zA6fTkWvwwI?t=363)

## Подводные камни
- У новых слоёв по умолчанию включён falloff, а сила объекта — 10%; и то и другое приводит к утечкам частиц.

## Как сейчас (новые инструменты)
Fused 2024.3: слои xpFlowField можно анимировать ключами. NeXus 2026: **nxFlowField** (со слоем **Cyclic** в 2026.1); альтернативы — **nxFollowGeo** (несколько сплайнов, Guide/Force, Fused 2025.4) или **nxWarp Path** (2026.1).
