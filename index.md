<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ page.title | default: site.title }} - Tunless</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #667eea;
            --primary-dark: #764ba2;
            --bg-light: #f5f7fa;
            --bg-dark: #0f0f1e;
            --text-light: #2d3748;
            --text-dark: #e2e8f0;
            --card-light: #ffffff;
            --card-dark: #1a1a2e;
            --accent: #25D366;
            --warning: #f59e0b;
            --success: #10b981;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--bg-light);
            color: var(--text-light);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            min-height: 100vh;
            overflow-x: hidden;
        }

        body.dark-mode {
            background: var(--bg-dark);
            color: var(--text-dark);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Navigation Bar */
        nav {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            padding: 12px 30px;
            border-radius: 15px;
            margin-bottom: 40px;
            display: flex;
            align-items: center;
            gap: 20px;
            flex-wrap: wrap;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.25);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 20px;
            z-index: 100;
            animation: slideDown 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .nav-logo {
            height: 45px;
            width: auto;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }

        .nav-links {
            display: flex;
            gap: 5px;
            flex-wrap: wrap;
            flex: 1;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: 600;
            padding: 10px 18px;
            border-radius: 10px;
            transition: all 0.3s ease;
            position: relative;
            font-size: 0.95em;
        }

        nav a::before {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 2px;
            background: white;
            transform: translateX(-50%);
            transition: width 0.3s ease;
        }

        nav a:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: translateY(-3px);
        }

        nav a:hover::before {
            width: 70%;
        }

        nav a.active {
            background: rgba(255, 255, 255, 0.25);
        }

        .theme-toggle {
            background: transparent;
            border: 2px solid rgba(255, 255, 255, 0.5);
            color: white;
            padding: 8px 14px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.3em;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 44px;
            height: 44px;
        }

        .theme-toggle:hover {
            border-color: rgba(255, 255, 255, 0.8);
            background: rgba(255, 255, 255, 0.1);
            transform: scale(1.08);
        }

        .theme-toggle:active {
            transform: scale(0.95);
        }

        /* SVG Icons - контурные */
        .sun-icon, .moon-icon {
            width: 24px;
            height: 24px;
            transition: opacity 0.3s ease;
            fill: none;
            stroke: currentColor;
            stroke-width: 2;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .sun-icon {
            opacity: 1;
        }

        .sun-icon.hidden {
            opacity: 0;
            position: absolute;
        }

        .moon-icon {
            opacity: 0;
            position: absolute;
        }

        .moon-icon.visible {
            opacity: 1;
            position: static;
        }

        /* Content */
        .content {
            line-height: 1.9;
            animation: fadeInUp 0.8s ease 0.3s both;
        }

        .content h2 {
            color: var(--primary);
            margin-top: 50px;
            margin-bottom: 30px;
            font-size: 2.2em;
            position: relative;
            padding-bottom: 20px;
            font-weight: 700;
        }

        .content h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 80px;
            height: 5px;
            background: linear-gradient(90deg, var(--primary), var(--primary-dark));
            border-radius: 3px;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
        }

        .content h3 {
            color: var(--primary-dark);
            margin-top: 30px;
            margin-bottom: 20px;
            font-size: 1.6em;
            font-weight: 600;
        }

        .content ul, .content ol {
            margin-left: 30px;
            margin-bottom: 25px;
        }

        .content li {
            margin-bottom: 15px;
            transition: all 0.3s ease;
            padding-left: 10px;
        }

        .content li:hover {
            padding-left: 20px;
            color: var(--primary);
        }

        .content a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            position: relative;
            transition: all 0.3s ease;
            padding-bottom: 2px;
        }

        .content a::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s ease;
        }

        .content a:hover {
            color: var(--primary-dark);
        }

        .content a:hover::after {
            width: 100%;
        }

        /* Feature Cards - 3 в ряд */
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
            font-size: 1.5em;
        }

        /* Контурные иконки */
        .feature-icon svg {
            width: 32px;
            height: 32px;
            fill: none;
            stroke: var(--text-light);
            stroke-width: 2;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        body.dark-mode .feature-icon svg {
            stroke: var(--text-dark);
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
            padding: 40px 20px;
            margin: 50px 0;
        }

        .cta-section h2 {
            font-size: 2.5em;
            font-weight: 800;
            margin-bottom: 30px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
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
            gap: 12px;
            padding: 16px 32px;
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
        }

        /* Footer */
        .footer {
            margin-top: 80px;
            text-align: center;
            padding: 40px 20px;
            border-top: 2px solid #e0e0e0;
            animation: fadeInUp 0.8s ease 0.5s both;
        }

        body.dark-mode .footer {
            border-top-color: #444;
        }

        .footer p {
            margin: 10px 0;
            font-weight: 500;
        }

        .footer a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 700;
            transition: all 0.3s ease;
        }

        .footer a:hover {
            color: var(--primary-dark);
            transform: translateY(-2px);
        }

        /* Animations */
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

        /* Responsive */
        @media (max-width: 768px) {
            .container {
                padding: 15px;
            }

            nav {
                flex-direction: column;
                align-items: stretch;
                position: static;
            }

            .nav-logo {
                margin: 0 auto;
            }

            .nav-links {
                width: 100%;
                justify-content: space-around;
            }

            .theme-toggle {
                width: 100%;
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

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 12px;
        }

        ::-webkit-scrollbar-track {
            background: var(--bg-light);
        }

        body.dark-mode ::-webkit-scrollbar-track {
            background: var(--bg-dark);
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            border-radius: 6px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--primary-dark);
        }
    </style>
</head>
<body>
    <div class="container">
        <nav>
            <img src="{{ site.baseurl }}/assets/images/logo_640x640.GIF" alt="Tunless Logo" class="nav-logo">
            <div class="nav-links">
                {% for link in site.nav_links %}
                    <a href="{{ link.url }}" {% if page.url == link.url %}class="active"{% endif %}>{{ link.title }}</a>
                {% endfor %}
            </div>
            <button class="theme-toggle" id="themeToggle" title="Переключить тему">
                <svg class="sun-icon" viewBox="0 0 24 24">
                    <circle cx="12" cy="12" r="5"></circle>
                    <line x1="12" y1="1" x2="12" y2="3"></line>
                    <line x1="12" y1="21" x2="12" y2="23"></line>
                    <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
                    <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
                    <line x1="1" y1="12" x2="3" y2="12"></line>
                    <line x1="21" y1="12" x2="23" y2="12"></line>
                    <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
                    <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
                </svg>
                <svg class="moon-icon" viewBox="0 0 24 24">
                    <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
                </svg>
            </button>
        </nav>

        <div class="content">
            {{ content }}
        </div>

        {% if page.url == '/' %}
        <!-- Feature Cards - 3 карточки -->
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">
                    <svg viewBox="0 0 24 24">
                        <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon>
                    </svg>
                </div>
                <h3>Современные решения</h3>
                <p>Высокоскоростные серверы с безлимитным трафиком. Протоколы VLESS/Hysteria для минимальной задержки.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">
                    <svg viewBox="0 0 24 24">
                        <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
                    </svg>
                </div>
                <h3>Быстрое, безопасное и анонимное соединение</h3>
                <p>Современное шифрование и защита данных. Никаких логов вашей активности.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">
                    <svg viewBox="0 0 24 24">
                        <circle cx="12" cy="12" r="10"></circle>
                        <line x1="2" y1="12" x2="22" y2="12"></line>
                        <path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"></path>
                    </svg>
                </div>
                <h3>Несколько локаций</h3>
                <p>Выбирайте из множества серверов и стран лучший для себя. Оптимальная маршрутизация.</p>
            </div>
        </div>

        <!-- CTA Section - без подложки -->
        <div class="cta-section">
            <h2>Начни прямо сейчас</h2>
            <div class="cta-buttons">
                <a href="https://t.me/Tunless_bot" target="_blank" class="cta-button">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M21.198 2.433a2.242 2.242 0 0 0-1.022.215l-8.609 3.33c-2.068.8-4.133 1.598-5.724 2.21a405.15 405.15 0 0 1-2.849 1.09c-.42.147-.99.332-1.473.901-.728.939.193 1.745.927 2.177 1.61.949 3.285 1.985 4.596 2.797.405.25.77.468 1.091.658.344.204.635.37.868.493.468.246.666.32.56.32-.113 0-.276-.05-.47-.125-.39-.152-.858-.398-1.365-.688-1.013-.58-2.226-1.386-3.227-2.135-.495-.371-.945-.755-1.296-1.168-.35-.412-.61-.92-.533-1.528.06-.473.29-.868.603-1.178.313-.31.708-.517 1.128-.668.84-.302 1.836-.54 2.925-.768 1.637-.342 3.54-.638 5.198-.788.41-.037.808-.06 1.188-.067.38-.007.742.004 1.07.048.328.044.62.127.85.266.23.14.392.336.458.598.066.262.02.534-.12.768-.14.234-.366.41-.648.518-.282.108-.615.148-.973.11-.358-.038-.738-.148-1.12-.328-.764-.36-1.548-.92-2.25-1.58-.702-.66-1.298-1.42-1.698-2.18-.2-.38-.36-.78-.46-1.18-.1-.4-.14-.82-.1-1.22.04-.4.16-.78.36-1.12.2-.34.48-.62.82-.82.34-.2.72-.32 1.12-.36.4-.04.82 0 1.22.1.4.1.8.26 1.18.46z"/>
                    </svg>
                    Перейти в Telegram бота
                </a>
                <a href="/Tunless_Modern/setup.html" class="cta-button secondary">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <circle cx="12" cy="12" r="10"></circle>
                        <polyline points="12 6 12 12 16 14"></polyline>
                    </svg>
                    Инструкция
                </a>
            </div>
        </div>
        {% endif %}

        <div class="footer">
            <p>© <script>document.write(new Date().getFullYear())</script> <strong>Tunless</strong>. Все права защищены.</p>
            <p style="font-size: 0.95em; margin-top: 15px; opacity: 0.8;">⚡ Быстро • 🔒 Безопасно • 👻 Анонимно</p>
        </div>
    </div>

    <script>
        // Dark Mode Toggle
        const themeToggle = document.getElementById('themeToggle');
        const sunIcon = document.querySelector('.sun-icon');
        const moonIcon = document.querySelector('.moon-icon');

        // Проверяем сохраненное предпочтение
        const isDarkMode = localStorage.getItem('darkMode') === 'true';
        if (isDarkMode) {
            document.body.classList.add('dark-mode');
            sunIcon.classList.add('hidden');
            moonIcon.classList.add('visible');
        }

        // Переключение темы
        themeToggle.addEventListener('click', () => {
            const isDark = document.body.classList.toggle('dark-mode');
            localStorage.setItem('darkMode', isDark);
            
            if (isDark) {
                sunIcon.classList.add('hidden');
                moonIcon.classList.add('visible');
            } else {
                sunIcon.classList.remove('hidden');
                moonIcon.classList.remove('visible');
            }
            
            // Анимация поворота
            themeToggle.style.transform = 'scale(0.9) rotate(-180deg)';
            setTimeout(() => {
                themeToggle.style.transform = 'scale(1) rotate(0deg)';
            }, 300);
        });

        // Установка активной ссылки
        document.querySelectorAll('.nav-links a').forEach(link => {
            if (link.getAttribute('href') === window.location.pathname) {
                link.classList.add('active');
            }
        });

        // Smooth scroll для якорей
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
</body>
</html>
