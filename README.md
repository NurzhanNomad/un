<!DOCTYPE html>
<html lang="ru" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title>UNAALINE CHECK</title>
    
    <!-- Стили -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #0F172A;
            --accent: #3498DB;  /* Глазурный синий */
            --surface: #1E293B;
            --text: #F8FAFC;
            --success: #2ECC71;
            --warning: #F1C40F;
            --error: #E74C3C;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
            font-family: 'Inter', sans-serif;
        }

        body {
            background: var(--primary);
            color: var(--text);
            min-height: 100vh;
            line-height: 1.5;
            -webkit-font-smoothing: antialiased;
        }

        /* Хедер с новым цветом */
        .app-header {
            background: var(--accent);  /* Основной цвет хедера */
            padding: 1.5rem 2rem;
            box-shadow: 0 4px 24px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .app-title {
            font-size: 1.8rem;
            font-weight: 700;
            color: white;
            letter-spacing: -0.5px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        /* Основной контент */
        .main-container {
            max-width: 800px;
            margin: 3rem auto;
            padding: 0 1.5rem;
        }

        /* Поле поиска */
        .search-container {
            position: relative;
            margin-bottom: 2.5rem;
        }

        .search-input {
            width: 100%;
            padding: 1.25rem 1.5rem;
            border: none;
            border-radius: 12px;
            background: rgba(255,255,255,0.05);
            color: var(--text);
            font-size: 1.1rem;
            padding-left: 4rem;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid rgba(255,255,255,0.1);
        }

        .search-input:focus {
            outline: none;
            box-shadow: 0 0 0 3px rgba(52,152,219,0.3);
            background: rgba(255,255,255,0.08);
        }

        .search-icon {
            position: absolute;
            left: 1.5rem;
            top: 50%;
            transform: translateY(-50%);
            color: white;
            font-size: 1.5rem;
            opacity: 0.8;
        }

        /* Карточка автомобиля */
        .vehicle-card {
            background: var(--surface);
            border-radius: 16px;
            padding: 2rem;
            margin: 1.5rem 0;
            box-shadow: 0 8px 32px rgba(0,0,0,0.2);
            opacity: 0;
            transform: translateY(20px);
            animation: cardEnter 0.6s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
        }

        @keyframes cardEnter {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .vehicle-header {
            display: flex;
            align-items: center;
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }

        .vehicle-icon {
            width: 56px;
            height: 56px;
            background: rgba(255,255,255,0.1);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            color: white;
        }

        .vehicle-title {
            font-size: 1.5rem;
            font-weight: 600;
            color: white;
        }

        /* Статус */
        .status-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.75rem;
            padding: 0.75rem 1.25rem;
            border-radius: 8px;
            font-weight: 500;
            margin: 1rem 0;
            background: rgba(46,204,113,0.1);
            color: var(--success);
        }

        /* Финансовая информация */
        .finance-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .finance-card {
            background: rgba(255,255,255,0.03);
            border-radius: 12px;
            padding: 1.5rem;
            position: relative;
            overflow: hidden;
        }

        .finance-label {
            font-size: 0.9rem;
            color: rgba(255,255,255,0.7);
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .finance-value {
            font-size: 1.4rem;
            font-weight: 600;
            color: white;
        }

        /* Адаптивность */
        @media (max-width: 768px) {
            .main-container {
                margin: 2rem auto;
                padding: 0 1rem;
            }

            .app-title {
                font-size: 1.4rem;
            }

            .search-input {
                padding: 1rem 1rem 1rem 3.5rem;
                font-size: 1rem;
            }

            .search-icon {
                left: 1rem;
            }

            .vehicle-header {
                flex-direction: column;
                align-items: flex-start;
            }
        }
    </style>
</head>
<body>
    <header class="app-header">
        <div class="header-content">
            <h1 class="app-title">UNAALINE CHECK</h1>
        </div>
    </header>

    <main class="main-container">
        <div class="search-container">
            <i class="fas fa-search search-icon"></i>
            <input 
                type="number"
                class="search-input"
                placeholder="Введите ID автомобиля"
                id="searchInput"
                inputmode="numeric"
                pattern="[0-9]*"
                autocomplete="off"
                autofocus
            >
        </div>
        
        <div id="result"></div>
    </main>

    <script>
        const CONFIG = {
            SPREADSHEET_ID: '19zA1fVAJXbcj6-v5Wc0J7Vui8Y0T2ovMiW4-LPuZKtY',
            API_KEY: 'AIzaSyAEhWnY3vrLXaev1Rfac6_pTEWOKKdwRqU',
            RANGE: encodeURIComponent('КУХНЯ!A:E')
        };

        let vehiclesData = [];
        
        async function initApp() {
            try {
                await loadData();
                setupEventListeners();
            } catch (error) {
                showMessage('Ошибка загрузки данных', 'error');
            }
        }

        async function loadData() {
            const url = `https://sheets.googleapis.com/v4/spreadsheets/${CONFIG.SPREADSHEET_ID}/values/${CONFIG.RANGE}?key=${CONFIG.API_KEY}&t=${Date.now()}`;
            const response = await fetch(url);
            
            if (!response.ok) throw new Error(`HTTP ${response.status}`);
            
            const data = await response.json();
            vehiclesData = data.values.slice(1).map(row => ({
                id: (row[0] || '').toString().replace(/\D/g, ''),
                brand: row[1] || 'Неизвестный автомобиль',
                status: row[2] || 'Статус не указан',
                paid: parseFloat(row[3]) || 0,
                remain: parseFloat(row[4]) || 0
            }));
        }

        function searchVehicle() {
            const searchId = document.getElementById('searchInput').value.replace(/\D/g, '');
            const resultContainer = document.getElementById('result');
            resultContainer.innerHTML = '';

            if (!searchId) return;

            const vehicle = vehiclesData.find(v => v.id === searchId);
            renderVehicleCard(vehicle, resultContainer);
        }

        function renderVehicleCard(vehicle, container) {
            if (!vehicle) {
                container.innerHTML = `
                    <div class="vehicle-card">
                        <div class="vehicle-header">
                            <div class="vehicle-icon">
                                <i class="fas fa-car-side"></i>
                            </div>
                            <div>
                                <h2 class="vehicle-title">Автомобиль не найден</h2>
                                <p>Проверьте правильность ID</p>
                            </div>
                        </div>
                    </div>
                `;
                return;
            }

            const statusConfig = {
                'актуален': { color: 'var(--success)', icon: 'check-circle' },
                'на рассмотрении': { color: 'var(--warning)', icon: 'clock' },
                'продан': { color: 'var(--error)', icon: 'times-circle' }
            };

            const status = statusConfig[vehicle.status.toLowerCase()] || { color: '#666', icon: 'question-circle' };
            const total = vehicle.paid + vehicle.remain;

            container.innerHTML = `
                <div class="vehicle-card">
                    <div class="vehicle-header">
                        <div class="vehicle-icon">
                            <i class="fas fa-car"></i>
                        </div>
                        <div>
                            <h2 class="vehicle-title">${vehicle.brand}</h2>
                            <div class="status-badge" style="background: ${status.color}1a; color: ${status.color}">
                                <i class="fas fa-${status.icon}"></i>
                                ${vehicle.status}
                            </div>
                        </div>
                    </div>
                    
                    <div class="finance-grid">
                        <div class="finance-card">
                            <div class="finance-label">
                                <i class="fas fa-wallet"></i>
                                Оплачено
                            </div>
                            <div class="finance-value" style="color: ${status.color}">
                                ${vehicle.paid.toLocaleString()} СОМ
                            </div>
                        </div>
                        
                        <div class="finance-card">
                            <div class="finance-label">
                                <i class="fas fa-hourglass-half"></i>
                                Остаток
                            </div>
                            <div class="finance-value">
                                ${vehicle.remain.toLocaleString()} СОМ
                            </div>
                        </div>
                        
                        <div class="finance-card">
                            <div class="finance-label">
                                <i class="fas fa-chart-pie"></i>
                                Всего
                            </div>
                            <div class="finance-value">
                                ${total.toLocaleString()} СОМ
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        function setupEventListeners() {
            const input = document.getElementById('searchInput');
            input.addEventListener('input', searchVehicle);
            input.addEventListener('keypress', e => {
                if (e.key === 'Enter') searchVehicle();
            });
        }

        // Инициализация
        window.addEventListener('DOMContentLoaded', initApp);
    </script>
</body>
</html>
