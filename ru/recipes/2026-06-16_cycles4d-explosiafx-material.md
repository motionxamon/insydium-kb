# Рендер nxExplosiaFX в Cycles 4D (Principled Volume)

- Источник: Top Tip Tuesday — Cycles4D EFX — https://www.youtube.com/watch?v=ZPLiuua0ffw (2026-06-16)
- Хост / поколение: C4D, Fused 2025.4+ (закэшированный nxExplosiaFX) + Cycles 4D (Device: OptiX)
- Задача: дым и огонь из закэшированного EFX-сима в Cycles — либо стилизованно (emission color), либо физически (blackbody).

## Дым
Principled Volume (материал Cycles 4D на объекте EFX):
`Point Density (EFX Smoke, Normalize OFF) → Color Ramp (clip wisps / thicken) → Math Multiply (thickness, e.g. 15–20) → Density`

## Огонь — вариант A: стилизованная эмиссия
`Point Density (EFX Temperature) → Map Range (From 1000…6000 → To 0…1)`
- → Math Multiply (например, ×50) → **Emission Strength**
- → Color Ramp (любой градиент: реалистичное пламя, розовый, сине-зелёный магический огонь) → **Emission Color**
- Опционально ещё один Color Ramp перед умножением, чтобы оставить пламя только в самых горячих местах.

## Огонь — вариант B: физический blackbody
- Map Range (1000…6000 → 0…1) → Multiply → **Blackbody Intensity**.
- Второй Map Range с From = To (1000…6000 → 1000…6000) → **Temperature** (реальный диапазон в Кельвинах, не нормализованный).

## Диапазоны (те же правила, что и в Redshift)
- EFX выдаёт реальные температуры; **ambient temperature 300** даёт дымку по всему домену → минимум должен быть не ниже 300, а **1000** совпадает с viewport (Flame Emit Above T).
- Настройки рендера: рендерер Cycles 4D (по умолчанию теперь Redshift), device OptiX, если доступен.
