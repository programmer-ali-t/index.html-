<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ALI HAZIM Ultra | Advanced RC Physics Laboratory</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;800&family=Cairo:wght@300;400;600;700;800&display=swap" rel="stylesheet">

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
}

body{
font-family:'Cairo',sans-serif;
background:
radial-gradient(circle at top,#1e3a8a 0%,#0f172a 45%,#020617 100%);
overflow-x:hidden;
color:white;
min-height:100vh;
}

/* Animated Background */

body::before{
content:'';
position:fixed;
width:900px;
height:900px;
background:#00e5ff;
filter:blur(220px);
opacity:.12;
top:-300px;
left:-200px;
animation:float 10s ease-in-out infinite;
z-index:-1;
}

body::after{
content:'';
position:fixed;
width:700px;
height:700px;
background:#3b82f6;
filter:blur(220px);
opacity:.12;
bottom:-250px;
right:-150px;
animation:float2 12s ease-in-out infinite;
z-index:-1;
}

@keyframes float{
0%,100%{transform:translateY(0)}
50%{transform:translateY(40px)}
}

@keyframes float2{
0%,100%{transform:translateY(0)}
50%{transform:translateY(-40px)}
}

/* Loading */

.loader{
position:fixed;
inset:0;
background:#020617;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
z-index:9999;
transition:1s;
}

.loader h1{
font-family:'Orbitron',sans-serif;
font-size:42px;
background:linear-gradient(90deg,#00e5ff,#60a5fa,#fff);
-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
margin-bottom:15px;
}

.loader p{
color:#94a3b8;
font-size:18px;
margin-bottom:30px;
}

.loading-bar{
width:320px;
height:10px;
background:#111827;
border-radius:30px;
overflow:hidden;
}

.loading-fill{
height:100%;
width:0%;
background:linear-gradient(90deg,#00e5ff,#3b82f6);
animation:loading 3s linear forwards;
}

@keyframes loading{
100%{width:100%;}
}

/* Main */

.container{
padding:25px;
max-width:1600px;
margin:auto;
}

.header{
display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:30px;
flex-wrap:wrap;
gap:20px;
}

.logo{
font-family:'Orbitron',sans-serif;
font-size:42px;
font-weight:800;
background:linear-gradient(90deg,#00e5ff,#60a5fa,#ffffff);
-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
}

.subtitle{
color:#94a3b8;
margin-top:5px;
}

.authors{
display:flex;
gap:15px;
flex-wrap:wrap;
}

.badge{
padding:14px 24px;
border-radius:20px;
background:rgba(255,255,255,.05);
border:1px solid rgba(255,255,255,.08);
backdrop-filter:blur(20px);
box-shadow:0 0 25px rgba(0,0,0,.25);
font-weight:700;
}

/* Layout */

.grid{
display:grid;
grid-template-columns:1.2fr .8fr;
gap:25px;
}

.card{
background:rgba(255,255,255,.04);
border:1px solid rgba(255,255,255,.08);
backdrop-filter:blur(25px);
border-radius:35px;
padding:25px;
position:relative;
overflow:hidden;
box-shadow:
0 10px 40px rgba(0,0,0,.35),
inset 0 0 25px rgba(255,255,255,.02);
}

.card::before{
content:'';
position:absolute;
inset:0;
background:linear-gradient(140deg,rgba(255,255,255,.04),transparent);
pointer-events:none;
}

.title{
font-size:26px;
font-weight:800;
margin-bottom:25px;
color:#dbeafe;
}

/* Simulator */

.simulator{
height:550px;
position:relative;
display:flex;
justify-content:center;
align-items:center;
overflow:hidden;
}

.wire{
position:absolute;
width:80%;
height:8px;
background:#00d9ff;
border-radius:30px;
box-shadow:0 0 35px #00d9ff;
}

.capacitor{
display:flex;
gap:28px;
position:absolute;
z-index:2;
transform:perspective(1000px) rotateY(-12deg);
}

.plate{
width:20px;
height:200px;
border-radius:12px;
background:linear-gradient(#ffffff,#00d9ff);
box-shadow:
0 0 35px #00d9ff,
0 0 70px rgba(0,229,255,.5);
animation:pulse 1.5s infinite;
}

@keyframes pulse{
0%,100%{
transform:scaleY(1);
opacity:.8;
}
50%{
transform:scaleY(1.08);
opacity:1;
}
}

/* Electrons */

.electron{
position:absolute;
width:18px;
height:18px;
background:#00e5ff;
border-radius:50%;
box-shadow:0 0 20px #00e5ff;
opacity:0;
}

/* Control Panel */

.panel{
display:flex;
flex-direction:column;
gap:18px;
}

.box{
background:rgba(255,255,255,.04);
padding:18px;
border-radius:22px;
border:1px solid rgba(255,255,255,.08);
}

.box label{
display:block;
margin-bottom:12px;
font-weight:700;
color:#7dd3fc;
}

input[type=range],
select{
width:100%;
}

.range-value{
margin-top:10px;
font-weight:700;
color:#cbd5e1;
}

/* Buttons */

.buttons{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:12px;
}

button{
padding:16px;
border:none;
border-radius:20px;
font-size:16px;
font-weight:800;
cursor:pointer;
transition:.3s;
color:white;
}

button:hover{
transform:translateY(-3px) scale(1.03);
}

.start{
background:linear-gradient(90deg,#00c853,#00ff95);
}

.stop{
background:linear-gradient(90deg,#ff1744,#ff5252);
}

.reset{
background:linear-gradient(90deg,#2979ff,#00b0ff);
}

/* Progress */

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
background:linear-gradient(90deg,#00e5ff,#3b82f6);
box-shadow:0 0 25px #00e5ff;
transition:.2s;
}

/* Meters */

.readings{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:15px;
margin-top:15px;
}

.reading{
background:rgba(255,255,255,.04);
padding:20px;
border-radius:22px;
text-align:center;
border:1px solid rgba(255,255,255,.08);
}

.reading h3{
font-size:14px;
margin-bottom:10px;
color:#7dd3fc;
}

.reading span{
font-size:30px;
font-weight:800;
font-family:'Orbitron',sans-serif;
}

/* Oscilloscope */

canvas{
background:#020617;
border-radius:20px;
padding:15px;
border:1px solid rgba(255,255,255,.08);
}

/* Equation */

.equation{
margin-top:20px;
padding:20px;
border-radius:20px;
background:rgba(255,255,255,.04);
border:1px solid rgba(255,255,255,.08);
font-size:22px;
text-align:center;
font-family:'Orbitron',sans-serif;
color:#7dd3fc;
overflow:auto;
}

/* Footer */

.footer{
margin-top:30px;
text-align:center;
color:#94a3b8;
padding-bottom:20px;
}

/* Responsive */

@media(max-width:1000px){

.grid{
grid-template-columns:1fr;
}

.logo{
font-size:30px;
}

.simulator{
height:400px;
}

}

</style>
</head>

<body>

<!-- Loader -->

<div class="loader" id="loader">

<h1>⚡ ALI HAZIM Ultra</h1>

<p>Advanced RC Physics Laboratory</p>

<div class="loading-bar">
<div class="loading-fill"></div>
</div>

</div>

<!-- Main -->

<div class="container">

<div class="header">

<div>

<div class="logo">
ALI HAZIM Ultra
</div>

<div class="subtitle">
Advanced RC Physics Laboratory
</div>

</div>

<div class="authors">

<div class="badge">
👨‍🏫 إعداد الأستاذ سيف
</div>

<div class="badge">
👨‍💻 إعداد الطالب ALI HAZIM
</div>

</div>

</div>

<div class="grid">

<!-- LEFT -->

<div class="card">

<div class="title">
⚡ RC Circuit Simulation
</div>

<div class="simulator">

<div class="wire"></div>

<div class="capacitor">

<div class="plate"></div>
<div class="plate"></div>

</div>

<div class="electron" id="e1"></div>
<div class="electron" id="e2"></div>
<div class="electron" id="e3"></div>

</div>

<div class="equation">
V(t)=V₀(1-e^(-t/RC))
</div>

</div>

<!-- RIGHT -->

<div class="card">

<div class="title">
🎛 Physics Control Panel
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

<input type="range" id="resistance" min="1" max="100" value="50">

<div class="range-value" id="resText">
50 Ω
</div>

</div>

<div class="box">

<label>Capacitance (µF)</label>

<input type="range" id="capacitance" min="100" max="5000" value="2200">

<div class="range-value" id="capText">
2200 µF
</div>

</div>

<div class="buttons">

<button class="start" onclick="startSimulation()">
تشغيل
</button>

<button class="stop" onclick="stopSimulation()">
إيقاف
</button>

<button class="reset" onclick="resetSimulation()">
إعادة
</button>

</div>

<div class="box">

<label>Charge Level</label>

<div class="progress">
<div class="fill" id="fill"></div>
</div>

</div>

<div class="readings">

<div class="reading">

<h3>Voltage</h3>

<span id="voltValue">
12V
</span>

</div>

<div class="reading">

<h3>Current</h3>

<span id="currentValue">
0A
</span>

</div>

<div class="reading">

<h3>Resistance</h3>

<span id="ohmValue">
50Ω
</span>

</div>

<div class="reading">

<h3>Capacitance</h3>

<span id="capValue">
2200
</span>

</div>

</div>

<div class="box">

<label>Oscilloscope</label>

<canvas id="scope" height="220"></canvas>

</div>

</div>

</div>

</div>

<div class="footer">
MIT / NASA Inspired Physics Simulation Interface © 2026
</div>

</div>

<script>

/* Loader */

setTimeout(()=>{

document.getElementById("loader").style.opacity="0";

setTimeout(()=>{

document.getElementById("loader").style.display="none";

},1000);

},3200);

/* Elements */

const voltage = document.getElementById("voltage");
const resistance = document.getElementById("resistance");
const capacitance = document.getElementById("capacitance");

const voltValue = document.getElementById("voltValue");
const currentValue = document.getElementById("currentValue");
const ohmValue = document.getElementById("ohmValue");
const capValue = document.getElementById("capValue");

const resText = document.getElementById("resText");
const capText = document.getElementById("capText");

const fill = document.getElementById("fill");

const electrons = [
document.getElementById("e1"),
document.getElementById("e2"),
document.getElementById("e3")
];

let running = false;
let progress = 0;
let interval;

/* Update Values */

function updateValues(){

voltValue.innerText = voltage.value + "V";

ohmValue.innerText = resistance.value + "Ω";

capValue.innerText = capacitance.value;

resText.innerText = resistance.value + " Ω";

capText.innerText = capacitance.value + " µF";

let current = (
voltage.value / resistance.value
).toFixed(2);

currentValue.innerText = current + "A";

}

voltage.onchange = updateValues;
resistance.oninput = updateValues;
capacitance.oninput = updateValues;

updateValues();

/* Simulation */

function startSimulation(){

if(running) return;

running = true;

interval = setInterval(()=>{

progress += 0.6;

if(progress > 100){
progress = 100;
}

fill.style.width = progress + "%";

animateElectrons();

},60);

}

function stopSimulation(){

running = false;

clearInterval(interval);

electrons.forEach(e=>{
e.style.opacity = 0;
});

}

function resetSimulation(){

progress = 0;

fill.style.width = "0%";

stopSimulation();

}

/* Electrons */

function animateElectrons(){

electrons.forEach((e,i)=>{

e.style.opacity = 1;

e.animate([

{
transform:"translateX(-350px)"
},

{
transform:"translateX(350px)"
}

],{

duration:1800,
iterations:1,
delay:i*200

});

});

}

/* Oscilloscope */

const ctx = document.getElementById('scope');

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

/* Live Graph */

let t = 0;

setInterval(()=>{

if(!running) return;

t++;

let V = (
voltage.value *
(1 - Math.exp(-t/30))
).toFixed(2);

let I = (
(voltage.value / resistance.value) *
Math.exp(-t/30)
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

},200);

</script>

</body>
</html>
