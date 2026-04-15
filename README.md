
<html lang="en" class="h-full">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SpeakUP English</title>
  <link
    href="https://fonts.googleapis.com/css2?family=Sora:wght@300;400;500;600;700;800&family=Space+Mono:wght@400;700&display=swap"
    rel="stylesheet">
  <style>
    :root {
      --primary: #4f46e5;
      --primary-light: #818cf8;
      --primary-dark: #3730a3;
      --accent: #f59e0b;
      --accent2: #10b981;
      --danger: #ef4444;
      --bg: #0a0a14;
      --bg2: #111120;
      --bg3: #1a1a2e;
      --surface: #1e1e38;
      --surface2: #252548;
      --border: rgba(255, 255, 255, 0.07);
      --text: #f0f0ff;
      --text2: #9090b8;
      --text3: #5050a0;
      --radius: 16px;
      --radius-sm: 10px;
      --glow: 0 0 24px rgba(79, 70, 229, 0.35);
      --glow2: 0 0 40px rgba(79, 70, 229, 0.15);
    }

    *,
    *::before,
    *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0
    }

    html,
    body {
      height: 100%;
      overflow: hidden;
      font-family: 'Sora', sans-serif;
      background: var(--bg);
      color: var(--text)
    }

    ::-webkit-scrollbar {
      width: 4px
    }

    ::-webkit-scrollbar-track {
      background: transparent
    }

    ::-webkit-scrollbar-thumb {
      background: var(--surface2);
      border-radius: 99px
    }

    #app {
      height: 100vh;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      background: radial-gradient(ellipse at 20% 0%, rgba(79, 70, 229, 0.08) 0%, transparent 60%), radial-gradient(ellipse at 80% 100%, rgba(129, 140, 248, 0.05) 0%, transparent 60%), var(--bg)
    }

    /* HEADER */
    header {
      background: rgba(17, 17, 32, 0.9);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      padding: 10px 16px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-shrink: 0;
      z-index: 10;
      position: relative
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 10px
    }

    .logo-icon {
      width: 34px;
      height: 34px;
      background: linear-gradient(135deg, var(--primary), var(--primary-light));
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 17px;
      box-shadow: var(--glow)
    }

    .logo-text {
      font-size: 17px;
      font-weight: 800;
      letter-spacing: -0.5px;
      background: linear-gradient(135deg, #fff 30%, var(--primary-light));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent
    }

    .logo-text span {
      background: linear-gradient(135deg, var(--primary-light), var(--accent));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 8px
    }

    .xp-badge {
      display: flex;
      align-items: center;
      gap: 5px;
      background: rgba(245, 158, 11, 0.12);
      border: 1px solid rgba(245, 158, 11, 0.25);
      border-radius: 99px;
      padding: 5px 11px;
      font-size: 12px;
      font-weight: 700;
      color: var(--accent)
    }

    .streak-badge {
      display: flex;
      align-items: center;
      gap: 4px;
      background: rgba(239, 68, 68, 0.1);
      border: 1px solid rgba(239, 68, 68, 0.2);
      border-radius: 99px;
      padding: 5px 9px;
      font-size: 12px;
      font-weight: 700;
      color: #fc8181
    }

    select.lang-sel {
      background: var(--surface);
      color: var(--text);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 5px 8px;
      font-size: 11px;
      font-family: 'Sora', sans-serif;
      cursor: pointer;
      outline: none
    }

    /* NAV */
    nav {
      background: rgba(17, 17, 32, 0.8);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border);
      display: flex;
      gap: 2px;
      padding: 6px 8px;
      overflow-x: auto;
      flex-shrink: 0
    }

    nav::-webkit-scrollbar {
      height: 0
    }

    .nav-btn {
      display: flex;
      align-items: center;
      gap: 5px;
      padding: 6px 12px;
      border-radius: 8px;
      border: none;
      background: transparent;
      color: var(--text2);
      font-family: 'Sora', sans-serif;
      font-size: 11px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s;
      white-space: nowrap
    }

    .nav-btn:hover {
      background: var(--surface);
      color: var(--text)
    }

    .nav-btn.active {
      background: var(--primary);
      color: #fff;
      box-shadow: var(--glow)
    }

    /* MAIN */
    main {
      flex: 1;
      overflow-y: auto;
      padding: 16px
    }

    /* CARDS */
    .card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 18px;
      transition: border-color 0.2s
    }

    .card:hover {
      border-color: rgba(79, 70, 229, 0.25)
    }

    .card-sm {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 13px 15px;
      cursor: pointer;
      transition: all 0.2s
    }

    .card-sm:hover {
      background: var(--surface2);
      border-color: rgba(79, 70, 229, 0.35);
      transform: translateY(-1px);
      box-shadow: 0 4px 16px rgba(0, 0, 0, 0.4)
    }

    .grid-2 {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px
    }

    .grid-3 {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px
    }

    @media(max-width:600px) {

      .grid-2,
      .grid-3 {
        grid-template-columns: 1fr
      }
    }

    .section-title {
      font-size: 20px;
      font-weight: 800;
      margin-bottom: 5px;
      letter-spacing: -0.5px
    }

    .section-sub {
      color: var(--text2);
      font-size: 12px;
      margin-bottom: 16px
    }

    .pill {
      display: inline-flex;
      align-items: center;
      gap: 3px;
      padding: 3px 9px;
      border-radius: 99px;
      font-size: 10px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.5px
    }

    .pill-purple {
      background: rgba(79, 70, 229, 0.18);
      color: var(--primary-light)
    }

    .pill-green {
      background: rgba(16, 185, 129, 0.18);
      color: #34d399
    }

    .pill-amber {
      background: rgba(245, 158, 11, 0.18);
      color: var(--accent)
    }

    .pill-red {
      background: rgba(239, 68, 68, 0.18);
      color: #fc8181
    }

    .pill-blue {
      background: rgba(59, 130, 246, 0.18);
      color: #60a5fa
    }

    /* BUTTONS */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      padding: 9px 18px;
      border-radius: var(--radius-sm);
      border: none;
      font-family: 'Sora', sans-serif;
      font-weight: 700;
      font-size: 13px;
      cursor: pointer;
      transition: all 0.2s
    }

    .btn-primary {
      background: var(--primary);
      color: #fff;
      box-shadow: var(--glow)
    }

    .btn-primary:hover {
      background: var(--primary-dark);
      transform: translateY(-1px)
    }

    .btn-outline {
      background: transparent;
      color: var(--text2);
      border: 1px solid var(--border)
    }

    .btn-outline:hover {
      background: var(--surface);
      color: var(--text)
    }

    .btn-accent {
      background: var(--accent);
      color: #1a1000
    }

    .btn-success {
      background: var(--accent2);
      color: #fff
    }

    .btn-danger {
      background: var(--danger);
      color: #fff
    }

    .btn:disabled {
      opacity: 0.5;
      cursor: not-allowed
    }

    /* QUIZ */
    .quiz-opt {
      width: 100%;
      text-align: left;
      padding: 13px 16px;
      background: var(--surface);
      border: 1.5px solid var(--border);
      border-radius: var(--radius-sm);
      color: var(--text);
      font-family: 'Sora', sans-serif;
      font-size: 13px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.15s;
      margin-bottom: 7px;
      display: flex;
      align-items: center;
      gap: 10px
    }

    .quiz-opt:hover:not(.disabled) {
      background: var(--surface2);
      border-color: var(--primary-light);
      transform: translateX(3px)
    }

    .quiz-opt.correct {
      background: rgba(16, 185, 129, 0.15) !important;
      border-color: var(--accent2) !important;
      color: #34d399 !important
    }

    .quiz-opt.wrong {
      background: rgba(239, 68, 68, 0.12) !important;
      border-color: var(--danger) !important;
      color: #fc8181 !important
    }

    .quiz-opt.disabled {
      pointer-events: none
    }

    .opt-letter {
      font-family: 'Space Mono', monospace;
      font-size: 11px;
      color: var(--text3);
      background: var(--bg);
      border-radius: 4px;
      padding: 1px 5px;
      flex-shrink: 0
    }

    /* PROGRESS */
    .progress-track {
      height: 5px;
      background: var(--surface);
      border-radius: 99px;
      overflow: hidden
    }

    .progress-fill {
      height: 100%;
      background: linear-gradient(90deg, var(--primary), var(--primary-light));
      border-radius: 99px;
      transition: width 0.5s ease
    }

    /* CHAT */
    .chat-wrap {
      display: flex;
      flex-direction: column;
      height: calc(100vh - 155px)
    }

    .chat-msgs {
      flex: 1;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      gap: 10px;
      padding-bottom: 10px
    }

    .chat-msg-ai,
    .chat-msg-user {
      max-width: 82%;
      padding: 11px 15px;
      border-radius: 14px;
      font-size: 13px;
      line-height: 1.65;
      animation: msgIn 0.3s ease
    }

    .chat-msg-ai {
      background: var(--surface);
      border: 1px solid var(--border);
      border-bottom-left-radius: 4px;
      align-self: flex-start
    }

    .chat-msg-user {
      background: var(--primary);
      border-bottom-right-radius: 4px;
      align-self: flex-end
    }

    .chat-input-row {
      display: flex;
      gap: 8px;
      margin-top: 10px
    }

    .chat-input {
      flex: 1;
      background: var(--surface);
      border: 1.5px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 11px 14px;
      color: var(--text);
      font-family: 'Sora', sans-serif;
      font-size: 13px;
      outline: none;
      transition: border-color 0.2s
    }

    .chat-input:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.1)
    }

    /* VOCAB */
    .vocab-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 13px;
      transition: all 0.2s;
      cursor: pointer
    }

    .vocab-card:hover {
      border-color: rgba(79, 70, 229, 0.35);
      transform: translateY(-2px);
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3)
    }

    .vocab-en {
      font-size: 15px;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 3px
    }

    .vocab-tr {
      font-size: 11px;
      color: var(--text2);
      margin-top: 2px
    }

    .vocab-cat {
      font-size: 9px;
      color: var(--text3);
      text-transform: uppercase;
      letter-spacing: 0.5px;
      margin-top: 5px
    }

    /* SCORE */
    .score-big {
      font-size: 68px;
      font-weight: 800;
      font-family: 'Space Mono', monospace;
      background: linear-gradient(135deg, var(--primary-light), var(--accent));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      line-height: 1
    }

    .stat-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 18px;
      text-align: center
    }

    .stat-num {
      font-size: 32px;
      font-weight: 800;
      font-family: 'Space Mono', monospace;
      color: var(--primary-light)
    }

    .stat-label {
      font-size: 11px;
      color: var(--text2);
      margin-top: 3px
    }

    /* TYPING */
    .typing-dot {
      display: inline-block;
      width: 5px;
      height: 5px;
      background: var(--primary-light);
      border-radius: 50%;
      animation: typingBounce 1s infinite;
      margin: 0 2px
    }

    .typing-dot:nth-child(2) {
      animation-delay: 0.2s
    }

    .typing-dot:nth-child(3) {
      animation-delay: 0.4s
    }

    @keyframes typingBounce {

      0%,
      80%,
      100% {
        transform: translateY(0)
      }

      40% {
        transform: translateY(-5px)
      }
    }

    @keyframes msgIn {
      from {
        opacity: 0;
        transform: translateY(7px)
      }

      to {
        opacity: 1;
        transform: translateY(0)
      }
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(10px)
      }

      to {
        opacity: 1;
        transform: translateY(0)
      }
    }

    .fade-in {
      animation: fadeIn 0.3s ease forwards
    }

    /* TOPIC CARD */
    .topic-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 16px;
      cursor: pointer;
      transition: all 0.2s;
      position: relative;
      overflow: hidden
    }

    .topic-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--primary), var(--primary-light));
      opacity: 0;
      transition: opacity 0.2s
    }

    .topic-card:hover::before {
      opacity: 1
    }

    .topic-card:hover {
      border-color: rgba(79, 70, 229, 0.3);
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35)
    }

    .topic-num {
      font-family: 'Space Mono', monospace;
      font-size: 10px;
      color: var(--text3);
      margin-bottom: 6px
    }

    .topic-name {
      font-size: 14px;
      font-weight: 700;
      margin-bottom: 5px
    }

    .topic-bar {
      margin-top: 8px
    }

    .level-chip {
      display: inline-block;
      padding: 2px 7px;
      border-radius: 99px;
      font-size: 9px;
      font-weight: 700
    }

    .level-0 {
      background: rgba(16, 185, 129, 0.18);
      color: #34d399
    }

    .level-1 {
      background: rgba(59, 130, 246, 0.18);
      color: #60a5fa
    }

    .level-2 {
      background: rgba(245, 158, 11, 0.18);
      color: #fbbf24
    }

    .level-3 {
      background: rgba(239, 68, 68, 0.18);
      color: #f87171
    }

    .level-4 {
      background: rgba(168, 85, 247, 0.18);
      color: #c084fc
    }

    /* RESULT ITEM */
    .result-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 11px 14px;
      background: var(--surface);
      border-radius: var(--radius-sm);
      border: 1px solid var(--border);
      margin-bottom: 7px;
      font-size: 12px
    }

    /* READING */
    .reading-text {
      background: var(--surface);
      border-left: 3px solid var(--primary);
      border-radius: 0 var(--radius-sm) var(--radius-sm) 0;
      padding: 15px 18px;
      font-size: 13px;
      line-height: 1.85;
      color: var(--text2);
      margin-bottom: 18px
    }

    /* SEARCH */
    .search-input {
      width: 100%;
      background: var(--surface);
      border: 1.5px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 10px 14px;
      color: var(--text);
      font-family: 'Sora', sans-serif;
      font-size: 13px;
      outline: none;
      transition: border-color 0.2s;
      margin-bottom: 12px
    }

    .search-input:focus {
      border-color: var(--primary)
    }

    /* SPEAK */
    .speak-prompt-box {
      background: linear-gradient(135deg, rgba(79, 70, 229, 0.12), rgba(129, 140, 248, 0.06));
      border: 1px solid rgba(79, 70, 229, 0.25);
      border-radius: var(--radius);
      padding: 22px;
      text-align: center;
      margin-bottom: 18px
    }

    .speak-prompt-text {
      font-size: 19px;
      font-weight: 700;
      margin-bottom: 7px
    }

    .speak-hint {
      font-size: 12px;
      color: var(--text2)
    }

    /* LB */
    .lb-row {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 11px 14px;
      background: var(--surface);
      border-radius: var(--radius-sm);
      border: 1px solid var(--border);
      margin-bottom: 7px
    }

    .lb-rank {
      font-family: 'Space Mono', monospace;
      font-size: 13px;
      font-weight: 700;
      width: 26px;
      text-align: center
    }

    .lb-name {
      flex: 1;
      font-weight: 600;
      font-size: 13px
    }

    .lb-score {
      font-family: 'Space Mono', monospace;
      font-size: 12px;
      color: var(--primary-light)
    }

    /* QUICK TIPS CHIPS */
    .tip-chip {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 6px 12px;
      font-size: 12px;
      cursor: pointer;
      transition: all 0.2s;
      margin: 3px
    }

    .tip-chip:hover {
      background: var(--surface2);
      border-color: rgba(79, 70, 229, 0.35);
      color: var(--primary-light)
    }

    /* AI SUGGESTIONS */
    .ai-suggest {
      display: flex;
      gap: 6px;
      flex-wrap: wrap;
      margin-bottom: 12px
    }

    /* DAILY WORD */
    .daily-word-card {
      background: linear-gradient(135deg, rgba(79, 70, 229, 0.18), rgba(245, 158, 11, 0.1));
      border: 1px solid rgba(79, 70, 229, 0.3);
      border-radius: var(--radius);
      padding: 20px;
      margin-bottom: 16px;
      position: relative;
      overflow: hidden
    }

    .daily-word-card::after {
      content: '✨';
      position: absolute;
      right: 16px;
      top: 50%;
      transform: translateY(-50%);
      font-size: 32px;
      opacity: 0.3
    }

    /* EMPTY STATE */
    .empty-state {
      text-align: center;
      padding: 50px 20px;
      color: var(--text3)
    }

    .empty-state .icon {
      font-size: 44px;
      margin-bottom: 10px
    }

    /* GRAMMAR PANEL */
    .grammar-info {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 16px;
      margin-bottom: 16px
    }

    .grammar-info pre {
      white-space: pre-wrap;
      font-family: 'Sora', sans-serif;
      font-size: 13px;
      line-height: 1.85;
      color: var(--text2)
    }

    /* BADGE POPUP */
    @keyframes badgePop {
      0% {
        transform: scale(0.5) translateY(20px);
        opacity: 0
      }

      70% {
        transform: scale(1.1)
      }

      100% {
        transform: scale(1) translateY(0);
        opacity: 1
      }
    }

    .badge-popup {
      position: fixed;
      top: 80px;
      right: 16px;
      background: linear-gradient(135deg, var(--primary), var(--primary-light));
      color: #fff;
      border-radius: 12px;
      padding: 12px 18px;
      font-size: 13px;
      font-weight: 700;
      z-index: 999;
      animation: badgePop 0.5s ease forwards;
      box-shadow: var(--glow)
    }

    /* TABS INDICATOR */
    .tab-count {
      display: inline-block;
      background: rgba(255, 255, 255, 0.2);
      border-radius: 99px;
      padding: 1px 5px;
      font-size: 9px;
      margin-left: 3px
    }
  </style>
</head>

<body>
  <div id="app">
    <header>
      <div class="logo">
        <div class="logo-icon">🗣️</div>
        <div class="logo-text">SpeakUP <span>English</span></div>
      </div>
      <div class="header-right">
        <div class="xp-badge">⚡ <span id="xpCount">0</span> XP</div>
        <div class="streak-badge">🔥 <span id="streakCount">0</span></div>
        <select class="lang-sel" id="langSel" onchange="changeLang(this.value)">
          <option value="en">🇬🇧 EN</option>
          <option value="ru">🇷🇺 RU</option>
          <option value="uz">🇺🇿 UZ</option>
          <option value="tj">🇹🇯 TJ</option>
        </select>
      </div>
    </header>
    <nav id="navBar"></nav>
    <main id="mainContent"></main>
  </div>

  <script>
    // ============================================================
    // TRANSLATIONS
    // ============================================================
    const LANGS = {
      en: {
        tabs: ['Home', 'Lessons', 'Listening', 'Reading', 'Speaking', 'Vocabulary', 'AI Tutor', 'Stats'],
        tabIcons: ['🏠', '📖', '🎧', '📰', '🎤', '📚', '🤖', '📊'],
        start: 'Start Quiz', back: 'Back', next: 'Next', submit: 'Submit',
        question: 'Question', of: 'of', correct: 'Correct!', wrong: 'Wrong!',
        yourScore: 'Your Score', tryAgain: 'Try Again', listenAgain: 'Listen Again',
        play: 'Play Audio', record: 'Answer', vocabSearch: 'Search words...',
        aiPlaceholder: 'Ask me anything about English...', aiSend: 'Send',
        aiWelcome: "Hi! I'm your English AI tutor powered by Claude. Ask me about grammar, vocabulary, pronunciation, writing tips, or get your text corrected! 🎓",
        statsTitle: 'Your Progress', noStats: 'No results yet. Complete some quizzes!',
        totalTests: 'Tests Done', avgScore: 'Avg Score', bestScore: 'Best Score',
        lessonSelect: 'Choose a grammar topic:', readingSelect: 'Choose a reading passage:',
        listenSelect: 'Choose a listening exercise:',
        speakTitle: 'Speaking Practice', speakInstr: 'Listen to the question, write your answer, get AI feedback.',
        levels: ['Beginner', 'Elementary', 'Intermediate', 'Upper-Int', 'Advanced'],
        topics: ['Present Simple', 'Past Simple', 'Future Simple', 'Present Continuous', 'Past Continuous', 'Present Perfect', 'Modal Verbs', 'Conditionals', 'Passive Voice', 'Articles', 'Comparatives', 'Prepositions', 'Reported Speech', 'Relative Clauses', 'Phrasal Verbs', 'Past Perfect', 'Future Continuous', 'Gerunds & Infinitives', 'Question Tags', 'Wish & If Only'],
        noResults: 'No results',
        dailyWord: 'Word of the Day',
        quickPractice: 'Quick Practice',
        continueLesson: 'Continue',
        startJourney: 'Your Learning Journey',
        totalWords: 'Words',
        tipTitle: 'Grammar Tip',
      },
      ru: {
        tabs: ['Главная', 'Уроки', 'Аудирование', 'Чтение', 'Говорение', 'Словарь', 'ИИ Репетитор', 'Статистика'],
        tabIcons: ['🏠', '📖', '🎧', '📰', '🎤', '📚', '🤖', '📊'],
        start: 'Начать тест', back: 'Назад', next: 'Далее', submit: 'Отправить',
        question: 'Вопрос', of: 'из', correct: 'Правильно!', wrong: 'Неправильно!',
        yourScore: 'Ваш балл', tryAgain: 'Ещё раз', listenAgain: 'Слушать снова',
        play: 'Воспроизвести', record: 'Ответить', vocabSearch: 'Поиск слов...',
        aiPlaceholder: 'Спросите об английском языке...', aiSend: 'Отправить',
        aiWelcome: 'Привет! Я ваш ИИ-репетитор по английскому. Спросите о грамматике, словах, произношении или получите исправление текста! 🎓',
        statsTitle: 'Ваш прогресс', noStats: 'Пока нет результатов. Пройдите тесты!',
        totalTests: 'Тестов', avgScore: 'Средний балл', bestScore: 'Лучший балл',
        lessonSelect: 'Выберите тему грамматики:', readingSelect: 'Выберите текст:', listenSelect: 'Выберите упражнение:',
        speakTitle: 'Практика речи', speakInstr: 'Прослушайте вопрос, напишите ответ, получите обратную связь от ИИ.',
        levels: ['Начальный', 'Элементарный', 'Средний', 'Выше среднего', 'Продвинутый'],
        topics: ['Настоящее простое', 'Прошедшее простое', 'Будущее простое', 'Наст. длительное', 'Прош. длительное', 'Наст. совершённое', 'Модальные глаголы', 'Условные предложения', 'Страдательный залог', 'Артикли', 'Сравнительные степени', 'Предлоги', 'Косвенная речь', 'Придаточные предложения', 'Фразовые глаголы', 'Прошедшее совершённое', 'Буд. длительное', 'Герундий и инфинитив', 'Разделительные вопросы', 'Wish и If Only'],
        noResults: 'Нет результатов',
        dailyWord: 'Слово дня',
        quickPractice: 'Быстрая практика',
        continueLesson: 'Продолжить',
        startJourney: 'Ваш путь обучения',
        totalWords: 'Слова',
        tipTitle: 'Совет по грамматике',
      },
      uz: {
        tabs: ['Bosh sahifa', 'Darslar', 'Tinglash', "O'qish", 'Gapirish', "Lug'at", 'AI Muallim', 'Statistika'],
        tabIcons: ['🏠', '📖', '🎧', '📰', '🎤', '📚', '🤖', '📊'],
        start: 'Testni boshlash', back: 'Orqaga', next: 'Keyingi', submit: 'Yuborish',
        question: 'Savol', of: 'dan', correct: "To'g'ri!", wrong: "Noto'g'ri!",
        yourScore: 'Natijangiz', tryAgain: 'Qayta urinish', listenAgain: 'Qayta tinglash',
        play: 'Ijro etish', record: 'Javob berish', vocabSearch: "So'z qidirish...",
        aiPlaceholder: "Ingliz tili haqida so'rang...", aiSend: 'Yuborish',
        aiWelcome: "Salom! Men AI-muallim bo'lib, ingliz tilini o'rganishga yordam beraman. Grammatika, so'zlar, talaffuz haqida so'rang! 🎓",
        statsTitle: 'Sizning natijangiz', noStats: "Hali natijalar yo'q. Testlarni bajaring!",
        totalTests: 'Testlar', avgScore: "O'rtacha ball", bestScore: 'Eng yaxshi ball',
        lessonSelect: 'Grammatika mavzusini tanlang:', readingSelect: 'Matnni tanlang:', listenSelect: "Mashqni tanlang:",
        speakTitle: 'Gapirish mashqi', speakInstr: "Savolni tinglang, javobingizni yozing, AI fikrlarini oling.",
        levels: ["Boshlang'ich", 'Elementar', "O'rta", "Yuqori o'rta", "Ilg'or"],
        topics: ['Present Simple', 'Past Simple', 'Future Simple', 'Present Continuous', 'Past Continuous', 'Present Perfect', "Modal fe'llar", 'Shartli gaplar', 'Passiv nisbat', 'Artikllar', 'Qiyoslash darajalari', 'Predloglar', 'Egri nutq', 'Nisbiy gaplar', "Frazeologik fe'llar", 'Past Perfect', 'Future Continuous', "Gerundiy va infinitiv", 'Ajratuvchi savollar', 'Wish va If Only'],
        noResults: "Natijalar yo'q",
        dailyWord: 'Kunlik so\'z',
        quickPractice: 'Tezkor mashq',
        continueLesson: 'Davom etish',
        startJourney: "Sizning o'quv yo'lingiz",
        totalWords: "So'zlar",
        tipTitle: 'Grammatika maslahati',
      },
      tj: {
        tabs: ['Хона', 'Дарсҳо', 'Гӯш кардан', 'Хондан', 'Гуфтугӯ', 'Луғат', 'ИИ Муаллим', 'Омор'],
        tabIcons: ['🏠', '📖', '🎧', '📰', '🎤', '📚', '🤖', '📊'],
        start: 'Санҷишро оғоз кунед', back: 'Бозгашт', next: 'Навбатӣ', submit: 'Фиристодан',
        question: 'Савол', of: 'аз', correct: 'Дуруст!', wrong: 'Нодуруст!',
        yourScore: 'Натиҷаи шумо', tryAgain: 'Аз нав кӯшиш кунед', listenAgain: 'Аз нав гӯш кунед',
        play: 'Пахш кунед', record: 'Ҷавоб диҳед', vocabSearch: 'Ҷустуҷӯи калима...',
        aiPlaceholder: 'Дар бораи забони англисӣ пурсед...', aiSend: 'Фиристодан',
        aiWelcome: 'Салом! Ман ёрдамчии ИИ шумо барои омӯзиши забони англисӣ ҳастам. Дар бораи грамматика, луғат ва талаффуз пурсед! 🎓',
        statsTitle: 'Пешрафти шумо', noStats: 'Ҳоло натиҷаҳо нест. Санҷишҳоро гузаред!',
        totalTests: 'Санҷишҳо', avgScore: 'Бали миёна', bestScore: 'Беҳтарин балл',
        lessonSelect: 'Мавзӯи грамматикаро интихоб кунед:', readingSelect: 'Матнро интихоб кунед:', listenSelect: 'Машқро интихоб кунед:',
        speakTitle: 'Машқи гуфтугӯ', speakInstr: 'Саволро гӯш кунед, ҷавоб нависед, баҳои ИИ гиред.',
        levels: ['Ибтидоӣ', 'Элементарӣ', 'Миёна', 'Болои миёна', 'Пешрафта'],
        topics: ['Present Simple', 'Past Simple', 'Future Simple', 'Present Continuous', 'Past Continuous', 'Present Perfect', 'Феълҳои модалӣ', 'Ҷумлаҳои шартӣ', 'Нидои маҷҳул', 'Артиклҳо', 'Дараҷаҳои муқоиса', 'Пешоянд', 'Нутқи ғайримустақим', 'Ҷумлаҳои нисбӣ', 'Феълҳои фразеологӣ', 'Past Perfect', 'Future Continuous', 'Герундий ва инфинитив', 'Саволҳои тасдиқӣ', 'Wish ва If Only'],
        noResults: 'Натиҷаҳо нест',
        dailyWord: 'Калимаи рӯз',
        quickPractice: 'Машқи зуд',
        continueLesson: 'Идома додан',
        startJourney: 'Роҳи омӯзиши шумо',
        totalWords: 'Калимаҳо',
        tipTitle: 'Маслиҳати грамматикӣ',
      }
    };

    // ============================================================
    // GRAMMAR QUESTIONS — 50 per topic (20 topics)
    // ============================================================
    const QUESTIONS = {
      'Present Simple': [
        { q: "She ___ to school every day.", o: ["go", "goes", "going", "gone"], a: 1 },
        { q: "They ___ football on Sundays.", o: ["plays", "play", "playing", "played"], a: 1 },
        { q: "He ___ not like coffee.", o: ["do", "does", "is", "are"], a: 1 },
        { q: "___ you speak English?", o: ["Do", "Does", "Are", "Is"], a: 0 },
        { q: "The sun ___ in the east.", o: ["rise", "rises", "rising", "rose"], a: 1 },
        { q: "My mother ___ breakfast every morning.", o: ["cook", "cooks", "cooked", "cooking"], a: 1 },
        { q: "Water ___ at 100°C.", o: ["boil", "boils", "boiled", "boiling"], a: 1 },
        { q: "I ___ to music every evening.", o: ["listen", "listens", "listening", "listened"], a: 0 },
        { q: "She ___ three languages fluently.", o: ["speak", "speaks", "spoke", "speaking"], a: 1 },
        { q: "The train ___ at 9 AM.", o: ["leave", "leaves", "leaving", "left"], a: 1 },
        { q: "Dogs ___ faithful animals.", o: ["is", "am", "are", "be"], a: 2 },
        { q: "He always ___ his homework.", o: ["do", "does", "did", "done"], a: 1 },
        { q: "We ___ in a big city.", o: ["live", "lives", "lived", "living"], a: 0 },
        { q: "She ___ TV every evening.", o: ["watch", "watches", "watched", "watching"], a: 1 },
        { q: "It often ___ in London.", o: ["rain", "rains", "rained", "raining"], a: 1 },
        { q: "I ___ tea in the mornings.", o: ["drink", "drinks", "drank", "drinking"], a: 0 },
        { q: "Birds ___ in the sky.", o: ["fly", "flies", "flew", "flying"], a: 0 },
        { q: "He never ___ late.", o: ["arrive", "arrives", "arrived", "arriving"], a: 1 },
        { q: "___ she work here?", o: ["Do", "Does", "Is", "Are"], a: 1 },
        { q: "The Earth ___ around the Sun.", o: ["rotate", "rotates", "rotating", "rotated"], a: 1 },
        { q: "My father ___ a car.", o: ["drive", "drives", "drove", "driving"], a: 1 },
        { q: "Cats ___ milk.", o: ["like", "likes", "liked", "liking"], a: 1 },
        { q: "She ___ her teeth twice a day.", o: ["brush", "brushes", "brushed", "brushing"], a: 1 },
        { q: "We ___ English at school.", o: ["study", "studies", "studied", "studying"], a: 0 },
        { q: "He ___ very fast.", o: ["run", "runs", "running", "ran"], a: 1 },
        { q: "The shop ___ at 9 AM.", o: ["open", "opens", "opening", "opened"], a: 1 },
        { q: "I ___ a student.", o: ["is", "am", "are", "be"], a: 1 },
        { q: "They ___ dinner at 7 PM.", o: ["has", "have", "having", "had"], a: 1 },
        { q: "She ___ beautiful songs.", o: ["sing", "sings", "sang", "singing"], a: 1 },
        { q: "It ___ cold in winter.", o: ["get", "gets", "got", "getting"], a: 1 },
        { q: "He ___ books every week.", o: ["read", "reads", "reading", "red"], a: 1 },
        { q: "We ___ to the gym on Mondays.", o: ["go", "goes", "going", "went"], a: 0 },
        { q: "The baby ___ a lot.", o: ["cry", "cries", "cried", "crying"], a: 1 },
        { q: "I ___ my friends on weekends.", o: ["meet", "meets", "met", "meeting"], a: 0 },
        { q: "She ___ hard every day.", o: ["work", "works", "worked", "working"], a: 1 },
        { q: "The doctor ___ patients every morning.", o: ["see", "sees", "seeing", "saw"], a: 1 },
        { q: "My dog ___ very loudly.", o: ["bark", "barks", "barking", "barked"], a: 1 },
        { q: "They ___ a bus to work.", o: ["take", "takes", "taking", "took"], a: 0 },
        { q: "He ___ chess very well.", o: ["play", "plays", "played", "playing"], a: 1 },
        { q: "The bank ___ at 10 AM.", o: ["open", "opens", "opened", "opening"], a: 1 },
        { q: "She ___ in the school library.", o: ["study", "studies", "studied", "studying"], a: 1 },
        { q: "I always ___ breakfast before leaving.", o: ["eat", "eats", "ate", "eating"], a: 0 },
        { q: "My sister ___ yoga every morning.", o: ["do", "does", "did", "doing"], a: 1 },
        { q: "___ your parents speak French?", o: ["Do", "Does", "Are", "Is"], a: 0 },
        { q: "He ___ to classical music.", o: ["listen", "listens", "listened", "listening"], a: 1 },
        { q: "Plants ___ water to survive.", o: ["need", "needs", "needed", "needing"], a: 0 },
        { q: "She ___ letters to her grandmother.", o: ["write", "writes", "wrote", "writing"], a: 1 },
        { q: "The bus ___ every 15 minutes.", o: ["come", "comes", "came", "coming"], a: 1 },
        { q: "I ___ my bike to school.", o: ["ride", "rides", "rode", "riding"], a: 0 },
        { q: "He ___ his phone everywhere.", o: ["bring", "brings", "brought", "bringing"], a: 1 },
      ],
      'Past Simple': [
        { q: "I ___ to the store yesterday.", o: ["go", "went", "gone", "going"], a: 1 },
        { q: "She ___ a letter last night.", o: ["write", "wrote", "written", "writing"], a: 1 },
        { q: "They ___ football last Sunday.", o: ["play", "played", "playing", "plays"], a: 1 },
        { q: "He ___ the book in two days.", o: ["read", "reads", "reading", "red"], a: 0 },
        { q: "We ___ a great movie last week.", o: ["see", "saw", "seen", "seeing"], a: 1 },
        { q: "She ___ dinner for everyone.", o: ["cook", "cooked", "cooking", "cooks"], a: 1 },
        { q: "The children ___ to the park.", o: ["run", "ran", "running", "runs"], a: 1 },
        { q: "I ___ my keys this morning.", o: ["lose", "lost", "losing", "loses"], a: 1 },
        { q: "He ___ to London last year.", o: ["travel", "travelled", "travelling", "travels"], a: 1 },
        { q: "They ___ the test easily.", o: ["pass", "passed", "passing", "passes"], a: 1 },
        { q: "She ___ the door quietly.", o: ["close", "closed", "closing", "closes"], a: 1 },
        { q: "We ___ breakfast at 7 AM.", o: ["have", "had", "having", "has"], a: 1 },
        { q: "He ___ the answer immediately.", o: ["know", "knew", "known", "knowing"], a: 1 },
        { q: "I ___ English for 5 years.", o: ["study", "studied", "studying", "studies"], a: 1 },
        { q: "She ___ a beautiful dress.", o: ["wear", "wore", "worn", "wearing"], a: 1 },
        { q: "They ___ a house last month.", o: ["buy", "bought", "buying", "buys"], a: 1 },
        { q: "He ___ me the truth.", o: ["tell", "told", "telling", "tells"], a: 1 },
        { q: "We ___ at the hotel.", o: ["stay", "stayed", "staying", "stays"], a: 1 },
        { q: "She ___ the window.", o: ["break", "broke", "broken", "breaking"], a: 1 },
        { q: "I ___ a taxi to work.", o: ["take", "took", "taken", "taking"], a: 1 },
        { q: "The baby ___ all night.", o: ["cry", "cried", "crying", "cries"], a: 1 },
        { q: "He ___ his bike to school.", o: ["ride", "rode", "ridden", "riding"], a: 1 },
        { q: "We ___ goodbye at the airport.", o: ["say", "said", "saying", "says"], a: 1 },
        { q: "She ___ the piano beautifully.", o: ["play", "played", "playing", "plays"], a: 1 },
        { q: "They ___ home at midnight.", o: ["come", "came", "coming", "comes"], a: 1 },
        { q: "I ___ tired after the race.", o: ["feel", "felt", "feeling", "feels"], a: 1 },
        { q: "He ___ the ball very far.", o: ["throw", "threw", "thrown", "throwing"], a: 1 },
        { q: "We ___ in the lake.", o: ["swim", "swam", "swimming", "swims"], a: 1 },
        { q: "She ___ all her exams.", o: ["pass", "passed", "passing", "passes"], a: 1 },
        { q: "The teacher ___ us homework.", o: ["give", "gave", "giving", "gives"], a: 1 },
        { q: "I ___ a strange noise.", o: ["hear", "heard", "hearing", "hears"], a: 1 },
        { q: "He ___ asleep quickly.", o: ["fall", "fell", "fallen", "falling"], a: 1 },
        { q: "We ___ many photos.", o: ["take", "took", "taken", "taking"], a: 1 },
        { q: "She ___ very happy.", o: ["seem", "seemed", "seeming", "seems"], a: 1 },
        { q: "They ___ the project on time.", o: ["finish", "finished", "finishing", "finishes"], a: 1 },
        { q: "I ___ him at the supermarket.", o: ["see", "saw", "seen", "seeing"], a: 1 },
        { q: "She ___ a letter to the manager.", o: ["send", "sent", "sending", "sends"], a: 1 },
        { q: "We ___ the wrong bus.", o: ["catch", "caught", "catching", "catches"], a: 1 },
        { q: "He ___ his phone at home.", o: ["leave", "left", "leaving", "leaves"], a: 1 },
        { q: "The lesson ___ at 9 AM.", o: ["begin", "began", "begun", "beginning"], a: 1 },
        { q: "She ___ a new language last year.", o: ["learn", "learnt", "learning", "learns"], a: 1 },
        { q: "We ___ the match 2-0.", o: ["win", "won", "winning", "wins"], a: 1 },
        { q: "He ___ the chair and sat down.", o: ["pull", "pulled", "pulling", "pulls"], a: 1 },
        { q: "I ___ a great book last summer.", o: ["find", "found", "finding", "finds"], a: 1 },
        { q: "She ___ about the problem.", o: ["think", "thought", "thinking", "thinks"], a: 1 },
        { q: "They ___ the same school as children.", o: ["attend", "attended", "attending", "attends"], a: 1 },
        { q: "He ___ his hand during the game.", o: ["hurt", "hurt", "hurting", "hurts"], a: 1 },
        { q: "We ___ the entire pizza.", o: ["eat", "ate", "eating", "eats"], a: 1 },
        { q: "She ___ a wonderful speech.", o: ["give", "gave", "given", "giving"], a: 1 },
        { q: "I ___ ten hours last night.", o: ["sleep", "slept", "sleeping", "sleeps"], a: 1 },
      ],
      'Future Simple': [
        { q: "I ___ call you tomorrow.", o: ["will", "would", "shall", "am going"], a: 0 },
        { q: "She ___ be 18 next month.", o: ["will", "would", "shall", "is"], a: 0 },
        { q: "They ___ travel to Paris next summer.", o: ["will", "would", "shall", "are"], a: 0 },
        { q: "He ___ pass the exam, I'm sure.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "We ___ buy a new car soon.", o: ["will", "would", "shall", "are"], a: 0 },
        { q: "It ___ rain tomorrow.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I ___ help you with that.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "She ___ be a doctor one day.", o: ["will", "would", "shall", "is"], a: 0 },
        { q: "They ___ arrive at 5 PM.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "We ___ not forget this day.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "He ___ finish work by Friday.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I think it ___ snow tonight.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "She ___ cook dinner for us.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "The movie ___ start at 8.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "We ___ see each other next week.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "I ___ study harder next semester.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "He ___ probably be late.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "They ___ build a new school here.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "She ___ send the email soon.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "___ you come to the party?", o: ["Will", "Would", "Shall", "Do"], a: 0 },
        { q: "I ___ not tell anyone.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "The price ___ increase next year.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "We ___ miss you a lot.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "He ___ get better soon.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I ___ always remember this.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "She ___ graduate next June.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "They ___ open a new shop.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "The weather ___ be nice tomorrow.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I ___ let you know the result.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "We ___ celebrate together.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "He ___ understand eventually.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "She ___ wait for you.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I ___ do my best.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "They ___ never forget this.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "It ___ take about an hour.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "The concert ___ start at 7 PM.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "She ___ join us for dinner.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I think they ___ agree with us.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "He ___ be surprised by the news.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "___ she come to the meeting?", o: ["Will", "Would", "Shall", "Does"], a: 0 },
        { q: "We ___ need more time.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "The shop ___ close at 9 PM.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I ___ write to you every week.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "They ___ arrive before midnight.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "She ___ definitely like this gift.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "He ___ not be at the office tomorrow.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "We ___ visit our grandparents this weekend.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "It ___ be a long journey.", o: ["will", "would", "shall", "does"], a: 0 },
        { q: "I ___ never give up.", o: ["will", "would", "shall", "do"], a: 0 },
        { q: "She ___ become a great musician.", o: ["will", "would", "shall", "does"], a: 0 },
      ],
      'Present Continuous': [
        { q: "I ___ reading a book now.", o: ["am", "is", "are", "be"], a: 0 },
        { q: "She ___ cooking dinner.", o: ["am", "is", "are", "be"], a: 1 },
        { q: "They ___ playing outside.", o: ["am", "is", "are", "be"], a: 2 },
        { q: "He ___ watching TV at the moment.", o: ["am", "is", "are", "be"], a: 1 },
        { q: "We ___ preparing for the exam.", o: ["am", "is", "are", "be"], a: 2 },
        { q: "Look! The baby ___ walking!", o: ["am", "is", "are", "be"], a: 1 },
        { q: "I ___ not sleeping, I am awake.", o: ["am", "is", "are", "be"], a: 0 },
        { q: "She ___ wearing a red dress today.", o: ["am", "is", "are", "be"], a: 1 },
        { q: "They ___ building a new house.", o: ["am", "is", "are", "be"], a: 2 },
        { q: "He ___ running in the park.", o: ["am", "is", "are", "be"], a: 1 },
        { q: "What ___ you doing?", o: ["am", "is", "are", "do"], a: 2 },
        { q: "The phone ___ ringing.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "We ___ waiting for the bus.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "She ___ learning to drive.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "I ___ writing an email.", o: ["am", "is", "are", "do"], a: 0 },
        { q: "The children ___ sleeping now.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "He ___ talking on the phone.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "It ___ raining outside.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "We ___ having lunch.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "She ___ listening to music.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "I ___ trying my best.", o: ["am", "is", "are", "do"], a: 0 },
        { q: "They ___ dancing at the party.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "He ___ fixing the car.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "The cat ___ sitting on the roof.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "We ___ moving to a new city.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "She ___ painting a picture.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "I ___ feeling much better now.", o: ["am", "is", "are", "do"], a: 0 },
        { q: "They ___ working on a project.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "He ___ having breakfast.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "Look! She ___ crying.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "We ___ planning a holiday.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "The dog ___ barking loudly.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "I ___ thinking about it.", o: ["am", "is", "are", "do"], a: 0 },
        { q: "They ___ getting ready for the show.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "She ___ smiling at me.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "He ___ studying for his exam.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "The students ___ taking notes.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "I ___ not watching TV right now.", o: ["am", "is", "are", "do"], a: 0 },
        { q: "She ___ shopping with her friends.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "We ___ travelling to Spain this summer.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "He ___ making a cake.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "They ___ competing in the tournament.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "The mechanic ___ repairing the engine.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "I ___ using your pen. Is that OK?", o: ["am", "is", "are", "do"], a: 0 },
        { q: "She ___ not coming to the party.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "We ___ learning a new song.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "He ___ jogging in the park.", o: ["am", "is", "are", "do"], a: 1 },
        { q: "The workers ___ installing new windows.", o: ["am", "is", "are", "do"], a: 2 },
        { q: "I ___ looking for my glasses.", o: ["am", "is", "are", "do"], a: 0 },
        { q: "She ___ presenting her project today.", o: ["am", "is", "are", "do"], a: 1 },
      ],
      'Past Continuous': [
        { q: "I ___ sleeping when you called.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ playing when it started to rain.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "She ___ reading at 8 PM.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ watching a movie.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "He ___ driving to work.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "The children ___ running in the garden.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "I ___ cooking when the phone rang.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "She ___ singing beautifully.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ studying all night.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "He ___ waiting for the bus.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ having dinner at 7.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "The dog ___ barking all morning.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "I ___ working when she arrived.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ dancing at the party.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "She ___ wearing a blue coat.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "He ___ cleaning his room.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ talking about you.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "The baby ___ crying loudly.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "I ___ thinking about the problem.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ walking to school.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "She ___ looking out the window.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "He ___ writing a letter.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ sitting in the park.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "The sun ___ shining brightly.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "I ___ having lunch at noon.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ arguing about something.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "She ___ teaching in the classroom.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "He ___ swimming in the pool.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ listening to the radio.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "When I woke up, it ___ snowing.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "I ___ dreaming about vacation.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ laughing at the joke.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "She ___ drawing a picture.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "He ___ fixing the fence.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ enjoying the concert.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "The students ___ taking an exam at 3 PM.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "He ___ not paying attention in class.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "She ___ cooking when her husband came home.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "I ___ jogging when it started to rain.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ discussing the project all evening.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "He ___ sleeping when the alarm went off.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ travelling when the train broke down.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "She ___ reading her book while he watched TV.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "The birds ___ singing early this morning.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "I ___ trying to sleep, but it was too loud.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "They ___ planning their trip at the cafe.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "He ___ talking on the phone for an hour.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "We ___ buying groceries when we met Tom.", o: ["was", "were", "am", "is"], a: 1 },
        { q: "She ___ not listening to the teacher.", o: ["was", "were", "am", "is"], a: 0 },
        { q: "The team ___ practising when the coach arrived.", o: ["was", "were", "am", "is"], a: 0 },
      ],
      'Present Perfect': [
        { q: "I ___ just finished my homework.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "She ___ visited Paris twice.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "They ___ never seen snow.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ lived here for 10 years.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "We ___ already had lunch.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ written three books.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ known him since childhood.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ moved to a new city.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ broken his arm.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "We ___ been to Japan.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ lost her keys.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ not seen this film yet.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ passed the exam.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ already cooked dinner.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "We ___ learned a lot today.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ just arrived.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ bought a new phone.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ cleaned the house.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ studied English for years.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "___ you ever been to London?", o: ["Have", "Has", "Are", "Were"], a: 0 },
        { q: "She ___ taught here since 2010.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ met him before.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ completed the project.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ grown much taller.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "We ___ heard the news.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ taken her medicine.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ forgotten his name.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ opened a new shop.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ chosen the blue one.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "We ___ spent all our money.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ sung this song before.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ driven this car before.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ found the answer.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ won the competition.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "We ___ told them everything.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ never tried sushi.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ already watched this film.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ recently started a new project.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ just left the building.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "We ___ worked together for years.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ not replied to my message.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ known this since last week.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ been very busy lately.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ read all of Shakespeare's plays.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "___ she ever lived abroad?", o: ["Have", "Has", "Is", "Was"], a: 1 },
        { q: "We ___ just received the package.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "She ___ achieved a lot in her career.", o: ["have", "has", "is", "was"], a: 1 },
        { q: "I ___ always loved this city.", o: ["have", "has", "am", "was"], a: 0 },
        { q: "They ___ made great progress.", o: ["have", "has", "are", "were"], a: 0 },
        { q: "He ___ not explained the problem clearly.", o: ["have", "has", "is", "was"], a: 1 },
      ],
      'Modal Verbs': [
        { q: "You ___ wear a seatbelt in the car.", o: ["must", "can", "will", "shall"], a: 0 },
        { q: "She ___ speak three languages.", o: ["can", "must", "will", "should"], a: 0 },
        { q: "I ___ help you if you want.", o: ["can", "must", "need", "should"], a: 0 },
        { q: "He ___ be at home. I'm not sure.", o: ["might", "must", "can", "need"], a: 0 },
        { q: "You ___ not park here.", o: ["must", "can", "will", "shall"], a: 0 },
        { q: "___ I borrow your pen?", o: ["Can", "Must", "Need", "Should"], a: 0 },
        { q: "We ___ study hard to pass.", o: ["should", "can", "might", "may"], a: 0 },
        { q: "She ___ swim when she was five.", o: ["could", "can", "must", "should"], a: 0 },
        { q: "You ___ see a doctor.", o: ["should", "can", "might", "may"], a: 0 },
        { q: "He ___ come late tonight.", o: ["might", "must", "can", "may"], a: 0 },
        { q: "Students ___ not cheat on exams.", o: ["must", "can", "will", "shall"], a: 0 },
        { q: "___ you pass the salt, please?", o: ["Could", "Must", "Need", "Should"], a: 0 },
        { q: "I ___ like some water, please.", o: ["would", "must", "should", "can"], a: 0 },
        { q: "She ___ be tired after the long trip.", o: ["must", "might", "will", "can"], a: 0 },
        { q: "We ___ go to the beach tomorrow.", o: ["could", "must", "need", "can"], a: 0 },
        { q: "You ___ eat more vegetables.", o: ["should", "can", "might", "may"], a: 0 },
        { q: "He ___ play the guitar very well.", o: ["can", "must", "will", "should"], a: 0 },
        { q: "___ I open the window?", o: ["Can", "Must", "Need", "Will"], a: 0 },
        { q: "They ___ have left already.", o: ["might", "may", "must", "will"], a: 0 },
        { q: "You ___ not touch that!", o: ["must", "can", "will", "shall"], a: 0 },
        { q: "She ___ dance beautifully.", o: ["can", "must", "will", "should"], a: 0 },
        { q: "We ___ leave now or we'll be late.", o: ["must", "can", "will", "shall"], a: 0 },
        { q: "He ___ come to the party. I'll invite him.", o: ["might", "must", "need", "should"], a: 0 },
        { q: "You ___ always tell the truth.", o: ["should", "can", "might", "may"], a: 0 },
        { q: "I ___ run faster when I was young.", o: ["could", "can", "must", "should"], a: 0 },
        { q: "She ___ not need to work tomorrow.", o: ["may", "must", "can", "might"], a: 0 },
        { q: "___ you help me carry this?", o: ["Could", "Must", "Need", "Should"], a: 0 },
        { q: "He ___ be the new teacher.", o: ["must", "can", "should", "will"], a: 0 },
        { q: "We ___ try the new restaurant.", o: ["should", "must", "need", "can"], a: 0 },
        { q: "They ___ have forgotten the meeting.", o: ["might", "must", "can", "need"], a: 0 },
        { q: "You ___ not worry about it.", o: ["need", "should", "can", "might"], a: 0 },
        { q: "She ___ read before she was four.", o: ["could", "can", "must", "might"], a: 0 },
        { q: "I ___ be going now. Bye!", o: ["must", "can", "would", "might"], a: 0 },
        { q: "___ we begin the lesson?", o: ["Shall", "Should", "Need", "Would"], a: 0 },
        { q: "He ___ have lifted 100 kg.", o: ["could", "must", "would", "will"], a: 0 },
        { q: "Passengers ___ fasten their seatbelts.", o: ["must", "can", "might", "shall"], a: 0 },
        { q: "You ___ take an umbrella. It might rain.", o: ["should", "can", "will", "shall"], a: 0 },
        { q: "She ___ have been at the party last night.", o: ["might", "must", "can", "will"], a: 0 },
        { q: "___ I speak to the manager?", o: ["Could", "Shall", "Need", "Will"], a: 0 },
        { q: "He ___ not have arrived yet.", o: ["may", "can", "will", "shall"], a: 0 },
        { q: "We ___ respect the elderly.", o: ["should", "must", "can", "will"], a: 0 },
        { q: "She ___ cook when she was young.", o: ["could", "should", "must", "will"], a: 0 },
        { q: "You ___ not eat in the library.", o: ["must", "can", "will", "shall"], a: 0 },
        { q: "I ___ definitely help you tomorrow.", o: ["will", "would", "should", "can"], a: 0 },
        { q: "___ you like to have some tea?", o: ["Would", "Will", "Shall", "Can"], a: 0 },
        { q: "They ___ have arrived hours ago.", o: ["should", "must", "can", "will"], a: 0 },
        { q: "She ___ be your new colleague.", o: ["must", "might", "will", "shall"], a: 0 },
        { q: "I ___ hear you. Please speak up.", o: ["can't", "don't", "won't", "mustn't"], a: 0 },
        { q: "He ___ not have told her the secret.", o: ["should", "can", "will", "shall"], a: 0 },
        { q: "We ___ to be more careful next time.", o: ["ought", "must", "need", "shall"], a: 0 },
      ],
      'Conditionals': [
        { q: "If it rains, I ___ stay at home.", o: ["will", "would", "was", "is"], a: 0 },
        { q: "If I ___ you, I would apologize.", o: ["were", "am", "be", "was"], a: 0 },
        { q: "If she studies, she ___ pass the exam.", o: ["will", "would", "could", "might"], a: 0 },
        { q: "If I had known, I ___ have helped.", o: ["would", "will", "can", "might"], a: 0 },
        { q: "If you heat water, it ___.", o: ["boils", "would boil", "boiled", "will boil"], a: 0 },
        { q: "If I ___ rich, I would travel the world.", o: ["were", "am", "would be", "was"], a: 0 },
        { q: "If he comes, we ___ start the meeting.", o: ["will", "would", "was", "shall"], a: 0 },
        { q: "If they worked harder, they ___ succeed.", o: ["would", "will", "can", "do"], a: 0 },
        { q: "If I had studied, I ___ have passed.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "If you mix red and blue, you ___ get purple.", o: ["get", "would get", "got", "will get"], a: 0 },
        { q: "I ___ call you if I have time.", o: ["will", "would", "shall", "can"], a: 0 },
        { q: "If she had come earlier, she ___ have been late.", o: ["would not", "will not", "shall not", "does not"], a: 0 },
        { q: "If we ___ the lottery, we would be rich.", o: ["won", "win", "had won", "wins"], a: 0 },
        { q: "If you press this button, the light ___ on.", o: ["turns", "would turn", "turned", "will turn"], a: 0 },
        { q: "If I were taller, I ___ play basketball.", o: ["would", "will", "can", "do"], a: 0 },
        { q: "If it snows, the children ___ be happy.", o: ["will", "would", "could", "had"], a: 0 },
        { q: "If he ___ me, I would have answered.", o: ["had called", "calls", "will call", "called"], a: 0 },
        { q: "If you eat too much, you ___ feel sick.", o: ["will", "would", "could", "shall"], a: 0 },
        { q: "If I ___ you, I would take that job.", o: ["were", "am", "would be", "was"], a: 0 },
        { q: "She ___ be happy if she heard this news.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "If we leave now, we ___ arrive on time.", o: ["will", "would", "could", "should"], a: 0 },
        { q: "If I had a car, I ___ drive to work.", o: ["would", "will", "can", "do"], a: 0 },
        { q: "If they invite us, we ___ go.", o: ["will", "would", "could", "shall"], a: 0 },
        { q: "If you ___ water them, plants die.", o: ["don't", "didn't", "won't", "wouldn't"], a: 0 },
        { q: "If he had studied medicine, he ___ be a doctor.", o: ["would", "will", "can", "does"], a: 0 },
        { q: "If I see her, I ___ say hello.", o: ["will", "would", "could", "shall"], a: 0 },
        { q: "If she ___ free, she would come.", o: ["were", "is", "will be", "was"], a: 0 },
        { q: "If you run fast, you ___ catch the bus.", o: ["will", "would", "could", "shall"], a: 0 },
        { q: "If I ___ the answer, I would tell you.", o: ["knew", "know", "had known", "knows"], a: 0 },
        { q: "If the weather ___ sunny, we will go.", o: ["is", "was", "will be", "would be"], a: 0 },
        { q: "If he saves money, he ___ buy a car.", o: ["will", "would", "could", "shall"], a: 0 },
        { q: "If I had wings, I ___ fly.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "If she exercised more, she ___ better results.", o: ["would get", "will get", "can get", "does get"], a: 0 },
        { q: "If you touch fire, you ___ get burned.", o: ["will", "would", "could", "shall"], a: 0 },
        { q: "If we had hurried, we ___ caught the train.", o: ["would have", "will have", "can have", "do have"], a: 0 },
        { q: "If I ___ harder, I would have passed.", o: ["had worked", "worked", "work", "will work"], a: 0 },
        { q: "She would feel better if she ___ some rest.", o: ["got", "gets", "will get", "has got"], a: 0 },
        { q: "If dogs ___ fly, the world would be different.", o: ["could", "can", "would", "will"], a: 0 },
        { q: "I ___ buy a house if I had more money.", o: ["would", "will", "could", "shall"], a: 0 },
        { q: "If it ___ freezing, water turns to ice.", o: ["is", "was", "will be", "would be"], a: 0 },
        { q: "If they ___ harder, they would succeed.", o: ["tried", "try", "will try", "have tried"], a: 0 },
        { q: "She would visit us more often if she ___ nearby.", o: ["lived", "lives", "will live", "has lived"], a: 0 },
        { q: "If I ___ to bed earlier, I would not be tired.", o: ["went", "go", "will go", "have gone"], a: 0 },
        { q: "If we had more time, we ___ the project.", o: ["would finish", "will finish", "finish", "finishing"], a: 0 },
        { q: "You will regret it if you ___.", o: ["don't study", "didn't study", "won't study", "not study"], a: 0 },
        { q: "If she ___ her keys, she cannot enter.", o: ["loses", "lost", "will lose", "would lose"], a: 0 },
        { q: "We could go hiking if the weather ___.", o: ["were better", "is better", "will be better", "had been better"], a: 0 },
        { q: "If he ___ more attention, he would understand.", o: ["paid", "pays", "will pay", "has paid"], a: 0 },
        { q: "If I ___ him, I would explain everything.", o: ["see", "saw", "had seen", "will see"], a: 0 },
        { q: "They would have been on time if they ___ left earlier.", o: ["had", "have", "will have", "did"], a: 0 },
      ],
      'Passive Voice': [
        { q: "The cake ___ baked by my mother.", o: ["was", "is being", "has", "did"], a: 0 },
        { q: "English ___ spoken all over the world.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The letter ___ written yesterday.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "The homework ___ done.", o: ["has been", "is", "was", "did"], a: 0 },
        { q: "The window ___ broken by a ball.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "Cars ___ produced in factories.", o: ["are", "is", "was", "has"], a: 0 },
        { q: "The book ___ published in 2020.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "The food ___ being cooked right now.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The test ___ taken by all students.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The house ___ painted blue.", o: ["was", "is being", "has", "does"], a: 0 },
        { q: "The report ___ be finished by Friday.", o: ["will", "is", "was", "has"], a: 0 },
        { q: "These shoes ___ made in Italy.", o: ["are", "is", "was", "has"], a: 0 },
        { q: "The thief ___ caught by the police.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "The song ___ sung by the choir.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "The building ___ being constructed.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "Rice ___ grown in Asia.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The invitations ___ sent yesterday.", o: ["were", "are", "do", "did"], a: 0 },
        { q: "The meeting ___ cancelled.", o: ["was", "is", "did", "do"], a: 0 },
        { q: "The road ___ repaired last month.", o: ["was", "is", "does", "do"], a: 0 },
        { q: "Coffee ___ served every morning.", o: ["is", "was", "does", "do"], a: 0 },
        { q: "The film ___ seen by millions.", o: ["was", "is", "does", "do"], a: 0 },
        { q: "The trees ___ planted by volunteers.", o: ["were", "was", "is", "does"], a: 0 },
        { q: "The door ___ locked at night.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The prize ___ won by our team.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "Bread ___ baked fresh daily.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The news ___ announced on TV.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "Homework ___ given every day.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The game ___ played on Saturday.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "Animals ___ protected by law.", o: ["are", "is", "was", "has"], a: 0 },
        { q: "The exam ___ postponed.", o: ["has been", "is", "was", "did"], a: 0 },
        { q: "The car ___ washed yesterday.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "Dinner ___ served at 7 PM.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "The bridge ___ built in 1990.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "The letters ___ delivered by the postman.", o: ["are", "is", "was", "has"], a: 0 },
        { q: "The project ___ be completed soon.", o: ["will", "is", "was", "has"], a: 0 },
        { q: "The emails ___ answered every day.", o: ["are", "is", "was", "does"], a: 0 },
        { q: "The new law ___ passed last month.", o: ["was", "is", "has", "did"], a: 0 },
        { q: "A new hospital ___ being built in the city.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The documents ___ signed by the director.", o: ["were", "was", "are", "have"], a: 0 },
        { q: "This glass ___ made of recycled material.", o: ["is", "was", "has", "does"], a: 0 },
        { q: "The stolen car ___ found near the lake.", o: ["was", "is", "has", "does"], a: 0 },
        { q: "The windows ___ cleaned every week.", o: ["are", "is", "was", "does"], a: 0 },
        { q: "The concert ___ cancelled due to bad weather.", o: ["was", "is", "has", "did"], a: 0 },
        { q: "All passengers ___ asked to board.", o: ["were", "was", "are", "have"], a: 0 },
        { q: "The new product ___ launched yesterday.", o: ["was", "is", "has", "did"], a: 0 },
        { q: "My bag ___ stolen on the train.", o: ["was", "is", "has", "did"], a: 0 },
        { q: "The village ___ destroyed by the flood.", o: ["was", "is", "has", "did"], a: 0 },
        { q: "These photos ___ taken in 1990.", o: ["were", "was", "are", "have"], a: 0 },
        { q: "The repairs ___ not finished yet.", o: ["have been", "are", "were", "did"], a: 0 },
        { q: "This novel ___ translated into 40 languages.", o: ["has been", "is", "was", "did"], a: 0 },
      ],
      'Articles': [
        { q: "I saw ___ elephant at the zoo.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "She is ___ best student in the class.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "He wants ___ apple.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "___ sun rises in the east.", o: ["The", "A", "An", "—"], a: 0 },
        { q: "She is ___ doctor.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "I need ___ hour to finish.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "___ water is essential for life.", o: ["—", "A", "An", "The"], a: 0 },
        { q: "He plays ___ guitar.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "I bought ___ new book.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "___ moon is beautiful tonight.", o: ["The", "A", "An", "—"], a: 0 },
        { q: "She is ___ honest person.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "I have ___ cat and ___ dog.", o: ["a, a", "an, a", "the, the", "a, an"], a: 0 },
        { q: "He went to ___ hospital.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "___ children love chocolate.", o: ["—", "A", "An", "The"], a: 0 },
        { q: "She gave me ___ umbrella.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "I watched ___ film last night.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "He is ___ engineer.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "___ Atlantic Ocean is very deep.", o: ["The", "A", "An", "—"], a: 0 },
        { q: "She wants ___ cup of tea.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "I need ___ information.", o: ["—", "a", "an", "the"], a: 0 },
        { q: "He is ___ university student.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "She played ___ piano at the concert.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "I want ___ orange juice.", o: ["—", "a", "an", "the"], a: 0 },
        { q: "He is ___ tallest boy in class.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "We went to ___ park yesterday.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "___ gold is expensive.", o: ["—", "A", "An", "The"], a: 0 },
        { q: "She works at ___ airport.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "I watched ___ interesting film.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "He needs ___ advice.", o: ["—", "a", "an", "the"], a: 0 },
        { q: "___ Pacific Ocean is huge.", o: ["The", "A", "An", "—"], a: 0 },
        { q: "I have ___ idea!", o: ["an", "a", "the", "—"], a: 0 },
        { q: "She is ___ only child.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "He is ___ European.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "She speaks ___ English very well.", o: ["—", "a", "an", "the"], a: 0 },
        { q: "I saw ___ accident on ___ way home.", o: ["an, the", "a, the", "the, a", "an, a"], a: 0 },
        { q: "Mount Everest is ___ highest mountain.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "He is ___ honest man.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "She drives ___ hour every day.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "They visited ___ Eiffel Tower.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "___ love is a wonderful feeling.", o: ["—", "A", "An", "The"], a: 0 },
        { q: "He bought ___ laptop last week.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "I met ___ old friend of mine.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "She is studying at ___ university.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "___ Sahara is the largest desert.", o: ["The", "A", "An", "—"], a: 0 },
        { q: "He went to ___ doctor yesterday.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "She gave me ___ useful piece of advice.", o: ["a", "an", "the", "—"], a: 0 },
        { q: "I am going to ___ library.", o: ["the", "a", "an", "—"], a: 0 },
        { q: "___ English is a global language.", o: ["—", "A", "An", "The"], a: 0 },
        { q: "We saw ___ elephant at the circus.", o: ["an", "a", "the", "—"], a: 0 },
        { q: "He is ___ best player on the team.", o: ["the", "a", "an", "—"], a: 0 },
      ],
      'Comparatives': [
        { q: "She is ___ than her sister.", o: ["taller", "tallest", "more tall", "most tall"], a: 0 },
        { q: "This is the ___ book I have ever read.", o: ["best", "better", "gooder", "more good"], a: 0 },
        { q: "He runs ___ than me.", o: ["faster", "fastest", "more fast", "most fast"], a: 0 },
        { q: "This test is ___ than the last one.", o: ["harder", "hardest", "more hard", "most hard"], a: 0 },
        { q: "He is ___ than his brother.", o: ["smarter", "smartest", "more smart", "most smart"], a: 0 },
        { q: "This is the ___ car here.", o: ["most expensive", "more expensive", "expensivest", "very expensive"], a: 0 },
        { q: "My house is ___ than yours.", o: ["bigger", "biggest", "more big", "most big"], a: 0 },
        { q: "Today is ___ than yesterday.", o: ["colder", "coldest", "more cold", "most cold"], a: 0 },
        { q: "He is ___ than his father.", o: ["younger", "youngest", "more young", "most young"], a: 0 },
        { q: "This is the ___ film in history.", o: ["worst", "worse", "more bad", "most bad"], a: 0 },
        { q: "She sings ___ of all.", o: ["best", "better", "more good", "most good"], a: 0 },
        { q: "This road is ___ than that one.", o: ["longer", "longest", "more long", "most long"], a: 0 },
        { q: "He is the ___ runner on the team.", o: ["fastest", "faster", "more fast", "most fast"], a: 0 },
        { q: "English is ___ for me than math.", o: ["easier", "easiest", "more easy", "most easy"], a: 0 },
        { q: "She is ___ than in the photo.", o: ["more beautiful", "most beautiful", "beautifuler", "beautifully"], a: 0 },
        { q: "He is the ___ person I know.", o: ["kindest", "kinder", "more kind", "most kind"], a: 0 },
        { q: "This chair is ___ than that one.", o: ["more comfortable", "most comfortable", "comfortabler", "comfortably"], a: 0 },
        { q: "She works ___ than anyone else.", o: ["harder", "hardest", "more hard", "most hard"], a: 0 },
        { q: "This is the ___ day of my life.", o: ["happiest", "happier", "more happy", "most happy"], a: 0 },
        { q: "He is ___ than his brother.", o: ["more careful", "most careful", "carefuller", "carefully"], a: 0 },
        { q: "This cake is ___ than the pie.", o: ["sweeter", "sweetest", "more sweet", "most sweet"], a: 0 },
        { q: "My bag is ___ than yours.", o: ["heavier", "heaviest", "more heavy", "most heavy"], a: 0 },
        { q: "This puzzle is ___ than that one.", o: ["more difficult", "most difficult", "difficulter", "difficultly"], a: 0 },
        { q: "He is the ___ man in the room.", o: ["oldest", "older", "more old", "most old"], a: 0 },
        { q: "Summer is ___ than spring.", o: ["hotter", "hottest", "more hot", "most hot"], a: 0 },
        { q: "This is the ___ story.", o: ["most interesting", "more interesting", "interestingest", "interestingly"], a: 0 },
        { q: "She is ___ than she looks.", o: ["stronger", "strongest", "more strong", "most strong"], a: 0 },
        { q: "This is the ___ room in the house.", o: ["smallest", "smaller", "more small", "most small"], a: 0 },
        { q: "He drives ___ than his wife.", o: ["faster", "fastest", "more fast", "most fast"], a: 0 },
        { q: "This restaurant is ___ than that one.", o: ["more popular", "most popular", "popularer", "popularly"], a: 0 },
        { q: "The journey was ___ than expected.", o: ["longer", "longest", "more long", "most long"], a: 0 },
        { q: "She is ___ at maths than her friend.", o: ["better", "best", "more good", "most good"], a: 0 },
        { q: "This hotel is ___ than the one we stayed in.", o: ["more luxurious", "most luxurious", "luxuriouser", "very luxurious"], a: 0 },
        { q: "He felt ___ after taking medicine.", o: ["better", "best", "more good", "gooder"], a: 0 },
        { q: "The second test was ___ than the first.", o: ["easier", "easiest", "more easy", "most easy"], a: 0 },
        { q: "She arrived ___ than I expected.", o: ["earlier", "earliest", "more early", "most early"], a: 0 },
        { q: "This film is ___ than his last one.", o: ["worse", "worst", "more bad", "most bad"], a: 0 },
        { q: "The weather today is ___ than yesterday.", o: ["worse", "worst", "more bad", "most bad"], a: 0 },
        { q: "Her voice is ___ than a whisper.", o: ["softer", "softest", "more soft", "most soft"], a: 0 },
        { q: "He is ___ now than he was last year.", o: ["taller", "tallest", "more tall", "most tall"], a: 0 },
        { q: "This bag is ___ than the one in the shop.", o: ["cheaper", "cheapest", "more cheap", "most cheap"], a: 0 },
        { q: "She speaks English ___ than her sister.", o: ["more fluently", "most fluently", "fluentlier", "very fluently"], a: 0 },
        { q: "This is the ___ news I've heard all day.", o: ["best", "better", "more good", "most good"], a: 0 },
        { q: "His new phone is ___ than his old one.", o: ["faster", "fastest", "more fast", "most fast"], a: 0 },
        { q: "The library is ___ than the café.", o: ["quieter", "quietest", "more quiet", "most quiet"], a: 0 },
        { q: "She is ___ student in the class.", o: ["the most talented", "a most talented", "most talented", "more talented"], a: 0 },
        { q: "The new bridge is ___ than the old one.", o: ["stronger", "strongest", "more strong", "most strong"], a: 0 },
        { q: "Today's lecture was ___ than yesterday's.", o: ["more interesting", "most interesting", "interestinger", "very interesting"], a: 0 },
        { q: "He is ___ about safety than his colleague.", o: ["more careful", "most careful", "carefuller", "more carefully"], a: 0 },
        { q: "This exam was the ___ I have ever taken.", o: ["hardest", "harder", "most hard", "more hard"], a: 0 },
      ],
      'Prepositions': [
        { q: "The cat is ___ the table.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "I live ___ New York.", o: ["in", "on", "at", "to"], a: 0 },
        { q: "She arrived ___ Monday.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "The meeting is ___ 3 PM.", o: ["at", "in", "on", "to"], a: 0 },
        { q: "He was born ___ 1995.", o: ["in", "on", "at", "to"], a: 0 },
        { q: "The book is ___ the shelf.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "We went ___ the park.", o: ["to", "in", "on", "at"], a: 0 },
        { q: "She is interested ___ music.", o: ["in", "on", "at", "to"], a: 0 },
        { q: "He is good ___ math.", o: ["at", "in", "on", "to"], a: 0 },
        { q: "The shop is ___ the corner.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "See you ___ Friday.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "She lives ___ the second floor.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "He depends ___ his parents.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "We arrived ___ the airport.", o: ["at", "in", "on", "to"], a: 0 },
        { q: "The picture is ___ the wall.", o: ["on", "in", "at", "to"], a: 0 },
        { q: "I am afraid ___ spiders.", o: ["of", "from", "to", "at"], a: 0 },
        { q: "She is waiting ___ the bus.", o: ["for", "to", "on", "in"], a: 0 },
        { q: "He apologized ___ being late.", o: ["for", "to", "about", "from"], a: 0 },
        { q: "The bird is flying ___ the house.", o: ["over", "on", "in", "at"], a: 0 },
        { q: "She walked ___ the room.", o: ["across", "on", "in", "at"], a: 0 },
        { q: "He sat ___ me and Tom.", o: ["between", "among", "in", "on"], a: 0 },
        { q: "She hid ___ the bed.", o: ["under", "on", "in", "at"], a: 0 },
        { q: "He is proud ___ his son.", o: ["of", "about", "for", "in"], a: 0 },
        { q: "We drove ___ the tunnel.", o: ["through", "on", "in", "at"], a: 0 },
        { q: "She is married ___ a doctor.", o: ["to", "with", "for", "at"], a: 0 },
        { q: "I agree ___ you.", o: ["with", "to", "for", "on"], a: 0 },
        { q: "He suffers ___ headaches.", o: ["from", "of", "with", "at"], a: 0 },
        { q: "The cat jumped ___ the wall.", o: ["over", "on", "in", "at"], a: 0 },
        { q: "She is responsible ___ the project.", o: ["for", "of", "about", "to"], a: 0 },
        { q: "He succeeded ___ business.", o: ["in", "on", "at", "to"], a: 0 },
        { q: "She has been here ___ 2018.", o: ["since", "for", "from", "in"], a: 0 },
        { q: "I waited ___ two hours.", o: ["for", "since", "from", "in"], a: 0 },
        { q: "The school is ___ the library.", o: ["next to", "close", "near to", "in"], a: 0 },
        { q: "He is interested ___ photography.", o: ["in", "on", "at", "for"], a: 0 },
        { q: "I will meet you ___ the entrance.", o: ["at", "in", "on", "for"], a: 0 },
        { q: "She is tired ___ studying.", o: ["of", "from", "with", "for"], a: 0 },
        { q: "He is different ___ his brother.", o: ["from", "to", "of", "with"], a: 0 },
        { q: "We went out ___ despite the rain.", o: ["—", "in", "on", "at"], a: 0 },
        { q: "She complained ___ the noise.", o: ["about", "of", "from", "to"], a: 0 },
        { q: "The stadium is ___ the city centre.", o: ["outside", "out", "away", "far"], a: 0 },
        { q: "He is very good ___ playing chess.", o: ["at", "in", "on", "for"], a: 0 },
        { q: "I got a message ___ my teacher.", o: ["from", "of", "with", "by"], a: 0 },
        { q: "She went to Paris ___ the first time.", o: ["for", "in", "on", "at"], a: 0 },
        { q: "The children ran ___ the garden.", o: ["around", "on", "in", "at"], a: 0 },
        { q: "He jumped ___ the swimming pool.", o: ["into", "in", "on", "at"], a: 0 },
        { q: "She translated the text ___ English.", o: ["into", "in", "on", "to"], a: 0 },
        { q: "The film is based ___ a true story.", o: ["on", "in", "at", "for"], a: 0 },
        { q: "I am looking forward ___ seeing you.", o: ["to", "for", "at", "in"], a: 0 },
        { q: "The plane arrived ___ time.", o: ["on", "in", "at", "by"], a: 0 },
        { q: "She is not aware ___ the problem.", o: ["of", "about", "with", "for"], a: 0 },
      ],
      'Reported Speech': [
        { q: "She said that she ___ tired.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "He told me that he ___ help.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "They said that they ___ leaving.", o: ["were", "are", "will be", "have been"], a: 0 },
        { q: "She said that she ___ finished.", o: ["had", "has", "will have", "is"], a: 0 },
        { q: "He said he ___ the book.", o: ["had read", "reads", "will read", "is reading"], a: 0 },
        { q: "She asked if I ___ English.", o: ["spoke", "speak", "will speak", "am speaking"], a: 0 },
        { q: "He said that he ___ go tomorrow.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "They told us that they ___ happy.", o: ["were", "are", "will be", "have been"], a: 0 },
        { q: "She said that she ___ a new job.", o: ["had found", "finds", "will find", "is finding"], a: 0 },
        { q: "He asked where I ___.", o: ["lived", "live", "will live", "am living"], a: 0 },
        { q: "She told me that she ___ cooking.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "He said that he ___ the film.", o: ["had seen", "has seen", "will see", "is seeing"], a: 0 },
        { q: "They asked if we ___ come.", o: ["could", "can", "will", "shall"], a: 0 },
        { q: "She said that she ___ to the shop.", o: ["had gone", "goes", "will go", "is going"], a: 0 },
        { q: "He said that he ___ busy.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "She asked what I ___ doing.", o: ["was", "am", "will be", "have been"], a: 0 },
        { q: "He said that the weather ___ good.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "They told us that they ___ arrived.", o: ["had", "have", "will have", "are"], a: 0 },
        { q: "She said that she ___ call later.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "He asked if she ___ come.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "She said that she ___ the answer.", o: ["knew", "knows", "will know", "is knowing"], a: 0 },
        { q: "He told me that he ___ study more.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "They said that they ___ not understand.", o: ["could", "can", "will", "shall"], a: 0 },
        { q: "She asked when we ___ leave.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "He said that he ___ never been there.", o: ["had", "has", "will have", "is"], a: 0 },
        { q: "She told me that she ___ a teacher.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "He said that he ___ his keys.", o: ["had lost", "has lost", "will lose", "is losing"], a: 0 },
        { q: "They asked if I ___ free.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "She said that the food ___ delicious.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "He told me that he ___ try harder.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "She said that she ___ waiting.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "He asked why I ___ late.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "They said that they ___ help us.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "She told me that she ___ heard the news.", o: ["had", "has", "will have", "is"], a: 0 },
        { q: "He said that he ___ feeling well.", o: ["was", "is", "will be", "has been"], a: 0 },
        { q: "The teacher said we ___ submit the work by Friday.", o: ["had to", "have to", "must", "should"], a: 0 },
        { q: 'He said "I am happy" → He said that he ___ happy.', o: ["was", "is", "were", "had been"], a: 0 },
        { q: 'She said "I will come" → She said that she ___ come.', o: ["would", "will", "shall", "could"], a: 0 },
        { q: 'He said "I have finished" → He said that he ___ finished.', o: ["had", "has", "was", "did"], a: 0 },
        { q: 'They said "We can help" → They said that they ___ help.', o: ["could", "can", "shall", "would"], a: 0 },
        { q: "He told me he ___ the exam the next day.", o: ["was taking", "is taking", "will take", "takes"], a: 0 },
        { q: "She asked me what I ___ for dinner.", o: ["wanted", "want", "will want", "am wanting"], a: 0 },
        { q: "They told us they ___ on holiday.", o: ["were going", "are going", "will go", "go"], a: 0 },
        { q: "He said he ___ his homework.", o: ["had done", "has done", "does", "did"], a: 0 },
        { q: "She asked if I ___ seen the news.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "He told her that he ___ her a gift.", o: ["had brought", "has brought", "brings", "brought"], a: 0 },
        { q: "They said the meeting ___ been postponed.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "She told me she ___ move to Paris.", o: ["might", "may", "will", "shall"], a: 0 },
        { q: "He said his brother ___ a new job.", o: ["had got", "has got", "gets", "got"], a: 0 },
        { q: "She said that the shop ___ at 9.", o: ["opened", "opens", "will open", "is opening"], a: 0 },
      ],
      'Relative Clauses': [
        { q: "The man ___ lives next door is a doctor.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The book ___ I read was amazing.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The girl ___ bag was stolen was crying.", o: ["whose", "who", "which", "whom"], a: 0 },
        { q: "The city ___ we visited was beautiful.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The teacher ___ taught us is retired.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The house ___ roof is red is mine.", o: ["whose", "who", "which", "whom"], a: 0 },
        { q: "The film ___ we watched was funny.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The woman ___ called you is my aunt.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The car ___ he bought is expensive.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The boy ___ father is a pilot is my friend.", o: ["whose", "who", "which", "whom"], a: 0 },
        { q: "The restaurant ___ we ate was excellent.", o: ["where", "who", "whose", "whom"], a: 0 },
        { q: "The students ___ passed the exam celebrated.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The dog ___ bit me was black.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The artist ___ paintings are famous died young.", o: ["whose", "who", "which", "whom"], a: 0 },
        { q: "The place ___ we met is special.", o: ["where", "who", "which", "whom"], a: 0 },
        { q: "The day ___ she arrived was rainy.", o: ["when", "who", "which", "whom"], a: 0 },
        { q: "The reason ___ he left is unknown.", o: ["why", "who", "which", "whom"], a: 0 },
        { q: "The people ___ work here are friendly.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The country ___ I was born is small.", o: ["where", "which", "who", "whom"], a: 0 },
        { q: "The woman ___ I met was kind.", o: ["whom", "who", "which", "where"], a: 0 },
        { q: "The hotel ___ we stayed was good.", o: ["where", "which", "who", "whom"], a: 0 },
        { q: "The children ___ parents came were happy.", o: ["whose", "who", "which", "whom"], a: 0 },
        { q: "The phone ___ is ringing is mine.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The doctor ___ treated me was gentle.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The song ___ she sang was popular.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The friend ___ helped me is loyal.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The year ___ he graduated was 2020.", o: ["when", "which", "who", "whose"], a: 0 },
        { q: "The company ___ I work for is growing.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The person ___ opinion I trust is you.", o: ["whose", "who", "which", "whom"], a: 0 },
        { q: "The park ___ we play is nearby.", o: ["where", "who", "whose", "which"], a: 0 },
        { q: "The neighbour ___ dog barks is annoying.", o: ["whose", "who", "which", "whom"], a: 0 },
        { q: "The letter ___ arrived today is important.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The city ___ I grew up is quiet.", o: ["where", "who", "whose", "which"], a: 0 },
        { q: "The student ___ won the prize is my friend.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The building ___ they work in is very modern.", o: ["which", "who", "whose", "where"], a: 0 },
        { q: "The summer ___ we met was very hot.", o: ["when", "which", "who", "whose"], a: 0 },
        { q: "The team ___ won the match is from Spain.", o: ["which", "who", "whose", "whom"], a: 0 },
        { q: "The language ___ I find hardest is Chinese.", o: ["which", "who", "whose", "where"], a: 0 },
        { q: "The professor ___ taught us retired last year.", o: ["who", "which", "whose", "whom"], a: 0 },
        { q: "The town ___ she grew up has changed a lot.", o: ["where", "when", "which", "who"], a: 0 },
        { q: "The reason ___ she was late is unclear.", o: ["why", "which", "when", "where"], a: 0 },
        { q: "That is the man ___ I told you about.", o: ["whom", "who", "which", "whose"], a: 0 },
        { q: "She is the teacher ___ class I love.", o: ["whose", "who", "which", "where"], a: 0 },
        { q: "The day ___ I passed my exam was unforgettable.", o: ["when", "which", "who", "where"], a: 0 },
        { q: "The laptop ___ I bought last month is broken.", o: ["which", "who", "whose", "where"], a: 0 },
        { q: "Is that the restaurant ___ opened last week?", o: ["which", "who", "whose", "where"], a: 0 },
        { q: "The man ___ wife is a scientist works here.", o: ["whose", "who", "which", "where"], a: 0 },
        { q: "The village ___ they grew up no longer exists.", o: ["where", "which", "who", "when"], a: 0 },
        { q: "That is the film ___ won three Oscars.", o: ["which", "who", "whose", "where"], a: 0 },
        { q: "She is the nurse ___ looked after my grandfather.", o: ["who", "which", "whose", "where"], a: 0 },
      ],
      'Phrasal Verbs': [
        { q: "Please ___ your shoes before entering.", o: ["take off", "put on", "pick up", "let in"], a: 0 },
        { q: "I need to ___ this word in the dictionary.", o: ["look up", "look after", "search for", "look into"], a: 0 },
        { q: "She ___ a great idea.", o: ["came up with", "came down", "came in", "came through"], a: 0 },
        { q: "He ___ smoking last year.", o: ["gave up", "gave in", "gave out", "gave away"], a: 0 },
        { q: "We ___ early for the trip.", o: ["set off", "set up", "set in", "set out"], a: 0 },
        { q: "Can you ___ the children while I'm away?", o: ["look after", "look up", "search for", "look into"], a: 0 },
        { q: "The plane ___ on time.", o: ["took off", "took on", "took in", "took up"], a: 0 },
        { q: "She ___ well with her colleagues.", o: ["gets along", "gets up", "gets over", "gets out"], a: 0 },
        { q: "He ___ the project alone.", o: ["carried out", "carried on", "carried away", "carried off"], a: 0 },
        { q: "Don't ___! Keep trying!", o: ["give up", "give in", "give away", "give out"], a: 0 },
        { q: "She ___ early every morning.", o: ["gets up", "gets in", "gets off", "gets along"], a: 0 },
        { q: "We need to ___ this problem.", o: ["figure out", "figure in", "work on", "sort out"], a: 0 },
        { q: "He ___ his cold.", o: ["got over", "got into", "got off", "got up"], a: 0 },
        { q: "She ___ the form carefully.", o: ["filled in", "filled out", "filled up", "filled off"], a: 0 },
        { q: "They ___ the meeting until Friday.", o: ["put off", "put on", "put up", "put in"], a: 0 },
        { q: "I can't ___ this noise anymore.", o: ["put up with", "put on", "put off", "put in"], a: 0 },
        { q: "She ___ a new hobby.", o: ["took up", "took off", "took on", "took in"], a: 0 },
        { q: "He ___ his father in many ways.", o: ["takes after", "takes on", "takes off", "takes in"], a: 0 },
        { q: "We ___ of milk. Please buy some.", o: ["ran out", "ran away", "ran off", "ran into"], a: 0 },
        { q: "She ___ the invitation.", o: ["turned down", "turned on", "turned off", "turned up"], a: 0 },
        { q: "Please ___ the light when you leave.", o: ["turn off", "turn on", "turn up", "turn down"], a: 0 },
        { q: "She ___ the truth eventually.", o: ["found out", "found on", "found off", "found in"], a: 0 },
        { q: "He ___ with the flu.", o: ["came down", "came up", "turned off", "turned on"], a: 0 },
        { q: "We need to ___ a solution.", o: ["come up with", "come down with", "turn on", "go in"], a: 0 },
        { q: "He ___ his jacket because it was hot.", o: ["took off", "took on", "took up", "took in"], a: 0 },
        { q: "We should ___ expenses this month.", o: ["cut down on", "cut off", "cut in", "turn on"], a: 0 },
        { q: "She ___ a story for the children.", o: ["made up", "made on", "made off", "made in"], a: 0 },
        { q: "We ___ for dinner at 7.", o: ["went out", "went in", "went up", "went off"], a: 0 },
        { q: "She quickly ___ the mess.", o: ["cleaned up", "cleaned out", "cleaned in", "cleaned off"], a: 0 },
        { q: "He ___ to be a good cook.", o: ["turned out", "turned on", "turned off", "turned up"], a: 0 },
        { q: "We ___ our holiday plans.", o: ["sorted out", "sorted on", "sorted off", "sorted in"], a: 0 },
        { q: "She ___ a brilliant idea at the meeting.", o: ["brought up", "brought in", "brought on", "brought over"], a: 0 },
        { q: "He couldn't ___ the long flight.", o: ["put up with", "put off", "put out", "put on"], a: 0 },
        { q: "I need to ___ my essay before I hand it in.", o: ["go over", "go on", "go up", "go off"], a: 0 },
        { q: "The alarm ___ at 6 AM.", o: ["went off", "went on", "went up", "went out"], a: 0 },
        { q: "She ___ learning Japanese after a month.", o: ["gave up", "gave in", "gave out", "gave away"], a: 0 },
        { q: "He ___ a lot of weight last year.", o: ["put on", "put off", "put up", "put out"], a: 0 },
        { q: "They ___ their differences and became friends.", o: ["got over", "got on", "got up", "got off"], a: 0 },
        { q: "The manager ___ a new employee last week.", o: ["took on", "took off", "took up", "took in"], a: 0 },
        { q: "She always ___ her friends when they need help.", o: ["stands by", "stands up", "stands off", "stands out"], a: 0 },
        { q: "He ___ the presentation very well.", o: ["pulled off", "pulled up", "pulled in", "pulled on"], a: 0 },
        { q: "They ___ the fire quickly.", o: ["put out", "put off", "put on", "put up"], a: 0 },
        { q: "She ___ her application before the deadline.", o: ["handed in", "handed out", "handed off", "handed up"], a: 0 },
        { q: "He ___ several articles for the magazine.", o: ["turned in", "turned up", "turned out", "turned off"], a: 0 },
        { q: "I ___ my old teacher in the supermarket.", o: ["ran into", "ran away", "ran off", "ran out"], a: 0 },
        { q: "She ___ learning piano as a child.", o: ["took up", "took off", "took in", "took on"], a: 0 },
        { q: "They needed to ___ where to go.", o: ["work out", "work on", "work in", "work off"], a: 0 },
        { q: "He ___ the job offer because the salary was low.", o: ["turned down", "turned off", "turned up", "turned out"], a: 0 },
        { q: "The concert ___ to be a great success.", o: ["turned out", "turned off", "turned on", "turned up"], a: 0 },
        { q: "She ___ the children during the school holiday.", o: ["looked after", "looked up", "looked into", "looked out"], a: 0 },
      ],
      'Past Perfect': [
        { q: "By the time I arrived, she ___ already left.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "He was tired because he ___ worked all day.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "They ___ finished dinner before the guests arrived.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "She ___ never seen snow before that winter.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "I realised I ___ forgotten my wallet.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "He told me he ___ studied in London.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "By 2010, they ___ sold over a million books.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "She was upset because she ___ lost the match.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "When I woke up, the rain ___.", o: ["had stopped", "stopped", "has stopped", "did stop"], a: 0 },
        { q: "He couldn't enter because he ___ forgotten the code.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "We ___ not eaten anything since morning.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "She remembered that she ___ met him before.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "By the time we arrived, the film ___.", o: ["had started", "started", "has started", "starts"], a: 0 },
        { q: "He looked tired because he ___ slept well.", o: ["hadn't", "hasn't", "wasn't", "didn't"], a: 0 },
        { q: "I was happy because I ___ passed my exam.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "She ___ just finished cooking when he came home.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "They knew each other because they ___ worked together.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "He couldn't answer because he ___ not studied.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "By last year she ___ been teaching for 20 years.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "I found the letter that I ___ been looking for.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "After he ___ finished the report, he sent it.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "She was nervous because she ___ never flown before.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "They left before we ___ a chance to speak.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "He admitted that he ___ made a mistake.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "When the police arrived, the thief ___.", o: ["had escaped", "escaped", "has escaped", "escapes"], a: 0 },
        { q: "I ___ never tried sushi before that trip.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "She told us she ___ visited the museum before.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "He was angry because they ___ lied to him.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "Once she ___ graduated, she started working.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "They ___ saved enough money before buying the house.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "She realised she ___ left the keys at home.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "He felt proud because he ___ worked hard.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "By the time she called, I ___ fallen asleep.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "We were surprised because nobody ___ warned us.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "She denied that she ___ taken the money.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "He was the best player they ___ ever seen.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "I returned the book because I ___ read it.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "She explained that she ___ missed the bus.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "They couldn't find the document because someone ___ moved it.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "After we ___ eaten, we went for a walk.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "He was relieved when he found out she ___.", o: ["had arrived", "arrived", "has arrived", "arrives"], a: 0 },
        { q: "She thanked him for what he ___ done.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "The guests ___ already left when we called.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "I knew I ___ met her somewhere before.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "By midnight he ___ written ten pages.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "She was sad because she ___ lost her cat.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "After they ___ spoken, they felt much better.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "He discovered that someone ___ broken in.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "Before the match, they ___ trained for months.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "She apologised because she ___ forgotten his name.", o: ["had", "has", "was", "did"], a: 0 },
      ],
      'Future Continuous': [
        { q: "At 8 PM tomorrow, I ___ watching the match.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "She ___ working all day tomorrow.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "They ___ travelling at this time next week.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "He ___ sleeping when you call.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "We ___ having lunch at noon.", o: ["will be", "would be", "are", "shall"], a: 0 },
        { q: "I ___ thinking about you.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "She ___ not working this time tomorrow.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "They ___ studying for their exams all week.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "He ___ driving at midnight.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "___ you using the car tomorrow?", o: ["Will you be", "Would you be", "Are you", "Shall you"], a: 0 },
        { q: "By 6 PM, she ___ still working.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "At this time tomorrow, I ___ flying to Spain.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "They ___ waiting for us when we arrive.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "He ___ practising guitar all evening.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "We ___ celebrating our anniversary next week.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "I ___ not using the laptop all day.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "She ___ cooking when you arrive.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "___ he working next Monday?", o: ["Will he be", "Would he be", "Is he", "Shall he"], a: 0 },
        { q: "By this evening, they ___ finishing the report.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "I ___ waiting for you outside.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "She ___ teaching the advanced class tomorrow.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "At midnight, he ___ still working.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "We ___ attending the conference all week.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "They ___ competing in the race.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "I ___ reading in the garden tomorrow afternoon.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "She ___ presenting her findings at noon.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "___ they playing when we arrive?", o: ["Will they be", "Would they be", "Are they", "Shall they"], a: 0 },
        { q: "He ___ not sleeping at this time tonight.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "By 9 AM, she ___ running in the park.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "We ___ watching the news at 7.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "I ___ working from home tomorrow.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "She ___ attending the conference next week.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "They ___ moving into the new apartment.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "He ___ speaking at the event.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "___ she joining us for dinner?", o: ["Will she be", "Would she be", "Is she", "Shall she"], a: 0 },
        { q: "At 10 tomorrow, I ___ meeting the director.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "He ___ coaching the junior team next season.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "We ___ renovating the kitchen all month.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "She ___ interviewing candidates all morning.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "They ___ sailing around the coast next summer.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "I ___ revising for my exams all weekend.", o: ["will be", "would be", "am", "shall"], a: 0 },
        { q: "He ___ visiting relatives during the holidays.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "She ___ running the marathon next month.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "By 3 PM, they ___ finishing the construction.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "___ I disturbing you if I call at 8?", o: ["Will I be", "Would I be", "Am I", "Shall I"], a: 0 },
        { q: "She ___ taking the train at this time.", o: ["will be", "would be", "is", "shall be"], a: 0 },
        { q: "We ___ enjoying the concert this evening.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "He ___ not coming to school tomorrow.", o: ["will be", "would be", "is", "shall"], a: 0 },
        { q: "They ___ discussing the plan at the meeting.", o: ["will be", "would be", "are", "shall be"], a: 0 },
        { q: "I ___ arriving at the airport at noon.", o: ["will be", "would be", "am", "shall"], a: 0 },
      ],
      'Gerunds & Infinitives': [
        { q: "I enjoy ___ books.", o: ["reading", "to read", "read", "readed"], a: 0 },
        { q: "She wants ___ a doctor.", o: ["to be", "being", "be", "been"], a: 0 },
        { q: "He avoided ___ the question.", o: ["answering", "to answer", "answer", "answered"], a: 0 },
        { q: "We decided ___ to the beach.", o: ["to go", "going", "go", "gone"], a: 0 },
        { q: "They finished ___ the report.", o: ["writing", "to write", "write", "written"], a: 0 },
        { q: "She hopes ___ abroad next year.", o: ["to study", "studying", "study", "studied"], a: 0 },
        { q: "He admitted ___ the money.", o: ["taking", "to take", "take", "taken"], a: 0 },
        { q: "I can't stand ___ late.", o: ["waiting", "to wait", "wait", "waited"], a: 0 },
        { q: "She agreed ___ help us.", o: ["to", "—", "for", "at"], a: 0 },
        { q: "He suggested ___ to the cinema.", o: ["going", "to go", "go", "gone"], a: 0 },
        { q: "I promise ___ you soon.", o: ["to call", "calling", "call", "called"], a: 0 },
        { q: "She keeps ___ the same mistakes.", o: ["making", "to make", "make", "made"], a: 0 },
        { q: "He refused ___ his homework.", o: ["to do", "doing", "do", "done"], a: 0 },
        { q: "I love ___ in the morning.", o: ["running", "to run", "run", "ran"], a: 0 },
        { q: "She managed ___ the exam.", o: ["to pass", "passing", "pass", "passed"], a: 0 },
        { q: "He denied ___ there.", o: ["being", "to be", "be", "been"], a: 0 },
        { q: "They plan ___ a new company.", o: ["to start", "starting", "start", "started"], a: 0 },
        { q: "I miss ___ with my old friends.", o: ["spending time", "to spend time", "spend time", "spent time"], a: 0 },
        { q: "She learnt ___ at age four.", o: ["to read", "reading", "read", "readed"], a: 0 },
        { q: "He couldn't help ___ at the joke.", o: ["laughing", "to laugh", "laugh", "laughed"], a: 0 },
        { q: "I need ___ you something important.", o: ["to tell", "telling", "tell", "told"], a: 0 },
        { q: "She practises ___ every day.", o: ["singing", "to sing", "sing", "sang"], a: 0 },
        { q: "He pretended ___ asleep.", o: ["to be", "being", "be", "been"], a: 0 },
        { q: "I enjoy ___ to jazz music.", o: ["listening", "to listen", "listen", "listened"], a: 0 },
        { q: "They expect ___ on Friday.", o: ["to arrive", "arriving", "arrive", "arrived"], a: 0 },
        { q: "She stopped ___ last year.", o: ["smoking", "to smoke", "smoke", "smoked"], a: 0 },
        { q: "He is considering ___ abroad.", o: ["studying", "to study", "study", "studied"], a: 0 },
        { q: "I would like ___ you again.", o: ["to see", "seeing", "see", "seen"], a: 0 },
        { q: "She dislikes ___ early.", o: ["waking up", "to wake up", "wake up", "woke up"], a: 0 },
        { q: "He aims ___ the top prize.", o: ["to win", "winning", "win", "won"], a: 0 },
        { q: "They reported ___ the crime.", o: ["having seen", "to see", "see", "seen"], a: 0 },
        { q: "I suggest ___ a taxi instead.", o: ["taking", "to take", "take", "taken"], a: 0 },
        { q: "She tends ___ overthink things.", o: ["to", "—", "for", "at"], a: 0 },
        { q: "He is looking forward to ___ you.", o: ["meeting", "to meet", "meet", "met"], a: 0 },
        { q: "I regret ___ that I can't help.", o: ["to say", "saying", "say", "said"], a: 0 },
        { q: "She began ___ when she heard the news.", o: ["crying", "to cry", "cry", "cried"], a: 0 },
        { q: "He is used to ___ up early.", o: ["getting", "to get", "get", "got"], a: 0 },
        { q: "They prefer ___ at home.", o: ["staying", "to stay", "stay", "stayed"], a: 0 },
        { q: "I forgot ___ the door.", o: ["to lock", "locking", "lock", "locked"], a: 0 },
        { q: "She loves ___ Italian food.", o: ["eating", "to eat", "eat", "ate"], a: 0 },
        { q: "He agreed ___ the contract.", o: ["to sign", "signing", "sign", "signed"], a: 0 },
        { q: "They postponed ___ the meeting.", o: ["holding", "to hold", "hold", "held"], a: 0 },
        { q: "I attempted ___ the mountain.", o: ["to climb", "climbing", "climb", "climbed"], a: 0 },
        { q: "She keeps ___ to play that song.", o: ["asking me", "ask me", "to ask me", "asked me"], a: 0 },
        { q: "He managed ___ the problem.", o: ["to solve", "solving", "solve", "solved"], a: 0 },
        { q: "They decided against ___ the house.", o: ["selling", "to sell", "sell", "sold"], a: 0 },
        { q: "I remember ___ the letter.", o: ["posting", "to post", "post", "posted"], a: 0 },
        { q: "She threatened ___ the police.", o: ["to call", "calling", "call", "called"], a: 0 },
        { q: "He avoided ___ the new road.", o: ["using", "to use", "use", "used"], a: 0 },
        { q: "We are committed to ___ quality.", o: ["delivering", "to deliver", "deliver", "delivered"], a: 0 },
      ],
      'Question Tags': [
        { q: "It's a nice day, ___?", o: ["isn't it", "is it", "wasn't it", "was it"], a: 0 },
        { q: "You are coming, ___?", o: ["aren't you", "are you", "don't you", "won't you"], a: 0 },
        { q: "She can swim, ___?", o: ["can't she", "isn't she", "doesn't she", "can she"], a: 0 },
        { q: "They have finished, ___?", o: ["haven't they", "didn't they", "aren't they", "don't they"], a: 0 },
        { q: "He doesn't know, ___?", o: ["does he", "doesn't he", "isn't he", "wasn't he"], a: 0 },
        { q: "You weren't listening, ___?", o: ["were you", "weren't you", "did you", "didn't you"], a: 0 },
        { q: "She won't be late, ___?", o: ["will she", "won't she", "is she", "isn't she"], a: 0 },
        { q: "We should leave now, ___?", o: ["shouldn't we", "should we", "don't we", "aren't we"], a: 0 },
        { q: "He has been here before, ___?", o: ["hasn't he", "has he", "didn't he", "isn't he"], a: 0 },
        { q: "You haven't seen this film, ___?", o: ["have you", "haven't you", "did you", "didn't you"], a: 0 },
        { q: "Let's go to the cinema, ___?", o: ["shall we", "will we", "don't we", "won't we"], a: 0 },
        { q: "They didn't arrive on time, ___?", o: ["did they", "didn't they", "were they", "aren't they"], a: 0 },
        { q: "She would help us, ___?", o: ["wouldn't she", "would she", "will she", "won't she"], a: 0 },
        { q: "You could speak Russian once, ___?", o: ["couldn't you", "could you", "weren't you", "didn't you"], a: 0 },
        { q: "There are enough chairs, ___?", o: ["aren't there", "are there", "isn't there", "is there"], a: 0 },
        { q: "I'm doing well, ___?", o: ["aren't I", "am I", "isn't it", "don't I"], a: 0 },
        { q: "He used to live here, ___?", o: ["didn't he", "used he", "wasn't he", "hasn't he"], a: 0 },
        { q: "Nothing went wrong, ___?", o: ["did it", "didn't it", "was it", "weren't they"], a: 0 },
        { q: "You will help me, ___?", o: ["won't you", "will you", "don't you", "wouldn't you"], a: 0 },
        { q: "She hasn't eaten yet, ___?", o: ["has she", "hasn't she", "is she", "did she"], a: 0 },
        { q: "We were right, ___?", o: ["weren't we", "were we", "didn't we", "aren't we"], a: 0 },
        { q: "He didn't call you, ___?", o: ["did he", "didn't he", "has he", "was he"], a: 0 },
        { q: "They can finish on time, ___?", o: ["can't they", "can they", "don't they", "won't they"], a: 0 },
        { q: "You've met my sister, ___?", o: ["haven't you", "have you", "weren't you", "didn't you"], a: 0 },
        { q: "She was disappointed, ___?", o: ["wasn't she", "was she", "isn't she", "didn't she"], a: 0 },
        { q: "He must be tired, ___?", o: ["mustn't he", "must he", "isn't he", "was he"], a: 0 },
        { q: "We needn't worry, ___?", o: ["need we", "do we", "should we", "must we"], a: 0 },
        { q: "Open the window, ___?", o: ["will you", "shall we", "won't we", "aren't you"], a: 0 },
        { q: "Everybody came, ___?", o: ["didn't they", "did they", "weren't they", "were they"], a: 0 },
        { q: "This is your bag, ___?", o: ["isn't it", "is it", "wasn't it", "wasn't this"], a: 0 },
        { q: "You speak English, ___?", o: ["don't you", "do you", "are you", "aren't you"], a: 0 },
        { q: "She sang beautifully, ___?", o: ["didn't she", "did she", "wasn't she", "was she"], a: 0 },
        { q: "We haven't been introduced, ___?", o: ["have we", "haven't we", "were we", "weren't we"], a: 0 },
        { q: "He could have been there, ___?", o: ["couldn't he", "could he", "wasn't he", "was he"], a: 0 },
        { q: "They won't tell anyone, ___?", o: ["will they", "won't they", "do they", "don't they"], a: 0 },
        { q: "You'd rather stay home, ___?", o: ["wouldn't you", "would you", "hadn't you", "hadn't you"], a: 0 },
        { q: "She should apologise, ___?", o: ["shouldn't she", "should she", "wasn't she", "didn't she"], a: 0 },
        { q: "Nobody phoned, ___?", o: ["did they", "didn't they", "was there", "wasn't there"], a: 0 },
        { q: "The match is on Saturday, ___?", o: ["isn't it", "is it", "wasn't it", "was it"], a: 0 },
        { q: "You had never met her before, ___?", o: ["had you", "hadn't you", "did you", "didn't you"], a: 0 },
        { q: "They might come, ___?", o: ["mightn't they", "might they", "won't they", "will they"], a: 0 },
        { q: "We ought to leave early, ___?", o: ["oughtn't we", "ought we", "shouldn't we", "should we"], a: 0 },
        { q: "It wasn't raining, ___?", o: ["was it", "wasn't it", "did it", "didn't it"], a: 0 },
        { q: "She hasn't called, ___?", o: ["has she", "hasn't she", "did she", "didn't she"], a: 0 },
        { q: "They were at school, ___?", o: ["weren't they", "were they", "didn't they", "aren't they"], a: 0 },
        { q: "He used to eat here, ___?", o: ["didn't he", "did he", "hasn't he", "had he"], a: 0 },
        { q: "You don't mind, ___?", o: ["do you", "don't you", "are you", "aren't you"], a: 0 },
        { q: "It had been a long day, ___?", o: ["hadn't it", "had it", "wasn't it", "was it"], a: 0 },
        { q: "We must leave now, ___?", o: ["mustn't we", "must we", "shouldn't we", "should we"], a: 0 },
        { q: "She would prefer tea, ___?", o: ["wouldn't she", "would she", "will she", "won't she"], a: 0 },
      ],
      'Wish & If Only': [
        { q: "I wish I ___ taller.", o: ["were", "am", "will be", "would be"], a: 0 },
        { q: "She wishes she ___ more time.", o: ["had", "has", "would have", "will have"], a: 0 },
        { q: "If only he ___ harder.", o: ["worked", "works", "will work", "would work"], a: 0 },
        { q: "I wish I ___ to the party.", o: ["had gone", "went", "have gone", "go"], a: 0 },
        { q: "She wishes she ___ the mistake.", o: ["hadn't made", "didn't make", "hasn't made", "won't make"], a: 0 },
        { q: "If only it ___ raining.", o: ["would stop", "stops", "stopped", "has stopped"], a: 0 },
        { q: "He wishes he ___ drive.", o: ["could", "can", "would", "will"], a: 0 },
        { q: "I wish you ___ make so much noise.", o: ["wouldn't", "won't", "don't", "didn't"], a: 0 },
        { q: "If only I ___ the answer.", o: ["knew", "know", "would know", "will know"], a: 0 },
        { q: "She wishes things ___ different.", o: ["were", "are", "will be", "would be"], a: 0 },
        { q: "I wish I ___ spoken to him.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "He wishes he ___ so rude.", o: ["hadn't been", "wasn't", "hasn't been", "won't be"], a: 0 },
        { q: "If only she ___ here now.", o: ["were", "is", "would be", "will be"], a: 0 },
        { q: "I wish I ___ remember his name.", o: ["could", "can", "would", "will"], a: 0 },
        { q: "She wishes she ___ in Paris.", o: ["lived", "lives", "would live", "will live"], a: 0 },
        { q: "If only we ___ more money.", o: ["had", "have", "would have", "will have"], a: 0 },
        { q: "He wishes he ___ the race.", o: ["had won", "won", "has won", "wins"], a: 0 },
        { q: "I wish the weather ___ better.", o: ["were", "is", "would be", "will be"], a: 0 },
        { q: "If only I ___ earlier.", o: ["had left", "left", "have left", "leave"], a: 0 },
        { q: "She wishes she ___ play the piano.", o: ["could", "can", "would", "will"], a: 0 },
        { q: "I wish he ___ stop interrupting.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "If only they ___ us the truth.", o: ["had told", "told", "have told", "tell"], a: 0 },
        { q: "He wishes he ___ taken the job.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "I wish I ___ so busy.", o: ["weren't", "am not", "won't be", "wouldn't be"], a: 0 },
        { q: "She wishes she ___ the exam.", o: ["had passed", "passed", "has passed", "passes"], a: 0 },
        { q: "If only we ___ more careful.", o: ["had been", "were", "have been", "are"], a: 0 },
        { q: "I wish I ___ fly.", o: ["could", "can", "would", "will"], a: 0 },
        { q: "He wishes he ___ a doctor.", o: ["were", "is", "would be", "will be"], a: 0 },
        { q: "If only she ___ called me.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "I wish I ___ spent more time with them.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "She wishes she ___ live abroad.", o: ["could", "can", "would", "will"], a: 0 },
        { q: "If only he ___ so stubborn.", o: ["weren't", "isn't", "won't be", "wouldn't be"], a: 0 },
        { q: "I wish the concert ___ cancelled.", o: ["hadn't been", "wasn't", "hasn't been", "won't be"], a: 0 },
        { q: "She wishes her parents ___ understood her better.", o: ["had", "have", "were", "did"], a: 0 },
        { q: "If only I ___ what to say.", o: ["knew", "know", "would know", "will know"], a: 0 },
        { q: "He wishes he ___ made a different choice.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "I wish you ___ here with me.", o: ["were", "are", "would be", "will be"], a: 0 },
        { q: "She wishes she ___ bought that house.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "If only we ___ away for the weekend.", o: ["could go", "can go", "will go", "shall go"], a: 0 },
        { q: "I wish it ___ stop raining.", o: ["would", "will", "can", "shall"], a: 0 },
        { q: "He wishes he ___ to that school.", o: ["had gone", "went", "has gone", "goes"], a: 0 },
        { q: "If only she ___ her phone today.", o: ["hadn't left", "didn't leave", "hasn't left", "won't leave"], a: 0 },
        { q: "I wish I ___ the right thing.", o: ["had done", "did", "have done", "do"], a: 0 },
        { q: "She wishes she ___ listened to her parents.", o: ["had", "has", "was", "did"], a: 0 },
        { q: "If only they ___ a better plan.", o: ["had had", "had", "have", "would have"], a: 0 },
        { q: "I wish this moment ___ last forever.", o: ["could", "can", "would", "will"], a: 0 },
        { q: "He wishes his sister ___ nearby.", o: ["lived", "lives", "would live", "will live"], a: 0 },
        { q: "If only I ___ worked harder at school.", o: ["had", "have", "was", "did"], a: 0 },
        { q: "She wishes she ___ so shy.", o: ["weren't", "isn't", "won't be", "wouldn't be"], a: 0 },
        { q: "I wish I ___ that last piece of cake.", o: ["hadn't eaten", "didn't eat", "haven't eaten", "won't eat"], a: 0 },
      ],
    };

    // ============================================================
    // VOCABULARY
    // ============================================================
    const VOCAB = [
      { en: "hello", ru: "привет", uz: "salom", tj: "салом", cat: "greeting" },
      { en: "goodbye", ru: "до свидания", uz: "xayr", tj: "хайр", cat: "greeting" },
      { en: "thank you", ru: "спасибо", uz: "rahmat", tj: "ташаккур", cat: "greeting" },
      { en: "please", ru: "пожалуйста", uz: "iltimos", tj: "лутфан", cat: "greeting" },
      { en: "sorry", ru: "извините", uz: "kechirasiz", tj: "бубахшед", cat: "greeting" },
      { en: "yes", ru: "да", uz: "ha", tj: "ҳа", cat: "basic" },
      { en: "no", ru: "нет", uz: "yo'q", tj: "не", cat: "basic" },
      { en: "water", ru: "вода", uz: "suv", tj: "об", cat: "food" },
      { en: "bread", ru: "хлеб", uz: "non", tj: "нон", cat: "food" },
      { en: "milk", ru: "молоко", uz: "sut", tj: "шир", cat: "food" },
      { en: "apple", ru: "яблоко", uz: "olma", tj: "себ", cat: "food" },
      { en: "coffee", ru: "кофе", uz: "qahva", tj: "қаҳва", cat: "food" },
      { en: "tea", ru: "чай", uz: "choy", tj: "чой", cat: "food" },
      { en: "rice", ru: "рис", uz: "guruch", tj: "биринҷ", cat: "food" },
      { en: "meat", ru: "мясо", uz: "go'sht", tj: "гӯшт", cat: "food" },
      { en: "house", ru: "дом", uz: "uy", tj: "хона", cat: "place" },
      { en: "school", ru: "школа", uz: "maktab", tj: "мактаб", cat: "place" },
      { en: "hospital", ru: "больница", uz: "kasalxona", tj: "беморхона", cat: "place" },
      { en: "office", ru: "офис", uz: "ofis", tj: "офис", cat: "place" },
      { en: "airport", ru: "аэропорт", uz: "aeroporti", tj: "фурудгоҳ", cat: "place" },
      { en: "book", ru: "книга", uz: "kitob", tj: "китоб", cat: "education" },
      { en: "teacher", ru: "учитель", uz: "o'qituvchi", tj: "муаллим", cat: "education" },
      { en: "student", ru: "студент", uz: "talaba", tj: "донишҷӯ", cat: "education" },
      { en: "homework", ru: "домашнее задание", uz: "uy ishi", tj: "вазифаи хона", cat: "education" },
      { en: "exam", ru: "экзамен", uz: "imtihon", tj: "имтиҳон", cat: "education" },
      { en: "dictionary", ru: "словарь", uz: "lug'at", tj: "луғат", cat: "education" },
      { en: "mother", ru: "мать", uz: "ona", tj: "модар", cat: "family" },
      { en: "father", ru: "отец", uz: "ota", tj: "падар", cat: "family" },
      { en: "brother", ru: "брат", uz: "aka", tj: "бародар", cat: "family" },
      { en: "sister", ru: "сестра", uz: "opa", tj: "хоҳар", cat: "family" },
      { en: "daughter", ru: "дочь", uz: "qiz", tj: "духтар", cat: "family" },
      { en: "son", ru: "сын", uz: "o'g'il", tj: "писар", cat: "family" },
      { en: "grandfather", ru: "дедушка", uz: "bobo", tj: "бобо", cat: "family" },
      { en: "grandmother", ru: "бабушка", uz: "buvi", tj: "момо", cat: "family" },
      { en: "friend", ru: "друг", uz: "do'st", tj: "дӯст", cat: "people" },
      { en: "child", ru: "ребёнок", uz: "bola", tj: "кӯдак", cat: "people" },
      { en: "man", ru: "мужчина", uz: "erkak", tj: "мард", cat: "people" },
      { en: "woman", ru: "женщина", uz: "ayol", tj: "зан", cat: "people" },
      { en: "boss", ru: "начальник", uz: "boshliq", tj: "раис", cat: "people" },
      { en: "neighbour", ru: "сосед", uz: "qo'shni", tj: "ҳамсоя", cat: "people" },
      { en: "day", ru: "день", uz: "kun", tj: "рӯз", cat: "time" },
      { en: "night", ru: "ночь", uz: "tun", tj: "шаб", cat: "time" },
      { en: "morning", ru: "утро", uz: "ertalab", tj: "субҳ", cat: "time" },
      { en: "evening", ru: "вечер", uz: "kechqurun", tj: "бегоҳ", cat: "time" },
      { en: "today", ru: "сегодня", uz: "bugun", tj: "имрӯз", cat: "time" },
      { en: "tomorrow", ru: "завтра", uz: "ertaga", tj: "фардо", cat: "time" },
      { en: "yesterday", ru: "вчера", uz: "kecha", tj: "дирӯз", cat: "time" },
      { en: "week", ru: "неделя", uz: "hafta", tj: "ҳафта", cat: "time" },
      { en: "month", ru: "месяц", uz: "oy", tj: "моҳ", cat: "time" },
      { en: "year", ru: "год", uz: "yil", tj: "сол", cat: "time" },
      { en: "big", ru: "большой", uz: "katta", tj: "калон", cat: "adjective" },
      { en: "small", ru: "маленький", uz: "kichik", tj: "хурд", cat: "adjective" },
      { en: "good", ru: "хороший", uz: "yaxshi", tj: "хуб", cat: "adjective" },
      { en: "bad", ru: "плохой", uz: "yomon", tj: "бад", cat: "adjective" },
      { en: "beautiful", ru: "красивый", uz: "chiroyli", tj: "зебо", cat: "adjective" },
      { en: "happy", ru: "счастливый", uz: "baxtli", tj: "хушбахт", cat: "adjective" },
      { en: "sad", ru: "грустный", uz: "g'amgin", tj: "ғамгин", cat: "adjective" },
      { en: "hot", ru: "горячий", uz: "issiq", tj: "гарм", cat: "adjective" },
      { en: "cold", ru: "холодный", uz: "sovuq", tj: "хунук", cat: "adjective" },
      { en: "tired", ru: "уставший", uz: "charchagan", tj: "хаста", cat: "adjective" },
      { en: "eat", ru: "есть", uz: "yemoq", tj: "хӯрдан", cat: "verb" },
      { en: "drink", ru: "пить", uz: "ichmoq", tj: "нӯшидан", cat: "verb" },
      { en: "sleep", ru: "спать", uz: "uxlamoq", tj: "хобидан", cat: "verb" },
      { en: "walk", ru: "ходить", uz: "yurmoq", tj: "роҳ рафтан", cat: "verb" },
      { en: "run", ru: "бежать", uz: "yugurmoq", tj: "давидан", cat: "verb" },
      { en: "read", ru: "читать", uz: "o'qimoq", tj: "хондан", cat: "verb" },
      { en: "write", ru: "писать", uz: "yozmoq", tj: "навиштан", cat: "verb" },
      { en: "speak", ru: "говорить", uz: "gapirmoq", tj: "гап задан", cat: "verb" },
      { en: "listen", ru: "слушать", uz: "tinglamoq", tj: "гӯш кардан", cat: "verb" },
      { en: "work", ru: "работать", uz: "ishlamoq", tj: "кор кардан", cat: "verb" },
      { en: "study", ru: "учиться", uz: "o'qimoq", tj: "хондан", cat: "verb" },
      { en: "understand", ru: "понимать", uz: "tushunmoq", tj: "фаҳмидан", cat: "verb" },
      { en: "remember", ru: "помнить", uz: "eslamoq", tj: "дар ёд доштан", cat: "verb" },
      { en: "forget", ru: "забывать", uz: "unutmoq", tj: "фаромӯш кардан", cat: "verb" },
      { en: "car", ru: "машина", uz: "mashina", tj: "мошин", cat: "transport" },
      { en: "bus", ru: "автобус", uz: "avtobus", tj: "автобус", cat: "transport" },
      { en: "train", ru: "поезд", uz: "poyezd", tj: "поезд", cat: "transport" },
      { en: "airplane", ru: "самолёт", uz: "samolyot", tj: "ҳавопаймо", cat: "transport" },
      { en: "bicycle", ru: "велосипед", uz: "velosiped", tj: "дучарха", cat: "transport" },
      { en: "dog", ru: "собака", uz: "it", tj: "саг", cat: "animal" },
      { en: "cat", ru: "кошка", uz: "mushuk", tj: "гурба", cat: "animal" },
      { en: "bird", ru: "птица", uz: "qush", tj: "парранда", cat: "animal" },
      { en: "fish", ru: "рыба", uz: "baliq", tj: "моҳӣ", cat: "animal" },
      { en: "horse", ru: "лошадь", uz: "ot", tj: "асп", cat: "animal" },
      { en: "lion", ru: "лев", uz: "sher", tj: "шер", cat: "animal" },
      { en: "red", ru: "красный", uz: "qizil", tj: "сурх", cat: "color" },
      { en: "blue", ru: "синий", uz: "ko'k", tj: "кабуд", cat: "color" },
      { en: "green", ru: "зелёный", uz: "yashil", tj: "сабз", cat: "color" },
      { en: "white", ru: "белый", uz: "oq", tj: "сафед", cat: "color" },
      { en: "black", ru: "чёрный", uz: "qora", tj: "сиёҳ", cat: "color" },
      { en: "yellow", ru: "жёлтый", uz: "sariq", tj: "зард", cat: "color" },
      { en: "sun", ru: "солнце", uz: "quyosh", tj: "офтоб", cat: "nature" },
      { en: "moon", ru: "луна", uz: "oy", tj: "моҳ", cat: "nature" },
      { en: "rain", ru: "дождь", uz: "yomg'ir", tj: "борон", cat: "nature" },
      { en: "snow", ru: "снег", uz: "qor", tj: "барф", cat: "nature" },
      { en: "wind", ru: "ветер", uz: "shamol", tj: "шамол", cat: "nature" },
      { en: "tree", ru: "дерево", uz: "daraxt", tj: "дарахт", cat: "nature" },
      { en: "flower", ru: "цветок", uz: "gul", tj: "гул", cat: "nature" },
      { en: "mountain", ru: "гора", uz: "tog'", tj: "кӯҳ", cat: "nature" },
      { en: "river", ru: "река", uz: "daryo", tj: "дарё", cat: "nature" },
      { en: "sea", ru: "море", uz: "dengiz", tj: "баҳр", cat: "nature" },
      { en: "ambitious", ru: "амбициозный", uz: "maqsadli", tj: "баландпарвоз", cat: "advanced" },
      { en: "accomplish", ru: "достигать", uz: "erishmoq", tj: "ноил шудан", cat: "advanced" },
      { en: "consequently", ru: "следовательно", uz: "natijada", tj: "аз ин рӯ", cat: "advanced" },
      { en: "nevertheless", ru: "тем не менее", uz: "shunga qaramay", tj: "бо вуҷуди ин", cat: "advanced" },
      { en: "approximately", ru: "приблизительно", uz: "taxminan", tj: "тахминан", cat: "advanced" },
      { en: "negotiate", ru: "переговоры вести", uz: "muzokaralar olib bormoq", tj: "гуфтушунид кардан", cat: "advanced" },
      { en: "efficient", ru: "эффективный", uz: "samarali", tj: "самаранок", cat: "advanced" },
      { en: "crucial", ru: "ключевой", uz: "muhim", tj: "муҳим", cat: "advanced" },
      { en: "perspective", ru: "перспектива", uz: "nuqtai nazar", tj: "дидгоҳ", cat: "advanced" },
      { en: "sustainable", ru: "устойчивый", uz: "barqaror", tj: "устувор", cat: "advanced" },
    ];

    // ============================================================
    // READING PASSAGES
    // ============================================================
    const READING = [
      {
        title: "A Day in the Park",
        text: "Sara woke up early on Saturday morning. The sun was shining brightly, and she decided to go to the park. She took a sandwich, an apple, and a bottle of water in her bag. At the park, she sat under a large oak tree and read her favourite book. Children were playing on the swings and slides. A small dog was running across the grass, chasing a red ball. Sara felt calm and happy. She stayed in the park until the sun began to set, painting the sky in beautiful shades of orange and pink. It was a perfect day.",
        qs: [
          { q: "When did Sara wake up?", o: ["Saturday morning", "Sunday morning", "Friday evening", "Monday morning"], a: 0 },
          { q: "What did Sara bring?", o: ["Sandwich, apple, water", "Pizza, juice, chips", "Rice, chicken, soda", "Bread, cheese, milk"], a: 0 },
          { q: "Where did she sit?", o: ["Under an oak tree", "On a bench", "By a lake", "On the grass"], a: 0 },
          { q: "What was the dog chasing?", o: ["A red ball", "A cat", "A bird", "A stick"], a: 0 },
          { q: "How did Sara feel?", o: ["Calm and happy", "Tired and bored", "Sad and lonely", "Angry and upset"], a: 0 },
        ]
      },
      {
        title: "The New Student",
        text: "On his first day at the new school, Tom was nervous. He walked through the big gates and looked around. The building was much bigger than his old school. A friendly boy named Alex came up to him and said, 'Hi! Are you new? I can show you around.' Tom smiled and felt relieved. Alex showed him the classrooms, the library, the canteen, and the sports field. By lunchtime, Tom had already made three new friends. He realized that starting at a new school was not as scary as he had thought. Sometimes changes can be wonderful.",
        qs: [
          { q: "How did Tom feel on his first day?", o: ["Nervous", "Excited", "Angry", "Bored"], a: 0 },
          { q: "Who helped Tom?", o: ["Alex", "Sam", "Mike", "John"], a: 0 },
          { q: "What did Alex show Tom?", o: ["Classrooms, library, canteen, sports field", "Only the classroom", "The car park", "The staff room"], a: 0 },
          { q: "How many friends did Tom make by lunch?", o: ["Three", "Two", "Five", "One"], a: 0 },
          { q: "What did Tom realise?", o: ["Changes can be wonderful", "School is boring", "He wanted to go home", "He missed his old friends"], a: 0 },
        ]
      },
      {
        title: "The Lost Cat",
        text: "On Tuesday evening, Mrs Johnson noticed that her cat, Whiskers, was missing. She searched the whole house — under the beds, behind the curtains, in the wardrobes — but Whiskers was nowhere to be found. She put up posters around the neighbourhood with a photo of Whiskers and her phone number. Three days later, a little girl named Emma called. She had found Whiskers hiding in her garden shed. Mrs Johnson was overjoyed. She thanked Emma by giving her a large box of chocolates. Whiskers seemed happy to be home and immediately curled up on his favourite spot on the sofa.",
        qs: [
          { q: "When did Mrs Johnson notice Whiskers was missing?", o: ["Tuesday evening", "Monday morning", "Wednesday afternoon", "Friday night"], a: 0 },
          { q: "What did she put up?", o: ["Posters", "Reward signs", "Nothing", "Flyers only"], a: 0 },
          { q: "Who found Whiskers?", o: ["Emma", "Tom", "Alex", "Sara"], a: 0 },
          { q: "Where was Whiskers found?", o: ["In a garden shed", "In the park", "At school", "Under a car"], a: 0 },
          { q: "What did Mrs Johnson give Emma?", o: ["Chocolates", "Money", "Flowers", "A book"], a: 0 },
        ]
      },
      {
        title: "A Letter to a Friend",
        text: "Dear Maria, I am writing to tell you about my new life in Edinburgh. The city is absolutely stunning — full of old castles, cobbled streets, and friendly people. I have started studying at the university here and I am enjoying my course very much. The weather is quite different from home: it rains almost every day and it gets dark early in winter! However, I have bought a warm coat and a good umbrella, so I manage fine. I have made some wonderful friends from different countries. We often explore the city together at weekends. I hope you can visit me soon! Best wishes, Sophie.",
        qs: [
          { q: "Where does Sophie live now?", o: ["Edinburgh", "London", "Paris", "Glasgow"], a: 0 },
          { q: "What is the weather like?", o: ["Rainy and dark in winter", "Hot and sunny", "Dry and cold", "Warm and mild"], a: 0 },
          { q: "What has Sophie started?", o: ["University studies", "A new job", "A business", "Learning to drive"], a: 0 },
          { q: "How does Sophie spend her weekends?", o: ["Exploring the city with friends", "Studying alone", "Visiting family", "Working part-time"], a: 0 },
          { q: "What did Sophie buy because of the weather?", o: ["A coat and umbrella", "A scarf and gloves", "A raincoat only", "Boots and a hat"], a: 0 },
        ]
      },
      {
        title: "The History of Coffee",
        text: "Coffee is one of the most popular drinks in the world, but its origins are quite fascinating. According to legend, coffee was discovered in Ethiopia around 850 AD when a goat herder named Kaldi noticed his goats were very energetic after eating berries from a certain tree. He tried the berries himself and felt the same effect. Word spread, and monks in nearby monasteries began making a drink from the berries to help them stay awake during long prayers. By the 15th century, coffee had reached the Arabian Peninsula and was being traded widely. Coffeehouses, known as 'qahveh khaneh', became popular social places. Coffee then spread to Europe in the 17th century, where it replaced beer and wine as a breakfast drink, making workers much more alert and productive.",
        qs: [
          { q: "Where did coffee originate?", o: ["Ethiopia", "Arabia", "Europe", "Brazil"], a: 0 },
          { q: "Who is said to have discovered coffee?", o: ["Kaldi", "Mohammed", "Marco", "Hassan"], a: 0 },
          { q: "What did monks use coffee for?", o: ["Staying awake during prayers", "Cooking food", "Trading with merchants", "Healing the sick"], a: 0 },
          { q: "What were coffeehouses in Arabia called?", o: ["Qahveh khaneh", "Café noir", "Koffie huis", "Tea rooms"], a: 0 },
          { q: "What did coffee replace in Europe?", o: ["Beer and wine", "Water and juice", "Tea and herbs", "Soup and broth"], a: 0 },
        ]
      },
    ];

    // ============================================================
    // LISTENING
    // ============================================================
    const LISTENING = [
      {
        title: "Self Introduction",
        text: "Hello! My name is John. I am twenty-five years old. I am from London, England. I work as a software engineer at a technology company. In my free time, I enjoy reading books, playing football, and cooking. I have one brother and one sister. My favourite food is pasta, and I love travelling to new countries. Nice to meet you!",
        qs: [
          { q: "What is the speaker's name?", o: ["John", "James", "Jack", "Jake"], a: 0 },
          { q: "How old is the speaker?", o: ["25", "30", "20", "35"], a: 0 },
          { q: "Where is the speaker from?", o: ["London", "Paris", "New York", "Tokyo"], a: 0 },
          { q: "What is the speaker's job?", o: ["Software engineer", "Teacher", "Doctor", "Chef"], a: 0 },
          { q: "What is the speaker's favourite food?", o: ["Pasta", "Pizza", "Sushi", "Burger"], a: 0 },
        ]
      },
      {
        title: "At the Restaurant",
        text: "Good evening! Welcome to The Golden Spoon restaurant. My name is Maria and I will be your server tonight. Today's specials are grilled salmon with vegetables for fifteen dollars, and chicken pasta for twelve dollars. We also have a wonderful chocolate cake for dessert. Would you like to start with something to drink? We have fresh orange juice, lemonade, and various teas. Please take your time with the menu and I will be back shortly to take your order.",
        qs: [
          { q: "What is the restaurant called?", o: ["The Golden Spoon", "The Silver Fork", "The Red Plate", "The Blue Cup"], a: 0 },
          { q: "What is the server's name?", o: ["Maria", "Anna", "Lisa", "Emma"], a: 0 },
          { q: "How much is the grilled salmon?", o: ["$15", "$12", "$20", "$10"], a: 0 },
          { q: "What is the dessert?", o: ["Chocolate cake", "Ice cream", "Fruit salad", "Cheesecake"], a: 0 },
          { q: "How much is the chicken pasta?", o: ["$12", "$15", "$10", "$20"], a: 0 },
        ]
      },
      {
        title: "Weather Forecast",
        text: "Good morning everyone! Here is your weather forecast for today. It will be sunny in the morning, with temperatures reaching twenty-three degrees Celsius. However, clouds will move in during the afternoon, and there is a sixty percent chance of rain by the evening. Temperatures will drop to about fifteen degrees at night. We recommend taking an umbrella if you are going out this afternoon. Tomorrow will be mostly cloudy with occasional showers. Have a great day!",
        qs: [
          { q: "What will the morning be like?", o: ["Sunny", "Rainy", "Cloudy", "Snowy"], a: 0 },
          { q: "What is the morning temperature?", o: ["23°C", "25°C", "20°C", "30°C"], a: 0 },
          { q: "What is the chance of rain?", o: ["60%", "40%", "80%", "50%"], a: 0 },
          { q: "What should people take?", o: ["An umbrella", "A jacket", "Sunglasses", "A hat"], a: 0 },
          { q: "What will tomorrow be like?", o: ["Mostly cloudy with showers", "Sunny", "Very hot", "Snowy"], a: 0 },
        ]
      },
      {
        title: "Doctor's Appointment",
        text: "Good morning! I have an appointment with Doctor Henderson at ten thirty. My name is Sarah Williams. Oh, I see — the doctor is running about fifteen minutes late today. Would you like to take a seat in the waiting area? There are some magazines and a water dispenser. Also, could you fill in this form with your symptoms? We need to know when they started and how severe they are. The doctor will see you as soon as possible. If you feel unwell while waiting, please tell one of the nurses immediately.",
        qs: [
          { q: "Who is the appointment with?", o: ["Doctor Henderson", "Doctor Williams", "Doctor Smith", "Doctor Brown"], a: 0 },
          { q: "What time is the appointment?", o: ["10:30", "9:30", "11:00", "10:00"], a: 0 },
          { q: "How late is the doctor?", o: ["15 minutes", "30 minutes", "10 minutes", "5 minutes"], a: 0 },
          { q: "What does the patient need to fill in?", o: ["A form about symptoms", "A personal information form", "A prescription", "An insurance form"], a: 0 },
          { q: "Who should patients tell if they feel unwell?", o: ["A nurse", "The receptionist", "The doctor", "Another patient"], a: 0 },
        ]
      },
    ];

    // ============================================================
    // SPEAKING PROMPTS
    // ============================================================
    const SPEAKING = [
      { prompt: "What is your name?", hint: "My name is...", example: "My name is Alex. Nice to meet you!" },
      { prompt: "How old are you?", hint: "I am ... years old.", example: "I am twenty years old." },
      { prompt: "Where are you from?", hint: "I am from...", example: "I am from Uzbekistan, a beautiful country in Central Asia." },
      { prompt: "What do you do?", hint: "I am a... / I work as...", example: "I am a student. I study English at university." },
      { prompt: "What is your favourite food?", hint: "My favourite food is...", example: "My favourite food is pizza. I love it with extra cheese!" },
      { prompt: "Do you have any hobbies?", hint: "Yes, I enjoy...", example: "Yes, I enjoy reading and playing football. I also like cooking." },
      { prompt: "What time do you wake up?", hint: "I wake up at...", example: "I usually wake up at seven o'clock in the morning." },
      { prompt: "Tell me about your family.", hint: "I have... My mum...", example: "I have a wonderful family. My mother is a teacher and my father works in finance." },
      { prompt: "What did you do yesterday?", hint: "Yesterday I...", example: "Yesterday I went to the park with my friends and we played basketball." },
      { prompt: "What are your plans for tomorrow?", hint: "Tomorrow I will...", example: "Tomorrow I will study English and then visit my grandmother." },
      { prompt: "Describe your best friend.", hint: "My best friend...", example: "My best friend is very kind and funny. We have known each other for ten years." },
      { prompt: "What is the weather like today?", hint: "Today the weather is...", example: "Today it is warm and sunny. It is a perfect day to go outside!" },
      { prompt: "What do you want to be in the future?", hint: "I want to be...", example: "I want to be a doctor so that I can help people in my community." },
      { prompt: "Tell me about your city.", hint: "My city...", example: "My city is Tashkent. It is the capital of Uzbekistan and is a very modern city." },
      { prompt: "What languages do you speak?", hint: "I speak...", example: "I speak Uzbek and Russian fluently, and I am currently learning English." },
      { prompt: "Describe your typical morning routine.", hint: "Every morning I...", example: "Every morning I wake up at 7, have breakfast, and then prepare for school or work." },
      { prompt: "What kind of music do you like?", hint: "I like... music because...", example: "I like pop and classical music. They help me relax and study." },
      { prompt: "Tell me about your school or workplace.", hint: "My school/work...", example: "I study at a university in the city centre. The campus is very large and modern." },
    ];

    // ============================================================
    // GRAMMAR LESSON INFO
    // ============================================================
    const LESSON_INFO = {
      'Present Simple': "Used for habits, routines, general truths and permanent situations.\n\nForm: Subject + base verb (-s/-es for he/she/it)\n\n✓ I work every day.\n✓ She plays tennis.\n✓ Water boils at 100°C.\n✓ The sun rises in the east.\n\nNegative: Subject + do/does + not + verb\nQuestion: Do/Does + subject + verb?\n\nTime expressions: always, usually, often, sometimes, never, every day/week",
      'Past Simple': "Used for completed actions at a specific time in the past.\n\nForm: Subject + past form of verb\nRegular: add -ed (work→worked, play→played)\nIrregular: change form (go→went, eat→ate, see→saw)\n\n✓ I visited Paris last year.\n✓ She wrote a letter yesterday.\n✓ We won the match.\n\nNegative: Subject + did not + base verb\nQuestion: Did + subject + base verb?\n\nTime expressions: yesterday, last week/year, ago, in 2020",
      'Future Simple': "Used for predictions, promises, decisions made at the moment of speaking.\n\nForm: Subject + will + base verb\n\n✓ I will call you tomorrow.\n✓ It will rain tonight.\n✓ She will be a great leader.\n\nNegative: Subject + will not (won't) + verb\nQuestion: Will + subject + verb?\n\nTime expressions: tomorrow, next week/year, soon, in the future",
      'Present Continuous': "Used for actions happening NOW or around the current time, and future arrangements.\n\nForm: Subject + am/is/are + verb-ing\n\n✓ I am reading right now.\n✓ She is cooking dinner.\n✓ We are moving to London next month.\n\nNegative: am/is/are + not + verb-ing\nQuestion: Am/Is/Are + subject + verb-ing?",
      'Past Continuous': "Used for actions in progress at a specific time in the past, often interrupted.\n\nForm: Subject + was/were + verb-ing\n\n✓ I was sleeping when you called.\n✓ They were playing while it rained.\n✓ She was studying at 9 PM.\n\nNegative: was/were + not + verb-ing\nKey pattern: was/were + -ing WHILE/WHEN simple past",
      'Present Perfect': "Used for past actions that are connected to the present. No specific time given.\n\nForm: Subject + have/has + past participle\n\n✓ I have just finished.\n✓ She has visited Paris twice.\n✓ They have never seen snow.\n✓ We have known each other for years.\n\nKey words: just, already, yet, never, ever, for, since, recently",
      'Modal Verbs': "Modals express ability, permission, obligation, advice, or possibility.\n\n• can/could – ability, permission, request\n• must/have to – strong obligation\n• should/ought to – advice\n• might/may – possibility\n• would – conditional, polite requests\n• shall – suggestions (formal)\n\n✓ You must wear a seatbelt.\n✓ She can speak French.\n✓ Could you help me?\n✓ You should see a doctor.\n\nForm: modal + base verb (no 's', no 'to'!)",
      'Conditionals': "Conditional sentences describe situations and their results.\n\n0 – General truth: If water boils, it evaporates.\n1 – Real/Possible: If it rains, I will stay home.\n2 – Unreal present: If I were rich, I would travel.\n3 – Unreal past: If I had studied, I would have passed.\n\nKey structures:\n• If + present → will\n• If + past → would\n• If + past perfect → would have + past participle",
      'Passive Voice': "Used when the action is more important than who does it, or the agent is unknown.\n\nForm: Subject + to be + past participle\n\n✓ The cake was baked by my mother.\n✓ English is spoken worldwide.\n✓ The bridge will be completed next year.\n✓ The car has been repaired.\n\nTenses in passive: is/are + pp, was/were + pp, has been + pp, will be + pp",
      'Articles': "Three articles: a, an, the, and no article (—)\n\na – singular countable, first mention, consonant sound\nan – singular countable, first mention, vowel sound\nthe – specific, known to both parties\n— – plural/uncountable in general\n\n✓ I saw a dog (first mention).\n✓ The dog was barking (known).\n✓ I drink tea every morning (general).\n✓ She plays the piano.\n\nTip: an before vowel SOUNDS: an hour, an umbrella, an honest man",
      'Comparatives': "Comparing 2 things: comparative adjective\nComparing 3+ things: superlative adjective\n\nShort adj (1 syllable):\n• tall → taller → tallest\n• big → bigger → biggest (double consonant)\n\nLong adj (2+ syllables):\n• beautiful → more beautiful → most beautiful\n\nIrregular:\n• good → better → best\n• bad → worse → worst\n• far → farther → farthest\n\nthan after comparatives: She is taller than me.",
      'Prepositions': "Time: on (days/dates), in (months/years/periods), at (clock times/specific places)\n• on Monday, in March, at 3 PM, at Christmas\n\nPlace: on (surface), in (enclosed space), at (point/location)\n• on the table, in the box, at the station\n\nOther useful prepositions:\n• for (duration), since (starting point), by (deadline)\n• with, without, about, of, from, to, through, over, under, between, among",
      'Reported Speech': "Reporting what someone said — tenses shift back.\n\nDirect: She said, 'I am tired.'\nReported: She said that she was tired.\n\nTense shifts:\nam/is → was | are → were | will → would\ncan → could | have/has → had | simple past → past perfect\n\nTime shifts: now → then | today → that day\ntomorrow → the next day | here → there",
      'Relative Clauses': "Relative clauses give additional information about a noun.\n\nwho – for people: The woman who called is my aunt.\nwhich – for things: The car which I bought is fast.\nthat – people or things (defining): The book that I read was great.\nwhose – possession: The boy whose bag is red is Tom.\nwhere – places: The city where I live is beautiful.\nwhen – time: The year when she was born was 1995.",
      'Phrasal Verbs': "Phrasal verbs = verb + particle (preposition/adverb)\nThey often have idiomatic meanings — memorise as chunks!\n\ngive up = stop trying\nlook after = take care of\nput off = postpone\ntake off = remove / (plane) depart\nfigure out = solve / understand\nrun out of = have nothing left\ncame up with = think of (an idea)\nturn down = refuse / lower\nget over = recover from\ngive away = reveal (a secret)",
      'Past Perfect': "Used for an action that happened BEFORE another past action.\n\nForm: had + past participle\n\n✓ By the time I arrived, she had already left.\n✓ He was tired because he had worked all day.\n✓ I couldn't enter — I had forgotten the key.\n\nKey words: by the time, before, after, already, just, never, when (in narrative)\n\nTimeline: Past Perfect → Past Simple → NOW",
      'Future Continuous': "Used for actions IN PROGRESS at a specific time in the future.\n\nForm: will be + verb-ing\n\n✓ At 8 PM tonight, I will be watching the match.\n✓ She will be working all day tomorrow.\n✓ This time next week, we will be travelling.\n\nQuestion: Will + subject + be + verb-ing?\n\nAlso used to ask politely about plans: Will you be using the car?",
      'Gerunds & Infinitives': "Gerund (verb-ing) as noun: subject, after certain verbs\nInfinitive (to + verb): after certain verbs, to show purpose\n\nVerbs + gerund: enjoy, finish, avoid, keep, suggest, admit, deny, consider, practise, can't stand, miss, give up\n\nVerbs + infinitive: want, decide, agree, promise, hope, manage, refuse, plan, learn, afford, expect\n\nVerbs + both (meaning may change):\nstop smoking (quit) vs stop to smoke (pause and smoke)\nremember posting (did it) vs remember to post (must do it)",
      'Question Tags': "Question tags are added to the end of statements to ask for confirmation.\n\nPositive statement → negative tag\nNegative statement → positive tag\n\n✓ It's a nice day, isn't it?\n✓ She can swim, can't she?\n✓ You haven't met him, have you?\n✓ They were late, weren't they?\n✓ Let's go, shall we?\n✓ I'm right, aren't I? (special case)\n\nTip: the verb in the tag matches the auxiliary in the main clause.",
      'Wish & If Only': "Used to express regrets or wishes about present/past situations.\n\nWish/If only + past simple → present unreal\n• I wish I had more money. (I don't have it now)\n• If only I were taller! (I'm not tall)\n\nWish/If only + past perfect → past regret\n• I wish I had studied harder. (I didn't)\n• If only we had left earlier! (we didn't)\n\nWish/If only + would → complaining about behaviour\n• I wish you would stop talking!\n• If only it would stop raining!",
    };

    // DAILY WORDS for Home screen
    const DAILY_WORDS = [
      { en: "Perseverance", ru: "Настойчивость", uz: "Qat'iyat", tj: "Матонат", example: "Perseverance is the key to success." },
      { en: "Eloquent", ru: "Красноречивый", uz: "Notiq", tj: "Забон овар", example: "She gave an eloquent speech." },
      { en: "Meticulous", ru: "Скрупулёзный", uz: "Aniq", tj: "Дақиқ", example: "He is meticulous about his work." },
      { en: "Ambiguous", ru: "Двусмысленный", uz: "Noaniq", tj: "Ду маъно", example: "The instruction was ambiguous." },
      { en: "Resilient", ru: "Жизнестойкий", uz: "Chidamli", tj: "Устувор", example: "Children are very resilient." },
      { en: "Endeavour", ru: "Усилие", uz: "Harakat", tj: "Кӯшиш", example: "She made every endeavour to succeed." },
      { en: "Eloquence", ru: "Красноречие", uz: "Notiqlik", tj: "Зебогӯӣ", example: "His eloquence impressed the audience." },
    ];

    const GRAMMAR_TIPS = [
      "Use 'a' before consonant sounds and 'an' before vowel sounds. Remember: 'an hour' (silent h!) ⏰",
      "Present Perfect uses 'have/has + past participle' for actions connected to now. NOT for specific past times! 📚",
      "'Could' is the past of 'can', but also used for polite requests: 'Could you help me?' 🎩",
      "Comparatives for short adjectives: add '-er'. For long: use 'more'. Irregular: good→better, bad→worse 📊",
      "Passive voice: 'to be + past participle'. Use it when the agent (who did it) is unknown or unimportant! 🔄",
      "In reported speech, present tense shifts to past: 'I am tired' → 'He said he was tired' ✍️",
      "Phrasal verbs are idiomatic! 'Give up' ≠ give + up. Learn them as complete phrases 💪",
      "'Who' is for people, 'which' for things, 'whose' for possession in relative clauses 🔗",
    ];

    // ============================================================
    // STATE
    // ============================================================
    let lang = 'en';
    let tab = 'home';
    let xp = 0;
    let streak = 0;
    let results = [];
    let quizState = null;
    let chatHistory = [];

    const TABS = ['home', 'lessons', 'listening', 'reading', 'speaking', 'vocabulary', 'ai', 'stats'];

    // ============================================================
    // UTILS
    // ============================================================
    function t() { return LANGS[lang]; }
    function shuffle(arr) { const a = [...arr]; for (let i = a.length - 1; i > 0; i--) { const j = Math.floor(Math.random() * (i + 1));[a[i], a[j]] = [a[j], a[i]]; } return a; }
    function speak(text) { if (!window.speechSynthesis) return; speechSynthesis.cancel(); const u = new SpeechSynthesisUtterance(text); u.lang = 'en-US'; u.rate = 0.85; speechSynthesis.speak(u); }
    function addXP(n) { xp += n; document.getElementById('xpCount').textContent = xp; showBadge('+' + n + ' XP'); }
    function el(id) { return document.getElementById(id); }
    function html(id, content) { const e = el(id); if (e) e.innerHTML = content; }
    let badgeTimer = null;
    function showBadge(msg) { if (badgeTimer) clearTimeout(badgeTimer); const old = document.querySelector('.badge-popup'); if (old) old.remove(); const d = document.createElement('div'); d.className = 'badge-popup'; d.textContent = msg; document.body.appendChild(d); badgeTimer = setTimeout(() => d.remove(), 2000); }

    // ============================================================
    // LANGUAGE
    // ============================================================
    function changeLang(l) { lang = l; renderAll(); }

    // ============================================================
    // NAV
    // ============================================================
    function renderNav() {
      const L = t();
      el('navBar').innerHTML = TABS.map((id, i) => `
    <button class="nav-btn ${tab === id ? 'active' : ''}" onclick="setTab('${id}')">
      <span>${L.tabIcons[i]}</span>${L.tabs[i]}
    </button>
  `).join('');
    }
    function setTab(id) { tab = id; quizState = null; renderAll(); }

    // ============================================================
    // RENDER ALL
    // ============================================================
    function renderAll() {
      renderNav();
      const c = el('mainContent');
      c.className = 'flex-1 overflow-y-auto padding-16 fade-in';
      c.style.padding = '16px';
      switch (tab) {
        case 'home': renderHome(); break;
        case 'lessons': renderLessons(); break;
        case 'listening': renderListening(); break;
        case 'reading': renderReading(); break;
        case 'speaking': renderSpeaking(); break;
        case 'vocabulary': renderVocab(); break;
        case 'ai': renderAI(); break;
        case 'stats': renderStats(); break;
      }
    }

    // ============================================================
    // HOME
    // ============================================================
    function renderHome() {
      const L = t();
      const TOPIC_KEYS = Object.keys(QUESTIONS);
      const dayWord = DAILY_WORDS[new Date().getDay() % DAILY_WORDS.length];
      const tip = GRAMMAR_TIPS[Math.floor(Math.random() * GRAMMAR_TIPS.length)];
      const completed = results.length;
      const totalQ = TOPIC_KEYS.reduce((s, k) => s + QUESTIONS[k].length, 0);
      const recentTopic = results.length ? results[results.length - 1].topic : null;
      const recentTopicName = recentTopic ? (L.topics[TOPIC_KEYS.indexOf(recentTopic)] || recentTopic) : null;

      html('mainContent', `
    <div class="fade-in">
      <div style="margin-bottom:18px">
        <div class="section-title">👋 ${L.startJourney}</div>
        <div class="section-sub">${completed} tests completed · ${xp} XP earned</div>
      </div>
      
      <!-- DAILY WORD -->
      <div class="daily-word-card">
        <div style="font-size:11px;color:rgba(255,255,255,0.5);font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:8px">✨ ${L.dailyWord}</div>
        <div style="font-size:22px;font-weight:800;margin-bottom:4px">${dayWord.en}</div>
        <div style="font-size:13px;color:rgba(255,255,255,0.7);margin-bottom:10px">
          🇷🇺 ${dayWord.ru} · 🇺🇿 ${dayWord.uz} · 🇹🇯 ${dayWord.tj}
        </div>
        <div style="font-size:12px;color:rgba(255,255,255,0.55);font-style:italic">"${dayWord.example}"</div>
        <button class="btn btn-outline" style="margin-top:10px;font-size:11px;padding:5px 12px;border-color:rgba(255,255,255,0.2);color:rgba(255,255,255,0.7)" onclick="speak('${dayWord.en}. ${dayWord.example}')">🔊 Listen</button>
      </div>

      <!-- GRAMMAR TIP -->
      <div style="background:rgba(16,185,129,0.08);border:1px solid rgba(16,185,129,0.2);border-radius:12px;padding:14px 16px;margin-bottom:16px">
        <div style="font-size:11px;color:#34d399;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:6px">💡 ${L.tipTitle}</div>
        <div style="font-size:13px;color:var(--text2);line-height:1.6">${tip}</div>
      </div>

      <!-- STATS ROW -->
      <div class="grid-3" style="margin-bottom:18px">
        <div class="stat-card">
          <div class="stat-num">${completed}</div>
          <div class="stat-label">${L.totalTests}</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">${streak}🔥</div>
          <div class="stat-label">Streak</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">${VOCAB.length}</div>
          <div class="stat-label">${L.totalWords}</div>
        </div>
      </div>

      ${recentTopicName ? `
      <div style="margin-bottom:16px">
        <button class="btn btn-primary" style="width:100%;padding:13px;font-size:14px" onclick="setTab('lessons')">
          ▶ ${L.continueLesson}: ${recentTopicName}
        </button>
      </div>`: ''}

      <!-- QUICK PRACTICE -->
      <div style="font-weight:700;font-size:14px;margin-bottom:10px">⚡ ${L.quickPractice}</div>
      <div style="display:flex;flex-wrap:wrap;gap:0;margin-bottom:18px">
        ${TOPIC_KEYS.slice(0, 8).map((k, i) => `
          <button class="tip-chip" onclick="beginQuiz('${k}');setTab('lessons')">
            ${L.topics[i] || k}
          </button>
        `).join('')}
      </div>

      <!-- RECENT RESULTS -->
      ${results.length ? `
      <div style="font-weight:700;font-size:14px;margin-bottom:10px">📋 Recent Results</div>
      ${results.slice().reverse().slice(0, 3).map(r => `
        <div class="result-item">
          <div>
            <div style="font-weight:600;font-size:12px">${r.topic}</div>
            <div style="font-size:10px;color:var(--text3)">${r.date}</div>
          </div>
          <div class="pill ${r.pct >= 70 ? 'pill-green' : 'pill-red'}">${r.pct}%</div>
        </div>
      `).join('')}` : ''}
    </div>
  `);
    }

    // ============================================================
    // LESSONS
    // ============================================================
    const TOPIC_KEYS = Object.keys(QUESTIONS);
    const LEVEL_MAP = [0, 0, 0, 1, 1, 2, 2, 3, 3, 3, 4, 4, 3, 4, 4, 2, 2, 3, 3, 4];

    function renderLessons() {
      if (quizState) { renderQuiz(); return; }
      const L = t();
      const topicNames = L.topics;
      let h = `<div class="section-title">📖 ${L.tabs[1]}</div>
    <div class="section-sub">${L.lessonSelect}</div>
    <div class="grid-2">`;
      TOPIC_KEYS.forEach((key, i) => {
        const lvl = LEVEL_MAP[i] || 0;
        const done = results.filter(r => r.topic === key);
        const best = done.length ? Math.max(...done.map(r => r.pct)) : null;
        const progress = best !== null ? best : 0;
        h += `<div class="topic-card" onclick="startLesson('${key}')">
      <div class="topic-num">${String(i + 1).padStart(2, '0')} / ${TOPIC_KEYS.length}</div>
      <div class="topic-name">${topicNames[i] || key}</div>
      <div class="level-chip level-${lvl}">${L.levels[lvl]}</div>
      <div class="topic-bar">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:3px">
          <span style="font-size:10px;color:var(--text3)">${best !== null ? best + '%' : '—'}</span>
          <span style="font-size:10px;color:var(--text3)">${done.length} tests</span>
        </div>
        <div class="progress-track">
          <div class="progress-fill" style="width:${progress}%"></div>
        </div>
      </div>
    </div>`;
      });
      h += '</div>';
      html('mainContent', h);
    }

    function startLesson(key) {
      const info = LESSON_INFO[key] || '';
      const L = t();
      const topicIdx = TOPIC_KEYS.indexOf(key);
      const topicName = L.topics[topicIdx] || key;
      const qCount = QUESTIONS[key]?.length || 0;
      html('mainContent', `
    <div class="fade-in">
      <button class="btn btn-outline" style="margin-bottom:14px" onclick="renderLessons()">← ${L.back}</button>
      <div class="section-title">${topicName}</div>
      <div style="font-size:12px;color:var(--text3);margin-bottom:14px">${qCount} questions available · 50 per quiz</div>
      <div class="grammar-info">
        <pre>${info}</pre>
      </div>
      <button class="btn btn-primary" style="width:100%;padding:13px" onclick="beginQuiz('${key}')">
        🚀 ${L.start}
      </button>
    </div>
  `);
    }

    function beginQuiz(key) {
      const pool = QUESTIONS[key] || [];
      const selected = shuffle(pool).slice(0, 50);
      quizState = { topic: key, questions: selected, idx: 0, score: 0, answered: false, done: false };
      tab = 'lessons';
      renderQuiz();
    }

    function renderQuiz() {
      const Q = quizState;
      const L = t();
      if (Q.done) { renderQuizResult(); return; }
      const q = Q.questions[Q.idx];
      const topicIdx = TOPIC_KEYS.indexOf(Q.topic);
      const topicName = L.topics[topicIdx] || Q.topic;
      const pct = Math.round((Q.idx / Q.questions.length) * 100);
      html('mainContent', `
    <div class="fade-in">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
        <button class="btn btn-outline" onclick="quizState=null;renderLessons()">← ${L.back}</button>
        <span style="font-size:11px;color:var(--text2)">${topicName}</span>
        <span class="pill pill-purple">${L.question} ${Q.idx + 1}/${Q.questions.length}</span>
      </div>
      <div class="progress-track" style="margin-bottom:16px">
        <div class="progress-fill" style="width:${pct}%"></div>
      </div>
      <div class="card" style="margin-bottom:16px">
        <div style="font-size:16px;font-weight:700;line-height:1.5">${q.q}</div>
      </div>
      <div id="optionsArea">
        ${q.o.map((opt, i) => `
          <button class="quiz-opt" id="opt${i}" onclick="selectOpt(${i})">
            <span class="opt-letter">${String.fromCharCode(65 + i)}</span>
            ${opt}
          </button>
        `).join('')}
      </div>
      <div id="feedbackArea"></div>
    </div>
  `);
    }

    function selectOpt(chosen) {
      if (quizState.answered) return;
      quizState.answered = true;
      const q = quizState.questions[quizState.idx];
      const correct = q.a;
      const L = t();
      const isCorrect = chosen === correct;
      if (isCorrect) { quizState.score++; addXP(10); }
      for (let i = 0; i < q.o.length; i++) {
        const btn = el('opt' + i);
        if (!btn) continue;
        btn.classList.add('disabled');
        if (i === correct) btn.classList.add('correct');
        else if (i === chosen && !isCorrect) btn.classList.add('wrong');
      }
      const fb = el('feedbackArea');
      if (fb) {
        fb.innerHTML = `
      <div style="text-align:center;padding:14px 0">
        <div style="font-size:22px;margin-bottom:4px">${isCorrect ? '✅' : '❌'}</div>
        <div style="font-weight:700;color:${isCorrect ? 'var(--accent2)' : 'var(--danger)'}">${isCorrect ? L.correct : L.wrong}</div>
        ${!isCorrect ? `<div style="font-size:12px;color:var(--text2);margin-top:3px">✓ ${q.o[correct]}</div>` : ''}
        <button class="btn btn-primary" style="margin-top:10px" onclick="nextQuestion()">${L.next} →</button>
      </div>
    `;
      }
    }

    function nextQuestion() {
      quizState.idx++;
      quizState.answered = false;
      if (quizState.idx >= quizState.questions.length) {
        quizState.done = true;
        const pct = Math.round((quizState.score / quizState.questions.length) * 100);
        results.push({ topic: quizState.topic, score: quizState.score, total: quizState.questions.length, pct, date: new Date().toLocaleDateString() });
        if (pct >= 70) { streak++; el('streakCount').textContent = streak; addXP(50); showBadge('🔥 Streak +1!'); }
      }
      renderAll();
    }

    function renderQuizResult() {
      const Q = quizState;
      const L = t();
      const pct = Math.round((Q.score / Q.questions.length) * 100);
      const emoji = pct >= 90 ? '🏆' : pct >= 70 ? '🎉' : pct >= 50 ? '👍' : '💪';
      const topicIdx = TOPIC_KEYS.indexOf(Q.topic);
      const topicName = L.topics[topicIdx] || Q.topic;
      html('mainContent', `
    <div class="fade-in" style="text-align:center;padding:20px 0">
      <div style="font-size:46px;margin-bottom:10px">${emoji}</div>
      <div class="section-title">${L.yourScore}</div>
      <div class="score-big" style="margin:10px 0">${pct}%</div>
      <div style="color:var(--text2);margin-bottom:4px">${Q.score} / ${Q.questions.length}</div>
      <div class="pill pill-purple" style="margin-bottom:20px">${topicName}</div>
      <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap">
        <button class="btn btn-primary" onclick="beginQuiz('${Q.topic}')">🔄 ${L.tryAgain}</button>
        <button class="btn btn-outline" onclick="quizState=null;renderLessons()">← ${L.back}</button>
      </div>
    </div>
  `);
    }

    // ============================================================
    // LISTENING
    // ============================================================
    let listenState = null;
    function renderListening() {
      if (listenState && listenState.quiz) { renderListenQuiz(); return; }
      const L = t();
      let h = `<div class="section-title">🎧 ${L.tabs[2]}</div>
    <div class="section-sub">${L.listenSelect}</div>`;
      LISTENING.forEach((item, i) => {
        h += `<div class="card-sm" style="margin-bottom:10px" onclick="startListening(${i})">
      <div style="font-weight:700;font-size:14px;margin-bottom:3px">${item.title}</div>
      <div style="font-size:11px;color:var(--text3)">${item.qs.length} questions · 🔊 Text-to-Speech</div>
    </div>`;
      });
      html('mainContent', h);
    }

    function startListening(i) {
      listenState = { idx: i, item: LISTENING[i], qidx: 0, score: 0, quiz: false, answered: false };
      const L = t();
      html('mainContent', `
    <div class="fade-in">
      <button class="btn btn-outline" style="margin-bottom:14px" onclick="listenState=null;renderListening()">← ${L.back}</button>
      <div class="section-title">${listenState.item.title}</div>
      <div class="reading-text">${listenState.item.text}</div>
      <div style="display:flex;gap:8px;margin-bottom:18px;flex-wrap:wrap">
        <button class="btn btn-primary" onclick="speak(LISTENING[${i}].text)">🔊 ${L.play}</button>
        <button class="btn btn-outline" onclick="speechSynthesis.cancel()">⏹ Stop</button>
      </div>
      <button class="btn btn-accent" style="width:100%;padding:13px" onclick="startListenQuiz()">📝 ${L.start}</button>
    </div>
  `);
    }

    function startListenQuiz() { listenState.quiz = true; listenState.qidx = 0; listenState.score = 0; listenState.answered = false; renderListenQuiz(); }

    function renderListenQuiz() {
      const s = listenState; const L = t();
      if (s.qidx >= s.item.qs.length) {
        const pct = Math.round((s.score / s.item.qs.length) * 100);
        results.push({ topic: s.item.title, score: s.score, total: s.item.qs.length, pct, date: new Date().toLocaleDateString() });
        addXP(40);
        html('mainContent', `<div class="fade-in" style="text-align:center;padding:20px 0">
      <div style="font-size:46px;margin-bottom:10px">${pct >= 70 ? '🎉' : '💪'}</div>
      <div class="section-title">${L.yourScore}</div>
      <div class="score-big" style="margin:10px 0">${pct}%</div>
      <div style="color:var(--text2);margin-bottom:20px">${s.score} / ${s.item.qs.length}</div>
      <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap">
        <button class="btn btn-primary" onclick="startListenQuiz()">🔄 ${L.tryAgain}</button>
        <button class="btn btn-outline" onclick="listenState=null;renderListening()">← ${L.back}</button>
      </div></div>`);
        return;
      }
      const q = s.item.qs[s.qidx];
      const pct = Math.round((s.qidx / s.item.qs.length) * 100);
      html('mainContent', `
    <div class="fade-in">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
        <button class="btn btn-outline" onclick="speechSynthesis.cancel();listenState=null;renderListening()">← ${L.back}</button>
        <span class="pill pill-purple">${L.question} ${s.qidx + 1}/${s.item.qs.length}</span>
      </div>
      <div class="progress-track" style="margin-bottom:14px"><div class="progress-fill" style="width:${pct}%"></div></div>
      <div style="text-align:center;margin-bottom:12px">
        <button class="btn btn-outline" onclick="speak(LISTENING[${s.idx}].text)">🔊 ${L.listenAgain}</button>
      </div>
      <div class="card" style="margin-bottom:14px"><div style="font-size:15px;font-weight:700">${q.q}</div></div>
      ${q.o.map((opt, i) => `<button class="quiz-opt" id="lopt${i}" onclick="selectListenOpt(${i})"><span class="opt-letter">${String.fromCharCode(65 + i)}</span>${opt}</button>`).join('')}
      <div id="listenFeedback"></div>
    </div>
  `);
    }

    function selectListenOpt(chosen) {
      if (listenState.answered) return;
      listenState.answered = true;
      const q = listenState.item.qs[listenState.qidx];
      const correct = q.a; const L = t();
      const isCorrect = chosen === correct;
      if (isCorrect) { listenState.score++; addXP(10); }
      for (let i = 0; i < q.o.length; i++) { const btn = el('lopt' + i); if (!btn) continue; btn.classList.add('disabled'); if (i === correct) btn.classList.add('correct'); else if (i === chosen && !isCorrect) btn.classList.add('wrong'); }
      el('listenFeedback').innerHTML = `<div style="text-align:center;padding:10px 0">
    <div style="font-size:20px">${isCorrect ? '✅' : '❌'}</div>
    <div style="font-weight:700;color:${isCorrect ? 'var(--accent2)' : 'var(--danger)'}">${isCorrect ? L.correct : L.wrong}</div>
    ${!isCorrect ? `<div style="font-size:12px;color:var(--text2)">✓ ${q.o[correct]}</div>` : ''}
    <button class="btn btn-primary" style="margin-top:8px" onclick="nextListenQ()">${L.next} →</button>
  </div>`;
    }
    function nextListenQ() { listenState.qidx++; listenState.answered = false; renderListenQuiz(); }

    // ============================================================
    // READING
    // ============================================================
    let readState = null;
    function renderReading() {
      if (readState && readState.quiz) { renderReadQuiz(); return; }
      const L = t();
      let h = `<div class="section-title">📰 ${L.tabs[3]}</div>
    <div class="section-sub">${L.readingSelect}</div>`;
      READING.forEach((item, i) => {
        h += `<div class="card-sm" style="margin-bottom:10px" onclick="startReading(${i})">
      <div style="font-weight:700;font-size:14px;margin-bottom:3px">${item.title}</div>
      <div style="font-size:11px;color:var(--text3)">${item.qs.length} questions · 📖 Comprehension</div>
    </div>`;
      });
      html('mainContent', h);
    }

    function startReading(i) {
      readState = { idx: i, item: READING[i], qidx: 0, score: 0, quiz: false, answered: false };
      const L = t();
      html('mainContent', `
    <div class="fade-in">
      <button class="btn btn-outline" style="margin-bottom:14px" onclick="readState=null;renderReading()">← ${L.back}</button>
      <div class="section-title">${readState.item.title}</div>
      <div class="reading-text">${readState.item.text}</div>
      <button class="btn btn-accent" style="width:100%;padding:13px" onclick="startReadQuiz()">📝 ${L.start}</button>
    </div>
  `);
    }

    function startReadQuiz() { readState.quiz = true; readState.qidx = 0; readState.score = 0; readState.answered = false; renderReadQuiz(); }

    function renderReadQuiz() {
      const s = readState; const L = t();
      if (s.qidx >= s.item.qs.length) {
        const pct = Math.round((s.score / s.item.qs.length) * 100);
        results.push({ topic: s.item.title, score: s.score, total: s.item.qs.length, pct, date: new Date().toLocaleDateString() });
        addXP(40);
        html('mainContent', `<div class="fade-in" style="text-align:center;padding:20px 0">
      <div style="font-size:46px;margin-bottom:10px">${pct >= 70 ? '🎉' : '💪'}</div>
      <div class="section-title">${L.yourScore}</div>
      <div class="score-big" style="margin:10px 0">${pct}%</div>
      <div style="color:var(--text2);margin-bottom:20px">${s.score} / ${s.item.qs.length}</div>
      <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap">
        <button class="btn btn-primary" onclick="startReadQuiz()">🔄 ${L.tryAgain}</button>
        <button class="btn btn-outline" onclick="readState=null;renderReading()">← ${L.back}</button>
      </div></div>`);
        return;
      }
      const q = s.item.qs[s.qidx];
      const pct = Math.round((s.qidx / s.item.qs.length) * 100);
      html('mainContent', `
    <div class="fade-in">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
        <button class="btn btn-outline" onclick="readState=null;renderReading()">← ${L.back}</button>
        <span class="pill pill-purple">${L.question} ${s.qidx + 1}/${s.item.qs.length}</span>
      </div>
      <div class="progress-track" style="margin-bottom:14px"><div class="progress-fill" style="width:${pct}%"></div></div>
      <div class="card" style="margin-bottom:14px"><div style="font-size:15px;font-weight:700">${q.q}</div></div>
      ${q.o.map((opt, i) => `<button class="quiz-opt" id="ropt${i}" onclick="selectReadOpt(${i})"><span class="opt-letter">${String.fromCharCode(65 + i)}</span>${opt}</button>`).join('')}
      <div id="readFeedback"></div>
    </div>
  `);
    }

    function selectReadOpt(chosen) {
      if (readState.answered) return;
      readState.answered = true;
      const q = readState.item.qs[readState.qidx];
      const correct = q.a; const L = t();
      const isCorrect = chosen === correct;
      if (isCorrect) { readState.score++; addXP(10); }
      for (let i = 0; i < q.o.length; i++) { const btn = el('ropt' + i); if (!btn) continue; btn.classList.add('disabled'); if (i === correct) btn.classList.add('correct'); else if (i === chosen && !isCorrect) btn.classList.add('wrong'); }
      el('readFeedback').innerHTML = `<div style="text-align:center;padding:10px 0">
    <div style="font-size:20px">${isCorrect ? '✅' : '❌'}</div>
    <div style="font-weight:700;color:${isCorrect ? 'var(--accent2)' : 'var(--danger)'}">${isCorrect ? L.correct : L.wrong}</div>
    ${!isCorrect ? `<div style="font-size:12px;color:var(--text2)">✓ ${q.o[correct]}</div>` : ''}
    <button class="btn btn-primary" style="margin-top:8px" onclick="nextReadQ()">${L.next} →</button>
  </div>`;
    }
    function nextReadQ() { readState.qidx++; readState.answered = false; renderReadQuiz(); }

    // ============================================================
    // SPEAKING
    // ============================================================
    let speakIdx = 0;
    function renderSpeaking() {
      const L = t();
      const prompt = SPEAKING[speakIdx];
      html('mainContent', `
    <div class="fade-in">
      <div class="section-title">🎤 ${L.speakTitle}</div>
      <div class="section-sub">${L.speakInstr}</div>
      <div class="speak-prompt-box">
        <div style="font-size:34px;margin-bottom:8px">❓</div>
        <div class="speak-prompt-text">"${prompt.prompt}"</div>
        <div class="speak-hint" style="margin-top:6px">💡 ${prompt.hint}</div>
        <button class="btn btn-primary" style="margin-top:12px" onclick="speak('${prompt.prompt.replace(/'/g, "\\'")}')">
          🔊 ${L.play}
        </button>
      </div>
      <div style="margin-bottom:12px">
        <div style="font-size:12px;color:var(--text2);margin-bottom:7px">✍️ Write your answer:</div>
        <textarea id="speakAnswer" placeholder="${prompt.hint}" style="width:100%;background:var(--surface);border:1.5px solid var(--border);border-radius:var(--radius-sm);padding:11px 13px;color:var(--text);font-family:'Sora',sans-serif;font-size:13px;min-height:80px;outline:none;resize:vertical;transition:border-color 0.2s" onfocus="this.style.borderColor='var(--primary)'" onblur="this.style.borderColor='var(--border)'"></textarea>
      </div>
      <div style="display:flex;gap:8px;flex-wrap:wrap">
        <button class="btn btn-primary" onclick="checkSpeakAnswer()">🤖 Get AI Feedback</button>
        <button class="btn btn-outline" onclick="showSpeakExample()">💡 Example</button>
        <button class="btn btn-outline" onclick="nextSpeakPrompt()">→ Next</button>
      </div>
      <div id="speakFeedback" style="margin-top:14px"></div>
      <div style="margin-top:14px;text-align:center;font-size:12px;color:var(--text3)">${speakIdx + 1} / ${SPEAKING.length}</div>
    </div>
  `);
    }

    function checkSpeakAnswer() {
      const ans = el('speakAnswer');
      if (!ans || !ans.value.trim()) return;
      el('speakFeedback').innerHTML = `
    <div class="card" style="border-color:rgba(79,70,229,0.25)">
      <div style="font-size:12px;color:var(--text2);margin-bottom:6px">🤖 Getting AI feedback...</div>
      <div><span class="typing-dot"></span><span class="typing-dot"></span><span class="typing-dot"></span></div>
    </div>`;
      getAIFeedback(ans.value.trim(), SPEAKING[speakIdx].prompt);
    }

    function buildSpeakingFeedback(answer) {
      const words = answer.trim().split(/\s+/).filter(Boolean);
      const lower = answer.toLowerCase();
      let improve = [];

      if (words.length < 6) improve.push("Try writing a longer answer (at least 1-2 full sentences).");
      if (!/[.!?]$/.test(answer.trim())) improve.push("Add punctuation at the end of your sentence.");
      if (/\bi am\b/.test(lower) && !/\bI am\b/.test(answer)) improve.push("Use capital 'I' in English (I, I'm, I am).");
      if (/\bgoed\b/.test(lower)) improve.push("Use irregular past forms: 'went' instead of 'goed'.");
      if (/\bdont\b/.test(lower)) improve.push("Use apostrophes in contractions: don't, can't, isn't.");

      if (!improve.length) improve.push("Excellent structure. Try adding one more detail to sound more natural.");
      const better = answer.trim().length
        ? answer.trim().replace(/\s+/g, ' ').replace(/^./, c => c.toUpperCase()) + (/[.!?]$/.test(answer.trim()) ? "" : ".")
        : "I am learning English every day, and I enjoy practicing speaking.";

      return `✅ **What you did well**\nYour answer is clear and understandable. Great effort!\n\n📝 **What to improve**\n- ${improve.join('\n- ')}\n\n💡 **Better version**\n${better}`;
    }

    async function getAIFeedback(answer, prompt) {
      try {
        const text = buildSpeakingFeedback(answer, prompt);
        el('speakFeedback').innerHTML = `
      <div class="card" style="border-color:rgba(16,185,129,0.25)">
        <div style="font-size:12px;color:var(--accent2);font-weight:700;margin-bottom:6px">🤖 AI Feedback</div>
        <div style="font-size:13px;line-height:1.65;color:var(--text);white-space:pre-line">${text}</div>
      </div>`;
        addXP(15);
      } catch (e) {
        el('speakFeedback').innerHTML = `<div class="card"><div style="color:var(--text2);font-size:13px">Good effort! Keep practising every day. Consistency is the key to fluency! 🌟</div></div>`;
      }
    }

    function showSpeakExample() {
      const p = SPEAKING[speakIdx];
      el('speakFeedback').innerHTML = `
    <div class="card" style="border-color:rgba(245,158,11,0.25)">
      <div style="font-size:12px;color:var(--accent);font-weight:700;margin-bottom:6px">💡 Example Answer</div>
      <div style="font-size:13px;color:var(--text)">"${p.example}"</div>
      <button class="btn btn-outline" style="margin-top:8px;font-size:11px;padding:4px 10px" onclick="speak('${p.example.replace(/'/g, "\\'")}')">🔊 Listen</button>
    </div>`;
    }
    function nextSpeakPrompt() { speakIdx = (speakIdx + 1) % SPEAKING.length; renderSpeaking(); }

    // ============================================================
    // VOCABULARY
    // ============================================================
    function renderVocab() {
      const L = t();
      const cats = [...new Set(VOCAB.map(v => v.cat))];
      html('mainContent', `
    <div class="fade-in">
      <div class="section-title">📚 ${L.tabs[5]}</div>
      <input class="search-input" id="vocabSearch" placeholder="${L.vocabSearch}" oninput="filterVocab(this.value)">
      <div style="display:flex;gap:5px;flex-wrap:wrap;margin-bottom:14px" id="catFilters">
        <button class="btn btn-primary" style="padding:4px 11px;font-size:11px" onclick="setVocabCat(null)">All</button>
        ${cats.map(c => `<button class="btn btn-outline" style="padding:4px 11px;font-size:11px" onclick="setVocabCat('${c}')">${c}</button>`).join('')}
      </div>
      <div id="vocabGrid" class="grid-2"></div>
    </div>
  `);
      renderVocabGrid(VOCAB);
    }

    let vocabCatFilter = null;
    function setVocabCat(cat) { vocabCatFilter = cat; filterVocab(el('vocabSearch')?.value || ''); }
    function filterVocab(search) {
      const q = (search || '').toLowerCase();
      const filtered = VOCAB.filter(v => {
        const matchCat = !vocabCatFilter || v.cat === vocabCatFilter;
        const matchQ = !q || v.en.includes(q) || v.ru.includes(q) || v.uz.includes(q) || v.tj.includes(q);
        return matchCat && matchQ;
      });
      renderVocabGrid(filtered);
    }

    function renderVocabGrid(list) {
      const grid = el('vocabGrid');
      if (!grid) return;
      if (!list.length) { grid.innerHTML = '<div class="empty-state"><div class="icon">🔍</div><div>No words found</div></div>'; return; }
      grid.innerHTML = list.map(v => `
    <div class="vocab-card" onclick="speak('${v.en.replace(/'/g, "\\'")}')">
      <div class="vocab-en">${v.en} <span style="font-size:11px;color:var(--text3)">🔊</span></div>
      <div class="vocab-tr">🇷🇺 ${v.ru}</div>
      <div class="vocab-tr">🇺🇿 ${v.uz}</div>
      <div class="vocab-tr">🇹🇯 ${v.tj}</div>
      <div class="vocab-cat">${v.cat}</div>
    </div>
  `).join('');
    }

    // ============================================================
    // AI CHAT — Improved with suggestions and system prompt
    // ============================================================
    function renderAI() {
      const L = t();
      const suggestions = [
        "Correct my grammar: I goed to store yesterday.",
        "Explain the difference between 'make' and 'do'",
        "Give me 5 sentences using Present Perfect",
        "What is the difference between 'since' and 'for'?",
        "How do I use 'used to'?",
        "Translate and explain: 'It's raining cats and dogs'",
      ];
      html('mainContent', `
    <div class="chat-wrap fade-in">
      <div style="margin-bottom:10px">
        <div class="section-title">🤖 ${L.tabs[6]}</div>
        <div class="section-sub">Powered by Claude AI · Ask anything about English</div>
      </div>
      <div class="chat-msgs" id="chatMsgs">
        <div class="chat-msg-ai">${L.aiWelcome}</div>
      </div>
      <div class="ai-suggest" id="aiSuggest">
        ${suggestions.map(s => `<button class="tip-chip" style="font-size:11px" onclick="quickSend('${s.replace(/'/g, "\\'")}')">💬 ${s.length > 35 ? s.slice(0, 35) + '...' : s}</button>`).join('')}
      </div>
      <div class="chat-input-row">
        <input class="chat-input" id="chatInput" placeholder="${L.aiPlaceholder}" onkeydown="if(event.key==='Enter')sendChat()">
        <button class="btn btn-primary" onclick="sendChat()" style="padding:10px 14px">↑</button>
      </div>
    </div>
  `);
      if (chatHistory.length) {
        const box = el('chatMsgs');
        chatHistory.forEach(m => {
          const div = document.createElement('div');
          div.className = m.role === 'user' ? 'chat-msg-user' : 'chat-msg-ai';
          div.textContent = m.content;
          box.appendChild(div);
        });
        box.scrollTop = box.scrollHeight;
      }
    }

    function quickSend(text) {
      const inp = el('chatInput');
      if (inp) inp.value = text;
      const sugBox = el('aiSuggest');
      if (sugBox) sugBox.style.display = 'none';
      sendChat();
    }

    function buildLocalTutorReply(message) {
      const m = message.toLowerCase();
      if (m.includes("present perfect")) {
        return "Present Perfect = have/has + past participle.\nExamples:\n1) I have finished my homework.\n2) She has visited London.\n3) They have not seen this film yet.";
      }
      if (m.includes("since") && m.includes("for")) {
        return "'Since' = starting point (since 2020, since Monday).\n'For' = duration (for 2 hours, for 3 years).\nExample: I have lived here since 2022 / for 3 years.";
      }
      if (m.includes("make") && m.includes("do")) {
        return "Use 'make' for creating/producing (make a cake, make a decision).\nUse 'do' for actions/tasks (do homework, do the dishes, do exercise).";
      }
      if (m.includes("correct my grammar") || m.includes("correct")) {
        return "Sure! Send your sentence, and I will correct it with explanation.\nExample: ❌ I goed to store yesterday.\n✅ I went to the store yesterday.";
      }
      if (m.includes("used to")) {
        return "'Used to + verb' describes past habits/states that are not true now.\nExample: I used to play football every day (but now I don't).";
      }
      return "Great question! Here is a quick tip: write short, clear sentences, then expand with details. If you send one sentence, I can correct it and explain why. 💡";
    }

    async function sendChat() {
      const inp = el('chatInput');
      if (!inp || !inp.value.trim()) return;
      const msg = inp.value.trim();
      inp.value = '';
      const sugBox = el('aiSuggest');
      if (sugBox) sugBox.style.display = 'none';
      const box = el('chatMsgs');
      const userDiv = document.createElement('div');
      userDiv.className = 'chat-msg-user';
      userDiv.textContent = msg;
      box.appendChild(userDiv);
      const typingDiv = document.createElement('div');
      typingDiv.className = 'chat-msg-ai';
      typingDiv.innerHTML = '<span class="typing-dot"></span><span class="typing-dot"></span><span class="typing-dot"></span>';
      box.appendChild(typingDiv);
      box.scrollTop = box.scrollHeight;
      chatHistory.push({ role: 'user', content: msg });
      try {
        const reply = buildLocalTutorReply(msg);
        chatHistory.push({ role: 'assistant', content: reply });
        typingDiv.textContent = reply;
        typingDiv.className = 'chat-msg-ai';
        addXP(5);
      } catch (e) {
        typingDiv.textContent = "Connection error. Please check your internet and try again!";
        chatHistory.push({ role: 'assistant', content: typingDiv.textContent });
      }
      box.scrollTop = box.scrollHeight;
    }

    // ============================================================
    // STATS
    // ============================================================
    function renderStats() {
      const L = t();
      if (!results.length) {
        html('mainContent', `<div class="fade-in"><div class="section-title">📊 ${L.statsTitle}</div>
      <div class="empty-state"><div class="icon">📭</div><div>${L.noStats}</div></div></div>`);
        return;
      }
      const total = results.length;
      const avg = Math.round(results.reduce((s, r) => s + r.pct, 0) / total);
      const best = Math.max(...results.map(r => r.pct));
      const byTopic = {};
      results.forEach(r => { if (!byTopic[r.topic] || r.pct > byTopic[r.topic]) byTopic[r.topic] = r.pct; });
      const lb = Object.entries(byTopic).sort((a, b) => b[1] - a[1]);
      html('mainContent', `
    <div class="fade-in">
      <div class="section-title">📊 ${L.statsTitle}</div>
      <div class="grid-3" style="margin-bottom:20px">
        <div class="stat-card"><div class="stat-num">${total}</div><div class="stat-label">${L.totalTests}</div></div>
        <div class="stat-card"><div class="stat-num">${avg}%</div><div class="stat-label">${L.avgScore}</div></div>
        <div class="stat-card"><div class="stat-num">${best}%</div><div class="stat-label">${L.bestScore}</div></div>
      </div>
      <div style="font-weight:700;margin-bottom:10px;font-size:14px">🏆 Best Scores by Topic</div>
      ${lb.slice(0, 10).map(([topic, pct], i) => `
        <div class="lb-row">
          <div class="lb-rank" style="color:${i === 0 ? '#fbbf24' : i === 1 ? '#94a3b8' : i === 2 ? '#cd7f32' : 'var(--text3)'}">${i === 0 ? '🥇' : i === 1 ? '🥈' : i === 2 ? '🥉' : i + 1}</div>
          <div class="lb-name">${topic}</div>
          <div class="lb-score">${pct}%</div>
        </div>
      `).join('')}
      <div style="margin-top:20px;font-weight:700;margin-bottom:10px;font-size:14px">📋 Recent Tests</div>
      ${results.slice().reverse().slice(0, 8).map(r => `
        <div class="result-item">
          <div>
            <div style="font-weight:600;font-size:12px">${r.topic}</div>
            <div style="font-size:10px;color:var(--text3)">${r.date}</div>
          </div>
          <div class="pill ${r.pct >= 70 ? 'pill-green' : 'pill-red'}">${r.pct}%</div>
        </div>
      `).join('')}
    </div>
  `);
    }

    // ============================================================
    // INIT
    // ============================================================
    renderAll();
  </script>
</body>

</html>
