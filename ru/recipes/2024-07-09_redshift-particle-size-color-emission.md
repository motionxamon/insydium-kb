# Радиус частиц управляет цветом и свечением в Redshift (Scalar User Data ▸ Change Range ▸ Ramp / Scalar Ramp)

- Источник: Top Tip Tuesday — Particle Data in Redshift — https://www.youtube.com/watch?v=EQdOJuS6uv0 (2024-07-09)
- Хост / поколение: C4D; xpEmitter + NeXus (nxGravity, nxTurbulence, nxPush, nxScale 1–15 cm); Redshift
- Задача: раскрасить сферы по радиусу через ramp и заставить светиться только самые крупные.

## Шаги
1. Emitter с **Redshift Object tag ▸ Particles: Sphere Instances**; Redshift Standard Material на emitter, откройте node editor.
2. Добавьте **Scalar User Data** (Utilities ▸ User Data); атрибут через **Presets ▸ Particles ▸ Size**. Сырой выход трудно читать.
3. Нода **Change Range**: вход = scalar data, **Old Min 1 / Old Max 15** (диапазон радиусов в симуляции) → мелкие чёрные, крупные белые.
4. Нода **Ramp**: бросьте Change Range на её миниатюру и выберите **Alt Input**; загрузите пресет градиента → Output в **Base Color**.
5. Свечение: вторая ветка в **Scalar Ramp** (Alt Input), сделайте кривую линейной и задавите чёрные, пока белыми не останутся только самые крупные частицы.
6. Standard material: **Emission weight 2**; Ctrl-клик по маленькой кнопке у Emission Color, чтобы вывести порт, подключите Scalar Ramp → светятся только крупные частицы, включаясь и выключаясь по мере изменения размера.

## Подводные камни
- Old Min/Max должны совпадать с реальным диапазоном радиусов частиц, иначе данные выглядят плоскими.
