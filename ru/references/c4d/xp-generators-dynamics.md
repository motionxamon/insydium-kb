# X-Particles — генераторы, динамика, теги (CPU)

Источник: docs.insydium.ltd/x-particles/{generators,dynamics,tags}/* (Fused 2025, проверено 2026-11-03). Пересказ своими словами.

## Генераторы (превращают частицы в то, что рендерится)
- **xpGenerator** — инстансит дочерние объекты на частицы. Сначала привяжите emitter. Clone Type **Duplicate** (по умолчанию) / Instances / **Render Instances** / Multi Instances (для 10k+ берите RI/MI). Несколько дочерних объектов: Sequentially / Randomly / by Index / Gradient. Rotate Using Particle Rotation (на emitter нужен **Use Rotation**!). Scale Using Particle Radius (по умолчанию) / Scale / Source / Set. Для тяжёлых сцен — Draw Mode Particles Only. Если Geometry стоит на Render Only — исключайте из cache.
- **xpSprite** — лёгкие примитивы (куб, крест, плашка, сфера, цилиндр, капсула, конус, пирамида, диск, 3 плоскости), Light (добавляет Lens Effects), Points, **Text**, Rubble. Scale по умолчанию 1 → подгоняйте размер. Управляется через xpSpriteControl / xpLight / xpText.
- **xpTrail** — сплайны по траекториям частиц (или объектов). Length Mode Time, Trail Length в кадрах, Freeze When Complete. **Algorithm:** No Connections (классические шлейфы), Straight Sequence, Nearest by Index / **by Distance** (plexus), Cluster, Tendrils, Constraints, Infectio. **Draw Splines** должен быть включён. Рендер через X-Particles Material, C4D Hair, Sweep или xpSplineMesher. Важно, внутри системы объект или снаружи.
- **xpSplineMesher** — рендерящиеся трубки из xpTrail/сплайнов, сливает сегменты xpBranch; Growth 100%, Plane Up Free; для скорости — Render Only.
- **xpOpenVDBMesher** — воксельный мешер: режимы **Mesh / Spheres / ExplosiaFX / Fog / Voxels**; Voxel Size, Point Radius, стек Filters (Median включён по умолчанию; Gaussian и т. д. — порядок важен), CSG с объектами, Transfer Velocity (шлейфы/motion blur), Transfer Foam (из xpFoam), смешивание Object ID/цвета. CPU-аналог nxMesher.
- **xpPlanarMesher** — треугольники между соседними частицами (для plexus-поверхностей совпадайте дистанцией с xpTrail Nearest by Distance).
- **xpShatter** — разрушение мешей: режимы Volume (цельный объём) или Surface (оболочка); **рекурсивные слои** (каждый слой дробит осколки предыдущего) с генераторами точек (bounding box, surface, point container, shader, radial); триггеры Always / Time / Speed / **Collision** (с xpBullet: Rigid Body tag на shatter + Collider tag на препятствиях) / Volume; Explode, Offset (зазоры). Collision Speed по умолчанию 0.
- **xpFragmenter** — разбивает полигоны источника emitter на разлетающиеся грани (Faces Objects / Faces Polys) или двигает объекты вместе с частицами. Emitter должен эмитить из Polygon Center.
- **xpElektrix** — молнии: To Object / Spherical / To Particles / Particle to Particle; Divisions, ответвления, Bend, Displacement. Работает без emitter.
- **xpScatter** — раскидывает дочерние объекты по поверхности по текстуре, освещённости, топологии (высота/уклон/кривизна), spacing Kill/Push.
- **xpOcean** — меш или деформер океана по Тессендорфу: Wind Speed/Direction/Alignment, Smallest Wave, Choppiness, vertex map **Foam Map**; Ocean Size больше объекта, чтобы не было тайлинга.
- **xpCellAuto** — рост клеточными автоматами: Diffusion Limited Aggregation (рост кораллов/кристаллов), Elementary (Rule No.), Game of Life. Привязанный emitter жёстко в режиме Controlled Only.
- **xpDisplayRender** — делает рендерящимися отображение частиц во viewport / векторы полей / границы коллайдеров (техничный HUD-лук).

## Динамика
- **xpExplosiaFX (CPU дым/огонь)** — объектам нужен **xpExplosiaFX Source tag** (Fuel 0 = не горит; Heat, Smoke, Pressure, Velocity, Color From; emitter-ам нужны Temperature + топливо; клонеры — под Join; плотные меши для сэмплинга текстур), и они должны быть внутри бокса солвера. Voxel Size, **Upres** (черновик в низком разрешении → upres сохраняет лук), Burning Chemical/Custom, Dissipation, встроенный ветер по +Z, вкладка Modifiers (например, xpFlowField), адаптивные границы. Cache в OpenVDB через xpCache. Ради скорости лучше **nxExplosiaFX** на GPU.
- **xpFluidFX** — CPU SPH (средние–крупные объёмы). Accuracy Fast/Custom; Mode **Velocity** (по умолчанию, конфликтует с другими модификаторами) или Position (уживается с ними, медленнее, вязче); Velocity Correction; Check Density. Свойства жидкости — в emitter: Extended Data → Fluid.
- **xpFluidPBD** — CPU PBD-жидкость; Damping 1%; Treat Collision As None; Check Density; если взрывается — снизьте Strength.
- **xpFluidFLIP** — сеточная CPU-жидкость; Type **APIC** (по умолчанию) или FLIP (спокойнее); **voxel ≈ 3–4× радиуса частицы**; Sticky Objects включить; стенки; если нестабильно → снизьте CFL, поднимите substeps, Solid Objects.
- **xpFoam** — пена/брызги из (закэшированных) жидкостей: Crest, Air, Speed, Life, Radius; Surface ≈50%; After Age.
- **xpSheeter** — заполняет дыры в тонких плёнках жидкости.
- **xpSplash / xpWave** — CPU-версии nxSplash/nxWave.
- **xpConstraints** — тот же набор слоёв, что и в nxConstraints (связи по рождению/дистанции/кастомные, коллизии, силы, вязкость, трение, поверхностное натяжение). Для жёсткости → поднимите iterations/subframes в Project Settings. Display Constraints — на emitter.
- **xpPPCollisions** — столкновения частиц между собой; Spawn / Kill / **Connect on Collision**; отдельный emitter для спавна.
- **xpFlock** — CPU-стаи (Velocity перебивает турбулентность; Force смешивает).
- **xpFlowField** — сетка векторов скорости из слоёв random/shader/object/splines/polygons/turbulence/curl; Cell Size, Strength, влияет на Direction/Velocity/Acceleration; Animate Flow медленный. Работает и как модификатор внутри xpExplosiaFX.
- **xpClothFX** — **Create Cloth** (меню Dynamics) собирает: объект ткани + xpEmitter (из точек, по одной на вершину, Shot, скорость 0) + **xpClothDeformer** (нужен для примитивов) + **xpClothModifier** (без настроек, должен быть активен) + опционально **xpSurface** (толщина, subdivision, разрывы лучше). Настройки — на **xpCloth tag** (на деформере, если он используется): Iterations (жёсткость), Structure/Shear/Bend; **Plasticity** Start/Limit (остаточные вмятины — металл); **Tearing**: прочность, число разрывов от напряжения, карта разрывов; Pinning через vertex map; Collisions Simulate/Connect; Sticky (только полигоны). xpPin tag пинит к другому объекту. Больше subframes — жёстче ткань.
- **Bullet:** тег **xpBullet Rigid Body** (Activate Immediate / On Collision / After Time; форма Auto/Box/Sphere/Cylinder/Capsule/Convex Hull (+Full Hull)/Triangulated Mesh; плотность World/Custom/Mass; Bounce, Friction), тег **Soft Body**, тег **Collider**, вкладки Forces/Modifiers; **xpBulletConstraints** (Fixed, 6DOF, Cone, Hinge, Point to Point, Slider, Spring, Sticky; Break on Impulse). Scene Size — в Project Settings.

## Теги
- **xpCollider** — нужен, чтобы частицы сталкивались с объектом: Bounce/Variation, Friction, Scatter, движок коллизий (адаптивные границы), Actions при столкновении (question не нужен; speed-экшены не работают → используйте xpSpeed), **Connect on Collision** (липкая слизь). Список Groups ограничивает коллайдеры.
- **xpDynamics** — делает объект мягким/твёрдым через прикреплённые частицы (вершины/поверхность/объём): Rigidity, Pressure, Volume Pressure, силы связей, начальная Linear/Angular скорость. Не совмещайте keyframe и симуляцию.
- Теги **xpExplosiaFX Source / Collider** — см. выше.
- **xpWetMap** — vertex map мокрости там, где попали частицы (Distance, Wetness, Fade = высыхание, Spread); объект должен быть редактируемым; для превью снимите Render Only. Применение: потемнение мокрого песка/следов, промокшие от дождя поверхности.
- **xpPin**, **xpLink**, **xpTrailTip**, **xpPathData**, **xpNewtonGravity**, **xpFreeze**, **xpLight**, тег **xpCache** — мелкие вспомогательные теги (пиннинг ткани, привязка объектов к частицам, кончики шлейфов, данные пути, источники гравитации, заморозка, свет, включение cache для отдельного объекта).
