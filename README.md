<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Be My Valentine 💖</title>

<style>
body {
margin: 0;
height: 100vh;
font-family: 'Comic Sans MS', cursive;
background: linear-gradient(135deg, #ff9a9e, #fad0c4);
overflow: hidden;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
text-align: center;
}

h1 {
font-size: 3em;
color: #fff;
text-shadow: 2px 2px 5px rgba(0,0,0,0.2);
}

h2 {
color: white;
}

.buttons {
margin-top: 30px;
position: relative;
width: 300px;
height: 200px;
}

button {
font-size: 1.5em;
padding: 15px 30px;
border: none;
border-radius: 30px;
cursor: pointer;
position: absolute;
transition: 0.2s;
}

#yes {
background: #ff4d6d;
color: white;
left: 50%;
transform: translateX(-50%);
}

#no {
background: white;
color: #ff4d6d;
}

/* Floating hearts */
.heart {
position: fixed;
bottom: -20px;
font-size: 24px;
animation: floatUp 6s linear infinite;
opacity: 0.8;
pointer-events: none;
}

@keyframes floatUp {
0% {
transform: translateY(0) scale(1);
opacity: 1;
}
100% {
transform: translateY(-110vh) scale(1.5);
opacity: 0;
}
}

/* Explosion hearts */
.boom {
position: fixed;
font-size: 24px;
animation: explode 1.2s ease-out forwards;
pointer-events: none;
}

@keyframes explode {
0% {
transform: translate(0, 0) scale(1);
opacity: 1;
}
100% {
transform: translate(var(--x), var(--y)) scale(1.8);
opacity: 0;
}
}
</style>
</head>
<body>

<h1>Lea 💖</h1>
<h2>Will you be my Valentine?</h2>

<div class="buttons">
<button id="yes" onclick="yesClicked()">YES 💕</button>
<button id="no" onmouseover="moveNo()">NO 💔</button>
</div>

<script>
function yesClicked() {
explodeHearts();

setTimeout(() => {
document.body.innerHTML = `
<h1>YAYYYYY!!! 💖💖💖</h1>
<h2>Lea, you just made me the happiest person 🥰</h2>
<h3>Happy Valentine’s Day 😘</h3>
`;
}, 800);
}

function moveNo() {
const noBtn = document.getElementById("no");
const container = document.querySelector(".buttons");

const maxX = container.offsetWidth - noBtn.offsetWidth;
const maxY = container.offsetHeight - noBtn.offsetHeight;

noBtn.style.left = Math.random() * maxX + "px";
noBtn.style.top = Math.random() * maxY + "px";
}

// Floating hearts
function createHeart() {
const heart = document.createElement("div");
heart.className = "heart";
heart.innerHTML = "💖";

heart.style.left = Math.random() * 100 + "vw";
heart.style.animationDuration = (4 + Math.random() * 3) + "s";
heart.style.fontSize = (16 + Math.random() * 20) + "px";

document.body.appendChild(heart);

setTimeout(() => heart.remove(), 7000);
}

setInterval(createHeart, 300);

// Heart explosion
function explodeHearts() {
for (let i = 0; i < 40; i++) {
const heart = document.createElement("div");
heart.className = "boom";
heart.innerHTML = "💖";

heart.style.left = "50vw";
heart.style.top = "50vh";

const x = (Math.random() - 0.5) * 600 + "px";
const y = (Math.random() - 0.5) * 600 + "px";

heart.style.setProperty("--x", x);
heart.style.setProperty("--y", y);

document.body.appendChild(heart);

setTimeout(() => heart.remove(), 1200);
}
}
</script>

</body>
</html>
