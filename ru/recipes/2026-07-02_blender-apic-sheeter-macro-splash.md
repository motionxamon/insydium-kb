# Макро-всплеск воды с тонкими плёнками (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)

- Источник: NeXus for Blender Official Training — Fluid Splash — https://www.youtube.com/watch?v=eeigvIYA19Q (2026-07-02)
- Хост / поколение: Blender (NeXus for Blender, G3): nxEmitter, nxCollider, nxFluids APIC (в сравнении с FLIP), nxGravity, nxTurbulence + Mapping, nxSheeter, nxMesher; Cycles
- Задача: быстрая струя бьёт в сферу и раскрывается веером сплошных плёнок с рваными краями-усиками — в духе высокоскоростной макросъёмки.

## Исходная сцена
- Эмиттер **Sphere** (радиус по умолчанию), направление **+X**, **Shot 20,000**, скорость **17 m/s**.
- UV-сфера сразу за струёй; для неё слой **nxCollider**, bounce 0, friction 0.
- **nxFluids ▸ APIC**; bounds ~**38 × 33 × 15 m**, впритык вокруг эмиттера. Размер вокселя не масштабируется вместе с bounds (по умолчанию **0.1 m**) → ставим **0.15**. Display ▸ Back Only показывает плотность сетки.
- **nxGravity** strength **4** (фейковый слоумо; по умолчанию 9.8).
- Пол — куб (растянут за пределы кадра, скрыт) как второй слой nxCollider: bounce 0, небольшое трение (~3) — с FLIP/APIC даже немного трения сильно влияет.

## Шаги
1. **nxTurbulence** Voronoi, strength **55**; Mapping ▸ **Age** → слой Voronoi ▸ Turbulence Strength, диапазон **20→50 frames**, инвертированная кривая (полная → ~0), по желанию небольшой хвост. [▶ 7:15](https://youtu.be/eeigvIYA19Q?t=435)
2. **Стенки домена**: открыть **+X, +Z, +Y и −Y**. Вылетевшие частицы перестают считаться как флюид, но сохраняют velocity, гравитацию и турбулентность — дешёвая альтернатива огромному домену. [▶ 10:31](https://youtu.be/eeigvIYA19Q?t=631)
3. **nxMesher** ▸ слой Emitter: radius **0.08**, polygon size покрупнее, surface type **Zhu-Bridson** (Spheres подходит для вязкого складывания). [▶ 12:35](https://youtu.be/eeigvIYA19Q?t=755)
4. **nxSheeter** (по умолчанию, использует уже существующий эмиттер): заполняет промежутки между расходящимися частицами флюида; Output ▸ Custom Display розовым, чтобы видеть новые частицы. Мешер подхватывает их автоматически. [▶ 14:13](https://youtu.be/eeigvIYA19Q?t=853)
5. APIC **Surface Tension 35** + Sheeter Output **Velocity Scale 1 → 0.9** (лёгкое отставание) → капли на передних кромках и усики. [▶ 16:14](https://youtu.be/eeigvIYA19Q?t=974)
6. Доводка Sheeter: **Min hole size 0, Max hole size ~6** (меньше разреженных зон, больше паутинообразных усиков); **Insert Spacing 2 → 1** (× радиус частицы, плотнее заполнение). [▶ 17:14](https://youtu.be/eeigvIYA19Q?t=1034)
7. **Velocity Alignment** (вкл, по умолчанию 60°): плёнкой заполняются только частицы, расходящиеся в пределах этого угла; меньше (40–50°) = тоньше плёнка, больше отрывающихся усиков. [▶ 19:35](https://youtu.be/eeigvIYA19Q?t=1175)
8. Выбор солвера: **APIC** сохраняет угловой момент (брызги держат свою дугу); **FLIP** сильнее обтекает объект и даёт более острые усики, ему нужно меньше surface tension; **FLIP Fraction** 66% = более гладкие капли, 95% = энергично/шумно. [▶ 21:21](https://youtu.be/eeigvIYA19Q?t=1281)
9. Рендер: area light (Normalize выкл, большой, Track To на сферу). Пол: тёмный глянцевый диэлектрик. Материал на сгенерированном дочернем меше: Principled **Transmission 1, Roughness 0, IOR 1.333**; тёмные тени убираем миксом с **Transparent BSDF**, фактор — **Light Path ▸ Is Shadow Ray** (затемните цвет transparent, чтобы вернуть немного тени). Сфера: металл со сглаженным шейдингом. [▶ 29:03](https://youtu.be/eeigvIYA19Q?t=1743)
10. Cycles GPU, мало сэмплов + GPU-денойз, фиксированный noise seed, **Fast GI approximation выкл** (иначе тёмные пятна на стекле/воде), 100 кадров в 720p ≈ 7 мин; **Lock Interface** вкл. [▶ 32:22](https://youtu.be/eeigvIYA19Q?t=1942)
11. Motion blur (по желанию — на настоящей макросъёмке его почти не видно): nxMesher ▸ **Export Tags ▸ Transfer Velocity** (здесь max 10) + Motion Blur в Cycles. [▶ 33:35](https://youtu.be/eeigvIYA19Q?t=2015)
12. По желанию: слой сглаживания мешера **Mean Curvature** на полную, силу регулировать числом итераций. [▶ 35:31](https://youtu.be/eeigvIYA19Q?t=2131)

## Подводные камни
- Дефолтные размеры флюида/мешера рассчитаны на маленькие сцены — масштабируйте radius/polygon size под домен.
- С закрытыми стенками брызги отскакивают от невидимых потолков/стен прямо в кадре.

## Как сейчас (новые инструменты)
В 2026.1 beta у FLIP/APIC появились **Wall Friction**, настройки неньютоновской жидкости и **Mixer** на уровне эмиттера; nxMesher получил сглаживание Detail Aware и адвекцию UV. В C4D (Fused 2025.4 / NeXus 2026.1) работает та же цепочка nxFluids APIC + nxMesher.
