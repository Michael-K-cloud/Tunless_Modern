---
layout: default
title: Инструкция по настройке
---

<style>
/* === SETUP-SPECIFIC STYLES === */
/* Изолированные стили только для setup.md */

.setup-container {
    max-width: 1000px;
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
    animation: pulse 2s infinite;
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

/* Step Cards */
.step-section {
    margin: 40px 0;
    animation: fadeInUp 0.6s ease;
}

.step-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 25px;
    padding: 20px;
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    border-radius: 16px;
    box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
}

body.dark-mode .step-header {
    box-shadow: 0 10px 30px rgba(102, 126, 234, 0.2);
}

.step-number {
    width: 50px;
    height: 50px;
    background: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 800;
    font-size: 1.5em;
    color: var(--primary);
    flex-shrink: 0;
}

.step-header h3 {
    color: white;
    font-size: 1.6em;
    font-weight: 700;
    margin: 0;
}

/* Platform Cards Grid */
.platforms-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
    margin: 30px 0;
}

.platform-card {
    background: var(--card-light);
    border-radius: 16px;
    padding: 25px;
    border: 1px solid rgba(102, 126, 234, 0.3);
    box-shadow: 0 4px 20px rgba(102, 126, 234, 0.1);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    position: relative;
    overflow: hidden;
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

.platform-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 20px;
    padding-bottom: 15px;
    border-bottom: 2px solid rgba(102, 126, 234, 0.2);
}

.platform-icon {
    width: 40px;
    height: 40px;
    flex-shrink: 0;
}

.platform-icon svg {
    width: 100%;
    height: 100%;
}

.platform-header h4 {
    font-size: 1.3em;
    color: var(--primary);
    margin: 0;
    font-weight: 700;
}

/* App Lists */
.app-list {
    list-style: none;
    padding: 0;
    margin: 15px 0;
}

.app-list li {
    padding: 10px 0;
    border-bottom: 1px solid rgba(102, 126, 234, 0.1);
    display: flex;
    align-items: center;
    gap: 10px;
}

.app-list li:last-child {
    border-bottom: none;
}

.app-list li::before {
    content: '→';
    color: var(--primary);
    font-weight: 700;
    font-size: 1.2em;
}

/* Links with isolation from global .content a */
.setup-link {
    color: var(--primary) !important;
    text-decoration: none !important;
    font-weight: 600 !important;
    transition: all 0.3s !important;
    display: inline-flex !important;
    align-items: center !important;
    gap: 8px !important;
    padding: 0 !important;
    margin: 0 !important;
    line-height: 1.4 !important;
}

.setup-link:hover {
    transform: translateX(5px) !important;
    opacity: 0.8 !important;
}

.setup-link::after {
    display: none !important;
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
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 1.1em;
}

.info-box.recommendation .info-box-title {
    color: #10b981;
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

/* Code/Key Box */
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
    animation: fadeInUp 0.6s ease;
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
}

body.dark-mode .success-box p {
    color: var(--text-dark);
}

/* Animations */
@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.02); }
}

/* Responsive */
@media (max-width: 768px) {
    .setup-hero h2 { font-size: 1.7em; }
    .setup-hero p { font-size: 1em; }
    .step-header h4 { font-size: 1.3em; }
    .platforms-grid {
        grid-template-columns: 1fr;
        gap: 20px;
    }
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
    <h2>🚀 Как настроить подключение: Гайд за 2 минуты</h2>
    <p>Поздравляем! Ты теперь с нами.</p>
    <p>Ключ у тебя в кармане (в боте), осталось всего пару кликов, чтобы настроить подключение.</p>
    <div class="highlight">Скопировал → Вставил → Полетело</div>
</div>

<!-- Step 1 -->
<div class="step-section">
    <div class="step-header">
        <div class="step-number">1</div>
        <h3>Скачай приложение</h3>
    </div>
    
    <p style="font-size: 1.1em; line-height: 1.8; margin-bottom: 30px;">
        У нас современные протоколы, поэтому старые программы не подойдут. 
        Качай проверенные официальные клиенты:
    </p>

    <div class="platforms-grid">
        <!-- iOS -->
        <div class="platform-card">
            <div class="platform-header">
                <div class="platform-icon apple-icon">
                    <svg viewBox="0 0 24 24" fill="none" stroke="var(--primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"/>
                        <path d="M12 6v6l4 2"/>
                    </svg>
                </div>
                <h4>iPhone / iPad (iOS)</h4>
            </div>
            
            <div class="info-box">
                <div class="info-box-title">📱 Для тех, у кого Российский 🇷🇺 аккаунт Apple</div>
                <ul class="app-list">
                    <li><a href="#" class="setup-link">Скачиваем <strong>Karing</strong> → Скачать в AppStore</a></li>
                    <li><a href="/Tunless_Modern/karing.html" class="setup-link">👉 Инструкция по настройке Karing</a></li>
                    <li><a href="#" class="setup-link">или</a></li>
                    <li><a href="#" class="setup-link">Скачиваем <strong>Happ</strong> → Скачать в AppStore</a></li>
                </ul>
            </div>

            <div class="info-box">
                <div class="info-box-title">🌍 Для тех, кто хочет создать иностранный аккаунт</div>
                <p>Например, Американский 🇺🇸 и получить доступ к приложениям, удалённым из Российского 🇺 AppStore.</p>
                <p style="margin-top: 10px;"><em>Инструкция по созданию иностранного аккаунта скоро будет доступна.</em></p>
            </div>

            <div class="info-box recommendation">
                <div class="info-box-title">⭐ Приложения для тех, у кого есть иностранный аккаунт Apple</div>
                <ul class="app-list">
                    <li><a href="#" class="setup-link">Скачиваем <strong>Karing</strong> → Скачать в AppStore</a></li>
                    <li><a href="#" class="setup-link">Скачиваем <strong>V2Box</strong> → Скачать в AppStore</a></li>
                    <li><a href="#" class="setup-link">Скачиваем <strong>V2RayTUN</strong> → Скачать в AppStore</a></li>
                    <li><a href="#" class="setup-link">Скачиваем <strong>Hiddify</strong> → Скачать в AppStore</a></li>
                    <li><a href="#" class="setup-link">Скачиваем <strong>Happ</strong> → Скачать в AppStore</a></li>
                </ul>
                <p style="margin-top: 15px; font-size: 0.95em;"><strong>💡 Мы рекомендуем <strong>Karing</strong> или <strong>Hiddify</strong></strong>, т.к. в них, на данный момент, есть автоматическое переключение между протоколами.</p>
            </div>
        </div>

        <!-- Android -->
        <div class="platform-card">
            <div class="platform-header">
                <div class="platform-icon android-icon">
                    <svg viewBox="0 0 24 24" fill="none" stroke="var(--primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <rect x="4" y="8" width="16" height="12" rx="2"/>
                        <line x1="8" y1="4" x2="8" y2="8"/>
                        <line x1="12" y1="4" x2="12" y2="8"/>
                        <line x1="16" y1="4" x2="16" y2="8"/>
                    </svg>
                </div>
                <h4>Android / Android TV / Google TV</h4>
            </div>
            
            <p style="margin-bottom: 15px;"><strong>Тебе нужен:</strong></p>
            <ul class="app-list">
                <li><a href="#" class="setup-link"><strong>Karing</strong> (GitHub)</a></li>
                <li><a href="#" class="setup-link"><strong>V2RayTun</strong></a></li>
                <li><a href="#" class="setup-link"><strong>V2Box</strong></a></li>
                <li><a href="#" class="setup-link"><strong>Hiddify</strong></a></li>
                <li><a href="#" class="setup-link"><strong>Happ</strong></a></li>
            </ul>
        </div>

        <!-- Desktop -->
        <div class="platform-card">
            <div class="platform-header">
                <div class="platform-icon windows-icon">
                    <svg viewBox="0 0 24 24" fill="none" stroke="var(--primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
                        <line x1="8" y1="21" x2="16" y2="21"/>
                        <line x1="12" y1="17" x2="12" y2="21"/>
                    </svg>
                </div>
                <h4>Windows / Mac / Linux</h4>
            </div>
            
            <div class="info-box recommendation">
                <div class="info-box-title">⭐ Рекомендуем Karing</div>
                <p>Один из самых продвинутых с открытым исходным кодом и поддержкой самых современных протоколов и их автовыбором.</p>
                <p style="margin-top: 10px;"><a href="#" class="setup-link"> Скачать Karing (GitHub) Portable версия</a></p>
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
        </div>
    </div>
</div>

<!-- Step 2 -->
<div class="step-section">
    <div class="step-header">
        <div class="step-number">2</div>
        <h3>Скопируй свой ключ</h3>
    </div>
    
    <ol class="numbered-steps">
        <li>Зайди в бота, где купил ключ</li>
        <li>Нажми кнопку 🔑 <strong>Мои ключи</strong></li>
        <li>Выбери купленный ключ и нажми 📋 <strong>Получить ключ</strong></li>
        <li>Ключ (длинный код, начинающийся на <code>vless://</code>) скопируется в буфер обмена</li>
    </ol>

    <div class="key-box">
        vless://xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@server:port?encryption=none&security=tls&type=ws&host=example.com&path=%2Fpath#Tunless
    </div>
</div>

<!-- Step 3 -->
<div class="step-section">
    <div class="step-header">
        <div class="step-number">3</div>
        <h3>Запускаем!</h3>
    </div>
    
    <p style="font-size: 1.1em; margin-bottom: 30px;">Выбери свое устройство и делай как написано:</p>

    <div class="platforms-grid">
        <!-- iOS Karing -->
        <div class="platform-card">
            <div class="platform-header">
                <div class="platform-icon apple-icon">
                    <svg viewBox="0 0 24 24" fill="none" stroke="var(--primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"/>
                        <path d="M12 6v6l4 2"/>
                    </svg>
                </div>
                <h4>Для iPhone (Karing)</h4>
            </div>
            <p>У приложения одинаковый интерфейс на всех платформах. Всё будет знакомо!</p>
            <p style="margin-top: 15px;"><a href="/Tunless_Modern/karing.html" class="setup-link">👉 Подробная инструкция с картинками</a></p>
        </div>

        <!-- Android V2RayTun -->
        <div class="platform-card">
            <div class="platform-header">
                <div class="platform-icon android-icon">
                    <svg viewBox="0 0 24 24" fill="none" stroke="var(--primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <rect x="4" y="8" width="16" height="12" rx="2"/>
                        <line x1="8" y1="4" x2="8" y2="8"/>
                        <line x1="12" y1="4" x2="12" y2="8"/>
                        <line x1="16" y1="4" x2="16" y2="8"/>
                    </svg>
                </div>
                <h4>Для Android (V2RayTun)</h4>
            </div>
            <ol class="numbered-steps" style="margin: 15px 0;">
                <li>Открой скачанную программу</li>
                <li>Нажми на плюсик (+) в правом верхнем углу</li>
                <li>Выбери пункт "Импорт профиля из буфера обмена"</li>
                <li>Твой сервер появится в списке. Нажми на него, выбери протокол, чтобы он выделился (станет зеленым или серым)</li>
                <li>Нажми большую кнопку "Connect"</li>
            </ol>
        </div>

        <!-- Desktop Hiddify -->
        <div class="platform-card">
            <div class="platform-header">
                <div class="platform-icon windows-icon">
                    <svg viewBox="0 0 24 24" fill="none" stroke="var(--primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
                        <line x1="8" y1="21" x2="16" y2="21"/>
                        <line x1="12" y1="17" x2="12" y2="21"/>
                    </svg>
                </div>
                <h4>Для ПК (Hiddify)</h4>
            </div>
            <ol class="numbered-steps" style="margin: 15px 0;">
                <li>Открой Hiddify</li>
                <li>Нажми "Новый профиль" или большой плюс (+)</li>
                <li>Выбери "Добавить из буфера обмена"</li>
                <li>Нажми большую кнопку подключения по центру</li>
            </ol>
        </div>
    </div>
</div>

<!-- Success Box -->
<div class="success-box">
    <h3> Готово! Ты подключен к VPN!</h3>
    <p>Наслаждайся быстрым и безопасным интернетом!</p>
</div>

</div>
