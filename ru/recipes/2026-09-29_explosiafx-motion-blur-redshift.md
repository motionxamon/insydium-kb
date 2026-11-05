# nxExplosiaFX → OpenVDB → Redshift с векторным motion blur

- Источник: Top Tip Tuesday — ExplosiaFX MotionBlur — https://www.youtube.com/watch?v=qZyBMJaN6ak (2026-09-29)
- Хост / поколение: C4D, Fused 2025.4+ (GPU nxExplosiaFX) + Redshift
- Задача: отрендерить быстрый взрыв огня/дыма с корректным motion blur по скорости.

## Шаги
1. **Не используйте Upscaling**, если нужен motion blur на рендере: upscaling добавляет детали только в smoke и temperature, но не в velocity → blur не совпадёт. Детализацию добивайтесь **меньшим Voxel Size** (например, 3.5) — симуляция медленнее. [▶ 1:07](https://youtu.be/qZyBMJaN6ak?t=67)
2. **xpCache** (INSYDIUM ▸ Cache): **EFX Format → OpenVDB**; включите **Density, Temperature, Velocity** (velocity обязательна для blur); Fuel можно пропустить. Соберите (≈15 мин на 200 кадров в демо). [▶ 2:14](https://youtu.be/qZyBMJaN6ak?t=134)
3. Отключите nxExplosiaFX и кэш; добавьте Maxon **Volume Loader** и подключите **первый кадр VDB** — он находит density, temperature, vel_x / vel_y / vel_z. [▶ 2:56](https://youtu.be/qZyBMJaN6ak?t=176)
   - Во viewport Volume Loader выглядит намного плотнее, чем EFX — это просто другая калибровка, не обращайте внимания.
4. Материал: Redshift volume (Standard Volume) с двумя нодами Scalar Attribute → Density и Temperature. В пресете EFX атрибут дыма называется `smoke`; для Volume Loader поменяйте его на **`density`** (пресет: Volume Loader), иначе дым не отрендерится. [▶ 4:22](https://youtu.be/qZyBMJaN6ak?t=262)
5. Добавьте **Redshift Object tag** на Volume Loader → вкладка Motion Blur → Motion Vectors: **vel_x, vel_y, vel_z** (точные имена из лоадера). [▶ 6:38](https://youtu.be/qZyBMJaN6ak?t=398)
6. Render Settings ▸ Redshift ▸ Advanced: **Motion Blur вкл** + **Deformation Blur вкл**. [▶ 7:41](https://youtu.be/qZyBMJaN6ak?t=461)
7. Подстройте **Scale** на теге: 0.5 = едва заметно, 1 = естественно, 3 = утрированная скорость (теряются детали пламени). [▶ 10:20](https://youtu.be/qZyBMJaN6ak?t=620)

## Подводные камни
- Motion vectors работают только через Volume Loader, не напрямую на объекте EFX.
- С blur рендер дольше примерно на 25–40%.
- В 2026.1 beta появился автоматический Redshift-материал дыма по умолчанию, когда VDB-вывод nxExplosiaFX выставлен на render/live — проверьте его, прежде чем собирать материал вручную.
