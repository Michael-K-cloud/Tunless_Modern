---
layout: default
title: Инструкция по настройке
---

<style>
  /* Стили для иконок платформ */
  .platform-icon {
    display: inline-block;
    vertical-align: middle;
    margin-right: 8px;
    width: 24px;
    height: 24px;
  }

  /* Apple: черный на светлой, белый на темной */
  .apple-icon {
    filter: brightness(0);
  }
  body.dark-mode .apple-icon {
    filter: brightness(0) invert(1);
  }

  /* Android: зеленый (#3DDC84) на любой теме */
  .android-icon {
    filter: invert(68%) sepia(98%) saturate(393%) hue-rotate(85deg) brightness(103%) contrast(101%);
  }

  /* Windows: синий (#0078D4) на светлой, светло-голубой (#50E6FF) на темной */
  .windows-icon {
    filter: invert(35%) sepia(96%) saturate(3847%) hue-rotate(202deg) brightness(97%) contrast(101%);
  }
  body.dark-mode .windows-icon {
    filter: invert(75%) sepia(51%) saturate(541%) hue-rotate(153deg) brightness(104%) contrast(101%);
  }

  /* Стили для маленьких иконок в шаге 3 */
  .platform-icon-sm {
    width: 20px;
    height: 20px;
  }

  /* Сетка для изображений (на будущее) */
  .image-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    margin: 30px 0;
  }
  .image-card {
    background: var(--card-light);
    border-radius: 12px;
    padding: 15px;
    text-align: center;
    box-shadow: 0 4px 15px rgba(102, 126, 234, 0.1);
    transition: transform 0.3s ease;
  }
  body.dark-mode .image-card {
    background: var(--card-dark);
  }
  .image-card:hover {
    transform: translateY(-5px);
  }
  .image-card img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
  }
</style>

## 🚀 Как настроить подключение: Гайд за 2 минуты

Поздравляем! 
Ты теперь с нами. Ключ у тебя в кармане (в боте), осталось всего пару кликов, чтобы настроить подключение.

Мы не любим сложные инструкции, поэтому вот тебе простой гайд: 
**Скопировал → Вставил → Полетело.**

---

## Шаг 1. Скачай приложение

У нас современные протоколы, поэтому старые программы не подойдут. 
Качай проверенные официальные клиенты:

### <img src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Apple_logo_black.svg" class="platform-icon apple-icon" alt="Apple"> iPhone / iPad (iOS)

#### Приложение для тех, у кого Российский 🇷🇺 аккаунт Apple

Скачиваем **Karing** → [Скачать в AppStore](https://apps.apple.com/ru/app/karing/id6472431552)

👉 [Инструкция по приложению и настройке Karing](/Tunless_Modern/karing.html)

или

Скачиваем **Happ** → [Скачать в AppStore](https://apps.apple.com/app/happ/id6596055417)

#### Для тех, кто хочет создать иностранный аккаунт

Например, Американский 🇺🇸 и получить доступ к приложениям, удалённым из Российского 🇷🇺 AppStore.

Инструкция по созданию иностранного аккаунта [скоро будет доступна](/Tunless_Modern/account.html).

#### Приложения для тех, у кого есть иностранный аккаунт Apple

Скачиваем любое приложение. Но мы рекомендуем **Karing** или **Hiddify**!

- Скачиваем **Karing** → [Скачать в AppStore](https://apps.apple.com/ru/app/karing/id6472431552)
- Скачиваем **V2Box** → [Скачать в AppStore](https://apps.apple.com/app/v2box-v2ray-client/id6448898396)
- Скачиваем **V2RayTUN** → [Скачать в AppStore](https://apps.apple.com/app/v2raytun/id6476628951)
- Скачиваем **Hiddify** → [Скачать в AppStore](https://apps.apple.com/app/hiddify/id6596055417)
- Скачиваем **Happ** → [Скачать в AppStore](https://apps.apple.com/app/happ/id6596055417)

> Мы рекомендуем **Karing** или **Hiddify**, т.к. в них, на данный момент, есть автоматическое переключение между протоколами.

---

### <img src="https://upload.wikimedia.org/wikipedia/commons/d/d7/Android_robot.svg" class="platform-icon android-icon" alt="Android"> Android / Android TV / Google TV

Тебе нужен:

- **Karing** ([GitHub](https://github.com/KaringX/karing))
- **V2RayTun**
- **V2Box**
- **Hiddify**
- **Happ**

---

### <img src="https://upload.wikimedia.org/wikipedia/commons/5/5f/Windows_logo_-_2012.svg" class="platform-icon windows-icon" alt="Windows"> Windows / Mac / Linux

#### Рекомендуем Karing

Один из самых продвинутых с открытым исходным кодом и поддержкой самых современных протоколов и их автовыбором.

👉 [Скачать Karing (GitHub) Portable версия](https://github.com/KaringX/karing/releases)

#### Или Hiddify

Самый красивый и понятный клиент для компов с автовыбором наилучшего протокола.

👉 [Скачать Hiddify (GitHub) Portable версия](https://github.com/hiddify/hiddify-next/releases)

#### Ссылки на проекты на GitHub:

- 👉 [Karing](https://github.com/KaringX/karing)
- 👉 [Hiddify](https://github.com/hiddify/hiddify-next)

Выбирай файл `.exe` или `.zip` для Windows или `.dmg` для Mac.

Ну а если уже пользовались и привыкли к **Happ** и **V2RayN**, то аналогичные есть и на Windows и Mac:

- 👉 [Скачать Happ (GitHub)](https://github.com/Happ-proxy/happ-desktop/releases)
- 👉 [Скачать V2RayN](https://github.com/2dust/v2rayN/releases)

---

## Шаг 2. Скопируй свой ключ

1. Зайди в бота, где купил ключ
2. Нажми кнопку 🔑 **Мои ключи**
3. Выбери купленный ключ и нажми 📋 **Получить ключ**
4. Ключ (длинный код, начинающийся на `vless://`) скопируется в буфер обмена

---

## Шаг 3. Запускаем!

Выбери свое устройство и делай как написано:

### <img src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Apple_logo_black.svg" class="platform-icon platform-icon-sm apple-icon" alt="Apple"> Для iPhone (Karing):

У приложения одинаковый интерфейс на всех платформах. Всё будет знакомо!

👉 [Подробная инструкция с картинками](/Tunless_Modern/karing.html)

### <img src="https://upload.wikimedia.org/wikipedia/commons/d/d7/Android_robot.svg" class="platform-icon platform-icon-sm android-icon" alt="Android"> Для Android (V2RayTun):

1. Открой скачанную программу
2. Нажми на плюсик (+) в правом верхнем углу
3. Выбери пункт "Импорт профиля из буфера обмена"
4. Твой сервер появится в списке. Нажми на него, выбери протокол, чтобы он выделился (станет зеленым или серым)
5. Нажми большую кнопку "Connect"

### <img src="https://upload.wikimedia.org/wikipedia/commons/5/5f/Windows_logo_-_2012.svg" class="platform-icon platform-icon-sm windows-icon" alt="Windows"> Для ПК (Hiddify):

1. Открой Hiddify
2. Нажми "Новый профиль" или большой плюс (+)
3. Выбери "Добавить из буфера обмена"
4. Нажми большую кнопку подключения по центру

---

**Готово! Ты подключен к VPN! 🎉**
