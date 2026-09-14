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

.platform-card {
    background: var(--card-light);
    border-radius: 16px;
    padding: 20px;
    border: 1px solid rgba(102, 126, 234, 0.3);
    box-shadow: 0 4px 20px rgba(102, 126, 234, 0.1);
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    cursor: pointer;
    position: relative;
    overflow: hidden;
    min-height: 130px;
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

/* Active card - full width */
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

/* Держим полную ширину, пока карточка сворачивается */
.platform-card.collapsing {
    grid-column: 1 / -1;
}

.platform-header {
    display: flex;
    align-items: flex-start;
    gap: 15px;
    margin-bottom: 0;
}

.header-text {
    min-width: 0;
}

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
    max-height: 8000px;
    opacity: 1;
    margin-top: 30px;
    padding-top: 30px;
    border-top: 2px solid rgba(102, 126, 234, 0.2);
}

/* App tiles: светлая тема — как карточки главной; тёмная — #25294A */
.apps-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    margin: 25px 0;
}

.app-tile {
    background: var(--card-light);
    border-radius: 16px;
    padding: 25px 15px;
    border: 1px solid rgba(102, 126, 234, 0.3);
    box-shadow: 0 4px 20px rgba(102, 126, 234, 0.1);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    position: relative;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 12px;
    text-align: center;
}

body.dark-mode .app-tile {
    background: #25294A;
    border-color: rgba(255, 255, 255, 0.18);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
}

.app-tile::before {
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

.app-tile:hover::before {
    transform: scaleX(1);
}

.app-tile:hover {
    transform: translateY(-8px);
    box-shadow: 0 20px 40px rgba(102, 126, 234, 0.2);
}

body.dark-mode .app-tile:hover {
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
}

.app-icon {
    width: 90px;
    height: 90px;
    border-radius: 20px;
    object-fit: contain;
    flex-shrink: 0;
    background: #ffffff;
    padding: 2px;
    box-sizing: border-box;
}

.app-name {
    font-weight: 700;
    font-size: 1.15em;
    line-height: 1.3;
    color: var(--text-light);
}

body.dark-mode .app-name {
    color: var(--text-dark);
}

/* Кнопки плиток: одинаковый размер, изоляция от глобального .content a */
.app-btn {
    display: flex !important;
    align-items: center !important;
    justify-content: center !important;
    gap: 8px;
    width: 100%;
    max-width: 180px;
    padding: 10px 16px !important;
    background: linear-gradient(135deg, var(--primary), var(--primary-dark)) !important;
    color: #ffffff !important;
    text-decoration: none !important;
    border-radius: 10px;
    font-weight: 600;
    font-size: 0.95em;
    line-height: 1.2 !important;
    margin: 0 !important;
    box-sizing: border-box;
    transition: all 0.3s ease;
}

.app-btn::after {
    display: none !important;
}

.app-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(102, 126, 234, 0.35);
}

.app-btn svg {
    width: 16px;
    height: 16px;
    stroke: #ffffff !important;
    fill: none;
    stroke-width: 2;
    flex-shrink: 0;
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

/* Кнопка "Готово": внизу контента каждой раскрытой карточки */
.done-btn {
    display: block;
    margin: 25px auto 0;
    padding: 16px 70px;
    background: var(--card-light);
    border: 1px solid rgba(102, 126, 234, 0.3);
    border-radius: 12px;
    color: var(--text-light);
    font-family: inherit;
    font-size: 1.2em;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
}

body.dark-mode .done-btn {
    background: #25294A;
    border-color: rgba(255, 255, 255, 0.18);
    color: var(--text-dark);
}

.done-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
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

    .platform-header {
        flex-direction: column;
        align-items: center;
        text-align: center;
        gap: 10px;
    }

    .apps-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 15px;
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
                <svg viewBox="1 1 22 22" stroke-linecap="round" stroke-linejoin="round" style="stroke-width: 1.375">
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
            <h4 class="section-header">Как пользоваться ботом</h4>
            <ol class="numbered-steps">
                <li>Открой бота <a href="https://t.me/Tunless_bot" target="_blank" class="setup-link">@Tunless_bot</a></li>
                <li>Нажми <strong>«Start»</strong> — откроется главное меню с кнопками
                    <div class="screenshot-placeholder">📸 Место для скриншота: главное меню бота</div>
                </li>
                <li>Выбери тариф и оплати — ключ появится в твоём аккаунте сразу после оплаты
                    <div class="screenshot-placeholder">📸 Место для скриншота: выбор тарифа и оплата</div>
                </li>
                <li>Нажми 🔑 <strong>«Мои ключи»</strong>, выбери ключ и нажми 📋 <strong>«Получить ключ»</strong> — он скопируется в буфер обмена
                    <div class="screenshot-placeholder">📸 Место для скриншота: кнопка «Получить ключ»</div>
                </li>
                <li>В этом же меню можно продлевать подписку и смотреть остаток трафика</li>
            </ol>
            <div class="info-box">
                <div class="info-box-title">💡 Что дальше</div>
                <p>Скопированный ключ вставь в приложение своего устройства — вернись к карточке <strong>iOS</strong>, <strong>Android</strong> или <strong>PC</strong> выше и выполни Шаг 3.</p>
            </div>
            <button class="done-btn" onclick="event.stopPropagation(); closeAccordion()">Готово</button>
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
            <h4 class="section-header">Шаг 1: Скачай приложение</h4>
            
            <div class="apps-grid">
                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/karing_logo.png" alt="Karing">
                    <div class="app-name">Karing</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="/Tunless_Modern/karing.html" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/happ_logo.png" alt="Happ">
                    <div class="app-name">Happ</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/hiddify_logo.png" alt="Hiddify">
                    <div class="app-name">Hiddify</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/v2box_logo.png" alt="V2Box">
                    <div class="app-name">V2Box</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>
            </div>

            <h4 class="section-header">Шаг 2: Скопируй свой ключ</h4>
            <ol class="numbered-steps">
                <li>Зайди в бота, где купил ключ</li>
                <li>Нажми кнопку 🔑 <strong>Мои ключи</strong></li>
                <li>Выбери купленный ключ и нажми 📋 <strong>Получить ключ</strong></li>
                <li>Ключ (длинный код, начинающийся на <code>vless://</code>) скопируется в буфер обмена</li>
            </ol>

            <div class="key-box">
                vless://xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@server:port?encryption=none&security=tls&type=ws&host=example.com&path=%2Fpath#Tunless
            </div>

            <h4 class="section-header">Шаг 3: Запускаем!</h4>
            <div class="info-box">
                <div class="info-box-title">Для iOS (Karing)</div>
                <ol class="numbered-steps" style="margin: 15px 0;">
                    <li>Запустите Karing</li>
                    <li>Выберите регион — для России выберите “Russia”</li>
                    <li>Настройте роутинг — российские сайты будут работать без VPN</li>
                    <li>Включите режим “Новичка” — скроет настройки для “Экспертов”</li>
                    <li>Добавьте профиль — вставьте ключ из буфера обмена</li>
                    <li>Подключитесь — нажмите кнопку подключения со щитом</li>
                </ol>
            </div>
            <button class="done-btn" onclick="event.stopPropagation(); closeAccordion()">Готово</button>
        </div>
    </div>

    <!-- Android Card (4 плитки) -->
    <div class="platform-card" onclick="toggleAccordion(this)">
        <div class="close-btn" onclick="event.stopPropagation(); closeAccordion()">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
        </div>
        <div class="platform-header">
            <div class="platform-icon">
                <svg viewBox="3 2.5 18 18.5" stroke-linecap="round" stroke-linejoin="round" style="stroke-width: 1.16">
                    <path d="M7 10a5 5 0 0 1 10 0z"/>
                    <line x1="8.5" y1="3.5" x2="10" y2="6"/>
                    <line x1="15.5" y1="3.5" x2="14" y2="6"/>
                    <line x1="10" y1="7.5" x2="10.01" y2="7.5"/>
                    <line x1="14" y1="7.5" x2="14.01" y2="7.5"/>
                    <rect x="7" y="12" width="10" height="8" rx="2"/>
                    <line x1="4" y1="12.5" x2="4" y2="17.5"/>
                    <line x1="20" y1="12.5" x2="20" y2="17.5"/>
                </svg>
            </div>
            <div class="header-text">
                <h3 class="platform-title">Android</h3>
                <p class="platform-subtitle">Android / Android TV / Google TV</p>
            </div>
        </div>
        
        <div class="accordion-content">
            <h4 class="section-header">Шаг 1: Скачай приложение</h4>
            
            <div class="apps-grid">
                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/karing_logo.png" alt="Karing">
                    <div class="app-name">Karing</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="/Tunless_Modern/karing.html" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/v2raytun_logo.png" alt="V2RayTun">
                    <div class="app-name">V2RayTun</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/hiddify_logo.png" alt="Hiddify">
                    <div class="app-name">Hiddify</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/happ_logo.png" alt="Happ">
                    <div class="app-name">Happ</div>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>
            </div>

            <h4 class="section-header">Шаг 2: Скопируй свой ключ</h4>
            <ol class="numbered-steps">
                <li>Зайди в бота, где купил ключ</li>
                <li>Нажми кнопку 🔑 <strong>Мои ключи</strong></li>
                <li>Выбери купленный ключ и нажми 📋 <strong>Получить ключ</strong></li>
                <li>Ключ (длинный код, начинающийся на <code>vless://</code>) скопируется в буфер обмена</li>
            </ol>

            <div class="key-box">
                vless://xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@server:port?encryption=none&security=tls&type=ws&host=example.com&path=%2Fpath#Tunless
            </div>

            <h4 class="section-header">Шаг 3: Запускаем!</h4>
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
            <button class="done-btn" onclick="event.stopPropagation(); closeAccordion()">Готово</button>
        </div>
    </div>

    <!-- PC Card: 3 кнопки Скачать (Windows / Mac / Linux) с иконками ОС -->
    <div class="platform-card" onclick="toggleAccordion(this)">
        <div class="close-btn" onclick="event.stopPropagation(); closeAccordion()">
            <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
        </div>
        <div class="platform-header">
            <div class="platform-icon">
                <svg viewBox="2 2 20 20" stroke-linecap="round" stroke-linejoin="round" style="stroke-width: 1.25">
                    <rect x="3" y="3" width="8" height="8"/>
                    <rect x="13" y="3" width="8" height="8"/>
                    <rect x="3" y="13" width="8" height="8"/>
                    <rect x="13" y="13" width="8" height="8"/>
                </svg>
            </div>
            <div class="header-text">
                <h3 class="platform-title">PC</h3>
                <p class="platform-subtitle">Windows / Mac / Linux</p>
            </div>
        </div>
        
        <div class="accordion-content">
            <h4 class="section-header">Шаг 1: Скачай приложение</h4>
            
            <div class="apps-grid">
                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/karing_logo.png" alt="Karing">
                    <div class="app-name">Karing</div>
                    <a href="https://github.com/KaringX/karing/releases/download/v1.2.25.2802/karing_1.2.25.2802_windows_x64.zip" target="_blank" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="8" height="8"/><rect x="13" y="3" width="8" height="8"/><rect x="3" y="13" width="8" height="8"/><rect x="13" y="13" width="8" height="8"/></svg>
                        <span>Скачать .zip</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path stroke-width="1.5" d="M12.152 6.896c-.948 0-2.415-1.078-3.96-1.04-2.04.027-3.91 1.183-4.961 3.014-2.117 3.675-.546 9.103 1.519 12.09 1.013 1.454 2.208 3.09 3.792 3.039 1.52-.065 2.09-.987 3.935-.987 1.831 0 2.35.987 3.96.948 1.637-.026 2.676-1.48 3.676-2.948 1.156-1.688 1.636-3.325 1.662-3.415-.039-.013-3.182-1.221-3.22-4.857-.026-3.04 2.48-4.494 2.597-4.559-1.429-2.09-3.623-2.324-4.39-2.376-2-.156-3.675 1.09-4.61 1.09zM15.53 3.83c.843-1.012 1.4-2.427 1.245-3.83-1.207.052-2.662.805-3.532 1.818-.78.896-1.454 2.338-1.273 3.714 1.338.104 2.715-.688 3.559-1.701"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2.5c-2 0-3.3 1.5-3.3 3.5 0 1.4-.4 2.5-1.1 3.7-1.1 1.8-1.9 3.6-1.9 5.4 0 2.9 2.3 4.9 5.3 4.9h2c3 0 5.3-2 5.3-4.9 0-1.8-.8-3.6-1.9-5.4-.7-1.2-1.1-2.3-1.1-3.7 0-2-1.3-3.5-3.3-3.5z"/><ellipse cx="12" cy="14.5" rx="3.2" ry="4"/><line x1="10.6" y1="6" x2="10.61" y2="6"/><line x1="13.4" y1="6" x2="13.41" y2="6"/><path d="M10.8 7.6h2.4l-1.2 1.2z"/><path d="M9 20l-1.8 1.5"/><path d="M15 20l1.8 1.5"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="/Tunless_Modern/karing.html" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/hiddify_logo.png" alt="Hiddify">
                    <div class="app-name">Hiddify</div>
                    <a href="https://github.com/hiddify/hiddify-app/releases/download/v4.1.1/Hiddify-Windows-Portable-x64.zip" target="_blank" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="8" height="8"/><rect x="13" y="3" width="8" height="8"/><rect x="3" y="13" width="8" height="8"/><rect x="13" y="13" width="8" height="8"/></svg>
                        <span>Скачать .zip</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path stroke-width="1.5" d="M12.152 6.896c-.948 0-2.415-1.078-3.96-1.04-2.04.027-3.91 1.183-4.961 3.014-2.117 3.675-.546 9.103 1.519 12.09 1.013 1.454 2.208 3.09 3.792 3.039 1.52-.065 2.09-.987 3.935-.987 1.831 0 2.35.987 3.96.948 1.637-.026 2.676-1.48 3.676-2.948 1.156-1.688 1.636-3.325 1.662-3.415-.039-.013-3.182-1.221-3.22-4.857-.026-3.04 2.48-4.494 2.597-4.559-1.429-2.09-3.623-2.324-4.39-2.376-2-.156-3.675 1.09-4.61 1.09zM15.53 3.83c.843-1.012 1.4-2.427 1.245-3.83-1.207.052-2.662.805-3.532 1.818-.78.896-1.454 2.338-1.273 3.714 1.338.104 2.715-.688 3.559-1.701"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2.5c-2 0-3.3 1.5-3.3 3.5 0 1.4-.4 2.5-1.1 3.7-1.1 1.8-1.9 3.6-1.9 5.4 0 2.9 2.3 4.9 5.3 4.9h2c3 0 5.3-2 5.3-4.9 0-1.8-.8-3.6-1.9-5.4-.7-1.2-1.1-2.3-1.1-3.7 0-2-1.3-3.5-3.3-3.5z"/><ellipse cx="12" cy="14.5" rx="3.2" ry="4"/><line x1="10.6" y1="6" x2="10.61" y2="6"/><line x1="13.4" y1="6" x2="13.41" y2="6"/><path d="M10.8 7.6h2.4l-1.2 1.2z"/><path d="M9 20l-1.8 1.5"/><path d="M15 20l1.8 1.5"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/happ_logo.png" alt="Happ">
                    <div class="app-name">Happ</div>
                    <a href="https://github.com/Happ-proxy/happ-desktop/releases/download/4.2.1/setup-Happ.x64.exe" target="_blank" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="8" height="8"/><rect x="13" y="3" width="8" height="8"/><rect x="3" y="13" width="8" height="8"/><rect x="13" y="13" width="8" height="8"/></svg>
                        <span>Скачать .exe</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path stroke-width="1.5" d="M12.152 6.896c-.948 0-2.415-1.078-3.96-1.04-2.04.027-3.91 1.183-4.961 3.014-2.117 3.675-.546 9.103 1.519 12.09 1.013 1.454 2.208 3.09 3.792 3.039 1.52-.065 2.09-.987 3.935-.987 1.831 0 2.35.987 3.96.948 1.637-.026 2.676-1.48 3.676-2.948 1.156-1.688 1.636-3.325 1.662-3.415-.039-.013-3.182-1.221-3.22-4.857-.026-3.04 2.48-4.494 2.597-4.559-1.429-2.09-3.623-2.324-4.39-2.376-2-.156-3.675 1.09-4.61 1.09zM15.53 3.83c.843-1.012 1.4-2.427 1.245-3.83-1.207.052-2.662.805-3.532 1.818-.78.896-1.454 2.338-1.273 3.714 1.338.104 2.715-.688 3.559-1.701"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2.5c-2 0-3.3 1.5-3.3 3.5 0 1.4-.4 2.5-1.1 3.7-1.1 1.8-1.9 3.6-1.9 5.4 0 2.9 2.3 4.9 5.3 4.9h2c3 0 5.3-2 5.3-4.9 0-1.8-.8-3.6-1.9-5.4-.7-1.2-1.1-2.3-1.1-3.7 0-2-1.3-3.5-3.3-3.5z"/><ellipse cx="12" cy="14.5" rx="3.2" ry="4"/><line x1="10.6" y1="6" x2="10.61" y2="6"/><line x1="13.4" y1="6" x2="13.41" y2="6"/><path d="M10.8 7.6h2.4l-1.2 1.2z"/><path d="M9 20l-1.8 1.5"/><path d="M15 20l1.8 1.5"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>

                <div class="app-tile">
                    <img class="app-icon" src="/Tunless_Modern/assets/images/v2rayn_logo.png" alt="V2RayN">
                    <div class="app-name">V2RayN</div>
                    <a href="https://github.com/2dust/v2rayN/releases/download/7.25.1/v2rayN-windows-64.zip" target="_blank" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="8" height="8"/><rect x="13" y="3" width="8" height="8"/><rect x="3" y="13" width="8" height="8"/><rect x="13" y="13" width="8" height="8"/></svg>
                        <span>Скачать .zip</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path stroke-width="1.5" d="M12.152 6.896c-.948 0-2.415-1.078-3.96-1.04-2.04.027-3.91 1.183-4.961 3.014-2.117 3.675-.546 9.103 1.519 12.09 1.013 1.454 2.208 3.09 3.792 3.039 1.52-.065 2.09-.987 3.935-.987 1.831 0 2.35.987 3.96.948 1.637-.026 2.676-1.48 3.676-2.948 1.156-1.688 1.636-3.325 1.662-3.415-.039-.013-3.182-1.221-3.22-4.857-.026-3.04 2.48-4.494 2.597-4.559-1.429-2.09-3.623-2.324-4.39-2.376-2-.156-3.675 1.09-4.61 1.09zM15.53 3.83c.843-1.012 1.4-2.427 1.245-3.83-1.207.052-2.662.805-3.532 1.818-.78.896-1.454 2.338-1.273 3.714 1.338.104 2.715-.688 3.559-1.701"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2.5c-2 0-3.3 1.5-3.3 3.5 0 1.4-.4 2.5-1.1 3.7-1.1 1.8-1.9 3.6-1.9 5.4 0 2.9 2.3 4.9 5.3 4.9h2c3 0 5.3-2 5.3-4.9 0-1.8-.8-3.6-1.9-5.4-.7-1.2-1.1-2.3-1.1-3.7 0-2-1.3-3.5-3.3-3.5z"/><ellipse cx="12" cy="14.5" rx="3.2" ry="4"/><line x1="10.6" y1="6" x2="10.61" y2="6"/><line x1="13.4" y1="6" x2="13.41" y2="6"/><path d="M10.8 7.6h2.4l-1.2 1.2z"/><path d="M9 20l-1.8 1.5"/><path d="M15 20l1.8 1.5"/></svg>
                        <span>Скачать</span>
                    </a>
                    <a href="#" class="app-btn">
                        <svg viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
                        <span>Инструкция</span>
                    </a>
                </div>
            </div>

            <h4 class="section-header">Шаг 2: Скопируй свой ключ</h4>
            <ol class="numbered-steps">
                <li>Зайди в бота, где купил ключ</li>
                <li>Нажми кнопку 🔑 <strong>Мои ключи</strong></li>
                <li>Выбери купленный ключ и нажми 📋 <strong>Получить ключ</strong></li>
                <li>Ключ (длинный код, начинающийся на <code>vless://</code>) скопируется в буфер обмена</li>
            </ol>

            <div class="key-box">
                vless://xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx@server:port?encryption=none&security=tls&type=ws&host=example.com&path=%2Fpath#Tunless
            </div>

            <h4 class="section-header">Шаг 3: Запускаем!</h4>
            <div class="info-box">
                <div class="info-box-title">Для ПК (Hiddify)</div>
                <ol class="numbered-steps" style="margin: 15px 0;">
                    <li>Открой Hiddify</li>
                    <li>Нажми "Новый профиль" или большой плюс (+)</li>
                    <li>Выбери "Добавить из буфера обмена"</li>
                    <li>Нажми большую кнопку подключения по центру</li>
                </ol>
            </div>
            <button class="done-btn" onclick="event.stopPropagation(); closeAccordion()">Готово</button>
        </div>
    </div>
</div>

<script>
// Тапы по ссылкам и тексту ВНУТРИ открытой карточки не сворачивают её
document.querySelectorAll('.accordion-content').forEach(function (el) {
    el.addEventListener('click', function (e) {
        e.stopPropagation();
    });
});

function collapseCard(card) {
    const grid = document.getElementById('platformsGrid');
    card.classList.remove('active');
    card.classList.add('collapsing');
    grid.classList.add('has-active');
    setTimeout(function () {
        card.classList.remove('collapsing');
        if (!document.querySelector('.platform-card.active') &&
            !document.querySelector('.platform-card.collapsing')) {
            grid.classList.remove('has-active');
        }
    }, 450);
}

function toggleAccordion(card) {
    const grid = document.getElementById('platformsGrid');
    if (!card.classList.contains('active')) {
        document.querySelectorAll('.platform-card.active').forEach(function (c) {
            if (c !== card) collapseCard(c);
        });
        card.classList.remove('collapsing');
        card.classList.add('active');
        grid.classList.add('has-active');
    } else {
        collapseCard(card);
    }
}

function closeAccordion() {
    const openCard = document.querySelector('.platform-card.active');
    if (openCard) {
        collapseCard(openCard);
    } else {
        document.getElementById('platformsGrid').classList.remove('has-active');
    }
}
</script>
