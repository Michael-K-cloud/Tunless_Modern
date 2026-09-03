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

.step-section h3 {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-top: 0;
  margin-bottom: 15px;
  color: var(--primary);
  font-size: 1.4em;
}

.step-section h3 svg {
  width: 28px;
  height: 28px;
  stroke: var(--primary);
  fill: none;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
  flex-shrink: 0;
}

body.dark-mode .step-section h3 svg {
  stroke: #a5b4fc;
}

.warning-box {
  background: linear-gradient(135deg, var(--warning) 0%, #ef4444 100%);
  color: white;
  padding: 20px;
  border-radius: 12px;
  margin: 25px 0;
  text-align: center;
  font-weight: 700;
  font-size: 1.2em;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  animation: pulse 2s infinite;
}

.warning-box svg {
  width: 28px;
  height: 28px;
  stroke: white;
  fill: none;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
  flex-shrink: 0;
}

.warning-box span {
  flex: 1;
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 4px 15px rgba(245, 158, 11, 0.3);
  }
  50% {
    box-shadow: 0 4px 25px rgba(245, 158, 11, 0.6);
  }
}

/* Стили для кнопки "Вернуться" */
.cta-button {
  display: inline-flex !important;
  align-items: center !important;
  justify-content: center !important;
  gap: 12px;
  padding: 16px 32px !important;
  min-width: 280px;
  background: transparent;
  color: var(--primary) !important;
  text-decoration: none !important;
  border-radius: 12px;
  font-weight: 700;
  font-size: 1.1em;
  line-height: 1.2 !important;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  border: 2px solid var(--primary);
  box-sizing: border-box;
}

body.dark-mode .cta-button {
  color: #a5b4fc !important;
  border-color: #a5b4fc;
}

.cta-button:hover {
  background: rgba(102, 126, 234, 0.1);
  transform: translateY(-4px);
}

.cta-button svg {
  width: 24px;
  height: 24px;
  stroke: currentColor;
  fill: none;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
  flex-shrink: 0;
}

.cta-button span {
  display: inline-block;
  line-height: 1.2 !important;
  vertical-align: middle !important;
}

/* Стили для заголовков разделов с SVG */
.content h3 {
  display: flex;
  align-items: center;
  gap: 12px;
}

.content h3 svg {
  width: 28px;
  height: 28px;
  stroke: var(--primary-dark);
  fill: none;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
  flex-shrink: 0;
}

body.dark-mode .content h3 svg {
  stroke: #a5b4fc;
}

@media (max-width: 768px) {
  .image-grid {
    grid-template-columns: 1fr;
    gap: 15px;
  }
  
  .image-card {
    padding: 10px;
  }
  
  .cta-button {
    min-width: auto;
    width: 100%;
    max-width: 300px;
  }
}
</style>

<!-- Warning Box с иконками по краям -->
<div class="warning-box">
  <svg viewBox="0 0 24 24">
    <path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"></path>
    <line x1="12" y1="9" x2="12" y2="13"></line>
    <line x1="12" y1="17" x2="12.01" y2="17"></line>
  </svg>
  <span>Первый запуск приложения очень ВАЖЕН!</span>
  <svg viewBox="0 0 24 24">
    <path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"></path>
    <line x1="12" y1="9" x2="12" y2="13"></line>
    <line x1="12" y1="17" x2="12.01" y2="17"></line>
  </svg>
</div>

<div class="step-section">
  <h3>
    <svg viewBox="0 0 24 24">
      <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
      <polyline points="14 2 14 8 20 8"></polyline>
      <line x1="16" y1="13" x2="8" y2="13"></line>
      <line x1="16" y1="17" x2="8" y2="17"></line>
      <polyline points="10 9 9 9 8 9"></polyline>
    </svg>
    Что нужно перед запуском:
  </h3>
  <p>Перед запуском приложения, желательно скопировать ссылку для подключения, выданную в <strong>@Tunless_bot</strong>.</p>
</div>

### <svg viewBox="0 0 24 24" width="28" height="28" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="vertical-align: middle; margin-right: 8px;"><circle cx="12" cy="12" r="10"></circle><polygon points="16.24 7.76 14.12 14.12 7.76 16.24 9.88 9.88 16.24 7.76"></polygon></svg> Пошаговая настройка:

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
    <p>Шаг 4: Включите режим "Новичка"</p>
  </div>

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

### <svg viewBox="0 0 24 24" width="28" height="28" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="vertical-align: middle; margin-right: 8px;"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"></path></svg> Быстрая инструкция:

1. **Запустите Karing**
2. **Выберите регион** — для России выберите "Russia"
3. **Настройте роутинг** — российские сайты будут работать без VPN
4. **Включите режим "Новичка"** — скроет настройки для "Экспертов"
5. **Добавьте профиль** — вставьте ключ из буфера обмена
6. **Подключитесь** — нажмите кнопку подключения

**Готово! Ты под защитой ️**

---

<div style="text-align: center; margin-top: 40px;">
  <a href="/Tunless_Modern/setup.html" class="cta-button">
    <svg viewBox="0 0 24 24">
      <line x1="19" y1="12" x2="5" y2="12"></line>
      <polyline points="12 19 5 12 12 5"></polyline>
    </svg>
    <span>Вернуться к инструкции</span>
  </a>
</div>
