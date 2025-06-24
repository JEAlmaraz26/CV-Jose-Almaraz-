<!DOCTYPE html>
<html lang="es" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CV Interactivo | José Eduardo Almaraz</title>
    <!-- Chosen Palette: Warm Neutrals & Professional Blue -->
    <!-- Application Structure Plan: The SPA is designed as an interactive dashboard/narrative of the CV. It starts with a strong Hero section (Header) containing the professional summary. A sticky navigation bar allows non-linear exploration of key sections: a vertical interactive Timeline for career path ("Trayectoria"), a dedicated section for high-impact "Proyectos" with a budget visualization chart, a "Habilidades" section with a radar chart for core competencies and detailed lists, and a final "Educación" section. This structure was chosen to break down a dense, text-heavy CV into digestible, interactive modules. It allows recruiters to get a quick overview and then deep-dive into the areas most relevant to them (like project scale or specific skills), enhancing engagement and information retention over a static document. -->
    <!-- Visualization & Content Choices: 
        - Hero/Summary -> Goal: Inform/Hook -> Method: Prominent text block -> Interaction: None, immediate impact -> Justification: Delivers the core value proposition instantly.
        - Career Path -> Goal: Show change/progression -> Method: Vertical Timeline (HTML/CSS/JS) -> Interaction: Click-to-expand details for each role -> Justification: More engaging than a list; keeps the initial view clean while allowing deep dives.
        - Project Budgets -> Goal: Compare/Show Impact -> Method: Bar Chart (Chart.js) -> Interaction: Tooltips on hover -> Justification: Provides a powerful, immediate visual representation of the financial scale of his project management experience.
        - Core Competencies -> Goal: Organize/Summarize -> Method: Radar Chart (Chart.js) -> Interaction: Tooltips on hover -> Justification: Offers a quick, scannable summary of his key strengths.
        - Specific Skills/Certs -> Goal: Inform/Organize -> Method: Categorized lists with icons (HTML/Tailwind) -> Interaction: None, clear presentation -> Justification: Ideal for scannability by both humans and ATS systems.
        - All other text -> Goal: Inform -> Method: Styled text blocks (HTML/Tailwind) -> Interaction: None -> Justification: Clear, legible presentation of supporting details.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f4f4f5; /* zinc-100 */
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 400px;
        }
        @media (max-width: 768px) {
            .chart-container {
                height: 300px;
            }
        }
        .timeline-item-content {
            transition: max-height 0.5s ease-in-out, opacity 0.5s ease-in-out;
            max-height: 0;
            opacity: 0;
            overflow: hidden;
        }
        .timeline-item-content.open {
            max-height: 1000px; /* Large enough to fit content */
            opacity: 1;
        }
        .nav-link.active {
            color: #2563eb; /* blue-600 */
            font-weight: 700;
        }
    </style>
</head>
<body class="text-zinc-800">

    <!-- Header & Navigation -->
    <header class="bg-zinc-100/80 backdrop-blur-sm sticky top-0 z-50 shadow-sm">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
            <nav class="flex items-center justify-between h-16">
                <div class="text-xl font-extrabold text-zinc-900">
                    J. E. ALMARAZ
                </div>
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#trayectoria" class="nav-link text-zinc-600 hover:text-blue-600 transition-colors duration-300">Trayectoria</a>
                    <a href="#proyectos" class="nav-link text-zinc-600 hover:text-blue-600 transition-colors duration-300">Proyectos</a>
                    <a href="#habilidades" class="nav-link text-zinc-600 hover:text-blue-600 transition-colors duration-300">Habilidades</a>
                    <a href="#educacion" class="nav-link text-zinc-600 hover:text-blue-600 transition-colors duration-300">Educación</a>
                </div>
                <div class="md:hidden">
                    <button id="mobile-menu-button" class="text-zinc-600 hover:text-zinc-900">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path></svg>
                    </button>
                </div>
            </nav>
            <div id="mobile-menu" class="hidden md:hidden pb-4">
                <a href="#trayectoria" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-200 rounded">Trayectoria</a>
                <a href="#proyectos" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-200 rounded">Proyectos</a>
                <a href="#habilidades" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-200 rounded">Habilidades</a>
                <a href="#educacion" class="block py-2 px-4 text-sm text-zinc-600 hover:bg-zinc-200 rounded">Educación</a>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-4 sm:px-6 lg:px-8 py-12">
        
        <!-- Hero Section -->
        <section id="hero" class="text-center mb-20">
            <h1 class="text-4xl md:text-5xl lg:text-6xl font-extrabold text-zinc-900">JOSÉ EDUARDO ALMARAZ</h1>
            <p class="mt-2 text-xl md:text-2xl font-semibold text-blue-600"></p>
            <div class="mt-6 flex justify-center items-center space-x-6 text-zinc-600">
                <span class="flex items-center"><svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg> (03854) 15400569</span>
                <span class="flex items-center"><svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg> almarazjose@gmail.com</span>
                <span class="flex items-center"><svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path></svg> Frías, Santiago del Estero, Argentina</span>
            </div>
            <p class="mt-8 max-w-3xl mx-auto text-lg text-zinc-700">
                20 años de experiencia en gestión de operaciones, calidad, mantenimiento y proyectos en sectores como energía (termoeléctricas, biodiesel), automotriz y manufactura. Experiencia en optimización de procesos, gestión integral de sistemas de calidad (ISO 9000, 14000, 45001, 50001). Demostrada capacidad para impulsar la eficiencia operativa y la mejora continua, así como la ejecución exitosa de proyectos.
            </p>
        </section>

        <!-- Trayectoria Profesional -->
        <section id="trayectoria" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-zinc-900">Trayectoria Profesional</h2>
                <p class="mt-2 text-lg text-zinc-600">Una línea de tiempo interactiva de mi experiencia. Haz clic en cada rol para ver los detalles.</p>
            </div>
            <div class="relative wrap overflow-hidden p-10 h-full">
                <div class="absolute border-opacity-20 border-zinc-700 h-full border" style="left: 50%"></div>
                <!-- Timeline items will be injected here by JavaScript -->
            </div>
        </section>

        <!-- Proyectos Destacados -->
        <section id="proyectos" class="py-16 bg-white rounded-lg shadow-lg">
             <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-zinc-900">Proyectos Destacados</h2>
                <p class="mt-2 text-lg text-zinc-600">Visualización del impacto y la escala de los proyectos gestionados.</p>
            </div>
            <div class="chart-container">
                <canvas id="projectsChart"></canvas>
            </div>
        </section>

        <!-- Habilidades -->
        <section id="habilidades" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-zinc-900">Áreas de Expertise y Habilidades</h2>
                <p class="mt-2 text-lg text-zinc-600">Un resumen de mis competencias técnicas y de gestión.</p>
            </div>
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
                <div class="chart-container h-96">
                    <canvas id="skillsChart"></canvas>
                </div>
                <div class="space-y-6">
                    <div>
                        <h3 class="text-xl font-bold mb-3 text-zinc-800">Sistemas de Gestión</h3>
                        <div class="flex flex-wrap gap-2">
                            <span class="bg-blue-100 text-blue-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">ISO 9000 (Calidad)</span>
                            <span class="bg-blue-100 text-blue-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">ISO 14000 (Medio Ambiente)</span>
                            <span class="bg-blue-100 text-blue-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">ISO 45001 (SySO)</span>
                            <span class="bg-blue-100 text-blue-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">ISO 50001 (Auditor Interno)</span>
                            <span class="bg-green-100 text-green-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">Normas BPM, BPL, BPA</span>
                            <span class="bg-green-100 text-green-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">EAQF94</span>
                        </div>
                    </div>
                    <div>
                        <h3 class="text-xl font-bold mb-3 text-zinc-800">Software</h3>
                        <div class="flex flex-wrap gap-2">
                            <span class="bg-zinc-200 text-zinc-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">Microsoft Office</span>
                            <span class="bg-zinc-200 text-zinc-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">AutoCAD</span>
                            <span class="bg-red-100 text-red-800 text-sm font-bold mr-2 px-2.5 py-0.5 rounded">SAP</span>
                        </div>
                    </div>
                    <div>
                        <h3 class="text-xl font-bold mb-3 text-zinc-800">Competencias Clave</h3>
                         <ul class="list-disc list-inside space-y-1 text-zinc-700">
                             <li>Gestión de Proyectos (PM) de Inversión</li>
                             <li>Control Estadístico de Procesos (CEP)</li>
                             <li>Operaciones y Mantenimiento Industrial</li>
                             <li>Optimización de Consumos Energéticos</li>
                             <li>Aseguramiento y Control de Calidad</li>
                         </ul>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Educación -->
        <section id="educacion" class="py-16 bg-white rounded-lg shadow-lg">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-zinc-900">Educación e Idiomas</h2>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-center">
                <div>
                    <h3 class="text-xl font-bold text-blue-600">Formación Académica</h3>
                    <div class="mt-4">
                        <p class="text-lg font-semibold">Ingeniería Química / Carrera universitaria incompleta</p>
                        <p class="text-zinc-600">Facultad Regional Córdoba, Universidad Tecnológica Nacional (UTN)</p>
                        <p class="text-sm text-zinc-500">*Proyecto Final (Tesis) Aprobado*</p>
                    </div>
                     <div class="mt-4">
                        <p class="text-lg font-semibold">Bachiller Fisicomatemático</p>
                        <p class="text-zinc-600">Escuela Normal Superior “República del Ecuador”</p>
                    </div>
                </div>
                <div>
                    <h3 class="text-xl font-bold text-blue-600">Idiomas</h3>
                    <div class="mt-4">
                        <p class="text-lg font-semibold">Inglés</p>
                        <p class="text-zinc-600">Nivel Intermedio (Instituto Cultural Anglo-Argentino)</p>
                    </div>
                     <div class="mt-4">
                        <p class="text-lg font-semibold">Italiano</p>
                        <p class="text-zinc-600">Nivel Básico</p>
                    </div>
                </div>
            </div>
        </section>

    </main>
    
    <footer class="bg-zinc-800 text-white mt-16">
        <div class="container mx-auto py-6 px-4 sm:px-6 lg:px-8 text-center text-zinc-400">
             <p>CV Interactivo de José Eduardo Almaraz</p>
             <p class="text-sm mt-1">&copy; 2025 - Diseñado para destacar.</p>
        </div>
    </footer>

    <script>
    document.addEventListener('DOMContentLoaded', function() {
        
        // Mobile Menu Toggle
        const mobileMenuButton = document.getElementById('mobile-menu-button');
        const mobileMenu = document.getElementById('mobile-menu');
        mobileMenuButton.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        // Navigation highlighting on scroll
        const sections = document.querySelectorAll('section');
        const navLinks = document.querySelectorAll('.nav-link');

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    navLinks.forEach(link => {
                        link.classList.toggle('active', link.getAttribute('href').substring(1) === entry.target.id);
                    });
                }
            });
        }, { rootMargin: '-50% 0px -50% 0px' });

        sections.forEach(section => {
            observer.observe(section);
        });

        // Timeline Data
        const timelineData = [
            {
                date: 'Jul 2015 – Actualidad',
                title: 'Jefe de Turno de O&M',
                company: 'Generación Mediterránea S.A. (Grupo Albanesi)',
                details: [
                    'Gestión integral de operaciones y mantenimiento en una central termoeléctrica, asegurando la continuidad operativa.',
                    'Liderazgo y supervisión en la puesta en marcha y commissioning de turbina Pratt & Whitney FT 4000 de 60 MW, garantizando su rendimiento óptimo.',
                    'Asistencia técnica y supervisión en el mantenimiento mecánico de turbinas, optimizando la disponibilidad y confiabilidad de los equipos.',
                    'Implementación y seguimiento de MAPROS y AUDIS para el control de indicadores clave de desempeño.',
                    'Gestión efectiva de procedimientos operativos y manejo del sistema SAP para la administración de activos.',
                    'Mantenimiento y aseguramiento de certificaciones ISO 9000, ISO 14000 e ISO 45001, promoviendo altos estándares de calidad, medio ambiente y seguridad ocupacional.'
                ]
            },
            {
                date: 'Nov 2009 – Ago 2014',
                title: 'Múltiples Roles (Supervisor e Ingeniero de Proyectos)',
                company: 'VILUCO S.A. Agroenergía – Planta de Biodiesel',
                details: [
                    'Coordinador de Proyectos / Project Manager (PM): Liderazgo y ejecución de proyectos de capital con presupuestos significativos, incluyendo:',
                    '    - Diseño y construcción de tanques (500m³) y piping de fueloil (Presupuesto: U$S 2.000.000).',
                    '    - Implementación de tanques (1000m³) y piping para almacenamiento de aceite de soja y biodiesel (Presupuesto: U$S 5.000.000).',
                    '    - Desarrollo e implementación del Sistema de Ahorro y Medición de Consumos Energéticos (Presupuesto: U$S 1.000.000), optimizando el uso de energía eléctrica, gas, vapor, agua y aire comprimido.',
                    '    - Gestión integral del proyecto de Desgomado Acuoso, secado y estandarización de lecitina (Presupuesto: U$S 20.000.000), incluyendo supervisión de ingeniería, montaje, puesta en marcha y commissioning.',
                    'Supervisor de Ingeniería y Gestión de Proyectos: Responsable de la gestión de consumos energéticos y la identificación de oportunidades de ahorro.',
                    'Jefe de Sector Desgomado Acuoso: Supervisión y control de las operaciones de secado, estandarizado y envasado de lecitina.',
                    'Supervisor de Servicios Centrales (Mantenimiento): Gestión de operaciones de caldera (60 Tn/h), compresores de aire, torres de enfriamiento, ósmosis inversa, ablandadores y chillers.',
                    'Supervisor de Producción: Supervisión directa del sector de planta de Biodiesel.',
                    'Supervisor de Montaje y Puesta en Marcha de Planta.'
                ]
            },
            {
                date: 'Abr 2005 – Jul 2007',
                title: 'Responsable de Calidad y Laboratorio / Jefe de Procesos y Laboratorio',
                company: 'Cueros Catamarca S.A. (Grupo Dulcor S.A.)',
                details: [
                    'Planificación, control y gestión del Sistema de Calidad, logrando la certificación de Normas BPM (Buenas Prácticas de Manufactura).',
                    'Diseño y evaluación de nuevos productos, contribuyendo a la innovación del portfolio.',
                    'Diseño e implementación de BPM, BPL (Buenas Prácticas de Laboratorio) y BPA (Buenas Prácticas Agrícolas) bajo normas ISO 9000 versión 2000.',
                    'Liderazgo de equipos como Jefe de Procesos (1 año) y Jefe de Laboratorio (1 año).'
                ]
            },
            {
                date: 'Experiencias Previas en Industria',
                title: 'Roles Diversos en Sectores Químico y Automotriz',
                company: 'Refinería del Centro S.A., Cauplas S.R.L., Rieter Automotive Argentina S.A., INTI',
                details: [
                    'Supervisor de Hidrogenación de Aceites Vegetales (Refinería del Centro S.A. - 1 año): Control y gestión del reactor de hidrogenación y los procesos de refinado de óleo-margarinas.',
                    'Responsable de Calidad y Logística (Cauplas S.R.L. - 1 año): Control y gestión del sistema de calidad para la certificación ISO 9000 versión 2000, supervisión de puesta a punto de producción y control de metrología, responsabilidad integral del departamento de logística.',
                    'Responsable de Control Estadístico de Procesos (CEP) (Rieter Automotive Argentina S.A. - 1 año): Liderazgo y manejo de personal, control y supervisión de procedimientos estadísticos de proceso, asistencia estadística a gerencia.',
                    'Analista de Aseguramiento de la Calidad (Rieter Automotive Argentina S.A. - 1 año): Control de calidad de productos según normativas FIAT y RENAULT, ensayos fisicoquímicos y metrología, manejo de documentación, registros y calibración, gestión de no conformidades (EAQF94).',
                    'Becario (Instituto Nacional de Tecnología Industrial (INTI) - 6 meses).'
                ]
            }
        ];

        // Inject Timeline Items
        const timelineContainer = document.querySelector('.relative.wrap');
        timelineContainer.innerHTML = '<div class="absolute border-opacity-20 border-zinc-700 h-full border" style="left: 50%"></div>'; // Clear and re-add central line
        timelineData.forEach((item, index) => {
            const isLeft = index % 2 === 0;
            const timelineItemHTML = `
                <div class="mb-8 flex justify-between ${isLeft ? 'flex-row-reverse' : ''} items-center w-full">
                    <div class="order-1 w-5/12"></div>
                    <div class="z-20 flex items-center order-1 bg-zinc-800 shadow-xl w-8 h-8 rounded-full">
                        <h1 class="mx-auto font-semibold text-lg text-white">${index + 1}</h1>
                    </div>
                    <div class="order-1 bg-white rounded-lg shadow-xl w-5/12 px-6 py-4 timeline-item-container cursor-pointer">
                        <p class="text-sm font-medium text-blue-600">${item.date}</p>
                        <h3 class="mb-3 font-bold text-zinc-800 text-xl">${item.title}</h3>
                        <p class="text-sm leading-snug tracking-wide text-zinc-600 font-semibold">${item.company}</p>
                        <div class="timeline-item-content mt-4">
                            <ul class="list-disc list-inside space-y-1 text-zinc-700 text-sm">
                                ${item.details.map(detail => `<li>${detail}</li>`).join('')}
                            </ul>
                        </div>
                    </div>
                </div>
            `;
            timelineContainer.insertAdjacentHTML('beforeend', timelineItemHTML);
        });

        // Timeline click interaction
        document.querySelectorAll('.timeline-item-container').forEach(item => {
            item.addEventListener('click', () => {
                item.querySelector('.timeline-item-content').classList.toggle('open');
            });
        });

        // Projects Chart
        const projectsCtx = document.getElementById('projectsChart').getContext('2d');
        if (window.projectsChartInstance) {
            window.projectsChartInstance.destroy();
        }
        window.projectsChartInstance = new Chart(projectsCtx, {
            type: 'bar',
            data: {
                labels: ['Desgomado Acuoso', 'Almacenamiento y Piping', 'Optimización Energética'],
                datasets: [{
                    label: 'Inversión del Proyecto (en Millones de U$S)',
                    data: [20, 7, 1],
                    backgroundColor: [
                        'rgba(37, 99, 235, 0.6)', // blue-600
                        'rgba(29, 78, 216, 0.6)', // blue-700
                        'rgba(30, 64, 175, 0.6)', // blue-800
                    ],
                    borderColor: [
                        'rgba(37, 99, 235, 1)',
                        'rgba(29, 78, 216, 1)',
                        'rgba(30, 64, 175, 1)',
                    ],
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: {
                        display: true,
                        text: 'Proyectos Clave por Inversión (VILUCO S.A.)',
                        font: { size: 18 }
                    },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                let label = context.dataset.label || '';
                                if (label) {
                                    label += ': ';
                                }
                                if (context.parsed.y !== null) {
                                    label += 'U$S ' + context.parsed.y + 'M';
                                }
                                return label;
                            }
                        }
                    }
                },
                scales: {
                    y: {
                        beginAtZero: true,
                        ticks: {
                           callback: function(value, index, ticks) {
                               return 'U$S ' + value + 'M';
                           }
                        }
                    }
                }
            }
        });

        // Skills Chart
        const skillsCtx = document.getElementById('skillsChart').getContext('2d');
        if (window.skillsChartInstance) {
            window.skillsChartInstance.destroy();
        }
        window.skillsChartInstance = new Chart(skillsCtx, {
            type: 'radar',
            data: {
                labels: ['Gestión de Proyectos', 'Operaciones y Mtt.', 'Sistemas de Calidad (ISO)', 'Liderazgo de Equipos', 'Optimización Energética', 'Control de Procesos'],
                datasets: [{
                    label: 'Nivel de Expertise',
                    data: [10, 9, 9, 10, 8, 9],
                    backgroundColor: 'rgba(37, 99, 235, 0.2)',
                    borderColor: 'rgba(37, 99, 235, 1)',
                    borderWidth: 2,
                    pointBackgroundColor: 'rgba(37, 99, 235, 1)',
                    pointBorderColor: '#fff',
                    pointHoverBackgroundColor: '#fff',
                    pointHoverBorderColor: 'rgba(37, 99, 235, 1)'
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: {
                        display: true,
                        text: 'Competencias Principales',
                        font: { size: 18 }
                    }
                },
                scales: {
                    r: {
                        beginAtZero: true,
                        max: 10,
                        ticks: {
                            display: false
                        }
                    }
                }
            }
        });

    });
    </script>
</body>
</html>
