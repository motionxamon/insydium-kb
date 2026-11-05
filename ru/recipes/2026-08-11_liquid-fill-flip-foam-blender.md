# Preset Liquid Fill с FLIP/APIC, мешем и отдельным эмиттером пены (NeXus Liquid Fill, nxFoam, nxMesher)

- Источник: Top Tip Tuesday — Liquid Fill — https://www.youtube.com/watch?v=vglrHSL-uc4 (2026-08-11)
- Хост / поколение: Blender (NeXus for Blender 2026.0) — preset Liquid Fill: nxEmitter (Liquid Fill), nxFluids FLIP/APIC, nxMesher, nxFoam, nxCollider, nxWind
- Задача: быстро собранная жидкость в баке / заполненном объекте с поверхностной пеной, готовая к рендеру.

## Шаги
1. NeXus ▸ **Liquid Fill** → домен, nxGravity и папка с эмиттером, **nxFluids**, **nxMesher (выкл.)**, группой «foam» и **nxFoam (выкл.)**. Сразу работает как бак. [▶ 0:59](https://youtu.be/vglrHSL-uc4?t=59)
2. Движение по желанию: **nxWind** ▸ **Von Karman**, strength ~2.5, побольше вариативности, поднимите Turbulence ▸ Friction Velocity. [▶ 1:36](https://youtu.be/vglrHSL-uc4?t=96)
3. Эмиттер: Object = домен, Volume, Emission Type **Liquid Fill**, ссылается на солвер nxFluids; **Resolution** (50 → 70/75) и **Fill Level** (30%, Show Fill Level). Resolution задаёт размер вокселя солвера **и** количество частиц, чтобы число частиц на воксель оставалось правильным (при неверном соотношении жидкость схлопывается). Проверяйте через nxFluids Display ▸ voxel grid Back Only. [▶ 4:31](https://youtu.be/vglrHSL-uc4?t=271)
4. Тип солвера связан: переключение эмиттера на **APIC** переводит в APIC и nxFluids. [▶ 7:19](https://youtu.be/vglrHSL-uc4?t=439)
5. Заполнить другую форму: замените объект эмиттера на UV sphere; добавьте на неё **nxCollider** с **Inside normals**, Bounce 0, Friction 0, чтобы удерживать жидкость внутри. [▶ 7:02](https://youtu.be/vglrHSL-uc4?t=422)
6. Меш: включите **nxMesher** (уже связан; авто polygon size ~0.027); поднимите Scale до **300**, чтобы закрыть дыры; слой Smoothing **Mean Curvature**, iterations **5** (при 10 теряются капли). Export ▸ **Transfer Velocity** для motion blur. [▶ 18:41](https://youtu.be/vglrHSL-uc4?t=1121)
7. Пена: включите **nxFoam**; тип солвера должен совпадать (**APIC**); Simulation Bounds = сфера. Display эмиттера Points size 1, чтобы видеть белую воду. [▶ 19:12](https://youtu.be/vglrHSL-uc4?t=1152)
8. Оставьте только слой **Surface Foam**; **Spawn After Age** по умолчанию **30** кадров → **4**, чтобы пена появлялась раньше. [▶ 13:44](https://youtu.be/vglrHSL-uc4?t=824)
9. Отдельная пена: вместо Output Group «foam» создайте второй эмиттер «foam», поставьте Birth Rate **0** и укажите его в **Output Emitter** слоя пены (можно по эмиттеру на каждый тип белой воды). [▶ 15:59](https://youtu.be/vglrHSL-uc4?t=959)
10. Рендер: эмиттер пены ▸ Export ▸ **Create Point Cloud** (motion blur работает автоматически); жидкость = mesher. [▶ 17:56](https://youtu.be/vglrHSL-uc4?t=1076)

## Как сейчас (новые инструменты)
В бете 2026.1 добавлены неньютоновский FLIP, Wall Friction, Mixer, у nxMesher — **Blend into Ocean**, и связка FLIP с **nxOcean**.
