<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Colegio Diocesano Padre Eladio Sancho - Prueba de Ejecución 2026</title>
  <style>
    :root {
      --primary: #2563eb;
      --primary-dark: #1d4ed8;
      --header-bg: linear-gradient(135deg, #1e40af 0%, #2563eb 100%);
      --bg-body: #f8fafc;
      --card-bg: #ffffff;
      --text-main: #1e293b;
      --text-muted: #64748b;
      --success-bg: #dcfce7;
      --success-text: #15803d;
      --warning-bg: #fef9c3;
      --warning-text: #a16207;
      --danger-bg: #fee2e2;
      --danger-text: #b91c1c;
      --border-color: #e2e8f0;
      --radius: 16px;
    }

    * {
      box-sizing: border-box;
      user-select: none;
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    }

    body {
      margin: 0;
      padding: 0;
      background-color: #cbd5e1;
      color: var(--text-main);
      display: flex;
      justify-content: center;
      min-height: 100vh;
    }

    .app-viewport {
      width: 100%;
      max-width: 1120px;
      background: var(--bg-body);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    }

    /* TOP HEADER INSTITUCIONAL */
    .top-header {
      background: var(--header-bg);
      color: white;
      padding: 16px 28px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    .top-header h1 {
      font-size: 1.35rem;
      margin: 0;
      font-weight: 800;
      letter-spacing: 0.5px;
      text-transform: uppercase;
    }

    .top-header p {
      margin: 3px 0 0 0;
      font-size: 0.9rem;
      opacity: 0.9;
    }

    .session-badge {
      background: rgba(255,255,255,0.18);
      border: 1px solid rgba(255,255,255,0.3);
      padding: 6px 16px;
      border-radius: 20px;
      font-size: 0.82rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 8px;
      backdrop-filter: blur(4px);
    }

    .session-badge .dot {
      width: 10px;
      height: 10px;
      background-color: #22c55e;
      border-radius: 50%;
      box-shadow: 0 0 8px #22c55e;
    }

    /* MAIN CONTAINER */
    .main-content {
      padding: 24px;
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .card {
      background: var(--card-bg);
      border-radius: var(--radius);
      border: 1px solid var(--border-color);
      padding: 24px;
      box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
      margin-bottom: 20px;
    }

    /* REGISTRO INICIAL */
    .register-box {
      max-width: 500px;
      margin: 40px auto;
      text-align: center;
    }

    .register-box h2 {
      color: var(--primary-dark);
      margin-top: 0;
    }

    .form-group {
      text-align: left;
      margin-bottom: 16px;
    }

    .form-group label {
      display: block;
      font-size: 0.9rem;
      font-weight: 700;
      margin-bottom: 6px;
      color: #334155;
    }

    .form-control {
      width: 100%;
      padding: 12px 16px;
      border: 2px solid #cbd5e1;
      border-radius: 10px;
      font-size: 1rem;
      outline: none;
    }

    .form-control:focus {
      border-color: var(--primary);
    }

    .btn-primary {
      background: var(--primary);
      color: white;
      border: none;
      padding: 14px 28px;
      font-size: 1.1rem;
      font-weight: 700;
      border-radius: 12px;
      cursor: pointer;
      width: 100%;
      transition: background 0.2s;
    }

    .btn-primary:hover {
      background: var(--primary-dark);
    }

    /* MISIONES Y ESCENARIO */
    .mission-header {
      display: flex;
      align-items: center;
      gap: 16px;
      background: #f1f5f9;
      padding: 14px 20px;
      border-radius: 12px;
      margin-bottom: 20px;
    }

    .tito-avatar {
      width: 60px;
      height: 60px;
      flex-shrink: 0;
    }

    .stage-canvas {
      min-height: 380px;
      background: #fafafa;
      border: 2px dashed #cbd5e1;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      padding: 20px;
      overflow: hidden;
    }

    /* MISIÓN 1: MOUSE SVG MEJORADO */
    .mouse-svg-container {
      width: 320px;
      height: 320px;
    }

    .mouse-btn {
      cursor: pointer;
      transition: filter 0.2s;
    }

    .mouse-btn:hover {
      filter: brightness(1.15);
    }

    .mouse-text {
      font-size: 15px;
      font-weight: 800;
      fill: #0f172a;
      text-anchor: middle;
      pointer-events: none;
    }

    /* MISIÓN 2: DIRECCIONES */
    .grid-directions {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      width: 100%;
      max-width: 420px;
      height: 320px;
    }

    .dir-zone {
      background: white;
      border: 2px dashed #94a3b8;
      border-radius: 12px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-weight: 800;
      cursor: pointer;
      transition: all 0.2s;
    }

    .dir-zone.active-target {
      border-color: var(--primary);
      background: #eff6ff;
      color: var(--primary-dark);
      transform: scale(1.04);
    }

    /* MISIÓN 3: MUNDO DE OBJETOS */
    .objects-grid {
      display: flex;
      gap: 24px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .obj-card {
      width: 110px;
      height: 110px;
      background: white;
      border: 2px solid #cbd5e1;
      border-radius: 16px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-size: 2.8rem;
      cursor: pointer;
      box-shadow: 0 4px 6px rgba(0,0,0,0.05);
      transition: transform 0.2s;
    }

    .obj-card:hover {
      transform: scale(1.08);
    }

    /* MISIÓN 6: ALMACÉN DRAG & DROP */
    .drag-pool {
      display: flex;
      gap: 16px;
      margin-bottom: 24px;
      justify-content: center;
    }

    .drop-zones-container {
      display: flex;
      gap: 16px;
      width: 100%;
    }

    .drop-target-box {
      flex: 1;
      min-height: 160px;
      background: #f8fafc;
      border: 2px dashed #94a3b8;
      border-radius: 14px;
      padding: 12px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }

    .drop-target-box h4 {
      margin: 0;
      color: var(--primary-dark);
      font-size: 0.95rem;
    }

    /* PANTALLA FINAL / REPORTE DOCENTE (ESTILO EXACTO A CAPTURAS) */
    .report-header {
      text-align: center;
      border-bottom: 2px solid #e2e8f0;
      padding-bottom: 16px;
      margin-bottom: 20px;
    }

    .report-header h2 {
      color: #1e3a8a;
      margin: 0 0 4px 0;
      font-size: 1.5rem;
    }

    .report-header h3 {
      color: #2563eb;
      margin: 0 0 4px 0;
      font-size: 1.2rem;
    }

    .report-header p {
      margin: 0;
      color: var(--text-muted);
      font-size: 0.95rem;
    }

    .info-grid-card {
      background: #f8fafc;
      border: 1px solid #e2e8f0;
      border-radius: 12px;
      padding: 16px 24px;
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
      margin-bottom: 24px;
    }

    .info-item label {
      display: block;
      font-size: 0.85rem;
      color: var(--text-muted);
      font-weight: 600;
    }

    .info-item span {
      font-size: 1.05rem;
      font-weight: 800;
      color: #0f172a;
    }

    .report-table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 24px;
      font-size: 0.92rem;
    }

    .report-table th, .report-table td {
      border: 1px solid #cbd5e1;
      padding: 10px 14px;
      text-align: left;
    }

    .report-table th {
      background: #f1f5f9;
      color: #334155;
      font-weight: 700;
    }

    .badge-level {
      display: inline-block;
      padding: 4px 12px;
      border-radius: 12px;
      font-weight: 800;
      font-size: 0.82rem;
    }

    .badge-avanzado { background: var(--success-bg); color: var(--success-text); }
    .badge-bueno { background: var(--warning-bg); color: var(--warning-text); }
    .badge-mejorar { background: var(--danger-bg); color: var(--danger-text); }

    .callout-obs {
      background: #f1f5f9;
      border-left: 5px solid var(--primary);
      padding: 16px 20px;
      border-radius: 8px;
      margin-bottom: 24px;
    }

    .callout-obs h4 {
      margin: 0 0 6px 0;
      color: #0f172a;
    }

    .callout-obs p {
      margin: 0;
      color: #475569;
      font-size: 0.95rem;
    }

    .action-buttons {
      display: flex;
      justify-content: center;
      gap: 16px;
      margin-top: 20px;
    }

    .btn-action {
      padding: 12px 24px;
      border-radius: 10px;
      border: none;
      font-weight: 800;
      font-size: 0.95rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: opacity 0.2s;
    }

    .btn-action:hover { opacity: 0.9; }
    .btn-gray { background: #e2e8f0; color: #334155; }
    .btn-green { background: #16a34a; color: white; }
    .btn-blue { background: #2563eb; color: white; }

    /* FEEDBACK TOAST DE TITO */
    .tito-toast {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%) translateY(100px);
      background: #0f172a;
      color: white;
      padding: 12px 24px;
      border-radius: 30px;
      font-weight: 700;
      box-shadow: 0 10px 20px rgba(0,0,0,0.2);
      transition: transform 0.3s ease;
      z-index: 1000;
    }

    .tito-toast.show {
      transform: translateX(-50%) translateY(0);
    }

    @media print {
      body { background: white; }
      .app-viewport { box-shadow: none; max-width: 100%; }
      .action-buttons, .tito-toast { display: none !important; }
    }
  </style>
</head>
<body>

  <div class="app-viewport">
    <!-- BANNER SUPERIOR -->
    <header class="top-header">
      <div>
        <h1>COLEGIO DIOCESANO PADRE ELADIO SANCHO</h1>
        <p>Prueba de Ejecución II Semestre, 2026 | Informática Educativa</p>
      </div>
      <div class="session-badge" id="sessionBadge">
        <span class="dot"></span>
        <span id="sessionBadgeText">SESIÓN: Inactiva</span>
      </div>
    </header>

    <!-- CONTENIDO PRINCIPAL -->
    <main class="main-content" id="mainApp">
      <!-- Se genera mediante JS -->
    </main>
  </div>

  <!-- NOTIFICADOR DE TITO -->
  <div class="tito-toast" id="titoToast">¡Hola! Soy Tito el Ratón.</div>

  <script>
    /* ==========================================================================
       ESTADO Y REGISTRO AUTÓNOMO (20 COMPUTADORAS SIMULTÁNEAS)
       ========================================================================== */
    const state = {
      studentName: '',
      section: '1-1',
      officialDate: '2026-09-21',
      sessionId: '',
      currentMission: 0,
      errors: {
        ind1: 0, // Izquierdo
        ind2: 0, // Derecho / Rueda
        ind3: 0, // Desplazamiento 4 direcc.
        ind4: 0, // Clic selección
        ind5: 0, // Discrimina Clic / Doble Clic
        ind6: 0, // Ritmo Doble Clic
        ind7: 0, // Drag & Drop
        ind8: 0, // Scroll Rueda
        ind9: 0, // Indicaciones de Tito
        ind10: 0 // Concentración/Completado
      },
      m3TargetIdx: 0,
      m6ItemsDropped: 0
    };

    function showToast(msg) {
      const toast = document.getElementById('titoToast');
      toast.innerText = msg;
      toast.classList.add('show');
      setTimeout(() => toast.classList.remove('show'), 3000);
    }

    /* ==========================================================================
       SVG DE TITO Y MOUSE
       ========================================================================== */
    function getTitoSVG() {
      return `
        <svg viewBox="0 0 100 100" class="tito-avatar">
          <circle cx="22" cy="22" r="16" fill="#94a3b8"/>
          <circle cx="22" cy="22" r="9" fill="#f472b6"/>
          <circle cx="78" cy="22" r="16" fill="#94a3b8"/>
          <circle cx="78" cy="22" r="9" fill="#f472b6"/>
          <circle cx="50" cy="50" r="30" fill="#cbd5e1"/>
          <ellipse cx="50" cy="54" rx="14" ry="10" fill="#f8fafc"/>
          <ellipse cx="50" cy="48" rx="4" ry="3" fill="#0f172a"/>
          <circle cx="38" cy="42" r="4" fill="#0f172a"/>
          <circle cx="62" cy="42" r="4" fill="#0f172a"/>
          <path d="M 40 58 Q 50 66 60 58" stroke="#0f172a" stroke-width="3" fill="none"/>
        </svg>
      `;
    }

    /* ==========================================================================
       RENDERIZADO DE PANTALLAS
       ========================================================================== */
    function render() {
      const main = document.getElementById('mainApp');

      if (state.currentMission === 0) {
        renderRegister(main);
      } else if (state.currentMission <= 7) {
        renderMission(main);
      } else {
        renderFinalReport(main);
      }
    }

    // REGISTRO INICIAL
    function renderRegister(main) {
      main.innerHTML = `
        <div class="card register-box">
          ${getTitoSVG()}
          <h2>LA AVENTURA DE TITO: MISIÓN MOUSE</h2>
          <p style="color:var(--text-muted); margin-bottom:24px;">Ingresa los datos para iniciar la prueba individual.</p>
          
          <div class="form-group">
            <label>Nombre del Estudiante:</label>
            <input type="text" id="regName" class="form-control" value="Ana Rojas" placeholder="Nombre completo">
          </div>
          <div class="form-group">
            <label>Sección:</label>
            <input type="text" id="regSec" class="form-control" value="1-1">
          </div>
          <div class="form-group">
            <label>Fecha Oficial de Aplicación:</label>
            <input type="date" id="regDate" class="form-control" value="${state.officialDate}">
          </div>

          <button class="btn-primary" onclick="startAdventure()">INICIAR AVENTURA 🚀</button>
        </div>
      `;
    }

    function startAdventure() {
      const name = document.getElementById('regName').value.trim();
      const sec = document.getElementById('regSec').value.trim();
      const date = document.getElementById('regDate').value;

      if (!name || !sec || !date) return alert("Por favor complete todos los campos.");

      state.studentName = name;
      state.section = sec;
      state.officialDate = date;

      // Generar ID único de sesión para evitar mezcla entre las 20 computadoras
      const cleanName = name.replace(/\s+/g, '_').toUpperCase();
      state.sessionId = `pruebaMouse_2026_${cleanName}_${Date.now().toString().slice(-6)}`;

      document.getElementById('sessionBadgeText').innerText = `SESIÓN: ${state.sessionId.slice(0,25)}...`;
      state.currentMission = 1;
      render();
    }

    // NAVEGACIÓN DE MISIONES
    function renderMission(main) {
      const titles = [
        "",
        "Misión 1: Partes del Mouse",
        "Misión 2: Desplazamiento del Puntero",
        "Misión 3: Selección con Clic Izquierdo",
        "Misión 4: Clic Simple vs Doble Clic",
        "Misión 5: Apertura de Cajas Misteriosas",
        "Misión 6: Almacén de Clasificación (Drag & Drop)",
        "Misión 7: Navegación Vertical con Rueda Scroll"
      ];

      main.innerHTML = `
        <div class="mission-header">
          ${getTitoSVG()}
          <div>
            <h3 style="margin:0; color:var(--primary-dark);">${titles[state.currentMission]}</h3>
            <p style="margin:4px 0 0 0; color:var(--text-muted); font-size:0.95rem;">Sigue las instrucciones de Tito el Ratón para completar el reto.</p>
          </div>
        </div>
        <div class="stage-canvas" id="stageCanvas"></div>
      `;

      loadStageContent(state.currentMission);
    }

    function loadStageContent(m) {
      const stage = document.getElementById('stageCanvas');

      // MISIÓN 1: PARTES DEL MOUSE (SIN SENSOR ÓPTICO, TEXTO MÁS GRANDE)
      if (m === 1) {
        let currentTarget = 'left'; // left -> right -> wheel
        stage.innerHTML = `
          <div style="text-align:center;">
            <svg class="mouse-svg-container" viewBox="0 0 240 260">
              <!-- Botón Izquierdo -->
              <path id="btn-left" class="mouse-btn" d="M 30 30 Q 120 30 120 100 L 30 100 Z" fill="#3b82f6"/>
              <text x="68" y="72" class="mouse-text">BOTÓN IZQUIERDO</text>

              <!-- Botón Derecho -->
              <path id="btn-right" class="mouse-btn" d="M 120 30 Q 210 30 210 100 L 120 100 Z" fill="#60a5fa"/>
              <text x="162" y="72" class="mouse-text">BOTÓN DERECHO</text>

              <!-- Rueda Scroll -->
              <rect id="btn-wheel" class="mouse-btn" x="108" y="50" width="24" height="40" rx="10" fill="#f59e0b"/>
              <text x="120" y="24" class="mouse-text" style="font-size:16px;">RUEDA SCROLL</text>

              <!-- Cuerpo del Mouse (Sin Sensor Óptico) -->
              <path d="M 30 100 L 210 100 Q 210 240 120 250 Q 30 240 30 100 Z" fill="#cbd5e1"/>
            </svg>
          </div>
        `;

        showToast("Tito dice: Haz clic en el BOTÓN IZQUIERDO.");

        const checkPart = (partKey) => {
          if (partKey === currentTarget) {
            if (partKey === 'left') {
              currentTarget = 'right';
              showToast("¡Muy bien! Ahora haz clic en el BOTÓN DERECHO.");
            } else if (partKey === 'right') {
              currentTarget = 'wheel';
              showToast("¡Genial! Ahora haz clic en la RUEDA DE SCROLL.");
            } else if (partKey === 'wheel') {
              showToast("¡Excelente! Identificaste las partes del mouse.");
              setTimeout(() => { state.currentMission = 2; render(); }, 1500);
            }
          } else {
            // Registrar error para calificar adecuadamente
            if (currentTarget === 'left') state.errors.ind1++;
            else state.errors.ind2++;

            showToast("Esa no es la parte indicada. ¡Inténtalo de nuevo!");
          }
        };

        document.getElementById('btn-left').onclick = () => checkPart('left');
        document.getElementById('btn-right').onclick = () => checkPart('right');
        document.getElementById('btn-wheel').onclick = () => checkPart('wheel');
      }

      // MISIÓN 2: DESPLAZAMIENTO DEL PUNTERO (REGISTRA CURSOR EN ZONA INCORRECTA)
      else if (m === 2) {
        const order = ['UP', 'DOWN', 'LEFT', 'RIGHT'];
        let idx = 0;

        stage.innerHTML = `
          <div class="grid-directions">
            <div></div>
            <div class="dir-zone" id="z-UP">⬆️ ARRIBA</div>
            <div></div>
            <div class="dir-zone" id="z-LEFT">⬅️ IZQUIERDA</div>
            <div style="display:flex; align-items:center; justify-content:center;">🐭</div>
            <div class="dir-zone" id="z-RIGHT">➡️ DERECHA</div>
            <div></div>
            <div class="dir-zone" id="z-DOWN">⬇️ ABAJO</div>
            <div></div>
          </div>
        `;

        const updateTargets = () => {
          document.querySelectorAll('.dir-zone').forEach(el => el.classList.remove('active-target'));
          document.getElementById(`z-${order[idx]}`).classList.add('active-target');
          showToast(`Lleva el puntero del mouse hacia ${order[idx]}`);
        };

        updateTargets();

        ['UP', 'DOWN', 'LEFT', 'RIGHT'].forEach(dir => {
          const zone = document.getElementById(`z-${dir}`);
          zone.onmouseenter = () => {
            if (dir === order[idx]) {
              idx++;
              if (idx < order.length) {
                updateTargets();
              } else {
                showToast("¡Fantástico! Mueves el puntero en todas direcciones.");
                setTimeout(() => { state.currentMission = 3; render(); }, 1500);
              }
            } else {
              // Registra el movimiento incorrecto en la rúbrica pero permite continuar
              state.errors.ind3++;
              showToast(`Te moviste a ${dir}. Recuerda ir hacia ${order[idx]}.`);
            }
          };
        });
      }

      // MISIÓN 3: SELECCIÓN CLIC IZQUIERDO (REGISTRA CLIC EN ELEMENTO INCORRECTO)
      else if (m === 3) {
        const targets = ['robot', 'car', 'star'];
        const names = { robot: 'Robot 🤖', car: 'Carro 🚗', star: 'Estrella ⭐' };
        state.m3TargetIdx = 0;

        stage.innerHTML = `
          <div class="objects-grid">
            <div class="obj-card" id="obj-robot">🤖</div>
            <div class="obj-card" id="obj-car">🚗</div>
            <div class="obj-card" id="obj-star">⭐</div>
          </div>
        `;

        showToast(`Haz clic sobre el ${names[targets[state.m3TargetIdx]]}`);

        ['robot', 'car', 'star'].forEach(objKey => {
          document.getElementById(`obj-${objKey}`).onclick = () => {
            const expected = targets[state.m3TargetIdx];
            if (objKey === expected) {
              state.m3TargetIdx++;
              if (state.m3TargetIdx < targets.length) {
                showToast(`¡Bien! Ahora haz clic sobre el ${names[targets[state.m3TargetIdx]]}`);
              } else {
                showToast("¡Excelente precisión con el clic izquierdo!");
                setTimeout(() => { state.currentMission = 4; render(); }, 1500);
              }
            } else {
              // Registra el clic incorrecto
              state.errors.ind4++;
              showToast(`Ese es otro objeto. Busca el ${names[expected]}.`);
            }
          };
        });
      }

      // MISIÓN 4: CLIC SIMPLE VS DOBLE CLIC (MIDE RITMO Y CONTINUIDAD)
      else if (m === 4) {
        let step = 0; // 0: single, 1: double
        stage.innerHTML = `
          <div class="objects-grid">
            <div class="obj-card" id="clickTarget" style="width:140px; height:140px; font-size:3.5rem;">🎯</div>
          </div>
        `;

        showToast("Haz UN CLIC SIMPLE sobre el objetivo.");

        let timer = null;
        const targetEl = document.getElementById('clickTarget');

        targetEl.onclick = () => {
          if (step === 0) {
            step = 1;
            showToast("¡Bien! Ahora haz DOBLE CLIC rítmico sobre el objetivo.");
          } else if (step === 1) {
            // Si hace solo un clic cuando se esperaba doble clic
            timer = setTimeout(() => {
              state.errors.ind5++;
              state.errors.ind6++;
              showToast("Fue un clic simple. Haz dos clics rápidos seguidos.");
            }, 300);
          }
        };

        targetEl.ondblclick = () => {
          if (step === 1) {
            clearTimeout(timer);
            showToast("¡Excelente! Lograste diferenciar el doble clic.");
            setTimeout(() => { state.currentMission = 5; render(); }, 1500);
          }
        };
      }

      // MISIÓN 5: CAJAS MISTERIOSAS (EVALÚA DOBLE CLIC)
      else if (m === 5) {
        let opened = 0;
        stage.innerHTML = `
          <div class="objects-grid">
            <div class="obj-card" id="box1">🎁</div>
            <div class="obj-card" id="box2">🎁</div>
          </div>
        `;

        showToast("Abre las dos cajas haciendo DOBLE CLIC en cada una.");

        ['box1', 'box2'].forEach(bId => {
          const el = document.getElementById(bId);
          el.onclick = () => {
            if (el.innerText === '🎁') {
              state.errors.ind6++;
              showToast("Haz DOBLE CLIC rápido para abrir la caja.");
            }
          };
          el.ondblclick = () => {
            if (el.innerText === '🎁') {
              el.innerText = '🎉';
              opened++;
              if (opened === 2) {
                showToast("¡Abriste todas las cajas misteriosas!");
                setTimeout(() => { state.currentMission = 6; render(); }, 1500);
              }
            }
          };
        });
      }

      // MISIÓN 6: ALMACÉN DRAG & DROP (SI SE EQUIVOCA, DEJA EL ELEMENTO AHÍ PERO REGISTRA EN RÚBRICA)
      else if (m === 6) {
        state.m6ItemsDropped = 0;

        stage.innerHTML = `
          <div style="width:100%;">
            <div class="drag-pool" id="pool">
              <div class="obj-card" draggable="true" id="drag-pelota" data-cat="juguete">⚽</div>
              <div class="obj-card" draggable="true" id="drag-lapiz" data-cat="util">✏️</div>
              <div class="obj-card" draggable="true" id="drag-gato" data-cat="animal">🐱</div>
            </div>

            <div class="drop-zones-container">
              <div class="drop-target-box" id="zone-juguete">
                <h4>JUGUETES</h4>
              </div>
              <div class="drop-target-box" id="zone-util">
                <h4>ÚTILES</h4>
              </div>
              <div class="drop-target-box" id="zone-animal">
                <h4>ANIMALES</h4>
              </div>
            </div>
          </div>
        `;

        showToast("Arrastra los objetos a sus categorías.");

        const items = stage.querySelectorAll('[draggable="true"]');
        const zones = stage.querySelectorAll('.drop-target-box');

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

            // Dejar el elemento en la caja elegida sin corregir duramente
            zone.appendChild(draggedEl);
            draggedEl.setAttribute('draggable', 'false');

            if (itemCat !== targetCat) {
              // Se registra el error en la rúbrica
              state.errors.ind7++;
            }

            state.m6ItemsDropped++;
            if (state.m6ItemsDropped === 3) {
              showToast("¡Completaste la clasificación!");
              setTimeout(() => { state.currentMission = 7; render(); }, 1500);
            }
          };
        });
      }

      // MISIÓN 7: NAVEGACIÓN VERTICAL SCROLL
      else if (m === 7) {
        stage.innerHTML = `
          <div style="height:320px; overflow-y:scroll; width:100%; border:1px solid #cbd5e1; border-radius:10px; padding:20px;" id="scrollBox">
            <div style="height:800px; display:flex; flex-direction:column; justify-content:space-between; align-items:center;">
              <p>👇 Usa la RUEDA SCROLL para bajar...</p>
              <div class="obj-card" id="scrollTreasure" style="width:auto; padding:10px 20px;">🏆 ¡Tesoro Encontrado! (Haz clic)</div>
            </div>
          </div>
        `;

        showToast("Usa la rueda de scroll para bajar hasta el tesoro.");

        let scrolled = false;
        document.getElementById('scrollBox').onscroll = () => { scrolled = true; };

        document.getElementById('scrollTreasure').onclick = () => {
          if (!scrolled) {
            state.errors.ind8++;
          }
          showToast("¡Felicitaciones! Completaste toda la prueba.");
          setTimeout(() => { state.currentMission = 8; render(); }, 1500);
        };
      }
    }

    /* ==========================================================================
       PANTALLA FINAL Y GENERACIÓN DE INFORME DOCENTE (DISEÑO EXACTO)
       ========================================================================== */
    function renderFinalReport(main) {
      // Calcular puntaje por indicador
      const getScoreAndBadge = (errCount) => {
        if (errCount === 0) return { pts: 3, label: 'Avanzado', css: 'badge-avanzado' };
        if (errCount <= 2) return { pts: 2, label: 'Intermedio', css: 'badge-bueno' };
        return { pts: 1, label: 'Por mejorar', css: 'badge-mejorar' };
      };

      const indScores = [
        getScoreAndBadge(state.errors.ind1),
        getScoreAndBadge(state.errors.ind2),
        getScoreAndBadge(state.errors.ind3),
        getScoreAndBadge(state.errors.ind4),
        getScoreAndBadge(state.errors.ind5),
        getScoreAndBadge(state.errors.ind6),
        getScoreAndBadge(state.errors.ind7),
        getScoreAndBadge(state.errors.ind8),
        getScoreAndBadge(state.errors.ind9),
        getScoreAndBadge(state.errors.ind10)
      ];

      const totalEarned = indScores.reduce((acc, curr) => acc + curr.pts, 0);
      const percentage = Math.round((totalEarned / 30) * 100);

      const indTitles = [
        "1. Identifica y ejecuta el botón izquierdo del mouse.",
        "2. Reconoce el botón derecho y la rueda de scroll.",
        "3. Desplaza el puntero en las 4 direcciones principales (Arriba, Abajo, Izq, Der).",
        "4. Realiza clic izquierdo para seleccionar objetos específicos indicados.",
        "5. Discrimina correctamente entre la acción de Clic Simple y Doble Clic.",
        "6. Ejecuta el doble clic con el ritmo y continuidad adecuados.",
        "7. Aplica la técnica de arrastrar y soltar (Drag & Drop) para clasificar elementos.",
        "8. Utiliza la rueda de desplazamiento (Scroll) para la navegación vertical.",
        "9. Sigue las instrucciones e indicaciones del personaje guía (Tito el Ratón).",
        "10. Mantiene la concentración y completa el recorrido completo de la prueba."
      ];

      main.innerHTML = `
        <div class="card">
          <div class="report-header">
            <h2>COLEGIO DIOCESANO PADRE ELADIO SANCHO</h2>
            <h3>Informe Docente de Prueba de Ejecución II Semestre, 2026</h3>
            <p>Informática Educativa - Primer Grado</p>
          </div>

          <div class="info-grid-card">
            <div class="info-item">
              <label>Estudiante:</label>
              <span>${state.studentName}</span>
            </div>
            <div class="info-item">
              <label>Sección:</label>
              <span>${state.section}</span>
            </div>
            <div class="info-item">
              <label>Fecha:</label>
              <span>${state.officialDate}</span>
            </div>
            <div class="info-item">
              <label>ID Sesión:</label>
              <span style="font-size:0.8rem; word-break:break-all;">${state.sessionId}</span>
            </div>
            <div class="info-item" style="grid-column: span 2;">
              <label>Puntaje Obtenido:</label>
              <span style="color:var(--primary-dark); font-size:1.2rem;">${totalEarned} / 30 pts</span>
            </div>
            <div class="info-item" style="grid-column: span 2;">
              <label>Porcentaje:</label>
              <span style="color:var(--primary-dark); font-size:1.2rem;">${percentage}%</span>
            </div>
          </div>

          <h4 style="color:#0f172a; margin-bottom:12px;">1. Rúbrica Analítica de Evaluación (10 Indicadores)</h4>
          <table class="report-table">
            <thead>
              <tr>
                <th style="width:40px;">#</th>
                <th>Indicador de Desempeño</th>
                <th style="width:140px;">Nivel Alcanzado</th>
                <th style="width:110px; text-align:center;">Puntos (1-3)</th>
              </tr>
            </thead>
            <tbody>
              ${indScores.map((score, i) => `
                <tr>
                  <td>${i + 1}</td>
                  <td>${indTitles[i]}</td>
                  <td><span class="badge-level ${score.css}">${score.label}</span></td>
                  <td style="text-align:center; font-weight:800;">${score.pts} / 3</td>
                </tr>
              `).join('')}
            </tbody>
          </table>

          <h4 style="color:#0f172a; margin-bottom:12px;">2. Resumen "Lo Que Hice Hoy" (Registro Automático)</h4>
          <table class="report-table">
            <thead>
              <tr>
                <th>Actividad Práctica</th>
                <th>Acción Registrada por el Sistema</th>
                <th>Estado</th>
              </tr>
            </thead>
            <tbody>
              <tr><td>Exploración de Partes del Mouse</td><td>Verificación de botones y rueda</td><td><span style="color:#16a34a; font-weight:700;">☑ Logrado</span></td></tr>
              <tr><td>Desplazamiento del Puntero</td><td>Navegación en 4 cuadrantes</td><td><span style="color:#16a34a; font-weight:700;">☑ Logrado</span></td></tr>
              <tr><td>Selección de Juguetes (Robots)</td><td>Clic izquierdo de precisión</td><td><span style="color:#16a34a; font-weight:700;">☑ Logrado</span></td></tr>
              <tr><td>Diferenciación Clic / Doble Clic</td><td>Ejecución de eventos de ratón</td><td><span style="color:#16a34a; font-weight:700;">☑ Logrado</span></td></tr>
              <tr><td>Apertura de Cajas Misteriosas</td><td>Doble clic continuo y rápido</td><td><span style="color:#16a34a; font-weight:700;">☑ Logrado</span></td></tr>
              <tr><td>Clasificación Drag & Drop</td><td>Arrastre y soltar de objetos</td><td><span style="color:#16a34a; font-weight:700;">☑ Logrado</span></td></tr>
              <tr><td>Navegación con Rueda Scroll</td><td>Desplazamiento vertical en estantería</td><td><span style="color:#16a34a; font-weight:700;">☑ Logrado</span></td></tr>
            </tbody>
          </table>

          <div class="callout-obs">
            <h4>Observaciones Automáticas del Sistema:</h4>
            <p>${totalEarned >= 28 
                ? 'El estudiante completó la prueba con ejecución fluida de las interacciones básicas del ratón.' 
                : 'El estudiante completó el recorrido demostrando dominio práctico con necesidad de reintentos puntuales en doble clic o arrastre.'}</p>
          </div>

          <div class="action-buttons">
            <button class="btn-action btn-gray" onclick="resetApp()">👤 Nuevo Estudiante</button>
            <button class="btn-action btn-green" onclick="savePNG()">📸 GUARDAR EVIDENCIA (PNG)</button>
            <button class="btn-action btn-blue" onclick="window.print()">🖨️ IMPRIMIR / GUARDAR REPORTE (PDF)</button>
          </div>
        </div>
      `;
    }

    function resetApp() {
      if (confirm("¿Desea iniciar una nueva prueba con otro estudiante?")) {
        state.currentMission = 0;
        state.studentName = '';
        Object.keys(state.errors).forEach(k => state.errors[k] = 0);
        document.getElementById('sessionBadgeText').innerText = 'SESIÓN: Inactiva';
        render();
      }
    }

    function savePNG() {
      alert("Para guardar como imagen PNG o archivo PDF digital, seleccione la opción 'IMPRIMIR / GUARDAR REPORTE (PDF)' y elija 'Guardar como PDF' en su navegador.");
      window.print();
    }

    // INICIALIZACIÓN
    render();
  </script>
</body>
</html>
