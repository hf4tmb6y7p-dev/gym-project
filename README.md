# gym-project 
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#10130f">
<title>Gym Project</title>
<style>
:root {
  --bg:#10130f; --panel:#1a1f19;
  --green:#b8ff5c; --muted:#a5afa0;
}
* { box-sizing:border-box; }
body {
  margin:0; background:var(--bg); color:#f5f7f2;
  font-family:-apple-system,BlinkMacSystemFont,Arial,sans-serif;
}
header {
  padding:25px 18px; border-bottom:1px solid #30382b;
}
.logo { color:var(--green); font-weight:900; font-size:25px; }
header p { color:var(--muted); margin-bottom:0; }
main { max-width:760px; margin:auto; padding:20px 15px 45px; }
h2 { font-size:22px; }
.card {
  background:var(--panel); border:1px solid #30382b;
  border-radius:18px; padding:18px; margin-bottom:17px;
}
label { display:block; margin:15px 0 7px; color:#dce4d6; }
input,select {
  width:100%; padding:13px; border-radius:10px;
  border:1px solid #414a3d; background:#10130f;
  color:white; font-size:16px;
}
.grid { display:grid; grid-template-columns:1fr 1fr; gap:12px; }
button {
  width:100%; margin-top:19px; padding:15px;
  background:var(--green); color:#10130f; border:0;
  border-radius:11px; font-size:16px; font-weight:800;
}
.muted { color:var(--muted); line-height:1.5; font-size:14px; }
.result { padding:13px 0; border-bottom:1px solid #30382b; }
.result:last-child { border:0; }
.tag { color:var(--green); font-weight:700; }
.hidden { display:none; }
footer { text-align:center; color:var(--muted); padding:20px; }
@media(max-width:420px) {
  .grid { grid-template-columns:1fr; }
}
</style>
</head>
<body>
<header>
  <div class="logo">GYM PROJECT</div>
  <p>Твой путь. Твоя программа. Твой прогресс.</p>
</header>

<main>
  <section class="card">
    <h2>Создай свой профиль</h2>
    <p class="muted">Расскажи о себе, чтобы подобрать подходящую основу тренировок.</p>
    <form id="profile">
      <label for="sex">Пол</label>
      <select id="sex">
        <option value="male">Мужской</option>
        <option value="female">Женский</option>
        <option value="other">Предпочитаю не указывать</option>
      </select>

      <div class="grid">
        <div>
          <label for="age">Возраст</label>
          <input id="age" type="number" min="13" max="100" placeholder="Например, 18" required>
        </div>
        <div>
          <label for="experience">Опыт тренировок</label>
          <select id="experience">
            <option value="beginner">Новичок</option>
            <option value="some">Есть опыт</option>
            <option value="advanced">Продвинутый</option>
          </select>
        </div>
        <div>
          <label for="height">Рост (см)</label>
          <input id="height" type="number" min="100" max="250" placeholder="178" required>
        </div>
        <div>
          <label for="weight">Вес (кг)</label>
          <input id="weight" type="number" min="25" max="350" step="0.1" placeholder="65" required>
        </div>
      </div>

      <label for="goal">Главная цель</label>
      <select id="goal">
        <option value="muscle">Развитие мышц</option>
        <option value="strength">Развитие силы</option>
        <option value="fitness">Общая физическая форма</option>
      </select>

      <label for="days">Сколько тренировок в неделю?</label>
      <select id="days">
        <option value="2">2 дня</option>
        <option value="3" selected>3 дня</option>
        <option value="4">4 дня</option>
        <option value="5">5 дней</option>
      </select>

      <label for="limitations">Травмы и ограничения</label>
      <input id="limitations" maxlength="200" placeholder="Например, ограничение нагрузки на колено">

      <button type="submit">Создать программу →</button>
    </form>
  </section>

  <section class="card hidden" id="workout">
    <h2>Твоя программа</h2>
    <p class="muted" id="summary"></p>
    <div id="plan"></div>
    <p class="muted">Это базовый шаблон, а не медицинское назначение. При травме упражнения и нагрузки нужно согласовать со специалистом.</p>
    <button id="supplementsButton" type="button">Изучить добавки →</button>
  </section>

  <section class="card hidden" id="supplements">
    <h2>Добавки и питание</h2>
    <p class="muted">Добавки не обязательны для прогресса. Подбор зависит не только от пола, возраста и веса, но и от питания, здоровья и возможных противопоказаний.</p>
    <div class="result">
      <span class="tag">Белок</span>
      <p>Протеин — это удобный пищевой продукт, если обычной еды не хватает для удовлетворения потребности в белке. Он не обязателен, если питания достаточно.</p>
    </div>
    <div class="result">
      <span class="tag">Креатин</span>
      <p>Изучай доказательства эффективности, ограничения и возможные риски. Несовершеннолетним лучше обсуждать применение спортивных добавок с врачом и родителем.</p>
    </div>
    <div class="result">
      <span class="tag">Витамины и минералы</span>
      <p>Полезны при определённых потребностях или дефицитах. Не стоит принимать высокие дозировки наугад.</p>
    </div>
    <div class="result">
      <span class="tag">Основа прогресса</span>
      <p>Регулярное питание, достаточный сон, восстановление и постепенная нагрузка важнее покупки большого количества добавок.</p>
    </div>
  </section>
</main>

<footer>GYM PROJECT · Версия 0.1</footer>

<script>
const $ = id => document.getElementById(id);

$("profile").addEventListener("submit", function(event) {
  event.preventDefault();

  const age = Number($("age").value);
  const height = Number($("height").value);
  const weight = Number($("weight").value);
  const days = Number($("days").value);
  const experience = $("experience").value;
  const goal = $("goal").value;
  const limitations = $("limitations").value.trim();

  if (age < 13 || age > 100 || height < 100 ||
      height > 250 || weight < 25 || weight > 350) {
    alert("Проверь введённые данные.");
    return;
  }

  const goalNames = {
    muscle:"развитие мышц",
    strength:"развитие силы",
    fitness:"общая физическая форма"
  };
  const experienceNames = {
    beginner:"новичок",
    some:"есть опыт",
    advanced:"продвинутый уровень"
  };

  $("summary").textContent =
    `${age} лет · ${height} см · ${weight} кг · ` +
    `${goalNames[goal]} · ${experienceNames[experience]} · ${days} дня(ей) в неделю`;

  const templates = {
    2: [
      ["Тренировка A","Жим в тренажёре · Тяга горизонтального блока · Приседание к скамье при отсутствии ограничений · Упражнение на корпус"],
      ["Тренировка B","Тяга верхнего блока · Ягодичный мост · Жим плеч в тренажёре · Упражнение на корпус"]
    ],
    3: [
      ["Тренировка A","Жим в тренажёре · Тяга горизонтального блока · Упражнение на ноги · Упражнение на корпус"],
      ["Тренировка B","Тяга верхнего блока · Ягодичный мост · Жим плеч в тренажёре · Упражнение на корпус"],
      ["Тренировка C","Жим гантелей при подходящей технике · Тяга блока · Упражнение на заднюю поверхность бедра · Упражнение на корпус"]
    ],
    4: [
      ["Верх тела A","Жим в тренажёре · Тяга горизонтального блока · Тяга верхнего блока"],
      ["Низ тела A","Упражнения для ног с учётом ограничений · Ягодичный мост"],
      ["Верх тела B","Жим плеч в тренажёре · Тяга блока · Упражнения для рук"],
      ["Низ тела B","Упражнения для ног с учётом ограничений · Упражнение на корпус"]
    ],
    5: [
      ["День 1","Грудь и трицепс"],
      ["День 2","Спина и бицепс"],
      ["День 3","Ноги — только разрешённые упражнения"],
      ["День 4","Плечи и корпус"],
      ["День 5","Облегчённая тренировка всего тела"]
    ]
  };

  const chosen = templates[days];
  $("plan").innerHTML = chosen.map((item, i) =>
    `<div class="result"><span class="tag">${item[0]}</span>` +
    `<p>${item[1]}</p><p class="muted">Подходы и нагрузку необходимо адаптировать индивидуально.</p></div>`
  ).join("");

  if (limitations) {
    $("plan").insertAdjacentHTML("afterbegin",
      `<p class="muted">Важно: указано ограничение — ${limitations}. ` +
      `Шаблон не проверяет медицинскую безопасность упражнений. Не выполняй движения, противоречащие рекомендациям специалиста.</p>`
    );
  }

  if (age < 18) {
    $("plan").insertAdjacentHTML("afterbegin",
      '<p class="muted">Для подростков нагрузка должна соответствовать возрасту, технике и восстановлению, желательно под наблюдением квалифицированного тренера.</p>'
    );
  }

  $("workout").classList.remove("hidden");
  $("supplements").classList.add("hidden");
  $("workout").scrollIntoView({behavior:"smooth"});
});

$("supplementsButton").addEventListener("click", () => {
  $("supplements").classList.remove("hidden");
  $("supplements").scrollIntoView({behavior:"smooth"});
});
</script>
</body>
</html>
