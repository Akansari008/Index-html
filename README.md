# Index-html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Our Love Story ❤️</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap');
    body, html {
      margin: 0;
      padding: 0;
      font-family: 'Montserrat', sans-serif;
      background: linear-gradient(to bottom right, #ffc0cb, #ffe4e1, #dda0dd);
      overflow-x: hidden;
      overflow-y: hidden;
    }
    .container {
      position: relative;
      max-width: 800px;
      margin: 0 auto;
      padding: 50px 20px;
      text-align: center;
      z-index: 1;
    }
    h1 { font-size: 2.5rem; margin-bottom: 20px; }
    p { font-size: 1.2rem; margin: 15px 0; }
    .button {
      background-color: #ff4d6d;
      color: white;
      border: none;
      padding: 12px 25px;
      margin: 10px;
      font-size: 1rem;
      border-radius: 25px;
      cursor: pointer;
      transition: 0.3s;
    }
    .button:hover { background-color: #e63d5c; }
    /* Floating hearts */
    .heart {
      position: absolute;
      bottom: -50px;
      color: #ff4d6d;
      font-size: 20px;
      animation: floatUp linear infinite;
      pointer-events: none;
      z-index: 0;
    }
    @keyframes floatUp {
      0% { transform: translateY(0) scale(1); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(-700px) scale(1.5); opacity: 0; }
    }
    /* Modals */
    .modal {
      display: none;
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0,0,0,0.6);
      justify-content: center;
      align-items: center;
      z-index: 2;
    }
    .modal-content {
      background: white;
      border-radius: 20px;
      padding: 30px;
      max-width: 500px;
      width: 90%;
      text-align: center;
    }
    .close-btn { margin-top: 20px; }
    .hidden-btn { opacity: 0; transition: 0.7s; }
    .hidden-btn:hover { opacity: 1; }
  </style>
</head>
<body>
  <div class="container">
    <h1>Our Beginning 💫</h1>
    <p>It all started on <strong>22 April 2025</strong>… A simple group chat, a random conversation, and destiny quietly doing its magic.</p>
    <p>I never knew that one message on Instagram would turn into something so meaningful, so beautiful, and so life-changing.</p>
    <p>That day wasn’t just normal… it was the beginning of us, <strong>Kausar Qureshi</strong>. ❤️</p>
    <h1>The Day You Said Yes ❤️</h1>
    <p><strong>16 July 2025</strong> — the day my heart found its forever.</p>
    <p>When you accepted my proposal, Kausar Qureshi, it felt like the whole world paused just to celebrate us.</p>
    <p>That "yes" wasn’t just a word… it was a promise, a dream, a lifetime wrapped in one heartbeat.</p>
    <h1>Our Memories 🌸</h1>
    <p>We laughed together. We stayed up late talking about everything and nothing.</p>
    <p>We had misunderstandings, small fights, moments of silence… but even in those times, my heart still chose you, Kausar.</p>
    <p>Today, I hold onto the smiles, the warmth, and the love — leaving the bad memories behind.</p>
    <h1>The Next Window… 🌅</h1>
    <p>This is not just a celebration of one year since our first talk…</p>
    <p>It is the opening of our next window — a future where we grow together, understand each other deeper, and love each other stronger every single day.</p>
    <p class="font-bold">Countdown to our 1 year of first talk anniversary:</p>
    <p id="countdown" style="font-size:1.5rem; font-weight:bold;"></p>
    <p class="font-bold">Kausar Qureshi, will you continue this beautiful journey with me… forever? 💍</p>    
    <button class="button" id="loveLetterBtn">Say Yes Again 💖</button>
    <button class="button hidden-btn" id="surpriseBtn" title="Click me for a surprise! 👀💍">👀💍</button>
  </div>
  <!-- Love Letter Modal -->
  <div class="modal" id="loveLetterModal">
    <div class="modal-content">
      <h2>My Love Letter to You ❤️</h2>
      <p>My dearest Kausar Qureshi,</p>
      <p>From the day we started talking on 22 April 2025, my life has changed in ways I never imagined. You brought warmth into my ordinary days and turned simple conversations into precious memories.</p>
      <p>Yes, we had ups and downs. But every challenge only made my feelings stronger. I don’t want a perfect love story — I want ours. Real, honest, forever.</p>
      <p>I promise to choose you in happiness and in storms, in laughter and in silence. I promise to grow with you, respect you, and love you more with each passing year.</p>
      <p><strong>Forever yours. 💖</strong></p>
      <button class="button close-btn" onclick="closeModal('loveLetterModal')">Close</button>
    </div>
  </div>  
  <!-- Secret Surprise Modal -->
  <div class="modal" id="surpriseModal">
    <div class="modal-content">
      <h2>💖 Surprise! 💖</h2>
      <p>Kausar Qureshi, here’s a little twist… a secret promise hidden in your heart. Every time you see this page, remember that our love has endless surprises, just like this one. 💍✨</p>
      <p><strong>I love you forever! ❤️</strong></p>
      <button class="button close-btn" onclick="closeModal('surpriseModal')">Close Surprise</button>
    </div>
  </div>

  <script>
    // Countdown Timer
    const countdownElement = document.getElementById('countdown');
    const targetDate = new Date('April 22, 2026 00:00:00').getTime();

    setInterval(() => {
      const now = new Date().getTime();
      const distance = targetDate - now;
      const days = Math.floor(distance / (1000*60*60*24));
      const hours = Math.floor((distance % (1000*60*60*24)) / (1000*60*60));
      const minutes = Math.floor((distance % (1000*60*60)) / (1000*60));
      const seconds = Math.floor((distance % (1000*60)) / 1000);
      countdownElement.innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;
    }, 1000);

    // Modals
    const loveLetterBtn = document.getElementById('loveLetterBtn');
    const surpriseBtn = document.getElementById('surpriseBtn');

    loveLetterBtn.onclick = () => { document.getElementById('loveLetterModal').style.display = 'flex'; };
    surpriseBtn.onclick = () => { document.getElementById('surpriseModal').style.display = 'flex'; };

    function closeModal(id) {
      document.getElementById(id).style.display = 'none';
    }

    // Generate floating hearts
    for(let i=0;i<30;i++){
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.style.left = Math.random()*100+'%';
      heart.style.fontSize = 20 + Math.random()*20 + 'px';
      heart.style.animationDuration = 5 + Math.random()*5 + 's';
      heart.innerHTML = '❤️';
      document.body.appendChild(heart);
    }
    // Reveal hidden surprise button after 3 seconds
    setTimeout(() => {
      surpriseBtn.style.opacity = '1';
    }, 3000);
  </script>
</body>
</html>
