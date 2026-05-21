<!--
ALI HAZIM Ultra
Advanced RC Physics Laboratory
FINAL PRO MAX VERSION
-->

<!DOCTYPE html>
<html lang="ar" dir="rtl">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ALI HAZIM Ultra | Advanced RC Physics Laboratory</title>

<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;700;900&display=swap" rel="stylesheet">

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Cairo',sans-serif;
}

body{

background:
radial-gradient(circle at top,#0d1b3d 0%,#050816 50%,#02040d 100%);

overflow-x:hidden;
color:white;
min-height:100vh;
position:relative;
}

/* background particles */

body::before{

content:'';
position:fixed;
inset:0;

background:
radial-gradient(circle,#00ffff22 1px,transparent 1px);

background-size:40px 40px;

animation:gridMove 20s linear infinite;

opacity:.25;
pointer-events:none;
}

@keyframes gridMove{
0%{transform:translateY(0)}
100%{transform:translateY(40px)}
}

/* glow */

body::after{

content:'';
position:fixed;

width:900px;
height:900px;

background:#00d9ff22;

top:-300px;
left:50%;
transform:translateX(-50%);

filter:blur(180px);

pointer-events:none;
}

/* loading */

.loader{

position:fixed;
inset:0;

background:#02040d;

display:flex;
align-items:center;
justify-content:center;
flex-direction:column;

z-index:99999;

transition:1s;
}

.loader h1{

font-size:55px;
font-weight:900;

background:linear-gradient(to right,#00e5ff,#ffffff);

-webkit-background-clip:text;
-webkit-text-fill-color:transparent;

margin-bottom:20px;
}

.loader p{

opacity:.7;
letter-spacing:3px;
}

.loader.hide{

opacity:0;
visibility:hidden;
}

/* main */

.container{

width:95%;
max-width:1700px;

margin:auto;

padding:30px 0;
}

/* header */

.header{

display:flex;
justify-content:space-between;
align-items:center;
flex-wrap:wrap;

gap:20px;

margin-bottom:30px;
}

.logo h1{

font-size:42px;
font-weight:900;

background:linear-gradient(to right,#00e5ff,#7df9ff,#ffffff);

-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
}

.logo p{

opacity:.7;
margin-top:6px;
}

.badges{

display:flex;
gap:14px;
flex-wrap:wrap;
}

.badge{

padding:14px 22px;

border-radius:20px;

background:rgba(255,255,255,.05);

border:1px solid rgba(255,255,255,.08);

backdrop-filter:blur(18px);

box-shadow:
0 0 25px rgba(0,229,255,.12);
}

/* layout */

.grid{

display:grid;
grid-template-columns:1.5fr .9fr;
gap:25px;
}

@media(max-width:1100px){

.grid{
grid-template-columns:1fr;
}

}

/* glass */

.glass{

background:
linear-gradient(
145deg,
rgba(255,255,255,.05),
rgba(255,255,255,.02)
);

border:1px solid rgba(255,255,255,.08);

backdrop-filter:blur(20px);

border-radius:35px;

box-shadow:
0 0 40px rgba(0,229,255,.08),
inset 0 0 20px rgba(255,255,255,.03);
}

/* lab */

.lab{

padding:35px;
position:relative;
overflow:hidden;
min-height:850px;
}

/* lab title */

.labTitle{

font-size:30px;
font-weight:900;

margin-bottom:25px;

color:#7df9ff;
}

/* circuit */

.circuit{

height:520px;

position:relative;

display:flex;
align-items:center;
justify-content:center;
}

/* energy wire */

.wire{

position:absolute;

width:78%;
height:10px;

border-radius:30px;

background:
linear-gradient(
90deg,
#00ffff,
#7df9ff,
#00ffff
);

box-shadow:
0 0 30px #00ffff,
0 0 90px #00ffff;

animation:wireFlow 2s linear infinite;
}

@keyframes wireFlow{

0%{
filter:hue-rotate(0deg);
}

100%{
filter:hue-rotate(360deg);
}

}

/* electrons */

.electron{

position:absolute;

width:18px;
height:18px;

border-radius:50%;

background:#00ffff;

box-shadow:
0 0 20px #00ffff,
0 0 45px #00ffff;

animation:electronMove 2s linear infinite;
}

.e2{
animation-delay:.4s;
}

.e3{
animation-delay:.8s;
}

.e4{
animation-delay:1.2s;
}

@keyframes electronMove{

0%{
left:12%;
opacity:0;
}

10%{
opacity:1;
}

90%{
opacity:1;
}

100%{
left:84%;
opacity:0;
}

}

/* battery */

.battery{

position:absolute;
left:7%;

width:100px;
height:200px;

border-radius:30px;

background:
linear-gradient(
145deg,
#0d1327,
#132145
);

border:2px solid rgba(255,255,255,.08);

box-shadow:
0 0 40px rgba(0,255,170,.25),
inset 0 0 30px rgba(0,255,170,.08);

display:flex;
justify-content:center;
align-items:flex-end;

padding:15px;
}

.battery::before{

content:'';

position:absolute;

top:-15px;

width:40px;
height:12px;

border-radius:8px;

background:#bbb;
}

.level{

width:100%;
height:85%;

border-radius:18px;

background:
linear-gradient(
to top,
#00ff88,
#00ffd5
);

box-shadow:
0 0 30px #00ff88;

animation:batteryPulse 2s infinite;
}

@keyframes batteryPulse{

50%{
filter:brightness(1.5);
}

}

/* capacitor */

.capacitor{

position:relative;
display:flex;
gap:35px;
z-index:2;
}

.cap{

width:28px;
height:260px;

border-radius:25px;

background:
linear-gradient(
180deg,
#ffffff,
#8ffcff,
#00d9ff
);

box-shadow:
0 0 40px #00e5ff,
0 0 120px #00d9ff;
}

/* switch */

.switch{

position:absolute;
right:7%;

width:170px;
height:70px;

border-radius:24px;

background:
linear-gradient(
145deg,
#ffb100,
#ff8400
);

box-shadow:
0 0 35px #ff9900;

cursor:pointer;

transition:.4s;
}

.switch:hover{

transform:scale(1.05);
}

/* formula */

.formula{

margin-top:30px;

padding:25px;

text-align:center;

font-size:30px;

border-radius:28px;

background:rgba(255,255,255,.03);

border:1px solid rgba(255,255,255,.05);

color:#7df9ff;

text-shadow:
0 0 20px #00e5ff;
}

/* side */

.side{

padding:30px;

display:flex;
flex-direction:column;
gap:22px;
}

/* title */

.panelTitle{

font-size:28px;
font-weight:900;
}

/* control */

.control{

padding:22px;

border-radius:24px;

background:rgba(255,255,255,.03);

border:1px solid rgba(255,255,255,.05);
}

.control label{

display:block;
margin-bottom:12px;
opacity:.85;
font-size:17px;
}

/* slider */

input[type=range]{

width:100%;
accent-color:#00e5ff;
}

/* buttons */

.buttons{

display:grid;
grid-template-columns:1fr 1fr 1fr;
gap:16px;
}

.btn{

padding:18px;

border:none;

border-radius:20px;

font-size:18px;
font-weight:800;

cursor:pointer;

transition:.3s;

color:white;
}

.start{

background:
linear-gradient(
145deg,
#00ff88,
#00c779
);

box-shadow:
0 0 30px #00ff88;
}

.stop{

background:
linear-gradient(
145deg,
#ff355e,
#ff004c
);

box-shadow:
0 0 30px #ff004c;
}

.reset{

background:
linear-gradient(
145deg,
#00b7ff,
#006eff
);

box-shadow:
0 0 30px #008cff;
}

.btn:hover{

transform:
translateY(-5px)
scale(1.03);
}

/* meters */

.meters{

display:grid;
grid-template-columns:1fr 1fr;
gap:18px;
}

.meter{

padding:28px;

border-radius:28px;

background:rgba(255,255,255,.03);

border:1px solid rgba(255,255,255,.05);

text-align:center;

position:relative;
overflow:hidden;
}

.meter::before{

content:'';

position:absolute;

width:250px;
height:250px;

background:#00e5ff22;

filter:blur(90px);

top:-120px;
left:-70px;
}

.meter h3{

opacity:.75;

margin-bottom:18px;
}

.value{

font-size:44px;
font-weight:900;

text-shadow:
0 0 20px #00e5ff;
}

/* chart */

.chartBox{

margin-top:25px;

padding:30px;
}

.chartTitle{

font-size:28px;
font-weight:900;

margin-bottom:20px;

color:#7df9ff;
}

/* footer */

.footer{

margin-top:30px;

padding-bottom:30px;

text-align:center;

opacity:.45;
}

</style>
</head>

<body>

<!-- LOADING -->

<div class="loader" id="loader">

<h1>ALI HAZIM Ultra</h1>
<p>ADVANCED RC PHYSICS LABORATORY</p>

</div>

<div class="container">

<!-- HEADER -->

<div class="header">

<div class="logo">

<h1>ALI HAZIM Ultra</h1>
<p>Advanced RC Physics Laboratory</p>

</div>

<div class="badges">

<div class="badge">👨‍🏫 إعداد الأستاذ سيف</div>
<div class="badge">👨‍💻 إعداد الطالب ALI HAZIM</div>
<div class="badge">⚡ Physics Engine Online</div>

</div>

</div>

<!-- GRID -->

<div class="grid">

<!-- LAB -->

<div class="glass lab">

<div class="labTitle">
⚡ RC Quantum Simulation Chamber
</div>

<div class="circuit">

<div class="battery">

<div class="level"></div>

</div>

<div class="wire"></div>

<div class="electron"></div>
<div class="electron e2"></div>
<div class="electron e3"></div>
<div class="electron e4"></div>

<div class="capacitor">

<div class="cap"></div>
<div class="cap"></div>

</div>

<div class="switch"></div>

</div>

<div class="formula">
V(t)=V₀(1-e<sup>-t/RC</sup>)
</div>

</div>

<!-- SIDE -->

<div class="glass side">

<div class="panelTitle">
🎛 Physics Control Center
</div>

<div class="control">

<label>الجهد الكهربائي</label>

<input type="range" min="1" max="20" value="5" id="volt">

</div>

<div class="control">

<label>المقاومة Ω</label>

<input type="range" min="10" max="1000" value="100" id="res">

</div>

<div class="control">

<label>السعة μF</label>

<input type="range" min="100" max="10000" value="2200" id="capacitance">

</div>

<div class="buttons">

<button class="btn start">تشغيل</button>
<button class="btn stop">إيقاف</button>
<button class="btn reset">إعادة</button>

</div>

<div class="meters">

<div class="meter">

<h3>الجهد</h3>

<div class="value" id="voltVal">
5V
</div>

</div>

<div class="meter">

<h3>التيار</h3>

<div class="value" id="ampVal">
0.05A
</div>

</div>

<div class="meter">

<h3>المقاومة</h3>

<div class="value" id="resVal">
100Ω
</div>

</div>

<div class="meter">

<h3>السعة</h3>

<div class="value" id="capVal">
2200
</div>

</div>

</div>

</div>

</div>

<!-- OSCILLOSCOPE -->

<div class="glass chartBox">

<div class="chartTitle">
📡 LIVE RC OSCILLOSCOPE
</div>

<canvas id="chart"></canvas>

</div>

<div class="footer">
ALI HAZIM Ultra — Advanced RC Physics Laboratory
</div>

</div>

<script>

/* loading */

window.onload=()=>{

setTimeout(()=>{

document.getElementById('loader').classList.add('hide')

},2200)

}

/* controls */

const volt=document.getElementById('volt')
const res=document.getElementById('res')
const cap=document.getElementById('capacitance')

const voltVal=document.getElementById('voltVal')
const resVal=document.getElementById('resVal')
const capVal=document.getElementById('capVal')
const ampVal=document.getElementById('ampVal')

function updatePhysics(){

voltVal.innerText=volt.value+"V"

resVal.innerText=res.value+"Ω"

capVal.innerText=cap.value

let current=(volt.value/res.value).toFixed(2)

ampVal.innerText=current+"A"

}

volt.oninput=updatePhysics
res.oninput=updatePhysics
cap.oninput=updatePhysics

updatePhysics()

/* chart */

const ctx=document.getElementById('chart')

new Chart(ctx,{

type:'line',

data:{

labels:[0,1,2,3,4,5,6,7,8,9,10],

datasets:[

{

label:'Voltage',

data:[0,1,2,3,3.8,4.2,4.5,4.7,4.85,4.92,5],

borderColor:'#00ffff',

borderWidth:4,

tension:.4,

pointRadius:0

},

{

label:'Current',

data:[5,4,3.2,2.4,1.9,1.4,1,.7,.5,.3,.1],

borderColor:'#005eff',

borderWidth:4,

tension:.4,

pointRadius:0

}

]

},

options:{

responsive:true,

plugins:{

legend:{

labels:{
color:'white'
}

}

},

scales:{

x:{

ticks:{
color:'white'
},

grid:{
color:'#ffffff11'
}

},

y:{

ticks:{
color:'white'
},

grid:{
color:'#ffffff11'
}

}

}

}

})

</script>

</body>
</html>
