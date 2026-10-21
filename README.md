# jadwal-pelajaran-8B

<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Jadwal Pelajaran</title>
<style>
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f2f1ff;
  color: #252344;
}
header {
  background: linear-gradient(135deg,#5145cd,#9075ff);
  color: white;
  padding: 30px 20px;
  border-radius: 0 0 28px 28px;
}
header h1 { margin: 0 0 8px; font-size: 28px; }
header p { margin: 0; opacity: .85; }
main { max-width: 850px; margin: 22px auto; padding: 0 15px; }
.days {
  display: grid;
  grid-template-columns: repeat(5,1fr);
  gap: 8px;
  margin-bottom: 20px;
}
.days button {
  border: 0;
  border-radius: 12px;
  padding: 13px 3px;
  background: white;
  color: #5145cd;
  font-weight: bold;
  cursor: pointer;
}
.days button.active {
  background: #6555df;
  color: white;
}
.card {
  background: white;
  padding: 18px;
  border-radius: 18px;
  box-shadow: 0 5px 20px #3830800d;
}
.card h2 { margin-top: 0; font-size: 21px; }
.lesson {
  display: flex;
  align-items: center;
  gap: 13px;
  padding: 14px 0;
  border-bottom: 1px solid #eeeafa;
}
.lesson:last-child { border-bottom: 0; }
.number {
  background: #eeeaff;
  color: #6250d8;
  padding: 10px;
  border-radius: 10px;
  font-weight: bold;
}
.info { flex: 1; }
.info strong { display: block; margin-bottom: 5px; }
.time { color: #77758d; font-size: 13px; }
footer { text-align: center; padding: 25px; color: #77758d; font-size: 13px; }
</style>
</head>
<body>
<header>
  <h1>📚 Jadwal Pelajaran</h1>
  <p>Belajar teratur, raih masa depan!</p>
</header>

<main>
  <div class="days" id="days"></div>
  <section class="card">
    <h2 id="dayTitle">Jadwal Hari Senin</h2>
    <div id="schedule"></div>
  </section>
</main>

<footer>✨ Semangat belajar setiap hari!</footer>

<script>
const days = ["Senin","Selasa","Rabu","Kamis","Jumat"];

const times = [
  "07.00 – 07.45",
  "07.45 – 08.30",
  "08.30 – 09.15",
  "09.30 – 10.15",
  "10.15 – 11.00",
  "11.00 – 11.45",
  "12.30 – 13.15"
];

// Ganti nama pelajaran ini sesuai jadwal sekolahmu.
const subjects = {
  Senin: ["Matematika","Bahasa Indonesia","IPA","IPS","Bahasa Inggris","Informatika","Seni Budaya"],
  Selasa: ["Bahasa Indonesia","Matematika","PPKn","IPA","Bahasa Inggris","PJOK","IPS"],
  Rabu: ["IPA","Matematika","Bahasa Inggris","IPS","Informatika","PPKn","Seni Budaya"],
  Kamis: ["Matematika","Bahasa Indonesia","IPA","Bahasa Inggris","IPS","Agama","PJOK"],
  Jumat: ["Agama","Bahasa Indonesia","Matematika","PPKn","Bahasa Inggris","Prakarya","Wali Kelas"]
};

const daysBox = document.getElementById("days");
const scheduleBox = document.getElementById("schedule");
const title = document.getElementById("dayTitle");

function showDay(day) {
  title.textContent = "Jadwal Hari " + day;
  scheduleBox.innerHTML = "";

  subjects[day].forEach((subject, index) => {
    const lesson = document.createElement("div");
    lesson.className = "lesson";

    const number = document.createElement("div");
    number.className = "number";
    number.textContent = index + 1;

    const info = document.createElement("div");
    info.className = "info";

    const name = document.createElement("strong");
    name.textContent = subject;

    const time = document.createElement("span");
    time.className = "time";
    time.textContent = times[index];

    info.append(name, time);
    lesson.append(number, info);
    scheduleBox.appendChild(lesson);
  });

  document.querySelectorAll(".days button").forEach(button => {
    button.classList.toggle("active", button.dataset.day === day);
  });
}

days.forEach(day => {
  const button = document.createElement("button");
  button.textContent = day;
  button.dataset.day = day;
  button.onclick = () => showDay(day);
  daysBox.appendChild(button);
});

showDay("Senin");
</script>
</body>
</html>
