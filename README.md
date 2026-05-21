<!--
ALI HAZIM ULTRA
REALISTIC SCIENTIFIC RC LAB
ULTRA PRO MAX EDITION
-->

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ALI HAZIM ULTRA | Realistic RC Physics Laboratory</title>

<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;900&display=swap" rel="stylesheet">

<style>

:root{
--bg:#08111f;
--panel:#0f1d31;
--cyan:#34d6ff;
--green:#18ff9c;
--orange:#ff9f1a;
--white:#f5fbff;
--muted:#7e93b2;
}

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Tajawal',sans-serif;
}

body{
background:
radial-gradient(circle at top left,#10233d 0%,transparent 30%),
radial-gradient(circle at bottom right,#07111d 0%,transparent 40%),
linear-gradient(180deg,#030913,#08111f);
color:white;
overflow-x:hidden;
min-height:100vh;
}

body::before{
content:'';
position:fixed;
inset:0;
background:
linear-gradient(rgba(255,255,255,.03) 1px,transparent 1px),
linear-gradient(90deg,rgba(255,255,255,.03) 1px,transparent 1px);
background-size:45px 45px;
pointer-events:none;
opacity:.18;
}

.container{
width:min(1600px,95%);
margin:auto;
padding:25px 0;
}

.topbar{
display:flex;
justify-content:space-between;
align-items:center;
padding:22px 28px;
background:rgba(255,255,255,.05);
backdrop-filter:blur(14px);
border:1px solid rgba(255,255,255,.08);
border-radius:26px;
margin-bottom:25px;
box-shadow:0 10px 40px rgba(0,0,0,.35);
}

.brand h1{
font-size:38px;
font-weight:900;
background:linear-gradient(90deg,#fff,#34d6ff);
-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
}

.brand p{
color:var(--muted);
margin-top:5px;
}

.tags{
display:flex;
gap:12px;
flex-wrap:wrap;
}

.tag{
padding:12px 20px;
border-radius:16px;
background:rgba(255,255,255,.04);
border:1px solid rgba(255,255,255,.08);
font-weight:700;
}

.layout{
display:grid;
grid-template-columns:1.5fr .8fr;
gap:24px;
}

@media(max-width:1100px){
.layout{
grid-template-columns:1fr;
}
}

.panel{
background:rgba(255,255,255,.04);
backdrop-filter:blur(16px);
border:1px solid rgba(255,255,255,.07);
border-radius:30px;
padding:25px;
position:relative;
overflow:hidden;
box-shadow:
0 10px 40px rgba(0,0,0,.4),
inset 0 1px 1px rgba(255,255,255,.05);
}

.title{
font-size:28px;
font-weight:900;
margin-bottom:20px;
}

.lab{
position:relative;
height:650px;
border-radius:28px;
background:
linear-gradient(135deg,#0c1728,#09111d);
overflow:hidden;
}

svg{
width:100%;
height:100%;
}

.glow{
filter:drop-shadow(0 0 10px #34d6ff)
drop-shadow(0 0 25px #34d6ff);
}

.electron{
animation:flow 2s linear infinite;
}

@keyframes flow{
0%{
transform:translateX(0);
opacity:0;
}
50%{
opacity:1;
}
100%{
transform:translateX(700px);
opacity:0;
}
}

.controls{
display:grid;
gap:20px;
}

.control{
padding:20px;
background:rgba(255,255,255,.03);
border-radius:22px;
border:1px solid rgba(255,255,255,.06);
}

.control label{
display:block;
margin-bottom:14px;
font-size:18px;
font-weight:700;
}

input[type=range]{
width:100%;
accent-color:#34d6ff;
}

select{
width:100%;
padding:15px;
background:#0c1728;
border:none;
border-radius:16px;
color:white;
font-size:17px;
}

.buttons{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:15px;
}

button{
border:none;
padding:18px;
border-radius:18px;
font-size:18px;
font-weight:800;
cursor:pointer;
transition:.3s;
color:white;
}

.start{
background:linear-gradient(90deg,#00ff99,#00d47f);
}

.stop{
background:linear-gradient(90deg,#ff4d6d,#ff234f);
}

.reset{
background:linear-gradient(90deg,#34d6ff,#4d7dff);
}

button:hover{
transform:translateY(-3px) scale(1.03);
}

.stats{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:15px;
}

.stat{
padding:28px;
border-radius:24px;
background:rgba(255,255,255,.03);
border:1px solid rgba(255,255,255,.06);
text-align:center;
}

.stat h3{
color:var(--muted);
margin-bottom:10px;
font-size:17px;
}

.stat p{
font-size:42px;
font-weight:900;
}

.scope{
margin-top:20px;
background:black;
border-radius:24px;
padding:15px;
border:2px solid rgba(255,255,255,.08);
height:260px;
position:relative;
overflow:hidden;
}

canvas{
width:100%;
height:100%;
}

.footer{
margin-top:25px;
text-align:center;
color:var(--muted);
font-size:18px;
}

</style>

</head>

<body>

<div class="container">

<div class="topbar">

<div class="brand">
<h1>ALI HAZIM ULTRA</h1>
<p>Advanced Realistic RC Physics Laboratory</p>
</div>

<div class="tags">
<div class="tag">👨‍🏫 إعداد الأستاذ سيف</div>
<div class="tag">🧠 إعداد الطالب ALI HAZIM</div>
</div>

</div>

<div class="layout">

<div class="panel">

<div class="title">⚡ محاكاة فيزيائية واقعية</div>

<div class="lab">

<svg viewBox="0 0 1200 700">

<defs>

<linearGradient id="wireGlow" x1="0" x2="1">
<stop offset="0%" stop-color="#34d6ff"/>
<stop offset="100%" stop-color="#4d7dff"/>
</linearGradient>

<linearGradient id="metal" x1="0" x2="1">
<stop offset="0%" stop-color="#f2f7ff"/>
<stop offset="100%" stop-color="#8bdfff"/>
</linearGradient>

</defs>

<!-- wires -->

<line x1="180" y1="350" x2="980" y2="350"
stroke="url(#wireGlow)"
stroke-width="8"
class="glow"/>

<!-- battery -->

<rect x="70" y="240" width="90" height="210"
rx="24"
fill="#18283f"
stroke="#2d4566"
stroke-width="4"/>

<rect x="95" y="265" width="40" height="160"
rx="14"
fill="#18ff9c"
filter="url(#glow)"/>

<rect x="103" y="220" width="24" height="20"
rx="6"
fill="#dbe9ff"/>

<!-- capacitor -->

<rect x="520" y="190" width="18" height="300"
rx="12"
fill="url(#metal)"
class="glow"/>

<rect x="585" y="190" width="18" height="300"
rx="12"
fill="url(#metal)"
class="glow"/>

<!-- electric field -->

<g stroke="#d57bff" stroke-width="3">

<line x1="550" y1="220" x2="550" y2="450"/>
<line x1="570" y1="220" x2="570" y2="450"/>
<line x1="590" y1="220" x2="590" y2="450"/>

</g>

<!-- switch -->

<rect id="switchBody"
x="900"
y="310"
width="180"
height="80"
rx="40"
fill="#ff9f1a"/>

<circle id="switchKnob"
cx="955"
cy="350"
r="32"
fill="white"/>

<!-- electrons -->

<circle class="electron" cx="220" cy="350" r="7" fill="#34d6ff"/>
<circle class="electron" cx="280" cy="350" r="7" fill="#34d6ff"/>
<circle class="electron" cx="340" cy="350" r="7" fill="#34d6ff"/>

<!-- voltmeter -->

<rect x="350" y="180" width="120" height="120"
rx="20"
fill="#111c2d"
stroke="#2f4666"
stroke-width="4"/>

<text x="410" y="225"
fill="#fff"
font-size="24"
text-anchor="middle">
V
</text>

<text id="voltmeter"
x="410"
y="270"
fill="#18ff9c"
font-size="34"
font-weight="bold"
text-anchor="middle">
0V
</text>

</svg>

</div>

</div>

<div class="panel">

<div class="title">🎛️ لوحة التحكم الفيزيائية</div>

<div class="controls">

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
<input type="range" min="1" max="1000" value="100" id="resistance">
<h2 id="rValue">100 Ω</h2>
</div>

<div class="control">
<label>السعة µF</label>
<input type="range" min="100" max="5000" value="2200" id="capacitance">
<h2 id="cValue">2200 µF</h2>
</div>

<div class="buttons">
<button class="start" onclick="startSim()">تشغيل</button>
<button class="stop" onclick="stopSim()">إيقاف</button>
<button class="reset" onclick="resetSim()">إعادة</button>
</div>

<div class="stats">

<div class="stat">
<h3>الجهد</h3>
<p id="vDisplay">0V</p>
</div>

<div class="stat">
<h3>التيار</h3>
<p id="iDisplay">0A</p>
</div>

<div class="stat">
<h3>المقاومة</h3>
<p id="rDisplay">100Ω</p>
</div>

<div class="stat">
<h3>السعة</h3>
<p id="cDisplay">2200</p>
</div>

</div>

<div class="scope">
<canvas id="scope"></canvas>
</div>

</div>

</div>

</div>

<div class="footer">
ALI HAZIM ULTRA — Realistic Scientific RC Laboratory
</div>

</div>

<script>

const resistance=document.getElementById('resistance');
const capacitance=document.getElementById('capacitance');

resistance.oninput=()=>{
document.getElementById('rValue').innerText=resistance.value+' Ω';
document.getElementById('rDisplay').innerText=resistance.value+'Ω';
};

capacitance.oninput=()=>{
document.getElementById('cValue').innerText=capacitance.value+' µF';
document.getElementById('cDisplay').innerText=capacitance.value;
};

const canvas=document.getElementById('scope');
const ctx=canvas.getContext('2d');

canvas.width=900;
canvas.height=240;

let running=false;
let t=0;

function drawScope(v){

ctx.fillStyle='black';
ctx.fillRect(0,0,canvas.width,canvas.height);

ctx.strokeStyle='rgba(255,255,255,.08)';

for(let i=0;i<canvas.width;i+=40){
ctx.beginPath();
ctx.moveTo(i,0);
ctx.lineTo(i,canvas.height);
ctx.stroke();
}

for(let i=0;i<canvas.height;i+=40){
ctx.beginPath();
ctx.moveTo(0,i);
ctx.lineTo(canvas.width,i);
ctx.stroke();
}

ctx.beginPath();

ctx.strokeStyle='#34d6ff';
ctx.lineWidth=4;

for(let x=0;x<canvas.width;x++){

let y=canvas.height-(v*Math.exp(-x/220))*8;

if(x===0) ctx.moveTo(x,y);
else ctx.lineTo(x,y);

}

ctx.stroke();

}

function startSim(){

running=true;

document.getElementById('switchBody').style.fill='#18ff9c';
document.getElementById('switchKnob').setAttribute('cx','1020');

simulate();

}

function stopSim(){

running=false;

document.getElementById('switchBody').style.fill='#ff9f1a';
document.getElementById('switchKnob').setAttribute('cx','955');

}

function resetSim(){

running=false;

t=0;

drawScope(0);

document.getElementById('vDisplay').innerText='0V';
document.getElementById('iDisplay').innerText='0A';
document.getElementById('voltmeter').textContent='0V';

document.getElementById('switchBody').style.fill='#ff9f1a';
document.getElementById('switchKnob').setAttribute('cx','955');

}

function simulate(){

if(!running)return;

const V=parseFloat(document.getElementById('voltage').value);
const R=parseFloat(resistance.value);
const C=parseFloat(capacitance.value)/1000000;

const voltage=V*(1-Math.exp(-t/(R*C)));
const current=(V/R)*Math.exp(-t/(R*C));

document.getElementById('vDisplay').innerText=voltage.toFixed(2)+'V';
document.getElementById('iDisplay').innerText=current.toFixed(2)+'A';

document.getElementById('voltmeter').textContent=
voltage.toFixed(1)+'V';

drawScope(voltage);

t+=0.05;

requestAnimationFrame(simulate);

}

drawScope(0);

</script>

</body>
</html>
