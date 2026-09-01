---
layout: default
title: Добро пожаловать в Tunless
subtitle: VPN подписка - быстро, безопасно и анонимно
---

<style>
/* Hero Section */
.hero-main {
    text-align: center;
    padding: 60px 20px 40px;
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
    border-radius: 20px;
    margin-bottom: 50px;
}

.hero-main h1 {
    font-size: 3em;
    font-weight: 800;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 15px;
    animation: fadeInDown 0.8s ease;
}

.hero-main .subtitle {
    font-size: 1.3em;
    color: var(--text-light);
    opacity: 0.8;
    animation: fadeInUp 0.8s ease 0.2s both;
}

body.dark-mode .hero-main .subtitle {
    color: var(--text-dark);
}

/* Features Grid */
.features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 25px;
    margin: 50px 0;
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
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: white;
    font-size: 1.5em;
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
    padding: 60px 30px;
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.15) 0%, rgba(118, 75, 162, 0.15) 100%);
    border-radius: 20px;
    margin: 50px 0;
    border: 2px solid rgba(102, 126, 234, 0.2);
}

.cta-section h2 {
    font-size: 2.5em;
    font-weight: 800;
    margin-bottom: 30px;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: pulse 2s infinite;
}

.cta-buttons {
    display: flex;
    gap: 20px;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
}

.cta-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    padding: 16px 32px;
    min-height: 56px;
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: white;
    text-decoration: none;
    border-radius: 12px;
    font-weight: 700;
    font-size: 1.1em;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
    border: 2px solid transparent;
}

.cta-button:hover {
    transform: translateY(-4px);
    box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
    border-color: rgba(255, 255, 255, 0.3);
}

.cta-button.secondary {
    background: transparent;
    border: 2px solid var(--primary);
    color: var(--primary);
}

body.dark-mode .cta-button.secondary {
    color: #a5b4fc;
    border-color: #a5b4fc;
}

.cta-button.secondary:hover {
    background: rgba(102, 126, 234, 0.1);
}

.cta-button svg {
    width: 24px;
    height: 24px;
    flex-shrink: 0;
}

/* Animations */
@keyframes fadeInDown {
    from {
        opacity: 0;
        transform: translateY(-30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes pulse {
    0%, 100% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.02);
    }
}

/* Responsive */
@media (max-width: 768px) {
    .hero-main h1 {
        font-size: 2em;
    }

    .hero-main .subtitle {
        font-size: 1.1em;
    }

    .features-grid {
        grid-template-columns: 1fr;
        gap: 20px;
    }

    .feature-card {
        padding: 25px;
    }

    .cta-section h2 {
        font-size: 1.8em;
    }

    .cta-buttons {
        flex-direction: column;
        align-items: center;
    }

    .cta-button {
        width: 100%;
        max-width: 300px;
        justify-content: center;
    }
}
</style>

<!-- Hero Section -->
<div class="hero-main">
    <h1>Добро пожаловать в Tunless</h1>
    <p class="subtitle">VPN подписка — быстро, безопасно и анонимно</p>
</div>

<!-- Features Grid -->
<div class="features-grid">
    <div class="feature-card">
        <div class="feature-icon">⚡</div>
        <h3>Современные решения</h3>
        <p>Высокоскоростные серверы с безлимитным трафиком. Протоколы VLESS/Hysteria для минимальной задержки. Добавь Trojan, xHTTP, WebSocket.</p>
    </div>

    <div class="feature-card">
        <div class="feature-icon">🔓</div>
        <h3>Лёгкий доступ</h3>
        <p>Простая авторизация по email. Не нужен Telegram. Введите email, получите код — и получите ключ за 30 секунд.</p>
    </div>

    <div class="feature-card">
        <div class="feature-icon">🌍</div>
        <h3>Несколько локаций</h3>
        <p>Выбирайте из множества серверов и стран лучший для себя. Оптимальная маршрутизация для максимальной скорости.</p>
    </div>

    <div class="feature-card">
        <div class="feature-icon">🔒</div>
        <h3>Быстрое, безопасное и анонимное соединение</h3>
        <p>Современное шифрование и защита данных. Никаких логов вашей активности. Полная анонимность в интернете.</p>
    </div>

    <div class="feature-card">
        <div class="feature-icon">♾️</div>
        <h3>Без логов, без ограничений</h3>
        <p>Никаких ограничений по трафику и скорости. Мы не ведём логи и не храним данные о вашей активности.</p>
    </div>

    <div class="feature-card">
        <div class="feature-icon"></div>
        <h3>Управление в боте</h3>
        <p>Привяжите Telegram — и управляйте подпиской, продлевайте и просматривайте трафик в удобном Telegram боте.</p>
    </div>
</div>

<!-- CTA Section -->
<div class="cta-section">
    <h2>Начни прямо сейчас</h2>
    <div class="cta-buttons">
        <a href="https://t.me/Tunless_bot" target="_blank" class="cta-button">
            <svg viewBox="0 0 24 24" fill="currentColor">
                <path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/>
            </svg>
            Перейти в Telegram бота
        </a>
        <a href="/Tunless_Modern/setup.html" class="cta-button secondary">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M2 12s3-7 10-7 10 7 10 7-3 7-10 7-10-7-10-7Z"/>
                <circle cx="12" cy="12" r="3"/>
            </svg>
            Инструкция
        </a>
    </div>
</div>
