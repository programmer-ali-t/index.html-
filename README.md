<!--
ALI HAZIM ULTRA — Advanced RC Physics Laboratory
Premium Scientific Edition
-->

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ALI HAZIM ULTRA | Advanced RC Physics Laboratory</title>

<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;900&display=swap" rel="stylesheet">

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>

:root{
--bg:#07111f;
--panel:#0f1b2d;
--glass:rgba(255,255,255,.05);
--cyan:#35d6ff;
--blue:#4d7dff;
--green:#18ff9c;
--orange:#ff9f1a;
--red:#ff4d6d;
--text:#eaf4ff;
--muted:#8da2c0;
}

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Tajawal',sans-serif;
}

body{
background:
radial-gradient(circle at top left,#10213b 0%,transparent 30%),
radial-gradient(circle at bottom right,#091523 0%,transparent 30%),
linear-gradient(180deg,#040b14,#07111f);
color:var(--text);
min-height:100vh;
overflow-x:hidden;
}

body::before{
content:'';
position:fixed;
width:100%;
height:100%;
background-image:
linear-gradient(rgba(255,255,255,.03) 1px,transparent 1px),
linear-gradient(90deg,rgba(255,255,255,.03) 1px,transparent 1px);
background-size:40px 40px;
pointer-events:none;
opacity:.25;
}

.container{
width:min(1500px,95%);
margin:auto;
padding:30px 0;
}

.header{
display:flex;
justify-content:space-between;
align-items:center;
padding:20px 30px;
background:rgba(255,255,255,.04);
backdrop-filter:blur(14px);
border:1px solid rgba(255,255,255,.08);
border-radius:28px;
margin-bottom:25px;
box-shadow:0 0 40px rgba(0,0,0,.4);
}

.brand h1{
font-size:34px;
font-weight:900;
background:linear-gradient(90deg,#fff,#35d6ff);
-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
}

.brand p{
color:var(--muted);
margin-top:6px;
}

.badges{
display:flex;
gap:15px;
flex-wrap:wrap;
}

.badge{
padding:12px 22px;
border-radius:16px;
background:rgba(255,255,255,.05);
border:1px solid rgba(255,255,255,.08);
font-weight:700;
}

.layout{
display:grid;
grid-template-columns:1.4fr .9fr;
gap:25px;
}

@media(max-width:1100px){
.layout{
grid-template-columns:1fr;
}
}

.panel{
background:rgba(255,255,255,.04);
backdrop-filter:blur(14px);
border:1px solid rgba(255,255,255,.08);
border-radius:30px;
padding:28px;
box-shadow:
0 10px 40px rgba(0,0,0,.35),
inset 0 1px 1px rgba(255,255,255,.04);
position:relative;
overflow:hidden;
}

.panel-title{
font-size:28px;
font-weight:800;
margin-bottom:25px;
display:flex;
align-items:center;
gap:10px;
}

.circuit-area{
height:430px;
position:relative;
border-radius:28px;
background:
linear-gradient(135deg,#101c2e,#08111f);
overflow:hidden;
}

.wire{
position:absolute;
background:linear-gradient(90deg,#35d6ff,#4d7dff);
box-shadow:0 0 25px #35d6ff;
}

.w1{
width:65%;
height:6px;
top:50%;
left:15%;
border-radius:20px;
}

.capacitor{
position:absolute;
top:37%;
left:47%;
display:flex;
gap:20px;
transform:translate(-50%,-50%);
}

.plate{
width:18px;
height:150px;
border-radius:30px;
background:linear-gradient(#dff9ff,#35d6ff);
box-shadow:0 0 40px #35d6ff;
}

.battery{
position:absolute;
left:60px;
top:40%;
width:90px;
height:150px;
border-radius:22px;
background:linear-gradient(180deg,#1d2f46,#0f1d2e);
border:2px solid rgba(255,255,255,.1);
box-shadow:0 0 30px rgba(0,0,0,.4);
display:flex;
align-items:center;
justify-content:center;
}

.battery::before{
content:'';
position:absolute;
top:-12px;
width:30px;
height:12px;
background:#cdd6e3;
border-radius:10px 10px 0 0;
}

.battery-level{
width:55px;
height:110px;
border-radius:16px;
background:linear-gradient(180deg,#00ff99,#18ff9c);
box-shadow:0 0 30px #18ff9c;
animation:pulse 2s infinite;
}

@keyframes pulse{
0%,100%{opacity:1}
50%{opacity:.6}
}

.switch{
position:absolute;
right:70px;
top:45%;
width:120px;
height:55px;
border-radius:40px;
background:linear-gradient(90deg,#ffb703,#ff8800);
box-shadow:0 0 30px rgba(255,166,0,.6);
cursor:pointer;
transition:.4s;
}

.switch::before{
content:'';
position:absolute;
width:46px;
height:46px;
background:white;
border-radius:50%;
top:4px;
right:5px;
transition:.4s;
}

.switch.active{
background:linear-gradient(90deg,#18ff9c,#00d47f);
}

.switch.active::before{
right:68px;
}

.equation{
margin-top:25px;
padding:22px;
border-radius:22px;
background:rgba(255,255,255,.04);
border:1px solid rgba(255,255,255,.06);
font-size:24px;
text-align:center;
color:#8be7ff;
font-weight:700;
}

.controls{
display:grid;
gap:22px;
}

.control-box{
background:rgba(255,255,255,.03);
padding:20px;
border-radius:22px;
border:1px solid rgba(255,255,255,.06);
}

.control-box label{
display:block;
margin-bottom:12px;
font-size:18px;
font-weight:700;
}

input[type=range]{
width:100%;
accent-color:#35d6ff;
}

select{
width:100%;
padding:16px;
background:#0e1827;
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

.btn{
padding:18px;
border:none;
border-radius:18px;
font-size:18px;
font-weight:800;
cursor:pointer;
color:white;
transition:.3s;
}

.start{
background:linear-gradient(90deg,#00ff99,#00d47f);
}

.stop{
background:linear-gradient(90deg,#ff4d6d,#ff234f);
}

.reset{
background:linear-gradient(90deg,#35d6ff,#4d7dff);
}

.btn:hover{
transform:translateY(-3px) scale(1.02);
}

.stats{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:18px;
margin-top:20px;
}

.stat{
padding:30px;
border-radius:24px;
background:rgba(255,255,255,.03);
border:1px solid rgba(255,255,255,.06);
text-align:center;
}

.stat h3{
color:#8da2c0;
font-size:18px;
margin-bottom:10px;
}

.stat p{
font-size:42px;
font-weight:900;
}

.chart-box{
margin-top:25px;
padding:20px;
border-radius:25px;
background:#07111f;
border:1px solid rgba(255,255,255,.06);
}

.footer{
text-align:center;
margin-top:30px;
color:#8da2c0;
font-size:18px;
}

.particles{
position:absolute;
inset:0;
overflow:hidden;
pointer-events:none;
}

.particles span{
position:absolute;
width:6px;
height:6px;
background:#35d6ff;
border-radius:50%;
animation:float 8s linear infinite;
opacity:.7;
}

@keyframes float{
0%{
transform:translateY(400px);
opacity:0;
}
20%{
opacity:1;
}
100%{
transform:translateY(-100px);
opacity:0;
}
}

</style>
</head>

<body>

<div class="container">

<div class="header">

<div class="brand">
<h1>ALI HAZIM ULTRA</h1>
<p>Advanced RC Physics Laboratory</p>
</div>

<div class="badges">
<div class="badge">👨‍🏫 إعداد الأستاذ سيف</div>
<div class="badge">🧠 إعداد الطالب ALI HAZIM</div>
</div>

</div>

<div class="layout">

<div class="panel">

<div class="panel-title">
⚡ محاكاة دائرة RC الاحترافية
</div>

<div class="circuit-area">

<div class="particles" id="particles"></div>

<div class="battery">
<div class="battery-level"></div>
</div>

<div class="wire w1"></div>

<div class="capacitor">
<div class="plate"></div>
<div class="plate"></div>
</div>

<div class="switch" id="switch"></div>

</div>

<div class="equation">
V(t)=V₀(1-e^-t/RC)
</div>

</div>

<div class="panel">

<div class="panel-title">
🎛️ نظام التحكم الفيزيائي
</div>

<div class="controls">

<div class="control-box">
<label>الجهد الكهربائي</label>
<select id="voltage">
<option>5</option>
<option>9</option>
<option>12</option>
<option>24</option>
</select>
</div>

<div class="control-box">
<label>المقاومة (Ω)</label>
<input type="range" min="1" max="1000" value="100" id="resistance">
<h2 id="rValue">100 Ω</h2>
</div>

<div class="control-box">
<label>السعة (µF)</label>
<input type="range" min="100" max="5000" value="2200" id="capacitance">
<h2 id="cValue">2200 µF</h2>
</div>

<div class="buttons">
<button class="btn start" onclick="startSimulation()">تشغيل</button>
<button class="btn stop" onclick="stopSimulation()">إيقاف</button>
<button class="btn reset" onclick="resetSimulation()">إعادة</button>
</div>

<div class="stats">

<div class="stat">
<h3>الجهد</h3>
<p id="vDisplay">5V</p>
</div>

<div class="stat">
<h3>التيار</h3>
<p id="iDisplay">0.05A</p>
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

<div class="chart-box">
<canvas id="chart"></canvas>
</div>

</div>

</div>

</div>

<div class="footer">
ALI HAZIM ULTRA — Advanced RC Physics Laboratory
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

const ctx=document.getElementById('chart');

const chart=new Chart(ctx,{
type:'line',
data:{
labels:[],
datasets:[
{
label:'Voltage',
data:[],
borderColor:'#35d6ff',
borderWidth:3,
tension:.4
},
{
label:'Current',
data:[],
borderColor:'#4d7dff',
borderWidth:3,
tension:.4
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
ticks:{color:'white'}
},
y:{
ticks:{color:'white'}
}
}
}
});

let interval;

function startSimulation(){

document.getElementById('switch').classList.add('active');

clearInterval(interval);

let t=0;

chart.data.labels=[];
chart.data.datasets[0].data=[];
chart.data.datasets[1].data=[];

interval=setInterval(()=>{

const V=parseFloat(document.getElementById('voltage').value);
const R=parseFloat(resistance.value);
const C=parseFloat(capacitance.value)/1000000;

const voltage=V*(1-Math.exp(-t/(R*C)));
const current=(V/R)*Math.exp(-t/(R*C));

chart.data.labels.push(t.toFixed(2));
chart.data.datasets[0].data.push(voltage.toFixed(2));
chart.data.datasets[1].data.push(current.toFixed(2));

chart.update();

document.getElementById('vDisplay').innerText=voltage.toFixed(2)+'V';
document.getElementById('iDisplay').innerText=current.toFixed(2)+'A';

t+=0.05;

if(t>5){
clearInterval(interval);
}

},100);

}

function stopSimulation(){
clearInterval(interval);
document.getElementById('switch').classList.remove('active');
}

function resetSimulation(){

clearInterval(interval);

chart.data.labels=[];
chart.data.datasets[0].data=[];
chart.data.datasets[1].data=[];
chart.update();

document.getElementById('switch').classList.remove('active');

document.getElementById('vDisplay').innerText='0V';
document.getElementById('iDisplay').innerText='0A';

}

for(let i=0;i<50;i++){

const span=document.createElement('span');

span.style.left=Math.random()*100+'%';
span.style.animationDuration=(4+Math.random()*6)+'s';
span.style.animationDelay=Math.random()*5+'s';

document.getElementById('particles').appendChild(span);

}

</script>

</body>
</html>
