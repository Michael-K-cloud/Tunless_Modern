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
    border: 1px solid rgba(102, 126, 234, 0.3); /* Усилена граница */
    box-shadow: 0 4px 20px rgba(102, 126, 234, 0.1); /* Добавлена тень для светлой темы */
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    animation: fadeInUp 0.6s ease;
    position: relative;
    overflow: hidden;
}

body.dark-mode .feature-card {
    background: var(--card-dark);
    border-color: rgba(102, 126, 234, 0.2);
    box-shadow: none; /* На темной теме тень не нужна */
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

/* Иконки в 3-х блоках: цвет заголовка на светлой, белый на темной */
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

/* Кнопки с градиентным фоном для максимального контраста */
.cta-button {
    display: flex !important;
    align-items: center !important;
    justify-content: center !important;
    gap: 12px;
    padding: 18px 30px !important;
    min-width: 280px;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    color: #ffffff !important; /* Белый текст для читаемости */
    text-decoration: none !important;
    border-radius: 16px;
    font-weight: 700;
    font-size: 1.1em;
    line-height: 1.2 !important;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    border: 2px solid transparent;
    box-shadow: 0 8px 25px rgba(102, 126, 234, 0.3); /* Тень для объема */
    position: relative;
    overflow: hidden;
    box-sizing: border-box;
}

body.dark-mode .cta-button {
    background: var(--card-dark);
    color: #ffffff;
    border: 1px solid rgba(102, 126, 234, 0.3);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

.cta-button:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 35px rgba(102, 126, 234, 0.4);
}

body.dark-mode .cta-button:hover {
    box-shadow: 0 8px 25px rgba(102, 126, 234, 0.3);
}

/* Иконки в кнопках всегда белые (так как фон кнопки темный/градиентный) */
.cta-button svg {
    width: 24px;
    height: 24px;
    stroke: #ffffff;
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
   
