<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>La Aventura Digital con Tito - Desafío de Habilidades Digitales</title>
  <style>
    :root {
      --primary: #4A90E2;
      --secondary: #FF9F43;
      --accent: #2ECC71;
      --danger: #FF5252;
      --bg: #EEF5FC;
      --card-bg: #FFFFFF;
      --text: #2C3E50;
    }

    * {
      box-sizing: border-box;
      user-select: none;
      font-family: 'Comic Sans MS', 'Chalkboard SE', 'Fredoka', cursive, sans-serif;
    }

    body {
      margin: 0;
      padding: 0;
      background-color: var(--bg);
      color: var(--text);
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    /* HEADER & BARRA DE PROGRESO */
    header {
      background: linear-gradient(135deg, #1e3c72, #2a5298);
      color: white;
      padding: 15px 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      box-shadow: 0 4px 10px rgba(0,0,0,0.15);
    }

    .top-bar {
      display: flex;
      justify-content: space-between;
      width: 100%;
      max-width: 1000px;
      align-items: center;
    }

    .student-badge {
      background: rgba(255,255,255,0.2);
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 1rem;
    }

    .progress-container {
      width: 100%;
      max-width: 1000px;
      margin-top: 15px;
    }

    .progress-path {
      display: flex;
      justify-content: space-between;
      position: relative;
      align-items: center;
    }

    .progress-path::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 0;
      right: 0;
      height: 6px;
      background: rgba(255,255,255,0.3);
      z-index: 1;
      transform: translateY(-50%);
    }

    .progress-step {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background: #7f8c8d;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      z-index: 2;
      border: 3px solid white;
      transition: all 0.3s ease;
    }

    .progress-step.active {
      background: var(--secondary);
      transform: scale(1.15);
      box-shadow: 0 0 12px var(--secondary);
    }

    .progress-step.completed {
      background: var(--accent);
    }

    /* CONTENEDOR PRINCIPAL */
    main {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .mission-card {
      background: var(--card-bg);
      border-radius: 24px;
      box-shadow: 0 8px 30px rgba(0,0,0,0.08);
      width: 100%;
      max-width: 950px;
      min-height: 520px;
      padding: 25px;
      display: flex;
      flex-direction: column;
      position: relative;
      overflow: hidden;
    }

    .mission-header {
      display: flex;
      align-items: center;
      gap: 15px;
      margin-bottom: 20px;
      border-bottom: 2px dashed #E2E8F0;
      padding-bottom: 12px;
    }

    .tito-avatar {
      width: 70px;
      height: 70px;
      flex-shrink: 0;
    }

    .mission-title-box h2 {
      margin: 0;
      color: var(--primary);
      font-size: 1.5rem;
    }

    .mission-title-box p {
      margin: 4px 0 0 0;
      color: #64748B;
      font-size: 1.05rem;
    }

    .stage-area {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      background: #F8FAFC;
      border-radius: 16px;
      border: 2px inset #E2E8F0;
      padding: 20px;
      min-height: 350px;
    }

    /* REGISTRO INICIAL */
    .register-form {
      display: flex;
      flex-direction: column;
      gap: 15px;
      width: 100%;
      max-width: 400px;
      margin: 0 auto;
      text-align: center;
    }

    .register-form input {
      padding: 12px 18px;
      font-size: 1.1rem;
      border: 2px solid #CBD5E1;
      border-radius: 12px;
      outline: none;
    }

    .btn-start {
      background: var(--accent);
      color: white;
      font-size: 1.3rem;
      font-weight: bold;
      padding: 14px;
      border: none;
      border-radius: 14px;
      cursor: pointer;
      box-shadow: 0 4px 12px rgba(46, 204, 113, 0.4);
      transition: transform 0.2s;
    }

    .btn-start:hover {
      transform: scale(1.04);
    }

    /* MISIÓN 1: MOUSE */
    .mouse-illustration {
      position: relative;
      width: 320px;
      height: 300px;
    }

    .mouse-part {
      cursor: pointer;
      transition: filter 0.2s;
    }

    .mouse-part:hover {
      filter: brightness(1.2);
    }

    .part-label {
      position: absolute;
      background: white;
      border: 2px solid var(--primary);
      border-radius: 8px;
      padding: 4px 10px;
      font-size: 0.9rem;
      font-weight: bold;
      pointer-events: none;
    }

    /* MISIÓN 2: DIRECCIONES */
    .grid-directions {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: repeat(3, 1fr);
      gap: 15px;
      width: 340px;
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
      font-size: 1rem;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.2s;
    }

    .dir-zone:hover {
      border-color: var(--primary);
      background: #EBF5FF;
      transform: scale(1.05);
    }

    /* MISIÓN 3 & 6: DRAG & DROP */
    .drag-items-container {
      display: flex;
      gap: 20px;
      flex-wrap: wrap;
      justify-content: center;
      margin-bottom: 20px;
    }

    .draggable-obj {
      width: 80px;
      height: 80px;
      background: white;
      border: 2px solid #CBD5E1;
      border-radius: 16px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2.5rem;
      cursor: grab;
      box-shadow: 0 4px 8px rgba(0,0,0,0.08);
      transition: transform 0.2s;
    }

    .draggable-obj:active {
      cursor: grabbing;
      transform: scale(1.1);
    }

    .drop-zones-container {
      display: flex;
      gap: 20px;
      width: 100%;
      justify-content: space-around;
    }

    .drop-box {
      flex: 1;
      min-height: 160px;
      background: #F1F5F9;
      border: 3px dashed #94A3B8;
      border-radius: 16px;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 10px;
    }

    .drop-box.hovered {
      background: #E2E8F0;
      border-color: var(--primary);
    }

    .drop-box h4 {
      margin: 5px 0;
      color: var(--primary);
    }

    /* MISIÓN 4 & 5: CAJAS MÁGICAS & CLIC */
    .magic-boxes-grid {
      display: flex;
      gap: 30px;
    }

    .magic-box {
      width: 120px;
      height: 120px;
      background: linear-gradient(135deg, #FF9F43, #EE5253);
      border-radius: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3rem;
      color: white;
      cursor: pointer;
      box-shadow: 0 8px 15px rgba(238, 82, 83, 0.3);
      transition: transform 0.2s;
      position: relative;
    }

    .magic-box.opened {
      background: #2ECC71;
      box-shadow: 0 8px 15px rgba(46, 204, 113, 0.3);
    }

    /* MISIÓN 7: SCROLL VERTICAL */
    .scroll-stage {
      width: 100%;
      height: 320px;
      overflow-y: scroll;
      background: linear-gradient(to bottom, #87CEEB, #E0F6FF, #FFF5E6);
      border-radius: 16px;
      padding: 20px;
      position: relative;
    }

    .scroll-content {
      height: 1200px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
    }

    .scroll-item {
      background: white;
      border-radius: 12px;
      padding: 15px 25px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      display: flex;
      align-items: center;
      gap: 15px;
      font-size: 1.2rem;
      font-weight: bold;
      cursor: pointer;
    }

    /* RETROALIMENTACIÓN DE TITO */
    .feedback-toast {
      position: absolute;
      bottom: 25px;
      left: 50%;
      transform: translateX(-50%) translateY(100px);
      background: #2C3E50;
      color: white;
      padding: 12px 25px;
      border-radius: 30px;
      font-size: 1.1rem;
      font-weight: bold;
      box-shadow: 0 4px 20px rgba(0,0,0,0.25);
      opacity: 0;
      transition: all 0.4s ease;
      display: flex;
      align-items: center;
      gap: 10px;
      z-index: 100;
    }

    .feedback-toast.show {
      transform: translateX(-50%) translateY(0);
      opacity: 1;
    }

    /* PANTALLA FINAL Y RÚBRICA */
    .final-container {
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 20px;
      align-items: center;
    }

    .certificate-header {
      text-align: center;
      background: #FFF9E6;
      border: 3px double var(--secondary);
      border-radius: 16px;
      padding: 20px;
      width: 100%;
    }

    .rubric-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 15px;
      font-size: 0.88rem;
      background: white;
    }

    .rubric-table th, .rubric-table td {
      border: 1px solid #CBD5E1;
      padding: 8px 10px;
      text-align: left;
    }

    .rubric-table th {
      background: #F1F5F9;
      color: var(--primary);
    }

    .rubric-table tr.selected-level-3 td.lvl-3 {
      background: #D1FAE5;
      font-weight: bold;
      border: 2px solid var(--accent);
    }

    .rubric-table tr.selected-level-2 td.lvl-2 {
      background: #FEF3C7;
      font-weight: bold;
      border: 2px solid var(--secondary);
    }

    .rubric-table tr.selected-level-1 td.lvl-1 {
      background: #FEE2E2;
      font-weight: bold;
      border: 2px solid var(--danger);
    }

    .rubric-table tr.selected-level-0 td.lvl-0 {
      background: #E2E8F0;
      font-weight: bold;
    }

    .score-cell {
      text-align: center !important;
      font-weight: bold;
    }

    .btn-print {
      background: var(--primary);
      color: white;
      font-size: 1.1rem;
      padding: 12px 24px;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      margin-top: 15px;
      box-shadow: 0 4px 10px rgba(74, 144, 226, 0.3);
    }

    @media print {
      header, .btn-print, .progress-container {
        display: none !important;
      }
      body {
        background: white;
      }
      .mission-card {
        box-shadow: none;
        border: none;
        padding: 0;
      }
    }
  </style>
</head>
<body>

  <!-- ENCABEZADO -->
  <header>
    <div class="top-bar">
      <h1 style="margin:0; font-size:1.4rem;">🐭 Aventura Digital con Tito</h1>
      <div class="student-badge" id="studentDisplay">Estudiante: Invitado</div>
    </div>
    
    <div class="progress-container">
      <div class="progress-path">
        <div class="progress-step active" id="step-1">1</div>
        <div class="progress-step" id="step-2">2</div>
        <div class="progress-step" id="step-3">3</div>
        <div class="progress-step" id="step-4">4</div>
        <div class="progress-step" id="step-5">5</div>
        <div class="progress-step" id="step-6">6</div>
        <div class="progress-step" id="step-7">7</div>
        <div class="progress-step" id="step-8">🏆</div>
      </div>
    </div>
  </header>

  <!-- CONTENEDOR DE CONTENIDO -->
  <main>
    <div class="mission-card" id="mainCard">
      <!-- Se carga dinámicamente mediante JS -->
    </div>
  </main>

  <!-- NOTIFICACIÓN DE TITO -->
  <div class="feedback-toast" id="feedbackToast">
    <div id="toastTitoIcon" style="width:35px; height:35px;"></div>
    <span id="toastMessage">¡Hola! Soy Tito.</span>
  </div>

  <script>
    /* ==========================================================================
       AUDIO SYNTHESIZER (WEB AUDIO API - SIN ARCHIVOS EXTERNOS)
       ========================================================================== */
    const AudioCtx = new (window.AudioContext || window.webkitAudioContext)();

    function playSound(type) {
      if (AudioCtx.state === 'suspended') AudioCtx.resume();
      const osc = AudioCtx.createOscillator();
      const gain = AudioCtx.createGain();
      osc.connect(gain);
      gain.connect(AudioCtx.destination);

      if (type === 'click') {
        osc.frequency.setValueAtTime(600, AudioCtx.currentTime);
        gain.gain.setValueAtTime(0.1, AudioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.01, AudioCtx.currentTime + 0.05);
        osc.start();
        osc.stop(AudioCtx.currentTime + 0.05);
      } else if (type === 'success') {
        osc.frequency.setValueAtTime(440, AudioCtx.currentTime);
        osc.frequency.exponentialRampToValueAtTime(880, AudioCtx.currentTime + 0.2);
        gain.gain.setValueAtTime(0.2, AudioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.01, AudioCtx.currentTime + 0.2);
        osc.start();
        osc.stop(AudioCtx.currentTime + 0.2);
      } else if (type === 'pop') {
        osc.frequency.setValueAtTime(300, AudioCtx.currentTime);
        osc.frequency.exponentialRampToValueAtTime(600, AudioCtx.currentTime + 0.1);
        gain.gain.setValueAtTime(0.3, AudioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.01, AudioCtx.currentTime + 0.1);
        osc.start();
        osc.stop(AudioCtx.currentTime + 0.1);
      } else if (type === 'fanfare') {
        const notes = [523.25, 659.25, 783.99, 1046.50];
        notes.forEach((freq, idx) => {
          const noteOsc = AudioCtx.createOscillator();
          const noteGain = AudioCtx.createGain();
          noteOsc.connect(noteGain);
          noteGain.connect(AudioCtx.destination);
          noteOsc.frequency.value = freq;
          noteGain.gain.setValueAtTime(0.15, AudioCtx.currentTime + idx * 0.12);
          noteGain.gain.exponentialRampToValueAtTime(0.01, AudioCtx.currentTime + idx * 0.12 + 0.3);
          noteOsc.start(AudioCtx.currentTime + idx * 0.12);
          noteOsc.stop(AudioCtx.currentTime + idx * 0.12 + 0.3);
        });
      }
    }

    /* ==========================================================================
       SVG DEL PERSONAJE TITO (ILUSTRACIÓN ORIGINAL VECTORIAL)
       ========================================================================== */
    function getTitoSVG(pose = 'happy') {
      let eyeExpression = `<circle cx="38" cy="42" r="5" fill="#2C3E50"/><circle cx="62" cy="42" r="5" fill="#2C3E50"/><circle cx="40" cy="40" r="2" fill="white"/><circle cx="64" cy="40" r="2" fill="white"/>`;
      let mouthExpression = `<path d="M 40 58 Q 50 68 60 58" stroke="#2C3E50" stroke-width="3" fill="none" stroke-linecap="round"/>`;

      if (pose === 'surprised') {
        mouthExpression = `<circle cx="50" cy="60" r="6" fill="#2C3E50"/>`;
      } else if (pose === 'thinking') {
        eyeExpression = `<circle cx="38" cy="40" r="5" fill="#2C3E50"/><circle cx="62" cy="40" r="5" fill="#2C3E50"/>`;
        mouthExpression = `<path d="M 42 60 L 58 60" stroke="#2C3E50" stroke-width="3" fill="none"/>`;
      } else if (pose === 'celebrating') {
        mouthExpression = `<path d="M 38 55 Q 50 72 62 55 Z" fill="#E74C3C"/>`;
      }

      return `
        <svg viewBox="0 0 100 100" width="100%" height="100%">
          <!-- Orejas -->
          <circle cx="22" cy="22" r="18" fill="#A67C52"/>
          <circle cx="22" cy="22" r="11" fill="#F3A6B2"/>
          <circle cx="78" cy="22" r="18" fill="#A67C52"/>
          <circle cx="78" cy="22" r="11" fill="#F3A6B2"/>
          <!-- Cabeza -->
          <circle cx="50" cy="50" r="32" fill="#C49A6C"/>
          <!-- Hocico -->
          <ellipse cx="50" cy="54" rx="16" ry="12" fill="#FFF0DB"/>
          <ellipse cx="50" cy="48" rx="5" ry="3" fill="#2C3E50"/>
          <!-- Ojos -->
          ${eyeExpression}
          <!-- Boca -->
          ${mouthExpression}
          <!-- Mejillas -->
          <circle cx="32" cy="52" r="5" fill="#F3A6B2" opacity="0.6"/>
          <circle cx="68" cy="52" r="5" fill="#F3A6B2" opacity="0.6"/>
        </svg>
      `;
    }

    /* ==========================================================================
       ESTADO GLOBAL DE LA APLICACIÓN Y RÚBRICA
       ========================================================================== */
    const state = {
      studentName: '',
      studentSection: '',
      currentMission: 0,
      startDate: new Date().toLocaleDateString('es-ES'),
      // Registro de errores por indicador
      errors: {
        ind1: 0, // Mouse parts
        ind2: 0, // Directions
        ind3: 0, // Simple vs Double Click
        ind4: 0, // Differentiate Click
        ind5: 0, // Drag and Drop
        ind6: 0, // Classification
        ind7: 0, // Scroll
        ind8: 0  // Order & Cleanliness
      }
    };

    /* ==========================================================================
       MOTOR DE NAVEGACIÓN Y FEEDBACK
       ========================================================================== */
    function showToast(message, pose = 'happy') {
      const toast = document.getElementById('feedbackToast');
      document.getElementById('toastMessage').innerText = message;
      document.getElementById('toastTitoIcon').innerHTML = getTitoSVG(pose);
      toast.classList.add('show');
      setTimeout(() => toast.classList.remove('show'), 3000);
    }

    function updateProgress(step) {
      document.querySelectorAll('.progress-step').forEach((el, idx) => {
        el.classList.remove('active');
        if (idx < step - 1) el.classList.add('completed');
        if (idx === step - 1) el.classList.add('active');
      });
    }

    /* ==========================================================================
       PANTALLAS Y MISIONES
       ========================================================================== */

    // SCREEN 0: REGISTRO
    function renderRegister() {
      const card = document.getElementById('mainCard');
      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('happy')}</div>
          <div class="mission-title-box">
            <h2>¡Bienvenido a la Aventura Digital!</h2>
            <p>Soy Tito, tu guía. Escribe tu nombre para comenzar la prueba.</p>
          </div>
        </div>
        <div class="stage-area">
          <div class="register-form">
            <input type="text" id="inputName" placeholder="Tu Nombre Completo..." required>
            <input type="text" id="inputSection" placeholder="Sección / Grado (ej. 1-A)..." required>
            <button class="btn-start" onclick="startAdventure()">¡Iniciar Misión! 🚀</button>
          </div>
        </div>
      `;
    }

    function startAdventure() {
      const name = document.getElementById('inputName').value.trim();
      const sec = document.getElementById('inputSection').value.trim();
      if (!name) return alert('Por favor escribe tu nombre.');
      
      state.studentName = name;
      state.studentSection = sec || '1° Grado';
      document.getElementById('studentDisplay').innerText = `Estudiante: ${state.studentName} (${state.studentSection})`;
      
      playSound('success');
      loadMission(1);
    }

    function loadMission(missionNum) {
      state.currentMission = missionNum;
      updateProgress(missionNum);
      const card = document.getElementById('mainCard');

      if (missionNum === 1) renderMission1(card);
      else if (missionNum === 2) renderMission2(card);
      else if (missionNum === 3) renderMission3(card);
      else if (missionNum === 4) renderMission4(card);
      else if (missionNum === 5) renderMission5(card);
      else if (missionNum === 6) renderMission6(card);
      else if (missionNum === 7) renderMission7(card);
      else if (missionNum === 8) renderFinalScreen(card);
    }

    // MISIÓN 1: PARTES DEL MOUSE
    function renderMission1(card) {
      let partsFound = 0;
      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('thinking')}</div>
          <div class="mission-title-box">
            <h2>Misión 1: Reconociendo el Mouse</h2>
            <p>Haz clic en cada parte del mouse que Tito te indique.</p>
          </div>
        </div>
        <div class="stage-area">
          <div class="mouse-illustration">
            <svg viewBox="0 0 200 260" width="100%" height="100%">
              <!-- Botón Izquierdo -->
              <path class="mouse-part" id="part-left" d="M 40 20 Q 100 20 100 80 L 40 80 Z" fill="#4A90E2" onclick="checkPart('left')"/>
              <!-- Botón Derecho -->
              <path class="mouse-part" id="part-right" d="M 100 20 Q 160 20 160 80 L 100 80 Z" fill="#357ABD" onclick="checkPart('right')"/>
              <!-- Rueda -->
              <rect class="mouse-part" id="part-wheel" x="92" y="45" width="16" height="30" rx="8" fill="#FF9F43" onclick="checkPart('wheel')"/>
              <!-- Cuerpo / Sensor -->
              <path class="mouse-part" id="part-sensor" d="M 40 80 L 160 80 Q 160 220 100 240 Q 40 220 40 80 Z" fill="#CBD5E1" onclick="checkPart('sensor')"/>
            </svg>
            <div class="part-label" style="top:10px; left:-20px;">Botón Izquierdo</div>
            <div class="part-label" style="top:10px; right:-20px;">Botón Derecho</div>
            <div class="part-label" style="bottom:30px; left:50px;">Cuerpo / Sensor</div>
          </div>
        </div>
      `;

      showToast("¡Toca el Botón Izquierdo del mouse!", "thinking");

      window.checkPart = function(part) {
        if (part === 'left' && partsFound === 0) {
          partsFound++;
          playSound('success');
          showToast("¡Muy bien! Ahora toca el Botón Derecho.", "happy");
        } else if (part === 'right' && partsFound === 1) {
          partsFound++;
          playSound('success');
          showToast("¡Excelente! Ahora toca la Rueda del centro.", "happy");
        } else if (part === 'wheel' && partsFound === 2) {
          partsFound++;
          playSound('success');
          showToast("¡Genial! Finalmente toca el Sensor o cuerpo.", "happy");
        } else if (part === 'sensor' && partsFound === 3) {
          playSound('fanfare');
          showToast("¡Misión 1 Completada!", "celebrating");
          setTimeout(() => loadMission(2), 2000);
        } else {
          state.errors.ind1++;
          playSound('pop');
          showToast("¡Inténtalo otra vez! Tito te acompaña.", "thinking");
        }
      };
    }

    // MISIÓN 2: DIRECCIONES
    function renderMission2(card) {
      let currentTarget = 'UP';
      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('happy')}</div>
          <div class="mission-title-box">
            <h2>Misión 2: El Tablero de Aventura</h2>
            <p>Mueve el puntero hacia la figura indicada por Tito.</p>
          </div>
        </div>
        <div class="stage-area">
          <div class="grid-directions">
            <div></div>
            <div class="dir-zone" onclick="checkDir('UP')">⭐<br>ARRIBA</div>
            <div></div>
            <div class="dir-zone" onclick="checkDir('LEFT')">🤖<br>IZQUIERDA</div>
            <div style="display:flex; align-items:center; justify-content:center;">🐭</div>
            <div class="dir-zone" onclick="checkDir('RIGHT')">🚀<br>DERECHA</div>
            <div></div>
            <div class="dir-zone" onclick="checkDir('DOWN')">⚽<br>ABAJO</div>
            <div></div>
          </div>
        </div>
      `;

      showToast("Mueve el mouse hacia ARRIBA (Estrella ⭐)", "happy");

      window.checkDir = function(dir) {
        if (dir === currentTarget) {
          playSound('success');
          if (currentTarget === 'UP') {
            currentTarget = 'DOWN';
            showToast("¡Muy bien! Ahora mueve hacia ABAJO (Pelota ⚽)", "happy");
          } else if (currentTarget === 'DOWN') {
            currentTarget = 'LEFT';
            showToast("¡Genial! Ahora ve hacia la IZQUIERDA (Robot 🤖)", "happy");
          } else if (currentTarget === 'LEFT') {
            currentTarget = 'RIGHT';
            showToast("¡Excelente! Ve hacia la DERECHA (Cohete 🚀)", "happy");
          } else if (currentTarget === 'RIGHT') {
            playSound('fanfare');
            showToast("¡Misión 2 Completada!", "celebrating");
            setTimeout(() => loadMission(3), 2000);
          }
        } else {
          state.errors.ind2++;
          playSound('pop');
          showToast("¡Casi lo logras! Busca la dirección correcta.", "thinking");
        }
      };
    }

    // MISIÓN 3: MUNDO DE OBJETOS (DRAG AND DROP TRASLADAR)
    function renderMission3(card) {
      let movedCount = 0;
      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('happy')}</div>
          <div class="mission-title-box">
            <h2>Misión 3: El Mundo de Objetos</h2>
            <p>Arrastra los 3 objetos mágicos hacia el cofre de Tito.</p>
          </div>
        </div>
        <div class="stage-area" style="flex-direction:column;">
          <div class="drag-items-container">
            <div class="draggable-obj" draggable="true" ondragstart="drag(event)" id="drag1">🎨</div>
            <div class="draggable-obj" draggable="true" ondragstart="drag(event)" id="drag2">🧸</div>
            <div class="draggable-obj" draggable="true" ondragstart="drag(event)" id="drag3">📚</div>
          </div>
          <div class="drop-box" ondragover="allowDrop(event)" ondrop="dropM3(event)" style="width:280px; min-height:120px;">
            <h4>🧰 Cofre Mágico</h4>
            <div id="chestContent" style="display:flex; gap:10px; font-size:2rem;"></div>
          </div>
        </div>
      `;

      window.allowDrop = function(ev) { ev.preventDefault(); };
      window.drag = function(ev) { ev.dataTransfer.setData("text", ev.target.id); };
      window.dropM3 = function(ev) {
        ev.preventDefault();
        const data = ev.dataTransfer.getData("text");
        const el = document.getElementById(data);
        if (el) {
          document.getElementById('chestContent').appendChild(el);
          playSound('pop');
          movedCount++;
          if (movedCount === 3) {
            playSound('fanfare');
            showToast("¡Misión 3 Completada! Arrastraste todos los objetos.", "celebrating");
            setTimeout(() => loadMission(4), 2000);
          }
        }
      };
    }

    // MISIÓN 4: RETO DEL CLIC Y DOBLE CLIC
    function renderMission4(card) {
      let simpleDone = false;
      let doubleDone = false;

      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('happy')}</div>
          <div class="mission-title-box">
            <h2>Misión 4: El Reto del Clic</h2>
            <p>Haz 1 clic en la estrella y Doble Clic en el cohete.</p>
          </div>
        </div>
        <div class="stage-area" style="gap:40px;">
          <div class="magic-box" id="boxSimple" onclick="doSimpleClick()">
            ⭐
            <div style="font-size:0.8rem; position:absolute; bottom:5px;">Clic Sencillo</div>
          </div>
          <div class="magic-box" id="boxDouble" ondblclick="doDoubleClick()">
            🚀
            <div style="font-size:0.8rem; position:absolute; bottom:5px;">Doble Clic</div>
          </div>
        </div>
      `;

      window.doSimpleClick = function() {
        if (!simpleDone) {
          simpleDone = true;
          playSound('success');
          document.getElementById('boxSimple').style.background = '#2ECC71';
          showToast("¡Excelente clic sencillo! Ahora haz DOBLE CLIC en el cohete.", "happy");
          checkM4Completion();
        }
      };

      window.doDoubleClick = function() {
        if (!doubleDone) {
          doubleDone = true;
          playSound('success');
          document.getElementById('boxDouble').style.background = '#2ECC71';
          showToast("¡Genial doble clic!", "happy");
          checkM4Completion();
        }
      };

      function checkM4Completion() {
        if (simpleDone && doubleDone) {
          playSound('fanfare');
          showToast("¡Misión 4 Completada!", "celebrating");
          setTimeout(() => loadMission(5), 2000);
        }
      }
    }

    // MISIÓN 5: CAJAS MÁGICAS (DIFERENCIAR CLIC Y DOBLE CLIC)
    function renderMission5(card) {
      let openedBoxes = 0;
      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('surprised')}</div>
          <div class="mission-title-box">
            <h2>Misión 5: Las Cajas Mágicas</h2>
            <p>Abre las cajas secretas haciendo DOBLE CLIC en cada una.</p>
          </div>
        </div>
        <div class="stage-area">
          <div class="magic-boxes-grid">
            <div class="magic-box" onclick="failSingleClick()" ondblclick="openMagicBox(this, '🎁')">📦</div>
            <div class="magic-box" onclick="failSingleClick()" ondblclick="openMagicBox(this, '👑')">📦</div>
            <div class="magic-box" onclick="failSingleClick()" ondblclick="openMagicBox(this, '🦄')">📦</div>
          </div>
        </div>
      `;

      window.failSingleClick = function() {
        // Un clic sencillo no las abre
        state.errors.ind4++;
        showToast("¡Recuerda hacer DOBLE CLIC (dos clics rápidos)!", "thinking");
      };

      window.openMagicBox = function(element, surprise) {
        if (!element.classList.contains('opened')) {
          element.classList.add('opened');
          element.innerText = surprise;
          playSound('pop');
          openedBoxes++;
          if (openedBoxes === 3) {
            playSound('fanfare');
            showToast("¡Abriste todas las Cajas Mágicas!", "celebrating");
            setTimeout(() => loadMission(6), 2000);
          }
        }
      };
    }

    // MISIÓN 6: ALMACÉN DE TITO (CLASIFICACIÓN)
    function renderMission6(card) {
      let sortedCount = 0;
      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('happy')}</div>
          <div class="mission-title-box">
            <h2>Misión 6: El Almacén de Tito</h2>
            <p>Clasifica los objetos arrastrándolos a su zona correcta.</p>
          </div>
        </div>
        <div class="stage-area" style="flex-direction:column; gap:20px;">
          <div class="drag-items-container">
            <div class="draggable-obj" draggable="true" ondragstart="dragM6(event, 'juguete')" id="item1">⚽</div>
            <div class="draggable-obj" draggable="true" ondragstart="dragM6(event, 'util')" id="item2">✏️</div>
            <div class="draggable-obj" draggable="true" ondragstart="dragM6(event, 'animal')" id="item3">🐱</div>
          </div>
          <div class="drop-zones-container">
            <div class="drop-box" ondragover="allowDrop(event)" ondrop="dropM6(event, 'juguete')">
              <h4>⚽ JUGUETES</h4>
              <div class="box-target" style="display:flex; gap:5px;"></div>
            </div>
            <div class="drop-box" ondragover="allowDrop(event)" ondrop="dropM6(event, 'util')">
              <h4>✏️ ÚTILES</h4>
              <div class="box-target" style="display:flex; gap:5px;"></div>
            </div>
            <div class="drop-box" ondragover="allowDrop(event)" ondrop="dropM6(event, 'animal')">
              <h4>🐱 ANIMALES</h4>
              <div class="box-target" style="display:flex; gap:5px;"></div>
            </div>
          </div>
        </div>
      `;

      window.dragM6 = function(ev, category) {
        ev.dataTransfer.setData("text", ev.target.id);
        ev.dataTransfer.setData("category", category);
      };

      window.dropM6 = function(ev, targetCategory) {
        ev.preventDefault();
        const itemId = ev.dataTransfer.getData("text");
        const itemCategory = ev.dataTransfer.getData("category");
        const itemEl = document.getElementById(itemId);

        if (itemCategory === targetCategory) {
          playSound('success');
          ev.currentTarget.querySelector('.box-target').appendChild(itemEl);
          sortedCount++;
          showToast("¡Correcto! Objeto clasificado.", "happy");
          if (sortedCount === 3) {
            playSound('fanfare');
            showToast("¡Misión 6 Completada! Todo está ordenado.", "celebrating");
            setTimeout(() => loadMission(7), 2000);
          }
        } else {
          state.errors.ind6++;
          playSound('pop');
          showToast("¡Inténtalo otra vez! Busca el lugar correcto.", "thinking");
        }
      };
    }

    // MISIÓN 7: EXPLORACIÓN VERTICAL (RUEDA / SCROLL)
    function renderMission7(card) {
      let itemsFound = 0;
      card.innerHTML = `
        <div class="mission-header">
          <div class="tito-avatar">${getTitoSVG('thinking')}</div>
          <div class="mission-title-box">
            <h2>Misión 7: Exploración Vertical</h2>
            <p>Usa la rueda del mouse para desplazarte hacia abajo y encontrar los 2 tesoros.</p>
          </div>
        </div>
        <div class="stage-area">
          <div class="scroll-stage">
            <div class="scroll-content">
              <p>👇 Usa la rueda del mouse para bajar...</p>
              <div class="scroll-item" onclick="collectScrollItem(this)">💎 ¡Primer Tesoro! (Haz clic)</div>
              <p>👇 Sigue desplazándote hacia abajo...</p>
              <div class="scroll-item" onclick="collectScrollItem(this)">🏆 ¡Segundo Tesoro! (Haz clic)</div>
            </div>
          </div>
        </div>
      `;

      window.collectScrollItem = function(el) {
        if (!el.dataset.collected) {
          el.dataset.collected = "true";
          el.style.background = "#2ECC71";
          el.style.color = "white";
          playSound('success');
          itemsFound++;
          if (itemsFound === 2) {
            playSound('fanfare');
            showToast("¡Has completado todas las exploraciones!", "celebrating");
            setTimeout(() => loadMission(8), 2000);
          }
        }
      };
    }

    /* ==========================================================================
       PANTALLA FINAL Y EVALUACIÓN SEGÚN RÚBRICA
       ========================================================================== */
    function renderFinalScreen(card) {
      playSound('fanfare');

      // Función para calcular puntos de cada indicador (3, 2, 1 u 0 pts)
      const getScore = (errorCount) => {
        if (errorCount <= 1) return 3;
        if (errorCount <= 3) return 2;
        if (errorCount > 3) return 1;
        return 0;
      };

      const score1 = getScore(state.errors.ind1);
      const score2 = getScore(state.errors.ind2);
      const score3 = getScore(state.errors.ind3);
      const score4 = getScore(state.errors.ind4);
      const score5 = getScore(state.errors.ind5);
      const score6 = getScore(state.errors.ind6);
      const score7 = getScore(state.errors.ind7);
      const score8 = 3; // Presentación limpia y completa

      const totalScore = score1 + score2 + score3 + score4 + score5 + score6 + score7 + score8;
      const percentage = Math.round((totalScore / 24) * 100);

      card.innerHTML = `
        <div class="final-container">
          <div class="certificate-header">
            <div style="width:80px; height:80px; margin:0 auto;">${getTitoSVG('celebrating')}</div>
            <h1 style="color:var(--secondary); margin:5px 0;">¡AVENTURA COMPLETADA!</h1>
            <h3 style="margin:0;">Certificado de Competencia Digital Inicial</h3>
            <p style="margin:10px 0 0 0;"><strong>Estudiante:</strong> ${state.studentName} | <strong>Sección:</strong> ${state.studentSection} | <strong>Fecha:</strong> ${state.startDate}</p>
          </div>

          <h3 style="margin:10px 0 0 0; color:var(--primary);">📋 Reporte Oficial de Evaluación Pedagógica (Rúbrica)</h3>

          <table class="rubric-table">
            <thead>
              <tr>
                <th>Indicador Evaluado</th>
                <th>Muy bueno (3 pts)</th>
                <th>Bueno (2 pts)</th>
                <th>Por mejorar (1 pt)</th>
                <th>Omisión (0 pts)</th>
                <th>Puntos</th>
              </tr>
            </thead>
            <tbody>
              <tr class="selected-level-${score1}">
                <td><strong>1. Partes del mouse</strong></td>
                <td class="lvl-3">Reconoce todas las partes.</td>
                <td class="lvl-2">Reconoce 3 partes.</td>
                <td class="lvl-1">Reconoce 2 partes.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score1} / 3</td>
              </tr>
              <tr class="selected-level-${score2}">
                <td><strong>2. Control en 4 direcciones</strong></td>
                <td class="lvl-3">Manipula en las 4 direcciones.</td>
                <td class="lvl-2">Manipula en 3 direcciones.</td>
                <td class="lvl-1">Manipula en 2 direcciones.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score2} / 3</td>
              </tr>
              <tr class="selected-level-${score3}">
                <td><strong>3. Clic izquierdo y doble clic</strong></td>
                <td class="lvl-3">Ejecuta acciones sin errores.</td>
                <td class="lvl-2">Ejecuta 1 acción correctamente.</td>
                <td class="lvl-1">Errores frecuentes.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score3} / 3</td>
              </tr>
              <tr class="selected-level-${score4}">
                <td><strong>4. Diferenciar clic y doble clic</strong></td>
                <td class="lvl-3">Diferencia claramente.</td>
                <td class="lvl-2">Algunos errores.</td>
                <td class="lvl-1">Muchos errores.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score4} / 3</td>
              </tr>
              <tr class="selected-level-${score5}">
                <td><strong>5. Arrastrar y soltar objetos</strong></td>
                <td class="lvl-3">Traslada correctamente todos.</td>
                <td class="lvl-2">Traslada algunos.</td>
                <td class="lvl-1">Errores frecuentes.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score5} / 3</td>
              </tr>
              <tr class="selected-level-${score6}">
                <td><strong>6. Clasificar objetos digitales</strong></td>
                <td class="lvl-3">Clasifica todos correctamente.</td>
                <td class="lvl-2">Clasifica algunos.</td>
                <td class="lvl-1">Errores frecuentes.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score6} / 3</td>
              </tr>
              <tr class="selected-level-${score7}">
                <td><strong>7. Uso de la rueda (Scroll)</strong></td>
                <td class="lvl-3">Utiliza correctamente.</td>
                <td class="lvl-2">Utiliza parcialmente.</td>
                <td class="lvl-1">Errores frecuentes.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score7} / 3</td>
              </tr>
              <tr class="selected-level-${score8}">
                <td><strong>8. Trabajo limpio y completo</strong></td>
                <td class="lvl-3">Presenta trabajo limpio y completo.</td>
                <td class="lvl-2">Con detalles.</td>
                <td class="lvl-1">Incompleto.</td>
                <td class="lvl-0">Omitir.</td>
                <td class="score-cell">${score8} / 3</td>
              </tr>
            </tbody>
            <tfoot>
              <tr style="background:#F8FAFC; font-size:1rem;">
                <th colspan="5" style="text-align:right;">PUNTAJE TOTAL OBTENIDO:</th>
                <th style="text-align:center; color:var(--primary);">${totalScore} / 24 (${percentage}%)</th>
              </tr>
            </tfoot>
          </table>

          <button class="btn-print" onclick="window.print()">🖨️ Imprimir Certificado e Informe para la Familia</button>
        </div>
      `;
    }

    // INICIALIZACIÓN
    renderRegister();
  </script>
</body>
</html>
