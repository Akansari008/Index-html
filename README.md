<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Our Love Story ❤️</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap');

body{
  margin:0;
  font-family:'Montserrat',sans-serif;
  overflow:hidden;
}

/* Pages */
.page{
  position:absolute;
  width:100%;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  padding:20px;
  box-sizing:border-box;
  transition:0.7s ease;
  opacity:0;
  transform:translateX(100%);
}

.page.active{
  opacity:1;
  transform:translateX(0);
  z-index:2;
}

.container{max-width:700px;}
h1{font-size:2.3rem;}
p{font-size:1.2rem;}

button{
  padding:12px 25px;
  border:none;
  border-radius:25px;
  background:#ff4d6d;
  color:white;
  cursor:pointer;
  margin-top:20px;
}

button:hover{background:#e63d5c;}

/* Backgrounds */
#page1{background:linear-gradient(#ffc0cb,#dda0dd);}
#page2{background:linear-gradient(#ffdde1,#ee9ca7);}
#page3{background:linear-gradient(#fbc2eb,#a6c1ee);}
#page4{background:linear-gradient(#d4fc79,#96e6a1);}
#secret{background:black;color:white;}

/* Countdown */
#countdown{font-size:1.5rem;font-weight:bold;}

/* Love Letter Modal */
.modal{
  display:none;
  position:fixed;
  top:0;left:0;
  width:100%;height:100%;
  background:rgba(0,0,0,0.7);
  justify-content:center;
  align-items:center;
  z-index:10;
}

.modal-content{
  background:white;
  padding:30px;
  border-radius:20px;
  max-width:500px;
}

/* Fireworks canvas */
canvas{
  position:fixed;
  top:0;left:0;
  pointer-events:none;
  z-index:9;
}
</style>
</head>

<body>

<canvas id="fireworks"></canvas>

<!-- PAGE 1 -->
<div class="page active" id="page1">
<div class="container">
<h1>Our Beginning 💫</h1>
<p>22 April 2025 — where everything started.</p>
<p>A simple conversation turned into destiny.</p>
<button onclick="nextPage()">Next ❤️</button>
</div>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
<div class="container">
<h1>The Day You Said Yes 💍</h1>
<p>16 July 2025 — the most beautiful "Yes".</p>
<button onclick="nextPage()">Continue 🌸</button>
</div>
</div>

<!-- PAGE 3 -->
<div class="page" id="page3">
<div class="container">
<h1>Our Memories 🌷</h1>
<p>Laughs, late nights, small fights…</p>
<p>But my heart always chose you.</p>
<button onclick="nextPage()">Next Window 🌅</button>
</div>
</div>

<!-- PAGE 4 -->
<div class="page" id="page4">
<div class="container">
<h1>The Next Window 🌅</h1>
<p>Countdown to 22 April 2026:</p>
<p id="countdown"></p>
<button onclick="startFireworks()">Say Yes Again 💖</button>
<button onclick="openLetter()">Read Love Letter 💌</button>
</div>
</div>

<!-- SECRET PAGE -->
<div class="page" id="secret">
<div class="container">
<h1>🔐 Secret Page</h1>
<p>You found the hidden heart of this website.</p>
<p>No matter what happens in life…</p>
<h2>I will always choose you. ❤️</h2>
</div>
</div>

<!-- Love Letter Modal -->
<div class="modal" id="letterModal">
<div class="modal-content">
<h2>My Love Letter ❤️</h2>
<p>From the first message to forever…</p>
<p>I choose you in happiness and storms.</p>
<p>I don’t want perfect — I want us.</p>
<button onclick="closeLetter()">Close</button>
</div>
</div>

<script>
let currentPage=1;
const totalPages=5;

// Swipe Support
let startX=0;
document.addEventListener("touchstart",e=>{
  startX=e.touches[0].clientX;
});

document.addEventListener("touchend",e=>{
  let endX=e.changedTouches[0].clientX;
  if(startX-endX>50) nextPage();
  if(endX-startX>50) prevPage();
});

function nextPage(){
  if(currentPage<totalPages){
    document.getElementById("page"+currentPage)?.classList.remove("active");
    if(currentPage===4){
      document.getElementById("page4").classList.remove("active");
      document.getElementById("secret").classList.add("active");
      currentPage=5;
      return;
    }
    currentPage++;
    document.getElementById("page"+currentPage).classList.add("active");
  }
}

function prevPage(){
  if(currentPage>1){
    document.querySelector(".page.active").classList.remove("active");
    currentPage--;
    document.getElementById("page"+currentPage).classList.add("active");
  }
}

/* Countdown */
const countdown=document.getElementById("countdown");
const target=new Date("April 22, 2026 00:00:00").getTime();
setInterval(()=>{
  const now=new Date().getTime();
  const diff=target-now;
  const d=Math.floor(diff/(1000*60*60*24));
  const h=Math.floor((diff%(1000*60*60*24))/(1000*60*60));
  const m=Math.floor((diff%(1000*60*60))/(1000*60));
  const s=Math.floor((diff%(1000*60))/1000);
  countdown.innerHTML=`${d}d ${h}h ${m}m ${s}s`;
},1000);

/* Love Letter */
function openLetter(){
  document.getElementById("letterModal").style.display="flex";
}
function closeLetter(){
  document.getElementById("letterModal").style.display="none";
}

/* Fireworks */
const canvas=document.getElementById("fireworks");
const ctx=canvas.getContext("2d");
canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

function startFireworks(){
  for(let i=0;i<100;i++){
    setTimeout(()=>{
      ctx.fillStyle=`hsl(${Math.random()*360},100%,50%)`;
      ctx.beginPath();
      ctx.arc(Math.random()*canvas.width,
              Math.random()*canvas.height,
              Math.random()*5+2,0,2*Math.PI);
      ctx.fill();
    },i*20);
  }
}

/* Hidden Secret Trigger */
let tapCount=0;
document.getElementById("page4").addEventListener("click",()=>{
  tapCount++;
  if(tapCount===5){
    document.querySelector(".page.active").classList.remove("active");
    document.getElementById("secret").classList.add("active");
    currentPage=5;
  }
});
</script>

</body>
</html>
