<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>❤️</title>

<style>
body{
margin:0;
background:#0b0b0f;
font-family:'Cairo', sans-serif;
overflow:hidden;
color:#ddd;
}

/* 📱 iPhone */
.phone{
width:320px;
height:650px;
margin:auto;
margin-top:20px;
border-radius:40px;
background:rgba(255,255,255,0.05);
backdrop-filter:blur(20px);
box-shadow:0 0 40px rgba(255,0,100,0.2);
overflow:hidden;
position:relative;
}

.notch{
position:absolute;
top:0;
left:50%;
transform:translateX(-50%);
width:120px;
height:25px;
background:black;
border-radius:0 0 20px 20px;
z-index:10;
}

/* 🎬 loading */
#loading{
position:absolute;
width:100%;
height:100%;
background:black;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
z-index:20;
}

.loader-bar{
width:70%;
height:6px;
background:#222;
border-radius:10px;
overflow:hidden;
}

.loader-fill{
height:100%;
width:0%;
background:#ff4d6d;
animation:load 3s forwards;
}

@keyframes load{
to{width:100%;}
}

/* 🔐 */
#lock{
display:none;
text-align:center;
margin-top:60px;
}

.display{
letter-spacing:8px;
font-size:22px;
color:#aaa;
margin-bottom:15px;
}

.keys{
display:grid;
grid-template-columns:repeat(3,70px);
gap:10px;
justify-content:center;
}

.key{
background:rgba(255,255,255,0.08);
padding:15px;
border-radius:20px;
cursor:pointer;
color:#ccc;
}

.key:active{
background:#ff4d6d;
color:white;
}

/* 💌 */
.section{
position:absolute;
width:100%;
height:100%;
top:0;
left:0;
display:none;
padding:20px;
animation:fade 0.7s;
}

@keyframes fade{
from{opacity:0;transform:translateY(20px)}
to{opacity:1}
}

/* ❤️ hearts */
.heart{
position:absolute;
color:#ff4d6d;
animation:float 2s linear;
}
@keyframes float{
to{transform:translateY(-500px);opacity:0;}
}

/* 🎵 waves */
.wave{
position:absolute;
border:2px solid #ff4d6d;
border-radius:50%;
animation:wave 2s infinite;
}
@keyframes wave{
from{transform:scale(0.5);opacity:1}
to{transform:scale(2);opacity:0}
}

/* 🖼️ */
#gallery img{
width:100%;
border-radius:20px;
transition:1s;
}

/* 📖 */
#book{text-align:center}

/* ⏳ */
#counter{text-align:center}

button{
background:#ff4d6d;
border:none;
padding:10px 20px;
border-radius:20px;
color:white;
margin:5px;
}
</style>
</head>

<body>

<div class="phone">
<div class="notch"></div>

<!-- 🎬 Loading -->
<div id="loading">
<p>جارِ التحميل… ❤️</p>
<div class="loader-bar"><div class="loader-fill"></div></div>
</div>

<!-- 🔐 -->
<div id="lock">
<p>المكان ده لينا بس 🤍</p>
<div id="display" class="display"></div>

<div class="keys">
<div class="key">1</div><div class="key">2</div><div class="key">3</div>
<div class="key">4</div><div class="key">5</div><div class="key">6</div>
<div class="key">7</div><div class="key">8</div><div class="key">9</div>
<div class="key">0</div>
</div>

<p id="error"></p>
</div>

<!-- 💌 -->
<div id="message" class="section"></div>

<!-- 😏 -->
<div id="kiss" class="section">
<p id="kissText">مش هتعدي غير لما تديني بوسة 😏</p>
<button onclick="kiss()">امواااه 💋</button>
<button onclick="noKiss()">لا 😕</button>
</div>

<!-- 🎵 -->
<div id="audioSection" class="section">
<p>دوسي هنا 🎧</p>
<button onclick="playSong()">تشغيل</button>
<audio id="song" src="song.mp3"></audio>
</div>

<!-- 🖼️ -->
<div id="gallery" class="section">
<img id="img" src="img1.jpg">
</div>

<!-- 📖 -->
<div id="book" class="section">
<p id="page">بداية</p>
<button onclick="nextPage()">اقلب الصفحة</button>
</div>

<!-- ⏳ -->
<div id="counter" class="section">
<p id="time"></p>
<button onclick="love()">بتحبني قد اي</button>
<p id="loveCount"></p>
</div>

</div>

<script>

// 🎬 loading
setTimeout(()=>{
loading.style.display="none";
lock.style.display="block";
},3000);

// 🔐 password
let pass="2024326",input="";
document.querySelectorAll(".key").forEach(k=>{
k.onclick=()=>{
input+=k.innerText;
display.innerText=input;

if(input.length==pass.length){
if(input==pass){
lock.style.display="none";
show(message);
startMsg();
}else{
error.innerText="غلط 😏";
input="";display.innerText="";
}
}
}
});

// 🎬 transitions
function show(el){
document.querySelectorAll(".section").forEach(s=>s.style.display="none");
el.style.display="block";
}

// 💌
let msgs=[
"فاكرة أول مرة اتكلمنا فيها؟",
"أنا بحبك بطريقة مش بعرف أشرحها",
"بس بحسها كويس أوي ❤️"
];
let i=0;
function startMsg(){
let t=setInterval(()=>{
if(i<msgs.length){
let p=document.createElement("p");
p.innerText=msgs[i++];
message.appendChild(p);
}else{
clearInterval(t);
setTimeout(()=>show(kiss),2000);
}
},1500);
}

// 😏
let k=0;
function kiss(){
k++;
for(let i=0;i<15;i++){
let h=document.createElement("div");
h.className="heart";
h.innerText="❤️";
h.style.left=Math.random()*100+"%";
document.body.appendChild(h);
setTimeout(()=>h.remove(),2000);
}
if(k==3) show(audioSection);
}
function noKiss(){alert("غصب 😂");}

// 🎵
function playSong(){
song.play();
for(let i=0;i<3;i++){
let w=document.createElement("div");
w.className="wave";
w.style.width="100px";
w.style.height="100px";
w.style.top="50%";
w.style.left="50%";
document.body.appendChild(w);
}
show(gallery);
startGallery();
}

// 🖼️
let imgs=[
"img1.jpg","img2.jpg","img3.jpg","img4.jpg","img5.jpg",
"img6.jpg","img7.jpg","img8.jpg","img9.jpg","img10.jpg",
"img11.jpg","img12.jpg","img13.jpg","img14.jpg","img15.jpg",
"img16.jpg","img17.jpg","img18.jpg","img19.jpg","img20.jpg"
];

function startGallery(){
setInterval(()=>{
img.src=imgs[Math.floor(Math.random()*imgs.length)];
},3000);

setTimeout(()=>show(book),20000);
}

// 📖
let pages=["بداية","صدفة","ضحكة","حب","أنا","وانتي","سوا ❤️"];
let p=0;
function nextPage(){
page.innerText=pages[p++]||"❤️";
if(p>pages.length) show(counter);
}

// ⏳
let start=new Date("2024-03-26");
setInterval(()=>{
let now=new Date();
let d=Math.floor((now-start)/1000/60/60/24);
time.innerText=d+" يوم ❤️";
},1000);

// ❤️
let count=localStorage.getItem("love")||0;
function love(){
count++;
localStorage.setItem("love",count);
loveCount.innerText=count;

if(count%10==0) alert("بس كده؟ 😏");
if(count==100) alert("اهو بدأت اصدق ❤️");
}

// 👀 رجوع
if(localStorage.getItem("visited")){
alert("رجعتي تاني؟ 😏 وحشتيني ❤️");
}
localStorage.setItem("visited",true);

</script>

</body>
</html>
