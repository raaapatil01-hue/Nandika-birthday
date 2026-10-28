<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nandika - Birthday Surprise 🎂</title>

<style>
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  text-align: center;
  color: #fff;
  background: linear-gradient(135deg, #ff758c, #ff7eb3, #a18cd1);
  min-height: 100vh;
}
section {
  min-height: 100vh;
  padding: 35px 18px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.card {
  width: 100%;
  max-width: 520px;
  padding: 28px 20px;
  border-radius: 25px;
  background: rgba(255,255,255,.18);
  border: 1px solid rgba(255,255,255,.4);
  box-shadow: 0 10px 35px #7c245555;
}
h1 { font-size: clamp(30px, 7vw, 48px); }
h2 { font-size: 28px; }
p { font-size: 17px; line-height: 1.7; }
input, button {
  padding: 13px 17px;
  border: none;
  border-radius: 30px;
  margin: 8px;
  font-size: 16px;
}
input { width: min(240px, 90%); text-align: center; }
button {
  cursor: pointer;
  color: #d63370;
  background: #fff;
  font-weight: bold;
}
button:hover { transform: scale(1.04); }
.gift {
  font-size: 100px;
  cursor: pointer;
  animation: bounce 1.5s infinite;
}
.hidden { display: none !important; }
#message { color: #fff6a8; font-weight: bold; }
.memories {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
  gap: 12px;
  margin-top: 20px;
}
.memory {
  background: #ffffff30;
  border-radius: 15px;
  padding: 22px 8px;
  font-size: 32px;
}
.memory p { font-size: 14px; }
@keyframes bounce {
  0%,100% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
}
.heart { position: fixed; bottom: -30px; animation: float 7s linear infinite; }
@keyframes float {
  to { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
}
footer { padding: 20px; }
</style>
</head>

<body>

<section id="lock">
  <div class="card">
    <div style="font-size:65px">💌</div>
    <h1>A Surprise for Nandika</h1>
    <p>Someone has prepared something special for you! 💗</p>
    <p>Enter the secret code to unlock your surprise.</p>
    <input id="code" type="password" placeholder="Enter secret code">
    <br>
    <button onclick="unlock()">Unlock My Surprise 🔓</button>
    <p id="error"></p>
    <p style="font-size:13px">Website creator: change the secret code in the code below.</p>
  </div>
</section>

<section id="welcome" class="hidden">
  <div class="card">
    <h1>🎉 Happy Birthday, Nandika! 🎂</h1>
    <p>Today is all about YOU! 💖</p>
    <p>A little surprise, a little happiness, and lots of beautiful wishes are waiting for you.</p>
    <div class="gift" onclick="openGift()">🎁</div>
    <p>Tap the gift to open it!</p>
    <button onclick="openGift()">Open Your Gift 💝</button>
  </div>
</section>

<section id="surprise" class="hidden">
  <div class="card">
    <div style="font-size:75px">💖🌸💖</div>
    <h1>A Little Message for You</h1>
    <p>
      Dear Nandika,<br>
      May your birthday be filled with laughter, love,
      beautiful memories, and countless reasons to smile.
      May this new year of your life bring you happiness,
      success, and wonderful adventures.
    </p>
    <h2>Keep Smiling! 🥳</h2>
    <p id="message">You deserve a day as wonderful as you are! 💗</p>
    <button onclick="showMemories()">Our Memory Corner 📸</button>
    <button onclick="celebrate()">More Birthday Magic ✨</button>
  </div>
</section>

<section id="memory" class="hidden">
  <div class="card">
    <h1>Little Things, Big Memories 🌷</h1>
    <p>Some moments become memories we keep in our hearts forever.</p>
    <div class="memories">
      <div class="memory">🌸<p>Beautiful Moments</p></div>
      <div class="memory">😂<p>Endless Laughter</p></div>
      <div class="memory">💗<p>Special Memories</p></div>
      <div class="memory">🌈<p>More Adventures</p></div>
    </div>
    <h2>Here's to another wonderful year! 🥂</h2>
    <button onclick="celebrate()">Celebrate Again 🎉</button>
    <button onclick="backToSurprise()">Back 💕</button>
  </div>
</section>

<footer>Made with 💗 for Nandika</footer>

<script>
/* CHANGE THIS TO YOUR OWN SECRET CODE */
const SECRET_CODE = "NANDIKA";

function unlock() {
  const entered = document.getElementById("code").value.trim();
  if (entered.toUpperCase() === SECRET_CODE) {
    document.getElementById("lock").classList.add("hidden");
    document.getElementById("welcome").classList.remove("hidden");
    document.getElementById("error").textContent = "";
  } else {
    document.getElementById("error").textContent =
      "Oops! Try the correct secret code 💗";
  }
}

function openGift() {
  document.getElementById("welcome").classList.add("hidden");
  document.getElementById("surprise").classList.remove("hidden");
  window.scrollTo(0, 0);
}

function showMemories() {
  document.getElementById("surprise").classList.add("hidden");
  document.getElementById("memory").classList.remove("hidden");
  window.scrollTo(0, 0);
}

function backToSurprise() {
  document.getElementById("memory").classList.add("hidden");
  document.getElementById("surprise").classList.remove("hidden");
  window.scrollTo(0, 0);
}

function celebrate() {
  for (let i = 0; i < 35; i++) {
    const h = document.createElement("div");
    h.textContent = ["💖", "✨", "🎉", "🌸", "💕"][
      Math.floor(Math.random() * 5)
    ];
    h.className = "heart";
    h.style.left = Math.random() * 100 + "vw";
    h.style.fontSize = (18 + Math.random() * 25) + "px";
    h.style.animationDuration = (3 + Math.random() * 4) + "s";
    document.body.appendChild(h);
    setTimeout(() => h.remove(), 7500);
  }
}

document.getElementById("code").addEventListener("keydown", function(e) {
  if (e.key === "Enter") unlock();
});
</script>

</body>
</html>
