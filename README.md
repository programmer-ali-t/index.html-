<!--
╔══════════════════════════════════════════════╗
║      ALI HAZIM ULTRA — FINAL ULTIMATE       ║
║      NASA / MIT REAL ENGINEERING LAB        ║
╚══════════════════════════════════════════════╝
-->

<!--
⚠️ IMPORTANT:
حتى يشتغل المشروع كامل 100٪ لازم تحفظه باسم:
index.html

ويفضل تشغله عبر:
VS CODE + LIVE SERVER

حتى يشتغل الصوت و Three.js بأفضل أداء.
-->

<!DOCTYPE html>
<html lang="ar" dir="rtl">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ALI HAZIM ULTRA | Ultimate Physics Laboratory</title>

<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;900&display=swap" rel="stylesheet">

<script src="https://cdn.jsdelivr.net/npm/three@0.158.0/build/three.min.js"></script>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Tajawal',sans-serif;
}

body{
overflow:hidden;
background:#02070d;
color:white;
height:100vh;
}

/*══════════════════════
3D BACKGROUND
══════════════════════*/

#bg3d{
position:fixed;
inset:0;
z-index:0;
}

.overlay{
position:fixed;
inset:0;
background:
radial-gradient(circle at top,#16325f 0%,transparent 30%),
linear-gradient(180deg,rgba(0,0,0,.15),rgba(0,0,0,.8));
z-index:1;
pointer-events:none;
}

.grid{
position:fixed;
inset:0;
background:
linear-gradient(rgba(255,255,255,.03) 1px,transparent 1px),
linear-gradient(90deg,rgba(255,255,255,.03) 1px,transparent 1px);
background-size:40px 40px;
opacity:.18;
z-index:1;
pointer-events:none;
}

/*══════════════════════
MAIN UI
══════════════════════*/

.ui{
position:relative;
z-index:10;
padding:20px;
height:100vh;
display:flex;
flex-direction:column;
}

.topbar{
display:flex;
justify-content:space-between;
align-items:center;
padding:22px 28px;
border-radius:30px;

background:rgba(255,255,255,.05);
backdrop-filter:blur(20px);

border:1px solid rgba(255,255,255,.08);

box-shadow:
0 20px 80px rgba(0,0,0,.5),
inset 0 1px 1px rgba(255,255,255,.08);
}

.brand h1{
font-size:42px;
font-weight:900;

background:
linear-gradient(90deg,#ffffff,#34d6ff);

-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
}

.brand p{
margin-top:5px;
color:#90a8c8;
font-size:18px;
}

.badges{
display:flex;
gap:12px;
flex-wrap:wrap;
}

.badge{
padding:14px 22px;
border-radius:18px;

background:rgba(255,255,255,.05);

border:1px solid rgba(255,255,255,.08);

font-weight:700;
}

/*══════════════════════
LAYOUT
══════════════════════*/

.main{
display:grid;
grid-template-columns:1.6fr .8fr;
gap:22px;
margin-top:20px;
flex:1;
}

@media(max-width:1100px){

.main{
grid-template-columns:1fr;
overflow:auto;
}

}

/*══════════════════════
LAB
══════════════════════*/

.lab{
position:relative;

border-radius:34px;
overflow:hidden;

background:
linear-gradient(180deg,#091321,#08111f);

border:1px solid rgba(255,255,255,.08);

box-shadow:
0 30px 120px rgba(0,0,0,.7),
inset 0 0 100px rgba(52,214,255,.05);
}

#simCanvas{
width:100%;
height:100%;
}

/*══════════════════════
PANEL
══════════════════════*/

.panel{
background:rgba(255,255,255,.04);

backdrop-filter:blur(18px);

border-radius:34px;

border:1px solid rgba(255,255,255,.08);

padding:24px;

overflow:auto;
}

.title{
font-size:30px;
font-weight:900;
margin-bottom:22px;
}

.control{
margin-bottom:24px;
}

.control label{
display:block;
margin-bottom:12px;
font-size:18px;
font-weight:700;
}

input[type=range]{
width:100%;
accent-color:#34d6ff;
}

select{
width:100%;
padding:16px;
background:#091321;
border:none;
border-radius:16px;
color:white;
font-size:17px;
}

.buttons{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:12px;
margin-top:18px;
}

button{
padding:18px;
border:none;
border-radius:18px;

font-size:18px;
font-weight:800;

cursor:pointer;
transition:.3s;

color:white;
}

button:hover{
transform:translateY(-3px) scale(1.03);
}

.start{
background:linear-gradient(90deg,#00ff99,#00d47f);
}

.stop{
background:linear-gradient(90deg,#ff3d6e,#ff0055);
}

.reset{
background:linear-gradient(90deg,#34d6ff,#4876ff);
}

/*══════════════════════
STATS
══════════════════════*/

.stats{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:14px;
margin-top:22px;
}

.card{
padding:24px;

border-radius:24px;

background:rgba(255,255,255,.04);

border:1px solid rgba(255,255,255,.08);

text-align:center;
}

.card h3{
color:#8fa8c7;
margin-bottom:10px;
}

.card p{
font-size:42px;
font-weight:900;
}

/*══════════════════════
OSCILLOSCOPE
══════════════════════*/

.scope{
margin-top:24px;
background:black;
border-radius:26px;
overflow:hidden;
height:260px;

border:2px solid rgba(255,255,255,.08);

position:relative;
}

.scope::before{
content:'';
position:absolute;
inset:0;

background:
linear-gradient(rgba(255,255,255,.03) 1px,transparent 1px),
linear-gradient(90deg,rgba(255,255,255,.03) 1px,transparent 1px);

background-size:40px 40px;

pointer-events:none;
}

#oscilloscope{
width:100%;
height:100%;
}

/* scanline */

.scope::after{
content:'';
position:absolute;
left:0;
top:-100%;
width:100%;
height:100%;

background:
linear-gradient(
to bottom,
transparent,
rgba(52,214,255,.12),
transparent
);

animation:scan 4s linear infinite;
}

@keyframes scan{

0%{
top:-100%;
}

100%{
top:100%;
}

}

.footer{
margin-top:14px;
text-align:center;
color:#7890ae;
font-size:17px;
}

</style>

</head>

<body>

<canvas id="bg3d"></canvas>

<div class="overlay"></div>
<div class="grid"></div>

<div class="ui">

<!--══════════════════-->

<div class="topbar">

<div class="brand">

<h1>ALI HAZIM ULTRA</h1>

<p>
Ultimate Real Engineering RC Laboratory
</p>

</div>

<div class="badges">

<div class="badge">
👨‍🏫 إعداد الأستاذ سيف
</div>

<div class="badge">
🧠 إعداد الطالب ALI HAZIM
</div>

</div>

</div>

<!--══════════════════-->

<div class="main">

<!-- LAB -->

<div class="lab">
<canvas id="simCanvas"></canvas>
</div>

<!-- PANEL -->

<div class="panel">

<div class="title">
⚡ لوحة التحكم الفيزيائية
</div>

<div class="control">

<label>الجهد الكهربائي</label>

<select id="voltage">

<option>5</option>
<option>9</option>
<option>12</option>
<option>24</option>

</select>

</div>

<div class="control">

<label>المقاومة Ω</label>

<input
type="range"
min="1"
max="1000"
value="100"
id="resistance"
>

<h2 id="rText">100 Ω</h2>

</div>

<div class="control">

<label>السعة µF</label>

<input
type="range"
min="100"
max="5000"
value="2200"
id="capacitance"
>

<h2 id="cText">2200 µF</h2>

</div>

<div class="buttons">

<button class="start" onclick="startSim()">
تشغيل
</button>

<button class="stop" onclick="stopSim()">
إيقاف
</button>

<button class="reset" onclick="resetSim()">
إعادة
</button>

</div>

<!-- stats -->

<div class="stats">

<div class="card">
<h3>Voltage</h3>
<p id="voltageValue">0V</p>
</div>

<div class="card">
<h3>Current</h3>
<p id="currentValue">0A</p>
</div>

<div class="card">
<h3>Resistance</h3>
<p id="resistanceValue">100Ω</p>
</div>

<div class="card">
<h3>Capacitance</h3>
<p id="capacitanceValue">2200</p>
</div>

</div>

<!-- oscilloscope -->

<div class="scope">
<canvas id="oscilloscope"></canvas>
</div>

</div>

</div>

<div class="footer">

ALI HAZIM ULTRA — NASA / MIT ENGINEERING SIMULATION

</div>

</div>

<script>

/*══════════════════════════════
3D PARTICLE ENGINE
══════════════════════════════*/

const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera(
60,
window.innerWidth/window.innerHeight,
0.1,
1000
);

camera.position.z = 15;

const renderer = new THREE.WebGLRenderer({
canvas:document.getElementById('bg3d'),
alpha:true,
antialias:true
});

renderer.setSize(window.innerWidth,window.innerHeight);

const geometry = new THREE.BufferGeometry();

const vertices = [];

for(let i=0;i<5000;i++){

vertices.push(
(Math.random()-0.5)*120,
(Math.random()-0.5)*120,
(Math.random()-0.5)*120
);

}

geometry.setAttribute(
'position',
new THREE.Float32BufferAttribute(vertices,3)
);

const material = new THREE.PointsMaterial({
color:0x34d6ff,
size:0.08
});

const stars = new THREE.Points(
geometry,
material
);

scene.add(stars);

function animate3D(){

requestAnimationFrame(animate3D);

stars.rotation.y += 0.0007;
stars.rotation.x += 0.0003;

renderer.render(scene,camera);

}

animate3D();

/*══════════════════════════════
RC SIMULATION ENGINE
══════════════════════════════*/

const sim=document.getElementById('simCanvas');
const ctx=sim.getContext('2d');

function resize(){

sim.width=sim.parentElement.clientWidth;
sim.height=sim.parentElement.clientHeight;

}

resize();

window.onresize=resize;

let running=false;
let t=0;

/* controls */

const resistance=document.getElementById('resistance');
const capacitance=document.getElementById('capacitance');

resistance.oninput=()=>{

document.getElementById('rText').innerText=
resistance.value+' Ω';

document.getElementById('resistanceValue').innerText=
resistance.value+'Ω';

};

capacitance.oninput=()=>{

document.getElementById('cText').innerText=
capacitance.value+' µF';

document.getElementById('capacitanceValue').innerText=
capacitance.value;

};

/* sound engine */

const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

function clickSound(){

const osc = audioCtx.createOscillator();
const gain = audioCtx.createGain();

osc.type='square';
osc.frequency.value=160;

osc.connect(gain);
gain.connect(audioCtx.destination);

gain.gain.setValueAtTime(.05,audioCtx.currentTime);
gain.gain.exponentialRampToValueAtTime(.0001,audioCtx.currentTime+.15);

osc.start();
osc.stop(audioCtx.currentTime+.15);

}

/*══════════════════════════════
DRAW LAB
══════════════════════════════*/

function drawLab(v){

ctx.clearRect(0,0,sim.width,sim.height);

const bg=ctx.createLinearGradient(
0,0,0,sim.height
);

bg.addColorStop(0,'#091321');
bg.addColorStop(1,'#050b13');

ctx.fillStyle=bg;
ctx.fillRect(0,0,sim.width,sim.height);

/* copper wires */

ctx.strokeStyle='#34d6ff';
ctx.lineWidth=8;

ctx.shadowBlur=25;
ctx.shadowColor='#34d6ff';

ctx.beginPath();
ctx.moveTo(180,320);
ctx.lineTo(1050,320);
ctx.stroke();

ctx.shadowBlur=0;

/* realistic battery */

ctx.fillStyle='#101c2d';
ctx.fillRect(70,170,130,300);

ctx.fillStyle='#18ff9c';
ctx.fillRect(110,220,50,180);

ctx.fillStyle='#f1fbff';
ctx.fillRect(122,140,26,30);

/* battery reflections */

ctx.fillStyle='rgba(255,255,255,.12)';
ctx.fillRect(85,180,10,260);

/* capacitor */

const metal=ctx.createLinearGradient(
0,0,100,0
);

metal.addColorStop(0,'#ffffff');
metal.addColorStop(.5,'#8bdfff');
metal.addColorStop(1,'#e8ffff');

ctx.fillStyle=metal;

ctx.fillRect(550,120,24,420);
ctx.fillRect(650,120,24,420);

/* reflections */

ctx.fillStyle='rgba(255,255,255,.25)';
ctx.fillRect(556,130,4,400);
ctx.fillRect(656,130,4,400);

/* electric field */

ctx.strokeStyle='rgba(213,123,255,.8)';
ctx.lineWidth=2;

for(let i=0;i<12;i++){

ctx.beginPath();

ctx.moveTo(575+i*7,160);
ctx.lineTo(575+i*7,500);

ctx.stroke();

}

/* switch */

ctx.fillStyle=
running ? '#18ff9c' : '#ff9f1a';

ctx.beginPath();

ctx.roundRect(
930,260,200,100,50
);

ctx.fill();

ctx.fillStyle='white';

ctx.beginPath();

ctx.arc(
running ? 1080 : 980,
310,
36,
0,
Math.PI*2
);

ctx.fill();

/* electrons */

ctx.shadowBlur=30;
ctx.shadowColor='#34d6ff';

for(let i=0;i<20;i++){

ctx.beginPath();

ctx.arc(
220+i*55+
(
running
?
(Date.now()/8%55)
:
0
),
320,
6,
0,
Math.PI*2
);

ctx.fillStyle='#34d6ff';
ctx.fill();

}

ctx.shadowBlur=0;

/* analog meter */

ctx.beginPath();

ctx.arc(350,180,80,0,Math.PI*2);

ctx.fillStyle='#101a2a';
ctx.fill();

ctx.strokeStyle='#34d6ff';
ctx.lineWidth=4;
ctx.stroke();

/* needle */

ctx.save();

ctx.translate(350,180);

const angle=
(-Math.PI/1.5)+
(v/24)*Math.PI;

ctx.rotate(angle);

ctx.strokeStyle='#ff4d6d';
ctx.lineWidth=5;

ctx.beginPath();
ctx.moveTo(0,0);
ctx.lineTo(55,0);
ctx.stroke();

ctx.restore();

/* digital display */

ctx.fillStyle='#ffffff';

ctx.font='bold 38px Tajawal';

ctx.fillText(
v.toFixed(2)+'V',
300,
330
);

}

/*══════════════════════════════
OSCILLOSCOPE
══════════════════════════════*/

const osc=document.getElementById('oscilloscope');
const octx=osc.getContext('2d');

osc.width=900;
osc.height=260;

function drawOsc(v){

octx.fillStyle='black';
octx.fillRect(0,0,osc.width,osc.height);

/* grid */

octx.strokeStyle='rgba(255,255,255,.08)';

for(let i=0;i<osc.width;i+=40){

octx.beginPath();
octx.moveTo(i,0);
octx.lineTo(i,osc.height);
octx.stroke();

}

for(let i=0;i<osc.height;i+=40){

octx.beginPath();
octx.moveTo(0,i);
octx.lineTo(osc.width,i);
octx.stroke();

}

/* waveform */

octx.beginPath();

octx.strokeStyle='#34d6ff';
octx.lineWidth=4;

for(let x=0;x<osc.width;x++){

let y=
osc.height-
(v*Math.exp(-x/170))*10;

if(x===0)
octx.moveTo(x,y);
else
octx.lineTo(x,y);

}

octx.shadowBlur=25;
octx.shadowColor='#34d6ff';

octx.stroke();

octx.shadowBlur=0;

}

/*══════════════════════════════
PHYSICS
══════════════════════════════*/

function simulate(){

if(!running)return;

const V=parseFloat(
document.getElementById('voltage').value
);

const R=parseFloat(resistance.value);

const C=parseFloat(
capacitance.value
)/1000000;

/* RC equation */

const voltage=
V*(1-Math.exp(-t/(R*C)));

const current=
(V/R)*Math.exp(-t/(R*C));

document.getElementById('voltageValue').innerText=
voltage.toFixed(2)+'V';

document.getElementById('currentValue').innerText=
current.toFixed(2)+'A';

drawLab(voltage);
drawOsc(voltage);

t+=0.05;

requestAnimationFrame(simulate);

}

/* controls */

function startSim(){

clickSound();

running=true;

simulate();

}

function stopSim(){

clickSound();

running=false;

}

function resetSim(){

clickSound();

running=false;

t=0;

document.getElementById('voltageValue').innerText='0V';

document.getElementById('currentValue').innerText='0A';

drawLab(0);
drawOsc(0);

}

/* init */

drawLab(0);
drawOsc(0);

</script>

</body>
</html>
