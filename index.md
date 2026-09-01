---
layout: default
title: Tunless
---

<style>
/* Hero Section */
.hero-main {
    text-align: center;
    padding: 20px 20px 30px;
    margin-bottom: 40px;
}

.hero-main h1 {
    font-size: 2.8em;
    font-weight: 800;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 10px;
    animation: fadeInDown 0.8s ease;
}

.hero-main .subtitle {
    font-size: 1.2em;
    color: var(--text-light);
    opacity: 0.8;
    animation: fadeInUp 0.8s ease 0.2s both;
}

body.dark-mode .hero-main .subtitle {
    color: var(--text-dark);
}

/* Features Grid - 3 columns */
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

/* Контурные иконки - темные на светлой теме, белые на темной */
.feature-icon svg {
    width: 32px;
    height: 32px;
    stroke: var(--text-light);
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

/* CTA Section - без подложки */
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
    gap: 20px;
    justify-content: center;
    flex-wrap: wrap;
}

.cta-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    padding: 16px 32px;
    min-width: 250px;
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

/* Контурные иконки для кнопок */
.cta-button svg {
    width: 24px;
    height: 24px;
}

.cta-button:not(.secondary) svg {
    stroke: white;
    fill: none;
}

.cta-button.secondary svg {
    stroke: var(--primary);
    fill: none;
}

body.dark-mode .cta-button.secondary svg {
    stroke: #a5b4fc;
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
    
    .cta-section h3 {
        font-size: 1.6em;
    }
    
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

<!-- Hero Section -->
<div class="hero-main">
    <h1>Tunless</h1>
    <p class="subtitle">VPN подписка — быстро, безопасно и анонимно</p>
</div>

<!-- Features Grid - 3 блока -->
<div class="features-grid">
    <div class="feature-card">
        <div class="feature-icon">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/>
            </svg>
        </div>
        <h3>Современные решения</h3>
        <p>Высокоскоростные серверы с безлимитным трафиком. Протоколы VLESS/Hysteria для минимальной задержки. Trojan, xHTTP, WebSocket.</p>
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

<!-- CTA Section - без подложки -->
<div class="cta-section">
    <h3>Начни прямо сейчас</h3>
    <div class="cta-buttons">
        <a href="https://t.me/Tunless_bot" target="_blank" class="cta-button">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <path d="M21.198 2.433a2.242 2.242 0 0 0-1.022.215l-8.609 3.33c-2.068.8-4.133 1.598-5.724 2.21a405.15 405.15 0 0 1-2.849 1.09c-.42.147-.99.332-1.473.901-.728.939.193 1.745.927 2.177 1.61.949 3.285 1.985 4.596 2.797.405.25.77.468 1.091.658.344.204.635.37.868.493.468.246.666.32.56.32-.113 0-.276-.05-.47-.125-.39-.152-.858-.398-1.365-.688-1.013-.58-2.226-1.386-3.227-2.135-.495-.371-.945-.755-1.296-1.168-.35-.412-.61-.92-.533-1.528.06-.473.29-.868.603-1.178.313-.31.708-.517 1.128-.668.84-.302 1.836-.54 2.925-.768 1.637-.342 3.54-.638 5.198-.788.41-.037.808-.06 1.188-.067.38-.007.742.004 1.07.048.328.044.62.127.85.266.23.14.392.336.458.598.066.262.02.534-.12.768-.14.234-.366.41-.648.518-.282.108-.615.148-.973.11-.358-.038-.738-.148-1.12-.328-.764-.36-1.548-.92-2.25-1.58-.702-.66-1.298-1.42-1.698-2.18-.2-.38-.36-.78-.46-1.18-.1-.4-.14-.82-.1-1.22.04-.4.16-.78.36-1.12.2-.34.48-.62.82-.82.34-.2.72-.32 1.12-.36.4-.04.82 0 1.22.1.4.1.8.26 1.18.46z"/>
            </svg>
            Перейти в Telegram бота
        </a>
        <a href="/Tunless_Modern/setup.html" class="cta-button secondary">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="12" r="10"/>
                <path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/>
                <line x1="12" y1="17" x2="12.01" y2="17"/>
            </svg>
            Инструкция
        </a>
    </div>
</div>
