
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Test Platformasi</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
  :root {
    --primary: #6C63FF;
    --secondary: #FF6584;
    --accent: #43E97B;
    --dark: #1a1a2e;
    --card: #16213e;
    --card2: #0f3460;
    --text: #e0e0ff;
    --muted: #8888aa;
    --radius: 18px;
    --shadow: 0 8px 32px rgba(108,99,255,0.18);
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'Nunito', sans-serif;
    background: var(--dark);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* HEADER */
  .header {
    background: linear-gradient(135deg, var(--primary), #a855f7);
    padding: 18px 20px 14px;
    text-align: center;
    position: sticky; top: 0; z-index: 100;
    box-shadow: 0 4px 20px rgba(108,99,255,0.4);
  }
  .header h1 { font-size: 1.5rem; font-weight: 900; color: #fff; letter-spacing: 1px; }
  .header p { font-size: 0.8rem; color: rgba(255,255,255,0.75); margin-top: 2px; }

  /* LANG SWITCHER */
  .lang-bar {
    display: flex; justify-content: center; gap: 8px;
    padding: 12px 16px;
    background: var(--card);
  }
  .lang-btn {
    padding: 6px 18px; border-radius: 30px; border: 2px solid transparent;
    font-family: 'Nunito', sans-serif; font-weight: 700; font-size: 0.85rem;
    cursor: pointer; background: var(--card2); color: var(--muted);
    transition: all 0.2s;
  }
  .lang-btn.active { background: var(--primary); color: #fff; border-color: var(--primary); }

  /* SCREENS */
  .screen { display: none; padding: 20px 16px; max-width: 480px; margin: 0 auto; }
  .screen.active { display: block; }

  /* HOME */
  .grade-title { font-size: 1rem; font-weight: 800; color: var(--primary); margin-bottom: 12px; text-transform: uppercase; letter-spacing: 1px; }
  .grade-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-bottom: 24px; }
  .grade-btn {
    background: var(--card); border: 2px solid var(--card2);
    border-radius: var(--radius); padding: 18px 8px;
    text-align: center; cursor: pointer;
    transition: all 0.2s; color: var(--text);
    font-family: 'Nunito', sans-serif; font-weight: 800; font-size: 1.1rem;
  }
  .grade-btn:hover, .grade-btn.selected {
    border-color: var(--primary); background: rgba(108,99,255,0.15);
    color: #fff; transform: scale(1.04);
  }
  .grade-btn span { display: block; font-size: 0.65rem; font-weight: 600; color: var(--muted); margin-top: 2px; }

  .subject-title { font-size: 1rem; font-weight: 800; color: var(--secondary); margin-bottom: 12px; text-transform: uppercase; letter-spacing: 1px; }
  .subject-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px; }
  .subject-btn {
    background: var(--card); border: 2px solid var(--card2);
    border-radius: var(--radius); padding: 16px 10px;
    text-align: center; cursor: pointer;
    transition: all 0.2s; color: var(--text);
    font-family: 'Nunito', sans-serif; font-weight: 700; font-size: 0.9rem;
  }
  .subject-btn .icon { font-size: 1.8rem; display: block; margin-bottom: 4px; }
  .subject-btn:hover, .subject-btn.selected {
    border-color: var(--secondary); background: rgba(255,101,132,0.12);
    color: #fff; transform: scale(1.04);
  }

  .start-btn {
    width: 100%; margin-top: 24px;
    background: linear-gradient(135deg, var(--primary), #a855f7);
    color: #fff; border: none; border-radius: var(--radius);
    padding: 16px; font-family: 'Nunito', sans-serif;
    font-size: 1.1rem; font-weight: 900; cursor: pointer;
    box-shadow: var(--shadow); transition: all 0.2s; letter-spacing: 0.5px;
  }
  .start-btn:hover { transform: translateY(-2px); box-shadow: 0 12px 40px rgba(108,99,255,0.35); }
  .start-btn:disabled { opacity: 0.4; cursor: not-allowed; transform: none; }

  /* QUIZ */
  .quiz-header {
    display: flex; align-items: center; gap: 10px; margin-bottom: 16px;
  }
  .back-btn {
    background: var(--card); border: none; border-radius: 12px;
    color: var(--text); width: 38px; height: 38px;
    font-size: 1.1rem; cursor: pointer; flex-shrink: 0;
    display: flex; align-items: center; justify-content: center;
  }
  .quiz-meta { flex: 1; }
  .quiz-meta h2 { font-size: 1rem; font-weight: 800; color: #fff; }
  .quiz-meta p { font-size: 0.75rem; color: var(--muted); }
  .q-counter {
    font-size: 0.85rem; font-weight: 800; color: var(--primary);
    background: rgba(108,99,255,0.15); border-radius: 10px; padding: 4px 10px;
  }

  .progress-bar {
    height: 8px; background: var(--card2); border-radius: 10px; margin-bottom: 20px; overflow: hidden;
  }
  .progress-fill {
    height: 100%; background: linear-gradient(90deg, var(--primary), var(--accent));
    border-radius: 10px; transition: width 0.4s ease;
  }

  .question-card {
    background: var(--card); border-radius: var(--radius);
    padding: 20px; margin-bottom: 16px;
    border: 2px solid var(--card2);
    box-shadow: var(--shadow);
  }
  .question-num { font-size: 0.75rem; color: var(--primary); font-weight: 800; margin-bottom: 8px; }
  .question-text { font-size: 1rem; font-weight: 700; color: #fff; line-height: 1.5; }

  .options { display: flex; flex-direction: column; gap: 10px; margin-bottom: 20px; }
  .option-btn {
    background: var(--card); border: 2px solid var(--card2);
    border-radius: 14px; padding: 14px 16px;
    text-align: left; cursor: pointer;
    font-family: 'Nunito', sans-serif; font-weight: 700; font-size: 0.95rem;
    color: var(--text); transition: all 0.18s; display: flex; align-items: center; gap: 12px;
  }
  .option-letter {
    width: 30px; height: 30px; border-radius: 50%;
    background: var(--card2); display: flex; align-items: center;
    justify-content: center; font-size: 0.8rem; font-weight: 900;
    flex-shrink: 0; color: var(--muted);
  }
  .option-btn:hover:not(:disabled) { border-color: var(--primary); background: rgba(108,99,255,0.12); color: #fff; }
  .option-btn.correct { border-color: var(--accent); background: rgba(67,233,123,0.15); color: #fff; }
  .option-btn.correct .option-letter { background: var(--accent); color: #111; }
  .option-btn.wrong { border-color: var(--secondary); background: rgba(255,101,132,0.15); color: #fff; }
  .option-btn.wrong .option-letter { background: var(--secondary); color: #fff; }
  .option-btn:disabled { cursor: default; }

  .next-btn {
    width: 100%; background: linear-gradient(135deg, var(--primary), #a855f7);
    color: #fff; border: none; border-radius: var(--radius);
    padding: 14px; font-family: 'Nunito', sans-serif;
    font-size: 1rem; font-weight: 900; cursor: pointer;
    transition: all 0.2s; display: none;
  }
  .next-btn.show { display: block; }

  /* RESULT */
  .result-card {
    background: var(--card); border-radius: 24px;
    padding: 30px 20px; text-align: center;
    border: 2px solid var(--card2); box-shadow: var(--shadow);
    margin-bottom: 20px;
  }
  .result-emoji { font-size: 4rem; margin-bottom: 10px; }
  .result-score { font-size: 3rem; font-weight: 900; color: var(--primary); }
  .result-label { font-size: 1.1rem; font-weight: 700; color: var(--text); margin-bottom: 6px; }
  .result-grade { font-size: 0.85rem; color: var(--muted); margin-bottom: 20px; }
  .result-bars { text-align: left; }
  .bar-row { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; }
  .bar-label { font-size: 0.8rem; font-weight: 700; width: 70px; color: var(--muted); }
  .bar-track { flex: 1; height: 10px; background: var(--card2); border-radius: 10px; overflow: hidden; }
  .bar-fill-c { height: 100%; background: var(--accent); border-radius: 10px; }
  .bar-fill-w { height: 100%; background: var(--secondary); border-radius: 10px; }
  .bar-num { font-size: 0.8rem; font-weight: 800; width: 24px; text-align: right; }

  .retry-btn {
    width: 100%; background: linear-gradient(135deg, var(--accent), #38ef7d);
    color: #111; border: none; border-radius: var(--radius);
    padding: 14px; font-family: 'Nunito', sans-serif;
    font-size: 1rem; font-weight: 900; cursor: pointer; margin-bottom: 10px;
  }
  .home-btn {
    width: 100%; background: var(--card); color: var(--text);
    border: 2px solid var(--card2); border-radius: var(--radius);
    padding: 14px; font-family: 'Nunito', sans-serif;
    font-size: 1rem; font-weight: 700; cursor: pointer;
  }
</style>
</head>
<body>

<div class="header">
  <h1>🎓 <span id="hTitle">Test Platformasi</span></h1>
  <p id="hSub">5 - 11 sinf • 25 ta savol</p>
</div>

<div class="lang-bar">
  <button class="lang-btn active" onclick="setLang('uz')">🇺🇿 UZB</button>
  <button class="lang-btn" onclick="setLang('ru')">🇷🇺 RUS</button>
  <button class="lang-btn" onclick="setLang('en')">🇬🇧 ENG</button>
</div>

<!-- HOME SCREEN -->
<div class="screen active" id="homeScreen">
  <p class="grade-title" id="txt_grade">Sinfni tanlang</p>
  <div class="grade-grid" id="gradeGrid"></div>

  <p class="subject-title" id="txt_subject">Fanini tanlang</p>
  <div class="subject-grid" id="subjectGrid"></div>

  <button class="start-btn" id="startBtn" disabled onclick="startQuiz()" id="txt_start">Boshlash →</button>
</div>

<!-- QUIZ SCREEN -->
<div class="screen" id="quizScreen">
  <div class="quiz-header">
    <button class="back-btn" onclick="goHome()">←</button>
    <div class="quiz-meta">
      <h2 id="quizTitle">-</h2>
      <p id="quizSubtitle">-</p>
    </div>
    <div class="q-counter" id="qCounter">1/25</div>
  </div>
  <div class="progress-bar"><div class="progress-fill" id="progressFill" style="width:4%"></div></div>
  <div class="question-card">
    <div class="question-num" id="qNum">Savol 1</div>
    <div class="question-text" id="qText">...</div>
  </div>
  <div class="options" id="optionsContainer"></div>
  <button class="next-btn" id="nextBtn" onclick="nextQuestion()">Keyingisi →</button>
</div>

<!-- RESULT SCREEN -->
<div class="screen" id="resultScreen">
  <div class="result-card">
    <div class="result-emoji" id="resultEmoji">🏆</div>
    <div class="result-score" id="resultScore">0/25</div>
    <div class="result-label" id="resultLabel">Natija</div>
    <div class="result-grade" id="resultGradeInfo"></div>
    <div class="result-bars">
      <div class="bar-row">
        <div class="bar-label" id="txt_correct2">To'g'ri</div>
        <div class="bar-track"><div class="bar-fill-c" id="barCorrect"></div></div>
        <div class="bar-num" id="barCNum" style="color:var(--accent)">0</div>
      </div>
      <div class="bar-row">
        <div class="bar-label" id="txt_wrong2">Noto'g'ri</div>
        <div class="bar-track"><div class="bar-fill-w" id="barWrong"></div></div>
        <div class="bar-num" id="barWNum" style="color:var(--secondary)">0</div>
      </div>
    </div>
  </div>
  <button class="retry-btn" onclick="retryQuiz()" id="txt_retry">🔄 Qayta urinish</button>
  <button class="home-btn" onclick="goHome()" id="txt_home">🏠 Bosh sahifa</button>
</div>

<script>
// ===================== TRANSLATIONS =====================
const T = {
  uz: {
    hTitle: "Test Platformasi", hSub: "5 - 11 sinf • 25 ta savol",
    txt_grade: "Sinfni tanlang", txt_subject: "Fanini tanlang",
    txt_start: "Boshlash →", sinf: "sinf",
    qWord: "Savol", nextBtn: "Keyingisi →",
    txt_correct2: "To'g'ri", txt_wrong2: "Noto'g'ri",
    txt_retry: "🔄 Qayta urinish", txt_home: "🏠 Bosh sahifa",
    resultLabel: ["Ajoyib! 🔥", "Yaxshi! 👍", "O'rtacha 😐", "Zaif 😔"],
  },
  ru: {
    hTitle: "Тест Платформа", hSub: "5 - 11 класс • 25 вопросов",
    txt_grade: "Выберите класс", txt_subject: "Выберите предмет",
    txt_start: "Начать →", sinf: "класс",
    qWord: "Вопрос", nextBtn: "Следующий →",
    txt_correct2: "Верно", txt_wrong2: "Неверно",
    txt_retry: "🔄 Попробовать снова", txt_home: "🏠 Главная",
    resultLabel: ["Отлично! 🔥", "Хорошо! 👍", "Средне 😐", "Слабо 😔"],
  },
  en: {
    hTitle: "Test Platform", hSub: "Grade 5 - 11 • 25 Questions",
    txt_grade: "Select Grade", txt_subject: "Select Subject",
    txt_start: "Start →", sinf: "Grade",
    qWord: "Question", nextBtn: "Next →",
    txt_correct2: "Correct", txt_wrong2: "Wrong",
    txt_retry: "🔄 Try Again", txt_home: "🏠 Home",
    resultLabel: ["Excellent! 🔥", "Good! 👍", "Average 😐", "Weak 😔"],
  }
};

// ===================== SUBJECTS =====================
const subjects = {
  uz: [
    {id:"math", icon:"➕", name:"Matematika"},
    {id:"physics", icon:"⚡", name:"Fizika"},
    {id:"history", icon:"📜", name:"Tarix"},
    {id:"biology", icon:"🌿", name:"Biologiya"},
    {id:"geo", icon:"🌍", name:"Geografiya"},
    {id:"lit", icon:"📖", name:"Adabiyot"},
  ],
  ru: [
    {id:"math", icon:"➕", name:"Математика"},
    {id:"physics", icon:"⚡", name:"Физика"},
    {id:"history", icon:"📜", name:"История"},
    {id:"biology", icon:"🌿", name:"Биология"},
    {id:"geo", icon:"🌍", name:"География"},
    {id:"lit", icon:"📖", name:"Литература"},
  ],
  en: [
    {id:"math", icon:"➕", name:"Mathematics"},
    {id:"physics", icon:"⚡", name:"Physics"},
    {id:"history", icon:"📜", name:"History"},
    {id:"biology", icon:"🌿", name:"Biology"},
    {id:"geo", icon:"🌍", name:"Geography"},
    {id:"lit", icon:"📖", name:"Literature"},
  ]
};

// ===================== QUESTIONS DB =====================
// Each subject: grades 5-11, 25 questions each (sample set, rotated)
// For brevity: we generate from a pool of base questions per subject
// Real app would have full 7*25=175 per subject

const QDB = {
  math: {
    base: [
      // Grade-adjusted difficulty baked in by grade filter
      {q:{uz:"2 + 2 = ?", ru:"2 + 2 = ?", en:"2 + 2 = ?"}, opts:["4","3","5","6"], a:0, g:[5]},
      {q:{uz:"5 × 6 = ?", ru:"5 × 6 = ?", en:"5 × 6 = ?"}, opts:["30","25","35","36"], a:0, g:[5,6]},
      {q:{uz:"12 ÷ 4 = ?", ru:"12 ÷ 4 = ?", en:"12 ÷ 4 = ?"}, opts:["3","4","2","6"], a:0, g:[5,6]},
      {q:{uz:"√144 = ?", ru:"√144 = ?", en:"√144 = ?"}, opts:["12","11","13","14"], a:0, g:[6,7,8]},
      {q:{uz:"3² = ?", ru:"3² = ?", en:"3² = ?"}, opts:["9","6","8","12"], a:0, g:[5,6,7]},
      {q:{uz:"Aylana uzunligi formulasi?", ru:"Формула длины окружности?", en:"Formula for circumference?"}, opts:["2πr","πr²","πd²","2πd"], a:0, g:[6,7,8]},
      {q:{uz:"x² - 9 = 0, x = ?", ru:"x² - 9 = 0, x = ?", en:"x² - 9 = 0, x = ?"}, opts:["±3","±9","3","9"], a:0, g:[8,9]},
      {q:{uz:"sin 90° = ?", ru:"sin 90° = ?", en:"sin 90° = ?"}, opts:["1","0","-1","0.5"], a:0, g:[9,10,11]},
      {q:{uz:"log₂ 8 = ?", ru:"log₂ 8 = ?", en:"log₂ 8 = ?"}, opts:["3","2","4","8"], a:0, g:[10,11]},
      {q:{uz:"∫x dx = ?", ru:"∫x dx = ?", en:"∫x dx = ?"}, opts:["x²/2 + C","x² + C","2x + C","x/2 + C"], a:0, g:[11]},
      {q:{uz:"(a+b)² = ?", ru:"(a+b)² = ?", en:"(a+b)² = ?"}, opts:["a²+2ab+b²","a²+b²","a²-2ab+b²","2a+2b"], a:0, g:[7,8,9]},
      {q:{uz:"Pifagor teoremasi: a²+b² = ?", ru:"Теорема Пифагора: a²+b² = ?", en:"Pythagorean theorem: a²+b² = ?"}, opts:["c²","c","2c","c³"], a:0, g:[7,8]},
      {q:{uz:"3x = 15, x = ?", ru:"3x = 15, x = ?", en:"3x = 15, x = ?"}, opts:["5","3","15","12"], a:0, g:[5,6,7]},
      {q:{uz:"Uchburchak burchaklari yig'indisi?", ru:"Сумма углов треугольника?", en:"Sum of angles in a triangle?"}, opts:["180°","360°","90°","270°"], a:0, g:[5,6,7,8]},
      {q:{uz:"cos 0° = ?", ru:"cos 0° = ?", en:"cos 0° = ?"}, opts:["1","0","-1","0.5"], a:0, g:[9,10,11]},
      {q:{uz:"7! = ?", ru:"7! = ?", en:"7! = ?"}, opts:["5040","720","40320","210"], a:0, g:[10,11]},
      {q:{uz:"2⁵ = ?", ru:"2⁵ = ?", en:"2⁵ = ?"}, opts:["32","16","64","25"], a:0, g:[6,7,8]},
      {q:{uz:"Kvadrat ildiz: √81 = ?", ru:"Квадратный корень: √81 = ?", en:"Square root: √81 = ?"}, opts:["9","8","7","6"], a:0, g:[7,8,9]},
      {q:{uz:"y = x² funksiyasining hosila?", ru:"Производная y = x²?", en:"Derivative of y = x²?"}, opts:["2x","x","2","x²"], a:0, g:[11]},
      {q:{uz:"1 km = ? m", ru:"1 км = ? м", en:"1 km = ? m"}, opts:["1000","100","10000","10"], a:0, g:[5]},
      {q:{uz:"Protsent: 20% dan 50 = ?", ru:"20% от 50 = ?", en:"20% of 50 = ?"}, opts:["10","20","25","15"], a:0, g:[6,7]},
      {q:{uz:"tg 45° = ?", ru:"tg 45° = ?", en:"tan 45° = ?"}, opts:["1","0","√3","√2"], a:0, g:[9,10,11]},
      {q:{uz:"Arifmetik progressiyaning n-hadi: aₙ = ?", ru:"n-й член арифм. прогрессии?", en:"nth term of arithmetic progression?"}, opts:["a₁+(n-1)d","a₁·n","a₁+(n+1)d","nd"], a:0, g:[9,10]},
      {q:{uz:"Kombinatsiya: C(5,2) = ?", ru:"Сочетание: C(5,2) = ?", en:"Combination: C(5,2) = ?"}, opts:["10","20","5","15"], a:0, g:[10,11]},
      {q:{uz:"Matritsa 2x2 determinanti: |a b; c d| = ?", ru:"Определитель матрицы 2x2?", en:"Determinant of 2x2 matrix?"}, opts:["ad-bc","ab-cd","a+d","ac-bd"], a:0, g:[11]},
    ]
  },
  physics: {
    base: [
      {q:{uz:"Yorug'lik tezligi (m/s)?", ru:"Скорость света (м/с)?", en:"Speed of light (m/s)?"}, opts:["3×10⁸","3×10⁶","3×10⁷","3×10⁹"], a:0, g:[8,9,10,11]},
      {q:{uz:"F = ma — bu qaysi qonun?", ru:"F = ma — какой закон?", en:"F = ma — which law?"}, opts:["Nyuton 2-qonuni","Nyuton 1-qonuni","Nyuton 3-qonuni","Guk qonuni"], a:0, g:[7,8,9,10]},
      {q:{uz:"Elektr qarshilik birligi?", ru:"Единица электрического сопротивления?", en:"Unit of electrical resistance?"}, opts:["Om","Volt","Amper","Vatt"], a:0, g:[8,9,10]},
      {q:{uz:"Gravitatsiya tezlanishi (m/s²)?", ru:"Ускорение свободного падения (м/с²)?", en:"Gravitational acceleration (m/s²)?"}, opts:["9.8","10","8.9","11"], a:0, g:[7,8,9]},
      {q:{uz:"E = mc² — bu qaysi formula?", ru:"E = mc² — чья формула?", en:"E = mc² — whose formula?"}, opts:["Eynshteyn","Nyuton","Faradey","Plank"], a:0, g:[10,11]},
      {q:{uz:"Ovoz tezligi havoda (m/s)?", ru:"Скорость звука в воздухе (м/с)?", en:"Speed of sound in air (m/s)?"}, opts:["340","300","400","250"], a:0, g:[8,9]},
      {q:{uz:"1 kVt = ? Vt", ru:"1 кВт = ? Вт", en:"1 kW = ? W"}, opts:["1000","100","10","10000"], a:0, g:[7,8]},
      {q:{uz:"Magnit maydon birligi?", ru:"Единица магнитной индукции?", en:"Unit of magnetic flux density?"}, opts:["Tesla","Om","Farad","Genri"], a:0, g:[10,11]},
      {q:{uz:"Issiqlik miqdori formulasi?", ru:"Формула количества теплоты?", en:"Formula for heat energy?"}, opts:["Q=mcΔT","Q=mc²","Q=mT","Q=cΔT"], a:0, g:[8,9,10]},
      {q:{uz:"Yoritilganlik birligi?", ru:"Единица освещённости?", en:"Unit of illuminance?"}, opts:["Lyuks","Kandela","Lyumen","Vatt"], a:0, g:[11]},
      {q:{uz:"Mexanik energiya nima?", ru:"Что такое механическая энергия?", en:"What is mechanical energy?"}, opts:["KE+PE","KE×PE","KE-PE","F×d"], a:0, g:[7,8]},
      {q:{uz:"Om qonuni: I = ?", ru:"Закон Ома: I = ?", en:"Ohm's law: I = ?"}, opts:["U/R","U×R","R/U","U+R"], a:0, g:[9,10]},
      {q:{uz:"Isitgich quvvati: P = ?", ru:"Мощность нагревателя: P = ?", en:"Power of heater: P = ?"}, opts:["I²R","IR","I/R","R/I"], a:0, g:[9,10,11]},
      {q:{uz:"Foton energiyasi: E = ?", ru:"Энергия фотона: E = ?", en:"Energy of photon: E = ?"}, opts:["hν","mc²","mv²/2","hc"], a:0, g:[11]},
      {q:{uz:"Gidravlik press: P₁/P₂ = ?", ru:"Гидравлический пресс: P₁/P₂ = ?", en:"Hydraulic press: F₁/F₂ = ?"}, opts:["S₁/S₂","S₂/S₁","V₁/V₂","m₁/m₂"], a:0, g:[7,8]},
      {q:{uz:"Yadro reaksiyasida nima saqlanadi?", ru:"Что сохраняется в ядерной реакции?", en:"What is conserved in nuclear reaction?"}, opts:["Massa va energiya","Faqat massa","Faqat energiya","Zaryadlar"], a:0, g:[11]},
      {q:{uz:"Bog'lovchi kuch: F = ?", ru:"Сила связи: F = ?", en:"Coulomb force: F = ?"}, opts:["kq₁q₂/r²","kq/r","q₁q₂r","kq²"], a:0, g:[10,11]},
      {q:{uz:"Impuls nima?", ru:"Что такое импульс?", en:"What is momentum?"}, opts:["mv","ma","Ft","mgh"], a:0, g:[8,9,10]},
      {q:{uz:"Radioaktiv yemirilish — bu nima?", ru:"Что такое радиоактивный распад?", en:"What is radioactive decay?"}, opts:["Yadro yemirilishi","Atom bug'lanishi","Elektron yo'qolishi","Ionlanish"], a:0, g:[11]},
      {q:{uz:"1 atm = ? Pa", ru:"1 атм = ? Па", en:"1 atm = ? Pa"}, opts:["101325","100000","1000","10000"], a:0, g:[9,10]},
      {q:{uz:"Termometr asosi?", ru:"Принцип термометра?", en:"Principle of thermometer?"}, opts:["Kengayish","Isish","Tortishish","Eriish"], a:0, g:[5,6]},
      {q:{uz:"Linza fokus masofasi f = ?", ru:"Фокусное расстояние линзы?", en:"Focal length formula?"}, opts:["1/f=1/d+1/v","f=dv","f=d-v","1/f=dv"], a:0, g:[10,11]},
      {q:{uz:"Mayatnikning davri: T = ?", ru:"Период маятника: T = ?", en:"Period of pendulum: T = ?"}, opts:["2π√(l/g)","2πl/g","πl/g","2π√g"], a:0, g:[10,11]},
      {q:{uz:"Faradey elektroliz qonuni nimani aniqlaydi?", ru:"Что определяет закон Фарадея?", en:"What does Faraday's law define?"}, opts:["Elektrolizda ajraladigan modda miqdori","Tok kuchi","Qarshilik","Kuchlanish"], a:0, g:[10,11]},
      {q:{uz:"Suyuqlikning siqilmasligi — bu qaysi qonun?", ru:"Несжимаемость жидкости — какой закон?", en:"Incompressibility of liquid — which law?"}, opts:["Paskal","Arximed","Bernulli","Nyuton"], a:0, g:[8,9]},
    ]
  },
  history: {
    base: [
      {q:{uz:"O'zbekiston mustaqillikka qachon erishdi?", ru:"Когда Узбекистан получил независимость?", en:"When did Uzbekistan gain independence?"}, opts:["1991","1990","1992","1993"], a:0, g:[5,6,7,8,9,10,11]},
      {q:{uz:"Amir Temur qachon tug'ilgan?", ru:"Когда родился Амир Тимур?", en:"When was Amir Timur born?"}, opts:["1336","1300","1370","1400"], a:0, g:[6,7,8]},
      {q:{uz:"Ikkinchi Jahon Urushi qachon tugadi?", ru:"Когда закончилась Вторая мировая война?", en:"When did World War II end?"}, opts:["1945","1944","1946","1943"], a:0, g:[7,8,9,10,11]},
      {q:{uz:"Buyuk Britaniya qachon AQShdan mustaqillikni tan oldi?", ru:"Когда Великобритания признала независимость США?", en:"When did Britain recognize US independence?"}, opts:["1783","1776","1789","1800"], a:0, g:[9,10,11]},
      {q:{uz:"Rim imperiyasi qachon qulab tushdi?", ru:"Когда пала Римская империя?", en:"When did the Roman Empire fall?"}, opts:["476 yil","395 yil","410 yil","500 yil"], a:0, g:[8,9,10]},
      {q:{uz:"Napoleon qaysi mamlakatdan?", ru:"Из какой страны Наполеон?", en:"Napoleon was from which country?"}, opts:["Fransiya","Italiya","Ispaniya","Germaniya"], a:0, g:[7,8,9]},
      {q:{uz:"Birinchi kosmosga chiqqan odam?", ru:"Первый человек в космосе?", en:"First human in space?"}, opts:["Yuriy Gagarin","Nil Armstrong","Vostok","Buzov"], a:0, g:[5,6,7]},
      {q:{uz:"Mo'g'ul imperiyasini kim asos soldi?", ru:"Кто основал Монгольскую империю?", en:"Who founded the Mongol Empire?"}, opts:["Chingizxon","Temurchin","Qubilayxon","Batu"], a:0, g:[7,8,9]},
      {q:{uz:"Fransuz inqilobi qachon boshlandi?", ru:"Когда началась Французская революция?", en:"When did the French Revolution begin?"}, opts:["1789","1776","1799","1804"], a:0, g:[9,10,11]},
      {q:{uz:"O'rta asrlar qachon boshlangan deb hisoblanadi?", ru:"Когда началось Средневековье?", en:"When did the Middle Ages begin?"}, opts:["476 yil","1000 yil","500 yil","400 yil"], a:0, g:[8,9]},
      {q:{uz:"Ispaniya qachon Amerikani kashf etdi?", ru:"Когда Испания открыла Америку?", en:"When did Spain discover America?"}, opts:["1492","1500","1490","1498"], a:0, g:[7,8,9]},
      {q:{uz:"Sovet Ittifoqi qachon tarqaldi?", ru:"Когда распался СССР?", en:"When did the Soviet Union collapse?"}, opts:["1991","1989","1993","1990"], a:0, g:[8,9,10,11]},
      {q:{uz:"Birinchi Jahon Urushi qachon boshlandi?", ru:"Когда началась Первая мировая война?", en:"When did World War I begin?"}, opts:["1914","1918","1912","1916"], a:0, g:[8,9,10]},
      {q:{uz:"Samarqand kim tomonidan qurilgan?", ru:"Кем был основан Самарканд?", en:"Who founded Samarkand?"}, opts:["Qadimgi so'g'dlar","Amir Temur","Arablar","Mo'g'ullar"], a:0, g:[6,7,8]},
      {q:{uz:"Renesans davri qaysi mamlakatda boshlangan?", ru:"В какой стране началась эпоха Возрождения?", en:"In which country did the Renaissance begin?"}, opts:["Italiya","Fransiya","Ispaniya","Germaniya"], a:0, g:[9,10,11]},
      {q:{uz:"Buyuk Ipak yo'li qayerdan qayergacha?", ru:"Великий шёлковый путь — откуда до куда?", en:"The Silk Road stretched from where to where?"}, opts:["Xitoydan Yevropagacha","Hindistondan Afrikagacha","Rossiyadan Xitaygacha","Arabistondan Yeropagacha"], a:0, g:[6,7,8,9]},
      {q:{uz:"AQSh qachon mustaqil bo'ldi?", ru:"Когда США стали независимыми?", en:"When did the US declare independence?"}, opts:["1776","1783","1789","1775"], a:0, g:[8,9,10]},
      {q:{uz:"Xitoy devori qachon qurilgan?", ru:"Когда построили Китайскую стену?", en:"When was the Great Wall of China built?"}, opts:["Mil.avv. 221","Mil. 500","Mil.avv. 100","Mil. 200"], a:0, g:[7,8]},
      {q:{uz:"Otamurot Qodirov kim?", ru:"Кто такой Отамурот Кодиров?", en:"Who is Otamurot Qodirov?"}, opts:["O'zbek shoiri","Tarixchi","Fizik","Matematik"], a:0, g:[5,6]},
      {q:{uz:"Oltun O'rda davlati qachon qurilgan?", ru:"Когда основана Золотая Орда?", en:"When was the Golden Horde founded?"}, opts:["1242","1206","1300","1380"], a:0, g:[8,9]},
      {q:{uz:"Birinchi O'zbekiston Prezidenti kim?", ru:"Первый президент Узбекистана?", en:"First president of Uzbekistan?"}, opts:["Islom Karimov","Sh. Mirziyoyev","Ro'zi Nishonov","A. Mutalov"], a:0, g:[5,6,7,8]},
      {q:{uz:"Bunyodkor Sulaymon Qonuniy qaysi imperiyaning sultoni?", ru:"Сулейман Великолепный — султан какой империи?", en:"Suleiman the Magnificent — sultan of which empire?"}, opts:["Usmonli","Arablar","Safaviylar","Mo'g'ul"], a:0, g:[9,10,11]},
      {q:{uz:"Aleksandr Makedonskiy O'rta Osiyoni qachon bosib oldi?", ru:"Когда Александр Македонский завоевал Среднюю Азию?", en:"When did Alexander conquer Central Asia?"}, opts:["Mil.avv. 329","Mil.avv. 300","Mil.avv. 350","Mil.avv. 400"], a:0, g:[9,10,11]},
      {q:{uz:"Berlinning ikki qismga bo'linishi qachon tugadi?", ru:"Когда было объединение Германии?", en:"When did Germany reunify?"}, opts:["1990","1989","1991","1988"], a:0, g:[10,11]},
      {q:{uz:"Inqilobning bosh shorlari kim edi (Fransiya 1789)?", ru:"Кто возглавил Французскую революцию?", en:"Who led the French Revolution?"}, opts:["Robesper","Napoleon","Lui XVI","Danton"], a:0, g:[10,11]},
    ]
  },
  biology: {
    base: [
      {q:{uz:"Fotosintez qayerda sodir bo'ladi?", ru:"Где происходит фотосинтез?", en:"Where does photosynthesis occur?"}, opts:["Xloropiastda","Mitoxondriyada","Yadroda","Sitoplazma"], a:0, g:[6,7,8,9]},
      {q:{uz:"DNK nima?", ru:"Что такое ДНК?", en:"What is DNA?"}, opts:["Dezoksiribonuklein kislota","Ribonuklein kislota","Oqsil","Yog'"], a:0, g:[8,9,10,11]},
      {q:{uz:"Inson tanasida necha suyak bor?", ru:"Сколько костей в теле человека?", en:"How many bones in the human body?"}, opts:["206","200","215","180"], a:0, g:[7,8]},
      {q:{uz:"Qon guruhlari necha xil?", ru:"Сколько групп крови?", en:"How many blood types are there?"}, opts:["4","3","5","6"], a:0, g:[7,8,9]},
      {q:{uz:"Hujayra hayot asosi deb kim aniqladi?", ru:"Кто установил, что клетка — основа жизни?", en:"Who established the cell theory?"}, opts:["Shleyden va Shvann","Darvin","Mendel","Lyavuaze"], a:0, g:[9,10]},
      {q:{uz:"Meioz nima?", ru:"Что такое мейоз?", en:"What is meiosis?"}, opts:["Jinsiy bo'linish","Mitoz","Hujayra o'limi","Rivojlanish"], a:0, g:[9,10,11]},
      {q:{uz:"O2 qaysi organda hosil bo'ladi?", ru:"Где в растении образуется O2?", en:"Where is O2 produced in plants?"}, opts:["Bargda","Ildizda","Poyada","Mevasida"], a:0, g:[6,7]},
      {q:{uz:"Evolyutsiya nazariyasini kim yaratdi?", ru:"Кто создал теорию эволюции?", en:"Who created the theory of evolution?"}, opts:["Darvin","Mendel","Pastyor","Lemark"], a:0, g:[8,9,10]},
      {q:{uz:"Insulin qaysi organ ishlab chiqaradi?", ru:"Какой орган вырабатывает инсулин?", en:"Which organ produces insulin?"}, opts:["Me'da osti bezi","Jigar","Buyrak","Taloq"], a:0, g:[9,10,11]},
      {q:{uz:"Mitoxondriya funksiyasi?", ru:"Функция митохондрии?", en:"Function of mitochondria?"}, opts:["Energiya ishlab chiqarish","Oqsil sintezi","Fotosintez","Hazm"], a:0, g:[8,9,10]},
      {q:{uz:"Bakteriyalar qaysi hujayra turida?", ru:"К какому типу клеток относятся бактерии?", en:"Bacteria belong to which cell type?"}, opts:["Prokariot","Eukariot","Virus","Arxey"], a:0, g:[8,9]},
      {q:{uz:"Eng yirik umurtqasiz hayvon?", ru:"Крупнейшее беспозвоночное?", en:"Largest invertebrate?"}, opts:["Gigant kalmar","Dengiz yulduzi","Qisqichbaqa","Medusa"], a:0, g:[6,7,8]},
      {q:{uz:"Mendel genetika qonunlari necha ta?", ru:"Сколько законов Менделя?", en:"How many Mendel's laws are there?"}, opts:["3","2","4","1"], a:0, g:[10,11]},
      {q:{uz:"Inson miyasining vazni?", ru:"Масса мозга человека?", en:"Weight of human brain?"}, opts:["~1.4 kg","~2 kg","~1 kg","~3 kg"], a:0, g:[8,9]},
      {q:{uz:"Leykotsitlar nima?", ru:"Что такое лейкоциты?", en:"What are leukocytes?"}, opts:["Oq qon tanachalari","Qizil qon tanachalari","Trombositlar","Plazma"], a:0, g:[8,9,10]},
      {q:{uz:"Fotosintez formulasi?", ru:"Формула фотосинтеза?", en:"Formula for photosynthesis?"}, opts:["6CO₂+6H₂O→C₆H₁₂O₆+6O₂","6O₂+H₂O→CO₂","CO₂+O₂→H₂O","H₂O→O₂+CO₂"], a:0, g:[9,10,11]},
      {q:{uz:"Gemoglobin nima?", ru:"Что такое гемоглобин?", en:"What is hemoglobin?"}, opts:["Qondagi oqsil","Ferment","Vitamin","Gormon"], a:0, g:[9,10]},
      {q:{uz:"Eng kichik tirik organizm?", ru:"Наименьший живой организм?", en:"Smallest living organism?"}, opts:["Mikoplazma","Virus","Bakteriya","Arxey"], a:0, g:[10,11]},
      {q:{uz:"O'simliklarning ko'payishi necha xil?", ru:"Сколько способов размножения растений?", en:"How many types of plant reproduction?"}, opts:["2 (jinsiy va jinssiz)","1","3","4"], a:0, g:[7,8]},
      {q:{uz:"Jigar qanday funksiyani bajaradi?", ru:"Функция печени?", en:"Function of the liver?"}, opts:["Detoksikatsiya","Nafas olish","Hazm","Qon ishlab chiqarish"], a:0, g:[8,9]},
      {q:{uz:"Biota nima?", ru:"Что такое биота?", en:"What is biota?"}, opts:["Ekotizimdagi barcha jonzotlar","O'simliklar","Hayvonlar","Bakteriyalar"], a:0, g:[10,11]},
      {q:{uz:"Fototropizm nima?", ru:"Что такое фототропизм?", en:"What is phototropism?"}, opts:["Yorug'likka qarab o'sish","Gravitatsiyaga qarab o'sish","Suvga qarab o'sish","Tezkor o'sish"], a:0, g:[8,9]},
      {q:{uz:"Xromosom nima?", ru:"Что такое хромосома?", en:"What is a chromosome?"}, opts:["DNK va oqsil majmuasi","Faqat DNK","Faqat oqsil","RNK zanjiri"], a:0, g:[10,11]},
      {q:{uz:"Inson tanasida necha litr qon bor?", ru:"Сколько литров крови в теле человека?", en:"How many liters of blood in human body?"}, opts:["4.5-5.5","3-4","6-7","2-3"], a:0, g:[7,8,9]},
      {q:{uz:"Eng uzoq umr ko'ruvchi hayvon?", ru:"Какое животное живёт дольше всех?", en:"Longest-living animal?"}, opts:["Arktik dengiz mollyuskasi","Toshbaqa","Fil","Kit"], a:0, g:[6,7,8]},
    ]
  },
  geo: {
    base: [
      {q:{uz:"Dunyodagi eng baland tog'?", ru:"Самая высокая гора мира?", en:"Tallest mountain in the world?"}, opts:["Everest","K2","Kilimanjaro","Elbrus"], a:0, g:[5,6,7]},
      {q:{uz:"O'zbekiston poytaxti?", ru:"Столица Узбекистана?", en:"Capital of Uzbekistan?"}, opts:["Toshkent","Samarqand","Buxoro","Namangan"], a:0, g:[5,6]},
      {q:{uz:"Dunyodagi eng katta okean?", ru:"Самый большой океан?", en:"Largest ocean in the world?"}, opts:["Tinch okeani","Atlantika","Hind okeani","Arktika"], a:0, g:[5,6,7]},
      {q:{uz:"Amazonka daryosi qaysi qit'ada?", ru:"На каком континенте река Амазонка?", en:"Amazon river is on which continent?"}, opts:["Janubiy Amerika","Afrika","Shimoliy Amerika","Osiyo"], a:0, g:[6,7,8]},
      {q:{uz:"Sahara cho'li qaysi qit'ada?", ru:"На каком континенте пустыня Сахара?", en:"Sahara desert is on which continent?"}, opts:["Afrika","Osiyo","Avstraliya","Janubiy Amerika"], a:0, g:[6,7]},
      {q:{uz:"Dunyo aholi soni (taxminan)?", ru:"Население Земли (примерно)?", en:"World population (approximate)?"}, opts:["8 mlrd","7 mlrd","9 mlrd","6 mlrd"], a:0, g:[7,8,9]},
      {q:{uz:"O'rta Osiyo mamlakatlari nechta?", ru:"Сколько стран в Средней Азии?", en:"How many countries in Central Asia?"}, opts:["5","4","6","3"], a:0, g:[6,7,8]},
      {q:{uz:"Necha vaqt zonasi bor dunyoda?", ru:"Сколько часовых поясов на Земле?", en:"How many time zones on Earth?"}, opts:["24","12","48","36"], a:0, g:[7,8,9]},
      {q:{uz:"Braziliya poytaxti?", ru:"Столица Бразилии?", en:"Capital of Brazil?"}, opts:["Braziliya","San-Paulo","Rio-de-Janeyro","Salvador"], a:0, g:[8,9]},
      {q:{uz:"Nok qaysi mamlakatdan?", ru:"Из какой страны происходит груша?", en:"Where do pears originate from?"}, opts:["Xitoy","Rossiya","Italiya","Turkiya"], a:0, g:[5,6]},
      {q:{uz:"Dunyo eng ko'p aholili mamlakat?", ru:"Самая населённая страна мира?", en:"Most populous country in the world?"}, opts:["Hindiston","Xitoy","AQSh","Indoneziya"], a:0, g:[7,8,9,10]},
      {q:{uz:"Mariana chuquri qayerda joylashgan?", ru:"Где находится Марианская впадина?", en:"Where is the Mariana Trench located?"}, opts:["Tinch okeanida","Atlantikada","Hind okeanida","Arktikada"], a:0, g:[8,9,10]},
      {q:{uz:"Antarktida qit'asida qaysi davlat joylashgan?", ru:"Какое государство находится в Антарктиде?", en:"Which state is located in Antarctica?"}, opts:["Hech bir davlat yo'q","Norvegiya","Avstraliya","Argentina"], a:0, g:[7,8]},
      {q:{uz:"Eng katta davlat (maydon)?", ru:"Самое большое государство (площадь)?", en:"Largest country by area?"}, opts:["Rossiya","Kanada","Xitoy","AQSh"], a:0, g:[6,7,8]},
      {q:{uz:"Volga daryosi qaysi mamlakatda?", ru:"В какой стране река Волга?", en:"The Volga river is in which country?"}, opts:["Rossiya","Ukraina","Belarus","Qozog'iston"], a:0, g:[6,7,8]},
      {q:{uz:"Yer atrofidagi o'rta atmosfera balandligi?", ru:"Средняя высота атмосферы Земли?", en:"Average height of Earth's atmosphere?"}, opts:["~1000 km","~100 km","~500 km","~5000 km"], a:0, g:[9,10,11]},
      {q:{uz:"Afrika qit'asidagi eng uzun daryo?", ru:"Самая длинная река Африки?", en:"Longest river in Africa?"}, opts:["Nil","Kongo","Niger","Zambezi"], a:0, g:[7,8,9]},
      {q:{uz:"Aral dengizi qaysi mamlakatlarda?", ru:"В каких странах Аральское море?", en:"Which countries share the Aral Sea?"}, opts:["O'zbekiston va Qozog'iston","O'zbekiston va Turkmaniston","Qozog'iston va Turkmaniston","O'zbekiston va Tojikiston"], a:0, g:[7,8,9,10]},
      {q:{uz:"Demografiya nima?", ru:"Что такое демография?", en:"What is demography?"}, opts:["Aholi ilmi","Iqtisod ilmi","Tarix ilmi","Siyosat ilmi"], a:0, g:[9,10,11]},
      {q:{uz:"Janubi-Sharqiy Osiyodagi eng katta mamlakat?", ru:"Крупнейшая страна Юго-Восточной Азии?", en:"Largest country in Southeast Asia?"}, opts:["Indoneziya","Tailand","Vetnam","Filippin"], a:0, g:[9,10]},
      {q:{uz:"Qaysi qit'ada eng ko'p davlat bor?", ru:"На каком континенте больше всего стран?", en:"Which continent has the most countries?"}, opts:["Afrika","Osiyo","Yevropa","Amerika"], a:0, g:[8,9,10]},
      {q:{uz:"Yer necha yil oldin paydo bo'lgan?", ru:"Сколько лет назад образовалась Земля?", en:"How old is the Earth?"}, opts:["~4.5 mlrd yil","~1 mlrd yil","~10 mlrd yil","~2 mlrd yil"], a:0, g:[9,10,11]},
      {q:{uz:"SSSR sobiq respublikalari soni?", ru:"Количество бывших республик СССР?", en:"Number of former USSR republics?"}, opts:["15","12","16","14"], a:0, g:[8,9,10]},
      {q:{uz:"Yer yuzasining necha foizi suv?", ru:"Сколько % поверхности Земли покрыто водой?", en:"What % of Earth's surface is water?"}, opts:["71%","50%","60%","80%"], a:0, g:[7,8,9]},
      {q:{uz:"Cho'l iqlimi qanday?", ru:"Каков климат пустыни?", en:"What is desert climate like?"}, opts:["Quruq va issiq","Nam va sovuq","Nam va issiq","Quruq va sovuq"], a:0, g:[6,7,8]},
    ]
  },
  lit: {
    base: [
      {q:{uz:"'O'tkan kunlar' romanini kim yozgan?", ru:"Кто написал роман 'Минувшие дни'?", en:"Who wrote 'Days Gone By'?"}, opts:["Abdulla Qodiriy","Cho'lpon","Oybek","Hamza"], a:0, g:[7,8,9,10,11]},
      {q:{uz:"Navoiy to'liq ismi?", ru:"Полное имя Навои?", en:"Navoi's full name?"}, opts:["Alisher Navoiy","Nizomiddin Navoiy","Husayn Navoiy","Mir Navoiy"], a:0, g:[7,8,9]},
      {q:{uz:"'Shekspir' qaysi mamlakatdan?", ru:"Шекспир — из какой страны?", en:"Shakespeare was from which country?"}, opts:["Angliya","Fransiya","Italiya","Ispaniya"], a:0, g:[8,9,10]},
      {q:{uz:"'Hamlet' asarini kim yozgan?", ru:"Кто написал 'Гамлет'?", en:"Who wrote 'Hamlet'?"}, opts:["Shekspir","Pushkin","Dante","Gёte"], a:0, g:[9,10,11]},
      {q:{uz:"'Xamsa' asarini kim yozgan?", ru:"Кто написал 'Хамсу'?", en:"Who wrote 'Khamsa'?"}, opts:["Navoiy","Jomiy","Nizomiy","Firdavsiy"], a:0, g:[8,9,10]},
      {q:{uz:"'Farhod va Shirin' asarining janri?", ru:"Жанр произведения 'Фархад и Ширин'?", en:"Genre of 'Farhod and Shirin'?"}, opts:["Doston","Qissa","Roman","Hikoya"], a:0, g:[8,9,10]},
      {q:{uz:"'Jinlar bazmi' asarini kim yozgan?", ru:"Кто написал 'Джинн базми'?", en:"Who wrote 'Jinlar Bazmi'?"}, opts:["Abdulla Qahhor","Oybek","Hamza","Said Ahmad"], a:0, g:[8,9]},
      {q:{uz:"Pushkinning 'Yevgeniy Onegin' asarining janri?", ru:"Жанр 'Евгения Онегина' Пушкина?", en:"Genre of Pushkin's 'Eugene Onegin'?"}, opts:["Nazm romani","Qissa","She'r","Drama"], a:0, g:[9,10,11]},
      {q:{uz:"'Don Kixot' asarini kim yozgan?", ru:"Кто написал 'Дон Кихота'?", en:"Who wrote 'Don Quixote'?"}, opts:["Servantes","Shekspir","Gёte","Dante"], a:0, g:[9,10,11]},
      {q:{uz:"O'zbek mumtoz adabiyotida g'azal nima?", ru:"Что такое газель в узбекской поэзии?", en:"What is 'ghazal' in Uzbek poetry?"}, opts:["Lirik she'r shakli","Epik doston","Dramatik asar","Qo'shiq"], a:0, g:[8,9,10]},
      {q:{uz:"'Ikki eshak' masalini kim yozgan?", ru:"Кто написал басню 'Два осла'?", en:"Who wrote the fable 'Two Donkeys'?"}, opts:["Abdulla Qahhor","Navoiy","Muqimiy","Furqat"], a:0, g:[5,6,7]},
      {q:{uz:"'Anna Karenina' asarini kim yozgan?", ru:"Кто написал 'Анну Каренину'?", en:"Who wrote 'Anna Karenina'?"}, opts:["L.Tolstoy","Dostoyevskiy","Chekhov","Turgenev"], a:0, g:[10,11]},
      {q:{uz:"Cho'lponning asl ismi?", ru:"Настоящее имя Чулпана?", en:"Chulpan's real name?"}, opts:["Abdulhamid Sulaymon","Abdulla Oripov","Erkin Vohidov","Hamid Olimjon"], a:0, g:[9,10,11]},
      {q:{uz:"'Devonu lug'otit turk' asarini kim yozgan?", ru:"Кто написал 'Девону лугатит-турк'?", en:"Who wrote 'Divanu Lughat al-Turk'?"}, opts:["Mahmud Koshg'ariy","Yusuf Xos Hojib","Al-Beruniy","Ibn Sino"], a:0, g:[9,10,11]},
      {q:{uz:"'Romeo va Juletta' asarini kim yozgan?", ru:"Кто написал 'Ромео и Джульетту'?", en:"Who wrote 'Romeo and Juliet'?"}, opts:["Shekspir","Dante","Servantes","Gёte"], a:0, g:[8,9,10]},
      {q:{uz:"G'azalning matla' nima?", ru:"Что такое матла в газели?", en:"What is 'matla' in a ghazal?"}, opts:["Birinchi bayt","Oxirgi bayt","Rad","Maqta"], a:0, g:[10,11]},
      {q:{uz:"'Qutadg'u bilig' asarini kim yozgan?", ru:"Кто написал 'Кутадгу билиг'?", en:"Who wrote 'Kutadgu Bilig'?"}, opts:["Yusuf Xos Hojib","Mahmud Koshg'ariy","Navoiy","Al-Beruniy"], a:0, g:[9,10,11]},
      {q:{uz:"Abdulla Oripovning mashhur she'ri?", ru:"Известное стихотворение Абдуллы Орипова?", en:"Famous poem by Abdulla Oripov?"}, opts:["O'zbekiston","Vatan","Ona","Ona tili"], a:0, g:[6,7,8]},
      {q:{uz:"'Iliada' asarini kim yozgan?", ru:"Кто написал 'Илиаду'?", en:"Who wrote 'Iliad'?"}, opts:["Gomer","Aristotel","Platon","Sofokl"], a:0, g:[9,10,11]},
      {q:{uz:"Erkin Vohidov kimligini tanlang:", ru:"Кем является Эркин Вохидов?", en:"Erkin Vohidov is a/an:"}, opts:["Shoir","Rassom","Kompozitor","Dramaturg"], a:0, g:[7,8,9]},
      {q:{uz:"'Sariq devni minib' asarini kim yozgan?", ru:"Кто написал 'Sariq devni minib'?", en:"Who wrote 'Riding the Yellow Devil'?"}, opts:["Xudoyberdiy To'xtaboyev","Mirmuhsin","Said Ahmad","Primqul Qodirov"], a:0, g:[5,6,7]},
      {q:{uz:"She'rda rim nima?", ru:"Что такое рифма в стихе?", en:"What is rhyme in poetry?"}, opts:["Ohangdosh so'z oxirlari","She'r mazmuni","She'r turi","Vazn"], a:0, g:[6,7,8]},
      {q:{uz:"'Jinoyat va jazo' asarini kim yozgan?", ru:"Кто написал 'Преступление и наказание'?", en:"Who wrote 'Crime and Punishment'?"}, opts:["Dostoyevskiy","Tolstoy","Chekhov","Turgenev"], a:0, g:[10,11]},
      {q:{uz:"Badiiy adabiyotning asosiy janrlari?", ru:"Основные жанры художественной литературы?", en:"Main genres of fiction?"}, opts:["Epik, lirik, dramatik","Roman, she'r, qissa","Doston, hikoya, drama","Mashhur, klassik, zamonaviy"], a:0, g:[9,10,11]},
      {q:{uz:"'Mehrobdan chayon' asarini kim yozgan?", ru:"Кто написал 'Скорпион из алтаря'?", en:"Who wrote 'Scorpion from the Altar'?"}, opts:["Abdulla Qodiriy","Cho'lpon","Oybek","Hamza"], a:0, g:[9,10,11]},
    ]
  }
};

// ===================== STATE =====================
let lang = 'uz';
let selectedGrade = null;
let selectedSubject = null;
let currentQuestions = [];
let currentQ = 0;
let score = 0;
let answered = false;

// ===================== INIT =====================
function setLang(l) {
  lang = l;
  document.querySelectorAll('.lang-btn').forEach((b,i) => {
    b.classList.toggle('active', ['uz','ru','en'][i] === l);
  });
  applyLang();
  renderGrades();
  renderSubjects();
}

function applyLang() {
  const t = T[lang];
  document.getElementById('hTitle').textContent = t.hTitle;
  document.getElementById('hSub').textContent = t.hSub;
  document.getElementById('txt_grade').textContent = t.txt_grade;
  document.getElementById('txt_subject').textContent = t.txt_subject;
  document.getElementById('startBtn').textContent = t.txt_start;
  document.getElementById('txt_correct2').textContent = t.txt_correct2;
  document.getElementById('txt_wrong2').textContent = t.txt_wrong2;
  document.getElementById('txt_retry').textContent = t.txt_retry;
  document.getElementById('txt_home').textContent = t.txt_home;
  document.getElementById('nextBtn').textContent = t.nextBtn;
}

function renderGrades() {
  const grid = document.getElementById('gradeGrid');
  grid.innerHTML = '';
  for (let g = 5; g <= 11; g++) {
    const btn = document.createElement('button');
    btn.className = 'grade-btn' + (selectedGrade === g ? ' selected' : '');
    btn.innerHTML = `${g}<span>${T[lang].sinf}</span>`;
    btn.onclick = () => selectGrade(g);
    grid.appendChild(btn);
  }
}

function renderSubjects() {
  const grid = document.getElementById('subjectGrid');
  grid.innerHTML = '';
  subjects[lang].forEach(s => {
    const btn = document.createElement('button');
    btn.className = 'subject-btn' + (selectedSubject === s.id ? ' selected' : '');
    btn.innerHTML = `<span class="icon">${s.icon}</span>${s.name}`;
    btn.onclick = () => selectSubject(s.id);
    grid.appendChild(btn);
  });
}

function selectGrade(g) {
  selectedGrade = g;
  renderGrades();
  checkStartReady();
}

function selectSubject(id) {
  selectedSubject = id;
  renderSubjects();
  checkStartReady();
}

function checkStartReady() {
  document.getElementById('startBtn').disabled = !(selectedGrade && selectedSubject);
}

// ===================== QUIZ LOGIC =====================
function startQuiz() {
  const pool = QDB[selectedSubject].base;
  // Filter by grade (questions with g array containing selected grade)
  let filtered = pool.filter(q => q.g.includes(selectedGrade));
  // If not enough, use all
  if (filtered.length < 10) filtered = pool;
  // Shuffle and take 25 (or all if less)
  currentQuestions = shuffle([...filtered]).slice(0, 25);
  // Pad if needed with shuffled full pool
  if (currentQuestions.length < 25) {
    const extra = shuffle([...pool]).filter(q => !currentQuestions.includes(q));
    currentQuestions = [...currentQuestions, ...extra].slice(0, 25);
  }
  currentQ = 0; score = 0;
  showScreen('quizScreen');
  loadQuestion();
}

function shuffle(arr) {
  for (let i = arr.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [arr[i], arr[j]] = [arr[j], arr[i]];
  }
  return arr;
}

function loadQuestion() {
  const q = currentQuestions[currentQ];
  const total = currentQuestions.length;
  const t = T[lang];

  // Header
  const subj = subjects[lang].find(s => s.id === selectedSubject);
  document.getElementById('quizTitle').textContent = subj ? subj.name : '';
  document.getElementById('quizSubtitle').textContent = `${selectedGrade}-${t.sinf}`;
  document.getElementById('qCounter').textContent = `${currentQ+1}/${total}`;
  document.getElementById('progressFill').style.width = `${((currentQ+1)/total)*100}%`;
  document.getElementById('qNum').textContent = `${t.qWord} ${currentQ+1}`;
  document.getElementById('qText').textContent = q.q[lang];

  // Options - shuffle options but track correct
  const letters = ['A','B','C','D'];
  const indices = [0,1,2,3];
  const shuffled = shuffle([...indices]);
  const correctOriginal = q.a;
  let correctShuffledIdx = shuffled.indexOf(correctOriginal);

  const container = document.getElementById('optionsContainer');
  container.innerHTML = '';
  shuffled.forEach((origIdx, i) => {
    const btn = document.createElement('button');
    btn.className = 'option-btn';
    btn.innerHTML = `<span class="option-letter">${letters[i]}</span>${q.opts[origIdx]}`;
    btn.onclick = () => selectAnswer(i, correctShuffledIdx);
    container.appendChild(btn);
  });

  document.getElementById('nextBtn').classList.remove('show');
  answered = false;
}

function selectAnswer(chosen, correct) {
  if (answered) return;
  answered = true;
  const btns = document.querySelectorAll('.option-btn');
  btns.forEach((b, i) => {
    b.disabled = true;
    if (i === correct) b.classList.add('correct');
    else if (i === chosen && chosen !== correct) b.classList.add('wrong');
  });
  if (chosen === correct) score++;
  document.getElementById('nextBtn').classList.add('show');
}

function nextQuestion() {
  currentQ++;
  if (currentQ >= currentQuestions.length) {
    showResult();
  } else {
    loadQuestion();
  }
}

function showResult() {
  showScreen('resultScreen');
  const total = currentQuestions.length;
  const pct = score / total;
  const t = T[lang];
  const subj = subjects[lang].find(s => s.id === selectedSubject);

  document.getElementById('resultScore').textContent = `${score}/${total}`;
  document.getElementById('resultGradeInfo').textContent = `${selectedGrade}-${t.sinf} • ${subj ? subj.name : ''}`;

  let emoji, labelIdx;
  if (pct >= 0.9) { emoji='🏆'; labelIdx=0; }
  else if (pct >= 0.7) { emoji='👍'; labelIdx=1; }
  else if (pct >= 0.5) { emoji='😐'; labelIdx=2; }
  else { emoji='😔'; labelIdx=3; }

  document.getElementById('resultEmoji').textContent = emoji;
  document.getElementById('resultLabel').textContent = t.resultLabel[labelIdx];
  document.getElementById('barCorrect').style.width = `${(score/total)*100}%`;
  document.getElementById('barWrong').style.width = `${((total-score)/total)*100}%`;
  document.getElementById('barCNum').textContent = score;
  document.getElementById('barWNum').textContent = total - score;
}

function retryQuiz() { startQuiz(); }

function goHome() {
  showScreen('homeScreen');
  selectedGrade = null; selectedSubject = null;
  renderGrades(); renderSubjects();
  checkStartReady();
}

function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

// Init
renderGrades();
renderSubjects();
applyLang();
</script>
</body>
</html>
