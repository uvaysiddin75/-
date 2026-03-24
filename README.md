
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Викторина и Х и О</title>
<h1>Викторина и Х и О</h1>
<style>
body { font-family: Arial; background:#f0f0f0; padding:20px;}
nav { margin-bottom:20px; }
button.tab { padding:10px 20px; margin-right:5px; cursor:pointer; background:#2196f3; color:#fff; border:none; border-radius:5px; }
button.tab:hover { background:#1976d2; }
section { display:none; }
section.active { display:block; }

#question { font-size:1.2em; margin-bottom:15px; }
#answers { display:flex; flex-direction:column; gap:10px; margin-bottom:15px; }
.answer { padding:10px; border-radius:5px; border:1px solid #ccc; background:#fff; cursor:pointer; transition:0.3s;}
.answer.correct { background: #4caf50; color:#fff; }
.answer.wrong { background: #f44336; color:#fff; }
#result { font-weight:bold; min-height:20px; margin-bottom:10px;}
#progress { margin-bottom:10px;}

#tic-tac-toe { display:grid; grid-template-columns:repeat(3,100px); gap:5px; margin-top:20px;}
.ttt-cell { width:100px; height:100px; background:#fff; border:1px solid #000; display:flex; align-items:center; justify-content:center; font-size:2em; cursor:pointer; }
.ttt-cell.win { background: #4caf50; color:#fff; }
#ttt-result { margin-top:10px; font-weight:bold; }
</style>
</head>
<body>

<nav>
  <button class="tab" onclick="showTab('quiz')">Викторина</button>
  <button class="tab" onclick="showTab('xo')">Х и О</button>
</nav>

<section id="quiz" class="active">
  <div id="question"></div>
  <div id="answers"></div>
  <div id="result"></div>
  <div id="progress"></div>
</section>

<section id="xo">
  <button id="start-ttt">Начать Х и О</button>
  <div id="tic-tac-toe"></div>
  <div id="ttt-result"></div>
</section>

<script>
// ===== Навигация по вкладкам =====
function showTab(tabId){
  document.querySelectorAll('section').forEach(sec => sec.classList.remove('active'));
  document.getElementById(tabId).classList.add('active');
}

/* УРОВЕНЬ 1 */
{q:"2+2?", a:["3","4","5"], correct:1, level:1},
{q:"1+1?", a:["1","2","3"], correct:1, level:1},
{q:"5-3?", a:["1","2","3"], correct:1, level:1},
{q:"Сколько дней в неделе?", a:["5","7","10"], correct:1, level:1},
{q:"Цвет неба?", a:["Синий","Красный","Зелёный"], correct:0, level:1},
{q:"Сколько пальцев на руке?", a:["4","5","6"], correct:1, level:1},
{q:"Сколько месяцев?", a:["10","11","12"], correct:2, level:1},
{q:"Сколько часов в сутках?", a:["12","24","48"], correct:1, level:1},
{q:"Сколько глаз у человека?", a:["1","2","3"], correct:1, level:1},
{q:"3+1?", a:["3","4","5"], correct:1, level:1},

/* УРОВЕНЬ 2 */
{q:"5+5?", a:["10","15","20"], correct:0, level:2},
{q:"10-3?", a:["5","7","9"], correct:1, level:2},
{q:"2*3?", a:["5","6","7"], correct:1, level:2},
{q:"Цвет травы?", a:["Красный","Зелёный","Синий"], correct:1, level:2},
{q:"Сколько букв в 'кот'?", a:["2","3","4"], correct:1, level:2},
{q:"Сколько сторон у квадрата?", a:["3","4","5"], correct:1, level:2},
{q:"Сколько ушей у человека?", a:["1","2","3"], correct:1, level:2},
{q:"6+2?", a:["7","8","9"], correct:1, level:2},
{q:"9-4?", a:["4","5","6"], correct:1, level:2},
{q:"4+4?", a:["6","8","10"], correct:1, level:2},

/* УРОВЕНЬ 3 */
{q:"15+5?", a:["20","25","30"], correct:0, level:3},
{q:"20-10?", a:["5","10","15"], correct:1, level:3},
{q:"3*3?", a:["6","9","12"], correct:1, level:3},
{q:"10/2?", a:["4","5","6"], correct:1, level:3},
{q:"Столица Франции?", a:["Париж","Рим","Берлин"], correct:0, level:3},
{q:"Сколько дней в феврале?", a:["28","30","31"], correct:0, level:3},
{q:"Сколько ног у паука?", a:["6","8","10"], correct:1, level:3},
{q:"Самый большой океан?", a:["Тихий","Атлантический","Индийский"], correct:0, level:3},
{q:"8+7?", a:["14","15","16"], correct:1, level:3},
{q:"18-8?", a:["9","10","11"], correct:1, level:3},

/* УРОВЕНЬ 4 */
{q:"25+25?", a:["40","50","60"], correct:1, level:4},
{q:"50-20?", a:["20","30","40"], correct:1, level:4},
{q:"4*4?", a:["12","16","20"], correct:1, level:4},
{q:"12/3?", a:["3","4","5"], correct:1, level:4},
{q:"Столица Германии?", a:["Берлин","Париж","Рим"], correct:0, level:4},
{q:"Сколько планет?", a:["7","8","9"], correct:1, level:4},
{q:"Сколько букв в русском алфавите?", a:["31","33","35"], correct:1, level:4},
{q:"10+10?", a:["15","20","25"], correct:1, level:4},
{q:"30-10?", a:["10","20","30"], correct:1, level:4},
{q:"6*3?", a:["15","18","21"], correct:1, level:4},

/* УРОВЕНЬ 5 */
{q:"100-50?", a:["25","50","75"], correct:1, level:5},
{q:"30+70?", a:["90","100","110"], correct:1, level:5},
{q:"5*5?", a:["20","25","30"], correct:1, level:5},
{q:"20/4?", a:["4","5","6"], correct:1, level:5},
{q:"Столица Италии?", a:["Рим","Милан","Париж"], correct:0, level:5},
{q:"Сколько цветов радуги?", a:["5","7","9"], correct:1, level:5},
{q:"Сколько секунд в минуте?", a:["30","60","90"], correct:1, level:5},
{q:"40+10?", a:["40","50","60"], correct:1, level:5},
{q:"80-30?", a:["40","50","60"], correct:1, level:5},
{q:"7*3?", a:["20","21","24"], correct:1, level:5},

/* УРОВЕНЬ 6 */
{q:"200-100?", a:["50","100","150"], correct:1, level:6},
{q:"150+50?", a:["180","200","220"], correct:1, level:6},
{q:"6*6?", a:["30","36","42"], correct:1, level:6},
{q:"36/6?", a:["5","6","7"], correct:1, level:6},
{q:"Столица Японии?", a:["Токио","Сеул","Пекин"], correct:0, level:6},
{q:"Сколько дней в году?", a:["360","365","370"], correct:1, level:6},
{q:"Сколько минут в часе?", a:["30","60","90"], correct:1, level:6},
{q:"70+30?", a:["90","100","110"], correct:1, level:6},
{q:"90-40?", a:["40","50","60"], correct:1, level:6},
{q:"8*5?", a:["30","40","50"], correct:1, level:6},

/* УРОВЕНЬ 7 */
{q:"300-150?", a:["100","150","200"], correct:1, level:7},
{q:"400+100?", a:["400","500","600"], correct:1, level:7},
{q:"7*7?", a:["42","49","56"], correct:1, level:7},
{q:"49/7?", a:["6","7","8"], correct:1, level:7},
{q:"Столица США?", a:["Вашингтон","Нью-Йорк","Лос-Анджелес"], correct:0, level:7},
{q:"Сколько миллисекунд в секунде?", a:["100","1000","10000"], correct:1, level:7},
{q:"Самая глубокая точка океана?", a:["Марианская впадина","Байкал","Нил"], correct:0, level:7},
{q:"120+30?", a:["140","150","160"], correct:1, level:7},
{q:"200-50?", a:["100","150","200"], correct:1, level:7},
{q:"9*6?", a:["48","54","60"], correct:1, level:7},

/* УРОВЕНЬ 8 */
{q:"500-250?", a:["200","250","300"], correct:1, level:8},
{q:"600+200?", a:["700","800","900"], correct:1, level:8},
{q:"8*8?", a:["60","64","70"], correct:1, level:8},
{q:"64/8?", a:["6","8","10"], correct:1, level:8},
{q:"Столица Китая?", a:["Пекин","Токио","Сеул"], correct:0, level:8},
{q:"Сколько бит в байте?", a:["4","8","16"], correct:1, level:8},
{q:"Самый быстрый зверь?", a:["Гепард","Лев","Тигр"], correct:0, level:8},
{q:"300+200?", a:["400","500","600"], correct:1, level:8},
{q:"700-300?", a:["300","400","500"], correct:1, level:8},
{q:"9*8?", a:["64","72","80"], correct:1, level:8},

/* УРОВЕНЬ 9 */
{q:"700-300?", a:["300","400","500"], correct:1, level:9},
{q:"800+300?", a:["1000","1100","1200"], correct:1, level:9},
{q:"9*9?", a:["72","81","90"], correct:1, level:9},
{q:"81/9?", a:["8","9","10"], correct:1, level:9},
{q:"Столица Индии?", a:["Дели","Пекин","Токио"], correct:0, level:9},
{q:"Что такое переменная?", a:["Данные","Число","Картинка"], correct:0, level:9},
{q:"Что такое функция?", a:["Команда","Фото","Видео"], correct:0, level:9},
{q:"400+400?", a:["700","800","900"], correct:1, level:9},
{q:"900-400?", a:["400","500","600"], correct:1, level:9},
{q:"10*9?", a:["80","90","100"], correct:1, level:9},

/* УРОВЕНЬ 10 */
{q:"1000-500?", a:["400","500","600"], correct:1, level:10},
{q:"900+400?", a:["1200","1300","1400"], correct:1, level:10},
{q:"10*10?", a:["90","100","110"], correct:1, level:10},
{q:"100/10?", a:["5","10","15"], correct:1, level:10},
{q:"Столица Бразилии?", a:["Бразилиа","Рио","Сан-Паулу"], correct:0, level:10},
{q:"Что такое массив?", a:["Список","Число","Фото"], correct:0, level:10},
{q:"Что такое объект?", a:["Структура","Картинка","Видео"], correct:0, level:10},
{q:"Что такое JSON?", a:["Формат данных","Игра","Фото"], correct:0, level:10},
{q:"Что такое DOM?", a:["Структура страницы","Музыка","Видео"], correct:0, level:10},
{q:"Что такое async?", a:["Асинхронность","Синхронность","Ошибка"], correct:0, level:10}

];

// ===== Переменные викторины =====
let current = 0, score = 0, level = 1, questions = [], usedQuestions = [];

// ===== Функции викторины =====
function shuffle(array){for(let i=array.length-1;i>0;i--){let j=Math.floor(Math.random()*(i+1));[array[i],array[j]]=[array[j],array[i]];}return array;}
function getQuestions(level){
  let filtered=allQuestions.filter(q=>q.l===level).filter(q=>!usedQuestions.includes(q.q));
  let selected = shuffle(filtered).slice(0,10);
  selected.forEach(q=>usedQuestions.push(q.q));
  return selected;
}
function startGame(){current=0; score=0; level=1; usedQuestions=[]; questions=getQuestions(level); loadQuestion();}
function loadQuestion(){
  const q=questions[current]; document.getElementById("question").textContent="Уровень "+level+": "+q.q;
  const answers=document.getElementById("answers"); answers.innerHTML="";
  q.a.forEach((ans,i)=>{const btn=document.createElement("button"); btn.textContent=ans; btn.className="answer"; btn.onclick=()=>checkAnswer(i,btn); answers.appendChild(btn);});
  document.getElementById("progress").textContent=`Вопрос ${current+1} из ${questions.length}`; document.getElementById("result").textContent="";
}
function checkAnswer(i,btn){
  const q=questions[current]; Array.from(document.getElementById("answers").children).forEach((b,idx)=>{b.disabled=true; if(idx===q.c)b.classList.add("correct"); else if(idx===i)b.classList.add("wrong");});
  const result=document.getElementById("result"); if(i===q.c){ score++; result.textContent="✅ Правильно"; } else result.textContent="❌ Неправильно";
  current++; setTimeout(()=>{if(current<questions.length) loadQuestion(); else nextLevel();},700);
}
function nextLevel(){
  level++; if(level>10){document.getElementById("question").textContent="🏆 Викторина завершена!"; document.getElementById("answers").innerHTML=""; document.getElementById("result").textContent="Результат: "+score; document.getElementById("progress").textContent=""; return;}
  document.getElementById("question").textContent=`Уровень ${level-1} пройден!`; document.getElementById("answers").innerHTML="";
  const btn=document.createElement("button"); btn.textContent="Следующий уровень"; btn.onclick=()=>{current=0; questions=getQuestions(level); loadQuestion();}; document.getElementById("answers").appendChild(btn);
}

// ===== Игра Х и О =====
const ttt=document.getElementById("tic-tac-toe"); const tttResult=document.getElementById("ttt-result"); let board=["","","","","","","","",""]; let turn="X";
function startTTT(){board=["","","","","","","","",""]; tttResult.textContent=""; ttt.innerHTML=""; ttt.style.display="grid"; for(let i=0;i<9;i++){const cell=document.createElement("div"); cell.className="ttt-cell"; cell.dataset.idx=i; cell.onclick=()=>tttClick(i,cell); ttt.appendChild(cell);}}
function tttClick(i,cell){if(board[i]!=="") return; board[i]=turn; cell.textContent=turn; if(checkWin(turn)){highlightWin(turn); tttResult.textContent=turn+" выиграл!"; disableBoard(); return;} if(board.every(c=>c!=="")){ tttResult.textContent="Ничья!"; return;} turn = turn==="X"?"O":"X";}
function checkWin(p){const wins=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]; return wins.some(line=>line.every(idx=>board[idx]===p));}
function highlightWin(p){const wins=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]; wins.forEach(line=>{if(line.every(idx=>board[idx]===p)){line.forEach(idx=>ttt.children[idx].classList.add("win"));}});}
function disableBoard(){Array.from(ttt.children).forEach(c=>c.onclick=null);}
document.getElementById("start-ttt").onclick=startTTT;

// старт викторины
startGame();
</script>

</body>
</html>
instagram:https://www.instagram.com/uvaysiddin_22/#
telegram:https://t.me/EFOOTBALSTART_10
