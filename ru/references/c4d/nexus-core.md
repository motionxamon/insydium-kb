# NeXus (C4D) — базовые понятия, nxConstraints, nxFluids, nxExplosiaFX, nxMesher

Источник: docs.insydium.ltd/nexus/ (Fused 2025, проверено 2026-11-03). Заметки своими словами, а не копия документации.

## Что такое NeXus
- GPU-слой частиц/симуляций **внутри X-Particles** (Vulkan, движок "Theron"). Это не отдельный системный объект: вы по-прежнему работаете через **xpSystem → xpEmitter**.
- **Как включается GPU-режим:** поместите объект NeXus (любой `nx*` модификатор или солвер) **дочерним к xpEmitter / влияющим на него**. Иконка xpEmitter меняется с **синей на оранжевую** — значит, этот эмиттер теперь считается на GPU. Никакой галочки нет.
- На GPU работают только `nx*` объекты; классические `xp*` модификаторы считаются на CPU. Они могут жить в одной сцене (например, nxPush + xpFlowField), каждый на своём процессоре — но CPU-модификаторы на GPU-эмиттере тратят время на передачу данных; лучше держать на одном эмиттере только `nx`.
- Главный выигрыш: миллионы частиц, жидкости. nxPush / nxBlend гораздо быстрее, чем xpPush/xpBlend.
- Несколько GPU: устройство выбирается в **C4D Preferences → NeXus**.
- Общие вкладки у каждого nx-объекта: **Groups Affected** (кидаете объекты xpGroup; пусто = все), **Mapping** (управление любым параметром данными частиц — см. mapping), **Fields/Falloff** (ограничить зону действия; nxFalloff).

## nxConstraints (физика частица–частица, стек слоёв)
Глобальные настройки:
- **Iterations** (начните с ~3): точность; вместе с Connections ещё и делает пружины жёстче, когда Stiffness на максимуме.
- **Damping**: успокаивает расчёт, чтобы можно было поднять Iterations.
- **Add Constraint** → слои: Connections (Birth / Distance / Custom), Collisions, Forces, Viscosity, Friction, Surface Tension. Каждый слой переключается зелёный/красный — отключайте слои, чтобы изолировать поведение.
- У каждого слоя есть **Weight** (по умолчанию 100%). При нескольких слоях тому, который должен доминировать, может понадобиться >100%.

Слои:
- **Collisions** — Weight, Stiffness (низкое = мягко/упруго). Повторные отскоки лечатся добавлением слоя Friction с Connection Limit 1.
- **Connections → Birth** — пружины создаются один раз при рождении. Only Born, Connection Limit (2–12), Radius, Stiffness, Minimum Distance (чтобы не слипались), Break + Break Type: None / Relative Connected (% от длины при рождении, по умолчанию) / Relative Radius / Absolute. Показать связи: xpEmitter → Display → Enable Display Constraints. Применение: soft body, желе, разрывы (понизьте break).
- **Connections → Distance** — пружины образуются в любой момент, когда частицы оказываются в пределах Radius; Break в % от длины в момент соединения (например, 160%). Применение: тягучие сети, которые слипаются при контакте.
- **Connections → Custom** — см. заметки ниже (на основе правил).
- **Forces** — Attraction (Radius, Inner = зона без схлопывания, Falloff Flat/Linear/Quadratic/Cubic, по умолчанию Cubic) + Repulsion (свой Radius, Falloff). Connection Limit. Применение: слипание/когезия, расстояние между частицами.
- **Viscosity / Friction / Surface Tension** — см. ниже.

## nxFluids (жидкости и сыпучие среды)
Три солвера:
| Солвер | Для чего | Заметки |
|---|---|---|
| **PBD** | малые–средние, быстрые, стилизованные; хорошо дружит с nxConstraints/модификаторами | Substeps 3, итерации плотности Min 1/Max 10, Attraction 10% < Repulsion 20%, Ext Pressure 10% (когезия). Высокий Attraction без Repulsion ломает жидкость. |
| **SPH** | средние–большие реалистичные жидкости; режим **Granular** (песок/снег) | Fluid Type Liquid/Granular, Smoothing Radius 100%, Substeps 3 (для granular может понадобиться до 30), плотность Min/Max 3/7, Velocity Correction (естественный поток, медленнее), Viscosity + Viscosity Iter, Vorticity Small/Large, Surface Tension (капли), Internal Pressure 100% (объём), External Pressure 30% (когезия). Granular: Friction, Friction Iterations, Stability (скорость отрыва), Cohesion. |
| **FLIP / APIC** | большие, детальные, на сетке | Voxel Size, Domain Size, Retiming, FLIP fraction (100% энергично/шумно, ниже = спокойнее, PIC), Viscosity, Vorticity, Surface Tension, Weak Particle Repulsion (против слипания). Стенки на каждую грань: Closed/Open/Kill. Точность: Pressure/Viscosity accuracy+iterations, CFL, Min/Max substeps. APIC = больше завихрений, без FLIP fraction. |
- **Check Density** (PBD/SPH, по умолчанию выключено): удаляет новые частицы с избыточной плотностью — убирает «выстрелы» при эмиссии, но молча удаляет частицы.
- На Viscosity также влияет X-Particles Project Settings → **Subframe Steps**.
- **Несколько жидкостей:** добавьте **nxFluids tag** на каждый эмиттер (INSYDIUM Tags / Extensions) — для каждого эмиттера свои Density, Viscosity, Surface Tension, Friction, Fluid Type (например, Grains), PBD Viscosity/Ext Pressure/Vorticity. Вкладка PBD работает, только если объект nxFluids стоит в PBD. Применение: вода + песок, масло + вода.
- Меш результата — через **nxMesher**.

## nxExplosiaFX (дым и огонь на GPU)
- Вкладка Sources: меши (Emit From Surface/Volume), эмиттеры, сплайны. По каналам (Smoke, Temperature, Fuel, Pressure): Mode Set/Blend/Add/Sub, Weight by Tag/Texture/Noise; Frame Limit start/end для Fuel и Pressure (без ключей). Motion Gap Fill для быстрых источников. Velocity из Object Motion/Normal/Custom; Color из Object/Shader.
- Simulation: Domain Size, **Voxel Size** (главная ручка детализации/скорости), **Upscaling** (добавляет деталей, сохраняя форму — сильно ест VRAM, смотрите Memory Stats), Retiming; Burning (Burn Rate, Temperature/Smoke Production, Gas Expansion = взрывоопасность, Ignition Temperature); Diffusion; Dissipation; Buoyancy (отрицательная плавучесть дыма = оседающий дым).
- Solver: каналы (включите Color здесь и в Display, чтобы видеть цветной дым), точность pressure/diffusion, Advection CFL + substeps, **Adaptive Bounds** (держите ВКЛ), граничные стенки.
- Dynamics: встроенные слои Turbulence/Vorticity/Wind с mapping; подвкладка Modifiers принимает nxDirection, nxAttract и т. д.; **Particle Advection** — частицы эмиттера едут по полю скоростей дыма (отлично для искр/пыли).
- Colliders: Objects, Add Pressure (отрицательное притягивает), Velocity State.
- Display: Ray Marching (по умолчанию) или Slicing; Smoke Extinction/Tint/Albedo; Flame Blackbody. Отображение поля скоростей/трейлов сильно ест память.
- Подвох: Fuel выкл + Smoke вкл в сетапе под огонь → ничего не видно. Меш — через nxMesher (iso по smoke/temperature).

## nxMesher (частицы на GPU → полигоны)
- Layers: перетащите эмиттеры и/или nxExplosiaFX; опционально модификатор Smoothing на слой (Gaussian / Laplacian = сохраняет объём / Mean Curvature = убирает noise; Strength, Influence Range, Iterations).
- General: **Polygon Size** (разрешение), Surface Size Custom (Radius) или Source (радиус частицы × Scale), **Surface Type**: Spheres (быстрее всего, «блобы») / **Zhu-Bridson** (гладкая жидкость) / Anisotropic (вытягивание по скорости: Eccentricity, Max Speed). Tris или Quads.
- Export Tags: Color частиц → тег vertex color; Velocity → UV-тег (для motion blur/шейдинга).
- Domain: Adaptive (по умолчанию вкл) или фиксированный размер; частицы за пределами не мешатся.
- Совет: большой Polygon Size для превью, маленький для финала.
