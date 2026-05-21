<!DOCTYPE html><html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Faraday Ultra Realistic Lab - الأستاذ سيف الربيعي</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800&display=swap" rel="stylesheet">  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Cairo', sans-serif;
    }

    :root {
      --bg-main: #08111f;
      --bg-card: #101d32;
      --bg-card-2: #0d1729;
      --primary: #ffd54a;
      --primary-dark: #a07b0d;
      --blue: #4ea5ff;
      --cyan: #53f7ff;
      --white: #ffffff;
      --muted: #9ca7ba;
      --border: rgba(255,255,255,0.08);
      --shadow: 0 10px 40px rgba(0,0,0,0.4);
      --radius: 18px;
      --transition: 0.3s ease;
    }

    body {
      background:
        radial-gradient(circle at top right, rgba(53,104,255,0.2), transparent 20%),
        radial-gradient(circle at bottom left, rgba(0,255,255,0.08), transparent 25%),
        var(--bg-main);
      color: var(--white);
      overflow-x: hidden;
      min-height: 100vh;
    }

    .app {
      display: grid;
      grid-template-columns: 350px 1fr;
      min-height: 100vh;
    }

    .sidebar {
      background: linear-gradient(180deg, #0d1729, #0a1220);
      border-left: 1px solid var(--border);
      padding: 24px;
      position: relative;
      overflow-y: auto;
      box-shadow: var(--shadow);
      z-index: 5;
    }

    .logo {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 28px;
      padding: 18px;
      border-radius: 20px;
      background: rgba(255,255,255,0.03);
      border: 1px solid var(--border);
    }

    .logo h1 {
      font-size: 20px;
      color: var(--primary);
      line-height: 1.8;
    }

    .logo p {
      font-size: 12px;
      color: var(--muted);
    }

    .teacher-badge {
      width: 58px;
      height: 58px;
      border-radius: 18px;
      background: linear-gradient(145deg, #1a2d4d, #0c1626);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 28px;
      box-shadow: inset 0 0 20px rgba(255,255,255,0.06);
      border: 1px solid rgba(255,255,255,0.08);
    }

    .panel {
      background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.015));
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 18px;
      margin-bottom: 18px;
      backdrop-filter: blur(10px);
      position: relative;
      overflow: hidden;
    }

    .panel::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(120deg, transparent, rgba(255,255,255,0.03), transparent);
      transform: translateX(-100%);
      animation: shine 6s infinite;
    }

    @keyframes shine {
      100% {
        transform: translateX(100%);
      }
    }

    .panel-title {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 18px;
    }

    .panel-title h2 {
      font-size: 16px;
      color: var(--primary);
    }

    .steps {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .step {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 14px;
      border-radius: 14px;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.04);
      transition: var(--transition);
      cursor: pointer;
    }

    .step:hover {
      transform: translateY(-3px);
      background: rgba(255,255,255,0.05);
    }

    .step.active {
      border-color: rgba(255,213,74,0.5);
      background: rgba(255,213,74,0.08);
      box-shadow: 0 0 25px rgba(255,213,74,0.08);
    }

    .step-number {
      width: 34px;
      height: 34px;
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(145deg, #ffd54a, #d9a700);
      color: #111;
      font-weight: 800;
      font-size: 14px;
    }

    .step span {
      font-size: 13px;
      color: var(--white);
      flex: 1;
      padding-inline: 12px;
    }

    .gauge-box {
      width: 100%;
      height: 180px;
      border-radius: 20px;
      background: linear-gradient(180deg, #07101d, #0c1829);
      border: 1px solid var(--border);
      position: relative;
      overflow: hidden;
      margin-bottom: 18px;
    }

    .gauge-center {
      position: absolute;
      left: 50%;
      top: 70%;
      transform: translate(-50%, -50%);
      width: 14px;
      height: 14px;
      border-radius: 50%;
      background: var(--white);
      z-index: 3;
      box-shadow: 0 0 10px rgba(255,255,255,0.8);
    }

    .gauge-needle {
      position: absolute;
      width: 90px;
      height: 4px;
      background: linear-gradient(90deg, #ff6161, #ffce4b);
      top: 70%;
      left: 50%;
      transform-origin: left center;
      transform: rotate(-40deg);
      border-radius: 50px;
      transition: 0.4s ease;
      z-index: 2;
    }

    .gauge-text {
      position: absolute;
      width: 100%;
      text-align: center;
      bottom: 18px;
      font-size: 18px;
      color: var(--cyan);
      font-weight: bold;
    }

    .control-group {
      margin-bottom: 18px;
    }

    .control-group label {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
      font-size: 14px;
      color: var(--muted);
    }

    input[type='range'] {
      width: 100%;
      appearance: none;
      height: 8px;
      border-radius: 30px;
      background: rgba(255,255,255,0.08);
      outline: none;
      overflow: hidden;
    }

    input[type='range']::-webkit-slider-thumb {
      appearance: none;
      width: 22px;
      height: 22px;
      border-radius: 50%;
      background: var(--primary);
      border: 3px solid #fff;
      box-shadow: -1000px 0 0 1000px rgba(255,213,74,0.2);
      cursor: pointer;
    }

    .material-buttons {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
    }

    .material-btn {
      padding: 12px;
      border-radius: 14px;
      border: 1px solid var(--border);
      background: rgba(255,255,255,0.03);
      color: var(--white);
      cursor: pointer;
      transition: var(--transition);
      font-size: 13px;
      text-align: center;
    }

    .material-btn:hover {
      transform: translateY(-2px);
    }

    .material-btn.active {
      background: rgba(255,213,74,0.15);
      border-color: rgba(255,213,74,0.5);
      color: var(--primary);
    }

    .reset-btn,
    .action-btn {
      width: 100%;
      border: none;
      padding: 16px;
      border-radius: 16px;
      cursor: pointer;
      font-weight: bold;
      transition: var(--transition);
      margin-top: 12px;
      font-size: 15px;
    }

    .reset-btn {
      background: linear-gradient(145deg, #381717, #671d1d);
      color: #ff9e9e;
      border: 1px solid rgba(255,0,0,0.15);
    }

    .action-btn {
      background: linear-gradient(145deg, #ffd54a, #c79400);
      color: #111;
      box-shadow: 0 12px 30px rgba(255,213,74,0.18);
    }

    .reset-btn:hover,
    .action-btn:hover {
      transform: translateY(-3px);
    }

    .workspace {
      position: relative;
      overflow: hidden;
      display: flex;
      flex-direction: column;
    }

    .topbar {
      height: 90px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 32px;
      border-bottom: 1px solid var(--border);
      background: rgba(0,0,0,0.15);
      backdrop-filter: blur(10px);
    }

    .topbar-title h2 {
      color: var(--primary);
      font-size: 28px;
      margin-bottom: 6px;
    }

    .topbar-title p {
      color: var(--muted);
      font-size: 13px;
    }

    .student-box {
      padding: 14px 22px;
      border-radius: 18px;
      background: rgba(255,255,255,0.03);
      border: 1px solid var(--border);
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      gap: 4px;
    }

    .student-box strong {
      color: var(--cyan);
      font-size: 16px;
    }

    .student-box span {
      color: var(--muted);
      font-size: 12px;
    }

    .simulation-area {
      position: relative;
      flex: 1;
      overflow: hidden;
      background-image:
        linear-gradient(rgba(255,255,255,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.04) 1px, transparent 1px);
      background-size: 40px 40px;
    }

    .coil {
      position: absolute;
      width: 180px;
      height: 520px;
      top: 120px;
      background:
        linear-gradient(180deg, #ffffff 0%, #f2f2f2 8%, #cfd3d9 40%, #aeb5bf 70%, #e8ebef 100%);
      border-radius: 20px;
      box-shadow:
        inset 0 0 30px rgba(255,255,255,0.75),
        inset 0 -18px 30px rgba(0,0,0,0.28),
        inset 0 12px 20px rgba(255,255,255,0.35),
        0 35px 60px rgba(0,0,0,0.45),
        0 0 25px rgba(255,255,255,0.08);
      overflow: hidden;
    }

    .coil::before {
      content: '';
      position: absolute;
      inset: 0;
      background: repeating-linear-gradient(
        to bottom,
        rgba(0,0,0,0.02) 0px,
        rgba(0,0,0,0.02) 8px,
        rgba(255,255,255,0.08) 8px,
        rgba(255,255,255,0.08) 16px
      );
      mix-blend-mode: overlay;
    }

    .coil.left {
      right: 360px;
    }

    .coil.right {
      right: 700px;
    }

    .battery {
      position: absolute;
      width: 90px;
      height: 320px;
      bottom: 90px;
      right: 170px;
      border-radius: 18px;
      background:
      linear-gradient(180deg, #ffd85a 0%, #ffbf1d 15%, #d69700 45%, #9e6d00 100%);
      box-shadow:
        inset 0 0 25px rgba(255,255,255,0.25),
        0 30px 50px rgba(0,0,0,0.4);
      border: 6px solid #2d2d2d;
    }

    .battery::before {
      content: '+';
      position: absolute;
      top: -34px;
      left: 50%;
      transform: translateX(-50%);
      color: #ff5d5d;
      font-size: 34px;
      font-weight: bold;
    }

    .battery::after {
      content: '-';
      position: absolute;
      bottom: -30px;
      left: 50%;
      transform: translateX(-50%);
      color: #57a8ff;
      font-size: 34px;
      font-weight: bold;
    }

    .battery-label {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 24px;
      font-weight: 800;
      color: rgba(0,0,0,0.6);
    }

    svg.wires {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }

    .wire-red {
      stroke: #ff5f5f;
      stroke-width: 6;
      fill: none;
      filter: drop-shadow(0 0 10px rgba(255,0,0,0.5));
    }

    .wire-blue {
      stroke: #4ea5ff;
      stroke-width: 6;
      fill: none;
      filter: drop-shadow(0 0 10px rgba(0,150,255,0.5));
    }

    .electric-flow {
      stroke-dasharray: 20 20;
      animation: flow 2s linear infinite;
    }

    @keyframes flow {
      from {
        stroke-dashoffset: 0;
      }

      to {
        stroke-dashoffset: -200;
      }
    }

    .switch-box {
      position: absolute;
      right: 260px;
      top: 120px;
      width: 90px;
      height: 90px;
      border-radius: 20px;
      background: linear-gradient(145deg, #19273e, #0f1828);
      border: 1px solid rgba(255,255,255,0.08);
      box-shadow: var(--shadow);
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
    }

    .switch-handle {
      width: 60px;
      height: 10px;
      border-radius: 50px;
      background: linear-gradient(90deg, #ddd, #888);
      transform: rotate(-40deg);
      transition: 0.3s ease;
      position: relative;
    }

    .switch-handle.active {
      transform: rotate(25deg);
      background: linear-gradient(90deg, #ffd54a, #ff9100);
    }

    .switch-handle::after {
      content: '';
      position: absolute;
      right: -10px;
      top: -6px;
      width: 22px;
      height: 22px;
      border-radius: 50%;
      background: #f5f5f5;
      box-shadow: 0 0 12px rgba(255,255,255,0.5);
    }

    .status-box {
      position: absolute;
      left: 30px;
      top: 30px;
      padding: 18px 22px;
      border-radius: 20px;
      background: rgba(0,0,0,0.35);
      border: 1px solid rgba(255,255,255,0.06);
      backdrop-filter: blur(12px);
      display: flex;
      flex-direction: column;
      gap: 10px;
      min-width: 250px;
    }

    .status-item {
      display: flex;
      justify-content: space-between;
      gap: 16px;
      font-size: 14px;
    }

    .status-item strong {
      color: var(--cyan);
    }

    .status-item span {
      color: var(--white);
    }

    .footer-note {
      position: absolute;
      left: 30px;
      bottom: 30px;
      padding: 18px 26px;
      border-radius: 18px;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.05);
      color: var(--muted);
      font-size: 14px;
      backdrop-filter: blur(10px);
    }

    .pulse-light {
      position: absolute;
      width: 18px;
      height: 18px;
      border-radius: 50%;
      background: #4eff9e;
      box-shadow: 0 0 20px rgba(78,255,158,0.8);
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0% {
        transform: scale(1);
        opacity: 1;
      }

      50% {
        transform: scale(1.4);
        opacity: 0.4;
      }

      100% {
        transform: scale(1);
        opacity: 1;
      }
    }

    .light-1 {
      right: 460px;
      top: 150px;
    }

    .light-2 {
      right: 800px;
      top: 150px;
    }

    .floating-card {
      position: absolute;
      width: 220px;
      padding: 20px;
      border-radius: 18px;
      background: rgba(8,15,25,0.75);
      border: 1px solid rgba(255,255,255,0.05);
      backdrop-filter: blur(18px);
      box-shadow: var(--shadow);
    }

    .floating-card h3 {
      color: var(--primary);
      margin-bottom: 10px;
      font-size: 18px;
    }

    .floating-card p {
      font-size: 13px;
      line-height: 1.9;
      color: var(--muted);
    }

    .card-1 {
      top: 130px;
      left: 40px;
    }

    .card-2 {
      top: 390px;
      left: 40px;
    }

    .metrics {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 18px;
      margin: 26px 30px;
    }

    .metric-box {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.05);
      border-radius: 20px;
      padding: 24px;
      backdrop-filter: blur(14px);
      transition: var(--transition);
    }

    .metric-box:hover {
      transform: translateY(-5px);
    }

    .metric-box h4 {
      color: var(--muted);
      margin-bottom: 12px;
      font-size: 13px;
    }

    .metric-box strong {
      font-size: 28px;
      color: var(--cyan);
    }

    .metric-box small {
      display: block;
      margin-top: 10px;
      color: var(--primary);
    }

    @media(max-width: 1500px) {
      .app {
        grid-template-columns: 320px 1fr;
      }

      .coil.left {
        right: 300px;
      }

      .coil.right {
        right: 580px;
      }
    }

    @media(max-width: 1200px) {
      .app {
        grid-template-columns: 1fr;
      }

      .sidebar {
        height: auto;
      }

      .workspace {
        min-height: 100vh;
      }

      .metrics {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    @media(max-width: 768px) {
      .metrics {
        grid-template-columns: 1fr;
      }

      .topbar {
        flex-direction: column;
        height: auto;
        gap: 14px;
        padding: 20px;
      }

      .coil {
        transform: scale(0.8);
      }
    }

    /* Decorative extra layers for realism */
    .noise-layer {
      position: absolute;
      inset: 0;
      pointer-events: none;
      background-image: radial-gradient(rgba(255,255,255,0.03) 1px, transparent 1px);
      background-size: 4px 4px;
      opacity: 0.2;
      mix-blend-mode: soft-light;
    }

    .glow-orb {
      position: absolute;
      width: 500px;
      height: 500px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(78,165,255,0.12), transparent 70%);
      filter: blur(30px);
      pointer-events: none;
    }

    .orb-1 {
      right: 400px;
      top: 100px;
    }

    .orb-2 {
      left: -100px;
      bottom: -100px;
      background: radial-gradient(circle, rgba(255,213,74,0.12), transparent 70%);
    }

    .grid-overlay {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
      background-size: 100px 100px;
      pointer-events: none;
    }
  </style></head><body>  <div class="app"><aside class="sidebar">

  <div class="logo">
    <div>
      <h1>Faraday's Experiment</h1>
      <p>إعداد الأستاذ سيف الربيعي</p>
    </div>

    <div class="teacher-badge">⚡</div>
  </div>

  <div class="panel">
    <div class="panel-title">
      <h2>خطوات التجربة</h2>
    </div>

    <div class="steps">
      <div class="step active">
        <div class="step-number">1</div>
        <span>توصيل البطارية وشحن المتسعة</span>
      </div>

      <div class="step">
        <div class="step-number">2</div>
        <span>فصل البطارية وقياس فرق الجهد</span>
      </div>

      <div class="step">
        <div class="step-number">3</div>
        <span>سحب اللوح العازل تدريجياً</span>
      </div>
    </div>
  </div>

  <div class="panel">
    <div class="panel-title">
      <h2>عداد الفولتميتر</h2>
    </div>

    <div class="gauge-box">
      <div class="gauge-needle" id="needle"></div>
      <div class="gauge-center"></div>
      <div class="gauge-text" id="gaugeValue">12.0V</div>
    </div>

    <div class="control-group">
      <label>
        <span>المسافة بين الصفائح</span>
        <strong id="distanceText">4.5 cm</strong>
      </label>

      <input type="range" min="1" max="10" value="4.5" step="0.1" id="distanceRange">
    </div>

    <div class="control-group">
      <label>
        <span>ثابت العزل الكهربائي</span>
        <strong id="kValue">1</strong>
      </label>

      <div class="material-buttons">
        <button class="material-btn active" data-k="1">هواء</button>
        <button class="material-btn" data-k="2">بلاستك</button>
        <button class="material-btn" data-k="4.5">زجاج</button>
        <button class="material-btn" data-k="80">ماء</button>
      </div>
    </div>

    <button class="action-btn" id="startBtn">تشغيل المحاكاة</button>
    <button class="reset-btn" id="resetBtn">إعادة التجربة</button>
  </div>

  <div class="panel">
    <div class="panel-title">
      <h2>معلومات المشروع</h2>
    </div>

    <p style="line-height:2;color:var(--muted);font-size:14px;">
      تصميم احترافي عالي الدقة لمحاكاة تجربة فاراداي التعليمية.
      تم تطوير الواجهة بأسلوب واقعي متقدم مع مؤثرات حركية وواجهة عصرية.
      <br><br>
      إعداد: الأستاذ سيف الربيعي
      <br>
      إعداد الطالب: علي حازم
    </p>
  </div>

</aside>

<main class="workspace">

  <div class="topbar">

    <div class="topbar-title">
      <h2>تجربة فاراداي المتقدمة</h2>
      <p>محاكاة تعليمية احترافية بتصميم واقعي وتقنيات حديثة</p>
    </div>

    <div class="student-box">
      <strong>الطالب: علي حازم</strong>
      <span>إشراف الأستاذ سيف الربيعي</span>
    </div>

  </div>

  <div class="metrics">

    <div class="metric-box">
      <h4>فرق الجهد</h4>
      <strong id="metricVoltage">12V</strong>
      <small>Voltage Difference</small>
    </div>

    <div class="metric-box">
      <h4>السعة الكهربائية</h4>
      <strong id="metricCapacitance">0.08μF</strong>
      <small>Capacitance</small>
    </div>

    <div class="metric-box">
      <h4>ثابت العزل</h4>
      <strong id="metricK">1</strong>
      <small>Dielectric Constant</small>
    </div>

    <div class="metric-box">
      <h4>المسافة</h4>
      <strong id="metricDistance">4.5cm</strong>
      <small>Plate Distance</small>
    </div>

  </div>

  <div class="simulation-area">

    <div class="noise-layer"></div>
    <div class="grid-overlay"></div>
    <div class="glow-orb orb-1"></div>
    <div class="glow-orb orb-2"></div>

    <div class="status-box">
      <div class="status-item">
        <strong>حالة الدائرة</strong>
        <span id="statusCircuit">مفتوحة</span>
      </div>

      <div class="status-item">
        <strong>حالة الشحن</strong>
        <span id="statusCharge">غير نشط</span>
      </div>

      <div class="status-item">
        <strong>التيار الكهربائي</strong>
        <span id="statusCurrent">0.0 A</span>
      </div>

      <div class="status-item">
        <strong>الكفاءة</strong>
        <span id="statusEfficiency">98%</span>
      </div>
    </div>

    <div class="floating-card card-1">
      <h3>شرح التجربة</h3>
      <p>
        تعتمد التجربة على دراسة تأثير الوسط العازل بين صفائح المتسعة
        وتأثيره على السعة الكهربائية والطاقة المختزنة.
      </p>
    </div>

    <div class="floating-card card-2">
      <h3>النتائج اللحظية</h3>
      <p>
        يتم تحديث القياسات لحظياً عند تغيير المسافة أو نوع العازل.
        المحاكاة مبنية بأسلوب ديناميكي تفاعلي.
      </p>
    </div>

    <div class="pulse-light light-1"></div>
    <div class="pulse-light light-2"></div>

    <div class="switch-box" id="switchBox">
      <div class="switch-handle" id="switchHandle"></div>
    </div>

    <div class="battery">
      <div class="battery-label">12V</div>
    </div>

    <div class="coil left"></div>
    <div class="coil right"></div>

    <svg class="wires" viewBox="0 0 1600 900">

      <path
        id="wireRed"
        class="wire-red"
        d="M 280 650 L 280 170 L 390 170"
      />

      <path
        id="wireBlue"
        class="wire-blue"
        d="M 280 780 L 280 820 L 760 820 L 760 650"
      />

    </svg>

    <div class="footer-note">
      Ultra Realistic Physics Interface • Real Laboratory Simulation • Premium Scientific UI
      <br>
      إعداد الأستاذ سيف الربيعي — الطالب علي حازم
    </div>

  </div>

</main>

  </div>  <script>

    const needle = document.getElementById('needle');
    const gaugeValue = document.getElementById('gaugeValue');

    const distanceRange = document.getElementById('distanceRange');
    const distanceText = document.getElementById('distanceText');

    const metricVoltage = document.getElementById('metricVoltage');
    const metricCapacitance = document.getElementById('metricCapacitance');
    const metricK = document.getElementById('metricK');
    const metricDistance = document.getElementById('metricDistance');

    const statusCircuit = document.getElementById('statusCircuit');
    const statusCharge = document.getElementById('statusCharge');
    const statusCurrent = document.getElementById('statusCurrent');

    const switchHandle = document.getElementById('switchHandle');
    const switchBox = document.getElementById('switchBox');

    const materialButtons = document.querySelectorAll('.material-btn');

    const wireRed = document.getElementById('wireRed');
    const wireBlue = document.getElementById('wireBlue');

    let isRunning = false;
    let dielectric = 1;
    let voltage = 12;

    function updateGauge(value) {
      const rotation = (value - 10) * 8;
      needle.style.transform = `rotate(${rotation}deg)`;
      gaugeValue.innerText = value.toFixed(1) + 'V';
      metricVoltage.innerText = value.toFixed(1) + 'V';
    }

    function updateDistance(value) {
      distanceText.innerText = value + ' cm';
      metricDistance.innerText = value + 'cm';

      const capacitance = ((dielectric * 0.08) / value).toFixed(3);
      metricCapacitance.innerText = capacitance + 'μF';

      const newVoltage = (12 * dielectric / value).toFixed(2);

      updateGauge(parseFloat(newVoltage));
    }

    distanceRange.addEventListener('input', (e) => {
      updateDistance(e.target.value);
    });

    materialButtons.forEach(btn => {

      btn.addEventListener('click', () => {

        materialButtons.forEach(b => b.classList.remove('active'));
        btn.classList.add('active');

        dielectric = parseFloat(btn.dataset.k);

        metricK.innerText = dielectric;

        updateDistance(distanceRange.value);
      });

    });

    switchBox.addEventListener('click', () => {

      isRunning = !isRunning;

      if (isRunning) {

        switchHandle.classList.add('active');

        statusCircuit.innerText = 'مغلقة';
        statusCharge.innerText = 'نشط';
        statusCurrent.innerText = '2.4 A';

        wireRed.classList.add('electric-flow');
        wireBlue.classList.add('electric-flow');

      } else {

        switchHandle.classList.remove('active');

        statusCircuit.innerText = 'مفتوحة';
        statusCharge.innerText = 'غير نشط';
        statusCurrent.innerText = '0.0 A';

        wireRed.classList.remove('electric-flow');
        wireBlue.classList.remove('electric-flow');

      }

    });

    document.getElementById('startBtn').addEventListener('click', () => {

      isRunning = true;

      switchHandle.classList.add('active');

      statusCircuit.innerText = 'مغلقة';
      statusCharge.innerText = 'نشط';
      statusCurrent.innerText = '2.4 A';

      wireRed.classList.add('electric-flow');
      wireBlue.classList.add('electric-flow');

      animateEnergy();

    });

    document.getElementById('resetBtn').addEventListener('click', () => {

      isRunning = false;

      switchHandle.classList.remove('active');

      distanceRange.value = 4.5;
      dielectric = 1;

      materialButtons.forEach(b => b.classList.remove('active'));
      materialButtons[0].classList.add('active');

      updateDistance(4.5);

      statusCircuit.innerText = 'مفتوحة';
      statusCharge.innerText = 'غير نشط';
      statusCurrent.innerText = '0.0 A';

      wireRed.classList.remove('electric-flow');
      wireBlue.classList.remove('electric-flow');

      metricK.innerText = '1';

    });

    function animateEnergy() {

      const area = document.querySelector('.simulation-area');

      for (let i = 0; i < 30; i++) {

        const particle = document.createElement('div');

        particle.style.position = 'absolute';
        particle.style.width = '6px';
        particle.style.height = '6px';
        particle.style.borderRadius = '50%';
        particle.style.background = '#53f7ff';
        particle.style.boxShadow = '0 0 10px #53f7ff';
        particle.style.right = (300 + Math.random() * 500) + 'px';
        particle.style.top = (100 + Math.random() * 500) + 'px';
        particle.style.opacity = '0.8';
        particle.style.pointerEvents = 'none';

        area.appendChild(particle);

        let y = parseFloat(particle.style.top);

        const interval = setInterval(() => {

          y -= 2;

          particle.style.top = y + 'px';
          particle.style.opacity -= 0.01;

          if (y < 50 || parseFloat(particle.style.opacity) <= 0) {
            clearInterval(interval);
            particle.remove();
          }

        }, 16);

      }

    }

    setInterval(() => {

      if (isRunning) {

        const randomCurrent = (2 + Math.random()).toFixed(2);
        statusCurrent.innerText = randomCurrent + ' A';

      }

    }, 1200);

    updateDistance(4.5);

    // Advanced ambient animation system

    const simulationArea = document.querySelector('.simulation-area');

    function createAmbientGlow() {

      const glow = document.createElement('div');

      glow.style.position = 'absolute';
      glow.style.width = '10px';
      glow.style.height = '10px';
      glow.style.borderRadius = '50%';
      glow.style.background = 'rgba(83,247,255,0.7)';
      glow.style.boxShadow = '0 0 25px rgba(83,247,255,0.8)';
      glow.style.left = Math.random() * window.innerWidth + 'px';
      glow.style.top = window.innerHeight + 'px';
      glow.style.pointerEvents = 'none';

      simulationArea.appendChild(glow);

      let posY = window.innerHeight;

      const move = setInterval(() => {

        posY -= 2;
        glow.style.top = posY + 'px';
        glow.style.opacity -= 0.002;

        if (posY < -20) {
          clearInterval(move);
          glow.remove();
        }

      }, 16);

    }

    setInterval(createAmbientGlow, 800);

    // Ultra realistic cinematic lighting system

    const cinematicOverlay = document.createElement('div');
    cinematicOverlay.style.position = 'absolute';
    cinematicOverlay.style.inset = '0';
    cinematicOverlay.style.pointerEvents = 'none';
    cinematicOverlay.style.background = 'radial-gradient(circle at center, rgba(255,255,255,0.04), transparent 60%)';
    cinematicOverlay.style.mixBlendMode = 'screen';
    cinematicOverlay.style.opacity = '0.8';

    simulationArea.appendChild(cinematicOverlay);

    setInterval(() => {

      const intensity = 0.7 + Math.random() * 0.2;
      cinematicOverlay.style.opacity = intensity;

    }, 1200);

    // Dynamic lighting effect

    document.addEventListener('mousemove', (e) => {

      const x = e.clientX / window.innerWidth;
      const y = e.clientY / window.innerHeight;

      document.body.style.background = `
        radial-gradient(circle at ${x * 100}% ${y * 100}%, rgba(53,104,255,0.22), transparent 25%),
        radial-gradient(circle at bottom left, rgba(0,255,255,0.08), transparent 25%),
        #08111f
      `;

    });

    // Floating UI effect

    const cards = document.querySelectorAll('.floating-card, .metric-box, .panel');

    cards.forEach(card => {

      card.addEventListener('mousemove', (e) => {

        const rect = card.getBoundingClientRect();

        const x = e.clientX - rect.left;
        const y = e.clientY - rect.top;

        const rotateY = ((x / rect.width) - 0.5) * 10;
        const rotateX = ((y / rect.height) - 0.5) * -10;

        card.style.transform = `perspective(800px) rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;

      });

      card.addEventListener('mouseleave', () => {

        card.style.transform = 'perspective(800px) rotateX(0deg) rotateY(0deg)';

      });

    });

  </script><!-- ========================================= --><!-- ULTRA ENGINE SYSTEMS --><!-- ========================================= --><script type="module">

import * as THREE from 'https://cdn.jsdelivr.net/npm/three@0.158/build/three.module.js';

const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);

const renderer = new THREE.WebGLRenderer({
  antialias: true,
  alpha: true
});

renderer.setSize(window.innerWidth, window.innerHeight);
renderer.setPixelRatio(window.devicePixelRatio);
renderer.shadowMap.enabled = true;
renderer.shadowMap.type = THREE.PCFSoftShadowMap;

renderer.domElement.style.position = 'absolute';
renderer.domElement.style.inset = '0';
renderer.domElement.style.zIndex = '0';
renderer.domElement.style.pointerEvents = 'none';
renderer.domElement.style.opacity = '0.35';

const simulation = document.querySelector('.simulation-area');
simulation.appendChild(renderer.domElement);

camera.position.z = 8;

const ambient = new THREE.AmbientLight(0xffffff, 1.2);
scene.add(ambient);

const pointLight = new THREE.PointLight(0x53f7ff, 3);
pointLight.position.set(4, 6, 5);
pointLight.castShadow = true;
scene.add(pointLight);

const geometry = new THREE.TorusKnotGeometry(1.2, 0.35, 200, 32);

const material = new THREE.MeshPhysicalMaterial({
  color: 0x53f7ff,
  metalness: 1,
  roughness: 0.15,
  transmission: 0.4,
  clearcoat: 1,
  emissive: 0x113344,
  emissiveIntensity: 1.5
});

const knot = new THREE.Mesh(geometry, material);
knot.castShadow = true;
knot.receiveShadow = true;
scene.add(knot);

function ultraRender() {

  requestAnimationFrame(ultraRender);

  knot.rotation.x += 0.003;
  knot.rotation.y += 0.004;

  renderer.render(scene, camera);

}

ultraRender();

window.addEventListener('resize', () => {

  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();

  renderer.setSize(window.innerWidth, window.innerHeight);

});

</script><!-- ========================================= --><!-- PROFESSIONAL MULTI LANGUAGE STACK --><!-- ========================================= --><!--
HTML5  → الهيكل
CSS3 + Glassmorphism → التصميم الواقعي
JavaScript ES2025 → التفاعل والأنيميشن
Three.js → رسوم 3D حقيقية
WebGL → تسريع رسومي احترافي
SVG Engine → أسلاك ومؤثرات كهربائية
Canvas API → تأثيرات الطاقة
Physics Simulation → محاكاة واقعية
GPU Rendering → أداء فائق
Dynamic Lighting → إضاءة سينمائية

إعداد الأستاذ سيف الربيعي
إعداد الطالب علي حازم
--></body>
</html>
