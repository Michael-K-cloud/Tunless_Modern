---
layout: default
title: Инструкция по настройке
---

<style>
/* === SETUP ACCORDION STYLES === */
/* H2 не стилизуем: глобальный .content h2::after уже даёт черту снизу слева */

/* Platform Cards Grid (4 карточки) */
.platforms-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 25px;
    margin: 0 0 30px 0;
    position: relative;
}

/* Контент прижат к верху: верхние края иконок совпадают во всех карточках ряда */
.platform-card {
    background: var(--card-light);
    border-radius: 16px;
    padding: 25px;
    border: 1px solid rgba(102, 126, 234, 0.3);
    box-shadow: 0 4px 20px rgba(102, 126, 234, 0.1);
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    cursor: pointer;
    position: relative;
    overflow: hidden;
    min-height: 180px;
    display: flex;
    flex-direction: column;
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

/* Active card - full width (без order: карточка не прыгает на первое место) */
.platform-card.active {
    grid-column: 1 / -1;
    border-color: var(--primary);
    box-shadow: 0 20px 50px rgba(102, 126, 234, 0.4);
    z-index: 10;
}

/* Hide other cards when one is active or collapsing */
.platforms-grid.has-active .platform-card:not(.active):not(.collapsing) {
    display: none;
}

/* Держим полную ширину, пока карточка сворачивается (чинит "2 столбика") */
.platform-card.collapsing {
    grid-column: 1 / -1;
}

/* Шапка: верх иконки и верх заголовка на одной линии */
.platform-header {
    display: flex;
    align-items: flex-start;
    gap: 15px;
    margin-bottom: 15px;
}

.header-text {
    min-width: 0;
}

/* Иконка = высота двух строк текста справа */
.platform-icon {
    width: 50px;
    height: 50px;
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

/* Специфичность повышена: глобальный .content h3 иначе перебивает margin и font-weight */
.platform-card .platform-title {
    font-size: 1.4em;
    font-weight: 700;
    color: var(--primary);
    margin: 0;
    line-height: 1.1;
}

.platform-subtitle {
    font-size: 0.95em;
    color: var(--text-light);
    margin-top: 5px;
    line-height: 1.4;
}

body.dark-mode .platform-subtitle {
    color: var(--text-dark);
}

/* Close button: только у раскрытой карточки, в правом верхнем углу */
.close-btn {
    position: absolute;
    top: 15px;
    right: 15px;
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

/* Links - изоляция от глобальных стилей .content a */
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

/* Section Headers */
.section-header {
    font-size: 1.4em;
    font-weight: 700;
    color: var(--primary);
    margin: 25px 0 15px;
    padding-bottom: 10px;
    border-bottom: 2px solid rgba(102, 126, 234, 0.2);
}

/* Screenshots */
.screenshot {
    display: block;
    width: 100%;
    border-radius: 12px;
    border: 1px solid rgba(102, 126, 234, 0.3);
    margin: 15px 0;
}

.screenshot-placeholder {
    border: 2px dashed rgba(102, 126, 234, 0.4);
    border-radius: 12px;
    padding: 25px 15px;
    text-align: center;
    color: var(--text-light);
    background: rgba(102, 126, 234, 0.05);
    margin: 15px 0 5px;
    font-size: 0.95em;
    line-height: 1.6;
}

body.dark-mode .screenshot-placeholder {
    color: var(--text-dark);
    background: rgba(102, 126, 234, 0.1);
}

/* Back instruction (соседний селектор + : блок лежит ПОСЛЕ grid, а не внутри) */
.back-instruction {
    text-align: center;
    padding: 20px;
    margin: 20px 0;
    background: rgba(102, 126, 234, 0.08);
    border-radius: 12px;
    display: none;
}

.platforms-grid.has-active + .back-instruction {
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

/* === ПЕРЕБИВАНИЕ ГЛОБАЛЬНЫХ СТИЛЕЙ _layouts/default.html === */
.content .app-list,
.content .numbered-steps {
    margin-left: 0;
    margin-bottom: 15px;
}

.content .app-list li {
    margin-bottom: 0;
}

.content .app-list li:hover {
    padding-left: 0;
    color: inherit;
}

.content .numbered-steps li:hover {
    padding-left: 60px;
    color: inherit;
}

/* Responsive */
/* Планшет/телефон (портрет): 2 карточки в ряд, сжимаются под экран */
@media (max-width: 1100px) {
    .platforms-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 20px;
    }
}

@media (max-width: 768px) {
    .platform-card { padding: 20px; }
    .platform-card .platform-title { font-size: 1.3em; }
    .platform-icon { width: 48px; height: 48px; }

    /* Узкие карточки: колонка — иконка сверху по центру, под ней сиреневый заголовок, ниже светлый подзаголовок */
    .platform-header {
        flex-direction: column;
        align-items: center;
        text-align: center;
        gap: 10px;
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
    .content .numbered-steps li:hover { padding-left: 55px; }
}
</style>

<!-- H2 с чертой слева (черту даёт глобальный .content h2::after) -->
<h2>Настройка подключения</h2>

<div class="platforms-grid" id="platformsGrid">
    <!-- Telegram Card -->
    <div class="platform-card" onclick="toggleAccordion(this)">
        <div class="close-btn" onclick="event.stopPropagation(); closeAccordion()">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
        </div>
        <div class="platform-header">
            <div class="platform-icon">
                <!-- Контурная иконка Telegram (та же, что на кнопке главной страницы); плотный viewBox = иконка во весь блок -->
                <svg viewBox="1 1 22 22" stroke-linecap="round" stroke-linejoin="round">
                    <line x1="22" y1="2" x2="11" y2="13"></line>
                    <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
                </svg>
            </div>
            <div class="header-text">
                <h3 class="platform-title">Telegram</h3>
                <p class="platform-subtitle">Бот: ключи и подписка</p>
            </div>
        </div>
        
        <div class="accordion-content">
            <h4 class="section-header">🤖 Как пользоваться ботом</h4>
            <ol class="numbered-steps">
                <li>Открой бота <a href="https://t.me/Tunless_bot" target="_blank" class="setup-link">@Tunless_bot</a>
                </li>
                <li>Нажми <strong>«Start»</strong> — откроется главное меню с кнопками
                    <div class="screenshot-placeholder">📸 Место для скриншота: главное меню бота<br><!-- Замени на: <img class="screenshot" src="/Tunless_Modern/assets/images/bot_menu.png" alt="Главное меню бота"> --></div>
                </li>
                <li>Выбери тариф и оплати — ключ появится в твоём аккаунте сразу после оплаты
                    <div class="screenshot-placeholder">📸 Место для скриншота: выбор тарифа и оплата<br><!-- Замени на: <img class="screenshot" src="/Tunless_Modern/assets/images/bot_buy.png" alt="Выбор тарифа и оплата"> --></div>
                </li>
                <li>Нажми 🔑 <strong>«Мои ключи»</strong>, выбери ключ и нажми 📋 <strong>«Получить ключ»</strong> — он скопируется в буфер обмена
                    <div class="screenshot-placeholder">📸 Место для скриншота: кнопка «Получить ключ»<br><!-- Замени на: <img class="screenshot" src="/Tunless_Modern/assets/images/bot_key.png" alt="Кнопка Получить ключ"> --></div>
                </li>
                <li>В этом же меню можно продлевать подписку и смотреть остаток трафика</li>
            </ol>
            <div class="info-box">
                <div class="info-box-title">💡 Что дальше</div>
                <p>Скопированный ключ вставь в приложение своего устройства — вернись к карточке <strong>iOS</strong>, <strong>Android</strong> или <strong>PC</strong> выше и выполни Шаг 3.</p>
            </div>
        </div>
    </div>

    <!-- iOS Card -->
    <div class="platform-card" onclick="toggleAccordion(this)">
        <div class="close-btn" onclick="event.stopPropagation(); closeAccordion()">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
        </div>
        <div class="platform-header">
            <div class="platform-icon">
                <!-- Контурный логотип Apple -->
                <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                    <path stroke-width="1.5" d="M12.152 6.896c-.948 0-2.415-1.078-3.96-1.04-2.04.027-3.91 1.183-4.961 3.014-2.117 3.675-.546 9.103 1.519 12.09 1.013 1.454 2.208 3.09 3.792 3.039 1.52-.065 2.09-.987 3.935-.987 1.831 0 2.35.987 3.96.948 1.637-.026 2.676-1.48 3.676-2.948 1.156-1.688 1.636-3.325 1.662-3.415-.039-.013-3.182-1.221-3.22-4.857-.026-3.04 2.48-4.494 2.597-4.559-1.429-2.09-3.623-2.324-4.39-2.376-2-.156-3.675 1.09-4.61 1.09zM15.53 3.83c.843-1.012 1.4-2.427 1.245-3.83-1.207.052-2.662.805-3.532 1.818-.78.896-1.454 2.338-1.273 3.714 1.338.104 2.715-.688 3.559-1.701"/>
                </svg>
            </div>
            <div class="header-text">
                <h3 class="platform-title">iOS</h3>
                <p class="platform-subtitle">iPhone / iPad</p>
            </div>
        </div>
        
        <div class="accordion-content">
            <h4 class="section-header">📱 Шаг 1: Скачай приложение</h4>
            
            <div class="info-box">
                <div class="info-box-title">📱 Для тех, у кого Российский 🇷 аккаунт Apple</div>
                <ul class="app-list">
                    <li>Скачиваем <strong>Karing</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                    <li><a href="/Tunless_Modern/karing.html" class="setup-link">👉 Инструкция по настройке Karing</a></li>
                    <li>или</li>
                    <li>Скачиваем <strong>Happ</strong> → <a href="#" class="setup-link">Скачать в AppStore</a></li>
                </ul>
            </div>

            <div class="info-box">
                <div class="info-box-title">🌍 Для тех, кто хочет создать иностранный аккаунт</div>
                <p>Например, Американский 🇺🇸 и получить доступ к приложениям, удалённым из Российского 🇷 AppStore.</p>
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
                <p style="margin-top: 15px; font-size: 0.95em;"><strong>💡 Мы рекомендуем Karing или Hiddify</strong>, т.к. в них, на данный момент, есть автоматическое переключение между протоколами
