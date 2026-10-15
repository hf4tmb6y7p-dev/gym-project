<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#101510">
<title>GYM/PROJECT — твой личный тренер</title>
<style>
:root {
  --bg:#101510;
  --panel:#1a211a;
  --panel2:#202a20;
  --line:#303b30;
  --lime:#b8f36b;
  --text:#f3f5f0;
  --muted:#a4afa1;
  --red:#ff8585;
  --violet:#b4a8ff;
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  margin:0;background:var(--bg);color:var(--text);
  font:15px/1.5 system-ui,-apple-system,sans-serif
}
button,input,select,textarea{font:inherit}
button{cursor:pointer}
button:focus-visible,input:focus-visible,select:focus-visible,
textarea:focus-visible{outline:2px solid var(--lime);outline-offset:2px}
header{
  padding:30px 18px 36px;
  background:radial-gradient(ellipse at 80% 10%,#34462b 0,transparent 50%),
  linear-gradient(135deg,#263526,#101510 75%);
  border-bottom:1px solid var(--line)
}
.wrap{max-width:1000px;margin:auto;padding:16px}
.brand{font-size:12px;letter-spacing:3px;color:var(--lime);font-weight:900}
h1{font-size:clamp(34px,8vw,62px);line-height:1.04;letter-spacing:-2px;margin:16px 0}
h2{font-size:23px;line-height:1.2;margin:0 0 12px}
h3{font-size:17px;margin:0 0 8px}
p{color:var(--muted);line-height:1.6}
.muted{color:var(--muted)}
.small{font-size:12px;color:var(--muted)}
.hero{max-width:700px;margin:auto;text-align:center;padding:18px 0 10px}
.hero p{max-width:500px;margin:0 auto 20px}
.hero .brand{margin-bottom:10px}
.tagline{display:flex;justify-content:center;flex-wrap:wrap;gap:8px;margin-top:16px}
.tagline span,.pill{
  display:inline-block;padding:5px 9px;border-radius:99px;
  background:#293627;color:var(--lime);font-size:11px;font-weight:700
}
button{
  border:1px solid var(--line);background:var(--panel);
  color:var(--text);padding:11px 14px;border-radius:12px
}
button:hover{border-color:var(--lime)}
.primary{background:var(--lime);color:#14200e;border-color:var(--lime);font-weight:850}
.primary:hover{background:#cbff8d}
.large-button{padding:15px 22px;font-size:16px;min-width:210px}
.secondary-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:10px;margin:24px 0}
.option-card{
  min-width:0;text-align:left;padding:15px;border:1px solid var(--line);
  background:linear-gradient(145deg,var(--panel2),var(--panel));
  border-radius:16px;display:flex;flex-direction:column;gap:5px
}
.option-card .symbol{font-size:23px;margin-bottom:3px}
.option-card strong{font-size:14px}
.option-card span:last-child{font-size:12px;line-height:1.45;color:var(--muted)}
.option-card:hover{transform:translateY(-2px);border-color:var(--lime)}
.section-label{font-size:11px;letter-spacing:2px;color:var(--lime);font-weight:800;margin-bottom:8px}
nav{display:flex;gap:7px;overflow-x:auto;padding:12px 0;position:sticky;top:0;background:var(--bg);z-index:5}
nav button{white-space:nowrap;flex-shrink:0;padding:9px 12px;font-size:13px}
section{scroll-margin-top:70px;margin:22px 0}
.panel{background:var(--panel);border:1px solid var(--line);border-radius:18px;padding:18px;margin-bottom:14px}
.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}
.stats{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:10px;margin:22px 0}
.stat{background:#111811;border:1px solid var(--line);border-radius:14px;padding:12px}
.stat strong{display:block;font-size:24px;color:var(--lime)}
.stat span{font-size:11px;color:var(--muted)}
label{display:block;color:var(--muted);font-size:13px;margin:12px 0 6px}
input,select,textarea{
  width:100%;min-width:0;background:#101510;color:var(--text);
  border:1px solid var(--line);border-radius:10px;padding:11px
}
input[type=checkbox]{width:auto;accent-color:var(--lime)}
.checkline{display:flex;gap:9px;align-items:center;margin:14px 0;color:var(--text)}
.checkline label{margin:0;color:var(--text)}
.row{display:flex;gap:10px;align-items:center;flex-wrap:wrap}
.row>*{flex:1}
.actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:14px}
.actions button{flex:1}
.exercise{border:1px solid var(--line);border-radius:14px;padding:14px;margin:10px 0}
.exercise p{margin:7px 0}
.exercise-title{display:flex;justify-content:space-between;gap:10px;align-items:start}
.result{line-height:1.6}
.day{padding:14px 0;border-bottom:1px solid var(--line)}
.day:last-child{border-bottom:0}
.day h3{color:var(--lime)}
.hidden{display:none!important}
hr{border:0;border-top:1px solid var(--line);margin:16px 0}
canvas{width:100%;height:210px;display:block}
.notice{border-left:3px solid var(--lime);padding:10px 12px;background:#20291e;border-radius:0 10px 10px 0;font-size:13px;color:var(--muted)}
.warning{border-left-color:var(--red);background:#2b1d1d}
footer{text-align:center;padding:28px 12px;color:var(--muted);font-size:12px}
.back{margin-bottom:8px}
.empty{padding:18px 0;color:var(--muted);font-size:14px}
@media(max-width:650px){
  .secondary-grid{grid-template-columns:repeat(2,minmax(0,1fr));gap:8px}
  .option-card{padding:12px}
  .option-card .symbol{font-size:20px}
  .option-card strong{font-size:13px}
  .grid{grid-template-columns:1fr}
  .wrap{padding:12px}
  .panel{padding:14px}
  .stat{padding:9px}
  .stat strong{font-size:20px}
  .stats{gap:7px}
  header{padding:24px 14px 28px}
}
@media(max-width:360px){
  .secondary-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>

<header id="homePage">
  <div class="wrap hero">
    <div class="brand">GYM/PROJECT</div>
    <h1>НЕ ТЫ ПОД ПРОГРАММУ.<br>ПРОГРАММА ПОД ТЕБЯ.</h1>
    <p>Твой личный фитнес-помощник. Создавай план тренировок, изучай упражнения и следи за прогрессом.</p>
    <button class="primary large-button" onclick="openView('generator')">Заполнить анкету →</button>
    <div class="tagline">
      <span>ТВОИ ЦЕЛИ</span><span>ТВОЙ ПЛАН</span><span>ТВОЙ ПРОГРЕСС</span>
    </div>
  </div>
</header>

<main class="wrap" id="homeOptions">
  <div class="stats">
    <div class="stat"><strong id="statSessions">0</strong><span>Дней тренировок</span></div>
    <div class="stat"><strong id="statRecords">0</strong><span>Записей упражнений</span></div>
    <div class="stat"><strong id="statPR">0</strong><span>Улучшений по весу</span></div>
  </div>

  <div class="section-label">ЕЩЁ ВОЗМОЖНОСТИ</div>
  <h2>Всё для твоих тренировок</h2>
  <div class="secondary-grid">
    <button class="option-card" onclick="openView('library')">
      <span class="symbol">🏋️</span><strong>Упражнения</strong>
      <span>Библиотека и техника выполнения</span>
    </button>
    <button class="option-card" onclick="openView('log')">
      <span class="symbol">📝</span><strong>Записать тренировку</strong>
      <span>Рабочие веса и повторения</span>
    </button>
    <button class="option-card" onclick="openView('progress')">
      <span class="symbol">📈</span><strong>Мой прогресс</strong>
      <span>История и динамика результатов</span>
    </button>
    <button class="option-card" onclick="openView('guide')">
      <span class="symbol">🎯</span><strong>Правила прогресса</strong>
      <span>Как постепенно улучшать результаты</span>
    </button>
    <button class="option-card" onclick="openView('recovery')">
      <span class="symbol">🌙</span><strong>Восстановление</strong>
      <span>Сон, отдых и самочувствие</span>
    </button>
    <button class="option-card" onclick="openView('nutrition')">
      <span class="symbol">🥗</span><strong>Питание и добавки</strong>
      <span>Базовые знания без волшебных обещаний</span>
    </button>
  </div>
  <p class="small">Твои записи хранятся в браузере этого устройства. Экспортируй историю, чтобы сделать резервную копию.</p>
</main>

<div class="wrap hidden" id="appViews">
  <button class="back" onclick="showHome()">← Главная</button>
  <nav aria-label="Разделы сайта">
    <button onclick="go('generator')">Программа</button>
    <button onclick="go('log')">Запись</button>
    <button onclick="go('progress')">Прогресс</button>
    <button onclick="go('library')">Упражнения</button>
    <button onclick="go('guide')">Советы</button>
  </nav>

  <section id="generator">
    <div class="section-label">ШАГ 1 · ПЕРСОНАЛИЗАЦИЯ</div>
    <div class="panel">
      <h2>Составить программу</h2>
      <p>Выбери параметры — генератор соберёт примерный план из встроенной библиотеки упражнений.</p>
      <form id="planForm">
        <div class="grid">
          <div>
            <label for="goal">Цель</label>
            <select id="goal">
              <option value="muscle">Рост мышц</option>
              <option value="strength">Развитие силы</option>
              <option value="general">Общая форма</option>
              <option value="endurance">Выносливость</option>
            </select>
          </div>
          <div>
            <label for="level">Опыт</label>
            <select id="level">
              <option>Новичок</option>
              <option>Есть опыт</option>
              <option>Продвинутый</option>
            </select>
          </div>
          <div>
            <label for="days">Тренировок в неделю</label>
            <select id="days">
              <option value="2">2 дня</option>
              <option value="3" selected>3 дня</option>
              <option value="4">4 дня</option>
              <option value="5">5 дней</option>
              <option value="6">6 дней</option>
            </select>
          </div>
          <div>
            <label for="equipment">Оборудование</label>
            <select id="equipment">
              <option value="gym">Полный зал</option>
              <option value="dumbbells">Гантели и собственный вес</option>
              <option value="bodyweight">Только собственный вес</option>
            </select>
          </div>
          <div>
            <label for="duration">Длительность тренировки</label>
            <select id="duration">
              <option value="30">30 минут</option>
              <option value="45" selected>45 минут</option>
              <option value="60">60 минут</option>
              <option value="75">75 минут</option>
            </select>
          </div>
          <div>
            <label for="focus">Приоритет</label>
            <select id="focus">
              <option value="all">Всё тело</option>
              <option value="chest">Грудь</option>
              <option value="back">Спина</option>
              <option value="legs">Ноги и ягодицы</option>
              <option value="arms">Руки и плечи</option>
              <option value="core">Корпус</option>
            </select>
          </div>
        </div>
        <div class="checkline">
          <input type="checkbox" id="injury">
          <label for="injury">Есть травма, боль или ограничение движений</label>
        </div>
        <label for="injuryNote">Что учитывать? (необязательно)</label>
        <textarea id="injuryNote" rows="2" placeholder="Например: колено, плечо, спина или рекомендации специалиста"></textarea>
        <p class="small">При травме или продолжающейся боли не используй автоматически сгенерированный план как реабилитацию. Согласуй упражнения со специалистом.</p>
        <button class="primary" type="submit">Создать программу →</button>
      </form>
    </div>
    <div id="planResult" class="panel hidden result" aria-live="polite"></div>
  </section>

  <section id="log">
    <div class="section-label">ТРЕНИРОВОЧНЫЙ ДНЕВНИК</div>
    <div class="panel">
      <h2>Записать результат</h2>
      <p>Внеси результат после тренировки, чтобы отслеживать изменения.</p>
      <form id="logForm">
        <label for="exerciseName">Упражнение</label>
        <input id="exerciseName" list="exerciseOptions" required maxlength="100" placeholder="Например, жим лёжа">
        <datalist id="exerciseOptions"></datalist>
        <div class="grid">
          <div><label for="weight">Вес, кг</label><input id="weight" type="number" min="0" max="1000" step="0.25" value="0" required></div>
          <div><label for="sets">Подходы</label><input id="sets" type="number" min="1" max="30" value="3" required></div>
          <div><label for="reps">Повторения в каждом подходе</label><input id="reps" type="number" min="1" max="200" value="10" required></div>
          <div><label for="logDate">Дата</label><input id="logDate" type="date" required></div>
        </div>
        <label for="effort">Насколько тяжело?</label>
        <select id="effort">
          <option>Легко, большой запас</option>
          <option selected>Умеренно, техника хорошая</option>
          <option>Очень тяжело</option>
        </select>
        <label for="note">Заметка (необязательно)</label>
        <textarea id="note" rows="2" maxlength="500" placeholder="Самочувствие, техника, комментарий"></textarea>
        <div class="checkline">
          <input type="checkbox" id="pain">
          <label for="pain">Возникла боль или неприятные симптомы</label>
        </div>
        <button class="primary" type="submit">Сохранить результат</button>
        <p id="logMessage" class="small" aria-live="polite"></p>
      </form>
    </div>
  </section>

  <section id="progress">
    <div class="section-label">ДАННЫЕ И ДИНАМИКА</div>
    <div class="panel">
      <h2>Мой прогресс</h2>
      <label for="progressExercise">Упражнение для графика</label>
      <select id="progressExercise"></select>
      <canvas id="chart" width="900" height="260" aria-label="График веса по тренировкам"></canvas>
      <p id="chartCaption" class="small">Сохрани первую тренировку, чтобы увидеть историю.</p>
      <hr>
      <h3>Следующая цель</h3>
      <p id="nextGoal">Сначала запиши результат упражнения.</p>
    </div>
    <div class="panel">
      <h2>История</h2>
      <div id="history"></div>
      <hr>
      <div class="actions">
        <button type="button" onclick="exportData()">Экспорт данных</button>
        <button type="button" class="danger" onclick="clearHistory()">Удалить всю историю</button>
      </div>
    </div>
  </section>

  <section id="library">
    <div class="section-label">СПРАВОЧНИК</div>
    <div class="panel">
      <h2>Библиотека упражнений</h2>
      <label for="search">Поиск по названию, мышцам или технике</label>
      <input id="search" type="search" placeholder="Например, грудь, тяга, плечи">
      <div id="exerciseList"></div>
    </div>
  </section>

  <section id="guide">
    <div class="section-label">ПОЛЕЗНЫЕ ПРИВЫЧКИ</div>
    <div class="panel">
      <h2>Правила прогресса</h2>
      <div class="exercise"><strong>01 · Сначала техника</strong><p>Освой движение и стабильный диапазон повторений прежде, чем увеличивать вес.</p></div>
      <div class="exercise"><strong>02 · Прогресс постепенно</strong><p>Если подходы даются уверенно и без боли, можно постепенно добавить повторение. Не обязательно повышать нагрузку на каждой тренировке.</p></div>
      <div class="exercise"><strong>03 · Следи за восстановлением</strong><p>Сон, отдых, питание и регулярность помогают поддерживать тренировочный процесс.</p></div>
      <div class="exercise"><strong>04 · Не тренируйся через боль</strong><p>Остановись при боли или необычных симптомах. При травме следуй рекомендациям медицинского специалиста.</p></div>
      <div class="notice">Если тебе меньше 18 лет, выбирай подходящую нагрузку и попроси квалифицированного тренера проверить технику при необходимости.</div>
    </div>
  </section>

  <section id="recovery">
    <div class="panel">
      <div class="section-label">ВОССТАНОВЛЕНИЕ</div>
      <h2>Результат строится не только в зале</h2>
      <div class="exercise"><strong>Сон</strong><p>Старайся придерживаться регулярного режима сна. Усталость может ухудшать концентрацию и качество техники.</p></div>
      <div class="exercise"><strong>Отдых</strong><p>Чередуй нагрузку и восстановление. Больше тренировок не всегда означает лучший результат.</p></div>
      <div class="exercise"><strong>Самочувствие</strong><p>Отмечай необычную усталость, боль и снижение работоспособности. Не пытайся компенсировать пропущенные занятия чрезмерной нагрузкой.</p></div>
    </div>
  </section>

  <section id="nutrition">
    <div class="panel">
      <div class="section-label">ПИТАНИЕ И ДОБАВКИ</div>
      <h2>Сначала основы</h2>
      <div class="exercise"><strong>Разнообразное питание</strong><p>Регулярные приёмы пищи и разнообразные продукты помогают получать энергию и питательные вещества для повседневной активности.</p></div>
      <div class="exercise"><strong>Вода</strong><p>Пей регулярно, ориентируясь на жажду, погоду и активность. Не нужно заставлять себя пить чрезмерные объёмы.</p></div>
      <div class="exercise"><strong>Добавки — не обязательный шаг</strong><p>Добавки не заменяют питание, сон и грамотную программу. Особенно в подростковом возрасте обсуждай их применение с родителем и медицинским специалистом.</p></div>
      <div class="notice">Этот раздел — общая информация, а не персональное медицинское или диетологическое назначение.</div>
    </div>
  </section>
</div>

<footer>GYM/PROJECT · Твой тренировочный помощник<br>Данные сохраняются локально в браузере</footer>

<script>
"use strict";

const exercises = [
 {name:"Жим лёжа",muscle:"Грудь, трицепс",type:"gym",sets:"3 × 6–12",area:"upper",how:"Ляг на скамью, поставь стопы устойчиво. Опускай штангу подконтрольно к груди и выжимай вверх без отбива."},
 {name:"Жим гантелей на наклонной скамье",muscle:"Верх груди, трицепс",type:"gym",sets:"3 × 8–12",area:"upper",how:"Установи небольшой наклон. Опускай гантели подконтрольно, без резкого растяжения, затем выжимай вверх."},
 {name:"Сведение рук в тренажёре",muscle:"Грудь",type:"gym",sets:"3 × 10–15",area:"upper",how:"Настрой сиденье так, чтобы рукояти были на удобной высоте. Своди руки плавно, не бросай вес."},
 {name:"Отжимания",muscle:"Грудь, плечи, трицепс",type:"bodyweight",sets:"3 × 6–15",area:"upper",how:"Держи корпус ровно, опускайся подконтрольно. Выбирай вариант, в котором техника остаётся стабильной."},
 {name:"Тяга верхнего блока",muscle:"Спина, бицепс",type:"gym",sets:"3 × 8–12",area:"upper",how:"Опусти плечи и тяни рукоять к верхней части груди. Не раскачивайся и не тяни за голову."},
 {name:"Горизонтальная тяга блока",muscle:"Спина, бицепс",type:"gym",sets:"3 × 8–12",area:"upper",how:"Сохраняй нейтральное положение спины. Тяни рукоять к корпусу без рывка и медленно возвращай вес."},
 {name:"Тяга гантели одной рукой",muscle:"Спина, бицепс",type:"dumbbells",sets:"3 × 8–12 на сторону",area:"upper",how:"Обопрись свободной рукой, держи спину ровно. Веди локоть к тазу без разворота корпуса."},
 {name:"Приседание с собственным весом",muscle:"Ноги, ягодицы",type:"bodyweight",sets:"3 × 8–15",area:"lower",how:"Стой устойчиво, двигайся в комфортной амплитуде и сохраняй контроль корпуса."},
 {name:"Жим ногами",muscle:"Квадрицепсы, ягодицы",type:"gym",sets:"3 × 8–12",area:"lower",how:"Поставь стопы устойчиво. Работай в комфортной амплитуде и не блокируй колени резко."},
 {name:"Румынская тяга с гантелями",muscle:"Задняя поверхность бедра, ягодицы",type:"dumbbells",sets:"3 × 8–12",area:"lower",how:"Слегка согни колени, отводи таз назад и держи гантели близко к ногам. Не округляй спину."},
 {name:"Ягодичный мост",muscle:"Ягодицы",type:"bodyweight",sets:"3 × 10–15",area:"lower",how:"Поднимай таз плавно, не переразгибай поясницу, затем подконтрольно опускайся."},
 {name:"Подъём гантелей на бицепс",muscle:"Бицепс",type:"dumbbells",sets:"3 × 8–15",area:"upper",how:"Держи локти близко к корпусу. Не раскачивай туловище и медленно опускай гантели."},
 {name:"Разгибание рук на блоке",muscle:"Трицепс",type:"gym",sets:"3 × 10–15",area:"upper",how:"Держи локти близко к корпусу и разгибай руки без рывков."},
 {name:"Жим гантелей сидя",muscle:"Плечи, трицепс",type:"dumbbells",sets:"3 × 8–12",area:"upper",how:"Сядь устойчиво, напряги корпус. Работай в комфортной амплитуде без чрезмерного прогиба."},
 {name:"Подъёмы гантелей в стороны",muscle:"Средняя дельта",type:"dumbbells",sets:"3 × 12–15",area:"upper",how:"Поднимай гантели без рывка. Выбирай вес, который можешь контролировать."},
 {name:"Планка",muscle:"Мышцы корпуса",type:"bodyweight",sets:"3 × 20–45 секунд",area:"core",how:"Удерживай тело ровно, напряги живот и дыши спокойно. Прекрати подход, если теряешь положение."},
 {name:"Скручивания",muscle:"Мышцы живота",type:"bodyweight",sets:"3 × 10–20",area:"core",how:"Поднимай верх спины за счёт мышц живота, не тяни голову руками и избегай рывков."},
 {name:"Подъёмы на носки",muscle:"Икры",type:"gym",sets:"3 × 10–15",area:"lower",how:"Поднимай пятки подконтрольно и опускай без пружинящих движений."}
];

const $ = id => document.getElementById(id);
const STORE = "gymProject4Logs";
let logs = [];

try {
  const saved = JSON.parse(localStorage.getItem(STORE) || "[]");
  logs = Array.isArray(saved) ? saved.filter(x => x && typeof x === "object") : [];
} catch(e) { logs = []; }

function esc(value) {
  return String(value ?? "").replace(/[&<>"']/g, c => ({
    "&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"
  })[c]);
}
function fmt(n) {
  return Number(n).toLocaleString("ru-RU",{maximumFractionDigits:2});
}
function save() {
  try {
    localStorage.setItem(STORE,JSON.stringify(logs));
    return true;
  } catch(e) {
    alert("Не удалось сохранить данные. Проверь настройки браузера.");
    return false;
  }
}
function showHome() {
  $("homePage").classList.remove("hidden");
  $("homeOptions").classList.remove("hidden");
  $("appViews").classList.add("hidden");
  window.scrollTo({top:0,behavior:"smooth"});
}
function openView(id) {
  $("homePage").classList.add("hidden");
  $("homeOptions").classList.add("hidden");
  $("appViews").classList.remove("hidden");
  go(id);
}
function go(id) {
  const el = $(id);
  if(el) el.scrollIntoView({behavior:"smooth",block:"start"});
}
function initDate() {
  const d = new Date();
  $("logDate").value = [
    d.getFullYear(),
    String(d.getMonth()+1).padStart(2,"0"),
    String(d.getDate()).padStart(2,"0")
  ].join("-");
}
function populateOptions() {
  $("exerciseOptions").innerHTML = exercises.map(e =>
    `<option value="${esc(e.name)}"></option>`
  ).join("");
}
function renderLibrary() {
  const q = $("search").value.trim().toLowerCase();
  const filtered = exercises.filter(e =>
    (e.name+" "+e.muscle+" "+e.how).toLowerCase().includes(q)
  );
  $("exerciseList").innerHTML = filtered.map(e => `
    <article class="exercise">
      <div class="exercise-title">
        <div><h3>${esc(e.name)}</h3><span class="pill">${esc(e.muscle)}</span></div>
      </div>
      <p><strong>Ориентир:</strong> ${esc(e.sets)}</p>
      <p>${esc(e.how)}</p>
      <button type="button" onclick="chooseExercise('${esc(e.name).replace(/'/g,"&#39;")}')">Записать результат</button>
    </article>
  `).join("") || `<div class="empty">Ничего не найдено. Попробуй другое название.</div>`;
}
function chooseExercise(name) {
  $("exerciseName").value = name;
  openView("log");
  $("exerciseName").focus({preventScroll:true});
}
function equipmentFilter(e, equipment) {
  if(equipment === "bodyweight") return e.type === "bodyweight";
  if(equipment === "dumbbells") return e.type !== "gym";
  return true;
}
function injuryFilter(list, note) {
  const s = note.toLowerCase();
  let areas = [];
  if(/колен|голен|икр|лодыж|бедр|ног/.test(s)) areas.push("lower");
  if(/плеч|локт|запяст|кист|рук/.test(s)) areas.push("upper");
  if(/поясниц|спин|позвон|ше[яи]/.test(s)) areas.push("back");
  if(/живот|корпус|таз/.test(s)) areas.push("core");
  if(!areas.length) return list;
  return list.filter(e => {
    if(areas.includes("lower") && e.area === "lower") return false;
    if(areas.includes("upper") && e.area === "upper") return false;
    if(areas.includes("core") && e.area === "core") return false;
    if(areas.includes("back") && /тяга|планка|скручиван|румынская/i.test(e.name)) return false;
    return true;
  });
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

  let available = exercises.filter(e => equipmentFilter(e,equipment));
  if(injured && note) available = injuryFilter(available,note);

  const terms = {
    chest:/груд/,
    back:/спин|тяга верх|горизонтальная тяга/,
    legs:/ноги|ягодиц|бедр|квадрицепс|икры/,
    arms:/бицепс|трицепс|плечи|дельта/,
    core:/корпус|живот/
  };
  if(terms[focus]) {
    const preferred = available.filter(e => terms[focus].test(e.muscle+" "+e.name));
    const rest = available.filter(e => !preferred.includes(e));
    available = [...preferred,...rest];
  }

  let count = duration <= 30 ? 4 : duration <= 45 ? 5 : duration <= 60 ? 6 : 7;
  if(level === "Новичок") count = Math.min(count,5);
  count = Math.min(count,available.length);

  if(!available.length) {
    $("planResult").classList.remove("hidden");
    $("planResult").innerHTML = `<h2>Не удалось собрать план</h2>
      <p>По выбранным ограничениям не осталось подходящих упражнений. Измени оборудование или обсуди безопасные варианты со специалистом.</p>`;
    return;
  }

  const names = days <= 3
    ? ["Тренировка A — всё тело","Тренировка B — всё тело","Тренировка C — всё тело"]
    : ["Тренировка A","Тренировка B","Тренировка C","Тренировка D","Тренировка E","Тренировка F"];
  const used = new Set();
  const result = [];

  for(let d=0; d<days; d++) {
    let pool = [...available];
    if(days >= 4) {
      const lowerDay = d % 2 === 1;
      const specific = pool.filter(e => lowerDay ? e.area==="lower" : e.area!=="lower");
      const other = pool.filter(e => !specific.includes(e));
      pool = [...specific,...other];
    }
    if(focus !== "all" && terms[focus]) {
      pool.sort((a,b) => Number(terms[focus].test(b.muscle+" "+b.name))-Number(terms[focus].test(a.muscle+" "+a.name)));
    }
    pool.sort((a,b) => Number(used.has(a.name))-Number(used.has(b.name)));
    const chosen = pool.slice(0,count);
    chosen.forEach(e => used.add(e.name));
    result.push({title:names[d] || `Тренировка ${d+1}`,items:chosen});
  }

  const goalText = {
    muscle:"рост мышц",strength:"развитие силы",
    general:"общая физическая форма",endurance:"выносливость"
  }[goal];

  $("planResult").classList.remove("hidden");
  $("planResult").innerHTML = `
    <div class="section-label">ТВОЙ ПЛАН</div>
    <h2>Программа тренировок</h2>
    <p>Цель: <strong>${goalText}</strong> · Опыт: <strong>${esc(level)}</strong> · Дней в неделю: <strong>${days}</strong></p>
    ${result.map(day => `
      <div class="day">
        <h3>${esc(day.title)}</h3>
        ${day.items.map((e,i) => `
          <div class="exercise">
            <strong>${i+1}. ${esc(e.name)}</strong>
            <p>${esc(e.muscle)} · ${esc(e.sets)}</p>
            <p>${esc(e.how)}</p>
            <button type="button" onclick="chooseExercise('${esc(e.name).replace(/'/g,"&#39;")}')">Записать результат</button>
          </div>
        `).join("")}
      </div>
    `).join("")}
    <p>Отдыхай между тренировками и выполняй упражнения с контролируемой техникой. Количество подходов и повторений — ориентир, а не обязательство.</p>
    ${injured ? `<div class="notice warning"><strong>Важное предупреждение.</strong> Ты указал травму, боль или ограничение. ${note ? "Указанная область: "+esc(note)+". " : ""}Фильтр ориентируется только на отдельные слова и не умеет диагностировать травмы. Он может пропустить неподходящее движение. Не используй этот план для реабилитации: согласуй упражнения со специалистом и не выполняй движения, вызывающие боль.</div>` : ""}
    <p class="small">Это автоматически составленный примерный план, а не медицинское назначение. Настоящий ИИ пока не подключён.</p>
  `;
}
$("planForm").addEventListener("submit",e => {
  e.preventDefault();
  buildPlan();
});

$("search").addEventListener("input",renderLibrary);

function updateStats() {
  $("statSessions").textContent = new Set(logs.map(x=>x.date)).size;
  $("statRecords").textContent = logs.length;
  let improved = 0;
  [...new Set(logs.map(x=>x.exercise))].forEach(name => {
    const arr = logs.filter(x=>x.exercise===name).sort((a,b)=>a.date.localeCompare(b.date));
    if(arr.length >= 2 && Number(arr[arr.length-1].weight)>Number(arr[arr.length-2].weight)) improved++;
  });
  $("statPR").textContent = improved;
}
function refreshProgressSelect() {
  const old = $("progressExercise").value;
  const names = [...new Set(logs.map(x=>x.exercise))].sort();
  $("progressExercise").innerHTML = names.map(n=>`<option value="${esc(n)}">${esc(n)}</option>`).join("");
  if(names.includes(old)) $("progressExercise").value = old;
  drawProgress();
}
$("progressExercise").addEventListener("change",drawProgress);

function drawProgress() {
  const canvas = $("chart");
  const ctx = canvas.getContext("2d");
  const w = canvas.width, h = canvas.height;
  ctx.clearRect(0,0,w,h);
  ctx.strokeStyle="#303b30";
  ctx.fillStyle="#a4afa1";
  ctx.font="13px system-ui";
  const name = $("progressExercise").value;
  const arr = logs.filter(x=>x.exercise===name).sort((a,b)=>a.date.localeCompare(b.date));
  if(!arr.length) {
    ctx.fillText("Пока нет записей",w/2-55,h/2);
    $("chartCaption").textContent="Запиши несколько тренировок, чтобы отслеживать изменения.";
    $("nextGoal").textContent="Выбери упражнение и сохрани результат.";
    return;
  }
  const values = arr.map(x=>Number(x.weight));
  const min = Math.min(...values), max = Math.max(...values);
  const lo = Math.max(0,min-(max-min||5)*.2);
  const hi = max+(max-min||5)*.2;
  const left=55,right=w-20,top=20,bottom=h-40;
  for(let i=0;i<5;i++) {
    const y=top+(bottom-top)*i/4;
    ctx.beginPath();ctx.moveTo(left,y);ctx.lineTo(right,y);ctx.stroke();
    ctx.fillText(fmt(hi-(hi-lo)*i/4),4,y+4);
  }
  const points=arr.map((x,i)=>({
    x:arr.length===1?(left+right)/2:left+(right-left)*i/(arr.length-1),
    y:bottom-(Number(x.weight)-lo)/(hi-lo)*(bottom-top),
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
  if(arr.length>1) ctx.fillText(arr[arr.length-1].date,Math.max(left,right-78),bottom+24);
  $("chartCaption").textContent=`${arr.length} записей · от ${fmt(min)} до ${fmt(max)} кг`;
  const last=arr[arr.length-1], prev=arr.length>1?arr[arr.length-2]:null;
  let msg=`Последняя запись: ${fmt(last.weight)} кг, ${last.sets} подхода × ${last.reps} повторений. `;
  if(last.pain) msg+="Ты отметил боль: не увеличивай нагрузку и обсуди симптомы со специалистом.";
  else if(prev && Number(last.weight)>Number(prev.weight)) msg+="Вес выше предыдущей записи. Сохраняй технику и не спеши с дальнейшим увеличением.";
  else msg+="Следующая цель — уверенно повторить результат с хорошей техникой. Не обязательно увеличивать вес каждый раз.";
  $("nextGoal").textContent=msg;
}

$("logForm").addEventListener("submit",e=>{
  e.preventDefault();
  const name=$("exerciseName").value.trim();
  const weight=Number($("weight").value);
  const sets=Number($("sets").value);
  const reps=Number($("reps").value);
  const date=$("logDate").value;
  if(!name || !date || !Number.isFinite(weight) || weight<0 || sets<1 || reps<1) {
    $("logMessage").textContent="Проверь введённые данные.";
    return;
  }
  const entry={
    id:Date.now().toString()+Math.random().toString(36).slice(2,7),
    exercise:name,weight,sets,reps,effort:$("effort").value,date,
    note:$("note").value.trim(),pain:$("pain").checked
  };
  logs.push(entry);
  if(!save()){logs.pop();return;}
  $("logMessage").textContent="Результат сохранён!";
  $("note").value="";
  $("pain").checked=false;
  renderHistory();
  updateStats();
  refreshProgressSelect();
});

function renderHistory() {
  const sorted=[...logs].sort((a,b)=>b.date.localeCompare(a.date)||b.id.localeCompare(a.id));
  $("history").innerHTML=sorted.length ? sorted.map(x=>`
    <article class="exercise">
      <div class="exercise-title">
        <div><h3>${esc(x.exercise)}</h3><span class="small">${esc(x.date)}</span></div>
        <button type="button" onclick="deleteEntry('${esc(x.id)}')">Удалить</button>
      </div>
      <p><strong>${fmt(x.weight)} кг</strong> · ${x.sets} подхода × ${x.reps} повторений</p>
      <p class="small">${esc(x.effort||"")}</p>
      ${x.note?`<p>${esc(x.note)}</p>`:""}
      ${x.pain?`<p class="danger">Отмечена боль или неприятные симптомы.</p>`:""}
    </article>
  `).join(""):`<div class="empty">История пока пустая. Запиши первое упражнение.</div>`;
}
function deleteEntry(id) {
  if(!confirm("Удалить эту запись?")) return;
  const old=logs;
  logs=logs.filter(x=>x.id!==id);
  if(!save()){logs=old;return;}
  renderHistory();updateStats();refreshProgressSelect();
}
function clearHistory() {
  if(!logs.length){alert("История уже пустая.");return;}
  if(!confirm("Удалить все записи тренировок? Это действие нельзя отменить.")) return;
  const old=logs;logs=[];
  if(!save()){logs=old;return;}
  renderHistory();updateStats();refreshProgressSelect();
}
function exportData() {
  const blob=new Blob([JSON.stringify(logs,null,2)],{type:"application/json"});
  const url=URL.createObjectURL(blob);
  const a=document.createElement("a");
  a.href=url;a.download="gym-project-training-history.json";
  document.body.appendChild(a);a.click();a.remove();
  setTimeout(()=>URL.revokeObjectURL(url),1000);
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
