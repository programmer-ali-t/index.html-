<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ALI HAZIM Ultra | Advanced RC Physics Laboratory</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;800&family=Cairo:wght@300;400;600;700;800&display=swap" rel="stylesheet">

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>

/* ========================= */
/* RESET */
/* ========================= */

*{
margin:0;
padding:0;
box-sizing:border-box;
}

:root{

--bg:#020617;
--card:rgba(255,255,255,.04);
--border:rgba(255,255,255,.08);

--cyan:#00e5ff;
--blue:#3b82f6;
--white:#ffffff;
--text:#cbd5e1;

}

body{

font-family:'Cairo',sans-serif;
background:
radial-gradient(circle at top,#0f172a 0%,#020617 50%);
color:white;
overflow-x:hidden;
min-height:100vh;

}

/* ========================= */
/* BACKGROUND */
/* ========================= */

.bg-grid{

position:fixed;
inset:0;
background-image:
linear-gradient(rgba(255,255,255,.03) 1px, transparent 1px),
linear-gradient(90deg, rgba(255,255,255,.03) 1px, transparent 1px);

background-size:50px 50px;
z-index:-5;

}

.glow{

position:fixed;
width:800px;
height:800px;
border-radius:50%;
filter:blur(180px);
opacity:.12;
z-index:-4;

}

.glow1{
background:var(--cyan);
top:-300px;
left:-250px;
animation:move1 10s infinite ease-in-out;
}

.glow2{
background:var(--blue);
bottom:-300px;
right:-250px;
animation:move2 12s infinite ease-in-out;
}

@keyframes move1{

0%,100%{
transform:translateY(0);
}

50%{
transform:translateY(50px);
}

}

@keyframes move2{

0%,100%{
transform:translateY(0);
}

50%{
transform:translateY(-50px);
}

}

/* ========================= */
/* LOADING */
/* ========================= */

.loader{

position:fixed;
inset:0;
background:#020617;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
z-index:99999;
transition:1s;

}

.loader h1{

font-family:'Orbitron',sans-serif;
font-size:48px;
font-weight:800;

background:linear-gradient(90deg,var(--cyan),var(--blue),white);

-webkit-background-clip:text;
-webkit-text-fill-color:transparent;

margin-bottom:15px;

}

.loader p{

color:#94a3b8;
margin-bottom:30px;

}

.loading-bar{

width:340px;
height:10px;
background:#111827;
border-radius:50px;
overflow:hidden;

}

.loading-fill{

height:100%;
width:0%;

background:
linear-gradient(90deg,var(--cyan),var(--blue));

animation:load 3s linear forwards;

}

@keyframes load{

100%{
width:100%;
}

}

/* ========================= */
/* APP */
/* ========================= */

.app{

padding:25px;
max-width:1700px;
margin:auto;

}

/* ========================= */
/* HEADER */
/* ========================= */

.topbar{

display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:25px;
gap:20px;
flex-wrap:wrap;

}

.brand h1{

font-family:'Orbitron',sans-serif;
font-size:46px;
font-weight:800;

background:
linear-gradient(90deg,var(--cyan),var(--blue),white);

-webkit-background-clip:text;
-webkit-text-fill-color:transparent;

}

.brand p{

color:#94a3b8;
margin-top:5px;

}

.status{

display:flex;
gap:15px;
flex-wrap:wrap;

}

.status-card{

padding:14px 24px;

background:rgba(255,255,255,.05);

border:1px solid rgba(255,255,255,.08);

backdrop-filter:blur(20px);

border-radius:20px;

box-shadow:
0 0 30px rgba(0,0,0,.25);

font-weight:700;

}

/* ========================= */
/* MAIN GRID */
/* ========================= */

.grid{

display:grid;
grid-template-columns:1.2fr .8fr;
gap:25px;

}

/* ========================= */
/* CARD */
/* ========================= */

.card{

background:var(--card);

border:1px solid var(--border);

backdrop-filter:blur(25px);

border-radius:35px;

padding:25px;

position:relative;

overflow:hidden;

box-shadow:
0 10px 40px rgba(0,0,0,.35),
inset 0 0 30px rgba(255,255,255,.02);

}

.card::before{

content:'';

position:absolute;
inset:0;

background:
linear-gradient(
130deg,
rgba(255,255,255,.04),
transparent
);

pointer-events:none;

}

.card-title{

font-size:28px;
font-weight:800;
margin-bottom:25px;
color:#dbeafe;

}

/* ========================= */
/* LAB */
/* ========================= */

.lab{

height:650px;
position:relative;
overflow:hidden;
display:flex;
justify-content:center;
align-items:center;

}

/* wires */

.wire-horizontal{

position:absolute;

width:78%;
height:8px;

background:var(--cyan);

border-radius:50px;

box-shadow:
0 0 25px var(--cyan),
0 0 60px rgba(0,229,255,.5);

}

/* capacitor */

.capacitor{

position:absolute;

display:flex;
gap:35px;

transform:
perspective(1000px)
rotateY(-10deg);

z-index:3;

}

.plate{

width:22px;
height:220px;

border-radius:14px;

background:
linear-gradient(
180deg,
white,
var(--cyan)
);

box-shadow:
0 0 40px var(--cyan),
0 0 90px rgba(0,229,255,.5);

animation:pulse 1.5s infinite;

}

@keyframes pulse{

0%,100%{

transform:scaleY(1);
opacity:.8;

}

50%{

transform:scaleY(1.07);
opacity:1;

}

}

/* battery */

.battery{

position:absolute;
left:100px;

width:90px;
height:180px;

border-radius:18px;

background:
linear-gradient(
180deg,
#1e293b,
#0f172a
);

border:2px solid rgba(255,255,255,.15);

box-shadow:
0 0 40px rgba(0,229,255,.25);

display:flex;
justify-content:center;
align-items:center;
flex-direction:column;

}

.battery::before{

content:'+';

position:absolute;
top:10px;
color:#00ff95;
font-size:24px;

}

.battery::after{

content:'−';

position:absolute;
bottom:10px;
color:#ff1744;
font-size:24px;

}

.battery-level{

width:50px;
height:120px;

border-radius:12px;

background:
linear-gradient(
180deg,
#00ff95,
#00e676
);

box-shadow:
0 0 25px #00ff95;

}

/* resistor */

.resistor{

position:absolute;
right:100px;

width:160px;
height:45px;

border-radius:18px;

background:
linear-gradient(
90deg,
#d97706,
#f59e0b
);

box-shadow:
0 0 25px rgba(245,158,11,.45);

}

/* switch */

.switch{

position:absolute;

top:130px;
right:260px;

width:120px;
height:10px;

background:#334155;

border-radius:20px;

transform-origin:left center;

transition:.4s;

}

.switch.on{

transform:rotate(0deg);

background:#00ff95;

box-shadow:
0 0 25px #00ff95;

}

.switch.off{

transform:rotate(-35deg);

}

/* particles */

.particle{

position:absolute;

width:16px;
height:16px;

border-radius:50%;

background:var(--cyan);

box-shadow:
0 0 20px var(--cyan);

opacity:0;

}

/* equation */

.equation{

margin-top:25px;

padding:22px;

background:rgba(255,255,255,.04);

border-radius:22px;

border:1px solid rgba(255,255,255,.08);

font-size:24px;

font-family:'Orbitron',sans-serif;

text-align:center;

color:#7dd3fc;

overflow:auto;

}

/* ========================= */
/* CONTROL */
/* ========================= */

.panel{

display:flex;
flex-direction:column;
gap:18px;

}

.box{

background:rgba(255,255,255,.04);

padding:20px;

border-radius:24px;

border:1px solid rgba(255,255,255,.08);

}

.box label{

display:block;

margin-bottom:12px;

font-weight:700;

color:#7dd3fc;

}

/* select */

select{

width:100%;
padding:15px;

background:#0f172a;

border:none;

border-radius:18px;

color:white;

font-size:16px;

outline:none;

}

/* range */

input[type=range]{

width:100%;

}

/* values */

.range-value{

margin-top:10px;
font-weight:700;
color:#cbd5e1;

}

/* buttons */

.buttons{

display:grid;
grid-template-columns:repeat(3,1fr);
gap:12px;

}

button{

padding:17px;

border:none;

border-radius:20px;

font-size:16px;

font-weight:800;

cursor:pointer;

transition:.3s;

color:white;

}

button:hover{

transform:
translateY(-3px)
scale(1.03);

}

.start{

background:
linear-gradient(
90deg,
#00c853,
#00ff95
);

}

.stop{

background:
linear-gradient(
90deg,
#ff1744,
#ff5252
);

}

.reset{

background:
linear-gradient(
90deg,
#2979ff,
#00b0ff
);

}

/* progress */

.progress{

height:24px;

background:#111827;

border-radius:30px;

overflow:hidden;

margin-top:15px;

}

.fill{

height:100%;
width:0%;

background:
linear-gradient(
90deg,
var(--cyan),
var(--blue)
);

box-shadow:
0 0 25px var(--cyan);

transition:.15s;

}

/* meters */

.meters{

display:grid;
grid-template-columns:repeat(2,1fr);
gap:15px;
margin-top:15px;

}

.meter{

background:rgba(255,255,255,.04);

padding:20px;

border-radius:22px;

border:1px solid rgba(255,255,255,.08);

text-align:center;

}

.meter h3{

font-size:14px;

margin-bottom:10px;

color:#7dd3fc;

}

.meter span{

font-size:34px;

font-family:'Orbitron',sans-serif;
font-weight:800;

}

/* chart */

canvas{

background:#020617;

border-radius:22px;

padding:15px;

border:1px solid rgba(255,255,255,.08);

}

/* footer */

.footer{

margin-top:30px;

text-align:center;

color:#94a3b8;

padding-bottom:20px;

}

/* ========================= */
/* RESPONSIVE */
/* ========================= */

@media(max-width:1100px){

.grid{

grid-template-columns:1fr;

}

.lab{

height:500px;

}

.brand h1{

font-size:32px;

}

}

</style>
</head>

<body>

<!-- BACKGROUND -->

<div class="bg-grid"></div>

<div class="glow glow1"></div>
<div class="glow glow2"></div>

<!-- LOADER -->

<div class="loader" id="loader">

<h1>ALI HAZIM Ultra</h1>

<p>Advanced RC Physics Laboratory</p>

<div class="loading-bar">
<div class="loading-fill"></div>
</div>

</div>

<!-- APP -->

<div class="app">

<!-- HEADER -->

<div class="topbar">

<div class="brand">

<h1>ALI HAZIM Ultra</h1>

<p>Advanced RC Physics Laboratory</p>

</div>

<div class="status">

<div class="status-card">
🟢 SYSTEM ONLINE
</div>

<div class="status-card">
👨‍🏫 الأستاذ سيف
</div>

<div class="status-card">
👨‍💻 ALI HAZIM
</div>

</div>

</div>

<!-- GRID -->

<div class="grid">

<!-- LAB -->

<div class="card">

<div class="card-title">
⚡ Interactive RC Laboratory
</div>

<div class="lab">

<div class="wire-horizontal"></div>

<div class="battery">

<div class="battery-level"></div>

</div>

<div class="resistor"></div>

<div class="switch off" id="switch"></div>

<div class="capacitor">

<div class="plate"></div>
<div class="plate"></div>

</div>

<div class="particle" id="p1"></div>
<div class="particle" id="p2"></div>
<div class="particle" id="p3"></div>
<div class="particle" id="p4"></div>

</div>

<div class="equation">
V(t)=V₀(1-e^(-t/RC))
</div>

</div>

<!-- CONTROL -->

<div class="card">

<div class="card-title">
🎛 Physics Control System
</div>

<div class="panel">

<div class="box">

<label>Voltage</label>

<select id="voltage">

<option value="5">5V</option>
<option value="12">12V</option>
<option value="24">24V</option>
<option value="48">48V</option>
<option value="110">110V</option>
<option value="220">220V</option>

</select>

</div>

<div class="box">

<label>Resistance (Ω)</label>

<input type="range"
id="resistance"
min="1"
max="100"
value="50">

<div class="range-value" id="resText">
50 Ω
</div>

</div>

<div class="box">

<label>Capacitance (µF)</label>

<input type="range"
id="capacitance"
min="100"
max="5000"
value="2200">

<div class="range-value" id="capText">
2200 µF
</div>

</div>

<div class="buttons">

<button class="start" onclick="startSystem()">
تشغيل
</button>

<button class="stop" onclick="stopSystem()">
إيقاف
</button>

<button class="reset" onclick="resetSystem()">
إعادة
</button>

</div>

<div class="box">

<label>Charge Level</label>

<div class="progress">

<div class="fill" id="fill"></div>

</div>

</div>

<div class="meters">

<div class="meter">

<h3>Voltage</h3>

<span id="voltValue">
12V
</span>

</div>

<div class="meter">

<h3>Current</h3>

<span id="currentValue">
0A
</span>

</div>

<div class="meter">

<h3>Resistance</h3>

<span id="ohmValue">
50Ω
</span>

</div>

<div class="meter">

<h3>Capacitance</h3>

<span id="capValue">
2200
</span>

</div>

</div>

<div class="box">

<label>Live Oscilloscope</label>

<canvas id="scope" height="240"></canvas>

</div>

</div>

</div>

</div>

<div class="footer">
MIT / NASA Inspired Scientific Interface © 2026
</div>

</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script>

/* ========================= */
/* LOADER */
/* ========================= */

setTimeout(()=>{

document.getElementById("loader").style.opacity="0";

setTimeout(()=>{

document.getElementById("loader").style.display="none";

},1000);

},3200);

/* ========================= */
/* ELEMENTS */
/* ========================= */

const voltage =
document.getElementById("voltage");

const resistance =
document.getElementById("resistance");

const capacitance =
document.getElementById("capacitance");

const voltValue =
document.getElementById("voltValue");

const currentValue =
document.getElementById("currentValue");

const ohmValue =
document.getElementById("ohmValue");

const capValue =
document.getElementById("capValue");

const resText =
document.getElementById("resText");

const capText =
document.getElementById("capText");

const fill =
document.getElementById("fill");

const sw =
document.getElementById("switch");

const particles = [

document.getElementById("p1"),
document.getElementById("p2"),
document.getElementById("p3"),
document.getElementById("p4")

];

/* ========================= */
/* VALUES */
/* ========================= */

function updateValues(){

voltValue.innerText =
voltage.value + "V";

ohmValue.innerText =
resistance.value + "Ω";

capValue.innerText =
capacitance.value;

resText.innerText =
resistance.value + " Ω";

capText.innerText =
capacitance.value + " µF";

let current = (
voltage.value / resistance.value
).toFixed(2);

currentValue.innerText =
current + "A";

}

voltage.onchange = updateValues;
resistance.oninput = updateValues;
capacitance.oninput = updateValues;

updateValues();

/* ========================= */
/* SYSTEM */
/* ========================= */

let running = false;
let progress = 0;
let interval;

function startSystem(){

if(running) return;

running = true;

sw.classList.remove("off");
sw.classList.add("on");

interval = setInterval(()=>{

progress += 0.5;

if(progress > 100){
progress = 100;
}

fill.style.width =
progress + "%";

animateParticles();

},50);

}

function stopSystem(){

running = false;

clearInterval(interval);

sw.classList.remove("on");
sw.classList.add("off");

particles.forEach(p=>{
p.style.opacity = 0;
});

}

function resetSystem(){

progress = 0;

fill.style.width = "0%";

stopSystem();

}

/* ========================= */
/* PARTICLES */
/* ========================= */

function animateParticles(){

particles.forEach((p,i)=>{

p.style.opacity = 1;

p.animate([

{
transform:"translateX(-500px)"
},

{
transform:"translateX(500px)"
}

],{

duration:2200,
iterations:1,
delay:i*180

});

});

}

/* ========================= */
/* CHART */
/* ========================= */

const ctx =
document.getElementById('scope');

const chart = new Chart(ctx,{

type:'line',

data:{

labels:[],

datasets:[

{

label:'Voltage',

data:[],

borderColor:'#00e5ff',

borderWidth:3,

tension:.4

},

{

label:'Current',

data:[],

borderColor:'#3b82f6',

borderWidth:3,

tension:.4

}

]

},

options:{

responsive:true,

animation:false,

plugins:{

legend:{

labels:{
color:'#fff'
}

}

},

scales:{

x:{
ticks:{color:'#94a3b8'}
},

y:{
ticks:{color:'#94a3b8'}
}

}

}

});

/* ========================= */
/* LIVE GRAPH */
/* ========================= */

let t = 0;

setInterval(()=>{

if(!running) return;

t++;

let V = (

voltage.value *

(1 - Math.exp(-t/30))

).toFixed(2);

let I = (

(voltage.value / resistance.value)

* Math.exp(-t/30)

).toFixed(2);

if(chart.data.labels.length > 40){

chart.data.labels.shift();

chart.data.datasets[0].data.shift();

chart.data.datasets[1].data.shift();

}

chart.data.labels.push(t);

chart.data.datasets[0].data.push(V);

chart.data.datasets[1].data.push(I);

chart.update();

},180);

</script>

</body>
</html>
