# Три способа заставить частицы сталкиваться друг с другом (xpConstraints Collisions, xpPPCollisions, xpBullet)

- Источник: Top Tip Tuesday — xpCollisions — https://www.youtube.com/watch?v=GGI1MyewI2g (2023-02-21)
- Хост / поколение: C4D; CPU-динамика X-Particles + теги INSYDIUM Bullet
- Задача: выбрать подходящий метод коллизий частица–частица под нужную форму и детализацию.

## Исходная сцена
Частицы падают под гравитацией на пол с тегом **xpCollider** — и проходят друг сквозь друга.

## Шаги
1. Быстрее всего: Dynamics ▸ **xpConstraints** ▸ включить вкладку **Collisions**. Одна настройка — **Stiffness**. Быстро, базово. [▶ 0:47](https://youtu.be/GGI1MyewI2g?t=47)
2. Больше контроля: Dynamics ▸ **xpPPCollisions**. Работает уже по умолчанию; добавляет **Bounce** частица–частица (+ вариация), **Friction** (прилипание после контакта), **Scatter** (случайное направление отскока), а также опции рождения и соединения при столкновении. [▶ 2:12](https://youtu.be/GGI1MyewI2g?t=132)
3. Ограничение обоих: коллизии **сферические** (по радиусу) — нормально для отображения сферами; с **Box Filled** углы пересекаются, ничего не катится и не кувыркается. [▶ 2:51](https://youtu.be/GGI1MyewI2g?t=171)
4. С учётом формы: уберите xpCollider с пола; Tags ▸ Extensions ▸ INSYDIUM Bullet ▸ **Bullet Collider** на пол, тег **Bullet Rigid Body** на эмиттер (по умолчанию). [▶ 3:59](https://youtu.be/GGI1MyewI2g?t=239)
5. Bullet учитывает форму отображения — кубы, **Pyramid**, даже **Arrow Filled** — с перекатыванием и отскоками; у него свои bounce/friction/scatter. [▶ 4:42](https://youtu.be/GGI1MyewI2g?t=282)

## Подводные камни
У Bullet свой тег коллайдера; не смешивайте его с xpCollider на одном и том же полу.

## Как сейчас (новые инструменты)
Сферические коллизии на GPU: **слой Collisions в nxConstraints** / nxPPCollisions / nxPush. Для твёрдых частиц с точной формой GPU-варианта пока нет (единые rigid bodies только анонсированы в Nov 2026) — оставайтесь на xpBullet или тегах C4D Rigid Body на геометрии xpGenerator (рецепт 2025-08-26).
