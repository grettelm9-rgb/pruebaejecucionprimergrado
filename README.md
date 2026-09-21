<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Colegio Diocesano Padre Eladio Sancho - Prueba de Ejecución 2026</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Nunito', sans-serif;
            background: linear-gradient(135deg, #e0f2fe 0%, #f0f9ff 50%, #fef3c7 100%);
            min-height: 100vh;
            user-select: none;
            -webkit-user-select: none;
        }
        h1, h2, h3, h4, .font-heading {
            font-family: 'Fredoka', cursive;
        }
        
        @keyframes bounce-gentle {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }
        @keyframes pulse-glow {
            0%, 100% { filter: drop-shadow(0 0 6px rgba(245, 158, 11, 0.6)); }
            50% { filter: drop-shadow(0 0 16px rgba(245, 158, 11, 0.9)); }
        }
        @keyframes float-slow {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-5px) rotate(2deg); }
        }
        
        .animate-gentle { animation: bounce-gentle 2.5s infinite ease-in-out; }
        .animate-glow { animation: pulse-glow 1.8s infinite ease-in-out; }
        .animate-float { animation: float-slow 4s infinite ease-in-out; }

        .mouse-btn {
            cursor: pointer;
            transition: filter 0.2s, transform 0.1s;
        }
        .mouse-btn:hover {
            filter: brightness(1.15) drop-shadow(0 0 8px rgba(59, 130, 246, 0.5));
        }

        .badge-avanzado { background-color: #dcfce7; color: #15803d; }
        .badge-bueno { background-color: #fef9c3; color: #a16207; }
        .badge-mejorar { background-color: #fee2e2; color: #b91c1c; }

        @media print {
            body {
                background: white !important;
                color: black !important;
            }
            .no-print, #tito-toast {
                display: none !important;
            }
            .app-container {
                box-shadow: none !important;
                padding: 0 !important;
                max-width: 100% !important;
            }
        }
    </style>
</head>
<body class="text-slate-800 flex flex-col min-h-screen">

    <!-- Top Navigation Bar -->
    <header id="main-header" class="no-print bg-white/90 backdrop-blur-md border-b-4 border-amber-300 sticky top-0 z-40 shadow-sm px-4 py-2">
        <div class="max-w-6xl mx-auto flex flex-wrap items-center justify-between gap-2">
            <!-- Brand & Tito Badge -->
            <div class="flex items-center gap-3">
                <div class="w-11 h-11 rounded-full bg-amber-100 border-2 border-amber-400 flex items-center justify-center shadow-inner overflow-hidden p-0.5" id="header-tito-avatar"></div>
                <div>
                    <h1 class="text-base sm:text-lg font-bold text-sky-900 leading-none">LA AVENTURA DE TITO: MISIÓN MOUSE</h1>
                    <span id="student-badge" class="text-xs text-slate-500 font-semibold">Estudiante: <span id="header-student-name" class="text-amber-600">Invitado</span></span>
                </div>
            </div>

            <!-- Progress Trail (6 Misiones + Trofeo) -->
            <div id="progress-trail" class="hidden sm:flex items-center gap-1 bg-sky-50 px-3 py-1.5 rounded-full border border-sky-200">
                <div class="step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-amber-400 text-white shadow" id="dot-1">M1</div>
                <div class="h-1 w-2 bg-slate-200" id="line-1"></div>
                <div class="step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-slate-200 text-slate-500" id="dot-2">M2</div>
                <div class="h-1 w-2 bg-slate-200" id="line-2"></div>
                <div class="step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-slate-200 text-slate-500" id="dot-3">M3</div>
                <div class="h-1 w-2 bg-slate-200" id="line-3"></div>
                <div class="step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-slate-200 text-slate-500" id="dot-4">M4</div>
                <div class="h-1 w-2 bg-slate-200" id="line-4"></div>
                <div class="step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-slate-200 text-slate-500" id="dot-5">M5</div>
                <div class="h-1 w-2 bg-slate-200" id="line-5"></div>
                <div class="step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-slate-200 text-slate-500" id="dot-6">M6</div>
                <div class="h-1 w-2 bg-slate-200" id="line-6"></div>
                <div class="step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-emerald-500 text-white p-1" id="dot-7"></div>
            </div>

            <!-- Controls -->
            <div class="flex items-center gap-2">
                <div class="bg-blue-100 text-blue-900 text-xs font-bold px-3 py-1 rounded-full border border-blue-300 hidden md:flex items-center gap-1">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 animate-ping"></span>
                    <span id="session-badge-id">SESIÓN: Inactiva</span>
                </div>
                <button id="sound-btn" onclick="toggleSound()" class="bg-sky-100 hover:bg-sky-200 text-sky-700 p-2 rounded-full border border-sky-300 transition" title="Activar/Desactivar Sonido">
                </button>
            </div>
        </div>
    </header>

    <!-- Banner Institucional -->
    <div class="bg-blue-900 text-white py-2 px-4 shadow-md no-print">
        <div class="max-w-6xl mx-auto flex flex-wrap justify-between items-center text-xs sm:text-sm font-semibold">
            <span>COLEGIO DIOCESANO PADRE ELADIO SANCHO</span>
            <span>Prueba de Ejecución II Semestre, 2026 | Informática Educativa - Primer Grado</span>
        </div>
    </div>

    <!-- Main Container -->
    <main class="flex-grow max-w-5xl w-full mx-auto p-4 flex flex-col justify-center app-container">
        <div id="main-card-viewport" class="w-full"></div>
    </main>

    <!-- Tito Toast Feedback (Oculto al imprimir) -->
    <div id="tito-toast" class="no-print fixed bottom-6 left-1/2 -translate-x-1/2 bg-slate-900/95 text-white px-6 py-3 rounded-full font-bold shadow-2xl transition-all duration-300 transform translate-y-28 z-50 flex items-center gap-3 border-2 border-amber-400 backdrop-blur-sm">
        <div id="toast-tito-icon" class="w-10 h-10 flex-shrink-0"></div>
        <span id="toast-msg" class="text-sm sm:text-base font-heading tracking-wide">¡Hola! Soy Tito el Ratón.</span>
    </div>

    <script>
        /* ==========================================================================
           1. SISTEMA ILUSTRADO VECTORIAL SVG (TITO, POSES, ESCENARIOS Y OBJETOS)
           ========================================================================== */
        
        function getTitoSvg(pose = 'hello', size = 64) {
            let armLeft = `<path d="M 32 62 Q 20 65 18 52" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>`;
            let armRight = `<path d="M 68 62 Q 80 65 82 52" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>`;
            let eyes = `
                <circle cx="40" cy="42" r="5" fill="#0f172a"/>
                <circle cx="60" cy="42" r="5" fill="#0f172a"/>
                <circle cx="41.5" cy="40.5" r="2" fill="#ffffff"/>
                <circle cx="61.5" cy="40.5" r="2" fill="#ffffff"/>
            `;
            let mouth = `<path d="M 42 56 Q 50 63 58 56" stroke="#0f172a" stroke-width="3" stroke-linecap="round" fill="none"/>`;
            let eyebrows = `
                <path d="M 36 34 Q 40 32 44 34" stroke="#475569" stroke-width="2" stroke-linecap="round" fill="none"/>
                <path d="M 56 34 Q 60 32 64 34" stroke="#475569" stroke-width="2" stroke-linecap="round" fill="none"/>
            `;
            let extraDecor = '';

            if (pose === 'hello') {
                armRight = `<path d="M 68 60 Q 82 45 80 32" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>
                            <circle cx="80" cy="30" r="4" fill="#cbd5e1"/>`;
            } else if (pose === 'explaining') {
                armRight = `<path d="M 68 60 Q 82 55 90 42" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>
                            <line x1="88" y1="44" x2="98" y2="30" stroke="#f59e0b" stroke-width="3" stroke-linecap="round"/>`;
                mouth = `<path d="M 44 55 Q 50 60 56 55 Z" fill="#0f172a"/>`;
            } else if (pose === 'pointing') {
                armRight = `<path d="M 68 60 L 92 60" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>
                            <polygon points="90,56 98,60 90,64" fill="#cbd5e1"/>`;
            } else if (pose === 'celebrating') {
                armLeft = `<path d="M 32 60 Q 18 40 22 28" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>`;
                armRight = `<path d="M 68 60 Q 82 40 78 28" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>`;
                mouth = `<path d="M 40 54 Q 50 68 60 54 Z" fill="#0f172a"/>
                         <path d="M 44 56 Q 50 62 56 56" fill="#f472b6"/>`;
                extraDecor = `<polygon points="18,20 22,12 26,20" fill="#f59e0b"/>
                              <polygon points="80,20 84,12 88,20" fill="#f59e0b"/>`;
            } else if (pose === 'thinking') {
                armRight = `<path d="M 68 62 Q 62 50 56 52" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>`;
                eyebrows = `
                    <path d="M 36 32 Q 40 35 44 34" stroke="#475569" stroke-width="2" stroke-linecap="round" fill="none"/>
                    <path d="M 56 30 Q 60 28 64 31" stroke="#475569" stroke-width="2" stroke-linecap="round" fill="none"/>
                `;
                mouth = `<path d="M 44 58 Q 50 56 56 58" stroke="#0f172a" stroke-width="2.5" stroke-linecap="round" fill="none"/>`;
                extraDecor = `<circle cx="76" cy="30" r="3" fill="#38bdf8" opacity="0.6"/>
                              <circle cx="84" cy="20" r="5" fill="#38bdf8" opacity="0.8"/>`;
            } else if (pose === 'surprised') {
                eyes = `
                    <circle cx="40" cy="42" r="7" fill="#0f172a"/>
                    <circle cx="60" cy="42" r="7" fill="#0f172a"/>
                    <circle cx="41" cy="40" r="3" fill="#ffffff"/>
                    <circle cx="61" cy="40" r="3" fill="#ffffff"/>
                `;
                mouth = `<ellipse cx="50" cy="58" rx="5" ry="7" fill="#0f172a"/>`;
                eyebrows = `
                    <path d="M 34 28 Q 40 26 46 28" stroke="#475569" stroke-width="2" stroke-linecap="round" fill="none"/>
                    <path d="M 54 28 Q 60 26 66 28" stroke="#475569" stroke-width="2" stroke-linecap="round" fill="none"/>
                `;
            } else if (pose === 'encouraging') {
                armRight = `<path d="M 68 60 Q 85 58 82 46" stroke="#94a3b8" stroke-width="5" stroke-linecap="round" fill="none"/>
                            <circle cx="82" cy="42" r="5" fill="#38bdf8"/>`;
                mouth = `<path d="M 42 54 Q 50 64 58 54 Z" fill="#0f172a"/>`;
            }

            return `<svg width="${size}" height="${size}" viewBox="0 0 100 100">
                ${extraDecor}
                <!-- Orejas -->
                <circle cx="22" cy="22" r="16" fill="#94a3b8"/><circle cx="22" cy="22" r="9" fill="#f472b6"/>
                <circle cx="78" cy="22" r="16" fill="#94a3b8"/><circle cx="78" cy="22" r="9" fill="#f472b6"/>
                
                <!-- Brazos traseros -->
                ${armLeft}
                ${armRight}
                
                <!-- Cuerpo y Chaleco -->
                <ellipse cx="50" cy="72" rx="22" ry="20" fill="#cbd5e1"/>
                <path d="M 32 62 Q 50 64 68 62 L 66 88 Q 50 92 34 88 Z" fill="#2563eb"/>
                <path d="M 46 63 L 50 78 L 54 63 Z" fill="#f59e0b"/>
                
                <!-- Cabeza -->
                <circle cx="50" cy="48" r="28" fill="#cbd5e1"/>
                <ellipse cx="50" cy="53" rx="14" ry="9" fill="#f8fafc"/>
                <ellipse cx="50" cy="47" rx="4.5" ry="3.5" fill="#1e293b"/>
                
                <!-- Ojos, Cejas y Boca -->
                ${eyebrows}
                ${eyes}
                ${mouth}
            </svg>`;
        }

        function getScenarioBg(missionNum) {
            switch(missionNum) {
                case 1:
                    return `<svg class="absolute inset-0 w-full h-full opacity-20 pointer-events-none" viewBox="0 0 800 400" preserveAspectRatio="none">
                        <rect x="0" y="300" width="800" height="100" fill="#b45309"/>
                        <rect x="0" y="290" width="800" height="10" fill="#d97706"/>
                        <rect x="100" y="80" width="600" height="200" rx="16" fill="#0284c7"/>
                        <rect x="120" y="100" width="560" height="160" fill="#e0f2fe"/>
                    </svg>`;
                case 2:
                    return `<svg class="absolute inset-0 w-full h-full opacity-20 pointer-events-none" viewBox="0 0 800 400" preserveAspectRatio="none">
                        <circle cx="400" cy="200" r="180" fill="none" stroke="#0284c7" stroke-width="4" stroke-dasharray="8 8"/>
                        <circle cx="400" cy="200" r="100" fill="none" stroke="#38bdf8" stroke-width="2"/>
                    </svg>`;
                case 3:
                    return `<svg class="absolute inset-0 w-full h-full opacity-20 pointer-events-none" viewBox="0 0 800 400" preserveAspectRatio="none">
                        <path d="M 0 350 Q 200 320 400 350 T 800 350 L 800 400 L 0 400 Z" fill="#f472b6"/>
                        <circle cx="150" cy="120" r="40" fill="#fef08a"/>
                        <circle cx="680" cy="100" r="30" fill="#38bdf8"/>
                    </svg>`;
                case 4:
                    return `<svg class="absolute inset-0 w-full h-full opacity-20 pointer-events-none" viewBox="0 0 800 400" preserveAspectRatio="none">
                        <polygon points="100,0 200,400 0,400" fill="#fef08a"/>
                        <polygon points="700,0 800,400 600,400" fill="#38bdf8"/>
                    </svg>`;
                case 5:
                    return `<svg class="absolute inset-0 w-full h-full opacity-20 pointer-events-none" viewBox="0 0 800 400" preserveAspectRatio="none">
                        <rect x="50" y="40" width="700" height="15" fill="#94a3b8"/>
                        <rect x="50" y="180" width="700" height="15" fill="#94a3b8"/>
                        <rect x="50" y="320" width="700" height="15" fill="#94a3b8"/>
                    </svg>`;
                case 6:
                    return `<svg class="absolute inset-0 w-full h-full opacity-20 pointer-events-none" viewBox="0 0 800 400" preserveAspectRatio="none">
                        <rect x="0" y="0" width="800" height="400" fill="#fef3c7"/>
                        <line x1="80" y1="0" x2="80" y2="400" stroke="#b45309" stroke-width="8"/>
                        <line x1="720" y1="0" x2="720" y2="400" stroke="#b45309" stroke-width="8"/>
                    </svg>`;
                default:
                    return '';
            }
        }

        function getSvg(name, size = 48) {
            switch(name) {
                case 'star':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><polygon points="25,3 32,18 48,18 35,28 40,44 25,34 10,44 15,28 2,18 18,18" fill="#f59e0b" stroke="#d97706" stroke-width="2"/></svg>`;
                case 'ball':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><circle cx="25" cy="25" r="21" fill="#ef4444" stroke="#b91c1c" stroke-width="2"/><path d="M 10 25 Q 25 10 40 25" stroke="white" stroke-width="4" fill="none"/><path d="M 10 25 Q 25 40 40 25" stroke="white" stroke-width="4" fill="none"/><line x1="25" y1="4" x2="25" y2="46" stroke="white" stroke-width="3"/></svg>`;
                case 'robot':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><rect x="10" y="14" width="30" height="26" rx="4" fill="#8b5cf6" stroke="#6d28d9" stroke-width="2"/><circle cx="20" cy="24" r="4" fill="#67e8f9"/><circle cx="30" cy="24" r="4" fill="#67e8f9"/><rect x="18" y="32" width="14" height="4" rx="2" fill="#38bdf8"/><line x1="25" y1="4" x2="25" y2="14" stroke="#6d28d9" stroke-width="3"/><circle cx="25" cy="4" r="3" fill="#ef4444"/><rect x="4" y="20" width="6" height="12" rx="2" fill="#a78bfa"/><rect x="40" y="20" width="6" height="12" rx="2" fill="#a78bfa"/></svg>`;
                case 'rocket':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><path d="M 25 4 C 35 15 35 30 35 40 L 15 40 C 15 30 15 15 25 4 Z" fill="#3b82f6" stroke="#1d4ed8" stroke-width="2"/><circle cx="25" cy="22" r="5" fill="#67e8f9" stroke="#0284c7" stroke-width="2"/><path d="M 15 28 L 5 38 L 15 40 Z" fill="#ef4444"/><path d="M 35 28 L 45 38 L 35 40 Z" fill="#ef4444"/><polygon points="20,40 25,48 30,40" fill="#f59e0b"/></svg>`;
                case 'car':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><path d="M 8 26 L 15 14 L 35 14 L 42 26 L 46 26 C 48 26 48 32 46 32 L 4 32 C 2 32 2 26 4 26 Z" fill="#ef4444" stroke="#b91c1c" stroke-width="2"/><rect x="18" y="16" width="14" height="8" fill="#e0f2fe"/><circle cx="14" cy="34" r="5" fill="#1e293b"/><circle cx="14" cy="34" r="2" fill="#94a3b8"/><circle cx="36" cy="34" r="5" fill="#1e293b"/><circle cx="36" cy="34" r="2" fill="#94a3b8"/></svg>`;
                case 'doll':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50">
                        <circle cx="25" cy="16" r="9" fill="#fed7aa" stroke="#f97316" stroke-width="1.5"/>
                        <path d="M 16 16 C 16 7 34 7 34 16 C 34 11 16 11 16 16 Z" fill="#b45309"/>
                        <circle cx="14" cy="16" r="3" fill="#f472b6"/>
                        <circle cx="36" cy="16" r="3" fill="#f472b6"/>
                        <circle cx="21" cy="16" r="1.5" fill="#1e293b"/>
                        <circle cx="29" cy="16" r="1.5" fill="#1e293b"/>
                        <path d="M 22 20 Q 25 23 28 20" stroke="#ef4444" stroke-width="1.5" fill="none"/>
                        <path d="M 18 25 L 32 25 L 37 42 L 13 42 Z" fill="#ec4899" stroke="#be185d" stroke-width="1.5"/>
                        <line x1="20" y1="42" x2="20" y2="47" stroke="#334155" stroke-width="3"/>
                        <line x1="30" y1="42" x2="30" y2="47" stroke="#334155" stroke-width="3"/>
                    </svg>`;
                case 'pencil':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><path d="M 10 38 L 34 14 L 40 20 L 16 44 Z" fill="#f59e0b" stroke="#d97706" stroke-width="2"/><path d="M 34 14 L 40 20 L 44 16 L 38 10 Z" fill="#f472b6"/><path d="M 10 38 L 16 44 L 6 46 Z" fill="#fef08a"/><path d="M 6 46 L 8 44 L 6 44 Z" fill="#1e293b"/></svg>`;
                case 'book':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50">
                        <path d="M 8 10 L 24 12 L 24 40 L 8 38 Z" fill="#0284c7" stroke="#0369a1" stroke-width="2"/>
                        <path d="M 42 10 L 26 12 L 26 40 L 42 38 Z" fill="#0369a1" stroke="#075985" stroke-width="2"/>
                        <path d="M 24 12 L 26 12 L 26 40 L 24 40 Z" fill="#e0f2fe"/>
                        <line x1="12" y1="18" x2="20" y2="19" stroke="#ffffff" stroke-width="2"/>
                        <line x1="12" y1="24" x2="20" y2="25" stroke="#ffffff" stroke-width="2"/>
                        <line x1="30" y1="19" x2="38" y2="18" stroke="#ffffff" stroke-width="2"/>
                        <line x1="30" y1="25" x2="38" y2="24" stroke="#ffffff" stroke-width="2"/>
                    </svg>`;
                case 'cat':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><circle cx="25" cy="28" r="16" fill="#f97316" stroke="#c2410c" stroke-width="2"/><polygon points="12,18 10,6 20,14" fill="#f97316"/><polygon points="38,18 40,6 30,14" fill="#f97316"/><circle cx="19" cy="25" r="3" fill="#1e293b"/><circle cx="31" cy="25" r="3" fill="#1e293b"/><polygon points="25,29 23,32 27,32" fill="#f472b6"/><path d="M 21 33 Q 25 37 29 33" stroke="#1e293b" stroke-width="2" fill="none"/></svg>`;
                case 'dog':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50">
                        <circle cx="25" cy="26" r="15" fill="#d97706" stroke="#78350f" stroke-width="2"/>
                        <ellipse cx="11" cy="22" rx="5" ry="10" fill="#92400e"/>
                        <ellipse cx="39" cy="22" rx="5" ry="10" fill="#92400e"/>
                        <ellipse cx="25" cy="30" rx="7" ry="5" fill="#fef3c7"/>
                        <ellipse cx="25" cy="28" rx="3" ry="2" fill="#1e293b"/>
                        <circle cx="19" cy="23" r="2.5" fill="#1e293b"/>
                        <circle cx="31" cy="23" r="2.5" fill="#1e293b"/>
                        <path d="M 25 32 Q 27 37 25 38 Q 23 37 25 32" fill="#f43f5e"/>
                    </svg>`;
                case 'treasure':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 50 50"><path d="M 8 20 L 42 20 L 42 38 C 42 41 39 42 36 42 L 14 42 C 11 42 8 41 8 38 Z" fill="#b45309" stroke="#78350f" stroke-width="2"/><path d="M 6 20 C 6 12 14 8 25 8 C 36 8 44 12 44 20 Z" fill="#d97706" stroke="#78350f" stroke-width="2"/><rect x="22" y="18" width="6" height="8" rx="1" fill="#f59e0b" stroke="#78350f" stroke-width="1"/><circle cx="25" cy="21" r="1.5" fill="#1e293b"/></svg>`;
                case 'check':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="none" stroke="#16a34a" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>`;
                case 'speakerOn':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="currentColor"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                case 'speakerOff':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="currentColor"><path d="M16.5 12c0-1.77-1.02-3.29-2.5-4.03v2.21l2.45 2.45c.03-.2.05-.41.05-.63zm2.5 0c0 .94-.2 1.82-.54 2.64l1.51 1.51C20.63 14.91 21 13.5 21 12c0-4.28-2.99-7.86-7-8.77v2.06c2.89.86 5 3.54 5 6.71zM4.27 3L3 4.27 7.73 9H3v6h4l5 5v-6.73l4.25 4.25c-.67.52-1.42.93-2.25 1.18v2.06c1.38-.31 2.63-.95 3.69-1.81L19.73 21 21 19.73 4.27 3zM12 4L9.91 6.09 12 8.18V4z"/></svg>`;
                case 'trophy':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="#f59e0b"><path d="M19 5h-2V3H7v2H5c-1.1 0-2 .9-2 2v1c0 2.55 1.92 4.63 4.39 4.94A5.01 5.01 0 0011 15.9V18H8v2h8v-2h-3v-2.1c2.28-.46 4-2.48 4-4.9v-1c0-1.1-.9-2-2-2zM5 8V7h2v3.82C5.84 10.4 5 9.3 5 8zm14 0c0 1.3-.84 2.4-2 2.82V7h2v1z"/></svg>`;
                case 'userIcon':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="currentColor"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>`;
                case 'cameraIcon':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="currentColor"><path d="M4 4h3l2-2h6l2 2h3a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2zm8 3a5 5 0 1 0 0 10 5 5 0 0 0 0-10zm0 2a3 3 0 1 1 0 6 3 3 0 0 1 0-6z"/></svg>`;
                case 'printIcon':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="currentColor"><path d="M19 8H5c-1.66 0-3 1.34-3 3v6h4v4h12v-4h4v-6c0-1.66-1.34-3-3-3zm-3 11H8v-5h8v5zm3-7c-.55 0-1-.45-1-1s.45-1 1-1 1 .45 1 1-.45 1-1 1zm-1-9H6v4h12V3z"/></svg>`;
                case 'rocketLaunch':
                    return `<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4.5 16.5c-1.5 1.26-2 5-2 5s3.74-.5 5-2c.71-.84.7-2.13-.09-2.91a2.18 2.18 0 0 0-2.91-.09z"/><path d="M12 15l-3-3a22 22 0 0 1 2-3.95A12.88 12.88 0 0 1 22 2c0 2.72-.78 7.5-3.05 11a22.35 22.35 0 0 1-3.95 2z"/></svg>`;
                default:
                    return '';
            }
        }

        /* ==========================================================================
           2. SINTETIZADOR DE AUDIO
           ========================================================================== */
        let soundEnabled = true;
        const AudioCtx = new (window.AudioContext || window.webkitAudioContext)();

        function toggleSound() {
            soundEnabled = !soundEnabled;
            const btn = document.getElementById('sound-btn');
            btn.innerHTML = soundEnabled ? getSvg('speakerOn', 18) : getSvg('speakerOff', 18);
        }

        function playSound(type) {
            if (!soundEnabled) return;
            if (AudioCtx.state === 'suspended') AudioCtx.resume();
            
            const osc = AudioCtx.createOscillator();
            const gain = AudioCtx.createGain();
            osc.connect(gain);
            gain.connect(AudioCtx.destination);
            const now = AudioCtx.currentTime;

            if (type === 'click') {
                osc.frequency.setValueAtTime(600, now);
                gain.gain.setValueAtTime(0.1, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.05);
                osc.start(now);
                osc.stop(now + 0.05);
            } else if (type === 'success') {
                osc.frequency.setValueAtTime(523.25, now);
                osc.frequency.exponentialRampToValueAtTime(880, now + 0.2);
                gain.gain.setValueAtTime(0.15, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.2);
                osc.start(now);
                osc.stop(now + 0.2);
            } else if (type === 'error') {
                osc.frequency.setValueAtTime(220, now);
                osc.frequency.exponentialRampToValueAtTime(110, now + 0.15);
                gain.gain.setValueAtTime(0.15, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.15);
                osc.start(now);
                osc.stop(now + 0.15);
            } else if (type === 'fanfare') {
                const notes = [523.25, 659.25, 783.99, 1046.50];
                notes.forEach((freq, idx) => {
                    const noteOsc = AudioCtx.createOscillator();
                    const noteGain = AudioCtx.createGain();
                    noteOsc.connect(noteGain);
                    noteGain.connect(AudioCtx.destination);
                    noteOsc.frequency.value = freq;
                    noteGain.gain.setValueAtTime(0.12, now + idx * 0.1);
                    noteGain.gain.exponentialRampToValueAtTime(0.01, now + idx * 0.1 + 0.25);
                    noteOsc.start(now + idx * 0.1);
                    noteOsc.stop(now + idx * 0.1 + 0.25);
                });
            }
        }

        /* ==========================================================================
           3. ESTADO GLOBAL DE LA PRUEBA (7 INDICADORES)
           ========================================================================== */
        const state = {
            studentName: 'Ana Rojas',
            section: '1-1',
            officialDate: '2026-09-21',
            sessionId: '',
            currentMission: 0,
            errors: {
                ind1: 0, ind2: 0, ind3: 0, ind4: 0, ind5: 0, ind6: 0, ind7: 0
            },
            m3TargetIdx: 0,
            m5ItemsDropped: 0
        };

        const successPhrases = ["¡Excelente!", "¡Muy bien!", "¡Lo lograste!", "¡Tito está feliz!", "¡Misión completada!"];
        const retryPhrases = ["¡Inténtalo otra vez!", "¡Casi lo logras!", "¡Busca nuevamente!", "Tito te ayuda."];

        function showFeedback(isSuccess, customMsg = null, poseOverride = null) {
            const toast = document.getElementById('tito-toast');
            let msg = customMsg;
            let pose = poseOverride;

            if (isSuccess) {
                if (!msg) msg = successPhrases[Math.floor(Math.random() * successPhrases.length)];
                if (!pose) pose = 'celebrating';
                playSound('success');
            } else {
                if (!msg) msg = retryPhrases[Math.floor(Math.random() * retryPhrases.length)];
                if (!pose) pose = 'encouraging';
                playSound('error');
            }

            document.getElementById('toast-tito-icon').innerHTML = getTitoSvg(pose, 40);
            document.getElementById('toast-msg').innerText = msg;
            toast.classList.remove('translate-y-28');
            setTimeout(() => toast.classList.add('translate-y-28'), 3000);
        }

        function updateProgressUI() {
            document.getElementById('header-student-name').innerText = state.studentName || 'Invitado';
            document.getElementById('dot-7').innerHTML = getSvg('trophy', 16);

            for (let i = 1; i <= 6; i++) {
                const dot = document.getElementById(`dot-${i}`);
                const line = document.getElementById(`line-${i}`);
                if (i < state.currentMission) {
                    dot.className = 'step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-emerald-500 text-white shadow';
                    if (line) line.className = 'h-1 w-2 bg-emerald-500';
                } else if (i === state.currentMission) {
                    dot.className = 'step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-amber-400 text-white shadow ring-2 ring-amber-300';
                    if (line) line.className = 'h-1 w-2 bg-amber-300';
                } else {
                    dot.className = 'step-dot font-heading text-xs font-bold w-7 h-7 rounded-full flex items-center justify-center bg-slate-200 text-slate-500';
                    if (line) line.className = 'h-1 w-2 bg-slate-200';
                }
            }
        }

        /* ==========================================================================
           4. RENDERIZADO DINO Y NAVEGACIÓN
           ========================================================================== */
        function render() {
            const viewport = document.getElementById('main-card-viewport');
            document.getElementById('header-tito-avatar').innerHTML = getTitoSvg('hello', 42);
            document.getElementById('sound-btn').innerHTML = soundEnabled ? getSvg('speakerOn', 18) : getSvg('speakerOff', 18);
            updateProgressUI();

            if (state.currentMission === 0) {
                renderWelcome(viewport);
            } else if (state.currentMission <= 6) {
                renderMissionContainer(viewport);
            } else {
                renderFinalReport(viewport);
            }
        }

        // PANTALLA INICIAL DE REGISTRO
        function renderWelcome(container) {
            container.innerHTML = `
                <section class="bg-white/95 backdrop-blur-md rounded-3xl p-6 sm:p-10 shadow-2xl border-4 border-amber-200 text-center relative overflow-hidden my-auto max-w-2xl mx-auto space-y-6">
                    <div class="w-36 h-36 mx-auto animate-gentle">${getTitoSvg('hello', 140)}</div>

                    <div class="space-y-2">
                        <span class="bg-sky-100 text-sky-700 text-xs font-bold px-4 py-1.5 rounded-full uppercase tracking-wider font-heading">Aventura Infantil de Clics</span>
                        <h2 class="text-3xl font-extrabold text-sky-900 font-heading">¡Hola! Soy Tito, tu amigo ratoncito</h2>
                        <p class="text-slate-600 text-sm sm:text-base">¿Estás listo para aprender a usar el mouse y explorar el mundo digital juntos?</p>
                    </div>

                    <div class="bg-amber-50/80 p-6 rounded-2xl border-2 border-amber-200 text-left space-y-4 max-w-md mx-auto shadow-inner">
                        <h3 class="font-heading text-amber-900 font-bold text-center text-base">Ingreso de Datos Oficiales</h3>
                        <div>
                            <label class="block text-xs font-bold text-slate-600 mb-1">Nombre completo del Estudiante:</label>
                            <input type="text" id="regName" class="w-full px-4 py-2.5 rounded-xl border border-amber-300 focus:ring-2 focus:ring-amber-500 focus:outline-none font-semibold text-slate-700" value="${state.studentName}">
                        </div>
                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label class="block text-xs font-bold text-slate-600 mb-1">Sección:</label>
                                <input type="text" id="regSec" class="w-full px-4 py-2.5 rounded-xl border border-amber-300 focus:ring-2 focus:ring-amber-500 focus:outline-none font-semibold text-slate-700" value="${state.section}">
                            </div>
                            <div>
                                <label class="block text-xs font-bold text-slate-600 mb-1">Fecha Oficial:</label>
                                <input type="date" id="regDate" class="w-full px-3 py-2 rounded-xl border border-amber-300 focus:ring-2 focus:ring-amber-500 focus:outline-none text-xs font-semibold text-slate-700" value="${state.officialDate}">
                            </div>
                        </div>
                    </div>

                    <button onclick="startAdventure()" class="w-full max-w-md mx-auto py-4 bg-gradient-to-r from-emerald-500 to-teal-500 hover:from-emerald-600 hover:to-teal-600 text-white font-heading text-xl font-bold rounded-2xl shadow-lg transform hover:-translate-y-1 transition duration-200 flex items-center justify-center gap-2">
                        ${getSvg('rocketLaunch', 24)}
                        <span>INICIAR LA AVENTURA</span>
                    </button>
                </section>
            `;
        }

        function startAdventure() {
            const name = document.getElementById('regName').value.trim();
            const sec = document.getElementById('regSec').value.trim();
            const date = document.getElementById('regDate').value;

            if (!name || !sec || !date) {
                alert("Por favor complete todos los datos requeridos.");
                return;
            }

            state.studentName = name;
            state.section = sec;
            state.officialDate = date;

            const cleanName = name.replace(/\s+/g, '_').toUpperCase();
            state.sessionId = `pruebaMouse_2026_${cleanName}_${Date.now().toString().slice(-6)}`;
            document.getElementById('session-badge-id').innerText = `SESIÓN: ${state.sessionId.slice(0, 22)}...`;

            playSound('fanfare');
            state.currentMission = 1;
            render();
        }

        // CONTENEDOR DE MISIÓN
        function renderMissionContainer(container) {
            const titles = [
                "",
                "Misión 1: Partes del Mouse",
                "Misión 2: Desplazamiento del Puntero",
                "Misión 3: Selección con Clic Izquierdo",
                "Misión 4: Clic Simple vs Doble Clic",
                "Misión 5: Almacén de Clasificación (Drag & Drop)",
                "Misión 6: Navegación Vertical con Rueda Scroll"
            ];

            const poses = ["", "explaining", "pointing", "thinking", "surprised", "explaining", "encouraging"];

            container.innerHTML = `
                <section class="bg-white rounded-3xl p-6 shadow-xl border-4 border-sky-200 flex flex-col items-center relative overflow-hidden">
                    ${getScenarioBg(state.currentMission)}

                    <div class="w-full flex justify-between items-center mb-3 z-10">
                        <span class="bg-sky-100 text-sky-800 font-bold px-3 py-1 rounded-full text-xs font-heading">MISIÓN ${state.currentMission} DE 6</span>
                        <span class="text-slate-400 text-xs font-semibold">Evaluación Práctica</span>
                    </div>

                    <div class="w-full bg-amber-50/90 border-2 border-amber-300 rounded-2xl p-4 flex items-center gap-4 mb-4 shadow-sm z-10 backdrop-blur-xs">
                        <div class="w-16 h-16 flex-shrink-0 animate-float">${getTitoSvg(poses[state.currentMission], 64)}</div>
                        <div>
                            <h3 class="font-heading font-bold text-sky-900 text-lg sm:text-xl">${titles[state.currentMission]}</h3>
                            <p id="mission-instruction-text" class="text-slate-700 text-sm font-medium">Sigue las instrucciones de Tito para avanzar.</p>
                        </div>
                    </div>

                    <div id="stage-area" class="w-full min-h-[360px] bg-slate-50/80 border-2 border-dashed border-slate-300 rounded-2xl flex items-center justify-center p-4 relative overflow-hidden z-10">
                    </div>
                </section>
            `;

            loadStageContent(state.currentMission);
        }

        function loadStageContent(m) {
            const stage = document.getElementById('stage-area');
            const instr = document.getElementById('mission-instruction-text');

            // MISIÓN 1: PARTES DEL MOUSE
            if (m === 1) {
                let currentTarget = 'left';
                instr.innerHTML = `Tito dice: "Haz clic en el <strong class="text-amber-700 font-extrabold underline">BOTÓN IZQUIERDO</strong> que usamos para seleccionar cosas."`;

                stage.innerHTML = `
                    <div class="text-center">
                        <svg class="w-80 h-80 mx-auto filter drop-shadow-lg" viewBox="0 0 240 260">
                            <path id="btn-left" class="mouse-btn" d="M 30 30 Q 120 30 120 100 L 30 100 Z" fill="#3b82f6"/>
                            <path id="btn-right" class="mouse-btn" d="M 120 30 Q 210 30 210 100 L 120 100 Z" fill="#60a5fa"/>
                            <rect id="btn-wheel" class="mouse-btn" x="108" y="50" width="24" height="40" rx="10" fill="#f59e0b"/>
                            <path d="M 30 100 L 210 100 Q 210 240 120 250 Q 30 240 30 100 Z" fill="#cbd5e1"/>
                        </svg>
                    </div>
                `;

                showFeedback(true, "Tito dice: Haz clic en el BOTÓN IZQUIERDO.", 'explaining');

                const checkPart = (partKey) => {
                    if (partKey === currentTarget) {
                        if (partKey === 'left') {
                            currentTarget = 'right';
                            instr.innerHTML = `Tito dice: "¡Muy bien! Ahora haz clic en el <strong class="text-amber-700 font-extrabold underline">BOTÓN DERECHO</strong>."`;
                            showFeedback(true, "¡Muy bien! Ahora toca el BOTÓN DERECHO.", 'encouraging');
                        } else if (partKey === 'right') {
                            currentTarget = 'wheel';
                            instr.innerHTML = `Tito dice: "¡Genial! Ahora haz clic en la <strong class="text-amber-700 font-extrabold underline">RUEDA DE SCROLL</strong>."`;
                            showFeedback(true, "¡Excelente! Ahora toca la RUEDA DE SCROLL.", 'pointing');
                        } else if (partKey === 'wheel') {
                            showFeedback(true, "¡Misión completada!", 'celebrating');
                            setTimeout(() => { state.currentMission = 2; render(); }, 1500);
                        }
                    } else {
                        if (currentTarget === 'left') state.errors.ind1++;
                        else state.errors.ind2++;
                        showFeedback(false, "¡Inténtalo otra vez!", 'thinking');
                    }
                };

                document.getElementById('btn-left').onclick = () => checkPart('left');
                document.getElementById('btn-right').onclick = () => checkPart('right');
                document.getElementById('btn-wheel').onclick = () => checkPart('wheel');
            }

            // MISIÓN 2: DESPLAZAMIENTO DEL PUNTERO
            else if (m === 2) {
                const order = ['ARRIBA', 'ABAJO', 'IZQUIERDA', 'DERECHA'];
                let idx = 0;

                stage.innerHTML = `
                    <div class="grid grid-cols-3 gap-4 w-full max-w-md h-80">
                        <div></div>
                        <div class="dir-zone border-2 border-dashed border-slate-400 rounded-2xl flex flex-col items-center justify-center cursor-pointer p-2 bg-white/90 shadow-sm transition" id="z-ARRIBA">${getSvg('star', 40)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">ARRIBA</span></div>
                        <div></div>
                        <div class="dir-zone border-2 border-dashed border-slate-400 rounded-2xl flex flex-col items-center justify-center cursor-pointer p-2 bg-white/90 shadow-sm transition" id="z-IZQUIERDA">${getSvg('robot', 40)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">IZQUIERDA</span></div>
                        <div class="flex items-center justify-center">${getTitoSvg('pointing', 52)}</div>
                        <div class="dir-zone border-2 border-dashed border-slate-400 rounded-2xl flex flex-col items-center justify-center cursor-pointer p-2 bg-white/90 shadow-sm transition" id="z-DERECHA">${getSvg('rocket', 40)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">DERECHA</span></div>
                        <div></div>
                        <div class="dir-zone border-2 border-dashed border-slate-400 rounded-2xl flex flex-col items-center justify-center cursor-pointer p-2 bg-white/90 shadow-sm transition" id="z-ABAJO">${getSvg('ball', 40)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">ABAJO</span></div>
                        <div></div>
                    </div>
                `;

                const updateTargets = () => {
                    document.querySelectorAll('.dir-zone').forEach(el => el.classList.remove('border-blue-500', 'bg-blue-50', 'scale-105'));
                    const activeEl = document.getElementById(`z-${order[idx]}`);
                    activeEl.classList.add('border-blue-500', 'bg-blue-50', 'scale-105');
                    instr.innerHTML = `Tito dice: "Lleva el puntero del mouse hacia <strong class="text-amber-700 font-extrabold underline">${order[idx]}</strong>."`;
                    showFeedback(true, `Mueve el puntero hacia ${order[idx]}`, 'pointing');
                };

                updateTargets();

                ['ARRIBA', 'ABAJO', 'IZQUIERDA', 'DERECHA'].forEach(dir => {
                    const zone = document.getElementById(`z-${dir}`);
                    zone.onmouseenter = () => {
                        if (dir === order[idx]) {
                            idx++;
                            if (idx < order.length) {
                                updateTargets();
                            } else {
                                showFeedback(true, "¡Lo lograste! Excelente control del puntero.", 'celebrating');
                                setTimeout(() => { state.currentMission = 3; render(); }, 1500);
                            }
                        } else {
                            state.errors.ind3++;
                            showFeedback(false, "Tito te ayuda. ¡Busca nuevamente!", 'thinking');
                        }
                    };
                });
            }

            // MISIÓN 3: SELECCIÓN CLIC
            else if (m === 3) {
                const targets = ['car', 'robot', 'star'];
                const names = { car: 'Carro', robot: 'Robot', star: 'Estrella' };
                state.m3TargetIdx = 0;

                instr.innerHTML = `Tito dice: "Encuentra y haz clic sobre el <strong class="text-amber-700 font-extrabold underline">${names[targets[0]]}</strong>."`;

                stage.innerHTML = `
                    <div class="grid grid-cols-3 gap-4 w-full max-w-lg">
                        <div class="w-24 h-24 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-pointer hover:border-blue-500 hover:scale-105 transition p-2 shadow-md mx-auto" id="obj-car">${getSvg('car', 48)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">Carro</span></div>
                        <div class="w-24 h-24 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-pointer hover:border-blue-500 hover:scale-105 transition p-2 shadow-md mx-auto" id="obj-pencil">${getSvg('pencil', 48)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">Lápiz</span></div>
                        <div class="w-24 h-24 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-pointer hover:border-blue-500 hover:scale-105 transition p-2 shadow-md mx-auto" id="obj-robot">${getSvg('robot', 48)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">Robot</span></div>
                        <div class="w-24 h-24 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-pointer hover:border-blue-500 hover:scale-105 transition p-2 shadow-md mx-auto" id="obj-ball">${getSvg('ball', 48)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">Pelota</span></div>
                        <div class="w-24 h-24 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-pointer hover:border-blue-500 hover:scale-105 transition p-2 shadow-md mx-auto" id="obj-star">${getSvg('star', 48)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">Estrella</span></div>
                        <div class="w-24 h-24 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-pointer hover:border-blue-500 hover:scale-105 transition p-2 shadow-md mx-auto" id="obj-cat">${getSvg('cat', 48)}<span class="font-bold text-xs mt-1 text-slate-700 font-heading">Gato</span></div>
                    </div>
                `;

                showFeedback(true, `Haz clic sobre el ${names[targets[0]]}`, 'pointing');

                ['car', 'pencil', 'robot', 'ball', 'star', 'cat'].forEach(objKey => {
                    document.getElementById(`obj-${objKey}`).onclick = () => {
                        const expected = targets[state.m3TargetIdx];
                        if (objKey === expected) {
                            state.m3TargetIdx++;
                            if (state.m3TargetIdx < targets.length) {
                                instr.innerHTML = `Tito dice: "¡Excelente! Ahora haz clic sobre la <strong class="text-amber-700 font-extrabold underline">${names[targets[state.m3TargetIdx]]}</strong>."`;
                                showFeedback(true, `¡Muy bien! Ahora busca el ${names[targets[state.m3TargetIdx]]}`, 'encouraging');
                            } else {
                                showFeedback(true, "¡Tito está feliz! Misión completada.", 'celebrating');
                                setTimeout(() => { state.currentMission = 4; render(); }, 1500);
                            }
                        } else {
                            state.errors.ind4++;
                            showFeedback(false, "¡Casi lo logras! Busca nuevamente.", 'thinking');
                        }
                    };
                });
            }

            // MISIÓN 4: CLIC SIMPLE Y DOBLE CLIC
            else if (m === 4) {
                let step = 0;
                instr.innerHTML = `Tito dice: "Haz <strong class="text-amber-700 font-extrabold underline">1 CLIC SIMPLE</strong> sobre el CARRITO."`;

                stage.innerHTML = `
                    <div class="flex flex-col sm:flex-row gap-8 justify-center items-center">
                        <div id="card-car" class="w-36 h-36 bg-white/90 border-4 border-amber-400 rounded-3xl flex flex-col items-center justify-center cursor-pointer hover:scale-105 transition shadow-lg p-2">
                            ${getSvg('car', 64)}
                            <span class="font-bold text-xs text-slate-700 mt-2 font-heading">1 Clic: Carrito</span>
                        </div>
                        <div id="card-doll" class="w-36 h-36 bg-white/90 border-4 border-slate-200 opacity-50 rounded-3xl flex flex-col items-center justify-center cursor-pointer transition shadow-lg p-2">
                            ${getSvg('doll', 64)}
                            <span class="font-bold text-xs text-slate-500 mt-2 font-heading">Doble Clic: Muñeca</span>
                        </div>
                    </div>
                `;

                showFeedback(true, "Haz 1 CLIC SIMPLE sobre el carrito.", 'explaining');

                let timer = null;
                const carEl = document.getElementById('card-car');
                const dollEl = document.getElementById('card-doll');

                carEl.onclick = () => {
                    if (step === 0) {
                        step = 1;
                        carEl.classList.add('opacity-50', 'border-slate-200');
                        carEl.classList.remove('border-amber-400');
                        dollEl.classList.remove('opacity-50', 'border-slate-200');
                        dollEl.classList.add('border-amber-400', 'hover:scale-105');

                        instr.innerHTML = `Tito dice: "¡Muy bien! Ahora haz <strong class="text-amber-700 font-extrabold underline">DOBLE CLIC RÁPIDO</strong> sobre la MUÑECA."`;
                        showFeedback(true, "¡Muy bien! Ahora haz DOBLE CLIC en la muñeca.", 'surprised');
                    }
                };

                dollEl.onclick = () => {
                    if (step === 1) {
                        timer = setTimeout(() => {
                            state.errors.ind5++;
                            showFeedback(false, "¡Inténtalo otra vez! Dos clics rápidos.", 'thinking');
                        }, 300);
                    }
                };

                dollEl.ondblclick = () => {
                    if (step === 1) {
                        clearTimeout(timer);
                        showFeedback(true, "¡Lo lograste! Tito está feliz.", 'celebrating');
                        setTimeout(() => { state.currentMission = 5; render(); }, 1500);
                    }
                };
            }

            // MISIÓN 5: DRAG & DROP
            else if (m === 5) {
                state.m5ItemsDropped = 0;
                instr.innerHTML = `Tito dice: "Arrastra los 6 objetos hacia su categoría correspondiente."`;

                stage.innerHTML = `
                    <div class="w-full space-y-4">
                        <div class="flex flex-wrap gap-3 justify-center" id="pool">
                            <div class="w-20 h-20 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-grab active:cursor-grabbing p-1 shadow" draggable="true" id="drag-pelota" data-cat="juguete">${getSvg('ball', 40)}<span class="font-bold text-[10px] text-slate-700 font-heading mt-1">Pelota</span></div>
                            <div class="w-20 h-20 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-grab active:cursor-grabbing p-1 shadow" draggable="true" id="drag-carro" data-cat="juguete">${getSvg('car', 40)}<span class="font-bold text-[10px] text-slate-700 font-heading mt-1">Carro</span></div>
                            <div class="w-20 h-20 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-grab active:cursor-grabbing p-1 shadow" draggable="true" id="drag-lapiz" data-cat="util">${getSvg('pencil', 40)}<span class="font-bold text-[10px] text-slate-700 font-heading mt-1">Lápiz</span></div>
                            <div class="w-20 h-20 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-grab active:cursor-grabbing p-1 shadow" draggable="true" id="drag-libro" data-cat="util">${getSvg('book', 40)}<span class="font-bold text-[10px] text-slate-700 font-heading mt-1">Libro</span></div>
                            <div class="w-20 h-20 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-grab active:cursor-grabbing p-1 shadow" draggable="true" id="drag-gato" data-cat="animal">${getSvg('cat', 40)}<span class="font-bold text-[10px] text-slate-700 font-heading mt-1">Gato</span></div>
                            <div class="w-20 h-20 bg-white/90 border-2 border-slate-300 rounded-2xl flex flex-col items-center justify-center cursor-grab active:cursor-grabbing p-1 shadow" draggable="true" id="drag-perro" data-cat="animal">${getSvg('dog', 40)}<span class="font-bold text-[10px] text-slate-700 font-heading mt-1">Perro</span></div>
                        </div>

                        <div class="grid grid-cols-3 gap-3 w-full">
                            <div class="min-h-[150px] bg-white/90 border-2 border-dashed border-slate-400 rounded-2xl p-2 flex flex-col items-center gap-2 drop-zone" id="zone-juguete">
                                <h4 class="font-bold text-xs text-blue-800 uppercase font-heading">JUGUETES</h4>
                            </div>
                            <div class="min-h-[150px] bg-white/90 border-2 border-dashed border-slate-400 rounded-2xl p-2 flex flex-col items-center gap-2 drop-zone" id="zone-util">
                                <h4 class="font-bold text-xs text-blue-800 uppercase font-heading">ÚTILES</h4>
                            </div>
                            <div class="min-h-[150px] bg-white/90 border-2 border-dashed border-slate-400 rounded-2xl p-2 flex flex-col items-center gap-2 drop-zone" id="zone-animal">
                                <h4 class="font-bold text-xs text-blue-800 uppercase font-heading">ANIMALES</h4>
                            </div>
                        </div>
                    </div>
                `;

                showFeedback(true, "Arrastra los objetos a sus cajas correspondientes.", 'explaining');

                const items = stage.querySelectorAll('[draggable="true"]');
                const zones = stage.querySelectorAll('.drop-zone');

                items.forEach(item => {
                    item.ondragstart = (e) => {
                        e.dataTransfer.setData('text/plain', item.id);
                    };
                });

                zones.forEach(zone => {
                    zone.ondragover = (e) => e.preventDefault();
                    zone.ondrop = (e) => {
                        e.preventDefault();
                        const itemId = e.dataTransfer.getData('text/plain');
                        const draggedEl = document.getElementById(itemId);

                        if (!draggedEl) return;

                        const itemCat = draggedEl.getAttribute('data-cat');
                        const targetCat = zone.id.replace('zone-', '');

                        zone.appendChild(draggedEl);
                        draggedEl.setAttribute('draggable', 'false');

                        if (itemCat !== targetCat) {
                            state.errors.ind6++;
                            showFeedback(false, "Tito te ayuda.", 'thinking');
                        } else {
                            showFeedback(true, "¡Excelente!", 'encouraging');
                        }

                        state.m5ItemsDropped++;
                        if (state.m5ItemsDropped === 6) {
                            showFeedback(true, "¡Misión completada!", 'celebrating');
                            setTimeout(() => { state.currentMission = 6; render(); }, 1500);
                        }
                    };
                });
            }

            // MISIÓN 6: RUEDA SCROLL
            else if (m === 6) {
                instr.innerHTML = `Tito dice: "Usa la <strong class="text-amber-700 font-extrabold underline">RUEDA SCROLL</strong> para bajar por los estantes hasta encontrar el tesoro."`;

                stage.innerHTML = `
                    <div class="h-80 overflow-y-scroll w-full border-2 border-slate-300 rounded-2xl p-4 bg-amber-50/60 shadow-inner" id="scrollBox">
                        <div class="min-h-[900px] flex flex-col justify-between items-center py-4 space-y-12">
                            <div class="text-center bg-white p-3 rounded-xl border border-amber-200 shadow-sm">
                                <p class="font-bold text-xs text-slate-600">Gira la rueda del mouse hacia abajo para explorar los estantes...</p>
                            </div>

                            <div class="w-full max-w-md bg-white border-b-4 border-amber-800 p-3 rounded-t-xl flex justify-around items-center shadow-md">
                                ${getSvg('book', 40)}
                                ${getSvg('pencil', 40)}
                                ${getSvg('robot', 40)}
                            </div>

                            <div class="w-full max-w-md bg-white border-b-4 border-amber-800 p-3 rounded-t-xl flex justify-around items-center shadow-md">
                                ${getSvg('star', 40)}
                                ${getSvg('ball', 40)}
                                ${getSvg('car', 40)}
                            </div>

                            <div class="w-full max-w-md bg-white border-b-4 border-amber-800 p-3 rounded-t-xl flex justify-around items-center shadow-md">
                                ${getSvg('doll', 40)}
                                ${getSvg('dog', 40)}
                                ${getSvg('cat', 40)}
                            </div>

                            <div class="bg-amber-100 border-2 border-amber-500 rounded-2xl p-4 flex items-center gap-3 cursor-pointer hover:scale-105 transition shadow-xl" id="scrollTreasure">
                                ${getSvg('treasure', 50)}
                                <span class="font-heading font-bold text-sm text-amber-900">¡Tesoro Encontrado! (Haz Clic)</span>
                            </div>
                        </div>
                    </div>
                `;

                showFeedback(true, "Usa la rueda de scroll para bajar.", 'explaining');

                let scrolled = false;
                document.getElementById('scrollBox').onscroll = () => { scrolled = true; };

                document.getElementById('scrollTreasure').onclick = () => {
                    if (!scrolled) {
                        state.errors.ind7++;
                    }
                    playSound('fanfare');
                    showFeedback(true, "¡Lo lograste! Prueba completada.", 'celebrating');
                    setTimeout(() => { state.currentMission = 7; render(); }, 1500);
                };
            }
        }

        /* ==========================================================================
           5. PANTALLA FINAL Y REPORTE DOCENTE OFICIAL (7 INDICADORES / 21 PTS)
           ========================================================================== */
        function renderFinalReport(container) {
            // Ocultar notificación de Tito al cargar el reporte
            const toast = document.getElementById('tito-toast');
            if (toast) toast.classList.add('translate-y-28');

            const getScoreAndBadge = (errCount) => {
                if (errCount === 0) return { pts: 3, label: 'Avanzado', css: 'badge-avanzado', errs: 0 };
                if (errCount <= 2) return { pts: 2, label: 'Intermedio', css: 'badge-bueno', errs: errCount };
                return { pts: 1, label: 'Por mejorar', css: 'badge-mejorar', errs: errCount };
            };

            const indScores = [
                getScoreAndBadge(state.errors.ind1),
                getScoreAndBadge(state.errors.ind2),
                getScoreAndBadge(state.errors.ind3),
                getScoreAndBadge(state.errors.ind4),
                getScoreAndBadge(state.errors.ind5),
                getScoreAndBadge(state.errors.ind6),
                getScoreAndBadge(state.errors.ind7)
            ];

            const totalEarned = indScores.reduce((acc, curr) => acc + curr.pts, 0);
            const totalErrors = Object.values(state.errors).reduce((acc, curr) => acc + curr, 0);
            const percentage = Math.round((totalEarned / 21) * 100);

            const indTitles = [
                "1. Identifica y ejecuta el botón izquierdo del mouse.",
                "2. Reconoce el botón derecho y la rueda de scroll del mouse.",
                "3. Desplaza el puntero en las 4 direcciones principales (Arriba, Abajo, Izquierda, Derecha).",
                "4. Realiza clic izquierdo para seleccionar objetos específicos indicados.",
                "5. Discrimina y ejecuta correctamente las acciones de Clic Simple y Doble Clic.",
                "6. Aplica la técnica de arrastrar y soltar (Drag & Drop) para clasificar elementos.",
                "7. Utiliza la rueda de desplazamiento (Scroll) para la navegación vertical."
            ];

            container.innerHTML = `
                <div class="bg-white rounded-3xl p-6 shadow-xl border-4 border-blue-200 relative overflow-hidden">
                    <div class="flex justify-center mb-4">${getTitoSvg('celebrating', 100)}</div>

                    <div class="text-center border-b-2 border-slate-200 pb-4 mb-6">
                        <h2 class="text-2xl font-extrabold text-blue-900 font-heading">COLEGIO DIOCESANO PADRE ELADIO SANCHO</h2>
                        <h3 class="text-lg font-bold text-blue-600 font-heading">Informe Docente de Prueba de Ejecución II Semestre, 2026</h3>
                        <p class="text-xs text-slate-500 font-semibold">Informática Educativa - Primer Grado</p>
                    </div>

                    <div class="bg-slate-50 border border-slate-200 rounded-2xl p-4 grid grid-cols-2 md:grid-cols-5 gap-4 mb-6 text-sm">
                        <div>
                            <span class="block text-xs font-semibold text-slate-500">Estudiante:</span>
                            <span class="font-extrabold text-slate-800">${state.studentName}</span>
                        </div>
                        <div>
                            <span class="block text-xs font-semibold text-slate-500">Sección:</span>
                            <span class="font-extrabold text-slate-800">${state.section}</span>
                        </div>
                        <div>
                            <span class="block text-xs font-semibold text-slate-500">Fecha:</span>
                            <span class="font-extrabold text-slate-800">${state.officialDate}</span>
                        </div>
                        <div>
                            <span class="block text-xs font-semibold text-slate-500">Puntaje Obtenido:</span>
                            <span class="text-lg font-black text-blue-700">${totalEarned} / 21 pts (${percentage}%)</span>
                        </div>
                        <div>
                            <span class="block text-xs font-semibold text-amber-700">Total Errores / Reintentos:</span>
                            <span class="text-lg font-black text-amber-600">${totalErrors} error(es)</span>
                        </div>
                    </div>

                    <h4 class="font-heading font-bold text-slate-900 mb-3">1. Rúbrica Analítica de Evaluación (7 Indicadores - Base 21 Puntos)</h4>
                    <div class="overflow-x-auto mb-6">
                        <table class="w-full text-xs text-left border-collapse border border-slate-300">
                            <thead>
                                <tr class="bg-slate-100 text-slate-700 font-bold">
                                    <th class="border border-slate-300 p-2 w-8">#</th>
                                    <th class="border border-slate-300 p-2">Indicador de Desempeño</th>
                                    <th class="border border-slate-300 p-2 w-28 text-center bg-amber-50 text-amber-900">Errores / Reintentos</th>
                                    <th class="border border-slate-300 p-2 w-32">Nivel Alcanzado</th>
                                    <th class="border border-slate-300 p-2 w-28 text-center">Puntos (1-3)</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${indScores.map((score, i) => `
                                    <tr class="hover:bg-slate-50">
                                        <td class="border border-slate-300 p-2 font-bold">${i + 1}</td>
                                        <td class="border border-slate-300 p-2">${indTitles[i]}</td>
                                        <td class="border border-slate-300 p-2 text-center font-bold bg-amber-50/50 ${score.errs > 0 ? 'text-amber-700' : 'text-slate-400'}">${score.errs}</td>
                                        <td class="border border-slate-300 p-2"><span class="px-2 py-0.5 rounded-full font-bold text-[11px] ${score.css}">${score.label}</span></td>
                                        <td class="border border-slate-300 p-2 text-center font-extrabold">${score.pts} / 3</td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                    </div>

                    <h4 class="font-heading font-bold text-slate-900 mb-3">2. Resumen "Lo Que Hice Hoy" (Registro Automático)</h4>
                    <div class="overflow-x-auto mb-6">
                        <table class="w-full text-xs text-left border-collapse border border-slate-300">
                            <thead>
                                <tr class="bg-slate-100 text-slate-700 font-bold">
                                    <th class="border border-slate-300 p-2">Actividad Práctica</th>
                                    <th class="border border-slate-300 p-2">Acción Registrada por el Sistema</th>
                                    <th class="border border-slate-300 p-2 w-28">Estado</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="border border-slate-300 p-2">Exploración de Partes del Mouse</td>
                                    <td class="border border-slate-300 p-2">Verificación de botones y rueda </td>
                                    <td class="border border-slate-300 p-2 font-bold text-emerald-600 flex items-center gap-1">${getSvg('check', 16)} Logrado</td>
                                </tr>
                                <tr>
                                    <td class="border border-slate-300 p-2">Desplazamiento del Puntero</td>
                                    <td class="border border-slate-300 p-2">Navegación en 4 cuadrantes</td>
                                    <td class="border border-slate-300 p-2 font-bold text-emerald-600 flex items-center gap-1">${getSvg('check', 16)} Logrado</td>
                                </tr>
                                <tr>
                                    <td class="border border-slate-300 p-2">Selección de Objetos (Clic Izquierdo)</td>
                                    <td class="border border-slate-300 p-2">Clic izquierdo de precisión</td>
                                    <td class="border border-slate-300 p-2 font-bold text-emerald-600 flex items-center gap-1">${getSvg('check', 16)} Logrado</td>
                                </tr>
                                <tr>
                                    <td class="border border-slate-300 p-2">Diferenciación Clic / Doble Clic</td>
                                    <td class="border border-slate-300 p-2">Ejecución de eventos sobre carrito y muñeca</td>
                                    <td class="border border-slate-300 p-2 font-bold text-emerald-600 flex items-center gap-1">${getSvg('check', 16)} Logrado</td>
                                </tr>
                                <tr>
                                    <td class="border border-slate-300 p-2">Clasificación Drag & Drop</td>
                                    <td class="border border-slate-300 p-2">Arrastre de 6 objetos en cajas</td>
                                    <td class="border border-slate-300 p-2 font-bold text-emerald-600 flex items-center gap-1">${getSvg('check', 16)} Logrado</td>
                                </tr>
                                <tr>
                                    <td class="border border-slate-300 p-2">Navegación con Rueda Scroll</td>
                                    <td class="border border-slate-300 p-2">Desplazamiento vertical en estantería</td>
                                    <td class="border border-slate-300 p-2 font-bold text-emerald-600 flex items-center gap-1">${getSvg('check', 16)} Logrado</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>

                    <div class="bg-slate-50 border-l-4 border-blue-500 p-4 rounded-r-xl mb-6">
                        <h4 class="font-bold text-sm text-slate-800 mb-1">Observaciones Automáticas del Sistema:</h4>
                        <p class="text-xs text-slate-600">${totalErrors === 0 
                            ? 'El estudiante completó la prueba con ejecución impecable y sin registrar ningún fallo o reintento.' 
                            : `El estudiante completó la prueba registrando un total de ${totalErrors} error(es)/reintento(s) acumulados a lo largo de las 6 misiones.`}</p>
                    </div>

                    <div class="flex flex-wrap justify-center gap-4 no-print">
                        <button onclick="resetApp()" class="px-5 py-2.5 rounded-xl bg-slate-200 text-slate-700 font-bold text-xs hover:bg-slate-300 transition flex items-center gap-2">
                            ${getSvg('userIcon', 16)}
                            <span>Nuevo Estudiante</span>
                        </button>
                        <button onclick="savePNG()" class="px-5 py-2.5 rounded-xl bg-emerald-600 text-white font-bold text-xs hover:bg-emerald-700 transition flex items-center gap-2">
                            ${getSvg('cameraIcon', 16)}
                            <span>GUARDAR EVIDENCIA (PNG)</span>
                        </button>
                        <button onclick="window.print()" class="px-5 py-2.5 rounded-xl bg-blue-600 text-white font-bold text-xs hover:bg-blue-700 transition flex items-center gap-2">
                            ${getSvg('printIcon', 16)}
                            <span>IMPRIMIR / GUARDAR REPORTE (PDF)</span>
                        </button>
                    </div>
                </div>
            `;
        }

        function resetApp() {
            if (confirm("¿Desea iniciar una nueva prueba con otro estudiante?")) {
                state.currentMission = 0;
                state.studentName = 'Ana Rojas';
                Object.keys(state.errors).forEach(k => state.errors[k] = 0);
                document.getElementById('session-badge-id').innerText = 'SESIÓN: Inactiva';
                render();
            }
        }

        function savePNG() {
            alert("Para guardar el informe en formato PDF o impreso digital, presione 'IMPRIMIR / GUARDAR REPORTE (PDF)' y elija la opción 'Guardar como PDF' en su navegador.");
            window.print();
        }

        // INICIALIZACIÓN
        render();
    </script>
</body>
</html>
