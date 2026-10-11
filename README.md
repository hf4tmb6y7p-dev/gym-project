

<!doctype html>

<html lang="ru">

<head>

<meta charset="utf-8">

<meta name="viewport" content="width=device-width,initial-scale=1">

<meta name="theme-color" content="#101510">

<title>GYM PROJECT</title>

<style>

:root{--bg:#101510;--panel:#1a211a;--line:#303b30;--lime:#b8f36b;--text:#f3f5f0;--muted:#a4afa1;--red:#ff8585}

*{box-sizing:border-box}

body{margin:0;background:var(--bg);color:var(--text);font:16px system-ui,sans-serif}

header{padding:24px 18px;background:linear-gradient(135deg,#263526,#101510);border-bottom:1px solid var(--line)}

.wrap{max-width:950px;margin:auto;padding:16px}

.brand{font-size:12px;letter-spacing:3px;color:var(--lime);font-weight:800}

h1{font-size:clamp(32px,8vw,48px);margin:12px 0}

h2{font-size:22px;margin:0 0 14px}

h3{font-size:17px;margin:0 0 8px}

p{color:var(--muted);line-height:1.55}

button{border:1px solid var(--line);background:var(--panel);color:var(--text);padding:11px 14px;border-radius:12px;font:inherit;cursor:pointer}

button:hover{border-color:var(--lime)}

.primary{background:var(--lime);color:#14200e;font-weight:800}

.danger{color:var(--red)}

nav{display:flex;gap:8px;overflow:auto;padding:14px 0}

nav button{white-space:nowrap}

section{scroll-margin-top:12px;margin:22px 0}

.panel{background:var(--panel);border:1px solid var(--line);border-radius:18px;padding:18px;margin-bottom:14px}

.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}

.stats{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:10px}

.stat{background:#111811;border:1px solid var(--line);border-radius:14px;padding:12px}

.stat strong{display:block;font-size:24px;color:var(--lime)}

.stat span,.small{font-size:12px;color:var(--muted)}

label{display:block;color:var(--muted);font-size:13px;margin:12px 0 6px}

input,select,textarea{width:100%;background:#101510;color:var(--text);border:1px solid var(--line);border-radius:10px;padding:12px;font:inherit;min-width:0}

input[type=checkbox]{width:auto}

.row{display:flex;gap:10px;align-items:center;flex-wrap:wrap}

.row>*{flex:1}

.exercise{border:1px solid var(--line);border-radius:14px;padding:14px;margin:10px 0}

.pill{display:inline-block;padding:4px 9px;border-radius:99px;background:#293627;color:var(--lime);font-size:12px}

.result{white-space:pre-wrap;line-height:1.6}

.hidden{display:none!important}

hr{border:0;border-top:1px solid var(--line);margin:16px 0}

canvas{width:100%;height:210px;display:block}

footer{text-align:center;padding:30px;color:var(--muted);font-size:12px}

@media(max-width:580px){.grid{grid-template-columns:1fr}.stat{padding:8px}.stat strong{font-size:19px}.wrap{padding:12px}.panel{padding:14px}}

</style>

</head>

<body>

<header><div class="wrap">

<div class="brand">YOUR TRAINING. YOUR RULES.</div>

<h1>GYM <span style="color:var(--lime)">PROJECT</span></h1>

<p>Тренируйся с умом. Записывай результаты. Расти постепенно.</p>

<div class="stats">

<div class="stat"><strong id="statSessions">0</strong><span>Дней тренировок</span></div>

<div class="stat"><strong id="statRecords">0</strong><span>Записей упражнений</span></div>

<div class="stat"><strong id="statPR">0</strong><span>Личных улучшений*</span></div>

</div>

<p class="small">*Число упражнений, где последний записанный вес выше предыдущего.</p>

</div></header>

<div class="wrap">

<nav>

<button onclick="go('generator')">Программа</button>

<button onclick="go('log')">Записать тренировку</button>

<button onclick="go('progress')">Мой прогресс</button>

<button onclick="go('library')">Упражнения</button>

</nav>

<section id="generator">

<div class="panel">

<h2>Составить программу</h2>

<p>Выбери параметры для примерного тренировочного плана.</p>

<form id="planForm">

<div class="grid">

<div><label for="goal">Цель</label><select id="goal">

<option value="muscle">Рост мышц</option><option value="strength">Сила</option><option value="fitness">Общая форма</option><option value="endurance">Выносливость</option>

</select></div>

<div><label for="level">Опыт</label><select id="level">

<option>Новичок</option><option>Есть опыт</option><option>Продвинутый</option>

</select></div>

<div><label for="days">Тренировок в неделю</label><select id="days">

<option>2</option><option selected>3</option><option>4</option><option>5</option><option>6</option>

</select></div>

<div><label for="equipment">Оборудование</label><select id="equipment">

<option value="gym">Полный зал</option><option value="dumbbells">Гантели</option><option value="bodyweight">Свой вес</option>

</select></div>

<div><label for="duration">Длительность, мин</label><select id="duration">

<option>30</option><option selected>45</option><option>60</option><option>75</option>

</select></div>

<div><label for="focus">Приоритет</label><select id="focus">

<option value="all">Всё тело</option><option value="chest">Грудь</option><option value="back">Спина</option><option value="legs">Ноги</option><option value="arms">Руки и плечи</option><option value="core">Корпус</option>

</select></div>

</div>

<label><input type="checkbox" id="injury"> Есть травма, боль или ограничение движений</label>

<label for="injuryNote">Что учитывать? (необязательно)</label>

<textarea id="injuryNote" rows="2" placeholder="Например, колено или плечо"></textarea>

<p class="small">При травме согласуй упражнения и нагрузку со специалистом. Этот план не заменяет реабилитацию.</p>

<button class="primary" type="submit">Создать программу</button>

</form>

</div>

<div id="planResult" class="panel hidden"></div>

</section>

<section id="log">

<div class="panel">

<h2>Записать результат</h2>

<p>Вводи результат упражнения после тренировки.</p>

<form id="logForm">

<label for="exerciseName">Упражнение</label>

<input id="exerciseName" list="exerciseOptions" placeholder="Например, жим лёжа" required>

<datalist id="exerciseOptions"></datalist>

<div class="grid">

<div><label for="weight">Вес, кг</label><input id="weight" type="number" min="0" max="1000" step=".25" value="0" required></div>

<div><label for="sets">Подходы</label><input id="sets" type="number" min="1" max="30" value="3" required></div>

<div><label for="reps">Повторения в каждом подходе</label><input id="reps" type="number" min="1" max="200" value="10" required></div>

<div><label for="effort">Насколько тяжело?</label><select id="effort">

<option value="easy">Легко, большой запас</option><option value="moderate" selected>Умеренно, техника хорошая</option><option value="hard">Очень тяжело</option>

</select></div>

</div>

<label for="logDate">Дата</label><input id="logDate" type="date" required>

<label for="note">Заметка (необязательно)</label><input id="note" maxlength="200" placeholder="Например, техника стала лучше">

<label><input type="checkbox" id="pain"> Возникла боль или неприятные симптомы</label>

<button class="primary" type="submit">Сохранить результат</button>

</form>

<p id="logMessage" class="result"></p>

</div>

</section>

<section id="progress">

<div class="panel">

<h2>Мой прогресс</h2>

<label for="progressExercise">Упражнение для графика</label>

<select id="progressExercise"></select>

<canvas id="chart" width="800" height="300" aria-label="График рабочих весов"></canvas>

<p id="chartCaption" class="small">Сохрани первую тренировку, чтобы увидеть историю.</p>

<hr><h3>Следующая цель</h3>

<div id="nextGoal" class="result">Сначала запиши результат упражнения.</div>

</div>

<div class="panel">

<div class="row"><h2>История</h2><button type="button" onclick="exportData()">Экспорт данных</button></div>

<div id="history"></div>

<button type="button" class="danger" onclick="clearHistory()">Удалить всю историю</button>

</div>

</section>

<section id="library">

<div class="panel">

<h2>Библиотека упражнений</h2>

<label for="search">Поиск по названию или мышцам</label>

<input id="search" placeholder="Например, грудь или жим">

<div id="exerciseList"></div>

</div>

</section>

<section>

<div class="panel">

<h2>Правила прогресса</h2>

<p><span class="pill">1</span> Сначала освой технику и стабильный диапазон повторений.</p>

<p><span class="pill">2</span> Если подходы даются уверенно и без боли, попробуй добавить повторение.</p>

<p><span class="pill">3</span> Когда верхняя граница повторений стабильно получается с хорошей техникой, можно рассмотреть небольшой шаг веса.</p>

<p><span class="pill">4</span> Если прогресс остановился, проверь отдых, сон, технику и восстановление.</p>

<p><span class="pill">5</span> При боли не увеличивай нагрузку. При травме следуй рекомендациям медицинского специалиста.</p>

<p class="small">Если тебе меньше 18 лет, используй подходящую нагрузку и попроси квалифицированного тренера проверить технику при необходимости.</p>

</div>

</section>

<footer>GYM PROJECT · Версия 4.0 · Данные хранятся в браузере</footer>

</div>

<script>

const exercises = [
{name:"Жим лёжа",muscle:"Грудь, трицепс",type:"gym",sets:"3–4 × 6–12",how:"Ляг на скамью, поставь стопы устойчиво. Опускай штангу подконтрольно к середине груди, затем выжимай вверх. Не отбивай штангу от груди."},
{name:"Жим гантелей на наклонной скамье",muscle:"Верх груди, трицепс",type:"gym",sets:"3 × 8–12",how:"Установи небольшой наклон. Опускай гантели по сторонам груди без резкого растяжения, выжимай вверх контролируемо."},
{name:"Сведение рук в тренажёре",muscle:"Грудь",type:"gym",sets:"3 × 10–15",how:"Настрой сиденье так, чтобы локти были примерно на уровне груди. Своди руки плавно, не бросай вес при возвращении."},
{name:"Отжимания",muscle:"Грудь, плечи, трицепс",type:"bodyweight",sets:"3 × 6–15",how:"Держи корпус ровно, опускайся контролируемо и отталкивайся от пола. Выбери вариант, в котором сохраняется хорошая техника."},
{name:"Тяга верхнего блока",muscle:"Спина, бицепс",type:"gym",sets:"3 × 8–12",how:"Возьми рукоять, опусти плечи и тяни к верхней части груди. Не раскачивайся и не тяни за голову."},
{name:"Горизонтальная тяга блока",muscle:"Спина, бицепс",type:"gym",sets:"3 × 8–12",how:"Сохраняй нейтральную спину. Тяни рукоять к корпусу, своди лопатки без рывка, медленно возвращай вес."},
{name:"Тяга гантели одной рукой",muscle:"Спина, бицепс",type:"dumbbells",sets:"3 × 8–12 на сторону",how:"Обопрись свободной рукой, держи спину ровно. Веди локоть к тазу, не разворачивай корпус."},
{name:"Приседание с собственным весом",muscle:"Ноги, ягодицы",type:"bodyweight",sets:"3 × 8–15",how:"Стой устойчиво, двигайся в комфортной амплитуде, сохраняй контроль коленей и корпуса. При боли остановись."},
{name:"Жим ногами",muscle:"Квадрицепсы, ягодицы",type:"gym",sets:"3 × 8–12",how:"Поставь стопы устойчиво. Опускай платформу лишь до комфортной глубины, не округляй поясницу и не блокируй колени резко."},
{name:"Румынская тяга с гантелями",muscle:"Задняя поверхность бедра, ягодицы",type:"dumbbells",sets:"3 × 8–12",how:"Слегка согни колени, отводи таз назад, держи гантели близко к ногам. Поднимайся за счёт движения таза, не округляй спину."},
{name:"Ягодичный мост",muscle:"Ягодицы",type:"bodyweight",sets:"3 × 10–15",how:"Ляг на спину, согни ноги. Поднимай таз без чрезмерного прогиба поясницы, затем опускай плавно."},
{name:"Подъём гантелей на бицепс",muscle:"Бицепс",type:"dumbbells",sets:"3 × 8–15",how:"Держи локти близко к корпусу. Поднимай гантели без раскачивания туловища, опускай медленно."},
{name:"Разгибание рук на блоке",muscle:"Трицепс",type:"gym",sets:"3 × 10–15",how:"Прижми локти к корпусу и разгибай руки без движения плечами. Возвращай рукоять под контролем."},
{name:"Жим гантелей сидя",muscle:"Плечи, трицепс",type:"dumbbells",sets:"3 × 8–12",how:"Сядь устойчиво, напряги корпус. Выжимай гантели вверх в комфортной амплитуде, не прогибай поясницу."},
{name:"Подъёмы гантелей в стороны",muscle:"Средняя дельта",type:"dumbbells",sets:"3 × 12–15",how:"Поднимай гантели в стороны без рывка, не пожимай плечами. Выбирай вес, позволяющий контролировать движение."},
{name:"Планка",muscle:"Мышцы корпуса",type:"bodyweight",sets:"3 × 20–45 секунд",how:"Удерживай тело прямым, напряги живот и ягодицы, дыши спокойно. Прекрати подход при потере положения."},
{name:"Скручивания",muscle:"Мышцы живота",type:"bodyweight",sets:"3 × 10–20",how:"Поднимай верх спины за счёт мышц живота, не тяни голову руками. Выполняй без рывков."},
{name:"Подъёмы на носки",muscle:"Икры",type:"gym",sets:"3 × 10–15",how:"Поднимай пятки контролируемо, ненадолго задерживайся наверху и опускайся без пружинящих движений."}
];

const $ = id => document.getElementById(id);
const STORE = "gymProject4Logs";
let logs = [];
try { logs = JSON.parse(localStorage.getItem(STORE) || "[]"); } catch(e) { logs = []; }

function save() {
  try {
    localStorage.setItem(STORE, JSON.stringify(logs));
    return true;
  } catch(e) {
    alert("Не удалось сохранить данные. Проверь настройки браузера и свободное место.");
    return false;
  }
}
function go(id) {
  $(id).scrollIntoView({behavior:"smooth",block:"start"});
}
function esc(value) {
  return String(value ?? "").replace(/[&<>"']/g, c => ({
    "&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"
  }[c]));
}
function fmt(n) {
  return Number(n).toLocaleString("ru-RU",{maximumFractionDigits:2});
}
function initDate() {
  $("logDate").value = new Date().toLocaleDateString("en-CA");
}
function populateOptions() {
  $("exerciseOptions").innerHTML = exercises.map(e =>
    `<option value="${esc(e.name)}">`
  ).join("");
}
function renderLibrary() {
  const query = $("search").value.trim().toLowerCase();
  const filtered = exercises.filter(e =>
    (e.name+" "+e.muscle+" "+e.how).toLowerCase().includes(query)
  );
  $("exerciseList").innerHTML = filtered.map(e => `
    <article class="exercise">
      <h3>${esc(e.name)}</h3>
      <span class="pill">${esc(e.muscle)}</span>
      <p><b>Подходы:</b> ${esc(e.sets)}</p>
      <p>${esc(e.how)}</p>
      <button type="button" onclick="chooseExercise('${esc(e.name)}')">Записать результат</button>
    </article>
  `).join("") || "<p>Ничего не найдено.</p>";
}
function chooseExercise(name) {
  $("exerciseName").value = name;
  go("log");
}
function buildPlan() {
  const days = Number($("days").value);
  const equipment = $("equipment").value;
  const goal = $("goal").value;
  const level = $("level").value;
  const duration = Number($("duration").value);
  const focus = $("focus").value;
  const injured = $("injury").checked;
  const note = $("injuryNote").value.trim();

  let available = exercises.filter(e => {
    if (equipment === "bodyweight") return e.type === "bodyweight";
    if (equipment === "dumbbells") return e.type !== "gym";
    return true;
  });

  const focusTerms = {
    chest:["Грудь"],back:["Спина"],legs:["Ноги","ягодиц","бедра","Квадрицепсы","Икры"],
    arms:["бицепс","трицепс","Плечи","дельта"],core:["корпуса","живота"]
  };
  const preferred = focusTerms[focus];
  if (preferred) {
    const matches = available.filter(e =>
      preferred.some(t => (e.muscle+" "+e.name).toLowerCase().includes(t.toLowerCase()))
    );
    const rest = available.filter(e => !matches.includes(e));
    available = [...matches,...rest];
  }

  let count = duration <= 30 ? 4 : duration <= 45 ? 5 : duration <= 60 ? 6 : 7;
  if (level === "Новичок") count = Math.min(count,5);
  count = Math.min(count,available.length);

  const splitNames = days <= 3
    ? ["Тренировка A — всё тело","Тренировка B — всё тело","Тренировка C — всё тело"]
    : ["Тренировка A — верх тела","Тренировка B — низ тела","Тренировка C — верх тела","Тренировка D — низ тела","Тренировка E — всё тело","Тренировка F — лёгкая"];
  const result = [];
  for (let d=0; d<days; d++) {
    let pool = available.slice();
    if (days <= 3) {
      pool.sort((a,b) => {
        const ca = (a.muscle+" "+a.name).toLowerCase();
        const cb = (b.muscle+" "+b.name).toLowerCase();
        const score = s => /груд|спин|ног|ягодиц|плеч|бицепс|трицепс|корпус|живот/.test(s) ? 1 : 0;
        return score(cb)-score(ca);
      });
    } else {
      const upper = d % 2 === 0;
      pool = pool.filter(e => upper
        ? !/ноги|ягодиц|бедра|квадрицепсы|икры/i.test(e.muscle)
        : /ноги|ягодиц|бедра|квадрицепсы|икры/i.test(e.muscle)
      );
      if (pool.length < 3) pool = available.slice();
    }
    const offset = (d * count) % Math.max(1,pool.length);
    const rotated = pool.slice(offset).concat(pool.slice(0,offset));
    const chosen = rotated.slice(0,count);
    result.push({title:splitNames[d] || `Тренировка ${d+1}`,items:chosen});
  }

  const goalText = goal === "muscle" ? "рост мышц" :
    goal === "strength" ? "развитие силы" :
    goal === "endurance" ? "выносливость" : "общая физическая форма";

  $("planResult").classList.remove("hidden");
  $("planResult").innerHTML = `
    <h2>Твоя программа</h2>
    <p>Цель: <b>${goalText}</b>. Опыт: ${esc(level)}. План на ${days} дней в неделю.</p>
    ${result.map((day,i)=>`
      <div class="exercise">
        <h3>${esc(day.title)}</h3>
        ${day.items.map((e,j)=>`
          <p><b>${j+1}. ${esc(e.name)}</b><br>
          ${esc(e.sets)}<br><span class="small">${esc(e.muscle)}</span></p>
          <button type="button" onclick="chooseExercise('${esc(e.name)}')">Записать упражнение</button>
        `).join("")}
      </div>`).join("")}
    <p><b>Отдых:</b> оставляй время на восстановление между тренировками. Не тренируйся через боль.</p>
    ${injured ? `<p class="danger"><b>Важно:</b> ты указал травму или боль${note ? " ("+esc(note)+")" : ""}. Этот автоматический план не оценивает безопасность упражнений для твоей травмы. Исключи болезненные движения и согласуй нагрузку с врачом или физиотерапевтом.</p>` : ""}
    <p class="small">Это примерный план, а не медицинское назначение. Если упражнение не подходит, замени его на безболезненный вариант.</p>
  `;
}
$("planForm").addEventListener("submit", e => {
  e.preventDefault();
  buildPlan();
});
$("search").addEventListener("input",renderLibrary);

function updateStats() {
  const dates = new Set(logs.map(x=>x.date));
  $("statSessions").textContent = dates.size;
  $("statRecords").textContent = logs.length;
  const names = [...new Set(logs.map(x=>x.exercise))];
  let improved = 0;
  names.forEach(name => {
    const arr = logs.filter(x=>x.exercise===name).sort((a,b)=>a.date.localeCompare(b.date));
    if (arr.length >= 2 && Number(arr[arr.length-1].weight)>Number(arr[arr.length-2].weight)) improved++;
  });
  $("statPR").textContent = improved;
}
function refreshProgressSelect() {
  const old = $("progressExercise").value;
  const names = [...new Set(logs.map(x=>x.exercise))].sort();
  $("progressExercise").innerHTML = names.map(n=>
    `<option value="${esc(n)}">${esc(n)}</option>`
  ).join("");
  if (names.includes(old)) $("progressExercise").value = old;
  drawProgress();
}
$("progressExercise").addEventListener("change",drawProgress);

function drawProgress() {
  const canvas = $("chart");
  const ctx = canvas.getContext("2d");
  const w = canvas.width, h = canvas.height;
  ctx.clearRect(0,0,w,h);
  ctx.strokeStyle="#303b30"; ctx.fillStyle="#a4afa1";
  ctx.font="14px system-ui";
  const name = $("progressExercise").value;
  const arr = logs.filter(x=>x.exercise===name).sort((a,b)=>a.date.localeCompare(b.date));
  if (!arr.length) {
    ctx.fillText("Пока нет записей",w/2-55,h/2);
    $("chartCaption").textContent="Запиши несколько тренировок, чтобы отслеживать изменения.";
    $("nextGoal").textContent="Выбери упражнение и сохрани результат.";
    return;
  }
  const values = arr.map(x=>Number(x.weight));
  const min = Math.min(...values), max = Math.max(...values);
  const lo = Math.max(0,min-(max-min||5)*.2);
  const hi = max+(max-min||5)*.2;
  const left=48,right=w-20,top=24,bottom=h-38;
  for(let i=0;i<5;i++){
    const y=top+(bottom-top)*i/4;
    ctx.beginPath();ctx.moveTo(left,y);ctx.lineTo(right,y);ctx.stroke();
    ctx.fillText(fmt(hi-(hi-lo)*i/4),4,y+4);
  }
  const points=arr.map((x,i)=>({
    x: arr.length===1?(left+right)/2:left+(right-left)*i/(arr.length-1),
    y: bottom-(Number(x.weight)-lo)/(hi-lo)*(bottom-top),
    item:x
  }));
  ctx.strokeStyle="#b8f36b";ctx.lineWidth=3;ctx.beginPath();
  points.forEach((p,i)=>i?ctx.lineTo(p.x,p.y):ctx.moveTo(p.x,p.y));
  ctx.stroke();
  points.forEach(p=>{
    ctx.fillStyle="#b8f36b";ctx.beginPath();ctx.arc(p.x,p.y,5,0,Math.PI*2);ctx.fill();
  });
  ctx.fillStyle="#a4afa1";
  ctx.fillText(arr[0].date,left,bottom+24);
  if(arr.length>1)ctx.fillText(arr[arr.length-1].date,Math.max(left,right-78),bottom+24);
  $("chartCaption").textContent=`${arr.length} записей · от ${fmt(min)} до ${fmt(max)} кг`;
  const last=arr[arr.length-1];
  const previous=arr.length>1?arr[arr.length-2]:null;
  let msg=`Последняя запись: ${fmt(last.weight)} кг, ${last.sets} подхода(ов) × ${last.reps} повторений. `;
  if(last.pain) msg+="Ты отметил боль: не увеличивай нагрузку и обсуди симптомы со специалистом. ";
  else if(previous && Number(last.weight)>Number(previous.weight)) msg+="Вес вырос относительно предыдущей записи. Сохраняй технику и не спеши с дальнейшим увеличением.";
  else msg+="Следующая цель — уверенно повторить результат с хорошей техникой. Если это легко и без боли, можно постепенно добавить повторение.";
  $("nextGoal").textContent=msg;
}

$("logForm").addEventListener("submit", e => {
  e.preventDefault();

  const name = $("exerciseName").value.trim();
  const weight = Number($("weight").value);
  const sets = Number($("sets").value);
  const reps = Number($("reps").value);
  const date = $("logDate").value;

  if (!name || !date || weight < 0 || sets < 1 || reps < 1) {
    $("logMessage").textContent = "Проверь введённые данные.";
    return;
  }

  const entry = {
    id: Date.now().toString() + Math.random().toString(36).slice(2,7),
    exercise: name,
    weight,
    sets,
    reps,
    effort: $("effort").value,
    date,
    note: $("note").value.trim(),
    pain: $("pain").checked
  };

  logs.push(entry);

  if (!save()) {
    logs.pop();
    return;
  }

  $("logMessage").textContent = "Результат сохранён!";
  $("note").value = "";
  $("pain").checked = false;

  renderHistory();
  updateStats();
  refreshProgressSelect();
});

function renderHistory() {
  const sorted = [...logs].sort((a,b) =>
    b.date.localeCompare(a.date) || b.id.localeCompare(a.id)
  );

  $("history").innerHTML = sorted.length
    ? sorted.map(x => `
      <article class="exercise">
        <div class="row">
          <div>
            <h3>${esc(x.exercise)}</h3>
            <span class="small">${esc(x.date)}</span>
          </div>
          <button type="button" class="danger" onclick="deleteEntry('${esc(x.id)}')">Удалить</button>
        </div>
        <p><b>${fmt(x.weight)} кг</b> · ${x.sets} подхода × ${x.reps} повторений</p>
        ${x.note ? `<p>${esc(x.note)}</p>` : ""}
        ${x.pain ? `<p class="danger">Отмечена боль или неприятные симптомы.</p>` : ""}
      </article>
    `).join("")
    : "<p>История пока пустая. Запиши первое упражнение выше.</p>";
}

function deleteEntry(id) {
  if (!confirm("Удалить эту запись?")) return;
  const old = logs;
  logs = logs.filter(x => x.id !== id);
  if (!save()) {
    logs = old;
    return;
  }
  renderHistory();
  updateStats();
  refreshProgressSelect();
}

function clearHistory() {
  if (!logs.length) {
    alert("История уже пустая.");
    return;
  }
  if (!confirm("Удалить все записи тренировок? Это действие нельзя отменить.")) return;
  const old = logs;
  logs = [];
  if (!save()) {
    logs = old;
    return;
  }
  renderHistory();
  updateStats();
  refreshProgressSelect();
}

function exportData() {
  const data = JSON.stringify(logs, null, 2);
  const blob = new Blob([data], {type:"application/json"});
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url;
  a.download = "gym-project-training-history.json";
  document.body.appendChild(a);
  a.click();
  a.remove();
  URL.revokeObjectURL(url);
}

function startApp() {
  initDate();
  populateOptions();
  renderLibrary();
  renderHistory();
  updateStats();
  refreshProgressSelect();
}

startApp();
</script>
</body>
</html>
