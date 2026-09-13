---
layout: default
title: Инструкция по настройке
---

<style>
/* === SETUP ACCORDION STYLES === */

.setup-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px 15px;
}

/* Hero Section */
.setup-hero {
    text-align: center;
    padding: 40px 20px;
    margin-bottom: 40px;
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
    border-radius: 20px;
    border: 1px solid rgba(102, 126, 234, 0.2);
}

body.dark-mode .setup-hero {
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.15) 0%, rgba(118, 75, 162, 0.15) 100%);
}

.setup-hero h2 {
    font-size: 2.2em;
    font-weight: 800;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 20px;
}

.setup-hero p {
    font-size: 1.2em;
    line-height: 1.8;
    color: var(--text-light);
    margin-bottom: 15px;
}

body.dark-mode .setup-hero p {
    color: var(--text-dark);
}

.setup-hero .highlight {
    font-weight: 700;
    color: var(--primary);
    padding: 8px 16px;
    background: rgba(102, 126, 234, 0.1);
    border-radius: 8px;
    display: inline-block;
    margin: 10px 0;
}

/* Platform Cards Grid */
.platforms-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 25px;
    margin: 30px 0;
    position: relative;
}

.platform-card {
    background: var(--card-light);
    border-radius: 16px;
    padding: 30px;
    border: 1px solid rgba(102, 126, 234, 0.3);
    box-shadow: 0 4px 20px rgba(102, 126, 234, 0.1);
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    cursor: pointer;
    position: relative;
    overflow: hidden;
    min-height: 180px;
}

body.dark-mode .platform-card {
    background: var(--card-dark);
    border-color: rgba(102, 126, 234, 0.2);
    box-shadow: none;
}

.platform-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 3px;
    background: linear-gradient(90deg, var(--primary), var(--primary-dark));
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.3s ease;
}

.platform-card:hover::before { 
    transform: scaleX(1); 
}

.platform-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 15px 35px rgba(102, 126, 234, 0.2);
}

/* Active card - full width */
.platform-card.active {
    grid-column: 1 / -1;
    order: -1;
    border-color: var(--primary);
    box-shadow: 0 20px 50px rgba(102, 126, 234, 0.4);
    z-index: 10;
}

/* Hide other cards when one is active */
.platforms-grid.has-active .platform-card:not(.active) {
    opacity: 0;
    pointer-events: none;
    transform: scale(0.8);
}

.platform-header {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-bottom: 15px;
}

.platform-icon {
    width: 60px;
    height: 60px;
    flex-shrink: 0;
}

.platform-icon svg {
    width: 100%;
    height: 100%;
    stroke: var(--primary);
    stroke-width: 2;
    fill: none;
}

body.dark-mode .platform-icon svg { 
    stroke: #ffffff; 
}

.platform-title {
    font-size: 1.5em;
    font-weight: 700;
    color: var(--primary);
    margin: 0;
}

.platform-subtitle {
    font-size: 1em;
    color: var(--text-light);
    margin-top: 5px;
    line-height: 1.5;
}

body.dark-mode .platform-subtitle {
    color: var(--text-dark);
}

.expand-icon {
    position: absolute;
    top: 20px;
    right: 20px;
    width: 30px;
    height: 30px;
    transition: transform 0.3s ease;
}

.expand-icon svg {
    width: 100%;
    height: 100%;
    stroke: var(--primary);
    stroke-width: 2;
    fill: none;
}

.platform-card.active .expand-icon {
    transform: rotate(180deg);
}

/* Close button */
.close-btn {
    position: absolute;
    top: 20px;
    right: 60px;
    width: 30px;
    height: 30px;
    background: rgba(102, 126, 234, 0.2);
    border-radius: 50%;
    display: none;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.3s;
    z-index: 20;
}

.close-btn:hover {
    background: rgba(102, 126, 234, 0.4);
    transform: rotate(90deg);
}

.close-btn svg {
    width: 20px;
    height: 20px;
    stroke: var(--primary);
    stroke-width: 2;
    fill: none;
}

.platform-card.active .close-btn {
    display: flex;
}

/* Accordion Content */
.accordion-content {
    max-height: 0;
    overflow: hidden;
    opacity: 0;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    margin-top: 0;
}

.platform-card.active .accordion-content {
    max-height: 5000px;
    opacity: 1;
    margin-top: 30px;
    padding-top: 30px;
    border-top: 2px solid rgba(102, 126, 234, 0.2);
}

/* Info Boxes */
.info-box {
    background: rgba(102, 126, 234, 0.08);
    border-left: 4px solid var(--primary);
    border-radius: 12px;
    padding: 20px;
    margin: 20px 0;
}

body.dark-mode .info-box {
    background: rgba(102, 126, 234, 0.15);
}

.info-box.recommendation {
    background: rgba(16, 185, 129, 0.08);
    border-left-color: #10b981;
}

body.dark-mode .info-box.recommendation {
    background: rgba(16, 185, 129, 0.15);
}

.info-box-title {
    font-weight: 700;
    color: var(--primary);
    margin-bottom: 10px;
    font-size: 1.1em;
    line-height: 1.5;
}

.info-box.recommendation .info-box-title {
    color: #10b981;
}

.info-box p {
    line-height: 1.7;
    margin: 10px 0;
}

/* App Lists */
.app-list {
    list-style: none;
    padding: 0;
    margin: 15px 0;
}

.app-list li {
    padding: 12px 0;
    border-bottom: 1px solid rgba(102, 126, 234, 0.1);
    line-height: 1.6;
}

.app-list li:last-child {
    border-bottom: none;
}

.app-list li::before {
    content: '→ ';
    color: var(--primary);
    font-weight: 700;
    font-size: 1.2em;
}

/* Links - изоляция от глобальных стилей */
.setup-link {
    color: var(--primary) !important;
    text-decoration: none !important;
    font-weight: 600 !important;
    transition: opacity 0.3s !important;
    display: inline !important;
    padding: 0 !important;
    margin: 0 !important;
    line-height: 1.6 !important;
    word-break: break-word !important;
}

.setup-link:hover {
    opacity: 0.8 !important;
    text-decoration: underline !important;
}

.setup-link::after {
    display: none !important;
}

/* Numbered Steps */
.numbered-steps {
    counter-reset: step-counter;
    list-style: none;
    padding: 0;
    margin: 20px 0;
}

.numbered-steps li {
    counter-increment: step-counter;
    padding: 15px 20px 15px 60px;
    position: relative;
    margin-bottom: 15px;
    background: var(--card-light);
    border-radius: 12px;
    border: 1px solid rgba(102, 126, 234, 0.2);
    line-height: 1.6;
}

body.dark-mode .numbered-steps li {
    background: var(--card-dark);
}

.numbered-steps li::before {
    content: counter(step-counter);
    position: absolute;
    left: 15px;
    top: 50%;
    transform: translateY(-50%);
    width: 35px;
    height: 35px;
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 1.1em;
}

/* Key Box */
.key-box {
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
    border: 2px dashed var(--primary);
    border-radius: 12px;
    padding: 20px;
    margin: 20px 0;
    font-family: 'Courier New', monospace;
    word-break: break-all;
    text-align: center;
    font-weight: 600;
    color: var(--primary);
    line-height: 1.6;
}

body.dark-mode .key-box {
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.2), rgba(118, 75, 162, 0.2));
}

/* Success Box */
.success-box {
    text-align: center;
    padding: 40px 30px;
    background: linear-gradient(135deg, rgba(16, 185, 129, 0.1), rgba(5, 150, 105, 0.1));
    border: 2px solid #10b981;
    border-radius: 20px;
    margin: 40px 0;
}

body.dark-mode .success-box {
    background: linear-gradient(135deg, rgba(16, 185, 129, 0.2), rgba(5, 150, 105, 0.2));
}

.success-box h3 {
    font-size: 2em;
    color: #10b981;
    margin-bottom: 15px;
    font-weight: 800;
}

.success-box p {
    font-size: 1.3em;
    color: var(--text-light);
    line-height: 1.6;
}

body.dark-mode .success-box p {
    color: var(--text-dark);
}

/* Section Headers */
.section-header {
    font-size: 1.4em;
    font-weight: 700;
    color: var(--primary);
    margin: 25px 0 15px;
    padding-bottom: 10px;
    border-bottom: 2px solid rgba(102, 126, 234, 0.2);
}

/* Back instruction */
.back-instruction {
    text-align: center;
    padding: 20px;
    margin: 20px 0;
    background: rgba(102, 126, 234, 0.08);
    border-radius: 12px;
    display: none;
}

.platforms-grid.has-active .back-instruction {
    display: block;
}

.back-instruction p {
    color: var(--text-light);
    font-size: 1.1em;
    margin: 0;
}

body.dark-mode .back-instruction {
    background: rgba(102, 126, 234, 0.15);
}

/* Responsive */
@media (max-width: 968px) {
    .platforms-grid {
        grid-template-columns: 1fr;
        gap: 20px;
    }
    
    .platform-card.active {
        grid-column: 1;
    }
    
    .platforms-grid.has-active .platform-card:not(.active) {
        display: none;
    }
}

@media (max-width: 768px) {
    .setup-hero h2 { font-size: 1.7em; }
    .setup-hero p { font-size: 1em; }
    .platform-card { padding: 25px; }
    .platform-title { font-size: 1.3em; }
    .platform-icon { width: 50px; height: 50px; }
    .numbered-steps li {
        padding: 15px 15px 15px 55px;
    }
    .numbered-steps li::before {
        width: 30px;
        height: 30px;
        left: 10px;
        font-size: 0.9em;
    }
}
</style>

<div class="setup-container">

<!-- Hero Section -->
<div class="setup-hero">
    <h3>Настройка подключения: Гайд за 2 минуты</h3>
    <p>Поздравляем! Ты теперь с нами.</p>
    <p>Ключ у тебя в кармане (в боте), осталось всего пару кликов, чтобы настроить подключение.</p>
    <div class="highlight">Скопировал → Вставил → Полетело</div>
</div>

<!-- Platform Selection -->
<p style="text-align: center; font-size: 1.3em; margin-bottom: 30px; color: var(--text-light);">
    <strong>Выбери своё устройство:</strong>
</p>

<div class="platforms-grid" id="platformsGrid">
    <!-- iOS Card -->
    <div class="platform-card" onclick="toggleAccordion(this)">
        <div class="expand-icon">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
        </div>
        <div class="close-btn" onclick="event.stopPropagation(); closeAccordion()">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
        </div>
        <div class="platform-header">
            <div class="platform-icon">
                <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"/>
                    <path d="M12 6v6l4 2"/>
                </svg>
            </div>
            <div>
                <h3 class="platform-title">iOS</h3>
                <p class="platform-subtitle">iPhone / iPad</p>
            </div>
        </div>
        
        <div class="accordion-content">
            <h4 class="section-header">📱 Шаг 1: Скачай приложение</h4>
            
            <div class="info-box">
                <div class="info-box-title">📱 Для тех, у кого Российский 🇷🇺 аккаунт Apple</div>
                <ul class="app-list">
                    <li>Скачиваем <strong>Karing</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                    <li><a href="/Tunless_Modern/karing.html" class="setup-link">👉 Инструкция по настройке Karing</a></li>
                    <li>или</li>
                    <li>Скачиваем <strong>Happ</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                </ul>
            </div>

            <div class="info-box">
                <div class="info-box-title"> Для тех, кто хочет создать иностранный аккаунт</div>
                <p>Например, Американский 🇺🇸 и получить доступ к приложениям, удалённым из Российского 🇷🇺 AppStore.</p>
                <p style="margin-top: 10px;"><em>Инструкция по созданию иностранного аккаунта скоро будет доступна.</em></p>
            </div>

            <div class="info-box recommendation">
                <div class="info-box-title">⭐ Приложения для тех, у кого есть иностранный аккаунт Apple</div>
                <ul class="app-list">
                    <li>Скачиваем <strong>Karing</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                    <li>Скачиваем <strong>V2Box</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                    <li>Скачиваем <strong>V2RayTUN</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                    <li>Скачиваем <strong>Hiddify</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                    <li>Скачиваем <strong>Happ</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                </ul>
                <p style="margin-top: 15px; font-size: 0.95em;"><strong>💡 Мы рекомендуем Karing или Hiddify</strong>, т.к. в них, на данный момент, есть автоматическое переключение между протоколами.</p>
            </div>

            <h4 class="section-header"> Шаг 2: Скопируй свой ключ</h4>
            <ol class="numbered-steps">
                <li>Зайди в бота, где купил ключ</li>
                <li>Нажми кнопку 🔑 <strong>Мои ключи</strong></li>
                <li>Выбери купленный ключ и нажми 📋 <strong>Получить ключ</strong></li>
                <li>Ключ (длинный код, начинающийся на <code>vless://</code>) скопируется в буфер обмена</li>
            </ol>

            <div class="key-box">
                vless://xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@server:port?encryption=none&security=tls&type=ws&host=example.com&path=%2Fpath#Tunless
            </div>

            <h4 class="section-header">⚡ Шаг 3: Запускаем!</h4>
            <div class="info-box">
                <div class="info-box-title">Для iPhone (Karing)</div>
                <p>У приложения одинаковый интерфейс на всех платформах. Всё будет знакомо!</p>
                <p style="margin-top: 15px;"><a href="/Tunless_Modern/karing.html" class="setup-link">👉 Подробная инструкция с картинками</a></p>
            </div>
        </div>
    </div>

    <!-- Android Card -->
    <div class="platform-card" onclick="toggleAccordion(this)">
        <div class="expand-icon">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
        </div>
        <div class="close-btn" onclick="event.stopPropagation(); closeAccordion()">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
        </div>
        <div class="platform-header">
            <div class="platform-icon">
                <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                    <rect x="4" y="8" width="16" height="12" rx="2"/>
                    <line x1="8" y1="4" x2="8" y2="8"/>
                    <line x1="12" y1="4" x2="12" y2="8"/>
                    <line x1="16" y1="4" x2="16" y2="8"/>
                </svg>
            </div>
            <div>
                <h3 class="platform-title">Android</h3>
                <p class="platform-subtitle">Android / Android TV / Google TV</p>
            </div>
        </div>
        
        <div class="accordion-content">
            <h4 class="section-header">📱 Шаг 1: Скачай приложение</h4>
            
            <p style="margin-bottom: 15px;"><strong>Тебе нужен:</strong></p>
            <ul class="app-list">
                <li><a href="#" class="setup-link"><strong>Karing</strong> (GitHub)</a></li>
                <li><a href="#" class="setup-link"><strong>V2RayTun</strong></a></li>
                <li><a href="#" class="setup-link"><strong>V2Box</strong></a></li>
                <li><a href="#" class="setup-link"><strong>Hiddify</strong></a></li>
                <li><a href="#" class="setup-link"><strong>Happ</strong></a></li>
            </ul>

            <h4 class="section-header"> Шаг 2: Скопируй свой ключ</h4>
            <ol class="numbered-steps">
                <li>Зайди в бота, где купил ключ</li>
                <li>Нажми кнопку 🔑 <strong>Мои ключи</strong></li>
                <li>Выбери купленный ключ и нажми 📋 <strong>Получить ключ</strong></li>
                <li>Ключ (длинный код, начинающийся на <code>vless://</code>) скопируется в буфер обмена</li>
            </ol>

            <div class="key-box">
                vless://xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@server:port?encryption=none&security=tls&type=ws&host=example.com&path=%2Fpath#Tunless
            </div>

            <h4 class="section-header">⚡ Шаг 3: Запускаем!</h4>
            <div class="info-box">
                <div class="info-box-title">Для Android (V2RayTun)</div>
                <ol class="numbered-steps" style="margin: 15px 0;">
                    <li>Открой скачанную программу</li>
                    <li>Нажми на плюсик (+) в правом верхнем углу</li>
                    <li>Выбери пункт "Импорт профиля из буфера обмена"</li>
                    <li>Твой сервер появится в списке. Нажми на него, выбери протокол, чтобы он выделился (станет зеленым или серым)</li>
                    <li>Нажми большую кнопку "Connect"</li>
                </ol>
            </div>
        </div>
    </div>

    <!-- PC Card -->
    <div class="platform-card" onclick="toggleAccordion(this)">
        <div class="expand-icon">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
        </div>
        <div class="close-btn" onclick="event.stopPropagation(); closeAccordion()">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
        </div>
        <div class="platform-header">
            <div class="platform-icon">
                <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                    <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
                    <line x1="8" y1="21" x2="16" y2="21"/>
                    <line x1="12" y1="17" x2="12" y2="21"/>
                </svg>
            </div>
            <div>
                <h3 class="platform-title">PC</h3>
                <p class="platform-subtitle">Windows / Mac / Linux</p>
            </div>
        </div>
        
        <div class="accordion-content">
            <h4 class="section-header">💻 Шаг 1: Скачай приложение</h4>
            
            <div class="info-box recommendation">
                <div class="info-box-title">⭐ Рекомендуем Karing</div>
                <p>Один из самых продвинутых с открытым исходным кодом и поддержкой самых современных протоколов и их автовыбором.</p>
                <p style="margin-top: 10px;"><a href="#" class="setup-link">👉 Скачать Karing (GitHub) Portable версия</a></p>
            </div>

            <div class="info-box">
                <div class="info-box-title">💎 Или Hiddify</div>
                <p>Самый красивый и понятный клиент для компов с автовыбором наилучшего протокола.</p>
                <p style="margin-top: 10px;"><a href="#" class="setup-link">👉 Скачать Hiddify (GitHub) Portable версия</a></p>
            </div>

            <div style="margin-top: 20px; padding-top: 20px; border-top: 2px solid rgba(102, 126, 234, 0.2);">
                <p style="margin-bottom: 10px;"><strong>Ссылки на проекты на GitHub:</strong></p>
                <ul class="app-list">
                    <li><a href="#" class="setup-link">👉 Karing</a></li>
                    <li><a href="#" class="setup-link">👉 Hiddify</a></li>
                </ul>
                <p style="font-size: 0.9em; margin: 15px 0;"><em>Выбирай файл <code>.exe</code> или <code>.zip</code> для Windows или <code>.dmg</code> для Mac.</em></p>
            </div>

            <div class="info-box" style="margin-top: 20px;">
                <p>Ну а если уже пользовались и привыкли к <strong>Happ</strong> и <strong>V2RayN</strong>, то аналогичные есть и на Windows и Mac:</p>
                <ul class="app-list" style="margin-top: 10px;">
                    <li><a href="#" class="setup-link">👉 Скачать Happ (GitHub)</a></li>
                    <li><a href="#" class="setup-link">👉 Скачать V2RayN</a></li>
                </ul>
            </div>

            <h4 class="section-header">🔑 Шаг 2: Скопируй свой ключ</h4>
            <ol class="numbered-steps">
                <li>Зайди в бота, где купил ключ</li>
                <li>Нажми кнопку 🔑 <strong>Мои ключи</strong></li>
                <li>Выбери купленный ключ и нажми 📋 <strong>Получить ключ</strong></li>
                <li>Ключ (длинный код, начинающийся на <code>vless://</code>) скопируется в буфер обмена</li>
            </ol>

            <div class="key-box">
                vless://xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@server:port?encryption=none&security=tls&type=ws&host=example.com&path=%2Fpath#Tunless
            </div>

            <h4 class="section-header">⚡ Шаг 3: Запускаем!</h4>
            <div class="info-box">
                <div class="info-box-title">Для ПК (Hiddify)</div>
                <ol class="numbered-steps" style="margin: 15px 0;">
                    <li>Открой Hiddify</li>
                    <li>Нажми "Новый профиль" или большой плюс (+)</li>
                    <li>Выбери "Добавить из буфера обмена"</li>
                    <li>Нажми большую кнопку подключения по центру</li>
                </ol>
            </div>
        </div>
    </div>
</div>

<!-- Back Instruction -->
<div class="back-instruction">
    <p>💡 Чтобы выбрать другое устройство, закрой эту инструкцию (нажми на ✕ или кликни ещё раз)</p>
</div>

<!-- Success Box -->
<div class="success-box">
    <h3>✅ Готово! Ты подключен к VPN!</h3>
    <p>Наслаждайся быстрым и безопасным интернетом!</p>
</div>

</div>

<script>
function toggleAccordion(card) {
    const grid = document.getElementById('platformsGrid');
    const isActive = card.classList.contains('active');
    
    // Close all cards
    const allCards = document.querySelectorAll('.platform-card');
    allCards.forEach(c => c.classList.remove('active'));
    
    if (!isActive) {
        // Open clicked card
        card.classList.add('active');
        grid.classList.add('has-active');
        
        // Smooth scroll to card
        setTimeout(() => {
            card.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }, 100);
    } else {
        // All cards closed
        grid.classList.remove('has-active');
    }
}

function closeAccordion() {
    const grid = document.getElementById('platformsGrid');
    const allCards = document.querySelectorAll('.platform-card');
    allCards.forEach(c => c.classList.remove('active'));
    grid.classList.remove('has-active');
}
</script>
