# Рендер лучей mtRayLine + трейлов как аддитивных градиентных кривых внутри стекла с дисплейсом (Redshift)

- Источник: Top Tip Tuesday — Redshift Rayline — https://www.youtube.com/watch?v=K560tf-sU0I (2025-06-03)
- Хост / поколение: закэшированный sim NeXus + **MeshTools mtRayLine** + xpTrail + Redshift
- Задача: светящиеся щупальца, лучи и трейлы, видимые сквозь стеклянную сферу с дисплейсом.

## Шаги
1. Элементы: частицы эмиттера (щупальца) → mtRayLine пускает лучи во внутреннюю сферу → частицы в точках контакта → xpTrail. [▶ 0:54](https://youtu.be/K560tf-sU0I?t=54)
2. Сфера для рендера = чуть увеличенная копия; стекло Standard с Maxon Noise на roughness + displacement → Redshift Object tag ▸ Geometry ▸ **Tessellation + Displacement on** (5/5). [▶ 2:48](https://youtu.be/K560tf-sU0I?t=168)
3. Redshift Object tag на лучи, трейлы, частицы: Curves ▸ **Cylinder instances** (лучи r 2; трейлы r 1 с сужением по сплайну радиуса); частицы ▸ Sphere instances. [▶ 6:48](https://youtu.be/K560tf-sU0I?t=408)
4. Материал: Emission 2; **Ramp → Geometry Opacity** (аддитивный вид); цвета ramp на значении 50 % (запас под яркие пересечения). [▶ 4:34](https://youtu.be/K560tf-sU0I?t=274)
5. Градиент вдоль каждой кривой: **Vertex Attribute ▸ preset Curves ▸ Curve Position** → вход Alt у ramp. [▶ 5:42](https://youtu.be/K560tf-sU0I?t=342)
6. Пост: Bloom threshold ~3, softness 0; Color Controls contrast 0.1. [▶ 7:58](https://youtu.be/K560tf-sU0I?t=478)
