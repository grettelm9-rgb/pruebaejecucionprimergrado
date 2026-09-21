<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LA AVENTURA DE TITO: MISIÓN MOUSE - Prueba de Ejecución 2026</title>
  <style>
    /* ==========================================================================
       1. ESTILOS DE LA IDENTIDAD VISUAL Y TEMA INFANTIL MODERNO
       ========================================================================== */
    :root {
      --primary: #3B82F6;
      --primary-dark: #1D4ED8;
      --secondary: #F59E0B;
      --accent: #10B981;
      --purple: #8B5CF6;
      --pink: #EC4899;
      --bg-gradient: linear-gradient(135deg, #E0F2FE 0%, #F0FDFA 50%, #FEF3C7 100%);
      --card-bg: #FFFFFF;
      --text-main: #1E293B;
      --text-muted: #64748B;
      --border-radius: 24px;
      --shadow-soft: 0 10px 25px -5px rgba(0, 0, 0, 0.08), 0 8px 10px -6px rgba(0, 0, 0, 0.04);
      --shadow-hover: 0 20px 30px -10px rgba(59, 130, 246, 0.2);
    }

    * {
      box-sizing: border-box;
      user-select: none;
      -webkit-user-drag: none;
      font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Comic Sans MS', 'Chalkboard SE', sans-serif;
    }

    body {
      margin: 0;
      padding: 0;
      min-height: 100vh;
      background: var(--bg-gradient);
      color: var(--text-main);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      overflow-x: hidden;
    }

    /* CONTENEDOR PRINCIPAL */
    .app-container {
      width: 100%;
      max-width: 1100px;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      padding: 16px;
    }

    /* BANNER INSTITUCIONAL */
    .inst-header {
      background: rgba(255, 255, 255, 0.9);
      backdrop-filter: blur(8px);
      border-radius: 16px;
      padding: 12px 20px;
      border: 2px solid #E2E8F0;
      box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 12px;
    }

    .inst-info h1 {
      font-size: 1.1rem;
      margin: 0;
      color: var(--primary-dark);
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .inst-info p {
      margin: 2px 0 0 0;
      font-size: 0.85rem;
      color: var(--text-muted);
      font-weight: 600;
    }

    .badge-details {
      display: flex;
      gap: 12px;
      background: #F1F5F9;
      padding: 6px 12px;
      border-radius: 12px;
      font-size: 0.8rem;
      font-weight: 700;
      color: #334155;
    }

    /* TARJETA DE CONTENIDO */
    .main-card {
      background: var(--card-bg);
      border-radius: var(--border-radius);
      box-shadow: var(--shadow-soft);
      padding: 24px;
      flex: 1;
      display: flex;
      flex-direction: column;
      position: relative;
      border: 3px solid #F1F5F9;
      margin-bottom: 16px;
    }

    /* PANTALLA DE BIENVENIDA / REGISTRO */
    .welcome-screen {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding: 20px 10px;
      max-width: 650px;
      margin: 0 auto;
    }

    .tito-welcome-box {
      width: 180px;
      height: 180px;
      margin-bottom: 15px;
      animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }

    .welcome-title {
      font-size: 2rem;
      font-weight: 900;
      color: var(--primary-dark);
      margin: 0 0 8px 0;
    }

    .welcome-subtitle {
      font-size: 1.1rem;
      color: var(--text-muted);
      margin-bottom: 24px;
    }

    .form-group {
      width: 100%;
      margin-bottom: 16px;
      text-align: left;
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
      padding: 14px 18px;
      font-size: 1.05rem;
      border: 2px solid #CBD5E1;
      border-radius: 14px;
      outline: none;
      transition: all 0.2s;
    }

    .form-control:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.15);
    }

    .btn-adventure {
      background: linear-gradient(135deg, #10B981 0%, #059669 100%);
      color: white;
      font-size: 1.3rem;
      font-weight: 800;
      padding: 16px 36px;
      border: none;
      border-radius: 20px;
      cursor: pointer;
      box-shadow: 0 10px 20px -5px rgba(16, 185, 129, 0.4);
      transition: all 0.2s;
      width: 100%;
      margin-top: 10px;
    }

    .btn-adventure:hover {
      transform: translateY(-2px) scale(1.02);
      box-shadow: 0 15px 25px -5px rgba(16, 185, 129, 0.5);
    }

    /* RUTA DE PROGRESO DE AVENTURA */
    .adventure-path {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      position: relative;
      padding: 0 10px;
    }

    .path-line {
      position: absolute;
      top: 50%;
      left: 30px;
      right: 30px;
      height: 6px;
      background: #E2E8F0;
      z-index: 1;
      transform: translateY(-50%);
      border-radius: 3px;
    }

    .path-line-progress {
      position: absolute;
      top: 50%;
      left: 30px;
      height: 6px;
      background: linear-gradient(90deg, var(--primary), var(--accent));
      z-index: 1;
      transform: translateY(-50%);
      border-radius: 3px;
      transition: width 0.4s ease;
      width: 0%;
    }

    .path-node {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      background: #FFFFFF;
      border: 3px solid #CBD5E1;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 800;
      font-size: 0.95rem;
      color: var(--text-muted);
      z-index: 2;
      transition: all 0.3s;
    }

    .path-node.active {
      border-color: var(--primary);
      background: var(--primary);
      color: white;
      transform: scale(1.15);
      box-shadow: 0 0 0 6px rgba(59, 130, 246, 0.2);
    }

    .path-node.completed {
      border-color: var(--accent);
      background: var(--accent);
      color: white;
    }

    /* ENCABEZADO DE MISIÓN */
    .mission-header-box {
      display: flex;
      align-items: center;
      gap: 16px;
      background: #F8FAFC;
      border-radius: 16px;
      padding: 12px 18px;
      margin-bottom: 20px;
      border: 2px solid #E2E8F0;
    }

    .tito-avatar-small {
      width: 65px;
      height: 65px;
      flex-shrink: 0;
    }

    .mission-title-container h2 {
      margin: 0;
      font-size: 1.3rem;
      color: var(--primary-dark);
      font-weight: 800;
    }

    .mission-title-container p {
      margin: 4px 0 0 0;
      font-size: 0.95rem;
      color: #475569;
      font-weight: 600;
    }

    /* ESCENARIOS DE INTERACCIÓN */
    .stage-canvas {
      flex: 1;
      background: #F1F5F9;
      border-radius: 18px;
      border: 2px inset #CBD5E1;
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      min-height: 380px;
      overflow: hidden;
      padding: 16px;
    }

    /* MISIÓN 1: MOUSE SVG */
    .mouse-parts-svg {
      width: 320px;
      height: 320px;
    }

    .part-interactive {
      cursor: pointer;
      transition: all 0.2s;
    }

    .part-interactive:hover {
      filter: brightness(1.15) drop-shadow(0 0 6px rgba(59, 130, 246, 0.5));
    }

    /* MISIÓN 2: DIRECCIONES */
    .direction-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: repeat(3, 1fr);
      gap: 16px;
      width: 100%;
      max-width: 420px;
      height: 340px;
    }

    .dir-zone {
      background: white;
      border: 3px dashed #CBD5E1;
      border-radius: 16px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-weight: 800;
      color: var(--text-muted);
      transition: all 0.2s;
      cursor: pointer;
    }

    .dir-zone.highlight {
      border-color: var(--primary);
      background: #E0F2FE;
      color: var(--primary-dark);
      transform: scale(1.03);
    }

    /* MISIÓN 3: MUNDO DE OBJETOS */
    .objects-world {
      display: flex;
      flex-wrap: wrap;
      gap: 24px;
      justify-content: center;
      align-items: center;
      max-width: 600px;
    }

    .world-item {
      width: 110px;
      height: 110px;
      background: white;
      border-radius: 20px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.06);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      border: 3px solid #E2E8F0;
      transition: all 0.2s;
    }

    .world-item:hover {
      transform: scale(1.08);
      border-color: var(--primary);
    }

    .world-item svg {
      width: 60px;
      height: 60px;
    }

    /* MISIÓN 4 & 5: RETO CLIC Y CAJAS MÁGICAS */
    .magic-boxes-container {
      display: flex;
      gap: 30px;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
    }

    .magic-box-card {
      width: 140px;
      height: 140px;
      background: linear-gradient(135deg, #F59E0B 0%, #D97706 100%);
      border-radius: 24px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: 800;
      cursor: pointer;
      box-shadow: 0 10px 20px rgba(217, 119, 6, 0.3);
      transition: all 0.3s;
      position: relative;
    }

    .magic-box-card:hover {
      transform: translateY(-4px) scale(1.04);
    }

    .magic-box-card.opened {
      background: linear-gradient(135deg, #10B981 0%, #059669 100%);
      box-shadow: 0 10px 20px rgba(16, 185, 129, 0.3);
    }

    /* MISIÓN 6: ALMACÉN (DRAG & DROP) */
    .warehouse-container {
      display: flex;
      flex-direction: column;
      gap: 20px;
      width: 100%;
    }

    .drag-items-pool {
      display: flex;
      justify-content: center;
      gap: 16px;
      flex-wrap: wrap;
      min-height: 90px;
      background: white;
      padding: 12px;
      border-radius: 16px;
      border: 2px dashed #CBD5E1;
    }

    .drop-categories {
      display: flex;
      gap: 16px;
      justify-content: space-between;
    }

    .drop-zone-box {
      flex: 1;
      min-height: 160px;
      background: white;
      border: 3px dashed #94A3B8;
      border-radius: 18px;
      padding: 12px;
      display: flex;
      flex-direction: column;
      align-items: center;
      transition: all 0.2s;
    }

    .drop-zone-box.drag-over {
      background: #FEF3C7;
      border-color: var(--secondary);
    }

    .drop-zone-title {
      font-size: 0.95rem;
      font-weight: 800;
      color: var(--primary-dark);
      margin-bottom: 8px;
      text-transform: uppercase;
    }

    /* MISIÓN 7: SCROLL VERTICAL */
    .scroll-view-stage {
      width: 100%;
      height: 360px;
      overflow-y: scroll;
      background: linear-gradient(to bottom, #E0F2FE 0%, #FEF3C7 50%, #ECFDF5 100%);
      border-radius: 16px;
      padding: 20px;
      position: relative;
    }

    .scroll-content-long {
      height: 1300px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      padding: 20px 0;
    }

    .hidden-treasure-item {
      background: white;
      padding: 14px 24px;
      border-radius: 16px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      display: flex;
      align-items: center;
      gap: 12px;
      font-weight: 800;
      color: var(--primary-dark);
      border: 2px solid var(--primary);
      cursor: pointer;
    }

    /* RETROALIMENTACIÓN DE TITO (TOAST) */
    .tito-toast {
      position: fixed;
      bottom: 24px;
      left: 50%;
      transform: translateX(-50%) translateY(120px);
      background: #1E293B;
      color: white;
      padding: 14px 24px;
      border-radius: 30px;
      display: flex;
      align-items: center;
      gap: 12px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
      z-index: 1000;
      transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      font-weight: 700;
      font-size: 1.05rem;
    }

    .tito-toast.show {
      transform: translateX(-50%) translateY(0);
    }

    .tito-toast-avatar {
      width: 40px;
      height: 40px;
    }

    /* PANTALLA FINAL Y REPORTE DOCENTE */
    .celebration-screen {
      text-align: center;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 16px;
    }

    .summary-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 12px;
      font-size: 0.88rem;
    }

    .summary-table th, .summary-table td {
      border: 1px solid #CBD5E1;
      padding: 8px 12px;
      text-align: left;
    }

    .summary-table th {
      background: #F1F5F9;
      color: var(--primary-dark);
    }

    .btn-action-group {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 16px;
    }

    .btn-secondary-action {
      background: #3B82F6;
      color: white;
      padding: 12px 20px;
      border-radius: 12px;
      border: none;
      font-weight: 700;
      cursor: pointer;
      transition: all 0.2s;
    }

    .btn-secondary-action:hover {
      background: var(--primary-dark);
    }

    /* ESTILOS DE IMPRESIÓN */
    @media print {
      body {
        background: white !important;
        color: black !important;
      }
      .inst-header, .adventure-path, .btn-action-group, .tito-toast {
        display: none !important;
      }
      .main-card {
        box-shadow: none !important;
        border: none !important;
        padding: 0 !important;
      }
    }
  </style>
</head>
<body>

  <div class="app-container">
    <!-- ENCABEZADO INSTITUCIONAL -->
    <header class="inst-header">
      <div class="inst-info">
        <h1>Colegio Diocesano Padre Eladio Sancho</h1>
        <p>Departamento de Informática Educativa | II Semestre, 2026</p>
      </div>
      <div class="badge-details">
        <span>Nivel: Primer Grado</span>
        <span>Docente: Grettel Monge Rojas</span>
        <span>Porcentaje: 30%</span>
      </div>
    </header>

    <!-- TARJETA PRINCIPAL DE LA AVENTURA -->
    <main class="main-card" id="mainContainer">
      <!-- Se renderiza dinámicamente -->
    </main>
  </div>

  <!-- TOAST DE RETROALIMENTACIÓN DE TITO -->
  <div class="tito-toast" id="titoToast">
    <div class="tito-toast-avatar" id="toastTitoAvatar"></div>
    <span id="toastMessage">¡Hola! Soy Tito.</span>
  </div>

  <script>
    /* ==========================================================================
       2. SINTETIZADOR DE AUDIO WEB (100% OFFLINE, SIN ARCHIVOS MP3)
       ========================================================================== */
    const AudioCtx = new (window.AudioContext || window.webkitAudioContext)();

    function playSound(type) {
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
      } else if (type === 'pop') {
        osc.frequency.setValueAtTime(300, now);
        osc.frequency.exponentialRampToValueAtTime(600, now + 0.1);
        gain.gain.setValueAtTime(0.2, now);
        gain.gain.exponentialRampToValueAtTime(0.01, now + 0.1);
        osc.start(now);
        osc.stop(now + 0.1);
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
       3. ILUSTRADOR SVG DE TITO (PERSONAJE CONSISTENTE CON POSES)
       ========================================================================== */
    function getTitoSVG(pose = 'happy') {
      let eyes = `<circle cx="38" cy="42" r="5" fill="#1E293B"/><circle cx="62" cy="42" r="5" fill="#1E293B"/><circle cx="40" cy="40" r="2" fill="white"/><circle cx="64" cy="40" r="2" fill="white"/>`;
      let mouth = `<path d="M 40 58 Q 50 68 60 58" stroke="#1E293B" stroke-width="3.5" fill="none" stroke-linecap="round"/>`;

      if (pose === 'surprised') {
        mouth = `<circle cx="50" cy="60" r="7" fill="#1E293B"/>`;
      } else if (pose === 'thinking') {
        eyes = `<circle cx="38" cy="39" r="5" fill="#1E293B"/><circle cx="62" cy="39" r="5" fill="#1E293B"/>`;
        mouth = `<path d="M 42 60 L 58 60" stroke="#1E293B" stroke-width="3.5" fill="none"/>`;
      } else if (pose === 'celebrating') {
        mouth = `<path d="M 38 54 Q 50 72 62 54 Z" fill="#EF4444"/>`;
      }

      return `
        <svg viewBox="0 0 100 100" width="100%" height="100%">
          <!-- Orejas -->
          <circle cx="22" cy="22" r="18" fill="#94A3B8"/>
          <circle cx="22" cy="22" r="11" fill="#F472B6"/>
          <circle cx="78" cy="22" r="18" fill="#94A3B8"/>
          <circle cx="78" cy="22" r="11" fill="#F472B6"/>
          <!-- Cabeza -->
          <circle cx="50" cy="50" r="32" fill="#CBD5E1"/>
          <!-- Hocico -->
          <ellipse cx="50" cy="55" rx="16" ry="12" fill="#F8FAFC"/>
          <ellipse cx="50" cy="48" rx="5" ry="3.5" fill="#1E293B"/>
          <!-- Ojos y Boca -->
          ${eyes}
          ${mouth}
          <!-- Camisa/Acceso -->
          <path d="M 30 80 Q 50 70 70 80 L 75 100 L 25 100 Z" fill="#3B82F6"/>
        </svg>
      `;
    }

    /* ==========================================================================
       4. ESTADO DE LA SESIÓN Y TELEMETRÍA DE LA PRUEBA
       ========================================================================== */
    const defaultState = {
      studentName: '',
      section: '',
      officialDate: '',
      sessionId: '',
      startTime: null,
      endTime: null,
      currentMission: 0,
      completed: false,
      logs: [],
      indicatorScores: {}
    };

    let session = { ...defaultState };

    // Verificar LocalStorage
    function checkLocalStorage() {
      try {
        localStorage.setItem('test_ls', '1');
        localStorage.removeItem('test_ls');
        return true;
      } catch (e) {
        alert("⚠️ ATENCIÓN DOCENTE: El almacenamiento local (localStorage) no está disponible en este navegador. Verifique la configuración antes de aplicar la prueba.");
        return false;
      }
    }

    function saveSession() {
      if (!session.sessionId) return;
      try {
        const key = `mouseTest_2026_${session.studentName}_${session.officialDate}_${session.sessionId}`;
        localStorage.setItem(key, JSON.stringify(session));
      } catch (e) {
        console.error("Error al guardar sesión en LocalStorage", e);
      }
    }

    function logTelemetry(mission, activity, indicator, expected, actual, isSuccess) {
      const entry = {
        mission,
        activity,
        indicator,
        expectedAction: expected,
        actualAction: actual,
        result: isSuccess ? 'success' : 'error',
        timestamp: new Date().toISOString()
      };
      session.logs.push(entry);
      saveSession();
    }

    function showToast(message, pose = 'happy') {
      const toast = document.getElementById('titoToast');
      document.getElementById('toastMessage').innerText = message;
      document.getElementById('toastTitoAvatar').innerHTML = getTitoSVG(pose);
      toast.classList.add('show');
      setTimeout(() => toast.classList.remove('show'), 3200);
    }

    /* ==========================================================================
       5. NAVEGACIÓN Y COMPONENTES DE INTERFAZ
       ========================================================================== */
    function renderApp() {
      const container = document.getElementById('mainContainer');

      if (session.currentMission === 0) {
        renderWelcomeScreen(container);
      } else if (session.currentMission <= 7) {
        renderMissionCard(container);
      } else {
        renderFinalScreen(container);
      }
    }

    function renderWelcomeScreen(container) {
      container.innerHTML = `
        <div class="welcome-screen">
          <div class="tito-welcome-box">${getTitoSVG('happy')}</div>
          <h1 class="welcome-title">LA AVENTURA DE TITO: MISIÓN MOUSE</h1>
          <p class="welcome-subtitle">¡Hola! Soy Tito. Ayúdame a completar todas las misiones digitales con tu mouse.</p>
          
          <div class="form-group">
            <label for="inputName">Nombre completo del estudiante:</label>
            <input type="text" id="inputName" class="form-control" placeholder="Ej. Lucía Vargas Solís" value="${session.studentName}">
          </div>

          <div class="form-group">
            <label for="inputSection">Sección:</label>
            <input type="text" id="inputSection" class="form-control" placeholder="Ej. 1-A" value="${session.section}">
          </div>

          <div class="form-group">
            <label for="inputDate">Fecha oficial de aplicación:</label>
            <input type="date" id="inputDate" class="form-control" value="${session.officialDate}">
          </div>

          <button class="btn-adventure" onclick="handleStartAdventure()">INICIAR AVENTURA 🚀</button>
        </div>
      `;
    }

    function handleStartAdventure() {
      if (!checkLocalStorage()) return;

      const name = document.getElementById('inputName').value.trim();
      const section = document.getElementById('inputSection').value.trim();
      const date = document.getElementById('inputDate').value;

      if (!name || !section || !date) {
        alert("⚠️ Por favor, la docente debe ingresar el Nombre, Sección y Fecha oficial antes de iniciar.");
        return;
      }

      session.studentName = name;
      session.section = section;
      session.officialDate = date;
      session.sessionId = 'S_' + Date.now();
      session.startTime = new Date().toISOString();
      session.currentMission = 1;

      saveSession();
      playSound('fanfare');
      renderApp();
    }

    function renderMissionCard(container) {
      const missionTitles = [
        "",
        "Misión 1: Conozco mi Mouse",
        "Misión 2: Muevo el Puntero",
        "Misión 3: Encuentra y Selecciona",
        "Misión 4: El Reto del Clic",
        "Misión 5: Las Cajas Mágicas",
        "Misión 6: El Almacén de Tito",
        "Misión 7: Busca más Objetos"
      ];

      const missionInstructions = [
        "",
        "Haz clic en cada parte del mouse que Tito te vaya indicando.",
        "Mueve físicamente tu mouse para llevar el puntero a la zona indicada.",
        "Mueve el puntero y selecciona con clic izquierdo el objeto solicitado.",
        "Sigue las instrucciones de Tito: aplica Clic Sencillo o Doble Clic.",
        "Aplica DOBLE CLIC sobre cada caja mágica para abrirlas todas.",
        "Arrastra los objetos de la parte superior hacia la categoría correcta.",
        "Usa la RUEDA del mouse para desplazarte verticalmente hacia abajo."
      ];

      // Progreso visual
      let pathHTML = '<div class="adventure-path"><div class="path-line"></div>';
      const progressWidth = ((session.currentMission - 1) / 6) * 100;
      pathHTML += `<div class="path-line-progress" style="width: ${progressWidth}%"></div>`;

      for (let i = 1; i <= 7; i++) {
        let statusClass = '';
        if (i < session.currentMission) statusClass = 'completed';
        if (i === session.currentMission) statusClass = 'active';
        pathHTML += `<div class="path-node ${statusClass}">${i < session.currentMission ? '✓' : i}</div>`;
      }
      pathHTML += '</div>';

      container.innerHTML = `
        ${pathHTML}
        <div class="mission-header-box">
          <div class="tito-avatar-small">${getTitoSVG('explaining')}</div>
          <div class="mission-title-container">
            <h2>${missionTitles[session.currentMission]}</h2>
            <p>${missionInstructions[session.currentMission]}</p>
          </div>
        </div>
        <div class="stage-canvas" id="stageArea"></div>
      `;

      loadMissionStage(session.currentMission);
    }

    /* ==========================================================================
       6. LÓGICA INTERACTIVA DE LAS 7 MISIONES (EVENTOS REALES)
       ========================================================================== */
    function loadMissionStage(m) {
      const stage = document.getElementById('stageArea');

      if (m === 1) setupMission1(stage);
      else if (m === 2) setupMission2(stage);
      else if (m === 3) setupMission3(stage);
      else if (m === 4) setupMission4(stage);
      else if (m === 5) setupMission5(stage);
      else if (m === 6) setupMission6(stage);
      else if (m === 7) setupMission7(stage);
    }

    // MISIÓN 1: CONOZCO MI MOUSE (INDICADOR 1)
    function setupMission1(stage) {
      let currentStep = 0;
      const steps = [
        { key: 'left', name: 'Botón Izquierdo' },
        { key: 'right', name: 'Botón Derecho' },
        { key: 'wheel', name: 'Rueda' },
        { key: 'sensor', name: 'Sensor / Cuerpo' }
      ];

      stage.innerHTML = `
        <div style="text-align:center;">
          <svg class="mouse-parts-svg" viewBox="0 0 200 260">
            <!-- Botón Izquierdo -->
            <path id="part-left" class="part-interactive" d="M 40 20 Q 100 20 100 80 L 40 80 Z" fill="#3B82F6"/>
            <!-- Botón Derecho -->
            <path id="part-right" class="part-interactive" d="M 100 20 Q 160 20 160 80 L 100 80 Z" fill="#2563EB"/>
            <!-- Rueda -->
            <rect id="part-wheel" class="part-interactive" x="92" y="45" width="16" height="30" rx="8" fill="#F59E0B"/>
            <!-- Sensor / Cuerpo -->
            <path id="part-sensor" class="part-interactive" d="M 40 80 L 160 80 Q 160 220 100 240 Q 40 220 40 80 Z" fill="#94A3B8"/>
          </svg>
        </div>
      `;

      showToast(`Tito dice: "Señala el ${steps[0].name}"`, "thinking");

      ['left', 'right', 'wheel', 'sensor'].forEach(partKey => {
        const el = document.getElementById(`part-${partKey}`);
        el.addEventListener('click', () => {
          const expected = steps[currentStep].key;
          if (partKey === expected) {
            playSound('success');
            logTelemetry('Misión 1', 'Reconocimiento de partes', 1, expected, partKey, true);
            currentStep++;
            if (currentStep < steps.length) {
              showToast(`¡Excelente! Ahora señala el ${steps[currentStep].name}`, "happy");
            } else {
              playSound('fanfare');
              showToast("¡Magnífico! Reconoces todas las partes del mouse.", "celebrating");
              setTimeout(nextMission, 1800);
            }
          } else {
            playSound('pop');
            logTelemetry('Misión 1', 'Reconocimiento de partes', 1, expected, partKey, false);
            showToast("¡Casi! Inténtalo nuevamente. Tito te acompaña.", "thinking");
          }
        });
      });
    }

    // MISIÓN 2: MUEVO EL PUNTERO (INDICADOR 2)
    function setupMission2(stage) {
      let targetIdx = 0;
      const targets = ['UP', 'DOWN', 'LEFT', 'RIGHT'];
      const targetLabels = { UP: 'ARRIBA', DOWN: 'ABAJO', LEFT: 'IZQUIERDA', RIGHT: 'DERECHA' };

      stage.innerHTML = `
        <div class="direction-grid">
          <div></div>
          <div class="dir-zone" id="zone-UP">⬆️<br>ARRIBA</div>
          <div></div>
          <div class="dir-zone" id="zone-LEFT">⬅️<br>IZQUIERDA</div>
          <div style="display:flex; align-items:center; justify-content:center;">🐭</div>
          <div class="dir-zone" id="zone-RIGHT">➡️<br>DERECHA</div>
          <div></div>
          <div class="dir-zone" id="zone-DOWN">⬇️<br>ABAJO</div>
          <div></div>
        </div>
      `;

      function highlightNext() {
        document.querySelectorAll('.dir-zone').forEach(z => z.classList.remove('highlight'));
        const nextKey = targets[targetIdx];
        document.getElementById(`zone-${nextKey}`).classList.add('highlight');
        showToast(`Lleva el puntero del mouse hacia ${targetLabels[nextKey]}`, "happy");
      }

      highlightNext();

      // Throttling con requestAnimationFrame para el evento real mousemove
      let ticking = false;
      stage.addEventListener('mousemove', (e) => {
        if (!ticking) {
          window.requestAnimationFrame(() => {
            const currentTarget = targets[targetIdx];
            const zoneEl = document.getElementById(`zone-${currentTarget}`);
            const rect = zoneEl.getBoundingClientRect();

            if (e.clientX >= rect.left && e.clientX <= rect.right && e.clientY >= rect.top && e.clientY <= rect.bottom) {
              playSound('success');
              logTelemetry('Misión 2', 'Desplazamiento de puntero', 2, currentTarget, currentTarget, true);
              targetIdx++;
              if (targetIdx < targets.length) {
                highlightNext();
              } else {
                playSound('fanfare');
                showToast("¡Fantástico! Dominas el puntero en todas direcciones.", "celebrating");
                setTimeout(nextMission, 1800);
              }
            }
            ticking = false;
          });
          ticking = true;
        }
      });
    }

    // MISIÓN 3: ENCUENTRA Y SELECCIONA (INDICADORES 3 Y 4)
    function setupMission3(stage) {
      let currentItemIdx = 0;
      const items = [
        { id: 'star', name: 'Estrella', svg: '<polygon points="25,2 32,18 49,18 35,29 40,46 25,35 10,46 15,29 1,18 18,18" fill="#F59E0B"/>' },
        { id: 'robot', name: 'Robot', svg: '<rect x="10" y="10" width="30" height="30" fill="#8B5CF6"/><circle cx="20" cy="20" r="3" fill="white"/><circle cx="30" cy="20" r="3" fill="white"/>' },
        { id: 'ball', name: 'Pelota', svg: '<circle cx="25" cy="25" r="20" fill="#EF4444"/><path d="M 10 25 Q 25 10 40 25" stroke="white" stroke-width="4" fill="none"/>' }
      ];

      stage.innerHTML = `
        <div class="objects-world">
          ${items.map(it => `
            <div class="world-item" id="item-${it.id}">
              <svg viewBox="0 0 50 50">${it.svg}</svg>
              <span style="font-size:0.8rem; font-weight:800; margin-top:4px;">${it.name}</span>
            </div>
          `).join('')}
        </div>
      `;

      showToast(`Busca la ${items[0].name} y haz CLIC IZQUIERDO sobre ella.`, "thinking");

      items.forEach(it => {
        document.getElementById(`item-${it.id}`).addEventListener('click', () => {
          const expected = items[currentItemIdx].id;
          if (it.id === expected) {
            playSound('success');
            logTelemetry('Misión 3', 'Señalamiento y Clic', 3, expected, it.id, true);
            logTelemetry('Misión 3', 'Ejecución Clic Izquierdo', 4, 'left-click', 'left-click', true);
            currentItemIdx++;
            if (currentItemIdx < items.length) {
              showToast(`¡Muy bien! Ahora haz clic sobre la ${items[currentItemIdx].name}.`, "happy");
            } else {
              playSound('fanfare');
              showToast("¡Excelente! Seleccionaste los objetos indicados.", "celebrating");
              setTimeout(nextMission, 1800);
            }
          } else {
            playSound('pop');
            logTelemetry('Misión 3', 'Señalamiento y Clic', 3, expected, it.id, false);
            showToast("¡Casi! Revisa bien y haz clic en el objeto correcto.", "thinking");
          }
        });
      });
    }

    // MISIÓN 4: EL RETO DEL CLIC (INDICADORES 5 Y 6)
    function setupMission4(stage) {
      let step = 0;
      const sequence = [
        { type: 'single', label: 'CLIC SENCILLO en la Estrella ⭐' },
        { type: 'double', label: 'DOBLE CLIC en el Cohete 🚀' }
      ];

      stage.innerHTML = `
        <div class="magic-boxes-container">
          <div class="world-item" id="btnStar" style="width:130px; height:130px;">
            <span style="font-size:3rem;">⭐</span>
            <span style="font-size:0.85rem; font-weight:800;">Estrella</span>
          </div>
          <div class="world-item" id="btnRocket" style="width:130px; height:130px;">
            <span style="font-size:3rem;">🚀</span>
            <span style="font-size:0.85rem; font-weight:800;">Cohete</span>
          </div>
        </div>
      `;

      showToast(`Misión: Haz ${sequence[0].label}`, "thinking");

      // Desambiguador técnico de Clic Sencillo vs Doble Clic
      let clickTimer = null;

      function bindClickDisambiguator(elementId, targetKey) {
        const el = document.getElementById(elementId);

        el.addEventListener('click', (e) => {
          if (clickTimer === null) {
            clickTimer = setTimeout(() => {
              clickTimer = null;
              handleAction(targetKey, 'single');
            }, 260);
          }
        });

        el.addEventListener('dblclick', (e) => {
          if (clickTimer) {
            clearTimeout(clickTimer);
            clickTimer = null;
          }
          handleAction(targetKey, 'double');
        });
      }

      bindClickDisambiguator('btnStar', 'star');
      bindClickDisambiguator('btnRocket', 'rocket');

      function handleAction(targetKey, actionType) {
        const currentReq = sequence[step];
        const expectedTarget = currentReq.type === 'single' ? 'star' : 'rocket';

        if (targetKey === expectedTarget && actionType === currentReq.type) {
          playSound('success');
          logTelemetry('Misión 4', 'Diferenciación Clic', 6, currentReq.type, actionType, true);
          if (actionType === 'double') {
            logTelemetry('Misión 4', 'Aplica Doble Clic', 5, 'double', 'double', true);
          }
          step++;
          if (step < sequence.length) {
            showToast(`¡Excelente! Ahora haz ${sequence[step].label}`, "happy");
          } else {
            playSound('fanfare');
            showToast("¡Increíble! Diferencias perfectamente el clic del doble clic.", "celebrating");
            setTimeout(nextMission, 1800);
          }
        } else {
          playSound('pop');
          logTelemetry('Misión 4', 'Diferenciación Clic', 6, currentReq.type, actionType, false);
          showToast("¡Casi! Inténtalo otra vez con la acción correcta.", "thinking");
        }
      }
    }

    // MISIÓN 5: LAS CAJAS MÁGICAS (INDICADOR 7)
    function setupMission5(stage) {
      let openedCount = 0;

      stage.innerHTML = `
        <div class="magic-boxes-container">
          <div class="magic-box-card" id="box1"><span style="font-size:3rem;">🎁</span><span>Caja 1</span></div>
          <div class="magic-box-card" id="box2"><span style="font-size:3rem;">🎁</span><span>Caja 2</span></div>
        </div>
      `;

      showToast("Haz DOBLE CLIC sobre las cajas para abrir los regalos.", "happy");

      ['box1', 'box2'].forEach(boxId => {
        const boxEl = document.getElementById(boxId);

        boxEl.addEventListener('click', () => {
          if (!boxEl.classList.contains('opened')) {
            playSound('pop');
            logTelemetry('Misión 5', 'Abrir recursos con doble clic', 7, 'double-click', 'single-click', false);
            showToast("Recuerda: ¡Haz DOBLE CLIC rápido para abrir la caja!", "thinking");
          }
        });

        boxEl.addEventListener('dblclick', () => {
          if (!boxEl.classList.contains('opened')) {
            boxEl.classList.add('opened');
            boxEl.innerHTML = `<span style="font-size:3.5rem;">🎉</span><span>¡Abierta!</span>`;
            playSound('success');
            logTelemetry('Misión 5', 'Abrir recursos con doble clic', 7, 'double-click', 'double-click', true);
            openedCount++;

            if (openedCount === 2) {
              playSound('fanfare');
              showToast("¡Espectacular! Abriste todas las cajas mágicas.", "celebrating");
              setTimeout(nextMission, 1800);
            }
          }
        });
      });
    }

    // MISIÓN 6: EL ALMACÉN DE TITO (INDICADORES 8 Y 9)
    function setupMission6(stage) {
      let sortedCount = 0;

      stage.innerHTML = `
        <div class="warehouse-container">
          <div class="drag-items-pool" id="dragPool">
            <div class="world-item" draggable="true" id="item-ball" data-cat="JUGUETES"><span style="font-size:2rem;">⚽</span><span>Pelota</span></div>
            <div class="world-item" draggable="true" id="item-pencil" data-cat="ÚTILES"><span style="font-size:2rem;">✏️</span><span>Lápiz</span></div>
            <div class="world-item" draggable="true" id="item-mouse" data-cat="OBJETOS DIGITALES"><span style="font-size:2rem;">🖱️</span><span>Mouse</span></div>
          </div>
          <div class="drop-categories">
            <div class="drop-zone-box" id="drop-JUGUETES">
              <span class="drop-zone-title">⚽ JUGUETES</span>
            </div>
            <div class="drop-zone-box" id="drop-ÚTILES">
              <span class="drop-zone-title">✏️ ÚTILES</span>
            </div>
            <div class="drop-zone-box" id="drop-OBJETOS DIGITALES">
              <span class="drop-zone-title">💻 DIGITALES</span>
            </div>
          </div>
        </div>
      `;

      showToast("Arrastra cada objeto hacia su categoría correspondiente.", "happy");

      const items = stage.querySelectorAll('[draggable="true"]');
      const dropZones = stage.querySelectorAll('.drop-zone-box');

      items.forEach(item => {
        item.addEventListener('dragstart', (e) => {
          e.dataTransfer.setData('text/plain', item.id);
          logTelemetry('Misión 6', 'Acción Arrastrar', 8, 'drag', 'drag', true);
        });
      });

      dropZones.forEach(zone => {
        zone.addEventListener('dragover', (e) => {
          e.preventDefault();
          zone.classList.add('drag-over');
        });

        zone.addEventListener('dragleave', () => {
          zone.classList.remove('drag-over');
        });

        zone.addEventListener('drop', (e) => {
          e.preventDefault();
          zone.classList.remove('drag-over');
          const itemId = e.dataTransfer.getData('text/plain');
          const itemEl = document.getElementById(itemId);

          if (!itemEl) return;

          const itemCat = itemEl.getAttribute('data-cat');
          const targetCat = zone.id.replace('drop-', '');

          if (itemCat === targetCat) {
            playSound('success');
            zone.appendChild(itemEl);
            itemEl.setAttribute('draggable', 'false');
            logTelemetry('Misión 6', 'Clasificación Arrastrar/Soltar', 9, targetCat, itemCat, true);
            sortedCount++;

            if (sortedCount === 3) {
              playSound('fanfare');
              showToast("¡Magnífico! Clasificaste todos los objetos del almacén.", "celebrating");
              setTimeout(nextMission, 1800);
            }
          } else {
            playSound('pop');
            logTelemetry('Misión 6', 'Clasificación Arrastrar/Soltar', 9, targetCat, itemCat, false);
            showToast("¡Busca el lugar correcto! Tito te acompaña.", "thinking");
          }
        });
      });
    }

    // MISIÓN 7: BUSCA MÁS OBJETOS (INDICADOR 10)
    function setupMission7(stage) {
      let wheelDetected = false;

      stage.innerHTML = `
        <div class="scroll-view-stage" id="scrollStage">
          <div class="scroll-content-long">
            <p style="font-weight:800; color:var(--primary-dark);">👇 Usa la RUEDA del mouse para bajar por el camino...</p>
            <div class="hidden-treasure-item" id="treasureItem">
              <span style="font-size:2rem;">💎</span>
              <span>¡Encontraste el Tesoro Escondido! (Haz Clic)</span>
            </div>
          </div>
        </div>
      `;

      showToast("Gira la RUEDA del mouse hacia abajo para buscar el tesoro.", "happy");

      const scrollStage = document.getElementById('scrollStage');

      // Evento real wheel
      scrollStage.addEventListener('wheel', (e) => {
        if (e.deltaY > 0 && !wheelDetected) {
          wheelDetected = true;
          playSound('click');
          logTelemetry('Misión 7', 'Uso Rueda del Mouse', 10, 'wheel-down', 'wheel-down', true);
        }
      });

      document.getElementById('treasureItem').addEventListener('click', () => {
        if (wheelDetected) {
          playSound('fanfare');
          logTelemetry('Misión 7', 'Localización de Objeto con Scroll', 10, 'find-item', 'find-item', true);
          showToast("¡Felicidades! Completaste la aventura con la rueda del mouse.", "celebrating");
          setTimeout(nextMission, 1800);
        } else {
          playSound('pop');
          showToast("Primero debes usar la rueda del mouse para desplazarte.", "thinking");
        }
      });
    }

    function nextMission() {
      session.currentMission++;
      if (session.currentMission > 7) {
        session.completed = true;
        session.endTime = new Date().toISOString();
      }
      saveSession();
      renderApp();
    }

    /* ==========================================================================
       7. EVALUACIÓN Y CÁLCULO DE RÚBRICA (10 INDICADORES, 30 PTS MÁX)
       ========================================================================== */
    function calculateEvaluation() {
      // Definición oficial de los 10 indicadores y sus rúbricas
      const indicators = [
        {
          id: 1,
          title: "Reconocer las partes principales del mouse",
          rubric: {
            3: "Reconoce todas las partes principales del mouse y relaciona cada una con su función.",
            2: "Reconoce la mayoría de las partes principales del mouse y relaciona sus funciones.",
            1: "Reconoce algunas partes principales del mouse y relaciona algunas funciones.",
            0: "Omite el reconocimiento de las partes principales del mouse."
          }
        },
        {
          id: 2,
          title: "Manipular el mouse en diferentes direcciones",
          rubric: {
            3: "Manipula el mouse para dirigir el puntero correctamente hacia las cuatro direcciones indicadas.",
            2: "Manipula el mouse para dirigir el puntero hacia tres de las direcciones indicadas.",
            1: "Manipula el mouse para dirigir el puntero hacia dos de las direcciones indicadas.",
            0: "Omite la manipulación del mouse para dirigir el puntero hacia las direcciones indicadas."
          }
        },
        {
          id: 3,
          title: "Señalar objetos en diferentes zonas",
          rubric: {
            3: "Señala correctamente todos los objetos ubicados en las zonas indicadas.",
            2: "Señala correctamente la mayoría de los objetos ubicados en las zonas indicadas.",
            1: "Señala correctamente algunos de los objetos ubicados en las zonas indicadas.",
            0: "Omite señalar los objetos ubicados en las zonas indicadas."
          }
        },
        {
          id: 4,
          title: "Ejecutar clic izquierdo",
          rubric: {
            3: "Ejecuta el clic izquierdo correctamente sobre todos los elementos indicados.",
            2: "Ejecuta el clic izquierdo correctamente sobre la mayoría de los elementos indicados.",
            1: "Ejecuta el clic izquierdo correctamente sobre algunos de los elementos indicados.",
            0: "Omite la ejecución del clic izquierdo sobre los elementos indicados."
          }
        },
        {
          id: 5,
          title: "Aplicar el doble clic para seleccionar",
          rubric: {
            3: "Aplica el doble clic correctamente en todas las actividades indicadas.",
            2: "Aplica el doble clic correctamente en la mayoría de las actividades indicadas.",
            1: "Aplica el doble clic correctamente en algunas de las actividades indicadas.",
            0: "Omite la aplicación del doble clic en las actividades indicadas."
          }
        },
        {
          id: 6,
          title: "Diferenciar clic sencillo de doble clic",
          rubric: {
            3: "Diferencia el clic sencillo del doble clic durante todas las actividades indicadas.",
            2: "Diferencia el clic sencillo del doble clic durante la mayoría de las actividades indicadas.",
            1: "Diferencia el clic sencillo del doble clic durante algunas de las actividades indicadas.",
            0: "Omite la diferenciación entre el clic sencillo y el doble clic."
          }
        },
        {
          id: 7,
          title: "Ejecutar doble clic para abrir recursos",
          rubric: {
            3: "Ejecuta el doble clic para abrir correctamente todos los recursos indicados.",
            2: "Ejecuta el doble clic para abrir correctamente la mayoría de los recursos indicados.",
            1: "Ejecuta el doble clic para abrir correctamente algunos de los recursos indicados.",
            0: "Omite la ejecución del doble clic para abrir los recursos indicados."
          }
        },
        {
          id: 8,
          title: "Ejecutar acción de arrastrar y soltar",
          rubric: {
            3: "Ejecuta correctamente el arrastre y suelta todos los objetos en los espacios indicados.",
            2: "Ejecuta correctamente el arrastre y suelta la mayoría de los objetos en los espacios indicados.",
            1: "Ejecuta correctamente el arrastre y suelta algunos de los objetos en los espacios indicados.",
            0: "Omite la ejecución del arrastre y soltar de los objetos indicados."
          }
        },
        {
          id: 9,
          title: "Clasificar objetos mediante arrastrar y soltar",
          rubric: {
            3: "Clasifica correctamente todos los objetos mediante arrastrar y soltar.",
            2: "Clasifica correctamente la mayoría de los objetos mediante arrastrar y soltar.",
            1: "Clasifica correctamente algunos objetos mediante arrastrar y soltar.",
            0: "Omite la clasificación de los objetos mediante arrastrar y soltar."
          }
        },
        {
          id: 10,
          title: "Utilizar la rueda del mouse (Scroll)",
          rubric: {
            3: "Utiliza correctamente la rueda del mouse para desplazarse verticalmente por todo el contenido indicado.",
            2: "Utiliza correctamente la rueda del mouse para desplazarse por la mayoría del contenido indicado.",
            1: "Utiliza correctamente la rueda del mouse para desplazarse por parte del contenido indicado.",
            0: "Omite el uso de la rueda del mouse para desplazarse verticalmente."
          }
        }
      ];

      let results = [];
      let totalEarned = 0;

      indicators.forEach(ind => {
        const indLogs = session.logs.filter(l => l.indicator === ind.id);
        const successes = indLogs.filter(l => l.result === 'success').length;
        const errors = indLogs.filter(l => l.result === 'error').length;
        const attempts = indLogs.length;

        let score = 3;
        if (attempts === 0) {
          score = 0;
        } else if (errors === 0 || (errors <= 1 && successes >= 1)) {
          score = 3; // Muy bueno
        } else if (errors <= 3 && successes >= 1) {
          score = 2; // Bueno
        } else if (successes >= 1) {
          score = 1; // Por mejorar
        } else {
          score = 0; // Omisión
        }

        totalEarned += score;

        let statusTag = "✓ Logrado";
        if (score === 2 || score === 1) statusTag = "◐ En proceso";
        if (score === 0) statusTag = "○ Pendiente";

        results.push({
          indicatorId: ind.id,
          title: ind.title,
          score,
          descriptor: ind.rubric[score],
          successes,
          errors,
          attempts,
          statusTag
        });
      });

      const percentage = Math.round((totalEarned / 30) * 100);

      // Dificultades observadas reales
      let difficulties = [];
      results.forEach(r => {
        if (r.errors > 1) {
          if (r.indicatorId === 6 || r.indicatorId === 5) {
            difficulties.push("Presentó dificultad inicial para diferenciar o aplicar el doble clic.");
          } else if (r.indicatorId === 9) {
            difficulties.push("Presentó vacilaciones durante la clasificación de objetos mediante arrastrar y soltar.");
          } else {
            difficulties.push(`Requirió reintentos adicionales en la habilidad de: ${r.title}.`);
          }
        }
      });

      if (difficulties.length === 0) {
        difficulties.push("Demostró un desempeño fluido y consistente durante todas las misiones realizadas.");
      }

      return {
        results,
        totalEarned,
        maxScore: 30,
        percentage,
        difficulties
      };
    }

    /* ==========================================================================
       8. PANTALLA FINAL DE CELEBRACIÓN Y GENERACIÓN DE EVIDENCIAS
       ========================================================================== */
    function renderFinalScreen(container) {
      playSound('fanfare');
      const evalData = calculateEvaluation();

      container.innerHTML = `
        <div class="celebration-screen">
          <div style="width:120px; height:120px;">${getTitoSVG('celebrating')}</div>
          <h1 style="color:var(--primary-dark); margin:0;">¡AVENTURA COMPLETADA!</h1>
          <p style="font-size:1.1rem; color:var(--text-muted); margin:0;">
            ¡Felicitaciones <strong>${session.studentName}</strong>! Has completado con éxito la Aventura de Tito.
          </p>

          <h3 style="margin-top:20px; color:var(--primary-dark);">Resumen "LO QUE HICE HOY"</h3>
          <table class="summary-table">
            <thead>
              <tr>
                <th>Misión / Habilidad</th>
                <th>Estado</th>
                <th>Aciertos</th>
                <th>Errores</th>
                <th>Detalle Observado</th>
              </tr>
            </thead>
            <tbody>
              ${evalData.results.map(r => `
                <tr>
                  <td><strong>${r.title}</strong></td>
                  <td>${r.statusTag}</td>
                  <td>${r.successes}</td>
                  <td>${r.errors}</td>
                  <td>${r.descriptor}</td>
                </tr>
              `).join('')}
            </tbody>
          </table>

          <div class="btn-action-group">
            <button class="btn-adventure" style="width:auto; padding:12px 24px;" onclick="generatePNGCertificate()">
              💾 GUARDAR EVIDENCIA (PNG)
            </button>
            <button class="btn-secondary-action" onclick="window.print()">
              🖨️ IMPRIMIR EVIDENCIA
            </button>
            <button class="btn-secondary-action" style="background:var(--purple);" onclick="renderTeacherReportModal()">
              📋 VER REPORTE DOCENTE
            </button>
            <button class="btn-secondary-action" style="background:#64748B;" onclick="handleNewStudent()">
              👤 NUEVO ESTUDIANTE
            </button>
          </div>
        </div>
      `;
    }

    // GENERADOR DE CERTIFICADO PNG (100% OFFLINE VÍA CANVAS)
    function generatePNGCertificate() {
      const evalData = calculateEvaluation();
      const canvas = document.createElement('canvas');
      canvas.width = 1000;
      canvas.height = 1300;
      const ctx = canvas.getContext('2d');

      // Fondo
      ctx.fillStyle = '#FFFFFF';
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      // Marco Decorativo
      ctx.strokeStyle = '#3B82F6';
      ctx.lineWidth = 12;
      ctx.strokeRect(20, 20, canvas.width - 40, canvas.height - 40);

      // Encabezado
      ctx.fillStyle = '#1D4ED8';
      ctx.font = 'bold 26px sans-serif';
      ctx.textAlign = 'center';
      ctx.fillText('COLEGIO DIOCESANO PADRE ELADIO SANCHO', 500, 70);

      ctx.fillStyle = '#64748B';
      ctx.font = '18px sans-serif';
      ctx.fillText('Departamento de Informática Educativa | Evidencia de Prueba de Ejecución 2026', 500, 100);

      ctx.fillStyle = '#10B981';
      ctx.font = 'bold 32px sans-serif';
      ctx.fillText('¡CERTIFICADO DE AVENTURA DIGITAL!', 500, 160);

      // Datos del Estudiante
      ctx.textAlign = 'left';
      ctx.fillStyle = '#1E293B';
      ctx.font = 'bold 20px sans-serif';
      ctx.fillText(`Estudiante: ${session.studentName}`, 60, 220);
      ctx.fillText(`Sección: ${session.section}`, 60, 250);
      ctx.fillText(`Fecha Oficial: ${session.officialDate}`, 600, 220);
      ctx.fillText(`Docente: Grettel Monge Rojas`, 600, 250);

      // Calificación
      ctx.fillStyle = '#F8FAFC';
      ctx.fillRect(60, 280, 880, 70);
      ctx.strokeRect(60, 280, 880, 70);

      ctx.fillStyle = '#1D4ED8';
      ctx.font = 'bold 22px sans-serif';
      ctx.fillText(`Puntaje Obt.: ${evalData.totalEarned} / 30 pts`, 90, 322);
      ctx.fillText(`Porcentaje: ${evalData.percentage}%`, 400, 322);
      ctx.fillText(`Valor: 30%`, 750, 322);

      // Tabla de Desempeño
      ctx.fillStyle = '#1D4ED8';
      ctx.font = 'bold 20px sans-serif';
      ctx.fillText('Resumen de Indicadores Evaluados:', 60, 390);

      let yPos = 430;
      evalData.results.forEach((r, idx) => {
        ctx.fillStyle = idx % 2 === 0 ? '#F1F5F9' : '#FFFFFF';
        ctx.fillRect(60, yPos - 20, 880, 35);

        ctx.fillStyle = '#1E293B';
        ctx.font = '15px sans-serif';
        ctx.fillText(`${r.indicatorId}. ${r.title.substring(0, 38)}`, 70, yPos);
        ctx.fillText(`Pts: ${r.score}/3`, 500, yPos);
        ctx.fillText(`${r.statusTag}`, 600, yPos);
        ctx.fillText(`Err: ${r.errors}`, 780, yPos);

        yPos += 38;
      });

      // Dificultades / Observaciones
      yPos += 20;
      ctx.fillStyle = '#1D4ED8';
      ctx.font = 'bold 18px sans-serif';
      ctx.fillText('Observaciones de Desempeño:', 60, yPos);

      yPos += 30;
      ctx.fillStyle = '#475569';
      ctx.font = '16px sans-serif';
      evalData.difficulties.forEach(d => {
        ctx.fillText(`• ${d}`, 70, yPos);
        yPos += 25;
      });

      // Descargar como archivo PNG
      const link = document.createElement('a');
      const cleanName = session.studentName.replace(/\s+/g, '_');
      link.download = `Evidencia_Prueba_Mouse_${cleanName}_${session.officialDate}.png`;
      link.href = canvas.toDataURL('image/png');
      link.click();
    }

    // REPORTE COMPLETO PARA LA DOCENTE
    function renderTeacherReportModal() {
      const evalData = calculateEvaluation();
      const reportWindow = window.open('', '_blank');

      reportWindow.document.write(`
        <!DOCTYPE html>
        <html lang="es">
        <head>
          <title>Reporte Docente - ${session.studentName}</title>
          <style>
            body { font-family: sans-serif; padding: 30px; color: #1E293B; }
            h1, h2 { color: #1D4ED8; margin-bottom: 4px; }
            table { width: 100%; border-collapse: collapse; margin-top: 16px; }
            th, td { border: 1px solid #CBD5E1; padding: 10px; text-align: left; font-size: 0.9rem; }
            th { background: #F1F5F9; }
            .badge { font-weight: bold; padding: 4px 8px; border-radius: 6px; }
          </style>
        </head>
        <body>
          <h1>COLEGIO DIOCESANO PADRE ELADIO SANCHO</h1>
          <p><strong>Departamento de Informática Educativa | Reporte Docente Oficial 2026</strong></p>
          <hr>
          <p><strong>Estudiante:</strong> ${session.studentName} | <strong>Sección:</strong> ${session.section}</p>
          <p><strong>Fecha Oficial de Prueba:</strong> ${session.officialDate} | <strong>Docente:</strong> Grettel Monge Rojas</p>
          <p><strong>Puntaje Obtenido:</strong> ${evalData.totalEarned} / 30 pts | <strong>Porcentaje:</strong> ${evalData.percentage}% (Valor: 30%)</p>

          <h2>Desglose de los 10 Indicadores Evaluados:</h2>
          <table>
            <thead>
              <tr>
                <th>#</th>
                <th>Indicador</th>
                <th>Puntos</th>
                <th>Descriptor de Rúbrica</th>
                <th>Aciertos</th>
                <th>Errores</th>
                <th>Intentos</th>
              </tr>
            </thead>
            <tbody>
              ${evalData.results.map(r => `
                <tr>
                  <td>${r.indicatorId}</td>
                  <td><strong>${r.title}</strong></td>
                  <td><strong>${r.score} / 3</strong></td>
                  <td>${r.descriptor}</td>
                  <td>${r.successes}</td>
                  <td>${r.errors}</td>
                  <td>${r.attempts}</td>
                </tr>
              `).join('')}
            </tbody>
          </table>

          <h2>Dificultades y Observaciones Registradas:</h2>
          <ul>
            ${evalData.difficulties.map(d => `<li>${d}</li>`).join('')}
          </ul>

          <br>
          <button onclick="window.print()">🖨️ Imprimir Reporte / Guardar PDF</button>
        </body>
        </html>
      `);
    }

    function handleNewStudent() {
      if (confirm("Antes de comenzar con otro estudiante, asegúrate de haber guardado o impreso la evidencia. ¿Deseas iniciar una nueva sesión?")) {
        session = { ...defaultState };
        renderApp();
      }
    }

    /* ==========================================================================
       9. RECUPERACIÓN DE SESIÓN EN RECARGA
       ========================================================================== */
    window.addEventListener('DOMContentLoaded', () => {
      // Buscar si existe alguna prueba guardada en progreso
      let foundKey = null;
      for (let i = 0; i < localStorage.length; i++) {
        const key = localStorage.key(i);
        if (key.startsWith('mouseTest_2026_')) {
          foundKey = key;
          break;
        }
      }

      if (foundKey) {
        try {
          const savedData = JSON.parse(localStorage.getItem(foundKey));
          if (savedData && !savedData.completed && savedData.studentName) {
            if (confirm(`Encontramos una prueba en progreso de: ${savedData.studentName} (${savedData.section}). ¿Deseas CONTINUAR la sesión?`)) {
              session = savedData;
            } else {
              localStorage.removeItem(foundKey);
            }
          }
        } catch (e) {
          console.error("Error recuperando sesión", e);
        }
      }

      renderApp();
    });
  </script>
</body>
</html>
