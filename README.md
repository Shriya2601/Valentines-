<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine 💖</title>

<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  height:100vh;
  background: linear-gradient(135deg,#ffd6e8,#fff0f6);
  display:flex;
  justify-content:center;
  align-items:center;
  font-family:'Poppins',sans-serif;
  overflow:hidden;
  text-align:center;
}

.screen{
  display:none;
  padding:20px;
  animation:fadeIn 0.8s ease;
}

.active{
  display:block;
}

h1,h2{
  font-family:'Pacifico',cursive;
  color:#ff4d88;
  margin-bottom:15px;
}

p{
  color:#ff4d88;
}

button{
  padding:14px 34px;
  border:none;
  border-radius:40px;
  font-size:18px;
  margin:10px;
  cursor:pointer;
}

.yes{
  background:#ff4d88;
  color:white;
}

.no{
  background:#ffd1dc;
  color:#ff4d88;
}

.no.small{
  transform:scale(0.4);
  opacity:0.6;
}

input{
  padding:12px;
  border-radius:20px;
  border:none;
  text-align:center;
  width:220px;
}

.couple-img{
  width:85%;
  max-width:300px;
  border-radius:25px;
  margin:20px auto;
  box-shadow:0 15px 30px rgba(255,77,136,0.4);
}

.heart{
  position:absolute;
  font-size:22px;
  animation:float 6s infinite;
}

@keyframes float{
  0%{transform:translateY(100vh);opacity:0;}
  50%{opacity:1;}
  100%{transform:translateY(-10vh);opacity:0;}
}

@keyframes fadeIn{
  from{opacity:0;transform:scale(0.9);}
  to{opacity:1;transform:scale(1);}
}
</style>
</head>

<body>

<!-- AUDIO -->
<audio id="bgMusic" src="https://cdn.pixabay.com/audio/2023/02/14/audio_8bdf9a40c4.mp3" loop></audio>
<audio id="clickSound" src="https://www.soundjay.com/buttons/sounds/button-09.mp3"></audio>

<!-- SCREEN 0 -->
<div class="screen active" id="screen0">
  <h1>Enter Password 💌</h1>
  <input type="password" id="password" placeholder="Hint: your name 😉">
  <br><br>
  <button class="yes" onclick="checkPass()">Unlock 💖</button>
</div>

<!-- SCREEN 1 -->
<div class="screen" id="screen1">
  <h1>Click on me 💌</h1>
  <button class="yes" onclick="next()">Tap 💕</button>
</div>

<!-- SCREEN 2 -->
<div class="screen" id="screen2">
  <h2 id="typing"></h2>
  <h1>Will you be my Valentine? 💘</h1>
  <button class="yes" onclick="yes()">YES 😍</button>
  <button class="no" id="noBtn" onclick="no()">NO 🙈</button>
</div>

<!-- SCREEN 3 -->
<div class="screen" id="screen3">
  <h1>Congratulations 🎉</h1>

  <!-- OPTIONAL IMAGE -->
  <img src="us.jpg" class="couple-img" alt="Us">

  <h2>You are officially<br><strong>mine forever 💞</strong></h2>
  <p>Happy Valentine’s Day Chirag 💖</p>
  <p>Love, Shriya 🫶</p>
</div>

<script>
const bgMusic = document.getElementById("bgMusic");
const clickSound = document.getElementById("clickSound");
const noBtn = document.getElementById("noBtn");

function play(){
  clickSound.currentTime = 0;
  clickSound.play();
}

function show(n){
  document.querySelectorAll(".screen").forEach(s=>s.classList.remove("active"));
  document.getElementById("screen"+n).classList.add("active");
}

function checkPass(){
  play();
  if(document.getElementById("password").value.toLowerCase()==="chirag"){
    bgMusic.play();
    show(1);
    hearts();
  }else{
    alert("Wrong password 😝");
  }
}

function next(){
  play();
  show(2);
  typeText();
  hearts();
}

function no(){
  play();
  noBtn.classList.add("small");
  noBtn.innerText="YES 😍";
  noBtn.classList.remove("no");
  noBtn.classList.add("yes");
  noBtn.onclick=yes;
}

function yes(){
  play();
  show(3);
  hearts();
}

function hearts(){
  for(let i=0;i<20;i++){
    const h=document.createElement("div");
    h.className="heart";
    h.innerHTML="💖";
    h.style.left=Math.random()*100+"vw";
    h.style.animationDuration=(Math.random()*3+3)+"s";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),6000);
  }
}

function typeText(){
  const text="Chirag 💕";
  let i=0;
  const el=document.getElementById("typing");
  el.innerHTML="";
  const t=setInterval(()=>{
    el.innerHTML+=text.charAt(i);
    i++;
    if(i>=text.length) clearInterval(t);
  },120);
}
</script>

</body>
</html>
