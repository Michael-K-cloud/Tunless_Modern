---
layout: default
title: Инструкция по настройке Karing
--- 
## Инструкция по настройке Karing


<style>
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
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.image-card p {
  margin-top: 12px;
  font-weight: 600;
  color: var(--primary);
}

.step-section {
  margin: 40px 0;
  padding: 25px;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
  border-radius: 15px;
  border-left: 4px solid var(--primary);
}

.warning-box {
  background: linear-gradient(135deg, var(--warning) 0%, #ef4444 100%);
  color: white;
  padding: 20px;
  border-radius: 12px;
  margin: 25px 0;
  text-align: center;
  font-weight: 700;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 4px 15px rgba(245, 158, 11, 0.3);
  }
  50% {
    box-shadow: 0 4px 25px rgba(245, 158, 11, 0.6);
  }
}

@media (max-width: 768px) {
  .image-grid {
    grid-template-columns: 1fr;
    gap: 15px;
  }
  
  .image-card {
    padding: 10px;
  }
}
</style>

<div class="warning-box">
  ⚠️ Первый запуск приложения очень ВАЖЕН! ⚠️
</div>

<div class="step-section">
  <h3>📋 Что нужно знать перед запуском:</h3>
  <p>Тут выбираются региональные настройки для роутинга. <strong>Российские сайты будут открываться не используя ВПН, а напрямую!</strong></p>
</div>

### 🎯 Пошаговая настройка:

<div class="image-grid">
  <div class="image-card">
    <img src="https://i.postimg.cc/mZvcKDMN/photo-1-2026-06-15-22-12-18.jpg" alt="Запуск Karing">
    <p>Шаг 1: Запустите приложение Karing</p>
  </div>
  
  <div class="image-card">
    <img src="https://i.postimg.cc/CM3Z91DN/photo-2-2026-06-15-22-12-18.jpg" alt="Выбор региона">
    <p>Шаг 2: Выберите региональные настройки</p>
  </div>
  
  <div class="image-card">
    <img src="https://i.postimg.cc/y6MJ2d9y/photo-3-2026-06-15-22-12-18.jpg" alt="Настройка роутинга">
    <p>Шаг 3: Настройте роутинг для российских сайтов</p>
  </div>
  
  <div class="image-card">
    <img src="https://i.postimg.cc/7PFCj67N/photo-4-2026-06-15-22-12-18.jpg" alt="Готово">
    <p>Шаг 4: Включаем режим "Новичка"</p>
  </div>
</div>

### 🔧 Дополнительные настройки:

<div class="image-grid">
  <div class="image-card">
    <img src="https://i.postimg.cc/SQBXHs8D/photo-5-2026-06-15-22-12-18.jpg" alt="Добавление профиля">
    <p>Добавление профиля из буфера обмена</p>
  </div>
  
  <div class="image-card">
    <img src="https://i.postimg.cc/FFMfwRcC/photo-6-2026-06-15-22-12-18.jpg" alt="Активация VPN">
    <p>Активация VPN подключения</p>
  </div>
</div>

---

### 📱 Быстрая инструкция:

1. **Запустите Karing** впервые
2. **Выберите регион** — для России выберите "Russia" или "Auto"
3. **Настройте роутинг** — российские сайты будут работать без VPN
4. **Добавьте профиль** — вставьте ключ из буфера обмена
5. **Подключитесь** — нажмите кнопку подключения

**Готово! Ты под защитой 🛡️**

---

[← Вернуться к инструкции по настройке](/Tunless_Modern/setup.html)
