# Motion blur на замешенной жидкости в Redshift (xpOpenVDBMesher Transfer Velocity → motion vectors в Redshift Object tag)

- Источник: Top Tip Tuesday — Motion Blur On Volume Meshes — https://www.youtube.com/watch?v=zZxnTC2jJm0 (2025-01-21)
- Хост / поколение: C4D; NeXus G2 nxFluids (высокое поверхностное натяжение) + CPU **xpOpenVDBMesher**; Redshift
- Задача: настоящий deformation blur на volume-меше, у которого число точек меняется каждый кадр.

## Исходная сцена
Закэшированный sim nxFluids (кэш ≈3.5 мин). **xpOpenVDBMesher** ▸ General мешит этот эмиттер, лёгкое сглаживание по кривизне; материал Redshift.

## Шаги
1. Мешер ▸ вкладка **Tags** ▸ включите **Transfer Velocity** → создаются color map плюс vertex map'ы X/Y/Z со скоростью частиц. [▶ 1:50](https://youtu.be/zZxnTC2jJm0?t=110)
2. Меш ▸ **Redshift Object tag ▸ Motion Blur**: включите **Motion Vector**, перетащите карты X, Y, Z в их поля. [▶ 2:34](https://youtu.be/zZxnTC2jJm0?t=154)
3. Render Settings ▸ Redshift ▸ Advanced ▸ Motion Blur: **Motion Blur on** + **Deformation Blur on**. [▶ 2:51](https://youtu.be/zZxnTC2jJm0?t=171)
4. Рендерите в Picture Viewer (в IPR не видно). По умолчанию эффект едва заметен → в Redshift tag **Scale ~20**; 25 — разумное финальное значение. [▶ 3:31](https://youtu.be/zZxnTC2jJm0?t=211)
5. Очень большие значения (например, 60) дают пятнистые артефакты: у соседних вершин сильно различаются скорости. Лечится в мешере Tags ▸ velocity **Smoothing ~20**. [▶ 4:48](https://youtu.be/zZxnTC2jJm0?t=288)

## Подводные камни
Обычный объектный motion blur на volume-мешах не работает, потому что вершины невозможно отследить от кадра к кадру — используйте карты скорости.

## Как сейчас (новые инструменты)
GPU **nxMesher** (Fused 2025.4) напрямую выводит color/velocity/emitter ID — мешите им и подключайте его velocity в Redshift tag тем же способом.
