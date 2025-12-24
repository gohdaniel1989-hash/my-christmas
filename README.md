# my-christmas
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Merry Christmas 🎄</title>
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@400;600&display=swap');

* { box-sizing: border-box; }

body {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  /* Christmas Gradient Background */
  background: radial-gradient(circle at center, #2b0505 0%, #05111a 100%);
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  position: relative;
}

.page {
  display: none;
  background: rgba(255, 255, 255, 0.12);
  padding: 40px 25px;
  border-radius: 25px;
  width: 88%; /* Mobile width optimization */
  max-width: 380px;
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 15px 35px rgba(0,0,0,0.7);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  z-index: 10;
  animation: slideUp 0.6s ease-out;
}

.page.active { display: block; }

@keyframes slideUp {
  0% { opacity: 0; transform: translateY(50px) scale(0.9); }
  100% { opacity: 1; transform: translateY(0) scale(1); }
}

h1, h2 {
  font-family: 'Pacifico', cursive;
  margin-bottom: 20px;
  color: #ff4d4d;
  font-size: 2.2rem;
  text-shadow: 0 0 10px rgba(255, 77, 77, 0.5);
}

p {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 30px;
}

button {
  width: 100%;
  padding: 16px;
  font-size: 1.1rem;
  font-weight: 600;
  border: none;
  border-radius: 50px;
  background: linear-gradient(45deg, #d42426, #b30000);
  color: white;
  cursor: pointer;
  box-shadow: 0 5px 15px rgba(212, 36, 38, 0.4);
  transition: all 0.3s ease;
  margin-bottom: 10px;
}

button:active {
  transform: scale(0.95);
}

.secondary-btn {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255,255,255,0.3);
  margin-top: 10px;
}

/* Snowflake styling */
.snowflake {
  position: fixed;
  top: -10px;
  color: white;
  z-index: 1;
  user-select: none;
  pointer-events: none;
  animation: fall linear infinite;
  text-shadow: 0 0 5px rgba(255,255,255,0.8);
}

@keyframes fall {
  0% { transform: translateY(-10px) rotate(0deg); }
  100% { transform: translateY(110vh) rotate(360deg); }
}
</style>
</head>
<body>

<audio id="music" loop>
  <source src="https://www.chosic.com/wp-content/uploads/2021/11/Jingle-Bells-3.mp3" type="audio/mpeg">
</audio>

<div class="page active" id="page1">
  <h1>🎄 Merry Christmas 🎄</h1>
  <p>Wishing you a season filled with<br><b>Magic & Happiness</b> ✨</p>
  <button onclick="startCelebration()">🎁 Play & Wish</button>
</div>

<div class="page" id="page2">
  <h2>🎅 Season of Love</h2>
  <p>Christmas is about love ❤️<br>kindness 🤝 and togetherness ✨</p>
  <button onclick="nextPage(3)">Next ➡️</button>
  <button class="secondary-btn" onclick="nextPage(1)">⬅️ Back</button>
</div>

<div class="page" id="page3">
  <h2>❄️ Keep Smiling</h2>
  <p>May your home be filled with<br>laughter 😄 and peace 🕊️</p>
  <button onclick="nextPage(4)">Next ➡️</button>
  <button class="secondary-btn" onclick="nextPage(2)">⬅️ Back</button>
</div>

<div class="page" id="page4">
  <h2>🎆 Happy 2026!</h2>
  <p>Thank you for being part<br>of this beautiful journey 🙏<br><br>Merry Christmas! 🎄</p>
  <button class="secondary-btn" onclick="nextPage(3)">⬅️ Back</button>
</div>

<script>
function launchConfetti() {
  confetti({
    particleCount: 120,
    spread: 70,
    origin: { y: 0.7 },
    colors: ['#ff0000', '#228b22', '#ffffff', '#ffd700']
  });
}

function startCelebration() {
  const music = document.getElementById("music");
  music.play().catch(e => console.log("Audio needs user interaction"));
  launchConfetti();
  nextPage(2);
}

function nextPage(num){
  launchConfetti();
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('page' + num).classList.add('active');
}

// Snowfall generator
const snowCount = 50;
for(let i=0; i<snowCount; i++){
  const snow = document.createElement('div');
  snow.className = 'snowflake';
  snow.style.left = Math.random() * 100 + 'vw';
  snow.style.fontSize = (Math.random() * 15 + 10) + 'px';
  snow.style.animationDuration = (Math.random()*5 + 5) + 's';
  snow.style.opacity = Math.random();
  snow.innerHTML = '❄️';
  document.body.appendChild(snow);
}
</script>

</body>
</html>
