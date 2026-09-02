---
layout: default
title: Добро пожаловать в Tunless
subtitle: Привычный доступ к любимым приложениям!
---

<style>
/* Features Grid */
.features-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 25px;
    margin: 40px 0;
}

.feature-card {
    background: var(--card-light);
    border-radius: 16px;
    padding: 30px;
    border: 1px solid rgba(102, 126, 234, 0.1);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    animation: fadeInUp 0.6s ease;
    position: relative;
    overflow: hidden;
}

body.dark-mode .feature-card {
    background: var(--card-dark);
    border-color: rgba(102, 126, 234, 0.2);
}

.feature-card::before {
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

.feature-card:hover::before { 
    transform: scaleX(1); 
}

.feature-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 20px 40px rgba(102, 126, 234, 0.2);
}

.feature-icon {
    width: 50px;
    height: 50px;
    margin-bottom: 20px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Контурные иконки в 3-х блоках: цвет заголовка на светлой, белый на темной */
.feature-icon svg {
    width: 32px;
    height: 32px;
    stroke: var(--primary);
    stroke-width: 2;
    fill: none;
}

body.dark-mode .feature-icon svg { 
    stroke: #ffffff; 
}

.feature-card h3 {
    font-size: 1.3em;
    margin-bottom: 12px;
    color: var(--primary);
    font-weight: 700;
}

.feature-card p {
    line-height: 1.7;
    opacity: 0.9;
}

/* CTA Section */
.cta-section {
    text-align: center;
    padding: 40px 30px 20px;
    margin: 40px 0;
}

.cta-section h3 {
    font-size: 2em;
    font-weight: 800;
    margin-bottom: 25px;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: pulse 2s infinite;
}

.cta-buttons {
    display: flex;
    gap: 25px;
    justify-content: center;
    flex-wrap: wrap;
    max-width: 700px;
    margin: 0 auto;
}

/* Кнопки в стиле карточек */
.cta-button {
    display: flex !important;
    align-items: center !important;
    justify-content: center !important;
    gap: 12px;
    padding: 18px 30px !important;
    min-width: 280px;
    background: var(--card-light);
    
    /* Текст как цвет заголовка (градиент) на светлой теме */
    background-image: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    color: transparent;
    
    text-decoration: none !important;
    border-radius: 16px;
    font-weight: 700;
    font-size: 1.1em;
    line-height: 1.2 !important;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    border: 1px solid rgba(102, 126, 234, 0.1);
    position: relative;
    overflow: hidden;
    box-sizing: border-box;
}

body.dark-mode .cta-button {
    background: var(--card-dark);
    /* На темной теме текст белый, без градиента */
    background-image: none;
    -webkit-background-clip: unset;
    -webkit-text-fill-color: #ffffff;
    background-clip: unset;
    color: #ffffff;
    border-color: rgba(102, 126, 234, 0.2);
}

.cta-button::before {
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

.cta-button:hover::before { 
    transform: scaleX(1); 
}

.cta-button:hover {
    transform: translateY(-8px);
    box-shadow: 0 20px 40px rgba(102, 126, 234, 0.2);
}

/* Контурные иконки в кнопках: цвет заголовка на светлой, белый на темной */
.cta-button svg {
    width: 24px;
    height: 24px;
    stroke: var(--primary);
    fill: none;
    stroke-width: 2;
    stroke-linecap: round;
    stroke-linejoin: round;
    flex-shrink: 0;
    margin: 0 !important;
    padding: 0 !important;
    display: block;
    vertical-align: middle !important;
}

body.dark-mode .cta-button svg { 
    stroke: #ffffff; 
}

.cta-button span {
    display: inline-block;
    line-height: 1.2 !important;
    margin: 0 !important;
    padding: 0 !important;
    vertical-align: middle !important;
}

/* СБРОС КОНФЛИКТНЫХ СТИЛЕЙ ОТ DEFAULT.HTML */
.cta-button::after {
    display: none !important;
}

.cta-button * {
    padding-bottom: 0 !important;
    margin-bottom: 0 !important;
}

@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.02); }
}

@media (max-width: 768px) {
    .features-grid {
        grid-template-columns: 1fr;
        gap: 20px;
    }
    .feature-card { padding: 25px; }
    .cta-section h3 { font-size: 1.6em; }
    .cta-buttons {
        flex-direction: column;
        align-items: center;
    }
    .cta-button {
        width: 100%;
        max-width: 300px;
        min-width: auto;
    }
}
</style>

<!-- Features Grid — 3 блока -->
<div class="features-grid">
    <div class="feature-card">
        <div class="feature-icon">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/>
            </svg>
        </div>
        <h3>Современные решения</h3>
        <p>Высокоскоростные серверы с безлимитным трафиком. Протоколы VLESS, Hysteria, Trojan, xHTTP, WebSocket для минимальной задержки.</p>
    </div>
    
    <div class="feature-card">
        <div class="feature-icon">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
            </svg>
        </div>
        <h3>Быстрое и безопасное соединение</h3>
        <p>Современное шифрование и защита данных. Никаких логов вашей активности. Полная анонимность в интернете.</p>
    </div>
    
    <div class="feature-card">
        <div class="feature-icon">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
                <line x1="8" y1="21" x2="16" y2="21"/>
                <line x1="12" y1="17" x2="12" y2="21"/>
            </svg>
        </div>
        <h3>Управление в боте</h3>
        <p>Привяжите Telegram — и управляйте подпиской, продлевайте и просматривайте трафик в удобном Telegram боте.</p>
    </div>
</div>

<!-- CTA Section -->
<div class="cta-section">
    <h3>Начни прямо сейчас</h3>
    <div class="cta-buttons">
        <a href="https://t.me/Tunless_bot" target="_blank" class="cta-button">
            <svg viewBox="0 0 24 24">
                <line x1="22" y1="2" x2="11" y2="13"></line>
                <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
            </svg>
            <span>Перейти в Telegram бота</span>
        </a>
        <a href="/Tunless_Modern/setup.html" class="cta-button">
            <svg viewBox="0 0 24 24">
                <circle cx="12" cy="12" r="10"></circle>
                <path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"></path>
                <line x1="12" y1="17" x2="12.01" y2="17"></line>
            </svg>
            <span>Инструкция</span>
        </a>
    </div>
</div>
