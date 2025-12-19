

<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Our Little World ❤️</title>  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #ffe0ef, #dbeeff);
      color: #333;
      overflow-x: hidden;
    }

    section {
      min-height: 100vh;
      display: none;
      padding: 25px 20px 90px;
      animation: fade 0.8s ease;
      text-align: center;
    }

    section.active { display: block; }

    h1 { font-size: 2.1rem; margin-bottom: 10px; }
    p { font-size: 1.05rem; max-width: 700px; margin: auto; line-height: 1.6; }

    button {
      padding: 12px 26px;
      border: none;
      border-radius: 30px;
      background: #ff7aa2;
      color: #fff;
      font-size: 0.95rem;
      cursor: pointer;
      margin-top: 20px;
    }

    button:hover { background: #ff4f87; }

    /* BOTTOM NAV */
    nav {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 65px;
      background: rgba(255,255,255,0.9);
      display: flex;
      justify-content: space-around;
      align-items: center;
      box-shadow: 0 -5px 15px rgba(0,0,0,0.1);
      backdrop-filter: blur(10px);
    }

    nav button {
      background: none;
      color: #ff5f8f;
      font-size: 0.8rem;
      padding: 0;
    }

    /* PHOTOS */
    .photos {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
      gap: 15px;
      margin-top: 25px;
    }

    .photos img {
      width: 100%;
      border-radius: 18px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    }

    /* NOTES */
    .note {
      background: rgba(255,255,255,0.85);
      padding: 18px;
      border-radius: 18px;
      margin: 15px auto;
      max-width: 600px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.1);
    }

    /* TIMELINE */
    .timeline {
      max-width: 700px;
      margin: 30px auto;
      text-align: left;
    }

    .event {
      margin-bottom: 25px;
      padding-left: 20px;
      border-left: 3px solid #ff7aa2;
    }

    .event h3 { margin: 0; color: #ff5f8f; }

    /* FLOATING HEARTS */
    .heart {
      position: fixed;
      bottom: -20px;
      animation: floatUp 6s linear infinite;
      opacity: 0.6;
    }

    @keyframes floatUp {
      from { transform: translateY(0); }
      to { transform: translateY(-110vh); }
    }

    @keyframes fade {
      from { opacity: 0; transform: translateY(15px); }
      to { opacity: 1; transform: translateY(0); }
    }

    audio { display: none; }
  </style></head>
<body><audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio><!-- COUNTDOWN --><section id="countdown" class="active">
  <h1>Counting down to you 🎂</h1>
  <p id="timer"></p>
</section><!-- CAKE --><section id="cake">
  <h1>Make a Wish 💖</h1>
  <div style="font-size:4.5rem;cursor:pointer" onclick="blowCandles()">🎂🔥🔥🔥</div>
</section><!-- BIRTHDAY --><section id="birthday">
  <h1>Happy Birthday My Love ❤️</h1>
  <p>This page stays forever, just like my love for you.</p>
</section><!-- NOTES --><section id="notes">
  <h1>Love Notes 💌</h1>
  <div class="note">No matter how many times you read this — I choose you. Always.</div>
  <div class="note">You are my calm, my chaos, and my happiest place.</div>
  <div class="note">Every future plan I imagine has you in it.</div>
</section><!-- GALLERY --><section id="gallery">
  <h1>Our Memories 📸</h1>
  <div class="photos">
    <img src="photo1.jpg"><img src="photo2.jpg"><img src="photo3.jpg">
    <img src="photo4.jpg"><img src="photo5.jpg"><img src="photo6.jpg">
    <img src="photo7.jpg"><img src="photo8.jpg"><img src="photo9.jpg">
    <img src="photo10.jpg"><img src="photo11.jpg"><img src="photo12.jpg">
  </div>
</section><!-- TIMELINE --><section id="timeline">
  <h1>Our Story 🗓️</h1>
  <div class="timeline">
    <div class="event"><h3>📍 First Meeting</h3><p>The day everything changed.</p></div>
    <div class="event"><h3>❤️ First 'I Love You'</h3><p>A moment I'll never forget.</p></div>
    <div class="event"><h3>✨ Today</h3><p>Still choosing each other.</p></div>
  </div>
</section><!-- SURPRISES --><section id="surprises">
  <h1>Future Surprises 🎁</h1>
  <p>This page will keep growing… just like us.</p>
</section><nav>
  <button onclick="show('birthday')">🎂<br>Birthday</button>
  <button onclick="show('notes')">💌<br>Notes</button>
  <button onclick="show('gallery')">📸<br>Gallery</button>
  <button onclick="show('timeline')">🗓️<br>Timeline</button>
  <button onclick="show('surprises')">🎁<br>Surprises</button>
</nav><script>
  const birthdayDate = new Date('2026-01-02T00:00:00');
  const timerEl = document.getElementById('timer');

  function updateCountdown() {
    const now = new Date();
    const diff = birthdayDate - now;
    if (diff <= 0) {
      show('cake');
      document.getElementById('bgMusic').play();
      return;
    }
    const d = Math.floor(diff / (1000*60*60*24));
    const h = Math.floor((diff / (1000*60*60)) % 24);
    const m = Math.floor((diff / (1000*60)) % 60);
    const s = Math.floor((diff / 1000) % 60);
    timerEl.textContent = `${d} days ${h} hrs ${m} min ${s} sec`;
  }
  setInterval(updateCountdown, 1000);

  function show(id) {
    document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
    document.getElementById(id).classList.add('active');
  }

  function blowCandles() {
    show('birthday');
  }

  setInterval(() => {
    const h = document.createElement('div');
    h.className = 'heart';
    h.textContent = '💖';
    h.style.left = Math.random()*100 + 'vw';
    h.style.fontSize = 14 + Math.random()*20 + 'px';
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),6000);
  }, 600);
</script></body>
</html>
