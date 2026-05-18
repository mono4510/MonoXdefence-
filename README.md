# MonoXdefence-
Defence Exam Preparation Quiz Platform • By Mono
<!DOCTYPE html>
<html lang="en">
<head>

<meta charset="UTF-8">
<meta name="viewport"
content="width=device-width, initial-scale=1.0">

<title>MonoXDefence Quiz</title>

<link rel="stylesheet"
href="style.css">

</head>

<body>

<div class="watermark">
BY MONO
</div>

<div class="container">

<h1>NDA/CDS GS & Maths PYQ Quiz</h1>

<div id="quiz-box">

<h2 id="question">
Loading...
</h2>

<div id="options">
</div>

<button id="nextBtn">
Next Question →
</button>

<div id="scoreBox">
</div>

</div>

</div>

<script src="questions.js"></script>
<script src="script.js"></script>

</body>
</html>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial,sans-serif;
}

body{

background:#07111f;

color:white;

display:flex;

justify-content:center;

align-items:center;

min-height:100vh;

padding:20px;
}

.container{

width:100%;

max-width:750px;

background:#111827;

padding:30px;

border-radius:20px;

box-shadow:0 0 25px
rgba(0,255,255,0.12);

position:relative;
}

h1{

text-align:center;

margin-bottom:30px;

color:#38bdf8;
}

#question{

font-size:24px;

margin-bottom:25px;
}

.option{

background:#1e293b;

padding:15px;

border-radius:12px;

margin-top:15px;

cursor:pointer;

transition:0.2s;
}

.option:hover{

background:#38bdf8;

color:black;
}

.correct{

background:#22c55e !important;
}

.wrong{

background:#ef4444 !important;
}

#nextBtn{

margin-top:30px;

padding:14px 35px;

border:none;

border-radius:40px;

background:#38bdf8;

color:white;

font-size:18px;

cursor:pointer;
}

#scoreBox{

margin-top:30px;

font-size:30px;

text-align:center;

color:#38bdf8;
}

.watermark{

position:fixed;

top:50%;

left:50%;

transform:
translate(-50%,-50%)
rotate(-30deg);

font-size:75px;

font-weight:bold;

color:rgba(255,255,255,0.03);

pointer-events:none;
}
const questions = [

{
question:
"भारत का राष्ट्रीय पशु कौन है?",

options:[
"Tiger",
"Lion",
"Elephant",
"Leopard"
],

answer:"Tiger"
},

{
question:
"2 + 2 × 5 = ?",

options:[
"20",
"12",
"10",
"14"
],

answer:"12"
},

{
question:
"Who is known as the Father of Indian Constitution?",

options:[
"Mahatma Gandhi",
"BR Ambedkar",
"Nehru",
"Rajendra Prasad"
],

answer:"BR Ambedkar"
},

{
question:
"Square root of 144?",

options:[
"10",
"11",
"12",
"14"
],

answer:"12"
},

{
question:
"Which planet is known as Red Planet?",

options:[
"Earth",
"Mars",
"Venus",
"Jupiter"
],

answer:"Mars"
}

];
const question =
document.getElementById("question");

const options =
document.getElementById("options");

const nextBtn =
document.getElementById("nextBtn");

const scoreBox =
document.getElementById("scoreBox");

let current = 0;

let score = 0;

function loadQuestion(){

const q = questions[current];

question.innerText =
q.question;

options.innerHTML = "";

q.options.forEach(opt=>{

const div =
document.createElement("div");

div.classList.add("option");

div.innerText = opt;

div.onclick = ()=>checkAnswer(div,opt);

options.appendChild(div);

});
}

function checkAnswer(div,opt){

const correct =
questions[current].answer;

document.querySelectorAll(".option")
.forEach(btn=>{

btn.style.pointerEvents="none";

if(btn.innerText===correct){

btn.classList.add("correct");
}
});

if(opt!==correct){

div.classList.add("wrong");

}else{

score++;
}
}

nextBtn.onclick = ()=>{

current++;

if(current<questions.length){

loadQuestion();

}else{

showScore();
}
};

function showScore(){

document.getElementById("quiz-box")
.innerHTML = `

<h1>
Your Score:
${score}/${questions.length}
</h1>

`;
}

loadQuestion();
