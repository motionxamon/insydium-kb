# Копоть на стенах от дыма nxExplosiaFX (xpVertexMap + Redshift)

- Источник: Top Tip Tuesday — Soot Damage — https://www.youtube.com/watch?v=kGTKDlTTyxE (2026-04-07)
- Хост / поколение: C4D, nxExplosiaFX + **xpVertexMap** (CPU-утилита) + Redshift
- Задача: после того как дым рассеется, стена, которой он касался, остаётся закопчённой.

## Шаги
1. Стена (куб) — **collider** для nxExplosiaFX, чтобы дым поднимался по ней. [▶ 0:24](https://youtu.be/kGTKDlTTyxE?t=24)
2. **xpVertexMap** (X-Particles ▸ Utilities), Object = стена → появляется тег vertex map. [▶ 1:41](https://youtu.be/kGTKDlTTyxE?t=101)
3. В дефолтном слое Polygon смените **Layer Mode → ExplosiaFX**, подключите объект EFX, Channel **Smoke**, диапазон 0–10. (С Blend Normal карта просто повторяет текущий дым и гаснет.) [▶ 2:15](https://youtu.be/kGTKDlTTyxE?t=135)
4. Накопление: слой **Blend → Screen** (или Add) и уменьшите **Strength** (~8–23%, остановились на 14%), чтобы копоть набиралась постепенно и не закрывала всё. [▶ 3:22](https://youtu.be/kGTKDlTTyxE?t=202)
5. Материал: финальная нода Standard существующего кирпичного материала → base в **Material Blender**; дубликат Standard в роли копоти (чёрный, roughness на максимум) → Layer 1. Нода **Vertex Attribute** (перетащите карту) → **Ramp** (прижмите белый узел по вкусу) → Blend Color. [▶ 6:30](https://youtu.be/kGTKDlTTyxE?t=390)

## Как сейчас (новые инструменты)
NeXus 2026.1: nxFalloff **Wet** / слои с памятью (Grow, Decay) и nxFalloffMap позволяют строить накапливающиеся GPU vertex map; взвешивание источника EFX по vertex map показано в рецепте «NeXus Falloffs».
