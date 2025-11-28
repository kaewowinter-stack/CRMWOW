# CRMWOW
CRM DE CLIENTES WORLD OF WONRDES - W.O.W INTERNATIONAL
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reporte de Gestión CRM - Noviembre 2025</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #fdfbf7; color: #4b5563; }
        .chart-container { 
            position: relative; 
            width: 100%; 
            max-width: 600px; 
            margin-left: auto; 
            margin-right: auto; 
            height: 300px; 
            max-height: 400px; 
        }
        @media (min-width: 768px) { .chart-container { height: 350px; } }
        
        .card-hover:hover { transform: translateY(-2px); box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05); }
        .transition-all-300 { transition: all 0.3s ease; }
        
        /* Custom Scrollbar for clean look */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        ::-webkit-scrollbar-thumb { background: #d1d5db; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #9ca3af; }

        .tab-active { border-bottom: 2px solid #b45309; color: #78350f; font-weight: 600; }
        .tab-inactive { color: #6b7280; font-weight: 400; }
        .tab-inactive:hover { color: #374151; }
    </style>
    <!-- Chosen Palette: Warm Neutrals (Sand/Beige base) with Earthy Accents (Terracotta, Sage, Slate) -->
    <!-- Application Structure Plan: 
         1. Header: Context (Date, Recipient).
         2. KPI Dashboard: Immediate view of "Wins" vs "Issues".
         3. Navigation Tabs: Logical separation of "Successes" (Money), "Roadblocks" (Issues), and "Prospects" (Future).
         4. Content Area: Dynamic injection based on tabs.
            - Success View: Grid of cards for converted clients + Charts.
            - Alert View: Categorized lists (Stock vs Mgmt vs Negative).
            - Prospect View: List of ongoing opportunities.
         5. Footer: Summary of immediate actions.
         Why? This separates the "Good News" (Revenue) from the "Work to Do" (Alerts), preventing cognitive overload.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
</head>
<body class="bg-[#fdfbf7] min-h-screen flex flex-col">

    <!-- Header -->
    <header class="bg-white shadow-sm border-b border-[#e5e7eb] sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
            <div>
                <h1 class="text-2xl font-bold text-[#292524]">Reporte de Gestión CRM</h1>
                <p class="text-sm text-[#78716c]">Fecha de Corte: 28 Noviembre 2025 | Para: Señorita Belén</p>
            </div>
            <div class="hidden md:block">
                <span class="px-3 py-1 rounded-full text-xs font-medium bg-green-100 text-green-800">Estado: Avance Positivo</span>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 w-full">

        <!-- Intro Section -->
        <section class="mb-8">
            <p class="text-lg text-[#57534e] max-w-4xl">
                Bienvenido al tablero interactivo del CRM. Este reporte destaca la evolución de clientes clave, cuantifica las nuevas conversiones ("Grandes Victorias") e identifica los cuellos de botella operativos que requieren atención inmediata. Utilice las pestañas a continuación para navegar entre las ventas cerradas, las alertas críticas y los prospectos en seguimiento.
            </p>
        </section>

        <!-- KPI Cards -->
        <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
            <div class="bg-white p-6 rounded-lg shadow-sm border border-[#e7e5e4] border-l-4 border-l-emerald-500">
                <p class="text-sm font-medium text-gray-500">Nuevas Ventas Totales</p>
                <p class="text-3xl font-bold text-gray-900" id="kpi-total-sales">$0.00</p>
                <p class="text-xs text-emerald-600 mt-1">Calculado de "Nuevos Convertidos"</p>
            </div>
            <div class="bg-white p-6 rounded-lg shadow-sm border border-[#e7e5e4] border-l-4 border-l-blue-500">
                <p class="text-sm font-medium text-gray-500">Clientes Convertidos</p>
                <p class="text-3xl font-bold text-gray-900" id="kpi-converted-count">0</p>
                <p class="text-xs text-gray-400 mt-1">Nuevas captaciones exitosas</p>
            </div>
            <div class="bg-white p-6 rounded-lg shadow-sm border border-[#e7e5e4] border-l-4 border-l-amber-500">
                <p class="text-sm font-medium text-gray-500">Alertas de Stock</p>
                <p class="text-3xl font-bold text-gray-900">1</p>
                <p class="text-xs text-amber-600 mt-1">Venta detenida (Gladys L.)</p>
            </div>
            <div class="bg-white p-6 rounded-lg shadow-sm border border-[#e7e5e4] border-l-4 border-l-red-500">
                <p class="text-sm font-medium text-gray-500">Riesgo / Lista Negra</p>
                <p class="text-3xl font-bold text-gray-900">3</p>
                <p class="text-xs text-red-600 mt-1">Clientes bloqueados/negativos</p>
            </div>
        </div>

        <!-- Navigation Tabs -->
        <div class="border-b border-gray-200 mb-6">
            <nav class="-mb-px flex space-x-8" aria-label="Tabs">
                <button onclick="switchTab('victorias')" id="tab-victorias" class="tab-active whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm transition-colors duration-200">
                    🏆 Grandes Victorias
                </button>
                <button onclick="switchTab('alertas')" id="tab-alertas" class="tab-inactive whitespace-nowrap py-4 px-1 border-b-2 border-transparent font-medium text-sm transition-colors duration-200">
                    ⚠️ Alertas y Bloqueos
                </button>
                <button onclick="switchTab('prospectos')" id="tab-prospectos" class="tab-inactive whitespace-nowrap py-4 px-1 border-b-2 border-transparent font-medium text-sm transition-colors duration-200">
                    ⏳ Seguimiento y Prospectos
                </button>
                <button onclick="switchTab('analisis')" id="tab-analisis" class="tab-inactive whitespace-nowrap py-4 px-1 border-b-2 border-transparent font-medium text-sm transition-colors duration-200">
                    📈 Análisis Visual
                </button>
            </nav>
        </div>

        <!-- Content Views -->
        <div id="content-area" class="min-h-[400px]">
            <!-- Dynamic Content Injected Here -->
        </div>

    </main>

    <!-- Footer -->
    <footer class="bg-white border-t border-gray-200 mt-auto">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <p class="text-sm text-gray-500">Sistema de Reportes CRM v2.0</p>
                <div class="flex space-x-4 mt-4 md:mt-0">
                    <span class="text-xs text-gray-400">Generado con base en datos del 28/11/2025</span>
                </div>
            </div>
        </div>
    </footer>

    <!-- Visualization & Content Choices: 
         - Stats Dashboard: Inform goal. Shows aggregated value of the provided report data.
         - Charts (Chart.js): Compare goal. Visualizing sales by vendor and client to identify top performers instantly. No SVG used.
         - Interactive Cards: Inform/Organize goal. Each client is a card with specific details (Action, Justification).
         - Color Coding: Green for sales, Red for blockers, Yellow for warnings.
    -->
    
    <script>
        // --- Data Source (Based on Reporte Oficial) ---
        const reportData = {
            converted: [
                { client: "LILIA MORA", vendor: "Elías Riascos", amount: 2523.96, justification: "¡Excelente Gestión! Venta de alto volumen.", action: "Iniciar plan de fidelización inmediato. Asegurar reposición.", priority: "High" },
                { client: "SUPERCONFITES", vendor: "Ricardo Figueroa", amount: 1332.16, justification: "Cliente Grande. Apertura exitosa.", action: "Solicitar feedback sobre rotación en 15 días.", priority: "High" },
                { client: "WILLIAM HIDALGO", vendor: "Juan Carlos Uzuay", amount: 1103.46, justification: "Venta cerrada bajo 'Riesgo Propio'.", action: "URGENTE: Validar comportamiento de pago para formalizar crédito.", priority: "Critical" },
                { client: "CÉSAR SÁNCHEZ CAMPOZANO", vendor: "Ricardo Figueroa", amount: 1051.41, justification: "Conversión sólida.", action: "Ofrecer mix de productos complementarios.", priority: "Medium" },
                { client: "COMATICO", vendor: "Ricardo Figueroa", amount: 952.26, justification: "Venta concretada.", action: "Programar visita posventa para asegurar exhibición.", priority: "Medium" },
                { client: "MERCY PICHUCHO TIPANLUISA", vendor: "Juan Carlos Uzuay", amount: 712.60, justification: "Revisión para ampliación de cupo.", action: "Aprobar ampliación para no frenar recompra.", priority: "Medium" },
                { client: "ZAIDA MANCACELA", vendor: "Elías Riascos", amount: 607.50, justification: "Se vendió pero no se firmó solicitud de crédito.", action: "ALERTA: Volver para firmar documentos o habrá problemas de cobro.", priority: "Critical" },
                { client: "POSLIGUA PINO JUAN FERNANDO", vendor: "Ricardo Figueroa", amount: 579.71, justification: "Venta concretada.", action: "Seguimiento estándar.", priority: "Low" },
                { client: "DIANA ILLESCAS RODRÍGUEZ", vendor: "Elías Riascos", amount: 573.95, justification: "Venta inicial exitosa. Conversión lograda.", action: "Seguimiento de satisfacción y reposición.", priority: "Medium" },
                { client: "MARISTELA SARABIA CARVAJAL", vendor: "Juan Carlos Uzuay", amount: 516.05, justification: "Cambio de estatus: De 'Contactado' a venta real.", action: "Confirmar satisfacción con el pedido.", priority: "Medium" },
                { client: "GALTOR SUPERMERCADO", vendor: "Manuel Gonzabay", amount: 502.20, justification: "Error CRM: Figura visitado pero generó pedido.", action: "Cambiar estado a CONVERTIDO. Motivar aumento de ticket.", priority: "Low" }
            ],
            alerts: [
                { client: "GLADYS LÓPEZ BARRERA", type: "Stock/Logística", status: "Visitado", detail: "Interesada en Orient, Cheesecake, Delinut, Manela 30g que NO DISPONEMOS.", action: "NO VISITAR hasta tener stock. Notificar llegada." },
                { client: "YAGUANA RICARDO", type: "Gestión/Ruta", status: "Riesgo", detail: "Se perdió contacto por desvinculación de vendedor J. Cuellar.", action: "Reasignación inmediata a Ricardo o Elías esta semana." },
                { client: "NUBE ROJAS LEÓN", type: "Gestión/Tiempo", status: "Sin Venta", detail: "No se concretó primera venta ($0). Vendedor no llegó por tiempo.", action: "Reprogramar con prioridad. Asegurar cierre." },
                { client: "INÉS MEJÍA PINEDA", type: "Gestión/Ruta", status: "Visitado", detail: "Cliente de Loja sin visita.", action: "Manuel Gonzabay DEBE agendar visita en próxima ruta." },
                { client: "LUIS ALBERTO DOMÍNGUEZ", type: "Cierre Definitivo", status: "Delincuente", detail: "Cliente moroso/conflictivo.", action: "LISTA NEGRA. Bloquear en sistema." },
                { client: "JOHANNA UGUÑA URGILÉS", type: "Cierre Definitivo", status: "Rechazo", detail: "Solo consumo masivo, no confitería.", action: "Sacar de ruta." },
                { client: "ADELA CORONEL REAL", type: "Cierre Definitivo", status: "Rechazo", detail: "Solo trabaja con marcas grandes.", action: "Sacar de ruta." }
            ],
            prospects: [
                { client: "MISKY PLANET", vendor: "Elías", status: "Enfriándose", detail: "No contesta llamadas.", action: "Visita presencial obligatoria o mensaje directo." },
                { client: "JOSÉ AGUALONGO SIZA", vendor: "J.C. Uzuay", status: "Negociación", detail: "Pide mejor precio en Chupiwom/Masmelo.", action: "Aprobar precios especiales YA para cerrar." },
                { client: "LUIS MARCATOMA GUARACA", vendor: "J.C. Uzuay", status: "Stock Lleno", detail: "Indica que ya tiene producto.", action: "Visitar en 15 días." },
                { client: "MARCATOMA GUARACA L.B.", vendor: "J.C. Uzuay", status: "Pausado", detail: "No compra por fin de mes. No le gustó producto mexicano.", action: "Esperar próximo mes. Ofrecer productos distintos." },
                { client: "GRUPO TRUJILLO", vendor: "Ricardo", status: "Muestras Entregadas", detail: "Muestras dejadas anteriormente.", action: "Próxima visita EXCLUSIVA para tomar pedido." }
            ]
        };

        // --- State Management ---
        let currentTab = 'victorias';

        // --- Core Logic ---
        function init() {
            calculateKPIs();
            renderContent();
        }

        function calculateKPIs() {
            const total = reportData.converted.reduce((sum, item) => sum + item.amount, 0);
            const count = reportData.converted.filter(c => c.amount > 0).length; // Exclude the $0 check case for count logic if desired, or keep all. Keeping all.
            
            document.getElementById('kpi-total-sales').textContent = `$${total.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
            document.getElementById('kpi-converted-count').textContent = reportData.converted.length;
        }

        function switchTab(tabName) {
            currentTab = tabName;
            
            // Update styles
            const tabs = ['victorias', 'alertas', 'prospectos', 'analisis'];
            tabs.forEach(t => {
                const btn = document.getElementById(`tab-${t}`);
                if (t === tabName) {
                    btn.classList.remove('tab-inactive', 'border-transparent');
                    btn.classList.add('tab-active', 'border-b-2');
                } else {
                    btn.classList.add('tab-inactive', 'border-transparent');
                    btn.classList.remove('tab-active', 'border-b-2');
                }
            });

            renderContent();
        }

        function renderContent() {
            const container = document.getElementById('content-area');
            container.innerHTML = ''; // Clear

            if (currentTab === 'victorias') {
                renderVictorias(container);
            } else if (currentTab === 'alertas') {
                renderAlertas(container);
            } else if (currentTab === 'prospectos') {
                renderProspectos(container);
            } else if (currentTab === 'analisis') {
                renderAnalisis(container);
            }
        }

        // --- Render Functions ---

        function renderVictorias(container) {
            const intro = document.createElement('div');
            intro.className = "mb-6";
            intro.innerHTML = `
                <h2 class="text-xl font-semibold text-gray-800">Nuevos Convertidos (Grandes Victorias)</h2>
                <p class="text-sm text-gray-600 mt-1">
                    Listado de clientes que han generado su primera factura significativa o han cambiado a estado "Convertido".
                    <span class="font-bold text-emerald-600">Acción clave:</span> Fidelización y aseguramiento de documentos.
                </p>
            `;
            container.appendChild(intro);

            const grid = document.createElement('div');
            grid.className = "grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6";

            // Sort by Amount Descending
            const sortedData = [...reportData.converted].sort((a, b) => b.amount - a.amount);

            sortedData.forEach(client => {
                const card = document.createElement('div');
                card.className = "bg-white rounded-lg shadow-sm border border-gray-200 p-5 card-hover transition-all-300 flex flex-col justify-between";
                
                let badgeColor = "bg-emerald-100 text-emerald-800";
                if (client.priority === "Critical") badgeColor = "bg-red-100 text-red-800 animate-pulse";
                if (client.amount === 0) badgeColor = "bg-gray-100 text-gray-800";

                card.innerHTML = `
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <span class="px-2 py-1 rounded text-xs font-bold ${badgeColor}">$${client.amount.toLocaleString('en-US', {minimumFractionDigits: 2})}</span>
                            <span class="text-xs text-gray-400 font-mono">${client.vendor}</span>
                        </div>
                        <h3 class="text-lg font-bold text-gray-900 mb-1">${client.client}</h3>
                        <p class="text-sm text-gray-600 italic mb-4">"${client.justification}"</p>
                    </div>
                    <div class="bg-amber-50 rounded p-3 border-l-2 border-amber-400 mt-auto">
                        <p class="text-xs font-bold text-amber-900 uppercase tracking-wide mb-1">Acción Requerida:</p>
                        <p class="text-sm text-amber-800 leading-snug">${client.action}</p>
                    </div>
                `;
                grid.appendChild(card);
            });
            container.appendChild(grid);
        }

        function renderAlertas(container) {
            const intro = document.createElement('div');
            intro.className = "mb-6";
            intro.innerHTML = `
                <h2 class="text-xl font-semibold text-gray-800">Alertas y Bloqueos</h2>
                <p class="text-sm text-gray-600 mt-1">
                    Atención requerida para desbloquear ventas o depurar la base de datos.
                    <span class="font-bold text-red-600">Prioridad:</span> Solucionar Stock de Gladys López y reasignar a Ricardo Yaguana.
                </p>
            `;
            container.appendChild(intro);

            const grid = document.createElement('div');
            grid.className = "space-y-4";

            reportData.alerts.forEach(alert => {
                const item = document.createElement('div');
                item.className = "bg-white rounded-lg border border-gray-200 p-4 flex flex-col md:flex-row md:items-center justify-between shadow-sm hover:shadow-md transition";
                
                let icon = "⚠️";
                let borderColor = "border-l-red-500";
                if (alert.type.includes("Stock")) { icon = "📦"; borderColor = "border-l-amber-500"; }
                if (alert.type.includes("Cierre")) { icon = "🚫"; borderColor = "border-l-gray-500"; }
                if (alert.type.includes("Gestión/Tiempo")) { icon = "⏰"; borderColor = "border-l-blue-500"; }

                item.classList.add('border-l-4', borderColor.replace('border-l-', '')); // Tailwind dynamic class workaround requires full class names usually, simplified here

                // Manual border color application
                if(alert.type.includes("Stock")) item.style.borderLeft = "4px solid #f59e0b";
                else if(alert.type.includes("Cierre")) item.style.borderLeft = "4px solid #6b7280";
                else if(alert.type.includes("Gestión/Tiempo")) item.style.borderLeft = "4px solid #3b82f6";
                else item.style.borderLeft = "4px solid #ef4444";

                item.innerHTML = `
                    <div class="flex-1">
                        <div class="flex items-center space-x-2 mb-1">
                            <span class="text-2xl">${icon}</span>
                            <h3 class="text-lg font-bold text-gray-800">${alert.client}</h3>
                            <span class="px-2 py-0.5 rounded text-xs bg-gray-100 text-gray-600 border border-gray-300">${alert.type}</span>
                        </div>
                        <p class="text-sm text-gray-600 mb-1"><span class="font-semibold">Problema:</span> ${alert.detail}</p>
                    </div>
                    <div class="mt-3 md:mt-0 md:ml-6 md:w-1/3 bg-red-50 p-3 rounded text-red-800 text-sm font-medium">
                        👉 ${alert.action}
                    </div>
                `;
                grid.appendChild(item);
            });
            container.appendChild(grid);
        }

        function renderProspectos(container) {
            const intro = document.createElement('div');
            intro.className = "mb-6";
            intro.innerHTML = `
                <h2 class="text-xl font-semibold text-gray-800">Seguimiento de Prospectos</h2>
                <p class="text-sm text-gray-600 mt-1">
                    Oportunidades abiertas que requieren un empuje final para el cierre.
                </p>
            `;
            container.appendChild(intro);

            const tableWrapper = document.createElement('div');
            tableWrapper.className = "overflow-x-auto bg-white rounded-lg shadow border border-gray-200";
            
            tableWrapper.innerHTML = `
                <table class="min-w-full divide-y divide-gray-200">
                    <thead class="bg-gray-50">
                        <tr>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Cliente</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Vendedor</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Estado</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Acción Sugerida</th>
                        </tr>
                    </thead>
                    <tbody class="bg-white divide-y divide-gray-200">
                        ${reportData.prospects.map(p => `
                            <tr>
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${p.client}</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${p.vendor}</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                                    <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                                        ${p.status}
                                    </span>
                                </td>
                                <td class="px-6 py-4 text-sm text-gray-600">${p.action}</td>
                            </tr>
                        `).join('')}
                    </tbody>
                </table>
            `;
            container.appendChild(tableWrapper);
        }

        function renderAnalisis(container) {
            const intro = document.createElement('div');
            intro.className = "mb-6";
            intro.innerHTML = `
                <h2 class="text-xl font-semibold text-gray-800">Análisis Visual de Datos</h2>
                <p class="text-sm text-gray-600 mt-1">
                    Distribución de nuevas ventas por vendedor y estatus de los clientes analizados.
                </p>
            `;
            container.appendChild(intro);

            const grid = document.createElement('div');
            grid.className = "grid grid-cols-1 md:grid-cols-2 gap-8";

            // Chart 1: Sales by Vendor
            const vendorContainer = document.createElement('div');
            vendorContainer.className = "bg-white p-4 rounded-lg shadow-sm border border-gray-200";
            vendorContainer.innerHTML = `
                <h3 class="text-md font-bold text-gray-700 mb-4 text-center">Ventas Nuevas por Vendedor</h3>
                <div class="chart-container">
                    <canvas id="chartVendor"></canvas>
                </div>
            `;
            grid.appendChild(vendorContainer);

            // Chart 2: Client Status Distribution
            const statusContainer = document.createElement('div');
            statusContainer.className = "bg-white p-4 rounded-lg shadow-sm border border-gray-200";
            statusContainer.innerHTML = `
                <h3 class="text-md font-bold text-gray-700 mb-4 text-center">Estado de Cartera Analizada</h3>
                <div class="chart-container">
                    <canvas id="chartStatus"></canvas>
                </div>
            `;
            grid.appendChild(statusContainer);

            container.appendChild(grid);

            // Process Data for Charts
            // 1. Vendor Data
            const vendorSales = {};
            reportData.converted.forEach(c => {
                // Normalize vendor names slightly if needed, but data looks consistent enough
                if (!vendorSales[c.vendor]) vendorSales[c.vendor] = 0;
                vendorSales[c.vendor] += c.amount;
            });

            // 2. Status Data (Counts)
            const statusCounts = {
                'Convertidos': reportData.converted.length,
                'Alertas/Bloqueos': reportData.alerts.length,
                'En Seguimiento': reportData.prospects.length
            };

            // Render Charts
            setTimeout(() => {
                new Chart(document.getElementById('chartVendor'), {
                    type: 'bar',
                    data: {
                        labels: Object.keys(vendorSales),
                        datasets: [{
                            label: 'Monto Vendido ($)',
                            data: Object.values(vendorSales),
                            backgroundColor: '#10b981', // Emerald 500
                            borderRadius: 4
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: { display: false }
                        },
                        scales: {
                            y: { beginAtZero: true }
                        }
                    }
                });

                new Chart(document.getElementById('chartStatus'), {
                    type: 'doughnut',
                    data: {
                        labels: Object.keys(statusCounts),
                        datasets: [{
                            data: Object.values(statusCounts),
                            backgroundColor: ['#10b981', '#ef4444', '#3b82f6'],
                            hoverOffset: 4
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false
                    }
                });
            }, 100);
        }

        // Initialize App
        document.addEventListener('DOMContentLoaded', init);

    </script>
</body>
</html>
